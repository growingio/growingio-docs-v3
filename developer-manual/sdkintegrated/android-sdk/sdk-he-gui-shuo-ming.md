# SDK合规说明

* 根据[工业和信息化部关于开展纵深推进APP侵害用户权益专项整治行动](http://www.gov.cn/zhengce/zhengceku/2020-08/02/content_5531975.htm)，App 需要通过隐私政策说明应用采集数据
* 需要告知用户您集成了 GrowingIO SDK，并且 GrowingIO SDK 会尝试获取 androidId，IMEI 信息用于渠道信息，并且采集用户信息进行行为分析

### 集成步骤

* 参照[无埋点SDK集成](https://docs.growingio.com/v3/developer-manual/sdkintegrated/android-sdk/auto-android-sdk)或[埋点SDK集成](https://docs.growingio.com/v3/developer-manual/sdkintegrated/android-sdk/manunl-android-sdk)

### 合规步骤

* 如您的 App 需要通过第三方安全检测，建议在隐私政策授权成功之后，再初始化 GrowingIO SDK（版本需在 2.9.1 及以上，2.9.1 以下会造成 VISIT 事件丢失、部分数据不正常的情况）

```text
if (授权隐私政策后) {
    // 初始化配置
    Configuration configuration = new Configuration();
    // 其它初始化配置如是否开启ebug等
    ...
    // 初始化SDK
    GrowingIO.startWithConfiguration(application, configuration);
}
```

* GrowingIO SDK 在 2.3.2+ 版本开始支持`disableDataCollect`接口，可在用户不同意数据采集时不发送数据

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

* 当用户同意数据采集后，通过`enableDataCollect`接口开启数据发送

```text
// 同意数据采集后，开启数据发送
GrowingIO.getInstance().enableDataCollect();
```

{% hint style="info" %}
当使用`disableDataCollect`在用户未同意数据采集阶段 SDK 不发送数据，数据量将会较之前有所下降
{% endhint %}

