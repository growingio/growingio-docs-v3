# 深度链接配置-done

深度链接（DeepLink）是通过链接启动应用的方法。更详细地说是通过映射预定义行为到唯一的链接上，让用户通过点击链接无缝跳转到特定的内容页面。

对于支持深度链接功能的移动应用，用户可以在其他处点击应用提供的深度打开应用，也可跳转到应用内指定页面，如首页、产品详情页面等。

## 1 进入深度链接配置模块

一. 在顶部导航栏选择“**获客分析 &gt; 广告监测”**，进入广告监测模块。

二. 在左侧导航栏选择“**高级设置 &gt; 深度链接配置”**，进入深度链接配置页面。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%286%29.png)

## 2 iOS 应用配置

找到需要配置的 iOS 应用，查看当前应用的配置。其中将包含所有当前应用的全部 DeepLink 配置信息。

### **2.1 查看应用基本信息**

其中包含当前应用的基本信息配置，如果您需要更改此处信息，请单击「前往应用管理」进行更改。

也可直接在应用管理中心修改，请参考[修改应用信息](../../xiang-mu-guan-li/application-manage.md#xiu-gai-shan-chu-ying-yong)。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LtP41qSBliAk88VA3Xe-LtPJ9y2NR46v9RUT5xLimage.png)

### 2.2 Universal Links配置

Universal Links 是 Apple 在 iOS 系统中提供的原生方案，如果您希望在 DeepLink 流程中达成更好的跳转体验，需对此进行配置。

而UniversalLink跳转方式可以实现无缝跳转，当浏览器识别到预先指定好的URL，就可以直接唤醒App，不需要在浏览器中打开再去点击其他按钮。

{% hint style="info" %}
Universal Links 适用于 iOS 9 及以上的版本，当用户设备系统版本在 iOS 9 以下时，DeepLink 将会自动回落至 URL Scheme 方案进行跳转。
{% endhint %}

#### **2.2.1 获取Team ID**

1、在您的 Xcode 中勾选 **Associated Domains** 功能。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2892%29.png)

1. 添加 GrowingIO域名到 Xcode。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2814%29.png)

{% hint style="info" %}
GrowingIO的域名：

`applinks:gio.ren`

`applinks:datayi.cn`
{% endhint %}

1. 在苹果开发者网站中找到 Team ID 与 Bundle ID，如下图。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28206%29.png)

#### **2.2.2 将 Team ID 配置到 GrowingIO 后台。**

1.在UniversalLink模块，单击模块右上角的编辑，进入配置 UniversalLink界面。

配置获取到的Team ID 并勾选“我已完成Xcode配置，开启Universal Link跳转”，同时确认您的 SDK 版本并进行确认。

{% hint style="info" %}
若以上配置完成后，且App端已经完成SDK集成，请勾选”我已完成Xcode配置，开启UniversalLink跳转“；如果SDK版本为2.8.4及以上，请勾选”已确认将iOS SDK升级至2.8.4或更高版本“将开启DeepLink 2.0方案，将获得更好的使用体验。
{% endhint %}

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LtP41qSBliAk88VA3Xe-LtPKKsn2R69VKrS_DHfimage.png)

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28125%29.png)

## 3 Android 应用配置

找到需要配置的 Android 应用，查看当前应用的配置。其中将包含所有当前应用的全部 DeepLink 配置信息。

### **3.1 查看应用基本信息**

其中包含当前应用的基本信息配置，如果您需要更改此处信息，请单击「前往应用管理」进行更改。

也可直接在应用管理中心修改，请参考[修改应用信息](../../xiang-mu-guan-li/application-manage.md#xiu-gai-shan-chu-ying-yong)。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LtPeN51XOz8pL5J28rs-LtPetuUHeUEFwBh_438image.png)

### 3.2 AppLinks配置

App Links 是 Google 在 Android 系统中提供的原生方案，如果您希望在 DeepLink 流程中达成更好的跳转体验，需对此进行配置。

App Links 适用于 Android 6.0 及以上的版本，当用户设备系统版本在 Android 6.0 以下时，DeepLink 将会自动回落至 URL Scheme 方案进行跳转。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LtPeya7y9j-Tf-SYwGB-LtPfdFJ_k7EIOVL8W14image.png)

详细配置步骤：

#### **3.2.1 获取应用签名 SHA256 指纹证书**

1.使用命令行进入你的证书目录，一般签名分为 debug keystore 和 release keystore ，开发期间建议先配置为 debug keystore ，上线前一定要更新为 release keystore 。如果担心忘记，建议新建应用。

1. 执行以下命令 ：

```text
keytool -list -v -keystore my-release-key.keystore
```

1. 执行后你将看到类似下面这样的结果，请复制下来并填写进 GrowingIO 对应的应用配置中。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LtPeya7y9j-Tf-SYwGB-LtPfGzEMvdZaL6PZwtk-LGNxeGABUADKiTWTaEM-Lqj1ayCSvZ98vlMMoj_-LqjDzowsF3cf7B2QR5gimage.png)

#### **3.2.2 在 Manifest.xml 中配置 Intent Filter**

1. 点击「复制代码片段」
2. 进入您的安卓应用源码中的 manifest.xml 文件中，找到您的主页面，建议复制在主页，即为 Launcher Activity 中。
3. 复制完成后，您的 manifest.xml 文件将**类似**这样：

```markup
  <activity
            android:name=".LauncherActivity"
            android:launchMode="singleTop"
            android:theme="@style/AppTheme">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
​
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>

            <!-- GIO 集成配置，使用圈选和 Debugger 等功能用作唤醒 APP-->
            <intent-filter>
                <data android:scheme="growing.xxxxxxxxxxxxxx" />

                <action android:name="android.intent.action.VIEW" />

                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />
            </intent-filter>

            <!-- GIO APPLinks 配置，广告监测用途，APP 用户点击广告监测短链直接跳转 APP-->
            <intent-filter android:autoVerify="true">
                <action android:name="android.intent.action.VIEW" />
​
                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />
​
                <data
                    android:host="gio.ren"
                    android:pathPattern="/xxxxx.*"
                    android:scheme="https" />
                <data
                    android:host="gio.ren"
                    android:pathPattern="/xxx.*xx.*"
                    android:scheme="https" />
                <data
                    android:host="gio.ren"
                    android:pathPattern="/xxx.*xx.*"
                    android:scheme="https" />
                <data
                    android:host="datayi.cn"
                    android:pathPattern="/xxxxx.*"
                    android:scheme="https" />
                <data
                    android:host="datayi.cn"
                    android:pathPattern="/xxx.*xx.*"
                    android:scheme="https" />
                <data
                    android:host="datayi.cn"
                    android:pathPattern="/xxx.*xx.*"
                    android:scheme="https" />
            </intent-filter>
​
        </activity>
```

{% hint style="danger" %}
* GrowingIO 暂不支持自定义 App Links 的 host，请不要修改复制的代码块中的 host；
* 建议不要尝试修改或者合并 GIO 的 intent filter ，[Google 官方解释](https://developer.android.com/training/app-links/deep-linking#adding-filters)。
* **Android 集成步骤中添加的 growing.xxxxxx 的 Intent Filter 不能与此处合并，请将两个 Intent Filter  分开写在 Launcher Activity 下。**
{% endhint %}

**3.2.3 验证您的 App Links**

1. 完成上述配置后，安装在手机上
2. 执行以下命令：

```text
adb shell dumpsys package d
```

1. 上述命令执行后的结果中，查找您应用的包名，当 Domains 已经出现 datayi.cn/ gio.ren 说明您的 Intent Filter 配置正确，示例如下：

```text
  Package: com.growingio.android.test    
  Domains: datayi.cn gio.ren  
  Status:  always
```

{% hint style="info" %}
domains 为 manifest.xml 文件中配置 Intent filter 中的 host ，GIO 可能后续会更改广告的域名，一切以您复制得到的代码片段为准即可。
{% endhint %}

#### 3.2.4 测试 App Links 唤起方式

当您 App Links 所有的环节已经配置完成后，可以利用测试设备测试唤起效果，测试步骤如下：

1、创建一条用于测试的 DeepLink ；

2、在测试设备中原生场景下进行测试，如：短信、备忘录等等；

（不要直接在第三方软件中进行测试，例如微信。第三方软件通常对 DeepLink 跳转存在限制）

3、点击测试 DeepLink，如果可以直接跳转到 App 中，说明可以直接唤起 App，为最理想流程。

4、如果未直接跳转到 App 中，而是跳入下载引导中间页，并且系统弹窗询问是否要在应用中打开，此时可以通过【步骤三】Status 中查看状态，如果状态显示为“ask”，并且确认 App Links 集成流程正确无误，则可能是当前测试设备机型在 AppLinks 遇到校验问题，对于该情况请参考下方常见问题说明。

对于 Status 状态的说明：

| Status 状态 | 描述 |
| :--- | :--- |
| ask | Applink校验失败, 每次打开连接跳转时会弹出一个对话框， 提示选择打开短链的App |
| always | 校验成功，理想状态 |
| never | 用户选择不再打开 |
| always-ask | 可忽略，尚未发现这一个出现, 跟 never 一样需要手动干预才会出现 |
| undefined | 尚未校验完成， 请稍后再试 |

**常见问题：**

**1.多数客户可能会在验证环节得到的 Status 为 ask，这是为什么呢？**

App _\*\*_Links 的合法性是由系统校验，不同的手机系统使用不同的校验组件，即使是一个厂商的不同型号手机都可能使用不同的校验组件。

如果系统使用 com.android.statementservice 进行 AppLinks 的校验，在网络正常的情况下基本都能顺利通过， 如果系统使用 com.google.android.gms 组件校验，在手机能够科学上网的情况，也就是能够正常访问 Google 时，校验才能通过。常见华为 mate 系列，P 系列使用的都是 gms，也就是 Status 会为 ask。

查看自己手机是使用哪种组件，在命令行中输入以下命令：

```text
adb shell dumpsys package i
```

综上，Applink 不能顺利通过系统检验，原因有以下可能：

* 可能是国内网络问题，使用 gms 组件校验的手机需要联通 Google 服务
* 可能是您产品配置问题，GIO 填写的签名和手机上运行的 APP 签名不同

{% hint style="info" %}
Status 状态为 ask 不代表唤起流程有问题，当用户操作允许后，后续唤起流程中将直接唤起，不会再出现询问弹窗。
{% endhint %}

#### 3.2.5 在 Callback 中接收自定义参数并跳转页面

在上文中，建议各位开发者将 GIO Intent Filter 代码块配置在 Launcher Activity 下，在用户点击短链后打开 App ，系统将自动跳转到 Launcher Activity ，此时 GIO DeepLink Callback 则会返回您在 GIO 官网广告监测中配置的自定义参数，此时您需要接收您的自定义参数，跳转到指定页面。

详见 [Android DeepLink CallBack 接收参数](../../../kai-fa-zhe-wen-dang/sdkintegrated/android-sdk/auto-android-sdk.md#16-deep-link-hui-tiao-can-shu-huo-qu)文档。

### 3.3 配置应用宝微下载

GrowingIO 提供跳转到应用宝微下载的功能，应用宝微下载为腾讯应用宝体系下的微下载链接。使用应用宝微下载，在微信等腾讯旗下软件中将转至微下载逻辑。

腾讯微下载介绍：[https://wiki.open.qq.com/index.php?title=mobile/应用宝微下载](https://wiki.open.qq.com/index.php?title=mobile/%E5%BA%94%E7%94%A8%E5%AE%9D%E5%BE%AE%E4%B8%8B%E8%BD%BD)​

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LtPfhH_p6U8X7dKYA6C-LtPh1V9S5SeR8Djq6mnimage.png)

{% hint style="warning" %}
在确认开启应用宝微下载前，请确认您已经达到腾讯微下载服务的量级标准，并且审核通过，否则直接开启将导致用户使用体验下降。
{% endhint %}

## 4 引导中间页配置

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%2872%29.png)

当您认为 GrowingIO 提供的默认下载引导页风格无法满足您的需求时，您可以对 DeepLink 中的下载引导页面进行定制，使其更符合您产品的风格，其中将提供两种方式对下载页面进行定制，简易布局和自由布局。

**简易布局**

在默认页面风格中对页面元素进行简单调整，如替换背景图片，对按钮颜色进行更换等。

**自由布局**

在此布局中，页面将只保留必要的操作按钮在页面底部，其余空间全部开放，您可以通过对背景图的自由设计，来实现任何您想要的关键元素或页面风格设计。

