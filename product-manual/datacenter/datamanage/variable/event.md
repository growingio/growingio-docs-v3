---
description: 在GrowingIO平台对埋点事件变量进行声明和管理。
---

# 事件变量

完成事件+变量的事件模型设计、在开始代码的部署前，需要先在变量管理处将事件的变量配置到GrowingIO平台。

## 创建事件变量

一. 在顶部导航栏选择“**数据中心 &gt; 数据管理”**，进入数据管理模块。

二. 在左侧导航栏选择“**变量 &gt; 事件变量”**，进入事件变量管理页面。

{% hint style="success" %}
事件变量分为事件级变量和页面级变量，需在各自页签进行配置。
{% endhint %}

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28156%29.png)

三. 单击变量列表上方的**创建事件/页面级变量**，弹出新建事件/页面级变量页面。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28124%29.png)

| 参数 | 说明 | 事件级变量 | 页面级变量 |
| :--- | :--- | :--- | :--- |


| 名称 | GrowingIO平台上变量的名称。 | ✔️ | ✔️ |
| :--- | :--- | :--- | :--- |


| 标识符 | 此变量在代码中的标识，仅允许大小写英文、数字、下划线，并且不能以数字开头。 | ✔️ | ✔️ |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x7C7B;&#x578B;</th>
      <th style="text-align:left">
        <ul>
          <li>&#x5B57;&#x7B26;&#x4E32;</li>
          <li>&#x6574;&#x6570;</li>
          <li>&#x5C0F;&#x6570;</li>
        </ul>
        <p>&#x6CE8;&#x610F;</p>
        <p>&#x5F53;&#x60A8;&#x9700;&#x8981;&#x5BF9;&#x4E8B;&#x4EF6;&#x7EA7;&#x53D8;&#x91CF;&#x8FDB;&#x884C;&#x8FD0;&#x7B97;&#x65F6;&#xFF0C;&#x624D;&#x9700;&#x9009;&#x62E9;&#x6570;&#x503C;&#x7C7B;&#x578B;&#xFF1B;&#x5176;&#x4ED6;&#x60C5;&#x51B5;&#x5EFA;&#x8BAE;&#x60A8;&#x4F18;&#x5148;&#x9009;&#x62E9;&#x5B57;&#x7B26;&#x4E32;&#x7C7B;&#x578B;&#x3002;&#x4EE5;<b>&#x8BA2;&#x5355;&#x91D1;&#x989D;</b>&#x4F5C;&#x4E3A;&#x6570;&#x503C;&#x7C7B;&#x578B;&#x7684;<b>&#x4E8B;&#x4EF6;&#x7EA7;&#x53D8;&#x91CF;</b>&#x4E3A;&#x4F8B;&#xFF0C;&#x6B64;&#x53D8;&#x91CF;&#x4FBF;&#x4F1A;&#x8F6C;&#x6362;&#x6210;&#x4E24;&#x4E2A;&#x6307;&#x6807;&#xFF1A;&#x8BA2;&#x5355;&#x91D1;&#x989D;&#x6C42;&#x548C;&#x3001;&#x8BA2;&#x5355;&#x91D1;&#x989D;&#x6C42;&#x5E73;&#x5747;&#xFF0C;&#x800C;&#x65E0;&#x6CD5;&#x5728;&#x56FE;&#x8868;&#x4E2D;&#x4F5C;&#x4E3A;&#x7EF4;&#x5EA6;&#x5C55;&#x793A;&#x3002;</p>
        <p>&#x521B;&#x5EFA;&#x6210;&#x529F;&#x53D8;&#x91CF;&#x7C7B;&#x578B;&#x4E0D;&#x53EF;&#x4FEE;&#x6539;&#xFF0C;&#x5982;&#x8981;&#x4FEE;&#x6539;&#x53EF;&#x5220;&#x9664;&#x540E;&#x91CD;&#x65B0;&#x521B;&#x5EFA;&#x3002;</p>
      </th>
      <th style="text-align:left">&#x2714;&#xFE0F;</th>
      <th style="text-align:left">-</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| 描述 | 变量的描述，可填写对应触发时机和应用场景，同时对变量值进行举例。 | ✔️ | ✔️ |
| :--- | :--- | :--- | :--- |


{% hint style="info" %}
在GrowingIO平台对变量标识进行创建后，即可在代码中进行部署，具体的说就是调用GrowingIO提供的API接口，上传数据。
{% endhint %}

## 管理事件变量

在事件变量列表可以查看事件变量的名称、描述、标识符、类型、创建人、创建时间、最后更新人、最后更新时间。

您也可以对事件变量进行已下操作：

**变量搜索**：您可以在列表上方的搜索框中按变量名称或标识符来搜索事件变量。

**QuickView：**点击任一事件变量，您可以在右侧弹出的变量详情中，查看变量的定义。

**编辑：**在QuickView界面单击变量的参数进行修改，修改后单击**保存**。

**列定制**：单击列表表头右侧的 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/lie-ding-zhi.png) 可选择列表展示项。

**删除**：单击单条事件变量右侧的 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/dian-dian-dian.png) 选择删除，可删除不需要的事件变量。

**批量操作**：在列表中使用复选框选择多个事件变量，可以进行批量删除。

