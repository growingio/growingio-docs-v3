# 获取分布分析数据

## URL <a id="url"></a>

[https://www.growingio.com/v3/exporter/projects/{project\_uid}/frequencies/{frequency\_id}](https://www.growingio.com/v3/exporter/projects/{project_uid}/frequencies/{frequency_id})

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
      <td style="text-align:left">frequency_id</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">
        <p>&#x5206;&#x5E03;&#x5206;&#x6790;&#x5355;&#x56FE;ID</p>
        <p>&#x8BE6;&#x7EC6;&#x8BF7;&#x53C2;&#x8003;&#xFF1A;<a href="../overview.md#tong-ji-shu-ju-dao-chu-fen-lei-2">&#x6982;&#x8FF0;</a> frequency_id&#x7684;&#x83B7;&#x53D6;&#x65B9;&#x5F0F;</p>
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
      <td style="text-align:left">split</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">
        <p>&#x9002;&#x7528;&#x56FE;&#x8868;&#xFF1A;&#x5206;&#x5E03;</p>
        <p>&#x5206;&#x5E03;&#x533A;&#x95F4;</p>
        <ul>
          <li>10&#xFF1A;10&#x5C42;&#x4EE5;&#x5185;</li>
          <li>15&#xFF1A;15&#x5C42;&#x4EE5;&#x5185;</li>
          <li>25&#xFF1A;25&#x5C42;&#x4EE5;&#x5185;</li>
          <li>[integer1&#xFF0C;integer2..]&#xFF1A;&#x81EA;&#x5B9A;&#x4E49;&#x5206;&#x5C42;</li>
        </ul>
        <p>&#x9ED8;&#x8BA4;&#x503C;&#xFF1A;&#x4EE5;&#x56FE;&#x8868;&#x914D;&#x7F6E;&#x4E3A;&#x51C6;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">interval</td>
      <td style="text-align:left">integer</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">
        <p>&#x9002;&#x7528;&#x56FE;&#x8868;&#xFF1A;&#x8D8B;&#x52BF;</p>
        <p>&#x6570;&#x636E;&#x7C92;&#x5EA6;&#xFF0C;&#x5355;&#x4F4D;&#x4E3A;&#x6BEB;&#x79D2;&#x3002;</p>
        <ul>
          <li>86400000(1&#x5929;)</li>
          <li>604800000(1&#x5468;)</li>
          <li>2592000000(1&#x6708;)</li>
        </ul>
        <p>&#x9ED8;&#x8BA4;&#x503C;&#xFF1A;&#x4EE5;&#x56FE;&#x8868;&#x914D;&#x7F6E;&#x4E3A;&#x51C6;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">statistic</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">
        <p>&#x9002;&#x7528;&#x56FE;&#x8868;&#xFF1A;&#x8D8B;&#x52BF;&#xFF08;&#x542B;&#x7EF4;&#x5EA6;&#x5BF9;&#x6BD4;/&#x7528;&#x6237;&#x5BF9;&#x6BD4;&#xFF09;</p>
        <p>&#x7EDF;&#x8BA1;&#x7C7B;&#x578B;</p>
        <ul>
          <li>max&#xFF1A;&#x6700;&#x5927;&#x503C;</li>
          <li>min&#xFF1A;&#x6700;&#x5C0F;&#x503C;</li>
          <li>avg&#xFF1A;&#x5E73;&#x5747;&#x503C;</li>
          <li>median&#xFF1A;&#x4E2D;&#x4F4D;&#x6570;</li>
          <li>0.25&#xFF1A;25&#x5206;&#x4F4D;&#x6570;</li>
          <li>0.75&#xFF1A;75&#x5206;&#x4F4D;&#x6570;</li>
        </ul>
        <p>&#x9ED8;&#x8BA4;&#x503C;&#xFF1A;&#x4EE5;&#x56FE;&#x8868;&#x914D;&#x7F6E;&#x4E3A;&#x51C6;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">startTime</td>
      <td style="text-align:left">integer</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">
        <p>&#x6570;&#x636E;&#x8D77;&#x59CB;&#x65F6;&#x95F4;&#xFF0C;unix&#x6BEB;&#x79D2;&#x65F6;&#x95F4;&#x6233;&#x3002;</p>
        <p>&#x9700;&#x4E0E;endTime&#x4E00;&#x8D77;&#x4F7F;&#x7528;&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">endTime</td>
      <td style="text-align:left">integer</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">
        <p>&#x6570;&#x636E;&#x7ED3;&#x675F;&#x65F6;&#x95F4;&#xFF0C;unix&#x6BEB;&#x79D2;&#x65F6;&#x95F4;&#x6233;&#x3002;</p>
        <p>&#x9700;&#x4E0E;startTime&#x4E00;&#x8D77;&#x4F7F;&#x7528;&#x3002;</p>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="返回示例" %}
未导出完成：

```text
{"id":"随机ID","status":"doing"}
```

导出完成：

```text

```
{% endtab %}
{% endtabs %}

