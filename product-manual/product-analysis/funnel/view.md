# 漏斗分析结果解读

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x9879;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x5355;&#x4F4D;&#x4E3A;&#x4EBA;&#x6570;</td>
      <td style="text-align:left">GrowingIO &#x7684;&#x6F0F;&#x6597;&#x57FA;&#x4E8E;&#x7528;&#x6237;&#x884C;&#x4E3A;&#x5206;&#x6790;&#xFF0C;&#x6F0F;&#x6597;&#x6BCF;&#x4E00;&#x6B65;&#x7684;&#x6570;&#x636E;&#x7EDF;&#x8BA1;&#x7684;&#x662F;&#x201C;<b>&#x4EBA;&#x6570;</b>&#x201D;&#xFF0C;&#x4E5F;&#x5C31;&#x662F;&#x6BCF;&#x4E00;&#x6B65;&#x6709;&#x591A;&#x5C11;&#x4EBA;&#x5B8C;&#x6210;&#xFF1B;&#x5982;&#x679C;&#x540C;1&#x4E2A;&#x7528;&#x6237;&#x5728;&#x9009;&#x5B9A;&#x7684;&#x65F6;&#x95F4;&#x8303;&#x56F4;&#x5B8C;&#x6210;&#x4E86;&#x67D0;&#x4E2A;&#x6B65;&#x9AA4;
        2 &#x6B21;&#xFF0C;&#x7B97;&#x4F5C; 1 (&#x5355;&#x4F4D;&#xFF1A;&#x4EBA;)&#xFF1B;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x6B65;&#x9AA4;&#x65F6;&#x5E8F;</td>
      <td style="text-align:left">
        <p></p>
        <p>&#x5728;&#x8F6C;&#x5316;&#x5468;&#x671F;&#x5185;&#x6F0F;&#x6597;&#x7B2C;&#x4E00;&#x6B65;&#x548C;&#x7B2C;&#x4E8C;&#x6B65;&#x4E3A;&#x4F8B;&#xFF1A;</p>
        <p>&#x5E38;&#x89C4;&#x987A;&#x5E8F;&#xFF1A;&#x5982;&#x679C;&#x7528;&#x6237;&#x5148;&#x5B8C;&#x6210;&#x7B2C;&#x4E00;&#x6B65;&#x53C8;&#x5B8C;&#x6210;&#x7B2C;&#x4E8C;&#x6B65;&#xFF0C;&#x5219;&#x7B2C;&#x4E8C;&#x6B65;&#x7528;&#x6237;&#x91CF;
          +1 &#xFF1B;</p>
        <p>&#x975E;&#x5E38;&#x89C4;&#x987A;&#x5E8F;&#xFF1A;&#x7528;&#x6237;&#x5148;&#x5B8C;&#x6210;&#x7B2C;&#x4E8C;&#x6B65;&#x518D;&#x5B8C;&#x6210;&#x7B2C;&#x4E00;&#x6B65;</p>
        <ul>
          <li>&#x4ECA;&#x65E5;&#x6570;&#x636E;&#xFF1A;&#x5728;&#x540C;&#x4E00;&#x5C0F;&#x65F6;&#x5185;&#x5B8C;&#x6210;&#xFF0C;&#x5219;&#x7B2C;&#x4E8C;&#x6B65;&#x7528;&#x6237;&#x91CF;
            +1&#xFF1B;&#x4E0D;&#x5728;&#x540C;&#x4E00;&#x5C0F;&#x65F6;&#x5B8C;&#x6210;&#xFF0C;&#x7B2C;&#x4E8C;&#x6B65;&#x7528;&#x6237;+0</li>
          <li>&#x4ECA;&#x65E5;&#x524D;&#x6570;&#x636E;&#xFF1A;&#x5728;&#x540C;&#x4E00;&#x5929;&#x5185;&#x5B8C;&#x6210;&#xFF0C;&#x5219;&#x7B2C;&#x4E8C;&#x6B65;&#x7528;&#x6237;&#x91CF;
            +1&#xFF1B;&#x4E0D;&#x5728;&#x540C;&#x4E00;&#x5929;&#x5B8C;&#x6210;&#xFF0C;&#x7B2C;&#x4E8C;&#x6B65;&#x7528;&#x6237;+0</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>在漏斗视图界面，单击图示界面上的 ![](../../../.gitbook/assets/mao-pao-ti-shi.png) ，可以看到该时间在选定事件周期内自身的数据情况，辅助您判断漏斗转化数据是否受到事件数据有效性的影响。

举例来说，您在 6 月 7 日圈选了某个事件 A ，数据回溯 7 天，事件 A 的有效期是从 6 月 1 日开始的；如果您在漏斗中使用了事件 A ，并且时间选择了「 5 月 20 日至昨天」，其他事件的有效期从 5 月 1 日开始，而事件 A 是从 6 月 1 日开始；您需要注意到，漏斗的转化率数据受到了事件 A 有效期的影响。

![](../../../.gitbook/assets/image%20%28173%29.png)

