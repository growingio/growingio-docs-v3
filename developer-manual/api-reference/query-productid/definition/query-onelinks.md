# 查询监测链接（增加APP下载量-同时推广iOS和Android）

### URL

https://www.growingio.com/api/v1/projects/{project\_uid}/meta/onelinks

### 请求类型

GET

### 请求头参数

公共头部请参考[公共请求头参数](../../authenticate.md)。

### 说明参数与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_id | string | 是 | 项目ID。 |
{% endtab %}

{% tab title="返回参数" %}
| 字段名 | 字段格式 | 说明 |
| :--- | :--- | :--- |
| id | String | 资源ID |
| linkId | String | 监测链接ID |
| name | String | 监测链接名称 |
| projectId | String | 项目UID |
| productIdIos | String | iOS产品ID |
| productNameIos | String | iOS产品名称 |
| productIdAndroid | String | Android产品ID |
| productNameAndroid | String | ndroid产品名称 |
| trackingUrl | String | 监测链接 |
| redirectUrl | String | 跳转链接 |
| campaignIdIos | String | iOS广告活动ID |
| campaignNameIos | String | iOS广告活动名称 |
| campaignIdAndroid | String | android活动id |
| campaignNameAndroid | String | android活动名称 |
| channelId | String | 渠道id |
| channelName | String | 渠道名称 |
| status | String | 状态 |
| creatorId | String | 创建人id |
| creatorName | String | 创建人名称 |
| updaterId | String | 最后更新人id |
| updaterName | String | 最后更新人名称 |
| createdAt | Long | 创建时间 |
| updatedAt | Long | 更新时间 |
{% endtab %}

{% tab title="返回示例" %}
```text
[
    {
        "id": "nxog09md",
        "linkId": "dGVr8e9",
        "name": "qwe",
        "projectId": "4PYJMWoM",
        "productIdIos": "xRxVp0o5",
        "productNameIos": "TestAPP",
        "productIdAndroid": "j9yEwm9y",
        "productNameAndroid": "123测试编辑编辑",
        "trackingUrl": "https://datayi.cn/dGVr8e9",
        "redirectUrl": "http://123.com",
        "campaignIdIos": "O4PKxoEb",
        "campaignNameIos": "321上线",
        "campaignIdAndroid": "xoga4DRm",
        "campaignNameAndroid": "321上线验证1",
        "channelId": "34RzeX9V",
        "channelName": "123测试编辑编辑",
        "status": "activated",
        "creatorId": "nRbm8d93",
        "creatorName": "xx,
        "updaterId": "nRbm8d93",
        "updaterName": "xx",
        "createdAt": 1521642287367,
        "updatedAt": 1521642287367
    }
]
```
{% endtab %}
{% endtabs %}



