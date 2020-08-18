# 概述

## 规格

| 是否付费 | 数据保留时间 | 导出延迟 | 导出格式 | 调用频率 |
| :--- | :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x662F;</th>
      <th style="text-align:left">&#x4ECE;&#x5F00;&#x901A;&#x4E4B;&#x65E5;&#x8D77;&#x4FDD;&#x7559;&#x6700;&#x8FD1;15&#x5929;</th>
      <th
      style="text-align:left">
        <p>&#x6309;&#x5C0F;&#x65F6;&#x5BFC;&#x51FA;&#xFF1A;</p>
        <p>&#x5E38;&#x89C4;&#x65F6;&#x6BB5;&#xFF1A;40&#x5206;&#x949F;</p>
        <p>23&#x70B9;-&#x6B21;&#x65E5;2&#x70B9;&#xFF1A;60&#x5206;&#x949F;</p>
        <p>&#x6309;&#x5929;&#x5BFC;&#x51FA;&#xFF1A;2-4&#x5C0F;&#x65F6;</p>
        </th>
        <th style="text-align:left">
          <p>gzip&#x538B;&#x7F29;&#x5305;&#x3002;</p>
          <p>&#x4EE5;&#x6BCF;64M&#x5927;&#x5C0F;&#x5206;&#x5305;&#x53D1;&#x9001;&#x3002;</p>
          <p>&#x5BFC;&#x51FA;&#x6570;&#x636E;&#x7686;&#x4E3A;csv&#x683C;&#x5F0F;&#xFF1A;</p>
          <ul>
            <li>&#x5206;&#x9694;&#x7B26;&#xFF1A; ,</li>
            <li>&#x5305;&#x56F4;&#x7B26;&#xFF1A;&quot;</li>
            <li>&#x8F6C;&#x4E49;&#x7B26;&#xFF1A;\</li>
          </ul>
        </th>
        <th style="text-align:left">&#x6BCF;&#x79D2;&#x6700;&#x591A;2&#x6B21;</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

{% hint style="info" %}
* 导出数据会有延迟，接口返回值status字段为FINISHED后，才会生成下载链接。
* 数据导出后表中所有时间相关字段都为[UTC](http://baike.baidu.com/link?url=T9ER87o8wd_ABq-oRrn839-Q2hxrV5WvIeQX2bJCOAWgne8C8BCw8yRWrISceZJEoR83GuIhdu0vSZFwzl4ngFrD7vUITsrlcY6U3Fj6lWCx7x0xWRTNDFOHkhJmnUW05hrb5df7vvz12EayMr_4b5QJZ1UcTs17ffae3wI18LNeF8j_4WpMZ_srcJHSXhpk)时间。
* 为了保证您的数据不出现中断，请您在导出时注意**失败重试**（重试间隔建议5分钟）
* 由于凌晨0点后平台会出现大量计算任务，建议天数据导出任务在早上六点后进行。
{% endhint %}

## 事件类型

原始数据导出API可导出的所有字段的事件分类如下：

{% hint style="info" %}
V2.0可导出字段的事件分类有10种。
{% endhint %}

| 事件大类 | 事件小类 |
| :--- | :--- |
| 无埋点事件 | visit、page、action、action\_tag |
| 埋点事件 | custom\_event（原custom\_attr）、pvar（新增）、evar（新增）、vstr（新增） |
| 广告相关 | ads\_track\_click、ads\_track\_activation |

