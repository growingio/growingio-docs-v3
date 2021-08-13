---
description: 初始化 SDK 时配置项 API ，可以控制 SDK  的采集上报流程，另外还可接收来自 GIO 的 callback。
---

# 初始化配置项API

初始化配置项均在`Application`的`onCreate`方法中 SDK 初始化代码块中设置，下面将分类并描述含义。

示例代码

```java
import android.app.Application;
​
import com.growingio.android.sdk.collection.Configuration;
import com.growingio.android.sdk.collection.GrowingIO;
import com.growingio.android.sdk.deeplink.DeeplinkCallback;
​
import java.util.Map;
​
public class TestApplication extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        GrowingIO.startWithConfiguration(this, new Configuration()
                .disableCellularImp()
                .disableImageViewCollection(false)
                .setBulkSize(100)
                .setCellularDataLimit(1000)
                .setChannel("渠道名")
                .setDebugMode(true)
                .setDeeplinkCallback(new DeeplinkCallback() {
                    @Override
                    public void onReceive(Map<String, String> params, int error, long appAwakePassedTime) {
                    }
                }).setDiagnose(false)
                .setDisabled(false)
                .setDisableImpression(false)
                .setFlushInterval(1000)
                .setMutiprocess(true)
                .setSampling(0.34)
                .setSessionInterval(23000)
                .setTestMode(true)
                .setThrottle(false)
                .setTrackWebView(true)
                .supportMultiProcessCircle(true)
                .trackAllFragments()
                .setImeiEnable(true)
                .setGoogleAdIdEnable(true)
                .setAndroidIdEnable(true)
                .setOAIDEnable(true));
​
    }
}
```

## 基础配置API

<table>
  <thead>
    <tr>
      <th style="text-align:left">API</th>
      <th style="text-align:center">&#x9ED8;&#x8BA4;&#x503C;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
      <th style="text-align:center">&#x65E0;&#x57CB;&#x70B9;SDK&#x7248;&#x672C;&#x652F;&#x6301;</th>
      <th style="text-align:center">&#x57CB;&#x70B9;SDK&#x7248;&#x672C;&#x652F;&#x6301;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">setDebugMode</td>
      <td style="text-align:center">false</td>
      <td style="text-align:left">&#x5728;Logcat&#x4E2D;&#x8F93;&#x51FA;&#x91C7;&#x96C6;&#x65E5;&#x5FD7;</td>
      <td
      style="text-align:center">ALL</td>
        <td style="text-align:center">ALL</td>
    </tr>
    <tr>
      <td style="text-align:left">setTestMode</td>
      <td style="text-align:center">false</td>
      <td style="text-align:left">
        <p>&#x5B9E;&#x65F6;&#x53D1;&#x9001;&#x6570;&#x636E;&#xFF0C;&#x5F00;&#x542F;&#x5219;&#x4E0D;&#x9075;&#x5FAA;&#x79FB;&#x52A8;&#x7F51;&#x7EDC;&#x72B6;&#x6001;&#x4E0B;&#x6570;&#x636E;&#x53D1;&#x9001;&#x5927;&#x5C0F;&#x9ED8;&#x8BA4;
          10 M &#x9650;&#x5236;&#x4EE5;&#x53CA;&#x91C7;&#x96C6;&#x6570;&#x636E;&#x7F13;&#x5B58;
          15 &#x79D2;&#x53D1;&#x9001;&#x7B56;&#x7565;&#x3002;</p>
        <p>&#x4E3A;&#x4E86;&#x65B9;&#x4FBF;&#x5F00;&#x53D1;&#x8005;&#x67E5;&#x770B;&#x65E5;&#x5FD7;&#xFF0C;&#x4E00;&#x822C;&#x548C;<code>setDebugMode</code>&#x4E00;&#x8D77;&#x4F7F;&#x7528;&#x3002;</p>
      </td>
      <td style="text-align:center">ALL</td>
      <td style="text-align:center">ALL</td>
    </tr>
    <tr>
      <td style="text-align:left">setChannel</td>
      <td style="text-align:center">&#x65E0;</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;App&#x4E0B;&#x8F7D;&#x6E20;&#x9053;</td>
      <td style="text-align:center">ALL</td>
      <td style="text-align:center">ALL</td>
    </tr>
    <tr>
      <td style="text-align:left">useID</td>
      <td style="text-align:center">true</td>
      <td style="text-align:left">&#x662F;&#x5426;&#x5728;&#x8BA1;&#x7B97;<code>xpath</code>&#x65F6;&#x4F7F;&#x7528;&#x63A7;&#x4EF6;<code>id&#xFF0C;</code>&#x9ED8;&#x8BA4;&#x4F7F;&#x7528;</td>
      <td
      style="text-align:center">&lt;2.6.0</td>
        <td style="text-align:center">-</td>
    </tr>
  </tbody>
</table>



| API | 默认值 | 说明 | 无埋点SDK版本支持 | 埋点SDK版本支持 |
| :--- | :--- | :--- | :--- | :--- |
| setDeeplinkCallback | 无 | DeepLink 回调接口，获得自定义参数以便跳转对应 APP页 面 | &gt;=2.3.2 | ALL |
| setTrackWebView | true | 是否采集全部的`WebView,`设置为`false`时不采所有`WebView`数据 | ALL | - |
| supportMultiProcessCircle | false | 是否使用多进程圈选功能 | ALL | - |
| setMutiprocess | false | 使用了多进程必须配置，自定义事件和变量值才会多进程共享 | ALL | ALL |
| trackAllFragments | false | 是否采集所有Fragment | ALL | - |
| setHashTagEnable | false | 在`WebView`中的页面访问，是否认为点击锚点链接是一个页面浏览 | ALL | - |
| setHarmonyEnable | false | 是否识别鸿蒙系统 | &gt;=2.9.6 | &gt;=2.9.6 |

## 数据采集发送API

| API | 默认值 | 说明 | 无埋点SDK版本支持 | 埋点SDK版本支持 |
| :--- | :--- | :--- | :--- | :--- |
| setDisabled | false | SDK 是否采集数据，设置为`true`时不采集数据 | ALL | ALL |
| setSampling | 1 | 采样率\[0.01~1\],若设置sampling = 0.01，则 1% 的设备会被采集数据，每次启动会根据用户设置的采样率判断设备是否在采集的范围之内，**使用之前请咨询技术支持** | ALL | ALL |
| setSessionInterval | 30 \* 1000 | 在后台停留时长超过此值，则产生新的`sessionId`,发送`visit`事件。 | ALL | ALL |
| setFlushInterval | 15 \* 1000 | 数据刷新的最长时间间隔，默认 15 秒 。如果距离上次发送数据事件超过此时间则发送事件 | ALL | ALL |
| setThrottle | false | 是否节流发送，节流发送时`imp`不发送，不发送但是采集，`imp`为元素展示事件 | ALL | - |
| setDisableImpression | true | 是否采集`imp`事件，`imp`为元素展示事件，默认不采集`imp。需要`setDisableImpression\(false\)，同时服务端返回配置为true时才会采集。 | &gt;=2.8.11 | - |
| disableCellularImp | false | 否关闭移动蜂窝网`imp`事件采集，`imp`为元素展示事件 | ALL | - |
| setCellularDataLimit | 10 \* 1024 \* 1024 | 一天的时间之内，在移动蜂窝网下的数据最大传输量，默认 10 M。 | ALL | ALL |
| setBulkSize | 300 | 如果数据库存储数据条数大于等于`bulkSize`，则马上发送数据。 | ALL | ALL |
| setImeiEnable | true | 设置为 false 则 SDK 不采集 `imei，`适用于**海外应用市场**上架的应用。 | &gt;=2.7.8 | - |
| setAndroidIdEnable | true | 设置为 false 则 SDK 不采集 `androidid` ，适用于**海外应用市场**上架的应用。 | &gt;=2.7.8 | - |
| setGoogleAdIdEnable | true | 设置为 false 则 SDK 不采集 `GoogleAdId` ，适用于**海外应用市场**上架的应用。 | &gt;=2.7.8 | - |
| setOAIDEnable | true | 国内[移动安全联盟MSA](http://www.msa-alliance.cn/col.jsp?id=120) 联合各大手机制造商推出了 OAID ， 作为唯一广告标识符。 | &gt;=2.8.5 | - |

