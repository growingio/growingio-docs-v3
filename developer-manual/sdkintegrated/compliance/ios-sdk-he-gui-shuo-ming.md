# iOS SDK合规说明

请使用最新 GrowingIO iOS SDK[ 稳定版本 ](../ios-sdk/iossdk-log.md)及以上

* 根据 根据[工业和信息化部关于开展纵深推进APP侵害用户权益专项整治行动](http://www.gov.cn/zhengce/zhengceku/2020-08/02/content\_5531975.htm)和 [User Privacy and Data Use](https://developer.apple.com/app-store/user-privacy-and-data-use/) ，App 需要通过隐私政策说明应用采集数据
* 需要告知用户您集成了 GrowingIO SDK，并且 GrowingIO SDK 会尝试获取 IDFA、IDFV 信息用于渠道信息，并且采集用户信息进行行为分析
* GrowingIO SDK 默认启用 IDFA，如您不希望启用 IDFA，参考：[App Store 提交应用注意事项](https://docs.growingio.com/v3/developer-manual/sdkintegrated/ios-sdk/manunl-ios-sdk#3-app-store-ti-jiao-ying-yong-zhu-yi-shi-xiang)

为确保您的App在集成 GrowingIO SDK之后，能够满足工信部和苹果用户隐私相关合规要求，请参考以下说明。

## 隐私协议填写

#### 收集和获取 <a href="#shou-ji-he-huo-qu" id="shou-ji-he-huo-qu"></a>

在您的APP《隐私协议》中收集和获得的个人信息栏目中根据实际情况填写如下内容：

```
我们的产品集成了GrowingIO SDK，我们会通过 GrowingIO SDK 收集您的设备信息（例如：`IDFA`、`IDFV`、操作系统、设备型号、系统版本、剪切板内容）用于统计分析您在 App 内的使用效果，从而改进我们的产品和服务。
```

可在第三方SDK列表中增加如下内容(设备信息按照实际情况填写)：

```
GIO移动端 SDK
用途：分析收集移动应用程序(App)用户的使用情况
收集个人信息类型：设备标识信息（如IDFA、IDFV），设备类型，设备版本，系统版本，地理位置信息，网络设备制造商，网络模式，剪切板内容
提供方：北京易数科技有限公司
第三方SDK隐私协议链接：https://accounts.growingio.com/user-privacy
```

在您的APP《隐私协议》中的与授权合作伙伴共享栏目中根据实际情况填写如下内容:

```
我们的产品集成了GrowingIO SDK，我们会通过 GrowingIO SDK 收集您的设备信息（例如：`IDFA`、`IDFV`、操作系统、设备型号、系统版本、剪切板内容）用于统计分析您在 App 内的使用效果，从而改进我们的产品和服务。
```

## 合规步骤

1.您需要确保 App 有《隐私协议》，并且在用户第一次启动 App 时就能向用户展示并取得用户同意；

2.请务必告知用户您使用了 GrowingIO SDK，请在 《隐私协议》 中添加隐私条款，参考[隐私协议填写](ios-sdk-he-gui-shuo-ming.md#yin-si-xie-yi-tian-xie)

3.延迟初始化

集成 [iOS SDK](../ios-sdk/)，请在用户同意《隐私协议》之后再初始化 GrowingIO SDK。如果配置有[UniversialLink](../../../product-manual/growing/product-configuration/deeplink.md#2.2-universal-links-pei-zhi)，则在SDK初始化之后可用。 示例代码如下：

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    if (<用户未同意隐私协议>) {
      // 展示隐私协议弹框，等待用户同意后，添加 GrowingIO SDK 初始化代码
    } else {
        //  GrowingIO SDK 初始化代码
    }
    ...
    return YES;
}
```

4.集成了 GrowingIO SDK，默认会尝试获取 `IDFA`、`IDFV` 信息，用于统计分析用户在 App 内的使用效果。 参考：[App Store 提交应用注意事项](../ios-sdk/auto-ios-sdk.md#11.-app-store-ti-jiao-ying-yong-zhu-yi-shi-xiang)​​

## iOS 权限说明

|  权限  | 用途                              |
| :--: | ------------------------------- |
|  网络  | 允许应用程序联网和发送数据权限，以便提供统计分析服务。必须权限 |
| IDFA | 允许应用获取 IDFA，以便标识匿名用户。可选权限       |

## 其他说明

### 关于 Privacy manifest 隐私清单

手动将以下内容合并到您的 App 的 PrivacyInfo.xcprivacy 中：
```xml
<key>NSPrivacyAccessedAPITypes</key>
<array>
  <dict>
    <key>NSPrivacyAccessedAPIType</key>
    <string>NSPrivacyAccessedAPICategoryFileTimestamp</string>
    <key>NSPrivacyAccessedAPITypeReasons</key>
    <array>
      <string>C617.1</string>
    </array>
  </dict>
  <dict>
    <key>NSPrivacyAccessedAPIType</key>
    <string>NSPrivacyAccessedAPICategoryDiskSpace</string>
    <key>NSPrivacyAccessedAPITypeReasons</key>
    <array>
      <string>7D9E.1</string>
    </array>
  </dict>
  <dict>
    <key>NSPrivacyAccessedAPIType</key>
    <string>NSPrivacyAccessedAPICategoryUserDefaults</string>
    <key>NSPrivacyAccessedAPITypeReasons</key>
    <array>
      <string>CA92.1</string>
    </array>
  </dict>
</array>
```

### 关于 GDPR <a href="#guan-yu-gdpr" id="guan-yu-gdpr"></a>

为符合[​General Data Protection Regulation 欧盟通用数据保护条例](https://zh.wikipedia.org/wiki/%E6%AD%90%E7%9B%9F%E4%B8%80%E8%88%AC%E8%B3%87%E6%96%99%E4%BF%9D%E8%AD%B7%E8%A6%8F%E7%AF%84)​，GrowingIO SDK 提供 `disableDataCollect` 接口，当用户不同意数据采集时，调用该接口， 禁止数据采集；在用户同意数据采集时，调用 `enableDataCollect`，开启数据采集。示例代码如下：

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // 1. 调用 disableDataCollect 接口
    // 设置禁止数据采集代码
    
    // 2.初始化 GrowingIO SDK
    // 初始化代码
  
    ...
    return YES;
}
​
// 某一时刻同意数据采集
- (void)userAcceptDataCollection {
    ...
    // 3. 调用 enableDataCollect 接口
    // 设置开启数据采集代码
    ...
}
```

### 关于 IDFA 广告标识符 <a href="#guan-yu-idfa-guang-gao-biao-shi-fu" id="guan-yu-idfa-guang-gao-biao-shi-fu"></a>

**使用途径**

GrowingIO SDK 会采集 `IDFA` 和 `IDFV` 字段上传，如果您的项目中引入了 `AdSupport.framework`，会尝试获取 `IDFA`。

除了 `IDFA` 和 `IDFV` 字段，GrowingIO SDK 使用 访问用户ID 字段标识访问用户 ，其值使用 IDFA 、IDFV 或 随机字符串 ，三者的优先级为 IDFA> IDFV > 随机字符串 ，例如：如果获取不到 IDFA，SDK 会使用 IDFV 作为访问用户ID。

**合规风险**

当使用 `IDFA` 时有一定的合规风险，但是考虑到采集的准确性，GrowingIO SDK 仍然提供`IDFA`的采集方法，如果不需要采集`IDFA`，请在项目工程中去除 `AdSupport.framework` 的引用，并且不要在项目中导入 `AdSupport` 相关头文件。

如果需要发布儿童级应用，完全不需要相关 `IDFA` 的获取逻辑，请联系我们的客户成功经理或技术支持获取 SDK。

## App Store 隐私问题

苹果在 iOS 14.3 系统更新了隐私政策，要求 App 更新或发布时需要发布者填写一份隐私报告。此时如果 App 集成 GrowingIO SDK 应该如何填写。

### 1. 是否会从此 App 中收集数据

**选择 「是，会从此 App 中收集数据」**

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.15.03 (1).png>)

### 2. 位置数据收集

**GrowingIO SDK 不会主动申请采集位置信息，如果客户的App申请获取了位置信息，GrowingIO就会采集位置信息用于定位用户城市级别的位置，需要勾选 「精准位置」**

> 如果你想禁用位置信息获取，调用 `+setEnableLocationTrack:` 为 `NO`

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.19.49.png>)

### 3. 标识符和使用数据收集

**默认情况下只需选择 「设备 ID」**

**如果使用用户关联，即调用 设置登录用户ID 接口则还需勾选 「用户 ID」**

**如果使用的是 无埋点SDK 需继续勾选 「产品交互」**

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.21.52.png>)

### 4. 崩溃数据收集

如果您使用了 `GrowingMonitorKit` 并调用`+setUploadExceptionEnable:` 方法开启了Crash监控上报，您还需要勾选 「崩溃数据」，如图：

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.24.12 (2).png>)

存储后会在您的 App 隐私页面根据我们的选择生成一些列收集类型面板，点击对应面板后可以继续做详细的选择，下面会详细介绍。

### 5.1 位置

**1. 请在 「位置」面板中，勾选 「分析」**

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.29.04 (1).png>)

**2. 然后下一步，勾选「是，从此 App 中收集的精确位置数据与用户身份关联」**

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.31.00.png>)

**3. 根据您App实际情况选择是否用于追踪目的**

### 5.2 最终用户 ID

**1. GrowingIO SDK 会在调用 设置登录用户ID 接口时收集用户 ID 用于分析功能，因此这里选择「分析」，如图**

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.32.10.png>)

&#x20;**2. 勾选后点击下一步，选择「是，从此 App 中收集的用户 ID 与用户身份关联」，这里根据具体的业务进行勾选，如图**

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.32.33 (1).png>)

**3. 点击下一步，需要选择「是，我们会将用户 ID 用于追踪目的」**

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.34.49.png>)

### 5.3 设备

**1. GrowingIO SDK 收集设备 ID 用于收集用户登录前的数据，因此这里继续选择「分析」，如图**

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.36.09.png>)

**2. 点击下一步，因为收集到的数据会与设备 id 绑定，所以此处继续选择「是」**

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.37.28 (1).png>)

**3. 继续下一步，同用户 ID ， 会使用 IDFA 与第三方数据相关联以用于定向广告或广告评估目的，如图**

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.40.35.png>)

### 5.4 产品交互

**1. 使用 GrowingIO 无埋点SDK后，会收集 APP启动，APP退出，用户点击，页面浏览等相关行为用于分析产品，因此这里继续选择「分析」，如图**

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.42.05.png>)

**2. 点击下一步，继续选择是，如图**

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.43.03 (1).png>)

**3. 最后追踪目的，请根据您实际情况选择，是否要用于追踪目的**

### 6. GrowingIO SDK 合规性说明

GrowingIO SDK 默认收集的数据类型只有「设备 ID」和「用户 ID」主要用于追踪，其他的数据类型采集需要根据您自己的采集业务以及选择的SDK 功能来做相应选择：

* 调用 `+setUserId:`接口：需选择「用户 ID」
* 使用无埋点 SDK：需选择「产品交互」
* 开启崩溃收集：需选择「崩溃数据」
* 开启经纬度采集：需选择「精确位置」

尽管有上述指南，您应知晓并同意，上述仅为指导性建议，您仍应根据相应管辖国家的法律的调整和更新，以及您自己的业务实际情况，及时调整、更新您平台或APP的隐私政策，以保证您在收集、使用最终用户信息时合法合规，且有充分的权利授权GIO为了向您提供服务的目的收集、使用必要的最终用户信息。否则，您不得使用GIO的任何服务。

## 常见问题

### Q：App一开始禁止了`IDFA`权限，后续允许了`IDFA` 权限，数据会有什么变化？[#](http://localhost:3000/growingio-sdk-docs/docs/compliance/iosCompliance#qapp%E4%B8%80%E5%BC%80%E5%A7%8B%E7%A6%81%E6%AD%A2%E4%BA%86idfa%E6%9D%83%E9%99%90%E5%90%8E%E7%BB%AD%E5%85%81%E8%AE%B8%E4%BA%86idfa-%E6%9D%83%E9%99%90%E6%95%B0%E6%8D%AE%E4%BC%9A%E6%9C%89%E4%BB%80%E4%B9%88%E5%8F%98%E5%8C%96) <a href="#qapp-yi-kai-shi-jin-zhi-le-idfa-quan-xian-hou-xu-yun-xu-le-idfa-quan-xian-shu-ju-hui-you-shen-me-bia" id="qapp-yi-kai-shi-jin-zhi-le-idfa-quan-xian-hou-xu-yun-xu-le-idfa-quan-xian-shu-ju-hui-you-shen-me-bia"></a>

A：对于`IDFA`，App生命周期内，`IDFA` 只会获取一次，就算后续 IDFA 权限打开了，也不会再获取，可以在下一次App启动后生效。对于 设备标识，仅且在 App第一次启动时生成，后续不再改变，优先级为 `IDFA`> `IDFV` > 随机字符串，如果 `IDFA` 无法获取，则会使用`IDFV` 且不再变动，会存入`Keychain`，卸载也无法修改。如果要设备标识 和 `IDFA` 绑定，则需要在用户同意 `IDFA`权限之后进行第一次SDK初始化操作。

### Q：延迟初始化之后，发现丢掉了部分事件 <a href="#q-yan-chi-chu-shi-hua-zhi-hou-fa-xian-diu-diao-le-bu-fen-shi-jian" id="q-yan-chi-chu-shi-hua-zhi-hou-fa-xian-diu-diao-le-bu-fen-shi-jian"></a>

A：对于SDK初始化之前，或者开启数据采集之前发生的事件，一概丢弃。

##
