# 产品使用

## 1. 一个项目下的两个应用 iOS 和 Android 的数据怎么一起统计？

概览数据不能合并，但是可以创建复合指标。

## 2. APP 页面升级以后，很多节点变了位置，是否需要重新定义事件？

是的。因为我们的圈选逻辑是以页面结构中的 xpath 为基础，节点位置改变意味着 xpath 改变，所以需要重新定义。

## 3. 是否可以统计到搜索引擎渠道的“搜索词”?

您的用户群体使用搜索引擎在搜索框中输入搜索词，通过此搜索词的返回结果访问您的网站，我们会记录用户在搜索框中输入的「搜索词」。

GrowingIO会针对百度、搜狗、谷歌、360这4个搜索引擎的搜索词进行解析。

* 谷歌的搜索词目前无法获取，包括所有浏览器。
* 付费的搜索词正常情况下都能被解析到 --- 未付费的搜索词对于不同的浏览器存在不同限制，当在不同的浏览器上使用上述搜索引擎搜索，能解析到的关键词会被收集，不能解析的归为“\[搜索引擎\]自然流量”。
* N/A表示，这部分流量不是通过搜索词访问的。

## 4. 指标管理中元素/页面暂无数据，圈选时还能看到数据？

该页面/元素所在页面可能带了查询条件（query），当页面带查询条件时，不会回溯数据，只会从保存那一刻开始统计数据，可以等 1-2 个小时后看。

圈选时显示的是没带查询的数据。

## 5. 我上传用户信息后，会以怎样的方式进行展示？

上传用户属性后，该属性将在「用户分群」的「维度」里展现。

## 6. 为什么我新用户数量为什么占比这么高？

GrowingIO 从集成代码后开始获取用户数据，此时所有的访问用户对于GrowingIO 来说，都是第一次访问。所以就会将他们全部定义成新用户。因此在刚刚集成代码的几天会统计到大量的新用户。建议您在统计一段时间后再参考新用户数据。

## 7. 我要如何看我们产品的每一页 PV？

您可以先定义全站的 PV 指标，然后在作图的时候选择"页面"维度即可。

## 8. 我如何用看我 App 每天的 DAU 呢？

概览中提供的『访问用户量』指标，即是您 App 每日的访问用户量

## 9. 引导页面第二、三屏会比第四屏低？

第二屏和第三屏一般会很快被用户划过，我们的采集逻辑是 1s 内如果用户就划过该屏，就不会去采集，所以第二、三屏会比第四屏低。

## 10. Android 中按钮点击一次，但发送两次点击事件？

因为按钮已经在 xm l文件里写了，系统自动绑定了 DeclaredOnClickListener，会执行 onClick 方法，但是自己又实现了一个名为 onClick 的点击方法，SDK 识别到 onClick 的点击方法就会算一次点击事件，所以点击一次会触发两个点击事件。

解决方式：把自己实现的 onClick 方法换个名称，例如 onButtonClick 等。
