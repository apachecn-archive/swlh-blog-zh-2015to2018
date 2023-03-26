# 垃圾收集与自动引用计数

> 原文：<https://medium.com/swlh/garbage-collection-vs-automatic-reference-counting-49154436966e>

![](img/002aae8b2640ccb6a5f544da41f7a317.png)

Photo by [Gary Chan](https://unsplash.com/photos/YzSZN3qvHeo?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/garbage?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

在之前的[博文](/@m.tabrizi/memory-management-in-swift-3c38065ecbbd)中，我们看到了 iOS 是如何使用自动引用计数(ARC)作为其对象生存期管理系统的。在这篇文章中，我试图指出 ARC 与垃圾收集或者更具体地说[跟踪垃圾收集](https://en.wikipedia.org/wiki/Tracing_garbage_collection)的一些显著区别(更准确地说，引用计数和跟踪是垃圾收集的两种不同实现。换句话说，ARC 是垃圾收集的一种形式。由于*跟踪垃圾收集*是最常见的垃圾收集类型，通常术语“垃圾收集”是指跟踪垃圾收集)。

# 自动引用计数

[ARC](/@m.tabrizi/memory-management-in-swift-3c38065ecbbd) 是一个[编译器特性](https://developer.apple.com/library/content/releasenotes/ObjectiveC/RN-TransitioningToARC/Introduction/Introduction.html)使用*对象所有权。*如果对象的[引用计数](https://en.wikipedia.org/wiki/Reference_counting)为零，即不再有所有者，ARC 将从内存中释放对象，而不是在运行时在后台查找未使用的对象。ARC 在编译时自动注入 Objective-C 运行时等价的 retain、release(编译器在所有需要的地方插入 retain 和 release)。我有一整篇[帖子](http://developer-toolbox.blogspot.com/2017/08/swift-memory-management.html)解释 ARC 是如何工作的。

## **自动引用计数的优势**

*   对象的销毁是实时的和可预测的。它有*确定性的*对象回收(当最后一个对该对象的强引用消失时)，而 GC 在“某个时候”释放一个对象。一旦对象不再被引用，就会被释放，而无需长时间暂停收集周期。这使得对象可以更快地被释放。这对于移动设备等内存有限的系统非常重要。这定义了一类微妙的 bug，它们可能存在于 GC 应用程序中，由于收集器不会在“错误窗口”中触发，所以不会暴露出来。
*   没有后台处理，这使得它对于低功耗系统来说效率更高。
*   如果活动对象集填满了大部分可用内存，跟踪垃圾收集周期就会被频繁触发，这就需要额外的空间来提高效率。随着可用空间总量的减少，引用计数性能不会下降。
*   引用计数的渐近复杂性不依赖于堆的总大小。

## **自动参考计数的缺点**

*   无法收集保留周期。保留周期保持引用计数大于零，即使它们不可达
*   需要考虑多线程引用计数。

# 碎片帐集

[垃圾收集](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science)) (GC)是一种自动内存管理的形式，试图回收垃圾，或者程序不再使用的对象所占用的内存。在存在任何垃圾收集之前，您必须手动添加对 retain 和 release 的调用(在其他语言中为“free”或“destroy”)。

有几种[策略](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science)#Strategies)来实现垃圾收集，最常见的两种是跟踪和引用计数。跟踪垃圾回收由。NET 和 Java 平台。

垃圾收集在运行时进行。它检测未使用的对象，一旦你的代码不再使用它们，它就释放它们。这发生在*不确定的*时间间隔(或者在一定时间过去后，或者当运行时发现可用内存变低时)，因此对象不一定在不再被使用时被释放。

## 垃圾收集的优势

*   GC 可以清理整个对象图，包括保留循环。这是垃圾收集相对于 ARC 的主要优势，您不需要担心保留周期。
*   GC 发生在后台，所以作为常规应用程序流的一部分，完成的内存管理工作较少。

## 垃圾收集的缺点

*   因为 GC 发生在后台，所以对象释放的确切时间框架是不确定的。
*   当 GC 发生时，应用程序中的其他线程可能会被暂时挂起。

# 继续教育

[ARC vs. GC](https://docs.elementscompiler.com/Concepts/ARCvsGC/)
[苹果 Objective-C 邮件列表上的一个线程](https://lists.apple.com/archives/objc-language/2011/Jun/msg00013.html)
[垃圾收集简史](https://www.ibm.com/developerworks/java/library/j-jtp10283/)

![](img/731acf26f5d44fdc58d99a6388fe935d.png)

## 这个故事发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，拥有 295，232+人关注。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)