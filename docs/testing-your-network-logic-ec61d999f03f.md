# 测试您的网络逻辑

> 原文：<https://medium.com/swlh/testing-your-network-logic-ec61d999f03f>

我们学习抽象业务逻辑，使其可测试；我们不再质疑视图模型或演示者应该进行单元测试，但是如果我说有更多的逻辑呢？你的网络逻辑呢？

![](img/410c177d880062f0d5c776051feadc3f.png)

Network logic can get complex…

如今，Android 开发者使用一种常见的设置，**用 **OkHttp** 和 **Moshi** 或 **Gson** 改造**。

```
val moshi = Moshi.Builder().build()
val okHttp = OkHttpClient.Builder().build()
val retrofit = Retrofit.Builder()
        .addConverterFactory(MoshiConverterFactory.create(moshi))
        .addCallAdapterFactory(RxJava2CallAdapterFactory.create())
        .client(okHttp)
        .baseUrl("Some url")
        .build()
```

然后一些需求开始进来

*   跟踪网络事件。
*   为您的后端添加自定义标题。
*   认证令牌的刷新机制。
*   还有更多…

我们受益于 OkHttp 机制，比如拦截器和认证器。

```
val level = if (BuildConfig.*DEBUG*) {
    HttpLoggingInterceptor.Level.BODY
} else {
    HttpLoggingInterceptor.Level.NONE
}
val loggingInterceptor = HttpLoggingInterceptor().setLevel(level)

val okHttp = OkHttpClient.Builder()
        .addInterceptor(authTokenInterceptor)
        .addInterceptor(loggingInterceptor)
        .authenticator(authentiactor)
        .build()
```

然后我们把所有的放在一起，希望它能起作用。

我们可以为每个拦截器或验证器添加单元测试，但是我们能确定整个网络层的组合和设置工作正常吗？

我们有没有想过在添加一个拦截器之前添加另一个会发生什么？或者我们改变适配器的顺序？

> 秩序很重要！

如果我们可以测试所有的设置和网络层而不攻击服务器，会怎么样？

# **WebMockServer 来拯救。**

OkHttp 不仅仅提供客户端库。如果我们检查回购协议，我们可以找到其他组件。那些 [MockWebServer](https://github.com/square/okhttp/tree/master/mockwebserver) 中的一个。

> 这个库使得测试你的应用程序在进行 HTTP 和 HTTPS 调用时做正确的事情变得容易。它允许您指定要返回的响应，然后验证请求是否按预期发出。

自述部分有一个很好的解释和一些例子，但下面我会解释谁使用它来测试我们的设置。

首先，让我们解释一下不同的概念:

*   **MockWebServer:** 一个精简类，它将拦截 HTTP 请求并根据配置的响应进行回复。
*   **MockResponse:** 可配置 OkHttp 响应。(即设置 HTTP 代码、正文、标题……)
*   MockWebServer **。enqueue(mockResponse):** 向队列中添加一个 mockResponse，第一个请求将被第一个入队的响应所回复，第二个请求将被第二个响应所回复，依此类推…
*   MockWebServer **。taker request():**等待下一个 HTTP 请求，记录它，并将其返回到 RecordedRequest 中。
*   **RecordedRequest:** 包含来自 HTTP 请求的记录字段的类(即头、体、方法、路径……)

这是我们目前需要的大部分东西，所以让我们设置我们的第一个测试。

一个好的做法是将上面解释的通用设置抽象成一个类，该类可用于生成我们的 API 接口，如下所示:

这个类将被任何需要 API 的组件使用。

接下来，我们可以设置我们的测试类:

1.  创建 **MockWebServer。**
2.  使用 mock web server**生成**URL，这样任何请求都会被转发到模拟服务器。
3.  使用**真正的**实现你的拦截器和认证器。
4.  使用**模仿**作为拦截器和验证器的依赖来验证它们。
5.  创建一个简单的 **TestApi** 和 **TestData** 来测试设置。

现在我们已经准备好了设置，我们需要定义测试什么。

1.  **解析器**:我们想要确保我们的 Moshi 设置是正确的
2.  [**拦截器**](https://github.com/square/okhttp/wiki/Interceptors) :我们希望确保当一个请求完成时，我们的拦截器的行为符合预期
3.  [**验证者**](https://github.com/square/okhttp/blob/master/samples/guide/src/main/java/okhttp3/recipes/Authenticate.java) :我们希望确保当返回 401 响应时，我们的验证者尝试刷新令牌并重试原始响应。
4.  (可选)**“真正的”API 接口**:我们可以用一些假数据测试我们所有的端点和 API，这样我们就可以验证我们所有的响应和请求体的解析

## 测试解析器

下面的代码显示了一个简单的解析测试示例，它验证了我们的 Moshi 和 retrofit 配置正确。

```
@Test
fun `When succeed with valid data, Then response is parsed`() {
    val testData = TestData("hello!")
    val testDataJson = "{\"name\":\"${testData.name}\"}"
    val successResponse **=** MockResponse().setBody(testDataJson)
 **mockWebServer.enqueue(successResponse)**

    val response = **testApi.test().execute()**

    mockWebServer**.takeRequest()**
    assertThat(response.body()!!, *is*(testData))
}
```

1.  用一些 JSON 数据创建一个成功的 MockResponse
2.  将响应排入队列
3.  调用 API 端点(HTTP 请求)
4.  等待，直到请求得到处理
5.  断言响应体被正确地解析到我们的数据类中

## 测试拦截器

下一个测试将检查我们的 *AuthInterceptor* 是否在我们的请求中添加了一个*载体*令牌头。

```
@Test
fun `When a call is done, Then auth header is added`() {
    val token = "Token"
    tokenStorage.setToken(token)
 **mockWebServer.enqueue(successResponse)**

 **testApi.test().execute()**

    val recordedRequest = **mockWebServer.takeRequest()**
    val header = recordedRequest.getHeader("authorization")
    *assertThat*(header, *is*("Bearer $token"))
}
```

1.  将预期的令牌设置到我们的存储中(由 AuthInterceptor 使用)
2.  将响应排入队列
3.  执行并等待记录的请求
4.  断言标头“authorization”存在，并且包含预期的令牌

## **测试认证器**

认证器可以用于几种情况([参见 OkHttp Recipes 部分](https://github.com/square/okhttp/wiki/Recipes#Handling$authentication))，在我们的例子中负责在服务器回复 401 时请求一个新令牌。

这可能是我们设置中最关键的部分，也是最难测试的部分，因为我们希望确保用户不会被注销，并且能够在没有注意到的情况下刷新 auth 令牌。

```
@Test
fun `When fails with 401, Then authenticator refreshes token`() {
    val invalidTokenResponse = MockResponse().setResponseCode(401)
    val authResponse = AuthResponse(
            accessToken = "New token", 
            expiresInSeconds = 0, 
            refreshToken = refreshToken
    )
    val responseBody = moshi.adapter(AuthResponse::class.*java*)
            .toJson(authResponse)
    val refreshResponse = MockResponse()
            .setResponseCode(200)
            .setBody(responseBody)
    tokenStorage.refreshToken = refreshToken

 *// Enqueue 401 response*
 **mockWebServer.enqueue(invalidTokenResponse)**
 *// Enqueue 200 refresh response*
 **mockWebServer.enqueue(refreshResponse)**
 *// Enqueue 200 original response*
 **mockWebServer.enqueue(successResponse)**

    val response = **testApi.test().execute()**

 **mockWebServer.takeRequest()
    mockWebServer.takeRequest()**
    val retryRequest = **mockWebServer.takeRequest()**
    val header = retryRequest.getHeader("authorization")
    *assertThat*(tokenStorage.token, *is*(authResponse.accessToken))
    *assertThat*(header, *is*("Bearer ${oAuthResponse.accessToken}"))
    *assertThat*(response.*isSuccessful*, *is*(true))
}
```

1.  用 401 代码设置失败响应
2.  使用新的身份验证令牌设置刷新响应
3.  将有序的响应集排队
4.  执行并等待所有三个请求
5.  检查标头是否有新令牌，以及令牌是否存储正确

我们可以越来越深入地了解不同的边缘案例，例如:

*   当刷新调用失败时，原始请求失败，返回 401。
*   当刷新调用以 401 失败时，则不会再次调用刷新调用。
*   当多个调用因 401 而失败时，则只进行一次刷新调用。
*   …

# 结论

使用 MockWebServer 测试网络并不困难，网络层是您的应用程序的一个非常重要的部分，服务器端是不可预测的，并且很难验证手动测试的所有情况。

## 外卖食品

*   **摘要**创建你的网络组件。
*   使用 **MockWebServer** 测试你的网络层。
*   在**设置**上创建 MockWebServer(它会自动启动)。
*   **用 mock web server
    *(val httpUrl = mock web server . URL(base URL))*的实例创建**基本 **URL**
*   **MockResponse** 带有一个**空体**，你的系统能处理吗？
*   **Enqueue** 和**taker request**默认是有序的，使用自己的 [**Dispatcher**](https://github.com/square/okhttp/tree/master/mockwebserver#dispatcher) 进行自定义行为。
*   测试所有 API 或创建测试 API。

[](https://github.com/marcelpinto) [## marcelpinto -概述

### arctic Code Vault Contributor rx Flux 是一个小框架，以便使用 RxJava 遵循 Flux 设计模式…

github.com](https://github.com/marcelpinto) [![](img/308a8d84fb9b2fab43d66c117fcc4bb4.png)](https://medium.com/swlh)

## 这个故事发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的企业家出版物，拥有 348，974+人。

## 在这里订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

[![](img/b0164736ea17a63403e660de5dedf91a.png)](https://medium.com/swlh)