---
description: 为小程序（包括微信、支付宝、百度小程序等）内 H5 页面、微信公众号 H5 应用等提供统一的数据采集 SDK。
---

# 小程序和微信公众号H5 内嵌页 SDK

## 准备条件

获取项目ID，获取方法请参考"项目管理 > 项目概览 > [查看项目基本信息](../../../product-manual/projectmange/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

## 1. 添加跟踪代码

### 1. H5页面添加代码

将以下JS代码复制到H5页面的 **\<head>** 和 **\</head>** 标签之间即可。安装成功后，除 localhost 和 IP 地址外，网址下所有的行为数据都将会被收集。

```javascript
<script type="text/javascript">
      !function(e,t,n,g,i){e[i]=e[i]||function(){(e[i].q=e[i].q||[]).push(arguments)},n=t.createElement("script"),tag=t.getElementsByTagName("script")[0],n.async=1,n.src=('https:'==document.location.protocol?'https://':'http://')+g,tag.parentNode.insertBefore(n,tag)}(window,document,"script","assets.giocdn.com/2.0/gio-wxwv.js","gio");
      // ‘你的appid’为选填项，如果你的微信内嵌页应用有微信分配的appid，建议填写；如果没有，可以留空。
      gio('init', '您的项目ID', '您的 appid', { debug: false });
      gio('send');
</script>
```

### 2. 多端使用同一SDK时的平台判断

需要在SDK初始化时进行平台的配置。

```javascript
gio('init', '您的项目ID', '您的 appid', { 
    platform：'Minp' //支持传入一个判断函数或者一个字符串
});
```

| 应用场景                | 统计平台               |
| ------------------- | ------------------ |
| **微信小程序**内嵌 H5 页面   | Minp（微信小程序）        |
| **微信公众号应用**使用 H5 页面 | wxwv（微信内嵌页应用）      |
| **移动端浏览器**打开 H5 页面  | Web（网页端）           |
| **支付宝小程序**内嵌 H5 页面  | alip（支付宝小程序）       |
| **百度小程序**内嵌 H5 页面   | baidup（百度小程序）      |
| **字节跳动小程序**内嵌 H5 页面 | bytedance（字节跳动小程序） |
| **QQ小程序**内嵌 H5 页面   | qq（QQ小程序）          |

### 3. 根据使用端的场景进行其他配置

配置平台：（以支付宝小程序为例， WebView加载的H5 页面）

判断平台，加入如下代码，并在platform 中传值”alip“。

```javascript
<!-- GrowingIO Analytics code version 2.1 -->
<!-- Copyright 2015-2017 GrowingIO, Inc. More info available at http://www.growingio.com -->
<script type='text/javascript'>
!function(e,t,n,g,i){e[i]=e[i]||function(){(e[i].q=e[i].q||[]).push(arguments)},n=t.createElement("script"),tag=t.getElementsByTagName("script")[0],n.async=1,n.src=('https:'==document.location.protocol?'https://':'http://')+g,tag.parentNode.insertBefore(n,tag)}(window,document,"script","assets.giocdn.com/2.0/gio-wxwv.js","gio");
gio('init', '你的 GrowingIO 项目ID', '你的支付宝小程序的 AppID', {
    platform: 'alip'
});
gio('send');
</script>
```

#### **H5页面与小程序**打通用户数据[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.3/commonlyApi#%E4%B8%8Eh5%E6%89%93%E9%80%9A%E7%94%A8%E6%88%B7%E6%95%B0%E6%8D%AEgetgioinfo) <a href="#yu-h5-da-tong-yong-hu-shu-ju-getgioinfo" id="yu-h5-da-tong-yong-hu-shu-ju-getgioinfo"></a>

当有H5页面需要获取小程序SDK采集用户数据的需求时(将H5页面采集的数据需要与小程序采集的数据做关联分析)，调用此接口可将获取以下数据

```javascript
gio('getGioInfo');
```

**注意：**\
**1）gio('getGioInfo') 返回的是一个 search 字符串，需要您在字符串前手动拼接 ? 或 & 符号。请拼接在 URL 的查询参数中；如果 URL 中有 Hashtag（#），不能拼接在 Hashtag（#）后的查询参数中。**

\
**2）gio('getGioInfo')获取的数据是一次性的，非动态获取，如果切换用户导致sessionId或userId等用户信息变动时，需要您销毁当前webview重设地址。并且使用不保留当前页面的跳转方式跳出承载webview的小程序页面。**

**示例**

```javascript
举例：
# webview.js
Page({
  data: { url: '' },
  onShow() {
    // 每次onShow时设url的值，保证getGioInfo拿到的是最新值
    this.setData({ url: `https://www.growingIO.com?${gio('getGioInfo')}` });
  },
  onHide() {
    // 退出webview承载页时要销毁webview，保证下次进入时是一个拿到最新数据的全新页面
    this.setData({ url: '' });
  },
  // 如果页面中有登录，需要在登录之后重设一次url的值
  handleLogin() {
    ...
    // 登录完成后重设一次url的值，保证先销毁webview，getGioInfo拿到的是最新值
    this.setData({ url: '' }, () => {
      this.setData({ url: `https://www.growingIO.com?${gio('getGioInfo')}` });
    });
  }
})



# webview.wxml
<web-view src="{{ webUrl }}"></web-view>
```

**`gio('getGioInfo')`默认获取到的数据示例：**

```javascript
// H5 页面原有的 URL为 :
'https://www.growingio.com/?foo=1#锚点'
```

```javascript
// 小程序WebView加载H5时的拼接示例为
`https://www.growingio.com/?foo=1&${gio('getGioInfo')}#锚点`

```

## 2. 高级配置

内嵌页 SDK 还有以下额外参数可以使用：

| 参数      | 值             | 解释                                                                                                                    |
| ------- | ------------- | --------------------------------------------------------------------------------------------------------------------- |
| hashtag | true \| false | GrowingIO默认不会把 hashtag 识别成页面 URL 的一部分。对于使用 hashtag 进行页面跳转的单页面网站应用来说，可以启用 hashtag 作为标识页面的一部分，将hashtag设置为true，默认为false。 |
| debug   | true \| false | 开启debug可以进行数据的实时调试，默认为false，调试方式为打开开发者工具，在console中查看。                                                                 |
| touch   | true \| false | 设置是否支持touch事件，如果为true则会采集touch事件，否则采集click事件。sdk中会判断当前是否支持touch事件设置默认值。                                               |

### 启用hashtag识别

GrowingIO默认不会把 hashtag 识别成页面 URL 的一部分。对于使用 hashtag 进行页面跳转的单页面网站应用来说，可以启用 hashtag 作为标识页面的一部分，将hashtag设置为true

在 微信小程序项目根目录的 app.js 文件设置参数如下：

```javascript
//如果内嵌页存在微信App_id，建议您填写相应的微信App_id,如果没有，就不用填写
gio('init', '你的项目ID'[,'微信App_id'], { setImp:false, hashtag: true });
```

### 微信用户ID 和 用户属性 <a href="#sdk-wei-xin-yong-hu-shu-xing-she-zhi" id="sdk-wei-xin-yong-hu-shu-xing-she-zhi"></a>

作为用户行为数据分析工具，用户信息的完善会给后续的分析带来很大的帮助。在微信内嵌页中，微信用户属性是非常重要的设置，只有完善了微信用户属性信息，微信的访问用户变量（如下表）才可以在分析工具中使用，交互数据定义、数据校验功能才会方便通过用户微信相关的信息（微信姓名和头像）定位用户。

下面是专门针对用户的两个个接口。

#### 绑定微信用户ID <a href="#bang-ding-wei-xin-yong-hu-id" id="bang-ding-wei-xin-yong-hu-id"></a>

当用户在你的微信内嵌页上授权获取到 openid 后，可以用过 `identify` 接口绑定微信用户ID，后续在 GrowingIO 中使用微信ID创建用户分群。示例代码如下：

```javascript
wx.request({ 
  url: 'https://YOUR_HOST_NAME/wechat/code2key',
  method: 'GET',
  data: { code: res.code }
  success: res => 
    var openid = res.data.openid;
    var unionid = res.data.unionid;
    // ...
    gio('identify', res.data.openid, res.data.unionid)
})
```

#### 设置微信用户信息 <a href="#she-zhi-wei-xin-yong-hu-xin-xi" id="she-zhi-wei-xin-yong-hu-xin-xi"></a>

当用户在你的微信内嵌页上绑定微信信息后，可以通过 `setVisitor` 接口设置微信用户信息，后续在 GrowingIO 中，使用访问用户变量分析这个数据。示例代码如下：

```javascript
wx.getUserInfo({
  success: res => 
    // ...
    gio('setVisitor', res.userInfo);
})
```

微信信息包含**微信昵称**、**微信头像**。

### 登录用户ID <a href="#deng-lu-yong-hu-id" id="deng-lu-yong-hu-id"></a>

设置登录用户ID，可以将用户行为和您业务系统中的用户ID打通，有助于您在分析用户时，能够进一步了解业务价值上的用户核心行为。

#### 设置登录用户 ID <a href="#she-zhi-deng-lu-yong-hu-idsetuserid" id="she-zhi-deng-lu-yong-hu-idsetuserid"></a>

当用户登录之后调用 setUserId API ，设置登录用户 ID 。

| 参数名称   | 参数类型   | 是否必须 | 说明      |
| ------ | ------ | ---- | ------- |
| userId | String | 是    | 用户的登录ID |

```javascript
//setUserId API原型
gio('setUserId', userId);
//setuserId API调用示例
gio('setUserId', '1234567890');
```

#### 清除登录用户 ID <a href="#qing-chu-deng-lu-yong-hu-idclearuserid" id="qing-chu-deng-lu-yong-hu-idclearuserid"></a>

当用户登出之后调用 clearUserId ，清除已经设置的登录用户 ID 。

```javascript
//clearUserId API原型和调用示例
gio('clearUserId');
```

#### 设置登录用户属性

当用户在你的小程序上传了注册用户ID后，可以通过 setUser 接口设置注册用户信息，后续在 GrowingIO 中分析这个数据。示例代码如下：

```javascript
gio('setUserId', user.id); 
gio('setUser', { id: user.id, name: user.name });
```

## 3.设置半自动采集浏览事件

用户标记一个元素并提供自定义事件和变量，SDK负责监控，当此元素出现在可视区域中时发送用户配置的自定义事件和变量。

半自动浏览事件指：

1. 采集用户主动标记的元素，事件类型使用自定义事件类型cstm，需要用户在代码中埋点并且在官网配置自定义事件和变量。
2. 半自动：指用户提供元素的自定义事件和变量内容，SDK根据当前元素是否在屏幕上可见，自动发送一个自定义事件。即：需要用户标记元素并且提供自定义事件和变量，SDK在元素出现在屏幕上时自动发送，不同于track接口发送的cstm事件，调用即发送。

{% hint style="info" %}
注意事项：

* 注意参数是否合法，与埋点 API 一样，eventID 和事件级变量 JSONObject 都有参数限制要求。
* 在元素展示前调用GIO API，GIO 负责监听元素展示并触发事件，半自动化浏览事件SDK 上传的数据类型为 cstm ，和自定义事件是同种类型，所以**需要您在官网新建对应的事件类型和变量，并且强烈建议使用数据校验工具验证埋点事件。**
* 触发 SDK 自动采集时机： 元素从当前屏幕上不可见到可见。
* 对于被追踪元素上方有其它元素遮挡的情况 ，GrowingIO 仍可能发送该元素的展示事件 （适配这种case会消耗巨大性能，暂时不兼容）。
{% endhint %}

### 配置半自动采集开关

```c
gio('init', ' your projectId', 'your appId', {imp: true})
```

### 标记半自动采集元素

使用此方法标记元素的浏览时，请在console验证cstm事件。

```markup
<body>
    <div>
        <h2 data-gio-imp-track='testImp' data-gio-track-foo='bar' data-gio-track-baz='qux'>标记元素并带上两个事件变量</h2>
    </div>
 </body>
```

以上示例相当于在用户元素出现在可视区域时，我们会对应的执行以下对应的API调用。

```markup
gio('track', 'testImp', { foo: 'bar', baz: 'qux'})
```

## 4. 自定义数据上传API

自定义数据上传API，请参考[自定义数据上传API](../mini-program-sdk/3.7-ji-yi-xia/customize-api.md)。

## 5. 创建应用

请在添加了跟踪代码的页面加载几次，上报数据给 GrowingIO。

在GrowingIO平台的创建内嵌页应用。创建应用请参考查看[创建应用](../../../product-manual/projectmange/application-manage.md#chuang-jian-ying-yong)。

## 6. 验证SDK是否正常采集数据

方式一：[小程序&内嵌页Debugger](../../debugging/minpdebugger.md)

方式二：在SDK中设置了Debug模式后，在开发者工具中查看数据采集日志。

方式三：[数据校验](../../../product-manual/data-center/datacheck/)
