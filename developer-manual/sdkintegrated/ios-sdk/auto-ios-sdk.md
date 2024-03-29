# 无埋点 SDK集成

无埋点 SDK 具备自动采集基本的用户行为事件，比如访问，页面浏览，元素点击等行为数据。同时也包含埋点SDK的所有功能。

## 准备条件

获取项目ID，请参考[查看项目基本信息](../../../product-manual/projectmange/details.md)。

获取URL Scheme，在GrowingIO平台创建对应的应用时会生成URL Scheme。请参考[创建应用](../../../product-manual/projectmange/application-manage.md#chuang-jian-ying-yong)。

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

• GrowingCoreKit (组件基础库,具备分析功能)

• GrowingAutoTrackKit (无埋点库)

{% hint style="warning" %}
请保证Growing、GrowingCoreKit、GrowingAutoTrackKit版本号一致。
{% endhint %}

### 1. 添加依赖

{% tabs %}
{% tab title="使用CocoaPods快速添加" %}
1. 在您的Podfile中添加`pod 'GrowingAutoTrackKit'`。
2. 执行或 `pod update` 更新pod依赖库。不要使用 `--no-repo-update`选项。
3. （可选）GrowingIO推荐您添加 **AdSupport.framework** 依赖库，用于来源管理激活匹配,有利于您更好的分析数据 ,添加项目依赖库的位置在项目设置target -> 选项卡General -> Linked Frameworks and Libraries
{% endtab %}

{% tab title="手动添加" %}
1. 下载iOS SDK以下包：[GrowingHeader](https://assets.growingio.com/sdk/ios/GrowingIO-iOS-PublicHeader-2.9.14.zip) ，[GrowingCoreKit](https://assets.growingio.com/sdk/ios/GrowingIO-iOS-CoreKit-2.9.14.zip)，[GrowingAutoTrackKit](https://assets.growingio.com/sdk/ios/GrowingIO-iOS-AutoTrackKit-2.9.14.zip)，并解压。
2. 将`Growing.h`、`GrowingCoreKit.framework`、`GrowingAutoTrackKit.framework`添加到iOS工程中。

{% hint style="info" %}
提醒：记得勾选”Copy item if needed“
{% endhint %}
{% endtab %}
{% endtabs %}

在工程项目中添加以下库文件。

> 添加项目依赖库的位置在项目设置target -> 选项卡General -> Linked -> Linked Frameworks and Librarie

| 库名称                           | 说明                     |
| ----------------------------- | ---------------------- |
| Foundation.framework          | 基础依赖库                  |
| Security.framework            | 用户App连接圈选页面SSL连接       |
| CoreTelephony.framework       | 用于读取运营商                |
| SystemConfiguration.framework | 用于判断网络状态               |
| AdSupport.framework           | 用于来源管理激活匹配             |
| libicucore.tbd                | 用户App连接圈选页面解析          |
| libsqlite3.tbd                | 存储日志                   |
| CoreLocation.framework        | 用于读取地理位置信息（如果您的App有权限） |
| JavaScriptCore.framework      | Web圈选App交互             |
| WebKit.framework              | Web圈选                  |

添加编译参数，并注意大小写。

![](<../../../.gitbook/assets/image (77).png>)

### 2. 添加 URL Scheme <a href="#urlscheme" id="urlscheme"></a>

URL Scheme 是您在 GrowingIO 平台创建应用时生成的该应用的唯一标识。把 URL Scheme 添加到您的项目中，以便在使用圈选，Mobile  Debugger，及深度链接功能时唤醒您的应用。

{% hint style="info" %}
URL Scheme 只能对应一个应用。当应用的包名发生变化时，需再次创建一个应用使用对应的 URL Scheme
{% endhint %}

![](<../../../.gitbook/assets/image (79).png>)

### 3. 初始化配置

在 AppDelegate 中引入`#import "Growing.h"`并添加初始化方法。

**为使 App 合规，请参考**[**iOS合规步骤**](../compliance/ios-sdk-he-gui-shuo-ming.md#he-gui-bu-zhou)**。**

{% tabs %}
{% tab title="Objective-C" %}
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
{% endtab %}

{% tab title="Swift" %}
```swift
import UIKit
import GrowingAutoTrackKit

@main
class AppDelegate: UIResponder, UIApplicationDelegate {



    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        // Override point for customization after application launch.
        Growing.start(withAccountId: "您的项目ID")
        return true
    }
    
    ...
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
请确保将代码添加在上述位置，添加到其他方法或异步block中可能导致数据不准确。
{% endhint %}

### 4.添加激活圈选的代码

在 AppDelegate 中添加激活圈选的代码

{% hint style="warning" %}
因为您代码的复杂程度以及 iOS SDK 的版本差异，有时候 `[Growing handleUrl:url]` 并没有被调用。请在各个平台上调试这段代码，确保当App被URL scheme唤醒之后，该函数能被调用到。
{% endhint %}

{% tabs %}
{% tab title="Objective-C" %}
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
{% endtab %}

{% tab title="Swift" %}
```swift
func application(_ app: UIApplication, open url: URL, options: [UIApplication.OpenURLOptionsKey : Any] = [:]) -> Bool {
    ...
    if (Growing.handle(url)) {
        return true
    }
    return false
    ...
}
```
{% endtab %}
{% endtabs %}

常用示例：

若您在 AppDelegate 中实现了以下一个或多个方法，请在已实现的函数中，调用`[Growing handleUrl:]`

{% tabs %}
{% tab title="Objective-C" %}
```objectivec
- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(nullable NSString *)sourceApplication annotation:(id)annotation
- (BOOL)application:(UIApplication *)application handleOpenURL:(NSURL *)url
- (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString*, id> *)options
```
{% endtab %}

{% tab title="Swift" %}
```swift
func application(_ app: UIApplication, open url: URL, options: [UIApplication.OpenURLOptionsKey : Any] = [:]) -> Bool
func application(_ application: UIApplication, handleOpen url: URL) -> Bool
func application(_ application: UIApplication, open url: URL, sourceApplication: String?, annotation: Any) -> Boolw
```
{% endtab %}
{% endtabs %}

若以上所有方法均未实现，请实现以下方法并调用`[Growing handleUrl:]`

{% tabs %}
{% tab title="Objective-C" %}
```swift
- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(nullable NSString *)sourceApplication annotation:(id)annotatio
```
{% endtab %}

{% tab title="Swift" %}
```swift
func application(_ application: UIApplication, open url: URL, sourceApplication: String?, annotation: Any) -> Bool
```
{% endtab %}
{% endtabs %}

## 2. 重要配置

{% hint style="info" %}
下列内容为常用配置，更多属性及接口详细信息见 Growing.h
{% endhint %}

### 1. 设置页面名称

有些时候，当您代码中的原有页面不足以支持业务人员对页面进行识别时，您可以使用此接口设置一个容易识别的页面名称来替换页面浏览事件的`p`字段。

为处理这种场景，我们提供了取别名的方法，方法如下：

```java
//手动标识该页面的标题，必须在该UIViewController显示之前设置
@property (nonatomic,copy) NSString* growingAttributesPageName;
```

{% hint style="info" %}
使用 `setPageName` 接口需要提前规划好页面名称。需保证业务上同一页面的页面名称保持不变，否则会造成同一页面的页面浏览量数据不准确。
{% endhint %}

{% hint style="info" %}
1. 必须在该UIViewController显示之前设置。
2. 页面别名建议设置为汉字、字母、数字、下划线的组合。
3. 为了查看数据方便，请尽量对不同端、不同页面的取不同的名称。
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

当您想采集一些可能没有文字的控件（比如UIImageView，UIView）时，可以给属性growingAttributesValue 赋值作为文字，用来在圈选的时候区分不同的内容。

如果您的 app 上方有横向滚动的 Banner 广告，若要收集 Banner 相关数据，请在响应点击的控件上添加如下代码：

```java
UIView *view;
…
view.growingAttributesValue = 广告的唯一ID;
```

其中 view 是您的广告元素，请确保两点：

* 对不同广告图，广告的唯一 ID 也不相同
* 响应点击的控件，与设置 ID 的控件是同一个

#### 【例子】当您的横向滚动广告共有3张广告图时，您可以在3个响应点击的View上分别设置不同的广告唯一ID，实现方式： <a href="#li-zi-dang-nin-de-heng-xiang-gun-dong-guang-gao-gong-you-3-zhang-guang-gao-tu-shi-nin-ke-yi-zai-3-ge" id="li-zi-dang-nin-de-heng-xiang-gun-dong-guang-gao-gong-you-3-zhang-guang-gao-tu-shi-nin-ke-yi-zai-3-ge"></a>

```swift
view1.growingAttributesValue = @"ad1";
view2.growingAttributesValue = @"ad2";
view3.growingAttributesValue = @"ad3";
```

### 4. 采集输入框数据

GrowingIO SDK 默认仅采集输入框内容改变次数，不采集输入框内的文字。

如果您需要采集应用内某个输入框内的文字（例如搜索框），请调用如下接口进行设置：

```swift
UIView *view; // view 可以是 UITextField, UITextView, UISearchBar
 ...
view.growingAttributesDonotTrackValue = NO;
```

view代表要被采集的输入框。 当这个输入框失去焦点（包括应用退到后台），且输入框内容跟获取焦点前相比发生变化时，输入框内文字会被发送回GrowingIO。

{% hint style="info" %}
对于密码输入框，即是被标记为需要采集输入框的文字，SDK不会进行采集。
{% endhint %}

### 5. Facebook广告SDK使用适配

如果您使用了 Facebook 广告 SDK，请务必在 main 函数第一行调用以下代码来避免冲突，否则可能造成无法创建项目或者统计准确性问题。注意：APP启动后，将不允许修改采集模式。

```swift
[Growing setAspectMode:GrowingAspectModeDynamicSwizzling];
```

### 6.  采集WebView页面数据

无埋点 SDK 会自动采集H5页面的数据，不需要特殊配置。

### 7. 采集GPS数据

用户开启相应获取地理位置信息权限，在SDK初始化前调用如下接口，设置为 `YES` （默认值），当 App 调用获取地理位置API 时，SDK会同步采集地理位置信息。用户未开启权限，则不采集。

如果希望禁止采集地理位置信息，在SDK初始化前调用如下接口，设置为 `NO`。

{% hint style="success" %}
如果没有用户的地理位置信息，我们会根据用户的`ip模糊匹配`用户所在城市地区，能够在最终的数据分析时看到`APP`用户地域分布。
{% endhint %}

{% hint style="info" %}
SDK 2.8.6及以上版本支持手动关闭采集地理位置信息数据。

`//在SDK初始化之前调用，设置为NO，将关闭地理位置信息采集`  \
`+(void)setEnableLocationTrack:(BOOL)enable;`
{% endhint %}

### 8. 设置内嵌H5页面锚点跳转触发页面浏览事件

GrowingIO SDK 默认情况下，不会把`HashTag`识别成页面 URL 的一部分，内嵌H5页面点击锚点页面跳转不计为页面浏览事件。

对于使用`HashTag`进行页面跳转的单页面网站应用来说，可以启用它来标识页面，`HashTag`的值也会记录在页面URL中。启用之后，如果用户点击页面中的锚点进行页面跳转，则发送一次页面浏览事件。

在SDK初始化代码中添加如下代码：

```swift
// 设置为 YES, 将启用 HashTag
+ (void)enableHybridHashTag:(BOOL)enable;
```

{% hint style="danger" %}
如果内嵌H5页面集成了Web JS SDK，则 Web JS SDK 中 [HashTag](../web-js-sdk/latest-jssdk.md#1.-hashtag-xi-tong-bian-liang) 配置有效，该接口调用无效
{% endhint %}

### 9. GDPR数据采集开关

{% hint style="warning" %}
SDK 版本支持：2.3.2及以上。
{% endhint %}

GrowingIO SDK 针对欧盟区的一般数据保护法（GDPR）提供了以下的API共开发者调用。

```
// 开启GDPR，不采集数据
[Growing disableDataCollect];

// 关闭GDPR，采集数据
[Growing enableDataCollect];
```

### 10. DeepLink & Universal Link

| DeepLink功能                   | SDK版本   |
| ---------------------------- | ------- |
| 基础DeepLink功能（Scheme打开App至首页） | >=2.3.0 |
| 直达落地页（Scheme打开至活动页）          | >=2.3.2 |
| Universal Link、应用宝微下载链接支持    | >=2.4.1 |

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
* SDK版本 < 2.8.5 请在 `+ (BOOL)handleUrl:(NSURL*)url`被调用前注册回调方法。
* SDK版本 >= 2.8.5 请保证注册回调方法的时机在startWithAccountId函数之前,并且在主线程当中。
{% endhint %}

#### Universal Link

使用 Universal Link 唤醒App，步骤如下：

1. 配置链接：[配置Universal Link、应用宝微下载（可选项）](../../../product-manual/growing/product-configuration/deeplink.md#ios-ying-yong-pei-zhi)。&#x20;
2. 请在AppDelegate.m添加以下代码：

```java
- (BOOL)application:(UIApplication *)application continueUserActivity:(NSUserActivity *)userActivity restorationHandler:(void (^)(NSArray * _Nullable))restorationHandler{
    [Growing handleUrl:userActivity.webpageURL];
    return YES;
}
```

3\. 添加Universal Link参数解析回调方法，此方法与DeepLink方法一致。

### 11. App Store提交应用注意事项

如果您添加了库**AdSupport.framework**，GrowingIO则会启用 IDFA，所以在向 App Store 提交应用时，需要：

* 对于问题 **Does this app use the Advertising Identifier (IDFA)**，选择 **YES**。
* 对于选项**Attribute this app installation to a previously served advertisement**，打勾。
* 对于选项**Attribute an action taken within this app to a previously served advertisement**，打勾。

> **为什么 GrowingIO 使用 IDFA?**
>
> GrowingIO 使用 IDFA 来做来源管理激活设备的精确匹配，让你更好的衡量广告效果。如您不希望启用IDFA，可以选择不引入 AdSupport.framework

#### 关于 IDFA 权限获取

* 对于iOS 14之前，你无需主动获取 `广告标识IDFA` 的权限
* 对于iOS 14之后，你需要使用如下方法来开启你的 `广告标识IDFA` 的权限

{% hint style="info" %}
2021 年 4 月 27 日，iOS 14.5 正式发布，新版本的 iOS 最主要变化如下：

自 iOS14.5、iPadOS 14.5 和 tvOS 14.5 开始，所有 App 都必须使用 `AppTrackingTransparency` 框架来征得用户的许可，才能对其进行跟踪或访问其设备的广告标识符。

And starting with iOS 14.5, iPadOS 14.5, and tvOS 14.5, you’ll be required to ask users for their permission to track them across apps and websites owned by other companies.
{% endhint %}

1.  Plist 文件中添加 `NSUserTrackingUsageDescription`

    ```
    <key>NSUserTrackingUsageDescription</key>
    <string>GrowingIO测试demo 需要使用你的广告标识信息以用于数据追踪分析</string> //描述内容请根据App修改
    ```
2. 导入框架 `#import <AppTrackingTransparency/AppTrackingTransparency.h>`
3.  调用获取权限代码

    ```
    - (void)applicationDidBecomeActive:(UIApplication *)application {
      // 调用AppTrackingTransparency相关实现请在ApplicationDidBecomeActive之后，适配iOS 15
      // 参考: https://developer.apple.com/forums/thread/690607?answerId=688798022#688798022
      if (@available(iOS 14, *)) {
         // iOS14及以上版本需要先请求权限
         [ATTrackingManager requestTrackingAuthorizationWithCompletionHandler:^(ATTrackingManagerAuthorizationStatus status) {
             switch (status) {
                 case ATTrackingManagerAuthorizationStatusDenied:
                     //用户拒绝向App授权
                     break;
                 case ATTrackingManagerAuthorizationStatusAuthorized:
                     //用户同意向App授权
                     break;
                 case ATTrackingManagerAuthorizationStatusNotDetermined:
                     //用户未做选择或未弹窗
                     break;
                 case ATTrackingManagerAuthorizationStatusRestricted:
                     //用户在系统级别开启了限制广告追踪
                     break;
                 default:
                     break;
             }
         }];
     }
    }
    ```

#### 关于使用 IDFA 作为访问用户ID

GrowingIO SDK 使用 访问用户ID 标识访问用户 ，其值使用 IDFA 、IDFV 或 随机字符串 ，三者的优先级为 IDFA > IDFV > 随机字符串 ，例如：如果获取不到 IDFA，SDK 会使用 IDFV 作为访问用户ID。

访问用户ID生成时机是在 SDK 第一次初始化时，生成之后会被存储在 Keychain 中，如果 Keychain 数据一直存在，则访问用户ID不会发生改变。

如果需要使用 IDFA 作为访问用户ID，则需要在请求获取 IDFA 权限之后再初始化SDK。如果用户不允许广告跟踪，则会按照 IDFV > 随机字符串 的逻辑生成访问用户ID。

```
- (void)applicationDidBecomeActive:(UIApplication *)application {
  // 调用AppTrackingTransparency相关实现请在ApplicationDidBecomeActive之后，适配iOS 15
  // 参考: https://developer.apple.com/forums/thread/690607?answerId=688798022#688798022
  if (@available(iOS 14, *)) {
    [ATTrackingManager requestTrackingAuthorizationWithCompletionHandler:^(ATTrackingManagerAuthorizationStatus status) {
      // 初始化 GrowingIO SDK
    }];
  } else {
    // 初始化 GrowingIO SDK
  }
}
```

{% hint style="info" %}
使用 IDFA 作为访问用户ID，同时为使 App 合规，则第一次SDK初始化应该在 用户同意隐私协议和获取 IDFA 权限之后。参考[合规步骤](../compliance/ios-sdk-he-gui-shuo-ming.md#he-gui-bu-zhou)
{% endhint %}

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

> SDK版本支持：>=2.8.4

{% hint style="info" %}
「用户浏览事件」半自动采集方案已经上线，详细配置请参考[iOS半自动采集浏览事件](ios-imp.md)。

* 事件/元素采集更具针对性，提升采集效率
* 优化采集逻辑，贴合业务场景，提升数据准确性
* 浏览事件关联自定义事件和变量，减少研发埋点工作量
{% endhint %}

### 14. 设置SDK异常上传开关 <a href="#5-she-zhi-dan-chuang-sdk-yi-chang-shang-chuan-kai-guan" id="5-she-zhi-dan-chuang-sdk-yi-chang-shang-chuan-kai-guan"></a>

SDK默认会开启收集SDK内部异常上报至服务端功能，方便开发更好的追踪SDK问题和完善SDK功能。如果您不希望收集SDK内部异常，或者和您的 crash 收集框架有冲突，您可以关闭该功能。

{% hint style="info" %}
请在 startWithAccountId: 或 startWithAccountId: withSampling: 接口之前设置 (SDK2.8.9以后)
{% endhint %}

```
- (void)setUploadExceptionEnable:(BOOL)uploadExceptionEnable;
```

```objectivec
// sdk crash 收集
[Growing setUploadExceptionEnable:YES];
[Growing startWithAccountId:@"aaaa"];
```

### 15. 获取 Apple Search Ads 归因数据分析 <a href="#5-she-zhi-dan-chuang-sdk-yi-chang-shang-chuan-kai-guan" id="5-she-zhi-dan-chuang-sdk-yi-chang-shang-chuan-kai-guan"></a>

如您需要使用 Apple Search Ads 归因数据分析，请在 SDK 初始化之前调用`setAsaEnabled`接口：

```objectivec
// 设置是否获取 Apple Search Ads 归因数据
[Growing setAsaEnabled:YES];
[Growing startWithAccountId:@"aaaa"];
```

在 Target -> Build Phases -> Link Binary With Libraries，添加 iAd.framework 和 AdServices.framework，并设置 AdServices.framework status 为 Optional

![](<../../../.gitbook/assets/image (179).png>)

## 3.自定义数据上传

除上述的用户行为数据（无埋点数据）之外，GrowingIO 还提供了多种 API 接口，供您上传一些自定义的数据指标及维度 ，请参考iOS SDK API > [自定义数据上传API](ios-sdk-api/customize-api.md) 。

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

方式三：[数据校验](https://docs.growingio.com/v3/product-manual/data-center/datacheck/)
