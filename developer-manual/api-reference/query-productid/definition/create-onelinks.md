# 新建监测链接（增加APP下载量-同时推广iOS和Android）

## URL

[https://www.growingio.com/api/v1/projects/{project\_uid}/meta/onelinks](https://www.growingio.com/api/v1/projects/{project_uid}/meta/onelinks)

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
| name | string | 是 | 监测链接名称。同一个账号下系统会进行链接的同名校验，请勿重复提交同名链接。 |
| productIdAndroid | string | 是 | Android产品ID。从[查询应用ID](cha-xun-ying-yong-id.md)获取。 |
| productIdIos | string | 是 | iOS产品ID。从[查询应用ID](cha-xun-ying-yong-id.md)获取。 |
| channelId | string | 是 | 推广渠道ID。 |
| campaignIdIos | string | 是 | iOS广告活动ID。 |
| campaignIdAndroid | string | 是 | Android广告活动ID。 |
| redirectUrl | string | 否 | 跳转链接。 |
{% endtab %}

{% tab title="返回参数" %}
| 名称 | 类型 | 说明 |
| :--- | :--- | :--- |


| linkId | String | 监测链接ID |
| :--- | :--- | :--- |


| id | String | 资源ID |
| :--- | :--- | :--- |


| name | String | 监测链接名称 |
| :--- | :--- | :--- |


| projectId | String | 项目UID |
| :--- | :--- | :--- |


| productIdAndroid | String | Android产品ID |
| :--- | :--- | :--- |


| productNameAndroid | String | Android 产品名称 |
| :--- | :--- | :--- |


| productIdIos | String | iOS产品ID |
| :--- | :--- | :--- |


| productNameIos | String | iOS产品名称 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">trackingUrl</th>
      <th style="text-align:left">String</th>
      <th style="text-align:left">
        <p>&#x76D1;&#x6D4B;&#x94FE;&#x63A5;</p>
        <p>GrowingIO &#x5206;&#x914D;&#x7684;&#x8FFD;&#x8E2A;&#x94FE;&#x63A5;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| redirectUrl | String | 目标链接 |
| :--- | :--- | :--- |


| channelId | String | 推广渠道ID |
| :--- | :--- | :--- |


| channelName | String | 推广渠道名称 |
| :--- | :--- | :--- |


| campaignIdIos | String | iOS 广告活动ID |
| :--- | :--- | :--- |


| campaignIdAndroid | String | Android广告活动ID |
| :--- | :--- | :--- |


| campaignNameIos | String | iOS应用所属推广活动名称 |
| :--- | :--- | :--- |


| campaignNameAndroid | String | Android 应用所属推广活动名称 |
| :--- | :--- | :--- |


| status | String | 状态 |
| :--- | :--- | :--- |


| creatorId | String | 创建人ID |
| :--- | :--- | :--- |


| creatorName | String | 创建人名称 |
| :--- | :--- | :--- |


| updaterId | String | 最后更新人ID |
| :--- | :--- | :--- |


| updaterName | String | 最后更新人名称 |
| :--- | :--- | :--- |


| createdAt | Long | 创建时间 |
| :--- | :--- | :--- |


| updatedAt | Long | 更新时间 |
| :--- | :--- | :--- |
{% endtab %}

{% tab title="body示例" %}
```text
{
    "name": "tt3ts",
    "productIdIos": "rREJ88PL",
    "productIdAndroid": "LPdgKARN",
    "redirectUrl": "http://www.download.com",
    "campaignIdIos": "4AovZoza",
    "campaignIdAndroid": "G39l3o20",
    "channelId": "yYo10lPl"
}
```
{% endtab %}

{% tab title="响应参数" %}
```text
{
    "id": "bR7mgxzo",
    "linkId": "oBWXRgK",
    "name": "tt3ts",
    "projectId": "4PYJMWoM",
    "productIdIos": "rREJ88PL",
    "productNameIos": "RnTestiOS",
    "productIdAndroid": "LPdgKARN",
    "productNameAndroid": "Android SDK Demo",
    "trackingUrl": "https://datayi/oBWXRgK",
    "redirectUrl": "http://www.download.com",
    "campaignIdIos": "4AovZoza",
    "campaignNameIos": "今日头条ios",
    "campaignIdAndroid": "G39l3o20",
    "campaignNameAndroid": "智汇推验证_android",
    "channelId": "yYo10lPl",
    "channelName": "测试渠道",
    "status": "activated",
    "creatorId": "AwoVvo28",
    "creatorName": "系统",
    "updaterId": "AwoVvo28",
    "updaterName": "系统",
    "createdAt": 1566187356083,
    "updatedAt": 1566187356083
}
```
{% endtab %}
{% endtabs %}

