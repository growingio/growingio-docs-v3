# 新建推广渠道

## URL

[https://www.growingio.com/api/v1/projects/{project\_uid}/meta/channels](https://www.growingio.com/api/v1/projects/{project_uid}/meta/channels)

## 请求类型

POST

## 请求头参数

公共头部请参考[公共请求头参数](../../authenticate.md)。

## 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |

| body参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| name | string |  | 渠道名称。 |
{% endtab %}

{% tab title="返回参数" %}
| 名称 | 类型 | 说明 |
| :--- | :--- | :--- |
| id | string | 渠道ID。 |
| name | string | 渠道名称。 |
{% endtab %}

{% tab title="body示例" %}
```text
{
  "name":"二维码推广"
}
```
{% endtab %}
{% endtabs %}

