# 微信小程序码&小程序监测链接创建服务API

{% hint style="success" %}
微信小程序二维码，是调用腾讯微信小程序接口生成的。微信提供A、B两个接口创建小程序码；提供C接口创建二维码。

GrowingIO在授权后，调用的是A和C接口分别创建小程序码和二维码。具体详情请参见微信开发者文档：[https://developers.weixin.qq.com/minigame/dev/guide/open-ability/qr-code.html](https://developers.weixin.qq.com/minigame/dev/guide/open-ability/qr-code.html)
{% endhint %}

{% hint style="info" %}
如使用此接口生成小程序码，只能生成已发布的小程序的码。

调用频率限制：每秒最多10次。
{% endhint %}

## URL

https://www.growingio.com/api/v1/projects/:project\_uid/meta/minplinks

## 请求类型

POST

## 请求头参数

公共头部请参考[公共请求头参数](authenticate.md)。

名称

| 类型 | 是否必传 | 说明 |  |
| :--- | :--- | :--- | :--- |
| Content | string | 是 | application/json |

## 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |

| body参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| productId | string | 是 | 对应微信小程序应用ID，在[查询应用ID](query-productid/definition/cha-xun-ying-yong-id.md)中获取。 |
| buildQrCode | boolean | 是 | 是否创建二维码 |
| redirectUrl | string | 是 | 跳转链接 |
| campaignId | string | 是 | 广告活动ID，在[查询推广活动I](query-productid/definition/querycampaignid.md) 中获取。 |
| channelId | string | 是 | 推广渠道ID，在[查询推广渠道ID](query-productid/definition/querychannelid.md) 中获取。 |
| utmMedium | string | 否 | utm medium 参数 |
| utmContent | string | 否 | utm content 参数 |
| utmTerm | string | 否 | utm term 参数 |
| comments | string | 否 | 备注 |
| codeType | string | 否 | 二维码类型，A码或C码 |
| name | string | 是 | 二维码名称 |
{% endtab %}

{% tab title="返回参数" %}
| 名称 | 类型 | 备注 |
| :--- | :--- | :--- |
| id | string | 小程序码ID |
| linkId | string | 监测链接ID |
| name | string | 监测链接名字 |
| projectId | string | 项目ID |
| spn | string | spn |
| trackingUrl | string | GrowingIO 分配的追踪链接 |
| redirectUrl | string | 目标链接 |
| campaignId | string | 广告活动ID |
| campaignName | string | 广告活动名称 |
| channelId | string | 推广渠道ID |
| channelName | string | 推广渠道名称 |
| utmMedium | string | utm medium 参数 |
| utmContent | null | utm content 参数 |
| utmTerm | null | utm term 参数 |
| comments | null | 备注 |
| status | string | 状态 |
| creatorId | string | 创建人ID |
| creatorName | string | 创建人名称 |
| updaterId | string | 更新人ID |
| updaterName | string | 更新人名称 |
| createdAt | number | 创建时间 |
| updatedAt | number | 更新时间 |
{% endtab %}

{% tab title="body示例" %}
{% code title="调用 A 接口创建 小程序码 的请求参数示例" %}
```text
// 创建小程序广告监测链接，同时创建小程序码 (A码)
// Request Payload
{
    "name": "minp-qrcode-test-001",
    "productId": "3oL4DgoW",
    "redirectUrl": "pages/list/list",
    "channelId": "woVOxv92",
    "campaignId": "39l1r3R2",
    "utmMedium": "广告媒介",
    "utmTerm": "免费试用",
    "utmContent": "广告内容",
    "comments": "这是注释",
    "buildQrCode": true,
    "codeType": "A"
}
```
{% endcode %}

{% code title="调用 C 接口创建 小程序码 的请求参数示例" %}
```text
// 创建小程序广告监测链接，同时创建小程序二维码 （C码）
// Request Payload
{
    "name": "minp-qrcode-test-002",
    "productId": "3oL4DgoW",
    "redirectUrl": "pages/list/list",
    "channelId": "woVOxv92",
    "campaignId": "39l1r3R2",
    "utmMedium": "广告媒介",
    "utmTerm": "免费试用",
    "utmContent": "广告内容",
    "comments": "这是注释",
    "buildQrCode": true,
    "codeType": "C"
}
```
{% endcode %}
{% endtab %}

{% tab title="响应示例" %}
{% code title="调用 A 接口创建 小程序码 的请求，返回参数示例" %}
```text
// Response
{
    "id": "a9a84ZoB",
    "linkId": "a9a84ZoB",
    "name": "minp-qrcode-test-001",
    "projectId": "GR4mj3PM",
    "spn": "wx51cba5e78d4ef4d8",
    "trackingUrl": "pages/list/list?aid=a9a84ZoB",
    "redirectUrl": "pages/list/list",
    "campaignId": "39l1r3R2",
    "campaignName": "上线前测试",
    "channelId": "woVOxv92",
    "channelName": "csdn",
    "utmMedium": "广告媒介",
    "utmContent": "广告内容",
    "utmTerm": "免费试用",
    "comments": "这是注释",
    "qrCode": "https://gta.growingio.com/buckets/uploads/files/81624/wxcode/A/1557038991079/wxcode.jpg?sign=QNV9UcW0i%2BLVbDj%2F59KXV5l0kVQtGN%2BwxRDDOLyQQWc%3D&expires=1557039291693",
    "status": "activated",
    "creatorId": "6LPdeoNl",
    "creatorName": "Dingding",
    "updaterId": "6LPdeoNl",
    "updaterName": "Dingding",
    "createdAt": 1557038990657,
    "updatedAt": 1557038990657
}
```
{% endcode %}

{% code title="调用 C 接口创建 小程序码 的请求，返回参数示例" %}
```text
//Response 
{
    "id": "nPNWAaoW",
    "linkId": "nPNWAaoW",
    "name": "minp-qrcode-test-002",
    "projectId": "GR4mj3PM",
    "spn": "wx51cba5e78d4ef4d8",
    "trackingUrl": "pages/list/list?aid=nPNWAaoW",
    "redirectUrl": "pages/list/list",
    "campaignId": "39l1r3R2",
    "campaignName": "上线前测试",
    "channelId": "woVOxv92",
    "channelName": "csdn",
    "utmMedium": "广告媒介",
    "utmContent": "广告内容",
    "utmTerm": "免费试用",
    "comments": "这是注释",
    "qrCode": "https://gta.growingio.com/buckets/uploads/files/81624/wxcode/C/1557039139065/wxcode.jpg?sign=NIWNlKpis743%2BJ%2FJbB3ObrqTHXi0OCRlWyfGD8ng%2BIQ%3D&expires=1557039439512",
    "status": "activated",
    "creatorId": "6LPdeoNl",
    "creatorName": "Dingding",
    "updaterId": "6LPdeoNl",
    "updaterName": "Dingding",
    "createdAt": 1557039138779,
    "updatedAt": 1557039138779
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

