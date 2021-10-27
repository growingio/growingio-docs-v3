# API Cloud埋点SDK

{% hint style="info" %}
GitHub Demo： [https://github.com/growingio/APICloud-growingio/tree/master/android/app](https://github.com/growingio/APICloud-growingio/tree/master/android/app)

* API Cloud 全版本支持
* App适配最低系统版本：iOS 8及以上、Android 4.2-10
* 不支持使用 Mobile Debugger ，请在配置文件中设置 debug 模式后查看日志
{% endhint %}

## 1. 配置config.xml文件

名称：GrowingIO

必要参数：accountId、URL Scheme

可选参数：trackerHost、reportHost、dataHost、gtaHost、wsHost、zone、channel、debug。

```markup
<feature name="GrowingIO">
<param name="android_accountId" value="xxxxx"/>
<param name="ios_accountId" value="xxxx"/>
<param name="ios_urlScheme" value="xx ios项目的urlScheme  xx"/>
<param name="android_urlScheme" value="xx android项目的urlScheme  xx"/>
<param name="trackerHost" value="xxxxx"/>
<param name="reportHost" value="xxxxx"/>
<param name="dataHost" value="xxxxx"/>
<param name="gtaHost" value="xxxxx"/>
<param name="wsHost" value="xxxxx"/>
<param name="zone" value="xxxxx"/>
<param name="channel" value="xxxx"/>
<param name="debug" value="true or false"/>
</feature>
<preference name="urlScheme" value=" xx ios项目的urlScheme  x " />
<preference name="urlScheme" value=" xx android项目的urlScheme  x " />
```

{% hint style="info" %}
API Cloud的debug模式只支持静态配置，不支持动态配置。
{% endhint %}

## 2. 添加模块

模块包下载：

* iOS模块包：[下载](https://github.com/growingio/APICloud-growingio/blob/master/iOS/iOS/GrowingIO\_iOS.zip)​
* Android模块包：[下载](https://github.com/growingio/APICloud-growingio/blob/master/android/GrowingIO.zip)

在API Cloud的开发控制台上选择应用，然后在界面右侧选择 端开发 > 模块。

在应用的模块配置下选择**自定义模块**页签下上传对用模块。

{% hint style="success" %}
* 模块名称需要和zip包名称一致。
* 在自动定义模块中上传了压缩包，保存成功后。一定要点击添加模块后面的“+”，否则不是真正添加成功。添加成功后，去已添加模块中能看到刚刚添加的模块。
{% endhint %}

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20\(219\).png)

## 3. Android的额外操作

Android云编译Loader为AppLoader， 使用自定义模块时需要编译Android自定义loader, 否则会出现模块未绑定错误, 另外需要注意的是在使用自定义loader时 请勾选 **使用升级环境编译**选项。

具体步骤如下：

1. 在API Cloud的开发控制台上选择应用，然后在界面右侧选择 端开发 > 模块。

在自定义loader页签下勾选**使用升级环境编译**。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20\(200\).png)

1. 云编译时，请勾选**使用升级环境编译。**

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20\(79\).png)

## 4. 插件API

### 初始化

```javascript
gio.init();
```

```
   **此接口为Android初始化， 在require后调用，iOS不需要，iOS已自动初始化**建议在require GrowingIO时调用此接口
```

```javascript
 vargio =null;
 apiready=function(){
     gio =api.require('GrowingIO');
     gio.init();
 }
```

### 设置地理位置

```javascript
gio.setGeoLocation(location);
```

| 参数名      | 类型     | 是否必填 | 参数描述 |
| -------- | ------ | ---- | ---- |
| location | object | 是    | 经纬度  |

调用示例：

```javascript
var gio = api.require('GrowingIO');  //引用模块
var param = {"longitude": longitude, "latitude": latitude}
gio.setGeoLocation(param);
```

### 采集自定义事件

发送一个自定义事件。在添加所需要发送的事件代码之前，需要在打点管理用户界面配置事件以及事件级变量。

```javascript
gio.track(event, callback);
```

| 参数名 | 类型 | 是否必填 | 参数描述 |
| --- | -- | ---- | ---- |

| event | object | 是 | <p>key:eventId(string类型,必要key) value:(string类型) ，事件标识符。</p><p>eventID 参数限制：非空，长度限制小于等于50；SDK 2.4.0以下版本不支持中文，仅支持0~9、a~z以及下划线，并且不能以数字开头。</p><p>key:eventLevelVariable(string类型,非必要key) value:(object类型) 。</p><p>事件发生时所伴随的维度信息。</p><p>限制：非空，长度限制小于等于100（eventLevelVariable.length()&#x3C;=100）；eventLevelVariable内部不允许含有JSONObject或者JSONArray；</p><p>key长度限制小于等于50，value长度限制小于等于1000，值不能为空字符串，也就是“”。</p> |
| ----- | ------ | - | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| callback | 函数 | 否 | <p>callback {function (ret)}：执行完读取操作后的回调函数。</p><p>ret 为 callback 函数的参数，有两个属性:</p><p>status:结果2种 true, false 都为布尔类型</p><p>msg:结果string类型</p> |
| -------- | -- | - | ------------------------------------------------------------------------------------------------------------------------------------------- |

```javascript
var gio = api.require('GrowingIO');  //引用模块
gio.track({
        eventId: 'GIOKey'
    },function(ret, err){
        //回调函数事件处理
});
```

### 设置转化变量

发送一个转化信息用于高级归因分析，在添加代码之前必须在打点管理界面上声明转化变量。

```javascript
gio.setEvar(conversionVariables,callback);
```

| 参数名 | 类型 | 是否必填 | 参数描述 |
| --- | -- | ---- | ---- |

| conversionVariables | object | 是 | <p>转化变量用于高级归因分析</p><p>限制：非空，长度限制小于等于100（<code>conversionVariables.length()&#x3C;=100</code>）；</p><p><code>conversionVariables</code> 内部不允许含有<code>JSONObject</code>或者<code>JSONArray</code>；</p><p><code>key</code> 长度限制小于等于50，<code>value</code>长度限制小等于1000，值不能为空串，也就是""。</p> |
| ------------------- | ------ | - | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

| callback | 函数 | 否 | <p>callback {function (ret)}：执行完读取操作后的回调函数。</p><p>ret 为callback 函数的参数，有两个属性:</p><p>status:结果2种true, false 都为布尔类型</p><p>msg:结果string类型</p> |
| -------- | -- | - | ----------------------------------------------------------------------------------------------------------------------------------------- |

```javascript
var gio = api.require('GrowingIO');  //引用模块
gio.setEvar({
           "ekey":"evalue","Date":"2018-07-02"
      },function(ret, err){
           //回调函数事件处理
});
```

### 设置登录用户变量

发送用户信息用于用户信息相关分析，在添加代码之前必须在打点管理界面上声明用户变量。

```javascript
gio.setPeopleVariable(peopleVariables,callback);
```

| 参数名 | 类型 | 是否必填 | 参数描述 |
| --- | -- | ---- | ---- |

| peopleVariables | object | 是 | <p>用户变量用于用户信息相关的分析。</p><p>限制：非空，长度限制小于等于100（<code>peopleVariables.length()&#x3C;=100</code>）；</p><p><code>peopleVariables</code> 内部不允许含有<code>JSONObject</code>或者<code>JSONArray</code>；</p><p><code>key</code>长度限制小于等于50，<code>value</code>长度限制小等于1000，值不能为空串，也就是""。</p> |
| --------------- | ------ | - | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| callback | 函数 | 否 | <p>callback {function (ret)}：执行完读取操作后的回调函数。</p><p>ret 为callback 函数的参数，有两个属性:</p><p>status:结果2种true, false 都为布尔类型</p><p>msg:结果string类型</p> |
| -------- | -- | - | ----------------------------------------------------------------------------------------------------------------------------------------- |

```javascript
var gio = api.require('GrowingIO');  //引用模块
gio.setPeopleVariable({
           "ekey":"evalue","Date":"2018-07-02"
      },function(ret, err){
            //回调函数事件处理
  });
```

### 设置登录用户ID

当用户登录之后调用setUserId API，设置登录用户ID。

```javascript
gio.setUserId(userIdObject,callback);
```

| 参数名 | 类型 | 是否必填 | 参数描述 |
| --- | -- | ---- | ---- |

| userIdObject | object | 是 | key:userId(string类型,必要key) value:(string或者number类型) |
| ------------ | ------ | - | --------------------------------------------------- |

| callback | 函数 | 否 | <p>callback {function (ret)}：执行完读取操作后的回调函数。</p><p>ret 为 callback 函数的参数，有两个属性:</p><p>status:结果2种true, false 都为布尔类型</p><p>msg:结果string类型</p> |
| -------- | -- | - | ------------------------------------------------------------------------------------------------------------------------------------------ |

```javascript
var gio = api.require('GrowingIO');  //引用模块
  gio.setUserId({
             "userId":"GIO"
        },function(ret, err){
             //回调函数事件处理
   });
```

### 清除登录用户ID

```javascript
gio.clearUserId(callback);
```

| 参数名 | 类型 | 是否必填 | 参数描述 |
| --- | -- | ---- | ---- |

| callback | 函数 | 否 | <p>callback {function (ret)}：执行完读取操作后的回调函数。</p><p>ret 为callback 函数的参数，有两个属性:</p><p>status:结果2种true, false 都为布尔类型</p><p>msg:结果string类型</p> |
| -------- | -- | - | ----------------------------------------------------------------------------------------------------------------------------------------- |

```javascript
var gio = api.require('GrowingIO');  //引用模块
gio.clearUserId(function(ret, err){
             //回调函数事件处理
});
```

### 设置访问用户变量

当用户未登录时，定义用户属性变量，也可用于A/B测试上传标签。

```javascript
gio.setVisitor(visitorVar);
```

| 参数名 | 类型 | 是否必填 | 参数描述 |
| --- | -- | ---- | ---- |

| visitorVar | Object | 是 | <p>不可使用嵌套的<code>JSONObject</code>对象，即为JSONObject中不可以放入<code>JSONObject</code>或者<code>JSONArray</code>；</p><p>key 长度限制小于等于50，value长度限制小等于1000，值不能为空串，也就是""。</p> |
| ---------- | ------ | - | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |

```javascript
var gio = api.require('GrowingIO');  //引用模块
gio.setVisitor({"gender":"male","age":21});
```

## 常见问题

### 1. 提示无法检测到URL Scheme？

（1）查看 config.xml 是否配置正确。

（2）需要同步代码到云端，云编译生效

### 2. 模拟器无法test？

只能真机测试

### 3. 此模块是否含有IDFA？

包含IDFA，GrowingIO 使用IDFA 来做来源管理激活设备的精确匹配，让您更好的衡量广告效果。

### 4. 官网Web提示未检测到SDK？

请使用正式版包来操作几次。
