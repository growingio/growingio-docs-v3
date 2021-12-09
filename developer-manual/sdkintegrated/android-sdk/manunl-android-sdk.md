---
description: 埋点 SDK 只自动采集用户访问事件，需要开发同学调用相应埋点 API 采集自定义事件。
---

# 埋点 SDK 集成

埋点 SDK 的目标用户是使用第三方插件开发的 APP， 比如使用 Weex、APICloud 等。在这些平台中，我们无法自动采集用户的点击事件和页面浏览事件等，需要依赖调用自定义事件和变量 API 来进行数据采集。

{% hint style="info" %}
如果您的 APP 使用 Android 原生开发，并且希望自动采集用户的点击事件、页面浏览事件等无埋点事件， 请集成 Android 无埋点SDK 。
{% endhint %}

前提条件

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
    implementation 'com.growingio.android:vds-android-agent:track-2.9.9'
}
```

### 2. 添加URL cheme和应用权限

**在当前Android项目的配置文件AndroidManifest.xml 中的 LAUNCHER Activity 下添加URL Scheme，以便在使用Mobile Debugger的时候通过DeepLink方式唤醒您的程序。**

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

请将以下 GrowingIO.startWithConfiguration加在您的Application 的 onCreate 方法中

代码示例

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
1. 请确保将代码添加在`Application`的`onCreate`方法中，添加到其他方法中可能导致数据不准确。
2. 其中`GrowingIO.startWithConfiguration`第一个参数为`ApplicationContext`对象。&#x20;
3. `setChannel`方法的参数定义了“自定义App渠道”这个维度的值。
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

SDK会收集SDK内部异常上报服务端，方便开发更好的追踪SDK的问题，和完善SDK的功能。如果您不想帮助我们产品完善功能，或者和您的crash收集框架有冲突，您可以选择关闭此功能。

#### 5.1 setUploadExceptionEnable <a href="#5-1-setuploadexceptionenable" id="5-1-setuploadexceptionenable"></a>

异常消息上报开关

```
setUploadExceptionEnable(boolean uploadExceptionEnable)
```

#### 5.2 参数说明 <a href="#52-can-shu-shuo-ming" id="52-can-shu-shuo-ming"></a>

| **参数名**               | **类型**  | **必填** | **默认值** | **说明**                     |
| --------------------- | ------- | ------ | ------- | -------------------------- |
| uploadExceptionEnable | boolean | 否      | true    | 开关SDK异常上传功能，true开启，false关闭 |

#### 5.3 代码示例 <a href="#53-dai-ma-shi-li" id="53-dai-ma-shi-li"></a>

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

### 1. 设置Debug模式（setDebugMode）

查看数据采集发送日志，能够在Android Studio中通过Logcat查看GrowingIO打印的数据发送日志。

在App的Application onCrate初始化SDK位置添加配置。

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

### 2. 设置Test模式（setTestMode）

实时发送数据，开启则不遵循移动网络状态下数据发送大小限制以及采集数据缓存30秒发送策略。为了方便开发者查看日志，一般和`setDebugMode`一起使用。

在App的Application onCrate初始化SDK位置添加配置。

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

### 3. 采集GPS数据（setGeoLocation）

精确采集`GPS`数据，请在获取坐标后，调用接口设置位置信息。当用户下一次切换页面，或者发生点击行为时，`GPS`数据会被发送回`GrowingIO`。

{% hint style="success" %}
如果您不调用此接口也可以，我们会根据用户的`ip`定义用户位置，能够在最终的数据分析时看到`APP`用户地域分布。
{% endhint %}

```java
GrowingIO.getInstance().setGeoLocation(double latitude,double longitude);
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
对应的清除地理位置的方法为 clearGeoLocation（）；
{% endhint %}

### 4. 多进程支持（setMutiprocess）

多进程支持，`SDK`默认不支持多进程使用， 但是可以通过`confiuration`进行设置支持多进程。 在`Application onCreate` 中初始化SDK代码块中配置。

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
1.  为什么不默认支持多进程？

    跨进程通信是一个相对较慢的过程， 默认不开启， 可以满足大部分用户的要求。

    1. 哪些进程需要初始化SDK？

    需要使用SDK功能的进程需要初始化SDK， 所有的UI进程 + 部分Service进程(如果这些进程中涉及手动埋点)。
{% endhint %}

### 5. GDPR数据采集开关

> SDK版本支持：2.3.2及以上

| 接口                   | 含义                              |
| -------------------- | ------------------------------- |
| disableDataCollect() | 遵守欧洲联盟出台的通用数据保护条例，用户不授权，不采集用户数据 |
| enableDataCollect()  | 遵守欧洲联盟出台的通用数据保护条例，用户授权，采集用户数据   |

### 6. Deep Link回调参数获取（setDeeplinkCallback）

​通过获取回调参数，GrowingIO SDK将会传递指定活动页面参数至您的App，请根据此参数和业务场景，执行相关的交互。

在 GrowingIO SDK 代码初始化部分配置。

{% tabs %}
{% tab title="Java" %}
```java
GrowingIO.startWithConfiguration(this, new Configuration()
                .setDeeplinkCallback(new DeeplinkCallback() {
                            @Override
                            public void onReceive(Map<String, String> params, int status, long time) { 
                            // 这里接收您的参数，匹配键值对，跳转指定 APP 内页面
                            }
                        })
            );
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
GrowingIO.startWithConfiguration(
    this, Configuration()
        .setDeeplinkCallback(object : DeeplinkCallback {

            override fun onReceive(params: MutableMap<String, String>?, status: Int, longTime: Long) {
                // 这里接收您的参数，匹配键值对，跳转指定 APP 内页面
            }
        })
)
```
{% endtab %}
{% endtabs %}

**返回值说明**

| 返回值名称  | 类型                  | 说明                                                                                                                                                   |
| ------ | ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| params | Map\<string,string> | 自定义参数，您自定义的键值对                                                                                                                                       |
| status | int                 | DeeplinkCallback.SUCCESS ：自定义参数获取成功； DeeplinkCallback.PARSE\_ERROR ：解析异常；DeeplinkCallback.ILLEGAL\_URI ：非法URI； DeeplinkCallback.NO\_QUERY : 自定义参数为空。 |

**示例代码**

{% tabs %}
{% tab title="Java" %}
```java
GrowingIO.startWithConfiguration(this, new Configuration()
    .setDeeplinkCallback(new DeeplinkCallback() {
                @Override
                public void onReceive(Map<String, String> params, int status,long time) {
                     if (status == DeeplinkCallback.SUCCESS) {
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
GrowingIO.startWithConfiguration(this, Configuration()
    .setDeeplinkCallback { params, status, time ->
        if (status == DeeplinkCallback.SUCCESS) {
            //获得您的自定义参数，处理您的相关逻辑
            Log.d("TestApplication", "DeepLink 参数获取成功，params$params")
        }
    }
)
```
{% endtab %}
{% endtabs %}

## 3. 自定义数据上传

GrowingIO 提供多种 API 接口，供您上传一些自定义的数据指标及维度 ，请参考Android SDK API > [自定义数](android-sdk-api/customize-api.md)[上传API](android-sdk-api/customize-api.md)。

## 4. 创建应用

{% hint style="danger" %}
**添加代码之后，请先Clean项目，然后再进行编译，并在你的 Android App 安装了 SDK 后重新启动几次 App，保证行为采集数据自动发送给 GrowingIO，以便顺利完成检测。**
{% endhint %}

在GrowingIO平台的应用创建页面继续完成应用创建的数据检测，检测成功后应用创建成功。

## 5. 验证SDK是否正常采集数据 <a href="#5-yan-zheng-sdk-shi-fou-zheng-chang-cai-ji-shu-ju" id="5-yan-zheng-sdk-shi-fou-zheng-chang-cai-ji-shu-ju"></a>

了解GrowingIO平台数据采集类型请参考[数据模型](../../../introduction/datamodel/)。

GrowingIO为您提供多种验证SDK是否正常采集数据的方式：

方式一：[Mobile Debugger​](../../debugging/mobile-debugger.md)

方式二：在SDK中设置了Debug模式后，在IDE编译器控制台查看数据采集日志。

方式三：[数据校验](https://docs.growingio.com/v3/product-manual/data-center/datacheck/app)
