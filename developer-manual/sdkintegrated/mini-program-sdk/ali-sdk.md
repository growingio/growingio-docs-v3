# 支付宝小程序SDK

## 准备条件

获取项目ID，获取方法请参考"项目管理 > 项目概览 > [查看项目基本信息](../../../product-manual/projectmange/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

## 1. 添加跟踪代码

### 1. 根据支付宝小程序框架选择SDK文件并添加跟踪代码

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

### **2. SDK参数配置**

每次发布小程序新版本的时候，更新一下版本号 **version**，可以在 GrowingIO 分析不同版本的数据。除了 version 之外，还有以下额外参数可以使用。

| 参数          | 值             | 解释                                                                              |
| ----------- | ------------- | ------------------------------------------------------------------------------- |
| getLocation | true \| false | 是否自动获取用户的地理位置信息。默认false                                                         |
| forceLogin  | true \| false | 是否要用用户登陆支付宝获取 userid作为访问用户ID标识采集，建议你的小程序在打开强制要求用户登陆支付宝获取 userid时，才进行开启。默认 false |
| debug       | true \| false | 是否开启调试模式，可以在调试体验版时看到采集的数据，默认 false                                              |
| version     | string        | 你的小程序的版本号                                                                       |
| followShare | true \| false | 详细跟踪分享数据，开启后可使用分享分析功能统计分享带来的用户量。默认 false                                        |

#### followShare参数

转发分享小程序是小程序获客的重要场景，想要详细的进行转发分享的统计，需要在SDK参数中，设置如下参数，值为true

| 参数          | 值             | 解释                                       |
| ----------- | ------------- | ---------------------------------------- |
| followShare | true \| false | 详细跟踪分享数据，开启后可使用分享分析功能统计分享带来的用户量。默认 false |

即支付宝小程序项目根目录的 app.js 文件设置参数如下：

```
var gio = require("utils/gio-alip.js");
// version 是你的小程序的版本号，发版时请调整
gio('init', '你的项目ID', '你的支付宝小程序AppID', { version: '1.0', followShare: true });
```

#### getLocation 参数

根据微信最新的用户地理位置获取的规则，GrowingIO 小程序SDK 默认不会在小程序启动时获取用户的坐标信息。

* 如果您的小程序在打开时就需要获取用户地理信息，就可以将这个参数配置为true。
* 如果您的小程序在用户点击某些按钮时，才触发获取位置，则可以按照配置方式，进行用户位置的补发，从而增强用户地理位置的分析能力。

| 参数          | 值             | 解释                      |
| ----------- | ------------- | ----------------------- |
| getLocation | true \| false | 是否自动获取用户的地理位置信息。默认false |

GrowingIO SDK 默认不会在小程序启动时获取用户的坐标信息。当用户访问到某一功能时需要位置信息时，可以调用以下位置接口，补发vst，采集位置信息，提升用户地域分布的分析准确性。

```
gio('getLocation')
```

#### forceLogin 参数

设置forceLogin参数后，访问用户ID会被支付宝userid替换，但是风险是，如果小程序打开时并不要求立即授权上报支付宝userid，则在上报支付宝userid前的操作数据不会发送；如果在上报支付宝userid前，用户就退出了小程序，用户数据不会上报。

{% hint style="warning" %}
forceLogin 是一个需要特别注意的参数。

GrowingIO 默认会在小程序里面设置用户标识符，存储在 Storage 里面。这个用户标识符潜在可能会被 `clearStorage`清除掉，所以有可能不同的用户标识符对应同一个支付宝用户的 userid。如果你的支付宝小程序在用户打开后会去做登陆并且获取 `userid` ，可以设置 `forceLogin` 为 true。当 forceLogin 为 true 的时候，用户标识符会使用 userid，潜在风险是如果用户没有授权，数据不会发送。
{% endhint %}

**所以请特别注意这个参数的设置**，具体集成示例：

```java
gio('init', '你的项目ID', '你的支付宝小程序AppID', { version: '1.0', forceLogin: true });
...
// 当获取到 userid 后，调用以下方法
gio("identify", userid);
```

## 2. 添加请求服务器域名

要正常采集小程序的数据并发送给 GrowingIO，需要在支付宝小程序里事先设置一个通讯域名，允许跟 GrowingIO API 服务器进行网络通信。具体步骤如下：

1. 登录支付宝小程序后台，进入配置
2. 打开小程序详情/设置/开发设置
3. 配置 **httpRequest接口请求域名白名单**：https://wxapi.growingio.com

![httpRequest 接口请求域名白名单](<../../../.gitbook/assets/image (87).png>)

## 3. 支付宝小程序用户属性设置

作为用户行为数据分析工具，用户信息的完善会给后续的分析带来很大的帮助。在小程序中，支付宝用户属性是非常重要的设置，只有完善了支付宝用户属性信息，支付宝的访问用户变量（如下表）才可以在分析工具中使用，交互数据定义、数据校验功能才会方便通过用支付宝相关的信息（支付宝姓名和头像）定位用户。

下面是专门针对用户的三个接口：

#### 绑定支付宝用户ID

当用户在你的小程序上登陆获取到 userid 后，可以用过 identify 接口绑定支付宝用户ID，后续在 GrowingIO 中获取更准确的支付宝访问用户量。示例代码如下：

```
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

#### 设置支付宝用户信息

当用户在你的小程序上绑定支付宝信息后，可以通过 setVisitor 接口设置支付宝用户信息，后续在 GrowingIO 中分析这个数据。示例代码如下：

```
my.getAuthUserInfo({
    success: (userInfo) => {
        gio('setVisitor', userInfo);
    }
    });
```

支付宝信息包含**用户昵称**、**用户头像**、**性别**、**支付宝所填国家**、**支付宝所填省份**、**支付宝所填城市**、**用户类型**、**用户状态**、**是否通过实名认证**、**学生认证**。

\*注：用户画像中的部分数据，只有在设置支付宝用户信息后，才可以统计。

#### 设置登录用户ID

当用户在你的小程序上注册以后，你的产品应用服务端会在CRM 用户数据库里添加一条记录并且分配一个 ID，可以通过 setUserId 接口设置注册用户ID，后续在 GrowingIO 中分析登录用户这个数据。示例代码如下：

```
gio('setUserId', YOUR_USER_ID);
```

#### 清除登录用户ID

用户退出登录时，清除登录用户ID。

```java
gio('clearUserId');
```

#### 设置登录用户属性

当用户在你的小程序上传了注册用户ID后，可以通过 setUser 接口设置注册用户信息,例如用户会员等级，后续在 GrowingIO 中分析这个数据。示例代码如下，

```java
    gio('setUserId', user.id);
    gio('setUser', {
        id: user.id,
        level: user.level
    });
```

## 4. 自定义数据上传API

自定义数据上传API，请参考[自定义数据上传API](customize-api.md)。

## 5. 创建应用

请在添加了跟踪代码的支付宝小程序重新启动几次，发送数据给 GrowingIO。

在GrowingIO平台的创建支付宝小程序应用。创建应用请参考查看[创建应用](../../../product-manual/projectmange/application-manage.md#chuang-jian-ying-yong)。

## 6. 验证SDK是否正常采集数据

方式一：[小程序&内嵌页Debugger](../../debugging/minpdebugger.md)

方式二：在SDK中设置了Debug模式后，在开发者工具中查看数据采集日志。

方式三：[数据校验](broken-reference)
