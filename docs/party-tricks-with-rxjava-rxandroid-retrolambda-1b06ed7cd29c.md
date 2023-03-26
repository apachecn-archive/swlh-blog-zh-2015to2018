# RxJava、RxAndroid 和 Retrolambda 的派对技巧

> 原文：<https://medium.com/swlh/party-tricks-with-rxjava-rxandroid-retrolambda-1b06ed7cd29c>

![](img/c27c5db468d4df9923b913e7715dbae4.png)

## 所有酷小孩都在做，为什么你不呢？

"*用户期望实时数据。他们现在想要自己的推文***。他们的顺序确认了* ***现在***。作为开发人员，您需要一劳永逸的消息传递。你真的不想在等待结果的时候被堵住……你想让结果在准备好的时候推给你，无论什么时候。更好的是，当处理大的结果集时，您希望在结果准备好的时候接收单个结果，因为您不想等到整个结果集被处理完之后才看到列表中的第一项。开发者有很多工具来推送数据，这很简单。开发人员需要工具来对推送的数据做出反应。*

## *让有光…甚至更好…反应扩展！*

*被描述为“*一个通过使用可观察序列*来组成异步和基于事件的程序的库”，它非常适合于引入和管理用于*卸载*目的的并发性。也就是说，并发执行一组给定的工作来释放当前线程(通常是 UI 线程)。这种方法的一个非常流行的用途是维护一个响应迅速的 UI，这对于一个出色的移动用户体验来说是必不可少的！*

*在过去的几个月里，当我学习如何使用它们时，我收集了一些用法示例，我决定分享它们…*

*请记住:*

> *无功代码的基本构件是**可观察对象**和**用户**。一个**可观察发射物品**；一个**用户消费那些项目**。*

***导入您的依赖关系:***

***…并配置 retrolambda:***

> *[https://github.com/orfjackal/retrolambda](https://github.com/orfjackal/retrolambda)*

***更新**:我已经写了一个关于配置 retrolambda [的超级简单方法的小教程 https://medium . com/@ cesarmferreira/retro lambda-on-Android-191 cc8151 f85](/@cesarmcferreira/retrolambda-on-android-191cc8151f85)*

*启动你的 IDE，让我们试试吧！*

*有些人认为，因为 RxJava 是关于“*异步序列*”的，所以默认情况下，所有事情都会发生在不同的线程上，但事实并非如此，所以不要忘记定义两个**。观察()**和。 **subscribeOn()。**第一个定义了订阅观察者的线程(完成后接收数据的线程),第二个产生了一个新的可观察对象，它将导致您的订阅发生在从指定调度程序中检索的线程上，而不是从调用 **subscribe()** 的线程(android 的主线程，UI 线程)上。*

## ***奖励**:改装*

*… + RxJava + RxAndroid + Retrolambda*

*让我们来看看他们的行动:*

*很可爱吧？*

*这里有几个额外的链接，里面有很酷的信息:*

*   *RxJava 官方文档[https://github.com/ReactiveX/RxJava/wiki](https://github.com/ReactiveX/RxJava/wiki)；*
*   *丹·卢(Dan Lew)在他的博客(http://blog.danlew.net/)上发表了一系列精彩的文章。*
*   *[杰克·沃顿](https://twitter.com/JakeWharton)关于改造和 RxJava(网飞开源 Meetup s02e 02 07/2014)[https://speakerdeck.com/jakewharton/2014-1](https://speakerdeck.com/jakewharton/2014-1)；*
*   *[Kaushik Gopal](https://twitter.com/kaushikgopal) (伟大[碎片化播客](https://twitter.com/FragmentedCast)的联合主持人)提供 RxJava 和 rx Android[https://www.youtube.com/watch?v=k3D0cWyNno4](https://www.youtube.com/watch?v=k3D0cWyNno4)上的入门；*
*   *由[考希克·戈帕尔](https://twitter.com/kaushikgopal)[https://github.com/kaushikgopal/RxJava-Android-Samples](https://github.com/kaushikgopal/RxJava-Android-Samples)提供的令人敬畏的例子列表；*
*   *杰克沃顿在测试，SqlBrite，NotRxAndroid，RxJava 和更多的[http://fragmentedpodcast.com/episodes/7/](http://fragmentedpodcast.com/episodes/7/)；*
*   *由方形[http://square.github.io/retrofit/](http://square.github.io/retrofit/)改装*
*   *rx Java[https://github.com/ReactiveX/RxJava](https://github.com/ReactiveX/RxJava)；*
*   *rx Android[https://github.com/ReactiveX/RxAndroid](https://github.com/ReactiveX/RxAndroid)。*

*如果你有你想看到的建议，请提出来或者创建一个**拉动请求**到这个**要点**[https://gist.github.com/cesarferreira/510aa2456dc0879f559f](https://gist.github.com/cesarferreira/510aa2456dc0879f559f)*

*如果你有 questions☺，请给我打电话*

*![](img/71d955550911c61d0aef4c66a71f8e15.png)*

**发表于* **创业、旅游癖和生活黑客***

*[![](img/0bf7ebc25c05a1d52c6add818a95aa71.png)](http://supply.us9.list-manage.com/subscribe?u=310af6eb2240d299c7032ef6c&id=d28d8861ad)**[![](img/1b4fd39dd738a88ac13336ad93f1049c.png)](https://blog.growth.supply/)**[![](img/93f21657a8ed7c0f741216a91b53c713.png)](https://twitter.com/swlh_)*

*-*