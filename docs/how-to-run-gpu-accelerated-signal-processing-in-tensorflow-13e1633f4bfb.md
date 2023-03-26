# 如何在 TensorFlow 中运行 GPU 加速信号处理

> 原文：<https://medium.com/swlh/how-to-run-gpu-accelerated-signal-processing-in-tensorflow-13e1633f4bfb>

![](img/16cd0a0e57685bf90288e56dea598e8a.png)

在 TensorFlow 框架的深处存在一个很少被注意到的模块: [tf.contrib.signal](https://www.tensorflow.org/api_docs/python/tf/contrib/signal) ，它可以帮助为你的 TensorFlow/Keras 模型构建 GPU 加速的音频/信号处理管道。在本帖中，我们将采用一种实用的方法来检验一些最流行的信号处理操作，并将结果可视化。

# 你可以在 [my GitHub](https://github.com/Tony607/tf_audio_signal) 上找到这篇文章的源代码，以及一个可运行的 [Google Colab 笔记本](https://colab.research.google.com/drive/1Adcy25HYC4c9uSBDK9q5_glR246m-TSx)。

# 开始

我们将在 TensorFlow 中构建一个完整的计算图，它采用 wav 文件名并输出 MFCC 特征。有一些中间输出/音频特性可能很有趣，因此我们将启用 TensorFlow eager execution，它允许我们立即评估操作，而无需构建完整的图形。如果你是第一次接触 TensorFlow eager execution，你会发现它比 graph API 更直观。

下面的代码片段将带您开始 TensorFlow 中的热切执行。

# 解码 WAV 文件

`tf.contrib.ffmpeg.decode_audio`依赖于本地安装的 FFmpeg 库来解码音频文件。

要在基于 Linux 的系统上安装 FFmpeg，请运行以下命令。

```
apt update -qq
apt install -y -qq ffmpeg
ffmpeg -version
```

之后，我们可以下载一个小样本的警笛声 wav 文件，用 TensorFlow 解码。

`waveform`是一个张量，在急切执行的帮助下，我们可以立即评估它的值并将其可视化。

![](img/581803e32a12c1875fcc44e9b4265728.png)

A section of the waveform

从原始波形中，我们几乎看不到任何警报声的特征，加上可能有太多的数据直接输入神经网络。接下来的几个步骤将提取音频信号的频域签名。

*Declaimer:Windows 不支持用* `*tf.contrib.ffmpeg*` *解码音频文件。* [*指 https://github.com/tensorflow/tensorflow/issues/8271*](https://github.com/tensorflow/tensorflow/issues/8271)*。*

Windows 上的另一种方法是用 scipy 解码 wav 文件。

# 计算光谱图

光谱图新手？看看酷的 [Chrome 音乐实验室实验](https://musiclab.chromeexperiments.com/Spectrogram/)将你的声音实时可视化为频谱图。

计算光谱图最常用的方法是采用 STFT(短时傅立叶变换)的幅度。

任何音频波形都可以用不同频率、相位和幅度的正弦波的组合来表示。当信号随时间变化时，STFT 可以确定信号本地部分的正弦频率和相位内容。

`tf.contrib.signal.stft`计算`signals`的 STFT。该操作接受一个形状为 ***(批量大小，样本)*** 的张量“信号”。

`stfts`张量具有 ***(batch_size，frames，fft_unique_bins)*** 的形状，每个值包含一个具有实部和虚部的`*a* + *bi*` 形式的复数。

能谱图是复值 STFT 的大小，即`sqrt{a^2 + b^2}`。

在 TensorFlow 中，它可以简单地计算为:

我们可以绘制能量谱图，我们可以发现图像顶部显示的一些模式，其中频率上下波动，类似于警笛声音的音高变化。

![](img/55574f3aabd57704faad9c0ff5ceb40c.png)

Magnitude spectrograms

# 计算梅尔频率倒谱系数

如你所见，在计算出的能量谱图中有 513 个频率组，许多是“空白”的。当处理音频的频谱表示时，Mel 频率倒谱系数(MFCCs)被广泛用于自动语音和说话人识别，这导致音频的较低维度和更感知相关的表示。

我们可以在 TensorFlow 中将能量/星等谱图转换为 Mel 谱图，并像这样绘制其结果。

如果需要，我们可以指定 Mel 频谱中包含的频率的下限和上限。

`**num_mel_bins**`指定生成的 Mel 光谱中有多少个波段。

![](img/d0688f46db1a0091956683fe6ed72e33.png)

Mel-spectrograms

要进一步压缩 Mel 频谱幅度，您可以应用压缩非线性，如对数压缩，这有助于平衡频谱的低能量和高能量区域中细节的重要性，这更符合人类的听觉灵敏度。

`log_offset`是一个小数字，用于避免在极少数情况下将 **log()** 应用于零。

![](img/e3f057563fde2bcaa0efa3a10794a394.png)

Log mel spectrograms

最后一步，`[tf.contrib.signal.mfccs_from_log_mel_spectrograms](https://www.tensorflow.org/api_docs/python/tf/contrib/signal/mfccs_from_log_mel_spectrograms)`根据`log_mel_spectrograms`计算[MFCC](https://en.wikipedia.org/wiki/Mel-frequency_cepstrum)。

![](img/dd1f8b4983b05c32b911f1a21c316205.png)

MFCCs

# 一起构建一切

将所有内容放入 TensorFlow 管道中。

# 结论和进一步阅读

在这篇文章中，我们介绍了如何在 TensorFlow 中进行 GPU 支持的信号处理。我们走过了从解码 WAV 文件到计算波形的 MFCCs 特征的每一步。构建最终管道，您可以应用到现有的 TensorFlow/Keras 模型，以制作端到端的音频处理计算图。

## 一些可能对你有帮助的相关资源。

[梅尔频率倒谱系数(MFCC)教程](http://practicalcryptography.com/miscellaneous/machine-learning/guide-mel-frequency-cepstral-coefficients-mfccs/)

[Chrome 音乐实验室声谱图实验](https://musiclab.chromeexperiments.com/Spectrogram/)

[GitHub](https://github.com/Tony607/tf_audio_signal) 上这篇文章的源代码。

[在 Twitter 上分享](https://twitter.com/intent/tweet?url=https%3A//www.dlology.com/blog/how-to-run-gpu-accelerated-signal-processing-in-tensorflow/&text=How%20to%20run%20GPU%20accelerated%20Signal%20Processing%20in%20TensorFlow) [在脸书分享](https://www.facebook.com/sharer/sharer.php?u=https://www.dlology.com/blog/how-to-run-gpu-accelerated-signal-processing-in-tensorflow/)

*原载于*[*www.dlology.com*](https://www.dlology.com/blog/how-to-run-gpu-accelerated-signal-processing-in-tensorflow/)*。*

[![](img/308a8d84fb9b2fab43d66c117fcc4bb4.png)](https://medium.com/swlh)

## 这篇文章发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，拥有+383，380 名读者。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

[![](img/b0164736ea17a63403e660de5dedf91a.png)](https://medium.com/swlh)