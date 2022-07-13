# 常见问题

## 1.  GrowingIO SDK无埋点采集的原理是什么？

实现原理：[Method Swizzling](http://nshipster.cn/method-swizzling/) ( method swizzling 作用为替换或者修改系统方法)，可理解为以下 5 个步骤。

1. 在系统方法M1中插入GIO代码GIO\_B1
2. 系统方法 M1 被执行，此时也会执行 GIO\_B1
3. 在 GIO\_B1 内遍历 View Tree / DOM Tree 以及 UIViewController 的层次关系以获取必要的数据
4. 生成待发送事件并缓存
5. 发送事件到服务器，完成采集

## 2.  GrowingIO SDK 支持哪些iOS系统？

支持iOS 8 以上，并持续更新适配最新版

## 3. SDK与其他SDK冲突报错，集成其他SDK后不采集数据，SDK开启debug模式无日志输出，APP在部分机型上没有采集到数据，该如何处理？

SDK 支持两种采集模式 Method Swizzling 和 KVO，默认情况下为  KVO。如果您出现问题中的情况，请按照下面方法尝试解决：在 main 方法实现的第一行中添加 `[Growing setAspectMode:GrowingAspectModeDynamicSwizzling];` 。如果工程是是Swift 语言开发的，在 UIAPplicationMain 函数的上方添加 `Growing.setAspectMode(.dynamicSwizzling)`&#x20;

## 4. 如果动态添加UIView、删除UIView或者修改UIView在父视图中的位置，会有什么影响？

SDK  依赖 subviews 里面的元素次序。如果有动态的需求，建议在 viewDidLoad 里加载所有可能的 UIView 节点，添加或删除可以通过设置 hidden 属性来实现，把不需要显示的设置 hidden 属性为 YES，把需要显示的设置 hidden 属性为 NO。在 UIView 已经显示之后，不要调用 -bringSubviewToFront:方法， -sendSubviewToBack:方法或 -insertSubview: 方法。

## 5. 子线程操作UI引起的问题如何处理？

答：GIO SDK 会在主线程中遍历找寻某个subView，如果此时在子线程中删除了该subView，就会造成错乱甚至 crash。此外，Apple 不建议用户在子线程更新 UI。建议客户在 Xcode 中打开 "Main Thread Checker" 检测线程使用是否合理。参考：[Main Thread Checker](https://developer.apple.com/documentation/xcode/diagnosing\_memory\_thread\_and\_crash\_issues\_early)

## 6. 圈选时，来自不同VC的元素显示的VC名称相同？

这种情况，一般是因为父 VC 添加子 VC 方式不正确引起的，请客户排查子VC的生命周期是否完整。

## 7. 是否允许设置view的growingAttributesValue为单个数字或者字母？

不允许这种设置。出于安全考虑，金融类 App 会自定义键盘（默认键盘容易被黑），如果 SDK 允许采集 V 值为单个数字或字母的点击事件，则有可能会记录用户输入的账号或密码。由于上述原因， SDK 不会发送V 值为单个字母或数字的点击事件，如果用户违反约定，则会导致某个元素只有浏览量而没有点击量。

## 8. 埋点为什么也要在主线程调用？

埋点采集UI操作，建议在UI线程（主线程）中调用。

## 9. 是否支持在开启热图的时候圈选？

不支持，开启热图可能会导致被圈选元素的 x 值发生变化。

## 10. 是否支持用UITouch事件的点击事件？

不支持，建议使用 UITapGestureRecognizer

## 11. GIO SDK是否支持Swift项目？

支持

## 12. App做了Button防重复点击，集成SDK后发现按钮无法点击？

如果您的UIButton 防重复方案中， hook了 UIControl 的 originalSelector：`@selector(sendAction:to:forEvent:)` 方法，请确保在您的 swizzledSelector：`@selector(your_swizzled_sendAction:to:forEvent:)` 方法**前面**执行 如下代码:\


```java
- (void)your_swizzled_sendAction:(SEL)action to:(id)target forEvent:(UIEvent *)event {
     
      //  Called before your  extra work
       if ([NSStringFromClass([target class]) isEqualToString:@"GrowingUIControlObserver"]) { 
              [self your_swizzled_sendAction:action to:target forEvent:event]; // call origin
              return;
       }

       // Do your extra work. such as judge click interval....

       [self your_swizzled_sendAction:action to:target forEvent:event]; // call origin
}
```

如果还是无法点击，请联系技术支持。

## 13. 如果项目中使用了Firebase SDK，需要注意什么？

如果您的iOS项目中集成了Firebase SDK，请确保使用的Firebase SDK版本在4.8.1及以上，否则会造成数据采集不到的情况。

当您的Firebase SDK版本符合要求，但是没有发送vst事件时，请将采集模式改为hook模式。

修改方法：

Object-C：修改main.m文件：

![](<../../../.gitbook/assets/image (73).png>)

Swift：修改AppDelegate.swift，并手动创建main.swift文件。

![](<../../../.gitbook/assets/image (74).png>)

![](<../../../.gitbook/assets/image (76).png>)

## 14. 关于苹果隐私政策相关事宜的公告

亲爱的客户：

您好！

从2018年10月3日开始，App Store Connect将要求所有新应用和应用更新版本时提供**隐私政策**，添加后才可以在App Store上提交或通过TestFlight外部测试进行分发。

【苹果通知：As a reminder, in June the App Store Review Guidelines were updated to require a privacy policy for all new apps and app updates as part of the app review process. Starting October 3, 2018, App Store Connect will require a privacy policy for all new apps and app updates before they can be submitted for distribution on the App Store or through TestFlight external testing. In addition, your app’s privacy policy link or text will only be editable when you submit a new version of your app.（详情可参见：[https://developer.apple.com/news/?id=08312018a](https://developer.apple.com/news/?id=08312018a) ）。

所以，在此提醒各位开发者：**提交App Store 审核前一定要准备自己的隐私权政策，并在app SafariViewContoller中弹出，否则会无法通过审核哦！如需要专业的法律意见，还请各位开发者小伙伴咨询您的律师或法律顾问哦！**

## **15. 圈选扫码无法唤起 App**

如果您在圈选或 Mobile Debugger 扫码验证时无法唤起 App，请核对 URL Scheme 是否配置正确，`+[Growing handleUrl:]` 函数调用是否正常，参考[添加 URL Scheme](https://docs.growingio.com/v3/developer-manual/sdkintegrated/ios-sdk/auto-ios-sdk#urlscheme)、[添加激活圈选的代码](https://docs.growingio.com/v3/developer-manual/sdkintegrated/ios-sdk/auto-ios-sdk#4-tian-jia-ji-huo-quan-xuan-de-dai-ma)

[其他圈选问题](../../../product-faq/quanxuan.md#yi-dong-duan-quan-xuan)
