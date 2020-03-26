---
description: 广告相关事件字段共分为2个事件类型。
---

# 广告相关字段

激活事件指GrowingIO 移动端Android/iOS SDK采集上报的激活事件数据。

如果激活事件能归因到某次点击事件，其中linkId、campaignId、channelId、linkName、campaignName、channelName、adsVariable 是对应点击事件的链接信息。

点击事件指Growingio广告监测链接收到\(点击\)访问数据。 其中的idfa、imei、uuid、androidId，如果有通常是由渠道方通过监测链接发送过来的数据。

{% tabs %}
{% tab title="ads\_track\_activation（广告激活事件）" %}
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
      <th style="text-align:left">IMEI</th>
      <th style="text-align:left">string&#xFF08;40&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;IMEI&gt;</p>
        <p>Android&#x5E73;&#x53F0;&#x7528;&#x4E8E;&#x5E7F;&#x544A;&#x76D1;&#x6D4B;&#x7684;ID&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;100500636E9AA9</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">uuid</th>
      <th style="text-align:left">string&#xFF08;40&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;UUID&gt;</p>
        <p>&#x7528;&#x4E8E;&#x5E7F;&#x544A;&#x76D1;&#x6D4B;&#x7684;ID&#x7684;UUID&#x683C;&#x5F0F;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;00000000-37fc-f5ob-1e8d-484b190312e1</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">androidId</th>
      <th style="text-align:left">string&#xFF08;40&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;Android ID&gt;</p>
        <p>SSAID&#xFF0C;&#x53C8;&#x79F0;&#x4E3A;Android ID&#x3002;&#x793A;&#x4F8B;&#xFF1A;2cab90e2a3b489ed</p>
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
      <th style="text-align:left">linkId</th>
      <th style="text-align:left">string&#xFF08;20&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x94FE;&#x63A5;ID&gt;</p>
        <p>&#x76D1;&#x6D4B;&#x94FE;&#x63A5;ID&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;Yo1KJXRl</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">campaignId</th>
      <th style="text-align:left">string&#xFF08;20&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x6D3B;&#x52A8;ID&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;GPndl79Y</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">channelID</th>
      <th style="text-align:left">string&#xFF08;20&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x6E20;&#x9053;ID&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;inmobi</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">linkName</th>
      <th style="text-align:left">string&#xFF08;60&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x94FE;&#x63A5;&#x540D;&#x79F0;&gt;</p>
        <p>2018/5/8 &#x5F00;&#x59CB;&#x751F;&#x6548;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x6D4B;&#x8BD5;&#x94FE;&#x63A5;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">campaignName</th>
      <th style="text-align:left">string&#xFF08;60&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x6D3B;&#x52A8;&#x540D;&#x79F0;&gt;</p>
        <p>2018/5/8 &#x5F00;&#x59CB;&#x751F;&#x6548;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x53CC;&#x5341;&#x4E00;&#x63A8;&#x5E7F;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">channelName</th>
      <th style="text-align:left">string&#xFF08;60&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x6E20;&#x9053;&#x540D;&#x79F0;&gt;</p>
        <p>2018/5/8 &#x5F00;&#x59CB;&#x751F;&#x6548;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x4ECA;&#x65E5;&#x5934;&#x6761;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">adsVariable</th>
      <th style="text-align:left">map&lt;String,String&gt;</th>
      <th style="text-align:left">
        <p>&lt;&#x94FE;&#x63A5;&#x7EF4;&#x5EA6;&#x53C2;&#x6570;&gt;</p>
        <p>2018/8/7 &#x5F00;&#x59CB;&#x751F;&#x6548;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;{&quot;city&quot;-&gt;&quot;beijing&quot;}&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| OAID | string（64） | &lt;匿名设备标识符&gt;Android平台用于广告监测的ID。2020/01/07 开始生效。 |
| :--- | :--- | :--- |
{% endtab %}

{% tab title="ads\_track\_click（广告点击事件）" %}
| 名称 | 类型（长度） | 说明 |
| :--- | :--- | :--- |


<table>
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
      <th style="text-align:left">IMEI</th>
      <th style="text-align:left">string&#xFF08;40&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x56FD;&#x9645;&#x79FB;&#x52A8;&#x8BBE;&#x5907;&#x8BC6;&#x522B;&#x7801;&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;867459000000000</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">uuid</th>
      <th style="text-align:left">string&#xFF08;40&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;UUID&gt;</p>
        <p>&#x7528;&#x4E8E;&#x5E7F;&#x544A;&#x76D1;&#x6D4B;&#x7684;ID&#x7684;UUID&#x683C;&#x5F0F;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;00000000-37fc-f5ob-1e8d-484b190312e1</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">androidId</th>
      <th style="text-align:left">string&#xFF08;40&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;Android ID&gt;</p>
        <p>SSAID&#xFF0C;&#x53C8;&#x79F0;&#x4E3A;Android ID&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;2cab90e2a3b489ed</p>
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
      <th style="text-align:left">eventTime</th>
      <th style="text-align:left">bigint</th>
      <th style="text-align:left">
        <p>&lt;&#x70B9;&#x51FB;&#x8BF7;&#x6C42;&#x65F6;&#x95F4;&gt;</p>
        <p>&#x8BF7;&#x6C42;&#x5728;SDK&#x53D1;&#x9001;&#x7684;&#x65F6;&#x95F4;&#x6233;.&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1521315962320</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">linkId</th>
      <th style="text-align:left">string(20)</th>
      <th style="text-align:left">
        <p>&lt;&#x94FE;&#x63A5;ID&gt;</p>
        <p>&#x76D1;&#x6D4B;&#x94FE;&#x63A5;ID&#x3002; &#x793A;&#x4F8B;&#xFF1A;Yo1KJXRl</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">campaignId</th>
      <th style="text-align:left">string&#xFF08;20&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x6D3B;&#x52A8;ID&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;GPndl79Y</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">channelId</th>
      <th style="text-align:left">string&#xFF08;20&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x6E20;&#x9053;ID&gt;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;inmobi</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">linkName</th>
      <th style="text-align:left">string&#xFF08;60&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x94FE;&#x63A5;&#x540D;&#x79F0;&gt;</p>
        <p>2018/5/8 &#x5F00;&#x59CB;&#x751F;&#x6548;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x6D4B;&#x8BD5;&#x94FE;&#x63A5;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">campaignName</th>
      <th style="text-align:left">string&#xFF08;60&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x6D3B;&#x52A8;&#x540D;&#x79F0;&gt;</p>
        <p>2018/5/8 &#x5F00;&#x59CB;&#x751F;&#x6548;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x53CC;&#x5341;&#x4E00;&#x63A8;&#x5E7F;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">channelName</th>
      <th style="text-align:left">string&#xFF08;60&#xFF09;</th>
      <th style="text-align:left">
        <p>&lt;&#x6E20;&#x9053;&#x540D;&#x79F0;&gt;</p>
        <p>2018/5/8 &#x5F00;&#x59CB;&#x751F;&#x6548;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;&#x4ECA;&#x65E5;&#x5934;&#x6761;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">adsVariable</th>
      <th style="text-align:left">map&lt;string,string&gt;</th>
      <th style="text-align:left">
        <p>&lt;&#x94FE;&#x63A5;&#x7EF4;&#x5EA6;&#x53C2;&#x6570;&gt;</p>
        <p>2018/8/7 &#x5F00;&#x59CB;&#x751F;&#x6548;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;{&quot;city&quot;-&gt;&quot;beijing&quot;}</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| OAID | string（64） | &lt;匿名设备标识符&gt;Android平台用于广告监测的ID。2020/01/07 开始生效。 |
| :--- | :--- | :--- |
{% endtab %}
{% endtabs %}

