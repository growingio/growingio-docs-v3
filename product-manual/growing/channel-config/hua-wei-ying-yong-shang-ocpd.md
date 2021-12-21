---
description: (华为内测功能)
---

# 华为应用商oCPD



一、投放说明：

华为应用商店oCPD功能目前为定向邀请功能，未开通的应用不能使用。如有疑问请通过客服、邮箱或者在线工单系统与华为应用商店相关人员进行联系咨询。

oCPD是一种任务投放形式，支持广告主以转化成本（如激活、注册）为目标的智能出价。使用oCPD之前，需要广告主把目标转化数据进行归因后通过Marketing API回传。投放平台基于自有数据分析已转化用户特征，帮助广告主找到与其已转化用户相似的人群作为目标投放受众。广告主无需再针对不同的人群尝试性的进行出价调整，定向和出价过程由oCPD算法自动完成。

在广告主使用Marketing API回传转化数据之前，需要完成两个准备工作：创建数据源和API客户端。

详情参考[华为官网文档](https://developer.huawei.com/consumer/cn/doc/distribution/promotion/ocpd-introduction-0000001147372698?preview=1)

&#x20;

完成设置后，请记录您的客户端ID和密钥。示例如下：

![](broken-reference)

二、创建监测链接

1 创建路径：

&#x20; 获客分析→获客追踪→新建监测链接

&#x20; 推广渠道：华为应用商店oCPD

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpsyZ5kSi.jpg)&#x20;

2 进行授权：填写正确的id及密钥后点击授权

&#x20; Client\_id为上文中的客户端id

&#x20; Client\_secret为上文中的密钥

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpshPzNVm.jpg)&#x20;

3 链接创建成功

&#x20; Growing IO会自动生成一条点击监测链接和一条曝光监测链接

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpsGN2XG7.jpg)&#x20;

三、投放建议

华为应用商店支持4种事件监测，示例如下：

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpskPPJHP.jpg)&#x20;

因oCPD是以下载为结算单元，所以推荐您把曝光监测链接投放在曝光位，点击监测链接投放到下载位，即：

曝光：曝光监测链接

点击:  置空

下载：点击监测链接

安装:  应用安装链接

当您需要区分更细的维度，可以通过链接维度参数的方式来区分，将 hw\_action\_type设置为扩展维度。映射方案如下：

（点击、下载、安装使用同一个监测链接即系统生成的点击监测链接）

曝光：曝光监测链接

点击：点击监测链接

下载：点击监测链接

安装：点击监测链接

&#x20;

但这种配置会造成获客分析首页的点击数据差异，展示点击数会高于实际数值，需要您在推广详细中根据维度来拆分各个事件数据。

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpsqQuMbs.jpg)&#x20;

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wps3cRyPN.jpg)
