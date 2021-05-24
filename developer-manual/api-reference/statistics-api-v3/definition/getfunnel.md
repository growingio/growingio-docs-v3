# 获取漏斗分析数据

## URL <a id="url"></a>

[https://www.growingio.com/v3/exporter/projects/{project\_uid}/funnels/{funnel\_id}](https://www.growingio.com/v3/exporter/projects/{project_uid}/funnels/{funnel_id})

## 请求类型 <a id="qing-qiu-lei-xing"></a>

GET

## 结果返回方式 <a id="qing-qiu-lei-xing"></a>

异步：参考 [概述](../overview.md) 部分的描述

## 请求头参数 <a id="qing-qiu-tou-can-shu"></a>

公共头部请参考[公共请求头参数](../../authenticate.md)。

## 参数说明与示例 <a id="can-shu-shuo-ming-yu-shi-li"></a>

{% tabs %}
{% tab title="请求参数" %}
<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x8DEF;&#x5F84;&#x53C2;&#x6570;</th>
      <th style="text-align:left">&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x662F;&#x5426;&#x5FC5;&#x4F20;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">funnel_id</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">
        <p>&#x6F0F;&#x6597;&#x5206;&#x6790;&#x5355;&#x56FE;ID</p>
        <p>&#x8BE6;&#x7EC6;&#x8BF7;&#x53C2;&#x8003;&#xFF1A; <a href="../../statistics-api/definition/get-chartinfo.md">&#x83B7;&#x53D6;&#x770B;&#x677F;&#x4E2D;&#x7684;&#x56FE;&#x8868;&#x4FE1;&#x606F;</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">project_uid</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x9879;&#x76EE;UID&#xFF0C;&#x8BE6;&#x7EC6;&#x8BF7;&#x53C2;&#x8003;
        <a
        href="../../../../product-manual/projectmange/projectmange/get-uid.md">&#x83B7;&#x53D6;&#x9879;&#x76EE;UID</a>
      </td>
    </tr>
  </tbody>
</table>

| 查询参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |


| conversionWindow | integer | 否 | 转化周期：单位：天 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">startTime</th>
      <th style="text-align:left">integer</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x6570;&#x636E;&#x8D77;&#x59CB;&#x65F6;&#x95F4;&#xFF0C;unix&#x6BEB;&#x79D2;&#x65F6;&#x95F4;&#x6233;&#x3002;</p>
        <p>&#x9700;&#x4E0E;endTime&#x4E00;&#x8D77;&#x4F7F;&#x7528;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">endTime</th>
      <th style="text-align:left">integer</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x6570;&#x636E;&#x7ED3;&#x675F;&#x65F6;&#x95F4;&#xFF0C;unix&#x6BEB;&#x79D2;&#x65F6;&#x95F4;&#x6233;&#x3002;</p>
        <p>&#x9700;&#x4E0E;startTime&#x4E00;&#x8D77;&#x4F7F;&#x7528;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="返回示例" %}
导出未完成：

```text
{"id":"随机ID","status":"doing"}
```

导出完成：

```text
{
"id":  "Funnel Uid",
"name":  "Funnel Name",
"conversionWindow":  1,
"startTime":  1571068800000,
"endTime":  1572278399999,
"interval":  86400000,
"meta":  [
    {"name":"目标用户","dimension":true},
    {"name":"时间","dimension":true},
    {"name":"总转化率","metric":true},
    {"name":"第一步人数","metric":true},
    {"name":"第一步转化率","metric":true},
    ...
    {"name":"最后一步人数","metric":true},
    {"name":"最后一步转化率","metric":true}
]
"data":  [
    [目标用户, 时间, 总转化率, 第一步人数, ... , 最后一步转化率],
    [目标用户, 时间, 总转化率, 第一步人数, ... , 最后一步转化率],
    ...
]
}
```
{% endtab %}
{% endtabs %}

