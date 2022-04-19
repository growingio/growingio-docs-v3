# 获取事件级变量

> 获取项目下打点维度列表。

## URL

`https://www.growingio.com/v1/api/projects/{project_uid}/vars/events`

## 请求类型

GET

## 请求头参数

公共头部请参考[公共请求头参数](../authenticate.md)。

## 请求参数与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数类型      | 类型     | 是否必传 | 书名     |
| ----------- | ------ | ---- | ------ |
| poject\_uid | string | 是    | 项目UID。 |
{% endtab %}

{% tab title="返回示例" %}
```
[
    {
        "id": "id1", // 打点维度 uid
        "key": "test1", // 打点维度标识符
        "name": "测试", // 打点维度名称
        "type": "String", // 打点维度类型，目前有 String, Int, Double 三种类型
        "projectId": "pid1", // 项目 uid
        "createdAt": 1534820494000, // 打点维度创建时间， unix 毫秒时间戳
        "updatedAt": 1534820494000 // 打点维度最后更新时间， unix 毫秒时间戳
    }
]
```
{% endtab %}
{% endtabs %}
