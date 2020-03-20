# 获取全部事件类型原始数据的下载链接

### URL

https://www.growingio.com/v2/insights/{export\_type}/{ai}/{export\_date}.json?expire={minutes}

### 请求类型

GET

### 请求头部

公共头部请参考[公共请求头参数](../../authenticate.md)。

### 参数说明与示例

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
      <td style="text-align:left">export_type</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x7C7B;&#x578B;&#xFF0C;&#x7CFB;&#x7EDF;&#x76EE;&#x524D;&#x652F;&#x6301;&#x5C0F;&#x65F6;&#x4E0E;&#x5929;&#x7684;&#x5BFC;&#x51FA;&#xFF0C;&#x53EF;&#x9009;&#x503C;&#xFF1A;hour
        &#x6216;&#x8005; day</td>
    </tr>
    <tr>
      <td style="text-align:left">ai</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x9879;&#x76EE;ID&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">export_date</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">
        <p>&#x5BFC;&#x51FA;&#x6570;&#x636E;&#x5317;&#x4EAC;&#x65F6;&#x95F4;&#xFF0C;&#x683C;&#x5F0F;&#x4E3A;
          yyyyMMddHHmm, &#x8868;&#x73B0;&#x8BF7;&#x6C42;&#x5BFC;&#x51FA;&#x54EA;&#x6BB5;&#x65F6;&#x95F4;&#x5185;&#x7684;&#x6570;&#x636E;&#xFF0C;&#x5206;&#x4E3A;&#x4EE5;&#x4E0B;&#x60C5;&#x51B5;&#xFF1A;</p>
        <ul>
          <li>&#x5F53; export_type &#x4E3A; day &#x65F6;&#xFF0C;&#x53EA;&#x4F1A;&#x622A;&#x53D6;
            export_date &#x4E2D; yyyyMMdd, &#x5176;&#x4F59;&#x5C06;&#x5FFD;&#x7565;&#x3002;</li>
          <li>&#x5F53; export_type &#x4E3A; hour &#x65F6;&#xFF0C;&#x53EA;&#x4F1A;&#x622A;&#x53D6;
            export_date &#x4E2D; yyyyMMddHH, &#x5176;&#x4F59;&#x5C06;&#x5FFD;&#x7565;&#x3002;</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">&#x67E5;&#x8BE2;&#x53C2;&#x6570;</th>
      <th style="text-align:left">&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x662F;&#x5426;&#x5FC5;&#x4F20;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">minutes</td>
      <td style="text-align:left">integer</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">
        <p>&#x94FE;&#x63A5;&#x5931;&#x6548;&#x65F6;&#x95F4;&#xFF0C;&#x5355;&#x4F4D;&#x4E3A;&#x5206;&#x949F;&#x3002;</p>
        <p>&#x6700;&#x5927;&#x503C;7&#x5929;&#x3002;</p>
        <p>&#x9ED8;&#x8BA4;&#x503C;&#xFF1A;5</p>
      </td>
    </tr>
  </tbody>
</table>
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
      <td style="text-align:left">status</td>
      <td style="text-align:left">
        <p>&#x5BFC;&#x51FA;&#x72B6;&#x6001;&#x3002;&#x53EF;&#x80FD;&#x503C;&#x4E3A;&#xFF1A;</p>
        <ul>
          <li>FINISHED&#xFF1A;&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x5B8C;&#x6210;&#xFF0C;&#x5BA2;&#x6237;&#x53EF;&#x4EE5;&#x4F7F;&#x7528;
            downloadLinks &#x4E2D;&#x7684;&#x94FE;&#x63A5;&#x8FDB;&#x884C;&#x6587;&#x4EF6;&#x4E0B;&#x8F7D;&#x3002;</li>
          <li>RUNNING&#xFF1A;&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x6B63;&#x5728;&#x8FD0;&#x884C;&#x3002;</li>
          <li>NOT_EXISTS&#xFF1A;&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x4E0D;&#x5B58;&#x5728;&#xFF0C;&#x8BF7;&#x68C0;&#x67E5;&#x662F;&#x5426;&#x5F00;&#x542F;&#x4E86;&#x5BFC;&#x51FA;&#x529F;&#x80FD;&#x5E76;&#x68C0;&#x67E5;&#x8BF7;&#x6C42;&#x65E5;&#x671F;&#x65F6;&#x95F4;&#x3002;</li>
          <li>ERROR&#xFF1A;&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x53D1;&#x751F;&#x9519;&#x8BEF;&#x3002;</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">downloadLinks</td>
      <td style="text-align:left">
        <p>&#x6587;&#x4EF6;&#x4E0B;&#x8F7D;&#x94FE;&#x63A5;&#x3002;</p>
        <p>&#x94FE;&#x63A5;&#x53EF;&#x80FD;&#x968F;&#x65F6;&#x8C03;&#x6574;&#xFF0C;&#x4E0D;&#x5E94;&#x4F7F;&#x7528;&#x94FE;&#x63A5;&#x4E2D;&#x7684;&#x4EFB;&#x4F55;&#x5185;&#x5BB9;&#x4F5C;&#x4E3A;&#x5904;&#x7406;&#x7A0B;&#x5E8F;&#x4F9D;&#x636E;&#xFF0C;&#x94FE;&#x63A5;&#x8FC7;&#x671F;&#x65F6;&#x95F4;&#x9ED8;&#x8BA4;&#x4E3A;5&#x5206;&#x949F;&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">exportType</td>
      <td style="text-align:left">&#x8868;&#x793A;&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x7C7B;&#x578B;&#xFF0C;&#x7531;&#x7528;&#x6237;&#x4F20;&#x5165;&#xFF0C;&#x670D;&#x52A1;&#x5668;&#x539F;&#x6837;&#x8FD4;&#x56DE;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">dataType</td>
      <td style="text-align:left">&#x8868;&#x793A;&#x5BFC;&#x51FA;&#x6570;&#x636E;&#x7C7B;&#x578B;&#xFF0C;&#x7531;&#x7528;&#x6237;&#x4F20;&#x5165;&#xFF0C;&#x670D;&#x52A1;&#x5668;&#x539F;&#x6837;&#x8FD4;&#x56DE;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">exportDate</td>
      <td style="text-align:left">&#x8868;&#x793A;&#x5BFC;&#x51FA;&#x6570;&#x636E;&#x65F6;&#x95F4;&#xFF0C;&#x7531;&#x7528;&#x6237;&#x4F20;&#x5165;&#xFF0C;&#x670D;&#x52A1;&#x5668;&#x6839;&#x636E;
        exportType &#x622A;&#x53D6;&#x540E;&#x8FD4;&#x56DE;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">exportVersion</td>
      <td style="text-align:left">&#x8868;&#x793A;&#x5BFC;&#x51FA;&#x6570;&#x636E;&#x7248;&#x672C;&#xFF0C;&#x5F53;&#x524D;&#x7248;&#x672C;&#x4E0B;&#x9ED8;&#x8BA4;&#x4E3A;
        v2&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">requestTime</td>
      <td style="text-align:left">&#x5BA2;&#x6237;&#x8BF7;&#x6C42;&#x53D1;&#x751F;&#x65F6;&#x670D;&#x52A1;&#x5668;&#x65F6;&#x95F4;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">errorMsg</td>
      <td style="text-align:left">&#x8BF7;&#x6C42;&#x53D1;&#x751F;&#x9519;&#x8BEF;&#x65F6;&#xFF0C;&#x670D;&#x52A1;&#x5668;&#x8FD4;&#x56DE;&#x7684;&#x9519;&#x8BEF;&#x4FE1;&#x606F;&#x3002;</td>
    </tr>
  </tbody>
</table>
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

