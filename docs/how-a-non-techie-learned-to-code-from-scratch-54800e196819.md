# 一个非技术人员如何从零开始学习编码

> 原文：<https://medium.com/swlh/how-a-non-techie-learned-to-code-from-scratch-54800e196819>

我的背景是商业，除了求知欲和对技术感兴趣之外，我没有任何编程、数据库或网页设计经验。像大多数非技术人员一样，我有很多想法(质量不一)，但缺乏技术知识，无法在不外包技术的情况下执行和开发最小可行产品(MVP)。

作为一个非技术型的创始人，你可以很容易地说服自己，你的知识是核心产品，技术只是一个载体，因此可以外包。不幸的是，这种推理往往会产生一种不希望的结果——几个月的面试软件开发公司，大量的文书工作，高成本，不可分散的风险，不可预见的延迟和质量控制问题，以及一种工作关系，在这种关系中，你依赖于开发人员的可用性和善意，直到你找到其他人来接管。最后，你可能会一无所获，或者得到一个不是你预想的产品，而你的失败是因为你依赖他人，而不是你自己的意愿，这让事情变得更糟。

2014 年 9 月，我决定自学 Ruby on Rails，并创建一个 web 应用程序。我有一个简单的想法，规划出整个以色列融资生态系统，帮助初创企业寻找潜在的资金，并促进初创国家的发展。我关注三件事:

1.  以色列投资者和在以色列有代表的投资者；
2.  数据的完整性；和
3.  搜索粒度允许初创公司找到与其位置、行业、市场和/或投资阶段相匹配的投资者。例如，[找到特拉维夫投资早期网络安全初创公司的](http://972vc.com/companies?utf8=&query=venture+capital+tel+aviv+cyber+security+early+stage)风险投资公司。

我创建了一个电子表格并设计了模式:列标题(如名称、位置、投资阶段)和属性(如种子、早期阶段)。然后，我开始整理数据并填充电子表格，不断完善模式以保持其最小化和相关性。到 9 月底，我已经为 250 多家公司整理了数据。我有意从数据开始，而不是学习如何编码，主要是因为这样一来，如果我无法构建应用程序，我至少可以开源电子表格，并为创业社区做出有意义的贡献。

现在，是时候学习如何编码了。

# 第一步:HTML 和 CSS

我花了一个周末浏览 Codecademy 关于 HTML 和 CSS 的[教程](http://www.codecademy.com/en/tracks/web)。这些练习可以让你有一个基本的了解，并快速学习如何创建网页文档的布局和样式。目标是理解你能用 HTML 和 CSS 做什么，并对语法有个感觉。不要在这些教程上花太多时间。

# 步骤 2:命令行界面

我开始熟悉自己电脑上的[命令行界面](http://en.wikipedia.org/wiki/Command-line_interface)(Mac 上的终端)。我学会了几个基本的命令:如何创建目录；移动、删除和重命名文件；从一个目录导航到另一个目录。这里的目标是揭开命令行界面的神秘面纱，并在日常生活中使用它，这样一旦您开始编码，您就会对这个工具感到舒适。

# 第三步:学习一门编程语言

有几篇文章和深入的论坛帖子讨论了您应该学习哪种编程语言以及为什么要学习。很遗憾，我不能告诉你该学哪种语言，除了可能没关系。如果你选择学习 PHP 或 Ruby，那没问题，或者你想学习 Swift 或 Objective-C 来创建 iPhone 应用，那也没问题。不要像大多数语言一样，花时间为你的项目寻找最佳语言。相反，专注于你想要构建的东西，以便缩小你的选择范围，复习语法，阅读一些材料，并开始学习与你最有共鸣的语言。我唯一的建议是，你选择一门有相当大的在线社区和强大学习材料的语言。如果你有一个开发者朋友，寻求他们的建议并听取他们的意见。

我选择了 Ruby，花了几天时间学习 Codecademy。这些[教程](http://www.codecademy.com/en/tracks/ruby)很好也很容易，提供了一个很好的语言介绍。你甚至会注意到，在没有任何先验知识的情况下，你仍然能够理解一些语言。你的目标应该是应用和理解，而不是记忆语法。例如，您将学习创建循环的不同方法，但是首先要关注为什么您可能想要创建循环。你在 972VC 主页上看到的公司列表通过一个循环。再次，考虑应用。

# 步骤 4:设置您的编码环境

我发现这是最难的一步；花了一个周末的时间做了几次尝试才把它做好。我建议您备份硬盘，因为在安装项目所需的技术时，您可能会无意中删除系统文件或弄乱某些东西。我还建议你安装[家酿](http://brew.sh/)，这是一个软件包管理系统，如果你用的是 Mac，它会让安装更容易。这可能是你最需要帮助的地方，所以如果你有一个开发者朋友或者参加一个聚会，一定要伸出援手。

您还需要下载一个代码编辑器。选择您朋友使用的工具或您喜欢的编辑器。

# 第五步:学习 Rails

在我建立了我的编码环境之后，我花了几天时间学习 Jumpstart Lab 的 [Blogger](http://tutorials.jumpstartlab.com/projects/blogger.html) 教程，该教程教授四个基本功能——创建、读取、更新和销毁(CRUD)——你需要在 Rails 上构建一个简单的 Ruby 应用程序。

目标与其他教程相似——关注应用和理解，而不是记忆语法。考虑一下您是否在教程中创建了可以用于项目的功能。同样重要的是，你要接受在你理解这些教程中你在做什么之前需要时间这一事实。顺其自然，拥抱不确定性。不要气馁，不要放弃。

# 步骤 6:开始构建您的应用程序

至此，你已经学会了基础知识:HTML、CSS 和你选择的语言。您还将熟悉命令行界面，并设置您的编码环境。

10 月，在我完成上述教程后，我开始自己开发 972VC，到 11 月底，该应用程序已经[上线](https://972vc.com)。

# 经验教训

## *学习如何搜索*

在开发的最初几天，我甚至无法完成最基本的任务；事实上，我在谷歌上花的时间比写代码还多。同样的事情也会发生在你身上，这就是为什么你不应该花时间去记忆语法。学习如何有效地搜索和足智多谋，因为这将是你最重要的技能。

## *精益启动原则*

与有经验的开发人员相比，你有明显的优势。由于你没有编码知识或经验，你将需要把你的应用程序想法剥离到它的必需品。专注于产品的核心，尽可能简化。

## *没有付出就没有收获*

不要依赖别人为你开发你的应用。

你需要坚持不懈，坚韧不拔。如果你不是技术人员，学习编码需要一种不同于你习惯的思维方式，所以当然会很难。但是通过几个小时对一个问题的修补，你会逐渐开始理解一切(某种程度上)是如何工作的。这将是发展过程中最有价值的一课。随着您学习的进展，您将不再满足于您找到的第一个解决方案——您将开始寻找更好的方法来解决您的编码问题。

## *堆栈溢出*

Stack Overflow 是一个在线社区，也是你学习编码时最好的资源之一。问很多问题，但不要指望别人解决每个问题。为了推进你的学习，你应该重新审视你正在经历的问题，即使你已经在 Stack Overflow 上发布了这些问题。你甚至可能最终会回答自己的一些问题，并为社区做出贡献。

## *编码就像拼图游戏*

在基本层面上，您可以将编码视为一个交互式拼图游戏。将你的想法分解成更小的可管理的部分，然后放在一起构建应用程序。

## *教程*

不要花几周或几个月的时间去钻研书籍、教程和视频。相反，应该专注于理解编程语言和开发人员的思维方式，并在实践中学习。这就是为什么从一开始你就清楚地知道你想要建造什么是很重要的。当你需要学习如何做特定的事情时，使用教程、博客和其他资源。一定要检查并从开源项目中学习。

## *开源*

对于学习编码的非技术人员来说，开源可能是最美妙的发现，因为你寻找的功能可能已经开源了，所以你不需要重新发明轮子。如果你需要一个内容管理系统，你可以找到免费的健壮的开源软件。

因此，你经常会采用“脏手方法”来学习:你会找到解决问题的代码，尝试让它在你的应用程序中工作，然后拆开它，提出问题，并根据你的目的修改代码。

## *每日编码，频繁部署*

尝试每天使用你的应用程序，即使只有几分钟，尤其是在项目的开始阶段，因为熟悉你的编码环境是很重要的。不要担心最佳实践和惯例。开始时那只是噪音，但是随着你的进步，你会想要学习那些原则。

我还建议你尽快在 Heroku、AWS 或其他主机服务上部署你的应用程序，以避免将来的问题。当你最终准备好启动你的应用时，频繁部署将会节省你的时间。

## *技术*

做好学习多种技术的准备，因为仅仅学习一种编程语言来构建你的应用是不够的。你最终可能会使用 Git、Heroku、JavaScript 和 PostgreSQL 等技术。

## *庆祝小胜利*

学习如何编码是很难的，如果你自己做就更难了。因此，你需要把向前的每一步，不管有多小，都看作是合理的成功。

# **即使不想做开发者，也应该学习如何编码吗？**

通过遵循上面的步骤并根据您的需要进行调整，您可能会在几个月内构建一个简单的应用程序。但是，更重要的是，你会增强自己的能力，成为工作场所中更有价值的一员。你不再是一无所知的非技术型创始人或团队成员，而是懂得基本代码并能与开发人员和网页设计师交流的人。你也将有能力执行自己的想法，而不需要花费大量的外包费用。在 972VC 的情况下，构建和启动应用程序的总成本是 **$9** (一个 [RailsCasts](http://railscasts.com/) pro 订阅)加上域名。此外，如果您选择外包技术来构建 MVP，您将在协商和监督开发方面处于更有利的地位。

如果你决定拿着你的 MVP 去做大(也就是，自己动手的方法)，你会学到一家初创公司的所有不同角色:如何组建公司、会计、销售和营销、工程、UX/UI 设计、产品管理、业务开发和管理。

# 今天:972 伏

自从我启动了 [972VC](https://972vc.com) 以来，它已经成为以色列初创公司寻求与[私募股权](https://972vc.com/private-equity/#q=idt_private_equity)和[风险投资](https://972vc.com/venture-capital/#q=idt_venture_capital)以及[加速器](https://972vc.com/accelerators/#q=idt_accelerator)和[孵化器](https://972vc.com/incubators/#q=idt_incubator)项目相关资金的最全面资源之一。此外，它还提供关于[天使投资人团体](https://972vc.com/angel-investors/#q=idt_angel_investor_group)、[众筹平台](https://972vc.com/crowdfunding/#q=idt_crowdfunding_platform)、[共同工作空间](https://972vc.com/coworking-spaces/#q=idt_coworking_space)和[非营利组织](https://972vc.com/tech-for-good/#q=idt_nonprofit)的信息，这些组织拥抱“科技为善”，帮助专注于社交技术的初创公司和企业家。

如果你是创业国家融资生态系统中的一员，并且不在 972VC 上，[加入这个社区](https://972vc.com/)！

*顺便说一句，如果你是一家正在寻找以色列天使投资人的初创公司，可以看看伊登·肖查特的众包* [*电子表格*](http://bit.ly/ViewIsraeliAngels) *，如果你对以色列的初创公司生态系统感兴趣，可以看看本·朗的* [*映射在以色列的*](https://mappedinisrael.com/) *。*

**我目前正在做的项目**:

*   [加密货币职位](https://cryptocurrencyjobs.co/):区块链和加密货币职位的领先职位板
*   NODESK :一个为数字游民和远程工作者管理的资源集合，包括一个工作板

# 资源

我整理了一个资源列表，以进一步帮助你学习如何编写和构建你的应用程序。这些是我在构建应用程序时使用或遇到的资源，最终使 972VC 成为可能。我希望它们对你同样有益。

*   **命令行界面**:[Mac 终端说明书](https://github.com/0nn0/terminal-mac-cheatsheet/wiki/Terminal-Cheatsheet-for-Mac-(-basics-))
*   **安装指南** : [GoRails](https://gorails.com/setup/osx/10.9-mavericks) ， [thoughtbot](https://github.com/thoughtbot/laptop/blob/master/mac)
*   **OS X 软件包经理** : [自制软件](http://brew.sh/)
*   **代码编辑器** : [原子](https://atom.io/)，[崇高文本](http://www.sublimetext.com/)， [Vim](http://www.vim.org/)
*   **教程** : [CSS-Tricks](http://css-tricks.com/) ，[代码学院](https://www.codeschool.com/)，[代码学院](http://www.codecademy.com/)， [Jumpstart 实验室](http://tutorials.jumpstartlab.com/)， [RailsCasts](http://railscasts.com/) ， [RubyMonk](https://rubymonk.com/) ，[茶叶学院](http://www.gotealeaf.com/)，[Ruby on Rails 教程](https://www.railstutorial.org/)，[试 Ruby](http://tryruby.org/) ， [Tuts+](http://tutsplus.com/) ，
*   **Ruby on Rails 开源项目** : [开源 Rails](http://www.opensourcerails.com/)
*   **认证** : [设计](https://github.com/plataformatec/devise)
*   **自动完成** : [jQuery UI](http://jqueryui.com/autocomplete/) ，[选择 2](http://select2.github.io/select2/) ，[选择](http://brianreavis.github.io/selectize.js/)， [typeahead.js](https://twitter.github.io/typeahead.js/)
*   **CMS** : [主动管理](http://activeadmin.info/)， [RailsAdmin](https://github.com/sferik/rails_admin)
*   **前端框架** : [引导](http://getbootstrap.com/)，[基础](http://foundation.zurb.com/)
*   **全文搜索** : [阿尔戈利亚](https://www.algolia.com/)，[弹力搜索](http://www.elasticsearch.org/)， [PgSearch](https://github.com/Casecommons/pg_search) ， [Solr](http://lucene.apache.org/solr/) ，[思维狮身人面像](http://pat.github.io/thinking-sphinx/)
*   **图标** : [字体牛逼](http://fortawesome.github.io/Font-Awesome/)
*   **分页** : [上成](https://github.com/amatsuda/kaminari)，[将 _ 分页](https://github.com/mislav/will_paginate)
*   **漂亮的网址** : [FriendlyId](https://github.com/norman/friendly_id)
*   **数据库** : [MongoDB](http://www.mongodb.org/) ， [MySQL](http://www.mysql.com/) ， [PostgreSQL](http://www.postgresql.org/)
*   **论坛** : [站点点](http://community.sitepoint.com/)，[堆栈溢出](http://stackoverflow.com/)
*   **浏览器中的代码编辑器** : [CodePen](http://codepen.io/) ， [JSFiddle](http://jsfiddle.net/)
*   **JavaScript 转 CoffeeScript 编译器** : [Js2coffee](http://js2coffee.org/)
*   **基于网络的办公套件** : [谷歌文档](http://www.google.com/docs/about/)
*   **Ruby 风格指南** : [社区驱动的 Ruby 编码风格指南](https://github.com/bbatsov/ruby-style-guide)
*   **版本控制** : [Git](http://git-scm.com/)
*   **存储库托管服务** : [GitHub](http://github.com/)
*   **虚拟主机服务** : [AWS](http://aws.amazon.com/) ， [Engine Yard](https://www.engineyard.com/) ， [Heroku](https://www.heroku.com/) ( [寝住](http://nezumiapp.com/)用于移动，[管理](https://www.adminium.io/)用于数据库后端， [OpenShift](https://www.openshift.com/) ， [Rackspace](http://www.rackspace.com/)
*   **DNS 和域名管理** : [DNSimple](https://dnsimple.com/)
*   **浏览器测试** : [浏览器堆栈](http://www.browserstack.com/)
*   **网站安全扫描器** : [检测](https://detectify.com/)
*   **负载测试** : [Loader.io](https://loader.io/)
*   **分析** : [谷歌分析](http://www.google.com/analytics/)，[细分](https://segment.com/)
*   **通迅** : [MailChimp](http://mailchimp.com/) ， [TinyLetter](http://tinyletter.com/)
*   **隐私策略生成器** : [iubenda](http://www.iubenda.com/)
*   **UI/UX 工具** : [草图](http://bohemiancoding.com/sketch/)
*   **域生成器** : [Domainr](https://domainr.com/) ， [NameMesh](http://www.namemesh.com/) ， [NameRobot](http://www.namerobot.com/) ， [Naminum](http://www.naminum.com/) ， [Panabee](http://www.panabee.com/)

这是两部分系列的第一部分。你可以在这里阅读 [*第二部分*](/@3reps/a-product-hunt-maker-success-story-d3fe6608e5c6) *。*

如果你喜欢这个故事，请点击👏好让其他人也能看到。