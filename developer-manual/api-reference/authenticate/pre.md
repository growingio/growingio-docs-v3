---
description: 介绍在进行认证及后续接口使用中需要提前准备的参数。
---

# 准备条件

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x51C6;&#x5907;&#x9879;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x9879;&#x76EE;&#x516C;&#x94A5;&#xFF08;X-Client-Id&#xFF09;</td>
      <td style="text-align:left">
        <p>GrowingIO&#x5206;&#x914D;&#x7684;&#x9879;&#x76EE;&#x516C;&#x94A5;&#xFF0C;&#x8BF7;&#x6C42;&#x65F6;&#x7528;&#x6765;&#x505A;&#x8EAB;&#x4EFD;&#x6821;&#x9A8C;&#x7684;&#x4E00;&#x4E32;&#x5B57;&#x7B26;&#x7801;&#x3002;&#x662F;&#x6240;&#x6709;&#x63A5;&#x53E3;&#x7684;&#x516C;&#x5171;&#x8BF7;&#x6C42;&#x5934;&#x53C2;&#x6570;&#x3002;</p>
        <p>&#x83B7;&#x53D6;&#x65B9;&#x5F0F;&#xFF1A;&#x767B;&#x5F55; GrowingIO &#x5E73;&#x53F0;&#xFF0C;&#x9009;&#x62E9;&#x5BF9;&#x5E94;&#x7684;&#x9879;&#x76EE;&#x540E;&#xFF0C;&#x5355;&#x51FB;&#x754C;&#x9762;&#x53F3;&#x4E0A;&#x89D2;
          <img
          src="../../../.gitbook/assets/2019-10-10_18-59-32 (1).png" alt/>&#x9009;&#x62E9;&#x3010;&#x9879;&#x76EE;&#x6982;&#x89C8;&#x3011;&#xFF0C;&#x5728;&#x9879;&#x76EE;&#x6982;&#x89C8;&#x9875;&#x9762;&#x7684;&#x57FA;&#x672C;&#x4FE1;&#x606F;&#x4E2D;&#x53EF;&#x4EE5;&#x67E5;&#x770B;&#x5F53;&#x524D;&#x9879;&#x76EE;&#x7684;&#x9879;&#x76EE;ID&#x3001;&#x9879;&#x76EE;&#x516C;&#x94A5;&#x3001;&#x9879;&#x76EE;&#x79C1;&#x94A5;&#x3002;
          &#x9879;&#x76EE; ID &#x4E5F;&#x662F;&#x96C6;&#x6210; SDK &#x65F6; setAccountId
          &#x6240;&#x7528;&#x7684;&#x90E8;&#x5206;&#x3002;&#x8BE6;&#x7EC6;&#x8BF7;&#x53C2;&#x8003;
          <a
          href="../../../product-manual/sysmanage/projectmange/details.md">&#x9879;&#x76EE;&#x6982;&#x89C8;</a>&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x9879;&#x76EE;&#x79C1;&#x94A5;</td>
      <td style="text-align:left">
        <p>GrowingIO&#x5206;&#x914D;&#x7684;&#x9879;&#x76EE;&#x79C1;&#x94A5;&#xFF0C;&#x751F;&#x6210;&#x52A0;&#x5BC6;&#x7B7E;&#x540D;&#x65F6;&#x4F7F;&#x7528;&#x3002;</p>
        <p>&#x83B7;&#x53D6;&#x65B9;&#x5F0F;&#xFF1A;&#x540C;&#x4E0A;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x9879;&#x76EE;ID&#xFF08;ai&#xFF09;</td>
      <td style="text-align:left">
        <p>GrowingIO&#x5206;&#x914D;&#x7684;&#x9879;&#x76EE;ID&#x3002;</p>
        <p>&#x83B7;&#x53D6;&#x65B9;&#x5F0F;&#xFF1A;&#x540C;&#x4E0A;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">project_uid</td>
      <td style="text-align:left">
        <p>&#x9879;&#x76EE;UID&#x3002;</p>
        <p>&#x767B;&#x5F55;GrowingIO&#x5E73;&#x53F0;&#xFF0C;&#x9009;&#x62E9;&#x5BF9;&#x5E94;&#x7684;&#x9879;&#x76EE;&#x540E;&#xFF0C;&#x9875;&#x9762;
          URL&#x4E2D;projects&#x540E;&#x7684;&#x503C;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;</p>
        <p>&#x9009;&#x62E9;&#x9879;&#x76EE;&#x540E;&#x9875;&#x9762;URL&#x4E3A;<code>https://www.growingio.com/admin/projects/nxog09md/dashboard</code>&#x5F53;&#x524D;&#x9879;&#x76EE;&#x7684;UID&#x4E3A;<code>nxog09md</code>&#x3002;&#x8BE6;&#x7EC6;&#x8BF7;&#x53C2;&#x8003;
          <a
          href="../../../product-manual/sysmanage/projectmange/get-uid.md">&#x83B7;&#x53D6;&#x9879;&#x76EE;UID</a>&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">tm</td>
      <td style="text-align:left">&#x5F53;&#x524D;&#x8BF7;&#x6C42;&#x7684;&#x65F6;&#x95F4;&#x6233;&#x3002;</td>
    </tr>
  </tbody>
</table>![&#x63A5;&#x53E3;&#x4F7F;&#x7528;&#x6D41;&#x7A0B;](../../../.gitbook/assets/jie-kou-shi-yong-liu-cheng.png)

为保证数据安全，GrowingIO所有的API服务，请求Head中需要携带认证码。



