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

| API | 默认值 | 说明 | 无埋点SDK版本支持 | 埋点SDK版本支持 |
| :--- | :--- | :--- | :--- | :--- |
| startWithAccountId:_**AccountId**_ | 无 | 初始化方法，_**AccountID**_为项目id，默认采样率为100%。 | ✔️ | ✔️ |
| startWithAccountId:_**AccountId**_ withSampling:_**sampling**_ | 无 | 初始化方法，_**AccountID**_为项目id；_**sampling**_为采样率。 | ✔️ | ✔️ |
| handleUrl | 无 | URL Scheme处理方法，通过参数不同区分圈选、MobileDebugger、DeepLink、用户运营预览弹窗等。 | ✔️ | ✔️ |

## SDK功能API

<table>
  <thead>
    <tr>
      <th style="text-align:left">API</th>
      <th style="text-align:left">&#x9ED8;&#x8BA4;&#x503C;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
      <th style="text-align:left">&#x65E0;&#x57CB;&#x70B9;SDK&#x7248;&#x672C;&#x652F;&#x6301;</th>
      <th style="text-align:left">&#x57CB;&#x70B9;SDK&#x7248;&#x672C;&#x652F;&#x6301;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">sdkVersion</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x83B7;&#x53D6;&#x5F53;&#x524D;GrowingIO SDK&#x7248;&#x672C;&#x53F7;&#x3002;</td>
      <td
      style="text-align:left">&gt;=2.0.0</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setEnableLog</td>
      <td style="text-align:left">YES</td>
      <td style="text-align:left">&#x91C7;&#x96C6;&#x65E5;&#x5FD7;&#x5F00;&#x5173;&#xFF0C;setEnableLog=YES&#x65F6;&#xFF0C;&#x4F1A;&#x8F93;&#x51FA;&#x8C03;&#x8BD5;&#x65E5;&#x5FD7;&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">getEnableLog</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x83B7;&#x53D6;&#x91C7;&#x96C6;&#x65E5;&#x5FD7;&#x5F00;&#x5173;&#x7684;&#x5F53;&#x524D;&#x72B6;&#x6001;&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">setTrackerHost</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x6570;&#x636E;&#x6536;&#x96C6;&#x5E73;&#x53F0;&#x670D;&#x52A1;&#x5668;&#x5730;&#x5740;&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">setReportHost</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x8BBE;&#x5907;&#x62A5;&#x6D3B;&#x670D;&#x52A1;&#x5668;&#x5730;&#x5740;&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">setDataHost</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x6570;&#x636E;&#x67E5;&#x770B;&#x5E73;&#x53F0;&#x670D;&#x52A1;&#x5668;&#x5730;&#x5740;&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">setGtaHost</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x6570;&#x636E;&#x540E;&#x53F0;&#x670D;&#x52A1;&#x5668;&#x5730;&#x5740;&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">setWsHost</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x6570;&#x636E;&#x540E;&#x53F0;&#x670D;&#x52A1;&#x5668;&#x5730;&#x5740;&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>setHybridJSSDK</p>
        <p>UrlPrefix</p>
      </td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x6570;&#x636E;&#x540E;&#x53F0;&#x670D;&#x52A1;&#x5668;&#x5730;&#x5740;&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setZone</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E; zone &#x4FE1;&#x606F;&#xFF0C;&#x5373;&#x65F6;&#x533A;&#x4FE1;&#x606F;&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">getDeviceId</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x83B7;&#x53D6;&#x5F53;&#x524D;&#x8BBE;&#x5907; ID&#x3002;</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">getVisitUserId</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x83B7;&#x53D6;&#x5F53;&#x524D;&#x8BBF;&#x95EE;&#x7528;&#x6237;ID&#x3002;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">getSessionId</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x83B7;&#x53D6;&#x5F53;&#x524D;&#x8BBF;&#x95EE;ID&#x3002;</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">growingAttributesDonotTrackImp</td>
      <td style="text-align:left">false</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x662F;&#x5426;&#x91C7;&#x96C6;view&#x53CA;&#x9875;&#x9762;&#x5143;&#x7D20;&#x7684;<code>imp</code>&#x4E8B;&#x4EF6;&#x3002;</td>
      <td
      style="text-align:left">&gt;=2.6.7</td>
        <td style="text-align:left">-</td>
    </tr>
  </tbody>
</table>

\#\#\# 数据采集发送API

<table>
  <thead>
    <tr>
      <th style="text-align:left">API</th>
      <th style="text-align:left">&#x9ED8;&#x8BA4;&#x503C;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
      <th style="text-align:left">&#x65E0;&#x57CB;&#x70B9;SDK&#x7248;&#x672C;&#x652F;&#x6301;</th>
      <th style="text-align:left">&#x57CB;&#x70B9;SDK&#x7248;&#x672C;&#x652F;&#x6301;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">setAspectMode</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x6570;&#x636E;&#x91C7;&#x96C6;&#x6A21;&#x5F0F;&#xFF0C;&#x6709;
        GrowingAspectModeSubClass &#x548C; GrowingAspectModeDynamicSwizzling &#x4E24;&#x79CD;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">setEnableDiagnose</td>
      <td style="text-align:left">enable</td>
      <td style="text-align:left">
        <p>&#x662F;&#x5426;&#x5141;&#x8BB8;&#x53D1;&#x9001;&#x57FA;&#x672C;&#x6027;&#x80FD;&#x8BCA;&#x65AD;&#x4FE1;&#x606F;&#xFF0C;&#x9ED8;&#x8BA4;&#x4E3A;&#x5F00;&#x3002;</p>
        <p>&#x57FA;&#x672C;&#x6027;&#x80FD;&#x6307;&#x53D1;&#x9001;&#x6210;&#x529F;&#x3001;&#x5931;&#x8D25;&#x3001;timeout&#x7B49;&#x4FE1;&#x606F;</p>
      </td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">disable</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x5168;&#x5C40;&#x4E0D;&#x53D1;&#x9001;&#x7EDF;&#x8BA1;&#x4FE1;&#x606F;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">enableAllWebViews</td>
      <td style="text-align:left">enable</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x662F;&#x5426;&#x91C7;&#x96C6;WKWebView &#x4FE1;&#x606F;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">enableHybridHashTag</td>
      <td style="text-align:left">enable</td>
      <td style="text-align:left">&#x662F;&#x5426;&#x542F;&#x7528; HashTag</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">isTrackingWebView</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left">&#x662F;&#x5426;&#x542F;&#x7528; trackingWebView</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setImp</td>
      <td style="text-align:left">NO</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x662F;&#x5426;&#x53D1;&#x9001;&#x5143;&#x7D20;&#x7684;&#x5C55;&#x73B0;&#x6B21;&#x6570;&#xFF08;&#x6D4F;&#x89C8;&#x91CF;&#x3001;&#x66DD;&#x5149;&#x91CF;&#xFF09;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setFlushInterval</td>
      <td style="text-align:left">30s</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x3001;&#x83B7;&#x53D6;&#x53D1;&#x9001;&#x6570;&#x636E;&#x7684;&#x65F6;&#x95F4;&#x95F4;&#x9694;&#xFF0C;&#x9ED8;&#x8BA4;&#x503C;&#x4E3A;30&#x79D2;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">setDailyDataLimit</td>
      <td style="text-align:left">3M</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x6BCF;&#x5929;&#x4F7F;&#x7528;&#x6570;&#x636E;&#x7F51;&#x7EDC;&#xFF08;2G&#x3001;3G&#x3001;4G&#xFF09;&#x4E0A;&#x4F20;&#x7684;&#x6570;&#x636E;&#x91CF;&#x7684;&#x4E0A;&#x9650;&#xFF08;&#x5355;&#x4F4D;&#x662F;
        KB&#xFF09;&#xFF0C;&#x9ED8;&#x8BA4;&#x503C;&#x4E3A; 3 MB</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">getDailyDataLimit</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x83B7;&#x53D6;&#x6BCF;&#x5929;&#x4F7F;&#x7528;&#x6570;&#x636E;&#x7F51;&#x7EDC;&#xFF08;2G&#x3001;3G&#x3001;4G&#xFF09;&#x4E0A;&#x4F20;&#x7684;&#x6570;&#x636E;&#x91CF;&#x7684;&#x4E0A;&#x9650;&#xFF08;&#x5355;&#x4F4D;&#x662F;
        KB&#xFF09;&#xFF0C;&#x9ED8;&#x8BA4;&#x503C;&#x4E3A;3 MB</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">disableDataCollect</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E; GDPR &#x751F;&#x6548;</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">enableDataCollect</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E; GDPR &#x5931;&#x6548;</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
      <td style="text-align:left">&#x2714;&#xFE0F;</td>
    </tr>
    <tr>
      <td style="text-align:left">disablePushTrack</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x662F;&#x5426;&#x91C7;&#x96C6;push&#x63A8;&#x9001;&#x70B9;&#x51FB;&#xFF0C;&#x9ED8;&#x8BA4;&#x4E0D;&#x91C7;&#x96C6;</td>
      <td
      style="text-align:left">&#x2714;&#xFE0F;</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setEnableLocationTrack</td>
      <td style="text-align:left">Yes</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x662F;&#x5426;&#x91C7;&#x96C6;&#x5730;&#x7406;&#x4F4D;&#x7F6E;&#x7684;&#x7EDF;&#x8BA1;&#x4FE1;&#x606F;&#xFF0C;&#x9ED8;&#x8BA4;&#x91C7;&#x96C6;</td>
      <td
      style="text-align:left">&gt;=2.8.6</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">getEnableLocationTrack</td>
      <td style="text-align:left">&#x65E0;</td>
      <td style="text-align:left">&#x83B7;&#x53D6;&#x662F;&#x5426;&#x91C7;&#x96C6;&#x5730;&#x7406;&#x4F4D;&#x7F6E;</td>
      <td
      style="text-align:left">&gt;=2.8.6</td>
        <td style="text-align:left">-</td>
    </tr>
  </tbody>
</table>

