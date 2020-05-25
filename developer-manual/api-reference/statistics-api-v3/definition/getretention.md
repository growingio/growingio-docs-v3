# 获取留存分析数据

## URL <a id="url"></a>

[https://www.growingio.com/v3/exporter/projects/{project\_uid}/retentions/{retention\_id}](https://www.growingio.com/v3/exporter/projects/{project_uid}/retentions/{retention_id})

## 请求类型 <a id="qing-qiu-lei-xing"></a>

GET

## 结果返回方式 <a id="qing-qiu-lei-xing"></a>

异步：参考 [概述](../overview.md) 部分的描述

## 请求头参数 <a id="qing-qiu-tou-can-shu"></a>

公共头部请参考[公共请求头参数](../../authenticate.md)。

## 参数说明与示例 <a id="can-shu-shuo-ming-yu-shi-li"></a>

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| retention\_id | string | 是 | 留存分析单图ID。 |
| project\_uid | string | 是 | 项目UID。 |

| 查询参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">range</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x4E8B;&#x4EF6;&#x8303;&#x56F4;&#x3002;</p>
        <ul>
          <li>day&#xFF08;&#x65E5;&#x7559;&#x5B58;&#xFF09;</li>
          <li>week&#xFF08;&#x5468;&#x7559;&#x5B58;&#xFF09;</li>
          <li>month&#xFF08;&#x6708;&#x7559;&#x5B58;&#xFF09;</li>
        </ul>
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
导出未完成：

```text
{"id":"随机ID","status":"doing"}
```

导出完成：

```text
{
    "id":  "Retention Uid",
    "name":  "Retention Name",
    "range":  "day",
    "startTime":  1569686400000,
    "endTime":  1572278399999,
    "interval":  86400000,
    "meta":  [
        {"name":"目标用户","dimension":true},
        {"name":"对比值","dimension":true},
        {"name":"用户行为","dimension":true},
        {"name":"时间","dimension":true},
        {"name":"留存人数","metric":true},
        {"name":"当日","metric":true},
        {"name":"当日留存率","metric":true},
        {"name":"次日","metric":true},
        {"name":"次日留存率","metric":true},
        {"name":"2日后","metric":true},
        {"name":"2日后留存率","metric":true},
        . . .
        {"name":"29日后","metric":true},
        {"name":"29日后留存率","metric":true}
    ],
    "data":  [
        [目标用户,对比值,用户行为,时间,留存,...,29日后留存],
        . . .,
        [目标用户,对比值,用户行为,时间,留存,...,29日后留存]
    ]
}
```
{% endtab %}
{% endtabs %}

