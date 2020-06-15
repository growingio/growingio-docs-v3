# 访问事件及变量

## 访问事件的定义

在 GrowingIO 的数据模型中，访问事件代表：

* Web端：用户在一定时间内首次打开网站页面
* 移动端：用户在一定时间内首次打开移动应用
* 小程序：用户在微信中打开小程序

一次访问会生成一个 session 值，各平台的 session 刷新时间如下：

* Web端：用户无操作30分钟后 session 值过期，30 分钟后的操作生成新的 session 值。
* 移动端：App退出30秒后再进入，刷新session值。
* 小程序：小程序关闭5分钟后再进入，刷新session值。

## 访问事件的变量

GrowingIO 从 SDK 生成和发送的访问事件中提取了很多信息，我们将之称为访问事件的变量，这些信息包括：

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x4FE1;&#x606F;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x7528;&#x6237;&#x8BBE;&#x5907;&#x4FE1;&#x606F;</td>
      <td style="text-align:left">
        <ul>
          <li>&#x64CD;&#x4F5C;&#x7CFB;&#x7EDF;&#x53CA;&#x7248;&#x672C;</li>
          <li>&#x8BBE;&#x5907;&#x54C1;&#x724C;</li>
          <li>&#x8BBE;&#x5907;&#x578B;&#x53F7;</li>
          <li>&#x8BBE;&#x5907;&#x7C7B;&#x578B;&#xFF08;&#x624B;&#x673A;/&#x5E73;&#x677F;&#xFF09;</li>
          <li>&#x8BBE;&#x5907;&#x5236;&#x9020;&#x5546;</li>
          <li>&#x6D4F;&#x89C8;&#x5668;&#x53CA;&#x7248;&#x672C;</li>
          <li>&#x7CFB;&#x7EDF;&#x8BED;&#x8A00;</li>
          <li>&#x5C4F;&#x5E55;&#x5927;&#x5C0F;</li>
          <li>&#x8BBE;&#x5907;&#x65B9;&#x5411;</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x7528;&#x6237;&#x4F4D;&#x7F6E;&#x4FE1;&#x606F;</td>
      <td style="text-align:left">
        <ul>
          <li>&#x56FD;&#x5BB6;&#x3001;&#x5730;&#x533A;&#x3001;&#x57CE;&#x5E02;&#x540D;&#x79F0;</li>
          <li>&#x56FD;&#x5BB6;&#x4EE3;&#x7801;</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x7528;&#x6237;&#x8BBF;&#x95EE;&#x7684;&#x5E94;&#x7528;&#x4FE1;&#x606F;</td>
      <td
      style="text-align:left">
        <ul>
          <li>&#x7F51;&#x7AD9;/&#x624B;&#x673A;&#x5E94;&#x7528;</li>
          <li>App&#x7248;&#x672C;</li>
        </ul>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x7528;&#x6237;&#x843D;&#x5730;&#x9875;&#x4FE1;&#x606F;</td>
      <td style="text-align:left">
        <ul>
          <li>&#x57DF;&#x540D;</li>
          <li>&#x9875;&#x9762;</li>
          <li>&#x8BBF;&#x95EE;&#x6765;&#x6E90;</li>
          <li>&#x9875;&#x9762;&#x6765;&#x6E90;</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

