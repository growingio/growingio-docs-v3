# SDK合规说明

* 根据[工业和信息化部关于开展纵深推进APP侵害用户权益专项整治行动](http://www.gov.cn/zhengce/zhengceku/2020-08/02/content_5531975.htm), App需要通过隐私政策说明应用采集数据
* 需要告知用户您集成了GrowingIO SDK, 并且GrowingIO SDK会尝试获取androidId, IMEI信息用于渠道信息, 并且采集用户信息进行行为分析

### 集成步骤

* 参照[无埋点SDK集成](https://docs.growingio.com/v3/developer-manual/sdkintegrated/android-sdk/auto-android-sdk)或[埋点SDK集成](https://docs.growingio.com/v3/developer-manual/sdkintegrated/android-sdk/manunl-android-sdk)

### 合规步骤

* GrowingIO SDK在2.3.2+版本开始支持`disableDataCollect`接口,  在用户不授权时不采集用户数据

```java
// 初始化配置
Configuration configuration = new Configuration();
// 其它初始化配置如是否开启debug等
...
// 根据隐私协议判断是否开启数据采集
if (未授权隐私政策) {
    configuration.disableDataCollect();
}
// 初始化SDK
GrowingIO.startWithConfiguration(application, configuration);
```

* 当用户授权隐私政策后, 通过`enableDataCollect`接口开启数据采集

```text
// 授权隐私政策后, 开启用户采集
GrowingIO.getInstance().enableDataCollect();
```

{% hint style="info" %}
当使用`disableDataCollect`在用户未同意隐私政策或首次启动到同意隐私政策阶段时不采集数据, 在数据中将会较之前数据量有所下降
{% endhint %}

