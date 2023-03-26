# 以太坊不会隐藏你的秘密

> 原文：<https://medium.com/swlh/ethereum-aint-hiding-your-secrets-703e89088937>

## 关于如何在协定私有变量中显示状态的技术演练

![](img/011ad17b4380da7038785d759d13e9ba.png)

Spammy Fun Image from Blog 4Linux

# 序

这是一个技术教程，它将带您了解从以太坊智能合约的私有变量中检索状态的具体步骤。这里的所有技术都可以应用到现实生活中。

*本教程由* [*以太者*](https://ethernaut.zeppelin.solutions/) *Lvl8 挑战鼓励。*

# 你可能需要什么

[松露](https://truffleframework.com/)/[ganache-CLI](https://github.com/trufflesuite/ganache-cli)/[node . js](https://nodejs.org/en/)/[curl](https://curl.haxx.se/)

# 合同代码

下面是一个非常简单的契约，有四个私有变量，有四种不同的类型: **uint256** 、**布尔**、 **uint16** 和**映射**。当契约被部署到网络时，这些值被初始化。我们假设合约已经部署到“0xb3b 4546 a6 D8 c8 CD 1081 AC 94 a 7 e 06 a 24 b 207 c 863d”。

```
contract PrivateStorage {
    // Private Variables
    uint256               private    v0;
    bool                  private    v1;
    uint16                private    v2;
    mapping(uint => uint) private    v3; // Initializations    
    constructor() {
        v0    =    5;
        v1    =    true;
        v2    =    6;
        v3[1] =    7;
    }
}
```

# 技巧(1)——揭示 uint256

不可能通过从外部调用来访问合同的值。为了跳过障碍，我们需要通过 web 3 API "**eth _ getStorageAt**"直接访问契约的**存储**。通过在控制台/终端中执行以下命令，我们在第 0 个状态“0xb3b45…”处访问契约，这是第一个声明的变量 *v0* 。

```
curl -X POST - data '{"jsonrpc":"2.0", "method": "**eth_getStorageAt**", "params": ["**0xb3b4546a6d8c8cd1081ac94a7e06a24b207c863d**", "**0x0**", "latest"], "id": 1}' localhost:8545
```

返回的答案将是:

```
{"id":1,"jsonrpc":"2.0","result":"**0x05**"}
```

表示“0xb3b45…”合同的第 0 个值为 **5** ！！！

# 技巧(二)——揭示布尔& uint16

由于 EVM 倾向于将多个小状态挤进同一个槽，所以布尔值 *v1* 和 uint16 值 *v2* 被分配到同一个存储槽位置——第 1 个位置。通过执行与技术(1)类似的命令，我们可以显示出 *v1* 和 *v2* 的组合答案。

```
curl -X POST --data '{"jsonrpc":"2.0", "method": "eth_getStorageAt", "params": ["0xb3b4546a6d8c8cd1081ac94a7e06a24b207c863d", "**0x1**", "latest"], "id": 1}' localhost:8545
```

回应将是:

```
{"id":1,"jsonrpc":"2.0","result":"**0x0601**"}
```

展示了第一私有状态 *v1* 的值为 **1** (为**真**)，第二私有状态 *v2* 的值为 **6** ，它们一个接一个地连接在一起。

# 技巧(3)——揭示映射

映射有一个不同的存储指示符，它是与协定中的映射位置连接在一起的映射键的散列。例如**hash([mapping _ key | mapping _ position])**。为了找到串联，我们将映射键 **1** 附加到映射位置**2**(因为其他私有状态 *v0、v1、v2* 用完了前两个位置。)

```
[mapping_key | mapping_position] = "0x1" + "0x2"
```

从技术上讲，我们需要在松露或其他地方创建一个可变的*梳子*:

```
var **comb** = "0000000000000000000000000000000000000000000000000000000000000001" + "0000000000000000000000000000000000000000000000000000000000000002"
```

我们散列这个*梳*以获得**eth _ getstoraget**访问的最终指示符。

```
var **indicator** = web3.sha3(**comb**, {"encoding": "hex"})
```

在这种情况下，我们将得到指示符为"**0x e 90 b 7 BC eb6 e 7 df 5418 FB 78d 8 ee 546 e 97 c 83 a 08 bbccc 01 a 0644d 599 CCD 2 a 7 C2 e 0**"，它在下面的命令中使用:

```
curl -X POST --data '{"jsonrpc":"2.0", "method": "eth_getStorageAt", "params": ["0xb3b4546a6d8c8cd1081ac94a7e06a24b207c863d", "**0xe90b7bceb6e7df5418fb78d8ee546e97c83a08bbccc01a0644d599ccd2a7c2e0**", "latest"], "id": 1}' localhost:8545
```

成功的结果将是:

```
{"id":1,"jsonrpc":"2.0","result":"**0x07**"}
```

就是这样。我们到此为止。:)

# 摘要

仅仅利用智能合约上的私有变量是无法隐藏信息的。强烈建议您在将任何秘密发送到区块链之前对其进行编码或加密，该秘密总是对所有人公开的。

# 伟大的参考

*   [https://github.com/ethereum/wiki/wiki/JavaScript-API](https://github.com/ethereum/wiki/wiki/JavaScript-API)
*   [https://medium . com/coin monks/how-to-read-private-variables-in-contract-storage-with-truffle-ether naut-lvl-8-walk through-b 2382741 da9f](/coinmonks/how-to-read-private-variables-in-contract-storage-with-truffle-ethernaut-lvl-8-walkthrough-b2382741da9f)
*   [https://ether naut . zeppelin . solutions](https://ethernaut.zeppelin.solutions)

[![](img/308a8d84fb9b2fab43d66c117fcc4bb4.png)](https://medium.com/swlh)

## 这篇文章发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，拥有+ 372，020 名读者。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

[![](img/b0164736ea17a63403e660de5dedf91a.png)](https://medium.com/swlh)