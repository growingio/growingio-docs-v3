# 微信小程序 SDK

## 准备条件

获取项目ID，获取方法请参考"项目管理 &gt; 项目概览 &gt; [查看项目基本信息](../../../chan-pin-shi-yong-wen-dang-fen-ban/xiang-mu-guan-li/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

## 1. 添加跟踪代码

### 选择对应的开发框架添加代码

{% tabs %}
{% tab title="原生" %}
1. 下载微信小程序SDK，并解压。下载地址：[https://assets.giocdn.com/sdk/gio-minp.zip](https://assets.giocdn.com/sdk/gio-minp.zip)
2. 将解压后的`gio-minp`目录放在小程序目录下（比如：/src/utils目录）。
3. 添加代码：

方式1：

在根目录app.js文件的顶部添加跟踪代码：

```javascript
var gio = require("utils/gio-minp/index.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本' });
```

方式2：

新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的必要配置参数：

```javascript
export default {
    projectId: '你的 GrowingIO 项目ID',
    appId: '你的小程序AppID',
    version: '小程序版本'
    // ...
}
```

在根目录 app.js文件的顶部添加跟踪代码：

```javascript
var gio = require("utils/gio-minp/index.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}

{% tab title="原生+第三方插件" %}
1. 下载微信小程序SDK，并解压。下载地址：[https://assets.giocdn.com/sdk/gio-minp.zip](https://assets.giocdn.com/sdk/gio-minp.zip)
2. 将解压后的`gio-minp`目录放在小程序目录下（比如：/src/utils目录）。
3. 添加代码：

方式1：

在根目录app.js文件的顶部添加跟踪代码

```javascript
var gio = require("utils/gio-minp/index.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', usePlugin: true });
const App = global.GioApp;
```

在每个page页面（新增页面也需要添加）的 .js 文件顶部添加如下代码

```javascript
// 在每个Page页面的 .js 文件顶部（其他代码之前）添加如下代码。（请注意是每个页面都要引入）
const Page = global.GioPage;
```

方式2：

新建一个gioConfig.js文件，并且配置gioConfig.js文件中的必要配置参数：

```javascript
export default {
    projectId: '你的 GrowingIO 项目ID',
    appId: '你的小程序AppID',
    version: '小程序版本',
    usePlugin: true 
    // ...
}
```

在根目录app.js文件的顶部添加跟踪代码：

```javascript
var gio = require("utils/gio-minp/index.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
// app.js 文件，在文件顶部 （其他代码之前）添加如下代码:
const App = global.GioApp
```

在每个page页面（新增页面也需要添加）的.js文件顶部添加如下代码

```javascript
// 在每个Page页面的 .js 文件顶部（其他代码之前）添加如下代码。（请注意是每个页面都要引入）
const Page = global.GioPage;
```
{% endtab %}

{% tab title="Taro" %}
1. 下载微信小程序SDK，并解压。下载地址：[https://assets.giocdn.com/sdk/gio-minp.zip](https://assets.giocdn.com/sdk/gio-minp.zip)
2. 将解压后的`gio-minp`目录放在小程序目录下（比如：/src/utils目录）。
3. 添加代码：

方式1：在根目录app.jsx文件的顶部添加跟踪代码：

```javascript
import Taro from '@tarojs/taro';
var gio = require("utils/gio-minp/index.js").default;
gio('init','你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', taro: Taro });
```

方式2：

新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数：

```javascript
export default {
    projectId: '你的 GrowingIO 项目ID',
    appId: '你的小程序AppID',
    version: '小程序版本',
    taro: Taro,
    // ...
}
```

在根目录 app.jsx文件的顶部添加跟踪代码

```javascript
var gio = require("utils/gio-minp/index.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}

{% tab title="WePY" %}
1. 下载微信小程序SDK，并解压。下载地址：[https://assets.giocdn.com/sdk/gio-minp.esm.zip](https://assets.giocdn.com/sdk/gio-minp.esm.zip)
2. 将解压后的`gio-minp`目录放在小程序目录下（比如：/src/utils目录）。
3. 添加代码：

#### WePY 1.x

方式1：

在根目录app.wpy文件的顶部添加跟踪代码

```javascript
import Vue from 'vue';
var gio = require("utils/gio-minp/index.js").default;
gio('init','你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', vue: Vue });
```

方式2：

新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数

```javascript
import Vue from 'vue';
export default {
    projectId: '你的 GrowingIO 项目ID',
    appId: '你的小程序AppID',
    version: '小程序版本',
    vue: Vue,
    // ...
}
```

在根目录 app.wpy文件的顶部添加跟踪代码

```javascript
var gio = require("utils/gio-minp/index.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```

#### WePY 2.x

方式1：

在根目录app.wpy文件的顶部添加跟踪代码

```javascript
import Wepy from '@wepy/core';
var gio = require("utils/gio-minp/index.js").default;
gio('init','你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', wepy: Wepy });
```

方式2：

新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数

```javascript
import Wepy from '@wepy/core';
export default {
    projectId: '你的 GrowingIO 项目ID',
    appId: '你的小程序AppID',
    version: '小程序版本',
    wepy: Wepy,
    // ...
}
```

在根目录 app.wpy文件的顶部添加跟踪代码

```javascript
var gio = require("utils/gio-minp/index.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}

{% tab title="WePY+第三方插件" %}
1. 下载微信小程序SDK，并解压。下载地址：[https://assets.giocdn.com/sdk/gio-minp.esm.zip](https://assets.giocdn.com/sdk/gio-minp.esm.zip)
2. 将解压后的`gio-minp`目录放在小程序目录下（比如：/src/utils目录）。
3. 添加代码：

#### WePY 1.x

方式1：

在根目录app.wpy文件的顶部添加跟踪代码

```javascript
import Vue from 'vue';
var gio = require("utils/gio-minp/index.js").default;
gio('init','你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', vue: Vue });
```

方式2：

新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数

```javascript
import Vue from 'vue';
export default {
    projectId: '你的 GrowingIO 项目ID',
    appId: '你的小程序AppID',
    version: '小程序版本',
    usePlugin: true,
    vue: Vue,
    // ...
}
```

在根目录 app.wpy文件的顶部添加跟踪代码

```javascript
var gio = require("utils/gio-minp/index.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```

#### WePY 2.x

方式1：

在根目录 app.wpy 文件的顶部添加跟踪代码

```java
import Wepy from '@wepy/core';
var gio = require("utils/gio-minp/index.js").default;
gio('init','你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', usePlugin: true, wepy: Wepy });
```

方式2：

新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数

```java
import Wepy from '@wepy/core';
export default {
    projectId: '你的 GrowingIO 项目ID',
    appId: '你的小程序AppID',
    version: '小程序版本',
    usePlugin: true,
    wepy: Wepy,
    // ...
}
```

在根目录 app.wpy文件的顶部添加跟踪代码

```java
var gio = require("utils/gio-minp/index.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}

{% tab title="mpvue/uni-app" %}
1. 下载微信小程序SDK，并解压。下载地址：[https://assets.giocdn.com/sdk/gio-minp.esm.zip](https://assets.giocdn.com/sdk/gio-minp.esm.zip)
2. 将解压后的`gio-minp`目录放在小程序目录下（比如：/src/utils目录）。
3. 添加代码：

方式1：在根目录main.js文件的顶部添加跟踪代码

```javascript
import Vue from 'vue';
import App from './App';
App.mpType = 'app';
var gio = require("utils/gio-minp/index.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本',vue: Vue });
```

方式2：

新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数

```javascript
import Vue from 'vue';
export default {
    projectId: '你的 GrowingIO 项目ID',
    appId: '你的小程序AppID',
    version: '小程序版本',
    vue: Vue,
    // ...
}
```

在根目录main.js文件的顶部添加跟踪代码

```javascript
var gio = require("utils/gio-minp/index.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
import App from './App';
App.mpType = 'app';
```
{% endtab %}

{% tab title="mpvue+第三方插件" %}
1. 下载微信小程序SDK，并解压。下载地址：[https://assets.giocdn.com/sdk/gio-minp.esm.zip](https://assets.giocdn.com/sdk/gio-minp.esm.zip)
2. 解压后的`index.js`和`gioConfig.js`目录放在小程序目录下（比如：/src/utils目录）。
3. 添加代码：
4. 第一步：更新`index.js`到最新版。
5. 第二步：添加`npm`包。

```text
npm install  imports-loader --save-dev
```

* 第三步：创建一个新文件`/src/utils/vue.js`文件。内容如下：

```javascript
import Vue from 'imports-loader?global=>undefined,Page=>GioPage,App=>GioApp,Component=>GioComponent!mpvue'
export default Vue
```

* 第四步：修改`/build/webpack.base.conf.js`配置。

```javascript
var path = require('path')
var fs = require('fs')
var utils = require('./utils')
var config = require('../config')
var vueLoaderConfig = require('./vue-loader.conf')
var webpack = require('webpack')
var MpvuePlugin = require('webpack-mpvue-asset-plugin')
var glob = require('glob')
function resolve (dir) {
  return path.join(__dirname, '..', dir)
}
function getEntry (rootSrc, pattern) {
  var files = glob.sync(path.resolve(rootSrc, pattern))
  return files.reduce((res, file) => {
    var info = path.parse(file)
    var key = info.dir.slice(rootSrc.length + 1) + '/' + info.name
    res[key] = path.resolve(file)
    return res
  }, {})
}
const appEntry = { app: resolve('./src/main.js') }
const pagesEntry = getEntry(resolve('./src'), 'pages/**/main.js')
const entry = Object.assign({}, appEntry, pagesEntry)
module.exports = {
  // 如果要自定义生成的 dist 目录里面的文件路径，
  // 可以将 entry 写成 {'toPath': 'fromPath'} 的形式，
  // toPath 为相对于 dist 的路径, 例：index/demo，则生成的文件地址为 dist/index/demo.js
  entry,
  target: require('mpvue-webpack-target'),
  output: {
    path: config.build.assetsRoot,
    filename: '[name].js',
    publicPath: process.env.NODE_ENV === 'production'
      ? config.build.assetsPublicPath
      : config.dev.assetsPublicPath
  },
  resolve: {
    extensions: ['.js', '.vue', '.json'],
    alias: {
      'vue': resolve('src/utils/vue'),
      '@': resolve('src'),
      'flyio': 'flyio/dist/npm/wx',
      'wx': resolve('src/utils/wx')
    },
    symlinks: false
  },
  module: {
    rules: [
      {
        test: /\.vue$/,
        loader: 'mpvue-loader',
        options: vueLoaderConfig
      },
      {
        test: /\.js$/,
        include: [resolve('src'), resolve('test')],
        use: [
          'babel-loader',
          {
            loader: 'mpvue-loader',
            options: {
              checkMPEntry: true
            }
          },
        ]
      },
      {
        test: /\.(png|jpe?g|gif|svg)(\?.*)?$/,
        loader: 'url-loader',
        options: {
          limit: 10000,
          name: utils.assetsPath('img/[name].[ext]')
        }
      },
      {
        test: /\.(mp4|webm|ogg|mp3|wav|flac|aac)(\?.*)?$/,
        loader: 'url-loader',
        options: {
          limit: 10000,
          name: utils.assetsPath('media/[name]].[ext]')
        }
      },
      {
        test: /\.(woff2?|eot|ttf|otf)(\?.*)?$/,
        loader: 'url-loader',
        options: {
          limit: 10000,
          name: utils.assetsPath('fonts/[name].[ext]')
        }
      }
    ]
  },
  plugins: [
    new MpvuePlugin(),
    new webpack.ProvidePlugin({
      GioPage: [resolve('src/utils/gio-minp.js'), 'GioPage'],
      GioApp: [resolve('src/utils/gio-minp.js'), 'GioApp'],
      GioComponent: [resolve('src/utils/gio-minp.js'), 'GioComponent']
    }),
  ]
}
```

* 第五步：修改`gioConfig.js`文件中的配置参数。

```javascript
import Vue from 'vue';
export default {
projectId: '你的小程序项目ID',//growingio的项目ID
version: '1.0.0',//小程序版本号，每次发版前请修改
debug: true, //是否开启调试模式，可以看到采集的数据。默认 false
forceLogin: false, //是否强制要求用户登陆微信获取 openid。默认 false
followShare: false, //是否详细跟踪分享数据，开启后可使用分享分析功能。默认false
usePlugin: true, //是否使用了第三方插件。默认false
getLocation: { //是否自动获取用户的地理位置信息, 并设置获取方式 
autoGet: false, //默认不自动获取
type: 'wgs84' //支持wgs84 | gcj02, 默认wgs84
},
vue:Vue, //是否使用了mpvue/uni-app框架, 取值: false | Vue
taro: false, //是否使用了taro框架, 取值: false | Taro
cml: false //是否使用了chameleon框架, 取值: false | Cml
}
```

* 第六步：在根目录main.js文件的顶部添加跟踪代码

```javascript
//请将gio放在Vue之后引入
import Vue from 'vue'
import App from './App'
import gio from './utils/index'
App.mpType = 'app'
```
{% endtab %}

{% tab title="Chameleon" %}
1. 下载微信小程序SDK，并解压。下载地址：[https://assets.giocdn.com/sdk/gio-minp.zip](https://assets.giocdn.com/sdk/gio-minp.zip)
2. 将解压后的gio-minp目录放在小程序目录下（比如：/src/utils目录）。
3. 添加代码：

方式1：

在根目录 app.cml 文件的顶部添加跟踪代码

```javascript
import Cml from 'chameleon-runtime';
var gio = require("utils/gio-minp/index.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', cml: Cml });
```

方式2：

新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数

```javascript
import Cml from 'chameleon-runtime';
export default {
    projectId: '你的 GrowingIO 项目ID',
    appId: '你的小程序AppID',
    version: '小程序版本',
    cml: Cml,
    // ...
}
```

在根目录 app.cml文件的顶部添加跟踪代码

```javascript
var gio = require("utils/gio-minp/index.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}
{% endtabs %}

### SDK参数配置

SDK中提供了以下几个参数可以用来进行配置。

| 参数 | 类型/值 | 说明 |
| :--- | :--- | :--- |


| version | string | 你的小程序的版本号。 |
| :--- | :--- | :--- |


| getLocation autoGet | true \| false | 是否自动获取用户的地理位置信息。默认false |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">getLocation type</th>
      <th style="text-align:left">wgs84 | gcj02</th>
      <th style="text-align:left">
        <ul>
          <li>wgs8&#xFF1A;&#x6807;&#x51C6;&#x5750;&#x6807;&#x7CFB;</li>
          <li>gcj02&#xFF1A;&#x706B;&#x661F;&#x5750;&#x6807;&#x7CFB;</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| followShare | true \| false | 详细跟踪分享数据，开启后可使用分享分析功能。默认true |
| :--- | :--- | :--- |


| forceLogin | true \| false | 你的小程序是否强制要求用户登陆微信获取 openid。默认 false |
| :--- | :--- | :--- |


| debug | true \| false | 是否开启调试模式，可以看到采集的数据。默认 false |
| :--- | :--- | :--- |


| usePlugin | true \| false | 你的小程序中是否使用了第三方插件。默认false |
| :--- | :--- | :--- |


每次发布小程序新版本的时候，需要更新一下版本号 version, 与线上发布小程序保持一致; 可以在 GrowingIO 平台使用 “App 版本”维度，分析不同版本的数据。

#### getLocation

根据微信最新的用户地理位置获取的规则，GrowingIO 小程序SDK 默认不会在小程序启动时获取用户的坐标信息。

* 如果您的小程序在打开时就需要获取用户地理信息，就可以将这个参数配置为true。

在 gioConfig.js 文件中将 getLocation 配置如下：

```java

```

getLocation: { //是否自动获取用户的地理位置信息, 并设置获取方式 autoGet: true, //默认不自动获取 type: 'gcj02' //支持wgs84 \| gcj02为火星坐标系, 默认wgs84 },

```text

```

* GrowingIO SDK 默认不会在小程序启动时获取用户的坐标信息。当用户访问到某一功能时需要位置信息时，可以调用以下位置接口，补发vst，采集位置信息，提升用户地域分布的分析准确性。

```java
// 获取用户的地理信息
gio('getLocation')
```

#### followShare

转发分享小程序是小程序获客的重要场景，想要详细的进行转发分享的统计，需要在SDK参数中，设置如下参数，默认值为true

在 gioConfig.js 文件中将 followShare 配置如下:

```javascript
followShare: true,     //是否详细跟踪分享数据，开启后可使用分享分析功能。默认true
```

#### forceLogin

GrowingIO 默认会在小程序里面设置用户标识符，存储在微信 Storage 里面。这个用户标识符潜在可能会被`clearStorage` 清除掉，所以有可能不同的用户标识符对应同一个微信里的 `OpenID`。

如果你的微信小程序在用户打开后会获取 `OpenID` ，可以设置 `forceLogin` 为 true，此时用户标识符会使用 `OpenID`，潜在风险是如果没有获取到`openID`，数据不会发送。

集成示例：

> 在 gioConfig.js 文件中将 forceLogin 配置如下:

```javascript
forceLogin: true,      //是否强制要求用户登陆微信获取 openid。默认 false
```

{% hint style="danger" %}
如果用户在打开您的微信小程后没有使用微信授权登录，但是小程序配置了forceLogin为true，此时GrowingIO 不能采集到的用户的数据 ，采集到的用户也会偏少，所以请特别注意这个参数的设置。

如果您不能确定是否要设置这个参数，请先咨询我们。
{% endhint %}

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

下面介绍专门针对用户的接口

#### 绑定微信用户ID（identify）

当用户在你的小程序上登录获取到 OpeniID后，可以通过 `identify` 接口绑定微信用户ID，后续在 GrowingIO 中获取更准确的微信访问用户量。

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

#### 设置登录**用户**ID

当用户在你的小程序上注册以后，你的产品应用服务端会在用户数据库里添加一条记录并且分配一个 ID，可以通过 setUserId 接口设置注册用户ID，后续在 GrowingIO 中分析登录用户这个数据。示例代码如下。

```java
gio('setUserId', YOUR_USER_ID);
```

#### 清除登录用户ID

用户退出登录时，清除登录用户ID。

```java
gio('clearUserId');
```

#### 设置登录用户属性

当用户在你的小程序上传了注册用户ID后，可以通过 setUser 接口设置注册用户信息，后续在 GrowingIO 中分析这个数据。示例代码如下：

```java
gio('setUserId', user.id); 
gio('setUser', { id: user.id, name: user.name });
```

## 3. 添加请求服务器域名

要正常采集微信小程序的数据并发送给 GrowingIO，需要在微信小程序里事先设置一个通讯域名，允许跟 GrowingIO API 服务器进行网络通信。具体步骤如下：

1. 登陆微信小程序后台，进入开发。
2. 打开开发设置，到服务器域名配置部分。
3. 在`request合法域名`中添加：[https://wxapi.growingio.com](https://wxapi.growingio.com)

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2844%29.png)

## 4. 无埋点采集事件逻辑和高级配置

#### 访问数据 <a id="fang-wen-shu-ju"></a>

每次用户打开小程序的时候，发送一条`应用打开`消息，对应的数据指标是打开次数。发送数据包含但不限于以下信息：进入页面、进入时间、场景值、来源小程序或 App、设备信息、微信信息、应用版本号。

每次用户关闭小程序的时候，关闭动作包括退出小程序回到微信、退出微信，会发送一条`应用关闭`消息，会根据这个消息来计算应用访问时长。发送数据包含但不限于以下信息：退出页面、退出时间。

#### 页面数据 <a id="ye-mian-shu-ju"></a>

每次用户访问一个新的页面，发送一条`页面打开`消息，对应的数据意义是页面分析。发送数据包含但不限于以下信息：页面信息、打开时间、页面来源、页面标题、页面级变量。

每次当用户点击转发按钮时，会弹出转发框，这时会发送一条`要转发消息`消息。这是一个自定义事件，数据包含以下信息：事件时间、所在页面、转发动作来源、转发页面标题和转发页面路径。注意这个事件不代表用户真正转发了消息到聊天里面，而是用户触发了转发动作。如果要跟踪成功转发消息事件，建议在 onShareAppMessage 的 success callback 里面发送一个自定义事件。

#### 行为数据

对于用户在页面发生的行为，如果这个行为有绑定事件比如 bindtap，并且在你的小程序里面进行处理，那么 GrowingIO 的小程序 SDK 会自动采集这些事件，发送一条行为消息。目前，我们支持的事件有 tap、longpress、confirm 和 change 事件。

#### tap

tap 事件是手指触摸后马上离开时触发的事件。当 wxml 中的 view 绑定了 bindtap 事件以后，在事件处理函数执行的时候，SDK 会自动采集 tap 事件，发送数据包含但不限于以下信息：点击事件时间、事件发生所在页面、点击控件相关信息

代码示例

比如如下&lt;view data-title='复仇者联盟3' data-index='1' bindtap='clickMovie'&gt;

```java
<view data-title='复仇者联盟3' data-index='1' bindtap='clickMovie'>
    <image src='IMAGE—URL' mode='aspectFill'/>
    <text>复仇者联盟3</text>
</view>
```

注意这里的 `data-title` 和 `data-index` 属性，因为微信小程序的限制，无法采集到控件的内容和结构数据，所以在小程序 SDK 里面我们采取的是声明式编程，通过在 wxml 文件里面设置 data- 属性，可以给 view 控件添加额外的`内容`和`位置`属性，方便后续在分析时可以按照元素内容和元素位置做分析，对于列表式的组件特别有用和方便。

{% hint style="info" %}
**建议在 View 的控件里面多使用 data-title 和 data-index 属性这种声明式编程方式。**
{% endhint %}

#### longpress

longpress 事件是手指触摸后，超过350ms再离开时触发的事件。当 wxml 的 view 绑定了 bindlongpress 事件以后，在事件处理函数执行的时候，SDK 会自动采集 longpress 事件，发送数据包含但不限于以下信息：点击事件时间、事件发生所在页面、点击控件相关信息。

示例代码

```java
<view data-title='复仇者联盟3' data-index='1' bindtap='clickMovie'>
  <image src='IMAGE—URL' mode='aspectFill'/>
  <text>复仇者联盟3</text>
</view>
```

注意这里的 `data-title` 和 `data-index` 属性，因为微信小程序的限制，无法采集到控件的内容和结构数据，所以在小程序 SDK 里面我们采取的是声明式编程，通过在 wxml 文件里面设置 data- 属性，可以给 view 控件添加额外的`内容`和`位置`属性，方便后续在分析时可以按照元素内容和元素位置做分析，对于列表式的组件特别有用和方便。

{% hint style="info" %}
**建议在 View 的控件里面多使用 data-title 和 data-index 属性这种声明式编程方式。**
{% endhint %}

#### change

change 事件是针对 checkbox、radio、picker-view 这些控件，当选择项发生改变时触发的事件。当 wxml 的 view 绑定了 bindchange 事件以后，在事件处理函数执行的时候，SDK 会自动采集 change 事件，发送数据包含但不限于以下信息：选择事件的发生时间、事件发生所在页面。如果设置了要采集内容，则也会包含选择项的内容信息。

代码示例

```java
<checkbox-group bindchange='checkboxChange' data-growing-track>
  <label class='checkbox'>
    <checkbox value='GrowingIO' checked='true' /> GrowingIO
  </label>
  <label class='checkbox'>
    <checkbox value='Tencent' checked='false' /> 腾讯小程序分析工具
  </label>
  <label class='checkbox'>
    <checkbox value='Google' checked='false' /> Google Analytics
  </label>
</checkbox-group>
```

当用户选择了某项以后，因为这里设置了 `data-growing-track` 属性，所以会采集到这一项对应的 value 值。

#### confirm

confirm 事件是对于 input 和 textarea 控件，当输入完成后触发的事件。当 wxml 的 view 绑定了 bindconfirm 事件以后，在事件处理函数执行的时候，SDK 会自动采集 confirm 事件，发送数据包含但不限于以下信息：输入事件的发生时间、事件发生所在页面。如果设置了要采集内容，则也会包含输入的内容。

代码示例

```java
<input class='new-todo'
       value='{{ input }}'
       placeholder='Anything here...'
       data-growing-track='true'
       bindinput='inputChangeHandle'
       bindconfirm='addTodoHandle'
/>
```

当用户输入完成后，因为这里指定了 `data-growing-track` 属性，所以会采集到输入的内容。

#### navigator组件

如果您的小程序使用了navigator组件，需要您手动绑定一个空的点击事件，GrowingIO才能实现跳转点击的采集。

```java
<navigator ...>
  <view bindtap="nameForThisClickButton">
     ...
  </view>
</navigator>
```

## 5. 设置半自动采集浏览事件

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

### 标记半自动采集元素

使用此方法标记元素的浏览时，请在console验证cstm事件。

{% hint style="info" %}
class 中必须加 growing\_collect\_imp 。
{% endhint %}

```markup
<view class="page-section growing_collect_imp" data-gio-imp-track='测试imp打点2' data-gio-track-age='18' data-gio-track-name='xxx' id='test_imp'>
  // ......
</view>
```

### 注册监听

在对应的 Page.js 的onShow方法中，调用 gio\('collectImp', this\)

```java
Page({
  // ...
  onShow: function () {
    gio('collectImp', this)
  },
  // ...
})
```

## 6. 自定义数据上传API

{% hint style="info" %}
小程序自定义事件和变量的埋点代码，建议放在onShow的生命周期函数中。
{% endhint %}

自定义数据上传API，请参考[自定义数据上传API](customize-api.md)。

## 7. 创建应用

在GrowingIO平台的创建微信小程序应用。创建应用请参考查看[创建应用](../../../chan-pin-shi-yong-wen-dang-fen-ban/xiang-mu-guan-li/application-manage.md#chuang-jian-ying-yong)。

## 8. 验证SDK是否正常采集数据

了解GrowingIO平台数据采集类型请参考[数据模型](../../../introduction/datamodel/)。

GrowingIO为您提供多种验证SDK是否正常采集数据的方式：

方式一：[小程序&内嵌页Debugger](../../debugging/minpdebugger.md)

方式二：在SDK中设置了Debug模式后，在微信开发者工具中查看数据采集日志。

方式三：[数据校验](../../../chan-pin-shi-yong-wen-dang-fen-ban/shu-ju-zhong-xin/shu-ju-xiao-yan/datacheck.md)

