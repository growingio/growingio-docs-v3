# 无埋点 SDK集成

## 准备条件

获取项目ID，请参考[查看项目基本信息](../../../chan-pin-shi-yong-wen-dang-fen-ban/xiang-mu-guan-li/details.md)。

获取URL Scheme，在GrowingIO平台创建对应的应用时会生成URL Scheme。请参考[创建应用](../../../chan-pin-shi-yong-wen-dang-fen-ban/xiang-mu-guan-li/application-manage.md#chuang-jian-ying-yong)。

{% hint style="info" %}
使用GrowingIO平台创建相应的应用，平台在应用创建界面自动为您生成已加载当前项目ID、URL Scheme的跟踪代码。
{% endhint %}

## 1. 添加跟踪代码

{% hint style="success" %}
集成环境：Xcode 9.0及以上；

App适配最低系统版本：iOS 8及以上
{% endhint %}

**组件化SDK**

GrowingIO iOS SDK 包含以下2个组件SDK:

• GrowingCoreKit \(组件基础库,具备分析功能\)

• GrowingAutoTrackKit \(无埋点库\)

{% hint style="warning" %}
请保证Growing、GrowingCoreKit、GrowingAutoTrackKit版本号一致。
{% endhint %}

### 1. 添加依赖

{% tabs %}
{% tab title="使用CocoaPods快速添加" %}
1. 在您的Podfile中添加`pod 'GrowingAutoTrackKit'`。
2. 执行或 `pod update` 更新pod依赖库。不要使用 `--no-repo-update`选项。
3. （可选）GrowingIO推荐您添加 **AdSupport.framework** 依赖库，用于来源管理激活匹配,有利于您更好的分析数据 ,添加项目依赖库的位置在项目设置target -&gt; 选项卡General -&gt; Linked Frameworks and Libraries
{% endtab %}

{% tab title="手动添加" %}
1. 下载iOS SDK以下包：[GrowingHeader](https://assets.growingio.com/sdk/ios/GrowingIO-iOS-PublicHeader-2.8.12.zip) ，[GrowingCoreKit](https://assets.growingio.com/sdk/ios/GrowingIO-iOS-CoreKit-2.8.12.zip)，[GrowingAutoTrackKit](https://assets.growingio.com/sdk/ios/GrowingIO-iOS-AutoTrackKit-2.8.12.zip)，并解压。
2. 将`Growing.h`、`GrowingCoreKit.framework`、`GrowingAutoTrackKit.framework`添加到iOS工程中。

{% hint style="info" %}
提醒：记得勾选”Copy item if needed“
{% endhint %}
{% endtab %}
{% endtabs %}

在工程项目中添加以下库文件。

> 添加项目依赖库的位置在项目设置target -&gt; 选项卡General -&gt; Linked -&gt; Linked Frameworks and Librarie

| 库名称 | 说明 |
| :--- | :--- |
| Foundation.framework | 基础依赖库 |
| Security.framework | 用户App连接圈选页面SSL连接 |
| CoreTelephony.framework | 用于读取运营商 |
| SystemConfiguration.framework | 用于判断网络状态 |
| AdSupport.framework | 用于来源管理激活匹配 |
| libicucore.tbd | 用户App连接圈选页面解析 |
| libsqlite3.tbd | 存储日志 |
| CoreLocation.framework | 用于读取地理位置信息（如果您的App有权限） |
| JavaScriptCore.framework | Web圈选App交互 |
| WebKit.framework | Web圈选 |

添加编译参数，并注意大小写。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2897%29.png)

### 2. 添加 URL Scheme

添加URL Scheme 到项目中，以便唤醒您的程序进行圈选。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2885%29.png)

### 3. 初始化配置

> 在 AppDelegate 中引入`#import "Growing.h"`并添加初始化方法。

```swift
#import "Growing.h"
- (BOOL)application:(UIApplication *)application
didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
  ...
  // 启动GrowingIO

   [Growing startWithAccountId:@"您的项目ID"];      // 替换为您的项目ID
      // 其他配置
      // 开启Growing调试日志 可以开启日志
      // [Growing setEnableLog:YES];
```

{% hint style="warning" %}
请确保将代码添加在上述位置，添加到其他方法或异步block中可能导致数据不准确。
{% endhint %}

### 4.添加激活圈选的代码

> 在 AppDelegate 中添加激活圈选的代码

{% hint style="warning" %}
因为您代码的复杂程度以及iOS SDK的版本差异，有时候 \[Growing handleUrl:url\] 并没有被调用。请在各个平台上调试这段代码，确保当App被URL scheme唤醒之后，该函数能被调用到。
{% endhint %}

```swift
- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation
{
    ...
 if ([Growing handleUrl:url]) // 请务必确保该函数被调用
  {
      return YES;
  }
  return NO;
 ...
}
```

常用示例：

若您在 AppDelegate 中实现了以下一个或多个方法，请在已实现的函数中，调用`[Growing handleUrl:]`

```swift
- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(nullable NSString *)sourceApplication annotation:(id)annotation
- (BOOL)application:(UIApplication *)application handleOpenURL:(NSURL *)url
- (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString*, id> *)options
```

若以上所有方法均未实现，请实现以下方法并调用`[Growing handleUrl:]`

```swift
- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(nullable NSString *)sourceApplication annotation:(id)annotatio
```

## 2. 重要配置

{% hint style="info" %}
下列内容为常用配置，更多属性及接口详细信息见 Growing.h
{% endhint %}

### 1. 设置页面别名

有些时候，当您代码中的原有页面标题不足以支持业务人员对页面进行识别时，您可以使用此接口设置一个容易识别的页面名称来替换页面标题字段。

为处理这种场景，我们提供了取别名的方法，方法如下：

```java
//手动标识该页面的标题，必须在该UIViewController显示之前设置
@property (nonatomic,copy) NSString* growingAttributesPageName;
```

{% hint style="info" %}
1. 必须在该UIViewController显示之前设置。
2. 页面别名建议设置为汉字、字母、数字、下划线的组合。
3. 未查看数据方便，请尽量对不同端、不同页面的取不同的名称。
{% endhint %}

### 2. 设置界面元素ID

当您的应用界面改版时，可能会导致无法准确地统计已经圈选的元素。因此，对于应用中的主要流程涉及到的界面元素，建议您为它们设置固定的唯一ID，以保证数据的一致性。

{% hint style="info" %}
* 主要流程是指登录、注册、购买、发帖等操作步骤
* 被设置 ID 的对象是界面的重要元素，如“注册”、“结算”、“发布”等按钮
{% endhint %}

若要为元素设置ID，请在viewWillAppear或者时机更早的方法里添加以下代码：

```swift
-(void)viewWillAppear {
    UIView *MyView;
    …
    MyView.growingAttributesUniqueTag = @"my_view";
}
```

{% hint style="danger" %}
* ID 只能设置为字母、数字和下划线的组合
* 对于已经集成过旧版SDK并圈选过的应用，对某个元素设置ID后再圈选它，指标数值会从零开始计算，类似初次集成SDK后发版的效果，但不影响之前圈选的其它指标数据。如果不希望出现这种情况，请不要使用这个方法。
{% endhint %}

### 3. 设置元素内容

当您想采集一些可能没有文字的控件（比如UIImageView，UIView）时，也可以给属性growingAttributesValue 赋值作为文字，用来在圈选的时候区分不同的内容。

如果您的 app 上方有横向滚动的 Banner 广告，若要收集 Banner 相关数据，请在响应点击的控件上添加如下代码：

```java
UIView *view;
…
view.growingAttributesValue = 广告的唯一ID;
```

其中 view 是您的广告元素，请确保两点：

* 对不同广告图，广告的唯一 ID 也不相同
* 响应点击的控件，与设置 ID 的控件是同一个

#### 【例子】当您的横向滚动广告共有3张广告图时，您可以在3个响应点击的View上分别设置不同的广告唯一ID，实现方式： <a id="li-zi-dang-nin-de-heng-xiang-gun-dong-guang-gao-gong-you-3-zhang-guang-gao-tu-shi-nin-ke-yi-zai-3-ge-xiang-ying-dian-ji-de-view-shang-fen-bie-she-zhi-bu-tong-de-guang-gao-wei-yi-id-shi-xian-fang-shi"></a>

```swift
view1.growingAttributesValue = @"ad1";
view2.growingAttributesValue = @"ad2";
view3.growingAttributesValue = @"ad3";
```

### 4. 采集输入框数据

如果您需要采集应用内某个输入框内的文字（例如搜索框），请调用如下接口进行设置：

```swift
UIView *view; // view 可以是 UITextField, UITextView, UISearchBar
 ...
view.growingAttributesDonotTrackValue = NO;
```

view代表要被采集的输入框。 当这个输入框失去焦点（包括应用退到后台），且输入框内容跟获取焦点前相比发生变化时，输入框内文字会被发送回GrowingIO。

{% hint style="info" %}
对于密码输入框，即便标记为需要采集，SDK也会忽略，不采集它的数据。
{% endhint %}

### 5. Facebook广告SDK

如果您使用了 Facebook 广告 SDK，请务必在 main 函数第一行调用以下代码来避免冲突，否则可能造成无法创建项目或者统计准确性问题。注意：APP启动后，将不允许修改采集模式。

```swift
[Growing setAspectMode:GrowingAspectModeDynamicSwizzling];
```

### 6  采集WebView页面数据

SDK会自动采集H5页面的数据，不需要特殊配置。

### 7. 采集GPS数据

如果您的应用有相应的圈选，SDK将自动采集您的GPS数据。

{% hint style="info" %}
SDK 2.8.6及以上版本支持手动关闭采集GPS数据。

`//设置为NO，将关闭GPS采集    
+(void)setEnableLocationTrack:(BOOL)enable;`
{% endhint %}

### 8. 启用Hashtag识别

您可以在项目中添加以下方法以启用Hashtag识别：

```swift
// 设置为 YES, 将启用 HashTag
+ (void)enableHybridHashTag:(BOOL)enable;
```

### 9. GDPR数据采集开关

{% hint style="warning" %}
SDK 版本支持：2.3.2及以上。
{% endhint %}

GrowingIO SDK 针对欧盟区的一般数据保护法（GDPR）提供了以下的API共开发者调用。

```text
// 开启GDPR，不采集数据
[Growing disableDataCollect];

// 关闭GDPR，采集数据
[Growing enableDataCollect];
```

### 10. DeepLink & Universal Link

| DeepLink功能 | SDK版本 |
| :--- | :--- |
| 基础DeepLink功能（Scheme打开App至首页） | &gt;=2.3.0 |
| 直达落地页（Scheme打开至活动页） | &gt;=2.3.2 |
| Universal Link、应用宝微下载链接支持 | &gt;=2.4.1 |

#### DeepLink

1. 确认URl Scheme添加正确。
2. 添加自定义参数回调方法：

```swift
/**
 deeplink广告落地页参数回调设置
​
 @param handler deeplink广告落地页参数回调, params 为解析正确时回调的参数, processTime为从app被deeplink唤起到handler回调的时间(单位秒), error 为解析错误时返回的参数.
                 handler 默认为空, 客户需要手动设置.
 */
+ (void)registerDeeplinkHandler:(void(^)(NSDictionary *params, NSTimeInterval processTime, NSError *error))handler;
```

```swift
//DeepLink 调用示例
[Growing registerDeeplinkHandler:^(NSDictionary *params, NSTimeInterval processTime, NSError *error) {
        NSLog(@"params : %@", params);
        XCTAssertNotNil(params);
        XCTAssertEqualObjects(params[@"key1"], @"value1");
        XCTAssertEqualObjects(params[@"key2"], @"value2");
 }];
```

{% hint style="info" %}
* params参数为您在DeepLink页面设置的”直达落地页参数“。
* SDK版本 &lt; 2.8.5 请在 `+ (BOOL)handleUrl:(NSURL*)url`被调用前注册回调方法。
* SDK版本 &gt;= 2.8.5 请保证注册回调方法的时机在startWithAccountId函数之前,并且在主线程当中。
{% endhint %}

#### Universal Link

使用Universal Link唤醒App，步骤如下：

1. 配置链接：[配置Universal Link、应用宝微下载（可选项）](../../../chan-pin-shi-yong-wen-dang-fen-ban/guang-gao-jian-ce/chan-pin-pei-zhi/deeplink.md#ios-ying-yong-pei-zhi)。 
2. 请在AppDelegate.m添加以下代码：

```java
- (BOOL)application:(UIApplication *)application continueUserActivity:(NSUserActivity *)userActivity restorationHandler:(void (^)(NSArray * _Nullable))restorationHandler{
    [Growing handleUrl:userActivity.webpageURL];
    return YES;
}
```

1. 添加Universal Link参数解析回调方法，此方法与DeepLink方法一致。

### 11. App Store提交应用注意事项

如果您添加了库**AdSupport.framework**，GrowingIO则会启用 IDFA，所以在向 App Store 提交应用时，需要：

* 对于问题 **Does this app use the Advertising Identifier \(IDFA\)**，选择 **YES**。
* 对于选项**Attribute this app installation to a previously served advertisement**，打勾。
* 对于选项**Attribute an action taken within this app to a previously served advertisement**，打勾。

> **为什么 GrowingIO 使用 IDFA?**
>
> GrowingIO 使用 IDFA 来做来源管理激活设备的精确匹配，让你更好的衡量广告效果。如您不希望启用IDFA，可以选择不引入 AdSupport.framework

### 12. 采集推送

在**IOS SDK 2.6.3** 版本， 支持采集用户**点击**本应用的通知的题和内容。此功能默认关闭，如需开启，请在 Application 初始化 GrowingIO 中设置，例如：

```swift
- (BOOL)application:(UIApplication *)application
    didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
 ...
  //开启推送点击采集
  [Growing disablePushTrack:NO];
  ...
  }
```

**查看通知采集数据**

支持对于通知的展现和点击事件的采集，GrowingIO 并未增加新的采集事件类型，而是使用了自定义事件发送，所以需要您创建自定义事件和事件级变量，事件级变量标识符为**`notification_title`**，**`notification_content`**，自定义事件的标识符为**`notification_show`**，**`notification_click`**如图：

{% hint style="info" %}
iOS SDK 不支持通知展现的事件采集，但是 Android SDK 支持。

这里为了满足大部分客户都有 Android 和 iOS 两个应用的情况，创建的推送展示自定义事件的统计值为0。
{% endhint %}

### 13. 浏览事件的半自动采集配置

> SDK版本支持：&gt;=2.8.4

{% hint style="info" %}
「用户浏览事件」半自动采集方案已经上线，详细配置请参考[iOS半自动采集浏览事件](ios-imp.md)。

* 事件/元素采集更具针对性，提升采集效率
* 优化采集逻辑，贴合业务场景，提升数据准确性
* 浏览事件关联自定义事件和变量，减少研发埋点工作量
{% endhint %}

## 3.自定义数据上传

除上述的用户行为数据（无埋点数据）之外，GrowingIO 还提供了多种 API 接口，供您上传一些自定义的数据指标及维度 ，请参考iOS SDK API &gt; [自定义数据上传API](ios-sdk-api/customize-api.md) 。

## 4. 创建应用

{% hint style="danger" %}
**添加代码之后，请先Clean项目，然后再进行编译，并在你的 iOS App 安装了 SDK 后重新启动几次 App，保证行为采集数据自动发送给 GrowingIO，以便顺利完成检测。**
{% endhint %}

在GrowingIO平台的应用创建页面继续完成应用创建的数据检测，检测成功后应用创建成功。

## 5. 验证SDK是否正常采集数据

{% hint style="info" %}
了解GrowingIO平台数据采集类型请参考[数据模型](../../../introduction/datamodel/)。
{% endhint %}

GrowingIO为您提供多种验证SDK是否正常采集数据的方式：

方式一：[Mobile Debugger](../../debugging/mobile-debugger.md)

方式二：在SDK中设置了Debug模式后，在IDE编译器控制台查看数据采集日志。

方式三：[数据校验](../../../chan-pin-shi-yong-wen-dang-fen-ban/shu-ju-zhong-xin/shu-ju-xiao-yan/datacheck.md)

