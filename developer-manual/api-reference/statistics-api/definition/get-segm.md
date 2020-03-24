# 获取分群列表

## URL

[https://www.growingio.com/projects/{project\_uid}/segmentations.json](https://www.growingio.com/projects/{project_uid}/segmentations.json)

## 请求类型

GET

## 请求头参数

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
    "id": "Segmentation Uid",
    "name": "Segmentation Name",
    "userType": 'u',
    "userNum": 1230,
    "updatedAt": "2016-08-03"
  },
  {
    "id": "Segmentation Uid",
    "name": "Segmentation Name",
    "userType": 'cs1',
    "userNum": 1230,
    "updatedAt": "2016-08-03"
  },
  ...
]
```
{% endtab %}
{% endtabs %}

