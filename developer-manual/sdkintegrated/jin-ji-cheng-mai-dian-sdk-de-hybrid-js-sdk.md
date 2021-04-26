---
description: 仅集成埋点SDK，没有集成无埋点时使用，需手动集成，采集App内嵌H5的埋点用户行为数据。
---

# 仅集成埋点SDK的Hybrid JS SDK

## 简介 <a id="jian-jie"></a>

仅集成原生埋点SDK，没有集成无埋点时使用。 埋点SDK需更新到最新版本

Hybrid JS SDK 负责采集用户在 App 中内嵌 H5 页面中的埋点用户行为数据。

## 1. 添加跟踪代码 <a id="1-tian-jia-gen-zong-dai-ma"></a>

###  1. H5页面添加代码 <a id="1-h-5-ye-mian-tian-jia-dai-ma"></a>

将以下JS代码复制到H5页面的 **&lt;head&gt;** 和 **&lt;/head&gt;** 标签之间即可。安装成功后，除 localhost 和 IP 地址外，网址下的埋点行为数据在app内都将会被收集通过移动端上报，移动端需要去设置bridge，[iOS 设置bridgeForWKWebView](https://docs.growingio.com/v3/developer-manual/sdkintegrated/ios-sdk/ios-sdk-api/sdk-other) ，[安卓设置bridgeForWebView或bridgeForX5WebView](https://docs.growingio.com/v3/developer-manual/sdkintegrated/android-sdk/android-sdk-api/run-api) 

{% hint style="info" %}
移动端需要去设置bridge，[iOS 设置bridgeForWKWebView](https://docs.growingio.com/v3/developer-manual/sdkintegrated/ios-sdk/ios-sdk-api/sdk-other) ，[安卓设置bridgeForWebView或bridgeForX5WebView](https://docs.growingio.com/v3/developer-manual/sdkintegrated/android-sdk/android-sdk-api/run-api) 
{% endhint %}

```javascript
<script>
  !function (e, t, n, g, i) {
    e[i] = e[i] || function () { (e[i].q = e[i].q || []).push(arguments) }, n = t.createElement(
      'script'), tag = t.getElementsByTagName('script')[0], n.async = 1, n.src = ('https:' === document.location.protocol
      ? 'https://'
      : 'http://') + g, tag.parentNode.insertBefore(n, tag)
  }(window, document, 'script', 'assets.giocdn.com/sdk/hybrid/2.0/gio_hybrid_track.js', 'gio')
  gio('init', 'fakeAccountID', { hashtag: false, debug: false, autotrack: false })
  gio('send')
</script>

```



#### 高级配置

| 字段 | 类型 | 说明 |
| :--- | :--- | :--- |
| debug | boolean | 是否开启调试模式，输出日志（仅对hybrid有效） |
| hashtag | boolean | 是否开启hash模式路由处理 |
| autotrack | boolean | 是否集成无埋点sdk |

1. 关于`autotrack`字段

该字段和hybrid无埋点sdk是否接入无关系，当该字段为`true`时，无埋点js sdk将被接入

2.hybrid埋点sdk接入时机

仅在当前app中只接入了埋点sdk时才会接入，若同时集成了无埋点sdk则不会被接入

3.hybrid数据转发条件

仅在hybrid sdk中的ai和app中的ai一致时，数据才会转发到app



### 1. 设置自定义事件和事件级变量（track） <a id="1-she-zhi-zi-ding-yi-shi-jian-he-shi-jian-ji-bian-liang-track"></a>

在添加所需要发送的事件代码之前，需要在打点管理用户界面配置事件以及事件级变量。

| 参数名称 | 参数类型 | 是否必须 | 说明 |
| :--- | :--- | :--- | :--- |
| eventId | String | 是 | 事件标识符 |
| eventLevelVariables | JSON Object | 否 | 包含事件级变量的JSON对象，暨事件发生时所伴随的维度信息。 |

```javascript
// track API原型
gio('track', eventId, eventLevelVariables);
// track API调用示例一
gio('track', 'registerSuccess');
// track API调用示例二
gio('track', 'registerSuccess', {'gender':'male', 'age':21});
```

### 2. 设置转化变量（evar.set） <a id="3-she-zhi-zhuan-hua-bian-liang-evarset"></a>

发送一个转化信息用于高级归因分析，在添加代码之前必须在打点管理界面上声明转化变量。

| 参数名称 | 参数类型 | 是否必须 | 说明 |
| :--- | :--- | :--- | :--- |
| key | String | 否 | 转化变量的标识符 |
| Value | String | 否 | 转化变量的值 |
| conversionVariables | JSON Object | 否 | 包含转化变量的JSON对象 |

```javascript
// evar.set API原型
gio('evar.set', key, value);gio('evar.set', conversionVariables);
// evar.set API调用示例一
gio('evar.set', 'campaignId'，'1234567890');
// evar.set API调用示例二
gio('evar.set', {'campaignId': '1234567890', 'campaignOwner':'lisi'});
```



### 3. 设置访问用户变量 <a id="4-she-zhi-yong-hu-ji-bian-liang-peopleset"></a>

| 参数名称 | 参数类型 | 是否必须 | 说明 |
| :--- | :--- | :--- | :--- |
| key | String | 否 | 用户变量的标识符 |
| value | String | 否 | 用户变量的值 |
| customerVariables | JSON Object | 否 | 包含用户变量的JSON对象 |

```javascript
// visitor.set API原型
gio('visitor.set', key, value);gio('visitor.set', customerVariables);
// people.set API调用示例一
gio('visitor.set', 'gender', 'male');
//people.set API调用示例二
gio('visitor.set', {'gender':'male', 'age':'25'});
```



### 4. 设置登录用户变量（people.set） <a id="4-she-zhi-yong-hu-ji-bian-liang-peopleset"></a>

发送用户信息用于用户信息相关分析，在添加代码之前必须在打点管理界面上声明转化变量。

| 参数名称 | 参数类型 | 是否必须 | 说明 |
| :--- | :--- | :--- | :--- |
| key | String | 否 | 用户变量的标识符 |
| value | String | 否 | 用户变量的值 |
| customerVariables | JSON Object | 否 | 包含用户变量的JSON对象 |

```javascript
// people.set API原型
gio('people.set', key, value);gio('people.set', customerVariables);
// people.set API调用示例一
gio('people.set', 'gender', 'male');
//people.set API调用示例二
gio('people.set', {'gender':'male', 'age':'25'});
```

### 5. 设置登录用户ID

```javascript
gio('setUserId', 'zhangsan'); 
```

### 6. 清除登录用户ID

```javascript
gio('clearUserId');
```

