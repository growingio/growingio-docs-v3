---
description: 对产品内所有的计算指标进行统一的维护与管理。
---

# 计算指标

## **简介** <a id="1-jian-jie"></a>

如果您在进行数据分析时，需要使用到相除计算或是加权计算的统计指标，可以使用 GrowiongIO 的「计算指标」功能来创建自定义规则的计算指标。计算指标可以把各种事件与指标自由计算与加权组合，来更综合地衡量业务运营情况。常见的使用场景如下：

* **注册按钮点击率（CTR） ：**若您想要得到用户在注册页面的注册按钮点击率，我们可以定义分子为注册按钮点击次数（人数），分母为注册页面浏览次数（人数）。
* **注册转化率：**若您想了解你的注册转化率，我们可以定义分子为注册成功事件的次数（人数），分母为注册页面的页面浏览次数（人数）。
* **统计产品功能的渗透率：**如果您想了解使用您某一产品功能的用户渗透率，我们可以定义分子为产品功能 A 的页面浏览人数，分母为总用户数，来得到使用产品功能 A 的用户占所有用户的占比；
* **统计用户使用产品的活跃度：**如果您想了解您的用户使用您产品的整体活跃度情况，可以把产品活跃度定义为您产品一系列核心页面或是交互功能的总和，接着使用计算指标将这一系列事件进行次数相加即可。
* **设置权重：**对于一个产品的不同的业务模块而言，我们更希望用户在核心产品模块上活跃。当我们衡量产品活跃度的时候，可以针对核心产品模块的指标分配更高的权重，对于非活核心产品模块分配较低的权重。

在新的数据管理上线后，我们全面将原先的「复合指标」功能全面升级为「计算指标」功能，新的计算指标功能支持任意事件与指标组合的计算，您原先创建的复合指标也会全数迁移到新的计算指标功能当中。

## **创建计算指标** <a id="2-ji-suan-zhi-biao-gong-neng-shi-yong"></a>

一. 在顶部导航栏选择“**数据中心 &gt; 数据管理”**，进入数据管理模块。

二. 在左侧导航栏选择“**自定义 &gt; 计算指标”**，进入计算指标管理页面。

![](../../../../.gitbook/assets/image%20%2838%29.png)

三. 单击计算指标列表界面左上角的创建计算指标，弹出创建计算指标界面。

![](../../../../.gitbook/assets/image%20%2819%29.png)

![](../../../../.gitbook/assets/ji-suan-zhi-biao-.png)

| 参数 | 说明 |
| :--- | :--- |


| 分子计算区 | 创建计算指标弹框左侧上方部分为分子计算区域，点击【添加事件或指标】，选择您想要进行计算的事件或指标进入此处进行加法运算。 |
| :--- | :--- |


| 分母计算区 | 创建计算指标弹框左侧下方部分为分母计算区域，若您想要创建点击率、转化率、渗透率等涉及除法计算的指标，您可以通过在此处选择您想要进行计算的事件或指标作为分母进行指标计算。 |
| :--- | :--- |


| 选择度量单位 | 在选定事件后，您可以选择统计事件的度量单位为「人」，或是「次」，举例说，如果您想要创建注册按钮人均点击率指标，您可以定义分子为注册按钮点击次数，分母为注册按钮点击人数。 |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x8BBE;&#x7F6E;&#x6743;&#x91CD;</th>
      <th style="text-align:left">
        <p>&#x5982;&#x679C;&#x60A8;&#x60F3;&#x8981;&#x521B;&#x5EFA;&#x5E26;&#x6709;&#x6743;&#x91CD;&#x6BD4;&#x7387;&#x8BBE;&#x7F6E;&#x7684;&#x8BA1;&#x7B97;&#x6307;&#x6807;&#xFF0C;&#x60A8;&#x53EF;&#x4EE5;&#x901A;&#x8FC7;&#x8BBE;&#x7F6E;&#x6743;&#x91CD;&#x6765;&#x4E3A;&#x6240;&#x9009;&#x4E8B;&#x4EF6;&#x81EA;&#x7531;&#x5206;&#x914D;&#x6743;&#x91CD;&#x3002;&#x6BD4;&#x5982;&#x5F53;&#x6211;&#x4EEC;&#x8861;&#x91CF;&#x4EA7;&#x54C1;&#x6D3B;&#x8DC3;&#x5EA6;&#x7684;&#x65F6;&#x5019;&#xFF0C;&#x53EF;&#x4EE5;&#x9488;&#x5BF9;&#x6838;&#x5FC3;&#x4EA7;&#x54C1;&#x6A21;&#x5757;&#x7684;&#x6307;&#x6807;&#x5206;&#x914D;&#x66F4;&#x9AD8;&#x7684;&#x6743;&#x91CD;&#xFF0C;&#x5BF9;&#x4E8E;&#x975E;&#x6838;&#x5FC3;&#x4EA7;&#x54C1;&#x6A21;&#x5757;&#x5206;&#x914D;&#x8F83;&#x4F4E;&#x7684;&#x6743;&#x91CD;&#x3002;</p>
        <p>&#x2B50; &#x5982;&#x679C;&#x60F3;&#x8981;&#x5B9E;&#x73B0;&#x4E24;&#x4E2A;&#x6307;&#x6807;&#x7684;&#x76F8;&#x51CF;&#xFF0C;&#x53EF;&#x4EE5;&#x76F4;&#x63A5;&#x5C06;&#x2795;&#x6539;&#x4E3A;&#x2796;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

{% hint style="warning" %}
计算指标说明

所有计算指标不支持在漏斗、留存、实时中使用。
{% endhint %}

四. 配置完成后，单击保存。

## **管理计算指标**

在计算指标列表可以查看计算指标的名称、描述、创建时间、最后更新人、最后更新时间、业务标签、状态。

您也可以对计算指标进行已下操作：

**指标搜索**：您可以在列表上方的搜索框中按指标名称或创建人来搜索计算指标。

**QuickView：**点击任一计算指标，您可以在右侧弹出的详情中，查看计算指标的定义条件与统计趋势。您也可以通过点击QuickView右上角编辑按钮，修改计算指标的定义。

**快速创建事件分析**：在QuickView见面，可单击创建事件分析，快速进入当前事件分析。

**权限设置**：新创建的计算指标资源权限默认【所有人可见，不可编辑】，所有人都能够看到以及使用该计算指标，但只有该计算指标的创建者和项目的超级管理员拥有权限对该指标进行编辑。您可以在QuickView中的【其他信息】中更改计算指标的资源权限。

**添加业务标签**：单击单条计算指标右侧业务标签列的 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/tian-jia-biao-qian.png) 添加业务标签。

**列定制**：单击列表表头右侧的 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/lie-ding-zhi.png) 可选择列表展示项。

**编辑**：单击单条计算指标右侧的 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/dian-dian-dian.png) 选择编辑，可修改计算指标的定义条件、名称、描述等。

**删除**：单击单条计算指标右侧的 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/dian-dian-dian.png) 选择删除，可删除不需要的计算指标。

**收藏**：单击单条计算指标左侧的 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/shi-jian-shou-cang.png) 可收藏此计算指标，在其他情况进行快速选择。

**批量操作**：在列表中使用复选框选择多个计算指标，可以进行批量添加标签、创建时间分析、删除。

## **常见问题** <a id="5-chang-jian-wen-ti"></a>

### **1. 合并事件和计算指标有什么区别呢？**

合并事件，常用来表征同样业务含义的事件相加，比如多个注册入口按钮，不同平台的相同事件等。

计算指标，常常用来支持更加复杂的业务逻辑，比如用户活跃度（带有权重设置）、点击率、转化率、产品渗透率等带有除法运算的指标等。合并事件可以在漏斗、留存分析等各个模块中使用；计算指标不可以被用在漏斗、留存分析、实时等分析和监控模块中。

### **2. 为什么我找不到复合指标了？**

在新的数据管理上线后，我们全面将原先的「复合指标」功能全面升级为「计算指标」功能，新的计算指标功能支持任意事件与指标组合的计算，您原先创建的复合指标也会全数迁移到新的计算指标功能当中，期待您体验全新的计算指标功能。

