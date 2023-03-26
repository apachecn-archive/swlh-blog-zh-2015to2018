# 在 AWS 上部署 Rails Web 应用程序的最佳方式是什么？

> 原文：<https://medium.com/swlh/whats-the-best-way-to-deploy-rails-web-applications-on-aws-e7c982258e9>

![](img/95f695e90834f872177e1530c6c6e8b7.png)

What’s The Best Way To Deploy Rails Web Applications on AWS?

今天，你的选择太多了。您有足够多的、易于遵循的选项来让您的 Rails 应用程序立即在 Amazon Web Services 上运行。如果你发现以前很难部署你的 Rails 应用程序，因为你不能像在 PHP 中那样把代码放进去，然后在 Apache 上运行它，现在 Phusion Passenger 使之成为可能。即便如此，您也不希望错过自动化部署工具带来的好处，除非您有一个非常简单的应用程序，并且您正在寻找的只是代码更新，也许还有 Rails 迁移。自动化部署工具的好处包括提高生产率、可见性、可审计性和方法，更不容易出错。

# 最好的方法？

同样，你会在大多数博客中听到很多这样的话，这些博客在不了解你的背景的情况下推荐一种特定的方法，这是一个笼统的推荐。有保留地接受它，或者更确切地说，适当考虑您的优先级和用户的需求。

**Capistrano** 在 Rails 社区中非常受欢迎，理由很充分。它适用于所有必须将 web 应用程序部署到服务器的常见情况。Capistrano 是一个简单的工具。首先将代码从 Git 复制到服务器，然后执行一系列部署功能，比如重启 web 服务器、重命名文件、破坏缓存、运行数据库迁移等等。Capistrano 还允许多服务器、多阶段部署。

最近，Amazon Web Services 引入了 Elastic Beanstalk，用于在其生态系统中部署和扩展 Rails web 应用程序。Elastic Beanstalk 是平台即服务(PaaS)下的一种易于使用的服务。您所要做的就是上传代码，Beanstalk 会处理部署，从容量供应、负载平衡、自动伸缩到健康监控，您仍然可以控制应用程序所需的资源。您可以随时访问这些资源。此外，您只需为启动和运行应用程序所需的 AWS 资源付费。Beanstalk 还将为您提供所有必需的 AWS 资源。简而言之，EB 为您提供了一个功能强大的 CLI，类似于 Heroku 的，不同的部署策略，如蓝绿色部署或滚动更新和可定制的监控仪表板。

使用 ECS，您没有很多这样的选择。如果您选择使用 Docker 容器进行部署，那么 Elastic Beanstalk 将在 ECS 上运行。ECS 旨在让您定制您的软件堆栈。它在 EC2 机器集群上高效地调度 Docker 容器。Docker 容器也是 AWS 相对较新的特性。

比较 Capistrano 和 Beanstalk 仍然是不公平的，因为它们旨在服务于不同的目的并带来不同的好处。即便如此，如果 Beanstalk 为您做了同样的工作，为什么还要编写处理 Capistrano 的基础设施的代码呢？它还消除了扩展 web 应用程序带来的许多痛苦。在大多数情况下，从长远来看，弹性豆茎更容易维护。

*原载于* [***产品洞察博客***](https://www.cognitiveclouds.com/insights/) *来自 cognitive clouds:Top*[***Ruby on Rails 开发公司***](https://www.cognitiveclouds.com/custom-software-development-services/ruby-on-rails-development-company)

![](img/731acf26f5d44fdc58d99a6388fe935d.png)

## 这个故事发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，拥有 299，352+人关注。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)