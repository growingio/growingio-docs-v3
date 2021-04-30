---
description: 运行时 API 可对 SDK 进行采集上报数据的控制。
---

# 运行时API

GrowingIO为App提供运行时随意调用的API，使用方法如下：

{% tabs %}
{% tab title="Java" %}
```java
// 得到 GrowingIO 实例后可以调用其中 API
GrowingIO gio = GrowingIO.getInstance();
gio.setUserId("张溪梦");
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
val gio = GrowingIO.getInstance()
gio.userId = "张溪梦"
```
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
GrowingIO所有API都需要在主线程调用。
{% endhint %}

## 基础配置API

<table>
  <thead>
    <tr>
      <th style="text-align:left">API</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
      <th style="text-align:left">&#x65E0;&#x57CB;&#x70B9;SDK&#x7248;&#x672C;&#x652F;&#x6301;</th>
      <th style="text-align:left">&#x57CB;&#x70B9;SDK&#x7248;&#x672C;&#x652F;&#x6301;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">setGeoLocation</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x7ECF;&#x7EAC;&#x5EA6;&#xFF0C;&#x5E76;&#x5728; vst &#x4E8B;&#x4EF6;&#x4E2D;&#x53D1;&#x9001;&#xFF0C;Android
        SDK &#x6682;&#x65F6;&#x6CA1;&#x529E;&#x6CD5;&#x81EA;&#x52A8;&#x83B7;&#x53D6;<code>GPS</code>&#x6570;&#x636E;&#xFF0C;&#x5982;&#x679C;&#x60A8;&#x8981;&#x91C7;&#x96C6;<code>GPS</code>&#x6570;&#x636E;&#xFF0C;&#x9700;&#x8981;&#x5728;&#x60A8;&#x7684;App&#x6BCF;&#x6B21;&#x83B7;&#x53D6;&#x5B8C;<code>GPS</code>&#x6570;&#x636E;&#x4E4B;&#x540E;&#xFF0C;&#x901A;&#x8FC7;&#x8BE5;<code>API</code>&#x544A;&#x77E5;
        SDK&#x3002;&#x5982;&#x679C;&#x60A8;&#x4E0D;&#x8BBE;&#x7F6E;&#xFF0C;&#x6211;&#x4EEC;&#x9ED8;&#x8BA4;&#x4F7F;&#x7528;&#x7528;&#x6237;<code>IP</code>&#x7684;<code>Location&#x3002;</code>
      </td>
      <td style="text-align:left">ALL</td>
      <td style="text-align:left">ALL</td>
    </tr>
    <tr>
      <td style="text-align:left">clearGeoLocation</td>
      <td style="text-align:left">&#x6E05;&#x7A7A;&#x7ECF;&#x7EAC;&#x5EA6;</td>
      <td style="text-align:left">ALL</td>
      <td style="text-align:left">ALL</td>
    </tr>
    <tr>
      <td style="text-align:left">setViewInfo</td>
      <td style="text-align:left">
        <p>&#x914D;&#x7F6E; view &#x7684; Tag&#xFF0C;&#x6807;&#x8BB0; View &#xFF0C;&#x5E76;&#x5728;
          GrowingIO &#x76F8;&#x5173;&#x4E8B;&#x4EF6;&#x4E2D;&#x53D1;&#x9001; &#xFF0C;&#x5185;&#x5BB9;&#x5BF9;&#x5E94; <code>xPath</code> &#x4E2D;&#x7684; <code>obj</code>
        </p>
        <p>&#x4F8B;&#x5982;&#xFF1A;&#x5728;&#x5546;&#x54C1;<code>ListView</code>&#x6DFB;&#x52A0;&#x8D2D;&#x7269;&#x8F66;&#x7684;&#x573A;&#x666F;&#x4E2D;&#xFF0C;&#x6BCF;&#x4E2A;&#x5546;&#x54C1;<code>item</code>&#x90FD;&#x542B;&#x6709;&#x4E00;&#x4E2A;&#x52A0;&#x5165;&#x8D2D;&#x7269;&#x8F66;&#x6309;&#x94AE;&#xFF0C;&#x8FD9;&#x65F6;&#x65E0;&#x6CD5;&#x533A;&#x5206;&#x5546;&#x54C1;<code>item</code>&#x4E0E;&#x5C06;&#x5B83;&#x52A0;&#x5165;&#x8D2D;&#x7269;&#x8F66;&#x6309;&#x94AE;&#x7684;&#x4E00;&#x5BF9;&#x4E00;&#x5173;&#x7CFB;&#xFF0C;&#x6B64;&#x65F6;&#x8C03;&#x7528;&#x6B64;&#x65B9;&#x6CD5;&#x589E;&#x52A0;&#x63CF;&#x8FF0;&#x3002;</p>
        <p>&#x6CE8;&#x610F;&#xFF1A;&#x9002;&#x7528;&#x4E8E;&#x539F;&#x6709;<code>v</code>&#x5B57;&#x6BB5;&#x542B;&#x4E49;&#x4E0D;&#x5927;&#xFF0C;&#x53EA;&#x5173;&#x6CE8;&#x63CF;&#x8FF0;&#x7684;&#x573A;&#x666F;&#xFF0C;&#x4F7F;&#x7528;&#x6B64;&#x63A5;&#x53E3;&#x540E;<code>v</code>&#x5B57;&#x6BB5;&#x5C06;&#x4E0D;&#x91C7;&#x96C6;</p>
      </td>
      <td style="text-align:left">ALL</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setViewContent</td>
      <td style="text-align:left">
        <p>&#x914D;&#x7F6E; view &#x7684; Tag&#xFF0C;&#x6807;&#x8BB0; View &#xFF0C;&#x5E76;&#x5728;
          GrowingIO&#x76F8;&#x5173;&#x4E8B;&#x4EF6;&#x4E2D;&#x53D1;&#x9001;&#xFF0C;&#x5185;&#x5BB9;&#x5BF9;&#x5E94; <code>xPath</code> &#x4E2D;&#x7684; <code>v</code>
        </p>
        <p>SDK&#x9ED8;&#x8BA4;&#x4E0D;&#x4F1A;&#x91C7;&#x96C6;ImageView&#x7684;&#x5185;&#x5BB9;&#xFF0C;&#x4E3A;&#x4E86;&#x80FD;&#x5BF9;&#x4E0D;&#x540C;&#x7684;&#x56FE;&#x7247;&#x5143;&#x7D20;&#xFF08;ImageView&#xFF09;&#x533A;&#x5206;&#x7EDF;&#x8BA1;&#xFF0C;&#x9700;&#x8981;&#x5BF9;&#x6BCF;&#x4E2A;&#x5177;&#x6709;&#x5206;&#x6790;&#x610F;&#x4E49;&#x7684;&#x56FE;&#x7247;&#x5143;&#x7D20;&#xFF08;ImageView&#xFF09;&#x6DFB;&#x52A0;&#x63CF;&#x8FF0;&#x3002;</p>
      </td>
      <td style="text-align:left">ALL</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setViewID</td>
      <td style="text-align:left">
        <p>&#x8BBE;&#x7F6E; View id &#xFF0C;&#x914D;&#x7F6E;&#x4E4B;&#x540E;&#x5BF9;&#x5E94;
          xPath &#x4E2D;&#x7684; view id&#xFF0C;SDK&#x5C06;&#x4F1A;&#x4F7F;&#x7528;Layout&#x6587;&#x4EF6;&#x4E2D;&#x7684;ID&#x6765;&#x8BC6;&#x522B;&#x4E00;&#x4E2A;&#x5143;&#x7D20;&#x3002;</p>
        <p>&#x5982;&#x679C;&#x90E8;&#x5206;&#x5143;&#x7D20;&#x5728;Layout&#x6587;&#x4EF6;&#x4E2D;&#x6CA1;&#x6709;ID&#xFF0C;&#x5EFA;&#x8BAE;&#x5728;Layout&#x6587;&#x4EF6;&#x4E2D;&#x6DFB;&#x52A0;&#x3002;</p>
        <p>&#x5BF9;&#x4E8E;&#x52A8;&#x6001;&#x751F;&#x6210;&#x7684;&#x5143;&#x7D20;&#xFF0C;&#x53EF;&#x4EE5;&#x4F7F;&#x7528;&#x5982;&#x4E0B;&#x65B9;&#x6CD5;&#x5BF9;&#x5B83;&#x8BBE;&#x7F6E;&#x552F;&#x4E00;&#x7684;ID&#x3002;</p>
        <p>&#x5F53;&#x60A8;&#x7684;&#x5E94;&#x7528;&#x754C;&#x9762;&#x6539;&#x7248;&#x65F6;&#xFF0C;&#x53EF;&#x80FD;&#x4F1A;&#x5BFC;&#x81F4;&#x65E0;&#x6CD5;&#x51C6;&#x786E;&#x5730;&#x7EDF;&#x8BA1;&#x5DF2;&#x7ECF;&#x5708;&#x9009;&#x7684;&#x5143;&#x7D20;&#x3002;&#x56E0;&#x6B64;&#xFF0C;&#x5BF9;&#x4E8E;&#x5E94;&#x7528;&#x4E2D;&#x7684;&#x4E3B;&#x8981;&#x6D41;&#x7A0B;&#x6D89;&#x53CA;&#x5230;&#x7684;&#x754C;&#x9762;&#x5143;&#x7D20;&#xFF0C;&#x5EFA;&#x8BAE;&#x60A8;&#x4E3A;&#x5B83;&#x4EEC;&#x8BBE;&#x7F6E;&#x56FA;&#x5B9A;&#x7684;&#x552F;&#x4E00;ID&#xFF0C;&#x4EE5;&#x4FDD;&#x8BC1;&#x6570;&#x636E;&#x7684;&#x4E00;&#x81F4;&#x6027;&#x3002;</p>
        <ul>
          <li>ID &#x53EA;&#x80FD;&#x8BBE;&#x7F6E;&#x4E3A;&#x5B57;&#x6BCD;&#x3001;&#x6570;&#x5B57;&#x548C;&#x4E0B;&#x5212;&#x7EBF;&#x7684;&#x7EC4;&#x5408;</li>
          <li>&#x5982;&#x679C;&#x5728;ViewGroup&#x4E0A;&#x8BBE;&#x7F6E;ID&#x7684;&#x8BDD;&#xFF0C;SDK&#x4F1A;&#x5FFD;&#x7565;&#x4ED6;&#x6240;&#x6709;&#x5B50;&#x5143;&#x7D20;&#x7684;&#x9ED8;&#x8BA4;ID&#xFF08;&#x5C31;&#x662F;&#x5199;&#x5728;xml&#x6587;&#x4EF6;&#x91CC;&#x7684;&#xFF09;&#x53EA;&#x4F1A;&#x4F7F;&#x7528;GrowingIO.setViewID&#x8BBE;&#x7F6E;&#x7684;ID&#x3002;</li>
          <li>&#x5BF9;&#x4E8E;&#x5DF2;&#x7ECF;&#x96C6;&#x6210;&#x8FC7;&#x65E7;&#x7248;SDK&#x5E76;&#x5708;&#x9009;&#x8FC7;&#x7684;&#x5E94;&#x7528;&#xFF0C;&#x5BF9;&#x67D0;&#x4E2A;&#x5143;&#x7D20;&#x8BBE;&#x7F6E;ID&#x540E;&#x518D;&#x5708;&#x9009;&#x5B83;&#xFF0C;&#x6307;&#x6807;&#x6570;&#x503C;&#x4F1A;&#x4ECE;&#x96F6;&#x5F00;&#x59CB;&#x8BA1;&#x7B97;&#xFF0C;&#x7C7B;&#x4F3C;&#x521D;&#x6B21;&#x96C6;&#x6210;SDK&#x540E;&#x53D1;&#x7248;&#x7684;&#x6548;&#x679C;&#xFF0C;&#x4F46;&#x4E0D;&#x5F71;&#x54CD;&#x4E4B;&#x524D;&#x5708;&#x9009;&#x7684;&#x5176;&#x5B83;&#x6307;&#x6807;&#x6570;&#x636E;&#x3002;&#x5982;&#x679C;&#x4E0D;&#x5E0C;&#x671B;&#x51FA;&#x73B0;&#x8FD9;&#x79CD;&#x60C5;&#x51B5;&#xFF0C;&#x8BF7;&#x4E0D;&#x8981;&#x4F7F;&#x7528;&#x8FD9;&#x4E2A;&#x65B9;&#x6CD5;</li>
        </ul>
      </td>
      <td style="text-align:left">ALL</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setChannel</td>
      <td style="text-align:left">
        <ul>
          <li><b>&lt;2.6.5 &#x7248;&#x672C;</b>&#xFF1A; &#x5148;&#x8BBE;&#x7F6E;&#x6E20;&#x9053;&#x4FE1;&#x606F;&#xFF0C;&#x518D;&#x53D1;&#x9001;&#x6570;&#x636E;
            &#x80FD;&#x591F;&#x4FDD;&#x8BC1;&#x6240;&#x6709;&#x6570;&#x636E;&#x90FD;&#x4E00;&#x5B9A;&#x4F1A;&#x5E26;&#x4E0A;&#x6E20;&#x9053;&#x4FE1;&#x606F;&#x3002;</li>
          <li><b>&gt;=2.6.5 &#x7248;&#x672C;</b>&#xFF1A; &#x4FDD;&#x7559;&#x539F;&#x6709;&#x8BBE;&#x7F6E;&#x6E20;&#x9053;&#x4FE1;&#x606F;&#x7684;&#x65B9;&#x6CD5;&#xFF0C;&#x65B0;&#x589E;&#x5728;&#x8FD0;&#x884C;&#x65F6;&#x8BBE;&#x7F6E;&#x6E20;&#x9053;&#x4FE1;&#x606F;&#x3002;&#x65B0;&#x589E;&#x7684;&#x63A5;&#x53E3;&#x65E0;&#x6CD5;&#x4FDD;&#x8BC1;&#x6240;&#x6709;&#x6570;&#x636E;&#x90FD;&#x4E00;&#x5B9A;&#x4F1A;&#x5E26;&#x4E0A;&#x6E20;&#x9053;&#x4FE1;&#x606F;&#xFF08;&#x867D;&#x7136;&#x6211;&#x4EEC;&#x4F1A;&#x901A;&#x8FC7;&#x91CD;&#x53D1;&#x673A;&#x5236;&#x8FDB;&#x884C;&#x4FDD;&#x8BC1;&#xFF0C;&#x4F46;&#x662F;&#x65E0;&#x6CD5;&#x505A;&#x5230;100%&#xFF09;&#x3002;</li>
        </ul>
      </td>
      <td style="text-align:left">ALL</td>
      <td style="text-align:left">-</td>
    </tr>
  </tbody>
</table>

\#\#\# 数据采集API

<table>
  <thead>
    <tr>
      <th style="text-align:left">API</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
      <th style="text-align:left">&#x65E0;&#x57CB;&#x70B9;SDK&#x7248;&#x672C;&#x652F;&#x6301;</th>
      <th style="text-align:left">&#x57CB;&#x70B9;SDK&#x7248;&#x672C;&#x652F;&#x6301;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">isDeeplinkUrl</td>
      <td style="text-align:left">&#x6821;&#x9A8C;&#x94FE;&#x63A5;URI&#x662F;&#x5426;&#x6EE1;&#x8DB3;GIO&#x7684;&#x683C;&#x5F0F;&#xFF0C;&#x5982;&quot;gio.ren&quot;&#x6216;&quot;.datayi.cn&quot;&#x7ED3;&#x5C3E;&#x7B49;</td>
      <td
      style="text-align:left">&gt;=2.8.11</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">doDeeplinkByUrl</td>
      <td style="text-align:left">true &#x8868;&#x793A;&#x662F;GIO&#x7684;deeplink&#x94FE;&#x63A5;&#xFF0C;&#x8FDB;&#x884C;&#x4E0B;&#x4E00;&#x6B65;&#x5224;&#x65AD;&#xFF0C;
        false &#x8868;&#x793A;&#x975E;GIO&#x76F8;&#x5173;&#x94FE;&#x63A5;.&#x53C2;&#x6570;callback&#x4E0D;&#x586B;&#x5219;&#x9ED8;&#x8BA4;&#x4F7F;&#x7528;&#x5168;&#x5C40;&#x521D;&#x59CB;&#x5316;&#x65F6;&#x8BBE;&#x7F6E;&#x7684;callback</td>
      <td
      style="text-align:left">&gt;=2.8.11</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">disableDataCollect</td>
      <td style="text-align:left">&#x9075;&#x5B88;&#x6B27;&#x6D32;&#x8054;&#x76DF;&#x51FA;&#x53F0;&#x7684;&#x901A;&#x7528;&#x6570;&#x636E;&#x4FDD;&#x62A4;&#x6761;&#x4F8B;&#xFF0C;&#x7528;&#x6237;&#x4E0D;&#x6388;&#x6743;&#xFF0C;&#x4E0D;&#x91C7;&#x96C6;&#x7528;&#x6237;&#x6570;&#x636E;</td>
      <td
      style="text-align:left">&gt;=2.3.2</td>
        <td style="text-align:left">ALL</td>
    </tr>
    <tr>
      <td style="text-align:left">enableDataCollect</td>
      <td style="text-align:left">&#x9075;&#x5B88;&#x6B27;&#x6D32;&#x8054;&#x76DF;&#x51FA;&#x53F0;&#x7684;&#x901A;&#x7528;&#x6570;&#x636E;&#x4FDD;&#x62A4;&#x6761;&#x4F8B;&#xFF0C;&#x7528;&#x6237;&#x6388;&#x6743;&#xFF0C;&#x91C7;&#x96C6;&#x7528;&#x6237;&#x6570;&#x636E;</td>
      <td
      style="text-align:left">&gt;=2.3.2</td>
        <td style="text-align:left">ALL</td>
    </tr>
    <tr>
      <td style="text-align:left">disable</td>
      <td style="text-align:left">GrowingIO&#x505C;&#x6B62;&#x91C7;&#x96C6;</td>
      <td style="text-align:left">ALL</td>
      <td style="text-align:left">ALL</td>
    </tr>
    <tr>
      <td style="text-align:left">resume</td>
      <td style="text-align:left">GrowingIO&#x6062;&#x590D;&#x91C7;&#x96C6;</td>
      <td style="text-align:left">ALL</td>
      <td style="text-align:left">ALL</td>
    </tr>
    <tr>
      <td style="text-align:left">stop</td>
      <td style="text-align:left">GrowingIO&#x505C;&#x6B62;&#x91C7;&#x96C6;&#xFF0C;&#x53EF;&#x4EE5;&#x4E0D;&#x5728;&#x4E3B;&#x7EBF;&#x7A0B;&#x8C03;&#x7528;</td>
      <td
      style="text-align:left">ALL</td>
        <td style="text-align:left">ALL</td>
    </tr>
    <tr>
      <td style="text-align:left">setThrottle</td>
      <td style="text-align:left">&#x662F;&#x5426;&#x8282;&#x6D41;&#x53D1;&#x9001;&#xFF08;&#x8282;&#x6D41;&#x53D1;&#x9001;&#x65F6;imp&#x4E0D;&#x53D1;&#x9001;&#xFF09;&#xFF0C;&#x5185;&#x90E8;&#x5B9E;&#x9645;&#x8C03;&#x7528;
        Configuration &#x4E2D;&#x7684;&#x540C;&#x540D;&#x65B9;&#x6CD5;&#xFF0C;&#x6240;&#x4EE5;&#x5728;&#x521D;&#x59CB;&#x5316;&#x65F6;&#x5019;&#x914D;&#x7F6E;&#x548C;&#x8FD0;&#x884C;&#x65F6;&#x52A8;&#x6001;&#x914D;&#x7F6E;&#xFF0C;&#x6548;&#x679C;&#x4E00;&#x6837;&#x3002;</td>
      <td
      style="text-align:left">ALL</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setImp</td>
      <td style="text-align:left"><code>imp</code>&#x4E8B;&#x4EF6;&#x5F00;&#x5173;&#xFF0C;<code>true</code> &#x4E3A;&#x6253;&#x5F00;</td>
      <td
      style="text-align:left">ALL</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">disableImpression</td>
      <td style="text-align:left">&#x4E0D;&#x53D1;&#x9001;<code>imp</code>
      </td>
      <td style="text-align:left">ALL</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">ignoredView</td>
      <td style="text-align:left">
        <p>&#x5FFD;&#x7565;&#x914D;&#x7F6E;&#x7684; View &#xFF0C;&#x4E0D;&#x91C7;&#x96C6;&#x7528;&#x6237;&#x6570;&#x636E;&#x3002;</p>
        <p>&#x5982;&#x679C;&#x60A8;&#x9700;&#x8981;&#x5FFD;&#x7565;&#x67D0;&#x4E9B;&#x7279;&#x6B8A;&#x5185;&#x5BB9;&#xFF0C;&#x6BD4;&#x5982;&#x5012;&#x8BA1;&#x65F6;&#x5143;&#x7D20;&#x6216;&#x6D89;&#x53CA;&#x9690;&#x79C1;&#x7684;&#x5185;&#x5BB9;&#xFF0C;&#x53EF;&#x4EE5;&#x4F7F;&#x7528;&#x6B64;&#x63A5;&#x53E3;&#x3002;</p>
      </td>
      <td style="text-align:left">ALL</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">ignoreFragment</td>
      <td style="text-align:left">&#x4E0D;&#x91C7;&#x96C6;&#x914D;&#x7F6E;&#x7684; Fragment &#x9875;&#x9762;&#x6D4F;&#x89C8;&#x4E8B;&#x4EF6;&#xFF08;<code>page</code>&#xFF09;&#xFF0C;&#x4E0D;&#x5C06;<code>Fragment</code>&#x89C6;&#x4F5C;&#x4E00;&#x4E2A;&#x9875;&#x9762;&#xFF0C;&#x53EF;&#x4EE5;&#x7406;&#x89E3;&#x6210;&#x5F53;&#x4F5C;&#x4E3A;&#x4E00;&#x4E2A;&#x53EF;&#x70B9;&#x51FB;&#x7684;view&#x3002;&#x81EA;&#x52A8;&#x91C7;&#x96C6;&#x7528;&#x6237;&#x884C;&#x4E3A;&#x4E8B;&#x4EF6;&#xFF08;<code>clck&#x3001;chng</code>&#xFF09;&#x548C;&#x5143;&#x7D20;&#x5C55;&#x793A;&#x4E8B;&#x4EF6;&#xFF08;<code>imp</code>&#xFF09;&#x3002;</td>
      <td
      style="text-align:left">ALL</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">ignoreFragmentX</td>
      <td style="text-align:left">&#x652F;&#x6301; AndroidX &#xFF0C; &#x529F;&#x80FD;&#x540C; ignoreFragment&#x3002;</td>
      <td
      style="text-align:left">&gt;=2.6.6</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">ignoreViewImp</td>
      <td style="text-align:left">
        <p>&#x5FFD;&#x7565;&#x914D;&#x7F6E;&#x7684; View &#xFF0C;&#x4E0D;&#x91C7;&#x96C6;&#x7528;&#x6237;&#x5143;&#x7D20;&#x6D4F;&#x89C8;&#x6570;&#x636E;&#x3002;</p>
        <p>&#x5982;&#x679C;&#x60A8;&#x9700;&#x8981;&#x5FFD;&#x7565;&#x67D0;&#x4E9B;&#x5927;&#x91CF;&#x7684;
          &#x6570;&#x636E;&#xFF0C;&#x6BD4;&#x5982;&#x5F39;&#x5E55;&#xFF0C;&#x53EF;&#x4EE5;&#x4F7F;&#x7528;&#x6B64;&#x63A5;&#x53E3;&#x3002;</p>
      </td>
      <td style="text-align:left">&gt;=2.6.7</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setPageName</td>
      <td style="text-align:left">
        <p>&#x8BBE;&#x7F6E;&#x9875;&#x9762;&#x522B;&#x540D;&#xFF0C;&#x6709;&#x4E9B;&#x65F6;&#x5019;&#xFF0C;&#x5BF9;&#x4E8E;&#x5B8C;&#x6210;&#x67D0;&#x4E2A;&#x529F;&#x80FD;&#x7684;&#x9875;&#x9762;&#xFF0C;&#x7EDF;&#x8BA1;&#x65F6;&#x53EF;&#x80FD;&#x9700;&#x8981;&#x8FDB;&#x4E00;&#x6B65;&#x7EC6;&#x5206;&#x3002;
          &#x6BD4;&#x5982;&#xFF0C;&#x5BF9;&#x4E8E;&#x5C55;&#x793A;&#x5546;&#x54C1;&#x5217;&#x8868;&#x7684;&#x9875;&#x9762;&#xFF0C;&#x9700;&#x8981;&#x533A;&#x5206;&#x8863;&#x7269;&#x7C7B;&#x5546;&#x54C1;&#xFF0C;&#x4EE5;&#x53CA;&#x98DF;&#x54C1;&#x7C7B;&#x5546;&#x54C1;&#x7684;&#x4E24;&#x79CD;&#x5217;&#x8868;&#x7684;&#x8BBF;&#x95EE;&#x91CF;&#x3002;</p>
        <p>&#x200B;</p>
        <p>&#x6CE8;&#x610F;</p>
        <ol>
          <li>&#x5FC5;&#x987B;&#x5728;&#x8BE5;<code>Activity</code>&#x7684;<code>onCreate</code>&#x65B9;&#x6CD5;&#x4E2D;&#x5B8C;&#x6210;&#x8BE5;&#x5C5E;&#x6027;&#x7684;&#x8D4B;&#x503C;&#x64CD;&#x4F5C;&#x3002;</li>
          <li>&#x9875;&#x9762;&#x522B;&#x540D;&#x53EA;&#x80FD;&#x8BBE;&#x7F6E;&#x4E3A;&#x5B57;&#x6BCD;&#x3001;&#x6570;&#x5B57;&#x548C;&#x4E0B;&#x5212;&#x7EBF;&#x7684;&#x7EC4;&#x5408;&#x3002;</li>
          <li>&#x4E3A;&#x67E5;&#x770B;&#x6570;&#x636E;&#x65B9;&#x4FBF;&#xFF0C;&#x8BF7;&#x5C3D;&#x91CF;&#x5BF9;iOS&#x548C;&#x5B89;&#x5353;&#x7684;&#x540C;&#x529F;&#x80FD;&#x9875;&#x9762;&#x53D6;&#x4E0D;&#x540C;&#x7684;&#x540D;&#x79F0;&#x3002;</li>
        </ol>
      </td>
      <td style="text-align:left">ALL</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setPageNameX</td>
      <td style="text-align:left">&#x652F;&#x6301; AndroidX &#xFF0C; &#x529F;&#x80FD;&#x540C; setPageName&#x3002;</td>
      <td
      style="text-align:left">&gt;=2.6.6</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">getSessionId</td>
      <td style="text-align:left">&#x5F97;&#x5230; session id</td>
      <td style="text-align:left">ALL</td>
      <td style="text-align:left">ALL</td>
    </tr>
    <tr>
      <td style="text-align:left">getDeviceId</td>
      <td style="text-align:left">&#x83B7;&#x53D6;&#x8BBE;&#x5907;id&#xFF0C;&#x5BF9;&#x5E94;&#x6570;&#x636E;&#x91C7;&#x96C6;&#x7684;<code>u</code>&#x5B57;&#x6BB5;&#xFF0C;&#x53C8;&#x79F0;&#x4E3A;<code>&#x533F;&#x540D;&#x7528;&#x6237;id</code>&#xFF0C;&#x7528;&#x6765;&#x5B9A;&#x4E49;&#x4E00;&#x53F0;&#x8BBE;&#x5907;&#xFF0C;SDK
        &#x81EA;&#x52A8;&#x751F;&#x6210;&#x3002;</td>
      <td style="text-align:left">ALL</td>
      <td style="text-align:left">ALL</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x200B;trackBanner</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x6240;&#x6709;&#x5E7F;&#x544A;&#x56FE;&#x5BF9;&#x5E94;&#x7684;&#x5E7F;&#x544A;&#x5185;&#x5BB9;&#x63CF;&#x8FF0;&#xFF0C;&#x5185;&#x5BB9;&#x63CF;&#x8FF0;&#x9700;&#x8981;&#x8DDF;&#x5E7F;&#x544A;&#x7684;&#x987A;&#x5E8F;&#x76F8;&#x540C;&#x3002;</td>
      <td
      style="text-align:left">ALL</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x200B;trackEditText</td>
      <td style="text-align:left">
        <p>&#x200B;SDK &#x9ED8;&#x8BA4;&#x4E0D;&#x91C7;&#x96C6;&#x7528;&#x6237;&#x8F93;&#x5165;&#x6846;&#x7684;&#x5185;&#x5BB9;&#xFF0C;&#x8BBE;&#x7F6E;&#x4EE5;&#x540E;&#xFF0C;&#x91C7;&#x96C6;&#x9664;&#x4E86;&#x5BC6;&#x7801;&#x4EE5;&#x5916;&#x7684;&#x8F93;&#x5165;&#x6846;&#x6587;&#x672C;&#x5185;&#x5BB9;&#x3002;&#x200B;&#x200B;</p>
        <p>&#x5F53;&#x8FD9;&#x4E2A;&#x8F93;&#x5165;&#x6846;&#x5931;&#x53BB;&#x7126;&#x70B9;&#xFF08;&#x5305;&#x62EC;&#x5E94;&#x7528;&#x9000;&#x5230;&#x540E;&#x53F0;&#xFF09;&#xFF0C;&#x4E14;&#x8F93;&#x5165;&#x6846;&#x5185;&#x5BB9;&#x8DDF;&#x83B7;&#x53D6;&#x7126;&#x70B9;&#x524D;&#x76F8;&#x6BD4;&#x53D1;&#x751F;&#x53D8;&#x5316;&#x65F6;&#xFF0C;&#x8F93;&#x5165;&#x6846;&#x5185;&#x6587;&#x5B57;&#x4F1A;&#x88AB;&#x53D1;&#x9001;&#x56DE;GrowingIO&#x3002;</p>
        <p>&#x6CE8;&#x610F;&#xFF1A;&#x5BF9;&#x4E8E;&#x5BC6;&#x7801;&#x8F93;&#x5165;&#x6846;&#xFF0C;&#x5373;&#x4FBF;&#x6807;&#x8BB0;&#x4E3A;&#x9700;&#x8981;&#x91C7;&#x96C6;&#xFF0C;SDK&#x4E5F;&#x4F1A;&#x5FFD;&#x7565;&#xFF0C;&#x4E0D;&#x91C7;&#x96C6;&#x5B83;&#x7684;&#x6570;&#x636E;&#x3002;</p>
      </td>
      <td style="text-align:left">ALL</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">trackFragment</td>
      <td style="text-align:left">
        <p>&#x5982;&#x679C;APP&#x521D;&#x59CB;&#x5316;&#x65F6;&#x5019;&#xFF0C;&#x6CA1;&#x6709;&#x8BBE;&#x7F6E; <code>trackAllFragment</code> &#x5373;&#x4E0D;&#x91C7;&#x96C6;&#x5168;&#x90E8; <code>Fragment</code>&#xFF0C;&#x53EF;&#x4EE5;&#x9009;&#x62E9;&#x6027;&#x91C7;&#x96C6;&#x6307;&#x5B9A; <code>Fragment</code>&#xFF0C;&#x8BBE;&#x7F6E;&#x4E4B;&#x540E;
          sdk &#x5C06;&#x76D1;&#x542C; <code>Fragment</code> &#x7684;&#x5404;&#x4E2A;&#x751F;&#x547D;&#x5468;&#x671F;&#xFF0C;
          &#x91C7;&#x96C6;&#x76F8;&#x5173;&#x7528;&#x6237;&#x884C;&#x4E3A;&#x6570;&#x636E;&#x3002;</p>
        <p>&#x8BF7;&#x5728; <code>new Fragment</code> &#x7684;&#x65F6;&#x5019;&#x8C03;&#x7528;&#x6B64;&#x65B9;&#x6CD5;&#x3002;</p>
      </td>
      <td style="text-align:left">ALL</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">trackFragmentX</td>
      <td style="text-align:left">
        <p>&#x652F;&#x6301; AndroidX &#xFF0C; &#x529F;&#x80FD;&#x540C; trackFragment&#x3002;</p>
        <p>&#x8BF7;&#x5728; <code>new Fragment</code> &#x7684;&#x65F6;&#x5019;&#x8C03;&#x7528;&#x6B64;&#x65B9;&#x6CD5;&#x3002;</p>
      </td>
      <td style="text-align:left">&gt;=2.6.6</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">trackWebView</td>
      <td style="text-align:left">&#x91C7;&#x96C6; <code>WebView</code> &#x4E8B;&#x4EF6;&#xFF0C;&#x9ED8;&#x8BA4;&#x91C7;&#x96C6;&#xFF0C;&#x60A8;&#x53EF;&#x4EE5;&#x5728;&#x4E0D;&#x5168;&#x91CF;&#x91C7;&#x96C6;<code>WebView</code>&#x7684;&#x65F6;&#x5019;&#xFF0C;&#x5B9A;&#x5236;&#x91C7;&#x96C6;&#x67D0;&#x4E2A;<code>WebView</code>
      </td>
      <td style="text-align:left">&gt;=2.8.22</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">trackX5WebView</td>
      <td style="text-align:left">&#x91C7;&#x96C6; X5WebView &#x4E8B;&#x4EF6;&#xFF0C;&#x9ED8;&#x8BA4;&#x91C7;&#x96C6;</td>
      <td
      style="text-align:left">&lt;2.6.0</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setTabName</td>
      <td style="text-align:left">&#x5982;&#x679C;&#x60A8;&#x6709;&#x67D0;&#x4E9B;View&#x52A8;&#x6001;&#x6DFB;&#x52A0;&#x5230;ViewTree&#x4E2D;&#x5E76;&#x4E14;&#x5728;&#x7236;&#x5BB9;&#x5668;&#x4E2D;&#x7684;&#x4F4D;&#x7F6E;&#x4E0D;&#x56FA;&#x5B9A;&#xFF08;&#x4F8B;&#x5982;&#x5E38;&#x89C1;&#x7684;&#x591A;Fragment&#x5B9E;&#x73B0;&#x7684;Tab&#x5207;&#x6362;&#xFF09;&#xFF0C;&#x8BF7;&#x7ED9;&#x6BCF;&#x4E2A;View&#x8BBE;&#x7F6E;ID&#x6765;&#x8F85;&#x52A9;&#x7EDF;&#x8BA1;</td>
      <td
      style="text-align:left">ALL</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setImeiEnable</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x4E3A; false &#x5219; SDK &#x4E0D;&#x91C7;&#x96C6; <code>imei&#xFF0C;</code>&#x9002;&#x7528;&#x4E8E;<b>&#x6D77;&#x5916;&#x5E94;&#x7528;&#x5E02;&#x573A;</b>&#x4E0A;&#x67B6;&#x7684;&#x5E94;&#x7528;&#x3002;</td>
      <td
      style="text-align:left">&gt;=2.7.8</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setAndroidIdEnable</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x4E3A; false &#x5219; SDK &#x4E0D;&#x91C7;&#x96C6; <code>androidId</code> ,&#x9002;&#x7528;&#x4E8E;<b>&#x6D77;&#x5916;&#x5E94;&#x7528;&#x5E02;&#x573A;</b>&#x4E0A;&#x67B6;&#x7684;&#x5E94;&#x7528;&#x3002;</td>
      <td
      style="text-align:left">&gt;=2.7.8</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setGoogleAdIdEnable</td>
      <td style="text-align:left">&#x8BBE;&#x7F6E;&#x4E3A; false &#x5219; SDK &#x4E0D;&#x91C7;&#x96C6; <code>GoogleAdId</code> ,&#x9002;&#x7528;&#x4E8E;<b>&#x6D77;&#x5916;&#x5E94;&#x7528;&#x5E02;&#x573A;</b>&#x4E0A;&#x67B6;&#x7684;&#x5E94;&#x7528;&#x3002;</td>
      <td
      style="text-align:left">&gt;=2.7.8</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setOAIDEnable</td>
      <td style="text-align:left">&#x56FD;&#x5185;<a href="http://www.msa-alliance.cn/col.jsp?id=120">&#x79FB;&#x52A8;&#x5B89;&#x5168;&#x8054;&#x76DF;MSA</a> &#x8054;&#x5408;&#x5404;&#x5927;&#x624B;&#x673A;&#x5236;&#x9020;&#x5546;&#x63A8;&#x51FA;&#x4E86;
        OAID &#xFF0C; &#x4F5C;&#x4E3A;&#x552F;&#x4E00;&#x5E7F;&#x544A;&#x6807;&#x8BC6;&#x7B26;&#x3002;<b>Android 2.8.5</b> &#x65B0;&#x589E;&#x3002;</td>
      <td
      style="text-align:left">&gt;=2.8.5</td>
        <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">bridgeForWebView</td>
      <td style="text-align:left">&#x63D0;&#x4F9B;&#x539F;&#x751F;&#x7684; WebView bridge&#x4F9B;hybrid&#x8C03;&#x7528;,
        &#x652F;&#x6301;hybrid&#x4E8B;&#x4EF6;&#x53D1;&#x9001;</td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">&gt;=2.9.0</td>
    </tr>
    <tr>
      <td style="text-align:left">bridgeForX5WebView</td>
      <td style="text-align:left">&#x63D0;&#x4F9B;&#x817E;&#x8BAF;X5&#x5185;&#x6838;&#x7684;WebView bridge&#x4F9B;hybrid&#x8C03;&#x7528;,
        &#x652F;&#x6301;hybrid&#x4E8B;&#x4EF6;&#x53D1;&#x9001;</td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">&gt;=2.9.0</td>
    </tr>
  </tbody>
</table>

