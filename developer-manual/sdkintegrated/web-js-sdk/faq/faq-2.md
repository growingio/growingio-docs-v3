# 为什么我的网站不能复写 window 对象？

可视化圈选事件功能使用 HTML5 的 postMessage 技术完成跨域通信。如果window.top、window.parent、window.name被复写，将使通信中断，无法圈选。

如果出于某些原因你不能改变这一设置，建议下载圈选插件进行圈选。 [Web端数据定义（Web圈选）](broken-reference)
