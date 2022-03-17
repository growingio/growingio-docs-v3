# 字节跳动小程序SDK

## 准备条件

获取项目ID，获取方法请参考"项目管理 > 项目概览 > [查看项目基本信息](../../../product-manual/projectmange/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

## 1. 添加跟踪代码

根据字节跳动小程序框架选择 SDK 并添加跟踪代码。

参照小程序的开发框架，下载相应的SDK，并添加跟踪代码。

* 字节跳动 原生框架
* Taro 框架
* mpvue / uni-app 框架

{% tabs %}
{% tab title="原生框架" %}
### 1. 下载 gio-bytedance-minp.js 文件

把文件放在字节跳动小程序项目里，比如 utils 目录下。

```
curl --compressed https://assets.giocdn.com/sdk/gio-bytedance-minp.js -o gio-bytedance-minp.js
```

2、添加跟踪代码

方式一：

在根目录 app.js 文件的顶部添加跟踪代码。

```java
var gio = require("utils/gio-bytedance-minp.js").default;
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

步骤二：在根目录 app.js文件的顶部添加跟踪代码。

```java
var gio = require("utils/gio-bytedance-minp.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}

{% tab title="Taro框架" %}
### 1.下载 gio-bytedance-minp.js 文件

把文件放在字节跳动小程序项目里，比如 utils 目录下。

```
curl --compressed https://assets.giocdn.com/sdk/gio-bytedance-minp.js -o gio-bytedance-minp.js
```

### 2、添加跟踪代码

方式一：

在根目录 app.js 文件的顶部添加跟踪代码。

```java
import Taro from '@tarojs/taro';
var gio = require("utils/gio-bytedance-minp.js").default;
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
var gio = require("utils/gio-bytedance-minp.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}

{% tab title="mpvue框架/uni-app框架" %}
### 1.下载 gio-bytedance-minp.js 文件

把文件放在字节跳动小程序项目里，比如 utils 目录下。

```
curl --compressed https://assets.giocdn.com/sdk/gio-bytedance-minp.esm.js -o gio-bytedance-minp.j
```

### 2、添加跟踪代码

方式一：

在根目录 app.js 文件的顶部添加跟踪代码。

```java
import Vue from 'vue';
import App from './App';
App.mpType = 'app';
var gio = require("utils/gio-bytedance-minp.js").default;
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
var gio = require("utils/gio-bytedance-minp.js").default;
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
| forceLogin          | true \| false  | 你的小程序是否强制要求用户登陆字节跳动获取 openid，默认 false |
| debug               | true \| false  | 是否开启调试模式，可以看到采集的数据。默认 false           |

### 跟踪分享数据

#### 配置`followShare`

转发分享小程序是小程序获客的重要场景，默认情况下，SDK开启跟踪分享数据功能，详细的进行转发分享的统计，来帮助您更好的分析。

如您不需要此功能，可以初始化配置中设置 `followShare: false` 来关闭跟踪分享。

即小程序项目根目录的 app.js 文件设置参数如下：

```
var gio = require("utils/gio-alip.js");
// version 是你的小程序的版本号，发版时请调整
gio('init', '您的项目ID', '您的字节小程序AppID', { version: '1.0', followShare: true });
```

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

### 强制登录模式

**配置`forceLogin`**

默认情况下，SDK 会自动生成访问用户ID来标识访问用户，存储在 Storage 里面。这个用户标识符潜在可能会被`clearStorage` 清除掉，所以有可能不同的自动生成访问用户ID对应同一个字节小程序用户的 userId

如您需要使用 userId 标识访问用户，可以在初始化配置中设置 `forceLogin: true` 来打开强制登录模式。

强制登录模式适用于打开小程序就调用登陆并且获取 userId 的小程序。 开启此模式并调用 `identity` 上报 userId，会将上报的 userId 作为访问用户ID。

设置`forceLogin`为`true`后，SDK会继续采集但暂停上报数据，待调用 登陆并且获取 userId，调用 `identify` 方法后开始数据上报。**调用 `identify` 会替换事件数据的 u(访问用户ID) 字段的值 为设定值（一般是小程序的 userId），包括调用`identify`之前触发的事件。**

获取到 **userId** 后调用 [`identify`](byte-dance.md#bang-ding-zi-jie-tiao-dong-yong-hu-id) 接口。

{% hint style="danger" %}
适用于打开小程序就调用登陆并且获取 userId `的小程序`。

小程序SDK初始化时配置了 `forceLogin` 为 `true`，如果打开小程序后没有调用登陆并且获取`userid`，没有调用 `identify` 方法，会导致SDK不能上报数据，访问数据将大幅减少。如果调用了`，但时机不在小程序打开时，而在小程序使用中较晚的时机，在调用之前若小程序关闭则会造成此次访问过程中采集的数据丢失。`\


如果您不能确定是否要设置这个参数，请先咨询我们技术支持。
{% endhint %}

## 3. 添加请求服务器域名

要正常采集字节跳动小程序的数据并发送给 GrowingIO，需要在字节跳动小程序里事先设置一个通讯域名，允许跟 GrowingIO API 服务器进行网络通信。具体步骤如下：

1. 登录字节跳动小程序后台，进入配置
2. 打开开发设置，到服务器域名配置部分
3. 在request合法域名中添加：[https://wxapi.growingio.com](https://wxapi.growingio.com)

## 4. 字节跳动小程序 用户属性设置

作为用户行为数据分析工具，用户信息的完善会给后续的分析带来很大的帮助。在小程序中，字节跳动用户属性是非常重要的设置，只有完善了字节跳动用户属性信息，字节跳动的访问用户变量（如下表）才可以在分析工具中使用，交互数据定义、数据校验功能才会方便通过用户字节跳动相关的信息（字节跳动姓名和头像）定位用户。

下面是专门针对用户的接口。

### 绑定字节跳动用户openId 、unionId <a href="#bang-ding-zi-jie-tiao-dong-yong-hu-id" id="bang-ding-zi-jie-tiao-dong-yong-hu-id"></a>

上报节跳动用户openId 、unionId，支持按照 openId、unionId 进行用户分群，以及使用字节推送等高级功能。

当您的小程序调用 `tt.login`  获取到 openId、unionId 后，可以通过 `identify` 接口绑定微信用户 openId 、unionId，后续在 GrowingIO 平台用户分群功能使用。

**接口定义**

```java
gio('identify', openId, unionId)
```

**参数说明**

| 参数      | 类型     | 是否必须 | 说明           |
| ------- | ------ | ---- | ------------ |
| openId  | string | 是    | 获取到的  openId |
| unionId | string | 否    | 获取到的 unionId |

**示例代码**

```java
tt.login({
  success (res) {
    if (res.code) {
      //发起网络请求
      wx.request({
        url: 'https://example.com/onLogin',
        data: {
          code: res.code
        },
        success: res => {
          var openid = res.data.openid;
          var unionid = res.data.unionid;
          // ...
          gio('identify', res.data.openid, res.data.unionid)
        }
      })
    } else {
      console.log('登录失败！' + res.errMsg)
    }
  }
})
```

{% hint style="danger" %}
如果 SDK 初始化配置项中 **没有配置** `forceLogin` 为 true，而调用了该接口， **** u(访问用户ID) 字段的值会是自动生成的访问用户ID。**如果配置了**，调用此接口后，u(访问用户ID) 字段的值会是 参数 openId 的值。

调用 `identify 接口会发送 vstr(访问用户变量)事件，但是 openId，unionId 不能作为访问用户变量来使用，会在`GrowingIO 平台用户分群功能使用。
{% endhint %}

### 设置字节跳动用户信息 <a href="#she-zhi-zi-jie-tiao-dong-yong-hu-xin-xi" id="she-zhi-zi-jie-tiao-dong-yong-hu-xin-xi"></a>

当您的小程序上获取到字节用户信息后，可以通过 `setVisitor` 接口上报字节用户信息，后续在 GrowingIO 平台中使用上述变量分析字节用户属性数据。

**接口定义**

```java
gio('setVisitor', userInfo)
```

**参数说明**

| 名称       | 类型     | 是否必须 | 说明     |
| -------- | ------ | ---- | ------ |
| userInfo | Object | 是    | 字节用户信息 |

**示例代码**

```java
wx.getUserInfo({ 
  success: res => 
    // ...
    gio('setVisitor', res.userInfo);
})
```

{% hint style="info" %}
字节用户信息包含**昵称**、**头像**、**性别**、字节应用**所填国家**、字节应用**所填省份**、字节应用**所填城市**。

性别、字节应用所填国家、字节应用所填省份、字节应用所填城市会作为访问用户变量，这些访问用户变量标识符平台会自动生成，无需添加配置。

用户画像中的部分数据，只有在设置字节应用用户信息后，才可以统计。
{% endhint %}

## 5. 无埋点采集逻辑和高级配置

在进行无埋点数据采集时，您需要了解和使用[无埋点采集逻辑及行为数据采集的高级配置](wu-mai-dian-cai-ji-luo-ji-he-gao-ji-pei-zhi.md)

## 6. 自定义数据上传API

自定义数据上传API，请参考[自定义数据上传API](customize-api.md)。

## 7. 创建应用

请在添加了跟踪代码的字节小程序重新启动几次，发送数据给 GrowingIO。

在GrowingIO平台的创建字节小程序应用。创建应用请参考查看[创建应用](../../../product-manual/projectmange/application-manage.md#chuang-jian-ying-yong)。

## 8. 验证SDK是否正常采集数据

方式一：[小程序&内嵌页Debugger](../../debugging/minpdebugger.md)

方式二：在SDK中设置了Debug模式后，在开发者工具中查看数据采集日志。

方式三：[数据校验](broken-reference)
