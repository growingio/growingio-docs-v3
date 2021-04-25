# iOS SDK合规说明

请升级到最新GrowingIO iOS SDK版本 

* 您需要确保 App 有《隐私政策》，并且在用户首次启动 App 时就弹出《隐私政策》取得用户同意。
* 您需要告知用户您 App 集成了GrowingIO SDK：
  * 如果您没有使用 IDFA, 请在隐私政策中增加如下参考条款： “我们使用了GrowingIO SDK，采集您的 IDFV 信息，用于统计分析您在 App 内的使用效果。”
  * 如果您使用了 IDFA，请在隐私政策中增加如下参考条款： “我们使用了GrowingIO SDK，采集您的 IDFA 信息，用于统计分析您在 App 内的使用效果。”
* 您务必确保用户同意《隐私政策》后，再初始化GrowingIO SDK。
