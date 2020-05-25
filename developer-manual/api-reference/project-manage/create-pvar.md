# 创建页面级变量

> 创建页面级变量，目前仅支持创建，不支持修改，如需修改，请到 GrowingIO 平台管理界面修改。

## URL

[https://www.growingio.com/v1/api/projects/{project\_uid}/vars/pages](https://www.growingio.com/v1/api/projects/{project_uid}/vars/pages)

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
| name | string | 是 | 变量名称，最大长度30. |
| key | string | 是 | 变量标识符，字母或下划线开头，包含下划线，字母，数字的字符串」，最大长度为 50 |
| description | string | 否 | 变量描述：最大长度50 |
{% endtab %}

{% tab title="响应示例" %}
200: OK
{% endtab %}
{% endtabs %}

