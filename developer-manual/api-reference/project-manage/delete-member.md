# 从项目内移除成员

> 通过邮箱删除用户，用于清理项目内失效成员。

## URL

[https://www.growingio.com/api/v1/projects/{project\_uid}/accounts/delete](https://www.growingio.com/api/v1/projects/{project_uid}/accounts/delete)

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
| email | string | 是 | 待删除的成员邮箱。 |
{% endtab %}

{% tab title="响应示例" %}
* 200: OK

```text
{
    "status": "success"
    }
```

* 400: Bad Request 请求失败，message 中会有错误消息

```text
{
    "status": "fail",    "message": "error message"}
```

* 403: Forbidden 认证失败
{% endtab %}
{% endtabs %}

