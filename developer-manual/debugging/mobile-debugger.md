---
description: 此功能可以方便查看移动端 SDK 上传的数据信息。
---

# Mobile Debugger

## 启动Mobile Debugger <a id="qi-dong-mobile-debugger"></a>

**第一步、进入Mobile Debugger启动页**

登录GrowingIO平台，在任意界面单机右上角 ![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/2019-10-10_18-59-32.png) 选择**Mobile Debugger**进入Mobile Debugger启动页。

![Mobile Debugger&#x542F;&#x52A8;&#x9875;](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28205%29.png)

第二步、扫码唤起App

1. 选择项目中需要进行测试的应用，并保证手机中已经安装该APP，且该APP已经集成GrowingIO 2.2.0及以上的SDK。
2. 使用手机浏览器扫描入口的二维码唤起Debug的APP，需要注意微信中扫码无法唤起APP。

## 使用 Mobile Debugger 测试数据 <a id="shi-yong-mobile-debugger-ce-shi-shu-ju"></a>

在唤起Debug的APP后，该APP采集的行为数据以及当前页面截图就会出现在网页上，测试同学可以根据数据看数据的采集以及发送情况，对数据进行测试。

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/image%20%28233%29.png)

在此概览中可能出现的数据日志含义分别有：

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x8BF7;&#x6C42;&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">page</td>
      <td style="text-align:left">&#x9875;&#x9762;&#x6D4F;&#x89C8;&#x6570;&#x636E;</td>
    </tr>
    <tr>
      <td style="text-align:left">vst</td>
      <td style="text-align:left">&#x7528;&#x6237;&#x8BBF;&#x95EE;&#x6570;&#x636E;</td>
    </tr>
    <tr>
      <td style="text-align:left">clck</td>
      <td style="text-align:left">&#x70B9;&#x51FB;&#x884C;&#x4E3A;&#x6570;&#x636E;</td>
    </tr>
    <tr>
      <td style="text-align:left">chng</td>
      <td style="text-align:left">&#x8F93;&#x5165;&#x6846;&#x884C;&#x4E3A;&#x6570;&#x636E;</td>
    </tr>
    <tr>
      <td style="text-align:left">cstm</td>
      <td style="text-align:left">&#x201C;&#x4E8B;&#x4EF6;&#x4EE5;&#x53CA;&#x5173;&#x8054;&#x7684;&#x4E8B;&#x4EF6;&#x7EA7;&#x53D8;&#x91CF;&#x201D;&#x6570;&#x636E;</td>
    </tr>
    <tr>
      <td style="text-align:left">pvar</td>
      <td style="text-align:left">&#x201C;&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&#x201D;&#x6570;&#x636E;</td>
    </tr>
    <tr>
      <td style="text-align:left">evar</td>
      <td style="text-align:left">&#x201C;&#x8F6C;&#x5316;&#x53D8;&#x91CF;&#x201D;&#x6570;&#x636E;</td>
    </tr>
    <tr>
      <td style="text-align:left">ppl</td>
      <td style="text-align:left">&#x201C;&#x7528;&#x6237;&#x53D8;&#x91CF;&#x201D;&#x6570;&#x636E;</td>
    </tr>
    <tr>
      <td style="text-align:left">imp</td>
      <td style="text-align:left">
        <p>&#x5143;&#x7D20;&#x6D4F;&#x89C8;&#x6570;&#x636E;</p>
        <p>&#x6570;&#x636E;&#x91CF;&#x7EA7;&#x8FC7;&#x5927;&#xFF0C;&#x5F71;&#x54CD;Mobile
          Debugger&#x6027;&#x80FD;&#xFF0C;Mobile Debugger&#x4E0D;&#x5C55;&#x793A;&#x8FD9;&#x90E8;&#x5206;&#x6570;&#x636E;</p>
      </td>
    </tr>
  </tbody>
</table>

