---
description: 自定义数据常用作打通业务逻辑
---

# 自定义数据上传API

您的APP 集成了 Android 无埋点 SDK 之后，它将会自动地为您采集访问，页面浏览，元素点击等用户行为数据，进行数据分析。除自动收集的用户行为数据（或称为无埋点数据）之外，SDK 还提供了多种 API 接口，供您上传一些自定义数据，下面介绍自定义数据 API 使用方法，后文简称埋点 API。

{% hint style="danger" %}
GrowingIO所有运行时API需要在主线程调用。
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
// 设置登录用户ID API
GrowingIO.getInstance().setUserId(String userId);

// 发送登录用户变量 API
GrowingIO gio = GrowingIO.getInstance();
gio.setPeopleVariable(String key, String value);
gio.setPeopleVariable(String key, Number value);
gio.setPeopleVariable(String key, Boolean value);
gio.setPeopleVariable(JSONObject peopleVariables);
​
// 清除登录用户ID API
GrowingIO.getInstance().clearUserId();
​
// 设置访问用户变量，或者设置 A/B 测试标签
GrowingIO.getInstance().setVisitor(JSONObject visitorVariable);
```

## 接口定义

### **1.** 设置登录用户ID

当用户登录之后调用`setUserId` API，设置登录用户ID。

```java
//setuserid API原型
GrowingIO.getInstance().setUserId(String userId);
```

**参数说明**

| 参数名称   |   类型   | 是否必须 | 说明                                                                                          |
| ------ | :----: | :--: | ------------------------------------------------------------------------------------------- |
| userId | String |   是  | <p>登录用户ID，长度限制小于等于1000；</p><p>如果设置饿值为空，则清空登录用户ID，不建议这么用；</p><p>请使用 clearUserId 清除登录用户ID</p> |

```java
//setUserId API调用示例
GrowingIO.getInstance().setUserId("1234567890");
```

{% hint style="info" %}
如果您的App每次用户升级版本时无需重新登录的话，为防止用户本地缓存被清除导致的无法被识别为登录用户，建议在用户每次升级App版本后初次访问时重新调用上述`setUserId`方法。
{% endhint %}

### 2. 清除登录用户ID

当用户退出登录之后调用`clearUserId`，清除已经设置的登录用户ID。

**示例代码**

```java
//clearUserId API原型和调用示例
GrowingIO.getInstance().clearUserId();
```

### 3. 设置登录用户变量

当需要上报登录用户变量时，调用 `setPeopleVariable` API。

发送登录用户信息用于登录用户信息相关分析，在添加代码之前必须在打点管理界面上创建登录用户变量。

```java
// setPeopleVariable API原型
GrowingIO gio = GrowingIO.getInstance();
gio.setPeopleVariable(String key, String value);
gio.setPeopleVariable(String key, Number value);
gio.setPeopleVariable(String key, Boolean value);
gio.setPeopleVariable(JSONObject peopleVariables);
```

| 参数名称            | 类型         | 是否必须 | 说明                                                                                                                                                                                                                                                                          |
| --------------- | ---------- | ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| key             | String     | 否    | 用户变量的标识符。限制：非空，长度<=50                                                                                                                                                                                                                                                       |
| value           | String     | 否    | <p>用户变量的值。</p><p>限制：非空，长度&#x3C;=1000</p>                                                                                                                                                                                                                                    |
| peopleVariables | JSONObject | 否    | <p>用户变量用于用户信息相关的分析。</p><p>限制：非空，长度限制小于等于100（<code>peopleVariables.length()&#x3C;=100</code>）；</p><p><code>peopleVariables</code> 内部不允许含有<code>JSONObject</code>或者<code>JSONArray</code>；</p><p><code>key</code>长度&#x3C;=50，<code>value</code>长度&#x3C;=1000，值不能为空串，也就是""</p> |

{% hint style="info" %}
推荐您使用[Mobile Debugger](../../../debugging/mobile-debugger.md)，我们为您列举了应用场景和验证示例，请参考：[验证埋点事件](../../../debugging/verification/)>[**ppl（用户变量）事件**](../../../debugging/verification/ppl.md)。
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

注意 `t` 字段等于 ppl，表示登录用户变量发送成功，需注意 `var`字段中的 `key` 和 `value` 是否符合预期，其它字段无需仔细验证。

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

### **4.** 设置访问用户变量

当用户未登录时，定义用户属性变量，也可用于A/B测试上传标签。

当需要上报访问用户变量时，调用 `setVisitor` API。

发送访问用户信息用于访问用户信息相关分析，在添加代码之前必须在打点管理界面上创建访问用户变量。

{% hint style="warning" %}
版本支持：>=2.4.0
{% endhint %}

```java
//setVisitor API原型
GrowingIO.getInstance().setVisitor(JSONObject visitorVar)
```

**参数说明**

| **参数说明**   | 类型         | 是否必填 | 说明                                                                                                                                                               |
| ---------- | ---------- | ---- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| visitorVar | JSONObject | 是    | <p>不可使用嵌套的<code>JSONObject</code>对象，即为JSONObject中不可以放入<code>JSONObject</code>或者<code>JSONArray</code>；</p><p>key 长度&#x3C;=50，value长度&#x3C;=1000，值不能为空串，也就是""</p> |

{% tabs %}
{% tab title="Java" %}
```java
//setVisitor API调用示例
GrowingIO gio = GrowingIO.getInstance();
jsonObject.put("gender", "male");
jsonObject.put("age", "21");
gio.setVisitor(jsonObject);
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
//setVisitor API调用示例
val gio = GrowingIO.getInstance()
jsonObject.put("gender", "male")
jsonObject.put("age", "21")
gio.setVisitor(jsonObject)
```
{% endtab %}
{% endtabs %}

**检验数据发送日志示例**

注意 `t` 字段等于 vstr，表示访问用户变量发送成功，需注意 `var`字段中的 `key` 和 `value` 是否符合预期，其它字段无需仔细验证**。**

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

### 5. 设置页面级变量

{% hint style="info" %}
使用限制：适用于无埋点SDK。
{% endhint %}

当需要上报页面级变量时，调用 `setPageVariable` API。

发送页面级别的维度信息，用于标记当前页面，在添加代码之前必须在打点管理界面上创建页面级变量。

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
注意确认当前页面，通过圈选方式最快定位当前页面，在当前页面埋点最稳定可靠，如果页面未确认，可能在Activity和Fragment嵌套的场景下埋点失败。如未能成功发送自定义页面变量，请参考”Android SDK集成FAQ > [无埋点API使用问题](../faq/class2.md#zi-ding-yi-ye-mian-bian-liang-shi-jian-fa-song-shi-bai)“

参数选择是当前被识别的页面对象，可能是 Activity 或 Fragment，可以使用 Mobile Debugger 或debug日志确认。
{% endhint %}

| 参数名称               | 类型         | 是否必须 | 说明                                                                                                                                                                                                                                                                          |
| ------------------ | ---------- | ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| activity           | Activity   | 是    | 当前页面访问事件（page事件）发送的页面                                                                                                                                                                                                                                                       |
| fragment           | Fragment   | 否    | 当前页面访问事件（page事件）发送的页面                                                                                                                                                                                                                                                       |
| key                | tring      | 否    | <p>页面级变量的标识符</p><p>限制：非空，长度&#x3C;=50</p>                                                                                                                                                                                                                                    |
| value              | String     | 否    | <p>页面级变量的值</p><p>限制：非空，长度&#x3C;=等于1000</p>                                                                                                                                                                                                                                  |
| pageLevelvariables | JSONObject | 否    | <p>页面级变的信息</p><p>限制：非null，长度&#x3C;=100（<code>pageLevelVariable.length()&#x3C;=100</code>）；</p><p><code>pageLevelVariable</code> 内部不允许含有<code>JSONObject</code>或者<code>JSONArray</code>；</p><p><code>key</code> 长度&#x3C;=50，<code>value</code>长度&#x3C;=1000，值不能为空串，也就是""</p> |

{% hint style="info" %}
**`SDK 2.4.0`** 以上能够在 Log 日志中查看对应报错，之下版本无提示信息。调用后请关注日志，查看数据发送是否成功，事件类型`t`为`pvar`。

**`SDK 2.6.7`** 将页面级变量**`pageLevelVariables`**与该页面对象绑定，设置不同的值将会合并，如果想要清空，需要传 null 。

推荐您使用[Mobile Debugger](../../../debugging/mobile-debugger.md)，我们为您列举了应用场景和验证示例，请参考：[验证埋点事件](../../../debugging/verification/)>[pvar（页面级变量）事件](../../../debugging/verification/pvar.md)。
{% endhint %}

**示例代码**

{% tabs %}
{% tab title="Java" %}
```java
// setPageVariable API调用示例
GrowingIO gio = GrowingIO.getInstance();
JSONObject jsonObject = new JSONObject();
jsonObject.put("gender", "male");
jsonObject.put("age", "21");
gio.setPageVariable(myActivity, jsonObject);
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
// setPageVariable API调用示例
val gio = GrowingIO.getInstance()
val jsonObject = JSONObject()
jsonObject.put("gender", "male")
jsonObject.put("age", "21")
gio.setPageVariable(myActivity, jsonObject)
```
{% endtab %}
{% endtabs %}

**检验数据发送日志示例：**

注意 `t` 等于`pvar`字段，表示自定义事件发送成功，需注意 `var`字段中的 `key` 和 `value` 是否符合预期，其它字段无需仔细验证**。**

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

### 6. 设置转化变量

当需要上报转化变量时，调用 `setEvar` API。

发送一个转化信息用于高级归因分析，在添加代码之前必须在打点管理界面上创建转化变量。

```java
// setEvar API原型
GrowingIO gio = GrowingIO.getInstance();
gio.setEvar(String key, String value);
gio.setEvar(String key, Number value);
gio.setEvar(String key, Boolean value);
gio.setEvar(JSONObject conversionVariables);
```

参数说明

| 参数名称                | 类型         | 是否必须 | 说明                                                                                                                                                                                                                                                                                |
| ------------------- | ---------- | ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| key                 | String     | 否    | <p>转化变量的标识符</p><p>限制：非空，长度&#x3C;=50</p>                                                                                                                                                                                                                                           |
| value               | String     | 否    | <p>转化变量的值</p><p>限制：非空，长度&#x3C;=1000</p>                                                                                                                                                                                                                                           |
| conversionVariables | JSONObject | 否    | <p>转化变量用于高级归因分析</p><p>限制：非空，长度&#x3C;=100（<code>conversionVariables.length()&#x3C;=100</code>）；</p><p><code>conversionVariables</code> 内部不允许含有<code>JSONObject</code>或者<code>JSONArray</code>；</p><p><code>key</code> 长度&#x3C;=50，<code>value</code>长度&#x3C;=1000，值不能为空串，也就是""</p> |

{% hint style="info" %}
推荐您使用[Mobile Debugger](../../../debugging/mobile-debugger.md)，我们为您列举了应用场景和验证示例，请参考：[验证埋点事件](../../../debugging/verification/)>[evar（转化变量）事件](../../../debugging/verification/evar.md)。
{% endhint %}

{% tabs %}
{% tab title="Java" %}
```java
// setEvar API调用示例一
GrowingIO gio = GrowingIO.getInstance();
gio.setEvar("campaignId", "1234567890");
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
// setEvar API调用示例一
val gio = GrowingIO.getInstance()
gio.setEvar("campaignId", "1234567890")
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Java" %}
```java
// setEvar API调用示例二
GrowingIO gio = GrowingIO.getInstance();
JSONObject jsonObject = new JSONObject();
jsonObject.put("campaignId", "1234567890");
jsonObject.put("campaignOwner", "Li Si");
gio.setEvar(jsonObject);
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
// setEvar API调用示例二
val gio = GrowingIO.getInstance()
val jsonObject = JSONObject()
jsonObject.put("campaignId", "1234567890")
jsonObject.put("campaignOwner", "Li Si")
gio.setEvar(jsonObject)
```
{% endtab %}
{% endtabs %}

**检验数据发送日志示例：**

注意 `t` 字段等于 evar ，表示转化事件发送成功，需注意 `var`字段中的 `key` 和 `value` 是否符合预期，其它字段无需仔细验证。

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

### 7. 设置埋点事件和事件级变量

当需要上报埋点事件和事件级变量时，调用 `track` API。

发送一个埋点事件，在添加所需要发送的事件代码之前，需要在打点管理用户界面创建埋点事件以及事件级变量，并完成埋点事件和事件级变量的绑定。

```java
// track API原型
GrowingIO gio = GrowingIO.getInstance();
gio.track(String eventId);
gio.track(String eventId, JSONObject eventLevelVariables);
```

| 参数名称               | 类型         | 是否必须 | 说明                                                                                                                                                                                              |
| ------------------ | ---------- | ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| eventId            | String     | 是    | 事件标识符                                                                                                                                                                                           |
| eventLevelVariable | JSONObject | 否    | <p>事件发生时所伴随的维度信息。</p><p>限制：非空，键值对个数&#x3C;=100（eventLevelVariable.length()&#x3C;=100）；eventLevelVariable内部不允许含有JSONObject或者JSONArray；</p><p>key长度&#x3C;=50，value长度&#x3C;=1000，值不能为空字符串，也就是“”</p> |

{% hint style="info" %}
SDK 2.4.0以上能够在Log日志中查看对应报错，之下版本无提示信息。调用后请关注日志，查看数据发送是否成功，事件类型t为cstm。

推荐您使用[Mobile Debugger](../../../debugging/mobile-debugger.md)，我们为您列举了应用场景和验证示例，请参考：[验证埋点事件](../../../debugging/verification/)>[cstm（事件以及关联的事件级变量）事件](../../../debugging/verification/cstm.md)。
{% endhint %}

**示例代码**

{% tabs %}
{% tab title="Java" %}
```java
// track API调用示例一
GrowingIO gio = GrowingIO.getInstance();
gio.track("registerSuccess");
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
// track API调用示例一
val gio = GrowingIO.getInstance()
gio.track("registerSuccess")
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Java" %}
```java
// track API调用示例二
GrowingIO gio = GrowingIO.getInstance();
JSONObject jsonObject = new JSONObject();
jsonObject.put("gender", "male");
jsonObject.put("age", "21");
gio.track("registerSuccess", jsonObject);
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
val gio = GrowingIO.getInstance()
val jsonObject = JSONObject()
jsonObject.put("gender", "male")
jsonObject.put("age", "21")
gio.track("registerSuccess", jsonObject)
```
{% endtab %}
{% endtabs %}

**检验数据发送日志示例**

注意 `t` 等于 `cstm` 字段，表示自定义事件发送成功，`n` 字段表示埋点事件的标识符，需注意 `var`字段中的 `key` 和 `value` 是否符合预期，其它字段无需仔细验证**。**

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
