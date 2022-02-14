---
description: 运行时 API 可对 SDK 进行采集上报数据的控制。
---

# 运行时API

GrowingIO为App提供运行时随意调用的API，使用方法如下：

{% tabs %}
{% tab title="Java" %}
```java
// 得到 GrowingIO 实例后可以调用其中 API
GrowingIO gio = GrowingIO.getInstance();
gio.setUserId("张溪梦");
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
val gio = GrowingIO.getInstance()
gio.userId = "张溪梦"
```
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
GrowingIO所有API都需要在主线程调用。
{% endhint %}

## 基础配置API

| API              | 说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | 无埋点SDK版本支持 | 埋点SDK版本支持 |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------- |
| setGeoLocation   | 设置经纬度，并在 vst 事件中发送，Android SDK 暂时没办法自动获取`GPS`数据，如果您要采集`GPS`数据，需要在您的App每次获取完`GPS`数据之后，通过该`API`告知 SDK。如果您不设置，我们默认使用用户`IP`的`Location。`                                                                                                                                                                                                                                                                                                                                                   | ALL        | ALL       |
| clearGeoLocation | 清空经纬度                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | ALL        | ALL       |
| setViewInfo      | <p>配置 view 的 Tag，标记 View ，并在 GrowingIO 相关事件中发送 ，内容对应 <code>xPath</code> 中的 <code>obj</code></p><p>例如：在商品<code>ListView</code>添加购物车的场景中，每个商品<code>item</code>都含有一个加入购物车按钮，这时无法区分商品<code>item</code>与将它加入购物车按钮的一对一关系，此时调用此方法增加描述。</p><p>注意：适用于原有<code>v</code>字段含义不大，只关注描述的场景，使用此接口后<code>v</code>字段将不采集</p>                                                                                                                                                                            | ALL        | -         |
| setViewContent   | <p>配置 view 的 Tag，标记 View ，并在 GrowingIO相关事件中发送，内容对应 <code>xPath</code> 中的 <code>v</code></p><p>SDK默认不会采集ImageView的内容，为了能对不同的图片元素（ImageView）区分统计，需要对每个具有分析意义的图片元素（ImageView）添加描述。</p>                                                                                                                                                                                                                                                                                                   | ALL        | -         |
| setViewID        | <p>设置 View id ，配置之后对应 xPath 中的 view id，SDK将会使用Layout文件中的ID来识别一个元素。</p><p>如果部分元素在Layout文件中没有ID，建议在Layout文件中添加。</p><p>对于动态生成的元素，可以使用如下方法对它设置唯一的ID。</p><p>当您的应用界面改版时，可能会导致无法准确地统计已经圈选的元素。因此，对于应用中的主要流程涉及到的界面元素，建议您为它们设置固定的唯一ID，以保证数据的一致性。</p><ul><li>ID 只能设置为字母、数字和下划线的组合</li><li>如果在ViewGroup上设置ID的话，SDK会忽略他所有子元素的默认ID（就是写在xml文件里的）只会使用GrowingIO.setViewID设置的ID。</li><li>对于已经集成过旧版SDK并圈选过的应用，对某个元素设置ID后再圈选它，指标数值会从零开始计算，类似初次集成SDK后发版的效果，但不影响之前圈选的其它指标数据。如果不希望出现这种情况，请不要使用这个方法</li></ul> | ALL        | -         |
| setChannel       | <ul><li><strong>&#x3C;2.6.5 版本</strong>： 先设置渠道信息，再发送数据 能够保证所有数据都一定会带上渠道信息。</li><li><strong>>=2.6.5 版本</strong>： 保留原有设置渠道信息的方法，新增在运行时设置渠道信息。新增的接口无法保证所有数据都一定会带上渠道信息（虽然我们会通过重发机制进行保证，但是无法做到100%）。</li></ul>                                                                                                                                                                                                                                                                             | ALL        | -         |

\### 数据采集API

| API                | 说明                                                                                                                                                                                                                                                             | 无埋点SDK版本支持 | 埋点SDK版本支持 |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------- |
| isDeeplinkUrl      | 校验链接URI是否满足GIO的格式，如"gio.ren"或".datayi.cn"结尾等                                                                                                                                                                                                                   | >=2.8.11   | -         |
| doDeeplinkByUrl    | true 表示是GIO的deeplink链接，进行下一步判断， false 表示非GIO相关链接.参数callback不填则默认使用全局初始化时设置的callback                                                                                                                                                                            | >=2.8.11   | -         |
| disableDataCollect | 遵守欧洲联盟出台的通用数据保护条例，用户不授权，不采集用户数据                                                                                                                                                                                                                                | >=2.3.2    | ALL       |
| enableDataCollect  | 遵守欧洲联盟出台的通用数据保护条例，用户授权，采集用户数据                                                                                                                                                                                                                                  | >=2.3.2    | ALL       |
| disable            | GrowingIO停止采集                                                                                                                                                                                                                                                  | ALL        | ALL       |
| resume             | GrowingIO恢复采集                                                                                                                                                                                                                                                  | ALL        | ALL       |
| stop               | GrowingIO停止采集，可以不在主线程调用                                                                                                                                                                                                                                        | ALL        | ALL       |
| setThrottle        | 是否节流发送（节流发送时imp不发送），内部实际调用 Configuration 中的同名方法，所以在初始化时候配置和运行时动态配置，效果一样。                                                                                                                                                                                       | ALL        | -         |
| setImp             | `imp`事件开关，`true` 为打开                                                                                                                                                                                                                                           | ALL        | -         |
| disableImpression  | 不发送`imp`                                                                                                                                                                                                                                                       | ALL        | -         |
| ignoredView        | <p>忽略配置的 View ，不采集用户数据。</p><p>如果您需要忽略某些特殊内容，比如倒计时元素或涉及隐私的内容，可以使用此接口。</p>                                                                                                                                                                                       | ALL        | -         |
| ignoreFragment     | 不采集配置的 Fragment 页面浏览事件（`page`），不将`Fragment`视作一个页面，可以理解成当作为一个可点击的view。自动采集用户行为事件（`clck、chng`）和元素展示事件（`imp`）。                                                                                                                                                    | ALL        | -         |
| ignoreFragmentX    | 支持 AndroidX ， 功能同 ignoreFragment。                                                                                                                                                                                                                              | >=2.6.6    | -         |
| ignoreViewImp      | <p>忽略配置的 View ，不采集用户元素浏览数据。</p><p>如果您需要忽略某些大量的 数据，比如弹幕，可以使用此接口。</p>                                                                                                                                                                                            | >=2.6.7    | -         |
| setPageName        | <p>设置页面别名，有些时候，对于完成某个功能的页面，统计时可能需要进一步细分。 比如，对于展示商品列表的页面，需要区分衣物类商品，以及食品类商品的两种列表的访问量。</p><p>​</p><p>注意</p><ol><li>必须在该<code>Activity</code>的<code>onCreate</code>方法中完成该属性的赋值操作。</li><li>页面别名只能设置为字母、数字和下划线的组合。</li><li>为查看数据方便，请尽量对iOS和安卓的同功能页面取不同的名称。</li></ol> | ALL        | -         |
| setPageNameX       | 支持 AndroidX ， 功能同 setPageName。                                                                                                                                                                                                                                 | >=2.6.6    | -         |
| getSessionId       | 得到 session id                                                                                                                                                                                                                                                  | ALL        | ALL       |
| getDeviceId        | 获取设备id，对应数据采集的`u`字段，又称为`匿名用户id`，用来定义一台设备，SDK 自动生成。                                                                                                                                                                                                             | ALL        | ALL       |
| ​trackBanner       | 设置所有广告图对应的广告内容描述，内容描述需要跟广告的顺序相同。                                                                                                                                                                                                                               | ALL        | -         |



| trackEditText       | <p>SDK 默认不采集用户输入框的内容，设置以后，采集除了密码以外的输入框文本内容。​​</p><p>当这个输入框失去焦点（包括应用退到后台），且输入框内容跟获取焦点前相比发生变化时，输入框内文字会被发送回GrowingIO。</p><p>注意：对于密码输入框，即便标记为需要采集，SDK也会忽略，不采集它的数据。</p>                                                     | ALL      | -       |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | ------- |
| trackFragment       | <p>如果APP初始化时候，没有设置 <code>trackAllFragment</code> 即不采集全部 <code>Fragment</code>，可以选择性采集指定 <code>Fragment</code>，设置之后 sdk 将监听 <code>Fragment</code> 的各个生命周期， 采集相关用户行为数据。</p><p>请在 <code>new Fragment</code> 的时候调用此方法。</p> | ALL      | -       |
| trackFragmentX      | <p>支持 AndroidX ， 功能同 trackFragment。</p><p>请在 <code>new Fragment</code> 的时候调用此方法。</p>                                                                                                                                   | >=2.6.6  | -       |
| trackWebView        | 采集 `WebView` 事件，默认采集，您可以在不全量采集`WebView`的时候，定制采集某个`WebView`                                                                                                                                                             | >=2.8.22 | -       |
| trackX5WebView      | 采集 X5WebView 事件，默认采集                                                                                                                                                                                                   | <2.6.0   | -       |
| setTabName          | 如果您有某些View动态添加到ViewTree中并且在父容器中的位置不固定（例如常见的多Fragment实现的Tab切换），请给每个View设置ID来辅助统计                                                                                                                                        | ALL      | -       |
| setImeiEnable       | 设置为 false 则 SDK 不采集 `imei，`适用于**海外应用市场**上架的应用。                                                                                                                                                                         | >=2.7.8  | -       |
| setAndroidIdEnable  | 设置为 false 则 SDK 不采集 `androidId` ,适用于**海外应用市场**上架的应用。                                                                                                                                                                   | >=2.7.8  | -       |
| setGoogleAdIdEnable | 设置为 false 则 SDK 不采集 `GoogleAdId` ,适用于**海外应用市场**上架的应用。                                                                                                                                                                  | >=2.7.8  | -       |
| setOAIDEnable       | 国内[移动安全联盟MSA](http://www.msa-alliance.cn/col.jsp?id=120) 联合各大手机制造商推出了 OAID ， 作为唯一广告标识符。**Android 2.8.5** 新增。                                                                                                           | >=2.8.5  | -       |
| bridgeForWebView    | 提供原生的 WebView bridge供hybrid调用, 支持hybrid事件发送                                                                                                                                                                            | -        | >=2.9.0 |
| bridgeForX5WebView  | 提供腾讯X5内核的WebView bridge供hybrid调用, 支持hybrid事件发送                                                                                                                                                                         | -        | >=2.9.0 |
