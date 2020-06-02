# KPI看板

## 简介 <a id="kpi-kan-ban-ke-yi-zuo-shi-mo"></a>

KPI看板可以帮助业务负责人在 GrowingIO 平台上监控 KPI 数据，判断 KPI 是否符合预期。若数据与预期不符，用户可以借助维度拆解和下钻，迅速找到影响KPI表现的原因。

您可以将您的 KPI 放在 KPI 看板上，一站式获得KPI所有信息，避免KPI分散在各处。每一个KPI看板可以创建 8 个KPI指标，您可以把对您的组织最重要的KPI 放在一个看板里，对核心指标一览无余。

**以某电商公司 KPI 看板为例子：**

我们将销售量、销售额、用户量、复购、转发等放在KPI看板。您打开KPI看板后，借助大数字图，所有核心指标表现一览无余，帮您迅速了解整体表现和有异常的 KPI。比如，我们可以看到下图中**复购次数**这个KPI出现了问题。同比出现了超过20%的下降。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Lqd9xdJhneyOoLoHdHd-LqdBbNTY0qACdCk186pKPIE79C8BE69DBF.png)

## **规划KPI数据** <a id="ru-he-pei-zhi-yi-ge-zhe-yang-de-kpi-kan-ban"></a>

> 如果已经进行了对KPI的规划和实施，此步骤可以忽略。

首先要确定什么是你的KPI，其次确定要通过哪些维度去监控拆解KPI。

若购买成功是你的核心KPI，你会通过商品品类、渠道、会员等级去监控购买。那么你可以设置购买成功为自定义事件，用商品品类、渠道、会员等级为变量。

将这些数据上传给 GrowingIO之后，即可通过创建KPI单图看到这个KPI对应的数据。

## 创建KPI单图

一. 在顶部导航栏选择"**看板** &gt; **KPI看板**"，进入看板列表的KPI看板列表。

二. 单击列表上方的**创建看板**，新建一个KPI看板并进入看板内。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2881%29.png)

三. 单击**添加KPI**，弹出**创建KPI指标**页面。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28221%29.png)

| 参数 | 说明 |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x65F6;&#x95F4;&#x8303;&#x56F4;</th>
      <th style="text-align:left">
        <p>&#x9009;&#x62E9;&#x65F6;&#x95F4;&#x8303;&#x56F4;&#xFF0C;&#x9009;&#x62E9;
          &#x4ECA;&#x5929;&#x3001;&#x672C;&#x5468;&#x3001;&#x672C;&#x6708;&#x6765;&#x76D1;&#x6D4B;
          KPI &#x6307;&#x6807;&#x7684;&#x65F6;&#x95F4;&#x8303;&#x56F4;&#x3002;</p>
        <ul>
          <li>&#x82E5;&#x60A8;&#x9009;&#x62E9;&#x4ECA;&#x5929;&#xFF0C;&#x53EF;&#x4EE5;&#x770B;&#x5230;&#x4ECA;&#x5929;&#x7684;&#x5C0F;&#x65F6;&#x7EA7;&#x522B;&#x6570;&#x636E;&#xFF0C;&#x5982;&#x679C;&#x4F60;&#x5BF9;&#x67D0;&#x4E00;&#x4E2A;&#x6307;&#x6807;&#x7684;&#x5173;&#x6CE8;&#x5EA6;&#x662F;&#x6BCF;&#x5C0F;&#x65F6;&#x90FD;&#x4F1A;&#x770B;&#x4E00;&#x770B;&#xFF0C;&#x6216;&#x8005;&#x6BCF;&#x534A;&#x5929;&#x90FD;&#x4F1A;&#x770B;&#x4E00;&#x4E0B;&#xFF0C;&#x5EFA;&#x8BAE;&#x9009;&#x62E9;&#x4ECA;&#x5929;&#x3002;</li>
          <li>&#x82E5;&#x60A8;&#x9009;&#x62E9;&#x672C;&#x5468;&#xFF08;&#x4E0D;&#x5305;&#x62EC;&#x4ECA;&#x5929;&#xFF09;&#xFF0C;&#x53EF;&#x4EE5;&#x770B;&#x5230;&#x672C;&#x5468;&#x7684;&#x5929;&#x7EA7;&#x522B;&#x6570;&#x636E;&#xFF0C;&#x5982;&#x679C;&#x4F60;&#x5BF9;&#x67D0;&#x4E00;&#x4E2A;&#x6307;&#x6807;&#x7684;&#x5173;&#x6CE8;&#x5EA6;&#x662F;&#x6BCF;&#x5929;&#x90FD;&#x4F1A;&#x770B;&#x4E00;&#x770B;&#xFF0C;&#x5468;&#x672B;&#x4F1A;&#x505A;&#x4E00;&#x4E2A;&#x603B;&#x7ED3;&#x62A5;&#x544A;&#xFF0C;&#x5EFA;&#x8BAE;&#x9009;&#x62E9;&#x672C;&#x5468;&#x3002;</li>
          <li>&#x82E5;&#x60A8;&#x9009;&#x62E9;&#x672C;&#x6708;&#xFF08;&#x4E0D;&#x5305;&#x62EC;&#x4ECA;&#x5929;&#xFF09;&#xFF0C;&#x53EF;&#x4EE5;&#x770B;&#x5230;&#x672C;&#x6708;&#x5929;&#x7EA7;&#x522B;&#x7684;KPI&#x6570;&#x636E;&#xFF0C;&#x5982;&#x679C;&#x4F60;&#x5BF9;&#x67D0;&#x4E00;&#x4E2A;&#x6307;&#x6807;&#x7684;&#x5173;&#x6CE8;&#x5EA6;&#x662F;&#x6BCF;&#x5929;&#x6216;&#x8005;&#x5468;&#x90FD;&#x4F1A;&#x770B;&#x4E00;&#x770B;&#xFF0C;&#x6708;&#x4F1A;&#x505A;&#x4E00;&#x4E2A;&#x603B;&#x7ED3;&#x62A5;&#x544A;&#xFF0C;&#x5EFA;&#x8BAE;&#x9009;&#x62E9;&#x672C;&#x6708;&#x3002;</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

| 目标用户 | 设置目标人群，以便于了解特殊人群的KPI表现，如重新购买，新注册等。 |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">KPI&#x6307;&#x6807;</th>
      <th style="text-align:left">
        <p>&#x9009;&#x62E9;KPI&#x6307;&#x6807;&#x3002;</p>
        <p>KPI &#x7531; &#x4E8B;&#x4EF6;&#xFF0C;&#x4E8B;&#x4EF6;&#x7684;&#x5EA6;&#x91CF;&#x65B9;&#x5F0F;&#xFF08;&#x4EBA;
          &#x6B21; &#x4EBA;&#x5747;&#xFF09;&#x548C; &#x8FC7;&#x6EE4;&#x6761;&#x4EF6;&#x6784;&#x6210;&#xFF0C;&#x4EE5;&#x4E0B;&#x6307;&#x6807;&#x90FD;&#x53EF;&#x4EE5;&#x662F;
          KPI</p>
        <p>&#x90A3;&#x4E48; &#x8D2D;&#x4E70;&#x4EBA;&#x6570;&#xFF0C; &#x8D2D;&#x4E70;&#x6B21;&#x6570;
          &#xFF0C;&#x5E73;&#x5747;&#x8D2D;&#x4E70;&#x6B21;&#x6570;&#xFF0C; &#x8D2D;&#x4E70;&#x91D1;&#x989D;&#xFF0C;&#x624B;&#x673A;&#x8D2D;&#x4E70;&#x91CF;
          &#x7B49;&#x90FD;&#x53EF;&#x4EE5;&#x6210;&#x4E3A;&#x9009;&#x9879;&#x3002;</p>
        <p>&#x4ED6;&#x53EF;&#x4EE5;&#x501F;&#x52A9;&#x4E8B;&#x4EF6; &#x201C;&#x8D2D;&#x201D;&#x4E70;&#xFF0C;
          &#x201C;&#x8D2D;&#x4E70;&#x201D;&#x4E8B;&#x4EF6;&#x7684;&#x5EA6;&#x91CF;&#x65B9;&#x5F0F;
          &#x4EBA;&#xFF0C; &#x6B21;&#xFF0C; &#x4EBA;&#x5747;&#xFF0C; &#x4E8B;&#x4EF6;&#x7684;&#x53D8;&#x91CF;&#xFF1A;&#x91D1;&#x989D;&#xFF0C;&#x54C1;&#x7C7B;&#x7B49;&#x7EC4;&#x5408;&#x6784;&#x6210;&#x3002;</p>
        <p>&#x6CE8;&#xFF1A;KPI &#x4F5C;&#x4E3A;&#x6838;&#x5FC3;&#x4E1A;&#x52A1;&#x6307;&#x6807;&#xFF0C;&#x9700;&#x8981;&#x901A;&#x8FC7;&#x4E1A;&#x52A1;&#x7EF4;&#x5EA6;&#x5BF9;&#x5176;&#x8FDB;&#x884C;&#x62C6;&#x89E3;&#xFF0C;&#x540C;&#x65F6;&#x5BF9;&#x6570;&#x636E;&#x7684;&#x51C6;&#x786E;&#x6027;&#x7A33;&#x5B9A;&#x6027;&#x6709;&#x8F83;&#x9AD8;&#x7684;&#x8981;&#x6C42;&#xFF0C;&#x6211;&#x4EEC;&#x66F4;&#x5EFA;&#x8BAE;&#x60A8;&#x91C7;&#x7528;&#x57CB;&#x70B9;&#x6307;&#x6807;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

## 设置KPI目标

您可以对KPI设置目标，即使观察目标进度是否符合预期。

在KPI看板内部，单击单个KPI指标框右上角的 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/kpi-kan-ban-dian-dian-dian.png) 选择编辑，在编辑页面设置目标值。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28155%29.png)

设置完成后即可在单个KPI框右下角查看目标完成度。

| 未设置目标值 | 已设置目标值 |
| :--- | :--- |
| ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/wu-kpi-mu-biao.png) | ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/you-kpi-mu-biao%20%281%29.png) |

| 参数 | 说明 |
| :--- | :--- |


| 标题 | 我们默认用了事件名称来指代标题，您可以通过KPI单图右上角的操作按钮进行编辑。建议标题设置一定要简单明了，所有人看到标题后就能明白它的业务含义。 |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x65F6;&#x95F4;&#x8303;&#x56F4;</th>
      <th style="text-align:left">
        <p>&#x8003;&#x5BDF;KPI&#x7684;&#x8303;&#x56F4;&#xFF0C;&#x4E00;&#x822C;&#x60C5;&#x51B5;&#x4E0B;&#x516C;&#x53F8;&#x7528;&#x4ECA;&#x5929;&#x3001;&#x672C;&#x5468;&#x3001;&#x672C;&#x6708;&#x6765;&#x770B;KPI&#x7684;&#x8868;&#x73B0;&#x3002;</p>
        <p>&#x5728;&#x7F16;&#x8F91;&#x65F6;&#x60A8;&#x53EF;&#x4EE5;&#x66F4;&#x7075;&#x6D3B;&#x7684;&#x9009;&#x62E9;&#x65F6;&#x95F4;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x540C;&#x6BD4;</th>
      <th style="text-align:left">
        <p>&#x540C;&#x6BD4;&#x662F;&#x4E00;&#x4E2A;&#x4E1A;&#x52A1;&#x6982;&#x5FF5;&#xFF0C;&#x662F;&#x57FA;&#x4E8E;&#x4E1A;&#x52A1;&#x5468;&#x671F;&#x7684;&#x5B9A;&#x4E49;&#x3002;</p>
        <p>&#x5BF9;&#x6BD4;&#x89C4;&#x5219;&#xFF1A;&#x672C;&#x5468;&#x6BD4;&#x4E0A;&#x5468;&#x3001;&#x672C;&#x6708;&#x6BD4;&#x4E0A;&#x6708;&#x3001;&#x4ECA;&#x5E74;&#x6BD4;&#x53BB;&#x5E74;&#x3002;</p>
        <p>&#x5982;&#x679C;&#x4ECA;&#x5929;&#x662F;&#x5468;&#x4E09;&#xFF0C;&#x90A3;&#x4E48;&#x672C;&#x5468;&#x6BD4;&#x4E0A;&#x5468;&#x5C31;&#x662F;&#x672C;&#x5468;&#x4E00;&#x4E8C;&#x4E09;&#x7684;&#x6570;&#x636E;&#x6BD4;&#x4E0A;&#x5468;&#x4E00;&#x4E8C;&#x4E09;&#x7684;&#x6570;&#x636E;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x73AF;&#x6BD4;</th>
      <th style="text-align:left">
        <p>&#x5B9A;&#x4E49;&#x4E3A;&#x8FD9;&#x4E2A;N&#x5929;&#x6BD4;&#x4E0A;&#x4E2A;N&#x5929;&#x3002;</p>
        <p>&#x6BD4;&#x5982;&#xFF1A;&#x4ECA;&#x5929;&#x6BD4;&#x6628;&#x5929;&#xFF0C;&#x8FC7;&#x53BB;7&#x5929;&#x7684;&#x6570;&#x636E;&#x6BD4;&#x8FC7;&#x53BB;8~14&#x5929;&#x6570;&#x636E;&#xFF0C;&#x73AF;&#x6BD4;&#x66F4;&#x5173;&#x6CE8;&#x4E1A;&#x52A1;&#x7684;&#x8FDE;&#x7EED;&#x6027;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x76EE;&#x6807;</th>
      <th style="text-align:left">
        <p>&#x7ED9;&#x4E88;&#x6240;&#x9009;&#x65F6;&#x95F4;&#x8303;&#x56F4;&#x548C;&#x7C92;&#x5EA6;&#x7684;&#x76EE;&#x6807;&#x3002;&#x6BD4;&#x5982;&#x672C;&#x5468;&#x76EE;&#x6807;&#xFF0C;&#x672C;&#x6708;&#x76EE;&#x6807;&#x7B49;&#x3002;&#x5BF9;&#x4E8E;&#x6240;&#x9009;&#x65F6;&#x95F4;&#x8303;&#x56F4;&#x548C;&#x7C92;&#x5EA6;&#x7684;KPI&#x60A8;&#x53EF;&#x4EE5;&#x8BBE;&#x5B9A;&#x5BF9;&#x5E94;&#x7684;&#x76EE;&#x6807;&#x3002;</p>
        <p>&#x6CE8;&#xFF1A;&#x5F53;&#x6240;&#x9009;&#x65F6;&#x95F4;&#x8303;&#x56F4;&#x53D1;&#x751F;&#x53D8;&#x5316;&#x65F6;&#xFF0C;&#x76EE;&#x6807;&#x9700;&#x8981;&#x91CD;&#x65B0;&#x586B;&#x5199;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

| 目标完成率 | 实际KPI表现/目标值，您可以借助目标完成率来追踪进程是否符合预期。 |
| :--- | :--- |


当你发现KPI不符合预期，点击KPI单图进入KPI详情页，详情页将帮助你快速找到数据波动的原因。

KPI详情页构成：

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2835%29.png)

| 项 | 说明 |
| :--- | :--- |
| 1-时间范围与粒度 | 灵活选择事件与粒度。 |
| 2-用户范围 | 更改目标人群。 |
| 3-趋势图 | 趋势线图，帮助您监测 KPI 趋势与波动状况。 |
| 4-趋势图洞察 | 基于您关注的业务维度，直接呈现 KPI 变化的主要影响因子。快速理解导致数据波动的核心原因。 |
| 5-维度拆解 | 您可以按照业务维度对您的KPI进行拆解，找到 KPI 变化的影响因子。同时提供不同业务维度下的数据变化量与变化率。 |
| 6-选择下钻维度 | 单击维度列单元格可以对维度进行下钻。可以根据您的业务思路，不断拆解下钻找到最小粒度的原因。 |

下钻示例：

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28179%29.png)

## 管理KPI看板

KPI看板与分析看板的管理方式相同，请参考[看板管理](../../../product-manual-old/charts/manage.md#2-gong-neng-shuo-ming)。

