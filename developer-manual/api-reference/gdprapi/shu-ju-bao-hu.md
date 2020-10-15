# 数据保护

2018年5月21日起，GrowingIO在Web、Android和iOS SDK中提供了以下的API供开发者调用满足客户网站或移动应用符合欧盟区的《一般数据保护条例》\(GDPR\)。

* GrowingIO SDK提供默认是否开启数据采集的配置项
* GrowingIO SDK提供关闭或开启全局数据采集的接口，开发者可在APP中任何场景时调用该接口
* GrowingIO SDK提供获取该设备的设备ID接口，开发者可配合数据侧提供的接口删除或导出该设备的行为数据

{% tabs %}
{% tab title="Web JS" %}
初始化配置项：无

关闭或开启全局数据采集：

```java
// 停止采集数据，全局配置, 请在调用gio('send')之前调用
window.gio('config',{"dataCollect": true}); 
// 采集数据 (默认)，全局配置, 请在调用gio('send')之前调用
window.gio('config',{"dataCollect": false});
```

获取访问用ID：

```java
window.gio('getVisitUserId'); // 请在调用gio('send')之前调用
```

样例：

```java
// 停止采集数据
window.gio('config',{"dataCollect": true}); 
// 采集数据 (默认)
window.gio('config',{"dataCollect": false}); 
// 获取访问用户ID 
window.gio('getVisitUserId');
```
{% endtab %}

{% tab title="Android" %}
初始化配置项中关闭数据采集：

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

```text
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
// 采集数据 （默认）
[Growing enableDataCollect]; 
// 获取设备ID 
NSString *viId = [Growing getVisitUserId];
```
{% endtab %}

{% tab title="小程序" %}
初始化配置项：无

关闭或开启全局数据采集：

```java
//停止采集数据，在gio('init')之后调用
gio('setConfig',{"dataCollect": false}); 
//采集数据 (默认) ，在gio('init')之后调用
gio('setConfig',{"dataCollect": true});
```

获取访问用ID：

```java
window.gio('getVisitorId'); // 在gio('init')之后调用
```
{% endtab %}

{% tab title="内嵌页" %}
初始化配置项：无

关闭或开启全局数据采集：

```java
//停止采集数据，在gio('send')之前调用
gio('setDataCollect', false)
//采集数据 (默认) ，在gio('send')之前调用
gio('setDataCollect', true)
```

获取访问用ID：

```java
gio('getVisitUserId'); // 在gio('send')之前调用
```
{% endtab %}
{% endtabs %}

