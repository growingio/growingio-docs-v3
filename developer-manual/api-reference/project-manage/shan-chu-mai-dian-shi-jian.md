# 删除埋点事件

{% hint style="warning" %}
灰度功能 ，如需体验试用，请联系客户经理 。
{% endhint %}

**注意事项：调用删除埋点接口，与页面删除功能效果一致。埋点删除后，会从报表界面消失，由该事件保存的历史数据也会消失。删除后无法恢复，请谨慎使用！**

## URL

`https://www.growingio.com/v1/api/projects/{project_uid}/dim/events/{event_id}`

## 请求类型

DELETE

## 请求头参数

公共头部请参考[公共请求头参数](../authenticate.md)。

## 请求参数与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数         | 类型     | 是否必传 | 说明      |
| ------------ | ------ | ---- | ------- |
| project\_uid | string | 是    | 项目UID。  |
| event\_id    | string | 是    | 埋点事件ID。 |
{% endtab %}

{% tab title="响应示例" %}
200：OK
{% endtab %}
{% endtabs %}

