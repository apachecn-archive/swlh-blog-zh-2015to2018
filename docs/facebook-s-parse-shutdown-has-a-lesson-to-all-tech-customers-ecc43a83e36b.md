# 脸书 Parse 的关闭给所有科技客户上了一课

> 原文：<https://medium.com/swlh/facebook-s-parse-shutdown-has-a-lesson-to-all-tech-customers-ecc43a83e36b>

![](img/e2e55bc20d44247abc3290f8d5a0031d.png)

1 月 28 日，脸书宣布他们将关闭 [Parse](https://parse.com) ，这是一项软件开发者用来存储和管理应用程序中数据的服务。

考虑到云服务关闭时糟糕的客户服务标准，脸书非常优雅地处理了这个过程。该公司将 Parse 保持了整整一年，并且已经将 Parse 服务器的[源代码](https://github.com/ParsePlatform/parse-server)作为开源发布。这使得软件开发商可以建立自己的类似解析的服务，并传输他们在脸书服务器上的数据。

然而，有多少 Parse 用户会这么做还是个未知数。有成千上万的应用程序使用 Parse。这些大部分是 iOS 和 Android 的移动应用程序，并且很多都没有积极维护。

手机应用的“保质期”相当短。团队迅速转向新项目。除非应用程序产生有意义的收入，否则为一个新的后端改造一个三年的应用程序并不在任何开发者的任务清单上。

当 Parse 后端从互联网上消失后，不更新的应用会发生什么？对于一些只依赖 Parse 进行简单数据或云备份的应用程序来说，这种影响可能微乎其微——例如，一款游戏可能会丢失其高分列表，但仍会继续工作。大多数应用程序可能对服务器丢失没有那么强的适应能力。在最坏的情况下，应用程序将完全停止工作，因为它们无法验证登录。在中间情况下，本地数据仍然可以访问，但任何在线功能都将丢失……这并不能让人松一口气，因为很少有用户会继续使用这样明显损坏的应用程序。

许多开发商感到不安，因为他们期望脸书能提供更多的稳定性。在消费者的世界里，有一个隐含的假设，即脸书将永远保存你的数据，并使其可以在任何地方访问。(众所周知，脸书因欧洲隐私法而陷入困境，因为即使你希望他们删除数据，他们[也不会删除。)](http://mashable.com/2011/10/21/facebook-deleted-data-fine/#oDciljb08Oqm)

开发人员现在发现，B2B 公司脸书与他们自以为了解的脸书大不相同。保持解析是脸书的主要成本中心。免费计划对许多应用程序来说已经足够好了，所以许多用户不用支付任何费用；与此同时，带宽和存储成本很高。脸书上市公司两天前刚刚公布了不错的季度收益。现在关闭 Parse 是确保他们明年赚更多钱的一种方式，当你不断受到华尔街的审查时，这一点总是很重要。

在某种程度上，脸书在 2013 年收购 Parse 似乎推迟了这一必然。作为一家初创公司，Parse 总是容易出现资金短缺。作为脸书内部的一个部门，Parse 总是容易失去战略支持。无论哪种方式，对于平台的用户和客户来说，结果都是一样的。

对于购买科技产品的人来说，这是一个重要的教训。从大供应商那里购买没有内在的安全性。一家追逐增长的初创公司和一家互联网巨头都可能变得太不稳定，以至于你无法在技术选择上下注。

相反，你应该寻找一家真正想向你销售产品的公司。这里的关键词是“卖”。像 Parse 这样的成长型初创公司往往会为了吸引用户而慷慨解囊。这样的公司希望用投资者的钱来抵消不断增加的损失，其目标要么是被财大气粗的人收购(正如 Parse 所发生的那样)，要么是变得足够大，成为市场的垄断者，在这一点上，随着用户变得“有粘性”，他们最终可以打开资金水龙头。

硅谷资本推动的礼物马竞技不能成为任何长期计划的基础。如果你需要稳定性和一致性，找一家关心客户并收取合理价格的小企业。(一个合理的价格是指你不需要怀疑卖家卖给你的东西是否会让你破产。)

小公司之所以伟大，往往是因为它们能像合伙人一样，与你共同成长。硅谷的初创公司通常会利用你来维持一个超高速增长的图表，这个图表最终会出现在你并不重要的地方。