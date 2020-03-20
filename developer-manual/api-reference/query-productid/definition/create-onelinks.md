# 新建监测链接（增加APP下载量-同时推广iOS和Android）

### URL

https://www.growingio.com/api/v1/projects/{project\_uid}/meta/onelinks

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
| name | string | 是 | 监测链接名称。同一个账号下系统会进行链接的同名校验，请勿重复提交同名链接。 |
| productIdAndroid | string | 是 | Android产品ID。从[查询应用ID](cha-xun-ying-yong-id.md)获取。 |
| productIdIos | string | 是 | iOS产品ID。从[查询应用ID](cha-xun-ying-yong-id.md)获取。 |
| channelId | string | 是 | 推广渠道ID。 |
| campaignIdIos | string  | 是 | iOS广告活动ID。 |
| campaignIdAndroid | string | 是 | Android广告活动ID。 |
| redirectUrl | string | 否 | 跳转链接。 |
{% endtab %}

{% tab title="返回参数" %}


<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x540D;&#x79F0;</th>
      <th style="text-align:left">&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">linkId</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x76D1;&#x6D4B;&#x94FE;&#x63A5;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x8D44;&#x6E90;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x76D1;&#x6D4B;&#x94FE;&#x63A5;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">projectId</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x9879;&#x76EE;UID</td>
    </tr>
    <tr>
      <td style="text-align:left">productIdAndroid</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Android&#x4EA7;&#x54C1;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">productNameAndroid</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Android &#x4EA7;&#x54C1;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">productIdIos</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">iOS&#x4EA7;&#x54C1;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">productNameIos</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">iOS&#x4EA7;&#x54C1;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">trackingUrl</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p>&#x76D1;&#x6D4B;&#x94FE;&#x63A5;</p>
        <p>GrowingIO &#x5206;&#x914D;&#x7684;&#x8FFD;&#x8E2A;&#x94FE;&#x63A5;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">redirectUrl</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x76EE;&#x6807;&#x94FE;&#x63A5;</td>
    </tr>
    <tr>
      <td style="text-align:left">channelId</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x63A8;&#x5E7F;&#x6E20;&#x9053;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">channelName</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x63A8;&#x5E7F;&#x6E20;&#x9053;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">campaignIdIos</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">iOS &#x5E7F;&#x544A;&#x6D3B;&#x52A8;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">campaignIdAndroid</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Android&#x5E7F;&#x544A;&#x6D3B;&#x52A8;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">campaignNameIos</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">iOS&#x5E94;&#x7528;&#x6240;&#x5C5E;&#x63A8;&#x5E7F;&#x6D3B;&#x52A8;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">campaignNameAndroid</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Android &#x5E94;&#x7528;&#x6240;&#x5C5E;&#x63A8;&#x5E7F;&#x6D3B;&#x52A8;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">status</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x72B6;&#x6001;</td>
    </tr>
    <tr>
      <td style="text-align:left">creatorId</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x521B;&#x5EFA;&#x4EBA;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">creatorName</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x521B;&#x5EFA;&#x4EBA;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">updaterId</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x6700;&#x540E;&#x66F4;&#x65B0;&#x4EBA;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">updaterName</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x6700;&#x540E;&#x66F4;&#x65B0;&#x4EBA;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">createdAt</td>
      <td style="text-align:left">Long</td>
      <td style="text-align:left">&#x521B;&#x5EFA;&#x65F6;&#x95F4;</td>
    </tr>
    <tr>
      <td style="text-align:left">updatedAt</td>
      <td style="text-align:left">Long</td>
      <td style="text-align:left">&#x66F4;&#x65B0;&#x65F6;&#x95F4;</td>
    </tr>
  </tbody>
</table>
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

