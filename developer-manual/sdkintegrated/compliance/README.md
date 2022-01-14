# 合规指南

**鉴于您需要使用GIO提供的服务，请您务必于使用GIO服务之前完成如下合规工作：**

## 1. 隐私政策指南

### 1.1. 收集和获取

在《隐私政策》中收集和获得最终用户的个人信息栏目中根据实际情况填写以下内容。当最终用户在激活使用时，我们会通过 SDK 收集最终用户的设备信息（例如：`IDFA`、`IDFV`、`操作系统`、`设备型号`、`系统版本`、`AndroidID`、`IMEI` 、`粘贴板内容`等）用于统计分析最终用户在 App 内的使用效果。

以下为各类SDK默认采集数据及设置方式，供参考。

{% tabs %}
{% tab title="IOS SDK" %}
| 字段               | 如何设置不采集                       |
| ---------------- | ----------------------------- |
| 页面               | -                             |
| 页面来源             | -                             |
| idfa             | 不集成了AdSupport.framework       |
| idfv             | -                             |
| 设备方向             | -                             |
| 屏幕高宽             | -                             |
| 设备品牌、型号          | -                             |
| 操作系统             | -                             |
| 操作系统版本           | -                             |
| 语言环境             | -                             |
| 剪切板-GIO设置的深度链接信息 | setReadClipBoardEnable(false) |
{% endtab %}

{% tab title="Android SDK" %}


| 字段               | 如何设置不采集                                     |
| ---------------- | ------------------------------------------- |
| 页面路径             | -                                           |
| 页面来源             | -                                           |
| 页面标题             | -                                           |
| imei             | configuration.setImeiEnable(false);         |
| adrid            | configuration.setAndroidIdEnable(false)     |
| gaid             | configuration.setGoogleAdIdEnable(false);   |
| oaid             | configuration.setOAIDEnable(false)          |
| 设备方向             | -                                           |
| 屏幕高宽             | -                                           |
| 设备品牌、型号          | -                                           |
| 操作系统             | -                                           |
| 操作系统版本           | -                                           |
| 语言环境             | -                                           |
| 剪切板-GIO设置的深度链接信息 | configuration.setReadClipBoardEnable(false) |
{% endtab %}

{% tab title="Web SDK" %}


| 字段   | 如何设置不采集 |
| ---- | ------- |
| 页面路径 | -       |
| 页面来源 | -       |
| 页面标题 | -       |
| 页面参数 | -       |
| 屏幕高宽 | -       |
| 语言环境 | -       |
| 设备类型 | -       |
{% endtab %}

{% tab title="小程序 SDK" %}


| 字段      | 如何设置不采集 |
| ------- | ------- |
| 网络类型    | -       |
| 页面路径    | -       |
| 页面来源    | -       |
| 页面参数    | -       |
| 设备类型    | -       |
| 屏幕高宽    | -       |
| 设备品牌、型号 | -       |
| 操作系统    | -       |
| 操作系统版本  | -       |
| 语言环境    | -       |
| 小程序场景值  | -       |
{% endtab %}
{% endtabs %}

### 1.2. 与授权合作伙伴共享

在《隐私政策》中的与授权合作伙伴共享栏目中根据实际情况填写以下内容：GrowingIO SDK：收集最终用户的设备信息（例如：`IDFA`、`IDFV`、`操作系统`、`设备型号`、`系统版本`、`AndroidID`、`IMEI` 、`粘贴板内容`等）用于数据分析，从而改进我们的产品和服务。

### 1.3. 设备信息说明

#### 1.3.1. IDFA

* 使用途径

`GrowingIO SDK` 会采集 `IDFA` 和 `IDFV` 字段上传，如果最终用户的项目中引入了 `AdSupport.framework`，会尝试获取 `IDFA`。除了 `IDFA` 和 `IDFV` 字段，SDK会生成 `设备标识` ，其值使用 `IDFA` `IDFV` 和 `UUID` ，三者的优先级为 `IDFA`> `IDFV` > `UUID` ，例如：如果获取不到 `IDFA`，SDK 会使用 `IDFV` 。

* 合规风险

当使用 `IDFA` 时有一定的合规风险，但是考虑到采集的准确性，GrowingIO仍然提供`IDFA`的采集方法，如果不需要采集`IDFA`，请在项目工程中去除 `AdSupport.framework` 的引用，并且不要在项目中导入 `AdSupport` 相关头文件。如果需要发布 `儿童级应用` ，完全不需要相关 `IDFA` 的获取逻辑，在 `iOS SDK >= 2.9.1` 版本之后，会默认提供一份 `不包含IDFA` 的SDK版本，并没有发布在 `Cocoapods` ，请自行在官网下载。

* 常见问题

1. Q1：App一开始禁止了`IDFA`权限，后续允许了`IDFA` 权限，数据会有什么变化？

A：对于`IDFA`，App生命周期内，`IDFA` 只会获取一次，就算后续 `IDFA` 权限打开了，也不会再获取，可以在下一次App启动后生效。对于 `设备标识`，仅且在 App第一次启动时生成，后续不再改变，优先级为 `IDFA`> `IDFV` > `UUID`，如果 `IDFA` 无法获取，则会使用`IDFV` 且不再变动，会存入`Keychain`，卸载也无法修改。如果要`设备标识` 和 `IDFA` 绑定，则需要在用户同意 `IDFA`权限之后进行第一次SDK初始化操作。

#### 1.3.2. AndroidId

`GrowingIO SDK`在采集 `设备标识` 时，会默认采集 `AndroidId`，有一定的合规风险，但是考虑采集的准确性，GrowingIO 仍然提供 AndroidId 的采集方法，如果最终用户不需要采集 AndroidId，请配置`Configuration`

```
configuration.setAndroidIdEnable(false);
```

无埋点版本SDK可以通过gradle配置关闭AndroidId采集

```
growingio {
    defaultConfig {
        androidIdEnable f​alse
    }
}
```

#### 1.3.3. IMEI

在使用渠道追踪功能时，`GrowingIO SDK`会使用到 IMEI。如果最终用户不想采集，需要配置`Configuration`

```
configuration.setImeiEnable(false);
```

无埋点版本SDK可以通过gradle配置关闭IMEI采集

```
growingio {
    defaultConfig {
        imeiEnable f​alse
    }
}
```

#### 1.3.4. GoogleAdId

在使用渠道追踪功能时，`GrowingIO SDK`会使用到 GoogleAdId。如果最终用户不想采集，需要配置`Configuration`

```
configuration.setGoogleAdIdEnable(false);
```

无埋点版本SDK可以通过gradle配置关闭GoogleAdId采集

```
growingio {
    defaultConfig {
        googleAdIdEnable f​alse
    }
}
```

#### 1.3.5. OAID

在使用渠道追踪功能时，`GrowingIO SDK`会使用到 OAID。如果最终用户不想采集，需要配置`Configuration`

```
configuration.setOAIDEnable(false)
```

无埋点版本SDK可以通过gradle配置关闭OAID采集

```
growingio {
    defaultConfig {
        oaidEnable false
    }
}
```

## 2. SDK 如何支持合规

### 2.1 Android 合规步骤

SDK 在 `2.8.25` 版本及以上提供了合规接口，可以设置在最终用户同意您平台的《隐私政策》后，开启数据采集。具体可以参考以下步骤：最终用户未同意您平台的隐私条款时，可以在 SDK 初始化配置时调用 `disableDataCollect()` 来禁用数据采集（不获取 AndroidId，不获取任何设备信息，也不上报数据）。

```
GrowingIO.startWithConfiguration(this, new Configuration()
                ...
                . disableDataCollect()
                ...
                );
```

当最终用户同意您平台的隐私条款时，调用如下接口，开启数据采集。

```
GrowingIO.getInstance().enableDataCollect();
```

> 注意：
>
> 1\. 第一次打开 App 后，在最终用户同意《隐私条款》前的所有事件不会采集。2. SDK Version > 2.8.25，enableDataCollect 会在调用了 disableDataCollect 且初始化了 SDK的前提下补发 visit 事件

### 2.2 iOS 合规步骤

因为在 `iOS 14` 之后的IDFA权限需要最终用户授权，需要同意您平台的`隐私条款`之后才能获取到IDFA。

* iOS SDK 在 2.9.1 之前，需要您确保最终用户在同意您平台的`隐私条款`后初始化 SDK。

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
  if (同意隐私条款) {
    //初始化 SDK
    [Growing startWithAccountId:@"xxxxxxxxxxx"];
  }
   
  ...
  return YES;
}
```

* 在 2.9.1 之后，在最终用户同意您平台的`隐私条款`前调用`disableDataCollect`，并初始化SDK ，待最终用户同意您平台的`隐私条款`后调用 `enableDataCollect`

```
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
>
> 1\. 第一次打开 App 后，在最终用户同意《隐私条款》前的所有事件不会采集。2. SDK Version > 2.9.1，enableDataCollect 会在调用了 disableDataCollect 且初始化了 SDK的前提下补发 visit 事件

#### 2.3 常见问题

Q1：延迟初始化之后，发现丢掉了部分事件

&#x20;A：对于SDK初始化之前，或者`enableDataCollect` 之前的数据，一概丢弃。

&#x20;Q2：发现部分事件沿用了上一次的 `SessionID`

&#x20;A：请使用最新版本 `iOS >= 2.9.1` ，`Android >= 2.8.25`，`SessionID` 需要伴随 `Visit` 事件重置，如果事件发送在 `SDK初始化` 之后，`Visit` 事件之前，则会使用上一次的 `SessionID` ，属于已知问题。

Q3：发现App启动后丢了`Visit`事件，其他事件正常

&#x20;A：请使用最新版本 `iOS >= 2.9.1` ，`Android >= 2.8.25` ，对于延迟初始化，老版本没有补发 `Visit` 事件，请升级版本，并按照 `合规步骤` 进行集成。

Q4：发现App访问时长超长

&#x20;A：请使用最新版本 `iOS >= 2.9.1` ，`Android >= 2.8.25` ，`SessionID` 需要伴随 `Visit` 事件重置，如果事件发送在 `SDK初始化` 之后，`Visit` 事件之前，则会使用上一次的 `SessionID` ，导致访问时长超长，属于已知问题，同Q2。

## 3. App Store 广告标识符（IDFA）说明

SDK 不会主动获取 `IDFA 权限`，您需要自行获取 `IDFA 权限`, 请参考 [埋点 SDK集成](https://docs.growingio.com/v3/developer-manual/sdkintegrated/ios-sdk/manunl-ios-sdk#3-app-store-ti-jiao-ying-yong-zhu-yi-shi-xiang) 。

## 4. App Store 隐私问题

苹果在 iOS 14.3 系统更新了隐私政策，要求 App 更新或发布时需要发布者填写一份隐私报告。此时如果 App 集成 GrowingIO SDK 应该如何填写。

1\. 选择 「是，会从此 App 中收集数据」

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.15.03 (1).png>)

2\. GrowingIO 不会主动申请采集位置信息，如果您的App申请获取了位置信息，GrowingIO就会采集位置信息用于定位用户城市级别的位置，需要勾选 「精准位置」

> 如果你想禁用位置信息获取，调用 `+setEnableLocationTrack:` 为 `NO`

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.19.49.png>)

3\. 默认情况下只需选择 「设备 ID」。如果使用的是 `无埋点SDK` 需继续选择 「产品交互」。如果使用最终用户关联，即调用 `+setUserId:`接口则还需勾选 「用户 ID」，如图

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.21.52.png>)

4\. 如果您使用了 `GrowingMonitorKit` 并调用`+setUploadExceptionEnable:` 方法开启了Crash监控上报，您还需要勾选 「崩溃数据」，如图：

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.24.12 (2).png>)

储后会在您的 App 隐私页面根据我们的选择生成一些列收集类型面板，点击对应面板后可以继续做详细的选择，下面会详细介绍。

### 4.1 位置

1.请在 「位置」面板中，勾选 「分析」

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.29.04 (1).png>)

2\. 然后下一步，勾选「**是**，从此 App 中收集的精确位置数据与用户身份关联」

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.31.00.png>)

3\. 根据您的App实际情况选择是否用于追踪目的。

### 4.2 最终用户 ID

1\. GrowingIO SDK 会在调用 `+setUserId:`接口时收集最终用户 id 用于分析功能，因此这里选择「分析」，如图 ：

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.32.10.png>)

&#x20;2\. 勾选后点击下一步，选择「**是**，从此 App 中收集的用户 ID 与用户身份关联」，这里根据具体的业务进行勾选，如图 ：

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.32.33 (1).png>)

3\. 点击下一步，需要选择「**是**，我们会将用户 ID 用于追踪目的」

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.34.49.png>)

### 4.3 设备

1\. GrowingIO SDK 收集设备 id 用于收集最终用户登录前的数据，因此这里继续选择「分析」，如图 :

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.36.09.png>)

2\. 点击下一步，因为收集到的数据会与设备 id 绑定，所以此处继续选择「是」

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.37.28 (1).png>)

3\. 继续下一步，同最终用户 ID ， 会使用 IDFA 与第三方数据相关联以用于定向广告或广告评估目的，如图 ：

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.40.35.png>)

### 4.4 产品交互

1\. 使用 GrowingIO 无埋点SDK后，会收集 `APP启动`，`APP退出`，`用户点击`，`页面浏览`等相关行为用于`分析产品`，因此这里继续选择「分析」，如图 ：

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.42.05.png>)

2\. 点击下一步，继续选择是，如图 ：

![](<../../../.gitbook/assets/截屏2021-10-11 上午10.43.03 (1).png>)

3\. 最后追踪目的，请根据您实际情况选择，是否要用于追踪目的。

## 5. GrowingIO SDK 合规性说明

GrowingIO SDK 默认收集的数据类型只有「设备 ID」和「用户 ID」主要用于追踪，其他的数据类型采集需要根据您自己的采集业务以及选择的SDK 功能来做相应选择：

* 调用 `+setUserId:`接口：需选择「用户 ID」
* 使用无埋点 SDK：需选择「产品交互」
* 开启崩溃收集：需选择「崩溃数据」
* 开启经纬度采集：需选择「精确位置」

**尽管有上述指南，您应知晓并同意，上述仅为指导性建议，您仍应根据相应管辖国家的法律的调整和更新，以及您自己的业务实际情况，及时调整、更新您平台或APP的隐私政策，以保证您在收集、使用最终用户信息时合法合规，且有充分的权利授权GIO为了向您提供服务的目的收集、使用必要的最终用户信息。否则，您不得使用GIO的任何服务。**

## **6. 隐私条款**

除上述指南外，您还必须知晓并同意GIO企业客户隐私政策，具体如下链接：

[https://accounts.growingio.com/privacy](https://accounts.growingio.com/user-privacy)

GIO亦根据中国法律法规的要求制定了GIO关于最终用户个人信息的隐私政策，具体如下链接，您可以根据您平台或APP隐私政策的需要，选择是否向最终用户公开：

[https://accounts.growingio.com/user-privacy](https://accounts.growingio.com/user-privacy)

您应知晓，GIO会不时更新该合规指南。届时，GIO会通知您具体更新的内容，还请您参考新的合规指南完成合规性操作。
