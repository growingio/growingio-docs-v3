# Android SDK合规说明

请升级到最新 GrowingIO Android SDK [稳定版本](https://docs.growingio.com/v3/developer-manual/sdkintegrated/android-sdk/androidsdk-log) 及以上

* 根据[工业和信息化部关于开展纵深推进APP侵害用户权益专项整治行动](http://www.gov.cn/zhengce/zhengceku/2020-08/02/content_5531975.htm)，App 需要通过隐私政策说明应用采集数据
* 需要告知用户您集成了 GrowingIO SDK，并且 GrowingIO SDK 会尝试获取 ANDROID\_ID，IMEI 信息用于渠道信息，并且采集用户信息进行行为分析
* 为减小您的 App 安装包大小，版本 2.9.3 及以下，GrowingIO SDK 中圈选与 Mobile Debugger 功能相关代码通过热更新方式集成。自版本 2.9.4 起，相关代码将直接集成在 GrowingIO SDK 中

### 集成步骤

参照[无埋点SDK集成](https://docs.growingio.com/v3/developer-manual/sdkintegrated/android-sdk/auto-android-sdk)或[埋点SDK集成](https://docs.growingio.com/v3/developer-manual/sdkintegrated/android-sdk/manunl-android-sdk)

#### 隐私政策

如您的 App 需要通过第三方安全检测，建议在隐私政策授权成功之后，再初始化 GrowingIO SDK（版本需在 2.9.1 及以上，2.9.1 以下会造成 visit 事件丢失、部分数据不正常的情况）

#### Google Play

如您的 App 需要在 Google Play 分发，依据 Google Play [相关政策](https://support.google.com/googleplay/android-developer/answer/9888379?hl=zh-Hans&ref_topic=9877467#zippy=%2C%E5%B8%B8%E8%A7%81%E8%BF%9D%E8%A7%84%E8%A1%8C%E4%B8%BA%E7%A4%BA%E4%BE%8B)，请务必升级至版本 2.9.4 及以上

### 合规步骤

#### GDPR

[General Data Protection Regulation 欧盟通用数据保护条例](https://zh.wikipedia.org/wiki/%E6%AD%90%E7%9B%9F%E4%B8%80%E8%88%AC%E8%B3%87%E6%96%99%E4%BF%9D%E8%AD%B7%E8%A6%8F%E7%AF%84)

GrowingIO SDK 提供`disableDataCollect`接口，可在用户不同意数据采集时不发送数据

```java
// 初始化配置
Configuration configuration = new Configuration();
// 其它初始化配置如是否开启ebug等
...
// 根据数据采集开关判断
if (未同意数据采集) {
    configuration.disableDataCollect();
}
// 初始化SDK
GrowingIO.startWithConfiguration(application, configuration);
```

当用户同意数据采集后，通过`enableDataCollect`接口开启数据发送

```java
// 同意数据采集后，开启数据发送
GrowingIO.getInstance().enableDataCollect();
```

{% hint style="info" %}
当使用`disableDataCollect`在关闭数据采集阶段， SDK 不发送数据，数据量将会较之前有所下降
{% endhint %}

