# 同时集成了web sdk 和 hybrid sdk 会怎么处理？

GrowingIO SDK 提供了一个全局变量 webViewRequestSend，在 web sdk 中会判断当用户设置 window.webViewRequestSend 为 false 并且 hybrid sdk 加载成功，则 web sdk 不再采集数据。
