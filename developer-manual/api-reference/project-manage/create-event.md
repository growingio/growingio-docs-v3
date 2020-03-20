# 创建埋点事件

> 创建打点事件，注意目前仅支持创建，不支持修改，如需修改，请到 GrowingIO 平台管理界面修改。
>
> 打点事件支持批量创建，如果一次仅创建一条，body 内也需要使用数组形式。

### URL

https://www.growingio.com/v1/api/projects/{project\_uid}/dim/events

### 请求类型

POST

### 请求头参数

公共头部请参考[公共请求头参数](../authenticate.md)。

### 请求参数与示例

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
      <td style="text-align:left">&#x4E8B;&#x4EF6;&#x540D;&#x79F0;&#xFF0C;&#x6700;&#x5927;&#x957F;&#x5EA6;&#x4E3A;30&#x5B57;&#x7B26;</td>
    </tr>
    <tr>
      <td style="text-align:left">type</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">
        <p>&#x4E8B;&#x4EF6;&#x7C7B;&#x578B;&#x3002;</p>
        <ul>
          <li>counter&#xFF1A;&#x8BA1;&#x6570;&#x5668;</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">key</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x4E8B;&#x4EF6;&#x6807;&#x8BC6;&#x7B26;&#xFF0C;&#x53EA;&#x5141;&#x8BB8;&#x4EE5;&#x5B57;&#x6BCD;&#x6216;&#x4E0B;&#x5212;&#x7EBF;&#x5F00;&#x5934;&#xFF0C;&#x5305;&#x542B;&#x4E0B;&#x5212;&#x7EBF;&#x3001;&#x5B57;&#x6BCD;&#x548C;&#x6570;&#x5B57;&#x7684;&#x5B57;&#x7B26;&#x4E32;&#xFF0C;&#x6700;&#x5927;&#x957F;&#x5EA6;&#x662F;50.</td>
    </tr>
    <tr>
      <td style="text-align:left">description</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">&#x4E8B;&#x4EF6;&#x63CF;&#x8FF0;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">attrs</td>
      <td style="text-align:left">array</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">&#x4E8B;&#x4EF6;&#x5173;&#x8054;&#x7684;&#x7EF4;&#x5EA6;&#x5C5E;&#x6027;&#x3002;</td>
    </tr>
  </tbody>
</table>attrs字段为事件需要关联的维度属性，以下为attrs对应的字段：

| 名称 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| id | Sring | 是 | 事件级变量的UID。 |
{% endtab %}

{% tab title="响应示例" %}
200：OK
{% endtab %}
{% endtabs %}



