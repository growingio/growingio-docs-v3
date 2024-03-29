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

{% tab title="返回参数" %}
| 字段 | 类型 | 说明 |
| :--- | :--- | :--- |
| projectId | string | 项目 uid |
| id | string | 变量 uid |
| key | string | 变量标识符 |
| name | string | 变量名称 |
| description | string | 变量描述 |
| isSystem | boolean | 是否系统创建 |
| attribution | string | 归因，mostRecent: 最近归因，final: 最终归因 |
| valueType | string | string：字符串，date：日期 |
| createdAt | number | 变量创建时间， unix 毫秒时间戳 |
| creator | string | 创建人 |
| updatedAt | number | 变量最后一次修改时间， unix 毫秒时间戳 |
| updater | string | 更新人 |
{% endtab %}

{% tab title="返回示例" %}
```text
[{
	"id": "j9yDX123",
	"key": "ml02",
	"name": "ml测试02",
	"description": "",
	"isSystem": false,
	"projectId": "nxog1234",
	"createdAt": 1615360319000,
	"updatedAt": 1619159037000,
	"creator": "zhanghao",
	"updater": "杨强",
	"attribution": "mostRecent",
	"valueType": "string"
}]
```
{% endtab %}
{% endtabs %}

