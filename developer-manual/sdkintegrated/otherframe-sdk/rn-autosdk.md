# React Native无埋点SDK

{% hint style="success" %}
GitHub Demo：[https://github.com/growingio/ReactNativeDemo](https://github.com/growingio/ReactNativeDemo) 。
{% endhint %}

{% hint style="info" %}
版本支持：

* 兼容 React Native 版本：0.46-0.56、0.59.9
* 兼容组件 react-navigation 版本：^2.7.4、^3.11.0
* 兼容组件 react-native-navigation 版本：^1.1.486
* App适配最低系统版本：iOS 8及以上、Android 4.2-10

如果没有使用react-navigation或者react-native-navigation作为导航，请仔细阅读 **下文3.3 page设置API**。
{% endhint %}

## 1. 预处理 JS 文件

RN无埋点的实现原理是修改用户`React Native`，`React-navigation`， `React-Native-Navigation`的源码。所以需要预先处理`js`文件，[GitHub 开源 JS 脚本](https://github.com/growingio/GIORNHook)。

#### 使用命令行进入项目根目录，执行下面操作（二者任选其一即可）：

```objectivec
npm install --save react-native-autotrack-growingio
```

```text
npm install --save https://github.com/growingio/GIORNHook.git#0.0.6
```

####  配置 package.json 文件

考虑到了`hook.js`每次`npm install`之后都需要执行， 建议直接配在项目的`package.json`中， 在原有文件中，添加如下代码，保存后执行**`npm install`**。

```javascript
"scripts": {
	  "postinstall": "node node_modules/react-native-autotrack-growingio/hook.js -run"
}
```

## 2. 集成

{% tabs %}
{% tab title="Android" %}
### 1. 添加Android无埋点SDK依赖

React Native无埋点SDK是在Android原生SDK上的扩展，请参照Android SDK&gt; [无埋点 SDK集成](../android-sdk/auto-android-sdk.md) 完成添加跟踪代码配置。

{% hint style="warning" %}
注意替换SDK版本号：

请将autotrack-`version`替换成RN版本：RN-autotrack-`version`。

`version`为Android 无埋点SDK版本号，最新版本号请参考原生Android SDK[更新日志](../android-sdk/androidsdk-log.md)。
{% endhint %}

集成步骤中只有版本号不同，适配RN与原生混合开发场景。

### 2. 重要配置

#### 2.1 添加GrowingIOPackage

由于SDK需要在 java 代码中进行初始化，需要在项目的 Application 中添加 GrowingIOPackage。

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

#### 2.2 代码混淆

注意混淆文件比 Android 原生 SDK 多一条 RN 控件的混淆代码，请复制全部内容添加到您的 `proguard_rules.pro` 文件中，如下：

```java
# GIO RN 控件混淆代码，不添加则会造成点击事件采集失败
-keep class com.facebook.react.uimanager.JSTouchDispatcher{
    *;
}
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
{% endtab %}

{% tab title="iOS" %}
### 1. 添加依赖

方式一：使用CocoaPods 快速添加

1. 添加 `pod 'GrowingReactNativeKit'`到Podfile中。
2. 执行`pod install` 或 `pod update` 更新pod依赖库。
3. （可选）GrowingIO推荐您添加 **AdSupport.framework** 依赖库，用于来源管理激活匹配,有利于您更好的分析数据 ,添加项目依赖库的位置在项目设置target -&gt; 选项卡General -&gt; Linked Frameworks and Libraries

方式二：手动添加

1. 下载 [GrowingCoreKit](https://assets.growingio.com/sdk/ios/GrowingIO-iOS-CoreKit-2.8.12.zip)、[GrowingAutoTrackKit](https://assets.growingio.com/sdk/ios/GrowingIO-iOS-AutoTrackKit-2.8.12.zip)、[GrowingReactNativeKit](https://assets.growingio.com/sdk/ios/GrowingIO-iOS-ReactNativeKit-2.8.12.zip)、[GrowingHeader](https://assets.growingio.com/sdk/ios/GrowingIO-iOS-PublicHeader-2.8.12.zip)，并解压。
2. 将 `Growing.h` 、`module.modulemap` 和 `GrowingCoreKit.framework`、`GrowingAutoTrackKit.framework`、`GrowingReactNativeKit.framework`

   添加到iOS工程中。

其他参照 iOS SDK &gt; [无埋点 SDK集成](../ios-sdk/auto-ios-sdk.md) ，操作步骤一致。

### 2. 集成 React Native 埋点SDK

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

### 3. 重要配置

与原生混合开发的开发者可详细查看 iOS SDK &gt; 无埋点 SDK&gt; [重要配置](../ios-sdk/auto-ios-sdk.md#fu-lu-1-zhong-yao-pei-zhi)文档，如果原生控件使用不多，只需关注如下配置即可：

* **​**[**App Store 提交应用注意事项**](../ios-sdk/auto-ios-sdk.md#app-store-ti-jiao-ying-yong-zhu-yi-shi-xiang)\*\*\*\*
{% endtab %}
{% endtabs %}

## 3. 页面识别

由于RN应用的页面切换并不遵循原生的生命周期， 需要单独适配， 目前在 React Native 页面中我们只支持`react-navigation`， `react-native-navigation`作为导航器, 并且为了拓展性， 留下了手动的page接口， 开发者可自行适配（[直接更改 hook.js 脚本](https://github.com/growingio/GIORNHook)）。

### 3.1 react-navigation

如果使用react-navigation， 我们的hook脚本进行了自动适配, 默认的page名称为其key值。 用户可以自行设置， 如下代码：

```java
this.props.navigation.setParams({growingPagePath: 'xx'});
```

{% hint style="info" %}
采集原理参照 [react-navigation 的 screen tracking](https://reactnavigation.org/docs/en/screen-tracking.html)，目前仅兼容 [`Listening to State Changes`](https://reactnavigation.org/docs/en/screen-tracking.html#listening-to-state-changes)方式，如果用户使用 Redux ，请结合官网的 [`Screen tracking with Redux`](https://reactnavigation.org/docs/en/screen-tracking.html#screen-tracking-with-redux) 和 **3.3 Page 设置 API** 采集页面。
{% endhint %}

### 3.2 react-native-navigation

当前支持`react-native-navigation`版本为 1.1.486， 1.1.406。 理论上兼容1.1版本。

`react-native-navigation`其标题默认取`title`， 如果没有`title`则取`screenId`，作为唯一标记。

用户可以设置自定义`title`, 只需要设置`growingPagePath`字段， 该字段与`title`同级即可。

### 3.3 page 设置API

如果SDK目前支持的路由方案不能满足您的需求， SDK留下拓展接口， 您需要在您认为页面发生切换时， 将最新的page名称告诉我们。 调用方法如下：

```java
import {
    NativeModules
  } from 'react-native';
​
// 在react native页面将要展示时调用
NativeModules.GrowingIO.onPagePrepare("pageName");
// 在react native页面已经展示时调用
NativeModules.GrowingIO.onPageShow("pageName");
```

## 4. 自定义数据上传

自定义数据上传其实最终是通过 NativeModules.GrowingIO 调用的原生GrowingIO 无埋点的API，以上接口使用时，对应的参数限制条件对您很重要。

| 方法名 | 参数类型 | 说明                                      |
| :--- | :--- | :--- |
| track | \(String eventId, Object eventLevelVariable\(optional\)\) | 自定义事件 |
| setEvar | \(Object conversionVariables\) | 设置转化变量 |
| setPeopleVariable | \(Object peopleVariables\) | 设置用户变量 |
| setUserId | \(String userId\) | 设置登录用户ID |
| clearUserId | 无参数 | 清除登录用户ID |
| setVisitor | \(Object visitor\) | 设置访问用户变量 |
| setPageVariable | \(String pageName, JSONObject pageVariable\) | 设置页面级变量 |

{% hint style="warning" %}
埋点接口其实最终是通过 NativeModules.GrowingIO 调用的原生GrowingIO 无埋点的API，参数限制与其一致。
{% endhint %}

**代码示例**

GrowingIOPackage 向 RN 提供了一个 NativeModule ，所有埋点接口都是由其实现，使用方法如下：

```java
//在使用 GrowingIO 埋点功能的文件中导入 NativeModules
import {
    NativeModules
  } from 'react-native';
​
//埋点方法调用示例如下：
​
//track 设置自定义事件
NativeModules.GrowingIO.track('testEventId', {'卖家Id': 'xxxxxx', '地点': '北京'});
​
//setPeopleVariable 设置用户变量
NativeModules.GrowingIO.setPeopleVariable({ "name": "Danny", "Age": 20 });
​
//setEvar 设置转化变量
NativeModules.GrowingIO.setEvar({ "registered": true, "fee": "200" });
​
//setUserId 设置登录用户名称
NativeModules.GrowingIO.setUserId("Gioer");
​
//clearUserId 清除登录用户名称
NativeModules.GrowingIO.clearUserId();
​
//setVisitor 设置访问用户变量
NativeModules.GrowingIO.setVisitor({ "age": 20, "gender": "male" });

//setPageVariable 设置页面级变量
NativeModules.GrowingIO.setPageVariable("HomePage",{ "registered": true, "fee": "200" });
```

## 5. 高级选项设置

开发者可以为 UI 元素添加 growingParams

代码示例：

```java
<Text growingParams={{id:"test",content:"test",info:"test",ignore:"true"}}>高级选项设置</Text>
```

属性列表

| 属性名称 | 参数限制 | 描述 |
| :--- | :--- | :--- |
| ignore | 仅接受 true | 忽略对应的元素，不采集点击事件和浏览事件 |
| track | 仅接受 true | 采集输入框内容，默认采集输入框内容变化次数，不采集内容 |
| id | - | 设置界面元素ID |
| content | - | 设置界面元素内容 |
| info | - | 设置元素对象 |

支持设置组件（Component）列表（包括但不限于）

| 组件 |
| :--- |
| View |
| ScrollView |
| ListView |
| Picker |
| Text |
| TextInput |
| WebView |
| RefreshControl |
| ActivityIndicator |

## 6. 创建应用

{% hint style="danger" %}
**添加代码之后，请先Clean项目，然后再进行编译，并在你的 App 安装了 SDK 后重新启动几次 App，保证行为采集数据自动发送给 GrowingIO，以便顺利完成检测。**
{% endhint %}

 在GrowingIO平台的应用创建页面继续完成应用创建的数据检测，检测成功后应用创建成功。

## 7. 验证SDK是否正常采集数据 <a id="5-yan-zheng-sdk-shi-fou-zheng-chang-cai-ji-shu-ju"></a>

了解GrowingIO平台数据采集类型请参考[数据模型](../../../introduction/datamodel/)。

GrowingIO为您提供多种验证SDK是否正常采集数据的方式：

方式一：[Mobile Debugger​​](../../debugging/mobile-debugger.md)

方式二：在SDK中设置了Debug模式后，在IDE编译器控制台查看数据采集日志。

方式三：[数据校验](../../../product-manual/datacenter/datacheck.md)

## 常见问题

### 1. iOS使用 react native location 功能时与GrowingIO有冲突吗？

有，但不属于GrowingIO的原因,具体可以参考[issue](https://github.com/growingio/react-native-growingio/issues/4)中的解答,并且可以使用[rn-patch.zip](https://github.com/growingio/react-native-growingio/files/2166299/rn-patch.zip)来解决这个问题。

### 2. 使用Debugger 工具时是否可以校验SDK采集数据的准确性？

目前不支持，Debugger工具可以辅助您来调试自己的项目，建议您在release 环境下校验。

### 3. react native 页面中的 tabbar imp event 不准确，click event是否受影响？

（1）原则上对于react native中的tabbar控件,我们只能保证使用原生代码UITabBarController，或者不是RCT为前缀的原生控件实现的tabbar，可以正确采集tabbar上的imp

 （2）click event不受影响,可正确采集

