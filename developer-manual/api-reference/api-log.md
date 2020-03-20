# API更新日志

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x7248;&#x672C;</th>
      <th style="text-align:left">&#x53D8;&#x66F4;&#x70B9;</th>
      <th style="text-align:left">&#x65F6;&#x95F4;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">V19.9.0</td>
      <td style="text-align:left">
        <p><b>&#x65B0;&#x529F;&#x80FD;&#xFF1A;</b>
        </p>
        <p>&#x63A8;&#x5E7F;&#x6D3B;&#x52A8;&#x76F8;&#x5173; API&#x53D8;&#x66F4;&#xFF0C;&#x6D3B;&#x52A8;&#x63D0;&#x5347;&#x5230;&#x9879;&#x76EE;&#x7EA7;&#x522B;&#x3002;</p>
      </td>
      <td style="text-align:left">2019-05-28</td>
    </tr>
    <tr>
      <td style="text-align:left">V18.11.1</td>
      <td style="text-align:left">
        <p><b>&#x65B0;&#x529F;&#x80FD;&#xFF1A;</b>
        </p>
        <ol>
          <li>&#x65B0;&#x589E; collectWebViewUserAgent &#x63A5;&#x53E3;&#xFF0C;&#x7528;&#x6237;&#x53EF;&#x4EE5;&#x9009;&#x62E9;&#x662F;&#x5426;&#x91C7;&#x96C6;&#x7528;&#x6237;
            UserAgent&#x3002;</li>
          <li>Configuration &#x5220;&#x9664; collectMacAddress&#x63A5;&#x53E3;&#x3002;</li>
        </ol>
      </td>
      <td style="text-align:left">2018-06-19</td>
    </tr>
    <tr>
      <td style="text-align:left">V18.8.1</td>
      <td style="text-align:left">&#x65B0;&#x589E;&#x7528;&#x6237;&#x5220;&#x9664;&#x63A5;&#x53E3;&#xFF0C;&#x53C2;&#x8003;
        <a
        href="gdprapi/">&#x6570;&#x636E;&#x7BA1;&#x7406;API&#xFF08;GDPR&#xFF09;</a>&#xFF0C;&#x6EE1;&#x8DB3;
          GDPR &#x7684;&#x8981;&#x6C42;&#x3002;</td>
      <td style="text-align:left">2018-05-22</td>
    </tr>
    <tr>
      <td style="text-align:left">V18.5.0</td>
      <td style="text-align:left">
        <p><b>&#x65B0;&#x529F;&#x80FD;&#xFF1A;</b>
        </p>
        <ol>
          <li>&#x200B;<a href="https://docs.growingio.com/docs/api/raw-data-api/raw-data-export-2.0">&#x539F;&#x59CB;&#x6570;&#x636E;&#x5BFC;&#x51FA; 2.0 API &#x529F;&#x80FD;</a>&#x3002;&#x63D0;&#x4F9B;&#x6700;&#x65B0;
            SDK 2.x &#x7684;&#x539F;&#x59CB;&#x6570;&#x636E;&#x5BFC;&#x51FA;&#x652F;&#x6301;&#x3002;</li>
          <li>&#x7528;&#x6237;&#x53D8;&#x91CF;&#x5206;&#x7C7B;&#x6269;&#x5C55;API&#x3002;&#x63D0;&#x4F9B;&#x4E86;&#x670D;&#x52A1;&#x5668;&#x5BF9;&#x63A5;&#xFF08;S2S&#xFF09;&#x7684;&#x65B9;&#x5F0F;&#x4E0A;&#x4F20;&#x7528;&#x6237;&#x7EF4;&#x5EA6;&#x7684;API&#x3002;</li>
        </ol>
      </td>
      <td style="text-align:left">2018-04-08</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>&#x589E;&#x52A0;&#x81EA;&#x5B9A;&#x4E49;&#x4E8B;&#x4EF6;&#x539F;&#x59CB;&#x6570;&#x636E;&#x5BFC;&#x51FA;</p>
        <ol>
          <li>visit&#x6570;&#x636E;&#x589E;&#x52A0;&#x65B0;&#x5B57;&#x6BB5;lat, lng,
            &#x4E3A;mobile&#x5E73;&#x53F0;&#x91C7;&#x96C6;&#x7684;gps&#x4FE1;&#x606F;</li>
          <li>&#x589E;&#x52A0;&#x6253;&#x70B9;&#x6570;&#x636E;&#x7684;&#x5BFC;&#x51FA;&#xFF0C;&#x5177;&#x4F53;&#x683C;&#x5F0F;&#x53C2;&#x8003;custom_attr&#x8868;&#x5B57;&#x6BB5;&#x8BF4;&#x660E;</li>
        </ol>
      </td>
      <td style="text-align:left">2017-02-21</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>&#x589E;&#x52A0;&#x8BBF;&#x95EE;&#x7EA7;&#x522B;&#x7684;query&#x4E0E;ps&#x9875;&#x9762;&#x4FE1;&#x606F;&#x5B57;&#x6BB5;</p>
        <ol>
          <li>&#x5728;visit&#x7EA7;&#x522B;&#x589E;&#x52A0;&#x65B0;&#x5B57;&#x6BB5;query&#xFF0C;&#x7528;&#x4E8E;&#x63D0;&#x53D6;&#x7528;&#x6237;&#x8BBF;&#x95EE;&#x65F6;&#x7684;utm&#x5B57;&#x6BB5;&#x4FE1;&#x606F;</li>
          <li>&#x5728;page&#x7EA7;&#x522B;&#x589E;&#x52A0;&#x65B0;&#x5B57;&#x6BB5;pagegroup,
            ps1~ps10&#xFF0C;&#x5BF9;&#x5E94;sdk&#x91C7;&#x96C6;&#x65F6;&#x8BBE;&#x7F6E;&#x7684;&#x9875;&#x9762;&#x4FE1;&#x606F;&#x5B57;&#x6BB5;</li>
        </ol>
      </td>
      <td style="text-align:left">2016-09-08</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>&#x5BFC;&#x51FA;&#x6570;&#x636E;&#x589E;&#x52A0;action_tag&#x4E0E;rules&#x4E24;&#x5F20;&#x6570;&#x636E;&#x8868;</p>
        <ol>
          <li>&#x5BFC;&#x51FA;&#x6570;&#x636E;&#x4E2D;&#x589E;&#x52A0;action_tag&#x6570;&#x636E;&#xFF0C;&#x7528;&#x4E8E;&#x5173;&#x8054;action&#x7EA7;&#x522B;&#x6570;&#x636E;&#x4E2D;&#x7684;action_id&#x4E0E;rule_id&#x5B57;&#x6BB5;</li>
          <li>rules&#x8868;&#x7528;&#x4E8E;&#x5173;&#x8054;rule_id&#x4E0E;rule&#x540D;&#x79F0;&#xFF0C;&#x4FBF;&#x4E8E;&#x8FDB;&#x4E00;&#x6B65;&#x5206;&#x6790;GrowingIO&#x5E73;&#x53F0;&#x5708;&#x9009;&#x7684;&#x6807;&#x7B7E;&#x6570;&#x636E;</li>
          <li>action_tag&#x4E0E;&#x4E4B;&#x524D;&#x7684;&#x5BFC;&#x51FA;&#x6570;&#x636E;&#x63A5;&#x53E3;&#x4E00;&#x81F4;&#xFF0C;&#x5728;&#x83B7;&#x53D6;&#x7684;&#x4E0B;&#x8F7D;&#x94FE;&#x63A5;&#x4E2D;&#x591A;&#x51FA;action_tag&#x4E00;&#x9879;&#xFF0C;&#x800C;rules&#x9700;&#x8981;&#x901A;&#x8FC7;&#x989D;&#x5916;&#x63A5;&#x53E3;&#x83B7;&#x53D6;</li>
        </ol>
      </td>
      <td style="text-align:left">2016-08-09</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>&#x5728;action&#x7EA7;&#x522B;&#x6570;&#x636E;&#x4E2D;&#x589E;&#x52A0;&#x5B57;&#x6BB5;index&#xFF0C;info&#x3002;</p>
        <ol>
          <li>index&#x7528;&#x4E8E;&#x6807;&#x8BB0;&#x5217;&#x8868;&#x4E2D;&#x7684;&#x7B2C;&#x51E0;&#x9879;&#x9879;&#x76EE;&#xFF0C;&#x4E3A;bigint&#x7C7B;&#x578B;</li>
          <li>info&#x7528;&#x4E8E;&#x7528;&#x6237;&#x81EA;&#x5B9A;&#x4E49;&#x6DFB;&#x52A0;&#x7684;&#x6807;&#x8BC6;&#x4FE1;&#x606F;&#xFF0C;string&#x7C7B;&#x578B;&#xFF0C;&#x5BF9;&#x5E94;&#x6570;&#x636E;&#x91C7;&#x96C6;&#x65F6;growingAttributesInfo&#x5B9A;&#x4E49;&#x7684;&#x5C5E;&#x6027;</li>
          <li>&#x6B64;&#x6B21;&#x4FEE;&#x6539;&#x4EC5;&#x5728;action&#x7EA7;&#x522B;&#x589E;&#x52A0;&#x5B57;&#x6BB5;&#x4FE1;&#x606F;&#xFF0C;visit&#x4E0E;page&#x4E0D;&#x53D7;&#x5F71;&#x54CD;</li>
        </ol>
      </td>
      <td style="text-align:left">2016-07-3</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ol>
          <li>&#x8BA4;&#x8BC1;&#x7684;&#x65F6;&#x5019;&#x9700;&#x8981;&#x4F20;&#x5165;
            tm &#x53C2;&#x6570;&#xFF0C;tm &#x662F;&#x5F53;&#x524D;&#x65F6;&#x95F4;&#x6233;&#xFF08;<b>&#x6BEB;&#x79D2;</b>)</li>
          <li>insights API &#x652F;&#x6301;&#x4F20;&#x5165; expire &#x53C2;&#x6570;&#xFF0C;&#x6765;&#x63A7;&#x5236;&#x94FE;&#x63A5;&#x8FC7;&#x671F;&#x65F6;&#x95F4;&#xFF0C;&#x9ED8;&#x8BA4;
            5 &#x5206;&#x949F;&#x3002;</li>
          <li>insights API &#x53EF;&#x4EE5;&#x8BF7;&#x6C42;&#x5C0F;&#x65F6;&#x6570;&#x636E;&#xFF0C;&#x6BD4;&#x5982;
            2016060510&#xFF0C;&#x8868;&#x793A;&#x83B7;&#x53D6;6&#x6708;5&#x53F7;10&#x70B9;&#x5230;11&#x70B9;&#x7684;&#x6570;&#x636E;&#x3002;</li>
        </ol>
      </td>
      <td style="text-align:left">2016-06-05</td>
    </tr>
  </tbody>
</table>