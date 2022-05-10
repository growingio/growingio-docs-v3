# QQ小程序SDK

## 准备条件

获取项目ID，获取方法请参考"项目管理 > 项目概览 > [查看项目基本信息](../../../product-manual/projectmange/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

## 1. 添加跟踪代码

根据QQ小程序框架选择SDK并添加跟踪代码

参照小程序的开发框架，下载相应的SDK，并添加跟踪代码。

* QQ 原生框架
* Taro 框架
* uni-app 框架

{% tabs %}
{% tab title="QQ原生框架" %}
### 1.下载 gio-qq-minp.js 文件

把文件放在QQ小程序项目里，比如 utils 目录下。

```
curl --compressed https://assets.giocdn.com/sdk/gio-qq-minp.js -o gio-qq-minp.js
```

### 2、添加跟踪代码

方式一：

在根目录 app.js 文件的顶部添加跟踪代码。

```java
var gio = require("utils/gio-qq-minp.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本' });
```

方式二：

步骤一：新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数。

```java
export default {
projectId: '你的 GrowingIO 项目ID',
appId: '你的小程序AppID',
version: '小程序版本'
...
}
```

步骤二：在根目录 app.js文件的顶部添加跟踪代码

```java
var gio = require("utils/gio-qq-minp.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}

{% tab title="Taro框架" %}
### 1.下载 gio-qq-minp.js 文件

把文件放在QQ小程序项目里，比如 utils 目录下。

```
curl --compressed https://assets.giocdn.com/sdk/gio-qq-minp.js -o gio-qq-minp.js
```

### 2、添加跟踪代码

方式一：

在根目录 app.js 文件的顶部添加跟踪代码。

```java
import Taro from '@tarojs/taro';
var gio = require("utils/gio-qq-minp.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', taro: Taro });
```

方式二：

步骤一：新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数。

```java
import Taro from '@tarojs/taro';
export default {
projectId: '你的 GrowingIO 项目ID',
appId: '你的小程序AppID',
version: '小程序版本',
taro: Taro,
...
}
```

步骤二：在根目录 app.js文件的顶部添加跟踪代码。

```java
var gio = require("utils/gio-qq-minp.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}

{% tab title="uni-app框架" %}
### 1.下载 gio-qq-minp.js 文件

把文件放在QQ小程序项目里，比如 utils 目录下。

```
curl --compressed https://assets.giocdn.com/sdk/gio-qq-minp.esm.js -o gio-qq-minp.js
```

### 2、添加跟踪代码

方式一：

在根目录 app.js 文件的顶部添加跟踪代码。

```java
import Vue from 'vue';
import App from './App';
App.mpType = 'app';
var gio = require("utils/gio-qq-minp.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', vue: Vue });
```

方式二：

步骤一：新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数。

```java
import Vue from 'vue';
export default {
projectId: '你的 GrowingIO 项目ID',
appId: '你的小程序AppID',
version: '小程序版本',
vue: Vue
...
}
```

步骤二：在根目录 app.js文件的顶部添加跟踪代码。

```java
var gio = require("utils/gio-qq-minp.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}
{% endtabs %}

## 2. SDK参数配置

建议每次发布小程序新版本的时候，更新一下版本号 version，可以在 GrowingIO 分析不同版本的数据。除了 version 之外，还有以下额外参数可以使用。

| 参数                  | 值              | 解释                                    |
| ------------------- | -------------- | ------------------------------------- |
| version             | string         | 你的小程序的版本号                             |
| getLocation autoGet | true \| false  | 是否自动获取用户的地理位置信息。默认false               |
| getLocation type    | wgs84 \| gcj02 | gcj02 为火星坐标系                          |
| followShare         | true \| false  | 详细跟踪分享数据，开启后可使用分享分析功能。默认true          |
| forceLogin          | true \| false  | 你的 QQ 小程序是否强制要求用户登陆获取 openid。默认 false |
| debug               | true \| false  | 是否开启调试模式，可以看到采集的数据。默认 false           |

### 采集GPS数据

#### 配置 `getLocation`

GrowingIO SDK 默认不采集地理位置信息。

如您需要在小程序打开时获取用户地理位置信息，需在初始化配置项中设置 `autoGet: true` 来打开此功能。同时您可能需要配置项目的`permission`字段：[参考文档](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#permission)：

```java
getLocation: {          //是否自动获取用户的地理位置信息, 并设置获取方式
   autoGet: true,       //默认不自动获取
   type: 'gcj02'           //支持wgs84 | gcj02为火星坐标系, 默认wgs84
},
```

如果您初始化配置项中没有打开此功能，当用户访问至某一功能需要位置信息时，可以手动调用获取地理位置接口，自动补发访问事件，采集位置信息，提升用户地域分布的分析准确性。

```java
// 获取用户的地理信息
gio('getLocation')
```

{% hint style="danger" %}
**如果您初始化开启getLocation配置，用户打开小程序即需要授权；手动调用getLocation方法时，需要用户授权。都需要配置项目中的`permission`字段：**[**参考文档**](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#permission)
{% endhint %}

### 跟踪分享数据

#### 配置`followShare`

转发分享小程序是小程序获客的重要场景，默认情况下，SDK开启跟踪分享数据功能，详细的进行转发分享的统计，来帮助您更好的分析。

如您不需要此功能，可以在初始化配置中设置`followShare: false` 来关闭跟踪分享。

在 gioConfig.js 文件或初始化配置项中将 followShare 配置如下:

```javascript
followShare: false,     //是否详细跟踪分享数据，关闭后不使用分享分析功能。默认true
```

### 强制登录模式

**配置`forceLogin`**

默认情况下，SDK 会自动生成访问用户ID来标识访问用户，存储在 Storage 里面。这个用户标识符潜在可能会被`clearStorage` 清除掉，所以有可能不同的自动生成访问用户ID对应同一个QQ用户里的 `OpenID。`

如您需要使用 openId 或 unionId 标识访问用户，可以在初始化配置中设置 `forceLogin: true` 来打开强制登录模式。

强制登录模式适用于打开小程序就调用 `wx.login` ([参考文档](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/login/wx.login.html)) 获取 openId 或 unionId 的小程序。 开启此模式并调用 `identity` 上报 openid 或 unionId，会将上报的 Id 作为访问用户ID，

设置`forceLogin`为`true`后，SDK会继续采集但暂停上报数据，待调用 `wx.login`后获取 openId 或 unionId，调用 `identify` 方法后开始数据上报。**调用 `identify` 会替换事件数据的 u(访问用户ID) 字段的值 为设定值（一般是小程序openId 或 unionId），包括调用`identify`之前触发的事件**

需在 gioConfig.js 文件或初始化配置项将 forceLogin 配置如下:

```javascript
forceLogin: true, //是否强制要求调用 wx.login 获取 opend 或 unionId。默认 false
```

获取到 openId 或  unionId 后调用 [`identify`](qq-sdk.md#bang-ding-wei-xin-yong-hu-openid-unionid) 接口。

{% hint style="danger" %}
适用于打开小程序就调用 `wx.login` 获取 openId 或 unionId 的小程序。

小程序SDK初始化时配置了 `forceLogin` 为 `true`，如果打开小程序后没有调用 `wx.login` 获取 openId 或 unionId，没有调用 `identify` 方法，会导致SDK不能上报数据，访问数据将大幅减少。如果调用了`，但时机不在小程序打开时，而在小程序使用中较晚的时机，在调用之前若小程序关闭则会造成此次访问过程中采集的数据丢失。`\


如果您不能确定是否要设置这个参数，请先咨询我们技术支持。
{% endhint %}

## 3. 添加请求服务器域名

要正常采集QQ小程序的数据并发送给 GrowingIO，需要在QQ小程序里事先设置一个通讯域名，允许跟 GrowingIO API 服务器进行网络通信。具体步骤如下：

1. 登录QQ小程序后台，进入配置
2. 打开开发设置，到服务器域名配置部分
3. 在request合法域名中添加：`https://wxapi.growingio.com`

## 4. QQ小程序 用户属性设置

作为用户行为数据分析工具，用户信息的完善会给后续的分析带来很大的帮助。在小程序中，QQ用户属性是非常重要的设置，只有完善了QQ用户属性信息，QQ的访问用户变量（如下表）才可以在分析工具中使用，交互数据定义、数据校验功能才会方便通过用户QQ相关的信息（QQ姓名和头像）定位用户。

下面是专门针对用户的接口。

### 绑定QQ用户ID

当用户在你的小程序上登陆获取到 openid 后，可以用过 identify 接口绑定QQ用户ID，后续在 GrowingIO 中获取更准确的QQ访问用户量。示例代码如下：

```java
qq.request({
  url: 'https://YOUR_HOST_NAME/wechat/code2key',
  method: 'GET',
  data: { code: res.code },
  success: function(res) {
    var openid = res.data.openid;
    var unionid = res.data.unionid;
    ...
    gio('identify', openid, unionid);
  }
})
```

### 设置QQ用户信息

当用户在你的小程序上绑定QQ信息后，可以通过 setVisitor 接口设置QQ用户信息，后续在 GrowingIO 中分析这个数据。示例代码如下：

```java
qq.getUserInfo({
  success: function(res) {
    ...
    gio('setVisitor', res.userInfo);
  }
})
```

QQ信息包含**QQ昵称**、**QQ头像**、**性别**、**QQ所填国家**、**QQ所填省份**、**QQ所填城市**。

{% hint style="info" %}
\*注：用户画像中的部分数据，只有在设置QQ用户信息后，才可以统计。
{% endhint %}

## 5. 无埋点采集逻辑和高级配置

在进行无埋点数据采集时，您需要了解和使用[无埋点采集逻辑及行为数据采集的高级配置](wu-mai-dian-cai-ji-luo-ji-he-gao-ji-pei-zhi.md)

## 6. 自定义数据上传API

自定义数据上传API，请参考[自定义数据上传API](customize-api.md)。

## 7. 创建应用

请在添加了跟踪代码的支付宝小程序重新启动几次，发送数据给 GrowingIO。

在GrowingIO平台的创建微信小程序应用。创建应用请参考查看[创建应用](../../../product-manual/projectmange/application-manage.md#chuang-jian-ying-yong)。

## 8. 验证SDK是否正常采集数据

方式一：[小程序&内嵌页Debugger](../../debugging/minpdebugger.md)

方式二：在SDK中设置了Debug模式后，在开发者工具中查看数据采集日志。

方式三：[数据校验](broken-reference)
