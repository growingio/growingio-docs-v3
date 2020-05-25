---
description: 1.x 及其以下 SDK 升级 2.x 以上 SDK 需要遵循文档升级，有重大更新。
---

# 1.x Android SDK 升级指导

{% hint style="danger" %}
升级到SDK 2.x前，请务必联系客服协助您完成后台配置的升级。
{% endhint %}

本文旨在帮助您从 1.x 版本无缝升级至 2.x 版本，由于两个版本的诸多接口、方法、字段含义均有较大变动，因此建议您在升级前一定参照本文完成必要的实施工作。

## 1. 重新集成SDK

请参考Android [无埋点SDK](auto-android-sdk.md)。

建议您在开发中，使用ugMode或Mobile Debugger校验GrowingIO SDK的数据是否正常上传，其中开启DebugMode的方式见调试查看发送数据日志。

## 2. 迁移用户属性字段（CS字段）

如果您未做用户属性字段上传，请忽略此部分。

用户属性字段（简称CS字段）是 1.x 版本的概念，升级至 2.x 版本后：

* CS1字段，会强制命名为“登陆用户ID”，并且上传接口与其他变量不同。
* CS2-10字段，会迁移至“应用级变量”，应用级变量与CS字段的使用方式无任何区别。
* CS11-20字段，会迁移至[用户变量](android-sdk-api/customize-api.md#2-qing-chu-deng-lu-yong-hu-idclearuserid)。两者的区别主要在于：用户变量支持自定义的归因方式。

### 上传接口

{% tabs %}
{% tab title="2.x版本方法格式" %}
对于CS1字段，也就是登录用户ID，请使用以下方法：

```java
// 设置登录用户ID API
GrowingIO.getInstance().setUserId(String userId);
​
// 清除登录用户ID API
GrowingIO.getInstance().clearUserId();
```

对于应用级变量，也就是1.x版本中的CS2-CS10，请使用以下方法：

```java
GrowingIO.setAppVariable(JSONObject variables)
GrowingIO.setAppVariable(String key, Number variable)
GrowingIO.setAppVariable(String key, String variable)
GrowingIO.setAppVariable(String key, Boolean variable)
```

对于用户变量，也就是1.x版本中的CS11-CS20，请使用以下方法：

```java
GrowingIO gio = GrowingIO.getInstance();
gio.setPeopleVariable(String key, String value);
gio.setPeopleVariable(String key, Number value);
gio.setPeopleVariable(String key, Boolean value);
gio.setPeopleVariable(JSONObject peopleVariables);// 多个变量，可组合为一个JSON对象peopleVariables传入
```
{% endtab %}

{% tab title="1.x版本方法格式" %}
```java
GrowingIO growingIO = GrowingIO.getInstance();
    growingIO.setCS1("user_id", "100324");
    growingIO.setCS2("company_id", "943123");
    growingIO.setCS3("user_name", "张溪梦");
```
{% endtab %}
{% endtabs %}

### GrowingIO后台配置

2.x版本取消了应用级变量的配置，但如果您在1.x中已配置，且进行了数据迁移操作，2.x将为您保留此部分迁移数据在维度选择时使用。

如需新增用户变量字段请在“**数据中心 &gt; 数据管理 &gt; 变量 &gt; 用户变量**”，下的**登录用户变量**页签下配置。配置方式请参考[用户变量](../../../product-manual/data-center/data-management/user/)。

## 3. 迁移页面属性字段（PS字段）

如果您未做页面属性字段上传，请忽略此部分。

类似于用户属性字段，在 2.x 版本中，页面属性字段被迁移到了“[页面级变量](../../../introduction/data-definition/pagevar.md)”。与页面属性字段不同的是，**页面级变量相当于过去的 PS 字段，不再存在过去的 PG 字段**。

### 上传接口

{% tabs %}
{% tab title="2.x版本方法格式" %}
```java
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
```
{% endtab %}

{% tab title="1.x版本方法格式" %}
```java
GrowingIO.setPageGroup(Activity activity, String name); 
GrowingIO.setPS1(Activity activity, String property); 
GrowingIO.setPS2(Activity activity, String property);
```
{% endtab %}
{% endtabs %}

### GrowingIOh后台配置

您需要在 **“数据中心 &gt; 数据管理 &gt; 事件变量 ”** 的页面级变量中进行配置。配置方式请参考[创建页面级变量](../../api-reference/project-manage/create-pvar.md)。

## 4. 迁移自定义事件（埋点事件）

如果您未做自定义事件的上传，请忽略此部分。

2.x 版本的自定义事件，在概念上与 1.x 版本无任何区别，但上传接口和配置方式上有以下变更。

### 上传接口

{% tabs %}
{% tab title="2.x版本方法格式" %}
```java
GrowingIO gio = GrowingIO.getInstance();
gio.track(String eventId);
gio.track(String eventId, Number eventNumber);
gio.track(String eventId, Number eventNumber, JSONObject eventLevelVariables);
gio.track(String eventId, JSONObject eventLevelVariables);
```
{% endtab %}

{% tab title="1.x版本方法格式" %}
```java
public class GrowingIO {
    public GrowingIO track(String eventName, JSONObject properties)
}
```
{% endtab %}
{% endtabs %}

### GrowingIO后台配置

自定义事件的配置，您需要在 **“数据中心 &gt; 数据管理 &gt; 埋点事件 ”** 中进行配置。配置方式请参考[埋点事件管理](../../../product-manual/data-center/data-management/manual.md)。

也是在**“管理” - “自定义事件和变量”** 页面中的 **“自定义事件” Tab 页**。但您会发现，除了 “自定义事件” Tab 页外，现在还提供了 “事件级变量” Tab 页来专门管理事件级变量的配置。您只需在 “事件级变量” Tab 页完成事件级变量的配置，然后在新建自定义事件时，从已经建好的事件级变量中选择即可。

## 5. 数据迁移

进行事件及属性迁移后，会根据新方法采集新产生的数据，旧数据依然可使用原有的属性值进行查看，如您想使用迁移后的属性值平滑的查看新旧数据，请您发起数据迁移工单。

## 6. 数据校验

在完成了上述代码实施和配置后，我们当然需要对数据是否成功上传进行校验。点击查看 [GrowingIO Mobile Debugger 的安装和使用](../../debugging/mobile-debugger.md)。

