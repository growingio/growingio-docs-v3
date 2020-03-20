# App内嵌H5页面常见问题

## 1. H5页面需要集成SDK吗？

如果您集成原生Android无埋点 SDK ， 则不需要单独集成 hybrid sdk ，无埋点 sdk 会将 hybrid sdk 自动注入，并且采集点击、浏览、文本输入等事件。

## 2. H5页面什么情况需要集成Web JS SDK？

如果您的页面，在移动端和网站同时投放，不考虑平台只关注这个页面的数据时，集成 web js sdk 。

此时，由于您集成了 web js sdk ，并且移动端无埋点 sdk 会自动注入 hybrid sdk ，则会发两份数据采集信息，web js sdk 发送一份， hybrid sdk 发送一份。

如果您单独期望关闭 web js sdk 的数据采集，请在Web JS SDK初始化之前调用`window.webViewRequestSend，`值为`false`。

## 3. H5怎么增加自定义事件和变量？

请参考：Web JS SDK埋点文档 和 Hybrid SDK埋点文档。 

[Web JS SDK API](../../web-js-sdk/web-sdk-api/)

[Hybrid SDK API ](../../hybrid-js-sdk.md#mai-dian-api)

