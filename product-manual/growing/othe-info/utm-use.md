# UTM参数使用指南

## 概述 <a id="gai-shu"></a>

对于运营人员来说，UTM 是个非常熟悉的东西。例如，通过 UTM 码就可以知道每一篇文章带来的流量和用户。

但是通过 GrowingIO，UTM 码还有更强大的功能：可以根据不同渠道、不同内容做精细化分析，帮你对比区分优质和劣质渠道，提高流量在产品内的转化。

使用添加 GrowingIO 添加 UTM 参数的链接投放后，每一个渠道带来的流量都十分清晰，用户在产品内的行为也一目了然，是否注册了，是否最终购买了，都可以看到。我们可以看到讲述 heatmap 热图的这篇内容在渠道「微博1」投放的链接，带来了 9992 个页面浏览量，2066 个注册用户量，以及 1614 个购买用户量。

![](https://gblobscdn.gitbook.com/assets%2F-Lo08UtW7H58ehFKeZ4g%2F-LuAgFT3I_gSUI2qTH0d%2F-LuAjSwiBvhNDn-jgM4x%2Fimage.png?alt=media&token=5db43aef-e7c7-4e90-95d4-64c9cdd8aa59)

而且不仅可以看到同一篇文章在不同渠道的流量情况，如 heatmap 热图这篇内容在微信、微博和其他渠道的推广情况；还可以看到同一个渠道不同文章带来的流量情况，如在微博渠道，heatmap 热图的文章的导流情况比 features 功能文章的导流情况更好。

用户在产品内的行为，有多少进行了注册，有多少完成了购买，清清楚楚，而且，我们还可以将不同渠道进行分组，查看不同渠道的留存和转化。

当您自行在投放链接上添加GrowingIO格式的UTM参数时，请注意保证查询条件格式合法。

查询条件格式为：`www.xxxx.com/path?utm_source=a&utm_medium=b`

常见的错误的格式有：

* 使用多个问号：www.xxx.com/path?utm\_source=a?utm\_medium=b
* 缺少问号：www.xxx.com/path&utm\_source=a&utm\_medium=b
* 使用其他符号：www.xxx.com/path?otherconfig="utm\_source=a&utm\_medium=b"

## UTM 参数设置 <a id="utm-can-shu-she-zhi"></a>

通过 UTM 参数追踪外部流量的访问情况的原理是：把你投放在不同渠道的链接打上特定的标记，以监控各个链接的流量情况。

### 1. 确定目标链接 <a id="1-que-ding-mu-biao-lian-jie"></a>

首先，确定这个链接最终指向的目标网页是哪个？一般来说是你自己的网站的某个页面，然后这个页面需要加载过统计分析工具的 SDK 。也就是说前提是，链接最终指向加载了相应的分析代码的你自己的网站。

### 2. 添加自定义的参数 <a id="2-tian-jia-zi-ding-yi-de-can-shu"></a>

接下来，我们需要设置 UTM 的参数，也就是在链接上添加规则，进行标记，投放链接后我们就可以知道是哪个来源带来的流量了。对于不同的活动或文章，我们要设置不同的 UTM 参数用来区分。

这里就是指你用各种各样的内容来描述这条链接是放在哪个活动、哪个来源上的，例如：

![](https://docs.growingio.com/.gitbook/assets/utm2.jpeg)

以现在很常用的新媒体营销方式为例，我们在微信的阅读原文里放了一条引导流量的链接：

```text
https://www.growingio.com/?utm_source=weixin&utm_medium=article1&utm_campaign=product&utm_content=0811-tool&utm_term=tool
```

这条链接的意思是什么呢？

![](https://docs.growingio.com/.gitbook/assets/utm3.jpeg)

“ ? ” 之后的 UTM 参数可以理解为链接的名字，即为投放在不同渠 道的每个链接起的分析工具能够识别的名字。 这条 UTM 代表的含义就是：这个指向 www.growingio.com 的投放链接，是在 8 月 11 日 utm\_content=0811-tool 微信公众号 utm\_source=weixin 的首条推送文章里 utm\_medium=article1 投放的，这篇文章是介绍工具 utm\_term=tool 的产品文章 utm\_campaign=product 。

网页链接也有很多种表现形式，比如说做成二维码，用在各个活动里使用。

我们提供网页UTM链接批量生成工具：[自主投放URL构建工具](https://assets.growingio.com/help/doc/%E8%AF%A5%E6%96%87%E6%A1%A3%E7%94%A8%E6%9D%A5%E7%94%9F%E6%88%90%E6%8A%95%E6%94%BEURL_V2.0.xlsm)​

以现在很常用文章内二维码获客方式为例，我们在公众号关于增长的内容里放了一个小程序链接二维码，可以让用户直接扫一扫打开。生成二维码的实际链接如下：

```text
pages/index/index?utm_source=wechat_articel&utm_content=618Growth
```

这条链接的意思是什么呢？“?” 之后的 UTM 参数可以理解为链接的信息，即为投放在不同渠 道的每个链接起的分析工具能够识别的名字。这条 UTM 代表的含义就是：这个指向你的小程序页面 pages/index/index 的投放链接，是一个在微信公众号中的618推送的增长相关的文章，因为 utm\_source=wechat\_article 标记是微信公众号文章渠道，utm\_content=618Growth 标记是 618 增长文章。

另外公众号链接到小程序的图文链接，也可以在微信公众号设置文字、图片或者卡片链接时，在落地指向页面的连接中添加UTM参数。

当我们有很多内容同时在各个渠道投放时，这样的链接就十分有用了。例如通过大V公众号推广小程序时，utm\_source上标记不同大V的ID，我们就可以非常清晰的知道每个大V的内容带来的流量；也可以按照不同的渠道将流量进行分组，分析不同渠道带来的效果和质量。

GrowingIO 提供的 UTM 参数和自定义参数的方式采用的是目前市面上最常用的定义方式：

![](https://docs.growingio.com/.gitbook/assets/utm4.jpeg)

我们可以根据需要，进行各种各样自定义的填充，因为UTM最初是用在广告监控上的，所以它的很多名称还是关于广告的，但是我们现在已经可以把它放在各个内容、活动、推广中，监控渠道的流量情况。具体的填写参数的意义和方法，可以根据具体的场景进行灵活的变通。

小程序可监测的UTM参数维度，和网站监测产品是一致的，采用的是目前市面上最常用的定义方式。

## UTM参数映射 <a id="utm-can-shu-ying-she"></a>

如果你有自定义的参数没办法进行调整，你可以使用UTM映射功能进行参数映射和配置。请参考[UTM映射管理](../../projectmange/projectmange/utm.md)。

## 使用案例 <a id="shi-yong-an-li"></a>

UTM 做好了之后，可以做哪些分析呢？我们就可以进行日常的监控和活动的监控了。

现在，我们知道哪些投放的渠道来的量高、哪些量低了，可以有的放矢地进行市场推广和渠道运营，我们可以用UTM里面的维度来制图，看一下这一周文章投放的效果：

![](https://docs.growingio.com/.gitbook/assets/utm8.jpeg)

接下来，你可能想了解更多细节，这些人都访问了哪些页面呢？比如说他们是否最终注册完成了呢？我们可以加上注册页面的指标来做图：

![](https://docs.growingio.com/.gitbook/assets/utm9.jpeg)

这些都只是一个开始，接下来我们还可以做更有价值的分析，在漏斗里，用UTM参数作为不同的维度，可以对比不同来源不同内容的转化率：

## 常见问题 <a id="chang-jian-wen-ti"></a>

### 1. UTM 参数中存在多个问号会遇到什么问题？ <a id="1-utm-can-shu-zhong-cun-zai-duo-ge-wen-hao-hui-yu-dao-shi-mo-wen-ti"></a>

问号在 HTTP 协议中作为特殊字符，GrowingIO 会根据 "?" 符号来获取查询条件参数，用 “&” 符号分隔查询条件中的参数，用 “=” 分隔参数与具体值。

当网页地址中有多个问号时，默认处理逻辑会从第一个问号开始做参数识别，后续再次出现的问号会作为参数中的信息被识别，影响后续参数信息的识别，从而影响 UTM 各维度的信息统计。在广告投放时需要对网页地址做规范化处理。

#### ​ <a id="undefined"></a>

​

​

