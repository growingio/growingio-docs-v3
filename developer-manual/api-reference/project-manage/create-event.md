# 创建埋点事件

> 创建打点事件，打点事件支持批量创建，如果一次仅创建一条，body 内也需要使用数组形式。

## URL

`https://www.growingio.com/v1/api/projects/{project_uid}/dim/events`

## 请求类型

POST

## 请求头参数

公共头部请参考[公共请求头参数](../authenticate.md)。

## 请求参数与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数         | 类型     | 是否必传 | 说明     |
| ------------ | ------ | ---- | ------ |
| project\_uid | string | 是    | 项目UID。 |

| body参数 | 类型 | 是否必传 | 说明 |
| ------ | -- | ---- | -- |

| name | string | 是 | 事件名称，最大长度为30字符 |
| ---- | ------ | - | -------------- |

| type | string | 是 | <p>事件类型。</p><ul><li>counter：计数器</li></ul> |
| ---- | ------ | - | ----------------------------------------- |

| key | string | 是 | 事件标识符，只允许以字母或下划线开头，包含下划线、字母和数字的字符串，最大长度是50. |
| --- | ------ | - | ------------------------------------------- |

| description | string | 否 | 事件描述。 |
| ----------- | ------ | - | ----- |

| attrs | array | 否 | 事件关联的维度属性。 |
| ----- | ----- | - | ---------- |

| 名称 | 类型    | 是否必传 | 说明         |
| -- | ----- | ---- | ---------- |
| id | Sring | 是    | 事件级变量的UID。 |
{% endtab %}

{% tab title="请求示例" %}
```
[
    {
        "key": "test",
        "name": "test",
        "description": "这是事件描述。。",
        "type": "counter",
        "attrs": [
            {
                "id": "RbDnyqNG"
            },{
                "id": "RexMqYbL"
            }
        ]
    }
]
```
{% endtab %}

{% tab title="响应示例" %}
200：OK
{% endtab %}
{% endtabs %}

* id（事件级变量ID）可通过[获取事件级变量](get-cstm.md)获取
