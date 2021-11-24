# 删除埋点事件

## URL

`https://www.growingio.com/v1/api/projects/{project_uid}/dim/events/{event_id}`

## 请求类型

DELETE

## 请求头参数

公共头部请参考[公共请求头参数](../authenticate.md)。



## 请求参数与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数         | 类型     | 是否必传 | 说明       |
| ------------ | ------ | ---- | -------- |
| project\_uid | string | 是    | 项目UID。   |
| event\_id    | string | 是    |  埋点事件ID。 |
{% endtab %}

{% tab title="响应示例" %}
200：OK
{% endtab %}
{% endtabs %}

