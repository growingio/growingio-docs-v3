# 访问用户

## 访问用户定义

访问用户是 GrowingIO 对访问您的应用（包括网页、App、微信小程序等，下同）的用户的一种识别机制。

每一个访问您的应用的用户都会在对应的设备中生成并记录一个唯一的 ID，我们称之为访问用户 ID。

对于不同平台类型的应用，GrowingIO 提供了多种识别方案，从而尽可能的实现对用户的唯一标识。

同一个项目中相同的访问用户 ID 会识别为一个用户。

## 访问用户ID

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

访问用户ID 将保存到 storage 中。

[访问用户ID生成机制详细说明](visituser.md#10-ke-hu-duan-sdkdeviceid-sheng-cheng-ji-zhi-jian-yao-luo-ji-shi-shen-me)

## 常见问题

**访问用户 ID 在哪些情况下会发生变化？**

**A:**

Web：1. 用户使用浏览器的隐身模式；2.用户手动清空Cookie；3.同一个用户使用多个浏览器

iOS：1. App 所属 Apple Developer Team 改变，即[ App 转让](https://help.apple.com/app-store-connect/#/deved688524f)；2.用户设备抹掉所有内容和设置

Android：

* 当访问用户ID 是 UUID时，1. 用户删除了应用重新安装；2. 用户在设置中清除了APP的数据
* 当访问用户ID是AndroidID或IMEI时，发生上述行为，如果再次获取时获取不到AndroidID或IMEI，访问用户ID 变化

微信小程序：

* 当访问用户ID 是 UUID时，1. 用户长按小程序入口的小程序图标，删除了小程序；2. 更换了手机设备；3. 手动更新了微信的缓存等
* 当访问用户ID 是openID时，上述行为不会导致 访问用户ID 变化

#### 客户端SDK 访问用户ID生成机制是什么？[​](http://localhost:3000/growingio-sdk-docs/question/common#10-%E5%AE%A2%E6%88%B7%E7%AB%AFsdk-deviceid-%E7%94%9F%E6%88%90%E6%9C%BA%E5%88%B6%E7%AE%80%E8%A6%81%E9%80%BB%E8%BE%91%E6%98%AF%E4%BB%80%E4%B9%88) <a href="#10-ke-hu-duan-sdkdeviceid-sheng-cheng-ji-zhi-jian-yao-luo-ji-shi-shen-me" id="10-ke-hu-duan-sdkdeviceid-sheng-cheng-ji-zhi-jian-yao-luo-ji-shi-shen-me"></a>

**A:**

* iOS： IDFA > IDFV > 随机访问用户ID
* Android：androidId > imei > 随机访问用户ID
* 小程序：OpenID > 随机访问用户ID
* Web: 随机访问用户ID

访问用户ID 的生成时机是在SDK初始化时。\
iOS设备如果想要使用IDFA作为访问用户ID，需要在用户授权获取到之后初始化SDK；如果拒绝授权，iOS 按照优先级 IDFV > 随机访问用户ID, 生成访问用户ID **。**Keychain存储。

```c
NSString *uuid;
NSUUID *idfa = ((NSUUID * (*)(id, SEL))[sharedManager methodForSelector:advertisingIdentifierSelector])(
        sharedManager, advertisingIdentifierSelector);
uuid = [idfa UUIDString];

uuid = [[[UIDevice currentDevice] identifierForVendor] UUIDString];

uuid = [[NSUUID UUID] UUIDString];
```

Android 设备首先会获取AndroidID，如果AndroidID 为空或为“9774d56d682e549c”(山寨机或其他设备)，会通过用户授权获取IMEI，如果IMEI获取不到，会随机生成访问用户ID 。本地文件存储。

```java
String uuid = null;

String adId = getAndroidId();
uuid = UUID.nameUUIDFromBytes(adId.getBytes(Charset.forName("UTF-8"))).toString();
        
String imi = getImei();
uuid = UUID.nameUUIDFromBytes(imi.getBytes(Charset.forName("UTF-8"))).toString();

uuid = UUID.randomUUID().toString();
```

小程序：如果SDK设置了强制登录模式，小程序打开时调用 wx.login 获取openid或unionId，且调用 identify 上报，会使用第一参数 作为 访问用户 ID ，否则会自动生成 随机访问用户ID。访问用户ID 将保存到 storage 中。

Web: 随机访问用户ID 存储在 localStorage 中，永久有效。

\
这样复杂逻辑的目的是尽量使用访问用户ID 标识唯一一台设备，将同一台设备上的访问用户标识为同一个用户。
