# 如何提高你的网站的可访问性+搜索引擎优化

> 原文：<https://medium.com/swlh/how-to-boost-both-your-website-accessibility-seo-c7ee63625cdd>

## 找到可访问性和 SEO 愉快共存的地方

![](img/b1a8a5ceee432dd602db61f1e1cfdaf0.png)

It is not a myth — there are some areas where SEO and accessibility can intersect. Credit: [Unsplash](https://unsplash.com)

搜索引擎优化(SEO)和[网站可访问性](/statuscode/getting-started-with-website-accessibility-5586c7febc92)不是一回事。有不同的规则要遵循，有不同的目标受众，有不同的方法来测试每种方法的有效性。

为搜索引擎机器人优化你的网站并不意味着它会自动地被真实的人访问。一些 SEO 实践甚至可能*损害*你的网站的可访问性。

然而，这并不全是坏消息，两个世界在一些领域有重叠。如果你的项目预算和/或时间有限，瞄准这六个领域*可能会同时提高搜索引擎优化和网站的可访问性。

**注:本文的重点是重叠的领域。下面每个领域的每个特定任务可能更多地针对 SEO，一些任务可能更多地针对可访问性。*

![](img/555b7b443d94566bab85cf3c5c1bcdda.png)

Warning: bearded hipster pizza guy will hunt you down you and force you to drink a handcrafted brew he made in his bathtub, if you underestimate the importance of UI for SEO and website accessibility. Credit: [Unsplash](https://unsplash.com)

# 结构很重要

不要低估好的用户界面(UI)的力量。具有干净、清晰、一致的用户界面的网站特别适合搜索引擎机器人和使用辅助技术设备的人或者只使用键盘的人。想一想——如果用户或机器人找不到页面，他们怎么可能阅读它或与之交互呢？你需要尽可能地让寻找网页和与网站互动变得容易。

## 最佳实践

*   以清晰一致的方式构建你的导航和页面布局，并有多种方式找到内容。搜索、网站地图、目录)。搜索引擎机器人喜欢组织良好的网站架构，这导致他们以更有意义的方式索引你的内容。
*   如果你的网站难以导航或使用，它可能会影响你的用户分析统计数据，包括在网站上的时间，浏览的页面和跳出率。这可能会反过来伤害你的搜索引擎优化排名。最起码会激怒你的用户。
*   避免使用 [CSS 或其他风格标记](https://uxplanet.org/designing-for-all-5-ways-to-make-your-next-website-design-more-accessible-23a3528bc8dc)来传达意思。你不应该“伪造”一个应该使用 HTML 标记的元素。
*   适当的时候，使用[可访问的 HTML 5 页面元素](http://stevefaulkner.github.io/HTML5accessibility/)，比如`<article>`、`<section>`、`<header>`、`<footer>`。这些元素比普通的`<div>`或`<p>`元素更能描述搜索引擎机器人和辅助技术设备。

![](img/c74a486223d0a718255c0df25a9b0604.png)

Tags, tags, everywhere tags. Handmade package tags of various sizes and colors. Credit: [Unsplash](https://unsplash.com)

# 标签的正确使用

您的网站内容本质上可以归结为 HTML 标记，包括用于页面标题的标签(不要与`<header>`标签混淆)。通过`<h1>`和`<h2>`标签导航可以给用户或搜索引擎机器人一个页面的概览，以及它的内容是如何构成的，而`<h3>`到`<h6>`标签提供了对每个部分的细节的快速理解。获得正确的标签对于网站的可访问性和 SEO 都很重要。

## 最佳实践

*   保持标题标签的一致性，不要仅仅为了给标题提供视觉外观而设计文本，要使用真正的标题标签。否则，搜索引擎机器人和用户将不会知道哪个内容是最重要的。
*   标题标签应该按顺序排列。这意味着一个`<h1>`后面跟着一个`<h2>`，一个`<h2>`后面跟着一个`<h2>`或`<h3>`等等。
*   在网站页面上按顺序排列时，避免跳过标题标签。例如，不要从`<h2>`跳到`<h5>`。注意:如果您正在开始一个新的页面部分，当按顺序(`<h5>`到`<h1>`)向上时，可以*跳过标题标签。*
*   最好的做法是每页只有一个`<h1>`。把`<h1>`标签想象成本质上的[第二页标题标签](https://cbutterworth.com/do-h1-tags-still-help-seo/)，它向搜索引擎机器人发送相关性信号。

![](img/fdb86e2d77de1f02d14627156df660cc.png)

Practice makes perfect. Athlete rests white Adidas shoes on chainlink fence. Credit: [Unsplash](https://unsplash.com)

# 完善你的链接

对于搜索引擎机器人和使用辅助技术设备(如屏幕阅读器)的人来说，链接可以创建或破坏一个网站。在查看了页面标题之后，链接是用户和爬虫最常注意的下一个主要元素，所以你的链接必须尽可能完美。

## 最佳实践

*   确保没有断开的链接。这可以被看作是一个被忽视或被放弃的搜索引擎优化网站的标志。这也是一种糟糕的网站可访问性实践，会让你的用户感到沮丧/困惑。
*   使用内部标签类型的链接，但不要过度。根据[Yoast.com](https://yoast.com/articles/wordpress-seo/#tag-optimizatio)的说法:“它通过将一个内容与另一个内容关联起来，更具体地说是一组帖子之间的关联，来改善你的 SEO。”它还允许用户通过一次点击轻松访问相似的内容。
*   提供描述性链接文本。避免使用像`click here`和`read more`这样的短语。如果你喜欢使用这些短语，你可以保留它们，如果你使用视觉隐藏或 ARIA 方法添加[附加链接信息](http://a11y-style-guide.com/style-guide/section-general.html#kssref-general-read-more)。
*   跳过添加描述性的[标题属性](https://silktide.com/i-thought-title-text-improved-accessibility-i-was-wrong/)到你的链接(当你悬停在一个链接上时出现的文本)。添加链接标题并不一定是错误的，但是可以说[对于 SEO 或者网站的可访问性来说](https://www.w3.org/TR/WCAG20-TECHS/H33.html)并不是很有帮助。

![](img/95725827b28b13d3b4ec4967849485c9.png)

Say cheese! Woman in pink floral shirt holding retro Nikon camera. Credit: [Unsplash](https://unsplash.com)

# 图像优化

尽管搜索引擎机器人和使用屏幕阅读器的人不能“看到”传统意义上的东西，但他们都依赖图像名称和替代文本来告诉他们图像描述的是什么。将这些元素放在适当的位置对于补充周围的内容和整体用户体验都是必不可少的。

## 最佳实践

*   给图像命名时尽可能保持一致和准确。例如，不要把你的文件命名为`brown-puppy.jpg`一张橙色斑猫的照片。
*   避免使用非字母字符(例如 7，%，&，$)并在单词之间使用破折号，而不是在图像名称或替代文本中使用下划线。比如写`orange-tabby-cat.jpg`而不写`0r@nge_t@66y_c@t!.jpg`
*   将您的替代文本控制在 125 个字符以内。如果需要更多字符，请使用标题文本或在页面的主文本区域进一步描述图像。
*   像人而不是机器人一样写替代文本。关键字填充对任何人都没有好处——使用屏幕阅读器的人会很生气，搜索引擎机器人会惩罚你。就是不做。

![](img/fe0e60f3d2632961a46a8ee02e892a2a.png)

Make your media work for bots and humans. Close-up of spinning record player. Credit: [Unsplash](https://unsplash.com)

# 补充您的媒体

视障人士(例如癫痫症、失明)、听觉障碍(例如聋人、重听人)、情境性/暂时性残疾、带宽连接差的人以及许多其他人可以从以可访问的方式显示的媒体中受益匪浅。类似地，搜索引擎机器人是“残疾”的，因为它们没有眼睛、耳朵或手，所以这是 SEO 和网站可访问性有一些不错的重叠的领域。

## 最佳实践

*   少即是多。限制使用复杂的媒体组件(例如幻灯片，视频)在你的设计中。不用担心…有[替代布局选项](https://uxplanet.org/6-design-alternatives-to-avoid-evil-slideshows-9d442cf680d3)。
*   为基本媒体添加清晰、完整、简洁的文本描述和标记。对于保留非必要的介质，请三思。
*   所有的视频和幻灯片应该有一个播放/暂停按钮，如果它是自动前进的，但请不要自动开始。理想情况下，所有媒体控件都应该可以访问。
*   提供访问媒体的替代方式。例如，具有视频的抄本和/或字幕；为纯音频文件创建副本；向您的媒体添加一个[盲文格式的文件](http://www.brailleauthority.org/)。有许多不同类型的[替代格式](http://www.queensu.ca/accessibility/how-info/what-are-alternate-formats)可供您使用。

![](img/6ed769c41d8ca1e9f945852464f1e907.png)

Content is King. Container of printing press block letters of various sizes and font families. Credit: [Unsplash](https://unsplash.com)

# 整理你的内容

最后但同样重要的是，在解决了网站的整体结构、标题标签、链接、图像和其他媒体之后，下一步是关注实际内容。因为每个网站都是独一无二的雪花，所以从一个网站到下一个网站，网站内容有很大的可变性。对某些网站上的某些用户有效的东西，可能对你和你的网站无效。关键是尽你所能写出最好的内容，并牢记谷歌的内容创作箴言:

> 想想是什么让你的网站独一无二、有价值或吸引人。让你的网站在你的领域中脱颖而出。”

## 最佳实践

*   将每段的长度限制在大约三句话以内，并设定与你的读者一致的阅读等级。理想情况下，为了网站的可访问性和搜索引擎优化的目的，你应该把目标定在大约[九年级](https://www.w3.org/TR/WCAG20/)的水平。
*   不要使用粗体和斜体标签来突出单词，而是使用强调。从视觉上看，它们看起来彼此相似，但是屏幕阅读器(在正确的模式下)会强调由`<strong>`和`<em>`标签包围的单词，而它们会完全忽略或者仅仅稍微改变`<b>`和`<i>`标签。
*   不要复制你的内容。搜索引擎机器人会注意到并惩罚你。你的用户只会感到困惑。
*   项目符号和编号列表有助于为读者分解内容，使其更加用户友好。额外收获:一些研究表明，相比纯文本，搜索引擎机器人更喜欢带有[项目符号和数字](http://forums.seochat.com/search-engine-optimization-28/bullets-search-engine-optimization-right-way-do-288202.html)的内容。

*❤如果你喜欢这篇文章，请点击“鼓掌”图标(次数不限)，在社交媒体上分享这个故事，并在* [*媒体*](/@cariefisher/) *或* [*推特*](https://twitter.com/cariefisher) *上关注我，以示支持！谢谢你和快乐的 reading❤*

![](img/731acf26f5d44fdc58d99a6388fe935d.png)

## 这个故事发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的企业家出版物，拥有 273，971+人。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)