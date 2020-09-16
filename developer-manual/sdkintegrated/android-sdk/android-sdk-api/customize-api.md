---
description: 自定义数据常用作打通业务逻辑
---

# 自定义数据上传API

您的APP或网页在集成了 GrowingIO 的 SDK 之后，它将会自动地为您采集一系列用户行为数据，进行数据分析。除自动收集的用户行为数据（或称为无埋点数据）之外，GrowingIO 还提供了多种 API 接口，供您上传一些自定义事件和变量，下面介绍自定义事件和变量 API 使用方法，后文简称埋点事件API。

{% hint style="danger" %}
GrowingIO所有运营时API需要在主线程调用。
{% endhint %}

## API概览

```java
// 发送自定义事件 API
GrowingIO gio = GrowingIO.getInstance();
gio.track(String eventId);
gio.track(String eventId, JSONObject eventLevelVariables);
​
// 发送页面级变量 API
GrowingIO gio = GrowingIO.getInstance();
gio.setPageVariable(Activity activity, String key, String value);
gio.setPageVariable(Activity activity, String key, Number value);
gio.setPageVariable(Activity activity, String key, Boolean value);
gio.setPageVariable(Activity activity, JSONObject pageLevelVariables);
​
gio.setPageVariable(Fragment fragment, String key, String value);
gio.setPageVariable(Fragment fragment, String key, Number value);
gio.setPageVariable(Fragment fragment, String key, Boolean value);
gio.setPageVariable(Fragment fragment, JSONObject pageLevelVariables);
​
// 发送转化变量 API
GrowingIO gio = GrowingIO.getInstance();
gio.setEvar(String key, String value);
gio.setEvar(String key, Number value);
gio.setEvar(String key, Boolean value);
gio.setEvar(JSONObject conversionVariables);
​
// 发送用户变量 API
GrowingIO gio = GrowingIO.getInstance();
gio.setPeopleVariable(String key, String value);
gio.setPeopleVariable(String key, Number value);
gio.setPeopleVariable(String key, Boolean value);
gio.setPeopleVariable(JSONObject peopleVariables);
​
// 设置登录用户ID API
GrowingIO.getInstance().setUserId(String userId);
​
// 清除登录用户ID API
GrowingIO.getInstance().clearUserId();
​
// 设置访问用户变量，或者设置 A/B 测试标签
GrowingIO.getInstance().setVisitor(JSONObject visitorVariable);
```

## 接口定义

### **1.** 设置登录用户ID（setUserId）

当用户登录之后调用setUserId API，设置登录用户ID。

```java
//setuserid API原型
GrowingIO.getInstance().setUserId(String userId);
```

**参数说明**

| 参数名称 | 类型 | 是否必须 | 说明 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">userId</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x662F;</th>
      <th style="text-align:left">
        <p>&#x767B;&#x5F55;&#x7528;&#x6237;Id&#xFF0C;&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;1000&#xFF1B;</p>
        <p>&#x5982;&#x679C;&#x503C;&#x4E3A;&#x7A7A;&#x5219;&#x6E05;&#x7A7A;&#x4E86;&#x767B;&#x5F55;&#x7528;&#x6237;&#x53D8;&#x91CF;&#xFF0C;&#x4E0D;&#x5EFA;&#x8BAE;&#x8FD9;&#x4E48;&#x7528;&#xFF0C;</p>
        <p>&#x8BF7;&#x4F7F;&#x7528; clearUserId &#x6E05;&#x9664;&#x767B;&#x5F55;&#x7528;&#x6237;&#x53D8;&#x91CF;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

```java
//setUserId API调用示例
GrowingIO.getInstance().setUserId("1234567890");
```

{% hint style="info" %}
如果您的App每次用户升级版本时无需重新登录的话，为防止用户本地缓存被清除导致的无法被识别为登录用户，建议在用户每次升级App版本后初次访问时重新调用上述setUserId方法。
{% endhint %}

### 2. 清除登录用户ID（clearUserId）

当用户登出之后调用clearUserId，清除已经设置的登录用户ID。

**示例代码**

```java
//clearUserId API原型和调用示例
GrowingIO.getInstance().clearUserId();
```

### 3. 设置登录用户变量（setPeopleVariable）

发送用户信息用于用户信息相关分析，在添加代码之前必须在打点管理界面上声明用户变量。

```java
// setPeopleVariable API原型
GrowingIO gio = GrowingIO.getInstance();
gio.setPeopleVariable(String key, String value);
gio.setPeopleVariable(String key, Number value);
gio.setPeopleVariable(String key, Boolean value);
gio.setPeopleVariable(JSONObject peopleVariables);
```

| 参数名称 | 类型 | 是否必须 | 说明 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">key</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x7528;&#x6237;&#x53D8;&#x91CF;&#x7684;&#x6807;&#x8BC6;&#x7B26;&#x3002;</p>
        <p>&#x9650;&#x5236;&#xFF1A;&#x975E;&#x7A7A;&#xFF0C;&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">value</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x7528;&#x6237;&#x53D8;&#x91CF;&#x7684;&#x503C;&#x3002;</p>
        <p>&#x9650;&#x5236;&#xFF1A;&#x975E;&#x7A7A;&#xFF0C;&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;1000&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">peopleVariables</th>
      <th style="text-align:left">JSONObject</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x7528;&#x6237;&#x53D8;&#x91CF;&#x7528;&#x4E8E;&#x7528;&#x6237;&#x4FE1;&#x606F;&#x76F8;&#x5173;&#x7684;&#x5206;&#x6790;&#x3002;</p>
        <p>&#x9650;&#x5236;&#xFF1A;&#x975E;&#x7A7A;&#xFF0C;&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;100&#xFF08;<code>peopleVariables.length()&lt;=100</code>&#xFF09;&#xFF1B;</p>
        <p><code>peopleVariables</code> &#x5185;&#x90E8;&#x4E0D;&#x5141;&#x8BB8;&#x542B;&#x6709;<code>JSONObject</code>&#x6216;&#x8005;<code>JSONArray</code>&#xFF1B;</p>
        <p><code>key</code>&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#xFF0C;<code>value</code>&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x7B49;&#x4E8E;1000&#xFF0C;&#x503C;&#x4E0D;&#x80FD;&#x4E3A;&#x7A7A;&#x4E32;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&quot;&quot;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

{% hint style="info" %}
推荐您使用[Mobile Debugger](../../../debugging/mobile-debugger.md)，我们为您列举了应用场景和验证示例，请参考：[验证埋点事件](../../../debugging/verification/)&gt;[**ppl（用户变量）事件**](../../../debugging/verification/ppl.md)。
{% endhint %}

**示例代码**

```java
// setPeopleVariable API调用示例一
GrowingIO gio = GrowingIO.getInstance();
gio.setPeopleVariable("gender", "male");
```

```java
// setPeopleVariable API调用示例二
GrowingIO gio = GrowingIO.getInstance();
jsonObject.put("gender", "male");
jsonObject.put("age", "21");
gio.setPeopleVariable(jsonObject);
```

**检验数据发送日志示例：**

注意 `t` 等于`ppl`字段，表示用户变量发送成功，只需注意 `var`字段，其它字段无需仔细验证。

```java
{
    "s":"a35872af-13df-4479-90bc-25558d12328e",
    // t 为事件类型， pvar 为发送用户变量事件
    "t":"ppl",
    "tm":1532339208991,
    "d":"com.growingio.android.test",
    "cs1":"GrowingIO",
    // 用户变量
    "var":{
        "gender":"male",
        "age":"21"
    },
    "gesid":311,
    "esid":0
}
```

### **4.** 设置访问用户变量（setVisitor）

当用户未登录时，定义用户属性变量，也可用于A/B测试上传标签。

{% hint style="warning" %}
版本支持：&gt;=2.4.0
{% endhint %}

```java
//setVisitor API原型
GrowingIO.getInstance().setVisitor(JSONObject visitorVar)
```

**参数说明**

| **参数说明** | 类型 | 是否必填 | 说明 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">visitorVar</th>
      <th style="text-align:left">JSONObject</th>
      <th style="text-align:left">&#x662F;</th>
      <th style="text-align:left">
        <p>&#x4E0D;&#x53EF;&#x4F7F;&#x7528;&#x5D4C;&#x5957;&#x7684;<code>JSONObject</code>&#x5BF9;&#x8C61;&#xFF0C;&#x5373;&#x4E3A;JSONObject&#x4E2D;&#x4E0D;&#x53EF;&#x4EE5;&#x653E;&#x5165;<code>JSONObject</code>&#x6216;&#x8005;<code>JSONArray</code>&#xFF1B;</p>
        <p>key &#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#xFF0C;value&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x7B49;&#x4E8E;1000&#xFF0C;&#x503C;&#x4E0D;&#x80FD;&#x4E3A;&#x7A7A;&#x4E32;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&quot;&quot;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

```java
//setVisitor API调用示例
GrowingIO gio = GrowingIO.getInstance();
jsonObject.put("gender", "male");
jsonObject.put("age", "21");
gio.setVisitor(jsonObject);
```

**检验数据发送日志示例**

注意 `t` 等于`vstr`字段，表示访问用户变量发送成功，其它字段无需仔细验证**。**

```java
{
    "s":"d334b4a1-57eb-4bf4-b426-64c1cce5a5c0",
    // t 为事件类型， vstr 为发送访问用户变量事件
    "t":"vstr",
    "tm":1532341259134,
    "d":"com.growingio.android.test",
    "cs1":"GrowingIO",
    //访问用户变量
    "var":{
        "gender":"male",
        "age":"21"
    },
    "gesid":322,
    "esid":0
}
```

### 5. 设置页面级变量（setPageVariable）

{% hint style="info" %}
使用限制：适用于无埋点SDK。
{% endhint %}

发送页面级别的信息，在添加代码之前必须在打点管理界面上声明页面级变量。

```java
// setPageVariable API原型
GrowingIO gio = GrowingIO.getInstance();
gio.setPageVariable(Activity activity, String key, String value);
gio.setPageVariable(Activity activity, String key, Number value);
gio.setPageVariable(Activity activity, String key, Boolean value);
gio.setPageVariable(Activity activity, JSONObject pageLevelVariables);
​
gio.setPageVariable(Fragment fragment, String key, String value);
gio.setPageVariable(Fragment fragment, String key, Number value);
gio.setPageVariable(Fragment fragment, String key, Boolean value);
gio.setPageVariable(Fragment fragment, JSONObject pageLevelVariables);
​
// SDK 2.6.6 以上支持 androidx, 增加接口:
gio.setPageVariableX(Fragment fragment, String key, String value);
gio.setPageVariableX(Fragment fragment, String key, Number value);
gio.setPageVariableX(Fragment fragment, String key, Boolean value);
gio.setPageVariableX(Fragment fragment, JSONObject pageLevelVariables);
```

{% hint style="success" %}
注意确认当前页面，通过圈选方式最快定位当前页面，在当前页面埋点最稳定可靠，如果页面未确认，可能在Activity和Fragment嵌套的场景下埋点失败。如未能成功发送自定义页面变量，请参考”Android SDK集成FAQ &gt; [无埋点API使用问题](../faq/class2.md#zi-ding-yi-ye-mian-bian-liang-shi-jian-fa-song-shi-bai)“

参数选择是当前被识别的页面对象，可能是 Activity 或 Fragment，可以使用 Mobile Debugger 或debug日志确认。
{% endhint %}

| 参数名称 | 类型 | 是否必须 | 说明 |
| :--- | :--- | :--- | :--- |


| activity | Activity | 是 | 当前页面访问事件（page事件）发送的页面 |
| :--- | :--- | :--- | :--- |


| fragment | Fragment | 是 | 当前页面访问事件（page事件）发送的页面 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">key</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&#x7684;&#x6807;&#x8BC6;&#x7B26;</p>
        <p>&#x9650;&#x5236;&#xFF1A;&#x975E;&#x7A7A;&#xFF0C;&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">value</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&#x7684;&#x503C;</p>
        <p>&#x9650;&#x5236;&#xFF1A;&#x975E;&#x7A7A;&#xFF0C;&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;1000</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">pageLevelvariables</th>
      <th style="text-align:left">JSONObject</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x7684;&#x4FE1;&#x606F;</p>
        <p>&#x9650;&#x5236;&#xFF1A;&#x975E;null&#xFF0C;&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;100&#xFF08;<code>pageLevelVariable.length()&lt;=100</code>&#xFF09;&#xFF1B;</p>
        <p><code>pageLevelVariable</code> &#x5185;&#x90E8;&#x4E0D;&#x5141;&#x8BB8;&#x542B;&#x6709;<code>JSONObject</code>&#x6216;&#x8005;<code>JSONArray</code>&#xFF1B;</p>
        <p><code>key</code> &#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#xFF0C;<code>value</code>&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x7B49;&#x4E8E;1000&#xFF0C;&#x503C;&#x4E0D;&#x80FD;&#x4E3A;&#x7A7A;&#x4E32;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&quot;&quot;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

{% hint style="info" %}
**`SDK 2.4.0`** 以上能够在 Log 日志中查看对应报错，之下版本无提示信息。调用后请关注日志，查看数据发送是否成功，事件类型`t`为`pvar`。

**`SDK 2.6.7`** 将页面级变量**`pageLevelVariables`**与该页面对象绑定，设置不同的值将会合并，如果想要清空，需要传 null 。

推荐您使用[Mobile Debugger](../../../debugging/mobile-debugger.md)，我们为您列举了应用场景和验证示例，请参考：[验证埋点事件](../../../debugging/verification/)&gt;[pvar（页面级变量）事件](../../../debugging/verification/pvar.md)。
{% endhint %}

**示例代码**

```java
// setPageVariable API调用示例
GrowingIO gio = GrowingIO.getInstance();
JSONObject jsonObject = new JSONObject();
jsonObject.put("gender", "male");
jsonObject.put("age", "21");
gio.setPageVariable(myActivity, jsonObject);
```

**检验数据发送日志示例：**

注意 `t` 等于`pvar`字段，表示自定义事件发送成功，只需注意 `var`字段，其它字段无需仔细验证**。**

```java
{
    "s":"0a7e8150-c409-45d4-96ed-b5781fe652cb",
    // t 为事件类型，pvar 页面级事件
    "t":"pvar",
    "tm":1532337448255,
    "d":"com.growingio.android.test",
    "cs1":"GrowingIO",
    "p":"SetUserIdFragment1",
    "ptm":1532337448255,
    //页面级变量
    "var":{
        "gender":"male",
        "age":"21"
    },
    "gesid":292,
    "esid":0
}
```

### 6. 设置转化变量（setEvar）

发送一个转化信息用于高级归因分析，在添加代码之前必须在打点管理界面上声明转化变量。

```java
// setEvar API原型
GrowingIO gio = GrowingIO.getInstance();
gio.setEvar(String key, String value);
gio.setEvar(String key, Number value);
gio.setEvar(String key, Boolean value);
gio.setEvar(JSONObject conversionVariables);
```

参数说明

| 参数名称 | 类型 | 是否必须 | 说明 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">key</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x8F6C;&#x5316;&#x53D8;&#x91CF;&#x7684;&#x6807;&#x8BC6;&#x7B26;</p>
        <p>&#x9650;&#x5236;&#xFF1A;&#x975E;&#x7A7A;&#xFF0C;&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">value</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x8F6C;&#x5316;&#x53D8;&#x91CF;&#x7684;&#x503C;</p>
        <p>&#x9650;&#x5236;&#xFF1A;&#x975E;&#x7A7A;&#xFF0C;&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;1000</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">conversionVariables</th>
      <th style="text-align:left">JSONObject</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x8F6C;&#x5316;&#x53D8;&#x91CF;&#x7528;&#x4E8E;&#x9AD8;&#x7EA7;&#x5F52;&#x56E0;&#x5206;&#x6790;</p>
        <p>&#x9650;&#x5236;&#xFF1A;&#x975E;&#x7A7A;&#xFF0C;&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;100&#xFF08;<code>conversionVariables.length()&lt;=100</code>&#xFF09;&#xFF1B;</p>
        <p><code>conversionVariables</code> &#x5185;&#x90E8;&#x4E0D;&#x5141;&#x8BB8;&#x542B;&#x6709;<code>JSONObject</code>&#x6216;&#x8005;<code>JSONArray</code>&#xFF1B;</p>
        <p><code>key</code> &#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#xFF0C;<code>value</code>&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x7B49;&#x4E8E;1000&#xFF0C;&#x503C;&#x4E0D;&#x80FD;&#x4E3A;&#x7A7A;&#x4E32;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&quot;&quot;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

{% hint style="info" %}
推荐您使用[Mobile Debugger](../../../debugging/mobile-debugger.md)，我们为您列举了应用场景和验证示例，请参考：[验证埋点事件](../../../debugging/verification/)&gt;[evar（转化变量）事件](../../../debugging/verification/evar.md)。
{% endhint %}

```java
// setEvar API调用示例一
GrowingIO gio = GrowingIO.getInstance();
gio.setEvar("campaignId", "1234567890");
```

```java
// setEvar API调用示例二
GrowingIO gio = GrowingIO.getInstance();
JSONObject jsonObject = new JSONObject();
jsonObject.put("campaignId", "1234567890");
jsonObject.put("campaignOwner", "Li Si");
gio.setEvar(jsonObject);
```

**检验数据发送日志示例：**

注意 `t` 等于`evar`字段，表示转化事件发送成功，只需注意 `var`字段，其它字段无需仔细验证。

```java
{
    "s":"e1c48845-dd60-4cf2-b1a5-a8e529d2188d",
    // t 为事件类型， evar 为转化事件
    "t":"evar",
    "tm":1532338526083,
    "d":"com.growingio.android.test",
    "cs1":"GrowingIO",
    // 转化变量
    "var":{
        "evarTest":111,
        "campaignId":"1234567890",
        "campaignOwner":"Li Si"
    },
    "gesid":300,
    "esid":22
}
```

### 7. 设置自定义事件和事件级变量（track）

发送一个自定义事件。在添加所需要发送的事件代码之前，需要在打点管理用户界面配置事件以及事件级变量。

```java
// track API原型
GrowingIO gio = GrowingIO.getInstance();
gio.track(String eventId);
gio.track(String eventId, JSONObject eventLevelVariables);
```

| 参数名称 | 类型 | 是否必须 | 说明 |
| :--- | :--- | :--- | :--- |


| eventId | string | 是 | 事件标识符。 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">eventLevelVariable</th>
      <th style="text-align:left">JSONObject</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x4E8B;&#x4EF6;&#x53D1;&#x751F;&#x65F6;&#x6240;&#x4F34;&#x968F;&#x7684;&#x7EF4;&#x5EA6;&#x4FE1;&#x606F;&#x3002;</p>
        <p>&#x9650;&#x5236;&#xFF1A;&#x975E;&#x7A7A;&#xFF0C;&#x952E;&#x503C;&#x5BF9;&#x4E2A;&#x6570;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;100&#xFF08;eventLevelVariable.length()&lt;=100&#xFF09;&#xFF1B;eventLevelVariable&#x5185;&#x90E8;&#x4E0D;&#x5141;&#x8BB8;&#x542B;&#x6709;JSONObject&#x6216;&#x8005;JSONArray&#xFF1B;</p>
        <p>key&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#xFF0C;value&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;1000&#xFF0C;&#x503C;&#x4E0D;&#x80FD;&#x4E3A;&#x7A7A;&#x5B57;&#x7B26;&#x4E32;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&#x201C;&#x201D;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

{% hint style="info" %}
SDK 2.4.0以上能够在Log日志中查看对应报错，之下版本无提示信息。调用后请关注日志，查看数据发送是否成功，事件类型t为cstm。

推荐您使用[Mobile Debugger](../../../debugging/mobile-debugger.md)，我们为您列举了应用场景和验证示例，请参考：[验证埋点事件](../../../debugging/verification/)&gt;[cstm（事件以及关联的事件级变量）事件](../../../debugging/verification/cstm.md)。
{% endhint %}

**示例代码**

```java
// track API调用示例一
GrowingIO gio = GrowingIO.getInstance();
gio.track("registerSuccess");
```

```java
// track API调用示例二
GrowingIO gio = GrowingIO.getInstance();
JSONObject jsonObject = new JSONObject();
jsonObject.put("gender", "male");
jsonObject.put("age", "21");
gio.track("registerSuccess", jsonObject);
```

**检验数据发送日志示例**

注意 `t` 等于 `cstm` 字段，表示自定义事件发送成功，只需注意 `var`、`n` 字段，其它字段无需仔细验证**。**

```java
//展示 track 接口调用示例三日志内容
{
    "s":"31e3aa14-5241-490c-821c-a741e9bf0f87",
    // t 为事件类型， track 接口调用发送的事件类型为 cstm
    "t":"cstm",
    "tm":1532085495251,
    "d":"com.growingio.android.test",
    // n 为 eventId 参数携带的值
    "n":"loanAmount",
    // var 为 eventLevelVariable 参数携带的值
    "var":{
        "gender":"male",
        "age":"21"
    },
    "ptm":0,
    "gesid":18,
    "esid":0,
    "u":"b6247b01-a31a-3bc6-a391-4c456888c1ee"
}
```

