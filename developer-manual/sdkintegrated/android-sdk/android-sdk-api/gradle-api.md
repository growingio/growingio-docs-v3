---
description: 应用在编译时的自定义配置API。
---

# Gradle配置API

{% hint style="warning" %}
SDK支持限制：只支持**Android 无埋点 SDK**
{% endhint %}

{% hint style="info" %}
**注意，imeiEnable、androidEnable、googleAdIdEnable 配置项不支持 com.android.tools.build:gradle 3.0.x 以下版本**。
{% endhint %}

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
      <td style="text-align:left">imeiEnable</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left">&#x4E3A;&#x4E86;&#x6D77;&#x5916;&#x5E94;&#x7528;&#x5E02;&#x573A;&#x4E0A;&#x67B6;&#x5E94;&#x7528;&#xFF0C;&#x8BBE;&#x7F6E;&#x4E3A;
        false &#x5219; SDK &#x4E0D;&#x91C7;&#x96C6; <code>imei</code> &#x3002;<b>&#x5728;&#x7F16;&#x8BD1;&#x671F;&#x914D;&#x7F6E;&#x5C06;&#x5220;&#x9664;&#x8BE5;&#x90E8;&#x5206;&#x7684;&#x91C7;&#x96C6;&#x4EE3;&#x7801;&#xFF0C;&#x540E;&#x7EED;&#x914D;&#x7F6E;&#xFF08;&#x521D;&#x59CB;&#x5316;&#x6216;&#x8005;&#x8FD0;&#x884C;&#x65F6;&#xFF09;&#x5C06;&#x5931;&#x6548;&#x3002;</b>
      </td>
      <td style="text-align:left">&gt;=2.7.8</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">androidIdEnable</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left">&#x4E3A;&#x4E86;&#x6D77;&#x5916;&#x5E94;&#x7528;&#x5E02;&#x573A;&#x4E0A;&#x67B6;&#x5E94;&#x7528;&#xFF0C;&#x8BBE;&#x7F6E;&#x4E3A;
        false &#x5219; SDK &#x4E0D;&#x91C7;&#x96C6; <code>androidId</code> &#x3002;<b>&#x5728;&#x7F16;&#x8BD1;&#x671F;&#x914D;&#x7F6E;&#x5C06;&#x5220;&#x9664;&#x8BE5;&#x90E8;&#x5206;&#x7684;&#x91C7;&#x96C6;&#x4EE3;&#x7801;&#xFF0C;&#x540E;&#x7EED;&#x914D;&#x7F6E;&#xFF08;&#x521D;&#x59CB;&#x5316;&#x6216;&#x8005;&#x8FD0;&#x884C;&#x65F6;&#xFF09;&#x5C06;&#x5931;&#x6548;&#x3002;</b>
      </td>
      <td style="text-align:left">&gt;=2.7.8</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">googleAdIdEnable</td>
      <td style="text-align:left">true</td>
      <td style="text-align:left">&#x4E3A;&#x4E86;&#x6D77;&#x5916;&#x5E94;&#x7528;&#x5E02;&#x573A;&#x4E0A;&#x67B6;&#x5E94;&#x7528;&#xFF0C;&#x8BBE;&#x7F6E;&#x4E3A;
        false &#x5219; SDK &#x4E0D;&#x91C7;&#x96C6; <code>GoogleAdId</code> &#x3002;<b>&#x5728;&#x7F16;&#x8BD1;&#x671F;&#x914D;&#x7F6E;&#x5C06;&#x5220;&#x9664;&#x8BE5;&#x90E8;&#x5206;&#x7684;&#x91C7;&#x96C6;&#x4EE3;&#x7801;&#xFF0C;&#x540E;&#x7EED;&#x914D;&#x7F6E;&#xFF08;&#x521D;&#x59CB;&#x5316;&#x6216;&#x8005;&#x8FD0;&#x884C;&#x65F6;&#xFF09;&#x5C06;&#x5931;&#x6548;&#x3002;</b>
      </td>
      <td style="text-align:left">&gt;=2.7.8</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">oaidEnable</td>
      <td style="text-align:left">ture</td>
      <td style="text-align:left">
        <p>&#x56FD;&#x5185;<a href="http://www.msa-alliance.cn/col.jsp?id=120">&#x79FB;&#x52A8;&#x5B89;&#x5168;&#x8054;&#x76DF;MSA</a> &#x8054;&#x5408;&#x5404;&#x5927;&#x624B;&#x673A;&#x5236;&#x9020;&#x5546;&#x63A8;&#x51FA;&#x4E86;
          OAID &#xFF0C; &#x4F5C;&#x4E3A;&#x552F;&#x4E00;&#x5E7F;&#x544A;&#x6807;&#x8BC6;&#x7B26;&#x3002;</p>
        <p><b>&#x8BBE;&#x7F6E;&#x4E3A; false &#x5219;&#x8FD0;&#x884C;&#x65F6;&#x548C;&#x521D;&#x59CB;&#x5316;&#x7684;&#x914D;&#x7F6E;&#x5219;&#x65E0;&#x6548;&#x3002;</b>
        </p>
      </td>
      <td style="text-align:left">&gt;=2.8.5</td>
      <td style="text-align:left">-</td>
    </tr>
  </tbody>
</table>**示例代码**

```java
android {    ···}
// 须位于 android 代码块下
growingio {
    defaultConfig {
        imeiEnable true
        androidIdEnable true
        googleAdIdEnable true
    }
​
    buildTypes {
        googlePlay {
            imeiEnable false
            andoridIdEnable false
            googleAdIdEnable true
        }
    }
}
```

