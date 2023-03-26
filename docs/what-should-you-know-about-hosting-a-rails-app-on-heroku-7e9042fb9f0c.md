# 关于在 Heroku 上托管 Rails 应用程序，你应该知道些什么？

> 原文：<https://medium.com/swlh/what-should-you-know-about-hosting-a-rails-app-on-heroku-7e9042fb9f0c>

![](img/bdd64e8c93541d702321ea854f6c20eb.png)

What should you know about hosting a Rails app on Heroku?

你已经设计了一个极好的自包含的[网络应用](http://www.cognitiveclouds.com/custom-software-development-services/web-application-development-company)，它可以在网络浏览器上运行，不像你的用户会从应用商店下载的那种应用。在您的场景中，您的应用程序需要在 Web 上找到一个家。换句话说，它需要一个网址，以便你的用户可以通过它访问你的应用程序，同时还需要存储你的应用程序的代码以及相关的背景和数据支持，以确保流量峰值不会在离线时破坏它。

许多第一次选择共享主机，因为他们可以支付相对较少的费用。你会发现足够多的共享主机公司为 Rails 提供支持。一旦你的开发者稍微摆弄一下，他们很快就能上传你的 RoR 文件。牢记在心；很可能，它不支持任何部署工具。此外，当你需要安装任何宝石，他们将是一个适当的程序，你将不得不通过它每次你安装一个宝石。考虑到一个典型的 Rails 应用程序可以轻松拥有 10-15 个 gem，这个过程很快就会被证明是令人厌倦的。虽然也有例外，但大多数情况下，这是您在大多数非专业的 Rails 共享托管环境中的经历。除非您的应用程序是初级的，否则请选择支持 Rails 的应用程序，比如 Heroku。

Heroku 是一个你在互联网上搜索一个你的应用程序可以称之为家的地方时可能会遇到的名字。你会注意到，Heroku 尽最大努力简化你的部署过程，试图把它降低到几次点击。然而，部署的容易程度最终将取决于您的应用程序的复杂性，比如您使用哪种 gem，等等。你可能需要修改一些代码，学习 Git 和 S3。当然，除非你的开发者已经构建了内置“Heroku 兼容性”的应用。规模是另一大原因，Heroku 是开发者的最爱。Heroku 可以容纳大量的用户，即使你的普通应用突然变成了新的大东西。

# Heroku 入门

*   注册是一个简单快捷的过程，你只需要一个邮件 id 和密码。Heroku 附带了很多有用的附件，你很有可能会发现它们的用处。如果是这样，那么你必须输入你的卡的详细信息。无论哪种方式，最好的事情是，你可以从一个免费的托管计划开始。
*   此外，请确保在您的本地工作站上安装 Heroku Toolbelt。这是一个捆绑了三种工具的资源。Heroku 命令行客户端是一个管理和创建 Heroku 应用程序的工具，Foreman，让您可以在本地运行您的应用程序，Git 是一个版本控制系统，允许您将应用程序推送到 Heroku 堆栈。借助 Toolbelt，您可以从电脑上轻松创建、管理、测试和部署应用。
*   安装 Git。我假设您在本地安装了 Rails。除此之外，还必须安装 Git，Heroku 才能工作。
*   要安装 Heroku gem，请运行“gem install Heroku”一旦你安装了 gem，尝试运行“Heroku”，它必须列出可用的命令。看，gem 依赖项是 Heroku 为您的应用程序安装的，当您进行 git 推送时。这意味着它需要一个易于解析格式的. gems 文件。
*   现在我们差不多到了，推送你的应用，然后迁移数据库，在 web 浏览器中打开它。
*   这就是了。您的应用程序应该在 Heroku 的服务器上启动并运行。

您很快就会发现，Heroku 是部署 Rails 应用程序的一个很好的方式。根据规则进行设置，部署将变得轻而易举。一行代码就能搞定一切。尽管如此，如果你的开发人员在开发时没有考虑到“云”架构，他们还是要进行一些重写。积极的一面是，他们只需要做一次。Heroku 的另一个优点是，由于基于 Git 的托管能力，Heroku 允许开箱即用的协作。

> 最终，学习和理解 Heroku 的最好地方是在上面。事实上，Heroku 附带了一个很好的快速启动指南，如果你需要更多的细节，你可以很容易地跟随它。当然，如果你想问我们答案，我们就在这里。

*原载于 2017 年 7 月 17 日*[*【www.cognitiveclouds.com*](http://www.cognitiveclouds.com/insights/what-should-you-know-about-hosting-a-rails-app-on-heroku/)*。*

![](img/731acf26f5d44fdc58d99a6388fe935d.png)

## 这篇文章发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，拥有 299，352+人关注。

## 在此订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)