# 新建推广活动

### URL

https://www.growingio.com/api/v1/projects/{project\_uid}/meta/campaigns

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

<table>
  <thead>
    <tr>
      <th style="text-align:left">body&#x53C2;&#x6570;</th>
      <th style="text-align:left">&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x662F;&#x5426;&#x5FC5;&#x4F20;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">name</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">
        <p>&#x540D;&#x79F0;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x53CC;&#x5341;&#x4E00;&#x63A8;&#x5E7F;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">productId</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">&#x5BF9;&#x5E94;&#x7684;App&#x7684;ID&#x3002;</td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="body示例" %}
```text
{
  "productId":"rREJ88PL",
  "name":"双十一推广"
}
```
{% endtab %}

{% tab title="返回参数" %}
| 名称 | 类型 | 说明 |
| :--- | :--- | :--- |
| id | string | 活动ID。 |
| name | string | 活动名称。 |
| productId | string | 对应App的ID。 |
{% endtab %}

{% tab title="响应示例" %}
```text
{
  "id": "gnPNkoWA",
  "productId":"rREJ88PL",
  "name":"双十一推广"
}
```
{% endtab %}
{% endtabs %}

