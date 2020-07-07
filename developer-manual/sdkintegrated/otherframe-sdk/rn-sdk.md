# React Native埋点SDK

{% hint style="success" %}
React Native 埋点 SDK 仅自动采集设备信息和埋点数据，如果想自动采集用户点击事件或者页面访问事件等， 请集成 ReactNative 无埋点 SDK。
{% endhint %}

{% hint style="success" %}
版本支持：

* 兼容 React Native 版本：0.46-0.56、0.59.9
* App适配最低系统版本：iOS 8及以上、Android 4.2-10
{% endhint %}

## 1. 集成SDK

{% tabs %}
{% tab title="Android" %}
### 1. 添加跟踪代码

React Native埋点SDK是在Android 原生SDK上的扩展，请参照Android SDK &gt; [埋点SDK](../android-sdk/manunl-android-sdk.md)，完成添加跟踪代码配置。

{% hint style="warning" %}
添加跟踪代码时注意将SDK版本号换成RN版本： `RN-track-2.8.20`
{% endhint %}

集成步骤中，只有版本号不同，适配RN与原生混合开发场景。

**代码示例**

```javascript
apply plugin: 'com.android.application'
android {
    defaultConfig {
        resValue("string", "growingio_project_id", "您的项目ID")
        resValue("string", "growingio_url_scheme", "您的URL Scheme")
    }
}
dependencies {
    //GrowingIO RN 埋点 SDK
    implementation 'com.growingio.android:vds-android-agent:RN-track-2.8.20'
}
```

### 2. 重要配置

由于 SDK 需要在`java`代码中进行初始化。

在项目的Application中，添加`GrowingIOPackage`：

```java
public class MainApplication extends Application implements ReactApplication {
    @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
          new MainReactPackage(), 
          // 此处加入GrowingIOPackage
          new GrowingIOPackage()
      );
    }
}
```
{% endtab %}

{% tab title="iOS" %}
### 1. 添加跟踪代码

React Native 埋点 SDK 是在 iOS 原生 SDK 上的扩展，请参照iOS SDK &gt; [埋点 SDK集成](../ios-sdk/manunl-ios-sdk.md) ，完成添加跟踪代码配置。

### 2. 集成React Native埋点SDK

```text
npm install --save https://github.com/growingio/react-native-growingio.git#0.0.7
```

```text
react-native link react-native-growingio
```

{% hint style="danger" %}
react-native link react-native-growingio 失败（即发现 Libraries中没有 GrowingIORNPlugin.xcodeproj ，则可手动配置）处理方法：

1. 打开 XCode 工程中, 右键点击 Libraries 文件夹 ➜ Add Files to &lt;...&gt;
2. 去 `node_modules` ➜ `react-native-growingio` ➜ iOS ➜ 选择 `GrowingIORNPlugin.xcodeproj`
3. 在工程`Build Phases` ➜ `Link Binary With Libraries`中添加`libGrowingIORNPlugin.a`
{% endhint %}

{% hint style="info" %}
如果您使用的是pod方式集成：

请添加以下内容到Podfile中，并在添加之后执行**`pod update`**：

pod 'GrowingReactNativeTrackKit', :path =&gt; '../node\_modules/react-native-growingio'
{% endhint %}

### 重要配置

与原生混合开发的开发者可详细查看 iOS SDK &gt; 无埋点 SDK &gt; [重要配置](../ios-sdk/auto-ios-sdk.md#fu-lu-1-zhong-yao-pei-zhi)文档，如果原生控件使用不多，只需关注如下配置即可：

* **​**[**App Store 提交应用注意事项**](../ios-sdk/auto-ios-sdk.md#app-store-ti-jiao-ying-yong-zhu-yi-shi-xiang)\*\*\*\*
{% endtab %}
{% endtabs %}

## 2. 自定义数据上传

同[React Native 无埋点SDK 自定义数据上传](rn-autosdk.md#4-zi-ding-yi-shu-ju-shang-chuan)一致。

## 3. 创建应用

{% hint style="danger" %}
**添加代码之后，请先Clean项目，然后再进行编译，并在你的 App 安装了 SDK 后重新启动几次 App，保证行为采集数据自动发送给 GrowingIO，以便顺利完成检测。**
{% endhint %}

在GrowingIO平台的应用创建页面继续完成应用创建的数据检测，检测成功后应用创建成功。

## 4. 验证SDK是否正常采集数据 <a id="5-yan-zheng-sdk-shi-fou-zheng-chang-cai-ji-shu-ju"></a>

了解GrowingIO平台数据采集类型请参考[数据模型](../../../introduction/datamodel/)。

GrowingIO为您提供多种验证SDK是否正常采集数据的方式：

方式一：[Mobile Debugger​​](../../debugging/mobile-debugger.md)

方式二：在SDK中设置了Debug模式后，在IDE编译器控制台查看数据采集日志。

方式三：[数据校验]()

