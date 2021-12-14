# 初始化配置项API

GrowingIO初始化配置项均在AppDelegate.m文件中的didFinishLaunchingWithOptions方法中 SDK 初始化代码块中设置，下面将分类并描述含义。

**代码示例**

```swift
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // Override point for customization after application launch.
    [Growing startWithAccountId:@"0a1b4118dd954ec3bcc69da5138bdb96"];
    //输出调试日志
    [Growing setEnableLog:YES];
    // 设置为 YES, 将启用 HashTag
    [Growing enableHybridHashTag:YES];
    return YES；
}
```

## 基础配置API

| API                                                            | 默认值 | 说明                                                           | 无埋点SDK版本支持 | 埋点SDK版本支持 |
| -------------------------------------------------------------- | --- | ------------------------------------------------------------ | ---------- | --------- |
| startWithAccountId:_**AccountId**_                             | 无   | 初始化方法，_**AccountID**_为项目id，默认采样率为100%。                       | ✔️         | ✔️        |
| startWithAccountId:_**AccountId**_ withSampling:_**sampling**_ | 无   | 初始化方法，_**AccountID**_为项目id；_**sampling**_为采样率。               | ✔️         | ✔️        |
| handleUrl                                                      | 无   | URL Scheme处理方法，通过参数不同区分圈选、MobileDebugger、DeepLink、用户运营预览弹窗等。 | ✔️         | ✔️        |

## SDK功能API

| API                                   | 默认值 | 说明                                | 无埋点SDK版本支持 | 埋点SDK版本支持 |
| ------------------------------------- | --- | --------------------------------- | ---------- | --------- |
| sdkVersion                            | 无   | 获取当前GrowingIO SDK版本号。             | >=2.0.0    | -         |
| setEnableLog                          | YES | 采集日志开关，setEnableLog=YES时，会输出调试日志。 | ✔️         | ✔️        |
| getEnableLog                          | 无   | 获取采集日志开关的当前状态。                    | ✔️         | ✔️        |
| setTrackerHost                        | 无   | 设置数据收集平台服务器地址。                    | ✔️         | ✔️        |
| setReportHost                         | 无   | 设置设备报活服务器地址。                      | ✔️         | ✔️        |
| setDataHost                           | 无   | 设置数据查看平台服务器地址。                    | ✔️         | ✔️        |
| setGtaHost                            | 无   | 设置数据后台服务器地址。                      | ✔️         | ✔️        |
| setWsHost                             | 无   | 设置数据后台服务器地址。                      | ✔️         | ✔️        |
| <p>setHybridJSSDK</p><p>UrlPrefix</p> | 无   | 设置数据后台服务器地址。                      | ✔️         | -         |
| setZone                               | 无   | 设置 zone 信息，即时区信息。                 | ✔️         | ✔️        |
| getDeviceId                           | 无   | 获取当前设备 ID。                        | ✔️         | ✔️        |
| getVisitUserId                        | 无   | 获取当前访问用户ID。                       | ✔️         | ✔️        |
| getSessionId                          | 无   | 获取当前访问ID。                         | ✔️         | ✔️        |
| growingAttributesDonotTrackImp        | NO  | 设置是否采集view及页面元素的`imp`事件。          | >=2.6.7    | -         |

## 数据采集发送API

| API                    | 默认值  | 说明                                                                          | 无埋点SDK版本支持 | 埋点SDK版本支持 |
| ---------------------- | ---- | --------------------------------------------------------------------------- | ---------- | --------- |
| setAspectMode          | 无    | 设置数据采集模式，有 GrowingAspectModeSubClass 和 GrowingAspectModeDynamicSwizzling 两种 | ✔️         | ✔️        |
| setEnableDiagnose      | YES  | <p>是否允许发送基本性能诊断信息，默认为开。</p><p>基本性能指发送成功、失败、timeout等信息</p>                   | ✔️         | ✔️        |
| disable                | 无    | 全局不发送统计信息                                                                   | ✔️         | ✔️        |
| enableAllWebViews      | YES  | 全局设置是否采集 WKWebView 信息                                                       | ✔️         | -         |
| enableHybridHashTag    | YES  | 设置是否启用 Hash Tag                                                             | ✔️         | -         |
| isTrackingWebView      | YES  | 返回是否全局采集 WKWebView 信息                                                       | ✔️         | -         |
| setImp                 | NO   | 设置是否发送元素的展现次数（浏览量、曝光量）                                                      | ✔️         | -         |
| setFlushInterval       | 15s  | 设置发送数据的时间间隔，默认值为15秒                                                         | ✔️         | ✔️        |
| setDailyDataLimit      | 10MB | 设置每天使用数据网络（3G、4G、5G）上传的数据量的上限（单位是 KB），默认值为 10 MB                            | ✔️         | ✔️        |
| getDailyDataLimit      | 无    | 获取每天使用数据网络（3G、4G、5G）上传的数据量的上限（单位是 KB），默认值为10 MB                             | ✔️         | ✔️        |
| disableDataCollect     | 无    | 设置 GDPR 生效                                                                  | ✔️         | ✔️        |
| enableDataCollect      | 无    | 设置 GDPR 失效                                                                  | ✔️         | ✔️        |
| disablePushTrack       | YES  | 设置是否采集push推送点击，默认不采集                                                        | ✔️         | -         |
| setEnableLocationTrack | YES  | 设置是否采集地理位置的统计信息，默认采集                                                        | >=2.8.6    | -         |
| getEnableLocationTrack | 无    | 获取是否采集地理位置                                                                  | >=2.8.6    | -         |
| setReadClipBoardEnable | YES  | 设置是否读取剪切板                                                                   | >=2.9.8    | >=2.9.8   |
| setAsaEnabled          | NO   | 设置是否获取 Apple Search Ads 归因数据                                                | >=2.9.9    | >=2.9.9   |
