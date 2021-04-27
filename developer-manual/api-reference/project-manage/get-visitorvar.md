# 获取访问用户变量

## URL

[https://www.growingio.com/v1/api/projects/:project\_id/vars/visitors](https://www.growingio.com/v1/api/projects/:project_id/vars/visitors)

## 请求类型

GET

## 请求头参数

公共头部请参考[公共请求头参数](https://docs.growingio.com/v3/developer-manual/api-reference/authenticate)。

## 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |
{% endtab %}

{% tab title="返回参数" %}
| 字段 | 类型 | 说明 |
| :--- | :--- | :--- |
| projectId | string | 项目 uid |
| id | string | 变量 uid |
| key | string | 变量标识符 |
| name | string | 变量名称 |
| description | string | 变量描述 |
| isSystem | boolean | 是否系统创建 |
| createdAt | number | 变量创建时间， unix 毫秒时间戳 |
| creator | string | 创建人 |
| updatedAt | number | 变量最后一次修改时间， unix 毫秒时间戳 |
| updater | string | 更新人 |
{% endtab %}

{% tab title="返回示例" %}
```text
[
    {
        "id": "xRxV1234",
        "key": "gio_push_device_brand",
        "name": "触达设备品牌",
        "description": "触达设备品牌",
        "isSystem": true,
        "projectId": "nxog1234",
        "createdAt": 1582023964000,
        "updatedAt": 1582023964000,
        "creator": "系统",
        "updater": "系统"
    }
]
```
{% endtab %}
{% endtabs %}





