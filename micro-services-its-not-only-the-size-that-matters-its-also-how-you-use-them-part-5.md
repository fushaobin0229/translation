Microservices: It’s not (only) the size that matters, it’s (also) how you use them – part 5

> https://www.tigerteam.dk/2015/microservices-its-not-only-the-size-that-matters-its-also-how-you-use-them-part-5/

第四部分我们建议围绕功能分区或者业务功能/界限上下文来构建服务。我们讨论了附属与业务能力的业务数据和逻辑必须被封装在服务里一边确保数据的单一来源。这也意味着其他服务不允许拥有别的服务已经拥有的数据，既然我们想要服务自治（也就是可以不需要和其他服务同步通信就可以工作），我们也看了如何避免服务间双向通信（RPC，REST 或者 请求/应答），我们找到的方案是组合 UI 已经通过事件进行数据复制，我们也简单讨论了第三种方案：涉及到服务的不同视角，不需要自治，代替服务暴露刻意的接口并协调多个自治的纪录系统的更新和读取，许多有大遗留系统的公司应该尝试使用第三种方案，比起开发新的对应业务能力的自治服务来说摩擦更少。

第五部分继续讨论根据自治的服务构建 SOA 和微服务。

## 业务能力和服务

第四部分我们建议围绕功能分区或者业务功能/界限上下文来构建服务。
我想语气应该更强硬一点：我们应该让服务匹配业务功能。

为什么？Bill Poole 在 [](http://bill-poole.blogspot.dk/2008/07/business-capabilities.html) 文中解释了为什么服务匹配业务功能是正确的方式：

“一个业务功能是什么？是一个机构执行的一些在某些方面上对整体功能的贡献。

业务功能的优点是其非常的稳定，如果我们看一个典型的保险机构，它应该有销售、市场、保单管理、索赔管理、风险评估、开票、支付、客户服务、人力资源管理、渠道管理、费用管理、合规性、IT 支持和任务管理等业务，实际上，任何一个保险机构都会需要这些业务” -- Bill Poole

业务功能是我们开发的软件的根基，Dan North 说过下面这段话：

![Dan North：业务功能是资产](http://www.tigerteam.dk/wp-content/uploads/2015/02/dan-north-on-business-capabilities.png)

最后 Udi Dahan 在 [The Known Unknowns of SOA](http://www.udidahan.com/2010/11/15/the-known-unknowns-of-soa/) 一文中说明了为什么他觉得服务应该是自治的，并成为特定业务功能的技术权威。

“同步的生产者/消费者意味着模型服务不调用其它服务就不能满足他们的目标。为了让我们能够实现 SOA 承诺的 IT/业务一致性，我们需要服务是自治的，也就是能够不依赖那种外部分就能完成自己的目标。

服务是特定业务功能的技术权威，任何数据和业务规则都必须只属于一个服务。

这意味着，即使服务发布和订阅对方的事件，我们只是知道每一个数据块和规则的权威事实来源”  -- Udi Dahan

我把上面的描述总结为以下规则：

## 一个服务是

- 对于一个给定的业务功能的技术权威
- 所有支持该业务功能的数据和业务规则的所有者 - 每个地方都是
- 形成了功能的单一事实源头
- 形成业务和 IT 匹配确保维持服务的自治性和封装性

定义的结果是：服务需要部署和随处可得，数据/逻辑是必要的。

思考后会觉得更合理，Udi Dahan 在 [The Known Unknowns of SOA](http://udidahan.com/2010/11/15/the-known-unknowns-of-soa/) 一文中解释了原因：

> “从业务功能的视角来看一个服务，我们看到许多用户界面展示了属于不同的功能的信息，产品价格旁边显示了是否有库存，为了让我们能够满足服务的上述要求，这导致我们理解用户界面实际上是一个混搭，每个服务通过它特有的数据处理 UI 中的一个区块。

> 最后，过程边界，像 Web 应用程序、后端、批处理是非常差的服务边界标识，我们希望每个这样的过程都能看到多个业务功能。” -- Udi Dahan

太抽象了，我么举个复合 UI 的例子：

![亚马逊的复合 UI](http://www.tigerteam.dk/wp-content/uploads/2015/02/Composite-UI-Amazon.png)

UI 区域的组合服务可以在客户端完成也可以在服务端完成。一种思考方式是每个服务渲染它负责的 UI 成为网上商城页面上一个特定的 DIV：

![HTML 组合](http://www.tigerteam.dk/wp-content/uploads/2015/03/HTML-Composition.png)

更新：如果组合发生在客户端，那么客户端 UI 组件和服务端对应的部分（比如一个 REST 接口）通常包含双向通信（也就是说很少使用发布/订阅模式，除非你希望服务器生成事件推到客户端）。为了让 UI 有应答洗脑洗，客户端 UI 组件和服务端对应的部分典型情况下使用基于异步的同步双向通信，比如使用带有 Javascript 回调的异步 Ajax 调用。

组合 UI 的优点是，像网上商城这样的应用程序，不需要知道提供页面上 UI 区块的每个服务的任何细节，事实上，评论就是分数、评论数和赞的数量在评论服务里的完整封装，评论分数渲染成星星而不是数字是一个具体的应用程序可视化的决定，所有的评论服务输出可能是 &lt;score&gt;4.2&lt;/score&gt;，UI 按样式的要求渲染，从应用程序的角度来看，他们共享的是页面上下文和样式协议，事实上，评论服务的 UI 会被渲染成一个 id 为 “Book:Review” 的 DIV，优点是评论功能增加新功能只需要在评论服务里实现，不同的应用程序平台的 UI 区块需要针对新去求更新并推到应用程序，但是应用程序内部不需要修改什么，修改完全在评论服务内部。

使用复合 UI 的另一个优点是别的服务很少需要订阅其他服务的事件来建立缓存或数据副本，这个问题已经在组合层面解决了。

缺点是给定的服务需要能够提供它的 UI 区块给所有可能的应用程序，比如 iOS 应用、后台 .Net 应用，基于 Java 的网上商城等等，下面的使用组合方式的例子中多个服务渲染/打印出发票的
一部分：

![复合 UI 发票例子]http://www.tigerteam.dk/wp-content/uploads/2015/02/Composite-Invoice.png

我觉得，复合 UI 是自治服务真正强大的场合，从多个服务渲染内容却不会让服务之间耦合。你获得在各个层级封装良好的服务，我们展示出来的接口/协议很少暴露服务的数据和功能，服务通常暴露给消费者驱动 IT 操作本地接口（第三方/遗留系统集成）、事件（典型情况下只需要包含发生了什么事以及变更影响的聚合 ID）、几个对外暴露的命令，当然还有我们的 UI 区块，除了这些只有非常少的协议/接口暴露给生态系统。

更新：复合 UI 的一个挑战是当发生更新时（比如提交表单跨越多个服务），因为我们这里又遇到跨事务边界更新数据的问题，当一个或多个服务更新失败而其他成功时没有两阶段提交事务来帮助解决问题。你还必须考虑到浏览器是一个不可信赖的平台，由于浏览器挂起或者用户关闭了页面，就像服务端实现相似的编排。

如果你对复合 UI 感兴趣，可以阅读 Udi Dahan 的 [Service-Oriented Composition](http://www.udidahan.com/2012/06/23/ui-composition-techniques-for-correct-service-boundaries/, http://www.udidahan.com/2014/07/30/service-oriented-composition-with-video/) 一文。

## 服务部署模型

希望服务被部署后任何需要他的数据的地方都能使用，这其实是有问题的，因为服务是有物理结构或者边界的。

根据 [Philippe Kruchten's 4+1 view](http://en.wikipedia.org/wiki/4+1_architectural_view_model) 对架构的描述，逻辑视图、物理视图（部署视图）应该彼此独立（也就是说它们不应该一对一的映射）。

结合上面的服务定义，我们得到的结论是：服务必须以业务逻辑作为构造单元和边界。

总结为以下定义：

- 系统和应用是运行时进程边界，进程边界时物理边界（简单的例子是一个单一 .exe 或者 .war 部署单元）
- 服务是逻辑边界，不是物理边界，你可以选择把服务部署为一个单一的物理进程，但这也只是部署服务的一种方式，并且不一定是正确的方式。
- 因此进程/应用/系统边界和服务边界可能是不一样的

为了支持将多个服务组合成应用程序，每个服务可以有以下的部署选项：

- 许多服务可以被部署在同一个系统、应用程序和进程内
- 一个服务的不同部分可以被分别部署为不同平台（Java、.NET、iOS、Android、Web 等等）的应用程序，比如服务的 UI 部分可以被部署成一个 Web 应用程序，一个 iOS 应用程序，一个 Android 应用程序（每一个都是单独实现并针对特定平台打包，但是让然数以同一个逻辑服务），举个例子：产品的价格在网上商城、后台应用、iOS 商业应用上都会显示（换句话说，业务功能快乐应用程序边界）
- 服务部署不需要强制分层，同样的服务可以部署到多层，甚至多个应用程序中。服务 A 和 B 的一部分可以被部署为 Web 层，另一部分可以被部署为同一个应用程序的后台/应用程序服务层。
- 许多服务可以被部署在同一个服务器
- 许多服务的 UI 可以被部署或者载入到同一个页面（服务混搭）

## 组成的服务是什么？



















