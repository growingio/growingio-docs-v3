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
                .setBulkSize(300)
                .setCellularDataLimit(10 * 1024 * 1024)
                .setChannel("渠道名")
                .setDebugMode(true)
                .setDeeplinkCallback(new DeeplinkCallback() {
                    @Override
                    public void onReceive(Map<String, String> params, int error, long appAwakePassedTime) {
                    }
                }).setDiagnose(false)
                .setDisabled(false)
                .setDisableImpression(false)
                .setFlushInterval(10 * 1000)
                .setMutiprocess(true)
                .setSampling(0.34)
                .setSessionInterval(23 * 1000)
                .setTestMode(true)
                .setThrottle(false)
                .setTrackWebView(true)
                .supportMultiProcessCircle(true)
                .trackAllFragments()
                .setImeiEnable(true)
                .setGoogleAdIdEnable(true)
                .setAndroidIdEnable(true)
                .setRequireAppProcessesEnabled(true)
                .setOAIDEnable(true)
                .setOAIDProvideConfig(OaidProvideConfig.provideOaid(
                        context -> "<Your Oaid>"
                )));
​
    }
}
```

## 基础配置API

| API          |  默认值  | 说明                                                                                                                | 无埋点SDK版本支持 | 埋点SDK版本支持 |
| ------------ | :---: | ----------------------------------------------------------------------------------------------------------------- | :--------: | :-------: |
| setDebugMode | false | 在Logcat中输出采集日志                                                                                                    |     ALL    |    ALL    |
| setTestMode  | false | <p>实时发送数据，开启则不遵循移动网络状态下数据发送大小默认 10 M 限制以及采集数据缓存 15 秒发送策略。</p><p>为了方便开发者查看日志，一般和<code>setDebugMode</code>一起使用。</p> |     ALL    |    ALL    |
| setChannel   |   无   | 设置App下载渠道                                                                                                         |     ALL    |    ALL    |
| useID        |  true | 是否在计算`xpath`时使用控件`id，`默认使用                                                                                        |   <2.6.0   |     -     |



| API                           | 默认值   | 说明                                          | 无埋点SDK版本支持 | 埋点SDK版本支持 |
| ----------------------------- | ----- | ------------------------------------------- | ---------- | --------- |
| setDeeplinkCallback           | 无     | DeepLink 回调接口，获得自定义参数以便跳转对应 APP页 面          | >=2.3.2    | ALL       |
| setTrackWebView               | true  | 是否采集全部的`WebView,`设置为`false`时不采所有`WebView`数据 | ALL        | -         |
| supportMultiProcessCircle     | false | 是否使用多进程圈选功能                                 | ALL        | -         |
| setMutiprocess                | false | 使用了多进程必须配置，自定义事件和变量值才会多进程共享                 | ALL        | ALL       |
| trackAllFragments             | false | 是否采集所有Fragment                              | ALL        | -         |
| setHashTagEnable              | false | 在`WebView`中的页面访问，是否认为点击锚点链接是一个页面浏览          | ALL        | -         |
| setHarmonyEnable              | false | 是否识别鸿蒙系统，默认不识别                              | >=2.9.6    | >=2.9.6   |
| setReadClipBoardEnable        | true  |  是否读取剪切板信息，默认读取                             | >=2.9.8    | >=2.9.8   |
| setRequireAppProcessesEnabled | true  | 是否获取多进程信息                                   | >=2.9.12   | >=2.9.12  |

## 数据采集发送API

| API                  | 默认值                 | 说明                                                                                            | 无埋点SDK版本支持 | 埋点SDK版本支持 |
| -------------------- | ------------------- | --------------------------------------------------------------------------------------------- | ---------- | --------- |
| setDisabled          | false               | SDK 是否采集数据，设置为`true`时不采集数据                                                                    | ALL        | ALL       |
| setSampling          | 1                   | 采样率\[0.01\~1],若设置sampling = 0.01，则 1% 的设备会被采集数据，每次启动会根据用户设置的采样率判断设备是否在采集的范围之内，**使用之前请咨询技术支持** | ALL        | ALL       |
| setSessionInterval   | 30 \* 1000          | 在后台停留时长超过此值，则产生新的`sessionId`,发送`visit`事件。                                                     | ALL        | ALL       |
| setFlushInterval     | 15 \* 1000          | 数据刷新的最长时间间隔，默认 15 秒 。如果距离上次发送数据事件超过此时间则发送事件                                                   | ALL        | ALL       |
| setThrottle          | false               | 是否节流发送，节流发送时`imp`不发送，不发送但是采集，`imp`为元素展示事件                                                     | ALL        | -         |
| setDisableImpression | true                | 是否采集`imp`事件，`imp`为元素展示事件，默认不采集`imp。需要`setDisableImpression(false)，同时服务端返回配置为true时才会采集。        | >=2.8.11   | -         |
| disableCellularImp   | false               | 否关闭移动蜂窝网`imp`事件采集，`imp`为元素展示事件                                                                | ALL        | -         |
| setCellularDataLimit | 10 \* 1024 \* 1024  | 一天的时间之内，在移动蜂窝网下的数据最大传输量，默认 10 M。                                                              | ALL        | ALL       |
| setBulkSize          | 300                 | 如果数据库存储数据条数大于等于`bulkSize`，则马上发送数据。                                                            | ALL        | ALL       |
| setImeiEnable        | true                | 设置为 false 则 SDK 不采集 `imei，`适用于**海外应用市场**上架的应用。                                                | >=2.7.8    | -         |
| setAndroidIdEnable   | true                | 设置为 false 则 SDK 不采集 `androidid` ，适用于**海外应用市场**上架的应用。                                          | >=2.7.8    | -         |
| setGoogleAdIdEnable  | true                | 设置为 false 则 SDK 不采集 `GoogleAdId` ，适用于**海外应用市场**上架的应用。                                         | >=2.7.8    | -         |
| setOAIDEnable        | true                | 国内[移动安全联盟MSA](http://www.msa-alliance.cn/col.jsp?id=120) 联合各大手机制造商推出了 OAID ， 作为唯一广告标识符。       | >=2.8.5    | -         |
| setOAIDProvideConfig | OaidProvideConfig对象 | OaidProvideConfig.provideOaid() -> 手动提供OAID值 OaidProvideConfig.provideCert() -> 手动提供CERT值     | >=2.9.11   |           |

