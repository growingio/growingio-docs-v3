# V3接口概述

## V3接口说明 <a id="tong-ji-shu-ju-dao-chu-fen-lei"></a>

V3接口与 [统计数据导出API](../statistics-api/) 区别主要是交互方式由同步改为异步。

V3接口适用于图表数据较大的场景，通过异步交互的方式，避免了客户端长期持有http连接的弊病。

V3接口还重新定义了url的规范，后续GrowingIO所有的Open API都将遵循这个新的规范。

V3接口目前还在持续补充，很快会覆盖现有的 [统计数据导出API](../statistics-api/) 。

## V3接口交互方式 <a id="tong-ji-shu-ju-dao-chu-fen-lei"></a>

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28127%29.png)

## 统计数据V3接口导出分类 <a id="tong-ji-shu-ju-dao-chu-fen-lei"></a>

| 统计数据导出分类 | 相关接口 | 使用限制 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x4E8B;&#x4EF6;&#x5206;&#x6790;&#x4E0B;&#x8F7D;</th>
      <th style="text-align:left"><a href="definition/getevent.md">&#x200B;&#x83B7;&#x53D6;&#x4E8B;&#x4EF6;&#x5206;&#x6790;&#x6570;&#x636E;&#x200B;</a>
      </th>
      <th style="text-align:left">
        <ul>
          <li>&#x5355;&#x56FE;&#x4E0B;&#x8F7D;&#x6BCF;&#x79D2;&#x9650;&#x901F;2&#x6B21;</li>
          <li>&#x5355;&#x5F20;&#x56FE;&#x8868;&#x5355;&#x6B21;&#x4E0B;&#x8F7D;&#x6570;&#x636E;&#x91CF;&#x4E0A;&#x9650;&#x4E3A;20&#x4E07;&#x6761;</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

| 漏斗分析下载 | [​获取漏斗分析数据​](definition/getfunnel.md) | 单图下载每秒限速2次 |
| :--- | :--- | :--- |


| 留存分析下载 | [​获取留存分析数据​](definition/getretention.md) | 单图下载每秒限速2次 |
| :--- | :--- | :--- |


| 获取用户分群下载链接 | [获取用户分群的下载链接](definition/get-segmentations.md) | 下载每秒限速2次 |
| :--- | :--- | :--- |


* 本章节中API 的 project\_uid（项目UID）、dashboard\_id（看板ID）、chart\_id（事件分析单图ID）、funnel\_id（漏斗分析单图ID）、retention\_id（留存分析单图ID） 字段，均可在项目页面url中找到，如："[https://www.growingio.com/admin/projects/nxog09md/dashboard/YoX28w7R](https://www.growingio.com/admin/projects/nxog09md/dashboard/YoX28w7R)" 中的 "nxog09md" 和 "YoX28w7R" 分别是 project\_id 和dashboard\_id。
  * dashboard\_id获取方式
    * 在项目URL中获取；
    * 通过[获取看板列表](https://docs.growingio.com/docs/developer-manual/api-reference/statistics-api/definition/get-charts)API根据project\_id获取所有看板信息。
  * chart\_id、funnel\_id、retention\_id的获取方式
    * 在项目URL中获取；
    * 通过[获取看板中的图表信息](https://docs.growingio.com/docs/developer-manual/api-reference/statistics-api/definition/get-chartinfo)API，根据dashboard\_id获取当前看板的所有图表信息，返回的信息中会包含图表ID，图表类型等信息。
  * segmentation\_id的获取方式
    * 通过[获取分群列表](../statistics-api/definition/get-segm.md)；
    * 在项目URL中获取。
* 统计数据导出的延迟一般为 30 分钟，比如导出早上 8 点到 9 点之间的数据时，一般需要 9:30 才能统计完毕。另外，每天凌晨因为需要运行天级别的统计任务，此时前一天的统计数据大概有 3-4 小时的延迟，建议在早上6点后进行导出任务。

