# 集成最新SDK

## 准备条件

获取项目ID，获取方法请参考"项目管理 &gt; 项目概览 &gt; [查看项目基本信息](../../../product-manual/xiang-mu-guan-li/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

## 1. 添加跟踪代码

请将以下的页面代码放置到需要分析的页面中的 &lt;head&gt; 和 &lt;/head&gt; 标签之间，即可完成最新 Web JS SDK 页面代码的添加。

{% hint style="warning" %}
请注意使用 **您创建Web应用所在项目的项目ID** 替换代码中的 **your projectId** 。
{% endhint %}

```javascript
<!-- GrowingIO Analytics code version 2.1 -->
<!-- Copyright 2015-2017 GrowingIO, Inc. More info available at http://www.growingio.com -->
<script type='text/javascript'>
!function(e,t,n,g,i){e[i]=e[i]||function(){(e[i].q=e[i].q||[]).push(arguments)},n=t.createElement("script"),tag=t.getElementsByTagName("script")[0],n.async=1,n.src=('https:'==document.location.protocol?'https://':'http://')+g,tag.parentNode.insertBefore(n,tag)}(window,document,"script","assets.giocdn.com/2.1/gio.js","gio");
  gio('init', 'your projectId', {});
  ​
  //custom page code begin here
​​
  //custom page code end here
​
  gio('send');

</script>
<!-- End GrowingIO Analytics code version: 2.1 -->
```

## 2. 配置系统变量

设置系统变量的代码请插入上述追踪代码的 custom page code 部分，在 init 和 send 中间。

### 1. hashtag系统变量

GrowingIO默认不会把 hashtag 识别成页面 URL 的一部分。对于使用 hashtag 进行页面跳转的单页面网站应用来说，可以启用 hashtag 作为标识页面的一部分:

```javascript
gio('config', {'hashtag':true}); //放在init和send之间
```

以此监听 hashtag 的变化，并采集不同页面的数据。每次 hashtag 的改变都会触发一次PV，hashtag 的信息也会记录在页面URL中。

### 2. imp系统变量

除点击、修改、提交等用户行为数据的采集，GrowingIO 还默认开启元素浏览量\(简称imp\)的无埋点采集。对于内容基本固定的网站，可以直接禁用元素浏览量采集。

```javascript
gio('config', {'imp':false}); //放在init和send之间
```

> 系统变量也可以在init进行配置，代码示例：

```text
gio('init', 'your projectId', {
  'imp':false，
  'hashtag':true
});
```

## 3. 高级设置

高级设置可以帮助你更自如地进行圈选操作，请将高级设置插入你Web应用的HTML代码中。

### 1. 设置采集容器（data-growing-container）

GrowingIO默认视button或a标签为可圈选容器。同时，默认可以圈选页面dom上所有叶子结点和叶子结点的上一级父节点。

当您想以button和a标签以外的标签作为容器进行圈选时您可以为期望圈选的容器标签添加data-growing-container 属性，圈选时即可圈到这个容器。容器内子标签的点击都会汇总到容器中。

代码示例：

div作为容器标签时，以id=1的div作为容器进行圈选的代码示例：

```aspnet
<div id="1" data-growing-container>
  <div id="2">
    <h1 id="3">商品名称</h1>
  </div>
  <div id="4">
    <div id="5">商品图片</div>
  </div>
  <div id="6">
    <div id="7">商品描述</div>
  </div>
</div>
```

更多容器信息规则，请参考第三节：[容器规则](https://sishen.gitbooks.io/gio-js-book/5/3.html)。

### 2. 设置采集文本信息（data-growing-title）

对于一些图片或者区块，可以通过设置title或者data-growing-title属性来设置采集点文本，其中title的优先级高于data-growing-title。

代码示例：

```aspnet
<li data-growing-title="上一页" class="ant-pagination-disabled ant-pagination-prev">
  <a></a>
</li>
```

这时，采集到的li节点的内容就是“上一页”。

更多的文本信息规则，请参考[第4节：What\(内容\)](https://sishen.gitbooks.io/gio-js-book/dom/4what.html)和[第1节：内容规则](https://sishen.gitbooks.io/gio-js-book/5/1.html)。

### 3. 设置采集位置信息（data-growing-idx）

除了内容以外，元素在列表里所在位置在某些场景下也是非常重要的信息，比如对于推荐广告位而言，我们是希望知道哪个位置的点击率最高。GrowingIO SDK 会自动识别列表元素，并附带上元素在列表里的位置。

LI 标签、TR 标签、DL 标签，会被自动识别为列表元素，列表内所有元素结点都会附带上位置信息。其他标签默认并不会带有位置信息，比如一些用 DIV 标签做的平铺容器。对于这种情况，可以使用 data-growing-idx。当在容器 DOM 结点上设置 data-growing-idx 属性，容器内的所有 DOM 元素同样，都会继承该属性值。

代码示例：

```aspnet
<div data-growing-idx="1">
  <div class="left-container">
    <img src="" alt="图片1"/>
  </div>
  <div class="right-container">
    <h3 class="title">
      文章一标题
    </h3>
  </div>
</div>
```

{% hint style="warning" %}
data-growing-idx属性需要赋值，建议传不为0的纯数字。

由于index必须是数字类型，Web JS SDK 在采集数据时，只会截取 data-growing-idx 中的数字部分（不包括单值为0时），自动忽略其他字符串，所以建议您传不为0的纯数字。

举例：`<div data-growing-idx="123abc">test</div>`// SDK 采集的index是 123
{% endhint %}

更多的位置信息规则，请参考[第2节：位置规则](https://sishen.gitbooks.io/gio-js-book/5/2.html)。

### 4. 设置数据采集黑名单（growing-ignore）

如果你希望过滤一些内容，可以在网站 DOM 结点上设置 growing-ignore 属性，这样这个容器里所有的元素的浏览量和点击量都不会被采集。

代码示例：

```aspnet
<div growing-ignore='true'>
 …
</div>
```

### 5. 开启输入文本框内容采集（growing-track）

由于输入文本框可能涉及一些隐私信息，比如账号、密码等，GrowingIO在采集数据的时候默认不采集输入文本框的数据。如果你希望采集某些文本框输入内容，比如搜索词，可以在input标签中设置growing-track属性，这样该文本框中的输入内容就会被采集到。如果input类型是password，即使开启内容采集，也不会采集该文本框的输入内容。

```aspnet
<input type='text' growing-track='true' />
```

## 4. 自定义数据上传

您的网页在集成了 GrowingIO 的 SDK 之后，它将会自动地为你采集一系列用户行为数据，并在 GrowingIO 分析后台供你制成数据分析报表。

除上述的用户行为数据（无埋点数据）之外，GrowingIO 还提供了多种 API 接口，供您上传一些自定义的数据指标及维度，请参考[API 2.x](web-sdk-api/websdk-apiv2.md) 。90% 以上的用户都会_上传登录用户 ID_，以便分析登录用户的数据情况。

## 5. 创建应用

在GrowingIO平台的创建相应的Web应用。创建应用请参考查看[创建应用](../../../product-manual/xiang-mu-guan-li/application-manage.md#chuang-jian-ying-yong)。

## 6. 验证SDK是否正常采集数据

{% hint style="info" %}
了解GrowingIO平台数据类型请参考[数据模型](../../../introduction/datamodel/)。
{% endhint %}

GrowingIO为您提供多种验证SDK是否正常采集数据的方式：

完成Web页面代码集成部署后，使用[Web Debugger](../../debugging/web-debugger.md) 工具校验您的网站是否在正常向GrowingIO平台发送数据。

