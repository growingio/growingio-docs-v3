# Web JS SDK升级指导

{% hint style="danger" %}
如果您目前希望从 1.x 版本升级至 2.x 版本，请务必联系 GrowingIO 对接人，我们需要在后台为你开启 2.x 版本所对应的功能权限。

如果直接重新集成2.x版本SDK，而后台对应功能权限未开启的话，可能会造成数据丢失问题。
{% endhint %}

## 1. 重新集成SDK

请参考[集成SDK（2.x）](latest-jssdk.md#1-tian-jia-gen-zong-dai-ma)

## 2. 迁移用户属性字段

{% hint style="info" %}
如果您在旧版本1.x版本未做用户属性字段上传，请忽略此部分。
{% endhint %}

用户属性字段（简称CS字段）是 1.x 版本的概念，升级至 2.x 版本后：

* CS1字段，会强制命名为“登陆用户ID”，并且上传接口与其他变量不同。
* CS2-10字段，会迁移至“应用级变量”，应用级变量与CS字段的使用方式无任何区别。
* CS11-20字段，会迁移至“用户变量“。两者的区别主要在于：用户变量支持自定义的归因方式。

### 2.1 上传接口

2.x 版本中的上传用户变量方法有较大改动，不再将 `'setCSn'` 这个字段作为参数，方法中只需写入用户变量的 key - value 对。

{% tabs %}
{% tab title="2.x版本方法格式" %}
对于 CS1 字段，也就是登陆用户ID，请使用以下方法：

```text
// 设置登录用户ID
gio('setUserId', userId);
​
// 清除登录用户ID
gio('clearUserId');
```

对于应用级变量，也就是 1.x 版本中的 CS2 - CS10，请使用以下方法：

```text
gio(‘app.set’, key, value) // 单个变量
gio('app.set', appLevelVariables) // 多个变量，可组合为一个JSON对象appLevelVariables传入
```

对于用户变量，也就是 1.x 版本中的 CS11 - CS20，请使用以下方法：

```text
gio('people.set', key, value); // 单个变量
gio('people.set', peopleVariables); // 多个变量，可组合为一个JSON对象peopleVariables传入
```
{% endtab %}

{% tab title="1.x版本方法格式" %}
```text
_vds.push(['setCS1', 'CS1的key', 'CS1的value']);
_vds.push(['setCS2', 'CS2的key', 'CS2的value']);
_vds.push(['setCS3', 'CS3的key', 'CS3的value']);
...
_vds.push(['setCS10', 'CS10的key', 'CS10的value']);
```
{% endtab %}
{% endtabs %}

### 2.2 GrowingIO后台配置

2.x版本取消了应用级变量的配置，但如果您在1.x中已配置，且进行了数据迁移操作，2.x将为您保留此部分迁移数据在维度选择时使用。

如需新增用户变量字段请在“**数据中心 &gt; 数据管理 &gt; 变量 &gt; 用户变量**”，下的**登录用户变量**页签下配置。配置方式请参考[用户变量](../../../product-manual/data-center/data-management/user/)。

## 3. 迁移页面属性字段

类似于用户属性字段，在 2.x 版本中，页面属性字段被迁移到了“页面级变量”。与页面属性字段不同的是，**页面级变量相当于过去的 PS 字段，不再存在过去的 PG 字段**。

### 3.1 上传接口

{% tabs %}
{% tab title="2.x版本方法格式" %}
```javascript
gio('page.set', key, value);
gio('page.set', pageLevelVariables); //多个变量，可组合为一个对象传入
```
{% endtab %}

{% tab title="1.x版本方法格式" %}
```javascript
_vds.push([’setPageGroup‘, ‘PageGroup 的名称’];
_vds.push([‘setPS1’, ‘PS1 的值’]);
_vds.push([‘setPS2’, ‘PS2 的值’]);
_vds.push([‘setPS3’, ‘PS1 的值’]);
```
{% endtab %}
{% endtabs %}

### 3.2 GrowingIO后台配置

您需要在“**数据中心 &gt; 数据管理 &gt; 变量 &gt; 事件变量**”，下的**页面级变量**页签下进行配置。

## 4. 迁移自定义事件（埋点事件）

{% hint style="info" %}
如果您在旧版本1.x版本未做自定义事件的上传，请忽略此部分。
{% endhint %}

2.x 版本的自定义事件，在概念上与 1.x 版本无任何区别，但上传接口和配置方式上有以下变更。

### 4.1 上传接口

{% tabs %}
{% tab title="2.x版本方法格式" %}
```java
gio('track', eventId);
gio('track', eventId, number);
gio('track', eventId, eventLevelVariables);
gio('track', eventId, number, eventLevelVariables);
```
{% endtab %}

{% tab title="1.x版本方法格式" %}
```java
window._vds.track(event_name, properties)
```
{% endtab %}
{% endtabs %}

### 4.2 GrowingIO后台配置

您需要在“**数据中心 &gt; 数据管理 &gt; 变量 &gt; 事件变量**”，下的**事件级变量**页签下配置事件变量。

在在“**数据中心 &gt; 数据管理 &gt; 事件 &gt; 埋点事件**”，下新建自定义事件，并选择已创建好的事件级变量。

## 5. 数据迁移

进行事件及属性迁移后，会根据新方法采集新产生的数据，旧数据依然可使用原有的属性值进行查看，如您想使用迁移后的属性值平滑的查看新旧数据，请您发起数据迁移工单。

## 6. 数据校验

在完成了上述代码实施和配置后，我们当然需要对数据是否成功上传进行校验。校验工作分为两步完成。GrowingIO 提供了 SDK debug 模式以及 debug 工具，来帮助您完成数据的校验。

\*\*\*\*[**点击查看 GrowingIO Web Debugger 的安装和使用**](../../debugging/web-debugger.md)。

