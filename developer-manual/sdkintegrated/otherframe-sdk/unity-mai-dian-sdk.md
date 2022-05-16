# Unity 埋点 SDK

{% hint style="success" %}
GitHub Demo： [https://github.com/growingio/GrowingSDK-Unity-GameTrack](https://github.com/growingio/GrowingSDK-Unity-GameTrack)

Unity 全版本支持

App适配最低系统版本：iOS 8及以上、Android 4.2-10
{% endhint %}

## 1. 集成

{% tabs %}
{% tab title="Android" %}
1. 将最新的Unity埋点SDK `vds-android-agent-game-track.jar`导入 Unity 项目目录`Assets/Plugins/Android/`
2. 在Android工程中集成 Android 原生埋点SDK，并初始化，参考[Android原生端埋点SDK文档](https://docs.growingio.com/docs/sdk-integration/android-sdk/android-mai-dian-sdk)，如已集成请跳过该步骤

```
public class GameApp extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        GrowingIO.startWithConfiguration(this, new Configuration()     
            .setProjectId("xxxxx")
            .setURLScheme("growing.xxxxx")
            .setDebugMode(true));
        );
    }
}
```

&#x20;3\. 在`LAUNCHER Activity`的`onNewIntent`方法中调用`public GrowingIO onNewIntent(Activity activity, Intent intent)`API。如果使用的是Unity默认的`UnityPlayerActivity`为`LAUNCHER Activity`，请自定义一个`LAUNCHER Activity`。

4\. 添加`AndroidManifest.xml`文件到 Unity 项目目录`Assets/Plugins/Android/`，并注意修改`AndroidManifest.xml`中`${您的APP包名}`等关键字

&#x20;5\. 更多细节请参看[UnityDemo](https://github.com/growingio/GrowingSDK-Unity-GameTrack/tree/master/UnityDemo)和[Android原生端埋点SDK文档](https://docs.growingio.com/docs/sdk-integration/android-sdk/android-mai-dian-sdk)
{% endtab %}

{% tab title="iOS" %}
1. 将最新的埋点SDK `GrowingCoreKit.framework` 参考[iOS原生端埋点SDK](https://docs.growingio.com/docs/sdk-integration/ios-sdk-1/mai-dian-sdk-ji-cheng)，导入 Unity 项目目录 `Assets/Plugins/iOS/` 中
2. 将 `BuildPostProcessor` 脚本文件导入 Unity 项目目录 `Assets/Editor`中
3. 配置 URLScheme：将在GrowingIO官网申请到的应用的 `URL Scheme` 填入到 `BuildPostProcessor` 中的 `AddInfoPlist(path, "XXXXX");` XXXXX 处并保存
4. 在iOS工程中集成 iOS 原生埋点SDK，并初始化，参考[iOS原生端埋点SDK文档](https://docs.growingio.com/docs/sdk-integration/ios-sdk-1/mai-dian-sdk-ji-cheng)，如已集成请跳过该步骤

```
- (BOOL)application:(UIApplication*)application didFinishLaunchingWithOptions:(NSDictionary*)launchOptions
{
     [Growing startWithAccountId:@"xxxxx"];
     return YES;
}
```

&#x20;5\. Unity 工程中可以通过 `GrowingIOGame.cs`脚本调用指定的埋点方法

&#x20;6\. 更多细节请参考[UnityDemo](https://github.com/growingio/GrowingSDK-Unity-GameTrack/tree/master/UnityDemo)和[iOS原生端埋点SDK文档](https://docs.growingio.com/docs/sdk-integration/ios-sdk-1/mai-dian-sdk-ji-cheng)
{% endtab %}
{% endtabs %}

## 2. 自定义数据上传

### 采集自定义事件

```javascript
public static void Track(string eventId)
public static void Track(string eventId, double number)
public static void Track(string eventId, Dictionary<string, object> variable)
public static void Track(string eventId, double number, Dictionary<string, object> variable)
```

采集自定义事件 `eventId`，该事件的属性信息属于事件级变量。

在添加所需要发送的事件代码之前，需要在打点管理用户界面配置事件以及事件级变量`eventLevelVariable`。

**参数说明：**

| 参数名称                 | 参数类型       | 必填 | 说明            |
| -------------------- | ---------- | -- | ------------- |
| `eventId`            | String     | 是  | 事件标识符         |
| `eventLevelVariable` | Dictionary | 否  | 事件发生时所伴随的维度信息 |

**参数限制条件：**

参数违反以下条件将不发送数据，调用后请验证数据是否发送，事件类型`t`为`cstm`。

| 参数名称                 | 限制条件                                                                                                                                                                                                                                              |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `eventId`            | 非空，长度限制小于等于50；                                                                                                                                                                                                                                    |
| `eventLevelVariable` | <p>非空，长度限制小于等于100（<code>eventLevelVariable.length()&#x3C;=100</code>）；</p><p><code>eventLevelVariable</code> 内部不允许嵌套 Dictionary；</p><p><code>eventLevelVariable</code>Dictionary 中的 <code>key</code>长度限制小于等于50，<code>value</code>长度限制小等于1000。</p> |

```javascript
//Track 设置自定义事件
GrowingIOGame.Track("StringTrack");
GrowingIOGame.Track("NumberTrack", 10);
    
//Track 设置自定义事件，传递字典参数
Dictionary<string, object> dictionary = new Dictionary<string, object> {{"key1", "value1"}, {"key2", 111}, {"key3", false}};
GrowingIOGame.Track("DictionaryTrack", dictionary);

Dictionary<string, object> dictionary = new Dictionary<string, object> {{"key1", "value1"}, {"key2", 111.11}};
GrowingIOGame.Track("NumberDictionaryTrack", 66.66, dictionary
```

### 设置转化变量

```javascript
public static void SetEvar(string key, string value)
public static void SetEvar(string key, double number)
public static void SetEvar(Dictionary<string, object> variable)
```

发送一个转化信息用于高级归因分析，在添加代码之前必须在打点管理界面上声明转化变量。

转化变量是一种非常强大的变量类型，主要是为了归因而用，比如访问渠道、站外搜索关键词、站内搜索关键词等等。在 GrowingIO 里面可以定制变量的归因方式和持久性范围。

**参数说明：**

| 参数名                 | 类型         | 是否必填 | 描述    |
| ------------------- | ---------- | ---- | ----- |
| conversionVariables | Dictionary | 是    | 转化级属性 |

**参数限制条件：**

| 参数名称                | 限制条件                                                                                                                                                                                                           |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| conversionVariables | <p>非空，键值对个数小于等于100；</p><p><code>conversionVariables</code> 内部不允许含有<code>Dictionary</code> 嵌套；</p><p><code>conversionVariables</code>Dictionary中的 <code>key</code>长度限制小于等于50，<code>value</code>长度限制小等于1000。</p> |

```java
 //SetEvar 设置转化变量
 GrowingIOGame.SetEvar("EvarStringKey", "EvarString");
 GrowingIOGame.SetEvar("EvarNumberKey", "100");
    
 //SetEvar 设置转化变量，传递字典参数
 Dictionary<string, object> dictionary = new Dictionary<string, object> {{"EvarKey1", "EvarValue1"}, {"EvarKey2", true}};
 GrowingIOGame.SetEvar(dictionary);
```

### 设置登录用户变量

```javascript
public static void SetPeopleVariable(string key, string value)
public static void SetPeopleVariable(string key, double number)
public static void SetPeopleVariable(Dictionary<string, object> variable)
```

设置用户自身属性相关的属性信息，比如用户姓名、邮件地址、信用等级等。

在添加代码之前必须在打点管理界面上声明用户变量。

**参数说明**

| 参数名             | 类型         | 是否必填 | 描述   |
| --------------- | ---------- | ---- | ---- |
| peopleVariables | Dictionary | 是    | 用户属性 |

**参数限制条件：**

| 参数名称            | 限制条件                                                                                                                                                                                                                                                  |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| peopleVariables | <p>非空，长度限制小于等于100（<code>peopleVariables.length()&#x3C;=100</code>）；</p><p><code>peopleVariables</code> 内部不允许含有<code>Dictionary</code>或者；</p><p><code>peopleVariables</code> Dictionary中的 <code>key</code>度限制小于等于50，<code>value</code>长度限制小等于1000。</p> |

```javascript
//SetPeopleVariable 设置用户变量
GrowingIOGame.SetPeopleVariable("PeopleStringKey", "PeopleString");
GrowingIOGame.SetPeopleVariable("PeopleNumberKey", "PeopleNumber");
    
//SetPeopleVariable 设置用户变量，传递字典参数
Dictionary<string, object> dictionary = new Dictionary<string, object> {{"PeopleKey1", "PeopleValue1"}, {"PeopleKey2", 6.66}};
GrowingIOGame.SetPeopleVariable(dictionary);
```

### 设置登录用户ID

```javascript
public static void SetUserId(string userId)
```

把 GrowingIO 识别的访问用户跟应用自身的注册用户做关联，用以登录用户行为分析。

**参数说明：**

| 参数名称   | 参数类型   | 必填 | 说明                                                                                        |
| ------ | ------ | -- | ----------------------------------------------------------------------------------------- |
| userId | String | 是  | <p>登录用户Id，长度限制小于等于1000；</p><p>如果值为空则清空了登录用户变量，不建议这么用，</p><p>请使用 clearUserId 清除登录用户变量。</p> |

```java
GrowingIOGame.SetUserId("张三");
```

注：您的 App 每次用户升级版本时无需重新登录的话，建议在用户每次升级App 版本后初次访问时重新调用上述 setUserId 方法。

### 清除登录用户ID

```javascript
public static void ClearUserId()
```

当访问用户跟注册用户关联后，之后触发的行为会绑定到该注册用户上。如果有需要解除绑定，比如用户退出登录后，可以通过该函数解决绑定。

**示例**

```javascript
GrowingIOGame.ClearUserId();
```

### 设置访问用户变量

当用户未登录时，定义用户属性变量，也可用于A/B测试上传标签。

```java
public static void SetVisitor(Dictionary<string, object> variable)
```

**参数说明：**

| 参数名称         | 参数类型       | 必填 | 说明                                                                                                                                     |
| ------------ | ---------- | -- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `visitorVar` | Dictionary | 是  | <p>不可使用嵌套的<code>Dictionary</code>对象，即为Dictionary中不可以放入<code>Dictionary</code>；</p><p>key 长度限制小于等于50，value长度限制小等于1000，值不能为空串，也就是""。</p> |

```java
//SetVisitor 设置访问用户变量，传递字典参数
Dictionary<string, object> dictionary = new Dictionary<string, object> {{"VisitorKey1", "VisitorValue1"}, {"VisitorKey2", false}};
GrowingIOGame.SetVisitor(dictionary);
```

## 3. 创建应用

{% hint style="danger" %}
**添加代码之后，请先Clean项目，然后再进行编译，并在你的 App 安装了 SDK 后重新启动几次 App，保证行为采集数据自动发送给 GrowingIO，以便顺利完成检测。**
{% endhint %}

在GrowingIO平台的应用创建页面继续完成应用创建的数据检测，检测成功后应用创建成功。

## 4. 验证SDK是否正常采集数据 <a href="#5-yan-zheng-sdk-shi-fou-zheng-chang-cai-ji-shu-ju" id="5-yan-zheng-sdk-shi-fou-zheng-chang-cai-ji-shu-ju"></a>

了解GrowingIO平台数据采集类型请参考[数据模型](../../../introduction/datamodel/)。

GrowingIO为您提供多种验证SDK是否正常采集数据的方式：

方式一：[Mobile Debugger​​](../../debugging/mobile-debugger.md)

方式二：在SDK中设置了Debug模式后，在IDE编译器控制台查看数据采集日志。
