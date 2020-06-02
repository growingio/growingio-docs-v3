# 埋点事件与变量字段

{% tabs %}
{% tab title="custom\_event（埋点事件）" %}
| 名称 | 类型（长度） | 说明 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">visitUserId</th>
      <th style="text-align:left">string&#xFF08;64&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x8BBF;&#x95EE;&#x7528;&#x6237;ID&gt;</p>
        <p>&#x8BBF;&#x95EE;&#x7528;&#x6237;&#x7684;&#x552F;&#x4E00;&#x6807;&#x8BC6;&#xFF0C;&#x7531;GrowingIo&#x81EA;&#x52A8;&#x751F;&#x6210;&#x3002;
          &#x793A;&#x4F8B;&#xFF1A;fc55728b-41ab-42ff-8b1f-714e44c65fd6</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">sessionId</th>
      <th style="text-align:left">string&#xFF08;50&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x8BBF;&#x95EE;ID&gt;</p>
        <p>&#x5F53;&#x524D;&#x8BBF;&#x95EE;&#x7684;&#x552F;&#x4E00;&#x6807;&#x8BC6;&#x3002;
          &#x793A;&#x4F8B;&#xFF1A;6b5099c7-6006-422d-92ac-4f3bf4ddd37c</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">time</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&lt;&#x65F6;&#x95F4;&#x6233;&gt;</p>
        <p>&#x4E8B;&#x4EF6;&#x53D1;&#x751F;&#x7684;&#x65F6;&#x95F4;&#x6233;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1520899220665</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">sendTime</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&lt;&#x53D1;&#x9001;&#x65F6;&#x95F4;&gt;</p>
        <p>&#x8BF7;&#x6C42;&#x5728;SDK&#x53D1;&#x9001;&#x7684;&#x65F6;&#x95F4;&#x6233;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1520899221211</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">pageTime</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&lt;&#x9875;&#x9762;&#x65F6;&#x95F4;&gt;</p>
        <p>pvar&#x5BF9;&#x5E94;&#x7684;&#x9875;&#x9762;&#x8BF7;&#x6C42;&#x7684;&#x4EA7;&#x751F;&#x65F6;&#x95F4;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1516349263375</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">domain</th>
      <th style="text-align:left">string&#xFF08;100&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x57DF;&#x540D;&gt;</p>
        <p>&#x8BBF;&#x95EE;&#x7684;&#x57DF;&#x540D;&#xFF0C;&#x5F53;&#x4E3A; iOS /
          Android &#x65F6;&#xFF0C;&#x4E3A; app &#x5305;&#x540D;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;www.growingio.com</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">page</th>
      <th style="text-align:left">string&#xFF08;1024&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x9875;&#x9762;&gt;</p>
        <p>&#x7528;&#x6237;&#x8BBF;&#x95EE;&#x7684;&#x5F53;&#x524D;&#x9875;&#x9762;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;pages/index</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">queryParameters</th>
      <th style="text-align:left">string &#xFF08;1024&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x67E5;&#x8BE2;&#x53C2;&#x6570;&gt;</p>
        <p>&#x5F53;&#x524D;&#x7F51;&#x7AD9;&#x9875;&#x9762;URL&#x4E2D;&#x7684;&#x67E5;&#x8BE2;&#x53C2;&#x6570;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;cid=1234567</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">eventName</th>
      <th style="text-align:left">string&#xFF08;50&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x4E8B;&#x4EF6;&#x540D;&#x79F0;&gt;</p>
        <p>&#x81EA;&#x5B9A;&#x4E49;&#x4E8B;&#x4EF6;&#x7684;&#x6807;&#x8BC6;&#x7B26;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;recenue</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">eventNumber</th>
      <th style="text-align:left">double</th>
      <th style="text-align:left">
        <p>&lt;&#x4E8B;&#x4EF6;&#x6570;&#x91CF;&gt;</p>
        <p>&#x5DF2;&#x5E9F;&#x5F03;&#xFF0C;&#x8BF7;&#x5FFD;&#x7565;&#x6B64;&#x5B57;&#x6BB5;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">eventVariable</th>
      <th style="text-align:left">map&lt;string,string&gt;</th>
      <th style="text-align:left">
        <p>&lt;&#x4E8B;&#x4EF6;&#x7EA7;&#x53D8;&#x91CF;&gt;</p>
        <p>&#x81EA;&#x5B9A;&#x4E49;&#x4E8B;&#x4EF6;&#x7EA7;&#x53D8;&#x91CF;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;{&quot;price&quot;:&quot;50.0&quot;,&quot;item&quot;:&quot;101&quot;}</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">loginUserId</th>
      <th style="text-align:left">string&#xFF08;200&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x767B;&#x5F55;&#x7528;&#x6237;ID&gt;</p>
        <p>&#x63A8;&#x8350;&#x4F7F;&#x7528;&#x90A3;&#x4E9B;&#x4E0D;&#x80FD;&#x5B9A;&#x4F4D;&#x5230;&#x4E2A;&#x4EBA;&#x7684;ID&#x4FE1;&#x606F;&#xFF0C;&#x901A;&#x5E38;&#x4E3A;&#x4F01;&#x4E1A;&#x5185;&#x90E8;&#x4F7F;&#x7528;&#x7684;CRM
          ID&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;user12345</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">pageRequestId</th>
      <th style="text-align:left">string&#xFF08;23&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x9875;&#x9762;&#x8BF7;&#x6C42;ID&gt;</p>
        <p>GrowingIO&#x7CFB;&#x7EDF;&#x5185;&#x90E8;&#x7528;&#x4E8E;&#x6807;&#x8BC6;&#x4E00;&#x4E2A;&#x552F;&#x4E00;&#x7684;&#x9875;&#x9762;&#x8BF7;&#x6C42;&#x7684;ID&#xFF0C;&#x53EF;&#x4EE5;&#x7528;&#x6765;&#x5173;&#x8054;page
          &#x6570;&#x636E;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1521010820647fa5a9314e6</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="pvar（自定义页面变量）" %}
| 名称 | 类型（长度） | 说明 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">visitUserId</th>
      <th style="text-align:left">string&#xFF08;64&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x8BBF;&#x95EE;&#x7528;&#x6237;ID&gt;</p>
        <p>&#x8BBF;&#x95EE;&#x7528;&#x6237;&#x7684;&#x552F;&#x4E00;&#x6807;&#x8BC6;&#xFF0C;&#x7531;GrowingIo&#x81EA;&#x52A8;&#x751F;&#x6210;&#x3002;
          &#x793A;&#x4F8B;&#xFF1A;fc55728b-41ab-42ff-8b1f-714e44c65fd6</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">sessionId</th>
      <th style="text-align:left">string&#xFF08;50&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x8BBF;&#x95EE;ID&gt;</p>
        <p>&#x5F53;&#x524D;&#x8BBF;&#x95EE;&#x7684;&#x552F;&#x4E00;&#x6807;&#x8BC6;&#x3002;
          &#x793A;&#x4F8B;&#xFF1A;6b5099c7-6006-422d-92ac-4f3bf4ddd37c</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">time</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&lt;&#x65F6;&#x95F4;&#x6233;&gt;</p>
        <p>&#x4E8B;&#x4EF6;&#x53D1;&#x751F;&#x7684;&#x65F6;&#x95F4;&#x6233;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1520899220665</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">sendTime</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&lt;&#x53D1;&#x9001;&#x65F6;&#x95F4;&gt;</p>
        <p>&#x8BF7;&#x6C42;&#x5728;SDK&#x53D1;&#x9001;&#x7684;&#x65F6;&#x95F4;&#x6233;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1520899221211</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">pageTime</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&lt;&#x9875;&#x9762;&#x65F6;&#x95F4;&gt;</p>
        <p>pvar&#x5BF9;&#x5E94;&#x7684;&#x9875;&#x9762;&#x8BF7;&#x6C42;&#x7684;&#x4EA7;&#x751F;&#x65F6;&#x95F4;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1520899221209</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">domain</th>
      <th style="text-align:left">string&#xFF08;100&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x57DF;&#x540D;&gt;</p>
        <p>&#x8BBF;&#x95EE;&#x7684;&#x57DF;&#x540D;&#xFF0C;&#x5F53;&#x4E3A; iOS /
          Android &#x65F6;&#xFF0C;&#x4E3A; app &#x5305;&#x540D;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;growingio.com</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">page</th>
      <th style="text-align:left">string&#xFF08;1024&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x9875;&#x9762;&gt;</p>
        <p>&#x7528;&#x6237;&#x8BBF;&#x95EE;&#x7684;&#x5F53;&#x524D;&#x9875;&#x9762;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;pages/funnel</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">pageVariable</th>
      <th style="text-align:left">map&lt;string,string&gt;</th>
      <th style="text-align:left">
        <p>&lt;&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&gt;</p>
        <p>&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&#x952E;&#x503C;&#x5BF9;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;{&quot;category&quot;:&quot;funnel&quot;}</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">pageRequestId</th>
      <th style="text-align:left">string&#xFF08;23&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x9875;&#x9762;&#x8BF7;&#x6C42;ID&gt;</p>
        <p>GrowingIO&#x7CFB;&#x7EDF;&#x5185;&#x90E8;&#x7528;&#x4E8E;&#x6807;&#x8BC6;&#x4E00;&#x4E2A;&#x552F;&#x4E00;&#x7684;&#x9875;&#x9762;&#x8BF7;&#x6C42;&#x7684;ID&#xFF0C;&#x53EF;&#x4EE5;&#x7528;&#x6765;&#x5173;&#x8054;page
          &#x6570;&#x636E;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1521010820647fa5a9314e6</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="evar（转化变量）" %}
| 名称 | 类型（长度） | 说明 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">visitUserId</th>
      <th style="text-align:left">string&#xFF08;64&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x8BBF;&#x95EE;&#x7528;&#x6237;ID&gt;</p>
        <p>&#x8BBF;&#x95EE;&#x7528;&#x6237;&#x7684;&#x552F;&#x4E00;&#x6807;&#x8BC6;&#xFF0C;&#x7531;GrowingIo&#x81EA;&#x52A8;&#x751F;&#x6210;&#x3002;
          &#x793A;&#x4F8B;&#xFF1A;fc55728b-41ab-42ff-8b1f-714e44c65fd6</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">sessionId</th>
      <th style="text-align:left">string&#xFF08;50&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x8BBF;&#x95EE;ID&gt;</p>
        <p>&#x5F53;&#x524D;&#x8BBF;&#x95EE;&#x7684;&#x552F;&#x4E00;&#x6807;&#x8BC6;&#x3002;
          &#x793A;&#x4F8B;&#xFF1A;6b5099c7-6006-422d-92ac-4f3bf4ddd37c</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">time</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&lt;&#x65F6;&#x95F4;&#x6233;&gt;</p>
        <p>&#x8BF7;&#x6C42;&#x53D1;&#x751F;&#x7684;&#x65F6;&#x95F4;&#x6233;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1520899220665</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">sendTime</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&lt;&#x53D1;&#x9001;&#x65F6;&#x95F4;&gt;</p>
        <p>&#x8BF7;&#x6C42;&#x5728;SDK&#x53D1;&#x9001;&#x7684;&#x65F6;&#x95F4;&#x6233;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1520899221211</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">domain</th>
      <th style="text-align:left">string&#xFF08;100&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x57DF;&#x540D;&gt;</p>
        <p>&#x8BBF;&#x95EE;&#x7684;&#x57DF;&#x540D;&#xFF0C;&#x5F53;&#x4E3A; iOS /
          Android &#x65F6;&#xFF0C;&#x4E3A; app &#x5305;&#x540D;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;growingio.com</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">conversionVariable</th>
      <th style="text-align:left">map&lt;string,string&gt;</th>
      <th style="text-align:left">
        <p>&lt;&#x8F6C;&#x5316;&#x53D8;&#x91CF;&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;{&quot;keyword&quot;,&quot;retention&quot;}</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="vstr（访问用户变量）" %}
| 名称 | 类型 | 说明 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">visitUserId</th>
      <th style="text-align:left">string(64)</th>
      <th style="text-align:left">
        <p>&lt;&#x8BBF;&#x95EE;&#x7528;&#x6237;ID&gt;</p>
        <p>&#x8BBF;&#x95EE;&#x7528;&#x6237;&#x7684;&#x552F;&#x4E00;&#x6807;&#x8BC6;&#xFF0C;&#x7531;GrowingIo&#x81EA;&#x52A8;&#x751F;&#x6210;&#x3002;
          &#x793A;&#x4F8B;&#xFF1A;fc55728b-41ab-42ff-8b1f-714e44c65fd6</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">sessionId</th>
      <th style="text-align:left">string(50)</th>
      <th style="text-align:left">
        <p>&lt;&#x8BBF;&#x95EE;ID&gt;</p>
        <p>&#x5F53;&#x524D;&#x8BBF;&#x95EE;&#x7684;&#x552F;&#x4E00;&#x6807;&#x8BC6;&#x3002;
          &#x793A;&#x4F8B;&#xFF1A;6b5099c7-6006-422d-92ac-4f3bf4ddd37c</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">time</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&lt;&#x65F6;&#x95F4;&#x6233;&gt;</p>
        <p>&#x8BF7;&#x6C42;&#x53D1;&#x751F;&#x7684;&#x65F6;&#x95F4;&#x6233;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1520899220665</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">sendTime</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&lt;&#x53D1;&#x9001;&#x65F6;&#x95F4;&gt;</p>
        <p>&#x8BF7;&#x6C42;&#x5728;SDK&#x53D1;&#x9001;&#x7684;&#x65F6;&#x95F4;&#x6233;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1520899221211</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

| visitorVariable | map&lt;string,string&gt; | &lt;访问用户变量&gt; |
| :--- | :--- | :--- |
{% endtab %}
{% endtabs %}

