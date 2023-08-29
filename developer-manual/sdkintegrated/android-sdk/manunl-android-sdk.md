---
description: 埋点 SDK 只自动采集用户访问事件，需要开发同学调用相应埋点 API 采集自定义事件。
---

# 埋点 SDK 集成

埋点 SDK 的目标是使用第三方插件开发的 APP， 比如使用 Weex、APICloud 等，或不需要SDK自动采集页面浏览，元素点击行为数据的APP。

在一些第三方混合开发框架中，我们无法自动采集用户的点击事件和页面浏览事件等，需要依赖调用埋点事件或事件变量 API 来进行数据采集。

{% hint style="info" %}
如果您的 APP 使用 Android 原生开发，并且希望自动采集用户的点击事件、页面浏览事件等无埋点事件， 请集成 Android 无埋点SDK 。
{% endhint %}

## 准备条件

* 获取项目 ID，获取方法请参考"项目管理 > 项目概览 > [查看项目基本信息](../../../product-manual/projectmange/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。
* 获取 URL Scheme，在 GrowingIO 平台创建对应的应用时会生成 URL Scheme。请参考[创建应用](../../../product-manual/projectmange/application-manage.md#chuang-jian-ying-yong)。

## 1. 添加跟踪代码

{% hint style="success" %}
Gradle 编译环境：Android Studio

App 适配最低系统版本：Android 4.2 及以上
{% endhint %}

### 1. 添加依赖

{% hint style="info" %}
2.9.0 版本后仓库从 JCenter 迁移到了 Maven Central, 请使用 mavenCentral() 替换 jcenter()
{% endhint %}

**在 module 级别的 build.gradle 文件中添加`vds-android-agent`依赖、项目 ID 和 URL Scheme。**

代码示例：

```javascript
android {
    defaultConfig {
        resValue("string", "growingio_project_id", "您的项目ID")
        resValue("string", "growingio_url_scheme", "您的URL Scheme")
    }
}
dependencies {
    //GrowingIO 埋点 SDK
    implementation 'com.growingio.android:vds-android-agent:track-2.10.0'
}
```

### 2. 添加URL Scheme和应用权限

URL Scheme 是您在 GrowingIO 平台创建应用时生成的该应用的唯一标识。把 URL Scheme 添加到您的项目中，以便在使用圈选，Mobile Debugger，及深度链接功能时唤醒您的应用。

{% hint style="info" %}
URL Scheme 只能对应一个应用。当应用的包名发生变化时，需再次创建一个应用使用对应的 URL Scheme
{% endhint %}

将 URLScheme 和应用权限添加到您的 AndroidManifest.xml 中的 LAUNCHER Activity 下。

代码示例：

```aspnet
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.growingio.testdemo">
​
    <!-- GIO 需要的权限 -->
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <!-- GIO 需要的权限 -->
​
    <!--请注意<application/>标签中的name属性值（这里为android:name=".MyApplication"）必须为您的Application类-->
    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:name=".MyApplication"
        android:theme="@style/AppTheme">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
​
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
            <!--请添加这里的整个 intent-filter 区块，并确保其中只有一个 data 字段-->
            <intent-filter>
                <data android:scheme="growing.您的URL Scheme" />
                <action android:name="android.intent.action.VIEW" />
​
                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />
            </intent-filter>
            <!--请添加这里的整个 intent-filter 区块，并确保其中只有一个 data 字段-->
        </activity>
    </application>
​
</manifest>
```

{% hint style="info" %}
请添加一整个 intent-filter 区块，并确保其中只有一个 data 字段。
{% endhint %}

### 3. SDK初始化配置

请将 GrowingIO.startWithConfiguration 加在您的 Application 的 onCreate 方法中。**为使 App 合规，请参考**[**合规步骤**](../compliance/sdk-he-gui-shuo-ming.md#he-gui-bu-zhou)**。**

代码示例\*\*：\*\*

{% tabs %}
{% tab title="Java" %}
```java
public class MyApplication extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        GrowingIO.startWithConfiguration(this, new Configuration()
            .setChannel("XXX应用商店")
        );
    }
}
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
class MyApplication : Application() {
    override fun onCreate() {
        super.onCreate()
        GrowingIO.startWithConfiguration(
            this, Configuration()
                .setChannel("XXX应用商店")
        )
    }
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
1. 其中`GrowingIO.startWithConfiguration`第一个参数为`ApplicationContext`对象。
2. `setChannel`方法的参数定义了“自定义App渠道”这个维度的值，填写APP要发布的应用商店名称。
{% endhint %}

### 4. 代码混淆

如果你启用了混淆，请在你的proguard-rules.pro中加入如下代码：

{% hint style="danger" %}
**SDK 2.6.0 更新了混淆文件，前后混淆文件内容截然不同，请注意更新。**
{% endhint %}

```javascript
-keep class com.growingio.** {
    *;
}
-dontwarn com.growingio.**
-keepnames class * extends android.view.View
-keepnames class * extends android.app.Fragment
-keepnames class * extends android.support.v4.app.Fragment
-keepnames class * extends androidx.fragment.app.Fragment
-keep class android.support.v4.view.ViewPager{
    *;
}
-keep class android.support.v4.view.ViewPager$**{
    *;
}
-keep class androidx.viewpager.widget.ViewPager{
    *;
}
-keep class androidx.viewpager.widget.ViewPager$**{
    *;
}
```

如果您使用了AndRestGuard，请在白名单里添加GrowingIO。

代码示例：

```aspnet
R.string.growingio*
```

### 5 设置SDK异常上传开关 <a href="#5-she-zhi-dan-chuang-sdk-yi-chang-shang-chuan-kai-guan" id="5-she-zhi-dan-chuang-sdk-yi-chang-shang-chuan-kai-guan"></a>

SDK默认会开启收集SDK内部异常上报至服务端功能，方便开发更好的追踪SDK问题和完善SDK功能。如果您不希望收集SDK内部异常，或者和您的 crash 收集框架有冲突，您可以关闭该功能。

```
setUploadExceptionEnable(boolean uploadExceptionEnable)
```

#### 参数说明 <a href="#52-can-shu-shuo-ming" id="52-can-shu-shuo-ming"></a>

| **参数名**               | **类型**  | **必填** | **默认值** | **说明**                     |
| --------------------- | ------- | ------ | ------- | -------------------------- |
| uploadExceptionEnable | boolean | 否      | true    | 开关SDK异常上传功能，true开启，false关闭 |

#### 代码示例 <a href="#53-dai-ma-shi-li" id="53-dai-ma-shi-li"></a>

{% tabs %}
{% tab title="Java" %}
```java
GrowingIO.startWithConfiguration(this, Configuration()
         .setUploadExceptionEnable(true)
);
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
GrowingIO.startWithConfiguration(this, Configuration()
    .setUploadExceptionEnable(true)
)
```
{% endtab %}
{% endtabs %}

## 2. 重要配置

### 1. 设置Debug模式

Debug 模式：在 Android Studio 中通过 Logcat 查看 GrowingIO SDK 打印的数据采集发送日志。

在SDK初始化代码中添加如下配置：

```java
setDebugMode(boolean debugMode);
```

**参数说明**

| **参数**    | 类型      | 是否必填 | 说明                           |
| --------- | ------- | ---- | ---------------------------- |
| debugMode | boolean | 是    | 开启GrowingIO日志，true开始，默认false |

**示例代码**

{% tabs %}
{% tab title="Java" %}
```java
GrowingIO.startWithConfiguration(this,new Configuration()
    //BuildConfig.DEBUG 这样配置就不会上线忘记关闭
    .setDebugMode(BuildConfig.DEBUG)
    ...
    );
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
GrowingIO.startWithConfiguration(
    this, Configuration() //BuildConfig.DEBUG 这样配置就不会上线忘记关闭
        .setDebugMode(BuildConfig.DEBUG)
)
```
{% endtab %}
{% endtabs %}

### 2. 设置Test模式

Test模式：实时发送数据，开启则不遵循移动网络状态下数据发送大小限制以及采集数据默认缓存 15 秒发送策略。为了方便开发者查看日志，一般和`setDebugMode`一起使用。

在SDK初始化代码中添加如下配置：

```java
setTestMode(boolean testMode);
```

**参数说明**

| 参数       | 类型      | 是否必填 | 说明                    |
| -------- | ------- | ---- | --------------------- |
| testMode | boolean | 是    | 开启测试模式，true开启，默认false |

**示例代码**

{% tabs %}
{% tab title="Java" %}
```java
GrowingIO.startWithConfiguration(this,new Configuration()
    //BuildConfig.DEBUG 这样配置就不会上线忘记关闭
    .setTestMode(BuildConfig.DEBUG)
    ...
    );
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
GrowingIO.startWithConfiguration(
    this, Configuration() //BuildConfig.DEBUG 这样配置就不会上线忘记关闭
        .setTestMode(BuildConfig.DEBUG)
)
```
{% endtab %}
{% endtabs %}

### 3. 采集WebView页面数据

埋点 SDK 会采集H5页面的数据，需要增加如下特殊配置。同时H5页面**需要手动集成** [Hybrid SDK](../jin-ji-cheng-mai-dian-sdk-de-hybrid-js-sdk.md)。

```java
// 提供原生的 WebView bridge供hybrid调用, 支持hybrid事件发送
public void bridgeForWebView(WebView webView)
// 提供腾讯X5内核的WebView bridge供hybrid调用, 支持hybrid事件发送
public void bridgeForX5WebView(com.tencent.smtt.sdk.WebView x5WebView)
```

{% hint style="info" %}
SDK 2.9.0及以上版本支持该接口
{% endhint %}

**示例代例**

```
//需要在 webview 初始化后调用
GrowingIO.getInstance().bridgeForWebView(webView);
```

### 4. 设置内嵌H5页面锚点跳转触发页面浏览事件

GrowingIO SDK 默认情况下，不会把`HashTag`识别成页面 URL 的一部分，内嵌H5页面点击锚点页面跳转不计为页面浏览事件。

对于使用`HashTag`进行页面跳转的单页面网站应用来说，可以启用它来标识页面，`HashTag`的值也会记录在页面URL中。启用之后，如果用户点击页面中的锚点进行页面跳转，则发送一次页面浏览事件。

在SDK初始化代码中添加如下代码：

```java
setHashTagEnable(boolean hashTagEnable)
```

{% hint style="danger" %}
如果内嵌H5页面集成了Web JS SDK，则 Web JS SDK 中 [HashTag](../web-js-sdk/latest-jssdk.md#1.-hashtag-xi-tong-bian-liang) 配置有效，该接口调用无效
{% endhint %}

**示例代码：**

{% tabs %}
{% tab title="Java" %}
```java
GrowingIO.startWithConfiguration(this, new Configuration().setHashTagEnable(true));
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
GrowingIO.startWithConfiguration(this, Configuration().setHashTagEnable(true))
```
{% endtab %}
{% endtabs %}

**场景示例**：

点击 APP `WebView` 中“代码混淆”的锚点链接，URL 中`#`号后面为锚点，设置后 SDK 会发送页面浏览事件，它的链接为：​[https://docs.growingio.com/docs/sdk-integration/android-sdk#4-dai-ma-hun-xiao](https://docs.growingio.com/docs/sdk-integration/android-sdk#4-dai-ma-hun-xiao)

![](<../../../.gitbook/assets/image (123).png>)

SDK发送对应采集数据：

```java
{
    "u":"2e94075c-ead2-33ac-ab7f-f9611162efc4",
    "s":"78383569-3038-4bd4-b27c-349939367922",
    "tl":"Android SDK - 帮助文档",
    //t 为事件类型，page 为页面浏览事件
    "t":"page",
    "tm":1532408777047,
    "pt":"https",
    "d":"com.growingio.android.test::docs.growingio.com",
    //p 为浏览的页面
    "p":"StandardWebView::/docs/sdk-integration/android-sdk#4-dai-ma-hun-xiao",
    "rp":"https://docs.growingio.com/docs/sdk-integration/android-sdk#ji-cheng",
    "cs1":"GrowingIO",
    "appId":"fakeAppID",
    "v":"Android SDK - 帮助文档",
    "r":"WIFI",
    "gesid":434,
    "esid":153
```

### 5. 设置采集GPS数据

GrowingIO SDK 默认不采集地理位置信息。

如果您需要精确采集`GPS`数据，请在获取坐标后，调用接口设置位置信息。

{% hint style="success" %}
如果您不调用此接口也可以，我们会根据用户的`ip模糊匹配`用户所在城市地区，能够在最终的数据分析时看到`APP`用户地域分布。
{% endhint %}

```java
setGeoLocation(double latitude,double longitude);
```

**参数说明**

| 参数        | 类型     | 是否必传 | 说明 |
| --------- | ------ | ---- | -- |
| latitude  | double | 是    | 纬度 |
| longitude | double | 是    | 经度 |

**示例代码**

```java
//北京的经纬度
GrowingIO.getInstance().setGeoLocation(39.9046900000,116.4071700000);
```

{% hint style="info" %}
对应清除地理位置的方法为 clearGeoLocation()；
{% endhint %}

### 6. 多进程支持

GrowingIO SDK默认不支持多进程使用， 但是可以通过`confiuration`进行设置支持多进程。

在SDK初始化代码中添加如下代码。

```java
//支持多进程数据采集
setMutiprocess(boolean setMutiprocess);
```

**参数说明**

| 参数             | 类型      | 是否必填 | 说明                 |
| -------------- | ------- | ---- | ------------------ |
| isMultiprocess | boolean | 是    | 开启多进程数据采集。默认值false |

示例代码：

{% tabs %}
{% tab title="Java" %}
```java
GrowingIO.startWithConfiguration(this, new Configuration()
                  .setMutiprocess(true)
                  );
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
GrowingIO.startWithConfiguration(
    this, Configuration()
        .setMutiprocess(true)
)
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
1. 为什么不默认支持多进程？

跨进程通信是一个相对较慢的过程， 默认不开启， 可以满足大部分用户的要求。

2\. 哪些进程需要初始化SDK？

需要使用SDK功能的进程需要初始化SDK， 所有的UI进程 + 部分Service进程(如果这些进程中涉及手动埋点)。
{% endhint %}

### 7. GDPR数据采集开关

> SDK版本支持：2.3.2及以上

| 接口                   | 含义                              |
| -------------------- | ------------------------------- |
| disableDataCollect() | 遵守欧洲联盟出台的通用数据保护条例，用户不授权，不采集用户数据 |
| enableDataCollect()  | 遵守欧洲联盟出台的通用数据保护条例，用户授权，采集用户数据   |

**示例代码：**

```
    // 初始化配置
    Configuration configuration = new Configuration();
    // 其它初始化配置如是否开启ebug等
    ...
    // 根据数据采集开关判断
    if (<未同意隐私协议>) {
        configuration.disableDataCollect();
    }
    // 初始化SDK
    GrowingIO.startWithConfiguration(application, configuration);
```

```java
// 同意数据采集后，开启数据发送
GrowingIO.getInstance().enableDataCollect();
```

### 8. Deep Link回调参数获取

​GrowingIO SDK 提供有 Deep Link 回调接口，调用后获取回调参数，您需要根据回调参数和业务场景，添加对应的交互代码。

{% hint style="info" %}
**SDK 2.3.2** 开始提供 DeepLink Callback 接口，在 **SDK 2.8.4** 支持 App Links ，为了保证接收自定义参数并进行自定义跳转这一流程的完整性，App Links 沿用此接口，并新增一个参数，下文将详细解释。
{% endhint %}

{% hint style="success" %}
此 Callback 只有在应用收到来自 GIO Intent 的时候才会触发，您需要先在广告监测新建监测链接，并使用监测链接唤醒 APP 时触发此 allback 。

[点击了解新建监测链接。](../../api-reference/query-productid/definition/create-deeplinks.md)
{% endhint %}

在 GrowingIO SDK 代码初始化部分配置。

{% tabs %}
{% tab title="Java" %}
```java
//sdk >= 2.3.2 && sdk < 2.8.19
GrowingIO.startWithConfiguration(this, new Configuration()
                .setDeeplinkCallback(new DeeplinkCallback() {
                            @Override
                            public void onReceive(Map<String, String> params, int status) { 
                            // 这里接收您的参数，匹配键值对，跳转指定 APP 内页面
                            }
                        })
            );
//sdk >= 2.8.4, 新增参数 long appAwakePassedTime 
GrowingIO.startWithConfiguration(this, new Configuration()
                .setDeeplinkCallback(new DeeplinkCallback() {
                            @Override
                            public void onReceive(Map<String, String> params, int status, long appAwakePassedTime) { 
                            // 这里接收您的参数，匹配键值对，跳转指定 APP 内页面
                            // appAwakePassedTime 这个新的参数用来判定 APP 是否已经打开了很久才收到自定义参数，进而判断是否再继续跳转指定页面
                            }
                        })
            );
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
//sdk >= 2.3.2 && sdk < 2.8.19
GrowingIO.startWithConfiguration(
    this, Configuration()
        .setDeeplinkCallback(object : DeeplinkCallback {
            fun onReceive(params: Map<String?, String?>?, status: Int) {
                // 这里接收您的参数，匹配键值对，跳转指定 APP 内页面
            }
        })
)
//sdk >= 2.8.4, 新增参数 long appAwakePassedTime 
GrowingIO.startWithConfiguration(this, Configuration()
    .setDeeplinkCallback { params, status, appAwakePassedTime ->
        // 这里接收您的参数，匹配键值对，跳转指定 APP 内页面
        // appAwakePassedTime 这个新的参数用来判定 APP 是否已经打开了很久才收到自定义参数，进而判断是否再继续跳转指定页面
    }
)
```
{% endtab %}
{% endtabs %}

**返回值说明:**

| 返回值名称              | 类型                   | 说明                                                                                                                                                                              |
| ------------------ | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| params             | Map\<String, String> | 自定义参数，您自定义的键值对                                                                                                                                                                  |
| status             | int                  | DeeplinkCallback.SUCCESS ：自定义参数获取成功； DeeplinkCallback.PARSE\_ERROR ：解析异常；DeeplinkCallback.ILLEGAL\_URI ：非法URI； DeeplinkCallback.NO\_QUERY : 自定义参数为空                             |
| appAwakePassedTime | long                 | <p>（SDK 2.8.4新增）App 唤醒到收到 GIO callback 的时间，<strong>单位毫秒</strong>。用以判断网络状态不好的情况，应用已经打开很久，才收到回调，开发人员决定是否收到参数后仍然跳转自定义的指定页面。</p><p><strong>当返回值为 0 的时候，为 DeepLink 方式打开</strong></p> |

**示例代码**

{% tabs %}
{% tab title="Java" %}
```java
//sdk >= 2.3.2 && sdk < 2.8.19
GrowingIO.startWithConfiguration(this, new Configuration()
    .setDeeplinkCallback(new DeeplinkCallback() {
                @Override
                public void onReceive(Map<String, String> params, int status) {
                     if (status == DeeplinkCallback.SUCCESS) {
                        //获得您的自定义参数，处理您的相关逻辑
                        Log.d("TestApplication", "DeepLink 参数获取成功，params" + params.toString());
                    }
                }
            })
);
//sdk >= 2.8.4, 新增参数 long appAwakePassedTime 
GrowingIO.startWithConfiguration(this, new Configuration()
    .setDeeplinkCallback(new DeeplinkCallback() {
                @Override
                public void onReceive(Map<String, String> params, int status, long appAwakePassedTime) {
                     //成功得到自定义参数，并且从 APP 打开到收到回调时间小于 1.5 秒
                     if (status == DeeplinkCallback.SUCCESS && appAwakePassedTime < 1500) {
                        //获得您的自定义参数，处理您的相关逻辑
                        Log.d("TestApplication", "DeepLink 参数获取成功，params" + params.toString());
                    }
                }
            })
);
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
//sdk >= 2.3.2 && sdk < 2.8.19
GrowingIO.startWithConfiguration(
    this, Configuration()
        .setDeeplinkCallback(object : DeeplinkCallback {
            fun onReceive(params: Map<String?, String?>, status: Int) {
                if (status == DeeplinkCallback.SUCCESS) {
                    //获得您的自定义参数，处理您的相关逻辑
                    Log.d("TestApplication", "DeepLink 参数获取成功，params$params")
                }
            }
        })
)
//sdk >= 2.8.4, 新增参数 long appAwakePassedTime 
GrowingIO.startWithConfiguration(this, Configuration()
    .setDeeplinkCallback { params, status, appAwakePassedTime ->
        //成功得到自定义参数，并且从 APP 打开到收到回调时间小于 1.5 秒
        if (status == DeeplinkCallback.SUCCESS && appAwakePassedTime < 1500) {
            //获得您的自定义参数，处理您的相关逻辑
            Log.d("TestApplication", "DeepLink 参数获取成功，params$params")
        }
    }
)
```
{% endtab %}
{% endtabs %}

## 3. 自定义数据上传

除上述的用户行为数据（无埋点数据）之外，GrowingIO 还提供了多种 API 接口，供您上传一些自定义的数据指标及维度 ，请参考Android SDK API > [自定义数](android-sdk-api/customize-api.md)[上传API](android-sdk-api/customize-api.md)。

{% hint style="success" %}
90% 以上的用户都会上传登录用户 ID ，以便分析登录用户的数据情况。
{% endhint %}

## 4. 创建应用

{% hint style="danger" %}
**添加代码之后，请先Clean项目，然后再进行编译，并在您的 Android App 安装了 SDK 后重新启动几次 App，保证行为采集数据自动发送给 GrowingIO，以便顺利完成检测。**
{% endhint %}

在 GrowingIO 平台应用创建页面继续完成应用创建的数据检测，检测成功后应用创建成功。

## 5. 验证SDK是否正常采集数据

{% hint style="info" %}
了解 GrowingIO 平台数据采集类型请参考[数据模型](../../../introduction/datamodel/)。
{% endhint %}

GrowingIO 为您提供多种验证SDK是否正常采集数据的方式：

方式一：[Mobile Debugger](../../debugging/mobile-debugger.md)

方式二：在SDK中设置了Debug模式后，在IDE编译器控制台查看数据采集日志。

方式三：（**推荐**）[数据校验](https://docs.growingio.com/v3/product-manual/data-center/datacheck/app)
