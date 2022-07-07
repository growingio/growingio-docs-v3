---
description: 小程序 SDK3.8对小程序旧版本SDK 进行了重构，支持更多小程序平台和框架。目前已在多家客户中稳定运行。
---

# 3.8

## 简介[​](http://localhost:3000/growingio-sdk-docs/docs/minprogram/3.8#%E7%AE%80%E4%BB%8B) <a href="#jian-jie" id="jian-jie"></a>

小程序 SDK3.8支持 `微信小程序`、`支付宝小程序`、`百度小程序`、`字节(抖音头条)小程序`、`QQ小程序`、`快应用`。

`快手小程序` 正在抓紧适配中，敬请期待。

目前具备以下特性：

* 埋点能力，开发同学可调用API主动采集自定义事件。
* 插件无埋点能力，自动采集用户行为事件，可通过开关和插件控制。
* 插件半自动埋点浏览能力，除快应用外，其他小程序均支持半自动埋点浏览事件。
* 新增uni-app vue3、taro3 vue3、remax的支持。
* 可依据使用场景自由搭配SDK插件。
* 支持自定义插件开发。（实验性功能，暂未开放）

### 选择小程序平台[​](http://localhost:3000/growingio-sdk-docs/docs/minprogram/3.8#%E9%80%89%E6%8B%A9%E5%B0%8F%E7%A8%8B%E5%BA%8F%E5%B9%B3%E5%8F%B0) <a href="#xuan-ze-xiao-cheng-xu-ping-tai" id="xuan-ze-xiao-cheng-xu-ping-tai"></a>

相比旧版本，我们依据不同的平台打包了平台专用的SDK（即原生开发的微信小程序只能使用微信小程序SDK）用户可根据自身开发的小程序平台或开发框架自由选择。由于只打包了特定平台的逻辑，做到了精简无冗余，对SDK的整体包大小控制更精准。当然我们也准备了节约理解成本的全量版本。

### 集成[​](http://localhost:3000/growingio-sdk-docs/docs/minprogram/3.8#%E9%9B%86%E6%88%90) <a href="#ji-cheng" id="ji-cheng"></a>

相比旧版本，我们适配了更多的小程序平台和框架，请在左侧菜单栏中选择对应的小程序端进行集成。

### 旧版本与3.8对比[​](http://localhost:3000/growingio-sdk-docs/docs/minprogram/3.8#33%E4%B8%8E38%E5%AF%B9%E6%AF%94) <a href="#33-yu-38-dui-bi" id="33-yu-38-dui-bi"></a>

为了更快速的帮助您理解小程序SDK3.8与旧版本的区别，我们为您详细罗列了两者的区别。

对比详情介绍请见[旧版本与3.8对比](jiu-ban-ben-yu-3.8-dui-bi.md)。

### 旧版本升级到3.8[​](http://localhost:3000/growingio-sdk-docs/docs/minprogram/3.8#33%E5%8D%87%E7%BA%A7%E5%88%B038) <a href="#33-sheng-ji-dao-38" id="33-sheng-ji-dao-38"></a>

为了帮助原先使用旧版本的用户快速升级到3.8，我们单独为您详细介绍了如何快速升级。

详情介绍请见[旧版本升级到3.8](jiu-ban-ben-sheng-ji-dao-3.8.md)。

