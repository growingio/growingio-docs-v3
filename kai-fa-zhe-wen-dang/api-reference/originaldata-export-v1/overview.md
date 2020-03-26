# 概述

## 概述

| 是否付费 | 数据保留时间 | 导出延迟 | 导出格式 | 时间 | 调用频率 |
| :--- | :--- | :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x662F;</th>
      <th style="text-align:left">&#x5F00;&#x901A;&#x4E4B;&#x65E5;&#x8D77;&#x6700;&#x591A;15&#x5929;</th>
      <th
      style="text-align:left">
        <p>&#x5C0F;&#x65F6;&#x6570;&#x636E;&#xFF1A;30&#x5206;&#x949F;&#x3002;&#x4E3E;&#x4F8B;&#x8BF4;&#x660E;&#xFF1A;xxxx</p>
        <p>&#x5929;&#x6570;&#x636E;&#xFF1A;1-2&#x5C0F;&#x65F6;&#x3002;&#x5EFA;&#x8BAE;&#x65E9;&#x4E0A;&#x516D;&#x70B9;</p>
        </th>
        <th style="text-align:left">
          <p>gzip&#x538B;&#x7F29;&#x5305;&#x3002;</p>
          <p>&#x4EE5;&#x6BCF;64M&#x5927;&#x5C0F;&#x5206;&#x5305;&#x53D1;&#x9001;&#x3002;</p>
        </th>
        <th style="text-align:left"><a href="http://baike.baidu.com/link?url=T9ER87o8wd_ABq-oRrn839-Q2hxrV5WvIeQX2bJCOAWgne8C8BCw8yRWrISceZJEoR83GuIhdu0vSZFwzl4ngFrD7vUITsrlcY6U3Fj6lWCx7x0xWRTNDFOHkhJmnUW05hrb5df7vvz12EayMr_4b5QJZ1UcTs17ffae3wI18LNeF8j_4WpMZ_srcJHSXhpk">UTC</a>&#x65F6;&#x95F4;</th>
        <th
        style="text-align:left">&#x6BCF;&#x79D2;&#x6700;&#x591A;2&#x6B21;</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>导出时数据以每 64M 为单位分包发送，导出数据默认采用 gzip 压缩。原始数据中所有时间字段均为 [UTC](http://baike.baidu.com/link?url=T9ER87o8wd_ABq-oRrn839-Q2hxrV5WvIeQX2bJCOAWgne8C8BCw8yRWrISceZJEoR83GuIhdu0vSZFwzl4ngFrD7vUITsrlcY6U3Fj6lWCx7x0xWRTNDFOHkhJmnUW05hrb5df7vvz12EayMr_4b5QJZ1UcTs17ffae3wI18LNeF8j_4WpMZ_srcJHSXhpk) 时间，并非中国时间；此处导出的压缩包名也是由 UTC 时间命名。

