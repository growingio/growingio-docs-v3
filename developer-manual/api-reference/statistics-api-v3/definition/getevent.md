# 获取事件分析数据

## URL <a id="url"></a>

[https://www.growingio.com/v3/exporter/projects/{project\_uid}/charts/{chart\_id}](https://www.growingio.com/v3/exporter/projects/{project_uid}/charts/{chart_id})

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
      <td style="text-align:left">chart_id</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">
        <p>&#x4E8B;&#x4EF6;&#x5206;&#x6790;&#x5355;&#x56FE;ID</p>
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


<table>
  <thead>
    <tr>
      <th style="text-align:left">interval</th>
      <th style="text-align:left">integer</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x6570;&#x636E;&#x7C92;&#x5EA6;&#xFF0C;&#x5355;&#x4F4D;&#x4E3A;&#x6BEB;&#x79D2;&#x3002;</p>
        <ul>
          <li>3600000(1&#x5C0F;&#x65F6;)</li>
          <li>86400000(1&#x5929;)</li>
          <li>604800000(1&#x5468;)</li>
          <li>2592000000(1&#x6708;)</li>
        </ul>
        <p>&#x9ED8;&#x8BA4;&#x503C;86400000&#xFF08;1&#x5929;&#xFF09;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">startTime</th>
      <th style="text-align:left">long</th>
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
      <th style="text-align:left">long</th>
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

{% tab title="响应示例" %}
导出未完成：

```text
{"id":"随机ID","status":"doing"}
```

导出完成：

```text
{
    "id":  "Chart  Uid",
    "name":  "Chart  Name",
    "startTime":  1462118400000,
    "endTime":  1462118400000,
    "interval":  86400000,
    "aggregator": {    // 当大数字图时返回该字段
        "values": [
            27557,    // 本周期聚合值
            25409     // 上周期聚合值
        ]
    }
    "meta":  [
        {  "name":  "目标用户",  "dimension":  true},
        {  "name":  "城市",  "dimension":  true  },
        {  "name":  "浏览器",  "dimension":  true  },
        {  "name":  "Metric  1",  "metric":  true  },
        {  "name":  "Metric  2",  "metric":  true  }
    ],
    "data":  [
        //  线图
        [目标用户,  timestamp,  metric1,  metric2],
        [目标用户,  timestamp,  metric1,  metric2]
​
        //  横向柱图
        [目标用户,  dimension_v1,  metric1],
        [目标用户,  dimension_v2,  metric1]
​
        //  纵向柱图
        [目标用户,  timestamp,  metric1,  metrics2],
        [目标用户,  timestamp,  metric1,  metrics2]
​
        //  表格
        [目标用户,  dimension1_v1,  dimension2_v1,  metric1,  metric2],
        [目标用户,  dimension1_v2,  dimension2_v1,  metric1,  metric2]
​
        //  大数字
        [目标用户,  timestamp,  metric1]
​
        //  气泡图
        [目标用户,  dimension1_v1,  dimension2_v1,  metric1,  metric2]
    ]
}
```
{% endtab %}
{% endtabs %}

