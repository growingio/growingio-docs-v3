# API Cloud埋点SDK

{% hint style="info" %}
GitHub Demo： [https://github.com/growingio/APICloud-growingio/tree/master/android/app](https://github.com/growingio/APICloud-growingio/tree/master/android/app%20%20)

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

* iOS模块包：[下载](https://github.com/growingio/APICloud-growingio/blob/master/iOS/iOS/GrowingIO_iOS.zip)​
* Android模块包：[下载](https://github.com/growingio/APICloud-growingio/blob/master/android/GrowingIO.zip)

在API Cloud的开发控制台上选择应用，然后在界面右侧选择 端开发 &gt; 模块。

在应用的模块配置下选择**自定义模块**页签下上传对用模块。

{% hint style="success" %}
* 模块名称需要和zip包名称一致。
* 在自动定义模块中上传了压缩包，保存成功后。一定要点击添加模块后面的“+”，否则不是真正添加成功。添加成功后，去已添加模块中能看到刚刚添加的模块。
{% endhint %}

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28219%29.png)

## 3. Android的额外操作

Android云编译Loader为AppLoader， 使用自定义模块时需要编译Android自定义loader, 否则会出现模块未绑定错误, 另外需要注意的是在使用自定义loader时 请勾选 **使用升级环境编译**选项。

具体步骤如下：

1. 在API Cloud的开发控制台上选择应用，然后在界面右侧选择 端开发 &gt; 模块。

在自定义loader页签下勾选**使用升级环境编译**。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28200%29.png)

1. 云编译时，请勾选**使用升级环境编译。**

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2879%29.png)

## 4. 插件API

### 初始化

```javascript
gio.init();
```

```text
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

| 参数名 | 类型 | 是否必填 | 参数描述 |
| :--- | :--- | :--- | :--- |
| location | object | 是 | 经纬度 |

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
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">event</th>
      <th style="text-align:left">object</th>
      <th style="text-align:left">&#x662F;</th>
      <th style="text-align:left">
        <p>key:eventId(string&#x7C7B;&#x578B;,&#x5FC5;&#x8981;key) value:(string&#x7C7B;&#x578B;)
          &#xFF0C;&#x4E8B;&#x4EF6;&#x6807;&#x8BC6;&#x7B26;&#x3002;</p>
        <p>eventID &#x53C2;&#x6570;&#x9650;&#x5236;&#xFF1A;&#x975E;&#x7A7A;&#xFF0C;&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#xFF1B;SDK
          2.4.0&#x4EE5;&#x4E0B;&#x7248;&#x672C;&#x4E0D;&#x652F;&#x6301;&#x4E2D;&#x6587;&#xFF0C;&#x4EC5;&#x652F;&#x6301;0~9&#x3001;a~z&#x4EE5;&#x53CA;&#x4E0B;&#x5212;&#x7EBF;&#xFF0C;&#x5E76;&#x4E14;&#x4E0D;&#x80FD;&#x4EE5;&#x6570;&#x5B57;&#x5F00;&#x5934;&#x3002;</p>
        <p>key:eventLevelVariable(string&#x7C7B;&#x578B;,&#x975E;&#x5FC5;&#x8981;key)
          value:(object&#x7C7B;&#x578B;) &#x3002;</p>
        <p>&#x4E8B;&#x4EF6;&#x53D1;&#x751F;&#x65F6;&#x6240;&#x4F34;&#x968F;&#x7684;&#x7EF4;&#x5EA6;&#x4FE1;&#x606F;&#x3002;</p>
        <p>&#x9650;&#x5236;&#xFF1A;&#x975E;&#x7A7A;&#xFF0C;&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;100&#xFF08;eventLevelVariable.length()&lt;=100&#xFF09;&#xFF1B;eventLevelVariable&#x5185;&#x90E8;&#x4E0D;&#x5141;&#x8BB8;&#x542B;&#x6709;JSONObject&#x6216;&#x8005;JSONArray&#xFF1B;</p>
        <p>key&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#xFF0C;value&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;1000&#xFF0C;&#x503C;&#x4E0D;&#x80FD;&#x4E3A;&#x7A7A;&#x5B57;&#x7B26;&#x4E32;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&#x201C;&#x201D;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">callback</th>
      <th style="text-align:left">&#x51FD;&#x6570;</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>callback {function (ret)}&#xFF1A;&#x6267;&#x884C;&#x5B8C;&#x8BFB;&#x53D6;&#x64CD;&#x4F5C;&#x540E;&#x7684;&#x56DE;&#x8C03;&#x51FD;&#x6570;&#x3002;</p>
        <p>ret &#x4E3A; callback &#x51FD;&#x6570;&#x7684;&#x53C2;&#x6570;&#xFF0C;&#x6709;&#x4E24;&#x4E2A;&#x5C5E;&#x6027;:</p>
        <p>status:&#x7ED3;&#x679C;2&#x79CD; true, false &#x90FD;&#x4E3A;&#x5E03;&#x5C14;&#x7C7B;&#x578B;</p>
        <p>msg:&#x7ED3;&#x679C;string&#x7C7B;&#x578B;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>```javascript
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
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">conversionVariables</th>
      <th style="text-align:left">object</th>
      <th style="text-align:left">&#x662F;</th>
      <th style="text-align:left">
        <p>&#x8F6C;&#x5316;&#x53D8;&#x91CF;&#x7528;&#x4E8E;&#x9AD8;&#x7EA7;&#x5F52;&#x56E0;&#x5206;&#x6790;</p>
        <p>&#x9650;&#x5236;&#xFF1A;&#x975E;&#x7A7A;&#xFF0C;&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;100&#xFF08;<code>conversionVariables.length()&lt;=100</code>&#xFF09;&#xFF1B;</p>
        <p><code>conversionVariables</code> &#x5185;&#x90E8;&#x4E0D;&#x5141;&#x8BB8;&#x542B;&#x6709;<code>JSONObject</code>&#x6216;&#x8005;<code>JSONArray</code>&#xFF1B;</p>
        <p><code>key</code> &#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#xFF0C;<code>value</code>&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x7B49;&#x4E8E;1000&#xFF0C;&#x503C;&#x4E0D;&#x80FD;&#x4E3A;&#x7A7A;&#x4E32;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&quot;&quot;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">callback</th>
      <th style="text-align:left">&#x51FD;&#x6570;</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>callback {function (ret)}&#xFF1A;&#x6267;&#x884C;&#x5B8C;&#x8BFB;&#x53D6;&#x64CD;&#x4F5C;&#x540E;&#x7684;&#x56DE;&#x8C03;&#x51FD;&#x6570;&#x3002;</p>
        <p>ret &#x4E3A;callback &#x51FD;&#x6570;&#x7684;&#x53C2;&#x6570;&#xFF0C;&#x6709;&#x4E24;&#x4E2A;&#x5C5E;&#x6027;:</p>
        <p>status:&#x7ED3;&#x679C;2&#x79CD;true, false &#x90FD;&#x4E3A;&#x5E03;&#x5C14;&#x7C7B;&#x578B;</p>
        <p>msg:&#x7ED3;&#x679C;string&#x7C7B;&#x578B;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>```javascript
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
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">peopleVariables</th>
      <th style="text-align:left">object</th>
      <th style="text-align:left">&#x662F;</th>
      <th style="text-align:left">
        <p>&#x7528;&#x6237;&#x53D8;&#x91CF;&#x7528;&#x4E8E;&#x7528;&#x6237;&#x4FE1;&#x606F;&#x76F8;&#x5173;&#x7684;&#x5206;&#x6790;&#x3002;</p>
        <p>&#x9650;&#x5236;&#xFF1A;&#x975E;&#x7A7A;&#xFF0C;&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;100&#xFF08;<code>peopleVariables.length()&lt;=100</code>&#xFF09;&#xFF1B;</p>
        <p><code>peopleVariables</code> &#x5185;&#x90E8;&#x4E0D;&#x5141;&#x8BB8;&#x542B;&#x6709;<code>JSONObject</code>&#x6216;&#x8005;<code>JSONArray</code>&#xFF1B;</p>
        <p><code>key</code>&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#xFF0C;<code>value</code>&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x7B49;&#x4E8E;1000&#xFF0C;&#x503C;&#x4E0D;&#x80FD;&#x4E3A;&#x7A7A;&#x4E32;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&quot;&quot;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">callback</th>
      <th style="text-align:left">&#x51FD;&#x6570;</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>callback {function (ret)}&#xFF1A;&#x6267;&#x884C;&#x5B8C;&#x8BFB;&#x53D6;&#x64CD;&#x4F5C;&#x540E;&#x7684;&#x56DE;&#x8C03;&#x51FD;&#x6570;&#x3002;</p>
        <p>ret &#x4E3A;callback &#x51FD;&#x6570;&#x7684;&#x53C2;&#x6570;&#xFF0C;&#x6709;&#x4E24;&#x4E2A;&#x5C5E;&#x6027;:</p>
        <p>status:&#x7ED3;&#x679C;2&#x79CD;true, false &#x90FD;&#x4E3A;&#x5E03;&#x5C14;&#x7C7B;&#x578B;</p>
        <p>msg:&#x7ED3;&#x679C;string&#x7C7B;&#x578B;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>```javascript
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
| :--- | :--- | :--- | :--- |


| userIdObject | object | 是 | key:userId\(string类型,必要key\) value:\(string或者number类型\) |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">callback</th>
      <th style="text-align:left">&#x51FD;&#x6570;</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>callback {function (ret)}&#xFF1A;&#x6267;&#x884C;&#x5B8C;&#x8BFB;&#x53D6;&#x64CD;&#x4F5C;&#x540E;&#x7684;&#x56DE;&#x8C03;&#x51FD;&#x6570;&#x3002;</p>
        <p>ret &#x4E3A; callback &#x51FD;&#x6570;&#x7684;&#x53C2;&#x6570;&#xFF0C;&#x6709;&#x4E24;&#x4E2A;&#x5C5E;&#x6027;:</p>
        <p>status:&#x7ED3;&#x679C;2&#x79CD;true, false &#x90FD;&#x4E3A;&#x5E03;&#x5C14;&#x7C7B;&#x578B;</p>
        <p>msg:&#x7ED3;&#x679C;string&#x7C7B;&#x578B;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>```javascript
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
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">callback</th>
      <th style="text-align:left">&#x51FD;&#x6570;</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>callback {function (ret)}&#xFF1A;&#x6267;&#x884C;&#x5B8C;&#x8BFB;&#x53D6;&#x64CD;&#x4F5C;&#x540E;&#x7684;&#x56DE;&#x8C03;&#x51FD;&#x6570;&#x3002;</p>
        <p>ret &#x4E3A;callback &#x51FD;&#x6570;&#x7684;&#x53C2;&#x6570;&#xFF0C;&#x6709;&#x4E24;&#x4E2A;&#x5C5E;&#x6027;:</p>
        <p>status:&#x7ED3;&#x679C;2&#x79CD;true, false &#x90FD;&#x4E3A;&#x5E03;&#x5C14;&#x7C7B;&#x578B;</p>
        <p>msg:&#x7ED3;&#x679C;string&#x7C7B;&#x578B;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>```javascript
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
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">visitorVar</th>
      <th style="text-align:left">Object</th>
      <th style="text-align:left">&#x662F;</th>
      <th style="text-align:left">
        <p>&#x4E0D;&#x53EF;&#x4F7F;&#x7528;&#x5D4C;&#x5957;&#x7684;<code>JSONObject</code>&#x5BF9;&#x8C61;&#xFF0C;&#x5373;&#x4E3A;JSONObject&#x4E2D;&#x4E0D;&#x53EF;&#x4EE5;&#x653E;&#x5165;<code>JSONObject</code>&#x6216;&#x8005;<code>JSONArray</code>&#xFF1B;</p>
        <p>key &#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#xFF0C;value&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x7B49;&#x4E8E;1000&#xFF0C;&#x503C;&#x4E0D;&#x80FD;&#x4E3A;&#x7A7A;&#x4E32;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&quot;&quot;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>```javascript
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

