# 页面级变量

在开始用户变量配置与定义之前，推荐您阅读[页面事件及属性](../datamodel/eventmodel/autotrack-event/page-events-and-properties.md)文档，了解 GrowingIO 如何标记页面。

## 页面级变量的持久性范围

页面级变量的持久性范围仅在当前页面内，随着用户操作行为导致页面变化，保存在页面级变量中的值就宣告失效。也就是说，页面级变量作为维度，只能用于分解它们标记的页面上的无埋点及埋点指标。

## 页面级变量的使用场景

页面级变量可以用于下述场景

* 各个不同板块页面的用户访问情况分析。在这种场景下，使用页面级变量保存页面所属板块的名称。
* 各个不同子站点的用户访问情况分析。在这种场景下，使用页面级变量保存页面所属子站点的名称。
* 各个不同类型页面的用户访问情况分析。在这种场景下，使用页面级变量保存页面所属的类型名称。例如功能引导页面，购物流程页面等。

**分析场景示例**

{% tabs %}
{% tab title="例一：页面级变量作为维度" %}
常用于商品详情页、搜索结果页等由同一个模板\(类\)填充的多个页面，以便区分这些页面间不同的业务含义。例如商品详情页可用页面级变量来标记：商品名称、商品 ID、品类、价格等信息。如图示：

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28223%29.png)

在按上图所示，为所有商品详情页打上页面级变量的标签后，在 GrowingIO 后台，上述 5 个页面级变量均会成为“维度”，可在各分析图表、工具中选用。例如在事件分析中，即可按商品 ID 来分解页面浏览量：

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28129%29.png)
{% endtab %}

{% tab title="例二：页面级变量作为页面标签" %}
**场景**：

在某门户网站里存在多个频道（新闻、娱乐等），用户可能会浏览新闻类页面，也可能会浏览娱乐类页面。

**使用**：

GrowingIO 推荐设置一个页面级变量来保存页面的类型信息。我们为所有的新闻类页面打上“频道=新闻”这样一个标签，然后在 GrowingIO 后台即可按频道来分解用户的浏览行为。

**代码示例**：

> 网站代码

`gio(“page.set”, “channel”, “新闻”);`

> Android代码

`GrowingIO.setPageVariable(Activity activity, ”channel”, “新闻”);`

> iOS代码

`[Growing setPageVariableWithKey:@"channel" andStringValue:@"新闻" toViewController:myViewController];`
{% endtab %}
{% endtabs %}

## 页面变量的配置和上传 <a id="zi-ding-yi-bian-liang-de-pei-zhi-he-shang-chuan"></a>

### **第一步：在 “事件和变量”中完成配置** <a id="di-yi-bu-zai-shi-jian-he-bian-liang-zhong-wan-cheng-pei-zhi"></a>

参考上述场景示例，配合梳理业务需求并完成“指标+维度”的设计，确认需要将哪些变量设置为页面级变量，请勿直接开始代码的部署，需要先到 GrowingIO 要求先在打点管理的界面上进行变量的声明操作。

配置方式参考[事件变量](../../product-manual/data-center/data-management/event.md)。

### **第二步：代码部署** <a id="di-er-bu-dai-ma-bu-shu"></a>

完成了配置后，即可在代码中完成以上设计的 “自定义事件和变量” 的部署。具体的说，就是调用 GrowingIO 提供的 API 接口，上传数据。

* [JS 接口文档​](../../kai-fa-zhe-wen-dang/sdkintegrated/web-js-sdk/web-sdk-api/)
* ​[Android 接口文档​](../../kai-fa-zhe-wen-dang/sdkintegrated/android-sdk/android-sdk-api/)
* ​[iOS 接口文档​](../../kai-fa-zhe-wen-dang/sdkintegrated/ios-sdk/ios-sdk-api/)
* [​小程序、小游戏以及内嵌页 SDK​](../../kai-fa-zhe-wen-dang/sdkintegrated/other-sdk/customize-api.md)

API中给出了页面级变量的上传方式。

