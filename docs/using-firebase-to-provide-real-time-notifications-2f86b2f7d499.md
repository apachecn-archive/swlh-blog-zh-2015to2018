# 使用 Firebase 提供实时通知

> 原文：<https://medium.com/swlh/using-firebase-to-provide-real-time-notifications-2f86b2f7d499>

![](img/e89630291691ce7d8c3fb3ff29a62fb7.png)

irebase 最初是一个云数据库，后来发展到包括通知、认证和其他功能。从表面上看，它很有趣，允许移动设备使用 Firebase API 加载和存储数据，无需拥有任何后端服务器或主机。为了容易地保持同步，使用 Firebase 的不同设备可以获得数据更改事件。作为其本机格式，数据库使用 JSON，这非常适合 web 或移动应用程序。Firebase 支持 Web、Android 和 iOS。这意味着它支持本地应用程序加上一个网站或基于网络的管理组件。Firebase 的最新版本 V3 现在完全托管在谷歌云上，并向我们介绍了一些不错的功能，如 iOS/Android 的推送通知和云存储。

# 什么是 Firebase？

Firebase 最初是一个后端即服务(BaaS)平台，后来发展成为谷歌云平台上的下一代[应用开发](https://www.cognitiveclouds.com/custom-software-development-services/mobile-app-development-company)平台。Firebase 让您可以专注于打造令人惊叹的用户体验。您不再需要管理服务器。你不再需要写 API 了。Firebase 可以是你的服务器、你的 API 和你的数据存储库，所有这些都写得很一般，你可以修改它来满足你的大部分需求。Firebase 允许您在前端开发整个应用程序，而无需任何服务器端代码。但是，如果您需要对一些事件(如创建数据或文件、登录、https 请求等)做出反应，它确实允许您通过 Firebase 函数设置一些服务器端逻辑。，您可以发送推送通知或电子邮件，或者在数据写入后进行处理。此外，你偶尔需要在高级应用中使用谷歌云的某些部分。Firebase 不会是每个人的一切，尽管它非常接近。另一方面，有很多事情它没有做。您需要在应用程序架构的上下文中考虑 Firebase。

# 这是实时数据库

Firebase 是一个实时数据库，您可以从客户端直接与之通信。当您将 JSON 数据保存到 Firebase 时，这些更改会立即发送到请求它们的所有 web 和移动客户端。Firebase 将通过内置的静态文件托管、用户管理和安全规则，帮助您更快地构建现代应用程序。

没有什么比得上实时数据。这是未来之路。大多数数据库需要您进行 HTTP 调用来获取和同步您的数据。这些数据库只有在你需要的时候才会给你数据。使用 Firebase，当你把你的应用程序连接到它时，你不是通过普通的 HTTP 连接。您正在通过 WebSocket 进行连接。WebSockets 比 HTTP 快很多。您不必进行单独的 WebSocket 调用，因为您只需要一个套接字连接。您的所有数据通过单个 WebSocket 自动同步，速度与您的客户端网络能够承载的速度一样快，Firebase 会在数据更新时向您发送新数据。当您的客户端保存对数据的更改时，所有连接的客户端几乎会立即收到更新的数据。Firebase 实时数据库为我们提供了保存、检索和同步 NoSQL 云数据库数据的能力。这些数据可以在所有客户端之间实时同步。您可以看到 Firebase 实时数据库是一个云托管的 NoSQL 数据库，其中存储为 JSON 的数据实时同步到所有连接的客户端。因此，与关系数据库相比，它具有不同的优化和功能。

![](img/2b092c3fc31ccba6db66308a088f363f.png)

*Using Firebase To Provide Real-Time Notifications*

Firebase 使开发人员能够构建出色的实时体验，在不影响响应速度的情况下为大量用户提供服务。因此，有必要记住，您需要根据用户访问数据的方式来组织数据库中的数据。如果你决定用 Firebase 的 Android、JavaScript 或 iOS SDKs 构建一个跨平台的应用，所有的客户端将共享一个实时数据库实例，并自动接收新数据的更新。Firebase 实时数据库在每次数据更改时都使用数据同步，因此任何连接的设备都会在几秒钟内收到更新。

# Firebase 通知

Firebase Notifications 是一项免费服务，为移动应用开发者提供有针对性的用户通知。Firebase Notifications 构建于 Firebase Cloud Messaging (FCM)和 FCM SDK 之上，为寻求灵活的通知平台的开发人员提供了一种选择，这种平台只需要最少的编码工作就可以开始，它还提供了一个用于发送消息的图形控制台。这样，您可以向所有支持的消息目标发送通知。Firebase 云消息处理路由和向目标设备的交付。

# 优势:

*   认证。Firebase auth 包括一个内置的电子邮件/密码认证系统。它还支持脸书、谷歌、Twitter 和 GitHub 的 OAuth2。此外，Firebase Auth 直接集成到 Firebase 数据库中，这样您就可以使用它来控制对数据的访问。
*   主持人。Firebase 为你所有的静态文件提供了一个易于使用的托管服务。它通过 HTTP/2 从全球 CDN 提供所有这些服务。
*   所有客户端之间的数据实时同步将非常方便，无论是 Android、iOS 还是 Web。用最少的代码，你可以做很多事情，比如聊天框，实时新闻提要，通知用户新的帖子或好友请求等等。
*   不管怎样，AJS 的代码都很简单。从查询数据到整合 Twitter、脸书和 Google+登录，你可以用一些漂亮的特性让它快速运行。
*   通过自动更新通知，它保持两个系统同步，无需手动消息传递、WebSockets 等。
*   允许您将数据视为流来构建高度可伸缩的应用程序。
*   简单的 UI 不需要服务器。
*   免费托管。

# 缺点:

*   由于 Firebase 的数据流模型，查询能力有限。一个主要的挑战将是数据库中数据的组织。今天，Firebase 数据库查询是有限的。某些查询选项不能组合。因此，您必须做出选择，要么按日期对文档进行排序，要么在数据库端使用[用户的搜索查询](https://www.datadab.com)进行过滤，然后在客户端执行其他操作。
*   传统的关系数据模型不适用于 NoSQL。因此，您的 SQL 印章不会转移。
*   无内部安装。
*   Firebase 非常面向实时同步。当您在文本字段中键入内容时，数据库会自动更新。如果其他人在文本栏中键入，您的屏幕会进行调整。主要的文档示例和角度集成似乎都关注于此。虽然这可能不是你想要的。您可能更习惯于编写查询并使用事件处理程序来更新数据库或接收其他人的更新。但这只是稍微调整一下的问题。
*   数据库惊人的有限。
*   如果没有后端，支持 Web、iOS 和 Android 意味着要多次重写业务逻辑和数据转换
*   角度集成只有在您寻找直接绑定到数据库更新的 HTML 小部件时才有帮助，中间没有侦听器或处理程序。
*   Firebase 只能升序排序，不能降序排序。

# 结论

找出 Firebase 适合您的应用程序的地方。如果你正在寻找一个实时的新闻提要，Firebase 做得很好。如果你想要站内通知，Firebase 是一个完美的选择。如果你想要一个聊天系统，很好。你希望给每个浏览网站的人展示新文章吗？Firebase 会很适合你。Firebase 是指快速项目。它快速、易于设置，并且在大多数情况下只需要前端逻辑。它让您专注于您的应用程序，而不是实现自定义身份验证、web 套接字或数据库连接。缺点是你必须尽可能简单地组织你的应用程序，例如，没有复杂业务逻辑的读写操作。

Firebase 广泛用于实时通知功能，因为它是一站式服务。Firebase 提供的不仅仅是对 Android 和 iOS 设备推送通知的支持。它还提供使用其实时数据库服务。Firebase 对其 SDK 的简单使用和轻松集成吸引了更多的开发人员。然而，总的来说，Firebase 并不适合我们开发的大多数应用程序。如果您已经决定全力以赴使用 Firebase，那么就利用角度集成，您可以获得许多功能，比如能够将数据库对象直接附加到您的屏幕小部件。但是，为了让 Firebase 具有吸引力，您的应用程序需要实时同步至关重要，多平台客户端很有帮助，并且数据模型不是特别复杂。所以你看，这只是一个确保应用程序符合 Firebase 的功能和限制的问题。在这方面，我认为所有的工具都是一样的。

*原载于*[*【CognitiveClouds.com】*](https://www.cognitiveclouds.com/insights/using-firebase-to-provide-real-time-notifications/)*:顶* [*节点 js 开发公司*](https://www.cognitiveclouds.com/custom-software-development-services/node-js-development-company)

![](img/731acf26f5d44fdc58d99a6388fe935d.png)

## 这个故事发表在 [The Startup](https://medium.com/swlh) 上，这是 Medium 最大的企业家出版物，拥有 299，352+人。

## 在此订阅接收[我们的头条新闻](http://growthsupply.com/the-startup-newsletter/)。

![](img/731acf26f5d44fdc58d99a6388fe935d.png)