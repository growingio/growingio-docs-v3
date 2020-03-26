# 获取用户分群的下载链接

## URL <a id="url"></a>

[https://www.growingio.com/v3/exporter/projects/{project\_uid}/segmentations/{segmentation\_id}/users](https://www.growingio.com/v3/exporter/projects/{project_uid}/segmentations/{segmentation_id}/users)

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
| segmentation\_id | string | 是 | 用户分群ID，可使用[获取分群列表API](../../statistics-api/definition/get-segm.md)获取。 |
| project\_uid | string | 是 | 项目UID。 |

| 查询参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">expire</th>
      <th style="text-align:left">integer</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x4E0B;&#x8F7D;&#x94FE;&#x63A5;&#x5931;&#x6548;&#x65F6;&#x95F4;&#xFF0C;&#x5355;&#x4F4D;&#x4E3A;&#x5206;&#x949F;&#x3002;&#x6700;&#x957F;&#x65F6;&#x95F4;&#x4E3A;7&#x5929;&#x3002;</p>
        <p>&#x9ED8;&#x8BA4;&#x503C;&#xFF1A;5</p>
        <p>&#x5907;&#x6CE8;&#xFF1A;&#x82E5;&#x8BF7;&#x6C42;&#x5DF2;&#x8FD4;&#x56DE;&#x4E86;&#x94FE;&#x63A5;&#x7ED3;&#x679C;&#xFF0C;&#x5219;&#x5728;&#x94FE;&#x63A5;&#x5931;&#x6548;&#x671F;&#x5185;&#xFF0C;&#x518D;&#x91CD;&#x65B0;&#x4F20;&#x5165;expire&#x5B57;&#x6BB5;&#x4E0D;&#x4F1A;&#x66F4;&#x65B0;&#x94FE;&#x63A5;&#x7684;&#x5931;&#x6548;&#x65F6;&#x95F4;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">parameters</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x901A;&#x8FC7;&#x7528;&#x6237;&#x53D8;&#x91CF;&#xFF08;&#x767B;&#x5F55;&#x7528;&#x6237;&#x53D8;&#x91CF;&#x548C;&#x8BBF;&#x95EE;&#x7528;&#x6237;&#x53D8;&#x91CF;&#xFF09;&#x5BF9;&#x5206;&#x7FA4;&#x8FDB;&#x884C;&#x4E8C;&#x6B21;&#x7B5B;&#x9009;&#xFF0C;&#x6B64;&#x5904;&#x4F20;&#x53D8;&#x91CF;&#x5B57;&#x6BB5;&#xFF0C;&#x4E0D;&#x4F20;&#x65F6;&#x4E0D;&#x8FDB;&#x884C;&#x4E8C;&#x6B21;&#x7B5B;&#x9009;&#x3002;</p>
        <p>&#x53D8;&#x91CF;&#x83B7;&#x53D6;&#x6709;&#x4E24;&#x79CD;&#x9014;&#x5F84;&#xFF1A;</p>
        <ol>
          <li><a href="../../project-manage/get-loginvar.md">&#x83B7;&#x53D6;&#x767B;&#x5F55;&#x7528;&#x6237;&#x53D8;&#x91CF;API</a>
          </li>
          <li>&#x5728;GrowingIO&#x5E73;&#x53F0;&#x83B7;&#x53D6;&#xFF0C;&#x8BF7;&#x53C2;&#x8003;
            <a
            href="../../../../chan-pin-shi-yong-wen-dang-fen-ban/shu-ju-zhong-xin/shu-ju-guan-li/user.md">&#x7528;&#x6237;&#x53D8;&#x91CF;</a>
          </li>
        </ol>
        <p>&#x4F20;&#x53C2;&#x683C;&#x5F0F;&#xFF1A;<b>&#x591A;&#x4E2A;&#x53C2;&#x6570;&#x9700;&#x7528;&#x82F1;&#x6587;&#x9017;&#x53F7;&#x94FE;&#x63A5;</b>
        </p>
        <p><b>&#x793A;&#x4F8B;:</b> parameters=open_id,role</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="响应参数" %}
| 参数 | 说明 |
| :--- | :--- |


| id | 随机的ID字符串。 |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">status</th>
      <th style="text-align:left">
        <p>&#x5BFC;&#x51FA;&#x72B6;&#x6001;&#x3002;</p>
        <ul>
          <li>done&#xFF1A;&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x5B8C;&#x6210;&#xFF0C;&#x5BA2;&#x6237;&#x53EF;&#x4EE5;&#x4F7F;&#x7528;
            downloadLinks &#x4E2D;&#x7684;&#x94FE;&#x63A5;&#x8FDB;&#x884C;&#x6587;&#x4EF6;&#x4E0B;&#x8F7D;&#x3002;</li>
          <li>doing&#xFF1A;&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x6B63;&#x5728;&#x8FD0;&#x884C;&#x3002;</li>
          <li>failed&#xFF1A;&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x53D1;&#x751F;&#x9519;&#x8BEF;&#x3002;</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
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
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">errorMsg</th>
      <th style="text-align:left">
        <p>&#x8BF7;&#x6C42;&#x53D1;&#x751F;&#x9519;&#x8BEF;&#x65F6;&#xFF0C;&#x670D;&#x52A1;&#x5668;&#x8FD4;&#x56DE;&#x7684;&#x9519;&#x8BEF;&#x4FE1;&#x606F;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;</p>
        <p>1&#x3001;&#x8BF7;&#x6C42;&#x53C2;&#x6570;&#x4E0D;&#x5408;&#x6CD5;&#xFF0C;{&#x4E0D;&#x5408;&#x6CD5;&#x503C;}</p>
        <p>2&#x3001;&#x8FC7;&#x671F;&#x65F6;&#x95F4;&#x5E94;&#x5C0F;&#x4E8E;7&#x5929;</p>
        <p>3&#x3001;&#x4E0B;&#x8F7D;&#x51FA;&#x9519;&#xFF0C;&#x8BF7;&#x60A8;&#x7A0D;&#x540E;&#x91CD;&#x8BD5;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="请求示例" %}
```text
https://www.growingio.com/v3/exporter/projects/nxog09md/segmentations/nP2lpkX9/users?expire=5&parameters=user_name,project
```
{% endtab %}

{% tab title="响应示例" %}
```text
{
  "id":"随机ID",
  "status": "done",
  "downloadLinks": ["https://gta.growingio.com/buckets/segment-download-jobs/20191226/195ae9eb-4a89-457b-b8ce-fb8ca2539131/20191212-20191225_%E6%B8%A0%E9%81%93%E8%AF%84%E4%BC%B0.csv?sign=R9y9atNVIDqU74q34BX%2FgPJI%2Bo22stsGPWZHJ7Tin%2FE%3D&expires=1577344409140"],
  "errorMsg": ""
}
```

针对该下载地址，可以直接访问并下载文件。文件地址中包含过期的有效时间。
{% endtab %}
{% endtabs %}

## 数据处理建议

数据处理建议请参考[导出数据处理建议](../../originaldata-export-v2/exportsuggest.md)。

