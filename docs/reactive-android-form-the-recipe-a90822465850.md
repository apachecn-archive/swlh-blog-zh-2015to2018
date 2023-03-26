# 反应式安卓形态。食谱

> 原文：<https://medium.com/swlh/reactive-android-form-the-recipe-a90822465850>

每个人都讨厌表单，但是有一类人更讨厌表单……**开发人员**。我们都厌倦了这些冗长的表格和处理所有可能的情况，所有的错误，然后让用户一切顺利和容易。我没有完美的解决方案，但我有一个方法可以让它变得更简单，让我说得更好。姑且称之为 **RxForms**

## 案件

*   空输入
*   无效输入
*   缺失内容
*   接受条款和条件
*   启用/禁用提交按钮

## 配料

*   Android Studio(最新版本)
*   [RxAndroid](https://github.com/ReactiveX/RxAndroid)
*   Android 设计支持库(可选)
*   [倒车雷达](https://github.com/evant/gradle-retrolambda)(可选)

## 该方法

**1。将依赖项添加到您的项目中**

```
dependencies {
    compile **'com.android.support:appcompat-v7:22.0.0'** compile **'com.android.support:design:22.2.0'** compile **'io.reactivex:rxandroid:0.25.0'** }plugins {
  id '**me.tatarka.retrolambda'** version **'3.2.0'**
} 
```

**2。创建表单视图**

这部分是你放置你的特殊触感的地方，按照你喜欢的方式设计它，在我的例子中，我创建了一个 ScrollView，它包含一些用支持视图 [TextInputLayout](https://cdn-images-1.medium.com/max/1000/1*cHpl5ROayZZjEh_7ZExEPw.gif) 包装的 EditText。

**3。反应视图**

这部分是这个食谱最重要的部分。我们将创建一个新类，姑且称之为 **RxViewUtils** 。这个类将为我们连接这些点，所以我们不需要处理表单的所有可能的情况，并将帮助我们减少样板代码。

这里的主要方法是 *verifyInput* 方法。它接受一个输入视图，在这个例子中是一个 TextInputLayout，使用 RxAndroid 库提供的方法从中创建一个可观察对象，并应用我们想要在这个输入中检查的**动作**。为了应用这个动作，我们使用**合成**方法( [@danlew42](https://twitter.com/danlew42) 很好地解释了它[在这里](http://blog.danlew.net/2015/03/02/dont-break-the-chain/))和**应用**变压器，这获得可观察的电流并应用以下方法。

1.  [**去抖**](http://reactivex.io/documentation/operators/debounce.html) ，所以我们等待用户停止敲击后再验证输入
2.  [**映射**](http://reactivex.io/documentation/operators/map.html) 把发射源变成我们的动作，这样会返回真或假
3.  **在 Android 主线程上观察**和**订阅**(我们在处理视图！)

来说说动作吧。action or **Func1 < String，Boolean >** 将一个字符串作为参数(在我们的例子中是用户输入的最后一个文本)并应用所需的检查，最后如果输入正确则返回 true，否则返回 false。

您可以自定义您的操作，应用您想要的规则，然后决定输入源是否有效。这些动作是处理表单案例的简单方法。

**4。全部订阅！**

最后，对于您的每个 **EditText** 或 input view，使用期望的动作创建可观察对象，并使用**combine test 将它们放在一个单独的可观察对象中。**每当创建的一个观察值发出时，CombineLatest 将发出结果列表。如果它们都为“真”，那么我们启用提交按钮。

这里的额外步骤是报告输入字段不正确。为此，我们使用 **doOnNext** 函数。每当源可观察对象发出一个项目时，都会用一个布尔参数调用它。这个布尔值告诉我们这个源是否有一个有效的输入。所以我们只需更新视图并告诉用户有问题。

## 结果呢

![](img/929ab49916590a44f8187f5ca8c91c94.png)

在 Twitter 上找到我:[@ marxalski](https://twitter.com/marxallski)和 [Google+](https://plus.google.com/u/1/+MarcelPint%C3%B3)

你可能也会喜欢我关于 [RxFlux](/@marxallski/rxflux-android-architecture-94f77c857aa2#.3kj1933pn) 的新帖子

![](img/c1192ebad88d6b1fc6ae1d6a2bc61154.png)

*发表于* **创业、旅游癖和生活黑客**

[![](img/de26c089e79a3a2a25d2b750ff6db50f.png)](http://supply.us9.list-manage.com/subscribe?u=310af6eb2240d299c7032ef6c&id=d28d8861ad)[![](img/f47a578114e0a96bdfabc3a5400688d5.png)](https://blog.growth.supply/)[![](img/c1351daa9c4f0c8ac516addb60c82f6b.png)](https://twitter.com/swlh_)

-