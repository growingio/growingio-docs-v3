---
description: 介绍SDK工作方式
---

# SDK 简介

## SDK 工作方式

### JS SDK

GrowingIO Web JS SDK 是运行于网页的一段 Javascript 代码，基于无埋点技术采集网站数据，同时 GrowingIO Web JS SDK 也提供丰富的接口以支持埋点。采集到的数据将被传输并存储在 GrowingIO 的云端服务器上。GrowingIO 通过使用这些数据来分析客户网站的用户的使用情况，生成网站使用报告，提供跟用户行为数据分析相关的服务。

GrowingIO Web JS SDK 会在网站用户加载网页后自动启动，并收集用户的行为数据，建议将 GrowingIO 提供的跟踪代码放在`<head> </head>`之间。JS SDK 采用异步方式加载，不会影响网站自身的加载数据。

目前 SDK 主要采集三类数据:

* **访问数据**:网站访客在何时何地访问了哪个网页，收集信息包括域名、页面路径、浏览器、操作系统、屏幕分辨率、访问来源、用户唯一标识 ID、访问唯一标识 ID、访问时间、页面标题等。如果客户集成时设置了自定义维度，也会一并收集。
* **行为数据**:用户在网站上的交互行为，比如点击链接、提交表单、修改选择，都会被自动采集。采集内容包括交互行为类型、交互元素的页面信息、交互元素的标记 ID、交互元素的超链接、交互元素的位置信息等。GrowingIO 不采集任何用户在文本框中输入的密码等个人隐私信息。
* **元素浏览数据**:当用户访问网站时，用户浏览的内容即页面出现的元素，会被自动采集，包括内容所在的页面信息、元素的标记 ID、文本内容、超链接、位置信息。

### 移动端 SDK

移动端SDK需要在应用打包时，被加载在您的应用当中。GrowingIO的「移动端SDK」会随着客户应用的启动而自动开始进行用户行为数据。当用户关闭应用时，SDK会随着客户应用的关闭而关闭，不会在后台做任何额外动作。

**时间延迟**

经过我们反复的测量，移动端SDK的数据发送仅仅会带来10ms以内的时间延迟，用户感知不到任何的差异。GrowingIO真正的做到了用户无感知的数据采集，不会对应用的用户体验带来任何降低。

**稳定性**

我们非常注重SDK的稳定性，每个版本的SDK我们都会进行大量的稳定性测试，以确保您的应用一如既往的稳定。从目前客户集成SDK的结果来看，应用的崩溃率没有因为集成而提高。

**移动端SDK采集的数据类型**

与「JS SDK」一样，移动端SDK主要采集三类数据：访问数据，内容数据，行为数据。并且，不采集应用文本框里的数据，也就不会主动记录普通用户填写的账户/电话/银行卡等隐私信息，在采集环节保证安全。

**移动端框架版本兼容**

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x6846;&#x67B6;</th>
      <th style="text-align:left">SDK&#x7C7B;&#x522B;</th>
      <th style="text-align:left">App&#x9002;&#x914D;&#x7684;&#x7CFB;&#x7EDF;&#x7248;&#x672C;</th>
      <th style="text-align:left">&#x6846;&#x67B6;&#x7248;&#x672C;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x539F;&#x751F;Android</td>
      <td style="text-align:left">&#x65E0;&#x57CB;&#x70B9;&#x3001;&#x57CB;&#x70B9;</td>
      <td style="text-align:left">
        <p>Android 4.2+</p>
        <p>iOS 8+</p>
      </td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x539F;&#x751F;iOS</td>
      <td style="text-align:left">&#x65E0;&#x57CB;&#x70B9;&#x3001;&#x57CB;&#x70B9;</td>
      <td style="text-align:left">iOS 8+</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">React Native</td>
      <td style="text-align:left">&#x65E0;&#x57CB;&#x70B9;&#x3001;&#x57CB;&#x70B9;</td>
      <td style="text-align:left">
        <p>Android 4.2+</p>
        <p>iOS 8+</p>
      </td>
      <td style="text-align:left">0.46-0.56&#x3001;0.59.9</td>
    </tr>
    <tr>
      <td style="text-align:left">Flutter</td>
      <td style="text-align:left">&#x57CB;&#x70B9;</td>
      <td style="text-align:left">
        <p>Android 4.2+</p>
        <p>iOS 8+</p>
      </td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">Cordova</td>
      <td style="text-align:left">&#x57CB;&#x70B9;</td>
      <td style="text-align:left">
        <p>Android 4.2+</p>
        <p>iOS 8+</p>
      </td>
      <td style="text-align:left">5.0.0</td>
    </tr>
    <tr>
      <td style="text-align:left">Weex</td>
      <td style="text-align:left">&#x57CB;&#x70B9;</td>
      <td style="text-align:left">
        <p>Android 4.2+</p>
        <p>iOS 8+</p>
      </td>
      <td style="text-align:left">0.16.0</td>
    </tr>
    <tr>
      <td style="text-align:left">API Cloud</td>
      <td style="text-align:left">&#x57CB;&#x70B9;</td>
      <td style="text-align:left">
        <p>Android 4.2+</p>
        <p>iOS 8+</p>
      </td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">APP Can</td>
      <td style="text-align:left">&#x57CB;&#x70B9;</td>
      <td style="text-align:left">
        <p>Android 4.2+</p>
        <p>iOS 8+</p>
      </td>
      <td style="text-align:left">-</td>
    </tr>
  </tbody>
</table>

