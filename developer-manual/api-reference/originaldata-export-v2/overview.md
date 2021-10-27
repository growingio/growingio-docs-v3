# 概述

## 规格

| 是否付费 | 数据保留时间 | 导出延迟 | 导出格式 | 调用频率 |
| ---- | ------ | ---- | ---- | ---- |

| 是 | 从开通之日起保留最近15天 | <p>按小时导出：</p><p>常规时段：40分钟</p><p>23点-次日2点：60分钟</p><p>按天导出：2-4小时</p> | <p>gzip压缩包。</p><p>以每64M大小分包发送。</p><p>导出数据皆为csv格式：</p><ul><li>分隔符： ,</li><li>包围符："</li><li>转义符：\</li></ul> | 每秒最多2次 |
| - | ------------- | ------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------- | ------ |

{% hint style="info" %}
* 导出数据会有延迟，接口返回值status字段为FINISHED后，才会生成下载链接。
* 数据导出后表中所有时间相关字段都为[UTC](http://baike.baidu.com/link?url=T9ER87o8wd\_ABq-oRrn839-Q2hxrV5WvIeQX2bJCOAWgne8C8BCw8yRWrISceZJEoR83GuIhdu0vSZFwzl4ngFrD7vUITsrlcY6U3Fj6lWCx7x0xWRTNDFOHkhJmnUW05hrb5df7vvz12EayMr\_4b5QJZ1UcTs17ffae3wI18LNeF8j\_4WpMZ\_srcJHSXhpk)时间。
* 为了保证您的数据不出现中断，请您在导出时注意**失败重试**（重试间隔建议5分钟）
* 由于凌晨0点后平台会出现大量计算任务，建议天数据导出任务在早上六点后进行。
{% endhint %}

## 事件类型

原始数据导出API可导出的所有字段的事件分类如下：

{% hint style="info" %}
V2.0可导出字段的事件分类有10种。
{% endhint %}

| 事件大类  | 事件小类                                                    |
| ----- | ------------------------------------------------------- |
| 无埋点事件 | visit、page、action、action\_tag                           |
| 埋点事件  | custom\_event（原custom\_attr）、pvar（新增）、evar（新增）、vstr（新增） |
| 广告相关  | ads\_track\_click、ads\_track\_activation                |
