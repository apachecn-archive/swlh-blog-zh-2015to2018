# Ruby On Rails 应用的最佳前端框架。JS 还是 AngularJS？

> 原文：<https://medium.com/swlh/best-front-end-framework-for-ruby-on-rails-app-ember-js-or-angularjs-76294f7598d9>

![](img/e3fa3c30a3d4ef1e19e2f0919dff349a.png)

Best Front End Framework For Ruby On Rails App- Ember.JS Or AngularJS?

我们谈论这一代用户，以及他们对页面加载延迟五秒或过多通知和广告的日益不容忍。你看，但是变化不仅仅发生在你的用户身上，你的开发者也一样，对他们选择使用的工具有更多的期待。即时的满足让我们这一代人永远不耐烦。过去，应用程序的客户端是一层非常薄的 HTML、cookies、查询参数和请求头。你的服务器将会承担所有的重量级任务。这意味着网站的单个请求将通过显示整个网页得到响应。

今天，网站吹嘘前端功能强大，足以创建光滑的单页应用程序(spa ),提供类似桌面的用户体验。在决定使用哪种 JavaScript 工具之前，做适量的功课是很重要的。随着选择越来越多，这份工作正在变成一项挑战。您选择使用哪种工具将会影响项目的最后期限、代码可维护性和可伸缩性。AngularJS 和 Ember.js 是基于模型视图控制器(MVC)设计模式的开源 JavaScript 框架，以通过将结构引入代码并保持其有组织性来帮助创建可伸缩、高性能和灵活的应用程序而闻名。两者都使用明显不同的设计哲学来实现他们的目标。下面，我们将它们放在一起，并在与 Rails 驱动的后端交互时比较它们的优缺点。

# 比较

AngularJS 和 Ember.js 被设计成后端不可知的。保持后端独立是一个很好的规则，因为前端看到了更多的增长。这个决定将为你在一两年后想要修改你的前端时省去一些麻烦。尽量保持后端 RESTful 并遵循 JSON 中构建 API 的标准，然后您就可以自由选择最适合您的环境的框架。

# 安古拉吉斯

AngularJS 允许你用指令扩展 HTML 的功能来开发单页应用程序(SPAs)。简而言之，它是为构建 web 应用程序而设计的 HTML。

*   如果您没有太多时间，并且需要构建一个优雅的中小型应用程序，AngularJS 是一个很好的选择。这些应用程序有可能不会遇到“脏检查”瓶颈。这意味着您可以利用使用普通 JavaScript 对象作为模型带来的所有好处，比如简单性和编码速度。
*   AngularJS 也是一个不错的选择，因为它有大量的社区支持，未来可能会有很大的增长。
*   AngularJS 的速度更快，也更宽松。你可以看到 AngularJS 强调让你的应用程序快速启动并运行，所以这需要很多时间。它对模型使用 JavaScript 对象的代价是使用“脏检查”，这会影响应用程序的性能。这不是一个非常复杂的过程，会大大降低您的速度，并可能成为维护的噩梦。
*   然而，随着 Angular 2.0 的发布，现在可以利用服务器端渲染，避免“脏检查”的陷阱。

综上所述，AngularJS 如此受欢迎是有原因的，很简单。有了简单的需求，你将拥有一个干净的代码库，提供良好的性能，而且由于框架的内容少了很多，所以更容易学习。如果您的应用程序是简单的，那么这种框架简单性是很好的。现在，如果您的应用程序雄心勃勃，并且您关心长期维护它，您应该谨慎选择简单性。

# Ember.js

*   Ember 采用了原生框架的概念，如苹果的 Cocoa，并将它们与 Rails 等开源框架附带的轻量级敏感性结合起来，以创建动态的、渲染精美的、可伸缩性良好的 spa。该框架提供了一种 URL 驱动的方法来构建不同的应用程序和通用数据绑定。
*   Ember.js 是一个[很棒的前端框架](http://www.cognitiveclouds.com/insights/top-responsive-web-design-frameworks/)，易于维护，极其稳定。Ember.js 将指导您的开发人员按照最佳实践进行编码，以避免将自己编码成类似“脏检查”的瓶颈。
*   Ember 接受了很多 Rails 的思想，比如“约定胜于配置”Ember CLI(命令行结构)让开发感觉就像写 Rails:强大的约定，优秀的资产管道和伟大的部署支持。
*   Ember 是希望扩展到更大项目的应用程序的绝佳选择。
*   请考虑 Ember，即使您的应用程序将保持较小，因为它具有更快的启动时间和内在的稳定性。
*   缺点是，核心团队的功能开发非常缓慢，Ember 的最后几个版本大多是小版本，没有带来什么新的东西。
*   更少的定制空间。
*   Ember 的学习曲线比 AngularJS 陡峭得多。

现在，在你因为它的复杂性而放弃 Ember 之前，考虑一下为什么开发者添加了所有额外的东西。Ember 就像一个工具箱，里面有足够多的概念，可以用来构建可维护的大型应用程序。它在 API 中所做的权衡有助于开发人员合理地构建代码。

# 结论

AngularJS 和 Ember 做着同样的工作，开发具有迷人的用户界面/UX 的动态水疗中心。但是，他们的设计理念不同。

Angular 是这两个中目前比较流行的。您可以将它用作一站式服务，它是许多大型企业的首选框架。它还得到了谷歌的支持，谷歌比竞争对手领先一步。如果你正在处理一个应该带来增强用户体验的更简单的 SPA，集成 Ember 可能没有意义，因为一个 [Angular 应用](http://www.cognitiveclouds.com/custom-software-development-services/angularjs-development-company)会做得很好。如果你正在寻找包含所有工具的框架方法，Ember 是最好的解决方案。Ember 为你做了很多决定，所以你不必花时间去研究和粘合库。很明显，没有明确的赢家。一旦你明确了你的目标，你就能看到哪个框架比其他框架更适合你的项目需求。

*最初发表于 CognitiveClouds 的产品洞察博客:Top* [***Ruby on Rails 开发公司***](https://www.cognitiveclouds.com/custom-software-development-services/ruby-on-rails-development-company)

![](img/731acf26f5d44fdc58d99a6388fe935d.png)

## 这篇文章发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，拥有 299，352+人关注。

## 在此订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)