# 使用 Python 的 AWS Lambdas 指南，由 API 调用触发

> 原文：<https://medium.com/swlh/a-guide-to-aws-lambdas-using-python-triggered-by-an-api-call-1e768edd13c5>

![](img/b6a7a7b8d1f8f49b7ccae387750e4699.png)

Let’s pretend that this is a relevant image

无服务器计算一直是最近讨论的话题。无服务器计算是服务器、操作系统和基础设施的抽象，同时保留核心功能-计算。无服务器计算有其自身的优势。开发人员不必担心在实际使用它们的功能之前设置整个服务器。此外，与基于时间的计费相比，某些应用程序更适合基于计算的计费。兰姆达斯有助于实现这一点。简而言之，lambdas 是只被分配一项任务的孤立功能。使用这种类型的体系结构的其他一些优点是可伸缩性和无障碍的资源分配。所有主要的云服务提供商( [AWS](https://aws.amazon.com/lambda/) 、 [GCP](https://cloud.google.com/functions/) )都提供 lambda 功能。下面是在 AWS 中创建基本 python lambda 的指南。此外，还有一个使用 API 调用触发这个 lambda 的示例代码，这是最常见的请求类型。

以下是我们将遵循的步骤:

*   λ创建
*   Lambda 部署
*   API 网关的配置

*本指南假定您有一个活跃的 AWS 帐户和一定的耐心。*

# λ创建

一个简单的 lambda 应该是这样的:

```
def lambda_handler(event, context):
    #lambda function here
    ...

    return { 'status' : 200, 'body' : 'Lambda executed successfully!' }
```

这个方法会放入一个入口点，姑且称之为 *main* .py，以后记住。

以下摘自官方[文件](https://docs.aws.amazon.com/lambda/latest/dg/python-programming-model-handler-types.html):

*   `event`–AWS Lambda 使用此参数将**事件数据**传递给处理程序。这个参数通常是 Python `dict`类型的。也可以是`list`、`str`、`int`、`float`或`NoneType`型。
*   `context`–AWS Lambda 使用此参数向您的处理程序提供**运行时信息**。该参数属于`LambdaContext`类型。

**处理额外的依赖关系**

Lambdas 托管在已经安装了基本软件包的 Linux 服务器上。所有附加的依赖项都必须以固定的格式明确地放入部署包中，这将在下面描述。

为了使这个过程顺利进行，为特定的项目建立一个虚拟环境。要创建一个部署包，创建一个 zip 文件，在 zip 文件的根层有一个主入口点文件`main.py`。额外的文件夹和文件可以以你认为合适的任何格式存在于 zip 中。**确保你的项目中没有绝对路径。**

它应该是这样的:

lambda-test.zip/
├──main . py(lambda 入口点包含 lambda_handler 方法
├──folder 1/
│├──file 1
│├──file 2
│├──some _ method . py
│└──docs
├──some other folder/
│├─file 1
└─docs
└─package 1
╸─package 2【2】

**添加依赖关系**:将`venv/lib/python2.7/site-packages/` 中的所有文件和文件夹复制到 zip 的根目录下(上图中的 packageX)。这里的`venv`是项目的虚拟环境文件夹。遵守亚马逊设定的[尺寸限制](https://docs.aws.amazon.com/lambda/latest/dg/limits.html)。让我们称这个压缩包为`lambda-test.zip`

# Lambda 部署

掰指关节，这很讨厌。

*   登录您的 AWS 帐户。在服务下，转到 *lambdas* 。创建一个新函数，姑且称之为`test`，将运行时改为`Python2.7`，并给它分配一个合适的角色。检查右上方的 lambda 区域。假设是这样的:

```
**ARN** - arn:aws:lambda:us-east-1:xxx:function:test
```

稍后我们需要记住的地区:`us-east-1`

*   从左侧菜单中添加一个触发器`API gateway`。在其配置中，创建一个新的 API。让安全系统暂时打开。在折叠的下拉菜单中命名该 API。添加并保存触发器。

**代码**

*   点击中间的功能`test`。有一个在线编辑代码的选项，但这适用于较小的项目。我们将使用我们的部署包。要使用它，去 **S3** 创建一个新的桶。**确保桶区域与拉姆达区域** `us-east-1` **相同。** *我花了很多时间才弄明白这个，别在这上面浪费时间了！*在这个桶中上传您的部署包`lambda-test.zip`并获得 zip 的链接。确保铲斗具有必要的安全参数。
*   回到 lambda 仪表板，将此链接粘贴到`code entry type`**-**-`Upload a zip from Amazon S3.`确保运行时是 Python2.7，处理程序设置为`main.lambda_handler.` 根据需要调整下面设置中的超时。处理时间短的应用程序不应被分配很长的超时时间。记住，我们是横向扩展，按计算能力付费。我浪费了更多的时间去想为什么我的请求会超时。你不应该。救人而不犯错误，值得庆幸。

# 配置 API 网关

*   在 lambda 仪表板上选择 API gateway。并进入**API 创建**、**、`test.`**

**在你的 API `test`中，创建一个新的资源——姑且称之为`number` ***。*** 中的`number`，做:**

1.  **`Actions` — `Enable CORS`:默认设置。**
2.  **`Actions` — `Create method` ( `GET`测试方法):勾选`Use Lambda Proxy integration`，同时添加 lambda 函数名`test`。**
3.  **点击这个*刚被*创建的`number`的 GET 方法，然后点击被测螺栓图标。您可以在这里进行模拟测试。如果一切顺利，您应该会在右侧的`Response Body`下看到以下内容。**

```
{
  "body": "Lambda executed successfully!",
  "status": 200
}
```

****注意** : `test` 是 API 套件。*`number`*就是那个套件里的一个资源。*`GET`*是那个套件中那个资源的一个方法。而`life` 是个谜。******

*****你的 lambda 现在可以运行了！*****

*****在结束之前，我将向您展示最后一样东西，从`GET`调用中获取一个参数。为此，请按照下列步骤操作:*****

*   *****转到`number`*的`GET`方法，点击`Method Request`。******
*   ****在`URL Query String Parameters`下，添加查询字符串，比如说`input`。`input`是我们将从`GET`调用中获得的参数。您可以选择强制执行此操作。(我希望你喜欢这里大量使用双关语。)****
*   ****在您的 lambda 函数`main.py`中，进行以下更改:****

```
**def lambda_handler(event, context):
    #get number from the GET call

     input = int(event['queryStringParameters']['input'])
     return { 'status' : 200, 'body' : 'Lambda executed successfully! Got the number : %d'%input }**
```

*****(你将不得不再次创建部署包，把它上传到 S3，然后在 lambda 函数中取回，但这应该不成问题，因为你现在是专家了。)*****

*   ****返回到资源编号，并在 GET 方法中单击 test(螺栓图标)。在`Query Strings` `{number}`中输入以下内容。****

```
**input=2**
```

*   ****点击测试。如果一切顺利，结果应该是，****

```
**Lambda executed successfully! Got the number : 2**
```

****[这里是](https://aws.amazon.com/blogs/machine-learning/how-to-deploy-deep-learning-models-with-aws-lambda-and-tensorflow/)一篇强调在 AWS lambdas 上部署深度学习模型(大尺寸)的文章。****

****干杯！****

****[![](img/308a8d84fb9b2fab43d66c117fcc4bb4.png)](https://medium.com/swlh)****

## ****这篇文章发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，拥有+ 378，907 读者。****

## ****在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。****

****[![](img/b0164736ea17a63403e660de5dedf91a.png)](https://medium.com/swlh)****