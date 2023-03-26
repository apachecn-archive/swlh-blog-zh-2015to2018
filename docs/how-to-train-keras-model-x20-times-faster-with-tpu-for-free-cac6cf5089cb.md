# 如何免费用 TPU 训练 Keras 车型速度快 20 倍

> 原文：<https://medium.com/swlh/how-to-train-keras-model-x20-times-faster-with-tpu-for-free-cac6cf5089cb>

![](img/5ff3e377aa5a009b611bf4eb9a16d09b.png)

在相当长的一段时间里，我对在单个 GTX 1070 显卡上训练我的模型感到满意，该显卡的单次精度约为 8.18 TFlops，然后谷歌在 Colab 上开放了免费的 Tesla K80 GPU，该 GPU 配有 12GB RAM，额定速度略快于 8.73 TFlops。直到最近，具有 180 TFlops 的云 TPU 选项才在 Colab 的运行时类型选择器中弹出。在这个快速教程中，您将学习如何将您现有的 Keras 模型转化为 TPU 模型，并在 Colab x20 上进行训练，与在我的 GTX1070 上进行免费训练相比，速度更快。

我们将构建一个易于理解但足够复杂的 Keras 模型，以便我们可以稍微预热一下云 TPU。在 IMDB 情感分类任务上训练 LSTM 模型可能是一个很好的例子，因为训练 LSTM 可能比其他层(如密集层和卷积层)在计算上更昂贵。

工作流程的概述，

*   构建一个 Keras 模型，用于使用静态输入`batch_size`进行函数式 API 的培训。
*   将 Keras 模型转换为 TPU 模型。
*   用静态`batch_size * 8`训练 TPU 模型并将权重保存到文件中。
*   构建一个 Keras 模型进行推理，具有相同的结构，但批量输入大小可变。
*   加载模型重量。
*   使用推理模型进行预测。

## 你可以一边阅读一边玩 Colab Jupyter 笔记本— [Keras_LSTM_TPU.ipynb](https://colab.research.google.com/drive/1QZf1WeX3EQqBLeFeT4utFKBqq-ogG1FN) 。

首先，按照下图中的说明在 Colab 运行时激活 TPU。

![](img/be099b2e5f07a92da959391ed9f838ea.png)

Activate TPU

# 静态输入批量

在 CPU 和 GPU 上运行的输入管道大多不受静态形状要求的约束，而在 XLA/TPU 环境中，静态形状和批量大小是必须的。

can TPU 包含 8 个 TPU 内核，作为独立的处理单元运行。除非使用全部八个内核，否则 TPU 不会得到充分利用。为了充分加快矢量化的训练速度，与在单个 GPU 上训练相同的模型相比，我们可以选择更大的批量。总批量大小为 1024(每个内核 128)通常是一个好的起点。

如果您要训练一个批量过大的较大模型，请尝试慢慢减少批量，直到它适合 TPU 内存，只是要确保总批量是 64 的倍数(每个内核的批量应该是 8 的倍数)。

在批量较大的训练时也值得一提；提高优化器的学习速度以允许更快的收敛通常是安全的。你可以在本文中找到一个参考——“[精准，大迷你批量 SGD:1 小时训练 ImageNet](https://arxiv.org/pdf/1706.02677.pdf)”。

在 Keras 中，为了定义静态批量大小，我们使用其函数 API，然后为输入层指定`batch_size`参数。请注意，该模型构建在一个采用`batch_size`参数的函数中，因此我们可以稍后回来创建另一个在 CPU 或 GPU 上运行的推理模型，该模型采用可变的批处理大小输入。

此外，使用`tf.train.Optimizer`代替标准的 Keras 优化器，因为 Keras 优化器对 TPU 的支持仍处于试验阶段。

# 将 Keras 模型转换为 TPU 模型

`tf.contrib.tpu.keras_to_tpu_model`功能将`tf.keras`模型转换成等效的 TPU 版本。

然后，我们使用标准的 Keras 方法来训练、保存权重和评估模型。请注意，`batch_size`设置为模型输入`batch_size`的八倍，因为输入样本均匀分布在 8 个 TPU 内核上运行。

我设置了一个实验来比较在我的 Windows PC 上运行的单个 GTX1070 和在 Colab 上运行的 TPU 之间的训练速度，下面是结果。

GPU 和 TPU 都采用 128 的输入批量，

GPU: **每历元 179 秒**。20 个时期达到 76.9%的验证准确度，总共 3600 秒。

TPU: **每个时段 5 秒**除了第一个时段用了 49 秒。20 个时期达到 95.2%的验证准确度，总共 150 秒。

20 个历元后 TPU 的验证精度高于 GPU 可能是由于一次训练 8 批 128 个样本的小批量造成的。

# CPU 上的推理

一旦我们有了模型权重，我们就可以像往常一样加载它，并在另一个设备(如 CPU 或 GPU)上进行预测。我们还希望推理模型接受灵活的输入批量，这可以通过前面的`make_model()`函数来实现。

您可以看到推理模型现在采用可变的输入样本，

```
_________________________________________________________________
Layer (type) Output Shape Param # 
=================================================================
Input (InputLayer) (None, 500) 0 
_________________________________________________________________
Embedding (Embedding) (None, 500, 128) 1280000 
_________________________________________________________________
LSTM (LSTM) (None, 32) 20608 
_________________________________________________________________
Output (Dense) (None, 1) 33 
=================================================================
```

然后，您可以在推理模型中使用标准的`fit()`、`evaluate()`函数。

# 结论和进一步阅读

这个快速教程向您展示了如何利用 Google Colab 上的免费云 TPU 资源更快地训练 Keras 模型。

[云 TPU 文档](https://cloud.google.com/tpu/docs/)

[云 TPU 性能指南](https://cloud.google.com/tpu/docs/performance-guide)

[云 TPU 故障排除指南](https://cloud.google.com/tpu/docs/troubleshooting)

[XLA 概述](https://www.tensorflow.org/performance/xla/)

[在 Twitter 上分享](https://twitter.com/intent/tweet?url=https%3A//www.dlology.com/blog/how-to-train-keras-model-x20-times-faster-with-tpu-for-free/&text=How%20to%20train%20Keras%20model%20x20%20times%20faster%20with%20TPU%20for%20free) [在脸书分享](https://www.facebook.com/sharer/sharer.php?u=https://www.dlology.com/blog/how-to-train-keras-model-x20-times-faster-with-tpu-for-free/)

【www.dlology.com】最初发表于[](https://www.dlology.com/blog/how-to-train-keras-model-x20-times-faster-with-tpu-for-free/)**。**

*[![](img/308a8d84fb9b2fab43d66c117fcc4bb4.png)](https://medium.com/swlh)*

## *这篇文章发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，拥有+ 378，907 读者。*

## *在此订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。*

*[![](img/b0164736ea17a63403e660de5dedf91a.png)](https://medium.com/swlh)*