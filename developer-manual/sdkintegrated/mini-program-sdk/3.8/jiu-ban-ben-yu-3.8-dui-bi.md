# 旧版本与3.8对比

本文将介绍旧版本与3.8版本的差异，方便您充分了解差异并放心的升级。文中将仅列出差异之处，共同之处将不再赘述。

### 架构调整[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/contrast#%E6%9E%B6%E6%9E%84%E8%B0%83%E6%95%B4) <a href="#jia-gou-tiao-zheng" id="jia-gou-tiao-zheng"></a>

我们将各个主模块进行了独立拆分，方法调用都是单向的，这大大降低了代码的耦合度，减少了出现缺陷的风险。

功能上，我们对各个模块进行了重新设计和完全的代码重写，以插件的形式进行拆分，进一步捋清了代码逻辑。抛弃了大量原有的冗余和过时逻辑，这对于减小SDK占用大小有很大的意义。下面是与旧版本的对比示例（均以原生开发微信小程序为例）：

> 旧版本SDK(含`埋点`+`无埋点`+`加密`功能)大小约 `58 KB`。
>
> 新版本SDK(含`埋点`+`无埋点`+`加密`功能)大小约为 `48 KB`，较旧版本节约 `10 KB`。

### 关于版本号[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/contrast#%E5%85%B3%E4%BA%8E%E7%89%88%E6%9C%AC%E5%8F%B7) <a href="#guan-yu-ban-ben-hao" id="guan-yu-ban-ben-hao"></a>

由于我们只是在架构层面进行调整，功能上和使用上与旧版本无太大变化，所以我们并没有直接进入4.0。

### 关于旧版本[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/contrast#%E5%85%B3%E4%BA%8E33%E6%97%A7%E7%89%88%E6%9C%AC) <a href="#guan-yu-33-jiu-ban-ben" id="guan-yu-33-jiu-ban-ben"></a>

旧版本我们也会继续维护，但仅限于重大问题的修复。

### 差异点[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/contrast#%E5%B7%AE%E5%BC%82%E7%82%B9) <a href="#cha-yi-dian" id="cha-yi-dian"></a>

#### 初始化[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/contrast#%E5%88%9D%E5%A7%8B%E5%8C%96) <a href="#chu-shi-hua" id="chu-shi-hua"></a>

**移除项：** `enableEventStore`、`usePlugin`、`vue`、`getLocation(含autoGet和type)` 配置项，`setConfig` 方法。

> 初始化配置项 `enableEventStore` 字段废弃；3.7.4版本起为解决没有使用运营SDK却导致存储超限问题而提供的配置项，重构后已改造此模块，因此废弃。未使用无影响，已使用直接移除即可。
>
> 初始化配置项 `usePlugin` 字段废弃；未使用无影响，已使用直接移除即可。
>
> 初始化配置项 `vue` 字段废弃；使用其他实例字段代替。
>
> 初始化方法 `setConfig` 废弃，仅支持通过 `init` 方法进行初始化；因为它容易歧义误导使用。

**新增项：** `wepy`、`uniVue`、`taroVue`、`remax` 配置项。

> 新增 `wepy`、`uniVue`、`taroVue`、`remax` 配置项字段；用于准确传入不同框架的实例。

#### 数据采集API[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/contrast#%E6%95%B0%E6%8D%AE%E9%87%87%E9%9B%86api) <a href="#shu-ju-cai-ji-api" id="shu-ju-cai-ji-api"></a>

**移除项：**  `getLocation` 方法。

> 自2022年4月18日起，微信官方修改了相关权限，获取位置信息将需要开通对应功能权限，为避免没有使用位置信息的小程序上线审核被驳回，我们废弃了`getLocation`方法。

**新增项：** `setOption`、`setLocation` 方法。

> 新增 `setOption` 方法；用于统一动态设置SDK配置项。[参考文档](chu-shi-hua-pei-zhi.md)
>
> 新增 [`setLocation`](shu-ju-cai-ji-api.md#she-zhi-wei-zhi-xin-xi) 方法；用于弥补移除了自动获取位置的功能。

### 功能点新增、优化、问题修复[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/contrast#%E5%8A%9F%E8%83%BD%E7%82%B9%E6%96%B0%E5%A2%9E%E4%BC%98%E5%8C%96%E9%97%AE%E9%A2%98%E4%BF%AE%E5%A4%8D) <a href="#gong-neng-dian-xin-zeng-you-hua-wen-ti-xiu-fu" id="gong-neng-dian-xin-zeng-you-hua-wen-ti-xiu-fu"></a>

1、新增`uni-app vue3`、`taro3 vue3`、`remax`的支持。

2、调用 `setUserId` 的API，设置或切换有效的登录用户ID时，会自动补发 VISIT 事件。

3、带有 `autoplay` 属性且值为 `true` 的原生组件（例如：swiper、video）产生的change事件会被自动忽略，如果您想采集它，请参考[无埋点采集逻辑和高级配置](wu-mai-dian-cai-ji-luo-ji-he-gao-ji-pei-zhi.md)。

4、在<3.8的旧版本中，使用taro或者uni-app框架开发的小程序在某些特定场景下可能会丢失自定义采集标记，我们在3.8版本中我们修复了它。
