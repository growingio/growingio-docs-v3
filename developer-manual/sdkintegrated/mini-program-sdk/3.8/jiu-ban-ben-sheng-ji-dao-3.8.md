# 旧版本升级到3.8

本文讲介绍如何从旧版本的SDK无缝升级到3.8版本。

**在升级之前，请充分阅读3.8版本的文档内容后再进行升级操作**[**​**](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/upgrade#%E5%9C%A8%E5%8D%87%E7%BA%A7%E4%B9%8B%E5%89%8D%E8%AF%B7%E5%85%85%E5%88%86%E9%98%85%E8%AF%BB38%E7%89%88%E6%9C%AC%E7%9A%84%E6%96%87%E6%A1%A3%E5%86%85%E5%AE%B9%E5%90%8E%E5%86%8D%E8%BF%9B%E8%A1%8C%E5%8D%87%E7%BA%A7%E6%93%8D%E4%BD%9C)

#### 初始化[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/upgrade#%E5%88%9D%E5%A7%8B%E5%8C%96) <a href="#chu-shi-hua" id="chu-shi-hua"></a>

1、下载最新版对应框架的SDK并替换，请参考集成文档选择正确的开发方式下载。

2、找到初始化代码，修改引用方式。如果您想保留原有 require 的引用方式跳过本步骤即可。

```javascript
const  = require('./utils/gio/sdk.js').default;
//          修改为 ↓↓↓
import gio from './utils/gio/sdk.js';
```

3、检查初始化方式，如果使用 `setConfig` 方法初始化，请参考集成文档重新集成；如果使用 `init` 方法进行初始化则跳过此步骤。

4、检查配置项，移除`usePlugin`、`enableEventStore`、`getLocation`（含autoGet和type）配置，如果没有则跳过此步骤。

5、检查配置项，如果您是`uni-app vue2`、`taro3 vue2`、`WePY`开发的小程序，请移除 **`vue`** 配置，并参考集成文档添加对应的实例参数。如果不是则跳过此步骤。例：

```javascript
gio('init', '您的 GrowingIO 项目ID', 'your AppId', {
    version: 'your miniProgram version',
    // vue: Vue,  移除此配置
    uniVue: Vue, // 新增此配置
    ...other settings
});
```

#### 页面[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/upgrade#%E9%A1%B5%E9%9D%A2) <a href="#ye-mian" id="ye-mian"></a>

1）如果您是阿里(支付宝)小程序，请恢复对`App({})`、`Page({})`和`Component({})`的原生写法。如果不是则跳过此步骤。

```javascript
$global.GioApp({ ... });
// 修改回原始写法 ↓↓↓
App({ ... });

$global.GioPage({ ... });
// 修改回原始写法 ↓↓↓
Page({ ... });

$global.GioComponent({ ... });
// 修改回原始写法 ↓↓↓
Component({ ... });
```

2）检查页面中是否调用`getLocation`方法，存在则参考文档修改为[`setLocation`](shu-ju-cai-ji-api.md#she-zhi-wei-zhi-xin-xi)。如果没有则跳过此步骤。

#### 其他[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/upgrade#%E5%85%B6%E4%BB%96) <a href="#qi-ta" id="qi-ta"></a>

如果您调用了`gioGlobal`中的内容，请尝试从`global（阿里(支付宝)小程序是 $global）`中重新获取，`gioGlobal`已经被弃用。

#### 建议性修改[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/upgrade#%E5%BB%BA%E8%AE%AE%E6%80%A7%E4%BF%AE%E6%94%B9) <a href="#jian-yi-xing-xiu-gai" id="jian-yi-xing-xiu-gai"></a>

1、如果您使用了旧版动态配置接口的调用方式，建议按新版使用方式进行修改。

2、在<3.8的旧版本中，可能您的 **`gio`** 方法是需要您通过手动挂载在例如`globalData`、`vue`、`gioGlobal`此类全局对象后再取出。从3.8的版本开始，您可以直接在页面中从 **`global（阿里(支付宝)是 $global）`**对象中取出，从而免去了繁杂的存取值流程。例：

```
const { gio } = global;

Page({ ... });
```
