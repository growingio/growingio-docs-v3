---
description: 通过用户标签 ID，下载用户列表及对应标签值。
---

# 获取用户标签的下载链接

{% hint style="warning" %}
用户标签为灰度功能，如需体验试用，请联系客户经理 。
{% endhint %}

## URL <a id="url"></a>

[https://www.growingio.com/v3/exporter/projects/{project\_uid}/tags/{tag\_id}/users](https://www.growingio.com/v3/exporter/projects/{project_uid}/tags/{tag_id}/users)

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
      <td style="text-align:left">tag_id</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">
        <p>&#x7528;&#x6237;&#x6807;&#x7B7E;ID</p>
        <p>&#x8BE6;&#x7EC6;&#x8BF7;&#x53C2;&#x8003;&#xFF1A;<a href="../overview.md#tong-ji-shu-ju-dao-chu-fen-lei-2">&#x6982;&#x8FF0;</a> tag_id&#x7684;&#x83B7;&#x53D6;&#x65B9;&#x5F0F;</p>
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

<table>
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
      <td style="text-align:left">expire</td>
      <td style="text-align:left">integer</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">
        <p>&#x4E0B;&#x8F7D;&#x94FE;&#x63A5;&#x5931;&#x6548;&#x65F6;&#x95F4;&#xFF0C;&#x5355;&#x4F4D;&#x4E3A;&#x5206;&#x949F;&#x3002;&#x6700;&#x957F;&#x65F6;&#x95F4;&#x4E3A;7&#x5929;&#x3002;</p>
        <p>&#x9ED8;&#x8BA4;&#x503C;&#xFF1A;5</p>
        <p>&#x5907;&#x6CE8;&#xFF1A;&#x82E5;&#x8BF7;&#x6C42;&#x5DF2;&#x8FD4;&#x56DE;&#x4E86;&#x94FE;&#x63A5;&#x7ED3;&#x679C;&#xFF0C;&#x5219;&#x5728;&#x94FE;&#x63A5;&#x5931;&#x6548;&#x671F;&#x5185;&#xFF0C;&#x518D;&#x91CD;&#x65B0;&#x4F20;&#x5165;expire&#x5B57;&#x6BB5;&#x4E0D;&#x4F1A;&#x66F4;&#x65B0;&#x94FE;&#x63A5;&#x7684;&#x5931;&#x6548;&#x65F6;&#x95F4;&#x3002;</p>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="响应参数" %}
<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x53C2;&#x6570;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">id</td>
      <td style="text-align:left">&#x968F;&#x673A;&#x7684;ID&#x5B57;&#x7B26;&#x4E32;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">status</td>
      <td style="text-align:left">
        <p></p>
        <p>&#x5BFC;&#x51FA;&#x72B6;&#x6001;&#x3002;</p>
        <ul>
          <li>done&#xFF1A;&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x5B8C;&#x6210;&#xFF0C;&#x5BA2;&#x6237;&#x53EF;&#x4EE5;&#x4F7F;&#x7528;
            downloadLinks &#x4E2D;&#x7684;&#x94FE;&#x63A5;&#x8FDB;&#x884C;&#x6587;&#x4EF6;&#x4E0B;&#x8F7D;&#x3002;</li>
          <li>doing&#xFF1A;&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x6B63;&#x5728;&#x8FD0;&#x884C;&#x3002;</li>
          <li>failed&#xFF1A;&#x5BFC;&#x51FA;&#x4EFB;&#x52A1;&#x53D1;&#x751F;&#x9519;&#x8BEF;&#x3002;</li>
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
      <td style="text-align:left">errorMsg</td>
      <td style="text-align:left">
        <p>&#x8BF7;&#x6C42;&#x53D1;&#x751F;&#x9519;&#x8BEF;&#x65F6;&#xFF0C;&#x670D;&#x52A1;&#x5668;&#x8FD4;&#x56DE;&#x7684;&#x9519;&#x8BEF;&#x4FE1;&#x606F;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;</p>
        <p>1&#x3001;&#x8BF7;&#x6C42;&#x53C2;&#x6570;&#x4E0D;&#x5408;&#x6CD5;&#xFF0C;{&#x4E0D;&#x5408;&#x6CD5;&#x503C;}</p>
        <p>2&#x3001;&#x8FC7;&#x671F;&#x65F6;&#x95F4;&#x5E94;&#x5C0F;&#x4E8E;7&#x5929;</p>
        <p>3&#x3001;&#x4E0B;&#x8F7D;&#x51FA;&#x9519;&#xFF0C;&#x8BF7;&#x60A8;&#x7A0D;&#x540E;&#x91CD;&#x8BD5;</p>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="请求示例" %}
```text
https://www.growingio.com/v3/exporter/projects/nxog09md/tags/5rREn4PL/users
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

