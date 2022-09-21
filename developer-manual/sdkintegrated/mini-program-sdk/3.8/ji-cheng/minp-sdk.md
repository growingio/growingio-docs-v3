# 微信小程序

对于微信小程序多样的开发方式，我们给出了主流开发方式的集成方法参考。如您使用了其他开发方式，请咨询我们。

如果您使用跨平台框架开发且有多端（特指小程序，快应用、App和Web除外）同时需要集成SDK的需求时，只需在框架代码中集成一次即可。例：

> 使用uni-app同时开发微信小程序和阿里(支付宝)小程序，只需集成一次即可。

## 准备条件

1、在 GrowingIO 平台中获取项目Id，获取方法请参考"项目管理 > 项目概览 > [查看项目基本信息](../../../../../product-manual/projectmange/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

2、在您的小程序中获取`appId`。

3、在下列选项中选择对应的开发框架，并下载对应的SDK文件存放在项目中或使用npm的方式集成。下文中以`utils/gio`目录作为下载集成的示例目录(目录和SDK文件可自定义重命名)。

## 在小程序中集成

参考示例在 app.js/main.js 小程序主文件中添加初始化代码。添加位置参考示例代码，注意不要随意修改初始化代码位置。**SDK不支持在小程序中任意生命周期中进行初始化。**

### Native原生

**1、加载SDK**

微信原生SDK下载：[https://assets.giocdn.com/sdk/minip/saas/3.8.7/gio-wechat.js](https://assets.giocdn.com/sdk/minip/saas/3.8.7/gio-wechat.js)

> (如果您点击链接在浏览器中直接打开了文件并不是下载文件，请尝试右键点击链接，选择 `链接存储为...` 即可正常触发下载)

**2、使用`init`方法进行初始化**

注意`init`方法所处位置在App实例之前。

**示例代码**

```javascript
// app.js
import gio from './utils/gio/gio-wechat.js';

gio('init', 'your GrowingIO 项目ID', 'your AppId', {
    version: 'your miniProgram version',
    ...other settings
});

App({ ... });
```

### uni-app 框架

**1、加载SDK**

**方式一：下载本地集成**

uni-app框架SDK下载：[https://assets.giocdn.com/sdk/minip/saas/3.8.7/gio-uniapp.js](https://assets.giocdn.com/sdk/minip/saas/3.8.7/gio-uniapp.js)

> (如果您点击链接在浏览器中直接打开了文件并不是下载文件，请尝试右键点击链接，选择 `链接存储为...` 即可正常触发下载)

**方式二：npm集成**

```bash
npm i gio-miniprogram-sdk-saas --save
```

**2、使用`init`方法进行初始化**

注意`init`方法所处位置（vue2和vue3中分别与app实例的相对位置不同）

**示例代码**

{% tabs %}
{% tab title="uni-app(vue2)" %}
```javascript
// main.js
import Vue from 'vue';
import App from './App.vue';
// 下载集成方式
import gio from './utils/gio/gio-uniapp.js';
// npm集成方式
import gio from 'gio-miniprogram-sdk-saas/gio-uniapp';

App.mpType = 'app';

gio('init', 'your GrowingIO 项目ID', 'your AppId', {
    version: 'your miniProgram version',
    uniVue: Vue,
    ...other settings
});

// 注意vue2中app实例在初始化之后
const app = new Vue(App);
app.$mount();
```
{% endtab %}

{% tab title="uni-app(vue3)" %}
```javascript
// main.js
import App from './App.vue';
import { createApp } from 'vue';
// 下载集成方式
import gio from './utils/gio/gio-uniapp.js';
// npm集成方式
import gio from 'gio-miniprogram-sdk-saas/gio-uniapp';

export function createApp() {
  // 注意vue3中app实例在初始化之前
  const app = createApp(App);

  gio('init', 'your GrowingIO 项目ID', 'your AppId', {
      version: 'your miniProgram version',
      uniVue: app,
      ...other settings
  });

  return { app };
}
```
{% endtab %}
{% endtabs %}

### Taro 框架

**1、加载SDK**

**方式一：下载本地集成**

Taro框架SDK下载：[https://assets.giocdn.com/sdk/minip/saas/3.8.7/gio-taro.js](https://assets.giocdn.com/sdk/minip/saas/3.8.7/gio-taro.js)

> (如果您点击链接在浏览器中直接打开了文件并不是下载文件，请尝试右键点击链接，选择 `链接存储为...` 即可正常触发下载)

**方式二：npm集成**

```bash
npm i gio-miniprogram-sdk-saas --save
```

**2、使用`init`方法进行初始化**

注意`init`方法所处位置（vue2和vue3中分别与app实例的相对位置不同）。使用vue开发时`taro`和`taroVue`都要传。

**示例代码**

{% tabs %}
{% tab title="Taro2" %}
````javascript
// app.jsx
import Taro, { Component } from '@tarojs/taro';
// 下载集成方式
import gio from './utils/gio/gio-taro.js';
// npm集成方式
import gio from 'gio-miniprogram-sdk-saas/gio-taro';

gio('init', 'your GrowingIO 项目ID', 'your AppId', {
    version: 'your miniProgram version',
    taro: Taro,
    ...other settings
});

class App extends Component { ... }
Taro.render(<App />, document.getElementById('app'));
```
````
{% endtab %}

{% tab title="Taro3(react)" %}
额外安装bable插件

```bash
npm i babel-plugin-setname --save
```

```javascript
// babel.config.js
module.exports = {
  presets: [['taro', { framework: 'react' }]],
  plugins: [
    [
      'babel-plugin-setname', {
        includes: ['src'],
        lower: false, // 从taro2升级至3时请修改为true
      }
    ]
  ]
};
```

```javascript
import React, { Component } from 'react';
import Taro from '@tarojs/taro';
// 下载集成方式
import gio from './utils/gio/gio-taro.js';
// npm集成方式
import gio from 'gio-miniprogram-sdk-saas/gio-taro';

gio('init', 'your GrowingIO 项目ID', 'your AppId', {
    version: 'your miniProgram version',
    taro: Taro,
    ...other settings
});

class App extends Component { ... }
export default App;
```
{% endtab %}

{% tab title="Taro3(vue2)" %}
```javascript
// app.js
import Vue from 'vue';
import Taro from '@tarojs/taro';
// 下载集成方式
import gio from './utils/gio/gio-taro.js';
// npm集成方式
import gio from 'gio-miniprogram-sdk-saas/gio-taro';

gio('init', 'your GrowingIO 项目ID', 'your AppId', {
    version: 'your miniProgram version',
    taro: Taro, // 注意taro和taroVue都需要传
    taroVue: Vue, // 注意taro和taroVue都需要传
    ...other settings
});

// 注意vue2中App实例在初始化之后
const App = { ... };
export default App;
```
{% endtab %}

{% tab title="Taro3(vue3)" %}
```javascript
// app.js
import { createApp } from 'vue';
import Taro from '@tarojs/taro';
// 下载集成方式
import gio from './utils/gio/gio-taro.js';
// npm集成方式
import gio from 'gio-miniprogram-sdk-saas/gio-taro';

// 注意vue3中App实例在初始化之前
const App = createApp({ ... });

gio('init', 'your GrowingIO 项目ID', 'your AppId', {
    version: 'your miniProgram version',
    taro: Taro, // 注意taro和taroVue都需要传
    taroVue: App, // 注意taro和taroVue都需要传
    ...other settings
});

export default App;
```
{% endtab %}
{% endtabs %}

### Chameleon 框架

****[**​**](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/integration/wechat#chameleon%E6%A1%86%E6%9E%B6sdk%E4%B8%8B%E8%BD%BDhttpsassetsgiocdncomsdkminipcdp380-rc6gio-chameleonjs)**1、加载SDK**

**方式一：下载本地集成**

Chameleon框架SDK下载：[https://assets.giocdn.com/sdk/minip/saas/3.8.7/gio-chameleon.js](https://assets.giocdn.com/sdk/minip/saas/3.8.7/gio-chameleon.js)

> (如果您点击链接在浏览器中直接打开了文件并不是下载文件，请尝试右键点击链接，选择 `链接存储为...` 即可正常触发下载)

**方式二：npm集成**

```bash
npm i gio-miniprogram-sdk-saas --save
```

**2、使用`init`方法进行初始化**

注意`init`方法所处位置在App实例之前。

**示例代码**

```javascript
// app.cml
import Cml from 'chameleon-runtime';
// 下载集成方式
import gio from './utils/gio/gio-chameleon.js';
// npm集成方式
import gio from 'gio-miniprogram-sdk-saas/gio-chameleon';

gio('init', 'your GrowingIO 项目ID', 'your AppId', {
    version: 'your miniProgram version',
    cml: Cml
    ...other settings
});

class App { ... }

export default new App();
```

### WePY2 框架

**1、加载SDK**

**方式一：下载本地集成**

WePY2框架SDK下载：[https://assets.giocdn.com/sdk/minip/saas/3.8.7/gio-wepy.js](https://assets.giocdn.com/sdk/minip/saas/3.8.7/gio-wepy.js)

> (如果您点击链接在浏览器中直接打开了文件并不是下载文件，请尝试右键点击链接，选择 `链接存储为...` 即可正常触发下载)

**方式二：npm集成**

```bash
npm i gio-miniprogram-sdk-saas --save
```

**2、使用`init`方法进行初始化**

注意`init`方法所处位置在App实例之前。

**示例代码**

```javascript
// app.wpy
import wepy from 'wepy';
// 下载集成方式
import gio from './utils/gio/gio-wepy.js';
// npm集成方式
import gio from 'gio-miniprogram-sdk-saas/gio-wepy';

gio('init', 'your GrowingIO 项目ID', 'your AppId', {
    version: 'your miniProgram version',
    wepy: wepy,
    ...other settings
});

wepy.app({ ... });
```

### Remax 框架

**1、加载SDK**

**方式一：下载本地集成**

Remax框架SDK下载：[https://assets.giocdn.com/sdk/minip/saas/3.8.7/gio-remax.js](https://assets.giocdn.com/sdk/minip/saas/3.8.7/gio-remax.js)

> (如果您点击链接在浏览器中直接打开了文件并不是下载文件，请尝试右键点击链接，选择 `链接存储为...` 即可正常触发下载)

**方式二：npm集成**

```bash
npm i gio-miniprogram-sdk-saas --save
```

**2、使用`init`方法进行初始化**

注意`init`方法所处位置在App实例之前。

**示例代码**[**​**](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/integration/wechat#%E5%A6%82%E6%9E%9C%E6%82%A8%E7%82%B9%E5%87%BB%E9%93%BE%E6%8E%A5%E5%9C%A8%E6%B5%8F%E8%A7%88%E5%99%A8%E4%B8%AD%E7%9B%B4%E6%8E%A5%E6%89%93%E5%BC%80%E4%BA%86%E6%96%87%E4%BB%B6%E5%B9%B6%E4%B8%8D%E6%98%AF%E4%B8%8B%E8%BD%BD%E6%96%87%E4%BB%B6%E8%AF%B7%E5%B0%9D%E8%AF%95%E5%8F%B3%E9%94%AE%E7%82%B9%E5%87%BB%E9%93%BE%E6%8E%A5%E9%80%89%E6%8B%A9-%E9%93%BE%E6%8E%A5%E5%AD%98%E5%82%A8%E4%B8%BA-%E5%8D%B3%E5%8F%AF%E6%AD%A3%E5%B8%B8%E8%A7%A6%E5%8F%91%E4%B8%8B%E8%BD%BD-5)

```javascript
// app.js
import * as remax from 'remax';
// 下载集成方式
import gio from './utils/gio/gio-remax.js';
// npm集成方式
import gio from 'gio-miniprogram-sdk-saas/gio-remax';

gio('init', 'your GrowingIO 项目', 'your AppId', {
    version: 'your miniProgram version',
    remax: remax,
    ...other settings
});

const App = (props) => props.children;

export default App;
```

## 小程序插件中集成

[小程序插件](https://developers.weixin.qq.com/miniprogram/introduction/plugin.html)中集成SDK参考小程序集成，在指定的插件 Component 组件的 js 中集成即可。SDK 初始化时会自动切换为插件模式，将当前 Component 视为一个独立应用发送VISIT事件。

```javascript
// myComponent.js
import gio from './utils/gio/sdk.js';

gio('init', 'your GrowingIO 项目ID', 'your AppId', {
    version: 'your miniProgram version',
    ...other settings
});

Component({ ... });
```

## 添加白名单

要正常采集微信小程序的数据并发送给 GrowingIO，需要事先设置一个通讯域名，允许跟 GrowingIO API 服务器进行网络通信。具体步骤如下：

1. 登陆[微信小程序后台](https://mp.weixin.qq.com/)，进入开发。
2. 打开开发设置，到服务器域名配置部分。
3. 在 **request 合法域名**中添加：https://wxapi.growingio.com

{% hint style="info" %}
请注意：如果小程序通过第三方平台发布代码，在发布代码之前，需要调用接口在requestdomain中添加`https://your serverHost`，参考[小程序官方第三方说明](https://developers.weixin.qq.com/doc/oplatform/Third-party\_Platforms/2.0/api/Mini\_Program\_Basic\_Info/Server\_Address\_Configuration.html)。
{% endhint %}

## 数据校验

GrowingIO为您提供多种验证SDK是否正常采集数据的方式：

方式一：[小程序&内嵌页Debugger](../../../../debugging/minpdebugger.md)（可能会受网络等因素影响，建议使用方式二）

方式二：在SDK中设置了Debug模式后，在开发者工具中查看数据采集日志。
