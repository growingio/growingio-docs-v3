# 创建登录用户变量

> 创建登录用户变量，目前仅支持创建，不支持修改，如需修改请到 GrowingIO 平台管理界面修改。

## URL

`https://www.growingio.com/v1/api/projects/{project_uid}/vars/peoples`

## 请求类型

POST

## 请求头参数

公共头部请参考[公共请求头参数](../authenticate.md)。

## 参数说明与示例

{% tabs %}
{% tab title="参数说明" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |

| body参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |


| name | string | 是 | 变量名称，最大长度为30 |
| :--- | :--- | :--- | :--- |


| key | string | 是 | 变量标识符，只允许以字母或下划线开头，包含下划线、字母、数字的字符串，最大长度为50. |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">attribution</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x662F;</th>
      <th style="text-align:left">
        <p>&#x5F52;&#x56E0;&#x65B9;&#x5F0F;</p>
        <ul>
          <li>mostRecent&#xFF1A;&#x6700;&#x8FD1;&#x5F52;&#x56E0;</li>
          <li>final&#xFF1A;&#x6700;&#x7EC8;&#x5F52;&#x56E0;</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

| description | string | 否 | 变量描述，最大长度为150 |
| :--- | :--- | :--- | :--- |
{% endtab %}

{% tab title="返回示例" %}
200: OK
{% endtab %}
{% endtabs %}

