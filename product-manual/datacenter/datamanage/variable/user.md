---
description: 在GrowingIO平台对用户变量进行声明和管理。
---

# 用户变量

完成事件+变量的用户模型设计，在开始代码的部署前，需要先在变量管理处将事件的变量配置到GrowingIO平台。

## 创建用户变量

一. 在顶部导航栏选择“**数据中心 &gt; 数据管理”**，进入数据管理模块。

二. 在左侧导航栏选择“**变量 &gt; 用户变量”**，进入用户变量管理页面。

{% hint style="success" %}
用户变量分为登录用户变量和访问用户变量，需在各自页签进行配置。
{% endhint %}

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28159%29.png)

{% hint style="info" %}
登录用户ID：当您在代码中上传了登录用户ID时，请在此处打开登录用户ID。
{% endhint %}

三. 单击变量列表上方的**创建登录/访问用户变量**，弹出新建登录/访问用户变量页面。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28204%29.png)

| 参数 | 说明 | 登录用户 | 访问用户 |
| :--- | :--- | :--- | :--- |


| 名称 | GrowingIO平台上变量的名称。 | ✔️ | ✔️ |
| :--- | :--- | :--- | :--- |


| 标识符 | 此变量在代码中的标识，仅允许大小写英文、数字、下划线，并且不能以数字开头。 | ✔️ | ✔️ |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5B57;&#x6BB5;&#x7C7B;&#x578B;</th>
      <th style="text-align:left">
        <ul>
          <li>&#x5B57;&#x7B26;&#x4E32;</li>
          <li>&#x65E5;&#x671F;</li>
        </ul>
        <p>&#x65E5;&#x671F;&#x7C7B;&#x578B;&#x7684;&#x53D8;&#x91CF;&#x5FC5;&#x987B;&#x7528;YYYYMMDD&#x7684;&#x6837;&#x5F0F;&#x4E0A;&#x4F20;&#xFF0C;&#x5426;&#x5219;&#x65E0;&#x6CD5;&#x751F;&#x6548;&#x3002;</p>
      </th>
      <th style="text-align:left"></th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5F52;&#x56E0;</th>
      <th style="text-align:left">
        <p>&#x5F53;&#x767B;&#x5F55;&#x7528;&#x6237;&#x53D8;&#x91CF;&#x53D1;&#x751F;&#x6539;&#x53D8;&#x65F6;&#xFF0C;&#x4E8B;&#x4EF6;&#x53D1;&#x751F;&#x65F6;&#x4F1A;&#x7B97;&#x5728;&#x6B64;&#x53D8;&#x91CF;&#x7684;&#x54EA;&#x4E2A;&#x503C;&#x4E0A;&#x3002;&#x5F53;&#x524D;&#x767B;&#x5F55;&#x7528;&#x6237;&#x53D8;&#x91CF;&#x652F;&#x6301;&#x4E24;&#x79CD;&#x5F52;&#x56E0;&#x6A21;&#x578B;&#xFF1A;</p>
        <p><b>&#x6700;&#x8FD1;</b>&#xFF1A;&#x5F53;&#x4E8B;&#x4EF6;&#x53D1;&#x751F;&#x65F6;&#xFF0C;&#x5F80;&#x524D;&#x770B;&#xFF0C;&#x65F6;&#x95F4;&#x6BB5;&#x6240;&#x6709;&#x6743;&#x91CD;&#x5168;&#x90E8;&#x5206;&#x914D;&#x7ED9;&#x7528;&#x6237;&#x53D8;&#x91CF;&#x4E2D;&#x79BB;&#x4E8B;&#x4EF6;&#x53D1;&#x751F;&#x7684;&#x4E8B;&#x4EF6;&#x6700;&#x8FD1;&#x7684;&#x503C;&#x4E0A;&#x3002;&#x4F8B;&#x5982;&#xFF0C;&#x7528;&#x6237;&#x5728;&#x67D0;&#x5929;&#x94F6;&#x5361;&#x5347;&#x7EA7;&#x6210;&#x4E3A;&#x91D1;&#x5361;&#xFF0C;&#x5728;&#x6700;&#x8FD1;&#x7684;&#x8FD9;&#x79CD;&#x5F52;&#x56E0;&#x6A21;&#x578B;&#x4E0B;&#xFF0C;&#x6240;&#x6709;&#x94F6;&#x5361;&#x65F6;&#x5019;&#x53D1;&#x751F;&#x7684;&#x9875;&#x9762;&#x6D4F;&#x89C8;&#x3001;&#x8BBF;&#x95EE;&#x3001;&#x8D2D;&#x4E70;&#x4E8B;&#x4EF6;&#x7B49;&#x7B49;&#x90FD;&#x4ECD;&#x7136;&#x5F52;&#x5230;&#x94F6;&#x5361;&#x4E0A;&#x3002;</p>
        <p><b>&#x6700;&#x7EC8;</b>&#xFF1A;&#x5F53;&#x4E8B;&#x4EF6;&#x53D1;&#x751F;&#x65F6;&#xFF0C;&#x5F80;&#x540E;&#x770B;&#xFF0C;&#x4E8B;&#x4EF6;&#x7684;&#x5DE6;&#x53F3;&#x6743;&#x91CD;&#x5168;&#x90E8;&#x5206;&#x914D;&#x7ED9;&#x7528;&#x6237;&#x53D8;&#x91CF;&#x4E2D;&#x6700;&#x7EC8;&#x8BBE;&#x7F6E;&#x7684;&#x503C;&#x4E0A;&#x3002;&#x4F8B;&#x5982;&#xFF1A;&#x5728;&#x7528;&#x6237;&#x5728;&#x67D0;&#x5929;&#x4ECE;&#x94F6;&#x5361;&#x5347;&#x7EA7;&#x5230;&#x91D1;&#x5361;&#xFF0C;&#x5728;&#x6700;&#x7EC8;&#x7684;&#x8FD9;&#x79CD;&#x5F52;&#x56E0;&#x6A21;&#x578B;&#x4E0B;&#xFF0C;&#x6240;&#x6709;&#x94F6;&#x5361;&#x65F6;&#x5019;&#x53D1;&#x751F;&#x7684;&#x9875;&#x9762;&#x6D4F;&#x89C8;&#x3001;&#x8BBF;&#x95EE;&#x3001;&#x8D2D;&#x4E70;&#x4E8B;&#x4EF6;&#x7B49;&#x7B49;&#x90FD;&#x4F1A;&#x5F52;&#x5230;&#x91D1;&#x5361;&#x4E0A;&#x3002;</p>
      </th>
      <th style="text-align:left">&#x2714;&#xFE0F;</th>
      <th style="text-align:left">-</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| 描述 | 变量的描述，可填写对应触发时机和应用场景，同时对变量值进行举例。 | ✔️ | ✔️ |
| :--- | :--- | :--- | :--- |


## 管理事件变量

在用户变量列表可以查看用户变量的名称、描述、标识符、归因、创建人、创建时间、最后更新人、最后更新时间。

您也可以对用户变量进行已下操作：

**变量搜索**：您可以在列表上方的搜索框中按变量名称或标识符来搜索事件变量。

**QuickView：**点击任一用户变量，您可以在右侧弹出的变量详情中，查看变量的定义。

**编辑：**在QuickView界面单击变量的参数进行修改，修改后单击**保存**。

**列定制**：单击列表表头右侧的 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/lie-ding-zhi.png) 可选择列表展示项。

**删除**：单击单条用户变量右侧的 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/dian-dian-dian.png) 选择删除，可删除不需要的用户变量。

**批量操作**：在列表中使用复选框选择多个用户变量，可以进行批量删除。

