# Cookies 与本地存储:有什么区别？

> 原文：<https://medium.com/swlh/cookies-vs-localstorage-whats-the-difference-d99f0eb09b44>

![](img/205bead2631967abe829b378e583df16.png)

Cookies — Photo by [rawpixel](https://unsplash.com/photos/0KSffDglOAE?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/cookies?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

很长一段时间，cookies 是存储用户访问你的应用程序或网站的信息的主要方式。它们被用来记录有状态的元素，比如用户更改的购物车条目或选项。它们还被用来记住用户的浏览习惯，或者在用户从一个页面转到另一个页面时保持用户登录。然后，HTML5 出现了，并引入了 LocalStorage 作为另一种数据存储选项。这个新的 Javascript 对象(以及 SessionStorage)拥有比 cookies 大得多的存储容量，高达 5MB。在本文中，我们将比较和对比 cookies 和本地存储。

饼干——小而强大
首先，我们将从探索饼干的基本信息开始。我们还将讨论它们的优缺点。那么，什么是饼干？据 whatarecookies.com 称，它们是由网站放在用户电脑上的小文本文件。它们以 4KB 的最大容量保存非常少量的数据。Cookies 有不同的用途，例如存储网站上访问过的页面或用户的登录信息。它们的局限性在于它们只能存储字符串。

许多安全网站在用户登录后使用 cookies 来验证他们的身份，以防止他们不得不在每个页面上重新输入他们的凭据。cookies 的另一个用途是根据网站上有限的浏览历史定制或调整用户体验。

![](img/dcfe07641504d151e82a17dbf008d9b0.png)

Two Types of Cookies — Photo by Oliya Nadya on Unsplash

**两种类型的 cookie** 有两种类型的 cookie:持久 cookie 和会话 cookie。会话 cookies 不包含过期日期。相反，它们仅在浏览器或选项卡打开时才会被存储。一旦浏览器关闭，它们就永远丢失了。这种类型的 cookie 可能用于存储银行用户在其银行网站中导航时的凭证，因为一旦选项卡关闭，他们的信息就会被遗忘。

永久 cookie*有截止日期吗？这些 cookies 存储在用户的磁盘上，直到过期，然后被永久删除。它们可以用于其他活动，例如记录用户在特定网站上的习惯，以便在每次访问时定制他们的体验。*

![](img/130530718549df513be0c6eb3ed6a971.png)

Macbook — Photo by rawpixel on Unsplash

**LocalStorage——更长久的解决方案** html 5 出来后，cookies 的很多用途都被 local storage 的使用所取代。这是因为 LocalStorage 比 cookies 有很多优势。最重要的区别之一是，与 cookies 不同，数据不必在每个 HTTP 请求中来回发送。这减少了客户端和服务器之间的总流量以及浪费的带宽量。这是因为数据存储在用户的本地磁盘上，不会因为失去互联网连接而被破坏或清除。此外，如前所述，LocalStorage 最多可以容纳 5MB 的信息。这比 cookies 存储的 4KB 要大得多。

就过期时间而言，LocalStorage 的行为更像持久性 cookies。除非通过 Javascript 代码清除数据，否则数据不会自动销毁。这对于需要存储更长时间的较大数据来说很有好处。此外，使用 LocalStorage，您不仅可以存储字符串，还可以存储 Javascript 原语和对象。

![](img/ce76982d26923c9b648c039dd03bc5e9.png)

People visiting a website — Photo by [John Schnobrich](https://unsplash.com/photos/2FPjlAyMQTA?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/laptop?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

在我的后端 web 开发课程中，我们讨论了 LocalStorage 优于 cookies 的情况。一个很好地使用本地存储的例子可能是在没有持久互联网连接的地区使用的应用程序。我的课程老师 Dani Roxberry 在过去开发了这样一个应用程序，并使用 LocalStorage 来保护和存储在 WiFi 或数据连接不良的地区收集的数据。

为了更好地利用本地存储，在这种情况下存储的数据的威胁级别必须非常低。为了保护客户端隐私，最好在重新建立连接时上传数据，然后删除本地存储的版本。此外，对存储的数据进行加密以使其不容易被黑客攻击也是有利的。在我们的课堂讨论中，我们还发现，像财务信息这样的高度易受攻击的数据，不能以这种方式使用本地存储进行适当的存储或保护。

**结论**
虽然这些存储选项各有利弊，但它们在现代 web 开发中都有应用。Cookies 比较小，可以随每个 HTTP 请求发回服务器信息，而 LocalStorage 比较大，可以在客户端保存信息。

当你制作下一个应用程序时，考虑这些不同的用途，并决定哪种类型的存储适合你。

[![](img/308a8d84fb9b2fab43d66c117fcc4bb4.png)](https://medium.com/swlh)

## 这篇文章发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，拥有+390，426 名读者。

## 在此订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

[![](img/b0164736ea17a63403e660de5dedf91a.png)](https://medium.com/swlh)