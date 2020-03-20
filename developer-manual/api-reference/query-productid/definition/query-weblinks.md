# 查询监测链接（推广网页）

### URL

https://www.growingio.com/api/v1/projects/{project\_uid}/meta/weblinks

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
| id | string | 资源ID |
| linkId | string | 监测链接ID |
| name | string | 监测链接名称 |
| projectId | string | 项目UID |
| trackingUrl | string | 监测链接 |
| redirectUrl | string | 跳转链接 |
| impressionUrl | string | 曝光检测链接 |
| campaignId | string | 推广活动ID |
| campaignName | string | 推广活动名称 |
| channelId | string | 渠道id |
| channelName | string | 渠道名称 |
| utmMedium | string | 广告媒介 |
| utmContent | string | 广告内容 |
| utmTerm | string | 广告关键字 |
| comments | string | 备注 |
| status | string | 状态 |
| creatorId | string | 创建人id |
| creatorName | string | 创建人名称 |
| updaterId | string | 最后更新人id |
| updaterName | string | 最后更新人名称 |
| createdAt | long | 创建时间 |
| updatedAt | long | 更新时间 |
{% endtab %}

{% tab title="返回示例" %}
Response: Status Code: 200 OK

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



