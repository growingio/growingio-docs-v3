# Flutter埋点SDK

{% hint style="success" %}
GitHub Demo：[https://github.com/growingio/flutter-growingio-track/tree/develop/example](https://github.com/growingio/flutter-growingio-track/tree/develop/example)。

App适配最低系统版本：iOS 8及以上、Android 4.2-10
{% endhint %}

## 1. 集成SDK

### 1. Flutter插件获取安装

根据[dart pub](https://pub.dartlang.org/packages/flutter\_growingio\_track#-installing-tab-)文档获取安装。

### 2. 添加跟踪代码

{% tabs %}
{% tab title="Android（Native部分）" %}
Flutter插件运行在Android手机上时依赖于GrowingIO Android SDK (可以是无埋 点SDK也可以是埋点SDK)2.6.0及以上, 原生部分请参考：

Android SDK > [无埋点 SDK集成](../android-sdk/auto-android-sdk.md)

Android SDK > [埋点 SDK集成](../android-sdk/manunl-android-sdk.md)
{% endtab %}

{% tab title="iOS（Native部分）" %}
Flutter 埋点插件是在iOS原生SDK上的扩展，请参考 iOS SDK > [埋点 SDK集成](../ios-sdk/manunl-ios-sdk.md)。
{% endtab %}
{% endtabs %}

## 2. 自定义数据上传

### 1. track

> 发送自定义事件, 对应于cstm事件

| **参数**   | **是否必填** | **说明**   |
| -------- | -------- | -------- |
| eventId  | 是        | 事件Id     |
| variable | 否        | 变量, Map型 |

调用示例:

```dart
import 'package:growingioflutter/growingio_track.dart';
```

```dart
GrowingIO.track('eventId');
GrowingIO.track('eventId', variable: {'testkey': 'testValue', 'testNumKey': 2333});
```

### 2. setEvar

> 发送转化变量, 对应于evar事件

函数原型为: setEvar(Map\<String, dynamic> variable), 调用示例:

```dart
import 'package:growingioflutter/growingio_track.dart';
```

```dart
GrowingIO.setEvar({
  'testKey': 'testValue', 'testNumKey': 2333.0
});
```

### 3. setPeopleVariable

> 发送用户变量, 对应于ppl事件

函数原型为: setPeopleVariable(Map\<String, dynamic> variable)

调用示例:

```dart
import 'package:growingioflutter/growingio_track.dart';
```

```dart
GrowingIO.setPeopleVariable({
  'testKey': 'testValue', 'testNumKey': 2333.0
});
```

### 4. setUserId

> 设置登录用户ID, 对应于cs1字段

| **参数** | **类型** | **描述** |
| ------ | ------ | ------ |
| userId | String | 登录用户Id |

函数原型: setUserId(String userId)

调用示例:

```dart
import 'package:growingioflutter/growingio_track.dart';
```

```dart
GrowingIO.setUserId("testUserId");
```

### 5. clearUserId

> 清除登录用户ID

函数原型: clearUserId()

调用示例:

```dart
import 'package:growingioflutter/growingio_track.dart';
```

```dart
GrowingIO.clearUserId();
```

### 6. setVisitor

> 设置访问用户变量, 对应于vstr事件

函数原型: setVisitor(Map\<String, dynamic> variable)

调用示例:

```dart
import 'package:growingioflutter/growingio_track.dart';
```

```dart
GrowingIO.setVisitor({
      "visitorKey": 'key', "visitorValue": 34
});
```

## 3. 创建应用

{% hint style="danger" %}
**添加代码之后，请先Clean项目，然后再进行编译，并在你的 App 安装了 SDK 后重新启动几次 App，保证行为采集数据自动发送给 GrowingIO，以便顺利完成检测。**
{% endhint %}

在GrowingIO平台的应用创建页面继续完成应用创建的数据检测，检测成功后应用创建成功。

## 4. 验证SDK是否正常采集数据 <a href="5-yan-zheng-sdk-shi-fou-zheng-chang-cai-ji-shu-ju" id="5-yan-zheng-sdk-shi-fou-zheng-chang-cai-ji-shu-ju"></a>

了解GrowingIO平台数据采集类型请参考[数据模型](../../../introduction/datamodel/)。

GrowingIO为您提供多种验证SDK是否正常采集数据的方式：

方式一：[Mobile Debugger​​](../../debugging/mobile-debugger.md)

方式二：在SDK中设置了Debug模式后，在IDE编译器控制台查看数据采集日志。

方式三：[数据校验](broken-reference)

## 常见问题

### 1. iOS ：App Store 提供应用注意事项

如果您添加了库AdSupport.framework, GrowingIO则会启用IDFA，所以在向App Store 提交应用时，需要：

* 对于问题Does this app use the Advertising Identifier (IDFA)，选择YES。
* 对于选项Attribute this app installation to a previously served advertisement，打勾。
* 对于选项Attribute an action taken within this app to a previously served advertisement，打勾。

### 2. iOS：为什么GrowingIO使用IDFA？

GrowingIO 使用IDFA 来做来源管理激活设备的精确匹配，让你更好的衡量广告效果。如果你不希望跟踪这个信息，可以选择不引入AdSupport.framework

### 3. 初始化Android SDK时，GrowingIO类可能会报红色怎么处理？

这个应该是Flutter项目结构的问题，并不影响运行，可以放心编译. 不过需要手动import。

```java
import 'package:growingioflutter/growingio_track.dart';
```

### 4. 为什么不在Flutter中单独初始化？

* 因为GrowingIO需要获取Android的Activity生命周期，为了数据的准确性，需要在Activity出现前就初始化完成
* 开发者相信很多用户都会使用flutter + native形式的进行开发，为了同时服务flutter于native
