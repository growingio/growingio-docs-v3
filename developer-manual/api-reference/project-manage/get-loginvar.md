# 获取登录用户变量

> 获得当前项目登录用户变量列表。

## URL

`https://www.growingio.com/v1/api/projects/{project_uid}/vars/peoples`

## 请求类型

GET

## 请求头参数

公共头部请参考[公共请求头参数](../authenticate.md)。

## 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |
{% endtab %}

{% tab title="返回示例" %}
```text
[
   {
        "id": "id1", // 变量 uid
        "key": "test1", // 变量标识符
        "name": "测试", // 变量名称
        "description": "测试", // 变量描述
        "projectId": "pid1", // 项目 uid
        "createdAt": 1532416276546, // 变量创建时间， unix 毫秒时间戳
        "updatedAt": 1532416276546, // 变量最后一次修改时间， unix 毫秒时间戳
        "attribution": "mostRecent" // 变量类型，mostRecent: 最近归因，final: 最终归因
    }
]
```
{% endtab %}
{% endtabs %}

