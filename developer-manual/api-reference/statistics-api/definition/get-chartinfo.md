# 获取看板中的图表信息

## URL

[https://www.growingio.com/projects/{project\_uid}/dashboards/{dashboard\_id}.json](https://www.growingio.com/projects/{project_uid}/dashboards/{dashboard_id}.json)

## 请求类型

GET

## 请求头参数

公共头部请参考[公共请求头参数](../../authenticate.md)。

## 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| dashboard\_id | string | 是 | 看板ID，详细请参考 [统计数据V3接口导出分类](../../statistics-api-v3/overview.md#tong-ji-shu-ju-dao-chu-fen-lei-2) |
| project\_uid | string | 是 | 项目UID，详细请参考 [获取项目UID](../../../../product-manual/projectmange/projectmange/get-uid.md) |
{% endtab %}

{% tab title="响应示例" %}
```text
{
  "id": "Dashboard Uid",
  "name": "Dashboard Name",
  "charts": [
    {
      "id": "Chart Uid",
      "name": "Chart Name",
      "createor": "Chart Creator",
      "createdAt": "Created Time"
    },
    {
      "id": "Chart Uid",
      "name": "Chart Name",
      "createor": "Chart Creator",
      "createdAt": "Created Time"
    }
  ]
}
```
{% endtab %}
{% endtabs %}

