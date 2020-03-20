# 创建事件级变量

> 创建事件级变量，目前仅支持创建，不支持修改，如需修改，请到 GrowingIO 平台管理界面修改。

### URL

https://www.growingio.com/v1/api/projects/{project\_uid}/vars/events

### 请求类型

POST

### 请求头参数

公共头部请参考[公共请求头参数](../authenticate.md)。

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
      <td style="text-align:left">&#x53D8;&#x91CF;&#x540D;&#x79F0;&#xFF0C;&#x6700;&#x5927;&#x957F;&#x5EA6;&#x4E3A;30</td>
    </tr>
    <tr>
      <td style="text-align:left">key</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x53D8;&#x91CF;&#x6807;&#x8BC6;&#x7B26;&#xFF0C;&#x53EA;&#x5141;&#x8BB8;&#x4EE5;&#x5B57;&#x6BCD;&#x83B7;&#x4E0B;&#x5212;&#x7EBF;&#x5F00;&#x5934;&#xFF0C;&#x5305;&#x542B;&#x4E0B;&#x5212;&#x7EBF;&#x3001;&#x5B57;&#x7801;&#x3001;&#x6570;&#x5B57;&#x7684;&#x5B57;&#x7B26;&#x4E32;&#xFF0C;&#x6700;&#x5927;&#x957F;&#x5EA6;&#x4E3A;30</td>
    </tr>
    <tr>
      <td style="text-align:left">type</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">
        <p>&#x53D8;&#x91CF;&#x7C7B;&#x578B;&#x3002;</p>
        <ul>
          <li>string</li>
          <li>int</li>
          <li>double</li>
        </ul>
        <p>&#x9ED8;&#x8BA4;&#x4E3A;string&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">description</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">&#x53D8;&#x91CF;&#x63CF;&#x8FF0;&#xFF0C;&#x6700;&#x5927;&#x957F;&#x5EA6;150&#x3002;</td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="返回示例" %}
200: OK
{% endtab %}
{% endtabs %}



