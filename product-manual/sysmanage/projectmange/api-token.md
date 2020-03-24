# API Token管理

API Token管理功能可直接由系统利用项目的公钥和私钥自动生成Token，省去了您频繁计算导致的错误、失效等问题。

## 生成Token

一. 界面右上角单击 ![](https://docs.growingio.com/.gitbook/assets/-Lo08UtW7H58ehFKeZ4g-Lsu2CWi8CGylwC7jWSB-LsuPIbtjENP0zZy9KaU2019-10-10_18-59-32.png) 选择项目配置，在项目配置界面选择**API token管理**页签。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28116%29.png)

二. 单击**新建API token**，输入描述后单击确定，弹出复制Token界面。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2830%29.png)

三. 复制Token界面关闭后不可再次查看，请您复制生成的token。

{% hint style="warning" %}
注意事项

* 生成的Token 只显示前 5 位字符 + \* + 最后 5 个字符 ，且不可查看原始值，如果忘记必须新建。
* 生成的Token永久生效，您可以手动删除使之失效。
{% endhint %}

{% hint style="success" %}
提醒：

* 多个Token可同时供多个人使用，多个人也可同时使用同一个Token。
* 您可以创建多个Token分给不同的应用或人员使用。
{% endhint %}

## 管理Token

修改描述：单击 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28178%29.png) ，可修改当前Token的描述。

删除：单击 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/la-ji-tong.png) ，可以删除当前Token，删除后该Token即失效。

## 管理代码生成的Token <a id="APIToken&#x7BA1;&#x7406;-&#x7BA1;&#x7406;&#x4EE3;&#x7801;&#x751F;&#x6210;&#x7684;Token"></a>

GrowingIO平台会记录最新由代码生成的Token，代码生成的token不可编辑，可以删除使之失效。

{% hint style="success" %}
为了您的数据安全，GrowingIO 即将禁止使用代码创建 Token，请您使用GrowingIO平台生成的 Token。
{% endhint %}

