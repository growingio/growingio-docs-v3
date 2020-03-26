# 获取原始数据下载链接

## URL

[https://www.growingio.com/insights/{ai}/{date}.json](https://www.growingio.com/insights/{ai}/{date}.json)

## 请求类型

GET

## 请求头参数

公共头部请参考[公共请求头参数](../../authenticate.md)。

## 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |


| ai | string | 是 | 项目ID |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">date</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x662F;</th>
      <th style="text-align:left">
        <p>&#x6570;&#x636E;&#x65E5;&#x671F;</p>
        <p>&#x5929;&#x7EA7;&#x522B;&#x793A;&#x4F8B;&#xFF1A;20160520</p>
        <p>&#x5C0F;&#x65F6;&#x7EA7;&#x522B;&#x793A;&#x4F8B;&#xFF1A;20160502008</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| 查询参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">expire</th>
      <th style="text-align:left">integer</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x8FC7;&#x671F;&#x65F6;&#x95F4;&#xFF0C;&#x4EE5;&#x5206;&#x4E3A;&#x5355;&#x4F4D;</p>
        <p>&#x9ED8;&#x8BA4;&#x503C;&#xFF1A; 5</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="返回示例" %}
```text
{
  "status": "FINISHED",
  "downlinks": [
    "link1",
    "link2"
  ]
}
```

响应中的 status 字段，状态值有： 1. FINISHED 任务完成； 2. RUNNING 任务正在跑； 3. NOT\_EXISTS 任务不存在，可能是任务还没跑或者请求日期格式不对。

使用下载链接时，可以先检查 status 字段，为 FINISHED 时才拿 downlinks 进行下载。
{% endtab %}
{% endtabs %}

