# 在 Rails App 中应该如何组织 Javascript？

> 原文：<https://medium.com/swlh/how-should-you-organize-javascript-in-rails-app-3d6cccdd3e28>

![](img/4474c1d47858408286503b079bdcad5b.png)

How Should You Organize Javascript In Rails App?

当谈到[构建一个 Rails 应用](https://www.cognitiveclouds.com/custom-software-development-services)时，这里没有逃脱的 JavaScript。不管我们是否喜欢，从一个小脚本到一个成熟的 JavaScript 框架网站，已经变得越来越依赖 JavaScript。过去，对于一个项目，您需要的只是一个样式表。今天，Rails 项目有一个资产管道，帮助我们创建不同的样式表或清单集。您浏览样式表，并将其全部绑定到 javascript 架构。这个资产管道使得在 Rails 应用程序中包含 JavaScript 变得更加容易。应用程序中包含的代码在所有页面上执行，无需任何额外的更改。然而，通过结合 CSS 类作用域和 jQuery 插件，您可以隔离某些 JavaScript 代码，使其只在特定页面上运行。

说到资产，Rails 是出了名的固执己见。你可以走手动路线，手动地包括任何地方的资产，但是最好把它们打包到一个文件中。这样，JavaScript 只需加载一次，就可以缓存在客户机上。此外，使用 Turbolinks 时，页面加载速度更快，因为不需要加载更多内容，只需要替换正文。

我们都见过缺乏组织性、模块化和灵活性的 Rails 项目。不得不接管这些项目是一件令人头痛的事。Turbolinks 就是为了解决这个问题。但是，如果您没有接触过 Turbolinks 以及它是如何帮助您组织 JavaScript 的，您可能已经将它从您的项目中删除了。在这里，我们给你介绍一下。

# 问题是

Rails 的核心原则围绕着采用约定来简化团队工作和减少工作量。然而，当涉及到组织 JavaScript 文件时，并没有广泛或公认的实践。如果不一致，在一个 [Rails 应用程序](https://www.cognitiveclouds.com/custom-software-development-services/ruby-on-rails-development-company)中留下一些 JavaScript 代码会很快变得笨拙。理想情况下，我们应该有一定的技术和指导方针来保持 Javascript 在我们的项目中有组织，此外，我们不希望必须禁用 Turbolinks 来使我们的应用程序按预期工作。

![](img/5ace383c5fc61f8f0ae2bc4b3caaf840.png)

*How should you organize JavaScript in Rails app*

作为 Rails 开发者，我们习惯于约定胜于配置。因此，让我们设计一种机制，允许我们在组织 Javascript 代码时做下面提到的所有事情。

*   仅在特定页面上执行的页面特定代码
*   创建一个 CoffeeScript 文件和一个 CoffeeScript 类的能力，当页面加载时会自动执行
*   我们需要做的就是创建一个 CoffeeScript 类，它遵循我们的约定，当我们有了一个新页面时，无需进一步配置就可以执行。

# 解决方案

JavaScript 的行为通常可以追溯到以下两类:

*   **“始终在线”行为**
*   **和** [行为触发**用户动作**](https://www.datadab.com)

在你处理这些之前，你需要处理一些事情来帮助你保持有条理。

*   类范围:这不仅允许您在需要时通过 jQuery 控制对 DOM 的访问，还为您提供了某些高级样式类，使您能够轻松地添加特定于页面的 CSS。
*   默认应用程序清单:这一步将确保文件夹中的 javascript 文件按字母顺序加载。
*   “永远在线”的 Javascript 功能:一旦你有了默认的方式，开始添加一些行为。
*   用户触发的 JavaScript:顾名思义，这种类型的 JavaScript 是作为用户点击或执行任何动作的结果而调用的 Javascript。您可能习惯于在 JavaScript 目录中添加一个随机文件，并在这一步加入一些 jQuery。虽然这样做在功能上可以很好地工作，但是在结构上保持这些文件的相似性会让您安心地继续工作。

希望您对如何在 Rails 应用程序中保持 Javascript 的组织性和可预测性有了一些了解。这种方法的一个好处是没有额外的插件。它使用了一个基本 Rails 应用程序中现有的所有工具，这意味着少了一件需要更新和维护的事情。

*原载于* [*产品洞察博客*](https://www.cognitiveclouds.com/insights/) *来自 cognitive clouds:Top*[*Ruby on Rails 开发公司*](https://www.cognitiveclouds.com/custom-software-development-services/ruby-on-rails-development-company)

![](img/731acf26f5d44fdc58d99a6388fe935d.png)

## 这个故事发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的企业家出版物，拥有 293，189+人。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)