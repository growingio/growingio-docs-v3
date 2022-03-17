# 百度小程序SDK

## 准备条件

获取项目ID，获取方法请参考"项目管理 > 项目概览 > [查看项目基本信息](../../../product-manual/projectmange/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

## 1. 添加跟踪代码

参照小程序的开发框架，下载相应的SDK，并添加跟踪代码。

* 原生框架
* Taro 框架
* mpvue / uni-app 框架
* chameleon 框架

{% tabs %}
{% tab title=" 原生框架" %}
### 1. 下载 gio-baidup.js 文件

把文件放在百度小程序项目里，比如 utils 目录下。

```
curl --compressed https://assets.giocdn.com/sdk/gio-baidup.js -o gio-baidup.js
```

### 2. 添加跟踪代码

方式一：

在百度小程序项目根目录的 app.js 文件的顶部添加以下 JS 代码，请注意一定要放在 App() 之前：

```java
var gio = require("utils/gio-baidup.js").default;
gio('init', '你的项目ID', '你的支付宝小程序AppID', { version: '你的小程序版本' });
```

方式二：

步骤一：新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数

```julia
export default {
    projectId: '你的 GrowingIO 项目ID',
    appId: '你的小程序AppID',
    version: '小程序版本'
    // ...
}
```

步骤二：在根目录 app.js文件的顶部添加跟踪代码

```java
var gio = require("utils/gio-baidup.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}

{% tab title="Taro" %}
### 1. 下载 gio-baidup.js

文件把文件放在百度小程序项目里，比如 utils 目录下。

```
curl --compressed https://assets.giocdn.com/sdk/gio-baidup.js -o gio-baidup.js
```

### 2. 添加跟踪代码

方式一：

在根目录 app.js 文件的顶部添加跟踪代码

```java
import Taro from '@tarojs/taro';
var gio = require("utils/gio-baidup.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', taro: Taro });
```

方式二：

步骤一：新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数

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

步骤二：在根目录 app.js文件的顶部添加跟踪代码

```java
var gio = require("utils/gio-baidup.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}

{% tab title="mpvue框架/uni-app框架" %}
### 1. 下载 gio-baidup.js 文件

把文件放在百度小程序项目里，比如 utils 目录下。

```
curl --compressed https://assets.giocdn.com/sdk/gio-baidup.esm.js -o gio-baidup.js
```

方式一：在根目录 app.js 文件的顶部添加跟踪代码

```java
import Vue from 'vue';
import App from './App';
App.mpType = 'app';
var gio = require("utils/gio-baidup.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本',vue: Vue });
```

方式二：

步骤一：新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数。

```java
import Vue from 'vue';
export default {
projectId: '你的 GrowingIO 项目ID',
appId: '你的小程序AppID',
version: '小程序版本',
vue: Vue,
...
}
```

步骤二：在根目录 app.js文件的顶部添加跟踪代码。

```java
var gio = require("utils/gio-baidup.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
import App from './App';
App.mpType = 'app';
```
{% endtab %}

{% tab title="Chameleon" %}
### 1.下载 gio-baidup.js 文件

把文件放在百度小程序项目里，比如 utils 目录下。

```
curl --compressed https://assets.giocdn.com/sdk/gio-baidup.js -o gio-baidup.js
```

### 2. 添加跟踪代码

方式一：在根目录 app.js 文件的顶部添加跟踪代码

```java
import Cml from 'chameleon-runtime';
var gio = require("utils/gio-baidup.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', cml: Cml });
```

方式二：

步骤一：新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数

```java
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

```java
var gio = require("utils/gio-baidup.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}
{% endtabs %}

## 2. SDK参数配置

{% hint style="success" %}
建议每次发布小程序新版本的时候，更新一下版本号 version，可以在 GrowingIO 分析不同版本的数据。除了 version 之外，还有以下额外参数可以使用。
{% endhint %}

| 参数          | 值             | 解释                                  |
| ----------- | ------------- | ----------------------------------- |
| forceLogin  | true \| false | 您的小程序是否强制要求用户登陆百度获取 swanid，默认 false |
| debug       | true \| false | 是否开启调试模式，可以看到采集的数据，默认 false         |
| version     | string        | 您的小程序的版本号                           |
| followShare | true \| false | 详细跟踪分享数据，开启后可使用分享分析功能。默认 true       |

### 跟踪分享数据

#### 配置`followShare`

转发分享小程序是小程序获客的重要场景，默认情况下，SDK开启跟踪分享数据功能，详细的进行转发分享的统计，来帮助您更好的分析。

如您不需要此功能，可以初始化配置中设置 `followShare: false` 来关闭跟踪分享。

即小程序项目根目录的 app.js 文件设置参数如下：

```javascript
// version 是您的小程序的版本号，发版时请调整
gio('init', '您的项目ID', '您的百度小程序AppID', { version: '1.0', followShare: true })
```

### 强制登录模式

**配置`forceLogin`**

默认情况下，SDK 会自动生成访问用户ID来标识访问用户，存储在 Storage 里面。这个用户标识符潜在可能会被`clearStorage` 清除掉，所以有可能不同的自动生成访问用户ID对应同一个百度用户的 `swanId`

如您需要使用 `swanId`标识访问用户，可以在初始化配置中设置 `forceLogin: true` 来打开强制登录模式。

强制登录模式适用于打开小程序就调用登陆并且获取 swanId 的小程序。 开启此模式并调用 `identity` 上报 swanId，会将上报的 swanId 作为访问用户ID。

设置`forceLogin`为`true`后，SDK会继续采集但暂停上报数据，待调用 登陆并且获取 `swanId`，调用 `identify` 方法后开始数据上报。**调用 `identify` 会替换事件数据的 u(访问用户ID) 字段的值 为设定值（一般是小程序的 swanId），包括调用`identify`之前触发的事件。**

获取到 swanId 后调用 [`identify`](baidu-sdk.md#bang-ding-bai-du-yong-hu-id) 接口。

{% hint style="danger" %}
适用于打开小程序就调用登陆并且获取 swanId `的小程序`。

小程序SDK初始化时配置了 `forceLogin` 为 `true`，如果打开小程序后没有调用登陆并且获取 swanId，没有调用 `identify` 方法，会导致SDK不能上报数据，访问数据将大幅减少。如果调用了`，但时机不在小程序打开时，而在小程序使用中较晚的时机，在调用之前若小程序关闭则会造成此次访问过程中采集的数据丢失。`\


如果您不能确定是否要设置这个参数，请先咨询我们技术支持。
{% endhint %}

**请特别注意这个参数的设置**，具体集成示例：

```javascript
gio('init', '你的项目 ID', '你的百度小程序 AppID', { version: '1.0', forceLogin: true });
...
// 当获取到 swanid 后，调用以下方法
gio("identify", swanid);
```

## 3. 添加请求服务器域名

要正常采集百度小程序的数据并发送给 GrowingIO，需要在百度小程序里事先设置一个通讯域名，允许跟 GrowingIO API 服务器进行网络通信。具体步骤如下：

1. 登陆百度小程序后台，进入配置
2. 打开开发设置，到服务器域名配置部分
3. 在request合法域名中添加：`https://wxapi.growingio.com`

## 4. 百度小程序用户属性设置

作为用户行为数据分析工具，用户信息的完善会给后续的分析带来很大的帮助。在小程序中，百度用户属性是非常重要的设置，只有完善了百度用户属性信息，百度的访问用户变量（如下表）才可以在分析工具中使用，交互数据定义、数据校验功能才会方便通过用百度相关的信息（百度姓名和头像）定位用户。

### 绑定百度用户swand

当用户在你的小程序上登陆获取到 swanid 后，可以用过 identify 接口绑定百度用户ID，后续在 GrowingIO 中获取更准确的百度访问用户量。示例代码如下：

```javascript
swan.getSwanId({ success: (res) => { gio('identify', res.data.swanid) } });
```

### 设置百度用户信息

当用户在你的小程序上绑定百度信息后，可以通过 setVisitor 接口设置百度用户信息，后续在 GrowingIO 中分析这个数据。示例代码如下：

```javascript
swan..getUserInfo({ success: function(res) { ... gio('setVisitor', res.userInfo); } });
```

百度信息包含**用户昵称**、**用户头像**、**性别**。

{% hint style="info" %}
注：用户画像中的部分数据，只有在设置百度用户信息后，才可以统计。
{% endhint %}

## 5. 无埋点采集逻辑和高级配置

在进行无埋点数据采集时，您需要了解和使用[无埋点采集逻辑及行为数据采集的高级配置](wu-mai-dian-cai-ji-luo-ji-he-gao-ji-pei-zhi.md)

## 6. 自定义数据上传API

自定义数据上传API，请参考[自定义数据上传API](customize-api.md)。

## 7. 创建应用

请在添加了跟踪代码的支付宝小程序重新启动几次，发送数据给 GrowingIO。

在GrowingIO平台的创建微信小游戏应用。创建应用请参考查看[创建应用](../../../product-manual/projectmange/application-manage.md#chuang-jian-ying-yong)。

## 8. 验证SDK是否正常采集数据

方式一：[小程序&内嵌页Debugger](../../debugging/minpdebugger.md)

方式二：在SDK中设置了Debug模式后，在开发者工具中查看数据采集日志。

方式三：[数据校验](../../../product-manual/data-center/datacheck/)
