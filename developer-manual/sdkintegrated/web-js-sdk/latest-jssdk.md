# 集成最新SDK

## 准备条件

获取项目ID，获取方法请参考"项目管理 > 项目概览 > [查看项目基本信息](../../../product-manual/projectmange/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

## 1. 添加跟踪代码

请将以下代码放置到需要分析页面中的 <mark style="color:red;">\<head></mark> 和 <mark style="color:red;">\</head></mark> 标签之间，即可完成最新版本 Web JS SDK 页面代码的添加。

{% hint style="warning" %}
请使用 **您创建Web应用所在项目的项目ID** 替换代码中的 **your projectId** 。
{% endhint %}

```javascript
<!-- GrowingIO Analytics code version 2.1 -->
<!-- Copyright 2015-2022 GrowingIO, Inc. More info available at http://www.growingio.com -->
<script type='text/javascript'>
!function(e,t,n,g,i){e[i]=e[i]||function(){(e[i].q=e[i].q||[]).push(arguments)},n=t.createElement("script"),tag=t.getElementsByTagName("script")[0],n.async=1,n.src=('https:'==document.location.protocol?'https://':'http://')+g,tag.parentNode.insertBefore(n,tag)}(window,document,"script","assets.giocdn.com/2.1/gio.js","gio");
  gio('init', 'your projectId', {});
  //custom page code begin here
  //custom page code end here​
  gio('send');
</script>
<!-- End GrowingIO Analytics code version: 2.1 -->
```

{% hint style="warning" %}
1. &#x20;assets.giocdn.com/2.1/gio.js 该地址为Web JS SDK 的CDN地址，使用该地址加载的是SDK的最新版本，即 SDK 每次发布版本，页面即可加载最新版本SDK。
2. Web JS SDK 默认是不会采集本地页面（域名为 **localhost** 或者 **file://** 协议），如果您希望 SDK 采集本地页面，需要在集成 SDK 代码前添加如下代码：    `window._gr_ignore_local_rule=true; //开启本地页面采集`
{% endhint %}

## 2. 配置系统变量

设置系统变量的代码请插入上述追踪代码的 custom page code 部分，在 init 和 send 中间。

### 1. hashtag系统变量

GrowingIO默认不会把 hashtag 识别成页面 URL 的一部分。对于使用 hashtag 进行页面跳转的单页面网站应用来说，可以启用 hashtag 作为标识页面的一部分:

```javascript
gio('config', {'hashtag':true}); //放在init和send之间
```

以此监听 hashtag 的变化，并采集不同页面的数据。每次 hashtag 的改变都会触发一次页面浏览事件，hashtag 的信息也会记录在页面URL中。

## 3. 高级设置

高级设置可以帮助您更好地进行圈选操作，请将高级设置插入Web应用的HTML代码中。

### 1. 设置采集容器

GrowingIO默认可以圈选页面 DOM 上所有叶子结点和叶子结点的上一级父节点，以及 button 或 a 标签。

当您期望将除上述以外的标签作为可圈选容器，您需要为期望圈选容器的标签添加 data-growing-container 属性。圈选时，容器内子标签的点击都会汇总到该容器中。

例如，div 作为容器标签，如果以 id=1 的 div 作为可圈选容器，可进行圈选的代码示例：

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

### 2. 设置采集文本信息

对于一些图片或者区块，可以通过设置 data-growing-title 属性来设置采集结点的文本。

代码示例：

```aspnet
<li data-growing-title="上一页" class="ant-pagination-disabled">
  <a></a>
</li>
```

这时，采集到的li节点的内容就是“上一页”。

更多的文本信息规则，请参考[第4节：What(内容)](https://sishen.gitbooks.io/gio-js-book/dom/4what.html)和[第1节：内容规则](https://sishen.gitbooks.io/gio-js-book/5/1.html)。

### 3. 设置采集位置信息

除了内容以外，元素在列表里所在位置在某些场景下也是非常重要的信息。例如，对于推荐广告位而言，希望知道哪个位置的点击率最高。

GrowingIO SDK 会自动识别列表元素，并附带上元素在列表里的位置。LI 标签、TR 标签、DL 标签，会被自动识别为列表元素，列表内所有元素结点都会附带上位置信息。其他标签默认并不会带有位置信息。

例如，一些用 div 标签做的平铺容器。可以通过设置 data-growing-idx 属性来设置采集结点的位置。当在容器 DOM 结点上设置 data-growing-idx 属性，容器内的所有 DOM 元素同样，都会自动继承该属性值。

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
data-growing-idx 属性需要赋值，建议设置不为0的纯数字。

由于 idx 必须是数字类型，Web JS SDK 在采集数据时，只会截取 data-growing-idx 中的数字部分（不包括单值为0时），自动忽略其他字符串，所以建议您设置不为0的纯数字。

举例：`<div data-growing-idx="123abc">test</div>`// SDK 采集的index是 123
{% endhint %}

更多的位置信息规则，请参考[第2节：位置规则](https://sishen.gitbooks.io/gio-js-book/5/2.html)。

### 4. 设置数据采集黑名单

如果您希望过滤一些内容，可以在网站 DOM 结点上设置 data-growing-ignore 属性值为 true，该容器里所有元素的浏览量和点击量都不会被采集。

代码示例：

```aspnet
<div data-growing-ignore='true'>
 …
</div>
```

### 5. 开启输入文本框内容采集

由于输入文本框可能涉及一些隐私信息，比如账号、密码等，GrowingIO在采集数据的时候默认不采集输入文本框的数据。

如果您希望采集某些文本框输入内容，比如搜索词，可以在 input 标签中设置 data-growing-track 属性为 true ，该文本框中的输入内容就会被采集。

如果 input 类型是 password ，即使开启内容采集，也不会采集该文本框的输入内容。

```aspnet
<input type='text' data-growing-track='true' />
```

## 4. 自定义数据上传

您的网页在集成 GrowingIO  SDK 之后，会自动采集一系列用户行为数据，如用户访问，页面浏览，元素点击等。在 GrowingIO 分析后台，您可以根据这些行为数据制成数据分析报表。

除上述用户行为数据（无埋点数据）外，GrowingIO 还提供了多种 API 接口，供您上传自定义数据指标及维度，请参考[API 2.x](web-sdk-api/websdk-apiv2.md) 。90% 以上的用户都会_上传登录用户 ID_，以便分析登录用户的数据情况。

## 5. 动态Platform

为了能区分出上报的数据来自哪个平台，SDK实现自动的平台判断，支持的平台如下：

| 平台        | 说明                             |
| --------- | ------------------------------ |
| Web       | 网页端（直接浏览器打开或不在以下环境中）           |
| MinP      | 微信小程序内嵌H5页面                    |
| alip      | 支付宝小程序内嵌H5页面                   |
| baidup    | 百度小程序内嵌H5页面                    |
| qq        | QQ小程序内嵌H5页面                    |
| bytedance | 字节跳动内嵌 H5 页面                   |
| Android   | 安卓App中内嵌H5页面（App需要集成安卓SDK）     |
| iOS       | iOS App中内嵌H5页面（App需要集成iOS SDK） |

## 6. 创建应用

在GrowingIO平台的创建相应的Web应用。创建应用请参考查看[创建应用](../../../product-manual/projectmange/application-manage.md#chuang-jian-ying-yong)。

## 7. 验证SDK是否正常采集数据

{% hint style="info" %}
了解GrowingIO平台数据类型请参考[数据模型](../../../introduction/datamodel/)。
{% endhint %}

GrowingIO为您提供多种验证SDK是否正常采集数据的方式：

完成Web页面代码集成部署后，使用[Web Debugger](../../debugging/web-debugger.md) 工具校验您的网站是否在正常向GrowingIO平台发送数据。
