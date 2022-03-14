# API 2.x

## API概览

```javascript
// 初始化参数
gio('init', projectId, options); 
gio('send')
​
// 修改系统变量API
gio('config', options);
​
// 发送事件API
gio('track', eventId);
gio('track', eventId, eventLevelVariables);
​
// 发送页面级变量API
gio('page.set', key, value);
gio('page.set', pageLevelVariables);
​
// 发送转化变量API
gio('evar.set', key, value);
gio('evar.set', conversionVariables);
​
// 发送登录用户变量API
gio('people.set', key, value);
gio('people.set', customerVariables);
​
// 发送访问用户变量API
gio('visitor.set', key, value);
gio('visitor.set', visitorVariables);
​
// 设置登录用户ID
gio('setUserId', userId); 
​
// 清除登录用户ID
gio('clearUserId');
```

## 接口定义

### 1. 初始化

初始化 `init` API ，用来设置项目ID和一些常用的配置项。

```javascript
//init API原型
gio('init', projectId, options);
```

| 参数名称      | 类型          | 是否必须 | 说明     |
| --------- | ----------- | ---- | ------ |
| projectId | string      | 是    | 项目ID   |
| options   | JSON Object | 否    | 系统变量配置 |

**代码示例：**

```javascript
//init API调用示例
// imp类型(元素浏览)事件默认禁止采集,即 'imp':false
gio('init', '1234567890', {'imp':false});
```

### 2. 设置登录用户ID

当用户登录之后调用 `setUserId` API，设置登录用户 ID，用于标记登录用户。

{% hint style="success" %}
90% 以上的用户都会上传登录用户 ID，以便分析登录用户的数据情况。
{% endhint %}

```javascript
//setUserId API原型
gio('setUserId', userId);
```

| 参数名称   | 类型     | 是否必须 | 说明        |
| ------ | ------ | ---- | --------- |
| userId | string | 是    | 用户的登录用户ID |

**代码示例：**

```javascript
//setuserId API调用示例
gio('setUserId', '1234567890');
```

### 3. 清除登录用户ID

当用户退出登录之后调用 `clearUserId` API，清除已经设置的登录用户 ID。

**代码示例：**

```javascript
//clearUserId API原型和调用示例
gio('clearUserId');
```

### 4. 设置登录用户变量

当需要上报登录用户变量时，调用 `people.set` API。

发送登录用户信息用于登录用户信息相关分析，在添加代码之前必须在打点管理界面上创建登录用户变量。

```javascript
// people.set API原型
gio('people.set', key, value);
gio('people.set', customerVariables);
```

| 参数名称              | 类型          | 是否必须 | 说明              |
| ----------------- | ----------- | ---- | --------------- |
| key               | tring       | 否    | 登录用户变量的标识符      |
| value             | tring       | 否    | 登录用户变量的值        |
| customerVariables | JSON Object | 否    | 包含登录用户变量的JSON对象 |

**代码示例：**

```javascript
// people.set API调用示例一
gio('people.set', 'gender', 'male');
```

```javascript
//people.set API调用示例二
gio('people.set', {'gender':'male', 'age':'25'});
```

### 5. 设置访问用户变量

当需要上报访问用户变量时，调用 `visitor.set` API。

发送访问用户信息用于访问用户信息相关分析，在添加代码之前必须在打点管理界面上创建访问用户变量。

```javascript
// visitor.set API原型
gio('visitor.set', key, value);
gio('visitor.set', visitorVariables);
```

| 参数名称             | 类型          | 是否必须 | 说明              |
| ---------------- | ----------- | ---- | --------------- |
| key              | string      | 否    | 访问用户变量的标识符      |
| value            | string      | 否    | 访问用户变量的值        |
| visitorVariables | JSON Object | 否    | 包含访问用户变量的JSON对象 |

**代码示例：**

```javascript
// visitor.set API调用示例一
gio('visitor.set', 'gender', 'male');
```

```javascript
// visitor.set API调用示例二
gio('visitor.set', {'gender':'male', 'age':'25'});
```

### 6. 设置页面级变量

当需要上报页面级变量时，调用 `page.set` API。

发送页面级别的维度信息，用于标记当前页面，在添加代码之前必须在打点管理界面上创建页面级变量。

```javascript
// page.set API原型
gio('page.set', key, value);
gio('page.set', pageLevelVariables);
```

| 参数名称               | 类型          | 是否必须 | 说明                      |
| ------------------ | ----------- | ---- | ----------------------- |
| key                | string      | 否    | 页面级变量的标识符               |
| value              | string      | 否    | 页面级变量的值                 |
| pageLevelVariables | JSON Object | 否    | 包含页面级变量的JSON对象，即页面级别的信息 |

**代码示例：**

```javascript
// page.set API调用示例一
gio('page.set', {'pageName': 'Home Page', 'author': 'Zhang San'});
```

```javascript
// page.set API调用示例二
gio('page.set', 'author', 'Zhang San');
```

### 7. 设置转化变量

当需要上报转化变量时，调用 `evar.set` API。

发送一个转化信息用于高级归因分析，在添加代码之前必须在打点管理界面上创建转化变量。

```javascript
// evar.set API原型
gio('evar.set', key, value);
gio('evar.set', conversionVariables);
```

| 参数名称                | 类型          | 是否必须 | 说明            |
| ------------------- | ----------- | ---- | ------------- |
| key                 | String      | 否    | 转化变量的标识符      |
| value               | Strng       | 否    | 转化变量的值        |
| conversionVariables | JSON Object | 否    | 包含转化变量的JSON对象 |

**代码示例：**

```javascript
// evar.set API调用示例一
gio('evar.set', 'campaignId'，'1234567890');
```

```javascript
// evar.set API调用示例二
gio('evar.set', {'campaignId': '1234567890', 'campaignOwner':'lisi'});
```

### 8. 设置埋点事件和事件级变量

当需要上报埋点事件和事件级变量时，调用 `track` API。

发送一个埋点事件，在添加所需要发送的事件代码之前，需要在打点管理用户界面创建埋点事件以及事件级变量，并完成埋点事件和事件级变量的绑定。

```javascript
// track API原型
gio('track', eventId, eventLevelVariables);
```

| 参数名称                | 类型          | 是否必须 | 说明                                                                                                                            |
| ------------------- | ----------- | ---- | ----------------------------------------------------------------------------------------------------------------------------- |
| eventId             | tring       | 是    | 事件标识符                                                                                                                         |
| eventLevelVariables | JSON Object | 否    | 包含事件级变量的JSON对象，即事件发生时所伴随的维度信息。限制：eventLevelVariable内部不允许含有JSONObject或者JSONArray； key长度限制小<=50，value长度限制<=1000，值不能为空字符串，也就是“ ” |

**代码示例：**

```javascript
// track API调用示例一
gio('track', 'registerSuccess');
```

```javascript
// track API调用示例二
gio('track', 'registerSuccess', {'gender':'male', 'age':21});
```

### 9. 手动发送页面浏览事件

`sendPage`

在默认情况下，由于用户浏览网站的交互行为导致当前页面的 URL 产生变化时，GrowingIO 的 Web JS SDK 会发送一个 page 类型的请求。

在一些特殊的情况下，例如用户在访问单页应用（Single Page Application）类型的网站时，用户的操作会导致业务上面理解的页面产生了变化，但是当前的 URL 可能并没有改变。这时，可以调用GrowingIO提供的 `sendPage` 接口手动发送页面浏览事件。

调用将会发送出一条 page 类型的数据，GIO 服务器在收到 page 类型的数据之后，页面浏览量这个预定义指标会加 1。

**代码示例：**

```javascript
//sendPage API原型和调用示例
gio('sendPage'); // 在调用 window.gio('send') 之后调用
```

### 10. GDPR数据采集开关

全局配置, 可以放到 `send` 调用之后。设置禁止或开启数据采集

```
// enableDataCollect，默认true，开启数据采集
// 支持初始化配置
gio('init', 'your projectId', {
    // 设置 false，禁止数据采集
    enableDataCollect: false,
});
gio('send');
// 设置为 true 开启数据采集
window.gio('config',{'enableDataCollect': true});
```

{% hint style="info" %}
SDK 版本2.2.7开始，推荐使用 `enableDataCollect`
{% endhint %}

```javascript
// dataCollect，sdk版本2.2.7之前可用！
// 禁止数据采集
window.gio('config',{'dataCollect': true}); 
// 开启数据采集 (默认)
window.gio('config',{'dataCollect': false});
```

### 11. 获取访问用户ID

`getVisitUserId`

调用该方法，可以获取 SDK 自动生成用于标记访问用户的访问用户ID

```javascript
gio('getVisitUserId'); // 在调用 window.gio('send') 之后调用
```
