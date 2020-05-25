# 广告相关字段

{% tabs %}
{% tab title="ads\_track\_activation" %}
| 列名 | 字段名称 | 字段格式 | 字段说明 | 值（example） |
| :--- | :--- | :--- | :--- | :--- |
| userId | 用户ID | string\(36\) | 针对单个用户生成的唯一id | 例如，web网站生成一个有效期三年的cookie值，App 则为机器唯一标识码 |
| idfa | idfa | string\(32\) | iOS系统中的设备标志 | CCD6E1CD-8C4B-40CB-8A62-4BBC7AFE07D6 |
| imei | imei | string\(32\) | 安卓系统中的设备唯一标志 | 10bc955ac2a67ed3 |
| uuid | uuid | string\(32\) | GIO在设备中成的设备标志ID | 略。即将下线，可忽视此字段 |
| androidid | androidid | string\(32\) | 安卓系统中的设备唯一标志 | 9774d56d682e549c |
| ip | ip | string\(64\) | 用户IP地址 | 10.10.0.21 |
| useragent | 用户客户端UA信息 | string\(1024\) | 简称ua，例如浏览器信息或者移动设备信息 | 略 |
| platform | 数据来源平台 | string\(10\) | 区分该数据属于哪个平台 | web, android, ios |
| osversion | 系统版本 | string\(50\) | 用户使用的设备系统版本 | ios 9.1.3 |
| sendTime | 发送时间 | bigint | 数据发送过来的时间 | 略 |
| link\_id | 监测链接ID | string\(10\) | 监测链接ID | o3ox2dV |
| campaign\_id | 推广活动ID | string\(10\) | 推广活动ID | 略 |
| channel\_id | 目标渠道ID | string\(20\) | 目标渠道ID | 略 |
| link\_name | 链接名称 | string | 链接名称 | 测试链接 |
| campaign\_name | 活动名称 | string | 活动名称 | 双十一推广 |
| channel\_name | 渠道名称 | string | 渠道名称 | 今日头条 |
{% endtab %}

{% tab title="ads\_track\_click" %}
| 列名 | 字段名称 | 字段格式 | 字段说明 | 值（example） |
| :--- | :--- | :--- | :--- | :--- |
| idfa | idfa | string\(32\) | iOS系统中的设备标志 | CCD6E1CD-8C4B-40CB-8A62-4BBC7AFE07D6 |
| imei | imei | string\(32\) | 安卓系统中的设备唯一标志 | 10bc955ac2a67ed3 |
| uuid | uuid | string\(32\) | GIO在设备中成的设备标志ID | 略。即将下线，可忽视此字段 |
| androidid | androidid | string\(32\) | 安卓系统中的设备唯一标志 | 9774d56d682e549c |
| ip | ip | string\(64\) | 用户IP地址 | 10.10.0.21 |
| useragent | 用户客户端UA信息 | string\(1024\) | 简称ua，例如浏览器信息或者移动设备信息 | 略 |
| platform | 数据来源平台 | string\(10\) | 区分该数据属于哪个平台 | web, android, ios |
| eventTime | 事件发生时间 | bigint | 事件实际发生的时间 | ​ |
| link\_id | 监测链接ID | string\(10\) | 监测链接ID | o3ox2dV |
| campaign\_id | 推广活动ID | string\(10\) | 推广活动ID | 略 |
| channel\_id | 目标渠道ID | string\(20\) | 目标渠道ID | 略 |
| link\_name | 链接名称 | string | 链接名称 | 测试链接 |
| campaign\_name | 活动名称 | string | 活动名称 | 双十一推广 |
| channel\_name | 渠道名称 | string | 渠道名称 | 今日头条 |
{% endtab %}
{% endtabs %}

