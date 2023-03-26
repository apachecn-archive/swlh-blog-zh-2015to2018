# 拉勒维尔增速器

> 原文：<https://medium.com/swlh/laravel-speed-booster-6babd07d84ab>

![](img/22f727fe4bb1046eebafb61ba5aeda30.png)

我猜想既然你在这里，你已经在使用 Laravel，我也猜想你用了足够的时间来达到这个水平，你开始调整它的工作方式并加以改进。是的，我同意 Laravel 是一个很棒的 PHP 框架，但是对于大多数应用程序来说，它的代码库太抽象和普通了，它试图覆盖应用程序可能有的所有情况。
但是，每当你做一些过于抽象或普通的东西时，你会增加额外的不必要的复杂性和浪费的速度，如果你担心性能，这肯定会惹恼你(我目前的公司就是这种情况，所以我们进行了调查)。

[![](img/78437253c88bc323dbb42fb6cd5c79da.png)](https://www.awin1.com/cread.php?s=2325653&v=6798&q=295495&r=628669)

当然，当我们在这里谈论性能改进时，我们谈论的是毫秒，尤其是如果你担心[谷歌的推荐](https://developers.google.com/speed/docs/insights/Server)低于 200 毫秒。

> 您应该将服务器响应时间减少到 200 毫秒以下。有许多潜在的因素可能会降低服务器的响应速度:缓慢的应用程序逻辑、缓慢的数据库查询、缓慢的路由、框架、库、资源 CPU 不足或内存不足。

在网站速度方面有一些客户端的改进可以真正改善你的用户体验[，其他专家可以谈论这些](/@ra.hul/kickass-your-website-front-end-speed-fedeaa51df36)，但是我们将在这里谈论服务器端的改进。

我们开始吧..

因此，经过一些调查和分析，我们发现了拉勒维尔潜在的改进之处:

*   视图管道
*   视图渲染
*   太多中间件
*   路线缓存:
*   其他 PHP 优化

# 视图管道

正如我们之前所说的，Laravel 添加了许多通用的东西来包含所有的可能性，在视图的情况下，它是数据的加载和检查过程，当渲染函数发生时发生。

更具体地说，每次渲染的开销之一是 **Illuminate\View** 中的函数 **gatherData** ，如果你的网站有一个非常嵌套的结构，即大量的@includes、@sections、@layouts、@for loops，..，等等

您会在这个函数中找到以下代码:

```
$data = array_merge($this->factory->getShared(), $this->data);**foreach** ($data **as** $key => $value) {
    **if** ($value **instanceof** Renderable) {
        $data[$key] = $value->render();
    }
}**return** $data;
```

根据我的经验，很少有人使用带有 Renderable passed 的视图。

所以最棒的是覆盖 Laravel 的功能[我不会说如何覆盖；谷歌上有很多这样的方法]并编写如下代码:

```
**protected function** gatherData()
{
    $data = array_merge($this->factory->getShared(), $this->data);

    **return** $data;
}
```

这样做之后，您会注意到性能的提高，这取决于服务器的速度/页面大小等等。

在我们的例子中，增量大约是服务器端加载时间的 5-10%[大约 20 毫秒]。

# 视图渲染:

上面提到的视图渲染是在一个会话调用中经常发生的事情，事情是这个[渲染函数](https://laravel.com/api/5.3/Illuminate/View/View.html#method_render)的管道是它以递归的方式工作。

如果您的页面包含几个部分，而没有很多嵌套视图，这是正常的。但是，如果您使用很多@ includes/@部分，尤其是在 ForLoops 中的部分，那么您的速度可能会大大降低。

这么说吧，如果你在一个页面里有 100 个产品，大概是这样的:

```
**@foreach (**$products **as** $key => $item) **@include(** 'productView',
          [
            'product' => $item,
          ]
        **)
@endforeach**
```

假设在产品视图中有两个其他的包含。在这种情况下，当视图被呈现时，将导致 200 次呈现调用。
在我们分析了我们的应用程序后，我们发现速度因此显著下降。解决这个问题的方法是:

*   设置一个标准，避免超过 2 个嵌套级别，以避免过多的渲染。
*   扁平化你的观点，少用 includes(这当然不是一个好的解决方案。如果是长期维护的平台)。
*   使用一个库，它将使你对生产部署过程的看法变得扁平(因为我没有找到这样做的包，所以我写了一个[编译刀片](https://github.com/Te-cho/compile-blades))。
    (请注意，如果你的刀片中有太多代码，也会造成速度大幅下降，所以你必须选择一个中间点)。

# 太多中间件:

也许你知道，也许你不知道，Laravel 的主要特性有很多管道开销，所以我建议不要使用很多中间件，因为每个中间件都有 pre&post 调用。作为最佳实践，我会选择 5 个最大中间件。

# 路线缓存:

我将引用 ionuț·比耶斯库在一篇文章中说的话，这篇文章比我以前解释得更好

> 在 laravel，路由也是一项昂贵的任务。要缓存 routes.php 文件，请运行以下命令:
> 
> `*php artisan route:cache*`
> 
> 请注意，它不适用于闭包。如果您使用闭包，这是将它们移入控制器的好机会，因为 artisan 命令会在试图编译绑定到闭包而不是正确的控制器方法的路线时抛出异常。
> 与配置缓存一样，对 routes.php 的任何更改将不再有任何影响。要刷新缓存，请在每次更改 routes 文件时运行上述命令。要完全清除路由缓存，请运行以下命令:
> 
> `*php artisan route:clear*`

[![](img/7fce355e1192b707d510fa8ae34d8fe3.png)](https://www.awin1.com/cread.php?s=2327751&v=6798&q=347896&r=628669)

# 其他 PHP 优化

其他一些可以显著提高网站速度的东西包括:

*   配置缓存
*   类别映射优化
*   优化合成器自动加载

这些也可以在这篇[技术细节文章](https://bajescu.com/posts/view/improving-your-laravel-application-performance)中查看。

根据我的经验，如果你做到了所有这些，而你以前没有做到，你将会在你的服务器页面加载时间上获得 20-50%的提升。

**仅供参考，你真的应该买一个** [**程序员笔记本电脑/工作站贴纸**](http://tidd.ly/8f345c71) **，它们太棒了😍。**

**其他有用的文章:**

*   [https://medium . com/tekno Muslim/simple-boost-laravel-performance-in-production-7e 5c 63 e 32 ffd](/teknomuslim/simply-boost-laravel-performance-in-production-7e5c63e32ffd)

![](img/9e47fe293d4de059bbccb4fef97b5ded.png)[![](img/308a8d84fb9b2fab43d66c117fcc4bb4.png)](https://medium.com/swlh)

## 这个故事发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的企业家出版物，拥有 308，589+人。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

[![](img/b0164736ea17a63403e660de5dedf91a.png)](https://medium.com/swlh)