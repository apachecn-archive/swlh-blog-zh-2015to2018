# 所有你需要知道的反应原生

> 原文：<https://medium.com/swlh/all-you-need-to-know-about-react-native-72f22c834c89>

![](img/4d9ce4ae3e8f85d23180e660cbf76bdb.png)

All You Need To Know About React Native

我们想要这一切。更短的开发周期、更快的部署和出色的应用性能。我们是专注于创建具有卓越用户体验的应用程序，还是开发速度更快、能在更多平台和设备上运行的应用程序？

混合移动应用开始尝试解决这个问题。它们看起来和感觉上都像一个本地的移动应用程序，但是在它们的基本框架之外，它们是由你公司的网站驱动的。这些应用程序采用大多数开发人员熟悉的技术构建，如 HTML5、JavaScript 和 CSS，封装在一个包中，使您的应用程序能够在设备上本地运行。混合应用程序框架在弥合这一差距方面取得了长足的进步。

脸书的 React 原生用户界面(UI)设计框架是这项技术的前沿。React Native 是您在 web 上习惯使用的一切与本机应用程序的优势之间的一种伙伴关系。它为您提供了本机应用程序的速度、保真度和感觉，同时保留了您习惯于在 web 上使用的东西，如快速开发周期和声明式自包含 UI 组件。

# 什么是反应原生

React Native 是由脸书开发的一个框架。有了 React Native，你不用构建一个“移动网络应用”或者甚至是一个“混合应用”。该框架允许您创建与使用 Swift 或 Java 构建的应用程序完全相同的真实移动应用程序。React Native 使用了 iOS 和 Android 使用的相同的基本 UI 构建块。这些构件只是用 JavaScript 和 React 组合在一起。

# React Native 和 React 有什么不同？

React Native 不是 React 的不同版本。React Native 是 React 的自定义渲染器，就像 Web 上的 React DOM 一样。React Native 使用本地组件，而不是像 React 这样的 web 组件作为构建块。从 React Native 开始，您需要了解基本的 React 概念，如 JSX、组件、状态和属性。如果你知道 React，你仍然需要学习 React 本地特有的东西，比如本地组件。除了转换 React 代码以在 iOS 和 Android 上工作之外，React Native 还提供了这些平台提供的功能。

# 如何反应本土作品？

如果你熟悉 React for web，你会觉得 React Native 很好用。如果你习惯于用 Java 或 Swift 编写应用程序，你会对 React Native 的许多组件感到如鱼得水。

React 是一个用于构建用户界面的 JavaScript 库，专注于应用程序的视图部分。这意味着当您编写 React 本机应用程序时，您的视图代码将包含 React 组件，这些组件是描述应用程序的一部分如何基于一些输入数据的小段代码。

# 与 React Native 合作过的公司

脸书、GitHub、Airbnb、Box、谷歌、微软、Pinterest、皮克斯动画工作室、Twitter、优步、Instagram、LinkedIn 和 WhatsApp 都使用 React 代码。

# 利益

*   **跨平台** Android 和 iOS 有不同的代码库，所以企业经常不得不雇佣工程师在两个平台上工作。有了 React Native，你不必为 iOS 和 Android 分别构建相同的应用。React Native 帮助开发人员跨 web、移动和其他操作系统重用公共逻辑层。
*   **真正的原生**为特定操作系统编写应用被定义为原生应用创建。许多软件框架让你相信它有能力为 Android 和 iOS 创建优秀的应用程序，但大多数情况下，产品最终会介于两者之间，没有真正的本土感。React Native 使开发人员能够开发真正的原生应用程序，包括原生平台，同时允许您的应用程序在平台之间共享其大部分代码库，而无需增加构建两个独立应用程序所需的预算。
*   可读性即使对不熟悉 React 的人来说，它也很容易读懂。许多框架要求你学习大量的概念，这些概念只在框架内有用。React 努力做相反的事情。
*   在声明式编程中，开发人员告诉应用程序他们想要实现什么。而对于命令式编程，开发人员必须具体说明如何去做。在这种风格的编程中，您在事情如何发生方面的灵活性较小，但是能够描述状态大大降低了出现错误的可能性。
*   **基于组件的结构允许使用 web 风格的开发方法** React Native 基于组件的结构允许开发人员使用比大多数混合框架更灵活的 web 风格的开发方法来构建应用程序，并且根本不需要任何 web。
*   **社区支持**您的 React 本机代码大部分是 JavaScript，因此您可以从该语言及其生态系统的所有进步中获益。如果你懂 JavaScript，React Native 会很容易上手，让大部分前端 web 开发者都能成为移动开发者。您只需要知道 JavaScript、平台 API、一些原生 UI 元素和任何其他特定于平台的设计模式，一切都已准备就绪。
*   **重新加载**不用重新编译，你可以瞬间重新加载你的 app。你有两个选择:实时重新加载将在你每次编辑和保存它的一个文件时重新加载应用程序。热重新加载仅重新加载您刚刚编辑的文件，而不是整个文件。
*   **需要时使用本机代码**如果需要优化应用程序的某些方面，使用本机代码很简单。在 React Native 中构建应用程序的一部分也很容易，直接使用本机代码构建应用程序的一部分，这就是脸书应用程序的工作方式。
*   **无需大修旧应用**你只需将 React 原生 UI 组件添加到现有应用的代码中，无需重写。或者使用插件，如果您当前的混合应用程序是使用 Cordova 和 Ionic 构建的，请重用基于 Cordova 的代码。这对于希望扩展现有应用程序而不必对其进行彻底检查的企业来说是一个显著的优势。
*   **效率**原生应用开发通常意味着效率低下、部署时间更长、开发人员生产力更低。React Native 旨在将 web 应用程序开发的高速、响应性和敏捷性以及有效的处理和最佳用户体验带入混合空间，为您的用户提供原生应用程序体验。

> React native 不仅仅是对 web 开发人员的本地应用程序的介绍。这是一个强大的工具，但不是所有解决方案的理想选择。请记住，复杂的应用程序需要更多的本地解决方案，这反过来又需要更多的本地开发人员。否则，它可能会减慢开发过程。然而，对于 UI 不太复杂的应用程序，React Native 是最好的方法。你将获得一个性能良好，真正的原生应用，花费更少的资源。

*原载于产品洞察博客来自*[***cognitive clouds***](https://www.cognitiveclouds.com)*:Top*[***SaaS 发展公司***](https://www.cognitiveclouds.com/custom-software-development-services/saas-application-development-company)

![](img/731acf26f5d44fdc58d99a6388fe935d.png)

## 这篇文章发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，拥有 299，352+人关注。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)