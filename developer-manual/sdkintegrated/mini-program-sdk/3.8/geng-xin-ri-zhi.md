# 更新日志

**SDK历史版本下载地址：**[https://github.com/growingio/growingio-sdk-miniprogram-autotracker/releases](https://github.com/growingio/growingio-sdk-miniprogram-autotracker/releases)

### V3.8.16 - 2023/09/25[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/version#v3812---20230111) <a href="#v3812---20230111" id="v3812---20230111"></a>

* 🐞 修复百度小程序无法正确获取场景值的问题。
* 🐞 修复taro2在百度小程序下无埋点失效的问题。
* 🐞 修复taro3react使用function component写法不定义生命周期不触发page事件，以及自定义方法报警告的问题。
* 🐞 修复uniapp-vue3中，使用setup写法并传参的自定义方法点击事件无法触发的问题。
* 🐞 修复曝光事件在页面销毁时可能没有及时销毁监听导致内存泄漏的问题。
* 🐞 修复小程序自定义组件中曝光事件无法触发的问题。

### V3.8.15 - 2023/09/25[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/version#v3812---20230111) <a href="#v3812---20230111" id="v3812---20230111"></a>

* 🌟 优化初始化配置项host处理逻辑。

### V3.8.14 - 2023/09/25[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/version#v3812---20230111) <a href="#v3812---20230111" id="v3812---20230111"></a>

* 🐞 修复进入小程序参数带中文时query会被encode导致平台解析错误的问题。
* 🐞 修复分享时promise不生效和自定义utm参数丢失的问题。
* 🌟 优化跳转小程序时extraData中的参数与query一起上报。
* 🌟 优化兼容微信小程序2.26.1基础库在windows上崩溃白屏问题。


### V3.8.13 - 2023/09/25[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/version#v3812---20230111) <a href="#v3812---20230111" id="v3812---20230111"></a>

* 🐞 修复分享事件可能在某些情况下丢失默认页面参数的问题。
* 🌟 优化降低本地存储的存取频率，减少对性能的影响。
* 🌟 优化事件发送失败时重发逻辑，提高重发成功率。
* 🌟 优化运营SDK初始化逻辑。
* 🎉 新增uni-appVue3、Taro3Vue3 <script setup> 写法的支持。

### V3.8.12 - 2023/02/21[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/version#v3812---20230111) <a href="#v3812---20230111" id="v3812---20230111"></a>

* 🐞 修复使用资源位组件时某些情况下报错的问题。
* 🐞 修复 Taro3react 框架中 FunctionComponent 调用 hooks 报错的问题。
* 🐞 修复 uniappVue3 框架中编译打包后点击事件丢失的问题。

### V3.8.11 - 2023/01/11[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/version#v3812---20230111) <a href="#v3812---20230111" id="v3812---20230111"></a>

* 🐞 修复平台没有运行中的运营弹窗任务时全量存储埋点导致本地存储超限的问题。
* 🐞 修复弹窗组件多个同时使用时多次弹窗的问题。
* 🎉 新增手动更新半自动埋点监控的功能（以应对动态渲染半自动埋点节点无法被监听的问题）。

### V3.8.10 - 2022/12/22 <a href="#v3811---20221222" id="v3811---20221222"></a>

* 🐞 修复在特定条件下调用getApp会导致死循环卡死的问题。
* 🐞 修复Taro2框架中支付宝小程序和百度小程序Page事件丢失的问题。
* 🐞 修复uniapp框架中支付宝小程序偶现报错或报警告的问题。
* 🌟 优化使用Component作为页面时自动适配，同时移除`comAsPage`初始化配置项。
* 🌟 优化修改gioPageTitle设置页面标题为setNavigationBarTitle生效。

### V3.8.9 - 2022/11/17 <a href="#v387---20220914" id="v387---20220914"></a>

* 🐞 修复在小程序页面型插件中集成报错的问题。
* 🐞 修复remax框架部分事件不触发的问题。
* 🐞 修复Taro3react无埋点xpath取值错误问题。
* 🐞 修复支付宝小程序（含原生及各框架）页面参数丢失的问题。
* 🐞 修复iOS下小程序分享完成后偶现事件卡住的问题。
* 🌟 优化初始化关闭数据采集或无埋点时，没有提示的问题。

### V3.8.8 - 2022/10/11 <a href="#v387---20220914" id="v387---20220914"></a>

* 🐞 修复uniapp框架中偶现点击事件丢失的问题。

### V3.8.7 - 2022/09/22 <a href="#v387---20220914" id="v387---20220914"></a>

* 🐞 修复Taro框架中阻止冒泡失效的问题。
* 🐞 修复pvar事件的页面时间在某些情况下可能取值错误的问题。
* 🌟 优化曝光监听逻辑，减少性能影响。

### V3.8.6 - 2022/09/14[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/version#v387---20220914) <a href="#v387---20220914" id="v387---20220914"></a>

* 🐞 修复`onShareTimeline`返回取值错误的问题。
* 🎉 新增微信小程序、QQ小程序`onAddToFavorites`预置埋点事件支持。

### V3.8.5 - 2022/09/06 <a href="#v383---20220802" id="v383---20220802"></a>

* 🐞 修复esid总是为1不累加的问题。
* 🐞 修复部分工具类方法极端取值时运行错误的问题。
* 🐞 修复运营弹窗条件复杂时运行报错的问题。

### V3.8.4 - 2022/08/09 <a href="#v383---20220802" id="v383---20220802"></a>

* 🐞 修复运营弹窗埋点存储过多导致存储可能超限和校验次数过多影响性能的问题。
* 🎉 新增半自动浏览事件单次发送功能。

### V3.8.3 - 2022/08/05[​](https://growingio.github.io/growingio-sdk-docs/docs/miniprogram/3.8/version#v383---20220802) <a href="#v383---20220802" id="v383---20220802"></a>

* 🐞 修复开启`forceLogin`且未调用`identify`时关闭小程序会上报匿名用户数据的问题。

### V3.8.2 - 2022/08/01[​](https://growingio.github.io/growingio-sdk-docs/docs/miniprogram/3.8/version#v383---20220802) <a href="#v383---20220802" id="v383---20220802"></a>

* 🐞 修复`onShareAppMessage、onShareTimeline`异步返回自定义参数时SDK取值错误导致分享链接错误的问题。

### V3.8.1 - 2022/07/26

* 🐞 修复设置identify补发的vstr事件字段名大小写问题。

### V3.8.0 - 2022/06/29

* 🎉 3.8.0正式版。
