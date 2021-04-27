# 查询监测链接（微信小程序）

## URL

[https://www.growingio.com/api/v1/projects/{project\_uid}/meta/minplinks](https://www.growingio.com/api/v1/projects/{project_uid}/meta/minplinks)

## 请求类型

GET

## 请求头参数

公共头部请参考[公共请求头参数](https://docs.growingio.com/v3/developer-manual/api-reference/authenticate)。

## 说明参数与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目ID。 |
{% endtab %}

{% tab title="返回参数" %}
| 名称 | 类型 | 备注 |
| :--- | :--- | :--- |
| id | string | 监测链接ID |
| linkId | string | 监测链接ID |
| name | string | 监测链接名字 |
| projectId | string | 项目ID |
| spn | string | 推广小程序 |
| trackingUrl | string | GrowingIO 分配的追踪链接 |
| redirectUrl | string | 小程序落地页路径 |
| campaignId | string | 广告活动ID |
| campaignName | string | 广告活动名称 |
| channelId | string | 推广渠道ID |
| channelName | string | 推广渠道名称 |
| utmMedium | string | utm medium 参数 |
| utmContent | string | utm content 参数 |
| utmTerm | string | utm term 参数 |
| comments | string | 备注 |
| status | string | 状态 |
| creatorId | string | 创建人ID |
| creatorName | string | 创建人名称 |
| updaterId | string | 更新人ID |
| updaterName | string | 更新人名称 |
| createdAt | number | 创建时间 |
| updatedAt | number | 更新时间 |
{% endtab %}

{% tab title="响应示例" %}
Response: Status Code: 200 OK

```text
[{
    "id": "4PK5D123",
    "linkId": "4PK5D123",
    "name": "c小程序二维码",
    "projectId": "nxog09md",
    "trackingUrl": "pages/overview/index?gio_link_id=4PK5D123",
    "redirectUrl": "pages/overview/index",
    "campaignId": "a9aMMZ9B",
    "campaignName": "测试广告",
    "channelId": "DnRb123",
    "channelName": "测试",
    "utmMedium": "",
    "utmContent": null,
    "utmTerm": null,
    "comments": null,
    "status": "activated",
    "creatorId": "korga123",
    "creatorName": "盼盼",
    "updaterId": "korga123",
    "updaterName": "盼盼",
    "createdAt": 1603683498890,
    "updatedAt": 1603683499386,
    "qrCode": "https://gta.growingio.com/buckets/uploads/files/3/wxcode/C/1601234567890/wxcode.jpg?sign=123&expires=123",
    "spn": "wx9d29e41234567890"
}]
```
{% endtab %}
{% endtabs %}



