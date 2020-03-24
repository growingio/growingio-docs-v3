# 获取事件分析数据

## URL

[https://www.growingio.com/v2/projects/{project\_uid}/charts/{chart\_id}.json](https://www.growingio.com/v2/projects/{project_uid}/charts/{chart_id}.json)

## 请求类型

GET

## 请求头参数

公共头部请参考[公共请求头参数](../../authenticate.md)。

## 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| chart\_id | string | 是 | 事件分析单图ID。 |
| project\_uid | string | 是 | 项目UID。 |

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
</table><table>
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
</table><table>
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

{% tab title="响应示例" %}
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

