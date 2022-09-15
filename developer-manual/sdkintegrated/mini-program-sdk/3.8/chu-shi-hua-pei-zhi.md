# 初始化配置

## 配置一览表[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/initSettings#%E9%85%8D%E7%BD%AE%E4%B8%80%E8%A7%88%E8%A1%A8) <a href="#pei-zhi-yi-lan-biao" id="pei-zhi-yi-lan-biao"></a>

下表中列出了所有小程序SDK的配置项，请按需设置。如您不确定是否需要，请咨询我们。

| **字段名**       | **参数类型**  | **默认值** | **说明**                           |
| ------------- | --------- | ------- | -------------------------------- |
| `autotrack`   | `boolean` | `true`  | 是否开启无埋点采集，集成无埋点插件后默认开启无埋点采集      |
| `cml`         | `any`     | `-`     | 使用 Chameleon 开发时使用的实例，参考集成示例代码   |
| `comAsPage`   | `boolean` | `false` | 是否将 Component 组件 当做 Page 处理      |
| `dataCollect` | `boolean` | `true`  | 是否开启数据采集                         |
| `debug`       | `boolean` | `false` | 是否开启调试模式                         |
| `followShare` | `boolean` | `true`  | 是否跟踪分享数据                         |
| `forceLogin`  | `boolean` | `false` | 是否开启强制登录模式                       |
| `remax`       | `any`     | `-`     | 使用 Remax 开发时使用的实例，参考集成示例代码       |
| `taro`        | `any`     | `-`     | 使用 Taro 开发时使用的实例，参考集成示例代码        |
| `taroVue`     | `any`     | `-`     | 使用 Taro3vue2/3 开发时使用的实例，参考集成示例代码 |
| `uniVue`      | `any`     | `-`     | 使用 uni-app 开发时使用的实例，参考集成示例代码     |
| `version`     | `string`  | `-`     | 小程序发版版本号(建议填写)                   |
| `wepy`        | `any`     | `-`     | 使用 WePY 开发时使用的实例，参考集成示例代码        |

## 配置项详解[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/initSettings#%E9%85%8D%E7%BD%AE%E9%A1%B9%E8%AF%A6%E8%A7%A3) <a href="#pei-zhi-xiang-xiang-jie" id="pei-zhi-xiang-xiang-jie"></a>

### autotrack[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/initSettings#autotrack) <a href="#autotrack" id="autotrack"></a>

默认情况下，SDK会自动开启无埋点采集。如果您不需要无埋点采集，可以通过初始化设置 `autotrack: false` 进行关闭。

```javascript
gio('init', ' GrowingIO 项目ID', '您的小程序AppID', {
  version: '1.0.0',
  autotrack: false  
});
```

关闭无埋点后 **`clck` 元素点击, `chng` 输入框内容变化, `sbmt`** **表单提交事件**将不会再被采集和上报。

您也可以通过调用动态修改配置接口来修改它。示例代码如下：

```javascript
gio('setOption', 'autotrack', true | false);
```

### comAsPage[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/initSettings#comaspage) <a href="#comaspage" id="comaspage"></a>

有时您可能会使用 Component 来代替 Page 进行代码编写。此时你需要设置 `comAsPage: true` 来将 Component 当做 Page 处理发送 PAGE 事件。

```javascript
gio('init', ' GrowingIO 项目ID', '您的小程序AppID', {
  version: '1.0.0',
  comAsPage: true  
});
```

**注意：**\
**一旦开启此配置，小程序中所有Component组件都会被视为一个页面，组件生命周期 page.show 一旦触发即发送page事件。**

### dataCollect <a href="#datacollect" id="datacollect"></a>

{% hint style="info" %}
如果您的小程序需要进行合规检查，请参考[小程序合规说明](https://docs.growingio.com/v3/developer-manual/sdkintegrated/compliance/xiao-cheng-xu-sdk-he-gui-shuo-ming)
{% endhint %}

默认情况下，SDK开启数据采集。如果您需要初始化时暂时关闭数据采集，可以通过指定 `dataCollect: false` 关闭。 初始化关闭数据采集后，至您打开数据采集之前都不会采集数据和上报。

```javascript
gio('init', ' GrowingIO 项目ID', '您的小程序AppID', {
  version: '1.0.0',
  dataCollect: false  
});
```

您也可以通过调用动态修改配置接口来修改它。参考代码如下：

```javascript
gio('setOption', 'dataCollect', true | false);
// <3.8.0版本的写法仍兼容，但不建议您再这么使用 // gio('setDataCollect', true | false);
```

### debug[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/initSettings#debug) <a href="#debug" id="debug"></a>

在开发时设置 `debug: true`，打开开发者工具控制台，即可看到实时采集的数据。

```javascript
gio('init', ' GrowingIO 项目ID', '您的小程序AppID', {
  version: '1.0.0',
  debug: true 
});
```

您也可以通过调用动态修改配置接口来修改它。参考代码如下：

```javascript
gio('setOption', 'debug', true | false);
// <3.8.0版本的写法仍兼容，但不建议您再这么使用 // gio('enableDebug', true | false);
```

### followShare[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/initSettings#followshare) <a href="#followshare" id="followshare"></a>

默认情况下，SDK开启跟踪分享数据功能，详细的进行转发分享的统计，来帮助您更好的分析。如您不需要此功能，可以通过指定 `followShare: false` 来关闭跟踪分享。

```javascript
gio('init', ' GrowingIO 项目ID', '您的小程序AppID', {
  version: '1.0.0',
  followShare: false  
});
```

在分享回调方法中，添加 `contentType` 和 `contentId` 字段。例如：

```javascript
onShareAppMessage: function(result) {
  return {
    ...result,
    title: '自定义分享标题',
    path: 'xxxxxx',
    contentType: '内容类型',
    contentId: '内容ID'
  }
},

onShareTimeline: function(result) {
  return {
    ...result,
    title: '自定义朋友圈标题',
    query: 'xxxxxx',
    contentType: '内容类型',
    contentId: '内容ID'
  }
}
```

### forceLogin <a href="#forcelogin" id="forcelogin"></a>

默认情况下，SDK 会自动生成访问用户ID来标识访问用户。这个用户标识符潜在可能会被`clearStorage` 清除掉，所以有可能不同的自动生成访问用户ID对应同一个微信里的 `OpenID。`如您需要使用 openId 或 unionId 标识访问用户，可以在初始化配置中设置 `forceLogin: true` 来打开强制登录模式。

强制登录模式适用于打开小程序就调用 `wx.login` ([参考文档](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/login/wx.login.html)) 获取 openId 或 unionId 的小程序。 开启此模式并调用 `identity` 上报 openid 或 unionId，会将上报的 Id 作为访问用户ID，有助于访问用户数据关联性分析。

设置`forceLogin`为`true`后，SDK会暂停上报数据，待调用 `wx.login`后获取 openId 或 unionId，调用 `identify` 方法后开始数据上报。**调用 `identify` 会替换事件数据的 deviceId 为设定值（一般是小程序openId 或 unionId），包括调用`identify`之前触发的事件。**

```javascript
gio('init', ' GrowingIO 项目ID', '您的小程序AppID', {
  version: '1.0.0',
  forceLogin: true 
});
```

```javascript
gio('identify', openId, unionId);
```

{% hint style="danger" %}
适用于打开小程序就调用 `wx.login` 获取 openId 或 unionId 的小程序。

小程序SDK初始化时配置了 `forceLogin` 为 `true`，如果打开小程序后没有调用 `wx.login` 获取 openId 或 unionId，没有调用 `identify` 方法，会导致SDK不能上报数据，访问数据将大幅减少。如果调用了`，但时机不在小程序打开时，而在小程序使用中较晚的时机，在调用之前若小程序关闭则会造成此次访问过程中采集的数据丢失。`

如果您不能确定是否要设置这个参数，请先咨询我们技术支持。
{% endhint %}

### version <a href="#qi-ta" id="qi-ta"></a>

此配置项建为小程序应用版本号，强烈建议填写，每次发布小程序新版本时更新版本号， 与线上发布小程序保持一致; 可以在 GrowingIO 平台使用 “App 版本”维度，分析不同版本的数据。

### 其他[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/initSettings#%E5%85%B6%E4%BB%96) <a href="#qi-ta" id="qi-ta"></a>

**`cml` , `taroVue` , `taro` , `uniVue` , `wepy` , `remax`**为小程序开用的框架实例，请参考集成使用。
