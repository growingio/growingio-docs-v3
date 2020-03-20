---
description: 此接口仅提供应用ID的查询，新建应用请在GIO后台操作。
---

# 查询应用ID

### URL

https://www.growingio.com/api/v1/projects/{project\_uid}/meta/products

### 请求类型

GET

### 请求头参数

公共头部请参考[公共请求头参数](../../authenticate.md)。

### 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |
{% endtab %}

{% tab title="返回参数" %}
<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x540D;&#x79F0;</th>
      <th style="text-align:left">&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">id</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x4EA7;&#x54C1;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">name</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x540D;&#x5B57;</td>
    </tr>
    <tr>
      <td style="text-align:left">displayName</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x4EA7;&#x54C1;&#x663E;&#x793A;&#x540D;&#x79F0;&#xFF0C;&#x5C55;&#x793A;&#x5728;deeplink&#x9875;&#x9762;</td>
    </tr>
    <tr>
      <td style="text-align:left">activated</td>
      <td style="text-align:left">boolean</td>
      <td style="text-align:left">
        <p>&#x662F;&#x5426;&#x6709;&#x6548;</p>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">spn</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">App&#x5305;&#x540D;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">urlScheme</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x4EA7;&#x54C1;&#x7684;URL Scheme</td>
    </tr>
    <tr>
      <td style="text-align:left">platform</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5E73;&#x53F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">createdAt</td>
      <td style="text-align:left">long</td>
      <td style="text-align:left">
        <p>&#x521B;&#x5EFA;&#x65F6;&#x95F4;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1522019721098</p>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="响应示例" %}
```text
[
    {
        "displayName": "renrendai",
        "name": "renrendai",
        "activated": true,
        "spn": "com.hecom.Guanghua",
        "id": "Lj9yBRyD",
        "createdAt": 1480635903152,
        "urlSchema": "8137d31f4e7b819f",
        "platform": "android"
    },
    {
        "displayName": "gio",
        "name": "Growingio 测试产品",
        "activated": true,
        "spn": "www.gioee.com",
        "id": "GQPDxPNm",
        "createdAt": 1522019721098,
        "urlSchema": "8137d31f4e7b819f",
        "platform": "ios"
    }
]
```
{% endtab %}
{% endtabs %}

