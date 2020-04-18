# 爬虫規則

爬虫规则只对Web平台发送过来的服务器请求生效。

在网站集成了GrowingIO Web JS SDK 之后，用户访问网站的行为数据会以服务器请求的方式发送给 GrowingIO 的服务器，每一条服务器请求都会经过爬虫规则的判断，判断该服务器请求是否是预定义爬虫产生的。

## 开启预定义爬虫规则

在界面右上角单击 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/2019-10-10_18-59-32%20%281%29.png) 选择项目配置，打开项目配置界面。选择**爬虫规则**页签。

打开开关。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28180%29.png)

单击开关右侧的**查看预定义爬虫规则详情**，查看系统预定义的爬虫规则。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2842%29.png)

## 对数据分析的影响

GrowingIO 爬虫规则会过滤事件分析、漏斗分析、分群、细查等数据分析工具中的数据。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/pa-chong-gui-ze-sheng-xiao-tu.png)

{% hint style="info" %}
**出于性能等方面的考虑，目前爬虫规则并没有过回溯功能中的数据。**
{% endhint %}

