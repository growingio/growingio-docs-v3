# 获取埋点数量限额

> GrowingIO 根据付费版本设定不同的埋点事件和维度的限额，通过此接口获取您项目的限额。

### URL

https://www.growingio.com/v1/api/projects/{project\_uid}/vars/quotas

### 请求类型

GET

### 请求头参数

公共头部请参考[公共请求头参数](../authenticate.md)。

### 参数说明与示例

{% tabs %}
{% tab title="参数说明" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |
{% endtab %}

{% tab title="返回示例" %}
200：OK

```text
{
    "event": 50000, // 打点事件限额
    "var": 100, // 事件级变量限额
    "pvar": 50, // 页面级变量限额
    "ppl": 50000 // 登录用户变量限额
}
```
{% endtab %}
{% endtabs %}

