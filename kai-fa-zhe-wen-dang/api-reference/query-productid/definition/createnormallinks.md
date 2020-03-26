# 新建监测链接（增加App下载量-推广iOS或Android单个平台）

## URL

[https://www.growingio.com/api/v1/projects/{project\_uid}/meta/normallinks](https://www.growingio.com/api/v1/projects/{project_uid}/meta/normallinks)

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
| productId | string | 是 | 应用ID。 |
| channelId | string | 是 | 渠道ID。 |
| campaignId | string | 是 | 活动ID。 |
| redirectUrl | string | 否 | 转跳链接。 |
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


| productId | string | 产品ID |
| :--- | :--- | :--- |


| appId | string | 产品的包名 |
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
</table>| redirectUrl | string | 跳转链接 |
| :--- | :--- | :--- |


| channelId | string | 推广渠道ID |
| :--- | :--- | :--- |


| channelName | string | 推广渠道名称 |
| :--- | :--- | :--- |


| campaignId | string | 广告活动ID |
| :--- | :--- | :--- |


| campaignName | string | 广告活动名称 |
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


| params | String | 腾讯社交广告参数 |
| :--- | :--- | :--- |
{% endtab %}

{% tab title="body示例" %}
```text
 {
        "name": "normallinkstest2",
        "productId": "LPdgKARN",
        "channelId": "yYo10lPl",
        "campaignId": "G39l3o20",
        "redirectUrl": "http://www.growingio.com"
 }
```
{% endtab %}

{% tab title="响应示例" %}
```text
{
    "id": "GPn0j0q9",
    "linkId": "reJmomJ",
    "name": "normallinkstest2",
    "projectId": "4PYJMWoM",
    "productId": "LPdgKARN",
    "appId": "com.demo.app.androidsdkdemo_android",
    "trackingUrl": "https://datayi.cn/reJmomJ",
    "redirectUrl": "http://www.growingio.com",
    "impressionUrl": null,
    "campaignId": "G39l3o20",
    "campaignName": "智汇推验证_android",
    "channelId": "yYo10lPl",
    "channelName": "测试渠道",
    "status": "activated",
    "creatorId": "AwoVvo28",
    "creatorName": "系统",
    "updaterId": "AwoVvo28",
    "updaterName": "系统",
    "createdAt": 1566188740225,
    "updatedAt": 1566188740225,
    "params": null
}
```
{% endtab %}
{% endtabs %}

