---
description: >-
  GrowingIO除了先进的数据分析理念和技术外，还从硅谷带来了对于数据安全与数据隐私极为重视的态度，我们将在每一个环节保证您的数据安全以及保护用户数据隐私。
---

# 数据安全

## 加密传输

GrowingIO使用SSL对数据传输进行加密。

数据全程使用超文本传输安全协议 \(https\) 进行传输，利用 SSL/TLS 加密数据包，能有效防护窃听与中间人攻击，最大程度地保护您数据传输的安全性。

## 隔离保存

传输过来的数据会储存在云服务上，我们采用的是全球最大的云服务商 AWS，并集成了 AWS 的安全机制，在 GrowingIO 内部也拥有一套完整的安全机制和权限管理，并且生产和开发环境完全隔离。

## 严格控制内部权限

GrowingIO 的客户服务人员无权访问客户数据，除非客户直接授权客服登录。同时，您的管理账户里面都有日志记录，详细记录了谁对您的账户进行了操作，其中客户服务或者任何有权限的人的操作都有日志您可以查询。

GrowingIO 提供的是数据分析的产品，方法论和最佳实践，不做未经客户授权的任何数据交易相关的业务。

{% hint style="info" %}
员工访问数据说明

* 客户所有帐号数据都是机密，并受合同条款的约束。
* 未经客户明确许可，客户服务代表和技术支持人员不得访问客户级数据。
* 访问客户数据时，员工的活动范围仅限于履行工作职责所需的数据。
* 员工不得使用非 GrowingIO 所有或未经 GrowingIO 批准的网络设备访问数据。
* GrowingIO员工需要履行严格的合同保密义务，如果其未能履行这些义务，就可能会被追究法律责任或被终止其与GrowingIO的合同关系。
{% endhint %}

## 符合欧盟《一般数据保护条例》 \(GDPR\)

2018年5月21日起，GrowingIO在Web、Android和iOS SDK中提供了以下的API供开发者调用满足客户网站或移动应用符合欧盟区的《一般数据保护条例》\(GDPR\)。

* GrowingIO SDK提供默认是否开启数据采集的配置项
* GrowingIO SDK提供关闭或开启全局数据采集的接口，开发者可在APP中任何场景时调用该接口
* GrowingIO SDK提供获取该设备的设备ID接口，开发者可配合数据侧提供的接口删除或导出该设备的行为数据

{% tabs %}
{% tab title="Android" %}
初始化配置中关闭数据采集：

```text
disableDataCollect()
```

关闭或开启全局数据采集：

```java
// 停止采集数据 
GrowingIO.getInstance().disableDataCollect(); 
// 开始采集数据 （默认）
GrowingIO.getInstance().enableDataCollect();
```

获取访问用户ID：

```text
GrowingIO.getInstance().getVisitUserId();
```

样例：

```java
GrowingIO.startWithConfiguration(this, new Configuration() 
.disableDataCollect() // 停止采集数据
.useID() 
.trackAllFragments()); 
// 停止采集数据 
GrowingIO.getInstance().disableDataCollect(); 
// 采集数据 
GrowingIO.getInstance().enableDataCollect(); 
// 获取访问用户ID 
GrowingIO.getInstance().getVisitUserId();
```
{% endtab %}

{% tab title="iOS" %}
初始化配置项：无

关闭或开启全局数据采集：

```java
// 停止采集数据
disableDataCollect  
// 开始采集数据 
enableDataCollect
```

获取访问用户ID：

```text
getVisitUserId
```

样例：

```java
// 停止采集数据
[Growing disableDataCollect]; 
// 开始采集数据 （默认）
[Growing enableDataCollect]; 
// 获取设备ID 
NSString *viId = [Growing getVisitUserId];
```
{% endtab %}

{% tab title="Web JS" %}
初始化配置项：无

关闭或开启全局数据采集：

```java
// 停止采集数据，全局配置, 可以放到send之后
window.gio('config',{"dataCollect": true}); 
// 采集数据 (默认)，全局配置, 可以放到send之后
window.gio('config',{"dataCollect": false});
```

获取访问用ID：

```java
window.gio('getVisitUserId'); // 放在send之后
```

样例：

```java
// 停止采集数据，全局配置, 可以放到send之后
window.gio('config',{"dataCollect": true}); 
// 采集数据 (默认)，放在send之后
window.gio('config',{"dataCollect": false}); 
// 获取访问用户ID ，放在send之后
window.gio('getVisitUserId'); // 放在send之后
```
{% endtab %}

{% tab title="小程序" %}
初始化配置项：无

关闭或开启全局数据采集：

```java
//停止采集数据，可以放到send之后
gio('setConfig',{"dataCollect": false}); 
//采集数据 (默认) ，可以放到send之后
gio('setConfig',{"dataCollect": true});
```

获取访问用ID：

```java
window.gio('getVisitUserId'); // 放在send之后
```
{% endtab %}
{% endtabs %}

