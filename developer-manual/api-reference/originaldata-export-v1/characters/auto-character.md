# 无埋点事件字段

## **无埋点事件**

{% tabs %}
{% tab title="visit" %}
| 名称 | 类型（长度） | 说明 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">userId</th>
      <th style="text-align:left">string&#xFF08;36&#xFF09;</th>
      <th style="text-align:left">
        <p>&#x7528;&#x6237;ID&#x3002;</p>
        <p>&#x6B63;&#x5BF9;&#x5355;&#x4E2A;&#x7528;&#x6237;&#x751F;&#x6210;&#x7684;&#x552F;&#x4E00;ID&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;Web&#x7F51;&#x7AD9;&#x751F;&#x6210;&#x4E00;&#x4E2A;&#x6709;&#x6548;&#x671F;3&#x5E74;&#x7684;cookie&#x503C;&#xFF0C;App&#x5219;&#x4E3A;&#x673A;&#x5668;&#x552F;&#x4E00;&#x6807;&#x8BC6;&#x7801;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">sessionId</th>
      <th style="text-align:left">string&#xFF08;36&#xFF09;</th>
      <th style="text-align:left">
        <p>&#x8BBF;&#x95EE;ID&#x3002;</p>
        <ul>
          <li>Web: 30&#x5206;&#x949F;&#x8FC7;&#x671F;&#x7684;session&#x503C;&#xFF0C;&#x4EE3;&#x8868;&#x4E00;&#x6B21;&#x8BBF;&#x95EE;&#x3002;</li>
          <li>&#x79FB;&#x52A8;&#x7AEF;: App&#x9000;&#x51FA;30&#x79D2;&#x540E;&#x518D;&#x8FDB;&#x5165;&#xFF0C;&#x5237;&#x65B0;session&#x503C;&#x3002;</li>
          <li>&#x5C0F;&#x7A0B;&#x5E8F;&#xFF1A;&#x5173;&#x95ED;5&#x5206;&#x949F;&#x518D;&#x8FDB;&#x5165;&#x5237;&#x65B0;session&#x503C;&#x3002;</li>
        </ul>
        <p>&#x793A;&#x4F8B;&#xFF1A;6b5099c7-6006-422d-92ac-4f3bf4ddd37c</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| sendTime | bigint | 发送时间。 |
| :--- | :--- | :--- |


| eventTime | bigint | 事件发生事件 |
| :--- | :--- | :--- |


| eventType | string（10） | 事件类型 |
| :--- | :--- | :--- |


| ip | string（64） |  |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">countryName</th>
      <th style="text-align:left">string&#xFF08;30&#xFF09;</th>
      <th style="text-align:left">
        <p>&#x56FD;&#x5BB6;&#x540D;&#x79F0;&#x3002;</p>
        <p>&#x7528;&#x6237;&#x6240;&#x5728;&#x7684;&#x56FD;&#x5BB6;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">region</th>
      <th style="text-align:left">string&#xFF08;30&#xFF09;</th>
      <th style="text-align:left">
        <p>&#x7701;&#x4EFD;&#x3002;</p>
        <p>&#x7528;&#x6237;&#x6240;&#x5728;&#x7684;&#x7701;&#x4EFD;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">city</th>
      <th style="text-align:left">string&#xFF08;30&#xFF09;</th>
      <th style="text-align:left">
        <p>&#x57CE;&#x5E02;&#x3002;</p>
        <p>&#x7528;&#x6237;&#x6240;&#x5728;&#x7684;&#x57CE;&#x5E02;&#x3002;</p>
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
        <p>&#x57DF;&#x540D;&#x3002;</p>
        <p>&#x7528;&#x6237;&#x8BBF;&#x95EE;&#x7684;&#x7F51;&#x7AD9;&#x57DF;&#x540D;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">path</th>
      <th style="text-align:left">string&#xFF08;512&#xFF09;</th>
      <th style="text-align:left">
        <p>&#x8DEF;&#x5F84;&#x3002;</p>
        <p>&#x7F51;&#x7AD9;&#x8DEF;&#x5F84;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| refer | string（1024） | 来源链接 |
| :--- | :--- | :--- |


| userAgent | string（1024） |  |
| :--- | :--- | :--- |


| appVersion | string（10） | 客户的产品版本，仅限App端。 |
| :--- | :--- | :--- |


| model | string（50） | 用户的设备型号 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">manufacturer</th>
      <th style="text-align:left">string&#xFF08;50&#xFF09;</th>
      <th style="text-align:left">
        <p>&#x7528;&#x6237;&#x7684;&#x8BBE;&#x5907;&#x751F;&#x4EA7;&#x4EA7;&#x5546;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x5C0F;&#x7C73;</p>
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
        <p>&#x4E0B;&#x8F7D;&#x6E20;&#x9053;&#x3002;</p>
        <p>App&#x7684;&#x4E0B;&#x8F7D;&#x6E20;&#x9053;&#xFF0C;&#x4EC5;&#x9650;&#x79FB;&#x52A8;&#x7AEF;&#x3002;</p>
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
        <p>&#x8BED;&#x8A00;&#x3002;</p>
        <p>&#x7528;&#x6237;&#x4F7F;&#x7528;&#x7684;&#x8BBE;&#x5907;&#x7CFB;&#x7EDF;&#x8BED;&#x8A00;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">osVersion</th>
      <th style="text-align:left">string&#xFF08;50&#xFF09;</th>
      <th style="text-align:left">
        <p>&#x7CFB;&#x7EDF;&#x7248;&#x672C;&#x3002;</p>
        <p>&#x7528;&#x6237;&#x4F7F;&#x7528;&#x7684;&#x8BBE;&#x5907;&#x7CFB;&#x7EDF;&#x7248;&#x672C;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">resolution</th>
      <th style="text-align:left">string&#xFF08;20&#xFF09;</th>
      <th style="text-align:left">
        <p>&#x8BBE;&#x5907;&#x5206;&#x8FA8;&#x7387;</p>
        <p>&#x7528;&#x6237;&#x4F7F;&#x7528;&#x7684;&#x8BBE;&#x5907;&#x5206;&#x8FA8;&#x7387;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">platform</th>
      <th style="text-align:left">string&#xFF08;10&#xFF09;</th>
      <th style="text-align:left">
        <p>&#x6570;&#x636E;&#x6765;&#x6E90;</p>
        <p>&#x5E73;&#x53F0;&#x533A;&#x5206;&#x8BE5;&#x6570;&#x636E;&#x5C5E;&#x4E8E;&#x54EA;&#x4E2A;&#x5E73;&#x53F0;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;Web Android iOS</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">id</th>
      <th style="text-align:left">string&#xFF08;16&#xFF09;</th>
      <th style="text-align:left">
        <p>&#x8BBF;&#x95EE;&#x4E8B;&#x4EF6;ID</p>
        <p>&#x5373;visit_id&#xFF0C;&#x7528;&#x4E8E;&#x4E0E;page&#x6570;&#x636E;&#x805A;&#x5408;&#xFF0C;&#x552F;&#x4E00;&#x6807;&#x8BB0;visit&#x4E8B;&#x4EF6;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">query</th>
      <th style="text-align:left">string&#xFF08;512&#xFF09;</th>
      <th style="text-align:left">
        <p>&#x8BBF;&#x95EE;&#x4E8B;&#x4EF6;&#x7684;query&#x4FE1;&#x606F;</p>
        <p>&#x8BBF;&#x95EE;&#x65F6;&#x7684;&#x8FDE;&#x63A5;&#x4E2D;&#x7684;query&#xFF0C;&#x4E0E;&#x6390;&#x5E74;&#x7684;domain&#xFF0C;path&#x4E00;&#x8D77;&#x6784;&#x5EFA;&#x5B8C;&#x6574;&#x7684;&#x94FE;&#x63A5;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">lat</th>
      <th style="text-align:left">double</th>
      <th style="text-align:left">
        <p>gps&#x7EAC;&#x5EA6;</p>
        <p>mobile&#x5E73;&#x53F0;&#xFF0C;&#x9700;&#x8981;gps&#x6743;&#x9650;&#x3002;&#xFF1F;&#xFF1F;&#xFF1F;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| lng | double | gps经度mobile平台独有的子弹，紧缺到小数点后5位。 |
| :--- | :--- | :--- |
{% endtab %}

{% tab title="page" %}
| 名称 | 类型（长度） | 说明 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">userId</th>
      <th style="text-align:left">string(36)</th>
      <th style="text-align:left">
        <p>&#x7528;&#x6237;ID</p>
        <p>&#x9488;&#x5BF9;&#x5355;&#x4E2A;&#x7528;&#x6237;&#x751F;&#x6210;&#x7684;&#x552F;&#x4E00;id</p>
        <p>&#x4F8B;&#x5982;&#xFF0C;web&#x7F51;&#x7AD9;&#x751F;&#x6210;&#x4E00;&#x4E2A;&#x6709;&#x6548;&#x671F;&#x4E09;&#x5E74;&#x7684;cookie&#x503C;&#xFF0C;App
          &#x5219;&#x4E3A;&#x673A;&#x5668;&#x552F;&#x4E00;&#x6807;&#x8BC6;&#x7801;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| sessionId | string\(36\) |  |
| :--- | :--- | :--- |


| sendTime | bigint | 数据发送过来的时间 |
| :--- | :--- | :--- |


| eventTime | bigint | 事件实际发生的时间 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">eventType</th>
      <th style="text-align:left">string(15)</th>
      <th style="text-align:left">
        <p>&#x8BE5;&#x6D88;&#x606F;&#x7684;&#x7C7B;&#x578B;</p>
        <p>page&#x8868;&#x5185;&#x7C7B;&#x578B;&#x4E3A;page</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| domain | string\(100\) | 用户访问的网站域名 |
| :--- | :--- | :--- |


| path | string\(512\) | 网站路径 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">query</th>
      <th style="text-align:left">string(512)</th>
      <th style="text-align:left">
        <p>request&#x8BF7;&#x6C42;&#x4E2D;&#x7684;&#x67E5;&#x8BE2;&#x53C2;&#x6570;</p>
        <p>k1=v1&amp;k2=v2</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| refer | string\(1024\) | 该用户从refer所在地址跳转过来 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">title</th>
      <th style="text-align:left">string(1024)</th>
      <th style="text-align:left">
        <p>&#x9875;&#x9762;&#x540D;&#x79F0;</p>
        <p>&#x8BE5;&#x7F51;&#x9875;&#x540D;&#x79F0;&#xFF0C;page title</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| platform | string\(10\) | 区分该数据属于哪个平台：web, android, ios |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">cs1</th>
      <th style="text-align:left">string(200)</th>
      <th style="text-align:left">
        <p>&#x7528;&#x6237;&#x4FE1;&#x606F;&#x5B57;&#x6BB5;1</p>
        <p>&#x5BA2;&#x6237;&#x5E73;&#x53F0;&#x7684;&#x767B;&#x9646;&#x7528;&#x6237;id&#xFF1A;cs1&#xFF0C;&#x5982;&#x679C;&#x5BA2;&#x6237;&#x5B89;&#x88C5;sdk&#x65F6;&#x8BBE;&#x7F6E;&#x8FC7;cs1&#x5B57;&#x6BB5;&#xFF08;&#x4E0A;&#x4F20;&#x7528;&#x6237;&#x5C5E;&#x6027;&#x5B57;&#x6BB5;&#x96C6;cs&#xFF0C;cs1&#x7528;&#x4E8E;&#x8BBE;&#x7F6E;&#x7528;&#x6237;id&#xFF09;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| cs2 | string\(200\) | 客户平台的项目id：cs2 |
| :--- | :--- | :--- |


| cs3 | string\(200\) | ​ |
| :--- | :--- | :--- |


| cs4 | string\(200\) | ​ |
| :--- | :--- | :--- |


| cs5 | string\(200\) | ​ |
| :--- | :--- | :--- |


| cs6 | string\(200\) | ​ |
| :--- | :--- | :--- |


| cs7 | string\(200\) | ​ |
| :--- | :--- | :--- |


| cs8 | string\(200\) | ​ |
| :--- | :--- | :--- |


| cs9 | string\(200\) | ​ |
| :--- | :--- | :--- |


| cs10 | string\(200\) | ​ |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">id</th>
      <th style="text-align:left">string(23)</th>
      <th style="text-align:left">
        <p>&#x9875;&#x9762;&#x4E8B;&#x4EF6;id</p>
        <p>&#x5373;page_id&#xFF0C;&#x7528;&#x4E8E;&#x4E0E;action&#x6570;&#x636E;&#x805A;&#x5408;</p>
        <p>&#x552F;&#x4E00;&#x6807;&#x8BB0;page&#x4E8B;&#x4EF6;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">visit_id</th>
      <th style="text-align:left">string(16)</th>
      <th style="text-align:left">
        <p>&#x8BBF;&#x95EE;&#x4E8B;&#x4EF6;ID</p>
        <p>&#x5373;visit_id&#xFF0C;&#x7528;&#x4E8E;&#x4E0E;visit&#x8868;&#x6570;&#x636E;&#x805A;&#x5408;</p>
        <p>&#x3002;visit&#x8868;&#x5185;id</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">pagegroup</th>
      <th style="text-align:left">string(100)</th>
      <th style="text-align:left">
        <p>&#x9875;&#x9762;&#x7EC4;&#x540D;&#x79F0;</p>
        <p>&#x9700;&#x8981;&#x5728;sdk&#x96C6;&#x6210;&#x65F6;&#x914D;&#x7F6E;</p>
        <p>&#x7528;&#x4E8E;&#x6807;&#x8BB0;&#x8BBE;&#x7F6E;&#x7684;&#x4E00;&#x7EC4;ps&#x5B57;&#x6BB5;&#x4FE1;&#x606F;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| ps1 | string\(200\) | sdk配置的页面信息字段1 |
| :--- | :--- | :--- |


| ps2 | string\(200\) | ​ |
| :--- | :--- | :--- |


| ps3 | string\(200\) | ​ |
| :--- | :--- | :--- |


| ps4 | string\(200\) | ​ |
| :--- | :--- | :--- |


| ps5 | string\(200\) | ​ |
| :--- | :--- | :--- |


| ps6 | string\(200\) | ​ |
| :--- | :--- | :--- |


| ps7 | string\(200\) | ​ |
| :--- | :--- | :--- |


| ps8 | string\(200\) | ​ |
| :--- | :--- | :--- |


| ps9 | string\(200\) | ​ |
| :--- | :--- | :--- |


| ps10 | string\(200\) | ​ |
| :--- | :--- | :--- |
{% endtab %}

{% tab title="action" %}
| 列名 | 字段名称 | 字段格式 | 字段说明 |
| :--- | :--- | :--- | :--- |


| userId | 用户ID | string\(36\) | ​ |
| :--- | :--- | :--- | :--- |


| sessionId | 会话ID | string\(36\) | "web: 30分钟过期的session值，代表一次会话,。mobile: app退出30秒后再进入，刷新session值" |
| :--- | :--- | :--- | :--- |


| sendTime | 发送时间 | bigint | 数据发送过来的时间 |
| :--- | :--- | :--- | :--- |


| eventTime | 事件发生时间 | bigint | 事件实际发生的时间 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">eventType</th>
      <th style="text-align:left">&#x4E8B;&#x4EF6;&#x7C7B;&#x578B;</th>
      <th style="text-align:left">string(10)</th>
      <th style="text-align:left">
        <p>&#x8BE5;&#x6D88;&#x606F;&#x7684;&#x7C7B;&#x578B;</p>
        <p>&#x53EF;&#x80FD;&#x503C;&#x4E3A;clck(click), chng(change)&#xFF0C;sbmt(submit)&#x4EE5;&#x53CA;imp(impression)&#xFF0C;change&#x7684;&#x542B;&#x4E49;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">eventValue</th>
      <th style="text-align:left">&#x4E8B;&#x4EF6;&#x503C;</th>
      <th style="text-align:left">string(1024)</th>
      <th style="text-align:left">
        <p>&#x8BE5;&#x6D88;&#x606F;&#x7684;&#x503C;&#xFF0C;&#x4F8B;&#x5982;&#x6807;&#x7B7E;&#x7684;value</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x786E;&#x5B9A;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">domain</th>
      <th style="text-align:left">&#x57DF;&#x540D;</th>
      <th style="text-align:left">string(100)</th>
      <th style="text-align:left">
        <p>&#x57DF;&#x540D;</p>
        <p>&#x7528;&#x6237;&#x8BBF;&#x95EE;&#x7684;&#x7F51;&#x7AD9;&#x57DF;&#x540D;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">path</th>
      <th style="text-align:left">&#x8DEF;&#x5F84;</th>
      <th style="text-align:left">string(512)</th>
      <th style="text-align:left">
        <p>&#x8DEF;&#x5F84;&#xFF1A;</p>
        <p>&#x7F51;&#x7AD9;&#x8DEF;&#x5F84;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">href</th>
      <th style="text-align:left">&#x94FE;&#x63A5;</th>
      <th style="text-align:left">string(1024)</th>
      <th style="text-align:left">
        <p>&#x94FE;&#x63A5;</p>
        <p>&#x6807;&#x7B7E;&#x5185;&#x7684;&#x8DF3;&#x8F6C;&#x94FE;&#x63A5;&#xFF08;&#x5982;&#x679C;&#x6CA1;&#x6709;&#x5219;&#x4E3A;null&#xFF09;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">page_id</th>
      <th style="text-align:left">&#x9875;&#x9762;ID</th>
      <th style="text-align:left">string(23)</th>
      <th style="text-align:left">
        <p>&#x9875;&#x9762;ID</p>
        <p>&#x9875;&#x9762;&#x552F;&#x4E00;&#x7684;id&#xFF0C;&#x7528;&#x4E8E;&#x4E0E;page&#x6570;&#x636E;join</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">action_id</th>
      <th style="text-align:left">&#x4E8B;&#x4EF6;ID</th>
      <th style="text-align:left">string(30)</th>
      <th style="text-align:left">
        <p>&#x4E8B;&#x4EF6;ID</p>
        <p>&#x6807;&#x7B7E;&#x4E8B;&#x4EF6;&#x7684;&#x552F;&#x4E00;id</p>
        <p>web&#x7684;action_id&#x4EE5;wa&#x5F00;&#x5934;&#xFF0C;mobile&#x4EE5;ma&#x5F00;&#x5934;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">index</th>
      <th style="text-align:left">&#x5217;&#x8868;&#x5E8F;&#x53F7;</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&#x5217;&#x8868;&#x5E8F;&#x53F7;</p>
        <p>&#x5217;&#x8868;&#x7C7B;&#x578B;&#x6807;&#x7B7E;&#x7684;&#x5E8F;&#x53F7;</p>
        <p>&#x7528;&#x4E8E;&#x6807;&#x8BB0;&#x5217;&#x8868;&#x5185;&#x7684;&#x7B2C;&#x51E0;&#x9879;&#xFF0C;&#x5206;&#x6790;&#x5217;&#x8868;&#x4E2D;&#x6700;&#x5E38;&#x88AB;&#x70B9;&#x51FB;&#x7684;&#x5185;&#x5BB9;&#x6216;&#x8005;&#x9996;&#x9879;&#x63A8;&#x5E7F;&#x6548;&#x679C;&#x7B49;&#x7B49;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">info</th>
      <th style="text-align:left">&#x4E8B;&#x4EF6;&#x9644;&#x52A0;&#x4FE1;&#x606F;</th>
      <th style="text-align:left">string(200)</th>
      <th style="text-align:left">
        <p>&#x4E8B;&#x4EF6;&#x9644;&#x52A0;&#x4FE1;&#x606F;</p>
        <p>&#x7528;&#x6237;&#x81EA;&#x5B9A;&#x4E49;&#x4E8B;&#x4EF6;&#x4FE1;&#x606F;</p>
        <p>&#x5BF9;&#x5E94;growingAttributesInfo&#x8BBE;&#x7F6E;&#x7684;&#x5B57;&#x6BB5;&#x4FE1;&#x606F;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}
{% endtabs %}

1. 三张数据表分别代表GIO定义的三种数据级别，访问级别（visit），页面级别（page）与标签级别（action）。visit代表访问级别的数据，按照session定义访问，page代表页面级别数据，打开的浏览页面就是一条记录，一条访问级别数据对应多条页面级别，action级别数据代表标签数据，定义页面元素标签的显示，点击，提交等事件，三者形成整个用户行为数据层级。目前导出的数据类型除了action下的imp\(impression\)类型因为数据量过大不可导出，其它数据都已经导出。
2. sendTime与eventTime的区别在于前者相当于是GIO平台接收到的时间，而eventTime是事件在客户端真正发生的时间，客户可以根据eventTime重现用户操作时间线。
3. 在refer中可以提取utm（广告链接关键字）或者搜索关键字等信息，用于分析访问来源。也可在visit表的query字段中提取utm信息。
4. appVersion，model，manufacturer，channel，osVersion仅在mobile端提供，更多信息可以从userAgent中提取。
5. 三张数据表可以根据“外键”join，分别是page\_id与page表的id，visit\_id与visit表的id，action\_id单独提供。因为标签事件并不导出impression（显示级别）的数据（数据量太大的缘故），所以建议通过action full outer join page，visit与page基本保持对应，若是在小时级别page数据无法join到对应的visit记录，visit记录可能存在于之前的小时单位中。
6. 所有数据已经根据userId, sessionId, sendTime进行排序，基本能够做到具体用户行为跟踪。
7. mobile端浏览器打开页面访问，默认platform类型为Web，若是需要区分则建议根据osVersion。
8. action数据中index，info为补充字段，参考changelog说明。

## 圈选数据映射关系

{% tabs %}
{% tab title="action\_tag" %}
| 名称 | 类型 | 说明 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">sendTime</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&#x53D1;&#x9001;&#x65F6;&#x95F4;</p>
        <p>&#x6570;&#x636E;&#x53D1;&#x9001;&#x8FC7;&#x6765;&#x7684;&#x65F6;&#x95F4;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">action_id</th>
      <th style="text-align:left">string(30)</th>
      <th style="text-align:left">
        <p>&#x4E8B;&#x4EF6;ID&#x3002;</p>
        <p>&#x6807;&#x7B7E;&#x4E8B;&#x4EF6;&#x7684;&#x552F;&#x4E00;id web&#x7684;action_id&#x4EE5;wa&#x5F00;&#x5934;&#xFF0C;mobile&#x4EE5;ma&#x5F00;&#x5934;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">rule_id</th>
      <th style="text-align:left">string(8)</th>
      <th style="text-align:left">
        <p>&#x89C4;&#x5219;ID&#x3002;</p>
        <p>&#x5339;&#x914D;&#x4E8B;&#x4EF6;&#x7684;&#x89C4;&#x5219;id&#xFF0C;&#x8BE5;id&#x4E3A;growingio&#x5E73;&#x53F0;&#x5708;&#x9009;&#x7684;&#x6807;&#x7B7E;&#x7684;&#x552F;&#x4E00;id.</p>
        <p>&#x8BE5;&#x503C;&#x7531;&#x5B57;&#x6BCD;&#x4E0E;&#x6570;&#x5B57;&#x7EC4;&#x6210;&#xFF0C;&#x4F8B;&#x5982;&#x2018;1ba052a9&#x2019;.</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="rules" %}
| 名称 | 类型 | 字段说明 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">rule_id</th>
      <th style="text-align:left">string(8)</th>
      <th style="text-align:left">
        <p>&#x89C4;&#x5219;ID&#xFF0C;&#x5339;&#x914D;&#x4E8B;&#x4EF6;&#x7684;&#x89C4;&#x5219;ID&#xFF0C;&#x8BE5;ID&#x4E3A;growingio&#x5E73;&#x53F0;&#x5708;&#x9009;&#x7684;&#x6807;&#x7B7E;&#x7684;&#x552F;&#x4E00;ID&#x3002;</p>
        <p>&#x8BE5;&#x503C;&#x7531;&#x5B57;&#x6BCD;&#x4E0E;&#x6570;&#x5B57;&#x7EC4;&#x6210;&#xFF0C;&#x4F8B;&#x5982;&#x2018;1ba052a9&#x2019;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">name</th>
      <th style="text-align:left">string(200)</th>
      <th style="text-align:left">
        <p>&#x89C4;&#x5219;&#x540D;&#x79F0;&#xFF0C;&#x5708;&#x9009;&#x7684;&#x6807;&#x7B7E;&#x540D;&#x79F0;&#x3002;</p>
        <p>&#x8BE5;&#x540D;&#x79F0;&#x4E0D;&#x53EF;&#x4EE5;&#x4F5C;&#x4E3A;&#x552F;&#x4E00;&#x4E3B;&#x952E;&#xFF0C;&#x53EA;&#x662F;&#x4FBF;&#x4E8E;&#x4F7F;&#x7528;&#x533A;&#x5206;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">ruleType</th>
      <th style="text-align:left">string(10)</th>
      <th style="text-align:left">
        <p>&#x89C4;&#x5219;&#x7C7B;&#x578B;&#xFF0C;&#x89C4;&#x5219;&#x5728;&#x5B9A;&#x4E49;&#x65F6;&#x53EF;&#x80FD;&#x6709;&#x4E0D;&#x540C;&#x7684;&#x7C7B;&#x578B;&#xFF0C;&#x4F8B;&#x5982;&#x6309;&#x94AE;&#x7684;imp&#x6216;&#x8005;clck&#x3002;</p>
        <p>&#x503C;&#x5305;&#x62EC; page, imp, clck, chng, sbmt&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}
{% endtabs %}

1. 在基础部分数据导出（visit, page, action\)之外，提供圈选数据与action级别数据的映射部分。
2. 通过action数据中的action\_id与action\_tag中的action\_id聚合，绑定对应的rule\_id（映射的规则名称）到action数据上。
3. rules代表了客户在GrowingIO平台上圈选的标签，rule\_id即其唯一标识符。
4. 通过rules表将名称绑定到上述的action\_tag表中，便于通过名称进行数据分析，识别导出数据中圈选部分的数据情况。
5. action\_tag与rules表均是关联信息表，用于更进一步分析导出的部分数据，在导出数据中定位圈选数据。建议规则建立时保持名称的唯一性，GrowingIO平台不保证规则名称唯一性。
6. 相同的规则名称下可能有多个规则类型，规则名称＋规则类型才能区分，此处的规则类型与基础数据action中的事件类型保持一致。

