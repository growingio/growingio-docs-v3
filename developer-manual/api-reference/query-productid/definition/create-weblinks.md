# 新建监测链接（推广网页）

### URL

https://www.growingio.com/api/v1/projects/{project\_uid}/meta/weblinks

### 请求类型

POST

### 请求头参数

公共头部请参考[公共请求头参数](../../authenticate.md)。

### 参数说明与示例

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
<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5B57;&#x6BB5;&#x540D;</th>
      <th style="text-align:left">&#x5B57;&#x6BB5;&#x683C;&#x5F0F;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">linkId</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x76D1;&#x6D4B;&#x94FE;&#x63A5;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">id</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x8D44;&#x6E90;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">name</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x76D1;&#x6D4B;&#x94FE;&#x63A5;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">projectId</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x9879;&#x76EE;UID</td>
    </tr>
    <tr>
      <td style="text-align:left">trackingUrl</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">
        <p>&#x76D1;&#x6D4B;&#x94FE;&#x63A5;&#x3002;</p>
        <p>GrowingIO &#x5206;&#x914D;&#x7684;&#x8FFD;&#x8E2A;&#x94FE;&#x63A5;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">redirectUrl</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x8F6C;&#x8DF3;&#x94FE;&#x63A5;</td>
    </tr>
    <tr>
      <td style="text-align:left">imptrackingUrl</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x66DD;&#x5149;&#x68C0;&#x6D4B;&#x94FE;&#x63A5;</td>
    </tr>
    <tr>
      <td style="text-align:left">redirectUrl</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x8DF3;&#x8F6C;&#x94FE;&#x63A5;</td>
    </tr>
    <tr>
      <td style="text-align:left">channelId</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x63A8;&#x5E7F;&#x6E20;&#x9053;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">channelName</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x63A8;&#x5E7F;&#x6E20;&#x9053;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">campaignId</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5E7F;&#x544A;&#x6D3B;&#x52A8;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">campaignName</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5E7F;&#x544A;&#x6D3B;&#x52A8;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">utmMedium</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5E7F;&#x544A;&#x5A92;&#x4ECB;</td>
    </tr>
    <tr>
      <td style="text-align:left">utmContent</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5E7F;&#x544A;&#x5185;&#x5BB9;</td>
    </tr>
    <tr>
      <td style="text-align:left">utmTerm</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5E7F;&#x544A;&#x5173;&#x952E;&#x5B57;</td>
    </tr>
    <tr>
      <td style="text-align:left">comment</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5907;&#x6CE8;</td>
    </tr>
    <tr>
      <td style="text-align:left">status</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x72B6;&#x6001;</td>
    </tr>
    <tr>
      <td style="text-align:left">creatorId</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x521B;&#x5EFA;&#x4EBA;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">creatorName</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x521B;&#x5EFA;&#x4EBA;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">updaterId</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x6700;&#x540E;&#x66F4;&#x65B0;&#x4EBA;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">updaterName</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x6700;&#x540E;&#x66F4;&#x65B0;&#x4EBA;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">createdAt</td>
      <td style="text-align:left">long</td>
      <td style="text-align:left">&#x521B;&#x5EFA;&#x65F6;&#x95F4;</td>
    </tr>
    <tr>
      <td style="text-align:left">updatedAt</td>
      <td style="text-align:left">long</td>
      <td style="text-align:left">&#x66F4;&#x65B0;&#x65F6;&#x95F4;</td>
    </tr>
  </tbody>
</table>
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

