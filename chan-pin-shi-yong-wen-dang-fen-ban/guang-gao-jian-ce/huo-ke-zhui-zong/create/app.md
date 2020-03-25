# 推广App

## 概述

推广App有两种场景：增加 App 下载量和吸引用户直接打开App。

* **增加 App 下载量**：适用于拉新场景，对于常见的 App 下载行为追踪，可选择该方式创建链接来追踪用户 App下载行为，方便您衡量广告推广效果。
* **吸引用户直接打开App**：适用于促活、唤回场景，对于 App 已安装，希望通过广告推广促进用户打开 App 或是召回老客户，可通过该方式来创建深度链接（DeepLink）来促使用户回到您的 App 中。

## SDK版本支持

如果您需要跟踪 App（ iOS & Android）由推广带来的 App 下载，可以使用此功能。使用之前请确保您的 App 中加载了GrowingIO 的 SDK1.0.3 及以上版本。

### DeepLink 唤起 App

| DeepLink功能 | App SDK版本 |
| :--- | :--- |
| DeepLink 基础功能（Scheme 唤起 App） | 2.3.0 |
| DeepLink 直达 App 内落地页（Scheme打开至活动页） | 2.3.2 |
| Universal Links / 应宝微下载支持 | 2.4.1 |
| Universal Links / App Links 一步跳入 App 支持 | 2.8.4 |

{% hint style="warning" %}
使用 DeepLink 功能需要 SDK 升级到 2.3.0 以上，SDK 版本功能向下兼容。
{% endhint %}

## 新建监测链接

一. 在顶部导航栏选择“**获客分析 &gt; 广告监测”**，进入广告监测模块。

二. 单击左上角的**新建监测链接**，默认进入推广App的新建监测链接页面。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2858%29.png)

| 参数 | 说明 | 增加App下载量 | 吸引用户直接打开App |
| :--- | :--- | :--- | :--- |


| 监测链接名称 | 监测链接名称，由中文、英文、短横线（-）、下划线（\_）、斜杠（/）组成，长度小于50个字符。 | ✔️ | ✔️ |
| :--- | :--- | :--- | :--- |


| 推广App | 选择您要推广的App，如果您需要在一条链接中同时推广您的 iOS 与 Android App，请勾选“一个链接同时推广iOS和Android App”。然后各自选择App。 | ✔️ | ✔️ |
| :--- | :--- | :--- | :--- |


| 应用下载地址 | 应用下载地址。 | - | ✔️ |
| :--- | :--- | :--- | :--- |


| 直达App内落地页 | 添加该参数后可实现直达 App 内的某一页面。 | - | ✔️ |
| :--- | :--- | :--- | :--- |


| 推广活动 | 选择该链接所属的推广活动。 | ✔️ | ✔️ |
| :--- | :--- | :--- | :--- |


| 推广渠道 | 选择该链接所属的推广渠道。 | ✔️ | ✔️ |
| :--- | :--- | :--- | :--- |


| 推广目标页地址 | 根据实际活动推广情况，填入目标页URL地址。 | ✔️ | - |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x521B;&#x5EFA;&#x7C7B;&#x578B;</th>
      <th style="text-align:left">
        <ul>
          <li>&#x5355;&#x4E2A;&#x521B;&#x5EFA;</li>
          <li>&#x6279;&#x91CF;&#x521B;&#x5EFA;</li>
        </ul>
        <p>&#x5728;&#x4E00;&#x6761;&#x94FE;&#x63A5;&#x63A8;&#x5E7F;&#x4E00;&#x4E2A;&#x5E73;&#x53F0;App&#x7684;&#x60C5;&#x51B5;&#x4E0B;&#xFF0C;&#x652F;&#x6301;&#x6279;&#x91CF;&#x521B;&#x5EFA;&#x3002;</p>
      </th>
      <th style="text-align:left">&#x2714;&#xFE0F;</th>
      <th style="text-align:left">-</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| 批量创建数量 | 创建类型选择批量创建时可选，支持2-100之前的正整数。 | ✔️ | - |
| :--- | :--- | :--- | :--- |


{% hint style="success" %}
**直达 App 内落地页的技术原理：**

在移动端 App 中我们使用 URI Scheme 来定位一个应用甚至应用里的某个具体的功能或页面，就像定位一个网页一样。

例如：在 App 中我们要定位某个功能页面 ID 为 1234 的某个具体页面，就可以通过 [myapp://com.gio.function?page=1234](myapp://com.gio.function?page=1234) 这样的 URI Scheme 来实现。其中，page=1234 即为当前活动页的 URI ，其中 key=page ，value=1234 。

如果要使用该技术，请与活动页的开发人员确认页面 URI 参数信息以及 Key/Value 值，确认无误后请填入直达落地页参数输入框，该条深度链接将会跳转到 App 内的具体页面。
{% endhint %}

## \[吸引用户直接打开App\]相关配置

在正确集成 GrowingIO 提供的 SDK ，以及 URL Scheme 的配置后，即可开始使用 GrowingIO 提供的 DeepLink 深度链接功能。

SDK 端配置：[iOS 端](../../../../developer-manual/sdkintegrated/ios-sdk/auto-ios-sdk.md#10-deeplink-and-universal-link)、[Android 端​](../../../../developer-manual/sdkintegrated/android-sdk/auto-android-sdk.md#16-deep-link-hui-tiao-can-shu-huo-qu)

为获得更好的用户使用体验，GrowingIO 同时建议您在 iOS 下开启 Universal Links 、在 Android 下开启 App Links ，该两项技术为 Apple 与 Google 提供的原生方案，使用该技术将在其系统生态中将获得更流畅的跳转体验。

Universal Links 配置：[配置方法​](../../chan-pin-pei-zhi/deeplink.md#22-universal-links-pei-zhi)

App Links 配置：[配置方法](../../chan-pin-pei-zhi/deeplink.md#32-applinks-pei-zhi)

## 延迟深度链接（Deferred DeepLink）

{% hint style="info" %}
延迟深度链接为深度链接的升级功能，平台基础版在完成延迟深度链接功能增购后可在深度链接配置的基础上直接实现功能使用，请参考[深度链接配置](../../chan-pin-pei-zhi/deeplink.md)。

如果您需要试用升级或了解其他信息，请联系您的客户成功经理。
{% endhint %}

在使用常规深度链接的场景中，已安装App的用户可以通过深度链接转跳到App内指定内容位置；未安装App的用户则会被导流至应用商店，引导用户去下载App。

在实际进行产品推广时，如果当前用户是未安装App的用户，按照实际使用场景，用户下载并打开App时通常会进入App的首页，此时无法达到活动预设的指定内容，用户没有顺利到达活动转化场景，无法完成转化。

那么是否有办法让下载App的新用户也同样可以到达App内的指定内容页，让这部分用户顺利完成转化？

延迟深度链接技术由此推出，通过“延迟”技术，使得新用户在首次安装App时，同样可以到达您设定的指定页面，在App内还原活动场景，促使用户完成转化。

### 查看数据指标

您可以查看有多少新用户通过延迟深度链接在App中到达了您设定的活动场景。

一. 在顶部导航栏选择获客分析 &gt; 广告监测，默认进入应用级数据页面。

二. 选择您的App应用。

三. 在下方的推广日报模块单击自定义指标，勾选延迟场景还原即可查看延迟深度链接的数据。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%284%29.png)

