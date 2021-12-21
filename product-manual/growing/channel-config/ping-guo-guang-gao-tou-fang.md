# 苹果广告投放

**当您要使用Growing IO获客分析服务对您在Apple Search Ads（下文简称ASA）上的投放进行归因分析时，请先确保您的App已经集成了Apple的iAd.framework和AdServices.framework ，同时集成Growing IO iOS SDK（2.9.9） 并按以下说明进行了相应设置，如有疑问请与您的App开发人员沟通。**

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpsJKTGp9.jpg) ****&#x20;

一、**广告归因与数据展示**

**1、在 Growing IO 后台，创建“苹果广告投放”监测链接，并绑定ASA账号进行相应的授权；‌**

**2、Growing IO 会以Campaign ID为维度，通过API接口获取广告投放相应信息；‌**

**3、Growing IO 会对ASA后台数据和服务端数据做归因匹配，并将归因的结果展示在 Growing IO 后台数据中。**

&#x20;****&#x20;

二、**创建监测链接与媒体授权**

1、在Growing IO后台**获客分析**→**获客追踪**→**新建监测链接** 中创建 App 推广链接，目标渠道选择“苹果广告投放”，然后点击确定。

**注：**推广APP请选择对应的**iOS** 应用

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpsVjACr9.jpg)&#x20;

2、确定后进入添加投放账号及授权流程

1）添加投放账号并授权：

&#x20;  点击添加投放账号→输入org\_id→点击授权

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpsv5Bgfa.jpg)&#x20;

其中Org\_id为您在苹果投放后帐户id，示例如下：

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpsbnAuGH.jpg)&#x20;

输入并点击授权后会跳转至苹果授权登录页，示例如下：

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpsyWntUd.png)‌

登录账号ID：填写对应的苹果广告后台的登录账号（Apple ID）

登录成功后进入选择权限页面，请选择：账号只读

&#x20; &#x20;

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpspY2b5M.jpg)&#x20;

&#x20;

2）授权成功后，请继续在Growing IO后台填写Campaign ID

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpsHrr0Jo.png)&#x20;

Campaign ID是您在ASA后台创建的广告系列 ID，示例如下：

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpsFuI6tp.jpg)&#x20;

当您有多个广告系列时，请在授权成功之后依次录入相应的Campaign ID。

&#x20;

三、**归因数据查看**

Apple Search Ads并不生成监测链接，因此相应归因数据的查看与其他渠道并不相同。您可以在以下几个维度查看相关数据。

1 推广日报数据报表：针对苹果广告投放渠道新增自定义指标：首次下载、重新下载。

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wps4WUnTS.jpg)&#x20;

其中首次下载是指用户首次在App Store下载该应用，重新下载是指以前安装过该应用的用户再次下载了应用。

&#x20;

2 渠道价值分析报表中‌：

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpsLYPY0e.jpg)&#x20;

因Apple不支持回传所以无法展示渠道回传事件，故渠道价值分析中苹果广告投放渠道数据展示规则同自然流量渠道规则。

&#x20;

**四 归因数据差异说明**

由于Growing IO与Apple的归因逻辑不同，双方平台出现数据差异属于正常现象，以下为数据差异产生的主要原因：

&#x20;

1.Apple Search Ads数据延迟

尽管Growing IO SDK拥有前置调用和重试机制，服务端请求苹果接口引入TSL/SSL会话复用，动态超时阈值等一系列手段规避数据延迟造成的数据差异，但当延迟状况严重的情况下，仍旧无法避免数据差异出现。

&#x20;

2.对转化时间定义不同

Apple将按照App安装完成时间作为转化时间，GIO则是按照App首次打开App时间（激活时间）统计转化。另外苹果的归因窗口期30天，因此查看数据时建议将渠道窗口期也设为30天。

&#x20;

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpsbgjwZ6.jpg)&#x20;

&#x20;

3.对新增定义不同

Apple按照Apple ID统计新增安装，Growing IO则是按照设备ID统计新增安装。

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wps5itWU6.jpg)&#x20;

4.对于Last Click的判定结果有可能不同

Apple Search Ads是自归因渠道，从而无法得知点击广告到用户安装之间，用户是否点击了其他广告。

![](file:///private/var/folders/qp/hzbm9hfj34v1284kvgjfc13c0000gn/T/com.kingsoft.wpsoffice.mac/wps-dada/ksohtml/wpspf1bfZ.jpg)&#x20;

5.广告隐私政策影响

如果用户启用了限制广告追踪（LAT），Growing IO 将无法从苹果搜索广告API中获取结果并进行归因，但ASA仍然会把对应广告计为ASA平台的归因。

&#x20;

&#x20;
