# Web端数据定义

## 圈选准备

GrowingIO 全量采集用户行为数据，你可以通过「圈选」来定义元素和页面，作为数据分析的基础指标。

在没有定义过的情况下，GrowingIO 保留和回溯元素过去 7 天的点击量，页面过去 7 天的浏览量。

{% hint style="info" %}
Hashtag使用说明

如果您的Web页面URL使用了Hashtag，请在加载SDK进行预先配置，请参考[Web JS SDK](../../../../developer-manual/sdkintegrated/web-js-sdk/)。
{% endhint %}

{% hint style="success" %}
URL解读

URL**示意：**www.xxx.com**/**12345/678/123**?**id=1\&ig=2

**拆分：**域名**/**路径**?**查询条件

**即** www.xxx.com **为域名，**/12345/678/123 **为路径，**?id=1\&ig=2 **为查询条件**
{% endhint %}

![](https://docs.growingio.com/.gitbook/assets/9412f46a-d87c-41ef-9ee6-9e6e408f4c6a-12626-00000bcf696b73c5\_tmp.jpg)

## [iframe圈选](web/iframe-quan-xuan.md) <a href="#1-kai-shi-quan-xuan" id="1-kai-shi-quan-xuan"></a>

## [Chrome插件圈选](web.md#3-qi-ta-te-shu-qing-kuang) <a href="#3-qi-ta-te-shu-qing-kuang" id="3-qi-ta-te-shu-qing-kuang"></a>

## 常见问题 <a href="#2-chang-jian-wen-ti-faq" id="2-chang-jian-wen-ti-faq"></a>

### **1. 如何定义「一组相似元素之和」？** <a href="#21-ru-he-ding-yi-yi-zu-xiang-si-yuan-su-zhi-he" id="21-ru-he-ding-yi-yi-zu-xiang-si-yuan-su-zhi-he"></a>

如果该元素有同类元素，不限定所有的限定条件，即是统计一组同类元素之和的数据。

### **2. 对于已定义过的元素，更改定义规则后，应该如何保存？** <a href="#22-dui-yu-yi-ding-yi-guo-de-yuan-su-geng-gai-ding-yi-gui-ze-hou-ying-gai-ru-he-bao-cun" id="22-dui-yu-yi-ding-yi-guo-de-yuan-su-geng-gai-ding-yi-gui-ze-hou-ying-gai-ru-he-bao-cun"></a>

更改新的规则后，如果原有数据仍然想继续统计，请选择“另存为”来定义新的规则。

### **3. 如何进行文本「内容」的模糊匹配？** <a href="#23-ru-he-jin-hang-wen-ben-nei-rong-de-mo-hu-pi-pei" id="23-ru-he-jin-hang-wen-ben-nei-rong-de-mo-hu-pi-pei"></a>

「限定内容」的情况下，将鼠标移动到「内容」的右边，可以看到一个小铅笔，点击小铅笔后，便打开了文本和模式编辑弹窗。默认为精准匹配，即「限定内容为xxx」，若改成模糊匹配，则意义是「限定内容包含xxx」。 保存元素规则后，将按照新的规则进行统计，如果原有数据仍然想继续统计，请选择「另存为」。

![](https://docs.growingio.com/.gitbook/assets/223435.jpg)

### **4. 月21日迭代后，新旧版本规则对应关系** <a href="#24-3-yue-21-ri-die-dai-hou-xin-jiu-ban-ben-gui-ze-dui-ying-guan-xi" id="24-3-yue-21-ri-die-dai-hou-xin-jiu-ban-ben-gui-ze-dui-ying-guan-xi"></a>

![](https://docs.growingio.com/.gitbook/assets/ping-mu-kuai-zhao-20180319-shang-wu-11.24.51.png)

### 5. 不能圈选的可能原因以及对应方法（web）

#### **不能圈选的原因**

不能圈选的原因包含了，但不仅限于：

* 元素包含属性：data-growing-ignore， 因此不可以被圈选。如果需要圈选该元素，请去除该属性。
* 密码框不支持被圈选。
* 元素已经被圈选，因此不能被重复圈选。
* 元素是叶子节点，无文本内容，且元素的占屏幕面积超过 50% ，因此不能被圈选。如果需要圈选该元素，请添加 data-growing-circle 属性。
* 元素所在的 Dom 嵌套层数过多，不在倒数后两层；或者层数符合但是没有实际内容，因此不能被圈选。

#### **data-growing-circle 属性的使用帮助：**

元素是叶子节点，无文本内容，且元素的占屏幕面积超过 50% ，因此不能被圈选。如果需要圈选该元素，请添加 data-growing-circle 属性。例如 ：

```
 <div id= "d1" style="border: 1px solid black; width: 80%; height: 80%"></div>
```

本来不可以圈选。在添加 data-growing-circle 属性后可以圈选：

```
<div  id= "d1" style="border: 1px solid black; width: 80%; height: 80%" data-growing-circle></div>
```

### **6. 如果我的页面改版，现在标记的指标是不是需要重新定义？**

改版后，变化的元素需要重新圈选。

### **7. 什么时候选择手动圈选，什么时候选择自动圈选？**

使用自动模式可以很方便快捷地圈选某些元素。但是有些时候由于页面框架的实现方式，自动圈选会圈选相似的模块进来，从而造成数据误差，所以必要时可以切换手动圈选来解决问题。

### **8. H5 怎么圈选？**

GrowingIO 可以统计原生应用中的 H5 页面和 H5 做成的应用。

* 原生应用中的 H5 页面，以及嵌在应用中的 H5，请参考 [App端数据定义](app.md)。
* 用 H5 做的应用请参考[ Web端数据定义](web.md)。 &#x20;

### **9. 为什么圈选的元素只有点击量，没有浏览量？**

1. 如果被圈选元素是 a, button, input，img，并且在倒数两层以下，只统计点击量，不统计浏览量。
2. 如果用户使用的是 IE8 及以下的 IE 浏览器版本，无法统计浏览量 ，只统计点击量。

### **10. 为什么圈选的元素只有浏览量，没有点击量？**

1. 可能真的是没有点击量。
2. 可能选中的是纯文本等没有带超链接可点击的元素。

### **11. 当页面带查询条件的时候，开关查询条件，数据为什么没有变化？**

当圈选元素所在的页面带查询条件的时候，此时圈选框内展示的数据是不带查询条件的数据。保存带查询条件指标后，指标不会回溯数据，会从保存后开始统计数据。

### **12. Web 圈选时候页面加载不完全？错位？**

部分浏览器会有兼容性问题，推荐使用 Chrome 浏览器。

### **13. Web 端已经装了 SDK，现在不能进行圈选。**

1. 有可能是工程师没有成功加载 JS；
2. 可能是该网站禁止了 iframe 的加载，请联系工程师修改配置；
3. 可能是工程师加载 js 代码时的项目 ID 填写有误（项目 ID 没有空格）；
4. 有可能复写 window 对象：可视化圈选时候，必须要保证您的网站与 GrowingIO 平台之间的通信。如果 window.top, window.parent, window.name, window.location 被复写，将导致无法圈选。

如果出于某些原因你不能改变 iframe 或 window 相关设置，建议使用[插件进行圈选](web/chrome-cha-jian-an-zhuang-bu-zhou.md) 。

### **14. 能否在 iframe 中进行圈选？**

如果 iFrame 中的内容集成了 GrowingIO 的代码就可以圈选，否则无法圈选。 GrowingIO 是使用 iframe 来加载目标网页进行可视化定义的。如果目标网站禁止了 iframe 加载，就无法正常定义标签，当点击某个按钮的时候，页面无法发生跳转且命令行显示：

```
Refused to display '**' in a frame because it set 'X-Frame-Options' to 'SAMEORIGIN'.
```

此时只允许同个顶级域名加载，所以需要设置http响应头允许 iframe 加载。

如果你的网站使用https协议，需向响应头添加配置

```
Content-Security-Policy: frame-ancestors 'self' https://www.growingio.com
X-Frame-Options: Allow-From https://www.growingio.com
```

如果你的网站使用http协议，需向响应头添加配置

```
Content-Security-Policy: frame-ancestors 'self' http://www.growingio.com
X-Frame-Options: Allow-From http://www.growingio.com
```

由于 Chrome 浏览器已经不再支持 X-Frame-Options 配置项，如果你只需在 Chrome 浏览器中进行圈选，建议通过浏览器检查后，只给 Chrome 请求的响应头添加配置

```
Content-Security-Policy: frame-ancestors 'self' http://www.growingio.com https://www.growingio.com
```

### **15. 在 web 圈选的时候，为什么有时候会一下圈出一组同类元素，有办法区分开么？**

GrowingIO 根据您网站 HTML 结构识别和定义页面上的元素。有的时候网站上的 HTML 标签写法完全相同，呈现在页面上的几个同类元素，可能 HTML 代码完全相同。此时 GrowingIO 采集、圈选数据时无法区分开。我们通过 HTML 标签的 id 和 class 来区分元素，这种情况下您可以在需要区分的标签 class 中添加一些字符串用于区分。

**仍有疑问？请参考**[**常见问题－圈选部分**](../../../../product-faq/quanxuan.md)
