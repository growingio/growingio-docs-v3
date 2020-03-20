# 推广App

## 概述

推广App有两种场景：增加 App 下载量和吸引用户直接打开App。

* **增加 App 下载量**：适用于拉新场景，对于常见的 App 下载行为追踪，可选择该方式创建链接来追踪用户 App下载行为，方便您衡量广告推广效果。
* **吸引用户直接打开App**：适用于促活、唤回场景，对于 App 已安装，希望通过广告推广促进用户打开 App 或是召回老客户，可通过该方式来创建深度链接（DeepLink）来促使用户回到您的 App 中。

## SDK版本支持

如果您需要跟踪 App（ iOS & Android）由推广带来的 App 下载，可以使用此功能。使用之前请确保您的 App 中加载了GrowingIO 的 SDK1.0.3 及以上版本。

#### DeepLink 唤起 App

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

![](../../../../.gitbook/assets/image%20%2858%29.png)

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x53C2;&#x6570;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
      <th style="text-align:left">&#x589E;&#x52A0;App&#x4E0B;&#x8F7D;&#x91CF;</th>
      <th style="text-align:left">&#x5438;&#x5F15;&#x7528;&#x6237;&#x76F4;&#x63A5;&#x6253;&#x5F00;App</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x76D1;&#x6D4B;&#x94FE;&#x63A5;&#x540D;&#x79F0;</td>
      <td style="text-align:left">&#x76D1;&#x6D4B;&#x94FE;&#x63A5;&#x540D;&#x79F0;&#xFF0C;&#x7531;&#x4E2D;&#x6587;&#x3001;&#x82F1;&#x6587;&#x3001;&#x77ED;&#x6A2A;&#x7EBF;&#xFF08;-&#xFF09;&#x3001;&#x4E0B;&#x5212;&#x7EBF;&#xFF08;_&#xFF09;&#x3001;&#x659C;&#x6760;&#xFF08;/&#xFF09;&#x7EC4;&#x6210;&#xFF0C;&#x957F;&#x5EA6;&#x5C0F;&#x4E8E;50&#x4E2A;&#x5B57;&#x7B26;&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x63A8;&#x5E7F;App</td>
      <td style="text-align:left">&#x9009;&#x62E9;&#x60A8;&#x8981;&#x63A8;&#x5E7F;&#x7684;App&#xFF0C;&#x5982;&#x679C;&#x60A8;&#x9700;&#x8981;&#x5728;&#x4E00;&#x6761;&#x94FE;&#x63A5;&#x4E2D;&#x540C;&#x65F6;&#x63A8;&#x5E7F;&#x60A8;&#x7684;
        iOS &#x4E0E; Android App&#xFF0C;&#x8BF7;&#x52FE;&#x9009;&#x201C;&#x4E00;&#x4E2A;&#x94FE;&#x63A5;&#x540C;&#x65F6;&#x63A8;&#x5E7F;iOS&#x548C;Android
        App&#x201D;&#x3002;&#x7136;&#x540E;&#x5404;&#x81EA;&#x9009;&#x62E9;App&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x5E94;&#x7528;&#x4E0B;&#x8F7D;&#x5730;&#x5740;</td>
      <td style="text-align:left">&#x5E94;&#x7528;&#x4E0B;&#x8F7D;&#x5730;&#x5740;&#x3002;</td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x76F4;&#x8FBE;App&#x5185;&#x843D;&#x5730;&#x9875;</td>
      <td style="text-align:left">&#x6DFB;&#x52A0;&#x8BE5;&#x53C2;&#x6570;&#x540E;&#x53EF;&#x5B9E;&#x73B0;&#x76F4;&#x8FBE;
        App &#x5185;&#x7684;&#x67D0;&#x4E00;&#x9875;&#x9762;&#x3002;</td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x63A8;&#x5E7F;&#x6D3B;&#x52A8;</td>
      <td style="text-align:left">&#x9009;&#x62E9;&#x8BE5;&#x94FE;&#x63A5;&#x6240;&#x5C5E;&#x7684;&#x63A8;&#x5E7F;&#x6D3B;&#x52A8;&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x63A8;&#x5E7F;&#x6E20;&#x9053;</td>
      <td style="text-align:left">&#x9009;&#x62E9;&#x8BE5;&#x94FE;&#x63A5;&#x6240;&#x5C5E;&#x7684;&#x63A8;&#x5E7F;&#x6E20;&#x9053;&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x63A8;&#x5E7F;&#x76EE;&#x6807;&#x9875;&#x5730;&#x5740;</td>
      <td style="text-align:left">&#x6839;&#x636E;&#x5B9E;&#x9645;&#x6D3B;&#x52A8;&#x63A8;&#x5E7F;&#x60C5;&#x51B5;&#xFF0C;&#x586B;&#x5165;&#x76EE;&#x6807;&#x9875;URL&#x5730;&#x5740;&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x521B;&#x5EFA;&#x7C7B;&#x578B;</td>
      <td style="text-align:left">
        <ul>
          <li>&#x5355;&#x4E2A;&#x521B;&#x5EFA;</li>
          <li>&#x6279;&#x91CF;&#x521B;&#x5EFA;</li>
        </ul>
        <p>&#x5728;&#x4E00;&#x6761;&#x94FE;&#x63A5;&#x63A8;&#x5E7F;&#x4E00;&#x4E2A;&#x5E73;&#x53F0;App&#x7684;&#x60C5;&#x51B5;&#x4E0B;&#xFF0C;&#x652F;&#x6301;&#x6279;&#x91CF;&#x521B;&#x5EFA;&#x3002;</p>
      </td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x6279;&#x91CF;&#x521B;&#x5EFA;&#x6570;&#x91CF;</td>
      <td style="text-align:left">&#x521B;&#x5EFA;&#x7C7B;&#x578B;&#x9009;&#x62E9;&#x6279;&#x91CF;&#x521B;&#x5EFA;&#x65F6;&#x53EF;&#x9009;&#xFF0C;&#x652F;&#x6301;2-100&#x4E4B;&#x524D;&#x7684;&#x6B63;&#x6574;&#x6570;&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">-</td>
    </tr>
  </tbody>
</table>三. 配置参数后单击确定，展示创建好的监测链接或二维码。

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

Universal Links 配置：[配置方法​](../advance/deeplink.md#22-universal-links-pei-zhi)

App Links 配置：[配置方法](../advance/deeplink.md#32-applinks-pei-zhi)

## 延迟深度链接（Deferred DeepLink）

{% hint style="info" %}
延迟深度链接为深度链接的升级功能，平台基础版在完成延迟深度链接功能增购后可在深度链接配置的基础上直接实现功能使用，请参考[深度链接配置](../advance/deeplink.md)。

如果您需要试用升级或了解其他信息，请联系您的客户成功经理。
{% endhint %}

在使用常规深度链接的场景中，已安装App的用户可以通过深度链接转跳到App内指定内容位置；未安装App的用户则会被导流至应用商店，引导用户去下载App。

在实际进行产品推广时，如果当前用户是未安装App的用户，按照实际使用场景，用户下载并打开App时通常会进入App的首页，此时无法达到活动预设的指定内容，用户没有顺利到达活动转化场景，无法完成转化。

那么是否有办法让下载App的新用户也同样可以到达App内的指定内容页，让这部分用户顺利完成转化？

延迟深度链接技术由此推出，通过“延迟”技术，使得新用户在首次安装App时，同样可以到达您设定的指定页面，在App内还原活动场景，促使用户完成转化。

#### 查看数据指标

您可以查看有多少新用户通过延迟深度链接在App中到达了您设定的活动场景。

一. 在顶部导航栏选择获客分析 &gt; 广告监测，默认进入应用级数据页面。

二. 选择您的App应用。

三. 在下方的推广日报模块单击自定义指标，勾选延迟场景还原即可查看延迟深度链接的数据。

![](../../../../.gitbook/assets/image%20%284%29.png)

