---
description: 无埋点 SDK 自动注入此 SDK，无需集成。采集App内嵌H5的用户行为数据。
---

# Hybrid JS SDK

## 简介

集成[Android 无埋点SDK](android-sdk/auto-android-sdk.md)或 [iOS 无埋点SDK](ios-sdk/auto-ios-sdk.md) 后，原生无埋点SDK会自动在 WebView 加载的页面中注入 Hybrid JS SDK，不需要手动集成此 SDK。

Hybrid JS SDK 负责采集用户在 App 中内嵌 H5 页面中的用户行为数据。

{% hint style="warning" %}
如果内嵌 H5 页面只在移动端的 App 中投放，可直接使用移动端圈选查看移动端采集的数据。

如果内嵌 H5 页面不仅在移动端投放，还可在 Web 端浏览，需要另外集成 Web JS SDK 并使用 Web 圈选来查看Web端采集的数据。

如果同时存在 Web JS SDK 和 Hybrid JS SDK , 埋点调用代码只用写一遍，数据会自动发两份。
{% endhint %}

## 重要配置项 <a href="#zhong-yao-pei-zhi-xiang" id="zhong-yao-pei-zhi-xiang"></a>

### 1. 在 App 中禁用 Web JS SDK <a href="#1-zai-app-zhong-jin-yong-web-js-sdk" id="1-zai-app-zhong-jin-yong-web-js-sdk"></a>

如果 H5 页面已经集成过 Web JS SDK，但不想在 App 中进行 Web JS SDK 的采集时，请将 `window.webViewRequestSend`的值为 false。

### 2. 在 App 中禁用 Hybrid JS SDK

如果不想在 App 中进行 Hybrid JS SDK 的采集，iOS SDK 可以配置 enableAllWebViews（全局）为 NO，或对于单个 webView，配置`webView.growingAttributesDonotTrack`为 YES；Android SDK 可以配置 setTrackWebView（全局）为 false，或对于单个 webView，`GrowingIO.ignoredView(webView)`为 true。

### 3. Touch 点击事件采集 <a href="#2-touch-dian-ji-shi-jian-cai-ji" id="2-touch-dian-ji-shi-jian-cai-ji"></a>

Hybrid 支持基于 touch 事件实现的点击数据采集, 如果用户使用了类似 Zepto 等三方框架，需要采集 tap 事件时，请在初始化时配置`window.hybridEnableTouch` 的值为 true。

### 4. 埋点时机配置项 <a href="#3-mai-dian-shi-ji-pei-zhi-xiang" id="3-mai-dian-shi-ji-pei-zhi-xiang"></a>

为了不影响用户 H5 页面的加载速度，我们优先加载用户的页面再注入Hybrid JS SDK ，保证用户页面先加载。这样就引出一个问题：用户的界面在加载过程中或者加载完成后立刻调用埋点方法会出现gio未定义，因为这时候Hybrid JS SDK 可能还没有完全注入成功。

如果用户需要在hybrid界面加载过程中或者加载完成后立刻调用埋点方法，需要在该H5页面的script标签最前端添加如下代码

```javascript
(function(){
    window["gio"] = window["gio"] || function(){
        (window["gio"].q = window["gio"].q || []).push(arguments);
    }
    gio('init', 'fakeAccountID');
})()
```

## 自定义数据上传 <a href="#mai-dian-api" id="mai-dian-api"></a>

> SDK 版本支持：无埋点SDK>=2.2

{% hint style="warning" %}
在H5页面与原生应用无法进行联调的情况下，可手动在head标签中加入以下代码，上线时删除即可

\<script

src="[https://assets.giocdn.com/sdk/hybrid/2.0/gio\_hybrid.min.js](https://assets.giocdn.com/sdk/hybrid/2.0/gio\_hybrid.min.js)" >

\</script>
{% endhint %}

**原生无埋点 SDK 2.2 及以上支持。**

### 1. 设置埋点事件和事件级变量 <a href="#1-she-zhi-zi-ding-yi-shi-jian-he-shi-jian-ji-bian-liang-track" id="1-she-zhi-zi-ding-yi-shi-jian-he-shi-jian-ji-bian-liang-track"></a>

在添加所需要发送的事件代码之前，需要在打点管理用户界面配置事件以及事件级变量。

| 参数名称                | 参数类型        | 是否必须 | 说明                             |
| ------------------- | ----------- | ---- | ------------------------------ |
| eventId             | String      | 是    | 事件标识符                          |
| eventLevelVariables | JSON Object | 否    | 包含事件级变量的JSON对象，暨事件发生时所伴随的维度信息。 |

```java
// track API原型
gio('track', eventId, eventLevelVariables);
// track API调用示例一
gio('track', 'registerSuccess');
// track API调用示例二
gio('track', 'registerSuccess', {'gender':'male', 'age':21});
```

### 2. 设置页面级变量 <a href="#2-she-zhi-ye-mian-ji-bian-liang-pageset" id="2-she-zhi-ye-mian-ji-bian-liang-pageset"></a>

发送页面级别的维度信息，在添加代码之前必须在打点管理界面上声明页面级变量。

| 参数名称               | 参数类型        | 是否必须 | 说明                      |
| ------------------ | ----------- | ---- | ----------------------- |
| key                | String      | 否    | 页面级变量的标识符               |
| value              | String      | 否    | 页面级变量的值                 |
| pageLevelVariables | JSON Object | 否    | 包含页面级变量的JSON对象，暨页面级别的信息 |

```javascript
// page.set API原型
gio('page.set', key, value);gio('page.set', pageLevelVariables);
// page.set API调用示例一
gio('page.set', {'pageName': 'Home Page', 'author': 'Zhang San'});
// page.set API调用示例二
gio('page.set', 'author', 'Zhang San');
```

### 3. 设置转化变量 <a href="#3-she-zhi-zhuan-hua-bian-liang-evarset" id="3-she-zhi-zhuan-hua-bian-liang-evarset"></a>

发送一个转化信息用于高级归因分析，在添加代码之前必须在打点管理界面上声明转化变量。

| 参数名称                | 参数类型        | 是否必须 | 说明            |
| ------------------- | ----------- | ---- | ------------- |
| key                 | String      | 否    | 转化变量的标识符      |
| Value               | String      | 否    | 转化变量的值        |
| conversionVariables | JSON Object | 否    | 包含转化变量的JSON对象 |

```javascript
// evar.set API原型
gio('evar.set', key, value);gio('evar.set', conversionVariables);
// evar.set API调用示例一
gio('evar.set', 'campaignId'，'1234567890');
// evar.set API调用示例二
gio('evar.set', {'campaignId': '1234567890', 'campaignOwner':'lisi'});
```

### 4. 设置用户级变量 <a href="#4-she-zhi-yong-hu-ji-bian-liang-peopleset" id="4-she-zhi-yong-hu-ji-bian-liang-peopleset"></a>

发送用户信息用于用户信息相关分析，在添加代码之前必须在打点管理界面上声明转化变量。

| 参数名称              | 参数类型        | 是否必须 | 说明            |
| ----------------- | ----------- | ---- | ------------- |
| key               | String      | 否    | 用户变量的标识符      |
| value             | String      | 否    | 用户变量的值        |
| customerVariables | JSON Object | 否    | 包含用户变量的JSON对象 |

```javascript
// people.set API原型
gio('people.set', key, value);gio('people.set', customerVariables);
// people.set API调用示例一
gio('people.set', 'gender', 'male');
//people.set API调用示例二
gio('people.set', {'gender':'male', 'age':'25'});
```

### 5. 设置用户登录用户ID <a href="#5-she-zhi-yong-hu-idhybridsetuserid" id="5-she-zhi-yong-hu-idhybridsetuserid"></a>

设置用户id 。

| 参数名称              | 参数类型   | 是否必须 | 说明                    |
| ----------------- | ------ | ---- | --------------------- |
| customerVariables | String | 是    | 长度不可以大于1000,并且不可为Null |

```javascript
//调用示例
gio('hybridSetUserId', '1234567890');
```

### 6. 清除登录用户ID <a href="#6-qing-chu-yong-hu-idhybridclearuserid" id="6-qing-chu-yong-hu-idhybridclearuserid"></a>

```javascript
//调用示例
gio('hybridClearUserId');
```

### 7. 设置访问用户变量 <a href="#7-she-zhi-fang-wen-yong-hu-bian-liang" id="7-she-zhi-fang-wen-yong-hu-bian-liang"></a>

```javascript
//调用示例
gio('hybridSetVisitor',{'testkey': 'testValue', 'testNumKey': 2333});
```
