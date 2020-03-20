# 导出流程

原始数据导出包括鉴权、获取链接、下载三个过程。

![](../../../../.gitbook/assets/image%20%2866%29.png)

鉴权：获取Authorization，参考[认证](../../authenticate/)章节。

获取下载链接：获取请求API的响应中的downloadLinks，参见[按事件类型导出原始数据](../definition/eventtype.md)和[导出全部事件类型原始数据](../definition/alltype.md)。

下载：通过“获取连接”获取到的链接下载文件。

