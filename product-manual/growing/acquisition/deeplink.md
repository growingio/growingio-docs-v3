# 深度链接

## 概述

深度链接适用于促活、唤回场景，对于 App 已安装，希望通过广告推广促进用户打开 App 或是召回老客户，可通过该方式来创建深度链接（DeepLink）来促使用户回到您的 App 中。

## SDK版本支持

| DeepLink功能 | App SDK版本 |
| :--- | :--- |
| DeepLink 基础功能（Scheme 唤起 App） | 2.3.0 |
| DeepLink 直达 App 内落地页（Scheme打开至活动页） | 2.3.2 |
| Universal Links / 应宝微下载支持 | 2.4.1 |
| Universal Links / App Links 一步跳入 App 支持 | 2.8.4 |
| 支持 Defer DeepLink 功能 | 2.8.5 |

{% hint style="warning" %}
使用 DeepLink 功能需要 SDK 升级到 2.3.0 以上，SDK 版本功能向下兼容。
{% endhint %}

## 相关配置

在使用 GrowingIO 的深度链接功能时，首选需要完成以下配置

在正确集成 GrowingIO 提供的 SDK ，以及 URL Scheme 的配置后，即可开始使用 GrowingIO 提供的 DeepLink 深度链接功能。

SDK 端配置：[iOS 端](https://docs.growingio.com/docs/developer-manual/sdkintegrated/ios-sdk/auto-ios-sdk#10-deeplink-and-universal-link)、[Android 端​](https://docs.growingio.com/docs/developer-manual/sdkintegrated/android-sdk/auto-android-sdk#16-deep-link-hui-tiao-can-shu-huo-qu)​

为获得更好的用户使用体验，GrowingIO 同时建议您在 iOS 下开启 Universal Links 、在 Android 下开启 App Links ，该两项技术为 Apple 与 Google 提供的原生方案，使用该技术将在其系统生态中将获得更流畅的跳转体验。

Universal Links 配置：[配置方法​](https://docs.growingio.com/docs/product-manual/growing/ads/advance/deeplink#22-universal-links-pei-zhi)​

App Links 配置：[配置方法](https://docs.growingio.com/docs/product-manual/growing/ads/advance/deeplink#32-applinks-pei-zhi)

## 新建监测链接

一. 在顶部导航栏选择“**获客追踪&gt;深度链接”**，进入深度链接列表。

二. 单击左上角的**新建深度链接**，进入新建深度链接页面。

三. 配置参数后单击确定，展示创建好的深度链接或二维码。

| 参数 | 说明 |
| :--- | :--- |
| 深度链接名称 | 深度链接名称，由中文、英文、短横线（-）、下划线（\_）、斜杠（/）组成，长度小于50个字符。 |
| 推广App | 选择您要推广的App，如果您需要在一条链接中同时推广您的 iOS 与 Android App，请勾选“一个链接同时推广iOS和Android App”。然后各自选择App。 |
| 应用下载地址 | 应用下载地址。 |
| 直达App内落地页 | 添加该参数后可实现直达 App 内的某一页面。 |
| 推广活动 | 选择该链接所属的推广活动。 |
| 推广渠道 | 选择该链接所属的推广渠道。 |

## 直达 App 内落地页

**技术原理介绍**

{% hint style="success" %}
在移动端 App 中我们使用 URI Scheme 来定位一个应用甚至应用里的某个具体的功能或页面，就像定位一个网页一样。

例如：在 App 中我们要定位某个功能页面 ID 为 1234 的某个具体页面，就可以通过 [myapp://com.gio.function?page=1234](myapp://com.gio.function?page=1234) 这样的 URI Scheme 来实现。其中，page=1234 即为当前活动页的 URI ，其中 key=page ，value=1234 。
{% endhint %}

## 延迟深度链接（Deferred DeepLink）

{% hint style="info" %}
延迟深度链接为深度链接的升级功能，在基础版本产品服务中无法使用该功能，如果您需要试用升级或了解其他信息，请联系您的客户成功经理。
{% endhint %}

在使用常规深度链接的场景中，已安装App的用户可以通过深度链接转跳到App内指定内容位置；未安装App的用户则会被导流至应用商店，引导用户去下载App。

在实际进行产品推广时，如果当前用户是未安装App的用户，按照实际使用场景，用户下载并打开App时通常会进入App的首页，此时无法达到活动预设的指定内容，用户没有顺利到达活动转化场景，无法完成转化。

那么是否有办法让下载App的新用户也同样可以到达App内的指定内容页，让这部分用户顺利完成转化？

延迟深度链接技术由此推出，通过“延迟”技术，使得新用户在首次安装App时，同样可以到达您设定的指定页面，在App内还原活动场景，促使用户完成转化。

#### 相关配置 <a id="cha-kan-shu-ju-zhi-biao"></a>

如果您的产品从未配置配置过深度链接（DeepLink），首先需要您需要完成深度链接的基本配置工作。提供链接到基本配置位置

如果您的产品已经完成深度链接（DeepLink）配置，无需您进行额外配置工作，您创建的深度链接（ DeepLink） 都将自动升级为延迟深度链接（ Deferred DeepLink）。

#### 查看数据指标 <a id="cha-kan-shu-ju-zhi-biao"></a>

您可以查看有多少新用户通过延迟深度链接在App中到达了您设定的活动场景。

一. 在顶部导航栏选择获客分析 &gt; 广告监测，默认进入应用级数据页面。

二. 选择您的App应用。

三. 在下方的推广日报模块单击自定义指标，勾选延迟场景还原即可查看延迟深度链接的数据。

![](../../../.gitbook/assets/image%20%284%29.png)

![](../../../.gitbook/assets/image%20%285%29.png)

