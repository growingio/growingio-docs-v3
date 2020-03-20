# 埋点事件和事件级变量

## 1. 数据规划 <a id="di-yi-bu-cong-shu-ju-xu-qiu-dao-ju-ti-zhi-biao-wei-du"></a>

数据规划就是将数据需求转化为具体的“指标+维度”。

在 GrowingIO 上着手进行任何分析之前，首先要确定的一个问题是：如何设计“指标 + 维度”的体系？

* 对于无埋点数据，我们通过圈选确定“指标”，而“维度”则由 GrowingIO 提供了数个预定义的维度。
* 对于自定义的埋点数据，我们可以相对更自由地选择“指标 + 维度”的体系。

更具体的说，从一个实际场景出发，我们需要确定在分析中需要用到哪些量化的值，然后用什么样的维度来分解这些值。例如，对于电商在分析用户下单情况时，用户的下单量就是我们需要量化的“指标”，而每个订单所含具体商品、商品分类、优惠券信息、下单金额等就是“维度”。

那么对于下单这件事，我们就可以这样设计 ”指标 + 维度“：

* 指标：
  * 订单总量
* 维度：
  * 商品ID/名称
  * 商品 SKU
  * 优惠券名称
  * 收货地址
  * 下单金额
  * ...

那么现在很明显了，"订单总量" 这个指标，需要用 “埋点事件” 来实现。

商品ID/名称、优惠券名称等维度，则可以通过下一章节的 “事件级变量” 来实现。

{% hint style="success" %}
**设计“指标 + 维度”体系时注意事项**

Android、iOS 以及 Web 端三端不需要区分：对于这三端，可以只定义一个指标，而不需要分别对三端定义三个指标。

举例来说，“订单总量”这个指标可以包含三端的总量，在 GrowingIO 平台分析时使用预定义维度“网站/手机应用”或者“操作系统”就可以拆分三端分别的量。
{% endhint %}

## 2. 平台数据声明 <a id="di-er-bu-zai-mai-dian-guan-li-zhong-wan-cheng-pei-zhi"></a>

在GrowingIO平台声明事件和事件级变量。

当我们完成 ”指标 + 维度“ 的设计之后，请勿直接开始代码的部署，需要先到 GrowingIO 平台的数据管理中完成对应的配置。

**埋点事件配置方式请参考**[**埋点事件管理**](../../../product-manual/datacenter/datamanage/event-manage/manual.md)**。**

**事件级变量配置方式请参考**[**事件变量**](../../../product-manual/datacenter/datamanage/variable/event.md)**。**

## 3. 代码部署

在GrowingIO平台对事件和事件级变量进行声明配置后，即可在代码中完成以上设计的 “事件和事件级变量” 的部署。具体的说，就是调用 GrowingIO 提供的 API 接口，上传数据。

* ​[JS 接口文档​](../../../developer-manual/sdkintegrated/web-js-sdk/web-sdk-api/)
* ​[Android 接口文档​](../../../developer-manual/sdkintegrated/android-sdk/android-sdk-api/)
* ​[iOS 接口文档​](../../../developer-manual/sdkintegrated/ios-sdk/ios-sdk-api/)
* [​小程序、小游戏以及内嵌页 SDK​](../../../developer-manual/sdkintegrated/other-sdk/customize-api.md)

API 中给出了埋点事件和事件级变量的上传方式。

## 4. 数据校验

在完成了【平台数据声明】，以及【代码部署】后，我们接下来需要对数据是否成功上传进行校验。

在SDK中设置了Debug 模式，您可以在开发者工具中查看数据采集日志。

以原生Android 无埋点 SDK为例：

在SDK中开启Debug：Android 无埋点 SDK &gt; [设置Debug模式](../../../developer-manual/sdkintegrated/android-sdk/auto-android-sdk.md#8-she-zhi-debug-mo-shi)。

在开发者工具中查看日志，如下图：

![](../../../.gitbook/assets/image%20%2815%29.png)

{% hint style="info" %}
其他数据校验方式

* 使用debug 工具，来帮助您进行数据的校验。具体请参考[SDK调试](../../../developer-manual/debugging/)。
* App及小程序可以使用数据校验功能校验进行[数据校验](../../../product-manual/datacenter/datacheck.md)。
{% endhint %}

