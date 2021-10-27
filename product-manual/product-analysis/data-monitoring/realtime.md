---
description: 借助实时监控模板，您可以实时监控你的业务进程：多用于运营活动的数据监测场景。
---

# 实时

借助实时监控模板，您可以实时监控你的业务进程：例如你可以看到此时此刻产品使用人数，今天截止到此刻的人数，不同城市，投放渠道，平台的实时人数。您可以将实时监控模板（或基于您业务场景的实时看板）投放在公司大屏幕上，让公司所有人同步看到公司的业务进程。

![](<../../../.gitbook/assets/image (27).png>)

## 应用场景 <a href="2-ying-yong-chang-jing" id="2-ying-yong-chang-jing"></a>

如果你对一个具体的场景有实时监控需求，你可以创建实时图表去监控。基于不同角色，我们提供了6个使用场景，供您参考：

作为市场投放人员，在进行投放活动时，您可能投放了 广点通，头条2个渠道，您能及时发现头条超出预期，因此加大投放，广点通低于预期及时止损，调整运营策略。

![](<../../../.gitbook/assets/image (28).png>)

作为电商平台的CEO 或者运营总监，在做大型活动的时候，您会分别实时监控 安卓，iOS，WEB端的用户数，加购次数，人数，购买成功次数人数，金额。

![](https://firebasestorage.googleapis.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M2rhnIRdtpnYwQL2kvm%2Fuploads%2FSZXleSdUSGEz97PcFJIc%2Ffile.png?alt=media)

作为电商商品运营人员，您可以实时查看不同商品活动页面的浏览人数。如来自百度的活动页面实时用户数据。

![](https://firebasestorage.googleapis.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M2rhnIRdtpnYwQL2kvm%2Fuploads%2FgEsjzm30TWxfCKNZ26TO%2Ffile.png?alt=media)

作为OTO出行运营人员，您可以分地区实时监控未接单的出租司机在线人数，和发起订单的乘客人数，以便您能及时调整供需，保证供需平衡。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LTV7aPXLHT23TurbXjF-LTVA8sJ6DNy731AqKy5image.png)

作为SaaS市场负责人，或者负责增长的产品经理，您可以实时查看不同渠道带来的注册成功人数和安装SDK成功人数。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LTV7aPXLHT23TurbXjF-LTVACz4wpIE3ThJVCwQimage.png)

作为一名产品负责人，在做版本升级后，您可以实时查看新版本的表现。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LTV7aPXLHT23TurbXjF-LTVAHRjwVNRCKqWj8mLimage.png)

## 常见问题

#### 1. 此时此刻的活跃用户数是如何定义的？

过去5分钟浏览过产品页面的人数，每20秒刷新一次。即每20秒会对过去5分钟的浏览过产品页面的人数进行刷新。

#### 2. GrowingIO 爬虫规则会过滤实时看板中的数据？

会的，详情请见[爬虫预防](../../projectmange/projectmange/spider-rules.md)。

#### 3. 添加新实时单图的时候，为什么创建的新图暂无数据？

刚添加新单图时，实时图表数字为0，5分钟后进行刷新并计算，显示的数据5分钟之内的总数。

#### 4. 为什么创建的新图，有的维度或者维度值会没有数据？

如果某一个指标未被您组织内其他人创建成实时图表，那么这个指标会在创建图表之后5分钟展示数据。

如果某一个指标未被他人用某个维度值在实时图表中展示过，那么这个纬度值的指标会在5分钟后展示数据。若您的公司首次监控城市维度值= 深圳 的用户实时数据，那么深圳的用户数据会在五分后展示。
