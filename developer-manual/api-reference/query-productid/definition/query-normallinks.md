# 查询监测链接（增加App下载量-推广iOS或Android单个平台）

### URL

https://www.growingio.com/api/v1/projects/{project\_uid}/meta/normallinks

### 请求类型

GET

### 请求头参数

公共头部请参考[公共请求头参数](../../authenticate.md)。

### 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |
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
      <td style="text-align:left">id</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x8D44;&#x6E90;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">linkId</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x76D1;&#x6D4B;&#x94FE;&#x63A5;ID</td>
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
      <td style="text-align:left">productId</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p>&#x4EA7;&#x54C1;ID</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;LPdgKARN</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">appId</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">
        <p>app ID</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;com.demo.app.androidsdkdemo_android</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">trackingUrl</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x76D1;&#x6D4B;&#x94FE;&#x63A5;</td>
    </tr>
    <tr>
      <td style="text-align:left">redirectUrl</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x8DF3;&#x8F6C;&#x94FE;&#x63A5;</td>
    </tr>
    <tr>
      <td style="text-align:left">impressionUrl</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x5E7F;&#x544A;&#x5C55;&#x793A;&#x94FE;&#x63A5;</td>
    </tr>
    <tr>
      <td style="text-align:left">campaignId</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">iOS&#x5E7F;&#x544A;&#x6D3B;&#x52A8;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">campaignName</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">iOS&#x5E7F;&#x544A;&#x6D3B;&#x52A8;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">channelId</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x6E20;&#x9053;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">channelName</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x6E20;&#x9053;&#x540D;&#x79F0;</td>
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
      <td style="text-align:left">
        <p>&#x521B;&#x5EFA;&#x65F6;&#x95F4;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1521642287367</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">updatedAt</td>
      <td style="text-align:left">Long</td>
      <td style="text-align:left">
        <p>&#x66F4;&#x65B0;&#x65F6;&#x95F4;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1521642287367</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">params</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x817E;&#x8BAF;&#x793E;&#x4EA4;&#x5E7F;&#x544A;&#x53C2;&#x6570;</td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="响应示例" %}
```text
[
    {
        "id": "La9BwRne",
        "linkId": "r3A5LOd",
        "name": "测试链接二",
        "projectId": "4PYJMWoM",
        "productId": "LPdgKARN",
        "appId": "com.demo.app.androidsdkdemo_android",
        "trackingUrl":"https://datayi.cn/r3A5LOd",
        "redirectUrl": null,
        "impressionUrl": null,
        "campaignId": "d4PYjoME",
        "campaignName": "大夜宵活动",
        "channelId": "GQPDxPNm",
        "channelName": "多盟",
        "status": "activated",
        "creatorId": "nPNgQkoW",
        "creatorName": "fowindhe111",
        "updaterId": "nPNgQkoW",
        "updaterName": "fowindhe111",
        "createdAt": 1521642287367,
        "updatedAt": 1521642287367,
        "params": null
    }
]
```
{% endtab %}
{% endtabs %}

