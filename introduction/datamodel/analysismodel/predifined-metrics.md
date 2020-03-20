# 预定义指标



{% tabs %}
{% tab title="用户级指标" %}
用户级指标：项目级别的用户总量统计。

| 指标 | 说明 |
| :--- | :--- |
| 访问用户量（web/app/小程序） | （接入 GrowingIO 后）访问用户的数量。 |
| 新访问用户量（web/app/小程序） | （接入 GrowingIO 后）365 天内第一次访问网站/小程序；打开App的访问用户数量。 |
| 登录用户量（web/App/小程序） | （接入 GrowingIO 后）登录用户的数量，需要上传登录用户 ID 。 |
| 新登录用户量（web/App/小程序） | （接入 GrowingIO 后）第一次登录网站的用户数量。 |

{% hint style="info" %}
访问用户的技术说明

Web：根据cookie

App：根据用户唯一ID区分访问用户

* Android用户唯一ID：Android ID或IMEI
* iOS用户唯一ID：IDFV或IDFA

小程序：默认按照cookie判断访问用户；如果不取关小程序，则cookie不会发生变化；当设置forceLogin后，则会默认按照openid来判断访问用户，且不采用365天的限制。
{% endhint %}
{% endtab %}

{% tab title="访问级指标" %}
访问级指标：衡量网站总体访问情况

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x6307;&#x6807;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x8BBF;&#x95EE;&#x91CF;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">&#x8BBF;&#x95EE;&#x7684;&#x6570;&#x91CF;&#x3002;&#x88AB;&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&#x5206;&#x89E3;&#x65F6;&#xFF0C;&#x4EE3;&#x8868;&#x7740;&#x5305;&#x542B;&#x8BE5;&#x9875;&#x9762;&#x7684;&#x8BBF;&#x95EE;&#x7684;&#x6B21;&#x6570;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x6BCF;&#x6B21;&#x8BBF;&#x95EE;&#x9875;&#x9762;&#x6D4F;&#x89C8;&#x91CF;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">
        <p>&#x5E73;&#x5747;&#x6BCF;&#x6B21;&#x8BBF;&#x95EE;&#x6D4F;&#x89C8;&#x7684;&#x9875;&#x9762;&#x7684;&#x6570;&#x91CF;&#x3002;</p>
        <p>&#x8BA1;&#x7B97;&#x65B9;&#x6CD5;&#xFF1A;&#x9875;&#x9762;&#x6D4F;&#x89C8;&#x91CF;/&#x8BBF;&#x95EE;&#x91CF;</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x4EBA;&#x5747;&#x8BBF;&#x95EE;&#x9875;&#x6570;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">
        <p>&#x5E73;&#x5747;&#x6BCF;&#x4E2A;&#x7528;&#x6237;&#x5B9E;&#x9645;&#x6D4F;&#x89C8;&#x8FC7;&#x7684;&#x7F51;&#x9875;&#x6570;&#x3002;</p>
        <p>&#x8BA1;&#x7B97;&#x65B9;&#x6CD5;&#xFF1A;&#x9875;&#x9762;&#x6D4F;&#x89C8;&#x91CF;/&#x7528;&#x6237;&#x91CF;</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x4EBA;&#x5747;&#x8BBF;&#x95EE;&#x6B21;&#x6570;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">
        <p>&#x5E73;&#x5747;&#x6BCF;&#x4E2A;&#x7528;&#x6237;&#x8BBF;&#x95EE;&#x7F51;&#x7AD9;&#xFF08;&#x6253;&#x5F00;App&#xFF09;&#x7684;&#x6B21;&#x6570;&#x3002;</p>
        <p>&#x8BA1;&#x7B97;&#x65B9;&#x6CD5;&#xFF1A;&#x8BBF;&#x95EE;&#x91CF;/&#x7528;&#x6237;&#x91CF;</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x603B;&#x8BBF;&#x95EE;&#x65F6;&#x957F;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">&#x6240;&#x6709;&#x8BBF;&#x95EE;&#x7684;&#x603B;&#x65F6;&#x957F;&#xFF0C;&#x4EE5;&#x5206;&#x949F;&#x4F5C;&#x4E3A;&#x5355;&#x4F4D;&#x5C55;&#x793A;&#xFF0C;&#x4E0D;&#x7EDF;&#x8BA1;&#x65F6;&#x95F4;&#x8DE8;&#x5EA6;&#x5C0F;&#x4E8E;1&#x79D2;&#x6216;&#x5927;&#x4E8E;1&#x5929;&#x7684;&#x8BBF;&#x95EE;&#x3002;&#x4E0D;&#x80FD;&#x4F7F;&#x7528;&#x9875;&#x9762;&#x7EA7;&#x7EF4;&#x5EA6;&#xFF08;&#x57DF;&#x540D;&#x3001;&#x9875;&#x9762;&#x3001;&#x81EA;&#x5B9A;&#x4E49;&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&#xFF09;&#x5206;&#x89E3;&#x3002;&#x7531;&#x4E8E;Web&#x7AEF;&#x65E0;&#x6CD5;&#x51C6;&#x786E;&#x83B7;&#x53D6;&#x5230;&#x7528;&#x6237;&#x7684;&#x79BB;&#x5F00;&#x65F6;&#x95F4;&#xFF0C;&#x6240;&#x4EE5;&#x6700;&#x540E;&#x4E00;&#x4E2A;&#x9875;&#x9762;&#x7684;&#x8BBF;&#x95EE;&#x65F6;&#x957F;&#x4E0D;&#x4F1A;&#x5305;&#x542B;&#x5728;&#x603B;&#x8BBF;&#x95EE;&#x65F6;&#x957F;&#x4E2D;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x5E73;&#x5747;&#x8BBF;&#x95EE;&#x65F6;&#x957F;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">
        <p>&#x5E73;&#x5747;&#x6BCF;&#x6B21;&#x8BBF;&#x95EE;&#x65F6;&#x957F;&#xFF0C;&#x4EE5;&#x5206;&#x949F;&#x4F5C;&#x4E3A;&#x5355;&#x4F4D;&#x5C55;&#x793A;&#x3002;&#x4E0D;&#x80FD;&#x4F7F;&#x7528;&#x9875;&#x9762;&#x7EA7;&#x7EF4;&#x5EA6;&#xFF08;&#x57DF;&#x540D;&#x3001;&#x9875;&#x9762;&#x3001;&#x81EA;&#x5B9A;&#x4E49;&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&#xFF09;&#x5206;&#x89E3;&#x3002;</p>
        <p>&#x8BA1;&#x7B97;&#x65B9;&#x6CD5;&#xFF1A;&#x603B;&#x8BBF;&#x95EE;&#x65F6;&#x957F;/&#x8BBF;&#x95EE;&#x91CF;</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x4EBA;&#x5747;&#x8BBF;&#x95EE;&#x65F6;&#x957F;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">
        <p>&#x5E73;&#x5747;&#x6BCF;&#x4E2A;&#x7528;&#x6237;&#x7684;&#x8BBF;&#x95EE;&#x65F6;&#x957F;&#x3002;</p>
        <p>&#x8BA1;&#x7B97;&#x65B9;&#x6CD5;&#xFF1A;&#x603B;&#x8BBF;&#x95EE;&#x65F6;&#x957F;/&#x7528;&#x6237;&#x91CF;</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x9000;&#x51FA;&#x6B21;&#x6570;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">&#x7528;&#x6237;&#x9000;&#x51FA;&#x7F51;&#x7AD9;&#x7684;&#x6570;&#x91CF;&#xFF0C;&#x901A;&#x5E38;&#x9700;&#x8981;&#x5728;&#x4E00;&#x5B9A;&#x8303;&#x56F4;&#x5185;&#xFF0C;&#x56E0;&#x4E3A;&#x6240;&#x6709;&#x7684;&#x7528;&#x6237;&#x6700;&#x7EC8;&#x90FD;&#x4F1A;&#x9000;&#x51FA;&#x7F51;&#x7AD9;&#x3002;
        &#x4E0E;&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&#x4E00;&#x8D77;&#x4F7F;&#x7528;&#x65F6;&#xFF0C;&#x7EDF;&#x8BA1;&#x7684;&#x662F;&#x8BE5;&#x9875;&#x9762;&#x4F5C;&#x4E3A;&#x7528;&#x6237;&#x4E00;&#x6B21;&#x8BBF;&#x95EE;&#x4E2D;&#x7684;&#x6700;&#x540E;&#x4E00;&#x4E2A;&#x9875;&#x9762;&#x7684;&#x8BBF;&#x95EE;&#x7684;&#x6B21;&#x6570;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x9000;&#x51FA;&#x7387;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">
        <p>&#x5982;&#x679C;&#x4E0E;&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&#x4E00;&#x8D77;&#x4F7F;&#x7528;&#xFF0C;&#x7EDF;&#x8BA1;&#x7684;&#x662F;&#x8BE5;&#x9875;&#x9762;&#x4F5C;&#x4E3A;&#x9000;&#x51FA;&#x9875;&#x7684;&#x6B21;&#x6570;&#xFF0C;&#x5360;&#x8FD9;&#x4E2A;&#x9875;&#x9762;&#x88AB;&#x8BBF;&#x95EE;&#x7684;&#x603B;&#x4F53;&#x6570;&#x91CF;&#x7684;&#x6BD4;&#x4F8B;&#x3002;
          &#x6BCF;&#x4E2A;&#x9875;&#x9762;&#x90FD;&#x6709;&#x53EF;&#x80FD;&#x6210;&#x4E3A;&#x9000;&#x51FA;&#x9875;&#xFF0C;&#x56E0;&#x4E3A;&#x7528;&#x6237;&#x603B;&#x8981;&#x79BB;&#x5F00;&#x7F51;&#x7AD9;&#xFF0C;&#x4F46;&#x662F;&#x5982;&#x679C;&#x5173;&#x952E;&#x6D41;&#x7A0B;&#x4E2D;&#x7684;&#x9875;&#x9762;&#x9000;&#x51FA;&#x7387;&#x9AD8;&#xFF0C;&#x5C31;&#x8BF4;&#x660E;&#x9875;&#x9762;&#x51FA;&#x73B0;&#x4E86;&#x95EE;&#x9898;&#xFF0C;&#x7528;&#x6237;&#x672C;&#x5E94;&#x8BE5;&#x7EE7;&#x7EED;&#x5B8C;&#x6210;&#x64CD;&#x4F5C;&#xFF0C;&#x4F46;&#x662F;&#x4E2D;&#x9014;&#x9000;&#x51FA;&#x4E86;&#x3002;
          *&#x9000;&#x51FA;&#x9875;&#xFF1A;&#x7528;&#x6237;&#x5728;&#x4E00;&#x6B21;&#x8BBF;&#x95EE;&#x4E2D;&#x8BBF;&#x95EE;&#x7684;&#x6700;&#x540E;&#x4E00;&#x4E2A;&#x9875;&#x9762;&#xFF0C;&#x662F;&#x8FD9;&#x6B21;&#x8BBF;&#x95EE;&#x7684;&#x9000;&#x51FA;&#x9875;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&#x7528;&#x6237;&#x7684;&#x8FD9;&#x6B21;&#x8BBF;&#x95EE;&#x662F;&#x5728;&#x8FD9;&#x91CC;&#x7ED3;&#x675F;&#x7684;&#x3002;</p>
        <p>&#x8BA1;&#x7B97;&#x65B9;&#x6CD5;&#xFF1A;&#x9000;&#x51FA;&#x6B21;&#x6570;/&#x8BBF;&#x95EE;&#x91CF;</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x603B;&#x9875;&#x9762;&#x505C;&#x7559;&#x65F6;&#x957F;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">&#x603B;&#x9875;&#x9762;&#x505C;&#x7559;&#x65F6;&#x957F;&#xFF08;&#x5206;&#x949F;&#xFF09;&#x6307;&#x6807;&#x53EA;&#x80FD;&#x88AB;&#x9875;&#x9762;&#x7EA7;&#x7EF4;&#x5EA6;&#xFF08;&#x57DF;&#x540D;&#x3001;&#x9875;&#x9762;&#x3001;&#x81EA;&#x5B9A;&#x4E49;&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&#xFF09;&#x5206;&#x89E3;&#xFF0C;&#x4EE3;&#x8868;&#x7740;&#x7528;&#x6237;&#x5728;&#x5F53;&#x524D;&#x9875;&#x9762;&#x4E0A;&#x505C;&#x7559;&#x7684;&#x603B;&#x65F6;&#x957F;&#xFF0C;&#x4E0D;&#x7EDF;&#x8BA1;&#x505C;&#x7559;&#x65F6;&#x957F;&#x5927;&#x4E8E;3&#x4E2A;&#x5C0F;&#x65F6;&#x7684;&#x9875;&#x9762;&#x3002;&#x7531;&#x4E8E;Web&#x7AEF;&#x65E0;&#x6CD5;&#x51C6;&#x786E;&#x83B7;&#x53D6;&#x5230;&#x7528;&#x6237;&#x7684;&#x79BB;&#x5F00;&#x65F6;&#x95F4;&#xFF0C;&#x6240;&#x4EE5;&#x6700;&#x540E;&#x4E00;&#x4E2A;&#x9875;&#x9762;&#x7684;&#x505C;&#x7559;&#x65F6;&#x957F;&#x4E0D;&#x4F1A;&#x5305;&#x542B;&#x5728;&#x603B;&#x9875;&#x9762;&#x505C;&#x7559;&#x65F6;&#x957F;&#x4E2D;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x5E73;&#x5747;&#x9875;&#x9762;&#x505C;&#x7559;&#x65F6;&#x957F;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">
        <p>&#x5E73;&#x5747;&#x9875;&#x9762;&#x505C;&#x7559;&#x65F6;&#x957F;&#xFF08;&#x5206;&#x949F;&#xFF09;&#x6307;&#x6807;&#x53EA;&#x80FD;&#x88AB;&#x9875;&#x9762;&#x7EA7;&#x7EF4;&#x5EA6;&#xFF08;&#x57DF;&#x540D;&#x3001;&#x9875;&#x9762;&#x3001;&#x81EA;&#x5B9A;&#x4E49;&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&#xFF09;&#x5206;&#x89E3;&#xFF0C;&#x4EE3;&#x8868;&#x7740;&#x7528;&#x6237;&#x5728;&#x5F53;&#x524D;&#x9875;&#x9762;&#x4E0A;&#x505C;&#x7559;&#x7684;&#x5E73;&#x5747;&#x65F6;&#x957F;&#x3002;</p>
        <p>&#x8BA1;&#x7B97;&#x65B9;&#x6CD5;&#xFF1A;&#x603B;&#x9875;&#x9762;&#x505C;&#x7559;&#x65F6;&#x957F;/&#xFF08;&#x9875;&#x9762;&#x6D4F;&#x89C8;&#x91CF;-&#x9000;&#x51FA;&#x6B21;&#x6570;&#xFF09;</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x8FDB;&#x5165;&#x91CF;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">
        <p>&#x8BBF;&#x95EE;&#x7528;&#x6237;&#x8FDB;&#x5165;&#x7F51;&#x7AD9;&#xFF08;&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;&#x8FDB;&#x884C;&#x8BBF;&#x95EE;&#x7684;&#x6570;&#x91CF;&#x3002;</p>
        <p>&#x8BF4;&#x660E;&#xFF1A;&#x5F53;&#x8FDB;&#x5165;&#x6B21;&#x6570;&#x6307;&#x6807;&#x88AB;&#x9875;&#x9762;&#x7EF4;&#x5EA6;&#x62C6;&#x5206;&#x65F6;&#xFF0C;&#x8FDB;&#x5165;&#x6B21;&#x6570;&#x6307;&#x4ECE;&#x8BE5;&#x9875;&#x9762;&#x7EA7;&#x7EF4;&#x5EA6;&#x7684;&#x5F53;&#x524D;&#x503C;&#xFF08;&#x9875;&#x9762;&#xFF09;&#x8FDB;&#x5165;&#xFF08;&#x5F00;&#x59CB;&#xFF09;&#x7684;&#x8BBF;&#x95EE;&#x7684;&#x6570;&#x91CF;&#x3002;&#x5728;&#x4F5C;&#x4E3A;&#x6307;&#x6807;&#x5355;&#x72EC;&#x4F7F;&#x7528;&#x6216;&#x8005;&#x88AB;&#x9664;&#x9875;&#x9762;&#x7EA7;&#x7EF4;&#x5EA6;&#x4EE5;&#x5916;&#x7684;&#x7EF4;&#x5EA6;&#x62C6;&#x5206;&#x65F6;&#xFF0C;&#x8FDB;&#x5165;&#x6B21;&#x6570;&#x5728;&#x6570;&#x503C;&#x4E0A;&#x7B49;&#x4E8E;&#x8BBF;&#x95EE;&#x91CF;&#x3002;</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x8BBF;&#x95EE;&#x7528;&#x6237;&#x4EBA;&#x5747;&#x8FDB;&#x5165;&#x6B21;&#x6570;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">
        <p>&#x5E73;&#x5747;&#x6BCF;&#x4E2A;&#x8BBF;&#x95EE;&#x7528;&#x6237;&#x8FDB;&#x5165;&#x7F51;&#x7AD9;/&#x5C0F;&#x7A0B;&#x5E8F;&#x8FDB;&#x884C;&#x8BBF;&#x95EE;&#x7684;&#x6570;&#x91CF;&#x3002;</p>
        <p>&#x8BA1;&#x7B97;&#x65B9;&#x6CD5;&#xFF1A;&#x8FDB;&#x5165;&#x91CF;/&#x8BBF;&#x95EE;&#x7528;&#x6237;&#x91CF;</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x603B;&#x8FDB;&#x5165;&#x65F6;&#x957F;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">&#x7528;&#x6237;&#x8FDB;&#x5165;&#x7F51;&#x7AD9;/&#x5C0F;&#x7A0B;&#x5E8F;&#x8FDB;&#x884C;&#x8BBF;&#x95EE;&#x7684;&#x603B;&#x65F6;&#x957F;&#xFF0C;&#x4EE5;&#x5206;&#x949F;&#x4F5C;&#x4E3A;&#x5355;&#x4F4D;&#x5C55;&#x793A;&#x3002;
        &#x4E0E;&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&#x4E00;&#x8D77;&#x4F7F;&#x7528;&#x65F6;&#xFF0C;&#x7EDF;&#x8BA1;&#x7684;&#x662F;&#x8BE5;&#x9875;&#x9762;&#x4F5C;&#x4E3A;&#x7528;&#x6237;&#x4E00;&#x6B21;&#x8BBF;&#x95EE;&#x4E2D;&#x7684;&#x7B2C;&#x4E00;&#x4E2A;&#x9875;&#x9762;&#x7684;&#x8BBF;&#x95EE;&#x7684;&#x65F6;&#x957F;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x5E73;&#x5747;&#x8FDB;&#x5165;&#x65F6;&#x957F;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">&#x7528;&#x6237;&#x5E73;&#x5747;&#x6BCF;&#x6B21;&#x8FDB;&#x5165;&#x7F51;&#x7AD9;/&#x5C0F;&#x7A0B;&#x5E8F;&#x8FDB;&#x884C;&#x8BBF;&#x95EE;&#x7684;&#x5E73;&#x5747;&#x65F6;&#x957F;&#xFF0C;&#x4EE5;&#x5206;&#x949F;&#x4F5C;&#x4E3A;&#x5355;&#x4F4D;&#x5C55;&#x793A;&#x3002;&#x8BA1;&#x7B97;&#x65B9;&#x6CD5;&#xFF1A;&#x603B;&#x8FDB;&#x5165;&#x65F6;&#x957F;/&#x8FDB;&#x5165;&#x91CF;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x6BCF;&#x6B21;&#x8FDB;&#x5165;&#x9875;&#x9762;&#x6D4F;&#x89C8;&#x91CF;&#xFF08;Web/App/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">&#x5E73;&#x5747;&#x6BCF;&#x6B21;&#x8FDB;&#x5165;&#x5E26;&#x6765;&#x7684;&#x9875;&#x9762;&#x6D4F;&#x89C8;&#x7684;&#x6570;&#x91CF;&#x3002;&#x8BA1;&#x7B97;&#x65B9;&#x6CD5;&#xFF1A;&#x8FDB;&#x5165;&#x603B;&#x9875;&#x9762;&#x6D4F;&#x89C8;&#x91CF;/&#x8FDB;&#x5165;&#x91CF;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x8DF3;&#x51FA;&#x6B21;&#x6570;&#xFF08;Web/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">&#x8BBF;&#x95EE;&#x4E00;&#x4E2A;&#x9875;&#x9762;&#x5C31;&#x79BB;&#x5F00;&#x7684;&#x6B21;&#x6570;&#xFF0C;&#x5373;&#x4E00;&#x6B21;&#x8BBF;&#x95EE;&#x4E2D;&#x53EA;&#x8BBF;&#x95EE;&#x4E86;&#x4E00;&#x4E2A;&#x9875;&#x9762;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x8DF3;&#x51FA;&#x7387;&#xFF08;Web/&#x5C0F;&#x7A0B;&#x5E8F;&#xFF09;</td>
      <td
      style="text-align:left">
        <p>&#x53EA;&#x6709;&#x4E00;&#x4E2A;&#x9875;&#x9762;&#x6D4F;&#x89C8;&#x7684;&#x8BBF;&#x95EE;&#x5360;&#x6240;&#x6709;&#x8BBF;&#x95EE;&#x7684;&#x6BD4;&#x7387;&#x3002;</p>
        <p>&#x8BA1;&#x7B97;&#x65B9;&#x6CD5;&#xFF1A;&#x8DF3;&#x51FA;&#x6B21;&#x6570;/&#x8FDB;&#x5165;&#x91CF;</p>
        <p>&#x9AD8;&#x8DF3;&#x51FA;&#x7387;&#x8868;&#x793A;&#x8BBF;&#x95EE;&#x8005;&#x5BF9;&#x5230;&#x8FBE;&#x7AD9;&#x5185;&#x65F6;&#x8BBF;&#x95EE;&#x7684;&#x7B2C;&#x4E00;&#x4E2A;&#x9875;&#x9762;&#x4E0D;&#x611F;&#x5174;&#x8DA3;&#xFF0C;&#x6CA1;&#x6709;&#x7EE7;&#x7EED;&#x8BBF;&#x95EE;&#x66F4;&#x6DF1;&#x5165;&#x7684;&#x9875;&#x9762;&#xFF0C;&#x6216;&#x8005;&#x662F;&#x767B;&#x5F55;&#x9875;&#x9762;&#x8BBE;&#x8BA1;&#x7684;&#x4E0D;&#x5408;&#x7406;&#x5BFC;&#x81F4;&#x7528;&#x6237;&#x53EA;&#x8BBF;&#x95EE;&#x4E00;&#x4E2A;&#x9875;&#x9762;&#x5C31;&#x79BB;&#x5F00;&#x3002;</p>
        </td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="页面级指标" %}
页面级指标：衡量页面的访问情况

| 指标 | 说明 |
| :--- | :--- |
| 页面浏览量（Web/App/小程序） | 用户实际浏览过的网页数量。 |
| 通过圈选定义的页面浏览量（Web/App/小程序） | 可以定义一个页面，也可以定义一组页面，统计定义页面的浏览量。 |
{% endtab %}

{% tab title="事件级指标" %}
事件级指标：可以通过圈选和创建自定义事件来实现。

| 指标 | 说明 |
| :--- | :--- |
| 通过圈选定义的元素指标化后（Web/App/小程序） | 通过圈选定义的元素，在使用的时候，会指标化为“该元素点击（浏览）的人数或次数” |
| 自定义事件（Web/App/小程序） | 通过打点实施创建自定义事件。 |
{% endtab %}
{% endtabs %}



