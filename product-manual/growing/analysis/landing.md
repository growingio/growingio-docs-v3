# 落地页分析

## 什么是落地页分析 <a id="id-&#x843D;&#x5730;&#x9875;&#x5206;&#x6790;&#x5E2E;&#x52A9;&#x6587;&#x6863;-&#x4E00;&#x3001;&#x4ECB;&#x7ECD;"></a>

落地页分析是对您线上活动页面的分析，只需要输入一个或一组落地页的 URL ，就可以获得基本的活动数据，节约处理数据的时间，直接获得洞察 ，帮助你监控落地页流量和来源情况，高效汇报，开心工作。

落地页分析支持：

* 查看落地页基本的数据流量和质量情况；
* 了解不同页面的转化情况；
* 了解落地页整体流量来源；
* 适于长期监控数据情况随时间的变化；

## 创建落地页分析

一. 在顶部导航栏选择“**获客分析 &gt; 分析 &gt; 落地页分析”**，进入落地页管理页面。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2888%29.png)

二. 单击**创建落地页分析**，进入**新建落地页分析**页面。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28166%29.png)

| 参数 | 说明 |
| :--- | :--- |
| URL | 输入待分析页面的URL，最多支持输入50个。 |

{% hint style="warning" %}
落地页分析**不支持带有查询条件（即原始URL中包含 ?后面的部分，且不可去掉）的页面**。因为一般官网落地页是不会用查询条件的，带有查询条件的可能是商品详情页，因为商品详情页做了广告投放，所以这也是一种分析意义上的落地页，我们建议您设置成页面级变量，在事件分析中使用，落地页分析暂时不支持这样的页面。
{% endhint %}

三. 输入参数后单击**进入分析**，弹出填写落地页分析名称对话框。

四. 填写落地页分析名称后单击**保存**，默认进入当前落地页分析页面。

{% hint style="info" %}
在填写名称时选择取消，也会生成分析。
{% endhint %}

五. 选择落地页分析展示的时间范围。

{% hint style="info" %}
**新创建的落地页分析，不管是否建立过指标，统一回溯过去 31 天数据。**
{% endhint %}

六. 设置转化目标。

> * 您可以将某个事件的发生作为活动目标（比如注册事件、领取优惠券事件等），来作为转化量的衡量。
> * 转化目标可选择埋点事件、无埋点事件、合并事件、计算指标。

## 各模块介绍

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28171%29.png)

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x6A21;&#x5757;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1-&#x9009;&#x62E9;&#x65F6;&#x95F4;</td>
      <td style="text-align:left">
        <p>&#x9009;&#x62E9;&#x843D;&#x5730;&#x9875;&#x5C55;&#x793A;&#x7684;&#x5206;&#x6790;&#x6570;&#x636E;&#x7684;&#x4E8B;&#x4EF6;&#x8303;&#x56F4;&#x3002;</p>
        <p>&#x4E0A;&#x5468;=&#x4E0A;&#x5468;&#x4E00;&#x81F3;&#x4E0A;&#x5468;&#x65E5;&#x3001;&#x4E0A;&#x6708;=&#x4E0A;&#x6708;1&#x65E5;&#x81F3;&#x6708;&#x5E95;&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2-&#x7BA1;&#x7406;URL</td>
      <td style="text-align:left">&#x6DFB;&#x52A0;&#x6216;&#x5220;&#x9664;&#x843D;&#x5730;&#x9875;URL&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">3-&#x5FEB;&#x901F;&#x4E0A;&#x624B;&#x5F15;&#x5BFC;</td>
      <td style="text-align:left">
        <p>&#x521B;&#x5EFA;&#x5B8C;&#x5206;&#x6790;&#x9875;&#x9762;&#x540E;&#x7684;&#x5F15;&#x5BFC;&#x4E8B;&#x9879;&#x3002;</p>
        <p>&#x64CD;&#x4F5C;&#x7B80;&#x5355;&#xFF0C;&#x8DDF;&#x7740;&#x4E00;&#x8D77;&#x505A;&#x4E00;&#x505A;&#xFF0C;&#x5FEB;&#x901F;&#x4E86;&#x89E3;&#x843D;&#x5730;&#x9875;&#x57FA;&#x672C;&#x60C5;&#x51B5;&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">4-&#x6570;&#x636E;&#x6982;&#x89C8;</td>
      <td style="text-align:left">&#x67E5;&#x770B;&#x65F6;&#x95F4;&#x8303;&#x56F4;&#x5185;&#x7684;PV&#x3001;UV&#x3001;&#x65B0;&#x7528;&#x6237;&#x8BBF;&#x95EE;&#x91CF;&#x3001;&#x8DF3;&#x51FA;&#x7387;&#xFF08;&#x4E0D;&#x652F;&#x6301;&#x4ECA;&#x65E5;&#xFF09;&#x3001;&#x9875;&#x9762;&#x505C;&#x7559;&#x65F6;&#x957F;&#xFF08;&#x4E0D;&#x652F;&#x6301;&#x4ECA;&#x65E5;&#xFF09;&#x3002;&#x5982;&#x679C;&#x8BBE;&#x7F6E;&#x4E86;&#x8F6C;&#x5316;&#x76EE;&#x6807;&#xFF0C;&#x8FD8;&#x53EF;&#x4EE5;&#x67E5;&#x770B;&#x65F6;&#x95F4;&#x8303;&#x56F4;&#x5185;&#x7684;&#x8F6C;&#x5316;&#x4EBA;&#x6570;&#xFF0C;&#x8F6C;&#x5316;&#x7387;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">5-&#x8BBE;&#x7F6E;&#x8F6C;&#x5316;&#x76EE;&#x6807;</td>
      <td style="text-align:left">&#x53EF;&#x4EE5;&#x5728;&#x6B64;&#x6A21;&#x5757;&#x8BBE;&#x7F6E;&#x8F6C;&#x5316;&#x76EE;&#x6807;&#xFF0C;&#x8BBE;&#x7F6E;&#x540E;&#x53EF;&#x4EE5;&#x5C55;&#x793A;&#x6765;&#x5230;&#x843D;&#x5730;&#x9875;&#x540E;&#x88AB;&#x8F6C;&#x5316;&#x7684;&#x4EBA;&#x6570;&#x3001;&#x8F6C;&#x5316;&#x7387;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">6-&#x8D8B;&#x52BF;&#x56FE;</td>
      <td style="text-align:left">
        <p>&#x8861;&#x91CF;&#x4E0D;&#x540C;&#x5206;&#x6790;&#x5BF9;&#x8C61;&#x968F;&#x65F6;&#x95F4;&#x7684;&#x6D41;&#x91CF;&#x53D8;&#x5316;&#x8D8B;&#x52BF;&#x3002;</p>
        <ul>
          <li>&#x652F;&#x6301;&#x5207;&#x6362;PV&#x3001;UV&#x4E24;&#x4E2A;&#x6307;&#x6807;&#x3002;</li>
          <li>&#x652F;&#x6301;&#x5207;&#x6362;&#x65F6;&#x95F4;&#x5355;&#x4F4D;&#xFF08;&#x5C0F;&#x65F6;&#x3001;&#x5929;&#x3001;&#x5468;&#x3001;&#x6708;&#xFF09;&#x3002;</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">7-&#x660E;&#x7EC6;&#x8868;</td>
      <td style="text-align:left">
        <p>&#x4EA7;&#x54C1;&#x843D;&#x5730;&#x9875;&#x660E;&#x7EC6;&#x8868;&#x3002;</p>
        <ul>
          <li>&#x652F;&#x6301;&#x5207;&#x6362;&#x5206;&#x6790;&#x5BF9;&#x8C61;&#xFF08;&#x5E7F;&#x544A;&#x6765;&#x6E90;&#x3001;&#x7F51;&#x9875;&#x76D1;&#x6D4B;&#x94FE;&#x63A5;&#x3001;&#x8BBF;&#x95EE;&#x6765;&#x6E90;&#x3001;&#x843D;&#x5730;&#x9875;&#x94FE;&#x63A5;&#x3001;&#x641C;&#x7D22;&#x8BCD;&#xFF09;&#x3002;</li>
          <li>&#x652F;&#x6301;&#x4E0B;&#x8F7D;csv&#x683C;&#x5F0F;&#x7684;&#x660E;&#x7EC6;&#x8868;&#x6587;&#x4EF6;&#x3002;</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>