# 来源管理数据导出

### URL

https://www.growingio.com/projects/{project\_uid}/activities.json

### 请求方式

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
      <th style="text-align:left">&#x540D;&#x79F0;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">id</td>
      <td style="text-align:left">ID</td>
    </tr>
    <tr>
      <td style="text-align:left">name</td>
      <td style="text-align:left">
        <p>&#x540D;&#x79F0;&#xFF08;&#x843D;&#x5730;&#x9875;&#x547D;&#x540D;&#xFF09;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;12.16&#x589E;&#x957F;&#x5927;&#x4F1A;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">href</td>
      <td style="text-align:left">
        <p>&#x76EE;&#x6807;&#x94FE;&#x63A5;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;www.growingio.com</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">platform</td>
      <td style="text-align:left">
        <p>&#x5E73;&#x53F0;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x7F51;&#x9875;&#x4E3A;web&#xFF0C;&#x79FB;&#x52A8;&#x5E94;&#x7528;&#x4E3A;mobile</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">utmCampaign</td>
      <td style="text-align:left">
        <p>&#x5E7F;&#x544A;&#x540D;&#x79F0;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x589E;&#x957F;&#x5927;&#x4F1A;&#x6D3B;&#x52A8;&#x9996;&#x9875;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">utmMedium</td>
      <td style="text-align:left">
        <p>&#x5E7F;&#x544A;&#x5A92;&#x4ECB;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;CPC</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">utmSource</td>
      <td style="text-align:left">
        <p>&#x5E7F;&#x544A;&#x6765;&#x6E90;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x5E7F;&#x70B9;&#x901A;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">utmContent</td>
      <td style="text-align:left">
        <p>&#x5E7F;&#x544A;&#x5185;&#x5BB9;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x6D3B;&#x52A8;&#x4ECB;&#x7ECD;&#x548C;&#x62A5;&#x540D;&#x8868;&#x5355;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">utmTerm</td>
      <td style="text-align:left">
        <p>&#x5E7F;&#x544A;&#x5173;&#x952E;&#x8BCD;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x589E;&#x957F;GrowingIO</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">comment</td>
      <td style="text-align:left">
        <p>&#x5907;&#x6CE8;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x63A8;&#x5E7F;&#x9884;&#x7B97;&#x4E24;&#x4E07;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">advertiser</td>
      <td style="text-align:left">
        <p>&#x63A8;&#x5E7F;&#x5E73;&#x53F0;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x666E;&#x901A;&#x63A8;&#x5E7F;&#x4F4D;&#x201D;none&#x201C;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">projectId</td>
      <td style="text-align:left">&#x9879;&#x76EE;ID</td>
    </tr>
    <tr>
      <td style="text-align:left">creatorName</td>
      <td style="text-align:left">
        <p>&#x521B;&#x5EFA;&#x4EBA;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;jacky</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">createdAt</td>
      <td style="text-align:left">
        <p>&#x521B;&#x5EFA;&#x65F6;&#x95F4;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1484397370856</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">shortUrl</td>
      <td style="text-align:left">
        <p>&#x7528;&#x4E8E;&#x6295;&#x653E;&#x7684;&#x77ED;&#x94FE;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;https://s.growingio.com/6XNmKl</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">uv</td>
      <td style="text-align:left">
        <p>&#x65B0;&#x7528;&#x6237;&#xFF0C;&#x901A;&#x8FC7;GIO&#x5E7F;&#x544A;&#x94FE;&#x63A5;&#x8BBF;&#x95EE;&#x5E7F;&#x544A;&#xFF0C;&#x5E76;&#x5728;&#x8FC7;&#x53BB;90&#x5929;&#x5185;&#x9996;&#x6B21;&#x4F7F;&#x7528;&#x60A8;&#x7684;App&#x6216;&#x7F51;&#x7AD9;&#x7684;&#x7528;&#x6237;&#x3002;&#x7528;&#x6237;&#x9996;&#x6B21;&#x4F7F;&#x7528;&#x540E;&#xFF0C;&#x6570;&#x636E;&#x6709;1&#x5C0F;&#x65F6;&#x5DE6;&#x53F3;&#x7684;&#x5EF6;&#x8FDF;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;100</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">tc</td>
      <td style="text-align:left">
        <p>&#x94FE;&#x63A5;&#x8BBF;&#x95EE;&#xFF0C;GIO&#x5E7F;&#x544A;&#x94FE;&#x63A5;&#x7684;&#x8BBF;&#x95EE;&#x6B21;&#x6570;&#xFF0C;&#x901A;&#x5E38;&#x901A;&#x8FC7;&#x70B9;&#x51FB;&#x5E7F;&#x544A;&#x4F4D;&#x6216;&#x8005;&#x626B;&#x7801;&#x8BBF;&#x95EE;&#x3002;&#x7528;&#x6237;&#x8BBF;&#x95EE;&#x540E;&#xFF0C;&#x6570;&#x636E;&#x6709;1&#x5C0F;&#x65F6;&#x5DE6;&#x53F3;&#x7684;&#x5EF6;&#x8FDF;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;120</p>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}
{% endtabs %}

