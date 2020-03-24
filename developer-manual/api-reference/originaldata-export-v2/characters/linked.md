# 事件表关联

**无埋点数据**

无埋点三张数据表分别代表GIO定义的三种数据级别：

* visit为访问级别的数据，按照session定义访问
* page为表页面级别数据，打开的浏览页面就是一条记录，一条访问级别数据对应多条页面级别
* action级别数据代表标签数据，定义页面元素标签的点击、修改、提交等事件

三者形成整个用户行为数据层级。

**广告监测数据**

ads\_track\_click和ads\_track\_activation两张表分别代表GIO定义的2种数据级别，ads\_track\_click为广告点击数据（每条监测链接统计到的点击次数），ads\_track\_activation为广告激活数据（在通过监测链接下载App 后首次联网打开的设备数）

## **常用关联场景**

![](https://github.com/growingio/growingio-docs-v3/tree/d520f4a494f6c0635c83422f55c665597e79ee96/.gitbook/assets/yuan-shi-shu-ju-guan-lian-guan-xi-tu%20%284%29.png)

| 关联 | 关联场景 |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x65E0;&#x57CB;&#x70B9;-&#x65E0;&#x57CB;&#x70B9;</th>
      <th style="text-align:left">
        <ul>
          <li>3&#x5F20;&#x8868;&#x53EF;&#x4EE5;&#x6839;&#x636E;&#x901A;&#x7528;&#x5B57;&#x6BB5;visitUserId&#x548C;sessionId&#x5173;&#x8054;&#x67E5;&#x8BE2;&#x3002;</li>
          <li>visit&#x4E0E;page&#x57FA;&#x672C;&#x4FDD;&#x6301;&#x5BF9;&#x5E94;&#xFF0C;&#x82E5;&#x662F;&#x5728;&#x5C0F;&#x65F6;&#x7EA7;&#x522B;page&#x6570;&#x636E;&#x65E0;&#x6CD5;join&#x5230;&#x5BF9;&#x5E94;&#x7684;visit&#x8BB0;&#x5F55;&#xFF0C;visit&#x8BB0;&#x5F55;&#x53EF;&#x80FD;&#x5B58;&#x5728;&#x4E8E;&#x4E4B;&#x524D;&#x7684;&#x5C0F;&#x65F6;&#x5355;&#x4F4D;&#x4E2D;&#xFF0C;&#x53EF;&#x4F7F;&#x7528;&#x901A;&#x7528;&#x5B57;&#x6BB5;<b>vstRequestId</b>&#x8FDB;&#x884C;&#x5173;&#x8054;&#x3002;&#x6BCF;&#x4E2A;visit&#xFF08;&#x6BCF;&#x6B21;&#x8BBF;&#x95EE;&#xFF09;&#x90FD;&#x4F1A;&#x81F3;&#x5C11;&#x8BBF;&#x95EE;&#x4E86;&#x4E00;&#x4E2A;page&#xFF0C;&#x6240;&#x4EE5;visit&#x4E2D;&#x7684;vstRequestId&#x53EF;&#x4EE5;&#x5728;page&#x4E2D;&#x81F3;&#x5C11;&#x5B58;&#x5728;&#x4E00;&#x4E2A;&#x76F8;&#x5BF9;&#x5E94;&#x7684;vstRequestId&#x3002;</li>
          <li>action&#x4E0E;page&#x8868;&#xFF0C;&#x53EF;&#x6839;&#x636E;&#x901A;&#x7528;&#x5B57;&#x6BB5;<b>pageRequestId</b>&#x8FDB;&#x884C;&#x5173;&#x8054;&#xFF0C;&#x4F46;page&#x8868;&#x4E2D;&#x7684;pageRequestId&#xFF0C;&#x5E76;&#x4E0D;&#x662F;&#x4E00;&#x5B9A;&#x5B58;&#x5728;&#x4E8E;action&#x8868;&#x4E2D;&#xFF0C;&#x53EA;&#x6709;&#x5F53;&#x7528;&#x6237;&#x5B58;&#x5728;clck&#xFF0C;chng&#x7B49;&#x884C;&#x4E3A;&#x65F6;&#xFF0C;&#x624D;&#x80FD;&#x5728;action&#x4E2D;&#x5BF9;&#x5E94;&#x5B58;&#x5728;pageRequestId&#x3002;</li>
          <li>&#x5BF9;&#x5E94;&#x5355;&#x72EC;&#x7EDF;&#x8BA1;&#x8FD9;&#x4E09;&#x4E2A;&#x6570;&#x636E;&#x8868;&#x65F6;&#xFF0C;page&#x8868;&#x53EF;&#x4F7F;&#x7528;pageRequestId&#x6765;&#x7EDF;&#x8BA1;&#x9875;&#x9762;&#x6D4F;&#x89C8;&#xFF0C;visit&#x8868;&#x53EF;&#x4F7F;&#x7528;sessionID&#x6765;&#x7EDF;&#x8BA1;&#x8BBF;&#x95EE;&#x6570;&#x636E;&#xFF0C;action&#x8868;&#x4E2D;&#x53EF;&#x4F7F;&#x7528;actionRequestId&#x6765;&#x7EDF;&#x8BA1;&#x4E8B;&#x4EF6;&#x6570;&#x636E;&#x3002;</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">&#x65E0;&#x57CB;&#x70B9;-&#x57CB;&#x70B9;</th>
      <th style="text-align:left">
        <ul>
          <li>&#x5173;&#x8054;&#x5B57;&#x6BB5;&#xFF1A;visitUserId&#xFF0C;sessionId</li>
          <li>&#x5BF9;&#x4E8E;&#x65E0;&#x57CB;&#x70B9;&#x6570;&#x636E;&#xFF08;page&#xFF0C;visit&#xFF0C;action&#xFF09;&#x548C;&#x57CB;&#x70B9;&#x6570;&#x636E;&#xFF08;custom_event&#xFF0C;pvar&#xFF0C;evar&#xFF0C;vstr&#xFF09;&#xFF0C;&#x90FD;&#x4F1A;&#x5B58;&#x5728;&#x8BBF;&#x95EE;&#x7528;&#x6237;ID&#x548C;&#x8BBF;&#x95EE;ID&#xFF0C;&#x53EF;&#x4F7F;&#x7528;&#x8FD9;&#x4E24;&#x4E2A;&#x5B57;&#x6BB5;&#x5173;&#x8054;&#x5404;&#x8868;&#x3002;</li>
          <li>page&#xFF0C;custom_event&#x548C;pvar&#x4E09;&#x5F20;&#x8868;&#xFF0C;&#x53EF;&#x4F7F;&#x7528;&#x5B57;&#x6BB5;pageRequestId&#x6765;
            join&#x67E5;&#x8BE2;&#xFF0C;&#x7EDF;&#x8BA1;&#x81EA;&#x5B9A;&#x4E49;&#x4E8B;&#x4EF6;&#x6240;&#x5728;&#x9875;&#x9762;&#x4EE5;&#x53CA;&#x5BF9;&#x5E94;&#x7684;&#x9875;&#x9762;&#x7EA7;&#x53D8;&#x91CF;&#x3002;</li>
          <li>evar&#x8868;&#x53EF;&#x4F7F;&#x7528;visitUserId&#xFF0C;sessionId&#x5206;&#x522B;&#x4E0E;page&#x8868;&#x548C;visit&#x8868;
            join&#x5173;&#x8054;&#x3002;</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5E7F;&#x544A;&#x76D1;&#x6D4B;-&#x5E7F;&#x544A;&#x76D1;&#x6D4B;</th>
      <th
      style="text-align:left">
        <ul>
          <li>&#x7528;&#x6237;&#x7528;&#x6237;&#x552F;&#x4E00;&#x8BBE;&#x5907;&#x53F7;&#xFF0C;&#x5BF9;&#x4E8E;&#x5B89;&#x5353;&#x5E94;&#x7528;&#xFF0C;GIO
            &#x4F18;&#x5148;&#x4F7F;&#x7528; IMEI &#x53F7;&#x8FDB;&#x884C;&#x7CBE;&#x51C6;&#x6FC0;&#x6D3B;&#x5339;&#x914D;&#xFF0C;&#x6CA1;&#x6709;
            IMEI &#x7684;&#x60C5;&#x51B5;&#x4E0B;&#x91C7;&#x7528; AndroidID &#x5339;&#x914D;&#xFF0C;&#x5982;&#x679C;&#x4E5F;&#x6CA1;&#x6709;&#x83B7;&#x53D6;&#x5230;
            AndroidID &#xFF0C;&#x5219;&#x91C7;&#x7528; IP+UA &#x7684;&#x65B9;&#x5F0F;&#x6A21;&#x7CCA;&#x5339;&#x914D;&#x3002;
            &#x5BF9;&#x4E8E; iOS &#x5E94;&#x7528;&#xFF0C;GIO &#x4F18;&#x5148;&#x4F7F;&#x7528;
            IDFA &#x8FDB;&#x884C;&#x7CBE;&#x51C6;&#x6FC0;&#x6D3B;&#x5339;&#x914D;&#xFF0C;&#x6CA1;&#x6709;
            IDFA &#x5219;&#x4F7F;&#x7528; IP+UA &#x7684;&#x65B9;&#x5F0F;&#x6A21;&#x7CCA;&#x5339;&#x914D;&#x3002;</li>
          <li>&#x4E24;&#x5F20;&#x6570;&#x636E;&#x8868;&#x53EF;&#x4EE5;&#x6839;&#x636E;&#x201C;&#x5916;&#x952E;&#x201D;join&#xFF0C;&#x53EF;&#x4F18;&#x5148;&#x4F7F;&#x7528;&#x8BBE;&#x5907;ID&#x8FDB;&#x884C;&#x5173;&#x8054;&#xFF08;IDFA/
            IMEI/ AndroidID &#xFF09;&#xFF0C;&#x5982;&#x8BBE;&#x5907;ID&#x4E3A;&#x7A7A;&#xFF0C;&#x5219;&#x53EF;&#x4F7F;&#x7528;&#x5B57;&#x6BB5;IP+&#x5B57;&#x6BB5;userAgent&#x8FDB;&#x884C;&#x5173;&#x8054;&#x67E5;&#x8BE2;&#x3002;</li>
          <li>&#x5982;&#x8981;&#x6839;&#x636E;&#x539F;&#x59CB;&#x6570;&#x636E;&#x7EDF;&#x8BA1;&#x6BCF;&#x6761;&#x76D1;&#x6D4B;&#x94FE;&#x63A5;&#x7684;&#x70B9;&#x51FB;&#x6570;&#x636E;&#x548C;&#x6FC0;&#x6D3B;&#x6570;&#x636E;&#xFF0C;&#x53EF;&#x4F7F;&#x7528;click&#x8868;&#x548C;activation&#x4E2D;&#x7684;&#x901A;&#x7528;&#x5B57;&#x6BB5;linkId
            &#x8FDB;&#x884C;&#x5173;&#x8054;&#x3002;</li>
          <li>&#x5982;&#x8981;&#x6839;&#x636E;&#x539F;&#x59CB;&#x6570;&#x636E;&#x7EDF;&#x8BA1;&#x5404;&#x76EE;&#x6807;&#x6E20;&#x9053;&#x7684;&#x70B9;&#x51FB;&#x6570;&#x636E;&#x548C;&#x6FC0;&#x6D3B;&#x6570;&#x636E;&#xFF0C;&#x53EF;&#x4F7F;&#x7528;click&#x8868;&#x548C;activation&#x4E2D;&#x7684;&#x901A;&#x7528;&#x5B57;&#x6BB5;channelId
            &#x8FDB;&#x884C;&#x5173;&#x8054;&#x3002;</li>
        </ul>
        </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5E7F;&#x544A;&#x76D1;&#x6D4B;-&#x65E0;&#x57CB;&#x70B9;</th>
      <th style="text-align:left">
        <p>&#x79FB;&#x52A8;&#x7AEF;&#x76D1;&#x6D4B;&#x6570;&#x636E;</p>
        <p>ads_track_activation&#x548C;visit&#x4E24;&#x8868;&#x5173;&#x8054;&#x5B57;&#x6BB5;&#xFF1A;visitUserId</p>
        <ul>
          <li>activation&#x8868;&#x4E2D;&#x6FC0;&#x6D3B;&#x6570;&#x636E;&#x4E3A;&#xFF0C;&#x901A;&#x8FC7;&#x76D1;&#x6D4B;&#x94FE;&#x63A5;&#x4E0B;&#x8F7D;app&#x540E;&#xFF0C;&#x9996;&#x6B21;&#x8054;&#x7F51;&#x6253;&#x5F00;&#xFF08;app&#x5DF2;&#x52A0;&#x8F7D;&#x4E86;gio
            Android/iOS sdk&#xFF09;</li>
          <li>&#x53EF;&#x4F7F;&#x7528;activation&#x8868;&#x4E2D;&#x5B57;&#x6BB5;visitUserId&#x4E0E;visit&#x8868;visitUserId&#x5173;&#x8054;&#x67E5;&#x8BE2;&#x3002;</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>{% tabs %}
{% tab title="时间字段" %}
所有原始数据导出接口中的时间字段，一般情况会包含下面两类：

| 类型 | 字段 | 说明 |
| :--- | :--- | :--- |
| 事件时间 | time | 取自客户端的系统时间，time字段中出现过去或者未来的时间，很大的可能是用户的系统时间是错的。 对于移动端来说，如果App异常退出，或者突然关闭网络，会导致数据晚发。 |
| 发送时间 | sendTime | 取自GIO接收到数据的时间，GIO所有小时、天数据全部使用此字段进行统计。 |
{% endtab %}

{% tab title="用户字段" %}
所有原始数据导出接口中会包含三类用户标识，用于您将GIO数据与您自有数据进行关联：

| 标识 | 说明 |
| :--- | :--- |


| 访问用户ID | 参考：[访问用户](../../../../introduction/datamodel/usermodel/visituser.md) |
| :--- | :--- |


| 登录用户ID | 参考：[登录用户](../../../../introduction/datamodel/usermodel/loginuser.md) |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5176;&#x4ED6;&#x8EAB;&#x4EFD;&#x6807;&#x8BC6;</th>
      <th style="text-align:left">
        <p>GrowingIO&#x5728;&#x5BFC;&#x51FA;&#x7684;&#x8BBF;&#x95EE;&#x4E8B;&#x4EF6;&#x4E2D;&#x5305;&#x542B;&#x4E86;&#x79FB;&#x52A8;&#x7AEF;&#x7528;&#x4E8E;&#x6807;&#x793A;&#x7528;&#x6237;&#x8EAB;&#x4EFD;&#x5E38;&#x7528;&#x7684;&#x4E09;&#x4E2A;&#x5B57;&#x6BB5;&#xFF1A;IDFA&#x3001;AndroidID&#x3001;IMEI</p>
        <p>&#x53C2;&#x8003;&#xFF1A;<a href="anto-character.md">&#x65E0;&#x57CB;&#x70B9;&#x4E8B;&#x4EF6;&#x5B57;&#x6BB5;</a>
        </p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}
{% endtabs %}

