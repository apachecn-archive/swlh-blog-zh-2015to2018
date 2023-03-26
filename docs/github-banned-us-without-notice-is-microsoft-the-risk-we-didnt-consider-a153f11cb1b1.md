# GitHub 在没有通知的情况下禁止了我们——微软是我们没有考虑到的风险吗？

> 原文：<https://medium.com/swlh/github-banned-us-without-notice-is-microsoft-the-risk-we-didnt-consider-a153f11cb1b1>

![](img/664116f335c31032e4359e51d73c0e8d.png)

Source: Github logo from Github website

像大多数 SaaS 公司一样，我们会定期进行风险评估。上周，微软直接或间接地(通过其对 GitHub 的新所有权)让我对这一评估增加了两个完全出乎意料的新风险。在下一次风险评估会议上，我们必须在思维上更有创造性。

和大多数 SaaS 公司一样，我们也有 API。我们的[语法检查 API](https://prowritingaid.com/en/App/Api) 让人们检查语法错误、风格改进和术语问题。虽然我们的 API 不是我们的主要收入来源，但它确实是收入的重要组成部分，并且像许多公司一样，我们在 GitHub 上托管我们 API 的代码。我们有 13 个包含不同语言 SDK 的存储库，以及许多包含不同文本编辑器插件的存储库，允许人们轻松集成实时语法检查。所有这些代码都是开源的，因为我们积极鼓励人们使用它。例如，我们为 [ProseMirror](https://prosemirror.net/) 编写了一个插件，允许人们集成实时语法和拼写检查。我在 ProseMirror 论坛上积极鼓励人们重用这些代码来集成我们自己以外的服务。

所以，想象一下，当我们的一个开发人员在对我们的新版本进行手工测试时，告诉我我们的 GitHub 账户似乎消失了，我有多惊讶。我去了 GitHub，登录了我们的账户，看到了这条可爱的信息。

![](img/f24f188993e564888265050f60e761b4.png)

注意被动语态:“已被标记”，而不是“我们已标记您的帐户”。作为一个写作学究，我立即想知道谁标记了我们的帐户。这是一个很好的例子，利用被动语态来完全免除自己的责任，这是辩护律师喜欢的一种伎俩。我假设 GitHub 有一些在后台运行的自动流程来标记帐户。

我的下一个想法是，我们一定是错过了一封来自 GitHub 的电子邮件，他们友好地通知我们，我们的帐户已被标记，并可能给出了更具体的标记原因。事实证明他们没有。所以他们完全没有通知或警告就封锁了我们的账户。

当我联系支持时，我解释说我们是一家真正的公司，做真正的生意，像许多其他 SaaS 公司一样使用 GitHub 托管我们的 SDK。这里有一张 Stripe 的 GitHub 账户的图片，他们做的完全一样。

![](img/ead37d4a1b7db8d72d309b7cfbf1eb45.png)

几个小时后，我收到了这样的回复:

```
Hi there, Chris,It appears that you may have set up a profile solely to link to an external website and service.We are a code hosting service and collaboration tool for software developers, so we'll have to keep your account hidden for now.
```

我们确实有链接到我们网站的存储库，但事实上世界上所有其他 SaaS 公司都有。我想我一定是漏掉了一些内容，但是在进一步阅读后，我发现没有任何内容表明我们所做的事情是不允许的。所以我给 GitHub 的支持人员写了回信，暗示这一定是个错误，并请求他们友好地恢复我们的帐户。

将近 24 小时后，GitHub 仍然没有回应，所以我们需要启动 B 计划——转向另一家提供商。在被微软收购的消息传出后，GitHub 看到了创纪录数量的存储库转移到其他服务，如 Bitbucket 和 GitLab。似乎 GitHub 现在也在积极鼓励其剩余用户离开。这可能是 GitHub 即将发生的事情的一个迹象吗，微软像一个专制政权一样，出于未公开的原因，在没有任何警告的情况下关闭了存储库甚至整个账户？我不确定。我希望这只是一个简单的误会，GitHub 会选择恢复我们的帐户，但谁知道呢。对我来说，在这种情况下，良好的沟通是关键。GitHub 在这方面绝对失败了。除非有严重不当行为的证据，否则 GitHub 应该在关闭客户账户之前与其进行讨论。他们至少应该告诉用户这是他们所做的，概述原因和补救措施。

我必须添加到我们风险评估中的第二个事件是什么？好吧，整个蔚蓝色的云正在下沉。我们在 Azure 中托管我们所有的服务。如果一个区域出现故障，我们应该会没事，因为我们会故障转移到另一个区域。然而，我们没有考虑到如果整个微软活动目录停止运行会发生什么，这就是发生的情况。你可以[在这里](https://www.zdnet.com/article/microsoft-south-central-u-s-datacenter-outage-takes-down-a-number-of-cloud-services/)了解更多信息。我们甚至无法登录 Azure 门户网站。甚至 Azure 状态页面也关闭了——当然他们应该在 AWS 上托管这个！

而这一切都发生在我们的 CTO 决定去度假的那个星期:另一个我没有考虑到的风险！

因此，如果你在 GitHub 上托管你的 SDK，而你的客户无法访问这些 SDK，这可能会中断你的收入流，那么考虑制定一个应急计划，作为你风险评估的一部分。

我们从这些经历中获得的其他重要信息是:

**1)制定风险评估计划时要更有想象力。审视一切可能影响你的收入和客户体验的因素，尤其是你无法直接控制的服务。**

2)将数据库备份存储在托管服务提供商之外。您甚至可能无法访问您的备份。

3)支持容器来托管不可知的部署。除非你真的需要，否则不要被某个主机提供商束缚住。你永远不知道什么时候你可能需要匆忙更换提供商。

**4)小心不要依赖你没有付费的第三方服务。**

【更新:又发了几封邮件后，我们终于收到了 GitHub 的回复，他们恢复了我们的账户。不过道歉会有很大帮助的！]

## 你试过[的 ProWritingAid](https://prowritingaid.com) 了吗？你还在等什么？

[![](img/839e00a66505235880e7a5c398bd5cec.png)](https://prowritingaid.com)[![](img/308a8d84fb9b2fab43d66c117fcc4bb4.png)](https://medium.com/swlh)

## 这篇文章发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，有+368，366 人关注。

## 订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

[![](img/b0164736ea17a63403e660de5dedf91a.png)](https://medium.com/swlh)