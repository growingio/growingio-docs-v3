# 用户模型

在 GrowingIO 的数据模型中，根据不同的分析场景需要，我们建立了两套用户模型来表达访问用户和登录用户的概念。

举例来说：

> 小明在手机上刷朋友圈时看到了某个电商平台的 H5 广告页面，他点击了这个广告内容，进入了一个引导注册的 H5 页面，小明填写自己的手机号通过验证，注册成功，并在成功页面看到提示下载 App 即送 5 张满减优惠券，小明下载了 App 并登录，选择了自己心仪的产品后使用优惠券结算，完成了购买流程。

上述的例子是一个典型的互联网营销的案例，我们通过上述案例来描述一下 GrowingIO 的两种用户模型分别适合在哪些分析场景下使用。

## 访问用户 <a id="fang-wen-yong-hu"></a>

访问用户ID：是 GrowingIO 为所有终端生成的唯一ID，如果你想要分析的是产品所有访客，可以选择“访问用户”；上面的例子中，小明访问 H5 广告页面时，GrowingIO 会在浏览器中的生成一个唯一的 ID 并记录在cookie 中，这个 ID 将作为小明今后在该 H5 站点的唯一 ID。

基于访问用户 ID，您可以进行渠道、转化等相关的分析，比如通过对广告页面、注册页面、下载页面上的访问用户进行漏斗分析，形成基本的注册转化流程分析。

## 登录用户 <a id="deng-lu-yong-hu"></a>

登录用户 ID：也就是注册用户 ID，当用户访问您的产品并发生注册/登录行为时，您可以通过GrowingIO SDK 中的 API 将该用户的注册 ID（或与之对应的唯一标识，可以加密处理）上传给 GrowingIO。

这个 ID 会被作为今后小明在各个地方使用您的产品的身份识别 ID。在上面的例子中，如果将小明的注册 ID 在小明发生 H5 注册时和 App 登录时通过 API 上传到 GrowingIO，GrowingIO 将可以通过登录用户 ID 将小明在多个平台上的行为归结为同一个人。

基于登录用户ID，您可以进行跨平台分析，也可以在登录用户ID的基础上，将更多的用户个人属性（如：性别、年龄段或您已经分析得出的用户标签）上传给 GrowingIO，从而实现更加高级的业务分析。

更加详细的信息，请您浏览下面的 「访问用户」

