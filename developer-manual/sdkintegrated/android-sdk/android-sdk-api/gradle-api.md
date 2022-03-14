---
description: 应用在编译时的自定义配置API。
---

# Gradle配置API

{% hint style="warning" %}
SDK支持限制：只支持**Android 无埋点 SDK**
{% endhint %}

{% hint style="info" %}
**注意，imeiEnable、androidEnable、googleAdIdEnable 配置项不支持 com.android.tools.build:gradle 3.0.x 以下版本**。
{% endhint %}

| API              | 默认值  | 说明                                                                                                                                                         | 无埋点SDK版本支持 | 埋点SDK版本支持 |
| ---------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------- |
| imeiEnable       | true | 为了海外应用市场上架应用，设置为 false 则 SDK 不采集 imei 。在编译期配置将删除该部分的采集代码，后续配置（初始化或者运行时）将失效。                                                                                | >=2.7.8    |           |
| androidIdEnable  | true | 为了海外应用市场上架应用，设置为 false 则 SDK 不采集 `androidId` 。**在编译期配置将删除该部分的采集代码，后续配置（初始化或者运行时）将失效。**                                                                     | >=2.7.8    |           |
| googleAdIdEnable | true | 为了海外应用市场上架应用，设置为 false 则 SDK 不采集 `GoogleAdId` 。**在编译期配置将删除该部分的采集代码，后续配置（初始化或者运行时）将失效。**                                                                    | >=2.7.8    |           |
| oaidEnable       | true | <p>国内<a href="http://www.msa-alliance.cn/col.jsp?id=120">移动安全联盟MSA</a> 联合各大手机制造商推出了 OAID ， 作为唯一广告标识符。</p><p><strong>设置为 false 则运行时和初始化的配置则无效。</strong></p> | >=2.8.5    |           |

```java
android {    ···}
// 须位于 android 代码块下
growingio {
    defaultConfig {
        imeiEnable true
        androidIdEnable true
        googleAdIdEnable true
    }
​
    buildTypes {
        googlePlay {
            imeiEnable false
            andoridIdEnable false
            googleAdIdEnable true
        }
    }
}
```
