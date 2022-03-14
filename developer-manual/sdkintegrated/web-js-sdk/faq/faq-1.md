# 为什么网站要允许iframe加载？

在 GrowingIO 平台上使用可视化圈选事件功能时，需要使用 iframe 技术来加载您的网站页面。如果网站禁止了 iframe 加载，就无法正常使用圈选功能定义事件，所以需要您的服务器在设置 http 响应头时，允许 iframe 加载。

如果网站使用 https 协议，需向响应头添加如下配置：

```
Content-Security-Policy: frame-ancestors 'self' https://www.growingio.com
X-Frame-Options: Allow-From https://www.growingio.com
```

如果网站使用 http 协议，需向响应头添加如下配置：

```
Content-Security-Policy: frame-ancestors 'self' http://www.growingio.com
X-Frame-Options: Allow-From http://www.growingio.com
```
