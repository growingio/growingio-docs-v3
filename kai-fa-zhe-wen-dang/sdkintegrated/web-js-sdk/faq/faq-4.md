# 同时集成了web sdk和hybrid sdk会怎么处理？

我们提供了一个全局变量 webViewRequestSend，在 web sdk 中会判断当用户设置 webViewRequestSend 为 false 并且 hybrid sdk 加载成功，则不进行 web sdk 数据的采集。

