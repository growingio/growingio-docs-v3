# 元素没有元素浏览量怎么处理？

首先确认这个元素是不是通过display:none/其它 控制显隐的，对于 display 为 none 的元素，我们会只采集 A 和 Button 标签的浏览量，所以如果你想要一个 display 为 none 的元素&lt;或其子元素&gt;的浏览量，把元素改为 A 或 button 标签实现。并且还需要确认你的网站是否配置了[元素浏览量的采集](../latest-jssdk.md#32-imp-xi-tong-bian-liang)。

