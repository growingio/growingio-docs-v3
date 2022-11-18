# 百度小程序

对于百度小程序多样的开发方式，我们给出了主流开发方式的集成方法参考。如您使用了其他开发方式，请咨询我们。

如果您使用跨平台框架开发且有多端（特指小程序，快应用、App和Web除外）同时需要集成SDK的需求时，只需在框架代码中集成一次即可。例：

> 使用uni-app同时开发微信小程序和阿里(支付宝)小程序，只需集成一次即可。

## 准备条件

1、在 GrowingIO 平台中获取项目Id，获取方法请参考"项目管理 > 项目概览 > [查看项目基本信息](../../../../../product-manual/projectmange/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

2、在您的小程序中获取`appId`。

3、在下列选项中选择对应的开发框架，并下载对应的SDK文件存放在项目中或使用npm的方式集成。下文中以`utils/gio`目录作为下载集成的示例目录(目录和SDK文件可自定义重命名)。

## 集成

参考示例在 app.js/main.js 小程序主文件中添加初始化代码。添加位置参考示例代码，注意不要随意修改初始化代码位置。**SDK不支持在小程序中任意生命周期中进行初始化。**

### Native原生

**1、加载SDK**

百度小程序原生SDK下载：[https://assets.giocdn.com/sdk/minip/saas/3.8.9/gio-baidu.js](https://assets.giocdn.com/sdk/minip/saas/3.8.9/gio-baidu.js)

> (如果您点击链接在浏览器中直接打开了文件并不是下载文件，请尝试右键点击链接，选择 `链接存储为...` 即可正常触发下载)

**2、使用`init`方法进行初始化**

注意`init`方法所处位置在App实例之前。

**示例代码**

```javascript
// app.js
import gio from './utils/gio/gio-baidu.js';

gio('init', 'your GrowingIO 项目ID', 'your AppId', {
    version: 'your miniProgram version',
    ...other settings
});

App({ ... });
```

### uni-app 框架

**1、加载SDK**

**方式一：下载本地集成**

uni-app框架SDK下载：[https://assets.giocdn.com/sdk/minip/saas/3.8.9/gio-uniapp.js](https://assets.giocdn.com/sdk/minip/saas/3.8.9/gio-uniapp.js)

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

Taro框架SDK下载：[https://assets.giocdn.com/sdk/minip/saas/3.8.9/gio-taro.js](https://assets.giocdn.com/sdk/minip/saas/3.8.9/gio-taro.js)

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

Chameleon框架SDK下载：[https://assets.giocdn.com/sdk/minip/saas/3.8.9/gio-chameleon.js](https://assets.giocdn.com/sdk/minip/saas/3.8.9/gio-chameleon.js)

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

## 添加白名单

要正常采集百度小程序的数据并发送给 GrowingIO，需要事先设置一个通讯域名，允许跟 GrowingIO API 服务器进行网络通信。具体步骤如下：

1. 登陆[百度小程序后台](https://smartprogram.baidu.com/developer/index.html)，进入设置。
2. 打开开发设置，到服务器域名配置部分。
3. 在 **request 合法域名**中添加：https://wxapi.growingio.com

## 数据校验

GrowingIO为您提供多种验证SDK是否正常采集数据的方式：

方式一：[小程序&内嵌页Debugger](../../../../debugging/minpdebugger.md)

方式二：在SDK中设置了Debug模式后，在开发者工具中查看数据采集日志。
