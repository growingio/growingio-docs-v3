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
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">userId</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x662F;</th>
      <th style="text-align:left">
        <p>&#x7528;&#x6237;&#x7684;<b>&#x767B;&#x5F55;&#x7528;&#x6237;ID</b>
        </p>
        <p>&#x9650;&#x5236;&#xFF1A;&#x82F1;&#x6587;&#x6570;&#x5B57;&#x7EC4;&#x5408;&#x7684;&#x5B57;&#x7B26;&#x4E32;&#xFF0C;&#x957F;&#x5EA6;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;1000&#xFF0C;&#x4E14;&#x4E0D;&#x80FD;&#x542B;&#x6709;&#x7279;&#x6B8A;&#x5B57;&#x7B26;&#xFF0C;&#x4E0D;&#x5141;&#x8BB8;&#x4F20;&#x7A7A;&#x3001;<code>&quot;&quot;</code> &#x6216;&#x8005;<code>nil</code>&#xFF0C;&#x5982;&#x6709;&#x6E05;&#x9664;&#x64CD;&#x4F5C;&#xFF0C;&#x8BF7;&#x8C03;&#x7528; <code>clearUserId</code> &#x65B9;&#x6CD5;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>```java
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
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">key</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x7528;&#x6237;&#x53D8;&#x91CF;&#x7684;&#x6807;&#x8BC6;&#x7B26;&#x3002;</p>
        <p><b>&#x9650;&#x5236;</b>&#xFF1A;&#x4E0D;&#x80FD;&#x4E3A;nil&#x6216;&quot;&quot;&#xFF0C;&#x957F;&#x5EA6;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">value</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x7528;&#x6237;&#x53D8;&#x91CF;&#x7684;&#x503C;&#x3002;</p>
        <p><b>&#x9650;&#x5236;</b>&#xFF1A;&#x53D8;&#x91CF;&#x4E0D;&#x4E3A;nil&#x6216;&#x8005;&quot;&quot;&#xFF0C;&#x82E5;&#x4E3A;&#x5B57;&#x7B26;&#x4E32;&#x5219;&#x957F;&#x5EA6;&#x5E94;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;
          1000&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">customerVariables</th>
      <th style="text-align:left">NSDictionary</th>
      <th style="text-align:left">
        <p>&#x7528;&#x6237;&#x53D8;&#x91CF;&#x7528;&#x4E8E;&#x7528;&#x6237;&#x4FE1;&#x606F;&#x76F8;&#x5173;&#x7684;&#x5206;&#x6790;&#x3002;</p>
        <p><b>&#x9650;&#x5236;</b>&#xFF1A;&#x4E0D;&#x80FD;&#x4E3A;nil&#xFF1B;<code>customerVariables</code> &#x5185;&#x90E8;&#x4E0D;&#x5141;&#x8BB8;&#x542B;&#x6709;<code>NSDictionary</code>&#x6216;&#x8005;<code>NSArray&#xFF1B;</code>
        </p>
        <p><code>key</code> &#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#xFF0C;<code>value</code> &#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x7B49;&#x4E8E;1000&#xFF0C;&#x503C;&#x4E0D;&#x80FD;&#x4E3A;&#x7A7A;&#x4E32;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&quot;&quot;&#x3002;</p>
      </th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody></tbody>
</table>```java
// setPeopleVariable API调用示例一
[Growing setPeopleVariableWithKey:@"gender" andStringValue:@"male"];
```

```java
// setPeopleVariable API调用示例二
[Growing setPeopleVariable:@{@"gender":@"male", @"age":@"25"}];
```

### 设置访问用户变量（setVisitor）

当用户未登录时，定义用户属性变量，也可以用于A/B测试上传标签。

**SDK版本支持：&gt;=2.4.0**

```java
// setVisitor 访问用户变量 API原型
+ (void)setVisitor:(NSDictionary<NSString *, NSObject *> *)variable;
```

**参数说明**

| **参数名称** | 类型 | 是否必须 | 说明 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">variable</th>
      <th style="text-align:left">NSDctionary</th>
      <th style="text-align:left">&#x662F;</th>
      <th style="text-align:left">
        <p>&#x8BBF;&#x95EE;&#x7528;&#x6237;&#x4FE1;&#x606F;&#x3002;</p>
        <p><b>&#x9650;&#x5236;</b>&#xFF1A;&#x4E0D;&#x80FD;&#x4E3A;<code>nil&#xFF1B;variable</code> &#x5185;&#x90E8;&#x4E0D;&#x5141;&#x8BB8;&#x542B;&#x6709;<code>NSDictionary</code>&#x6216;&#x8005;<code>NSArray&#xFF1B;</code>
        </p>
        <p><code>key</code> &#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#xFF0C;<code>value</code> &#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x7B49;&#x4E8E;1000&#xFF0C;&#x503C;&#x4E0D;&#x80FD;&#x4E3A;&#x7A7A;&#x4E32;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&quot;&quot;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>```java
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
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">key</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&#x7684;&#x6807;&#x8BC6;&#x7B26;&#x3002;</p>
        <p><b>&#x9650;&#x5236;</b>&#xFF1A;&#x4E0D;&#x80FD;&#x4E3A; nil &#x6216;&#x8005;&quot;&quot;&#xFF0C;&#x957F;&#x5EA6;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">value</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&#x7684;&#x503C;&#x3002;</p>
        <p><b>&#x9650;&#x5236;</b>&#xFF1A;&#x4E0D;&#x80FD;&#x4E3A; nil &#x6216;&#x8005;&quot;&quot;&#xFF0C;&#x82E5;&#x4E3A;&#x5B57;&#x7B26;&#x4E32;&#x5219;&#x957F;&#x5EA6;&#x5E94;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;
          1000&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">pageLevelVariables</th>
      <th style="text-align:left">NSDictionary</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x9875;&#x9762;&#x7EA7;&#x522B;&#x7684;&#x4FE1;&#x606F;&#x3002;</p>
        <p><b>&#x9650;&#x5236;</b>&#xFF1A;&#x4E0D;&#x80FD;&#x4E3A; nil&#xFF1B;<code>pageLevelVariable</code> &#x5185;&#x90E8;&#x4E0D;&#x5141;&#x8BB8;&#x542B;&#x6709;<code>NSDictionary</code>&#x6216;&#x8005;<code>NSArray&#xFF1B;</code>
        </p>
        <p><code>key</code> &#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#xFF0C;<code>value</code> &#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x7B49;&#x4E8E;1000&#xFF0C;&#x503C;&#x4E0D;&#x80FD;&#x4E3A;&#x7A7A;&#x4E32;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&quot;&quot;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>{% hint style="info" %}
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
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">key</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x8F6C;&#x5316;&#x53D8;&#x91CF;&#x7684;&#x6807;&#x8BC6;&#x7B26;&#x3002;</p>
        <p><b>&#x9650;&#x5236;</b>&#xFF1A;&#x4E0D;&#x80FD;&#x4E3A; nil &#x6216;&#x8005;&quot;&quot;&#xFF0C;&#x957F;&#x5EA6;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">value</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x8F6C;&#x5316;&#x53D8;&#x91CF;&#x7684;&#x503C;&#x3002;</p>
        <p><b>&#x9650;&#x5236;</b>&#xFF1A;&#x53D8;&#x91CF;&#x4E0D;&#x4E3A;nil&#x6216;&#x8005;&quot;&quot;&#xFF0C;&#x82E5;&#x4E3A;&#x5B57;&#x7B26;&#x4E32;&#x5219;&#x957F;&#x5EA6;&#x5E94;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;
          1000&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">conversionVariables</th>
      <th style="text-align:left">NSDictionary</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x8F6C;&#x5316;&#x53D8;&#x91CF;&#x7528;&#x4E8E;&#x9AD8;&#x7EA7;&#x5F52;&#x56E0;&#x5206;&#x6790;&#x3002;</p>
        <p><b>&#x9650;&#x5236;</b>&#xFF1A;&#x4E0D;&#x80FD;&#x4E3A;nil&#xFF1B;<code>conversinoLevelVariable</code> &#x5185;&#x90E8;&#x4E0D;&#x5141;&#x8BB8;&#x542B;&#x6709;<code>NSDictionary</code>&#x6216;&#x8005;<code>NSArray&#xFF1B;</code>
        </p>
        <p><code>key</code> &#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#xFF0C;<code>value</code> &#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x7B49;&#x4E8E;1000&#xFF0C;&#x503C;&#x4E0D;&#x80FD;&#x4E3A;&#x7A7A;&#x4E32;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&quot;&quot;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>```java
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
| :--- | :--- | :--- | :--- |


| eventId | string | 是 | 事件标识符。 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">eventLevelVariable</th>
      <th style="text-align:left">NSDictionary</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>&#x4E8B;&#x4EF6;&#x53D1;&#x751F;&#x65F6;&#x6240;&#x4F34;&#x968F;&#x7684;&#x7EF4;&#x5EA6;&#x4FE1;&#x606F;&#x3002;</p>
        <p>&#x9650;&#x5236;&#xFF1A;&#x975E;&#x7A7A;&#xFF0C;&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;100&#xFF08;eventLevelVariable.length()&lt;=100&#xFF09;&#xFF1B;eventLevelVariable&#x5185;&#x90E8;&#x4E0D;&#x5141;&#x8BB8;&#x542B;&#x6709;<code>NSDictionary</code>&#x6216;&#x8005;<code>NSArray</code>&#xFF1B;
          key&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;50&#xFF0C;value&#x957F;&#x5EA6;&#x9650;&#x5236;&#x5C0F;&#x4E8E;&#x7B49;&#x4E8E;200&#xFF0C;&#x503C;&#x4E0D;&#x80FD;&#x4E3A;&#x7A7A;&#x5B57;&#x7B26;&#x4E32;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&#x201C;&#x201D;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>```java
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

### 设置SDK异常上传开关 <a id="5-she-zhi-dan-chuang-sdk-yi-chang-shang-chuan-kai-guan"></a>

SDK会收集SDK内部异常上报服务端，方便开发更好的追踪SDK的问题，和完善SDK的功能。如果您不想帮助我们产品完善功能，或者和您的crash收集框架有冲突，您可以选择关闭此功能。

{% hint style="info" %}
请在 startWithAccountId: 或 startWithAccountId: withSampling: 接口之前设置 \(SDK2.8.9以后\)
{% endhint %}

* \(**void**\)setUploadExceptionEnable:\(**BOOL**\)uploadExceptionEnable;

```objectivec
// sdk crash 收集
[Growing setUploadExceptionEnable:YES];
[Growing startWithAccountId:@"aaaa"];
```

