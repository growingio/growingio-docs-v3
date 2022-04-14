# 无埋点采集逻辑和高级配置

## 访问数据 <a href="#fang-wen-shu-ju" id="fang-wen-shu-ju"></a>

每次用户打开小程序的时候，发送一条访问事件的消息，对应的数据指标是打开次数。发送数据包含但不限于以下信息：进入页面、进入时间、场景值、来源小程序或 App、设备信息、微信信息、应用版本号。

每次用户关闭小程序的时候，关闭动作包括退出小程序回到微信、退出微信，会发送一条`应用关闭`消息，会根据这个消息来计算应用访问时长。发送数据包含但不限于以下信息：退出页面、退出时间。

## 页面数据 <a href="#ye-mian-shu-ju" id="ye-mian-shu-ju"></a>

每次用户访问一个新的页面，发送一条页面浏览事件的消息，对应的数据意义是页面分析。发送数据包含但不限于以下信息：页面信息、打开时间、页面来源、页面标题、页面级变量。

每次当用户点击转发按钮时，会弹出转发框，这时会发送一条`要转发事件的`消息。这是一个自定义事件，数据包含以下信息：事件时间、所在页面、转发动作来源、转发页面标题和转发页面路径。注意这个事件不代表用户真正转发了消息到聊天里面，而是用户触发了转发动作。如果要跟踪成功转发消息事件，建议在 onShareAppMessage 的 success callback 里面发送一个自定义事件。

## 行为数据

对于用户在页面发生的行为，如果这个行为有绑定事件比如 bindtap，并且在您的小程序里面进行处理，那么 GrowingIO 的小程序 SDK 会自动采集这些事件，发送一条行为事件的消息。目前，我们支持的事件有 tap、longpress、confirm 和 change 事件。

### tap

tap 事件是手指触摸后马上离开时触发的事件。当 wxml 中的 view 绑定了 bindtap 事件以后，在事件处理函数执行的时候，SDK 会自动采集 tap 事件，发送数据包含但不限于以下信息：点击事件时间、事件发生所在页面、点击控件相关信息

代码示例如下：\<view data-title='复仇者联盟3' data-index='1' bindtap='clickMovie'>

```java
<view data-title='复仇者联盟3' data-index='1' bindtap='clickMovie'>
    <image src='IMAGE—URL' mode='aspectFill'/>
    <text>复仇者联盟3</text>
</view>
```

注意这里的 `data-title` 和 `data-index` 属性，因为微信小程序的限制，无法采集到控件的内容和结构数据，所以在小程序 SDK 里面我们采取的是声明式编程，通过在 wxml 文件里面设置 data- 属性，可以给 view 控件添加额外的`内容`和`位置`属性，方便后续在分析时可以按照元素内容和元素位置做分析，对于列表式的组件特别有用和方便。

{% hint style="info" %}
**建议在 View 的控件里面多使用 data-title 和 data-index 属性这种声明式编程方式。**
{% endhint %}

### longpress

longpress 事件是手指触摸后，超过350ms再离开时触发的事件。当 wxml 的 view 绑定了 bindlongpress 事件以后，在事件处理函数执行的时候，SDK 会自动采集 longpress 事件，发送数据包含但不限于以下信息：点击事件时间、事件发生所在页面、点击控件相关信息。

示例代码

```java
<view data-title='复仇者联盟3' data-index='1' bindlongpress='clickMovie'>
  <image src='IMAGE—URL' mode='aspectFill'/>
  <text>复仇者联盟3</text>
</view>
```

注意这里的 `data-title` 和 `data-index` 属性，因为微信小程序的限制，无法采集到控件的内容和结构数据，所以在小程序 SDK 里面我们采取的是声明式编程，通过在 wxml 文件里面设置 data- 属性，可以给 view 控件添加额外的`内容`和`位置`属性，方便后续在分析时可以按照元素内容和元素位置做分析，对于列表式的组件特别有用和方便。

{% hint style="info" %}
**建议在 View 的控件里面多使用 data-title 和 data-index 属性这种声明式编程方式。**
{% endhint %}

### change

change 事件是针对 checkbox、radio、picker-view 这些控件，当选择项发生改变时触发的事件。当 wxml 的 view 绑定了 bindchange 事件以后，在事件处理函数执行的时候，SDK 会自动采集 change 事件，发送数据包含但不限于以下信息：选择事件的发生时间、事件发生所在页面。

如果需要采集内容，需增加 data-growing-track 属性，发送的数据会包含选择项的内容信息。

代码示例

```java
<checkbox-group bindchange='checkboxChange' data-growing-track>
  <label class='checkbox'>
    <checkbox value='GrowingIO' checked='true' /> GrowingIO
  </label>
  <label class='checkbox'>
    <checkbox value='Tencent' checked='false' /> 腾讯小程序分析工具
  </label>
  <label class='checkbox'>
    <checkbox value='Google' checked='false' /> Google Analytics
  </label>
</checkbox-group>
```

{% hint style="info" %}
添加 data-growing-track 属性后，发送的数据会增加 v 字段，其值为选中的值
{% endhint %}

### confirm

confirm 事件是对于 input 和 textarea 控件，当输入完成后触发的事件。当 wxml 的 view 绑定了 bindconfirm 事件以后，在事件处理函数执行的时候，SDK 会自动采集 confirm 事件，发送数据包含但不限于以下信息：输入事件的发生时间、事件发生所在页面。

如果需要采集内容，需增加 data-growing-track 属性，发送的数据会包含选择项的内容信息。

代码示例

```java
<input class='new-todo'
       value='{{ input }}'
       placeholder='Anything here...'
       data-growing-track
       bindconfirm='addTodoHandle'
/>
```

{% hint style="info" %}
添加 data-growing-track 属性后，发送的数据会增加 v 字段，其值为输入的值。
{% endhint %}

{% hint style="danger" %}
**免责声明警告：**

请勿尝试在密码框上标记 data-growing-track 属性进行采集数据，会明文暴露用户填写的密码信息。GrowingIO不承担由此直接或间接产生的数据风险和法律风险。
{% endhint %}

### navigator组件

如果您的小程序使用了navigator组件，想要采集跳转点击事件，需要手动绑定一个空的点击事件，GrowingIO SDK才能实现跳转点击的采集。

```java
<navigator ...>
  <view bindtap="nameForThisClickButton">
     ...
  </view>
</navigator>
```

### 忽略采集标记

对于已经绑定事件的控件，如果希望不采集行为数据，可在控件中增加 data-growing-ignore 属性，忽略该控件的行为数据，例如：

```javascript
<view data-growing-ignore bindtap='clickMovie'>
    <image src='IMAGE—URL' mode='aspectFill'/>
    <text>复仇者联盟3</text>
</view>
```

###

## 设置半自动采集浏览事件

用户标记一个元素并提供埋点事件和事件级变量，SDK负责监控，当此元素出现在可视区域中时发送用户配置的埋点事件和事件级变量。

半自动浏览事件指：

1. 采集用户主动标记的元素，事件类型使用埋点事件类型cstm，需要用户在代码中埋点并且在GrowingIO 平台上数据中心配置埋点事件和事件级变量。
2. 半自动：指提供元素的埋点事件和事件级变量代码，SDK判断当前元素在屏幕上可见时，自动发送一个埋点事件。即：需要标记元素并且提供埋点事件和事件级变量，SDK在元素出现在屏幕上时自动发送，相当于自动生成并调用track接口代码发送cstm事件。

{% hint style="info" %}
注意事项：

* 注意参数是否合法，与埋点 API 一样，eventID （埋点事件标识符)和事件级变量 JSONObject 都有参数限制要求。
* 在元素展示前调用GIO API，GIO 负责监听元素展示并触发事件，半自动化浏览事件SDK 上传的数据类型为 cstm（埋点事件）类型，所以**需要您在官网新建对应的埋点事件和事件级变量，并且强烈建议使用数据校验工具验证埋点事件。**
* 触发 SDK 自动采集时机： 元素从当前屏幕上不可见到可见。
* 对于被追踪元素上方有其它元素遮挡的情况 ，GrowingIO SDK仍可能发送该元素的展示事件 （适配这种case会消耗巨大性能，暂时不兼容）。
{% endhint %}

### 标记半自动采集元素

使用此方法标记元素的浏览时，请在console 日志输出中验证是否发送埋点事件和事件级变量（t = cstm）。

```javascript
<view class="page-section growing_collect_imp" data-gio-imp-track='impTest' data-gio-track-age='18' data-gio-track-name='xxx' id='test_imp'>
  // ......
</view>
```

{% hint style="info" %}
class 中必须加 growing\_collect\_imp 。
{% endhint %}

### 注册监听

在对应页面的 Page.js 文件的`onShow`方法中，调用 `gio('collectImp', this)`

```java
Page({
  // ...
  onShow: function () {
    gio('collectImp', this)
  },
  // ...
})
```

##
