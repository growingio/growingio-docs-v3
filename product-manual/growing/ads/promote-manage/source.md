---
description: 统一管理广告监测的渠道。
---

# 推广渠道管理

系统预置的渠道和您在创建监测链接时创建的渠道都统一在此处管理，您也可以在此处创建渠道信息，在创建监测链接时直接选取；利用搜索功能快速查找您的渠道。

## 渠道管理

一. 在顶部导航栏选择“**获客分析 &gt; 广告监测”**，进入广告监测模块。

二. 在左侧导航栏选择“**管理 &gt; 推广渠道”**，进入渠道管理页面。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2854%29.png)

**新建渠道**：单击页面上方的新建渠道，输入渠道名称，选择渠道类型（广告平台、其他）后单击**确定**。

**渠道信息QuickView**：单击列表中的单条渠道，右侧将展开当前渠道的QuickView视图。

**编辑渠道**：单击单条私有渠道右侧的 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/guang-gao-jian-ce-bian-ji.png) 对该条渠道信息进行二次修改，公有渠道不支持修改。

**删除渠道**：单击单条私有渠道右侧的 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/1.png) 可删除该条不需要的、未被监测链接使用的、私有渠道。

{% hint style="success" %}
**删除提示**

* 如果渠道被监测链接使用，需先删除监测链接才能删除此渠道；
* 公有渠道不支持删除。
{% endhint %}

{% hint style="info" %}
GrowingIO 渠道类型中为两类：

* 公有渠道为 GrowingIO 预置的渠道，该类渠道通常为 GrowingIO 与渠道方完成了系统对接，广告数据会更加精准；
* 私有渠道即为当现有的公有渠道中未出现您要投放的渠道，可通过渠道创建创建您的私有渠道，方便标识您的广告渠道来源。
{% endhint %}

## 转化回传配置

当需要在媒体方进行 oCPM / oCPC / oCPA 模式进行投放时，通常需要将转化数据回传至媒体方，来实现对广告投放效果优化。

GrowingIO 目前已支持行业主流大多数媒体的转化数据回传，通过渠道列表下的简单配置，即可完成转化数据回传。

当渠道支持转化回传配置时，在渠道列表中点击该渠道，右侧将展示当前渠道详细信息，通过【添加回传事件】按钮，可添加转化回传事件，或直接在渠道列表中，通过右侧 “+” 操作，可直接添加转化回传事件。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LrscuRiNffmnHEFX4ks-Lrsd_ADsiemzOtmo19uimage.png)

新建：通过渠道列表下的添加按钮以及渠道详情中的添加按钮都可添加转化回传事件。

编辑：在已配置的转化回传事件中，可通过编辑操作更改回传配置。激活为预定义事件回传类型，不支持编辑操作。

删除：当不需要该条转化数据回传时，通过删除操作可删除该条配置信息。

当该渠道支持激活回传时，为方便您的使用， GrowingIO 默认打开渠道的激活回传。

### 自定义转化回传配置 <a id="zi-ding-yi-zhuan-hua-hui-chuan-pei-zhi"></a>

当渠道方支持更多深度转化数据回传时，如：注册、下单、留存等等，事件回传类型下拉选项中将会出现对应的事件类型可供选择。

一、选择需要转化回传的应用；

二、选择转化事件类型，例如：注册；

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LrscuRiNffmnHEFX4ks-Lrse-AkTa3HZvdt2Fh9image.png)

三、在事件选择器中关联对应回传事件。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LrscuRiNffmnHEFX4ks-LrsfhOvF9R8NP1iaN6Kimage.png)

完成回传事件关联，渠道回传事件列表中将会增加刚刚配置的回传事件。

在设定深度转化数据回传时，因涉及到关键业务数据，建议选择埋点事件类型进行回传。

完成回传事件关联，当前渠道回传事件列表中会新增刚刚配置的回传事件。

### **转化回传联调** <a id="zhuan-hua-hui-chuan-lian-tiao"></a>

在 GrowingIO 与媒体方全部完成转化回传配置后，在正式开启前，部分媒体会要求对转化事件进行测试或联调，GrowingIO 专门为此提供联调工具，该工具的操作引导，可使您快速完成联调流程。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LsQpogmCgsvVyGyHNyc-LsQq1Hs8xjipO2nw7nIimage.png)

按照步骤引导，确认 1 至 4 步骤均已完成配置，在回传事件联调工具中填写监测链接，和联调测试设备信息，此处需注意监测链接需与在媒体方配置的为同一条链接，联调测试设备应为同一设备。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LsQpogmCgsvVyGyHNyc-LsQqcOnSHBYgX2XZo9Yimage.png)

填写完毕后，点击「获取上报数据」按钮，等待联调数据上报，媒体方平台若显示已收到数据，说明联调成功，如媒体平台长时间未收到上报数据，可再次点击「获取上报数据」按钮，重新获取数据。

