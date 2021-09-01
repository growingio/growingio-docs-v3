# HUAWEI Ads

渠道名称：HUAWEIAds\_app\_oCPC\(v1.2\)

适用场景：推广产品为Android应用，出价方式为oCPC

#### 一、投放流程简介

1. 前往[HUAWEI Ads平台](https://ads.huawei.com)完成开户流程
2. 转化跟踪接口功能需要邮件申请开通权限，将监测链接加入华为侧白名单。
3. 积累转化数据，要求有稳定的、实时的转化数据回传至广告平台（要求7天内累积达到30个转化量）
4. 广告主和服务商申请开通对应转化目标/版位的oCPC功能；
5. 开始投放，创建oCPC任务，启动oCPC功能

详情参考[HUAWEI Ads文档中心](https://developer.huawei.com/consumer/cn/doc/distribution/promotion/ads_ocpc03-0000001058468932)

#### 二、监测链接创建与使用

1. 在GIO平台，新建监测链接【推广APP】，填写信息，选择推广渠道：HUAWEIAds\_app\_oCPC\(v1.2\)，点击【确定】后，获取监测链接。

![](../../../.gitbook/assets/image%20%28162%29.png)

{% hint style="warning" %}
HUAWEI Ads 一个应用只支持一个监测链接。在HUAWEI Ads平台创建多个转化指标，也只需要使用同一条监测链接。
{% endhint %}

![](../../../.gitbook/assets/image%20%28154%29.png)

2. 在HUAWEI Ads平台新建转化指标，并保存

![](../../../.gitbook/assets/image%20%28157%29.png)

![](../../../.gitbook/assets/image%20%28160%29.png)

{% hint style="warning" %}
注意：必须添加ip,user\_agent,trace\_time,os\_version,device\_id，且不可修改转化跟踪的自定义名称。否则, 将无法进行渠道归因。
{% endhint %}

![](../../../.gitbook/assets/image%20%28168%29.png)

3.（可选）配置监测链接参数，用于广告效果多维度分析。建议配置：广告计划、广告任务、广告创意3个维度

{% hint style="warning" %}
注意：链接参数名与转化指标的自定义名称保持一致，否则无法接收数据
{% endhint %}

![](../../../.gitbook/assets/image%20%28166%29.png)

4. 在GIO平台，填写转化指标关联的回传地址、回传秘钥，点击【完成】。

![](../../../.gitbook/assets/image%20%28164%29.png)

![](../../../.gitbook/assets/image%20%28150%29.png)

