# Android SDK合规说明

请使用最新 GrowingIO Android SDK[ 稳定版本](../android-sdk/androidsdk-log.md) 及以上

* 根据[工业和信息化部关于开展纵深推进APP侵害用户权益专项整治行动](http://www.gov.cn/zhengce/zhengceku/2020-08/02/content\_5531975.htm)，App 需要通过隐私政策说明应用采集数据
* 需要告知用户您集成了 GrowingIO SDK，并且 GrowingIO SDK 会尝试获取 ANDROID\_ID，IMEI 信息用于渠道信息，并且采集用户信息进行行为分析

为确保您的App在集成 GrowingIO SDK 之后，能够满足工信部相关合规要求，请参考以下说明。

## 隐私协议填写

### 收集和获取 <a href="#shou-ji-he-huo-qu" id="shou-ji-he-huo-qu"></a>

在您的APP《隐私协议》中收集和获得的个人信息栏目中根据实际情况填写如下内容：

```
我们的产品集成了 GrowingIO SDK，我们会通过 GrowingIO SDK 收集您的设备信息（例如：操作系统、设备型号、系统版本、`AndroidID`、`IMEI` 、IP地址、粘贴板内容）用于统计分析您在 App 内的使用效果，从而改进我们的产品和服务。 
```

可在第三方SDK列表中增加如下内容(设备信息按照实际情况填写)：

```
GIO移动端 SDK
用途：分析收集移动应用程序(App)用户的使用情况
收集个人信息类型：设备标识信息（如IMEI、Android ID、OAID），粘贴板内容，设备类型，设备版本，系统版本，地理位置信息，网络设备制造商，IP地址，网络模式
提供方：北京易数科技有限公司
第三方SDK隐私协议链接：https://accounts.growingio.com/user-privacy
```

### 与授权合作伙伴共享 <a href="#yu-shou-quan-he-zuo-huo-ban-gong-xiang" id="yu-shou-quan-he-zuo-huo-ban-gong-xiang"></a>

在您的APP《隐私协议》中的与授权合作伙伴共享栏目中根据实际情况填写如下内容:

```
我们的产品集成了 GrowingIO SDK，我们会通过 GrowingIO SDK 收集您的设备信息（例如：操作系统、设备型号、系统版本、`AndroidID`、`IMEI` 、IP地址、粘贴板内容）用于统计分析您在 App 内的使用效果，从而改进我们的产品和服务。
```

## 合规步骤

1.您需要确保 App 有《隐私协议》，并且在用户第一次启动 App 时就能向用户展示并取得用户同意；

2.请务必告知用户您使用了 GrowingIO SDK，请在 《隐私协议》 中添加隐私条款，参考[隐私协议填写](sdk-he-gui-shuo-ming.md#yin-si-xie-yi-tian-xie)

3.集成[原生 Android SDK](../android-sdk/)，请在用户同意《隐私协议》之后[再初始化GrowingIO SDK](sdk-he-gui-shuo-ming.md#fang-shi-yi-yan-chi-chu-shi-hua) 或[设置 GrowingIO SDK 的数据收集开关](sdk-he-gui-shuo-ming.md#fang-shi-er-guan-bi-shu-ju-shou-ji-kai-guan)。​

## 采集详情

### 个人信息字段采集

我们通过采集唯一设备识别码（如IMEI/AndroidID/IP地址）对用户进行唯一标识，以便进行诸如用户访问量，广告等数据统计。在无法获取设备识别码的情况下（如Android高版本API限制），我们推荐集成由[移动安全联盟MSA](http://www.msa-alliance.cn/)提供的 Oaid SDK 作为设备唯一识别码，以便正常提供统计分析服务。

### Android 设备权限 <a href="#android-she-bei-quan-xian" id="android-she-bei-quan-xian"></a>

|                     权限                    | 用途                                                                       |
| :---------------------------------------: | ------------------------------------------------------------------------ |
|        android.permission.INTERNET        | 允许应用程序联网和发送统计数据的权限，以便提供统计分析服务。必须权限                                       |
| android.permission.ACCESS\_NETWORK\_STATE | 检测联网方式，在网络异常状态下避免数据发送，节省流量和电量。必须权限                                       |
|   android.permission.ACCESS\_WIFI\_STATE  | 获取WIFI网络类型，检测联网方式，节省流量和电量。必须权限                                           |
|   android.permission.READ\_PHONE\_STATE   | 获取用户设备的IMEI，通过IMEI对用户进行唯一标识，以便提供统计分析服务。(只在Android 10以下可用，10以上已无法获取)。可选权限 |

## 初始化

### 方式一、延迟初始化 <a href="#fang-shi-yi-yan-chi-chu-shi-hua" id="fang-shi-yi-yan-chi-chu-shi-hua"></a>

如果未同意《隐私协议》， 在 Activity 的onCreate()方法中同意隐私协议后进行 SDK 初始化。如果已同意《隐私协议》，在 Application 的 onCreate() 方法主线程中初始化 SDK。

{% hint style="warning" %}
在隐私协议授权同意之后，再初始化 GrowingIO SDK（版本需在 2.9.1 及以上）。

如果配置有[AppLink](../../../product-manual/growing/product-configuration/deeplink.md#3.2-applinks-pei-zhi)，则在SDK初始化之后可用。
{% endhint %}

```
// 在 Activity 中同意隐私条款后初始化 SDK
public class MyActivity extends Activity {
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        if (<未同意隐私协议>){
            // 展示隐私协议弹窗，等待用户同意
            if (<用户同意隐私协议>){
              GrowingIO.startWithConfiguration(this, new Configuration()
                  .setChannel("XXX应用商店")
              );
            }
        }
    }
}
```

```
// Application 的 onCreate() 方法中主线程初始化 SDK
public class MyApplication extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        
        if (<用户已经同意隐私协议>){
              GrowingIO.startWithConfiguration(this, new Configuration()
                  .setChannel("XXX应用商店")
              );
        }

    }
}
```

### 方式二、设置数据收集开关

{% hint style="warning" %}
SDK版本需在 2.9.12及以上。如果配置有[AppLink](../../../product-manual/growing/product-configuration/deeplink.md#3.2-applinks-pei-zhi)，则在`enableDataCollect 之后可用`。
{% endhint %}

GrowingIO SDK 提供 `disableDataCollect` 接口，可在用户不同意隐私协议时，调用该接口， 禁止数据采集；在用户同意隐私协议时，调用 `enableDataCollect` 接口， 开启数据采集。若希望在开启数据采集前禁止获取 AndroidID ，请在 SDK 初始化配置项中设置 `.setAndroidIdEnable(false)`

```
// Application 的 onCreate() 方法中主线程初始化 SDK
public class MyApplication extends Application {
    @Override
    public void onCreate() {
        super.onCreate();

        // 初始化配置
        Configuration configuration = new Configuration();
        // 其它初始化配置如是否开启ebug等
        ...
        // 根据数据采集开关判断
        if (<未同意隐私协议>) {
            configuration.disableDataCollect();
        }
        // 初始化SDK
        GrowingIO.startWithConfiguration(application, configuration);
    }
}
```

```
// 同意数据采集后，开启数据发送
GrowingIO.getInstance().enableDataCollect();
```

## 其他说明

### 集成OAID SDK <a href="#ji-cheng-oaidsdk" id="ji-cheng-oaidsdk"></a>

具体可以参考 [采集OAID作为设备信息](../android-sdk/auto-android-sdk.md#18.-cai-ji-oaid)

### 关于 Google Play <a href="#guan-yu-googleplay" id="guan-yu-googleplay"></a>

如您的 App 需要在 Google Play 分发，请参照 Google Play 相关政策 - [Google Play 政策中心-用户数据帮助说明](https://support.google.com/googleplay/android-developer/answer/10144311)。 具体合规步骤同上文所述一致。

{% hint style="info" %}
符合Google paly 相关政策的SDK版本 在2.9.4 及以上
{% endhint %}

### 关于 GDPR <a href="#guan-yu-gdpr" id="guan-yu-gdpr"></a>

​为符合 [General Data Protection Regulation 欧盟通用数据保护条例​](https://zh.wikipedia.org/wiki/%E6%AD%90%E7%9B%9F%E4%B8%80%E8%88%AC%E8%B3%87%E6%96%99%E4%BF%9D%E8%AD%B7%E8%A6%8F%E7%AF%84)， 请参考 [方式二设置数据收集开关](sdk-he-gui-shuo-ming.md#fang-shi-er-she-zhi-shu-ju-shou-ji-kai-guan)

### 关于禁用 AndroidId

`GrowingIO SDK`在采集 `设备标识` 时，会默认采集 `AndroidId`，有一定的合规风险，但是考虑采集的准确性，GrowingIO 仍然提供 AndroidId 的采集方法。

如果您需要禁止采集 AndroidId，请配置`Configuration`

```
.setAndroidIdEnable(false);
```

无埋点版本SDK可以通过gradle配置关闭AndroidId采集

```
growingio {
    defaultConfig {
        androidIdEnable f​alse
    }
}
```

### 关于禁用 IMEI

在使用渠道追踪功能时，`GrowingIO SDK`会使用到 IMEI。

如果您需要禁止采集 IMEI，需要配置`Configuration`

```
.setImeiEnable(false);
```

无埋点版本SDK可以通过gradle配置关闭IMEI采集

```
growingio {
    defaultConfig {
        imeiEnable f​alse
    }
}
```

### 关于禁用 GoogleAdId

在使用渠道追踪功能时，`GrowingIO SDK`会使用到 GoogleAdId。

如果您需要禁止采集 GoogleAdId，需要配置`Configuration`

```
.setGoogleAdIdEnable(false);
```

无埋点版本SDK可以通过gradle配置关闭GoogleAdId采集

```
growingio {
    defaultConfig {
        googleAdIdEnable f​alse
    }
}
```

### 关于禁用 OAID

在使用渠道追踪功能时，会使用到 OAID。`GrowingIO SDK` 默认不采集 OAID。

### 关于禁用获取APP多进程信息

{% hint style="info" %}
SDK版本需在 2.9.12及以上
{% endhint %}

&#x20;GrowingIO SDK默认会获取app多进程信息，用于更准确的在不同进程共享数据。

如果您不希望 SDK 调用获取进程信息的敏感函数，例如 APP 需要隐私检查时，可在初始化时做如下设置&#x20;

```
.setRequireAppProcessesEnabled(false)；
```

## 常见问题

### Q：延迟初始化之后，发现丢掉了部分事件 <a href="#q-yan-chi-chu-shi-hua-zhi-hou-fa-xian-diu-diao-le-bu-fen-shi-jian" id="q-yan-chi-chu-shi-hua-zhi-hou-fa-xian-diu-diao-le-bu-fen-shi-jian"></a>

A：对于SDK初始化之前，或者开启数据采集之前发生的事件，一概丢弃。

