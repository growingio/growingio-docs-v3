# 访问用户变量

访问用户变量用来保存用户在非登录情况下跟用户本身相关的信息，例如用户的性别、A/B 测试分组等等。不建议在访问用户变量中保存跟交互行为相关的信息，例如当前正在浏览的商品，当前正在查看的某一个 SaaS 项目。这些随着用户的交互行为会发生变化的信息 GrowingIO 建议使用页面变量和转化变量来保存。

**不同于登录用户变量，访问用户变量适用于在对非登录状态下的访问用户进行标记**，便于后续做用户信息的相关分析。在添加所需要设置的访问用户变量的代码之前，需要在 GrowingIO 产品的`自定义事件和变量`管理页面配置访问用户级变量。

当前 GrowingIO 访问用户变量支持 Web、APP、微信小程序等平台；

* ​[​](https://docs.growingio.com/docs/sdk-integration/web-js-sdk/web-js-sdk-api#16-she-zhi-fang-wen-yong-hu-ji-bian-liang-visitorset)JS SDK：v2.1.17 及以上版本（web debugger 需要升级到 v1.1.1）
* Android Native SDK：v2.4.0 及以上版本
* iOS Native SDK：v2.4.0 及以上版本
* 小程序 SDK：始终支持

## 访问用户简介 <a id="fang-wen-yong-hu-jian-jie"></a>

访问用户是 GrowingIO 对访问您的应用（包括网页、App、微信小程序等，下同）的用户的一种识别机制。每一个访问您的应用的用户都会在对应的设备中生成并记录一个唯一的 ID，我们称之为访问用户 ID。

对于不同平台类型的应用，GrowingIO 提供了多种识别方案，从而尽可能的实现对用户的唯一标识。访问用户在不同平台的标识请参考[访问用户模型文档](../../datamodel/usermodel/#fang-wen-yong-hu)。

## 配置和上传 <a id="pei-zhi-he-shang-chuan"></a>

### **第一步：在 “事件和变量”中完成配置** <a id="di-yi-bu-zai-shi-jian-he-bian-liang-zhong-wan-cheng-pei-zhi"></a>

具体的将自定义变量添加到网站或者移动应用上之前，GrowingIO 要求先在打点管理的界面上进行变量的声明操作，然后再开展具体的添加自定义变量的操作。

配置方式参考[用户变量](../../../product-manual/data-center/data-management/user.md)。

### **第二步：代码部署** <a id="di-er-bu-dai-ma-bu-shu"></a>

完成了配置后，即可在代码中完成以上设计的 “自定义事件和变量” 的部署。具体的说，就是调用 GrowingIO 提供的 API 接口，上传数据。

* ​[JS 接口文档​](../../../kai-fa-zhe-wen-dang/sdkintegrated/web-js-sdk/web-sdk-api/)
* ​[Android 接口文档​](../../../kai-fa-zhe-wen-dang/sdkintegrated/android-sdk/android-sdk-api/)
* ​[iOS 接口文档​](../../../kai-fa-zhe-wen-dang/sdkintegrated/ios-sdk/ios-sdk-api/)
* [​小程序、小游戏以及内嵌页 SDK​](../../../kai-fa-zhe-wen-dang/sdkintegrated/other-sdk/customize-api.md)

API中给出了访问用户变量的上传方式

## **用户变量的持久性范围** <a id="yong-hu-bian-liang-de-chi-jiu-xing-fan-wei"></a>

访问用户变量持久性范围是 4 小时。所有的都统计都是基于最近 4 小时的数据，如果同一个维度值设置多次，取最后一次。建议用户每次访问时重新设置。

