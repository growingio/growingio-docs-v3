---
description: 创建小程序推广所用的二维码、小程序码。
---

# 小程序码管理

## 常见场景介绍 <a id="chang-jian-chang-jing-jie-shao"></a>

在小程序推广的常见场景下，市场和运营人员有在其他公众号、合作渠道进行推广的需求。

常见的手段有以下几种：

1. 在媒体、合作渠道等进行推广；
2. 利用其他小程序互相引流；
3. 进行微信广告平台的投放；
4. 进行线下场景的引流等。‌

其中1、2、4等场景，常见的推广手段之一就是利用小程序码、二维码等，引导用户扫码打开小程序。‌

## 功能使用 <a id="gong-neng-shi-yong-shuo-ming"></a>

‌在顶部导航栏选择“**获客分析 &gt; 获客追踪 &gt; 监测链接”**，选择小程序类型应用，会出现小程序码入口。

![](../../../../../.gitbook/assets/image.png)

### 小程序推广码创建的授权 <a id="di-yi-bu-jin-hang-xiao-cheng-xu-tui-guang-ma-chuang-jian-de-shou-quan-cao-zuo"></a>

{% hint style="info" %}
在开始新建小程序码之前，**为了小程序账号安全的角度考虑，首先需要小程序推广码生成的授权操作。**
{% endhint %}

在小程序码管理页面，单击**立刻新建**进入新建小程序码页面，单击页面右上角的**前往微信授权**，进入微信公众平台的授权页面，使用公众平台绑定的管理员个人微信号扫码授权。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2890%29.png)

{% hint style="success" %}
完成授权后，会显示“已授权”，接下来就可以进行推广码的创建。‌
{% endhint %}

### 创建推广码

一. 在已授权的小程序码管理页面，单机页面左上角的**新建小程序码**，弹出新建小程序码页面。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28167%29.png)

二. 填写二维码名称、落地页链接、广告渠道，选择码的类型等必填参数后单击页面右上角的生成二维码。

创建成功后会在页面右侧显示二维码，单机下载将二维码下载到本地进行推广使用。

{% hint style="warning" %}
腾讯对二维码参数中的字节长度进行了规范，最多128字节，故在填写时，需要注意参数长度。‌
{% endhint %}

## 管理推广码

在小程序码管理页面您可以

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28208%29.png)

下载二维码：单击单条小程序码右侧的下载按钮可下载二维码。

修改名称：单击单条小程序码右侧的修改按钮可修改小程序码的名称。

删除：单击单条小程序码右侧的删除按钮可删除不需要的条目。

{% hint style="info" %}
**删除二维码，仅仅是在GrowingIO平台上删除生成的码，不能再下载被使用；**如果二维码在投放中继续使用，也会持续收集新数据；已收集的数据也不会被删除。
{% endhint %}

## 查看推广效果

在小程序码管理界面，单击右上角的**过去7天广告获客量**，会自动跳转到新建事件分析页面，此页面展示了过去7天使用过UTM参数投放获客的用户量。

想要进一步查看具体的投放细节，可以在“添加维度”中，选择广告的几个维度，查看具体信息（维度值包含创建推广码时填写的参数）。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LMgq7UBb6BOpnVYXuBd-LMgrVSJ2jSg2pAzcBlW7FC838F9-11F0-4729-B239-8E7DA61068ED.png)

保存此事件分析，可以调整事件分析的时间，进行下钻，还可以查看不同用户群，加入核心事件等。‌

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LMgq7UBb6BOpnVYXuBd-LMgr_HGgOVe52KM7fZT820C07B2-3F38-40F7-9DCF-82C9EFEC1EB8.png)

{% hint style="info" %}
**注意**：GrowingIO调用A和C接口生成小程序码和小程序二维码，腾讯支持调用A\C接口共生成10w个码。具体的生成接口、生成限制、以及开发者文档，请参考如下链接：[https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/qr-code.html](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/qr-code.html)​‌
{% endhint %}

