# 新建监测链接（增加App下载量-推广iOS或Android单个平台）

### URL

https://www.growingio.com/api/v1/projects/{project\_uid}/meta/normallinks

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
| productId | string | 是 | 应用ID。 |
| channelId | string | 是 | 渠道ID。 |
| campaignId | string | 是 | 活动ID。 |
| redirectUrl | string | 否 | 转跳链接。 |
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
      <td style="text-align:left">productId</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x4EA7;&#x54C1;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">appId</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x4EA7;&#x54C1;&#x7684;&#x5305;&#x540D;</td>
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
    <tr>
      <td style="text-align:left">params</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x817E;&#x8BAF;&#x793E;&#x4EA4;&#x5E7F;&#x544A;&#x53C2;&#x6570;</td>
    </tr>
  </tbody>
</table>
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



