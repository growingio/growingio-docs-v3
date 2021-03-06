# 获取全部事件类型原始数据的下载链接

## URL

[https://www.growingio.com/v2/insights/{export\_type}/{ai}/{export\_date}.json?expire={minutes}](https://www.growingio.com/v2/insights/{export_type}/{ai}/{export_date}.json?expire={minutes})

## 请求类型

GET

## 请求头部

公共头部请参考[公共请求头参数](../../authenticate.md)。

## 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |


| export\_type | string | 是 | 导出任务类型，系统目前支持小时与天的导出，可选值：hour 或者 day |
| :--- | :--- | :--- | :--- |


| ai | string | 是 | 项目ID。 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">export_date</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x662F;</th>
      <th style="text-align:left">
        <p>&#x5BFC;&#x51FA;&#x6570;&#x636E;&#x5317;&#x4EAC;&#x65F6;&#x95F4;&#xFF0C;&#x683C;&#x5F0F;&#x4E3A;
          yyyyMMddHHmm, &#x8868;&#x73B0;&#x8BF7;&#x6C42;&#x5BFC;&#x51FA;&#x54EA;&#x6BB5;&#x65F6;&#x95F4;&#x5185;&#x7684;&#x6570;&#x636E;&#xFF0C;&#x5206;&#x4E3A;&#x4EE5;&#x4E0B;&#x60C5;&#x51B5;&#xFF1A;</p>
        <ul>
          <li>&#x5F53; export_type &#x4E3A; day &#x65F6;&#xFF0C;&#x53EA;&#x4F1A;&#x622A;&#x53D6;
            export_date &#x4E2D; yyyyMMdd, &#x5176;&#x4F59;&#x5C06;&#x5FFD;&#x7565;&#x3002;</li>
          <li>&#x5F53; export_type &#x4E3A; hour &#x65F6;&#xFF0C;&#x53EA;&#x4F1A;&#x622A;&#x53D6;
            export_date &#x4E2D; yyyyMMddHH, &#x5176;&#x4F59;&#x5C06;&#x5FFD;&#x7565;&#x3002;</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

| 查询参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">minutes</th>
      <th style="text-align:left">integer</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x94FE;&#x63A5;&#x5931;&#x6548;&#x65F6;&#x95F4;&#xFF0C;&#x5355;&#x4F4D;&#x4E3A;&#x5206;&#x949F;&#x3002;</p>
        <p>&#x6700;&#x5927;&#x503C;7&#x5929;&#x3002;</p>
        <p>&#x9ED8;&#x8BA4;&#x503C;&#xFF1A;5</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="返回参数" %}
| 名称 | 说明 |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">status</th>
      <th style="text-align:left">
        <p>&#x5BFC;&#x51FA;&#x72B6;&#x6001;&#x3002;&#x53EF;&#x80FD;&#x503C;&#x4E3A;&#xFF1A;</p>
        <ul>
          <li>FINISHED&#xFF1A;&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x5B8C;&#x6210;&#xFF0C;&#x5BA2;&#x6237;&#x53EF;&#x4EE5;&#x4F7F;&#x7528;
            downloadLinks &#x4E2D;&#x7684;&#x94FE;&#x63A5;&#x8FDB;&#x884C;&#x6587;&#x4EF6;&#x4E0B;&#x8F7D;&#x3002;</li>
          <li>RUNNING&#xFF1A;&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x6B63;&#x5728;&#x8FD0;&#x884C;&#x3002;</li>
          <li>NOT_EXISTS&#xFF1A;&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x4E0D;&#x5B58;&#x5728;&#xFF0C;&#x8BF7;&#x68C0;&#x67E5;&#x662F;&#x5426;&#x5F00;&#x542F;&#x4E86;&#x5BFC;&#x51FA;&#x529F;&#x80FD;&#x5E76;&#x68C0;&#x67E5;&#x8BF7;&#x6C42;&#x65E5;&#x671F;&#x65F6;&#x95F4;&#x3002;</li>
          <li>ERROR&#xFF1A;&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x53D1;&#x751F;&#x9519;&#x8BEF;&#x3002;</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">downloadLinks</th>
      <th style="text-align:left">
        <p>&#x6587;&#x4EF6;&#x4E0B;&#x8F7D;&#x94FE;&#x63A5;&#x3002;</p>
        <p>&#x94FE;&#x63A5;&#x53EF;&#x80FD;&#x968F;&#x65F6;&#x8C03;&#x6574;&#xFF0C;&#x4E0D;&#x5E94;&#x4F7F;&#x7528;&#x94FE;&#x63A5;&#x4E2D;&#x7684;&#x4EFB;&#x4F55;&#x5185;&#x5BB9;&#x4F5C;&#x4E3A;&#x5904;&#x7406;&#x7A0B;&#x5E8F;&#x4F9D;&#x636E;&#xFF0C;&#x94FE;&#x63A5;&#x8FC7;&#x671F;&#x65F6;&#x95F4;&#x9ED8;&#x8BA4;&#x4E3A;5&#x5206;&#x949F;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

| exportType | 表示导出任务类型，由用户传入，服务器原样返回。 |
| :--- | :--- |


| dataType | 表示导出数据类型，由用户传入，服务器原样返回。 |
| :--- | :--- |


| exportDate | 表示导出数据时间，由用户传入，服务器根据 exportType 截取后返回。 |
| :--- | :--- |


| exportVersion | 表示导出数据版本，当前版本下默认为 v2。 |
| :--- | :--- |


| requestTime | 客户请求发生时服务器时间。 |
| :--- | :--- |


| errorMsg | 请求发生错误时，服务器返回的错误信息。 |
| :--- | :--- |
{% endtab %}

{% tab title="响应示例" %}
```text
{
    "status": "FINISHED",
    "downloadLinks": {
        "evar": [],
        "vstr": [],
        "pvar": [],
        "action_tag": [],
        "custom_event": [],
        "page": [],
        "ads_track_activation": [],
        "visit": [],
        "ads_track_click": [],
        "action": []
    },
    "exportType": "hour",
    "exportDate": "2018070100",
    "exportVersion": "v2",
    "requestTime": "2018-07-18 02:37",
    "errorMsg": ""
}
```
{% endtab %}
{% endtabs %}

