# 新手程序员应该使用“Git”的 4 个理由

> 原文：<https://medium.com/swlh/git-as-the-newbies-learning-steroid-963a2146220b>

![](img/b0f40d85222149bc9e09c5faff85d245.png)

当我听到 word 版本控制或 [Git](https://en.wikipedia.org/wiki/Git) 时，我认为它是一组命令行，专业程序员使用它们在巨大的代码库上与他们的大团队协作。

> 不是给我的。我是个新手。我过会儿再看看。

不对。我后来才知道 Git 是新手的学习类固醇。

# **给 5 岁孩子的 Git**

> 想象你正在一本花卉涂色书上涂色。你给所有的叶子都涂上了绿色，现在是最精彩的部分，给花瓣上色。你知道你最喜欢红色，但是喝完之后看起来很糟糕。有了 Git，你可以立刻恢复你选择的红色，如果你改变主意，你可以自由地重新使用红色。一部作品不一定是永久的；每一个动作都被记录下来，并且是可逆的。 *(* [*来源*](https://dev.to/maestromac/comment/him) *)*

本文将解释作为一名初级程序员，我们如何利用 Git 的力量。

![](img/687a611b6226f677bd9b428562589273.png)

[Image’s Source](https://codereviewvideos.com/blog/wp-content/uploads/2015/06/git-goodness.gif)

# 利用在线教程

学习编码的最好方法是跟随演示项目的教程系列，键入代码，然后**将代码保存为参考**。

然而，随着本系列的继续，大多数教程都会覆盖这些代码。例如，第一集的代码被第二集的代码替换了。他们留给我们的只是最新版本的代码。

Git 将所有版本的代码保存为一个单独的提交。所以我们在开发自己的项目时会有各种各样的参考。

# 纠正错误

我们通过与虫子搏斗学到了很多东西。

尽管如此，总有我们陷入困境的时候。例如，bug 日志没有帮助，Google 给出了一堆不相关的结果，或者社区支持，比如 StackOverflow，不理解我们的问题。

Git 创建了一个检查点，我们可以回滚到这个检查点，重新评估策略，并重新开始。

此外，回滚鼓励试错。我们对代码进行实验，如果不满意就回滚，直到我们想出最优雅的解决方案。

# **学会分解事物**

![](img/da5c4e205eaf0e6217b1ec61b352df08.png)

Photo by [Vadim Sherbakov](https://unsplash.com/photos/osSryggkso4?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/pieces?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

为了利用回滚，提交必须很小。我们宁愿回滚 20 行代码，也不愿回滚 200 行。

使用 Git 训练我们将大问题分解成小的可提交单元。分解事物有助于设计一个鸟瞰计划。清晰的方向性计划使我们免于迷失在代码的迷宫中。

此外，它让我们为协作项目做好准备，在协作项目中，长时间后提交大型提交可能会导致[合并冲突](https://help.github.com/articles/about-merge-conflicts/)——一个分支中的提交与其他分支中的提交冲突。

# **修改变得容易**

我们中有多少人在很长一段时间后回到这个项目，而它却把我们当成陌生人看待？

![](img/639b3b4a34ace812c5312ae0055161f8.png)

Photo by [Edwin Andrade](https://unsplash.com/photos/4V1dC_eoCwg?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/raise-your-hand?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

> “嘿，亲爱的，”——*程序员*
> 
> “我认识你吗？”— *项目*
> 
> “通讯器接通了！我离开了一段时间，但我从未停止想念你，”——*程序员*
> 
> … — *项目*
> 
> “哦，请吧。又来了，”——*程序员*

看着一个旧的项目可能会令人困惑，如果不是恐吓的话。项目存储库由许多文件组成。每个文件包含数百行(如果不是数千行的话)代码。

我们搓着头问，

> “我从哪里开始？”

Git 给了我们简单的答案，

> "从第一次提交开始，一直到我们停止的地方."

它帮助我们跟踪开发的流程，从而加速修改。

Git 不仅是大型协作项目的强大工具，也是初学者的学习加速器。

Git 存储代码版本作为参考，有助于加速学习和修订。它还鼓励试错，并训练我们在编码前做好计划。

**从哪里开始:** [学习 Git 的可视化交互方式](https://learngitbranching.js.org/)。

**出发前:**新手如何使用 Git？

*最初发布于:*[www.beyondwantrepreneur.com](http://beyondwantrepreneur.com/)

如果你喜欢我的笔迹，这里还有一些:

[](/swlh/my-first-idea-execution-ecd1a1642e99) [## 我的第一次申请和它是如何失败的

### “习惯触发器”——一个重复的警报，提醒用户在一周的选定日期，在首选时间或在…

medium.com](/swlh/my-first-idea-execution-ecd1a1642e99) [](/the-post-grad-survival-guide/how-audiobooks-cure-my-insomnia-bfd583bf85e1) [## 如何用有声读物治愈失眠

### 有声书助你睡个好觉，醒得更聪明

medium.com](/the-post-grad-survival-guide/how-audiobooks-cure-my-insomnia-bfd583bf85e1) ![](img/731acf26f5d44fdc58d99a6388fe935d.png)

## 这篇文章发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，拥有 289，682+读者。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)