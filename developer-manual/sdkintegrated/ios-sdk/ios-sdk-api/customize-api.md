# 自定义数据上传API

您的APP或网页在集成了 GrowingIO 的 SDK 之后，它将会自动地为您采集一系列用户行为数据，并在 GrowingIO 分析后台供您制成数据分析报表。除上述的用户行为数据（或称为无埋点数据）之外，GrowingIO 还提供了多种 API 接口，供您上传一些自定义事件和变量，下面介绍自定义事件和变量 API 使用方法。

## API概览

SDK 提供多种不同类型的API，请根据您的实际需要正确地调用。

```java
// 发送自定义事件 API
+ (void)track:(NSString *)eventId;
+ (void)track:(NSString *)eventId withVariable:(NSDictionary<NSString *, NSObject *> *)variable;
​
// 发送页面级变量 API
+ (void)setPageVariableWithKey:(NSString *)key andStringValue:(NSString *)stringValue toViewController:(UIViewController *)viewController;
+ (void)setPageVariableWithKey:(NSString *)key andNumberValue:(NSNumber *)numberValue toViewController:(UIViewController *)viewController;
+ (void)setPageVariable:(NSDictionary<NSString *, NSObject *> *)variable toViewController:(UIViewController *)viewController;
​
// 发送转化变量 API
+ (void)setEvarWithKey:(NSString *)key andStringValue:(NSString *)stringValue;
+ (void)setEvarWithKey:(NSString *)key andNumberValue:(NSNumber *)numberValue;
+ (void)setEvar:(NSDictionary<NSString *, NSObject *> *)variable;
​
// 发送用户变量 API
+ (void)setPeopleVariableWithKey:(NSString *)key andStringValue:(NSString *)stringValue;
+ (void)setPeopleVariableWithKey:(NSString *)key andNumberValue:(NSNumber *)numberValue;
+ (void)setPeopleVariable:(NSDictionary<NSString *, NSObject *> *)variable;
​
// 访问用户变量 API
+ (void)setVisitor:(NSDictionary<NSString *, NSObject *> *)variable;
​
// 设置登录用户ID API
+ (void)setUserId:(NSString *)userId;
​
// 清除登录用户ID API
+ (void)clearUserId;
```

## 接口定义

### 设置登录用户ID（setUserId）

当用户登录之后调用setUserId API，设置登录用户ID。

```java
// setUserId API原型
+ (void)setUserId:(NSString *)userId;
```

**参数说明**

| 参数名称 | 类型 | 是否必须 | 说明 |
| ---- | -- | ---- | -- |

| userId | string | 是 | <p>用户的<strong>登录用户ID</strong></p><p>限制：英文数字组合的字符串，长度小于等于1000，且不能含有特殊字符，不允许传空、<code>""</code> 或者<code>nil</code>，如有清除操作，请调用 <code>clearUserId</code> 方法</p> |
| ------ | ------ | - | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |

```java
// setuserId API调用示例
[Growing setUserId:@"1234567890"];
```

{% hint style="info" %}
如果您的App每次用户升级版本时无需重新登录的话，为防止用户本地缓存被清除导致的无法被识别为登录用户，建议在用户每次升级App版本后初次访问时重新调用上述setUserId方法。
{% endhint %}

### 清除登录用户ID（clearUserId）

当用户登出之后调用clearUserId，清除已经设置的登录用户ID。

```java
// clearUserId API原型
+ (void)clearUserId;
```

```java
// clearUserId API调用示例
[Growing clearUserId];
```

### 设置登录用户变量（setPeopleVariable）

发送用户信息用于用户信息相关分析，在添加代码之前必须在打点管理界面上声明用户变量。

```java
// setPeopleVariable API原型
+ (void)setPeopleVariableWithKey:(NSString *)key andStringValue:(NSString *)stringValue;
+ (void)setPeopleVariableWithKey:(NSString *)key andNumberValue:(NSNumber *)numberValue;
+ (void)setPeopleVariable:(NSDictionary<NSString *, NSObject *> *)variable;
```

**参数说明**

| 参数名称 | 类型 | 是否必须 | 说明 |
| ---- | -- | ---- | -- |

| key | string | 否 | <p>用户变量的标识符。</p><p><strong>限制</strong>：不能为nil或""，长度小于等于50。</p> |
| --- | ------ | - | -------------------------------------------------------------- |

| value | string | 否 | <p>用户变量的值。</p><p><strong>限制</strong>：变量不为nil或者""，若为字符串则长度应小于等于 1000。</p> |
| ----- | ------ | - | ------------------------------------------------------------------------ |

| customerVariables | NSDictionary | <p>用户变量用于用户信息相关的分析。</p><p><strong>限制</strong>：不能为nil；<code>customerVariables</code> 内部不允许含有<code>NSDictionary</code>或者<code>NSArray；</code></p><p><code>key</code> 长度限制小于等于50，<code>value</code> 长度限制小等于1000，值不能为空串，也就是""。</p> |   |
| ----------------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | - |

```java
// setPeopleVariable API调用示例一
[Growing setPeopleVariableWithKey:@"gender" andStringValue:@"male"];
```

```java
// setPeopleVariable API调用示例二
[Growing setPeopleVariable:@{@"gender":@"male", @"age":@"25"}];
```

### 设置访问用户变量（setVisitor）

当用户未登录时，定义用户属性变量，也可以用于A/B测试上传标签。

**SDK版本支持：>=2.4.0**

```java
// setVisitor 访问用户变量 API原型
+ (void)setVisitor:(NSDictionary<NSString *, NSObject *> *)variable;
```

**参数说明**

| **参数名称** | 类型 | 是否必须 | 说明 |
| -------- | -- | ---- | -- |

| variable | NSDctionary | 是 | <p>访问用户信息。</p><p><strong>限制</strong>：不能为<code>nil；variable</code> 内部不允许含有<code>NSDictionary</code>或者<code>NSArray；</code></p><p><code>key</code> 长度限制小于等于50，<code>value</code> 长度限制小等于1000，值不能为空串，也就是""。</p> |
| -------- | ----------- | - | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

```java
// setVisitor API调用示例
[Growing setVisitor:@{@"gender":@"male", @"age":@"25"}];
```

### 设置页面级变量（setPageVariable）

{% hint style="info" %}
使用限制：适用于无埋点SDK。
{% endhint %}

发送页面级别的信息，在添加代码之前必须在打点管理界面上声明页面级变量。

```java
// setPageVariable API原型
+ (void)setPageVariableWithKey:(NSString *)key andStringValue:(NSString *)stringValue toViewController:(UIViewController *)viewController;
+ (void)setPageVariableWithKey:(NSString *)key andNumberValue:(NSNumber *)numberValue toViewController:(UIViewController *)viewController;
+ (void)setPageVariable:(NSDictionary<NSString *, NSObject *> *)variable toViewController:(UIViewController *)viewController;
```

**参数说明**

| 参数名称 | 类型 | 是否必须 | 说明 |
| ---- | -- | ---- | -- |

| key | string | 否 | <p>页面级变量的标识符。</p><p><strong>限制</strong>：不能为 nil 或者""，长度小于等于50。</p> |
| --- | ------ | - | ------------------------------------------------------------------ |

| value | string | 否 | <p>页面级变量的值。</p><p><strong>限制</strong>：不能为 nil 或者""，若为字符串则长度应小于等于 1000。</p> |
| ----- | ------ | - | -------------------------------------------------------------------------- |

| pageLevelVariables | NSDictionary | 否 | <p>页面级别的信息。</p><p><strong>限制</strong>：不能为 nil；<code>pageLevelVariable</code> 内部不允许含有<code>NSDictionary</code>或者<code>NSArray；</code></p><p><code>key</code> 长度限制小于等于50，<code>value</code> 长度限制小等于1000，值不能为空串，也就是""。</p> |
| ------------------ | ------------ | - | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

{% hint style="info" %}
**`SDK 2.6.7`** 将页面级变量**`pageLevelVariables`**与该页面对象绑定，设置不同的值将会合并，如果想要清空，需要传 null 。
{% endhint %}

**代码示例**

```java
// setPageVariable API调用示例一
[Growing setPageVariableWithKey:@"author" andStringValue:@"Zhang San" toViewController:myViewController];
```

```java
// setPageVariable API调用示例二
[Growing setPageVariable:@{@"pageName":@"Home Page", @"author":@"Zhang San"} toViewController:myViewController];
```

### 设置转化变量（setEvar）

发送一个转化信息用于高级归因分析，在添加代码之前必须在打点管理界面上声明转化变量。

```java
// setEvar API原型
+ (void)setEvarWithKey:(NSString *)key andStringValue:(NSString *)stringValue;
+ (void)setEvarWithKey:(NSString *)key andNumberValue:(NSNumber *)numberValue;
+ (void)setEvar:(NSDictionary<NSString *, NSObject *> *)variable;
```

**参数说明**

| 参数名称 | 类型 | 是否必须 | 说明 |
| ---- | -- | ---- | -- |

| key | string | 否 | <p>转化变量的标识符。</p><p><strong>限制</strong>：不能为 nil 或者""，长度小于等于50。</p> |
| --- | ------ | - | ----------------------------------------------------------------- |

| value | string | 否 | <p>转化变量的值。</p><p><strong>限制</strong>：变量不为nil或者""，若为字符串则长度应小于等于 1000。</p> |
| ----- | ------ | - | ------------------------------------------------------------------------ |

| conversionVariables | NSDictionary | 否 | <p>转化变量用于高级归因分析。</p><p><strong>限制</strong>：不能为nil；<code>conversinoLevelVariable</code> 内部不允许含有<code>NSDictionary</code>或者<code>NSArray；</code></p><p><code>key</code> 长度限制小于等于50，<code>value</code> 长度限制小等于1000，值不能为空串，也就是""。</p> |
| ------------------- | ------------ | - | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

```java
// setEvar API调用示例一
[Growing setEvarWithKey:@"campaignId" andStringValue:@"1234567890"];
```

```java
// setEvar API调用示例二
[Growing setEvar:@{@"campaignId":@"12345", @"campaignOwner":@"Li Si"}];
```

### 设置自定义事件和事件级变量（track）

发送一个自定义事件。在添加所需要发送的事件代码之前，需要在打点管理用户界面声明事件以及事件级变量。

```java
// track API原型
+ (void)track:(NSString *)eventId;
+ (void)track:(NSString *)eventId withVariable:(NSDictionary<NSString *, NSObject *> *)variable;
```

**参数说明**

| 参数名称 | 类型 | 是否必须 | 说明 |
| ---- | -- | ---- | -- |

| eventId | string | 是 | 事件标识符。 |
| ------- | ------ | - | ------ |

| eventLevelVariable | NSDictionary | 否 | <p>事件发生时所伴随的维度信息。</p><p>限制：非空，长度限制小于等于100（eventLevelVariable.length()&#x3C;=100）；eventLevelVariable内部不允许含有<code>NSDictionary</code>或者<code>NSArray</code>； key长度限制小于等于50，value长度限制小于等于200，值不能为空字符串，也就是“”。</p> |
| ------------------ | ------------ | - | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

```java
// track API调用示例一
[Growing track:@"registerSuccess"];
```

```java
// track API调用示例二
[Growing track:@"registerSuccess" withVariable:@{@"gender":@"male", @"age":@"21"}];
```

```java
// track API调用示例三
[Growing track:@"loanAmount" withNumber:@800000 andVariable:@{@"loanType":@"houseMortgage", @"province":@"Zhejiang"}];
```

### 设置SDK异常上传开关 <a href="#5-she-zhi-dan-chuang-sdk-yi-chang-shang-chuan-kai-guan" id="5-she-zhi-dan-chuang-sdk-yi-chang-shang-chuan-kai-guan"></a>

SDK会收集SDK内部异常上报服务端，方便开发更好的追踪SDK的问题，和完善SDK的功能。如果您不想帮助我们产品完善功能，或者和您的crash收集框架有冲突，您可以选择关闭此功能。

{% hint style="info" %}
请在 startWithAccountId: 或 startWithAccountId: withSampling: 接口之前设置 (SDK2.8.9以后)
{% endhint %}

* (**void**)setUploadExceptionEnable:(**BOOL**)uploadExceptionEnable;

```objectivec
// sdk crash 收集
[Growing setUploadExceptionEnable:YES];
[Growing startWithAccountId:@"aaaa"];
```

### 获取 Apple Search Ads 归因数据分析 <a href="#5-she-zhi-dan-chuang-sdk-yi-chang-shang-chuan-kai-guan" id="5-she-zhi-dan-chuang-sdk-yi-chang-shang-chuan-kai-guan"></a>

如您需要使用 Apple Search Ads 归因数据分析，请在 SDK 初始化之前调用`setAsaEnabled`接口：

```objectivec
// 设置是否获取 Apple Search Ads 归因数据
[Growing setAsaEnabled:YES];
[Growing startWithAccountId:@"aaaa"];
```

在 Target -> Build Phases -> Link Binary With Libraries，添加 iAd.framework 和 AdServices.framework，并设置 AdServices.framework status 为 Optional

![](<../../../../.gitbook/assets/image (180) (1).png>)
