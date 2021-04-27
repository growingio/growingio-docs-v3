# iOS SDK合规说明

请升级到最新GrowingIO iOS SDK版本 

2021年4月27日，iOS 14.5正式发布，新版本的iOS最主要变化如下： 自iOS14.5、iPadOS 14.5 和 tvOS 14.5开始，所有 App 都必须使用 AppTrackingTransparency 框架来征得用户的许可，才能对其进行跟踪或访问其设备的广告标识符。 And starting with iOS 14.5, iPadOS 14.5, and tvOS 14.5, you’ll be required to ask users for their permission to track them across apps and websites owned by other companies.

违反规定的App将可能面临无法上架的情况。

为此，请所有使用iOS SDK的客户注意：

* 您需要确保 App 有《隐私政策》，并且在用户首次启动 App 时就弹出《隐私政策》取得用户同意。
* 您需要告知用户您 App 集成了GrowingIO SDK：
  * 如果您没有使用 IDFA, 请在隐私政策中增加如下参考条款： “我们使用了GrowingIO SDK，采集您的 IDFV 信息，用于统计分析您在 App 内的使用效果。”
  * 如果您使用了 IDFA，请在隐私政策中增加如下参考条款： “我们使用了GrowingIO SDK，采集您的 IDFA 信息，用于统计分析您在 App 内的使用效果。”
* 您务必确保用户同意《隐私政策》后，再初始化GrowingIO SDK。

