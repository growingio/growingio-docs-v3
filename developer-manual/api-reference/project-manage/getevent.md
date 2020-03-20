# 获取埋点事件列表

> 获取当前项目打点事件，没有结果时返回空数组。

### URl

https://www.growingio.com/v1/api/projects/{project\_uid}/dim/events

### 请求类型

GET

### 请求头参数

公共头部请参考[公共请求头参数](../authenticate.md)。

### 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 名称 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |
{% endtab %}

{% tab title="返回示例" %}
返回成功时：

```text
[
    {
        "id": "id1", // 事件 uid
        "key": "test1", // 事件标识符
        "name": "测试1", // 事件名称
        "description": "测试", // 事件描述
        "type": "counter", // 事件类型, counter: 计数器, number: 数值
        "attrs": [ // 事件级变量
            {
                "id": "id2", // 变量 uid
                "key": "labore111", // 变量标识符
                "name": "变量1", // 变量名称
                "type": "String", // 变量类型, 目前有 String, Int, Double 类型
                "projectId": "id3", // 项目 uid
                "createdAt": 1534820494000, // 变量创建时间，unix 毫秒时间戳
                "updatedAt": 1534820494000 // 变量最后一次更新时间, unix 毫秒时间戳
            }
        ],
        "projectId": "id3", // 项目 uid
        "createdAt": 1534426936000, // 事件创建时间, unix 毫秒时间戳
        "updatedAt": 1535425076000, // 事件最后一次更新时间, unix 毫秒时间戳
        "creator": "User1", // 创建人
        "updater": "User1", // 最后一次更新人
        "eventType": "dash" // 事件类型, 目前仅有 dash，表示为打点事件
    }
]
```
{% endtab %}
{% endtabs %}



