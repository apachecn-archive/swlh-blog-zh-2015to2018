# 如何在你的网站上实现 Google AMP？

> 原文：<https://medium.com/swlh/how-to-implement-google-amp-on-your-website-3324cdb5419a>

![](img/43de8c5f95ff6834e80191d157f2d9b6.png)

How To Implement Google AMP On Your Website

A 加速移动页面是谷歌的一项举措，旨在改善用户的移动浏览器体验。谷歌希望让开发者更容易实现页面，实现货币化，拥抱开放的网络。AMP HTML 很像普通的 HTML，但是有一些规则和限制来促进良好的用户体验。

# AMP 是如何工作的？

AMP 是一个创建移动网页的框架，由三部分组成。

# 1.放大器 JS

AMP 为您提供了一个现成的 JavaScript 库，该库采用了最佳的性能实践，如管理资源处理、异步加载和提供要在 AMP HTML 中使用的定制标记。这些实践确保您的页面尽可能快地呈现。这样做的一个好处是可以确保来自外部的每个元素协调工作，防止页面中的任何内容被阻止呈现。预先计算页面上元素的布局，禁用慢速 CSS 选择器，以及沙盒 iframes，这些都有助于提高速度。

# 2.AMP HTML

AMP HTML 是标准的 HTML，带有许多自定义的 AMP 属性。换句话说，它是 HTML 的“减肥”版本，有一些限制，允许可靠的性能和一些扩展来帮助组合丰富的内容。AMP JS 库帮助您快速呈现 AMP HTML 页面。

# 3.放大器缓存

这是一个可选的基于代理的内容交付网络(CDN ),用于分发有效的 AMP 文档。CDN 获取您的 AMP HTML 页面，缓存它们，并自动优化您的页面性能。AMP 缓存系统附带了一个验证系统，用于确认页面是否能够独立于外部资源工作。

# 要记住的事情:

AMP HTML 不允许表单元素和第三方 JavaScript。这样做的缺点是，整合用户评论和其他交互式用户元素并不容易。这里的重点是速度和可读性。

您可能需要重写站点模板来为限制腾出空间。例如，自定义字体往往是负载密集型的，但是 AMP 中的所有 CSS 都必须是内嵌的，并且小于 50KB。这意味着你必须使用特定的 amp 字体扩展来加载它们。

为多媒体实现定制标签是非常困难的。例如，图像需要包含自定义元素，并且具有指定的宽度和高度。此外，如果您使用 gif 或本地嵌入的视频，您需要使用适当的 AMP 扩展组件。这些标签和扩展组件不难使用，但是在规划站点设计之前需要考虑它们。

# 如何实现 AMP？

是时候加速你的手机浏览器页面了。

首先，维护至少两个版本的页面是明智的。您的原始内容页面将是用户看到的移动浏览器友好版本。你也将有这个网页的 AMP 版本来加快速度。

对于 WordPress 用户，你需要在 GitHub 下载并安装 WordPress 插件。像其他插件一样，你也可以通过你的 WordPress 仪表盘安装 AMP 插件。一旦你完成了插件的安装和激活，将“/amp/”添加到你的页面中。附加这个"？相反，如果你没有友方永久链接。

> 不要忘记调整谷歌搜索控制台，以帮助谷歌更快地找到你文章的 AMP 版本。

此外，AMP Discovery 页面提到一些平台将需要 Schema.org 元数据，以使您的内容有资格出现在谷歌搜索新闻轮播的演示中。确保你的模式是正确的。

对于出版商来说，AMP 是一种相对简单的提高移动网站速度的方法。未来，加速移动页面将会影响很多社交媒体移动交互。在实施 AMP 的同时，不要忘记整合其他成熟的移动营销策略。这将证明把相关客户带到你的网站是至关重要的。

*原载于产品洞察博客来自*[***cognitive clouds***](https://www.cognitiveclouds.com)*:Top*[***SaaS 发展公司***](https://www.cognitiveclouds.com/custom-software-development-services/saas-application-development-company)

![](img/731acf26f5d44fdc58d99a6388fe935d.png)

## 这个故事发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，拥有 299，352+人关注。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)