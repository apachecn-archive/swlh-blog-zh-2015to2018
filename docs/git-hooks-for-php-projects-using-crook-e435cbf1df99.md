# 用 Crook 实现 PHP 项目的 Git 挂钩

> 原文：<https://medium.com/swlh/git-hooks-for-php-projects-using-crook-e435cbf1df99>

![](img/4e24d5980b3f5b35cc18dd4bfe79771e.png)

Photo by [Sara Cardoso](https://unsplash.com/photos/rylQj173QZI?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

这个项目从寻找一些工具来帮助我管理一个简单项目的 Git 挂钩开始。像每个正常的开发人员一样，在尝试编写自己的问题解决方案之前，我去找了优秀的 Packagist，并为这项工作寻找了一些工具。有的是！真的，很多工具。

我打开了几个标签，开始阅读关于项目、用法等，但我没有找到任何我想要的东西。所有这些工具不仅仅是管理 Git 挂钩。其中一些附带了一些检查，另一些则严重依赖于名称空间。一件简单的事情，一个非常复杂的过程。

# 我在找什么？

我想要最简单的事情:事件发生，然后触发一些由我或其他人编写的代码。不管是什么语言，如果我想在 Ruby 脚本中插入一个**预提交**钩子，那就没问题。如果我想运行一个 Bash 脚本，一个 Golang 的二进制文件，随便什么。对我来说，工具必须接受事件并触发挂钩的动作。就是这样。我没找到。当我们找不到合适的工具时，我们该怎么办？我们创造了一个，并将其开源。: )

# 第一，要求

我需要一些东西来管理客户端 Git 挂钩。当一些客户端钩子事件被触发时，这个工具应该允许我运行任何我想运行的东西，不管是什么语言。它必须简单、直接、易于安装、易于使用，必须是 Packagist 上可用的包，具有很少的依赖性，并且用 PHP 编写。

# 克鲁克来了

Crook 是(至少对我来说)管理 PHP 项目中 Git 挂钩的最简单的方法。是我试图为这项工作创造一个好的工具。在接下来的部分中，我将更详细地解释一切是如何工作的，以及如何使用它来集成项目中的动作和钩子。我在 Packagist [这里](https://packagist.org/packages/felipebool/crook)发表了它，你可以在我的 GitHub 页面[这里](https://github.com/felipebool/crook)找到源代码。

如果你只是需要一些基础知识，让我简单解释一下。**TL；DR** :安装后，在 composer 的脚本部分创建一个条目，并给它一个名称，任何名称，然后运行 Crook add 命令(一次)将该脚本(动作)绑定到给定的钩子名称(事件)。当事件被触发时，该脚本将运行。就是这样。

# 它是如何工作的？

首先，你跑

`$ vendor/bin/crook init`

这个命令将创建一个名为 crook.json 的 JSON 文件，这个文件负责保存 Git 钩子名称和动作之间的绑定，以及其他一些配置信息。没有必要手动更改它，你可以通过命令行使用 Crook 做任何事情。

在脚本部分的 composer.json 上添加一个条目后，您可以像这样将该操作绑定到钩子

`$ vendor/bin/crook add hook-name action-name`

移除钩子也是一样

`$ vendor/bin/crook remove hook-name`

所以，假设你在你的团队中讨论代码风格时遇到了困难，所有的代码评审都是基于“在这里放一个空行”，“将这个括号发送到下一行”和所有这类不重要的东西。选择您的代码检查/代码美化工具，并将其插入预提交 g it 挂钩。在 composer.json 中添加一些条目，然后运行

`$ vendor/bin/crook add pre-commit code-check`

下次有人试图创建一个新的提交时，代码检查将会运行，并根据您公司的代码标准运行一些修复。顺便说一下，我在另一篇文章中讨论了一些关于 phpc 和其他有趣的 PHP 工具和概念，如果你不知道或者想好好读一读，请看看[这就是现代 PHP 的样子](https://medium.freecodecamp.org/this-is-what-modern-php-looks-like-769192a1320)。

# 该机制

Git 挂钩基于你在里面创建的动作/文件。git/hooks。所以，如果你进入你的项目并列出这个目录，你会发现一些样本文件来帮助你创建你自己的钩子。

克鲁克所做的只是创建一个符号链接。git/hooks/some-hook 到一个名为 theHook 的文件，所以，每次你添加一个新的钩子，在钩子文件和 theHook 之间就会创建一个新的符号链接。这样，当它触发该脚本时，该书将运行，然后执行您添加的任何操作。这就是我在本文开头所说的原因，你可以运行任何你想运行的东西，服务器中所有可用的命令都可以使用，你可以用任何语言创建脚本，混合东西，在那里施展你的魔法。

# 该项目

我有一个很好的时间来创建这个，我希望它能对你的项目有所帮助。你可以在它的 Github 页面上找到更多关于 Crook 的信息。我上一次提交是在几个月前，但它似乎真的很稳定，并进行了一些测试。我知道一家公司用它为一个 PHP 团队管理钩子，我得到了一些好的反馈。如果有人可以使用它，发现问题，报告问题，或者做出贡献，我将不胜荣幸。欢迎任何批评或问题。

你用什么来管理 Git 挂钩？你对这种类型的工具有什么期望？在评论里告诉我。

[![](img/308a8d84fb9b2fab43d66c117fcc4bb4.png)](https://medium.com/swlh)

## 这篇文章发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，有+ 382，862 人关注。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

[![](img/b0164736ea17a63403e660de5dedf91a.png)](https://medium.com/swlh)