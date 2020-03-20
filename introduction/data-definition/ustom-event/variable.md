# 埋点事件级变量

## 第一步：从数据需求到具体 “指标 + 维度” <a id="di-yi-bu-cong-shu-ju-xu-qiu-dao-ju-ti-zhi-biao-wei-du"></a>

从一个实际场景出发，我们需要确定在分析中需要用到哪些量化的值，然后用什么样的维度来分解这些值。例如，对于电商在分析用户下单情况时，用户的下单量就是我们需要量化的“指标”，而每个订单所含具体商品、商品分类、优惠券信息等就是“维度”。那么对于下单这件事，我们就可以这样设计 ”指标 + 维度“：

* 指标：
  * 订单总量
* 维度：
  * 商品 ID/名称
  * 商品 SKU
  * 优惠券名称
  * 收货地址

    ...

上文中讲到，"订单总量" 这个指标需要用 ”埋点事件“ 来实现；而商品 ID/名称、优惠券名称等维度，则可以通过 **"埋点事件级变量"**来实现。

## 第二步：在 ”埋点管理“ 中完成配置 <a id="di-er-bu-zai-mai-dian-guan-li-zhong-wan-cheng-pei-zhi"></a>

当我们完成 ”指标 + 维度“ 的设计之后，请勿直接开始代码的部署，需要先到 GrowingIO 平台找数据管理功能，在界面中完成对应的配置。

#### **配置方式请参考**[**事件变量**](../../../product-manual/datacenter/datamanage/variable/event.md)**。** <a id="zi-ding-yi-shi-jian-pei-zhi"></a>

## 第三步：代码部署 <a id="di-san-bu-dai-ma-bu-shu"></a>

在完成了配置后，即可在代码中完成以上设计的 “自定义事件和变量” 的部署。具体的说，就是调用 GrowingIO 提供的 API 接口，上传数据。

* [JS 接口文档​](../../../developer-manual/sdkintegrated/web-js-sdk/web-sdk-api/)
* ​[Android 接口文档​](../../../developer-manual/sdkintegrated/android-sdk/android-sdk-api/)
* ​[iOS 接口文档​](../../../developer-manual/sdkintegrated/ios-sdk/ios-sdk-api/)
* [​小程序、小游戏以及内嵌页 SDK​](../../../developer-manual/sdkintegrated/other-sdk/customize-api.md)

API 中给出了埋点事件和埋点事件变量的上传方式。

