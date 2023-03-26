# 设计师的前端原则

> 原文：<https://medium.com/swlh/front-end-principles-for-designers-acb195495809>

![](img/22aa319ac043d31fbbc86634eb780b7b.png)

设计者认为代码在网络社区变得越来越普遍；虽然不是必需的，但是这项技能对设计师的工作质量有很大的影响。这是不是说一个设计师*必须*知道如何编码来创造伟大的数字体验？这种思维定势是教条式的，无法提出正确的问题，即*设计师需要了解哪些原则来创造更好的设计*？

# 放开控制

[灵活是网络的本性](http://alistapart.com/article/dao)，随着这种灵活性而来的是一定程度的放开控制。这一过程的第一步是抛开像素完美的想法:我们的媒介是流动的，我们的决定必须牢记这一点。在 Photoshop 中设计构图，然后打印出所有像素完美的细节，以便评论或展示它们，就像它们是海报一样，这是荒谬的。

# 避免太多的变化

在设计过程中，元素会不断变化，尤其是颜色、字体大小和间距。当有太多的变化时，CSS 会变得臃肿，边缘样式会导致开发人员难以创作和维护文件。这个问题在更大的项目中会被放大，导致对页面性能的负面影响。解决方案很简单:审核您的设计，并确保通过将它们提炼为几个共同的值来将差异保持在最低限度。

# 了解来源顺序

源顺序是指元素在页面上显示的顺序，基于它们在 HTML 中出现的位置。默认情况下，元素将从上到下从左到右显示——它们的宽度由它们的[显示属性](https://css-tricks.com/almanac/properties/d/display/)决定。虽然使用 CSS 将元素放置在文档流之外很容易，但是改变元素在文档流中出现的顺序就有点困难，并且有一些限制。当您考虑设计如何适应不同的视口宽度时，自然的源顺序应该可以为您提供指导。如果你需要改变这一点，要有选择性，并有一个好的理由。

# 了解你的数字

看到一个项目在生产过程中出现了与你预想的不一样的元素，这是非常令人沮丧的。从字体大小和一般间距到网格值，您的设计中充满了您应该密切关注的数字。如果您的开发团队正在使用一个框架，那么您应该知道这个框架风格的默认值以及在更改它们时可用的选项。如果您的项目是特定于平台的，那么您应该是该平台的 [DPI 和其他规格](http://sebastien-gabriel.com/designers-guide-to-dpi/)的专家。通过了解你的数字，你可以在向你的开发团队传达这些细节时说得更有见地。

# 让内容决定断点

基于流行的设备尺寸或常见的屏幕分辨率来确定断点就像在沙洲上建房子一样:景观总是在变化，对今天有什么做出决定是固有的缺陷。更有意义的是[让内容决定断点](http://bradfrost.com/blog/post/7-habits-of-highly-effective-media-queries/#content)，而不是把这些值建立在[几个今天相关的设备或分辨率](http://screensiz.es/phone)上。

# 保持一致性

当创建一个对用户来说容易的环境时，一致性是关键。它将确保有一个通用的设计语言，这使得开发更容易，因为开发人员必须考虑的边缘情况更少。始终审核您的设计的一致性并尽可能减少一次性解决方案是非常重要的。

# 牢记性能

[性能是基本的设计特征](http://bradfrost.com/blog/post/performance-as-design/)，而不仅仅是技术上的最佳实践。从一开始就必须将性能作为设计工作流程的一部分，而不是事后的想法。设计师可以对[的性能设计](http://larahogan.me/design/)做很多事情，包括[设定性能预算](http://timkadlec.com/2013/01/setting-a-performance-budget/)，接受[有条件加载](https://24ways.org/2011/conditional-loading-for-responsive-designs/)，[消除不必要的下载](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads?hl=en)，使用 SVG 代替光栅图形，优化图像，鼓励你的开发团队采用[响应图像策略](https://responsiveimages.org/)。通过优先考虑绩效和培训团队中的其他人，您可以确保最终结果不会受到缓慢体验的影响。

# 尽早并经常沟通

与开发人员合作时，最重要的原则是尽早和经常沟通。积极主动地发现他们需要什么，让他们参与设计决策，并考虑他们指出的任何技术限制，这对成功的合作至关重要。请记住:开发团队有着共同的目标，他们都希望给用户最好的体验。

记住这些原则，不仅您的设计会改进，而且结果会产生连锁反应效应:更好的设计意味着与开发团队之间的交流更少，这可以将更多的时间放在增强用户体验的功能上。更好的用户体验会让用户更开心，这也会反映到客户端。最后，更快乐的客户可以带来更多伟大的项目。

参见[http://jonyablonski . com/2015/front-end-principles-for-designers/](http://jonyablonski.com/2015/front-end-principles-for-designers/)的原始帖子

![](img/71d955550911c61d0aef4c66a71f8e15.png)

*发表于* **创业、旅游癖和生活黑客**

[![](img/f20f8a326d92cd024c2946c0427a85fd.png)](http://supply.us9.list-manage.com/subscribe?u=310af6eb2240d299c7032ef6c&id=d28d8861ad)[![](img/1b4fd39dd738a88ac13336ad93f1049c.png)](https://blog.growth.supply/)[![](img/93f21657a8ed7c0f741216a91b53c713.png)](https://twitter.com/swlh_)

-