# Gradle 常见问题

## 1. Gradle 支持版本

Android 无埋点 SDK 支持 `com.android.tools.build:gradle` **2.3.3** 及其以上版本，推荐版本是 **3.2.1**。下文将简称 `com.android.tools.build:gradle`为 gradle。

无埋点 SDK 随着 gradle 的升级也在逐步兼容，请参考以下表格更新 SDK：

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x65E0;&#x57CB;&#x70B9;SDK&#x7248;&#x672C;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">2.8.4+</td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>SDK 2.8.4 &#x53CA;&#x5176;&#x4EE5;&#x4E0A;&#x7248;&#x672C;&#x652F;&#x6301;
            gradle 3.5.0&#xFF1B;</li>
          <li>&#x65B0;&#x589E;&#x5728;&#x7F16;&#x8BD1;&#x671F;&#x95F4;&#x6821;&#x9A8C;&#x7528;&#x6237;&#x4F7F;&#x7528;&#x7684;
            SDK &#x662F;&#x5426;&#x4E3A;&#x7A33;&#x5B9A; SDK &#x7248;&#x672C;&#xFF0C;&#x5982;&#x679C;&#x4F7F;&#x7528;&#x6709;&#x95EE;&#x9898;&#x7684;&#x7248;&#x672C;&#x5C06;&#x4E3B;&#x52A8;&#x5728;&#x7F16;&#x8BD1;&#x65F6;&#x63D0;&#x793A;&#x7528;&#x6237;&#x5347;&#x7EA7;
            SDK&#xFF0C;&#x5E76;&#x629B;&#x51FA;&#x5F02;&#x5E38;&#x63D0;&#x793A;&#xFF0C;&#x62D2;&#x7EDD;&#x7F16;&#x8BD1;&#x3002;</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2.7.8</td>
      <td style="text-align:left">
        <p>&#x589E;&#x52A0;&#x63A5;&#x53E3; <code>setAndroidIdEnable</code> , <code>setImeiEnable</code>, <code>setGoogleAdIdEnable</code> &#x4E3A;&#x6D77;&#x5916;&#x4E0A;&#x67B6;&#x5E94;&#x7528;&#x6D89;&#x53CA;&#x91C7;&#x96C6;&#x7528;&#x6237; <code>androidId</code>, <code>imei</code>, <code>googleAdId</code> &#x9690;&#x79C1;&#x6570;&#x636E;&#x7684;&#x5F00;&#x5173;&#x652F;&#x6301;&#x3002;</p>
        <p><b>&#x8BE6;&#x89C1;</b><a href="../android-sdk-api/gradle-api.md"><b>Gradle&#x7F16;&#x8BD1;&#x65F6;&#x914D;&#x7F6E;API</b></a>&lt;b&gt;&lt;/b&gt;</p>
        <p><b>&#x6CE8;&#x610F;&#xFF0C;&#x4EE5;&#x4E0A;&#x63A5;&#x53E3;&#x4E0D;&#x652F;&#x6301; gradle 3.0.x &#x4EE5;&#x4E0B;&#x7248;&#x672C;</b>&#x3002;</p>
      </td>
    </tr>
  </tbody>
</table>## **2. 升级 2.8.4 编译报错**

升级无埋点 SDK 2.8.4如果报错如下：

> Unable to load class **'org.apache.http.impl.client.CloseableHttpClient'**. Possible causes for this unexpected error include: Gradle's dependency cache may be corrupt \(this sometimes occurs after a network connection timeout.\) Re-download dependencies and sync project \(requires network\)
>
> The state of a Gradle build process \(daemon\) may be corrupt. Stopping all Gradle daemons may solve this problem. Stop Gradle build processes \(requires restart\)
>
> Your project may be using a third-party plugin which is not compatible with the other plugins in the project or the version of Gradle requested by the project.
>
> In the case of corrupt Gradle processes, you can also try closing the IDE and then killing all Java processes.

此报错原因是在 SDK 2.8.4 时新增在编译期间校验用户使用的 SDK 是否为稳定 SDK 版本，如果使用有问题的版本将主动在编译时提示用户升级 SDK，并抛出异常提示，拒绝编译功能，此部分代码逻辑触发了Proguard 的 Bug ，导致报错。建议解决方案有两种：

1. 升级 gradle 为 3.2.1 及其以上版本；
2. 在项目级别 build.gradle 中添加以下依赖即可：

```text
classpath "org.apache.httpcomponents:httpclient:4.5.10"
```

示例代码：

```java
dependencies {
    //使用 gradle 3.2.1 以下并且 SDK 2.8.4 版本会触发此问题
    classpath 'com.android.tools.build:gradle:3.1.4'
    classpath 'com.growingio.android:vds-gradle-plugin:autotrack-2.8.4'
    //添加以下依赖能够解决，或者升级 gradle
    classpath "org.apache.httpcomponents:httpclient:4.5.10"
}
```

## 3. 使用Jack注意

依据Android Studio[官网说明](https://developer.android.com/studio/write/java8-support#migrate)，SDK不支持 Jack 编译器，请确认移除 jackOptions 代码块。

```java
android {
    ...
    defaultConfig {
        ...
        // Remove this block. 删掉这里！！！
        jackOptions {
            enabled true
            ...
        }
    }
    // Keep the following configuration in order to target Java 8.
    compileOptions {
        sourceCompatibility JavaVersion.VERSION_1_8
        targetCompatibility JavaVersion.VERSION_1_8
    }
}
```

{% hint style="danger" %}
如果您未移除，集成SDK后App将崩溃（Crash）。
{% endhint %}

