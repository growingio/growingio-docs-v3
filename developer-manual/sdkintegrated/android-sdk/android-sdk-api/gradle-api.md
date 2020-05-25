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

| API | 默认值 | 说明 | 无埋点SDK版本支持 | 埋点SDK版本支持 |
| :--- | :--- | :--- | :--- | :--- |


| imeiEnable | true | 为了海外应用市场上架应用，设置为 false 则 SDK 不采集 `imei` 。**在编译期配置将删除该部分的采集代码，后续配置（初始化或者运行时）将失效。** | &gt;=2.7.8 | - |
| :--- | :--- | :--- | :--- | :--- |


| androidIdEnable | true | 为了海外应用市场上架应用，设置为 false 则 SDK 不采集 `androidId` 。**在编译期配置将删除该部分的采集代码，后续配置（初始化或者运行时）将失效。** | &gt;=2.7.8 | - |
| :--- | :--- | :--- | :--- | :--- |


| googleAdIdEnable | true | 为了海外应用市场上架应用，设置为 false 则 SDK 不采集 `GoogleAdId` 。**在编译期配置将删除该部分的采集代码，后续配置（初始化或者运行时）将失效。** | &gt;=2.7.8 | - |
| :--- | :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">oaidEnable</th>
      <th style="text-align:left">ture</th>
      <th style="text-align:left">
        <p>&#x56FD;&#x5185;<a href="http://www.msa-alliance.cn/col.jsp?id=120">&#x79FB;&#x52A8;&#x5B89;&#x5168;&#x8054;&#x76DF;MSA</a> &#x8054;&#x5408;&#x5404;&#x5927;&#x624B;&#x673A;&#x5236;&#x9020;&#x5546;&#x63A8;&#x51FA;&#x4E86;
          OAID &#xFF0C; &#x4F5C;&#x4E3A;&#x552F;&#x4E00;&#x5E7F;&#x544A;&#x6807;&#x8BC6;&#x7B26;&#x3002;</p>
        <p><b>&#x8BBE;&#x7F6E;&#x4E3A; false &#x5219;&#x8FD0;&#x884C;&#x65F6;&#x548C;&#x521D;&#x59CB;&#x5316;&#x7684;&#x914D;&#x7F6E;&#x5219;&#x65E0;&#x6548;&#x3002;</b>
        </p>
      </th>
      <th style="text-align:left">&gt;=2.8.5</th>
      <th style="text-align:left">-</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>```java
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

