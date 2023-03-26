# 制作一个超级最小 API

> 原文：<https://medium.com/swlh/making-an-uber-minimal-api-f62f6189f262>

API 或“应用程序接口”是处理请求的简单方式，通常使得响应一致且易于解释。这是连接不同提供商的服务的重要组成部分，如谷歌地图应用编程接口(T1)，或 T2 的微服务架构(T3)，如网飞。

最基本的形式是:

1.用户(通常以编程方式)向主机服务器发送 http 请求。url 参数包含用户指定的“任务”的详细信息。

2.服务器解析 url 参数并执行其所需的任务。

3.服务器以机器友好格式的输出作为响应，例如:JSON。

这是有效的，因为用户与服务交互的方法不限于任何一个程序、语言或操作系统。这使得开发人员可以将 Instagram 等外部服务集成到他们的应用程序中，而 Instagram 不必放弃对外部方可以控制的内容的控制。因此，虽然我可以提供服务，让用户喜欢 Instagram 上的帖子，但我不能删除他们的数据库。

## 议程上的第一项—发送请求的地方:

可能是个好的开始。Flask 可以用来为此创建一个非常整洁的应用程序。

```
from flask import Flask, request, jsonifyapp = Flask(__name__)[@app](http://twitter.com/app).route('/api')
def API():
    return process_request(request.args) #get URL argumentsif __name__ == "__main__":
    app.run(debug=True)
```

## 下一步——让它做点什么！

举例来说，这个函数在给定体重、身高和可选性别的情况下计算身体质量指数。

```
def get_BMI(height, weight, sex='male'):
    #Calculate BMI and BMI category: #Some maths here #return a dict which will be converted to JSON
    return {"BMI": BMI, "category": category, 
           "data": {"height": height, "weight": weight, "sex": sex}}
```

它返回一个字典，可以转换成 JSON 以便接收方使用。process_request 函数确保所需的参数存在，否则抛出错误。

```
def process_request(query):
    if 'height' in query.keys() and 'weight' in query.keys():
        if 'sex' in query.keys():
            response = get_BMI(query['height'], 
                               query['weight'],
                               sex=query['sex'])
        else:
            response = get_BMI(query['height'], 
                               query['weight'])
    else:
        response = {"error": "'height' and 'weight' are required"}

    return jsonify(response)
```

现在，用户可以传递一个格式为:'【http://www.hostsite.com/api?weight=67】T4&性别=女性&身高=172 的 url，并在 JSON 中接收响应:

```
{
  "BMI": 20.74506939371804, 
  "category": "Healthy", 
  "data": {
    "height": "185", 
    "sex": "male", 
    "weight": "71"
  }
}
```

耶，你的 API 起作用了！

## 奖励回合—让它更好用:

虽然将字符串连接成一个 url，然后发送一个 GET 请求，然后在最终能够访问您的输出之前将响应转换成 JSON，但是组织经常发布库或包来使这个过程更加用户友好。通过将机制隐藏在一个包中，API 可以成为一个“黑匣子”,但这也大大降低了使用您的服务的障碍。在这种情况下，一个简单的 python 类就可以解决这个问题:

```
class Bmi(object):
    def __init__(self):
        self.BMI = 'no data'
        self.category = 'no data' def get(self, weight, height, sex="male"):
        import urllib2
        import json url = 'http://www.hostsite.com/api?*'*      
        query =  'weight='+str(weight)
        query += '&height='+str(height)
        query += '&sex='+sex
        response =  urllib2.urlopen(url + query)
        data = response.read()
        data = json.loads(data)

        self.BMI = data["BMI"]
        self.category = data["category"]
```

现在与 API 的交互更加“人性化”。

```
from bmi_package import bmitest = bmi.Bmi()
test.get(89, 185)print(“Your BMI is: {0}”.format(test.BMI))
print(“Based on this, you are: {0}”.format(test.category)
```

![](img/731acf26f5d44fdc58d99a6388fe935d.png)

## 这篇文章发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的创业刊物，有 285，454+人关注。

## 订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)