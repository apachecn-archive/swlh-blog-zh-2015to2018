# 用椰子和菠萝解释区块链

> 原文：<https://medium.com/swlh/explaining-blockchain-with-coconuts-and-pineapples-e44edcbe2e0f>

在我之前的博客[用沃利在哪里和一个摄像头解释区块链](/swlh/explaining-blockchain-with-wheres-wally-and-a-camera-79e860a05815)中，我对区块链技术做了一个直观易懂的解释(沃利在哪里针对美国的人)。阅读我以前的博客将有助于理解这一点。

在这部续集中，我们将看到区块链或照片链如何解决*的双重支出问题*。

![](img/c8ae296d93d448873d157b0c5340536f.png)

Two financial systems

# 场景的提醒

那么…什么是双重消费问题？让我们提醒自己。

我们回到了 2008 年。

神秘的 Satoshi 不喜欢银行，所以他正在设计一个新的金融系统(这将成为比特币)。他首先从银行取出交易分类账，交给用户。但是，当网络中的每个人都有共享账本的副本时，他就遇到了问题。

这样一个系统如何确保每个人的账本都在说同样的事情。这样的系统如何保证每个人的账本都在*共识*？

## 例子

让我们举个例子说明为什么这是个问题。假设一个交易发生在分散的网络上(上图中右边的那个)。例如，“卡罗琳付给蒂姆 10 个硬币”。该事务立即在网络上广播。一些用户在收到该交易后，将其添加到他们的分类帐版本中。但是，由于连接问题，少数用户收不到此交易。

在这种情况下，围绕网络如何就共享分类账的“最正确”版本达成一致存在问题，因为一些人的分类账说的是一件事，而其他人的分类账说的是另一件事。这就为一些不良行为敞开了大门。一个狡猾的用户可以利用这一点。他们可以攻击网络，花掉一些数字硬币两次。这个问题叫做*双重支出问题*。

为了解释双重支出问题，我将用一些椰子和菠萝来举例说明。

![](img/388164cfff9de8410cf577b8a61387f2.png)

# 双重支出

假设我是分散网络中的恶意用户，我的账户中有 10 个数字硬币。我要试着花两次这些数字硬币去买椰子和菠萝(我在做 pia colada！).

现在，重要的是，我们不要把这些数字硬币视为实物，因为不可能把任何实物花两次。如果我给了你一枚一英镑的硬币，没有什么聪明的方法可以不把它从你身上拿回来而再次花掉。然而，有了数字货币，这就成为可能(就像我们可以在电脑上复制一个文件，这样两个人就可以在自己的电脑上拥有同一个文件的一个版本)。

我在我的账户中有 10 个数字硬币，并且网络在这个数量上是一致的，即每个人的分类账都同意我有 10 个数字硬币。

## 我的惯例

我首先拜访了我的朋友 Alice，买了一些椰子(这是 Alice 在开始使用上一篇博客中描述的照片链技术之前的照片)。她是镇上最好的椰子小贩。我把我的 10 个数字硬币转给她，她把这笔交易加到她的账上。她给我椰子。

但是我知道爱丽丝的网速很慢，所以我感谢了爱丽丝，向她道别，然后迅速离开了。

我立即沿街跑向我的朋友鲍勃的家。鲍勃卖菠萝🍍(镇上最好的)我想买一些。它们的价格和椰子一样，整整 10 个数字硬币。

现在，由于我很快就到达了 Bob 的家，我与 Alice 的椰子交易还没有通过分散式网络到达 Bob，因此，当他查看他的共享分类账版本时，在他看来我仍然有 10 个数字硬币。

因此，Bob 很乐意接受我的交易，我们在 Bob 的计算机上提交交易。隐藏我的真实意图，我敦促 Bob 立即将菠萝交易发送给网络中的每个人，这样钱就安全地属于他了。幸运的是，他有光纤网络，他的信息可以传到 99%的网络上，而我和爱丽丝的椰子交易只能传到少数人那里。

由于大多数人(下图中的蓝色账本)认为鲍勃是我的数字硬币的合法所有者，他们说服了网络的其他人(下图中的黄色账本)，爱丽丝很遗憾地被排除在外。

现在，在这种情况下，爱丽丝可以来找我，并要求她的钱或至少她的椰子。但如果我是匿名网购者呢？那么爱丽丝只是被骗了。就这样，我已经攻击了系统，在椰子和菠萝上花了同样的 10 个数字硬币，我正在调鸡尾酒！

这在文献中被称为*双支出攻击*。

![](img/6dad0dfefe6ea18600831d483b25d99a.png)

Double spending problem

## 重复支出问题综述

当交易被立即添加到不同版本的共享总账时，我可以用相同的数字硬币购买椰子和菠萝。

因此，我们需要一种方法来防止双重支出攻击。区块链或照片链技术就是这样做的。

# 区块链防止双重支出攻击

*下面，我将使用我上一篇* [*博客*](/swlh/explaining-blockchain-with-wheres-wally-and-a-camera-79e860a05815) *中的照片链术语。至于官方术语，上面写着 Wally-searcher，想想 miner。上面写着照片的地方，想想街区。*

现在假设 Alice 和 Bob 是分散网络的一部分，该网络使用照片链来更新和维护他们的财务系统的共享交易分类账。让我们看看这对我同样的双倍消费习惯有什么影响。

## 我的惯例

我像以前一样开始。我出现在爱丽丝家。她好心地从她的寻找工作中抽出一些时间卖给我一些椰子。然而，她并没有马上把椰子给我。她让我在照片链网络的一次交易中给她转账 10 个数字硬币。我把我的交易发送到网络上，它就出现在网络上许多沃利搜索者的办公桌上，他们都试图解决自己的沃利在哪里的难题。

但此时爱丽丝没有交出椰子，而是等待着。我和她的交易还没有公布在账上。她一直在等待，直到她看到一张我和她交易的照片。

爱丽丝不信任我……的确如此！我还偷偷在网上从鲍勃那里买了菠萝，他又把那笔 10 枚硬币的交易发送到了网络上。

我现在开始出汗了。爱丽丝和鲍勃都向网络广播了交易，我仍然没有收到任何水果。

10 分钟后，一张照片出现在爱丽丝的桌子上，照片上有我和她交易的椰子(见下图)。网络中有人解决了他们当前的难题，并在他们的照片中加入了我的椰子交易。在这一点上，我知道大多数 Wally-searcher 将验证这张照片，并将转移到一个新的 Wally puzzle，在'这张照片之上'。

![](img/2e829f4f0197697d354193f4bb822458.png)

First photo to hit Alice’s desk

所以我不耐烦地问我是否可以带着椰子离开，然而爱丽丝仍然在等待！她是一个超级谨慎的卖家。她想确定网络上的其他人在之前的照片上没有其他的解决方案。

几分钟后，她从网络上收到了另一张照片，在这张照片中，她看到了之前照片空间中的照片，照片中有我与她进行的椰子交易。最后，她有足够的信心交出椰子，因为我对她的交易已经被另一张照片嵌入到链中。

所以我得到了椰子，但是我怎样才能得到菠萝呢？此时，要将 Bob 的交易而不是 Alice 的交易放入共享分类帐，我需要启动一个不同的照片链，其中包括菠萝交易，但不包括椰子交易。

## 那么我该怎么做呢？

我需要做的，完全靠我自己，是找到一个解决我自己的问题的方法，即在包含我与爱丽丝的椰子交易的照片(下图中的照片 346)之前，Wally 在照片链中的“顶部”。

如果我可以解决这个难题，那么我可以发布一张照片，其中包括我对 Bob 的菠萝交易，但不包括我对 Alice 的椰子交易，这将启动一个竞争链(下图中的顶部链)。但其他 Wally-searcher 正试图建立在最长的链上，因为在最长的链上，他们最有可能赢得竞争，最终将在照片链上结束。

所以我需要让我的对手链成为网络中最长的链。为了做到这一点，我需要在我需要解决的第一个问题的基础上解决第二个问题，并继续解决问题，直到我建立了一个比所有其他 Wally-searcher 竞争的链更长的链。如果我可以建立一个更长的链，那么我就可以将我的长链广播到网络上，在这一点上，其他 Wally-searcher 将开始对我的链进行工作，因为它更长了。

![](img/729daf36ad1f01d6381b14e5bd00b9b1.png)

The competing branches of the photo-chain

所以是我对抗所有其他搜索者，试图找到沃利在哪里的谜题的答案。但是沃利在哪里没有捷径，所以我比网络中的其他人更快找到解决方案的可能性非常小。即使我可以说服其他 Wally-searcher 加入我的任务，加倍消费并给我一些菠萝，我也需要超过一半的搜索者有很好的机会创造一个新的最长的链(这在文献中称为 *51%攻击*)。

## 到底发生了什么

不幸的是，由于爱丽丝是一个超级谨慎的销售人员，她一直等到我的交易被另一张照片粘在一起后才给我椰子，鲍勃没有接受我的交易，我也没有得到任何菠萝。

*在比特币网络中，许多卖家在接受交易有效之前，会等待 3 到 6 个区块被放置在包含相关交易的区块之上。*

## 概括起来

为了发布一张照片，Wally-searcher 不得不做的艰苦工作使得改变形成分类账的照片链变得非常困难。这意味着很难重复花费，因为要创建一个不同的最长的照片链需要做大量的 Wally-search，从链中较早的照片开始，并试图超越当前最长的链。

包含交易的照片在链中越靠下，从该照片下面开始的不同照片链越不可能成为最长的链。正是这种推理(以及一些概率论)证明了反对双重支出攻击的论点是正确的。

但是请记住，在足够多的块放在事务之上之前，事务是不会被安全执行的！

*如果你喜欢这个故事，请👏请与其他想了解区块链的人分享。*

*如果你对更多区块链相关的东西感兴趣，那就来看看我的博客* [*零知识证明*](/pilcro/zero-knowledge-proofs-a-tale-of-two-friends-d7a0ffac3185) *，也是深入浅出的讲解。*

*此外，请访问*[*【www.pilcro.com】*](https://www.pilcro.com/?utm_source=medium&utm_medium=Blockchain2&utm_campaign=awareness)*，了解访问和分享贵公司风格指南和品牌资产的最佳方式，所有这些都建立在 G-Suite 之上。*

![](img/731acf26f5d44fdc58d99a6388fe935d.png)

## 这个故事发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的企业家出版物，拥有 273，103+人。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)