# Flutter埋点SDK

{% hint style="success" %}
GitHub Demo：[https://github.com/growingio/flutter-growingio-track/tree/develop/example](https://github.com/growingio/flutter-growingio-track/tree/develop/example)。

App适配最低系统版本：iOS 8及以上、Android 4.2-10
{% endhint %}

## 1. 集成SDK

### 1. 环境配置

{% tabs %}
{% tab title="Android（Native 部分）" %}
Flutter 插件运行在 Android 手机上时依赖于 GrowingIO Android SDK (可以是无埋点 SDK 也可以是埋点 SDK) 2.6.0 及以上, 原生部分请参考：

Android SDK > [无埋点 SDK集成](../android-sdk/auto-android-sdk.md)

Android SDK > [埋点 SDK集成](../android-sdk/manunl-android-sdk.md)
{% endtab %}

{% tab title="iOS（Native 部分）" %}
Flutter 埋点插件是在 iOS 原生 SDK（无埋点或埋点）上的扩展，原生部分请参考：

iOS 无埋点 SDK > [无埋点 SDK集成](../ios-sdk/auto-ios-sdk.md)

iOS 埋点 SDK > [埋点 SDK集成](../ios-sdk/manunl-ios-sdk.md)
{% endtab %}
{% endtabs %}

### 2. Flutter SDK 集成

在`pubspec.yaml`文件中添加依赖

```yaml
dependencies:
  flutter_growingio_track:
    git:
      url: https://github.com/growingio/flutter-growingio-track.git
      ref: master
```

然后执行`flutter pub get`指令

### 3. 导入

在对应的 \*.dart 文件，使用以下方式导入

```dart
import 'package:flutter_growingio_track/flutter_growingio_track.dart';
```

## 2. 自定义数据上传

### 1. track

> 发送自定义事件, 对应于 cstm 事件

| **参数**   | **是否必填** | **说明**   |
| -------- | -------- | -------- |
| eventId  | 是        | 事件Id     |
| variable | 否        | 变量, Map型 |

调用示例:

```dart
GrowingIO.track('eventId');
GrowingIO.track('eventId', variable: {'testkey': 'testValue', 'testNumKey': 2333});
```

### 2. setEvar

> 发送转化变量, 对应于 evar 事件

函数原型为: setEvar(Map\<String, dynamic> variable)

调用示例:

```dart
GrowingIO.setEvar({
  'testKey': 'testValue', 'testNumKey': 2333.0
});
```

### 3. setPeopleVariable

> 发送用户变量, 对应于 ppl 事件

函数原型为: setPeopleVariable(Map\<String, dynamic> variable)

调用示例:

```dart
GrowingIO.setPeopleVariable({
  'testKey': 'testValue', 'testNumKey': 2333.0
});
```

### 4. setUserId

> 设置登录用户 ID, 对应于 cs1 字段

| **参数** | **类型** | **描述** |
| ------ | ------ | ------ |
| userId | String | 登录用户Id |

函数原型: setUserId(String userId)

调用示例:

```dart
GrowingIO.setUserId("testUserId");
```

### 5. clearUserId

> 清除登录用户 ID

函数原型: clearUserId()

调用示例:

```dart
GrowingIO.clearUserId();
```

### 6. setVisitor

> 设置访问用户变量, 对应于 vstr 事件

函数原型: setVisitor(Map\<String, dynamic> variable)

调用示例:

```dart
GrowingIO.setVisitor({
      "visitorKey": 'key', "visitorValue": 34
});
```

## 3. 创建应用

{% hint style="danger" %}
**添加代码之后，请先 Clean 项目，然后再进行编译，并在你的 App 安装了 SDK 后重新启动几次 App，保证行为采集数据自动发送给 GrowingIO，以便顺利完成检测。**
{% endhint %}

在 GrowingIO 平台的应用创建页面继续完成应用创建的数据检测，检测成功后应用创建成功。

## 4. 验证SDK是否正常采集数据 <a href="#5-yan-zheng-sdk-shi-fou-zheng-chang-cai-ji-shu-ju" id="5-yan-zheng-sdk-shi-fou-zheng-chang-cai-ji-shu-ju"></a>

了解 GrowingIO 平台数据采集类型请参考[数据模型](../../../introduction/datamodel/)。

GrowingIO 为您提供多种验证 SDK 是否正常采集数据的方式：

方式一：[Mobile Debugger​​](../../debugging/mobile-debugger.md)

方式二：在 SDK 中设置了 Debug 模式后，在 IDE 编译器控制台查看数据采集日志。

方式三：[数据校验](broken-reference)

## 常见问题

### 1. iOS ：App Store 提供应用注意事项

如果您添加了库 AdSupport.framework, GrowingIO 则会启用 IDFA，所以在向 App Store 提交应用时，需要：

* 对于问题 Does this app use the Advertising Identifier (IDFA)，选择 YES。
* 对于选项 Attribute this app installation to a previously served advertisement，打勾。
* 对于选项 Attribute an action taken within this app to a previously served advertisement，打勾。

### 2. iOS：为什么 GrowingIO 使用 IDFA？

GrowingIO 使用 IDFA 来做来源管理激活设备的精确匹配，让你更好的衡量广告效果。如果你不希望跟踪这个信息，可以选择不引入 AdSupport.framework

### 3. 初始化 Android SDK 时，GrowingIO 类可能会报红色怎么处理？

这个应该是 Flutter 项目结构的问题，并不影响运行，可以放心编译. 不过需要手动 import。

```java
import 'package:flutter_growingio_track/flutter_growingio_track.dart'; 
```

### 4. 为什么不在 Flutter 中单独初始化？

* 因为 GrowingIO 需要获取 Android 的 Activity 生命周期，为了数据的准确性，需要在 Activity 出现前就初始化完成
* 开发者相信很多用户都会使用 Flutter + Native 形式的进行开发，为了同时服务 Flutter 与 Native
