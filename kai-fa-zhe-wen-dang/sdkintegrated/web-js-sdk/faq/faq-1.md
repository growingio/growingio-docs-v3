# 为什么我们的网站要允许iframe加载？

在 GrowingIO 平台上使用可视化圈选事件功能需要使用 iframe 技术来加载你的页面。如果你的网站禁止了 iframe 加载，就无法正常使用圈选功能定义事件，所以需要设置http响应头允许 iframe 加载。

如果你的网站使用https协议，需向响应头添加配置

```text
Content-Security-Policy: frame-ancestors 'self' https://www.growingio.com
X-Frame-Options: Allow-From https://www.growingio.com
```

如果你的网站使用HTTP协议，需向响应头添加配置

```text
Content-Security-Policy: frame-ancestors 'self' http://www.growingio.com
X-Frame-Options: Allow-From http://www.growingio.com
```

