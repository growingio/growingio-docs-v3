# V3接口概述

## V3接口说明 <a id="tong-ji-shu-ju-dao-chu-fen-lei"></a>

V3接口与 [统计数据导出API](../statistics-api/) 区别主要是交互方式由同步改为异步。

V3接口适用于图表数据较大的场景，通过异步交互的方式，避免了客户端长期持有http连接的弊病。

V3接口还重新定义了url的规范，后续GrowingIO所有的Open API都将遵循这个新的规范。

V3接口目前还在持续补充，很快会覆盖现有的  [统计数据导出API](../statistics-api/) 。

## V3接口交互方式 <a id="tong-ji-shu-ju-dao-chu-fen-lei"></a>

![](../../../.gitbook/assets/image%20%28127%29.png)

## 统计数据V3接口导出分类 <a id="tong-ji-shu-ju-dao-chu-fen-lei"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x7EDF;&#x8BA1;&#x6570;&#x636E;&#x5BFC;&#x51FA;&#x5206;&#x7C7B;</th>
      <th
      style="text-align:left">&#x76F8;&#x5173;&#x63A5;&#x53E3;</th>
        <th style="text-align:left">&#x4F7F;&#x7528;&#x9650;&#x5236;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x4E8B;&#x4EF6;&#x5206;&#x6790;&#x4E0B;&#x8F7D;</td>
      <td style="text-align:left"><a href="definition/getevent.md">&#x200B;&#x83B7;&#x53D6;&#x4E8B;&#x4EF6;&#x5206;&#x6790;&#x6570;&#x636E;&#x200B;</a>
      </td>
      <td style="text-align:left">
        <ul>
          <li>&#x5355;&#x56FE;&#x4E0B;&#x8F7D;&#x6BCF;&#x79D2;&#x9650;&#x901F;2&#x6B21;</li>
          <li>&#x5355;&#x5F20;&#x56FE;&#x8868;&#x5355;&#x6B21;&#x4E0B;&#x8F7D;&#x6570;&#x636E;&#x91CF;&#x4E0A;&#x9650;&#x4E3A;20&#x4E07;&#x6761;</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x6F0F;&#x6597;&#x5206;&#x6790;&#x4E0B;&#x8F7D;</td>
      <td style="text-align:left"><a href="definition/getfunnel.md">&#x200B;&#x83B7;&#x53D6;&#x6F0F;&#x6597;&#x5206;&#x6790;&#x6570;&#x636E;&#x200B;</a>
      </td>
      <td style="text-align:left">&#x5355;&#x56FE;&#x4E0B;&#x8F7D;&#x6BCF;&#x79D2;&#x9650;&#x901F;2&#x6B21;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x7559;&#x5B58;&#x5206;&#x6790;&#x4E0B;&#x8F7D;</td>
      <td style="text-align:left"><a href="definition/getretention.md">&#x200B;&#x83B7;&#x53D6;&#x7559;&#x5B58;&#x5206;&#x6790;&#x6570;&#x636E;&#x200B;</a>
      </td>
      <td style="text-align:left">&#x5355;&#x56FE;&#x4E0B;&#x8F7D;&#x6BCF;&#x79D2;&#x9650;&#x901F;2&#x6B21;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x83B7;&#x53D6;&#x7528;&#x6237;&#x5206;&#x7FA4;&#x4E0B;&#x8F7D;&#x94FE;&#x63A5;</td>
      <td
      style="text-align:left"><a href="definition/get-segmentations.md">&#x83B7;&#x53D6;&#x7528;&#x6237;&#x5206;&#x7FA4;&#x7684;&#x4E0B;&#x8F7D;&#x94FE;&#x63A5;</a>
        </td>
        <td style="text-align:left">&#x4E0B;&#x8F7D;&#x6BCF;&#x79D2;&#x9650;&#x901F;2&#x6B21;</td>
    </tr>
  </tbody>
</table>## 注意事项 <a id="zhu-yi-shi-xiang"></a>

* 本章节中API 的 project\_uid（项目UID）、dashboard\_id（看板ID）、chart\_id（事件分析单图ID）、funnel\_id（漏斗分析单图ID）、retention\_id（留存分析单图ID） 字段，均可在项目页面url中找到，如："https://www.growingio.com/admin/projects/nxog09md/dashboard/YoX28w7R" 中的 "nxog09md" 和 "YoX28w7R" 分别是 project\_id 和dashboard\_id。
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



