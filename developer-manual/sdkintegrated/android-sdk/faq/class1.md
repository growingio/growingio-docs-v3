# 无埋点数据采集问题

## 1. GrowingIO对于页面的定义（标识）是什么？

确认当前页面的方法有三种：

1. 圈选时，查看圈选页面为当前页面​

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LI58sGTg1USJzrnTVZD-LI5KdIC78J2Y7tfdBp2image.png)

2.使用[DebugMode](../auto-android-sdk.md#1-she-zhi-debug-mo-shi-setdebugmode)日志，进入页面发送的`page`的`p`为当前的页面。

3.使用[Mobile Debugger](../../../debugging/mobile-debugger.md) 查看`page`事件的`p`。



## 2. 点击事件采集逻辑是什么？

设置以下点击事件的控件会被采集点击事件，如果您自定义了点击事件，不在下方列举之内，将无法采集点击事件，影响数据分析。

```java
onCheckedChanged(android/widget/CompoundButton)
onCheckedChanged(android/widget/RadioGroup)
onClick(android/content/DialogInterface)
onClick(android/view/View)
onItemClick(android/widget/AdapterView;android/view/View)
onItemSelected(android/widget/AdapterView;android/view/View)
onNewIntent(android/content/Intent)
onRatingChanged(android/widget/RatingBar)
onStopTrackingTouch(android/widget/SeekBar)
onFocusChange(android/view/View)
onMenuItemClick(android/view/MenuItem)
onOptionsItemSelected(android/view/MenuItem)
onGroupClick(android/widget/ExpandableListView;android/view/View)
onChildClick(android/widget/ExpandableListView;android/view/View)
```

如果您自定义了 Click 事件， 但是希望 SDK 采集。 可以放置一个 `onClickListener` 作为代理。这种方案即使随着我们的 SDK 升级也会被兼容。

{% hint style="info" %}
请注意设置您的 View 可点击：

`//设置view Clickable, 如果不设置会不能圈选这个 View。`

`view.setClickable(true);`
{% endhint %}

```java
public void onCustomClick(View view){
	// 您的业务
	...	
	// 为了 GrowingIO 能够采集自定义点击事件，调用 android.view.OnClickListener
    new View.OnClickListener() {
        @Override
        public void onClick(View view) {}
    }.onClick(view);
}
```

例： `TabHost` 的点击事件采集增加 onClickListener 后可以采集到点击事件

```java
TabHost.OnTabChangeListener listener = new TabHost.OnTabChangeListener() {
    public void onTabChanged(String tabId) {
        // GrowingIO 点击事件采集适配 TabHost 添加代码
        new View.OnClickListener() {
            @Override
            public void onClick(View view) {}
        }.onClick(mTabHost.getCurrentTabView());
    }
}
```

最后，如果您是在布局文件中在`view`上使用 `onClick` 属性的点击事件，不会被采集，不支持。

{% hint style="warning" %}
如果您还未采集到点击事件， 并且使用了 lambda 表达式，请参考[lambda配置](../auto-android-sdk.md#5-lambda-biao-da-shi-zhi-chi-pei-zhi-xiang)。
{% endhint %}

## 3. 如何查看当前App SDK的版本？

有以下多种方式，任选其一。

1. 唤起圈选，点击小红点，能够看到版本号；
2. 使用 Mobile Debugger ， 点击左侧截图区域的 `i` 图标，能够看到版本号；
3. 翻阅代码，app 目录层中的 build.gradle 文件中查找；
4. 查看日志，每条 vst 事件中 `av` 字段描述版本号；
5. 抓包查看，网络请求中包含。

## 4. 为何不建议自定义设备ID？

我们强烈不建议您自行定义设备ID有以下几个方面：

1. 我们采集的设备 ID 为了能够唯一标识一台设备信息，如果您进行自定义，有可能用户卸载重新安装应用，设备 ID 会不一致，造成老用户被识别成新用户；
2. 如果您未曾定义过设备ID，并且已经集成SDK并且发版过，则新旧设备 ID 不兼容，老用户被认为成新用户，导致新用户数量暴增；

## ​5. 多个URL Scheme怎么配置？

在 Android 无埋点 SDK 集成步骤中，其中有一步需要在 manifest.xml 文件中配置 `intent-filter` 代码块，如果有多个 `URLScheme` 配置，请参照以下代码：

```java
<activity
    android:name=".LauncherActivity"
    android:launchMode="singleTop"
    android:theme="@style/AppTheme">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
    <!-- GrowingIO URLScheme -->
    <intent-filter>
        <data android:scheme="growing.xxxxxxxxxxxxxxxx" />
        <action android:name="android.intent.action.VIEW" />
        <category android:name="android.intent.category.DEFAULT" />
        <category android:name="android.intent.category.BROWSABLE" />
    </intent-filter>
    <!-- 测试多个 scheme 能够成功被唤醒 -->
    <intent-filter>
        <data
            android:host="share"
            android:scheme="will" />
        <action android:name="android.intent.action.VIEW" />
        <category android:name="android.intent.category.DEFAULT" />
        <category android:name="android.intent.category.BROWSABLE" />
    </intent-filter>
</activity>
```

多个  Intent Filter 不建议合并，强烈建议不要合并，除非经过严谨的测试，[Google 官方解释](https://developer.android.com/training/app-links/deep-linking#adding-filters)。



