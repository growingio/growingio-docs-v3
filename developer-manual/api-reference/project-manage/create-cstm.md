# 创建事件级变量

> 创建事件级变量，目前仅支持创建，不支持修改，如需修改，请到 GrowingIO 平台管理界面修改。

## URL

[https://www.growingio.com/v1/api/projects/{project\_uid}/vars/events](https://www.growingio.com/v1/api/projects/{project_uid}/vars/events)

## 请求类型

POST

## 请求头参数

公共头部请参考[公共请求头参数](../authenticate.md)。

## 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |

| body参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |


| name | string | 是 | 变量名称，最大长度为30 |
| :--- | :--- | :--- | :--- |


| key | string | 是 | 变量标识符，只允许以字母获下划线开头，包含下划线、字码、数字的字符串，最大长度为30 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">type</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x53D8;&#x91CF;&#x7C7B;&#x578B;&#x3002;</p>
        <ul>
          <li>string</li>
          <li>int</li>
          <li>double</li>
        </ul>
        <p>&#x9ED8;&#x8BA4;&#x4E3A;string&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

| description | string | 否 | 变量描述，最大长度150。 |
| :--- | :--- | :--- | :--- |
{% endtab %}

{% tab title="返回示例" %}
200: OK
{% endtab %}
{% endtabs %}

