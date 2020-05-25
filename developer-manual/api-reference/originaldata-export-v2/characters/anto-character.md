---
description: 无埋点事件字段共分为4个事件类型。
---

# 无埋点事件字段

{% tabs %}
{% tab title="visit（访问事件）" %}
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
</table><table>
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
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">accountVersion</th>
      <th style="text-align:left">string&#xFF08;20&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;SDK&#x7248;&#x672C;&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;2.3.0</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">platform</th>
      <th style="text-align:left">string&#xFF08;64&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x5E73;&#x53F0;&gt;</p>
        <p>&#x8BBF;&#x95EE;&#x6240;&#x5C5E;&#x5E73;&#x53F0;&#xFF0C;&#x53EF;&#x80FD;&#x503C;&#x4E3A;
          iOS / Android / Web &#x7B49;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;Web</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
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
</table><table>
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
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">queryParameters</th>
      <th style="text-align:left">string&#xFF08;1024&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x67E5;&#x8BE2;&#x53C2;&#x6570;&gt;</p>
        <p>&#x5F53;&#x524D;&#x7F51;&#x7AD9;&#x9875;&#x9762;URL&#x4E2D;&#x7684;&#x67E5;&#x8BE2;&#x53C2;&#x6570;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;cid=1234567</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">referrer</th>
      <th style="text-align:left">string&#xFF08;1024&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x9875;&#x9762;&#x6765;&#x6E90;&gt;</p>
        <p>&#x5F53;&#x524D;&#x9875;&#x9762;&#x6D4F;&#x89C8;&#x7684;&#x5F15;&#x8350;&#x6765;&#x6E90;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;https://www.growingio.com?cid=1234567</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">language</th>
      <th style="text-align:left">string&#xFF08;10&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x8BED;&#x8A00;&gt;</p>
        <p>&#x7CFB;&#x7EDF;&#x4F7F;&#x7528;&#x7684;&#x8BED;&#x8A00;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;zh-cn</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">screenHeight</th>
      <th style="text-align:left">string&#xFF08;10&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x5C4F;&#x5E55;&#x9AD8;&#x5EA6;&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1242</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">screenWidth</th>
      <th style="text-align:left">string&#xFF08;10&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x5C4F;&#x5E55;&#x5BBD;&#x5EA6;&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;2016</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">time</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&lt;&#x65F6;&#x95F4;&#x6233;&gt;</p>
        <p>&#x8BF7;&#x6C42;&#x5728;&#x7528;&#x6237;&#x7AEF;&#x53D1;&#x751F;&#x7684;&#x65F6;&#x95F4;&#x6233;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1520899220665</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
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
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">ip</th>
      <th style="text-align:left">string&#xFF08;15&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;IP&#x5730;&#x5740;&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;127.0.0.1</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">userAgent</th>
      <th style="text-align:left">string&#xFF08;512&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x7528;&#x6237;&#x4EE3;&#x7406;&gt;</p>
        <p>&#x7B80;&#x79F0; UA&#xFF0C;&#x5B83;&#x662F;&#x4E00;&#x4E2A;&#x7279;&#x6B8A;&#x5B57;&#x7B26;&#x4E32;&#x5934;&#xFF0C;&#x4F7F;&#x5F97;&#x670D;&#x52A1;&#x5668;&#x80FD;&#x591F;&#x8BC6;&#x522B;&#x5BA2;&#x6237;&#x4F7F;&#x7528;&#x7684;&#x64CD;&#x4F5C;&#x7CFB;&#x7EDF;&#x53CA;&#x7248;&#x672C;&#x3001;CPU
          &#x7C7B;&#x578B;&#x3001;&#x6D4F;&#x89C8;&#x5668;&#x53CA;&#x7248;&#x672C;&#x3001;&#x6D4F;&#x89C8;&#x5668;&#x6E32;&#x67D3;&#x5F15;&#x64CE;&#x3001;&#x6D4F;&#x89C8;&#x5668;&#x8BED;&#x8A00;&#x3001;&#x6D4F;&#x89C8;&#x5668;&#x63D2;&#x4EF6;&#x7B49;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;Mozilla/5.0 (iPhone; CPU iPhone OS 11_2_6 like
          Mac OS X) AppleWebKit/604.5.6 (KHTML, like Gecko) Mobile/15D100</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">operatingSystem</th>
      <th style="text-align:left">string&#xFF08;30&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x64CD;&#x4F5C;&#x7CFB;&#x7EDF;&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;iOS/Android</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">operatingSystemVersion</th>
      <th style="text-align:left">string&#xFF08;50&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x64CD;&#x4F5C;&#x7CFB;&#x7EDF;&#x7248;&#x672C;&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;iOS 11.0.1 /Android 6.0.1</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">clientVersion</th>
      <th style="text-align:left">string&#xFF08;50&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x5BA2;&#x6237;&#x7684;&#x4EA7;&#x54C1;&#x7248;&#x672C;&gt;</p>
        <p>&#x4EC5;&#x9650;&#x79FB;&#x52A8;&#x7AEF;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1.0</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">channel</th>
      <th style="text-align:left">string&#xFF08;40&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;App&#x7684;&#x4E0B;&#x8F7D;&#x6E20;&#x9053;&gt;</p>
        <p>&#x4EC5;&#x9650;&#x79FB;&#x52A8;&#x7AEF;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;App tore</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">deviceBrand</th>
      <th style="text-align:left">string&#xFF08;20&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x8BBE;&#x5907;&#x54C1;&#x724C;&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;google</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">deviceModel</th>
      <th style="text-align:left">string&#xFF08;50&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x8BBE;&#x5907;&#x578B;&#x53F7;&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;Nexus 5</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">deviceType</th>
      <th style="text-align:left">string&#xFF08;50&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x8BBE;&#x5907;&#x7C7B;&#x578B;&gt;</p>
        <p>&#x8BBE;&#x5907;&#x7C7B;&#x578B;&#xFF1A;</p>
        <ul>
          <li>0&#xFF1A;&#x5E73;&#x677F;</li>
          <li>1&#xFF1A;&#x624B;&#x673A;</li>
        </ul>
        <p>&#x793A;&#x4F8B;&#xFF1A;1</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">deviceOrientation</th>
      <th style="text-align:left">string&#xFF08;10&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x8BBE;&#x5907;&#x65B9;&#x5411;&gt;</p>
        <p>&#x8BF7;&#x6C42;&#x4EA7;&#x751F;&#x65F6;&#x8BBE;&#x5907;&#x65B9;&#x5411;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;PORTRAIT</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">latitude</th>
      <th style="text-align:left">double</th>
      <th style="text-align:left">
        <p>&lt;&#x5730;&#x7406;&#x4F4D;&#x7F6E;&#x7EAC;&#x5EA6;&gt;</p>
        <p>&#x7CBE;&#x786E;&#x5230;&#x5C0F;&#x6570;&#x70B9;&#x540E;5&#x4F4D;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;29.43982</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">longitude</th>
      <th style="text-align:left">double</th>
      <th style="text-align:left">
        <p>&lt;&#x5730;&#x7406;&#x4F4D;&#x7F6E;&#x7CBE;&#x5EA6;&gt;</p>
        <p>&#x7CBE;&#x786E;&#x5230;&#x5C0F;&#x6570;&#x70B9;&#x540E;5&#x4F4D;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;29.43982</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">vstRequestId</th>
      <th style="text-align:left">string&#xFF08;16&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x8BBF;&#x95EE;&#x8BF7;&#x6C42;&#x5185;&#x90E8;ID&gt;</p>
        <p>GrowingIO&#x7CFB;&#x7EDF;&#x5185;&#x90E8;&#x7528;&#x4E8E;&#x6807;&#x8BC6;&#x4E00;&#x4E2A;&#x8BBF;&#x95EE;&#x8BF7;&#x6C42;&#x7684;ID&#xFF0C;&#x53EF;&#x4EE5;&#x7528;&#x6765;&#x5173;&#x8054;&#x8BBF;&#x95EE;&#x6570;&#x636E;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;c7db72a5841506bd</p>
        <p>&#x82E5;&#x662F;&#x5728;&#x5C0F;&#x65F6;&#x7EA7;&#x522B;page&#x6570;&#x636E;&#x65E0;&#x6CD5;join&#x5230;&#x5BF9;&#x5E94;&#x7684;visit&#x8BB0;&#x5F55;&#xFF0C;visit&#x8BB0;&#x5F55;&#x53EF;&#x80FD;&#x5B58;&#x5728;&#x4E8E;&#x4E4B;&#x524D;&#x7684;&#x5C0F;&#x65F6;&#x5355;&#x4F4D;&#x4E2D;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">idfa</th>
      <th style="text-align:left">string&#xFF08;40&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;iOS&#x72EC;&#x6709;&#x7684;&#x5E7F;&#x544A;&#x6807;&#x8BC6;&#x7B26;&gt;</p>
        <p>&#x82F9;&#x679C;&#x7CFB;&#x7EDF;&#x7528;&#x4E8E;&#x76D1;&#x6D4B;&#x5E7F;&#x544A;&#x7684;ID&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;A075A0F9-32D2-4671-A78D-144B6B7D2920</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">androidId</th>
      <th style="text-align:left">string&#xFF08;16&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x5B89;&#x5353;&#x7CFB;&#x7EDF;&#x7684;&#x4E00;&#x4E2A;ID&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;6284760c2926bcd5</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">IMEI</th>
      <th style="text-align:left">string&#xFF08;16&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x56FD;&#x9645;&#x79FB;&#x52A8;&#x8BBE;&#x5907;&#x8BC6;&#x522B;&#x7801;&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;867459000000000</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="page（页面事件）" %}
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
</table><table>
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
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">platform</th>
      <th style="text-align:left">string&#xFF08;20&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x5E73;&#x53F0;&gt;</p>
        <p>&#x8BBF;&#x95EE;&#x6240;&#x5C5E;&#x5E73;&#x53F0;&#xFF0C;&#x53EF;&#x80FD;&#x503C;&#x4E3A;
          iOS / Android / Web &#x7B49;&#x3002; &#x793A;&#x4F8B;&#xFF1A;Web</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
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
</table><table>
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
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">queryParameters</th>
      <th style="text-align:left">string&#xFF08;1024&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x67E5;&#x8BE2;&#x53C2;&#x6570;&gt;</p>
        <p>&#x5F53;&#x524D;&#x7F51;&#x7AD9;&#x9875;&#x9762;URL&#x4E2D;&#x7684;&#x67E5;&#x8BE2;&#x53C2;&#x6570;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;cid=1234567</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">referrer</th>
      <th style="text-align:left">string&#xFF08;1024&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x9875;&#x9762;&#x6765;&#x6E90;&gt;</p>
        <p>&#x5F53;&#x524D;&#x9875;&#x9762;&#x6D4F;&#x89C8;&#x7684;&#x5F15;&#x8350;&#x6765;&#x6E90;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x200B;http://www.growingio.com?cid=1234567</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">referrerPage</th>
      <th style="text-align:left">string&#xFF08;1024&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x9875;&#x9762;&#x6765;&#x6E90;&#x9875;&#x9762;&gt;</p>
        <p>&#x79FB;&#x52A8;&#x5E94;&#x7528;&#x7684;&#x6765;&#x6E90;&#x9875;&#x9762;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;myViewController</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">title</th>
      <th style="text-align:left">string&#xFF08;1024&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x9875;&#x9762;Title&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;GrowingIO</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">time</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&lt;&#x65F6;&#x95F4;&#x6233;&gt;</p>
        <p>&#x8BF7;&#x6C42;&#x5728;&#x7528;&#x6237;&#x7AEF;&#x53D1;&#x751F;&#x7684;&#x65F6;&#x95F4;&#x6233;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1520899220665</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
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
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">deviceOrientation</th>
      <th style="text-align:left">string(10)</th>
      <th style="text-align:left">
        <p>&lt;&#x8BBE;&#x5907;&#x65B9;&#x5411;&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;PORTRAIT</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">loginUserId</th>
      <th style="text-align:left">string&#xFF08;200&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x767B;&#x5F55;&#x7528;&#x6237;ID&gt;</p>
        <p>&#x767B;&#x5F55;&#x7528;&#x6237;ID&#xFF0C;&#x63A8;&#x8350;&#x4F7F;&#x7528;&#x90A3;&#x4E9B;&#x4E0D;&#x80FD;&#x5B9A;&#x4F4D;&#x5230;&#x4E2A;&#x4EBA;&#x7684;ID&#x4FE1;&#x606F;&#xFF0C;&#x901A;&#x5E38;&#x4E3A;&#x4F01;&#x4E1A;&#x5185;&#x90E8;&#x4F7F;&#x7528;&#x7684;CRM
          ID&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;user12345&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">pageGroup</th>
      <th style="text-align:left">string&#xFF08;200&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x9875;&#x9762;&#x7EC4;&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;myPG</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">appVariable</th>
      <th style="text-align:left">map&lt;string,string&gt;</th>
      <th style="text-align:left">
        <p>&lt;&#x5E94;&#x7528;&#x7EA7;&#x53D8;&#x91CF;&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;{&quot;version&quot;:&quot;1.1&quot;}&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| customerAttributes2 | string（200） | 用户属性2 |
| :--- | :--- | :--- |


| customerAttributes3 | string（200） | 用户属性3 |
| :--- | :--- | :--- |


| customerAttributes4 | string（200） | 用户属性4 |
| :--- | :--- | :--- |


| customerAttributes5 | string（200） | 用户属性5 |
| :--- | :--- | :--- |


| customerAttributes6 | string（200） | 用户属性6 |
| :--- | :--- | :--- |


| customerAttributes7 | string（200） | 用户属性7 |
| :--- | :--- | :--- |


| customerAttributes8 | string（200） | 用户属性8 |
| :--- | :--- | :--- |


| customerAttributes9 | string（200） | 用户属性9 |
| :--- | :--- | :--- |


| customerAttributes10 | string（200） | 用户属性10 |
| :--- | :--- | :--- |


| pageAttributes1 | string（200） | 页面属性1 |
| :--- | :--- | :--- |


| pageAttributes2 | string（200） | 页面属性2 |
| :--- | :--- | :--- |


| pageAttributes3 | string（200） | 页面属性3 |
| :--- | :--- | :--- |


| pageAttributes4 | string（200） | 页面属性4 |
| :--- | :--- | :--- |


| pageAttributes5 | string（200） | 页面属性5 |
| :--- | :--- | :--- |


| pageAttributes6 | string（200） | 页面属性6 |
| :--- | :--- | :--- |


| pageAttributes7 | string（200） | 页面属性7 |
| :--- | :--- | :--- |


| pageAttributes8 | string（200） | 页面属性8 |
| :--- | :--- | :--- |


| pageAttributes9 | string（200） | 页面属性9 |
| :--- | :--- | :--- |


| pageAttributes10 | string（200） | 页面属性10 |
| :--- | :--- | :--- |


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
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">vstRequestId</th>
      <th style="text-align:left">string&#xFF08;16&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x8BBF;&#x95EE;&#x8BF7;&#x6C42;&#x5185;&#x90E8;ID&gt;</p>
        <p>GrowingIO&#x7CFB;&#x7EDF;&#x5185;&#x90E8;&#x7528;&#x4E8E;&#x6807;&#x8BC6;&#x4E00;&#x4E2A;&#x8BBF;&#x95EE;&#x8BF7;&#x6C42;&#x7684;ID&#xFF0C;&#x53EF;&#x4EE5;&#x7528;&#x6765;&#x5173;&#x8054;&#x8BBF;&#x95EE;&#x6570;&#x636E;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;c7db72a5841506bd</p>
        <p>&#x82E5;&#x662F;&#x5728;&#x5C0F;&#x65F6;&#x7EA7;&#x522B;page&#x6570;&#x636E;&#x65E0;&#x6CD5;join&#x5230;&#x5BF9;&#x5E94;&#x7684;visit&#x8BB0;&#x5F55;&#xFF0C;visit&#x8BB0;&#x5F55;&#x53EF;&#x80FD;&#x5B58;&#x5728;&#x4E8E;&#x4E4B;&#x524D;&#x7684;&#x5C0F;&#x65F6;&#x5355;&#x4F4D;&#x4E2D;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="action（动作事件）" %}
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
</table><table>
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
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">requestType</th>
      <th style="text-align:left">string&#xFF08;10&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x8BF7;&#x6C42;&#x7C7B;&#x578B;&gt;</p>
        <p>&#x6839;&#x636E;&#x8BF7;&#x6C42;&#x7684;&#x7C7B;&#x578B;&#x4E0D;&#x540C;&#xFF0C;&#x53EF;&#x80FD;&#x503C;&#x4E3A;&#xFF1A;clck(click),
          chng(change)&#xFF0C;sbmt(submit)</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;clck</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
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
</table><table>
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
</table><table>
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
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">time</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&lt;&#x65F6;&#x95F4;&#x6233;&gt;</p>
        <p>&#x8BF7;&#x6C42;&#x5728;&#x7528;&#x6237;&#x7AEF;&#x53D1;&#x751F;&#x7684;&#x65F6;&#x95F4;&#x6233;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1520899220665</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">href</th>
      <th style="text-align:left">string&#xFF08;1024&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x6807;&#x7B7E;&#x5185;&#x7684;&#x8DF3;&#x8F6C;&#x8FDE;&#x63A5;&gt;</p>
        <p>&#x6CA1;&#x6709;&#x5219;&#x4E3A;null&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;help.growingio.com</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">requestValue</th>
      <th style="text-align:left">string&#xFF08;1024&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x8BF7;&#x6C42;&#x503C;&gt;</p>
        <p>&#x8BE5;&#x6D88;&#x606F;&#x7684;&#x503C;&#xFF0C;&#x4F8B;&#x5982;&#x6807;&#x7B7E;&#x7684;value&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x201C;&#x786E;&#x5B9A;&#x201D;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">index</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&lt;&#x6807;&#x7B7E;&#x5E8F;&#x53F7;&gt;</p>
        <p>&#x5217;&#x8868;&#x7C7B;&#x578B;&#x6807;&#x7B7E;&#x7684;&#x5E8F;&#x53F7;&#xFF0C;&#x7528;&#x4E8E;&#x6807;&#x8BB0;&#x5217;&#x8868;&#x5185;&#x7684;&#x7B2C;&#x51E0;&#x9879;&#xFF0C;&#x5206;&#x6790;&#x5217;&#x8868;&#x4E2D;&#x6700;&#x5E38;&#x88AB;&#x70B9;&#x51FB;&#x7684;&#x5185;&#x5BB9;&#x6216;&#x8005;&#x9996;&#x9879;&#x63A8;&#x5E7F;&#x6548;&#x679C;&#x7B49;&#x7B49;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">info</th>
      <th style="text-align:left">string&#xFF08;200&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x7528;&#x6237;&#x81EA;&#x5B9A;&#x4E49;&#x4FE1;&#x606F;&gt;</p>
        <p>&#x5BF9;&#x5E94;growingAttributesInfo&#x8BBE;&#x7F6E;&#x7684;&#x5B57;&#x6BB5;&#x4FE1;&#x606F;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
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
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">actionRequestId</th>
      <th style="text-align:left">string&#xFF08;30&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;Action&#x8BF7;&#x6C42;&#x5185;&#x90E8;ID&gt;</p>
        <p>&#x7528;&#x4E8E;&#x6807;&#x8BC6;&#x4E00;&#x4E2A;action&#x8BF7;&#x6C42;&#x7684;ID&#x3002;</p>
        <ul>
          <li>Web&#x4EE5;wa&#x5F00;&#x5934;</li>
          <li>&#x79FB;&#x52A8;&#x7AEF;&#x4EE5;ma&#x5F00;&#x5934;</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="action\_tag（元素圈选动作事件）" %}
| 名称 | 类型（长度） | 说明 |
| :--- | :--- | :--- |


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
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">actionRequestId</th>
      <th style="text-align:left">string&#xFF08;30&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;Action&#x8BF7;&#x6C42;&#x5185;&#x90E8;ID&gt;</p>
        <p>&#x7528;&#x4E8E;&#x6807;&#x8BC6;&#x4E00;&#x4E2A;action&#x8BF7;&#x6C42;&#x7684;ID&#x3002;</p>
        <ul>
          <li>web&#x7684;&#x4EE5;wa&#x5F00;&#x5934;</li>
          <li>mobile&#x7684;&#x4EE5;ma&#x5F00;&#x5934;</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">ruleId</th>
      <th style="text-align:left">string&#xFF08;8&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;Rule&#x5185;&#x90E8;ID&gt;</p>
        <p>&#x7528;&#x4E8E;&#x6807;&#x8BC6;<b>&#x5143;&#x7D20;&#x5708;&#x9009;</b>&#x65E0;&#x57CB;&#x70B9;&#x4E8B;&#x4EF6;&#x7684;&#x552F;&#x4E00;ID&#xFF0C;&#x7531;&#x5B57;&#x6BCD;&#x548C;&#x6570;&#x5B57;&#x7EC4;&#x6210;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;99ae0dec</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>{% hint style="info" %}
您可以通过[获取圈选元素定义](../../statistics-api/definition/get-auto.md)接口得到以下rules（圈选元素定义）字段表。
{% endhint %}

| 名称 | 类型 | 说明 |
| :--- | :--- | :--- |
| rule\_id | string\(8\) | 规则ID，匹配事件的规则ID，该ID为GrowingIO平台圈选的标签的唯一ID。该值有字母与数字组成，例如'1ba052a9'。 |
| name | string\(200） | 规则名称，圈选的标签名称。该名称不可以作为唯一主键，只是便于使用区分。 |
| ruleType | string\(10\) | 规则类型，规则在定义时可能有不同的类型，例如按钮clck。值包括page、clck、chng、sbmt。 |

1. 在基础部分数据导出（visit, page, action\)之外，提供圈选数据与action级别数据的映射部分。
2. 通过action数据中的action\_id与action\_tag中的action\_id聚合，绑定对应的rule\_id（映射的规则名称）到action数据上。
3. rules代表了客户在GrowingIO平台上圈选的标签，rule\_id即其唯一标识符。
4. 通过rules表将名称绑定到上述的action\_tag表中，便于通过名称进行数据分析，识别导出数据中圈选部分的数据情况。
5. action\_tag与rules表均是关联信息表，用于更进一步分析导出的部分数据，在导出数据中定位圈选数据。建议规则建立时保持名称的唯一性，GrowingIO平台不保证规则名称唯一性。
6. 相同的规则名称下可能有多个规则类型，规则名称＋规则类型才能区分，此处的规则类型与基础数据action中的事件类型保持一致。
{% endtab %}
{% endtabs %}

