---
description: 此接口仅提供应用ID的查询，新建应用请在GIO后台操作。
---

# 查询应用ID

## URL

[https://www.growingio.com/api/v1/projects/{project\_uid}/meta/products](https://www.growingio.com/api/v1/projects/{project_uid}/meta/products)

## 请求类型

GET

## 请求头参数

公共头部请参考[公共请求头参数](../../authenticate.md)。

## 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |
{% endtab %}

{% tab title="返回参数" %}
| 名称 | 类型 | 说明 |
| :--- | :--- | :--- |


| id | string | 产品ID |
| :--- | :--- | :--- |


| name | string | 名字 |
| :--- | :--- | :--- |


| displayName | string | 产品显示名称，展示在deeplink页面 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">activated</th>
      <th style="text-align:left">boolean</th>
      <th style="text-align:left">
        <p>&#x662F;&#x5426;&#x6709;&#x6548;</p>
        <p>true</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| spn | string | App包名。 |
| :--- | :--- | :--- |


| urlScheme | string | 产品的URL Scheme |
| :--- | :--- | :--- |


| platform | string | 平台 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">createdAt</th>
      <th style="text-align:left">long</th>
      <th style="text-align:left">
        <p>&#x521B;&#x5EFA;&#x65F6;&#x95F4;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1522019721098</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
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

