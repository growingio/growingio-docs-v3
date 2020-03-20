# 创建登录用户变量

> 创建登录用户变量，目前仅支持创建，不支持修改，如需修改请到 GrowingIO 平台管理界面修改。

### URL

https://www.growingio.com/v1/api/projects/{project\_uid}/vars/peoples

### 请求类型

POST

### 请求头参数

公共头部请参考[公共请求头参数](../authenticate.md)。

### 参数说明与示例

{% tabs %}
{% tab title="参数说明" %}
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
      <td style="text-align:left">&#x53D8;&#x91CF;&#x6807;&#x8BC6;&#x7B26;&#xFF0C;&#x53EA;&#x5141;&#x8BB8;&#x4EE5;&#x5B57;&#x6BCD;&#x6216;&#x4E0B;&#x5212;&#x7EBF;&#x5F00;&#x5934;&#xFF0C;&#x5305;&#x542B;&#x4E0B;&#x5212;&#x7EBF;&#x3001;&#x5B57;&#x6BCD;&#x3001;&#x6570;&#x5B57;&#x7684;&#x5B57;&#x7B26;&#x4E32;&#xFF0C;&#x6700;&#x5927;&#x957F;&#x5EA6;&#x4E3A;50.</td>
    </tr>
    <tr>
      <td style="text-align:left">attribution</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">
        <p>&#x5F52;&#x56E0;&#x65B9;&#x5F0F;</p>
        <ul>
          <li>mostRecent&#xFF1A;&#x6700;&#x8FD1;&#x5F52;&#x56E0;</li>
          <li>final&#xFF1A;&#x6700;&#x7EC8;&#x5F52;&#x56E0;</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">description</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">&#x53D8;&#x91CF;&#x63CF;&#x8FF0;&#xFF0C;&#x6700;&#x5927;&#x957F;&#x5EA6;&#x4E3A;150</td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="返回示例" %}
200: OK
{% endtab %}
{% endtabs %}

