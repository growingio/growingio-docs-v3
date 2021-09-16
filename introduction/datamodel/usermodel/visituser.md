# 访问用户

## 访问用户定义

访问用户是 GrowingIO 对访问您的应用（包括网页、App、微信小程序等，下同）的用户的一种识别机制。

每一个访问您的应用的用户都会在对应的设备中生成并记录一个唯一的 ID，我们称之为访问用户 ID。

对于不同平台类型的应用，GrowingIO 提供了多种识别方案，从而尽可能的实现对用户的唯一标识。

同一个项目中相同的访问用户 ID 会识别为一个用户。

## 访问用户ID生成机制

### WEB JS SDK

> 包括 Web 页面与 H5 页面

GrowingIO会使用随机 UUID 的方法生成访问用户ID，并将之记录在浏览器的 Cookie 中

### iOS SDK

GrowingIO会按照下面的顺序获取访问用户ID：

1. IDFA
2. IDFV
3. 随机 UUID

并将之存储至 keychain 中。

### Android SDK

GrowingIO 会按照如下顺序获取访问用户ID：

1. Android ID
2. IMEI
3. 随机UUID

进行 MD5 加密后将之存储至设备本地文件系统。

### 小程序 SDK

GrowingIO默认使用 UUID（随机 UUID 的方法生成访问用户 ID，并将之记录在浏览器的 Cookie 中）来作为访问用户 ID，您也可以通过 API 设置使用 openid 作为访问用户ID。

访问用户ID 将保存到微信浏览器的 cookie 中。

## 常见问题

访问用户 ID 在哪些情况下会发生变化？

Web：1. 用户使用浏览器的隐身模式；2.用户手动清空Cookie；3.同一个用户使用多个浏览器

iOS：1. App 所属 Apple Developer Team 改变，即[ App 转让](https://help.apple.com/app-store-connect/#/deved688524f)；2.用户设备抹掉所有内容和设置

Android：

* 当访问用户ID 是 UUID时，1. 用户删除了应用重新安装；2. 用户在设置中清除了APP的数据
* 当访问用户ID是AndroidID或IMEI时，上述行为不会导致访问用户ID 变化

微信小程序：

* 当访问用户ID 是 UUID时，1. 用户长按小程序入口的小程序图标，删除了小程序；2. 更换了手机设备；3. 手动更新了微信的缓存等
* 当访问用户ID 是openID时，上述行为不会导致 访问用户ID 变化

