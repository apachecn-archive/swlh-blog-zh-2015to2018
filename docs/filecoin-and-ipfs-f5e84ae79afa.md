# FileCoin 和 IPFS——重塑存储

> 原文：<https://medium.com/swlh/filecoin-and-ipfs-f5e84ae79afa>

## [区块链 vNext 系列](/@sgrasmann/blockchain-vnext-a-series-ff5469aa1f22)(第一部分)

[胡安·贝尼特](https://medium.com/u/6238e2d24931?source=post_page-----f5e84ae79afa--------------------------------)—[FileCoin](https://filecoin.io)的创始人——有着远大的抱负:他想创建一个分散存储网络(DSN)并在此基础上建立一个生动的市场。想想亚马逊 S3 或者类似的服务。不同之处在于，你不必相信像亚马逊这样的中央云供应商，他们可以决定其服务的价格。相反，任何有可用存储空间的人都可以加入，成为 FileCoin 存储提供商。在区块链术语中，这些是 FileCoin 的“矿工”。他们通过向用户提供的存储量在网络中获得影响力。

FileCoin 最终用户的一大优势是，他们的文件可能会存储在附近的 FileCoin 提供商处，而不是可能很远的中央云存储处——特别是如果用户生活在发展中国家。FileCoin 希望根据您的需求提供复制和加密数据的选项。文件的存储和检索将从物理地址透明地进行。

FileCoin 令牌用于创建存储市场:用户将使用 FileCoin 支付服务费用。存储提供商将通过 FileCoins 获得报酬。该视频有助于理解基本知识:

Introduction video to FileCoin, found on [https://filecoin.io/](https://filecoin.io/)

目前还不清楚 FileCoin 在哪里看到了他们服务的局限性。他们可以专注于他们的技术和市场。但他们也可以更进一步，提供更高级别的应用程序，并试图与像 [DropBox](https://www.dropbox.com) 或 [OneDrive](https://onedrive.live.com) 这样的服务竞争。

## 技术

FileCoin 在很大程度上建立在[IPFS](https://ipfs.io)——**星际文件系统**的基础上，它本身想要**取代 HTTP** 。是的，你没看错。

IPFS 的创建者看到了 HTTP 的基本设计中的许多问题，并希望创建一个不依赖中央实例和 URL 作为基本组件来检索数据的高级协议。基本想法很吸引人。我强烈推荐观看 IPFS 的创造者 Juan Benet 的 TED 演讲，他也深深地卷入了 FileCoin:

TED Talk about the motivation to create IPFS

IPFS 可以被视为区块链技术的一个令人信服的基础。根据文件的内容而不是位置来复制和寻址文件有一些令人印象深刻的特点。它还可以用来规避基于地址的审查——你可以从《观察家报》的[这篇有趣的文章中读到。一个想法是](http://observer.com/2017/05/turkey-wikipedia-ipfs/)[用 IPFS](https://github.com/ipfs/distributed-wikipedia-mirror) 镜像维基百科。这在最近的加泰罗尼亚危机中使用过。

FileCoin 在很大程度上建立在 IPFS 的成就之上。它在 IPFS 的基础上添加了其 [FileCoin 令牌(FIL)](https://coinlist.co/filecoin) 和区块链元素，以创建一个存储市场，让所有参与者都有动力存储和检索最终用户的文件。

有趣的部分是 FileCoin 的共识算法。它与现有的区块链策略有很大不同:FileCoin 使用**存储证明**，而不是我们从比特币或以太坊中知道的**工作证明**。FileCoin 的[白皮书](https://filecoin.io/filecoin.pdf)大谈其存储证明方法(有两种:复制证明和空间时间证明)如何工作，以服务于其主要用例，并确保存储提供商真正存储他们声称要做的事情。作者还解释了 FileCoin 寻找对其网络有用并产生可重用结果的共识算法的动机(白皮书第 6 章)。这应该有助于避免我们从比特币中了解到的巨大能耗问题。

该白皮书也相当诚实，并看到了许多开放的研究工作要完成，以使想法成为现实，并验证一些新的战略(见第 8 章)。

## 提供资金

FileCoin 由[协议实验室](https://protocol.ai/)驱动。他们将自己定义为网络协议的研究、开发和部署实验室(T2)。他们想用他们的协议创造新的市场，正如你所看到的[这里](https://protocol.ai/blog/protocol-labs-creating-new-networks/)。Protocol Labs 非常专注于开源软件，并得到了一些知名投资者的支持，如 Y-Combinator。

FileCoin 是 2017 年最大的 ico 之一和[收入 2.57 亿美元](https://www.coindesk.com/257-million-filecoin-breaks-time-record-ico-funding/)。然而，这是一个极其雄心勃勃的项目，需要一些时间来实现其承诺。我认为这是一项长期投资。

## 对社会的影响

FileCoin 可能会对社会产生巨大的积极影响——尤其是对那些与云提供商联系有限或缓慢的发展中国家的用户而言。如果 FileCoin 的计划按预期实施，这些用户应该可以更便宜、更快捷地访问相关数据。

它的设计也非常开放。理论上，硬盘上有空闲空间的每个人都可以作为存储提供商加入。

FileCoin 也可能有助于防止假新闻，因为文件是通过其内容的散列来识别的。文件中的更改将创建这些文件的新实例，因此原始内容不会丢失。

FileCoin 的发行还可能导致小型本地存储提供商的成立，他们充当 FileCoin 矿工——从而推动本地经济而不是全球参与者。但这种希望可能会被证明是错误的——正如我们在比特币生态系统中看到的那样，该系统拥有为数不多但规模庞大的矿业公司。

![](img/88772175fd3dc3c705808cf41e6a1dab.png)

Will FileCoin create a new world-wide storage bazaar with smaller players? Photo by [neosiam](https://www.pexels.com/de/u/neo8iam/), found on [Pexels](https://www.pexels.com/de/foto/asiatisches-essen-bohnen-essen-gewurz-618491/)

## 结论

FileCoin 和 IPFS 肯定是勇敢的项目。FileCoin 也是一个很好的例子，说明区块链技术如何努力不仅创造新的分散用例，还创造新的市场。这些新市场能否在用户和提供商之间建立必要的平衡还有待观察。

我一定会关注这些令人惊叹的项目。

***免责声明:*** *本文无意成为任何形式的投资建议。如果你打算投资本文提到的某个项目，自己做研究并寻求专业支持。*

如果你喜欢这个故事，你可能也会喜欢我的关于[“公用令牌的隐藏力量”](/swlh/the-hidden-power-of-utility-tokens-e846d3a5c1eb)或我的“[区块链 vNext 系列”](/@sgrasmann/blockchain-vnext-a-series-ff5469aa1f22)的新故事。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)

## 这篇文章发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，有 277，994+人关注。

## 订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)