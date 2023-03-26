# 如何构建一个规模达到数十亿的微小 URL 服务？

> 原文：<https://medium.com/swlh/how-to-build-a-tiny-url-service-that-scales-to-billions-f6fb5ea22e8c>

*这个故事最初发表在我的博客@linqz.io* [*这里*](https://www.linqz.io/2018/10/how-to-build-a-tiny-url-service-that-scales-to-billions.html) *。*

![](img/fe6f54a746083c866c94134e57fbe72d.png)

How to build a Url Shortner service ?

Twitter 的设计限制之一是每条消息被限制在 140 个字符以内，但如果你像我一样喜欢在 Twitter 消息中发布 URL，那 140 个字符就变得非常昂贵。这可能就是为什么 **Twitter 使用**[**TinyUrl**](http://tinyurl.com/)**服务或任何其他服务**自动将任何超过 30 个字符的 Url 转换为短 URL。后来，市场上出现了许多 url 缩短服务，即 Bitly、Google Url Shortner、Rebrandly 等。许多企业也开始在各种渠道的营销活动、广告活动等中使用它们。

**为 URL 创建一个唯一的、可重复的标识符**
我想很多人的第一反应可能是散列 URL 字符串——但这不是一个好主意，原因如下:

*   长度:大多数普通的散列算法(比如 md5)会产生很长的字符串，这有点违背了 url 缩短的目的。
*   唯一性:显然，如果这将是一个 URL 标识符，那么它需要是唯一的，而哈希本质上并不是唯一的——这意味着您需要处理 URL 创建了一个已经使用的哈希并且有一个替代项的情况。
*   查找:大多数散列是不可逆的，您需要使用散列作为 db 键来查找 URL——这对于一个非常大的 URL 集(想象一下几十亿)来说可能并不理想

今天我们将讨论如何构建和开发一个微型 url 服务。首先，让我们分成 3 个部分，算法，设计和如何扩展及其复杂性。

# 算法:

我们有 62 个字母数字字符，即[A-z0–9 A-Z]，尽管在 url 中允许使用连字符(-)和下划线(_)，但我们仍然希望避免使用它们，因为这将是一个难看的 url，如[http://abc.com/**c0-rw _**或](http://xyz.com/c0--rw_)[http://abc.com/**_ _ _ _ _ _-。**](http://xyz.com/______-.)
下面是 base10 到 base62 转换器的简单实现，这就是我们缩短一个 url 所需要的全部内容。

有了 62 个字符和一个 7，8，9，10，11 字符长的唯一字符串，我们可以缩短:

> ***62⁷= 3521614606208****网址*
> 
> ***62⁸=*218340105584896***网址*
> 
> ***62⁹=*13537086546263552***网址*
> 
> ***62⁰=*839299365868340224***网址*
> 
> ***62 =*52036560683837093888***网址*

所以你可以从上面看到，我们可以生成这些 62⁶= ~ 50 亿个可能的字符串& 62⁸ = ~218 万亿个可能的字符串，还可以根据需要生成更多。

所以，让我们说，我们决定要为下面的链接生成缩短的网址

> [https://medium . com/@ vaibhav 0109/cache-refreshing-techniques-446403 D1 ba 2](/@vaibhav0109/cache-refreshing-techniques-446403de1ba2)

所以我们将使用 base 62 生成一个唯一的 id，把它附加到我们的托管域，假设生成的 id 是`qa12WS4`，我们假设的托管域是`http://short.io`，那么我的小 url 就变成了`http://short.io/qa12WS4`

现在，我们只需要确保这个链接是唯一的，不会被再次分配，我们将在本博客的后面部分讨论如何存储的策略。

以下是可用于生成唯一字符串的两个函数:

```
private static final char[] corpus   = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789".toCharArray();/*
* Note if seed is unique then generated base62 number will be unique as well under load balance make sure this value is not same.
*/
public static final String getBase62From10(final long seed)
{
  String number = seed + "";
  char[] buf = new char[number.length()];
  int charPos = number.length() - 1;
  BigInteger bigIntegerNumber = new BigInteger(number);
  BigInteger radix = BigInteger.valueOf(62);

  while (bigIntegerNumber.compareTo(radix) >= 0)
  {
   buf[charPos--] = corpus[bigIntegerNumber.mod(radix).intValue()];
   bigIntegerNumber = bigIntegerNumber.divide(radix);
  }
  buf[charPos] = corpus[bigIntegerNumber.intValue()];
  return new String(buf, charPos, (number.length() - charPos));
}
/**
* @param longNumber
* a positive number in base 62
* @return the same number, in base 10
*/
public static final String getBase10From62(final long longNumber)
{
  String number = longNumber + "";
  BigInteger value = BigInteger.ZERO;
  for (char c : number.toCharArray())
  {
    value = value.multiply(BigInteger.valueOf(62)); 
    if ('0' <= c && c <= '9')
    {
      value = value.add(BigInteger.valueOf(c - '0'));
    }
    if ('a' <= c && c <= 'z')
    {
      value = value.add(BigInteger.valueOf(c - 'a' + 10));
    }
    if ('A' <= c && c <= 'Z')
    {
      value = value.add(BigInteger.valueOf(c - 'A' + 36));
    }
   }
   return value.toString();
}
```

# 设计:

现在让我们转到应用程序的设计部分。根据系统的负载或者应用程序是否在负载均衡器之后，可以有多种方法。首先是最简单的，其次是对第一种的改进。

在最简单的情况下，我们可能可以通过以下几列:

*   id(数据库生成的序列 ID)
*   原始 url-原始 URL 值
*   缩短 _url
*   创建日期
*   到期日期

**从数据库生成标识符**

1.  现在，如果您提供一个字符串 URL 值，您的代码只需要将它和创建日期一起插入到表中，这将创建行和惟一的 ID。
2.  接下来，获取唯一的数字 ID，并将其转换为 base-62(这将把数值转换为 base-62 表示(而不是普通的 base10，它将允许 0–9、a-z、A-Z 作为字符)。这为您提供了一个形式为`qa12WS4`的标识符。
3.  现在，将 base62 字符串添加到您的短域名`http://short.io`的基本 url 中，瞧，您得到一个缩短的 url 作为`http://short.io/qa12WS4`，并将其更新到短 url 列中，并注明到期日期。
4.  现在你只需要编写重定向逻辑，因为谁点击了这个缩短的 url，你就从 Db 中获取详细信息，并将其重定向到原始 Url。

这种方法有两个缺点:

*   首先，我们做了两个数据库操作，插入和更新，在高负载下它不会伸缩。
*   其次，在数据库迁移的情况下，序列 id 不能被合并，因为我们可能将相同的序列 id 生成到两个表中。

现在让我们来讨论一下改进，我们可以改进两件事，首先是数据库结构，其次，我们可以只进行单次插入，而不是插入和更新。数据库结构如下:

*   id_hash (base 62 生成的字符串作为主键)
*   原始 _url
*   缩短 _url
*   创建日期
*   到期日期

现在，要将 id_hash 作为主键，我们需要一个集中式服务，它为我提供唯一的种子令牌，例如，我们使用 Redis 自动增量功能(因为它本质上是原子的),我们可以获得一个种子编号并生成一个 base 62 字符串，这也将在负载平衡下的两个实例中工作。根据需求，可以构建多种方法来获得独特的种子。

# 该系统的规模和复杂性:

**流量估计:**对于每月 5 亿个新的网址缩短，我们可以预计在同一时期会有(100 * 500M = > 50B)个重定向。我们系统的每秒查询数(QPS)是多少？

每秒新的 URL 缩写:

a) 5 亿/ (30 天* 24 小时* 3600 秒)= ~ 192 个 URLs 秒

b) 10 亿/ (30 天* 24 小时* 3600 秒)= ~386 个网址/秒

每秒 URL 重定向数，考虑 100:1 的读/写比:

a) 100 * 5 亿= 500 亿次重定向

500 亿/ (30 天* 24 * 3600 ) = ~ 19K/s

b) 100 * 10 亿= 1000 亿次重定向

1000 亿次/ (30 天* 24 小时* 3600 秒)= ~ 38K/秒

**存储估计:**假设我们将每个 URL 缩短请求(以及相关的缩短链接)存储了 2 年。由于我们预计每个月会有 10 亿个新 URL，因此我们预计要存储的对象总数将达到 300 亿:

10 亿* 2 年* 12 个月= 240 亿

让我们假设每个存储的对象大约为 500 字节(这只是一个大概的估计——我们稍后会深入研究)。我们将需要 15TB 的总存储空间:

240 亿* 500 字节= 12 TB

**带宽估计:**对于写请求，由于我们预计每秒钟有 386 个新 URL，我们服务的总传入数据将为每秒 100KB:

386 * 500 字节=约 200 KB/秒

对于读取请求，由于每秒钟我们预计大约 19K 的 URL 重定向，我们服务的总传出数据将为每秒 9MB。

38K * 500 字节=约 18mb/秒

**内存估计:**如果我们想缓存一些经常访问的热门网址，我们需要多少内存来存储它们？如果我们遵循 80–20 规则，也就是说 20%的 URL 产生 80%的流量，我们会缓存这 20%的热门 URL。

因为我们每秒有 38，000 个请求，所以我们每天会收到 34 亿个请求:

38 K * 3600 秒* 24 小时= ~ 34 亿

为了缓存 20%的请求，我们需要 340GB 的内存。

0.2 * 34 亿* 500 字节=约 340 GB

现在，既然我们对规模有了简单的概念，我们就可以设计构建系统的约束条件，比如我们可以限制用户在某个时间段内创建和重定向一定数量的 URL。

我们还需要处理数据库(SQL 或 NoSQL)上的负载。现在让我们转到与规模相关的复杂问题。对于 DB 秤，我们需要:

**a .基于范围的分区:**我们可以根据 URL 的第一个字母或哈希键，或者根据创建日期或到期日期，将 URL 存储在单独的分区中。这种方法称为基于范围的分区。

这种方法的主要问题是它会导致不平衡的分区。

**b .基于散列的分区:**在这个方案中，我们获取存储对象的散列。然后，我们根据散列计算使用哪个分区。

我们的散列函数会将 URL 随机分配到不同的分区中(例如，我们的散列函数总是可以将任何键映射到[1…256]之间的一个数字)，这个数字将代表我们存储对象的分区。

**清除数据库数据:**

条目应该永远保留还是应该被清除？如果达到用户指定的过期时间，链接会发生什么情况？

如果我们选择主动搜索过期链接来删除它们，这将给我们的数据库带来很大压力。相反，我们可以慢慢地删除过期的链接，做一个懒惰的清理。我们的服务将确保只有过期的链接将被删除，虽然一些过期的链接可以生存更长时间，但永远不会返回给用户。

*   每当用户试图访问过期的链接时，我们可以删除该链接并向用户返回一个错误。
*   单独的清理服务可以定期运行，从我们的存储和缓存中删除过期的链接。该服务应该是非常轻量级的，并且可以被调度为仅在用户流量预计较低时运行。
*   我们可以为每个链接设置一个默认的到期时间(例如，两年)。
*   我们是否应该删除在一段时间内没有被访问过的链接，比如说六个月？这可能很棘手。由于存储越来越便宜，我们可以决定永远保留链接。

缓存是频繁访问 url 的另一个复杂方面。

**我们应该有多少缓存？**

我们可以从 20%的日流量开始，根据客户的使用模式，我们可以调整我们需要多少缓存服务器。根据上面的估计，我们需要 340 GB 的内存来缓存 20%的日常流量。

**哪种缓存回收策略最符合我们的需求？**

易失性— ttl、LRU 等是多个选项。

参考资料:

[https://www . educative . io/collection/page/5668639101419520/5649050225344512/5668600916475904](https://www.educative.io/collection/page/5668639101419520/5649050225344512/5668600916475904)

可能会有更多的缩放问题，我试图涵盖基本的最低要求，同时建立一个可扩展的缩短 url 服务。

有问题吗？建议？评论？

下一步是什么？ [**在媒体上关注我**](/@vaibhav0109) 成为第一个阅读我的故事的人。