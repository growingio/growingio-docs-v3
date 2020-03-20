# 查询监测链接（吸引用户直接打开App）

### URL

https://www.growingio.com/api/v1/projects/{project\_uid}/meta/deeplinks

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
      <td style="text-align:left">productIdAndroid</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Android&#x4EA7;&#x54C1;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">productNameAndroid</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Android&#x4EA7;&#x54C1;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">trackingUrl</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x76D1;&#x6D4B;&#x94FE;&#x63A5;</td>
    </tr>
    <tr>
      <td style="text-align:left">downloadUrlIos</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">iOS&#x5E94;&#x7528;&#x4E0B;&#x8F7D;&#x5730;&#x5740;</td>
    </tr>
    <tr>
      <td style="text-align:left">downloadUrlAndroid</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Android&#x5E94;&#x7528;&#x4E0B;&#x8F7D;&#x5730;&#x5740;</td>
    </tr>
    <tr>
      <td style="text-align:left">urlSchemaIos</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">iOS URL Scheme&#xFF1F;&#xFF1F;&#xFF1F;&#x5E94;&#x7528;&#x7684;urlscheme</td>
    </tr>
    <tr>
      <td style="text-align:left">urlSchemaAndroid</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Android URL Scheme</td>
    </tr>
    <tr>
      <td style="text-align:left">campaignIdIos</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">iOS&#x5E7F;&#x544A;&#x6D3B;&#x52A8;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">campaignNameIos</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">iOS&#x5E7F;&#x544A;&#x6D3B;&#x52A8;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">campaignIdAndroid</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Android&#x5E7F;&#x544A;&#x6D3B;&#x52A8;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">campaignNameAndroid</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Android&#x5E7F;&#x544A;&#x6D3B;&#x52A8;&#x540D;&#x79F0;</td>
    </tr>
    <tr>
      <td style="text-align:left">iosParams</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">iOS&#x5524;&#x9192;&#x53C2;&#x6570;</td>
    </tr>
    <tr>
      <td style="text-align:left">androidParams</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">Android&#x5524;&#x9192;&#x53C2;&#x6570;</td>
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
  </tbody>
</table>
{% endtab %}

{% tab title="响应示例" %}
```text
[
    {
        "id": "GQPDxPNm",
        "linkId": "dGVr8e9",
        "name": "321deeplink",
        "projectId": "4PYJMWoM",
        "productIdIos": "xRxVp0o5",
        "productNameIos": "TestAPP",
        "productIdAndroid": "LPdgKARN",
        "productNameAndroid": "Android SDK Demo",
        "trackingUrl": "https://datayi.cn/dGVr8e9",
        "downloadUrlIos": "http://baidu.com",
        "downloadUrlAndroid": "http://growingio.com",
        "urlSchemaIos": "c35abef955cd913a",
        "urlSchemaAndroid": "8137d31f4e7b819f",
        "campaignIdIos": "j9yB1nRy",
        "campaignNameIos": "321上线",
        "campaignIdAndroid": "xoga4DRm",
        "campaignNameAndroid": "321上线验证1",
        "iosParams": null,
        "androidParams": null,
        "channelId": "34RzeX9V",
        "channelName": "123测试编辑编辑",
        "status": "activated",
        "creatorId": "nRbm8d93",
        "creatorName": "xx",
        "updaterId": "nRbm8d93",
        "updaterName": "xx",
        "createdAt": 1521642287367,
        "updatedAt": 1521642287367
    }
]
```
{% endtab %}
{% endtabs %}

