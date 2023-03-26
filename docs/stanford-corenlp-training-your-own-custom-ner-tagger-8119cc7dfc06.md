# 斯坦福 CoreNLP:训练你自己的定制 NER tagger。

> 原文：<https://medium.com/swlh/stanford-corenlp-training-your-own-custom-ner-tagger-8119cc7dfc06>

![](img/c60e0c4d28ccee7fd07bd872febebe7c.png)

## Java 中的一个端到端的例子，使用你自己的数据集来训练一个定制的 NER 标记器。

斯坦福核心 NLP 是迄今为止最久经考验的 NLP 库。在某种程度上，它是当今 NLP 性能的黄金标准。在各种其他功能中，命名实体识别(NER)在库中得到支持，它允许在一段文本中标记重要的实体，如人名、地名等。

核心的自然语言处理 NER 标记器实现了条件随机场算法，这是解决自然语言处理中 NER 问题的最好方法之一。该算法在标记数据集上训练，输出是学习模型。

# 预训练模型

基本上，该模型学习训练数据中的信息和结构，并可以使用这些信息和结构来标记看不见的文本。CoreNLP 附带了一些预训练的模型，如英语模型，这些模型被训练成用于检测姓名、地点等的结构化英语文本。

# 训练你自己的模型

但是，如果您的领域或用例中的文本与构建预训练模型的领域不重叠，那么预训练模型可能不太适合您。在这种情况下，您可以选择构建自己的训练数据，并为您的用例训练一个自定义模型。

我们将展示如何使用 NER 标记器来学习电子商务搜索查询中的实体。

在此获取在[下使用的数据集。](https://dataturks.com/projects/Mohan/Best%20Buy%20E-commerce%20NER%20dataset)

# 训练数据格式

训练数据作为文本文件传递，其中每行是一个单词-标签对。该行中的每个单词都应该以类似“word\tLABEL”的格式进行标记，单词和标签名称由制表符“\t”分隔。对于一个文本句子，我们应该将它分解成单词，并在训练文件中为每个单词添加一行。为了标记下一行的开始，我们在训练文件中添加一个空行。

以下是输入培训文件的示例:

```
hp	Brand
spectre	ModelName
x360	ModelNamehome	Category
theater	Category
system	0horizon	ModelName
zero	ModelName
dawn	ModelName
ps4	0hoverboard	Category
```

注意:每个单词都需要一个标签。这里，对于我们不关心的单词，我们使用标签 0。

# 构建训练数据集

根据您的领域，您可以自动或手动构建这样的数据集。手动构建这样的数据集可能非常痛苦，像 [Dataturks NER tagger](https://dataturks.com/projects/Dataturks/Demo%20POS%20Tagging%20Project) 这样的工具可以帮助简化这个过程。

# 火车模型

这里重要的类是`CRFClassifier`，它保存实际的模型。下面是从训练数据文件构建模型并在文件中输出模型的代码。

```
public void trainAndWrite(String modelOutPath, String prop, String trainingFilepath) {
   Properties props = StringUtils.propFileToProperties(prop);
   props.setProperty("serializeTo", modelOutPath); //if input use that, else use from properties file.
   if (trainingFilepath != null) {
       props.setProperty("trainFile", trainingFilepath);
   } SeqClassifierFlags flags = new SeqClassifierFlags(props);
   CRFClassifier<CoreLabel> crf = new CRFClassifier<>(flags);
   crf.train(); crf.serializeClassifier(modelOutPath);
}
```

# 属性文件

CoreNLP 使用一个属性文件，我们可以在其中定义如何构建定制模型的参数。例如，我们可以定义如何构建要学习的特征等。下面是一个示例属性文件:

```
# location of the training file
trainFile = ./standford_train.txt
# location where you would like to save (serialize) your
# classifier; adding .gz at the end automatically gzips the file,
# making it smaller, and faster to load
serializeTo = ner-model.ser.gz# structure of your training file; this tells the classifier that
# the word is in column 0 and the correct answer is in column 1
map = word=0,answer=1# This specifies the order of the CRF: order 1 means that features
# apply at most to a class pair of previous class and current class
# or current class and next class.
maxLeft=1# these are the features we'd like to train with
# some are discussed below, the rest can be
# understood by looking at NERFeatureFactory
useClassFeature=true
useWord=true
# word character ngrams will be included up to length 6 as prefixes
# and suffixes only
useNGrams=true
noMidNGrams=true
maxNGramLeng=6
usePrev=true
useNext=true
useDisjunctive=true
useSequences=true
usePrevSequences=true
# the last 4 properties deal with word shape features
useTypeSeqs=true
useTypeSeqs2=true
useTypeySequences=true
#wordShape=chris2useLC
wordShape=none
#useBoundarySequences=true
#useNeighborNGrams=true
#useTaggySequences=true
#printFeatures=true
#saveFeatureIndexToDisk = true
#useObservedSequencesOnly = true
#useWordPairs = true
```

# 从文件中读取模型

由于我们已经将模型保存到一个文件中，现在我们可以加载该模型(或者将它分发给其他人使用):

```
public CRFClassifier getModel(String modelPath) {
    return CRFClassifier.getClassifierNoExceptions(modelPath);
}
```

# 使用模型做标记。

最后，我们可以看到该模型如何用于标记看不见的查询:

```
public void doTagging(CRFClassifier model, String input) {
  input = input.trim();
  System.out.println(input + "=>"  +  model.classifyToString(input));
}
```

这是使用我们的模型的示例输出

```
String[] tests = new String[] {"apple watch", "samsung mobile phones", " lcd 52 inch tv"};
for (String item : tests) {
  doTagging(model, item);
}
```

输出

```
apple watch=>apple/Brand watch/Category
samsung mobile phones=>samsung/Brand mobile/Category phones/Category
lcd 52 inch tv=>lcd/ModelName 52/ModelName inch/0 tv/Category
```

无耻插件:我们是一个数据注释平台，让你建立 ML 数据集超级容易。只需上传数据，邀请您的团队，快速构建数据集。来看看我们吧。

## [数据标注立易](https://dataturks.com/index.php?s=blg)

[![](img/308a8d84fb9b2fab43d66c117fcc4bb4.png)](https://medium.com/swlh)

## 这篇文章发表在《T4》杂志《创业》(The Startup)上，这是 Medium 最大的创业刊物，有 320，924+人关注。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

[![](img/b0164736ea17a63403e660de5dedf91a.png)](https://medium.com/swlh)