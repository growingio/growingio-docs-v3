# 新建监测链接（推广网页）

## URL

[https://www.growingio.com/api/v1/projects/{project\_uid}/meta/weblinks](https://www.growingio.com/api/v1/projects/{project_uid}/meta/weblinks)

## 请求类型

POST

## 请求头参数

公共头部请参考[公共请求头参数](../../authenticate.md)。

## 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |

| body参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| name | string | 是 | 监测链接名称，同一个账号下系统会进行链接的同名校验，请勿重复提交同名链接，长度50个字符内。 |
| utmMedium | string | 是 | 广告媒介。 |
| channelId | string | 是 | 渠道ID。 |
| campaignId | string | 是 | 活动ID。 |
| redirectUrl | string | 是 | 转跳链接。 |
| utmTerm | string | 否 | 广告关键字，选填 |
| utmContent | string | 否 | 广告内容 |
| comments | string | 否 | 备注 |
{% endtab %}

{% tab title="请求示例" %}
```text
{
    "redirectUrl":"http://www.www.www",
    "utmMedium":"对对对",
    "utmTerm":"免费观看",
    "utmContent":"内容",
    "comments":"备注",
    "name":"测试web8",
    "campaignId":"xogjZQ2P",
    "channelId":"vnomv9zJ"
}
```
{% endtab %}

{% tab title="返回参数" %}
| 字段名 | 字段格式 | 说明 |
| :--- | :--- | :--- |


| linkId | string | 监测链接ID |
| :--- | :--- | :--- |


| id | string | 资源ID |
| :--- | :--- | :--- |


| name | string | 监测链接名称 |
| :--- | :--- | :--- |


| projectId | string | 项目UID |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">trackingUrl</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">
        <p>&#x76D1;&#x6D4B;&#x94FE;&#x63A5;&#x3002;</p>
        <p>GrowingIO &#x5206;&#x914D;&#x7684;&#x8FFD;&#x8E2A;&#x94FE;&#x63A5;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| redirectUrl | string | 转跳链接 |
| :--- | :--- | :--- |


| imptrackingUrl | string | 曝光检测链接 |
| :--- | :--- | :--- |


| redirectUrl | string | 跳转链接 |
| :--- | :--- | :--- |


| channelId | string | 推广渠道ID |
| :--- | :--- | :--- |


| channelName | string | 推广渠道名称 |
| :--- | :--- | :--- |


| campaignId | string | 广告活动ID |
| :--- | :--- | :--- |


| campaignName | string | 广告活动名称 |
| :--- | :--- | :--- |


| utmMedium | string | 广告媒介 |
| :--- | :--- | :--- |


| utmContent | string | 广告内容 |
| :--- | :--- | :--- |


| utmTerm | string | 广告关键字 |
| :--- | :--- | :--- |


| comment | string | 备注 |
| :--- | :--- | :--- |


| status | string | 状态 |
| :--- | :--- | :--- |


| creatorId | string | 创建人ID |
| :--- | :--- | :--- |


| creatorName | string | 创建人名称 |
| :--- | :--- | :--- |


| updaterId | string | 最后更新人ID |
| :--- | :--- | :--- |


| updaterName | string | 最后更新人名称 |
| :--- | :--- | :--- |


| createdAt | long | 创建时间 |
| :--- | :--- | :--- |


| updatedAt | long | 更新时间 |
| :--- | :--- | :--- |
{% endtab %}

{% tab title="返回示例" %}
```text
{
    "id": "xogvY0Pm",
    "linkId": "xogvY0Pm",
    "name": "测试web8",
    "projectId": "4PYJMWoM",
    "trackingUrl": "https://datayi.cn/w/xogvY0Pm",
    "impTrackingUrl": null,
    "redirectUrl": "http://www.www.www",
    "campaignId": "xogjZQ2P",
    "campaignName": "test0620",
    "channelId": "vnomv9zJ",
    "channelName": "百度联盟",
    "utmMedium": "对对对",
    "utmContent": "内容",
    "utmTerm": "免费观看",
    "comments": "备注",
    "status": "activated",
    "creatorId": "AwoVvo28",
    "creatorName": "系统",
    "updaterId": "AwoVvo28",
    "updaterName": "系统",
    "createdAt": 1569465492862,
    "updatedAt": 1569465492862
}
```
{% endtab %}
{% endtabs %}

