# 预定义维度

{% tabs %}
{% tab title="用户来源维度" %}
> 用户来源维度：通过用户来源了解用户是怎样来到你的网站上的。

## 1.访问来源（Web）‌

网站的流量来源，可以是百度，谷歌，优酷等站外渠道，也可能是直接访问该网站。可以通过设置 UTM 参数来确定流量具体是哪个广告带来的。‌

访问来源中微信类来源: 微信目前是一个非常重要的流量来源。一般不考虑广点通等付费推广的话，微信渠道上很多H5\Web等有非常成熟的使用和分享、获客场景，根据微信环境中打开的数据参数，GrowingIO 识别了几种微信环境访问 H5/PC 的分类，常见的用例有这样几种：

| 访问来源具体值 | 场景 | 说明 |
| :--- | :--- | :--- |
| 微信-公众号 | 公众号中查看图文消息-点击“阅读原文” | GroiwngIO会识别到微信的环境，微信会返回“公众号”访问来源链接（例如mp.weixinbridge.com\)，即可以判断出公众号的来源。 |
| 微信-朋友圈 | 朋友圈里查看分享的页面类链接 | GroiwngIO会识别到微信的环境，同时微信会给出相应的技术参数，即可以判断为朋友圈打开。 |
| 微信-群聊 | 查看分享给群组的页面链接 | GroiwngIO会识别到微信的环境，同时微信会给出相应的技术参数，即可以判断为群组信息中打开。 |
| 微信-单聊 | 查看分享给单个好友的页面链接 | GroiwngIO会识别到微信的环境，同时微信会给出相应的技术参数，即可以判断为好友信息中打开。 |
| 微信-其他 | 扫描二维码在微信中打开H5页面查看 | 如果不使用GrowingIO生成具体的追踪链接，仅可以识别微信环境打开；如果想要识别具体的二维码的信息，例如那篇文章的，哪个公众号等，详情可以了解广告监测链接的相关功能。 |
| 微信-其他 | 公众号直接给文字/图片链接，用户打开 | 如果不使用GrowingIO生成具体的追踪链接，仅可以识别微信环境打开；如果想要识别具体的二维码的信息，例如那篇文章的，哪个公众号等，详情可以了解广告监测链接的相关功能。 |
| 微信-其他 | 打开分享到朋友圈、群聊、单聊消息中的URL链接 | 如果仅是URL，只会追踪具体的URL，但可以识别在微信环境中打开。 |

{% hint style="info" %}
小程序的访问来源只有两种：

* 直接访问：直接访问小程序；此时一级访问来源为：直接访问
* AppID：从别的小程序转跳而来；此时一级访问来源为：外部链接

建议您使用”自定义 App 渠道“维度来分析小程序的访问场景。
{% endhint %}

{% hint style="info" %}
App的访问来源只有一种：直接访问
{% endhint %}

## 2.一级访问来源（Web）

为便于分析使用，我们将访问来源进行了以下归类：直接访问、搜索引擎、社交媒体、视频媒体、新闻媒体、外部链接，六大分类。‌

**直接访问**‌

a.用户直接在浏览器中输入了一个域名或使用书签进行访问；‌

b.从邮件中点击链接访问网站取决于电子邮件的提供商/程序）；‌

c.从 Microsoft Office 或 PDF 文件中点击链接访问网站；‌

d.通过点击由原 url 生成的短链接访问网站；‌

e.通过 App 点击链接访问网站（比如今日头条、微博中的链接）（对微信做过识别，故此场景不适用微信）；‌

f.通过点击一个 https 类型的 url 访问一个 http 类型的 url（比如如果点击 [https://example.com/1](https://example.com/1) 转到 [http://example.com/2](http://example.com/2), 对于 example.com/2 的分析会认为是直接访问）；‌

g.部分浏览器（特别是移动端浏览器）会把搜索跳转当成直接访问。‌

**搜索引擎**

| **域名** | 来源方 |
| :--- | :--- |
| google.xx.xx | Google |
| yahoo.com | 雅虎 |
| bing.com | 必应 |
| www.baidu.com、m.baidu.com、bzclk.baidu.com | 百度 |
| so.com | 360 搜索 |
| sogou.com | 搜狗 |
| sm.cn | 神马 |
| youdao.com | 有道 |
| zhongsou.com | 中搜 |

**社交媒体**

| 域名 | 来源方 |
| :--- | :--- |


| facebook.com | Facebook |
| :--- | :--- |


| twitter.com、t.co | Twitter |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p>web.telegram.org&#x3001;org.telegram.plus&#x3001;org.telegram.multi&#x3001;</p>
        <p>org.telegram.messenger</p>
      </th>
      <th style="text-align:left">Telegram</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

| linkedin.com | Linkedin |
| :--- | :--- |


| instagram.com | Instagram |
| :--- | :--- |


| weibo.com、t.cn、weibo.cn | 微博 |
| :--- | :--- |


| zhihu.com | 知乎 |
| :--- | :--- |


| renren.com | 人人网 |
| :--- | :--- |


| mp.weixin.qq.com | 微信 |
| :--- | :--- |


**视频媒体**

| **域名** | 来源方 |
| :--- | :--- |
| www.youtube.com、m.youtube.com | Youtube |
| www.iqiyi.com | 爱奇艺 |
| v.qq.com | 腾讯视频 |
| v.youku.com | 优酷 |
| www.douyu.com | 斗鱼TV |
| www.bilibili.com | Bilibili |

**新闻媒体**

| **域名** | 来源方 |
| :--- | :--- |
| open.toutiao.com、ad.toutiao.com | 今日头条 |
| xw.qq.com | 腾讯新闻 |
| news.sohu.com | 搜狐新闻 |

**外部链接**‌

除直接访问及以上来源分类之外，其余全部算做外部链接。‌

{% hint style="success" %}
小程序的一级访问来源只有两种：

直接访问：直接访问小程序

外部链接：从其他小程序转跳
{% endhint %}

## 3.搜索词（web）

用户从搜索引擎进入网站所使用的搜索词，一般情况下付费搜索的搜索词可以被解析，百度、谷歌、搜狗和360渠道只有付费搜索词，其他渠道既有付费搜索词也有自然搜索词。‌

如果在值中出现 N/A ，意为这部分流量不是通过搜索词访问的。‌

## 4.App 版本（app/小程序）

App 和小程序 的版本号‌

## 5.自定义 App 渠道（app/小程序）

自定义 App 渠道：‌

在APP集成SDK的时候，针对安卓用户，设置分包渠道。‌

在小程序中，则自动获取小程序打开的来源。目前支持微信中60多种统计场景，例如：二维码扫码，群聊中点击分享的小程序卡片等。

**案例：**在「事件分析」横向柱图中添加不同的「维度」，可以查看不同访问来源下的页面浏览量情况。‌

​​

![](http://growing.cn-bj.ufileos.com/ccc10.png)

## 6. 广告监测

> **通过「广告监测」设置 App 推广的维度值**

通过顶部导航栏进入「广告监测」功能，设置 App 推广的字段：​

![](http://growing.cn-bj.ufileos.com/ccc11.png)

> **通过「广告监测」设置网站推广的维度值**

通过顶部导航栏进入「广告监测」功能，设置网站推广的字段：‌

​​

![](http://growing.cn-bj.ufileos.com/ccc12.png)

> **支持自定义 UTM 参数**

| UTM 参数 | 使用方式 | 示意 |
| :--- | :--- | :--- |
| 广告来源 utm\_source | 标识投放的网站，例如：google、baidu、toutiao | utm\_source=Google |
| 广告媒介 utm\_medium | 广告媒介或营销媒介，例如：CPC、Banner 和 EDM | utm\_medium=cpc |
| 广告名称 utm\_campaign | 产品的具体广告系列名称、标语、促销代码等 | utm\_campaign=spring\_sale |
| 广告关键词 utm\_term | 标识付费搜索关键字 | utm\_term=running+shoes |
| 广告内容 utm\_content | 用于区分相似内容或同一广告内的链接。如果在同一封 EDM 中使用了两个不同的链接，就可以使用 utm\_content 设置不同的值，以便判断哪个版本的效果更好 | utm\_content=logolink or utm\_content=textlink‌ |

UTM 渠道归因模式为非直接访问的最后一次访问。‌

**案例：**可以通过设置 utm 参数，选择相应的维度「广告来源」、「广告内容」、「广告名称」、「广告关键词」、「广告媒介」等，来监控投放的推广内容效果。‌

​
{% endtab %}

{% tab title="地域信息维度" %}
> 地域信息维度：了解用户在哪里访问你的网站。

| 维度 | 说明 |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x57CE;&#x5E02;&#x540D;&#x79F0;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</th>
      <th
      style="text-align:left">
        <p>Web &#x57FA;&#x4E8E; IP &#x5730;&#x5740;&#xFF0C;&#x4EE5;&#x57CE;&#x5E02;&#x4F5C;&#x4E3A;&#x7EF4;&#x5EA6;&#x503C;&#xFF0C;&#x76EE;&#x524D;&#x53EA;&#x652F;&#x6301;&#x56FD;&#x5185;&#x57CE;&#x5E02;&#x3002;</p>
        <p>App &#x548C;&#x5C0F;&#x7A0B;&#x5E8F; &#x57FA;&#x4E8E; IP &#x5730;&#x5740;&#x548C;
          GPS &#x3002;&#x4F18;&#x5148;&#x5224;&#x65AD;GPS&#x503C;&#xFF0C;GPS&#x503C;&#x7F3A;&#x5931;&#x65F6;&#xFF0C;&#x4F7F;&#x7528;IP&#x5730;&#x5740;&#x3002;</p>
        </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5730;&#x533A;&#x540D;&#x79F0;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</th>
      <th
      style="text-align:left">
        <p>Web &#x57FA;&#x4E8E;IP&#x5730;&#x5740;&#xFF0C;&#x8BE5;&#x7EF4;&#x5EA6;&#x5305;&#x542B;&#x56FD;&#x5185;&#x7701;&#x7EA7;&#x4EE5;&#x4E0A;&#x884C;&#x653F;&#x533A;&#xFF0C;&#x4EE5;&#x53CA;&#x56FD;&#x5916;&#x5730;&#x533A;&#x3002;</p>
        <p>app &#x548C;&#x5C0F;&#x7A0B;&#x5E8F; &#x57FA;&#x4E8E; IP &#x5730;&#x5740;&#x548C;
          GPS &#x3002;&#x4F18;&#x5148;&#x5224;&#x65AD;GPS&#x503C;&#xFF0C;GPS&#x503C;&#x7F3A;&#x5931;&#x65F6;&#xFF0C;&#x4F7F;&#x7528;IP&#x5730;&#x5740;&#x3002;</p>
        </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

| 国家代码（Web/App/小程序） | 用户所在的国家的英文缩写，常见的维度值有：CN，US，JP，SG等。 |
| :--- | :--- |


| 国家名称（Web/App/小程序） | 用户所在的国家的名称，常见的有：中国，美国，英国，新加坡等。技术说明：维度指为“未知”的原因可能是用户使用的是移动网络，或开了代理。 |
| :--- | :--- |


| 微信用户所在城市（小程序） | 小程序特有维度。表示用户在微信端设置的所在城市。使用前提是小程序SDK获取到微信访问用户属性。 |
| :--- | :--- |


| 微信用户所在省（小程序） | 小程序特有维度。表示用户在微信端设置的所在省。使用前提是小程序SDK获取到微信访问用户属性。 |
| :--- | :--- |


| 微信用户所在国家（小程序） | 小程序特有维度。表示用户在微信端设置的所在国家。使用前提是小程序SDK获取到微信访问用户属性。 |
| :--- | :--- |
{% endtab %}

{% tab title="设备信息维度" %}
> 设备信息维度：了解用户使用说明设备访问你的网站。

| 维度 | 说明 |
| :--- | :--- |
| 网站/手机应用（Web/App/小程序） | 用于区分该设备是接入了growingIO的是JS SDK还是iOS SDK |
| 屏幕大小（Wed/App/小程序） | Web 端是窗口大小，移动端是屏幕大小。 |
| 操作系统（Web/App/小程序） | 用户所使用的操作系统，比如 Windows 8 ，Windows 7 ，Mac OS X ，Android，weixin-iOS，weixin-Android。 |
| 操作系统版本Web/App/小程序） | 同「浏览器」，但是会按照不同的版本进行区分，比如 Android 4.0 等。 |
| 操作系统语言 | 统计不同的操作系统语言 |
| 浏览器（Web） | 用户所用浏览器的类型，比如 Chrome，Chrome Mobile，Safari，IE 等。 |
| 浏览器版本（Web） | 通过「浏览器」，但是会按照不同的版本进行区分，比如 Chrome 47.0.2526 等。 |
| 设备品牌（Web/App/小程序） | 将不同设备的品牌作为维度值。 |
| 设备型号（Web/App/小程序） | 用于区分具体的机型。 |
| 设备类型（App/小程序） | 设备的类型，平板和手机。 |
{% endtab %}

{% tab title="其他维度" %}
> **页面级维度**

对于 web 端可以这样理解： 用户先访问了 [https://www.growingio.com/](https://www.growingio.com/) 再访问了 [https://www.growingio.com/circle](https://www.growingio.com/circle)

### 1.域名（web/小程序） <a id="41"></a>

www.growingio.com 是这两个页面的域名。

小程序为appID.

### 2.页面（web/app/小程序） <a id="42"></a>

对于 web 端可以这样理解： / 是 [https://www.growingio.com\*\*/\*\*](https://www.growingio.com**/**) 的页面。 /circle 是 [https://www.growingio.com\*\*/circle\*\*](https://www.growingio.com**/circle**) 的页面。

对于 app 端可以这样理解： android : activity + fragment iOS : UIViewController

小程序：页面URL（不包括query）

### 3.页面来源（web/app/小程序） <a id="43"></a>

这次访问中 [https://www.growingio.com/circle](https://www.growingio.com/circle) 这个页面的页面来源是 [https://www.growingio.com/](https://www.growingio.com/) 。

> **事件级维度：当次事件发生时，对应的维度**

### 4.设备方向（app） <a id="44"></a>

可以理解为用户的手机时横屏还是竖屏。

### 5.元素内容（web/app/小程序） <a id="45"></a>

通过圈选可定义的维度包括“元素内容“ 和 “元素位置“。

圈选某个元素时，如果该元素本身有 "内容"信息，即可用 "元素内容" 来统计该元素对应的指标。

### 6.元素位置（web/app/小程序） <a id="46"></a>

如果该元素本身有 "位置"信息，即可用 "元素位置"来统计该元素对应的指标。

**案例：**我们在圈选时只能看到一种元素，但是可能用户看到的网站内容不一样，元素的内容也不一样，因此，当我们在定义一个元素时，要思考我们想要统计的是「现在这个位置的按钮点击情况」还是「这个位置上这个内容的按钮的点击情况」。常见于商品位、AB测试等使用场景。

在下图中，有一部分用户看到的按钮是「立即注册」，还有一部分用户看到的按钮是「免费试用」，因此，如果我想定义这个按钮的点击情况，不管是什么内容，那么就只「限定顺序」，不限定其他条件：

![](https://docs.growingio.com/.gitbook/assets/21_32_36__04_25_2018%20%281%29.jpg)

如果想看这个位置上不同内容的点击情况，可以在「事件分析」中，选择「柱图」，用「元素内容」作为维度，来进行分析。使用「元素位置」作为维度来分析时，可以看到「元素位置」的值都是 2（因为在圈选时限定了元素的位置）。

### 7.时间（web/app/小程序） <a id="47"></a>

以「小时」粒度切分时，代表当前小时的开始到结束； 以「天」粒度切分时，代表北京时间的 0:00-24:00。
{% endtab %}

{% tab title="用户性别" %}
### 微信用户性别 （小程序） <a id="1-wei-xin-yong-hu-xing-bie-xiao-cheng-xu"></a>

小程序特有维度。表示用户在微信端设置的性别。通常为男、女、未知（表示未设置性别信息）。使用前提是小程序SDK获取到微信访问用户属性。
{% endtab %}
{% endtabs %}

