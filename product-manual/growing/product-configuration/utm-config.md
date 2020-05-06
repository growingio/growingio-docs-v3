# 维度配置（链接扩展维度）-done

* 当您需要根据业务情况，希望投放链接可以统计到更多维度数据时，可以使用链接自定义维度配置。
* 举例，如果您想跟踪不同区域的效果数据，可以在此新建自定义为维度参数“area”，显示名称“区域”。配置后，可以在任一GrowingIO的移动监测链接中使用。
* 形如：[https://gio.ren/r3jEmQe](https://gio.ren/r3jEmQe) 这样的链接，配置“area”自定义维度后，可直接在链接后缀此参数，得到 [https://gio.ren/r3jEmQe?area=huabei](https://gio.ren/r3jEmQe?area=huabei) 的新链接。
* 进行投放后，增加的“区域”维度可以在事件分析/用户分群/漏斗等模块引用查看“区域”维度中不同值的表现。
* 其中自定义的维度链接参数需以数字+英文字母表达。显示名称则为在GrowingIO后台中维度的显示名称，可使用中文表达。

## 新增链接参数

一. 在顶部导航栏选择“**获客分析 &gt; 产品配置 &gt; 维度配置”**，进入维度配置功能。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28106%29.png)

二. 单击页面上方的新增链接参数，弹出新增链接参数对话框。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2864%29.png)

| 参数 | 说明 |
| :--- | :--- |
| 链接参数名 | 由英文小写字母、数字、下划线组成，且必须以英文小写字母或下划线开头。 |
| 实际显示名称 | 显示名称，30个字符以内。 |

## 链接参数应用

在链接创建环节中创建一条短链，形如：[https://gio.ren/r3jEmQe](https://gio.ren/r3jEmQe) 这样的链接，可以直接使用 Query String 的方式拼接成：[https://gio.ren/r3jEmQe?city=beijing](https://gio.ren/r3jEmQe?city=beijing) 。则投放北京区域可以直接使用此链接。

在查看数据（事件、分群、漏斗等）时，引用维度“城市”查看不同推广城市带来的效果。

{% hint style="warning" %}
维度值建议使用英文或数字；如果使用中文，请使用 URL Encode 编码。

实例：[https://gio.ren/r3jEmQe?keyword=%e5%a2%9e%e9%95%bf](https://gio.ren/r3jEmQe?keyword=%e5%a2%9e%e9%95%bf)
{% endhint %}

