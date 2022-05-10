# 支付宝小程序SDK

## 准备条件

获取项目ID，获取方法请参考"项目管理 > 项目概览 > [查看项目基本信息](../../../product-manual/projectmange/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

## 1. 添加跟踪代码

根据支付宝小程序框架选择SDK文件并添加跟踪代码

参照小程序的开发框架，下载相应的SDK，并添加跟踪代码。

* 原生框架
* Taro 框架
* mpvue / uni-app 框架
* chameleon 框架

{% tabs %}
{% tab title="原生框架" %}
#### 1. 根据下载小程序采集SDK

下载 gio-alip.js 文件

```
curl --compressed https://assets.giocdn.com/sdk/gio-alip.js -o gio-alip.js
```

当下载到 gio-alip.js 文件以后，把文件放在支付宝小程序项目里，比如 utils 目录下。下面会假设 SDK 文件放在 utils 目录下。

#### 2. 添加跟踪代码

方式一：

在支付宝小程序项目根目录的 app.js 文件的顶部添加以下 JS 代码，请注意一定要放在 App() 之前：

```javascript
var gio = require("utils/gio-alip.js").default;
// version 是你的小程序的版本号
gio('init', '你的项目ID', '你的支付宝小程序AppID', { version: '你的小程序版本'});

// 修改项目中的App和Page，如下：
// App({})改写为:
App($global.trackApp({

}))
// 所有的Page({})改写为：
$global.GioPage({

})
```

方式二：

步骤一：新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数

```javascript
export default {
projectId: '你的 GrowingIO 项目ID',
appId: '你的小程序AppID',
version: '小程序版本'
...
}
```

步骤二：在根目录 app.js文件的顶部添加跟踪代码

```javascript
var gio = require("utils/gio-alip.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
// 修改项目中的App和Page，如下：
// App({})改写为:
App($global.trackApp({

}))
// 所有的Page({})改写为：
$global.GioPage({

})
```
{% endtab %}

{% tab title="Taro" %}
#### 1.下载 gio-alip.js 文件

把文件放在支付宝小程序项目里，比如 utils 目录下。

```
curl --compressed https://assets.giocdn.com/sdk/gio-alip.js -o gio-alip.js
```

#### 2. 添加跟踪代码

方式一：

在根目录 app.js 文件的顶部添加跟踪代码

```javascript
import Taro from '@tarojs/taro';
var gio = require("utils/gio-alip.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', taro: Taro });
```

方式二：

步骤一：新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数

```javascript
import Taro from '@tarojs/taro';
export default {
projectId: '你的 GrowingIO 项目ID',
appId: '你的小程序AppID',
version: '小程序版本',
taro: Taro,
...
}
```

步骤二：在根目录 app.js文件的顶部添加跟踪代码

```javascript
var gio = require("utils/gio-alip.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}

{% tab title="mpvue框架/uni-app框架" %}
#### 1. 下载 gio-alip.js 文件

把文件放在支付宝小程序项目里，比如 utils 目录下。

```
curl --compressed https://assets.giocdn.com/sdk/gio-alip.esm.js -o gio-alip.js
```

#### 2. 添加跟踪代码

方式一：在根目录 app.js 文件的顶部添加跟踪代码

```javascript
import Vue from 'vue';
import App from './App';
App.mpType = 'app';
var gio = require("utils/gio-alip.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本',vue: Vue });
```

方式二：

步骤一：新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数

```javascript
import Vue from 'vue';
export default {
projectId: '你的 GrowingIO 项目ID',
appId: '你的小程序AppID',
version: '小程序版本',
vue: Vue,
...
}
```

步骤二：在根目录 app.js文件的顶部添加跟踪代码

```javascript
var gio = require("utils/gio-alip.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
import App from './App';
App.mpType = 'app';
```
{% endtab %}

{% tab title="Chameleon框架" %}
#### 1. 下载 gio-alip.js 文件

把文件放在支付宝小程序项目里，比如 utils 目录下。

```
curl --compressed https://assets.giocdn.com/sdk/gio-alip.js -o gio-alip.js
```

#### 2、添加跟踪代码

方式一：在根目录 app.js 文件的顶部添加跟踪代码

```javascript
import Cml from 'chameleon-runtime';
var gio = require("utils/gio-alip.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', cml: Cml });
```

方式二：

步骤一：新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数

```javascript
import Cml from 'chameleon-runtime';
export default {
projectId: '你的 GrowingIO 项目ID',
appId: '你的小程序AppID',
version: '小程序版本',
cml: Cml,
...
}
```

步骤二：在根目录 app.js文件的顶部添加跟踪代码

```javascript
var gio = require("utils/gio-alip.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}
{% endtabs %}

## **2. SDK参数配置**

SDK中提供了以下几个参数可以用来进行配置

| 参数          | 类型/值          | 解释                                                                              |
| ----------- | ------------- | ------------------------------------------------------------------------------- |
| getLocation | true \| false | 是否自动获取用户的地理位置信息，默认false (3.7.5+版本不支持)                                           |
| forceLogin  | true \| false | 是否要用用户登陆支付宝获取 userid作为访问用户ID标识采集，建议你的小程序在打开强制要求用户登陆支付宝获取 userid时，才进行开启。默认 false |
| debug       | true \| false | 是否开启调试模式，可以在调试体验版时看到采集的数据，默认 false                                              |
| version     | string        | 你的小程序的版本号                                                                       |
| followShare | true \| false | 详细跟踪分享数据，开启后可使用分享分析功能统计分享带来的用户量。默认 false                                        |

{% hint style="info" %}
**每次发布小程序新版本的时候，需要更新一下版本号 version 配置， 与线上发布小程序保持一致; 可以在 GrowingIO 平台使用 “App 版本”维度，分析不同版本的数据。**
{% endhint %}

### 跟踪分享数据

#### 配置`followShare`

转发分享小程序是小程序获客的重要场景，默认情况下，SDK开启跟踪分享数据功能，详细的进行转发分享的统计，来帮助您更好的分析。

如您不需要此功能，可以初始化配置中设置 `followShare: false` 来关闭跟踪分享。

即小程序项目根目录的 app.js 文件设置参数如下：

```
var gio = require("utils/gio-alip.js");
// version 是你的小程序的版本号，发版时请调整
gio('init', '你的项目ID', '你的支付宝小程序AppID', { version: '1.0', followShare: true });
```

### 采集GPS数据

#### 配置`getLocation`

{% hint style="info" %}
3.7.5+版本不支持，请使用  [`setLocation`](customize-api.md#she-zhi-wei-zhi-xin-xi) `接口`
{% endhint %}

GrowingIO SDK 默认不采集地理位置信息。

如您需要在小程序打开时获取用户地理位置信息，需在初始化配置项中设置 `getLocation:true` 来打开此功能。

```javascript
gio('init', ' GrowingIO 项目ID', '您的小程序AppID', {
  version: '1.0.0',
  getLocation: false  
});
```

如果您初始化配置项中没有打开此功能，当用户访问至某一功能需要位置信息时，可以手动调用获取地理位置接口，自动补发访问事件，采集位置信息，提升用户地域分布的分析准确性。

```
gio('getLocation')
```

### 强制登录模式

**配置`forceLogin`**

默认情况下，SDK 会自动生成访问用户ID来标识访问用户，存储在 Storage 里面。这个用户标识符潜在可能会被`clearStorage` 清除掉，所以有可能不同的自动生成访问用户ID对应同一个支付宝用户的 userId

如您需要使用 userId 标识访问用户，可以在初始化配置中设置 `forceLogin: true` 来打开强制登录模式。

强制登录模式适用于打开小程序就调用登陆并且获取 userId 的小程序。 开启此模式并调用 `identity` 上报 userId，会将上报的 userId 作为访问用户ID。

设置`forceLogin`为`true`后，SDK会继续采集但暂停上报数据，待调用 登陆并且获取 userId，调用 `identify` 方法后开始数据上报。**调用 `identify` 会替换事件数据的 u(访问用户ID) 字段的值 为设定值（一般是小程序的 userId），包括调用`identify`之前触发的事件。**

获取到 **userId** 后调用 [`identify`](ali-sdk.md#bang-ding-zhi-fu-bao-yong-hu-id) 接口。

{% hint style="danger" %}
适用于打开小程序就调用登陆并且获取 userId `的小程序`。

小程序SDK初始化时配置了 `forceLogin` 为 `true`，如果打开小程序后没有调用登陆并且获取`userid`，没有调用 `identify` 方法，会导致SDK不能上报数据，访问数据将大幅减少。如果调用了`，但时机不在小程序打开时，而在小程序使用中较晚的时机，在调用之前若小程序关闭则会造成此次访问过程中采集的数据丢失。`\


如果您不能确定是否要设置这个参数，请先咨询我们技术支持。
{% endhint %}

**所以请特别注意这个参数的设置**，具体集成示例：

```java
gio('init', '你的项目ID', '你的支付宝小程序AppID', { version: '1.0', forceLogin: true });
...
// 当获取到 userid 后，调用以下方法
gio("identify", userid);
```

## 3. 添加请求服务器域名

要正常采集小程序的数据并发送给 GrowingIO，需要在支付宝小程序里事先设置一个通讯域名，允许跟 GrowingIO API 服务器进行网络通信。具体步骤如下：

1. 登录支付宝小程序后台，进入配置
2. 打开小程序详情/设置/开发设置
3. 配置 **httpRequest接口请求域名白名单**：https://wxapi.growingio.com

![httpRequest 接口请求域名白名单](<../../../.gitbook/assets/image (87).png>)

## 4. 支付宝小程序用户属性设置

作为用户行为数据分析工具，用户信息的完善会给后续的分析带来很大的帮助。在小程序中，支付宝用户属性是非常重要的设置，只有完善了支付宝用户属性信息，支付宝的访问用户变量（如下表）才可以在分析工具中使用，交互数据定义、数据校验功能才会方便通过用支付宝相关的信息（支付宝姓名和头像）定位用户。

### 绑定支付宝用户 userId

当用户在您的小程序上登陆获取到 userId 后，可以用过 `identify` 接口绑定支付宝用户`userId`，后续在 GrowingIO 中获取更准确的支付宝访问用户量。

**接口定义**

```java
gio('identify', userId)
```

**参数说明**

| 参数     | 类型     | 是否必须 | 说明           |
| ------ | ------ | ---- | ------------ |
| userId | string | 是    | 获取到的  userId |

**示例代码**

```javascript
my.httpRequest({
    url: 'http://isv.com/auth', // 该url是自己的服务地址，实现的功能是服务端拿到authcode去开放平台进行token验证
    data: {
      authcode: res.authCode
    },
    success: (res) => {
      gio('identify', res.uid)
    }
  });
```

{% hint style="danger" %}
如果 SDK 初始化配置项中 **没有配置** `forceLogin` 为 true，而调用了该接口， **** u(访问用户ID) 字段的值会是自动生成的访问用户ID。**如果配置了**，调用此接口后，u(访问用户ID) 字段的值会是 参数 openId 的值。

调用 `identify 接口会发送 vstr(访问用户变量)事件，但是 userId 不能作为访问用户变量来使用，会在`GrowingIO 平台用户分群功能使用。
{% endhint %}

### 设置支付宝用户信息

当用户在你的小程序上绑定支付宝信息后，可以通过 setVisitor 接口设置支付宝用户信息，后续在 GrowingIO 中分析这个数据。

**接口定义**

```java
gio('setVisitor', userInfo)
```

**参数说明**

| 名称       | 类型     | 是否必须 | 说明      |
| -------- | ------ | ---- | ------- |
| userInfo | Object | 是    | 支付宝用户信息 |

**示例代码**

```javascript
my.getAuthUserInfo({
    success: (userInfo) => {
        gio('setVisitor', userInfo);
    }
    });
```

{% hint style="info" %}
支付宝信息包含**用户昵称**、**用户头像**、**性别**、**支付宝所填国家**、**支付宝所填省份**、**支付宝所填城市**、**用户类型**、**用户状态**、**是否通过实名认证**、**学生认证**。

性别、支付宝所填国家、支付宝所填省份、支付宝所填城市会作为访问用户变量，这些访问用户变量标识符平台会自动生成，无需添加配置。

用户画像中的部分数据，只有在设置支付宝用户信息后，才可以统计。
{% endhint %}

## 5. 无埋点采集逻辑和高级配置

在进行无埋点数据采集时，您需要了解和使用[无埋点采集逻辑及行为数据采集的高级配置](wu-mai-dian-cai-ji-luo-ji-he-gao-ji-pei-zhi.md)

## 6. 自定义数据上传API

自定义数据上传API，请参考[自定义数据上传API](customize-api.md)。

## 7. 创建应用

请在添加了跟踪代码的支付宝小程序重新启动几次，发送数据给 GrowingIO。

在GrowingIO平台的创建支付宝小程序应用。创建应用请参考查看[创建应用](../../../product-manual/projectmange/application-manage.md#chuang-jian-ying-yong)。

## 8. 验证SDK是否正常采集数据

方式一：[小程序&内嵌页Debugger](../../debugging/minpdebugger.md)

方式二：在SDK中设置了Debug模式后，在开发者工具中查看数据采集日志。

方式三：[数据校验](broken-reference)
