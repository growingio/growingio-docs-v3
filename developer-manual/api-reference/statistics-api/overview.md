# 概述

## 统计数据导出分类

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
      <td style="text-align:left">&#x770B;&#x677F;&#x6570;&#x636E;&#x4FE1;&#x606F;</td>
      <td style="text-align:left">
        <p><a href="definition/get-charts.md">&#x83B7;&#x53D6;&#x770B;&#x677F;&#x5217;&#x8868;</a>
        </p>
        <p><a href="definition/get-chartinfo.md">&#x83B7;&#x53D6;&#x770B;&#x677F;&#x4E2D;&#x7684;&#x56FE;&#x8868;&#x4FE1;&#x606F;</a>
        </p>
      </td>
      <td style="text-align:left">&#x65E0;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x4E8B;&#x4EF6;&#x5206;&#x6790;&#x4E0B;&#x8F7D;</td>
      <td style="text-align:left"><a href="definition/getevent.md">&#x83B7;&#x53D6;&#x4E8B;&#x4EF6;&#x5206;&#x6790;&#x6570;&#x636E;</a>
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
      <td style="text-align:left"><a href="definition/getfunnel.md">&#x83B7;&#x53D6;&#x6F0F;&#x6597;&#x5206;&#x6790;&#x6570;&#x636E;</a>
      </td>
      <td style="text-align:left">&#x5355;&#x56FE;&#x4E0B;&#x8F7D;&#x6BCF;&#x79D2;&#x9650;&#x901F;2&#x6B21;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x7559;&#x5B58;&#x5206;&#x6790;&#x4E0B;&#x8F7D;</td>
      <td style="text-align:left"><a href="definition/get-retention.md">&#x83B7;&#x53D6;&#x7559;&#x5B58;&#x5206;&#x6790;&#x6570;&#x636E;</a>
      </td>
      <td style="text-align:left">&#x5355;&#x56FE;&#x4E0B;&#x8F7D;&#x6BCF;&#x79D2;&#x9650;&#x901F;2&#x6B21;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x5206;&#x7FA4;&#x4E0B;&#x8F7D;</td>
      <td style="text-align:left">
        <p><a href="definition/get-segm.md">&#x83B7;&#x53D6;&#x5206;&#x7FA4;&#x5217;&#x8868;</a>
        </p>
        <p><a href="definition/get-segmentations.md">&#x83B7;&#x53D6;&#x7279;&#x5B9A;&#x5206;&#x7FA4;&#x7684;&#x7528;&#x6237;&#x5217;&#x8868;</a>
        </p>
      </td>
      <td style="text-align:left">
        <ul>
          <li>&#x5355;&#x56FE;&#x4E0B;&#x8F7D;&#x6BCF;&#x79D2;&#x9650;&#x901F;2&#x6B21;&#xFF1B;</li>
          <li>&#x5355;&#x5F20;&#x56FE;&#x8868;&#x5355;&#x6B21;&#x4E0B;&#x8F7D;&#x6570;&#x636E;&#x91CF;&#x4E0A;&#x9650;&#x4E3A;20&#x4E07;&#x6761;&#xFF1B;</li>
          <li>&#x5206;&#x7FA4;&#x7528;&#x6237;&#x8F83;&#x591A;&#x65F6;&#x5EFA;&#x8BAE;&#x964D;&#x4F4E;&#x4E0B;&#x8F7D;&#x9891;&#x6B21;&#x3002;</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x89C4;&#x5219;&#x903B;&#x8F91;</td>
      <td style="text-align:left"><a href="definition/get-auto.md">&#x83B7;&#x53D6;&#x5708;&#x9009;&#x5143;&#x7D20;&#x5B9A;&#x4E49;</a>
      </td>
      <td style="text-align:left">&#x65E0;</td>
    </tr>
  </tbody>
</table>## 注意事项

* 本章节中API 的 project\_uid（项目UID）、dashboard\_id（看板ID）、chart\_id（事件分析单图ID）、funnel\_id（漏斗分析单图ID）、retention\_id（留存分析单图ID）、segmentation\_id（分群ID） 字段，均可在项目页面url中找到，如："https://www.growingio.com/admin/projects/nxog09md/dashboard/YoX28w7R" 中的 "nxog09md" 和 "YoX28w7R" 分别是 project\_id 和dashboard\_id。
  * dashboard\_id获取方式
    * 在项目URL中获取；
    * 通过[获取看板列表](definition/get-charts.md)API根据project\_id获取所有看板信息。
  * chart\_id、funnel\_id、retention\_id的获取方式
    * 在项目URL中获取；
    * 通过[获取看板中的图表信息](definition/get-chartinfo.md)API，根据dashboard\_id获取当前看板的所有图表信息，返回的信息中会包含图表ID，图表类型等信息。
* 统计数据导出的延迟一般为 30 分钟，比如导出早上 8 点到 9 点之间的数据时，一般需要 9:30 才能统计完毕。另外，每天凌晨因为需要运行天级别的统计任务，此时前一天的统计数据大概有 3-4 小时的延迟，建议在早上6点后进行导出任务。

