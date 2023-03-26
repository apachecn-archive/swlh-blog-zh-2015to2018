# 将 Rails 应用程序设计成 RESTful 有什么好处？

> 原文：<https://medium.com/swlh/what-are-the-benefits-of-designing-a-rails-application-to-be-restful-c8d97a88d29c>

![](img/a67ad7cba7a2f4528224b85d863ccfa7.png)

What are the benefits of designing a Rails application to be RESTful?

uby on Rails 正在成为构建企业级 web 应用程序的主要参与者。您可以将 Rails 想象成一个开发工具的盒子，为开发人员提供必要的框架来构建他们的代码。由于开源软件库 RubyGems 的出现，初创公司也会发现它是构建网站的完美框架。Rails 的设计考虑到了最佳编程实践，因此它几乎可以指导您为后端编写良好的代码。它通过强调约定胜于配置来做到这一点，然后将其编码为 Rails API。

应用程序编程接口(API)是一种信使。一个 API 将接受你的请求，告诉系统你想让它做什么，然后把响应返回给你。很像餐馆里的服务员，他把你点的菜带到厨房，然后把回应或食物送回你的桌子。一个记录良好且一致的 API 是必不可少的。如果不能与其他服务轻松集成，无论您的应用程序有多棒，也永远达不到您的预期高度。当涉及到第三方集成时，最简单的方法是公开您的 REST(表述性状态转移技术)API 以供使用。换句话说，RESTful 接口允许后端 Rails 应用程序与前端 web 和移动客户端通信。

# 什么使得 API 是 RESTful 的？

简单地说，RESTful API 使用 HTTP 请求来获取、上传、发布和删除数据。浏览器使用的其余部分在某种程度上是互联网的语言。云已经越来越受欢迎，API 带来了新一波 web 服务，选择 REST 来构建允许您的消费者与云服务交互的 API 是一个合乎逻辑的决定。下面是管理 RESTful API 的主要原则。

*   所有这些都是资源。在这种架构风格中，功能和数据都被视为资源。
*   这些资源中的每一个都必须可以通过唯一的资源标识符(URI)来寻址
*   使用统一、简单、受约束的界面来操作您的资源。
*   通信或交互是通过服务的表示进行的。
*   保持无状态，因为它们更容易扩展。这意味着在两次执行之间，客户端状态不能保留在服务器上。
*   允许您的数据格式驱动应用程序中的状态转换。

# 优势:

1.  REST 了解网络的工作方式，而不是试图破解它。休息顺其自然。Rails 应用程序遵循的主要原则之一是约定胜于配置，以及 RESTful 应用程序设计。Rails 附带了大量的约定来加速 web 应用程序的开发过程，因此您的开发人员不需要花费时间和精力来配置安装文件。
2.  有了 REST，您的开发人员可以创建更智能的表单来区分方法而不仅仅是 URL，通过使用 HTTP 方法而不是 POST 来为您的服务器编程。记住，一个 URL 描述一个资源。一个帖子就是一种资源。这样，有了休息，你就能自然地处理资源。
3.  表述性状态转移或 REST 是一个基于客户机-服务器关系的框架。他们的应用程序有一个逻辑结构，这意味着他们可以很容易地被设计成一个 API。
4.  因为所有的调用都是无状态的，所以它有一个优点。当出现故障时，无状态组件可以很容易地重新部署，因为没有保存或保留的内容需要由下一个事务重新收集。
5.  REST 已经成为现代服务器应用程序与移动应用程序通信的标准格式，因为 REST APIs 易于调试和实现。它们与 HTTP 协议配合得很好，添加身份验证不会花费太多开发时间。
6.  从资源的角度思考将有助于简化您的代码，使其更具可读性和可理解性。正是请求类型和 URL 之间的简单性使得 REST 可读。创建东西的 POST，查看东西的 GET，更新东西的 PUT，删除东西的 DELETE。会有例外，但是通常你认为是例外的事情会变成他们的资源。
7.  它不仅为开发人员创造了一致性，也为用户提供了一致性。一般来说，对于 RESTful 应用程序，URL 更有意义，搜索引擎更喜欢那些晦涩难懂的。

> *总之，你不必以 RESTful 的方式设计 Rails 应用程序，但是 Rails 已经针对这种风格进行了大量优化，现在既然你已经理解了它带来的好处，我希望它能让你的决定更容易。*

*原载于* [***产品洞察博客***](https://www.cognitiveclouds.com/insights/) *来自 cognitive clouds:Top*[***Ruby on Rails 开发公司***](https://www.cognitiveclouds.com/custom-software-development-services/ruby-on-rails-development-company)

![](img/731acf26f5d44fdc58d99a6388fe935d.png)

## 这个故事发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，拥有 299，352+人关注。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)