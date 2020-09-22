---
description: 无埋点 SDK 具备自动采集基本的用户行为事件，比如访问和行为数据等。
---

# 无埋点 SDK集成

## 准备条件

获取项目ID，请参考[查看项目基本信息](../../../product-manual/projectmange/details.md)。

获取URL Scheme，在GrowingIO平台创建对应的应用时会生成URL Scheme。请参考[创建应用](../../../product-manual/projectmange/application-manage.md#chuang-jian-ying-yong)。

{% hint style="info" %}
使用GrowingIO平台创建相应的应用，平台在应用创建界面自动为您生成已加载当前项目ID、URL Scheme的跟踪代码。
{% endhint %}

## 1. 添加依赖代码

{% hint style="success" %}
Gradle编译环境：Android Studio

App适配最低系统版本：Android 4.2 及以上
{% endhint %}

### 1. 添加工程依赖

在project级别的build.gradle文件中添加`vds-gradle-plugin`依赖。

```javascript
buildscript {
    repositories {
        jcenter()
        google()
    }
    dependencies {
        //gradle 建议版本
        classpath 'com.android.tools.build:gradle:3.2.1'
        //GrowingIO 无埋点 SDK
        classpath 'com.growingio.android:vds-gradle-plugin:autotrack-2.8.23'
    }
}
```

在 module 级别的 build.gradle 文件中添加`com.growingio.android`插件、`vds-android-agent`依赖和对应的资源。

代码示例：

```javascript
apply plugin: 'com.android.application'
//添加 GrowingIO 插件
apply plugin: 'com.growingio.android'
android {
    defaultConfig {
        resValue("string", "growingio_project_id", "您的项目ID")
        resValue("string", "growingio_url_scheme", "您的URL Scheme")
    }
}
dependencies {
    //GrowingIO 无埋点 SDK
    implementation 'com.growingio.android:vds-android-agent:autotrack-2.8.23'
}
```

### 2. 添加 URL Scheme 和应用权限

URL Scheme 是您在 GrowingIO 平台创建应用时生成的该应用的唯一标识。把 URL Scheme 添加到您的项目，以便我们唤醒您的应用。

将应用的 URLScheme 和应用权限添加到你的 AndroidManifest.xml 中的 LAUNCHER Activity 下。

代码示例：

```aspnet
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.growingio.testdemo">

    <!-- GIO 需要的权限 -->
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <!-- GIO 需要的权限 -->

    <!--请注意<application/>标签中的name属性值（这里为android:name=".MyApplication"）必须为您的Application类-->
    <application
        android:name=".MyApplication"
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
            <!--请添加这里的整个 intent-filter 区块，并确保其中只有一个 data 字段-->
            <intent-filter>
                <data android:scheme="growing.您的URL Scheme" />
                <action android:name="android.intent.action.VIEW" />
                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />
            </intent-filter>
            <!--请添加这里的整个 intent-filter 区块，并确保其中只有一个 data 字段-->
        </activity>
    </application>
</manifest>
```

{% hint style="danger" %}
请添加一整个 intent-filter 区块，并确保其中只有一个 data 字段。

建议不要尝试修改或者合并 GIO 的 intent filter ，[Google Andorid 官方解释](https://developer.android.com/training/app-links/deep-linking#adding-filters)。
{% endhint %}

### 3. SDK初始化配置

SDK的初始化时机必须在 Application 的 onCreate 方法中进行。

请将 GrowingIO.startWithConfiguration 加在您的 Application 的 onCreate 方法中

```javascript
public class MyApplication extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        GrowingIO.startWithConfiguration(this, new Configuration()
            .trackAllFragments()
            // 建议使用 BuildConfig 设置
            .setChannel("XXX应用商店")
        );
    }
}
```

{% hint style="info" %}
1. 请确保将代码添加在`Application`的`onCreate`方法中，添加到其他方法中可能导致数据不准确。
2. 其中`GrowingIO.startWithConfiguration`第一个参数为`ApplicationContext`对象。 
3. `setChannel`方法的参数定义了“自定义App渠道”这个维度的值。
4. `trackAllFragments`方法作用是将 APP 内部的所有`Fragment`标记认为可以代表一个页面。 常见于`Activity` 中包含多个 `Fragment`， 在业务场景上这里的每一个 Fragment 都可以代表一个页面。例如点击 Tab 切换页面。
{% endhint %}

{% hint style="danger" %}
**注意事项**

`trackAllFragments`方法如果在初始化时调用，APP 内部的 Fragment 将代替 Activity 作为页面，一个 Activity 中包含多个 Fragment 时大概率会是面积最大的 Fragment 作为当前的页面事件\( Page \)。
{% endhint %}

### 4. 代码混淆

如果你启用了混淆，请在你的 proguard-rules.pro 中加入如下代码：

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

如果您使用了 AndRestGuard，请在白名单里添加 GrowingIO。

代码示例：

```aspnet
R.string.growingio*
```

### **5. lambda 表达式支持配置**

lambda 表达式目前业界主流两种，分别为 retrolambda 和 AndroidStudio 支持的 lambda。

GrowingIO 的SDK 只支持 AndroidStudio 自带的 lambda 表达式。

* 在SDK版本&lt;2.7.4时，对于 `android.enableD8.desugaring = true` 未做兼容。 在`com.android.tools.build:gradle:3.2.1` 之后， Google默认开启 `desugaring` 特性， 暂时需要用户手动关闭。

```java
//关闭方法：在项目根目录中 gradle.properties 文件中增加以下配置：
android.enableD8.desugaring=false
```

* 在SDK版本&gt;=2.7.4时，我们兼容了`android.enableD8.desugaring = true`，无需再做配置。

### 6 设置弹窗SDK异常上传开关 <a id="5-she-zhi-dan-chuang-sdk-yi-chang-shang-chuan-kai-guan"></a>

弹窗SDK会收集SDK内部异常上报服务端，方便开发更好的追踪弹窗SDK的问题，和完善弹窗SDK的功能。如果您不想帮助我们弹窗产品完善功能，或者和您的crash收集框架有冲突，您可以选择关闭此功能。

#### 6.1 setUploadExceptionEnable <a id="5-1-setuploadexceptionenable"></a>

弹窗异常消息上报开关

```text
setUploadExceptionEnable(boolean uploadExceptionEnable)
```

#### 6.2 参数说明 <a id="52-can-shu-shuo-ming"></a>

| **参数名** | **类型** | **必填** | **默认值** | **说明** |
| :--- | :--- | :--- | :--- | :--- |
| uploadExceptionEnable | boolean | 是 | true | 开关SDK异常上传功能，true开启，false关闭 |

#### 6.3 代码示例 <a id="53-dai-ma-shi-li"></a>

```text
GrowingIO.startWithConfig(this, new GTouchConfig()
                .setUploadExceptionEnable(true)
                ...
                );
```

## 2. 重要配置

### 1. 自定义点击事件

如果您有自定义的控件重写了`View`的`onTouchEvent`方法来判断和处理点击事件，那么必须调用它的`PerformClick`，并且设置相应的`onClickListener`。

或者使用手动调用系统点击事件方法。 请参考[点击事件采集逻辑。](faq/class1.md#2-dian-ji-shi-jian-cai-ji-luo-ji-shi-shen-me)

### 2. 设置页面别名

对于安卓应用，页面指的是`Activity`或者`Fragment`。

有些时候，当您代码中的原有页面标题不足以支持业务人员对页面进行识别时，您可以使用此接口设置一个容易识别的页面名称来替换页面标题字段。

为处理这种场景，我们提供了取别名的方法，方法如下：

```java
GrowingIO.setPageName(Activity activity, String name)
```

如果您设置的的对象是`Fragment`，将上方的`Activity`替换为`Fragment`即可。

**我们用**`Activity`**来举例，具体说明它的用法。**

1. 某个应用的商品列表页是用`FeedActivity`实现的，所以默认的页面名称都是`FeedActivity`。
2. 现在我们想区分衣物类商品列表和食品类商品列表，分别看它们的浏览量，可以在`onCreate`方法中添加如下代码：

```java
public class FeedActivity extends Activity {     
    @Override     
    protected void onCreate(Bundle savedInstanceState) {         
        super.onCreate(savedInstanceState);         
        GrowingIO.getInstance().setPageName(this, "Clothing");
     }
 }
```

{% hint style="info" %}
1. 必须在该`Activity`的`onCreate`方法中完成该属性的赋值操作。
2. 页面别名建议设置为汉字、字母、数字和下划线的组合。
3. 为查看数据方便，请尽量对 iOS 和安卓的同功能页面取不同的名称。
{% endhint %}

### 3. 设置界面元素内容

SDK 默认不会采集 `ImageView` 的内容，如果您需要区分不同的`ImageView`，可以使用 `contentDescription` 来标记，也可以调用下方的方法来设置：

```java
GrowingIO.setViewContent(View view, String contentDescription);
```

### 4. 设置界面元素ID

SDK 会使用 Layout 文件中的 ID 来识别一个元素。

如果部分元素在 Layout 文件中没有 ID，建议在 Layout 文件中添加。

对于动态生成的元素，可以使用如下方法对它设置唯一的 ID：

```java
GrowingIO.setViewID(View view, String id);
```

{% hint style="info" %}
1. 如果在 ViewGroup 上设置 ID 的话，SDK 会忽略他所有子元素的默认 ID（就是写在 xml 文件里的）只会使用 GrowingIO.setViewID 设置的 ID。
2. ID 只能设置为字母、数字和下划线的组合。
3. 对于已经集成过旧版 SDK \(1.x\) 并圈选过的应用，对某个元素设置 ID 后再圈选它，指标数值会从零开始计算，类似初次集成 SDK 后发版的效果，但不影响之前圈选的其它指标数据。如果不希望出现这种情况，请不要使用这个方法。
{% endhint %}

### 5. 忽略元素

如果您需要不采集某些元素，比如**倒计时元素**或**涉及隐私的内容**，可以使用此接口。另外如果想禁止 WebView 的数据采集，也可调用此接口。

```java
GrowingIO.ignoreView(View view)
```

### **6. 设置元素对象**

如果元素自身的内容并不能代表具体的意义，可以使用元素对象来标识。

例如：在商品`ListView`添加购物车的场景中，每个商品`item`都含有一个加入购物车按钮，这时无法区分商品`item`与将它加入购物车按钮的一对一关系，此时调用此方法增加描述。

```java
GrowingIO.setViewInfo(view view, String info);
```

{% hint style="info" %}
适用于原有元素内容含义不大，需要添加描述的场景。
{% endhint %}

### 7. 用户浏览事件的半自动采集配置

> **SDK版本支持：&gt;=2.8.4**

{% hint style="info" %}
「用户浏览事件」半自动采集方案已经上线，详细配置请参考[Android半自动采集浏览事件](android-imp.md)。

* 事件/元素采集更具针对性，提升采集效率
* 优化采集逻辑，贴合业务场景，提升数据准确性
* 浏览事件关联自定义事件和变量，减少研发埋点工作量
{% endhint %}

### 8. 设置Debug模式

查看数据采集发送日志，能够在 Android Studio 中通过 Logcat 查看GrowingIO 打印的数据发送日志。

在 App 的 Application onCreate 初始化 SDK 位置添加配置。

```java
setDebugMode(boolean debugMode);
```

**参数说明**

| **参数** | 类型 | 是否必填 | 说明 |
| :--- | :--- | :--- | :--- |
| debugMode | boolean | 是 | 开启GrowingIO日志，true开始，默认false |

**示例代码**

```java
GrowingIO.startWithConfiguration(this,new Configuration()
    //BuildConfig.DEBUG 这样配置就不会上线忘记关闭
    .setDebugMode(BuildConfig.DEBUG));
```

### 9. 设置Test模式

实时发送数据，开启则不遵循移动网络状态下数据发送大小限制以及采集数据缓存 30 秒发送策略。为了方便开发者查看日志，一般和`setDebugMode`一起使用。

在App的Application onCrate 初始化 SDK 位置添加配置。

```java
setTestMode(boolean testMode);
```

**参数说明**

| 参数 | 类型 | 是否必填 | 说明 |
| :--- | :--- | :--- | :--- |
| testMode | boolean | 是 | 开启测试模式，true开启，默认false |

**示例代码**

```java
GrowingIO.startWithConfiguration(this,new Configuration()
    //BuildConfig.DEBUG 这样配置就不会上线忘记关闭
    .setTestMode(BuildConfig.DEBUG));
```

### 10. 采集广告Banner数据

采集`Banner`数据，应用的界面上方横向滚动的`Banner`广告。

对于此类广告，如果您的应用通过 `ViewPager`、`AdapterView` 或者`RecyclerView` 实现，请在 Banner 创建时（包括动态创建）调用此接口来采集数据。

```java
GrowingIO.getInstance().trackBanner(View banner,List<String> bannerDescriptions);
```

**参数说明**

| 参数 | 类型 | 是否必填 | 说明 |
| :--- | :--- | :--- | :--- |
| banner | view | 是 | ViewPager、AdapterView、RecyclerView 实现的 View |
| bannerDescriptions | List&lt;string&gt; | 是 | 广告内容描述，顺序需要跟 banner view 顺序一致 |

**示例代码**

```java
 //Banner 初始化代码
 ViewPager banner = (ViewPager)findViewById(R.id.banner);
 ...
 //GrowingIO 采集 Banner 数据
 GrowingIO.trackBanner(banner.getViewPager(), Arrays.asList("banner 1", "banner 2", "banner 3"));
```

{% hint style="info" %}
Banner 描述和广告出现的顺序一致，通过 Log 查看或者MobileDebugger 的方式检查配置是否正确。查看 Banner clck 事件 `e` 字段中的 `v` 字段是否为您设置的 banner description。
{% endhint %}

**检验数据发送日志示例**

```java
{
    "s":"02015456-079b-49cc-8b42-a5cc6136f0ec",
    // t 为事件类型 type
    "t":"clck", 
    "tm":1531990474178,
    "d":"com.growingio.android.test",
    "p":"ConvenientBannerActivity",
    "ptm":1531990413207,
    "e":[
        {
            "x":"/MainWindow/LinearLayout[0]/FrameLayout[1]/FitWindowsLinearLayout[0]#action_bar_root/ContentFrameLayout[1]/FrameLayout[0]/RelativeLayout[0]/ConvenientBanner[0]#convenientBanner/LinearLayout[0]/RelativeLayout[0]/CBLoopViewPager[0]#cbLoopViewPager/ImageView[-]",
            "tm":1531990474179,
            "idx":1,
            //假如现在滚动到第二个banner，V显示为您设置的描述
            "v":"banner 2" 
        }
    ]
}
```

### 11. 采集GPS数据

精确采集`GPS`数据，请在获取坐标后，调用接口设置位置信息。当用户下一次切换页面，或者发生点击行为时，`GPS`数据会被发送回`GrowingIO`。

{% hint style="success" %}
如果您不调用此接口也可以，我们会根据用户的`ip`定义用户位置，能够在最终的数据分析时看到`APP`用户地域分布。
{% endhint %}

```java
GrowingIO.getInstance().setGeoLocation(double latitude,double longitude);
```

**参数说明**

| 参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| latitude | double | 是 | 纬度 |
| longitude | double | 是 | 经度 |

**示例代码**

```java
//北京的经纬度
GrowingIO.getInstance().setGeoLocation(39.9046900000,116.4071700000);
```

{% hint style="info" %}
对应的清除地理位置的方法为 clearGeoLocation\(\);
{% endhint %}

### 12. 采集输入框数据

GrowingIO 默认采集输入框内容改变次数，不采集文字。

在您需要采集应用内某个输入框内的文字（例如搜索框）时使用此接口。

{% hint style="success" %}
当这个输入框失去焦点（包括应用退到后台），且输入框内容跟获取焦点前相比发生变化时，输入框内文字会被发送回 GrowingIO 。
{% endhint %}

```java
GrowingIO.getInstance().trackEditText(EditText editText);
```

**参数说明**

| 参数 | 类型 | 是否必填 | 说明 |
| :--- | :--- | :--- | :--- |
| editText | ditText | 是 | 采集输入框 |

**示例代码**

```java
EditText editText = (EditText) findViewById(R.id.edit_text);
GrowingIO.getInstance().trackEditText(editText);
```

{% hint style="success" %}
* 对于密码输入框，即便标记为需要采集，SDK也会忽略不进行采集。
* 在**输入框失去焦点的时候或者 onPause 时才会采集事件**，如果输入完成，输入框光标仍然在闪动，则不会采集事件。为了保证数据准确性，请每次用户输入完成时，让输入框失去焦点，可使用editText.setFocusable\(false\);
{% endhint %}

### 13. WebView锚点链接页面访问

开启之后，App `WebView` 中的页面，如果用户点击带有锚点的跳转链接，则发送一次页面浏览事件，请在 `SDK` 初始化方法中设置，默认值为 false，即默认锚点链接不算做页面浏览事件。

GrowingIO 默认不会把`HashTag`识别成页面 URL 的一部分，对于使用`HashTag`进行页面跳转的单页面网站应用来说，可以启用它来标识页面，`HashTag`的值也会记录在页面URL中。

```java
GrowingIO.startWithConfiguration(this, new Configuration().setHashTagEnable(true));
```

举例：

点击 APP `WebView` 中代码混淆的锚点链接，URL 中`#`号后面为锚点，设置后 SDK 会发送页面浏览事件，它的链接为：​[https://docs.growingio.com/docs/sdk-integration/android-sdk\#4-dai-ma-hun-xiao](https://docs.growingio.com/docs/sdk-integration/android-sdk#4-dai-ma-hun-xiao)

![](../../../.gitbook/assets/image%20%28123%29.png)

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
}
```

### 14. 多进程支持

多进程支持，`SDK`默认不支持多进程使用， 但是可以通过`confiuration`进行设置支持多进程。 在`Application onCreate` 中初始化SDK代码块中配置。

```java
//支持多进程数据采集
setMutiprocess(boolean setMutiprocess);
//支持多进程圈选
supportMultiProcessCircle(boolean smpc);
```

参数说明

| 参数 | 类型 | 是否必填 | 说明 |
| :--- | :--- | :--- | :--- |
| isMultiprocess | boolean | 是 | 开启多进程数据采集。默认值false |
| smpc | boolean | 是 | 开启多进程圈选。默认值false |

示例代码：

```java
GrowingIO.startWithConfiguration(this, new Configuration()
                  .supportMultiProcessCircle(true)
                  .setMutiprocess(true)
                  );
```

{% hint style="info" %}
1. 为什么不默认支持多进程？

   跨进程通信是一个相对较慢的过程， 默认不开启， 可以满足大部分用户的要求。

   1. 哪些进程需要初始化SDK？

   需要使用SDK功能的进程需要初始化SDK， 所有的UI进程 + 部分Service进程\(如果这些进程中涉及手动打点\)。
{% endhint %}

### 15. GDPR数据采集开关

> SDK版本支持：2.3.2及以上。

| 接口 | 含义 |
| :--- | :--- |
| disableDataCollect\(\) | 遵守欧洲联盟出台的通用数据保护条例，用户不授权，不采集用户数据 |
| enableDataCollect\(\) | 遵守欧洲联盟出台的通用数据保护条例，用户授权，采集用户数据 |

### 16. Deep Link回调参数获取

​通过获取回调参数，GrowingIO SDK 将会传递指定活动页面参数至您的 App，请根据此参数和业务场景，执行相关的交互。

{% hint style="info" %}
**SDK 2.3.2** 开始提供 DeepLink Callback 接口，在 **SDK 2.8.4** 支持 App Links ，为了保证接收自定义参数并进行自定义跳转这一流程的完整性，App Links 沿用此接口，并新增一个参数，下文将详细解释。
{% endhint %}

{% hint style="success" %}
此 Callback 只有在应用收到来自 GIO Intent 的时候才会触发，您需要先在广告监测新建监测链接，并使用监测链接唤醒 APP 时触发此 callback 。

[点击了解新建监测链接。](../../api-reference/query-productid/definition/create-deeplinks.md)
{% endhint %}

在 GrowingIO SDK 代码初始化部分配置。

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

返回值说明

| 返回值名称 | 类型 | 说明 |
| :--- | :--- | :--- |


| params | Map&lt;string,string&gt; | 自定义参数，您自定义的键值对 |
| :--- | :--- | :--- |


| status | int | DeeplinkCallback.SUCCESS ：自定义参数获取成功； DeeplinkCallback.PARSE\_ERROR ：解析异常；DeeplinkCallback.ILLEGAL\_URI ：非法URI； DeeplinkCallback.NO\_QUERY : 自定义参数为空。DeeplinkCallback.APPLINK\_GET\_PARAMS\_FAILED : （SDK 2.8.4新增）AppLink 由于网络原因获取自定义参数失败。 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">appAwakePassedTime</th>
      <th style="text-align:left">long</th>
      <th style="text-align:left">
        <p>&#xFF08;SDK 2.8.4&#x65B0;&#x589E;&#xFF09;App &#x5524;&#x9192;&#x5230;&#x6536;&#x5230;
          GIO callback &#x7684;&#x65F6;&#x95F4;&#xFF0C;<b>&#x5355;&#x4F4D;&#x6BEB;&#x79D2;</b>&#x3002;&#x7528;&#x4EE5;&#x5224;&#x65AD;&#x7F51;&#x7EDC;&#x72B6;&#x6001;&#x4E0D;&#x597D;&#x7684;&#x60C5;&#x51B5;&#xFF0C;&#x5E94;&#x7528;&#x5DF2;&#x7ECF;&#x6253;&#x5F00;&#x5F88;&#x4E45;&#xFF0C;&#x624D;&#x6536;&#x5230;&#x56DE;&#x8C03;&#xFF0C;&#x5F00;&#x53D1;&#x4EBA;&#x5458;&#x51B3;&#x5B9A;&#x662F;&#x5426;&#x6536;&#x5230;&#x53C2;&#x6570;&#x540E;&#x4ECD;&#x7136;&#x8DF3;&#x8F6C;&#x81EA;&#x5B9A;&#x4E49;&#x7684;&#x6307;&#x5B9A;&#x9875;&#x9762;&#x3002;</p>
        <p><b>&#x5F53;&#x8FD4;&#x56DE;&#x503C;&#x4E3A; 0 &#x7684;&#x65F6;&#x5019;&#xFF0C;&#x4E3A; DeepLink &#x65B9;&#x5F0F;&#x6253;&#x5F00;&#x3002;</b>
        </p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

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

### 17. 采集推送配置

在 **Android SDK 2.6.3** 及以上版本，支持采集通知的标题和内容，此功能默认关闭，如需开启，请在 Application 初始化 GrowingIO 中设置，例如：

```java
...
@Override
public void onCreate() {
       GrowingIO.startWithConfiguration(this, new Configuration()
                //如果多进程应用，需要开启GrowingIO多进程
                .setMutiprocess(true)
                .supportMultiProcessCircle(true)
                // 开启采集通知
                .enablePushTrack()
        );
        ...
}
```

{% hint style="info" %}
SDK对通知的采集仅支持 4.4 及以上机型。
{% endhint %}

注意：

| 支持推送平台 | 注意事项 |
| :--- | :--- |


| Notification | 全部支持 |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x6781;&#x5149;&#x63A8;&#x9001;</th>
      <th style="text-align:left">
        <ol>
          <li>&#x521D;&#x59CB;&#x5316;&#x65F6;&#xFF0C;&#x6781;&#x5149;&#x8FDB;&#x7A0B;&#x4E5F;&#x9700;&#x8981;&#x521D;&#x59CB;&#x5316;</li>
          <li>&#x5982;&#x679C;&#x591A;&#x8FDB;&#x7A0B;&#x5E94;&#x7528;&#xFF0C;&#x9700;&#x8981;&#x5F00;&#x542F;GrowingIO&#x591A;&#x8FDB;&#x7A0B;</li>
        </ol>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x534E;&#x4E3A;&#x63A8;&#x9001;</th>
      <th style="text-align:left">
        <ol>
          <li>&#x521D;&#x59CB;&#x5316;&#x65F6;&#xFF0C;&#x63A8;&#x9001;&#x8FDB;&#x7A0B;&#x4E5F;&#x9700;&#x8981;&#x521D;&#x59CB;&#x5316;</li>
          <li>NC(Notification Center)&#x6D88;&#x606F;&#xFF0C;&#x9700;&#x8981;&#x7528;&#x6237;&#x8BBE;&#x7F6E;&#x81EA;&#x5B9A;&#x4E49;&#x5B57;&#x6BB5;:
            notification_title&#x8868;&#x793A;title&#xFF0C; &#x4E0E;notification_content&#x8868;&#x793A;&#x5185;&#x5BB9;&#xFF0C;&#x8BF7;&#x89C1;&#x8868;&#x683C;&#x4E0B;&#x65B9;&#x56FE;&#x7247;&#x3002;</li>
        </ol>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5C0F;&#x7C73;&#x63A8;&#x9001;</th>
      <th style="text-align:left">
        <ol>
          <li>&#x521D;&#x59CB;&#x5316;&#x65F6;&#xFF0C;&#x63A8;&#x9001;&#x8FDB;&#x7A0B;&#x4E5F;&#x9700;&#x8981;&#x521D;&#x59CB;&#x5316;</li>
          <li>SDK hook&#x4E86;PushMessageReceiver&#x7684;onNotificationMessageArrived&#x4E0E;onNotificationMessageClicked&#x51FD;&#x6570;,
            &#x4F1A;&#x89E6;&#x53D1;SDK&#x53D1;&#x9001;&#x4E24;&#x6761;&#x6D88;&#x606F;.
            &#x5176;&#x4E2D;onNotificationMessageArrived&#x9700;&#x8981;&#x7CFB;&#x7EDF;&#x652F;&#x6301;&#x3002;</li>
        </ol>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

查看通知采集数据

支持对于通知的展现和点击事件的采集，GrowingIO 并未增加新的采集事件类型，而是使用了自定义事件发送，所以需要您创建自定义事件和事件级变量，事件级变量标识符为**`notification_title`**，**`notification_content`**，自定义事件的标识符为**`notification_show`**，**`notification_click`** 创建事件分析，等候片刻即可看到数据。

### 18. 采集OAID

在 Android 10 版本中，非系统应用无法获取 IMEI。加上以前 Android 版本已经对 MAC 地址， AndroidID 的获取做了限制， 在 Android10 中缺少一种唯一标记设备的标识符。 在海外， Google 推荐使用 Google 的广告 ID 作为广告的唯一识别符，在国内[移动安全联盟MSA](http://www.msa-alliance.cn/col.jsp?id=120) 联合各大手机制造商推出了 OAID 的概念， 作为唯一广告标识符。

目前腾讯， 头条， 网易广告SDK已经要求使用 OAID， OAID 的准确性和覆盖率均满足广告场景的使用需求，Android SDK 提供采集 OAID 的能力。

{% hint style="info" %}
* 支持采集：**Android SDK 2.8.5** 及以上， 包含埋点包与无埋点包及对应插件版本；
* 目前 2.8.5 SDK 测试的 OAID SDK 版本为miit\_mdid\_sdk\_v1.0.10, 在API不变更的情况下支持后续版本；
* 目前仅在 **activate** 事件（激活，用户首次安装并打开应用时发送）中包含 OAID。
{% endhint %}

{% hint style="danger" %}
注意:

OAID 为可选字段，在客户集成 MSA SDK 情况下根据配置可选采集。GrowingIO SDK不会初始化 MSA SDK，我们仅调用其接口获取 OAID 值， 需要客户自行初始化 MSA的 SDK。

[点击查看 MSA 集成步骤](http://www.msa-alliance.cn/col.jsp?id=120)。
{% endhint %}

与 IMEI、AndroidId、Google AD ID 配置相同， GrowingIO SDK 对OAID 提供了编译期，初始化前， 初始化后三种配置 OAID 是否采集的选项，点击查看[ API 文档](android-sdk-api/)。

## 3. 自定义数据上传

除上述的用户行为数据（无埋点数据）之外，GrowingIO 还提供了多种 API 接口，供您上传一些自定义的数据指标及维度 ，请参考Android SDK API &gt; [自定义数](android-sdk-api/customize-api.md)[上传API](android-sdk-api/customize-api.md)。

{% hint style="success" %}
90% 以上的用户都会上传登录用户 ID ，以便分析登录用户的数据情况。
{% endhint %}

## 4. 创建应用

{% hint style="danger" %}
**添加代码之后，请先Clean项目，然后再进行编译，并在你的 Android App 安装了 SDK 后重新启动几次 App，保证行为采集数据自动发送给 GrowingIO，以便顺利完成检测。**
{% endhint %}

在GrowingIO平台的应用创建页面继续完成应用创建的数据检测，检测成功后应用创建成功。

## 5. 验证SDK是否正常采集数据

{% hint style="info" %}
了解GrowingIO平台数据采集类型请参考[数据模型](../../../introduction/datamodel/)。
{% endhint %}

GrowingIO为您提供多种验证SDK是否正常采集数据的方式：

方式一：[Mobile Debugger](../../debugging/mobile-debugger.md)

方式二：在SDK中设置了Debug模式后，在IDE编译器控制台查看数据采集日志。

方式三：（**推荐**）[数据校验](https://docs.growingio.com/v3/product-manual/data-center/datacheck/app)

