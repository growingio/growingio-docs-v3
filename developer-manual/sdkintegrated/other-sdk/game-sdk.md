# 微信小游戏SDK

## 准备条件

获取项目ID，获取方法请参考"项目管理 &gt; 项目概览 &gt; [查看项目基本信息](../../../product-manual/projectmange/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

## 1. 添加跟踪代码

目前支持微信原生小游戏以及所有游戏引擎构建的小游戏，请参照小游戏的开发框架，下载相应的SDK，并添加跟踪代码。

### 选择对应的开发框架添加代码

{% tabs %}
{% tab title="原生小游戏框架" %}
#### 1. 下载小游戏采集 SDK，下载 gio-ming.js 文件。

```java
curl --compressed https://assets.giocdn.com/gio-ming.js -o gio-ming.js
```

#### 2. 将下载好的 gio-ming.js 文件放在微信小游戏项目里，比如 utils 目录下。下面会假设 SDK 文件放在 utils 目录下。

#### 3. 在微信小游戏项目根目录的 game.js 文件的顶部添加以下JS代码。

```javascript
var gio = require("utils/gio-ming.js");
// version 是你的小游戏的版本号
gio('init', '你的 GrowingIO 项目ID', '你的微信小游戏的 AppID', { version: '1.0' });
```
{% endtab %}

{% tab title="使用游戏引擎构建微信小游戏" %}
#### 1. 下载小游戏采集 SDK，下载 gio-ming.js 文件。

```java
curl --compressed https://assets.giocdn.com/gio-ming.js -o gio-ming.js
```

#### 2. 将下载好的 gio-ming.js 文件放在微信小游戏项目目录中（一般为assets目录）。

#### 3. 在初始场景文件最上面引入SDK

```java
var gio = require("utils/gio-ming.js");
```

#### 4. 在初始场景文件 start 方法中init

```java
// version 是你的小游戏的版本号
gio('init', '你的 GrowingIO 项目ID', '你的微信小游戏的 AppID', { version: '1.0' });
```

#### 5. 初始场景文件示例

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LatAo-FMcDE3qcUgoZC-LatG-_U2BA1761miEpnimage.png)
{% endtab %}
{% endtabs %}

### SDK参数配置

SDK中提供了以下几个参数可以用来进行配置。

| 参数 | 类型/值 | 说明 |
| :--- | :--- | :--- |
| version | string | 你的小游戏的版本号 |
| forceLogin | true \| false | 你的小游戏是否强制要求用户登陆微信获取 openid。默认 false |
| followShare | true \| false | 详细跟踪微信组件中的wx. shareAppMessage事件的转发分享数据，开启后可使用分享分析功能。默认false |
| getLocation | true \| false | 是否自动获取用户的地理位置信息。默认false |
| debug | true \| false | 是否开启调试模式，可以看到采集的数据。默认 false |

#### version

每次发布小游戏新版本的时候，需要更新一下版本号 version, 与线上发布小游戏保持一致; 可以在 GrowingIO 平台使用 “App 版本”维度，分析不同版本的数据。

#### getLocation

根据微信最新的用户地理位置获取的规则，GrowingIO 小游戏SDK 默认不会在小游戏启动时获取用户的坐标信息。

* 如果您的小游戏在打开时就需要获取用户地理信息，就可以将这个参数配置为true。
* 如果您的小游戏在用户点击某些按钮时，才触发获取位置，则可以按照配置方式，进行用户位置的补发，从而增强用户地理位置的分析能力。

#### followShare

转发分享小游戏是小游戏获客的重要场景，想要详细的进行转发分享的统计，需要在SDK参数中设置如下参数，默认值为false

| 参数 | 开启值 | 说明 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">followShare</th>
      <th style="text-align:left">true</th>
      <th style="text-align:left">
        <p>&#x8BE6;&#x7EC6;&#x8DDF;&#x8E2A;&#x5FAE;&#x4FE1;&#x7EC4;&#x4EF6;&#x4E2D;&#x7684;wx.
          shareAppMessage&#x4E8B;&#x4EF6;&#x7684;&#x8F6C;&#x53D1;&#x5206;&#x4EAB;&#x6570;&#x636E;&#xFF0C;&#x5F00;&#x542F;&#x540E;&#x53EF;&#x4F7F;&#x7528;&#x5206;&#x4EAB;&#x5206;&#x6790;&#x529F;&#x80FD;&#x3002;</p>
        <p>&#x9ED8;&#x8BA4;&#x4E3A;&#x5173;&#x95ED;false</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

```java
var gio = require("utils/gio-ming.js");
// version 是你的小游戏的版本号，发版时请调整
gio('init', '9c76fe4756c3404d', 'wx87c6f4a3a6cf31e7', { version: '1.0', followShare: true });
//将微信的wx.OnShareAppMessage替换成gio("gioOnShareAppMessage", function(){})
//分享，监听用户点击右上角菜单的“转发”按钮时触发的事件
gio("gioOnShareAppMessage", function(){
return {
title: "试试我的小游戏"
}
})
//将微信的wx. shareAppMessage替换成gio("gioShareAppMessage", {})
//分享，主动拉起转发，进入选择通讯录界面
gio("gioShareAppMessage", {
title: "试试我的小游戏"
}
)
```

如果您希望采用微信的原生接口，那么需要在分享触发事件上做以下配置操作，这样GrowingIO才能采集到分享的数据。

```java
//设置follwShare
gio('init', '', '', { version: '1.0', debug: true, followShare: true});
//分享，监听用户点击右上角菜单的“转发”按钮时触发的事件
//调用 pageShareInfo 发送分享事件以及处理分享追踪信息
wx.onShareAppMessage(function () {
  var obj = {
    title: "试试我的小游戏"
  }
  obj = gio('pageShareInfo', obj);
  return obj;
})
//分享，主动拉起转发，进入选择通讯录界面
//调用 pageShareInfo 发送分享事件以及处理分享追踪信息
obj = gio('pageShareInfo', obj);
wx.shareAppMessage(obj)
```

#### forceLogin

forceLogin 是一个需要特别注意的参数。GrowingIO 默认会在小游戏里面设置用户标识符，存储在微信 Storage 里面。这个用户标识符潜在可能会被 `clearStorage` 清除掉，所以有可能不同的用户标识符对应同一个微信里的 openid。

如果你的微信小游戏在用户打开后会去获取 `openID` ，可以设置 `forceLogin` 为 true。当 forceLogin 为 true 的时候，用户标识符会使用 `openID`，潜在风险是如果用户没有获取到`openID`，数据不会发送，**所以请特别注意这个参数的设置。**

集成示例

```javascript
gio('init', '你的 GrowingIO 项目ID', '你的微信小程序的 AppID', { version: '1.0', forceLogin: true });
...
// 当获取到 openid 后，调用以下方法gio("identify", openid, unionid);
```

## 2. 微信用户信息的配置

上报微信信息，支持按照OpenID、UnionID进行用户分群，以及使用微信推送等高级功能。

### SDK微信用户属性设置

作为用户行为数据分析工具，用户信息的完善会给后续的分析带来很大的帮助。在小程序中，微信用户属性是非常重要的设置，只有完善了微信用户属性信息，微信的访问用户变量（如下表）才可以在分析工具中使用，交互数据定义、数据校验功能才会方便通过用户微信相关的信息（微信姓名和头像）定位用户。

| 微信访问用户变量 |
| :--- |
| 微信用户所在城市 |
| 微信用户所在省 |
| 微信用户所在国家 |
| 微信用户的性别 |

### 用户接口

下面介绍专门针对用户的接口：

#### 绑定微信用户ID（identify）

当用户在你的小程序上登录获取到 OpeniID后，可以用过 `identify` 接口绑定微信用户ID，后续在 GrowingIO 中获取更准确的微信访问用户量。

示例代码：

```java
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

#### 设置微信用户信息（setVisitor）

当用户在你的小程序上绑定微信信息后，可以通过 `setVisitor` 接口设置微信用户信息，后续在 GrowingIO 中分析这个数据。

示例代码：

```java
wx.getUserInfo({ 
  success: res => 
    // ...
    gio('setVisitor', res.userInfo);
})
```

{% hint style="info" %}
微信用户信息包含**微信昵称**、**微信头像**、**性别**、**微信所填国家**、**微信所填省份**、**微信所填城市**。

用户画像中的部分数据，只有在设置微信用户信息后，才可以统计。
{% endhint %}

#### 设置登录用户ID

当用户在你的小游戏上注册以后，你的产品应用服务端会在用户数据库里添加一条记录并且分配一个 ID，可以通过 setUserId 接口设置注册用户ID，后续在 GrowingIO 中分析登录用户这个数据。示例代码如下。设置了注册用户ID后，才可以使用**登录用户变量**。

```java
gio('setUserId', YOUR_USER_ID);
```

#### 清除登录用户ID

用户退出登录时，清除登录用户ID。

```java
gio('clearUserId');
```

#### 设置登录用户属性

当用户在你的小游戏上传了注册用户ID后，可以通过 setUser 接口设置注册用户信息，后续在 GrowingIO 中分析这个数据。示例代码如下：

```java
gio('setUserId', user.id); 
gio('setUser', { id: user.id, name: user.name });
```

## 3. 添加请求服务器域名

要正常采集微信小程序的数据并发送给 GrowingIO，需要在微信小程序里事先设置一个通讯域名，允许跟 GrowingIO API 服务器进行网络通信。具体步骤如下：

1. 登陆微信小程序后台，进入开发。
2. 打开开发设置，到服务器域名配置部分。
3. 在`request合法域名`中添加：[https://wxapi.growingio.com](https://wxapi.growingio.com)

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2837%29.png)

## 4. 自定义数据上传API

{% hint style="info" %}
小程序自定义事件和变量的埋点代码，建议放在onShow的生命周期函数中。
{% endhint %}

自定义数据上传API，请参考[自定义数据上传API](customize-api.md)。

## 5. 创建应用

当集成成功后，需要回到 GrowingIO SDK 集成页面检测数据。请在添加了跟踪代码的小游戏重新启动几次，发送数据给 GrowingIO。

在GrowingIO平台的创建微信小游戏应用。创建应用请参考查看[创建应用](../../../product-manual/projectmange/application-manage.md#chuang-jian-ying-yong)。

## 6. 验证SDK是否正常采集数据

方式一：[小程序&内嵌页Debugger](../../debugging/minpdebugger.md)

方式二：在SDK中设置了Debug模式后，在开发者工具中查看数据采集日志。

方式三：[数据校验]()

