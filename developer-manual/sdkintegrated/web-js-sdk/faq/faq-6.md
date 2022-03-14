# 元素没有元素浏览量怎么处理？

首先，确认该元素是不是通过display:none/控制其显隐的。对于 display 为 none 的元素，我们会只采集 a 和 button 标签的浏览量，所以如果您想要一个 display 为 none 的元素<或其子元素>的浏览量，把元素改为 a 或 button 标签实现。并且还需要确认您的网站是否配置了[元素浏览事件可采集](../web-sdk-api/websdk-apiv2.md#1.-chu-shi-hua)。
