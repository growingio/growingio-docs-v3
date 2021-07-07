# iOS SDK合规说明

请升级到最新 GrowingIO iOS SDK [稳定版本](https://docs.growingio.com/v3/developer-manual/sdkintegrated/ios-sdk/iossdk-log)

* 根据 [User Privacy and Data Use](https://developer.apple.com/app-store/user-privacy-and-data-use/)，App 需要通过隐私政策说明应用采集数据
* 需要告知用户您集成了 GrowingIO SDK，并且 GrowingIO SDK 会尝试获取 IDFA、IDFV 信息用于渠道信息，并且采集用户信息进行行为分析
* GrowingIO SDK 默认启用 IDFA，如您不希望启用 IDFA，参考：[App Store 提交应用注意事项](https://docs.growingio.com/v3/developer-manual/sdkintegrated/ios-sdk/manunl-ios-sdk#3-app-store-ti-jiao-ying-yong-zhu-yi-shi-xiang)

> 2021 年 4 月 27 日，iOS 14.5 正式发布，新版本的 iOS 最主要变化如下：
>
> 自 iOS14.5、iPadOS 14.5 和 tvOS 14.5 开始，所有 App 都必须使用 AppTrackingTransparency 框架来征得用户的许可，才能对其进行跟踪或访问其设备的广告标识符。 
>
> And starting with iOS 14.5, iPadOS 14.5, and tvOS 14.5, you’ll be required to ask users for their permission to track them across apps and websites owned by other companies.

违反规定的 App 将可能面临无法上架的情况。

### 集成步骤

* 参照[无埋点SDK集成](https://docs.growingio.com/v3/developer-manual/sdkintegrated/ios-sdk/auto-ios-sdk)或[埋点SDK集成](https://docs.growingio.com/v3/developer-manual/sdkintegrated/ios-sdk/manunl-ios-sdk)

### 合规步骤

#### 隐私政策

* 您需要确保 App 有《隐私政策》，并且在用户首次启动 App 时就弹出《隐私政策》取得用户同意。
* 您需要告知用户 App 集成了 GrowingIO SDK：
  * 如果您没有使用 IDFA, 请在隐私政策中增加如下参考条款： “我们使用了GrowingIO SDK，采集您的 IDFV 信息，用于统计分析您在 App 内的使用效果。”
  * 如果您使用了 IDFA，请在隐私政策中增加如下参考条款： “我们使用了GrowingIO SDK，采集您的 IDFA 信息，用于统计分析您在 App 内的使用效果。”

#### GDPR

[General Data Protection Regulation 欧盟通用数据保护条例](https://zh.wikipedia.org/wiki/%E6%AD%90%E7%9B%9F%E4%B8%80%E8%88%AC%E8%B3%87%E6%96%99%E4%BF%9D%E8%AD%B7%E8%A6%8F%E7%AF%84)

* GrowingIO SDK 在 2.3.2+ 版本开始支持`disableDataCollect`接口，在用户不授权时不采集用户数据

```text
if (未授权隐私政策) {
    // 关闭数据采集
    [Growing disableDataCollect];
}

// 初始化SDK
[Growing startWithAccountId:@"您的项目ID"]; 
```

* 当用户授权隐私政策后，通过`enableDataCollect`接口开启数据采集

```text
// 开启数据采集
[Growing enableDataCollect];
```

{% hint style="info" %}
当使用`disableDataCollect`在用户未同意隐私政策或首次启动到同意隐私政策阶段时不采集数据, 在数据中将会较之前数据量有所下降
{% endhint %}

