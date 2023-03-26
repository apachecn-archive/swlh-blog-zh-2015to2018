# 无线充电

> 原文：<https://medium.com/swlh/wireless-charging-c0a35351ffe8>

由[阿洛克·帕马尔](https://medium.com/u/9408b44d35d0?source=post_page-----c0a35351ffe8--------------------------------)和[苏坎特·库拉纳](https://medium.com/u/6d41261644a8?source=post_page-----c0a35351ffe8--------------------------------)

无线充电是一项无需设备实际接触即可为设备充电的技术。是的，你没听错，在无线充电的过程中，我们不需要每次都将笨重又长的 USB 连接到你的手机来为你的手机充电，但通过这项技术，电力是通过自由空间传输的。在文章的前半部分，我们回顾了高中物理，这是这项酷技术的背后。如果您想跳过这一部分，可以直接进入可用产品部分。

它实际上是如何工作的？移动充电器用于将交流电
从市电转换为所需的 DC 电平，然后经过一定的整流和过滤过程后，DC 电平馈入电池进行充电。在传统的充电中，充电器通过导电介质(USB 线)向移动设备的充电电路供电，但是假设从充电器单元到充电电路的这种能量传输在外部不需要物理介质的情况下发生？

无线充电基于磁共振或感应电能传输(IPT)的原理。这种在两个物体之间传输电流的过程可以通过使用线圈感应电磁场来实现。因此，要理解无线充电背后的概念，我们必须熟悉与之相关的术语。从充电器到手机的能量转移是通过相互感应来完成的，受法拉第感应定律支配。

法拉第实验

法拉第成功地证明了如果磁场强度发生变化，那么只会产生感应电流。磁场的强度可以假设为穿过特定区域的磁力线的数量。这也被称为磁通量。

![](img/db08c4384834d18711cf2369536e3570.png)

From: [https://byjus.com/physics/faradays-law/](https://byjus.com/physics/faradays-law/)

![](img/c9b69e452f3a313634f70af71f4ee9a7.png)

法拉第接下来的实验证明，当电流通过铁棒时，它就变成了电磁铁。他注意到，当磁铁和线圈之间有相对运动时，就会产生感应电磁力。当磁铁绕轴转动或保持不动时，就看不到电动势。因此，从上面的实验中可以推断出，电磁力的产生应该有磁通量的变化。

在第三个实验中，他发现检流计没有显示任何偏转，没有感应电流在线圈中产生当线圈在一个稳定的磁场中移动。当磁铁离开线圈时，安培计转向相反的方向。

法拉第定律:

**法拉第第一定律** :
法拉第电磁感应第一定律指出，每当导体位于波动磁场中时，都会感应出电动势，这被认定为感应电动势，如果导体电路闭合，也会感应出电流，这被称为感应电流。

改变磁场的方式:
1。通过相对于磁体旋转线圈。
2。通过将线圈移入或移出磁场。
3。通过改变放置在磁场中的线圈面积。
4。通过将磁铁移向或移离线圈。

**法拉第第二定律** :
它陈述了感应电动势等于磁链的变化率，其中磁链只不过是线圈匝数和与线圈相关的磁通量的乘积。

法拉第感应定律:
ε=−nδϕδt
感应电动势产生电流，电流沿单一方向运动，使得变化的磁场可以被磁场代替。没有电池的电路也能产生电流。法拉第定律描述了感应电动势以及通过感应一个电流来求感应电动势的方法。

因此结论是当磁通量或磁场随时间变化时，就会产生电动势”。

# 互感

互感是电机、变压器、发电机和任何其他与另一个磁场相互作用的电气部件的基本工作原理。那么我们可以将互感定义为一个线圈中的电流在相邻线圈中感应出电动势。
因此，互感被定义为两个线圈的一种特性，凭借这种特性，每个线圈通过感应自身的电动势来对抗流经另一个线圈的电流强度的变化。(或者简单地说，每当与一个线圈相关联的磁通量发生变化时，相邻线圈中就会感应出电动势。)

![](img/5c57e5817ef77a743ccaa9ecfbc47490.png)

From: [https://circuitglobe.com/](https://circuitglobe.com/what-is-faradays-law-of-electromagnetic-induction.html)

如果一个线圈非常靠近另一个线圈，那么几乎所有由第一个线圈产生的磁通量都将与第二个线圈的线圈匝相互作用，从而感应出相对较大的电动势，并因此产生较大的互感值。

如果线圈之间的距离相当大，来自初级线圈的少量磁通量
将与次级线圈的线圈匝
连接，在次级线圈中感应出一个小的电动势。

# 无线充电的概念:

与无线充电过程相关的步骤有:

让我们将完整的充电过程分成两个电路，即:
**发射器电路
接收器电路**

发射器电路的作用是将接收到的电压转换成高频交流电。在发射器电路产生高频电流后，它被馈送到该电路中的发射线圈。当高频交流电通过线圈释放时，它在线圈中感应出磁场，根据电磁感应定律，线圈现在作为电磁体工作。现在，随着一个线圈中的磁场发生变化，如果另一个线圈放置在足够近的距离内，相邻线圈中将感应出电动势。交流电在发射线圈中感应出交变磁通，发射线圈在磁芯中感应出交变磁通。当磁芯延伸穿过次级线圈时，一些磁通量也与次级线圈相连。现在，同样的反向现象将再次发生，根据法拉第感应定律，接收器线圈中的感应磁场将在接收器电路中产生交流电。因此，能量通过感应或耦合从发射器电路传输到接收电路。现在，在最后一步中，感应交流电通过一系列滤波器和整流器转换成所需的 DC 电压。最后将稳定的电流输入电池进行充电。因此，以这种方式进行无线充电。

标准无线电源技术:
当我们谈到无线充电技术时，市场上有两种最常见的技术。它们是:无线电力联盟(WPC)和电力事务联盟(PMA)。无线技术进入市场已有十年，为了让市场消费者使用这项技术，2008 年成立了无线电源联盟(WPC ),以规范无线充电解决方案的开发。之后，PMA 于 2012 年推出，以达到同样的目的。
PMA 和 WPC 是类似的技术，基于相同的磁感应原理工作，但在操作频率和不同的连接协议上有所不同。

![](img/6590c388be4c543998275f1858252174.png)

From: [https://www.idt.com/products/power-management/wireless-power/introduction-to-wireless-battery-charging](https://www.idt.com/products/power-management/wireless-power/introduction-to-wireless-battery-charging)

![](img/f555ee18391937885004cc267e6561b8.png)

From: [http://techlife.samsung.com/6-times-wireless-charging-comes-handy-1557.html](http://techlife.samsung.com/6-times-wireless-charging-comes-handy-1557.html)

概述:
谈 WPC 收费标准，是一个开放的会员组织，维护收费标准；其中一个就是齐标准。Qi 标准是最常见的标准，占市场标准的 90%以上，可用于许多移动设备和市场领导者，如三星、HTC、诺基亚和苹果手机。
通过 Qi 标准充电的设备需要与充电电源进行物理连接。Qi 技术目前支持 5 毫米距离内高达 5W 的无线功率传输，但它正在开发中，可在更远的距离内提供高达 15 W 的功率，此后可达到 120 W。

在 Qi 标准中，要求设备和充电电源之间有物理连接。也称为基站的源向移动设备提供感应功率。基站由产生交变电动势的发射器组成，移动设备包含具有嵌入其中的接收器线圈的接收器电路。下一步是交流电动势通过互感在接收器线圈中感应出电流。此外，Qi 技术通过使用站和设备之间的谐振电感来工作。

工作频率为 100–200 千赫。基于类似的原理，PMA 技术基于相同的感应原理工作，但是工作在不同的频率范围(通常是 Qi 标准的两倍)。最近几天，PMA 和 A4WP 签署了一项协议，建立一个合并的标准(现在的空气燃料联盟)。这项技术基于一种不同的原理，称为
磁共振(MR)。在早期阶段，标准允许功率传输为 3.5 W 和 6.5 W，但最近已增加到 50 W。由于这两种技术都基于磁耦合，但 A4WP 由耦合更松散、调谐更紧密的接收器和发射器线圈组成，具有非常高的 Q(品质因数)。因此，空气-燃料在发射器到接收器的物理放置方面提供了更大的灵活性。

**感应与谐振充电技术** :
以上讨论的无线充电标准适用于感应和谐振技术。感应技术是 Qi 标准在充电方面主要使用的合规类型。这种技术使用紧密耦合的线圈，并使用低频谐振回路仅在非常短的距离内传输功率。电力传输的距离小于 10 毫米。2009 年，最初，当齐标准使其出现在消费市场。那时的功率需求被认为是非常低的(大约 5 W)。随着时间的推移，2012 年通过 Qi 标准的功率输送能力增加到 15W 能力(“中等功率”)。实验结果和测试证实，Soon Qi 技术的目标是 100W 功率传输。

通过非常短的距离传输电力的缺点被另一种无线电力技术谐振所克服，谐振被认为是一种松散耦合的解决方案。通过这项技术，我们可以远距离传输电力(比电感耦合大很多倍)。共振技术的工作频率高于感应技术。此外，谐振技术的另一个优势是能够以 22W 为多个设备充电。磁共振耦合通常在兆赫频谱中，品质因数通常很高。随着充电范围的增加，高品质因数有助于缓解耦合效率以及充电效率的急剧下降。

![](img/b2409a503ef283501ac38cdfc5a79b5f.png)

From: [http://wirelesspowerrenaissance.blogspot.in/2014/05/ieee-p21001-a4wp-pma-wpc.html](http://wirelesspowerrenaissance.blogspot.in/2014/05/ieee-p21001-a4wp-pma-wpc.html)

![](img/41e29d9b7bed486c292787fc9a60a80d.png)

From: [www.mediatek.com](http://www.mediatek.com)

# 市场上的无线充电器:

**摩尔菲无线充电底座** :
这款充电器是专为 iPhone 型号特别是 iPhone 8 和 x 设计的。这款无线充电器非常便携，外形非常小巧，尺寸为 0.45 x 3.82 x 3.82 英寸，重量仅为 4.37 盎司。这种无线充电站可以很容易地存放在背包或手提箱中。该充电器旨在为您的 IOS 设备快速充电。这是一款 Qi 标准充电器，具有圆盘形状和橡胶表面，可防止其在光滑表面上打滑。摩尔菲充电器是市场上最节能的充电器，能够以高于平均功率的 7.5 W 为苹果设备充电。当此充电底座连接到您的设备时，嵌入此充电器的智能充电电路会与您的设备通信，以确定安全快速充电所需的正确电量
。故障安全电路可以防止过度充电，为了防止过热，它会智能地控制温度。

一些可区分的特征是:
超快速响应时间:设备一接触就立即开始充电。
低待机电流:该功能确保空闲时功耗最小。
异物检测:智能地与附近的设备通信，确保电源只发送到兼容的无线设备(Qi 标准设备)。

功率输出 7.5W

标准 Qi
尺寸 0.45 英寸 x 3.82 英寸
重量 4.37 克(124 克)
含线缆:是
含交流适配器:是

![](img/b2edcc299a147932f7b93013ee42a1a7.png)

From: [http://www.macotakara.jp/blog/accessories/entry-33405.html](http://www.macotakara.jp/blog/accessories/entry-33405.html)

**Ravpower 的无线快速充电板:**
这款充电器可以与 Android 平台、智能手表等各种设备配合使用。它也是基于 Qi 的充电器，可以输出 10W 的最大功率
。除了无线充电器，RavPower 的充电板还可以用作 USB 充电器，支持高通快速充电 3.0。此外，快速充电适配器(Quick Charge 3.0)与前述无线充电器捆绑在一起，能够提供 24W 的功率。除了这款设备的吸引力之外，它还有一个智能指示器，可以通知您当前的电池状态，同时内置的保护功能，如过电流、过压和过热，可以确保您的手机和设备得到保护。毫无疑问，在 50 美元的竞争价格，这是最快和最物有所值的无线充电器之一。
功率输出 10 W
标准 Qi
尺寸 3.54″ x 0.62″
重量 NA
线缆含:是
交流适配器含:是

![](img/f8bf7ef9236ceaec594ea13c24e9ae68.png)

From: [https://www.ravpower.com/RAVPower-wireless-charger-quick-charger-QC-adapter.html](https://www.ravpower.com/RAVPower-wireless-charger-quick-charger-QC-adapter.html)

**BELKIN BOOST↑UP 无线充电板**:
BELKIN 充电板专为苹果设备设计，荣获 2018 年度创新大奖。Belkin 与苹果公司密切合作，为 iPhone X、iPhone 8 等苹果设备制造无线充电技术。
一些关键特征是-
1 .贝尔金与苹果公司密切合作，为 iPhone X、iPhone 8
Plus 和 iPhone 8 设计了充电板。新 iphone 的技术非常好，
你的手机不会过热或意外关机。这款充电器的
功率为 7.5W。7.5W BOOST↑UP 无线
充电板能够比标准的 5W
充电器更快地充电，让您可以继续探索您的手机，而没有频繁充电的
麻烦。
1。当您的
手机正确对准面板并充电时，稳定的绿色 LED 灯会给出一个完美的指示。当绿灯出现时，你可以知道你的 iPhone X 会自动充电并为你准备好，继续你的一天。

2.一些金属物体，如钥匙和硬币，放置在充电板上或近距离内，会使您的手机远离充电，并干扰充电功能，甚至会损坏 iPhone 或充电板。为了保护您的设备，BOOST↑UP 无线充电板具有一个智能指示器，当检测到异物或您的手机未正确对齐时，它会向您发出警告。
功率输出 7.5
标准 Qi
尺寸 7.5″ x 1.75″ x 5.5″
重量 NA
线缆包含在内？是包括交流适配器吗？是

![](img/f5f861acdc9cdf3730b06a75bc131d42.png)

From: [http://www.belkin.com/us/p/P-F7U027/](http://www.belkin.com/us/p/P-F7U027/)

![](img/dbab3766d8fdb1150a0f834c97642647.png)

[http://www.belkin.com/us/p/P-F7U014/](http://www.belkin.com/us/p/P-F7U014/)

**槽制无线充电垫** :
这款充电器配有不锈钢底座和类似木塞的充电垫。就其设计和外形而言，它确实是市场上的最佳选择之一。这款充电器采用 Qi 技术，兼容所有 Qi 供电设备。

功率输出 7.5W
标准 Qi
尺寸 0.45″ x 3.82″
重量 4.37g (124g)
含线缆:是
含交流适配器:是

![](img/b490e380c20a02cf395049e598d88ebc.png)

from: [https://grovemade.com/product/wireless-charging-pad-light](https://grovemade.com/product/wireless-charging-pad-light)

# 无线电池充电的优势:

无线充电的主要优势在于，它提供了一种为电子设备充电的安全方式，并且由于消除了连接电缆的麻烦而提高了用户友好性。所以，你不需要担心你的线。此外，随着共振磁耦合和 A4WP 技术的进步，不同品牌和不同型号的设备也可以使用相同的充电器。我们可能有不同的电器与同一根 USB 线不兼容，但无线充电器可以用于所有的手机和其他设备。所以单个充电器可以支持多台设备充电。下一个优点是，它为非接触式设备提供了更好的产品耐用性(例如，防水和防尘)。由于无线充电技术是一个无接触的过程，设备的磨损可以忽略不计。无线充电是一个高能效的过程，因为充电器以按需方式提供充电设备所请求的电力。此外，随着市场上智能充电器的出现，加热效果和充电时间明显减少。

![](img/a97c70f80fcea35bda087eefd44a935d.png)

From: [https://grovemade.com/product/wireless-charging-pad-light](https://grovemade.com/product/wireless-charging-pad-light)

# 缺点:

我们知道，在通过感应充电时，能量通过自由空间传递，因此与传统充电器相比，这些充电器的效率相对较低。通过无线充电实现的平均传输效率约为 70%。
由于能量在传输过程中损失，这实际上使充电过程变得更慢。与常规充电相比，无线充电器产生的热量非常大。
无线充电器向太空发射电磁波，需要更仔细地研究它们对健康的影响。
无线充电器实际上并不是真正的无线充电器，要为设备充电，您需要将充电器插入电源，这使其成为非便携式设备。

![](img/2a8a418336e93f29ad201714fe1d411a.png)

**参考文献** :
一、[https://en.wikipedia.org/wiki/Inductive_charging](https://en.wikipedia.org/wiki/Inductive_charging)二、
二。[https://www.electronicshub.org/wireless-mobile-](https://www.electronicshub.org/wireless-mobile-)电池-充电器-电路/
三。[https://thewirecutter.com/blog/](https://thewirecutter.com/blog/)IV
。[http://www.techradar.com/news/best-wireless-](http://www.techradar.com/news/best-wireless-)充电器
五、[https://byjus.com/physics/faradays-law/](https://byjus.com/physics/faradays-law/)
六。[https://www . the guardian . com/technology/2017/sep/13/apple-iphone-](https://www.theguardian.com/technology/2017/sep/13/apple-iphone-)8-iphone-x-
what-is-wireless-charging-do-I-need-it
七、[https://en . Wikipedia . org/wiki/Qi _(标准)](https://en.wikipedia.org/wiki/Qi_(standard))
八。[https://www.androidauthority.com/wireless-charging-](https://www.androidauthority.com/wireless-charging-)

— -

**关于**:

Alok Parmar 先生作为公民科学家与 Khurana 博士一起工作。

LinkedIn 账户—[https://www.linkedin.com/in/alok-parmar-3412ba57](https://www.linkedin.com/in/alok-parmar-3412ba57)

https://m.facebook.com/alok.parmar1?ref=bookmarks 脸书账户—

Sukant Khurana 博士经营着一个学术研究实验室和几家科技公司。他也是著名的艺术家、作家和演说家。你可以在 www.brainnart.com[或 www.dataisnotjustdata.com](http://www.brainnart.com)[了解更多关于苏坎特的信息，如果你希望从事生物医学研究、神经科学、可持续发展、人工智能或数据科学项目，为公众谋福利，你可以在 skgroup.iiserk@gmail.com 联系他，或者通过 LinkedIn](http://www.dataisnotjustdata.com)[https://www.linkedin.com/in/sukant-khurana-755a2343/](https://www.linkedin.com/in/sukant-khurana-755a2343/)联系他。

[](https://twitter.com/Sukant_Khurana) [## Sukant khu Rana(@ Sukant _ khu Rana)|推特

### Sukant Khurana 的最新推文(@Sukant_Khurana)。创始人:https://t.co/WINhSDEuW0 和 3 家生物技术创业公司…

twitter.com](https://twitter.com/Sukant_Khurana) ![](img/731acf26f5d44fdc58d99a6388fe935d.png)

## 这篇文章发表在《创业公司》杂志上，这是 Medium 最大的创业刊物，有 300，118 人关注。

## 订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)