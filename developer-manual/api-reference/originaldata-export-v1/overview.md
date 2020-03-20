# 概述

## 概述

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x662F;&#x5426;&#x4ED8;&#x8D39;</th>
      <th style="text-align:left">&#x6570;&#x636E;&#x4FDD;&#x7559;&#x65F6;&#x95F4;</th>
      <th style="text-align:left">&#x5BFC;&#x51FA;&#x5EF6;&#x8FDF;</th>
      <th style="text-align:left">&#x5BFC;&#x51FA;&#x683C;&#x5F0F;</th>
      <th style="text-align:left">&#x65F6;&#x95F4;</th>
      <th style="text-align:left">&#x8C03;&#x7528;&#x9891;&#x7387;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x5F00;&#x901A;&#x4E4B;&#x65E5;&#x8D77;&#x6700;&#x591A;15&#x5929;</td>
      <td
      style="text-align:left">
        <p>&#x5C0F;&#x65F6;&#x6570;&#x636E;&#xFF1A;30&#x5206;&#x949F;&#x3002;&#x4E3E;&#x4F8B;&#x8BF4;&#x660E;&#xFF1A;xxxx</p>
        <p>&#x5929;&#x6570;&#x636E;&#xFF1A;1-2&#x5C0F;&#x65F6;&#x3002;&#x5EFA;&#x8BAE;&#x65E9;&#x4E0A;&#x516D;&#x70B9;</p>
        </td>
        <td style="text-align:left">
          <p>gzip&#x538B;&#x7F29;&#x5305;&#x3002;</p>
          <p>&#x4EE5;&#x6BCF;64M&#x5927;&#x5C0F;&#x5206;&#x5305;&#x53D1;&#x9001;&#x3002;</p>
          <p></p>
        </td>
        <td style="text-align:left"><a href="http://baike.baidu.com/link?url=T9ER87o8wd_ABq-oRrn839-Q2hxrV5WvIeQX2bJCOAWgne8C8BCw8yRWrISceZJEoR83GuIhdu0vSZFwzl4ngFrD7vUITsrlcY6U3Fj6lWCx7x0xWRTNDFOHkhJmnUW05hrb5df7vvz12EayMr_4b5QJZ1UcTs17ffae3wI18LNeF8j_4WpMZ_srcJHSXhpk">UTC</a>&#x65F6;&#x95F4;</td>
        <td
        style="text-align:left">&#x6BCF;&#x79D2;&#x6700;&#x591A;2&#x6B21;</td>
    </tr>
  </tbody>
</table>原始数据导出为付费功能，且只能导出从开通之日起的原始数据，原始数据仅保留15天，请定期下载。数据导出一般延迟为 30 分钟，比如早上 8 点到 9 点之间的数据，一般 9:30 会准备好。每天凌晨因为需要运行天级别的统计任务，所以导出任务会延迟 1-2 小时，在导出数据时请判断接口返回的 `status` 字段 。

导出时数据以每 64M 为单位分包发送，导出数据默认采用 gzip 压缩。原始数据中所有时间字段均为 [UTC](http://baike.baidu.com/link?url=T9ER87o8wd_ABq-oRrn839-Q2hxrV5WvIeQX2bJCOAWgne8C8BCw8yRWrISceZJEoR83GuIhdu0vSZFwzl4ngFrD7vUITsrlcY6U3Fj6lWCx7x0xWRTNDFOHkhJmnUW05hrb5df7vvz12EayMr_4b5QJZ1UcTs17ffae3wI18LNeF8j_4WpMZ_srcJHSXhpk) 时间，并非中国时间；此处导出的压缩包名也是由 UTC 时间命名。

