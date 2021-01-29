# Web半自动采集浏览事件

半自动浏览事件能够携带用户添加的自定义事件和变量，当元素从屏幕中出现则自动发送事件。

## 特性版本适配

| 无埋点SDK版本 | 特性 |
| :--- | :--- |
| 2.1.43 及以上 | 新增  data-gio-imp-attrs 属性支持 KV 和 json 格式的事件变量配置 |
| 2.1.41 及以上 | 支持驼峰命名埋点事件变量，如事件变量为 fooBar 埋点时为 data-gio-track-foo-bar |
| 2.1.40 及以上 | 支持半自动埋点，仅支持全小写埋点事件变量 |

## 旧版浏览事件介绍

集成无埋点 SDK 后，GIO 使用事件类型 **imp**（impression）采集用户浏览事件。

它的采集逻辑为 DOM 初始化完毕后，将发送 imp 事件。

{% hint style="info" %}
1. 当 DOM 初始化完毕后，会将 DOM 中的所有容器元素发送 imp 事件。
2. 自动浏览事件对于元素的可见性不作要求，即元素出现在 DOM 中就会发送 imp 事件，而不是出现在可视区域中。
{% endhint %}

综上，虽然 SDK 能够自动采集每个元素的浏览事件，但是有以下弊端：

* imp 事件的数量较多
* 无法准确的在元素出现在在可视区时触发
* 想自定义添加一些自定义变量，无法添加

## 新版半自动浏览事件介绍

新版方案：用户标记一个元素并提供自定义事件和变量，SDK 负责监控，当此元素出现在可视区域中时发送用户配置的自定义事件和变量。

新版用户浏览事件半自动究竟指什么？

1. 不再全量采集所有 元素的浏览事件，改为只采集用户主动标记的元素。事件类型使用自定义事件类型 **cstm**（custom），不再使用 **imp** （impression）。**需要用户在代码中埋点并且在官网配置自定义事件和变量。**
2. **半自动**：**指用户提供元素的自定义事件和变量内容，SDK 根据当前 元素是否在屏幕上可见，自动发送一个自定义事件。**即：需要用户标记元素并且提供自定义事件和变量，SDK 在元素出现在屏幕上时自动发送，不同于 track 接口发送的 cstm 事件，调用即发送。

下面我们将从两个方面介绍此方案。

### 1. 标记元素并设置自定义事件和变量

在旧版无埋点 SDK 中，如果想查看某个广告位的具体某个商品的曝光次数，通过圈选广告位的元素的 imp 事件是无法做到的，仍需要您埋点自定义事件。

在埋点元素曝光时，开发人员需要对元素在当前屏幕上的可见性做逻辑判断，需要监控元素是否在可视区域中，有一定代码实施难度。

此方案将监控元素的可见和埋点的触发时机交给 GIO SDK ， 开发者只需要将自定义事件的变量传递给 SDK 即可。

### 2. 元素的浏览事件相对于旧版更准

对于用户主动标记 imp 采集的元素，相对于旧版本自动采集会更加准确，我们举例以下场景来说明。

**场景示例：列表元素的展现统计**

![imp&#x573A;&#x666F;](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LsFN-kH_I1FhypMMhpC-LsGIgGsbAd0wdRHzc6Himage.png)

**旧版本：**

GIO 推荐广告位在DOM的最底部，需要用户滑动才能看到，但是页面初始化的时候绘制，只是当前屏幕不可见。

旧版本中只会在DOM初始化完成时发送一次 imp 事件。

**新版本：**

随着用户的滚动，元素进入屏幕则触发自动埋点事件。

新版本浏览事件的统计更加准确，更符合业务场景。

### 3. 提升用户浏览事件采集的性能

旧版本中，无埋点 SDK 将自动采集所有元素的信息，最终分析时不会分析所有 元素，在网站性能、用户流量上都是一种浪费。

新版本中，SDK 非全量采集所有 DOM中 的元素，只采集用户配置的元素，性能有较大提升。

## 重要配置

{% hint style="info" %}
注意事项

* 注意参数是否合法，与埋点 API 一样，eventID 和事件级变量 JSONObject 都有参数限制要求。
* 在元素展示前调用GIO API，GIO 负责监听元素展示并触发事件，半自动化 IMP 方案 SDK 上传的数据类型为 cstm ，和自定义事件是同种类型，所以**需要您在官网新建对应的事件类型和变量，并且强烈建议使用数据校验工具验证埋点事件。**
* 触发 SDK 自动采集时机： 元素从当前屏幕上不可见到可见。
* 对于被追踪元素上方有其它元素遮挡的情况 ，GrowingIO 仍可能发送该元素的展示事件 （适配这种case会消耗巨大性能，暂时不兼容）。
{% endhint %}

### 标记半自动化采集元素

使用此方法标记元素的浏览时，请使用 WebDebugger 插件验证 cstm 事件。

```markup
<body>
    <div>
        <h2 data-gio-imp-track='testImp' 
        data-gio-track-foo='bar' 
        data-gio-track-Baz='QUX'
        >标记元素并带上两个事件变量</h2>
    </div>
 </body>
```

以上示例相当于在用户元素出现在可视区域时，我们会对应的执行以下对应的API调用。

```markup
gio('track', 'testImp', { foo: 'bar', baz: 'QUX'})
```

### 通过 data-gio-imp-attrs 配置事件属性

原来利用 **data-gio-track-xxx** 的方式配置的埋点事件变量会被统一转化为小写，与定义的事件变量的大小写不同，导致数据无法统计。为解决这一问题，增加了 **data-gio-imp-attrs** 配置方式，支持更加丰富灵活的配置规则。

{% hint style="warning" %}
注意这两种事件变量配置方式不能同时使用。
{% endhint %}

其用法如下：

```markup
<body>
    <div>
        <h2 data-gio-imp-track='testImp' 
        data-gio-imp-attrs='foo:bar,BAZ:QUX,Empty:'>
        标记元素并带上三个事件变量</h2>
    </div>
</body>
```

以上示例相当于在用户元素出现在可视区域时，我们会对应的执行以下对应的API调用。

```markup
// 大小写被原样保留
gio('track', 'testImp', { foo: 'bar', BAZ: 'QUX', Empty:''}) 
```

{% hint style="info" %}
**data-gio-imp-attrs** 的配置格式为 'Key1:Value1,Key2:Value2'  的字符串，即通过英文冒号\(:\) 分割键和值，通过英文逗号\(,\) 分割不同的键值对。

可以在初始化 SDK 的时候通过配置项 **`impAttrSeparator`**指定其他分割符。请注意分隔符不要指定为英文冒号\(:\)，因为这是键和值的分隔符。

```markup
window.gio('init','your projectID', {
    manualImp: true,
    impAttrSeparator: ';'
 })
// 或者
window.gio('config', {
    manualImp: true,
    impAttrSeparator: '|'
})
```
{% endhint %}

data-gio-imp-attrs 还支持指定 JSON 字符串来配置事件变量，当 value 中包含英文冒号`:` 时可以使用着各种方式，其格式如下：

```markup
<body>
    <div>
        <h2 data-gio-imp-track='testImp' 
        data-gio-imp-attrs='{"foo":"bar:Bar:BAR","BAZ":"QUX,ABC","Empty":""}'>
        标记元素并带上三个事件变量</h2>
    </div>
 </body>
```

```markup
// 大小写被原样保留
gio('track', 'testImp', { foo: 'bar:Bar:BAR', BAZ: 'QUX,ABC', Empty:''}) 
```

### 配置采集开关

默认采集关闭，可以在初始化时打开。

```markup
window.gio('init','your projectID', {
    manualImp: true
 })
```

或者使用以下配置方式打开。

```markup
window.gio('config', {
    manualImp: true
})
```

## 常见问题

#### 1. 半自动方案中，元素是否是完全可见的时候，SDK才会发送事件？

元素任意部分可见时就自动触发埋点事件。

#### 2. 半自动方案中，当元素内容发送改变，会发送事件吗？

当元素内容发生变化，不会发送曝光cstm事件。

