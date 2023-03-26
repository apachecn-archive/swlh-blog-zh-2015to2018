# 为什么选择 RxFlux？

> 原文：<https://medium.com/swlh/why-rxflux-5b687f062709>

我意识到我的[上一篇文章](/swlh/rxflux-android-architecture-94f77c857aa2)展示了一个使用 [RxFlux](https://github.com/skimarxall/RxFlux) 的应用程序的真实例子是相当广泛的。

我决定做一个预介绍，在这里我将试图说服你为什么你应该使用它，或者至少阅读更多关于它的内容。

**那么……为什么？**

首先 RxFlux 来自于 [RxJava](https://github.com/ReactiveX/RxJava/wiki) 和 [Flux](https://facebook.github.io/flux/docs/overview.html) 模式的组合。如果你不知道 RxJava 的优势，只要谷歌一下，你会发现上千个关于它的帖子。另一方面，Flux 是不同平台中的一种已知模式，最近出现在 Android 世界中。

没有神奇的模式或框架，但我真的认为 RxFlux 可以帮助你，原因如下:

一个 **架构，** RxFlux 基于一个清晰明了的架构。这将保持你的应用程序有条理，同时让你在每个部分独立工作。

R **eadability，**视图-动作-存储之间有明确的契约。每个部分都定义了它能做什么和提供什么。这种契约使得在保持实现和样板代码分离的同时，很容易知道你的应用程序的实际方法和逻辑是什么。

T **estability，**各部分的清晰分离和定义的契约使得独立测试变得容易。我们可以模拟输入，测试逻辑并验证输出。应用程序的逻辑，分为商店和行动，可以进行“单元测试”，视图将被“功能测试”覆盖，集成测试将验证每个部分之间的连接。

S **calability，**Flux 的结构允许我们耦合和解耦模块，因为它们独立工作，允许应用程序以最小的变化进行扩展和修改。

![](img/68848fbfe5ea68e63f2ccbf98d60e3c9.png)

The acronym was not intended

以上是总体要点，现在让我们关注具体问题以及 RxFlux 如何解决这些问题。

你是否经常处理超长的活动或片段，混淆逻辑，生活在回调地狱？

> RxFlux 有一个清晰的概念分离，将保持你的活动和片段在一个饮食中，因为它使用 RxJava 和一个总线模式，它将从你的生活中移除回调地狱。

你有没有发现自己到处处理错误，到处复制代码和长 if/else 子句？

> RxFlux 将所有的错误处理集中在一个方法中，该方法可以在一个基本活动或其子活动中被覆盖，当试图执行一个动作时，每次发生错误时都会调用该方法。该操作将包含处理错误所需的所有信息(类型、错误、操作…)。

分析和营销工具呢？他们总是让代码变得肮脏，他们不断地改变，并且总是很难将他们集成到大项目中。

> RxFlux 流允许商店注册动作，为什么不创建一个“AnalyticStore”来获取所有调度的动作呢？这将允许我们将所有这些工具集中在一个点上，我们将能够从操作中获得所需的信息，甚至为它们创建特定的操作并将其推送到每个工具。

![](img/9ae8ddaecc37c3071044e5887d4822dc.png)

如果我的论点说服了你，那就花些时间阅读更多相关内容，并尝试一下资源库中的例子。否则，请留下评论，我很想听听你的意见。

后续步骤:

1.  检查 GitHub 存储库:

[](https://github.com/skimarxall/RxFlux) [## skimarxall/RxFlux

### RxFlux 是一个小的框架，以遵循带有 RxJava 功能的 Flux 设计模式

github.com](https://github.com/skimarxall/RxFlux) 

2.跟随[维基。](https://github.com/skimarxall/RxFlux/wiki)

3.阅读下一篇 [RxFlux Android 架构](/swlh/rxflux-android-architecture-94f77c857aa2#.ampkspe09)

在推特上找到我:[@ marxalski](https://twitter.com/marxallski)和 [Google+](https://plus.google.com/u/1/+MarcelPint%C3%B3)