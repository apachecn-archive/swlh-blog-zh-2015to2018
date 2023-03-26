# VMware 进军边缘计算

> 原文：<https://medium.com/swlh/vmware-moves-into-edge-computing-20e46e8c047d>

![](img/c55a4b795539832a72673752ad84e0de.png)

上周在 VMworld 2018 上最令人兴奋的发现之一是 [VMware 向物联网设备](https://blogs.vmware.com/vsphere/2018/08/introducing-project-dimension.html)提供云的未来愿景，或者更一般地说，向所谓的边缘设备提供云。

据广泛预测，在不久的将来，连接到互联网的边缘设备将无处不在。据估计，在未来 3-5 年内，边缘设备市场将以每年 30%的复合增长率增长，到 2022 年，其价值将超过[60 亿美元。这是一个很好的机会，有几个大玩家试图从中分一杯羹。](https://www.marketsandmarkets.com/PressReleases/edge-computing.asp)

# 边缘应用的挑战

边缘的现代机器学习应用程序，如机器人、智能家居和自动驾驶汽车，无法将所有计算密集型处理卸载到云，这有几个原因。

## 大规模生成的数据

大多数边缘设备至少由传感器组成，这些传感器测量现实世界的一些属性并生成非结构化数据。这是每秒钟的海量数据—想象一下足球场上的一组安全摄像机，它们试图模拟和识别可疑活动。将所有这些数据上传到云中进行处理，在带宽和其他成本方面都非常昂贵。

## 实时决策

一些边缘设备，如农田传感器，只能测量和监控。但是在很多应用中，设备需要做出实时决策并采取行动。这些应用程序会受到将数据上传到云以进行决策的网络延迟成本的负面影响。

## 到云的间歇性连接

该设备需要能够独立运行，无需访问互联网和云。智能汽车可以在没有像样互联网连接的地区行驶，但在路上不能停止运行。

# 项目维度

VMware 正在进行一个项目，旨在提供一种无缝、统一的方法来解决边缘问题。

## 将边缘集成到云计算环境中

借助 AWS 上的 VMware Cloud 和客户内部数据中心上的 vSphere，他们已经在为客户的云计算环境提供单一控制台界面和管理平台方面取得了进展。客户现在只需登录他们的 VMC 控制台，就可以访问他们所有的软件定义的数据中心(SDDCs)，他们可以监控运行状况、管理资源分配、部署主机，并利用他们所了解和喜爱的 vSphere 的操作一致性做各种事情。Project Dimension 更进一步，将边缘设备集成到这个“云网”中。目标是将客户内部 SDDCs 和 AWS 之间已经存在的操作一致性和兼容性扩展到他们的边缘设备，这些设备将作为虚拟化节点在他们自己的云中公开。

## 硬件即服务

VMware 计划不仅推出软件，还在边缘推出配套硬件。硬件将由 VMware 的技术人员亲手交付和安装。它将自动连接到 VMware Cloud，后者将管理所有基础架构软件更新和固件升级的部署。这种超融合基础架构不仅能使边缘设备高度优化，还能使故障排除变得更加容易，从而使 VMware 工程师和支持人员能够提供更快、更好的支持。

## 利用值得信赖的平台 vSphere

VMware 在边缘领域拥有巨大商机的一个原因是，它可以利用其 vSphere 软件堆栈，而不是构建自己的全新虚拟化和管理堆栈。vSphere 进入市场已近十年，在此期间经历了一系列迭代改进，以满足客户需求。在多次客户互动后，错误已得到修复，性能问题已得到解决，功能已得到优先考虑。vSphere 不仅作为一项技术已经成熟，还赢得了成千上万客户的宝贵信任，使其成为边缘计算早期采用者的绝佳候选。这还意味着 VMware 可以利用已经融入 vSphere 平台的安全性、隔离和性能原语，从而大大简化上市策略。

# 来自其他大玩家的竞争

## 微软 Azure

微软 Azure 的 Venkat Yalla 在软件工程日报的这一期精彩节目中谈论他们的边缘平台架构[。他们的想法是，有理由假设边缘设备将由运行 linux 的服务器级或至少桌面级机器组成。他描述了一种架构，该架构利用 Kubernetes 将边缘节点作为这些机器上的容器来编排部署和管理。除了上面讨论的内容之外，他们面向客户的主要价值主张是:](https://softwareengineeringdaily.com/2018/07/30/edge-kubernetes-with-venkat-yalla/)

1.  简单的部署界面
2.  用于设置和管理的 K8s APIs
3.  一键式将代码部署到边缘
4.  节点的自动调度和扩展

一个重要的面向内部的价值主张是，通过利用 Kubernetes 和他们自己已经存在的虚拟 Kubelet 来进行调度和其他任务，所产生的开发成本会大幅降低，从而严重影响他们的上市策略和迭代能力。

## 自动警报系统

通过他们占主导地位的无服务器模型， [AWS Greengrass](https://aws.amazon.com/greengrass/) 客户可以建立他们的边缘计算环境，并编写 Lambda 函数来运行他们希望在边缘节点执行的业务逻辑。虽然这带来了供应商锁定的负面影响，但 AWS 公共云用户可以在边缘使用丰富的云服务。由于大多数边缘应用程序预计将使用某种机器学习， [AWS SageMaker](https://aws.amazon.com/blogs/aws/new-machine-learning-inference-at-the-edge-using-aws-greengrass) 可由部署到边缘的代码直接使用。

其他重要的参与者，如 Nutanix，也在进军这一不远的未来愿景，即边缘设备运行基于机器学习的应用程序的工作负载。

# VMware 的独特优势:独立于云的方法

那么，VMware 的最大优势是什么？如果 Project Dimension 执行得很好，并且在多个公共云 IaaS 提供商产品中可用，他们的云提供商不可知方法可能会使他们与众不同。供应商锁定的威胁仍然是市场感到厌倦的一个问题，消除这一棘手问题可能是企业采用这一新技术的一个重要因素。

# 喜欢这个帖子？

在 https://ambidextrouspm.com 的[订阅更多双周 PM 帖子。我试图打破商业模式，挑战现状，并讨论 PM 最佳实践。](https://ambidextrouspm.com)

*原载于 2018 年 9 月 12 日*[*ambidextrouspm.com*](https://ambidextrouspm.com/vmware-moves-into-edge-computing/)*。*

[![](img/308a8d84fb9b2fab43d66c117fcc4bb4.png)](https://medium.com/swlh)

## 这篇文章发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，拥有+368，954 名读者。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

[![](img/b0164736ea17a63403e660de5dedf91a.png)](https://medium.com/swlh)