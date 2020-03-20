# 数据校验

{% hint style="info" %}
移动端SDK版本要求：&gt;=2.7.0
{% endhint %}

您可以使用数据校验功能在GrowingIO平台上进行实时的数据校验。

## 小程序端数据校验

一. 在顶部导航栏选择”数据中心 &gt; 数据校验 &gt; 开始校验（仅App）“，进入数据校验模块。

二. 选择小程序应用后，进入小程序用户实时行为数据校验页面。

三. 单击请扫码，使用手机端扫码器扫码弹出的二维码，进行添加手机IP。

![](https://growingio.atlassian.net/wiki/download/thumbnails/990019726/image2019-12-5_17-22-53.png?version=1&modificationDate=1575537741565&cacheVersion=1&api=v2&width=600&height=287)

四. 手机端显示添加IP成功后，请在手机端打开小程序，并关闭GrowingIO的二维码展示。

等待5秒左右，可以看到用户显示在页面中。当有多个用户进行扫码时，您可以使用下面的用户信息进行区分。

![](https://growingio.atlassian.net/wiki/download/thumbnails/990019726/image2019-12-5_17-32-49.png?version=1&modificationDate=1575538338498&cacheVersion=1&api=v2&width=600&height=573)

五. 单击您的用户头像，再单击开始校验，进入实时调试页面。

![](https://growingio.atlassian.net/wiki/download/thumbnails/990019726/image2019-12-5_17-40-14.png?version=1&modificationDate=1575538785203&cacheVersion=1&api=v2&width=600&height=441)

六. 在小程序中进行至少5步以上的操作，在调试页面进行验证。

视网络状况，小程序传回的信息可能会有5~10秒钟的延迟。

## App端数据校验

一. 在顶部导航栏选择”数据中心 &gt; 数据校验 &gt; 开始校验（仅App）“，进入数据校验模块。

![](https://growingio.atlassian.net/wiki/download/thumbnails/990019726/image2019-12-5_20-2-58.png?version=1&modificationDate=1575547348382&cacheVersion=1&api=v2&width=600&height=612)

二. 单击添加事件/变量，选择待验证的自定义事件及其他变量，单击下一步。

![](https://growingio.atlassian.net/wiki/download/thumbnails/990019726/image2019-12-5_19-14-17.png?version=1&modificationDate=1575544428052&cacheVersion=1&api=v2&width=600&height=538)

三. 选择要验证的移动端应用，使用手机端扫码器扫码二维码，唤起手机端App，在App中进行操作，在调试页面进行验证。

![](https://growingio.atlassian.net/wiki/download/thumbnails/990019726/image2019-12-5_19-43-5.png?version=1&modificationDate=1575546156066&cacheVersion=1&api=v2&width=600&height=454)

图中实时展示待验证的自定义事件及变量的验证状态，单击每一条状态可在页面右侧查看变量详情。

四. 验证完成后，单击页面下方的结束校验，生成验证报告。

![](https://growingio.atlassian.net/wiki/download/thumbnails/990019726/image2019-12-5_19-52-56.png?version=1&modificationDate=1575546747147&cacheVersion=1&api=v2&width=600&height=457)

