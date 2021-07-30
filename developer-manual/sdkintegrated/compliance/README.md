# 合规指南

## 1. 隐私政策填写

### 1.1. 收集和获取

在《隐私政策》中收集和获得您的个人信息栏目中根据实际情况填写以下内容。当您在激活使用时，我们会通过 SDK 收集您的设备信息（例如：`IDFA`、`IDFV`、`操作系统`、`设备型号`、`系统版本`、`AndroidID`、`IMEI` 等）用于统计分析您在 App 内的使用效果。

### 1.2. 与授权合作伙伴共享

在《隐私政策》中的与授权合作伙伴共享栏目中根据实际情况填写以下内容。GrowingIO SDK：收集您的设备信息（例如：`IDFA`、`IDFV`、`操作系统`、`设备型号`、`系统版本`、`AndroidID`、`IMEI` 等）用于数据分析，从而改进我们的产品和服务。

### 1.3. 设备信息说明

#### 1.3.1. IDFA

* 使用途径

`GrowingIO SDK` 会采集 `IDFA` 和 `IDFV` 字段上传，如果您的项目中引入了 `AdSupport.framework`，会尝试获取 `IDFA`。除了 `IDFA` 和 `IDFV` 字段，SDK会生成 `设备标识` ，其值使用 `IDFA` `IDFV` 和 `UUID` ，三者的优先级为 `IDFA`&gt; `IDFV` &gt; `UUID` ，例如：如果获取不到 `IDFA`，SDK 会使用 `IDFV` 。

* 合规风险

当使用 `IDFA` 时有一定的合规风险，但是考虑到采集的准确性，GrowingIO仍然提供`IDFA`的采集方法，如果不需要采集`IDFA`，请在项目工程中去除 `AdSupport.framework` 的引用，并且不要在项目中导入 `AdSupport` 相关头文件。如果需要发布 `儿童级应用` ，完全不需要相关 `IDFA` 的获取逻辑，在 `iOS SDK >= 2.9.1` 版本之后，会默认提供一份 `不包含IDFA` 的SDK版本，并没有发布在 `Cocoapods` ，请自行在官网下载。

* 常见问题

1. Q1：App一开始禁止了`IDFA`权限，后续允许了`IDFA` 权限，数据会有什么变化？

A：对于`IDFA`，App生命周期内，`IDFA` 只会获取一次，就算后续 `IDFA` 权限打开了，也不会再获取，可以在下一次App启动后生效。对于 `设备标识`，仅且在 App第一次启动时生成，后续不再改变，优先级为 `IDFA`&gt; `IDFV` &gt; `UUID`，如果 `IDFA` 无法获取，则会使用`IDFV` 且不再变动，会存入`Keychain`，卸载也无法修改。如果要`设备标识` 和 `IDFA` 绑定，则需要在用户同意 `IDFA`权限之后进行第一次SDK初始化操作。

#### 1.3.2. AndroidId

`GrowingIO SDK`在采集 `设备标识` 时，会默认采集 `AndroidId`，有一定的合规风险，但是考虑采集的准确性，GrowingIO 仍然提供 AndroidId 的采集方法，如果您不需要采集 AndroidId，请配置`Configuration`

```text
configuration.setAndroidIdEnable(false);
```

无埋点版本SDK可以通过gradle配置关闭AndroidId采集

```text
growingio {
    defaultConfig {
        androidIdEnable f​alse
    }
}
```

#### 1.3.3. IMEI

在使用渠道追踪功能时，`GrowingIO SDK`会使用到 IMEI。如果您不想采集，需要配置`Configuration`

```text
configuration.setImeiEnable(false);
```

无埋点版本SDK可以通过gradle配置关闭IMEI采集

```text
growingio {
    defaultConfig {
        imeiEnable f​alse
    }
}
```

#### 1.3.4. GoogleAdId

在使用渠道追踪功能时，`GrowingIO SDK`会使用到 GoogleAdId。如果您不想采集，需要配置`Configuration`

```text
configuration.setGoogleAdIdEnable(false);
```

无埋点版本SDK可以通过gradle配置关闭GoogleAdId采集

```text
growingio {
    defaultConfig {
        googleAdIdEnable f​alse
    }
}
```

#### 1.3.4. OAID

在使用渠道追踪功能时，`GrowingIO SDK`会使用到 OAID。如果您不想采集，需要配置`Configuration`

```text
configuration.setOAIDEnable(false)
```

无埋点版本SDK可以通过gradle配置关闭OAID采集

```text
growingio {
    defaultConfig {
        oaidEnable false
    }
}
```

## 2. SDK 如何支持合规

### 2.1 Android 合规步骤

SDK 在 `2.8.25` 版本及以上提供了合规接口，可以设置在用户同意《隐私政策》后，开启数据采集。具体可以参考以下步骤：用户未同意隐私条款时，可以在 SDK 初始化配置时调用 `disableDataCollect()` 来禁用数据采集（不获取 AndroidId，不获取任何设备信息，也不上报数据）。

```text
GrowingIO.startWithConfiguration(this, new Configuration()
                ...
                . disableDataCollect()
                ...
                );
```

当用户同意隐私条款时，调用如下接口，开启数据采集。

```text
GrowingIO.getInstance().enableDataCollect();
```

> 注意：

1. > 第一次打开 App 后，在最终用户同意《隐私条款》前的所有事件不会采集。
2. > SDK Version &gt; 2.8.25，enableDataCollect 会在调用了 disableDataCollect 且初始化了 SDK的前提下补发 visit 事件

### 2.2 iOS 合规步骤

因为在 `iOS 14` 之后的IDFA权限需要用户授权，需要同意`隐私条款`之后才能获取到IDFA。

* iOS SDK 在 2.9.1 之前，需要您确保用户在同意`隐私条款`后初始化 SDK。

```text
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
  if (同意隐私条款) {
    //初始化 SDK
    [Growing startWithAccountId:@"xxxxxxxxxxx"];
  }
   
  ...
  return YES;
}
```

* 在 2.9.1 之后，在用户同意`隐私条款`前调用`disableDataCollect`，并初始化SDK ，待用户同意`隐私条款`后调用 `enableDataCollect`

```text
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
  [Growing disableDataCollect];
  // Override point for customization after application launch.
  [Growing startWithAccountId:@"xxxxxxxxxxx"];
  
  ...
  return YES;
}
//某一时刻用户同意了隐私条款,允许获取idfa
- (void)userAcceptIDFAPrivacy {
  ...
  [Growing enableDataCollect];
  ...
}
```

> 注意：

1. > 第一次打开 App 后，在最终用户同意《隐私条款》前的所有事件不会采集。
2. > SDK Version &gt; 2.9.1，enableDataCollect 会在调用了 disableDataCollect 且初始化了 SDK的前提下补发 visit 事件

#### 2.3 常见问题

1. Q1：延迟初始化之后，发现丢掉了部分事件

 A：对于SDK初始化之前，或者`enableDataCollect` 之前的数据，一概丢弃。

1. Q2：发现部分事件沿用了上一次的 `SessionID`

 A：请使用最新版本 `iOS >= 2.9.1` ，`Android >= 2.8.25`，`SessionID` 需要伴随 `Visit` 事件重置，如果事件发送在 `SDK初始化` 之后，`Visit` 事件之前，则会使用上一次的 `SessionID` ，属于已知问题。

1. Q3：发现App启动后丢了`Visit`事件，其他事件正常

 A：请使用最新版本 `iOS >= 2.9.1` ，`Android >= 2.8.25` ，对于延迟初始化，老版本没有补发 `Visit` 事件，请升级版本，并按照 `合规步骤` 进行集成。

1. Q4：发现App访问时长超长

 A：请使用最新版本 `iOS >= 2.9.1` ，`Android >= 2.8.25` ，`SessionID` 需要伴随 `Visit` 事件重置，如果事件发送在 `SDK初始化` 之后，`Visit` 事件之前，则会使用上一次的 `SessionID` ，导致访问时长超长，属于已知问题，同Q2。

## 3. App Store 广告标识符（IDFA）说明

SDK 不会主动获取 `IDFA 权限`，您需要自行获取 `IDFA 权限`, 请参考 [埋点 SDK集成](https://docs.growingio.com/v3/developer-manual/sdkintegrated/ios-sdk/manunl-ios-sdk#3-app-store-ti-jiao-ying-yong-zhu-yi-shi-xiang) 。

## 4. App Store 隐私问题

苹果在 iOS 14.3 系统更新了隐私政策，要求 App 更新或发布时需要发布者填写一份隐私报告。此时如果 App 集成 GrowingIO SDK 应该如何填写。

1. 选择 「是，会从此 App 中收集数据」

![](https://growingio.feishu.cn/space/api/box/stream/download/asynccode/?code=OWQ1YjJiMmQxMDA0MTVhZDYwZjgwNjE4MDQ3ZGYyMTNfZGYzOHkxU09lQ3ZZc1ZuYklMSG1EM3Y4ZTJGM0s4cFNfVG9rZW46Ym94Y256VkIzaFlqdG4xUGtYMTdpaU9LUEpoXzE2Mjc2MzU3Njc6MTYyNzYzOTM2N19WNA)

1. GrowingIO 不会主动申请采集位置信息，如果客户的App申请获取了位置信息，GrowingIO就会采集位置信息用于定位用户城市级别的位置，需要勾选 「精准位置」

> 如果你想禁用位置信息获取，调用 `+setEnableLocationTrack:` 为 `NO`

![](https://growingio.feishu.cn/space/api/box/stream/download/asynccode/?code=MjExMjdiYjMxOWVmZmIyMDliNDZhZWNhOWMyNzAwMDFfMWU1QXk4akt3Tm9NRHlXVHA5cGM5YmtRQjNKWXV0RTlfVG9rZW46Ym94Y25yM3NQN2pnbldzb2FjSnl4anJ5MENkXzE2Mjc2MzU3Njc6MTYyNzYzOTM2N19WNA)

1. 默认情况下只需选择 「设备 ID」。如果使用的是 `无埋点SDK` 需继续选择 「产品交互」。如果使用用户关联，即调用 `+setUserId:`接口则还需勾选 「用户 ID」，如图

![](https://growingio.feishu.cn/space/api/box/stream/download/asynccode/?code=OTY2YzBlODg4Y2I2NDM4YzE0NWIzNjJiYjViYTRkNzdfWjNqVFFsTjRTbGJDYXRITTBGOHl3Mzgwc05TaGd6aFpfVG9rZW46Ym94Y25VZDNodXkxbU8yc2JsbkFpVThEUnJkXzE2Mjc2MzU3Njc6MTYyNzYzOTM2N19WNA)

1. 如果你使用了 `GrowingMonitorKit` 并调用`+setUploadExceptionEnable:` 方法开启了Crash监控上报，你还需要勾选 「崩溃数据」，如图：

![](https://growingio.feishu.cn/space/api/box/stream/download/asynccode/?code=NDJjYzI5NDNiODIwYzBiMTViNzdkMzM4NjM0YTQ2NGJfb0RhTHZGeWphOUMzVmZSdE1jaHhOME5sT2Fua0lYTjVfVG9rZW46Ym94Y25CdTUxU2NJeU1yWWRmM08xcVMxQm9mXzE2Mjc2MzU3Njc6MTYyNzYzOTM2N19WNA)存储后会在 App 隐私页面根据我们的选择生成一些列收集类型面板，点击对应面板后可以继续做详细的选择，下面会详细介绍。

### 4.1 位置

1. 请在 「位置」面板中，勾选 「分析」

![](https://growingio.feishu.cn/space/api/box/stream/download/asynccode/?code=YzA4ODQ4MGFlOTRiMzY2MWM4NTc4OTc5MWE4YWZmMDNfZmQ1Zm1pNTVLRGNMQVp5UWkxVHhNbGphaWdQWVgwRWtfVG9rZW46Ym94Y25JN2FTMGNFVENrUEVybERiWlRKTG5oXzE2Mjc2MzU3Njc6MTYyNzYzOTM2N19WNA)

1. 然后下一步，勾选「**是**，从此 App 中收集的精确位置数据与用户身份关联」

![](https://growingio.feishu.cn/space/api/box/stream/download/asynccode/?code=OWI5YzJkOWY5ODIxZDMzMjljOTI5ZTcxNTU4ODZlMjZfbWluaGNqblNtd21HWmk4Q2FOeURhYzMzdWVRbkdPQUlfVG9rZW46Ym94Y255bk1aZlVYeWFFMUdvUXJKOE5GN2wxXzE2Mjc2MzU3Njc6MTYyNzYzOTM2N19WNA)

1. 根据您App实际情况选择是否用于追踪目的。

### 4.2 用户 ID

1. GrowingIO SDK 会在调用 `+setUserId:`接口时收集用户 id 用于分析功能，因此这里选择「分析」，如图 ：

![](https://growingio.feishu.cn/space/api/box/stream/download/asynccode/?code=OGM1NTk1YWI0ZWRlMDBmZjIwZjNjMGQ3ZGVjYWY2MmVfVnUwb20yREZmbXpuZ1k0UU9VMWJVZ1FKcUV5dEF5MzJfVG9rZW46Ym94Y253NXJ5bUd6SWlsc2NSZGZKZmNpZFhoXzE2Mjc2MzU3Njc6MTYyNzYzOTM2N19WNA)

1. 勾选后点击下一步，选择「**是**，从此 App 中收集的用户 ID 与用户身份关联」，这里根据具体的业务进行勾选，如图 ：

![](https://growingio.feishu.cn/space/api/box/stream/download/asynccode/?code=ODM1NzA0NGU5M2E3YzlhMWE5ZGFmZTI5YzUzMGRlMGFfbVFaUDQ3OE80T0x5YUw3NWc4aWx6aUs2WVdzWWJRWE5fVG9rZW46Ym94Y25Ka3MzOWRJTERnckVmUjZhZUdISzNkXzE2Mjc2MzU3Njc6MTYyNzYzOTM2N19WNA)

1. 点击下一步，需要选择「**是**，我们会将用户 ID 用于追踪目的」

![](https://growingio.feishu.cn/space/api/box/stream/download/asynccode/?code=NmQwZjBlMTgyNTE4MzE4MjRmYzRiNmQ5N2QwZWViMmRfU1ozYklWRUtjTWNxbVNUMklnYWNCR1ZiV2JPM1lQcVVfVG9rZW46Ym94Y25JM3Fwblo3bDhSaVpDbjFHdm5QMDhjXzE2Mjc2MzU3Njc6MTYyNzYzOTM2N19WNA)

### 4.3 设备

1. GrowingIO SDK 收集设备 id 用于收集用户登录前的数据，因此这里继续选择「分析」，如图 :

![](https://growingio.feishu.cn/space/api/box/stream/download/asynccode/?code=YzYyOGYxZDg0ZGY2NmE1MGM2NDhkZmQ2YjVkZGMxNjRfVjZjSnJtbmh5VVFLQUNVcW5pNGNaMUluUTZJV2JJanRfVG9rZW46Ym94Y25DQ0FtYkZqN3k0WEJzMnJ3M2duT3BlXzE2Mjc2MzU3Njc6MTYyNzYzOTM2N19WNA)

1. 点击下一步，因为收集到的数据会与设备 id 绑定，所以此处继续选择「是」

![](https://growingio.feishu.cn/space/api/box/stream/download/asynccode/?code=OWQwZDNhOGM5NDA0NzkyZWM5MzRlZGMyZWM4ZTAwMjhfVUR5eUZ2blc5VEtGOFBCa2VqQWplelJWdkxtV1VTeUNfVG9rZW46Ym94Y25ibkNJTHBZYmdROFIxbEN2MVRSMUJiXzE2Mjc2MzU3Njc6MTYyNzYzOTM2N19WNA)

1. 继续下一步，同用户 ID ， 会使用 IDFA 与第三方数据相关联以用于定向广告或广告评估目的，如图 ：

![](https://growingio.feishu.cn/space/api/box/stream/download/asynccode/?code=NWU1YjhlMDkyYjBjMGU0ODhiMTFmN2U0OTgxMGY2Mjhfa0hDRWhsNXIwRUw3MFZxdnM0b3R2SUg3dUtEM2lkWm5fVG9rZW46Ym94Y25jRTNNdEZNN21tN1FYNVRKeHA2cU5lXzE2Mjc2MzU3Njc6MTYyNzYzOTM2N19WNA)

### 4.4 产品交互

1. 使用 GrowingIO 无埋点SDK后，会收集 `APP启动`，`APP退出`，`用户点击`，`页面浏览`等相关行为用于`分析产品`，因此这里继续选择「分析」，如图 ：

![](https://growingio.feishu.cn/space/api/box/stream/download/asynccode/?code=YjNkNjllMGQxNmYxMGMzNjM5OWFiYzVkODBlMzUyZTJfMTVDV2ZDYUxkemZmNkNrU1ZJNlJxNmd5S0VrV2JYWHFfVG9rZW46Ym94Y25wem51dTlqTGpjaGo1UUZod3l0UkdlXzE2Mjc2MzU3Njc6MTYyNzYzOTM2N19WNA)

1. 点击下一步，继续选择是，如图 ：

![](https://growingio.feishu.cn/space/api/box/stream/download/asynccode/?code=ZjIyOWMwNTdhMmI3ZTA3MWVlZjMxZGNiNTI1YTg5NGRfTEZvSERwNzJIN3lRUWhhbVp6NnFEa3dUc0tScGJzZWVfVG9rZW46Ym94Y24zeUIxVFAzNU90VnpXQkxhTHE4eDJiXzE2Mjc2MzU3Njc6MTYyNzYzOTM2N19WNA)

1. 最后追踪目的，请根据您实际情况选择，是否要用于追踪目的。

## 5. GrowingIO SDK 合规性说明

GrowingIO SDK 默认收集的数据类型只有「设备 ID」和「用户 ID」主要用于追踪，其他的数据类型采集需要根据自己的采集业务以及选择的SDK 功能来做相应选择：

* 调用 `+setUserId:`接口：需选择「用户 ID」
* 使用无埋点 SDK：需选择「产品交互」
* 开启崩溃收集：需选择「崩溃数据」
* 开启经纬度采集：需选择「精确位置」

另，该隐私政策的填写是可以更改的。**请根据自己 App 业务的调整及时更新隐私政策。**

1. **隐私条款**

[https://accounts.growingio.com/privacy](https://accounts.growingio.com/privacy)

