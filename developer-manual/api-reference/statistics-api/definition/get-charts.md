# 获取看板列表

## URL

[https://www.growingio.com/projects/{project\_uid}/dashboards.json](https://www.growingio.com/projects/{project_uid}/dashboards.json)

## ​请求类型

GET

## 请求头部

公共头部请参考[公共请求头参数](../../authenticate.md)。

## 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |
{% endtab %}

{% tab title="响应示例" %}
```text
[
  {
    "id": "Dashboard Uid",
    "name": "我的看板",
    "type": "看板类型", // normal: 普通看板, realtimeV2: 实时看板
    "createdAt": "2019-01-01",
    "updatedAt": "2019-01-02",
    "scope": "看板所属", // global: 全局, project: 项目, user: 个人
    "updater": "Dashboard Last Updator",
    "creator": "Dashboard Creator"
  },
  ...
]
```
{% endtab %}
{% endtabs %}

