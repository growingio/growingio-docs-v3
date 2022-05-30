# 微信小程序 SDK

## 准备条件

获取项目ID，获取方法请参考"项目管理 > 项目概览 > [查看项目基本信息](../../../product-manual/projectmange/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

## 1. 添加跟踪代码

**选择对应开发框架添加代码**

{% tabs %}
{% tab title="原生" %}
1. 下载微信小程序SDK，并解压。下载地址：[https://assets.giocdn.com/sdk/gio-minp.zip](https://assets.giocdn.com/sdk/gio-minp.zip)
2. 将解压后的`gio-minp`目录放在小程序目录下（比如：/src/utils目录）。
3. 添加代码：

方式1：

在根目录app.js文件的顶部添加跟踪代码：

```javascript
var gio = require("utils/gio-minp/index.js").default;
gio('init', '您的 GrowingIO 项目ID', '您的小程序AppID', { version: '小程序版本' });
```

方式2：

新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的必要配置参数：

```javascript
export default {
    projectId: '您的 GrowingIO 项目ID',
    appId: '您的小程序AppID',
    version: '小程序版本'
    // ...
}
```

在根目录 app.js文件的顶部添加跟踪代码：

```javascript
var gio = require("utils/gio-minp/index.js").default;
var gioConfig = require("您的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}

{% tab title="原生+第三方插件" %}
1. 下载微信小程序SDK，并解压。下载地址：[https://assets.giocdn.com/sdk/gio-minp.zip](https://assets.giocdn.com/sdk/gio-minp.zip)
2. 将解压后的`gio-minp`目录放在小程序目录下（比如：/src/utils目录）。
3. 添加代码：

#### 一、安装 SDK

**安装方式 1：**

在根目录app.js文件的顶部添加跟踪代码

```javascript
var gio = require("utils/gio-minp/index.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', usePlugin: true });
const App = global.GioApp;
```

**安装方式 2：**

新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的必要配置参数：

```javascript
export default {
    projectId: '你的 GrowingIO 项目ID',
    appId: '你的小程序AppID',
    version: '小程序版本',
    usePlugin: true 
    // ...
}
```

在根目录 app.js 文件的顶部添加跟踪代码：

```javascript
var gio = require("utils/gio-minp/index.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
// app.js 文件，在文件顶部 （其他代码之前）添加如下代码:
const App = global.GioApp
```

#### 二、修改页面及自定义组件定义

在每个page页面（新增页面也需要添加）的 .js 文件顶部添加如下代码：

```javascript
// 在每个 Page 页面的 .js 文件顶部（其他代码之前）添加如下代码。
// 请注意是每个 Page 都要引入
const Page = global.GioPage;
```

如果使用了自定义组件（Component ）在每个 Component 的 .js 文件顶部添加如下代码：

```javascript
// 在每个 Component 的 .js 文件顶部（其他代码之前）添加如下代码。
// 请注意是每个自定义 Component  都要引入
const Component = global.GioComponent;
```

如果使用了自定义组件（Behavior）在每个 Behavior 的 .js 文件顶部添加如下代码：

```javascript
// 在每个 Behavior 的 .js 文件顶部（其他代码之前）添加如下代码。
// 请注意是每个自定义 Behavior 都要引入
const Behavior = global.GioBehavior;
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

```
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

## 2. SDK初始化参数配置

SDK中提供了以下几个参数可以用来进行配置。

| **参数**              | 类型/值           | 说明                                                          |
| ------------------- | -------------- | ----------------------------------------------------------- |
| version             | string         | 您的小程序的版本号                                                   |
| getLocation.autoGet | true \| false  | 是否自动获取用户的地理位置信息，默认 false (3.7.5+版本不支持)                      |
| getLocation.type    | wgs84 \| gcj02 | wgs8：标准坐标系；gcj02：火星坐标系(3.7.5+版本不支持)                         |
| followShare         | true \| false  | 详细跟踪分享数据，开启后可使用分享分析功能，默认true                                |
| forceLogin          | true \| false  | 是否开启强制登录模式，默认 false                                         |
| debug               | true \| false  | 是否开启调试模式，可以在 console 打印采集的数据，默认 false。发布到生产环境时需关闭！！！        |
| usePlugin           | true \| false  | 您的小程序中是否使用了第三方插件，默认 false                                   |
| comAsPage           | true \| false  | 是否将 component 当做页面处理，默认 false。SDK 3.6.1 版本添加                |
| autotrack           | true \| false  | <p>是否开启无埋点采集<br>包括：<code>click, change, submit</code></p>   |
| dataCollect         | true \| false  | 是否开启数据采集，设为false不进行任何数据采集                                   |
| enableEventStore    | true \| false  | 是否开启事件本地存储，默认false；设为true，则会开启本地存储，使用运营SDK需设置（SDK版本>=3.7.4） |

{% hint style="info" %}
**每次发布小程序新版本的时候，需要更新一下版本号 version 配置， 与线上发布小程序保持一致; 可以在 GrowingIO 平台使用 “App 版本”维度，分析不同版本的数据。**
{% endhint %}

### 数据采集开关

#### 配置`dataCollect`

{% hint style="info" %}
如果您的小程序需要进行合规检查，请参考[小程序合规说明](../compliance/xiao-cheng-xu-sdk-he-gui-shuo-ming.md)
{% endhint %}

默认情况下，SDK开启数据采集。如果您需要初始化时暂时关闭数据采集，可在初始化配置中设置 `dataCollect: false` 关闭采集。 初始化关闭数据采集后，至您打开数据采集之前都不会采集数据和上报。

```

gio('init', ' GrowingIO 项目ID', '您的小程序AppID', {
  version: '1.0.0',
  dataCollect: false  
});
```

#### 调用接口 `setDataCollect`

默认开启数据采集。当设置为 `false` 时，SDK将不会采集和上报事件。当设置为 `true` 时，SDK将开启采集和上报事件。

```
gio('setDataCollect', true);
```

### 事件存储开关

**配置`enableEventStore`**

默认情况下，SDK关闭事件存储功能。此功能在小程序storage中存储SDK已上报的事件数据，用于运营SDK消费，**隔天清空**。\
**如果您不使用运营SDK可忽略此配置；如果您使用运营SDK，必须开启此配置项，设置为 `true`。**

### 采集GPS数据

#### 配置 `getLocation`

{% hint style="info" %}
3.7.5+版本不支持，请使用  [`setLocation`](customize-api.md#she-zhi-wei-zhi-xin-xi) `接口`
{% endhint %}

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

在需要分析社会关系的页面内，页面的分享方法需添加contentType、contentId字段，示例如下:

```javascript
onShareAppMessage: function() {
    // ...
    return {
        title: '自定义转发标题',
        path: 'xxxxxx',
        contentType: '内容类型',
        contentId: '内容ID'
    }
}
```

### 强制登录模式

**配置`forceLogin`**

默认情况下，SDK 会自动生成访问用户ID来标识访问用户，存储在微信 Storage 里面。这个用户标识符潜在可能会被`clearStorage` 清除掉，所以有可能不同的自动生成访问用户ID对应同一个微信里的 `OpenID。`

如您需要使用 openId 或 unionId 标识访问用户，可以在初始化配置中设置 `forceLogin: true` 来打开强制登录模式。

强制登录模式适用于打开小程序就调用 `wx.login` ([参考文档](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/login/wx.login.html)) 获取 openId 或 unionId 的小程序。 开启此模式并调用 `identity` 上报 openid 或 unionId，会将上报的 Id 作为访问用户ID，平台统计数据中访问用户量会与微信后台的比较接近。

设置`forceLogin`为`true`后，SDK会继续采集但暂停上报数据，待调用 `wx.login`后获取 openId 或 unionId，调用 `identify` 方法后开始数据上报。**调用 `identify` 会替换事件数据的 u(访问用户ID) 字段的值 为设定值（一般是小程序openId 或 unionId），包括调用`identify`之前触发的事件**

需在 gioConfig.js 文件或初始化配置项将 forceLogin 配置如下:

```javascript
forceLogin: true, //是否强制要求调用 wx.login 获取 opend 或 unionId。默认 false
```

获取到 openId 或  unionId 后调用 [`identify`](minp-sdk.md#bang-ding-wei-xin-yong-hu-openid-unionid) 接口。

{% hint style="danger" %}
适用于打开小程序就调用 `wx.login` 获取 openId 或 unionId 的小程序。

小程序SDK初始化时配置了 `forceLogin` 为 `true`，如果打开小程序后没有调用 `wx.login` 获取 openId 或 unionId，没有调用 `identify` 方法，会导致SDK不能上报数据，访问数据将大幅减少。如果调用了`，但时机不在小程序打开时，而在小程序使用中较晚的时机，在调用之前若小程序关闭则会造成此次访问过程中采集的数据丢失。`\
如果小程序首页中使用的是内嵌H5页面，需要使用内嵌H5用户数据打通功能。该场景下，需要在小程序冷启动时，使用开屏页(在小程序首页 page 前增加一个 page 开屏页)。

如果您不能确定是否要设置这个参数，请先咨询我们技术支持。
{% endhint %}

## 3. 添加请求服务器域名

要正常采集微信小程序的数据并发送给 GrowingIO，需要在微信小程序里事先设置一个通讯域名，允许跟 GrowingIO API 服务器进行网络通信。具体步骤如下：

1. 登陆微信小程序后台，进入开发。
2. 打开开发设置，到服务器域名配置部分。
3. 在 **request 合法域名**中添加：https://wxapi.growingio.com

![request 合法域名](<../../../.gitbook/assets/image (88).png>)

## 4. 微信用户信息配置

### 绑定微信用户 openId 、unionId

上报微信信息，支持按照 openId、unionId 进行用户分群，以及使用微信推送等高级功能。

当您的小程序调用 `wx.login` 获取到 openId、unionId 后，可以通过 `identify` 接口绑定微信用户 openId 、unionId，后续在 GrowingIO 平台用户分群功能使用。

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
wx.login({
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

### 微信用户属性设置

作为用户行为数据分析工具，用户信息的完善会给后续的分析带来很大的帮助。在小程序中，微信用户属性是非常重要的设置，只有完善了微信用户属性信息，系统自带的微信访问用户变量（如下表）才可以在分析工具中使用，交互数据定义、数据校验功能才会方便通过用户微信相关的信息（微信姓名和头像）定位用户。

| 系统自带的微信访问用户变量 |
| ------------- |
| 微信用户所在城市      |
| 微信用户所在省       |
| 微信用户所在国家      |
| 微信用户的性别       |

当您的小程序上获取到微信用户信息后，可以通过 `setVisitor` 接口上报微信用户信息，后续在 GrowingIO 平台中使用上述变量分析微信用户属性数据。

**接口定义**

```java
gio('setVisitor', userInfo)
```

**参数说明**

| 名称       | 类型     | 是否必须 | 说明     |
| -------- | ------ | ---- | ------ |
| userInfo | Object | 是    | 微信用户信息 |

**示例代码**

```java
wx.getUserInfo({ 
  success: res => 
    // ...
    gio('setVisitor', res.userInfo);
})
```

{% hint style="info" %}
微信用户信息包含**微信昵称**、**微信头像**、**性别**、**微信所填国家**、**微信所填省份**、**微信所填城市**。

性别、微信所填国家、微信所填省份、微信所填城市会作为访问用户变量，这些访问用户变量标识符平台会自动生成，无需添加配置。

用户画像中的部分数据，只有在设置微信用户信息后，才可以统计。
{% endhint %}

## 5. 无埋点采集逻辑和高级配置

在进行无埋点数据采集时，您需要了解和使用[无埋点采集逻辑及行为数据采集的高级配置](wu-mai-dian-cai-ji-luo-ji-he-gao-ji-pei-zhi.md)

## 6. 自定义数据上传API

{% hint style="info" %}
小程序自定义数据上报的埋点代码，建议放在onShow的生命周期函数之后。
{% endhint %}

自定义数据上传API，请参考[自定义数据上传API](customize-api.md)。

## 7. 创建应用

请在添加了跟踪代码的微信小程序重新启动几次，发送数据给 GrowingIO。

在GrowingIO平台的创建微信小程序应用。创建应用请参考查看[创建应用](../../../product-manual/projectmange/application-manage.md#chuang-jian-ying-yong)。

## 8. 验证SDK是否正常采集数据

了解GrowingIO平台数据采集类型请参考[数据模型](../../../introduction/datamodel/)。

GrowingIO为您提供多种验证SDK是否正常采集数据的方式：

方式一：[小程序&内嵌页Debugger](../../debugging/minpdebugger.md)

方式二：在SDK中设置了Debug模式后，在微信开发者工具中查看数据采集日志。

方式三：[数据校验](https://docs.growingio.com/v3/product-manual/data-center/datacheck/)
