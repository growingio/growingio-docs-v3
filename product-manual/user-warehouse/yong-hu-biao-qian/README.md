# 用户标签 - Beta

{% hint style="warning" %}
灰度beta功能 ，如需体验试用，请联系客户经理 。
{% endhint %}

## 简介

标签是用户行为和特征的抽象与描述。

目的為： 使大量业务价值低的数据 转变 ➡ 为更有价值的业务信息 。

在特定业务场景下，标签可以让我们快速的了解**`一个用户`**或**`一群用户`**的特征。

{% hint style="info" %}
举例：

如在电销场景下，我们的客服人员需要了解目标用户的性别、年龄、常住城市、家庭成员数量、历史购买记录、最近浏览偏好等标签信息。这些信息可以帮助客服人员在脑海中快速形成一个鲜活的人物形象，帮助客服人员在与客户的交谈中更好的组织语言、挖掘并满足客户需求。 
{% endhint %}



## 基础概念

按照`业务特征`划分，标签可以分为人口属性标签、交易属性标签、兴趣偏好标签等。

按照`创建方式`划分，标签可以分为属性标签、计算标签、分层标签和算法标签。

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x6807;&#x7B7E;&#x5206;&#x7C7B;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
      <th style="text-align:left">&#x7279;&#x70B9;</th>
      <th style="text-align:left">&#x4E3E;&#x4F8B;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x5C5E;&#x6027;&#x6807;&#x7B7E;</td>
      <td style="text-align:left">
        <p>&#x6839;&#x636E;&#x4F01;&#x4E1A;&#x6C89;&#x6DC0;&#x7684;&#x7528;&#x6237;&#x4FE1;&#x606F;&#xFF0C;</p>
        <p>&#x52A0;&#x5DE5;&#x8F6C;&#x6362;&#x751F;&#x6210;</p>
      </td>
      <td style="text-align:left">&#x6570;&#x91CF;&#x5C11;&#x3001;&#x4E1A;&#x52A1;&#x4FE1;&#x606F;&#x5927;</td>
      <td
      style="text-align:left">
        <p>&#x6839;&#x636E;&#x8EAB;&#x4EFD;&#x8BC1;&#x53F7;&#x751F;&#x6210;&#x6807;&#x7B7E;&#x3002;&#x5982;</p>
        <p>&#x5E74;&#x9F84;&#x3001;&#x6027;&#x522B;&#x3001;&#x662F;&#x5426;&#x662F;&#x751F;&#x65E5;&#x3001;</p>
        <p>&#x51FA;&#x751F;&#x7701;&#x5E02;&#x7B49;</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x8BA1;&#x7B97;&#x6807;&#x7B7E;</td>
      <td style="text-align:left">&#x6839;&#x636E;&#x7528;&#x6237;&#x7684;&#x884C;&#x4E3A;&#x548C;&#x7279;&#x5F81;&#x8BA1;&#x7B97;&#x751F;&#x6210;</td>
      <td
      style="text-align:left">&#x6570;&#x91CF;&#x591A;&#x3001;&#x4E1A;&#x52A1;&#x4FE1;&#x606F;&#x5C0F;</td>
        <td
        style="text-align:left">
          <p>&#x6839;&#x636E;&#x8D2D;&#x4E70;&#x4E8B;&#x4EF6;&#x8BA1;&#x7B97;&#x751F;&#x6210;</p>
          <p>&#x6700;&#x8FD1;&#x8D2D;&#x4E70;&#x8DDD;&#x4ECA;&#x5929;&#x6570;(R)&#x3001;</p>
          <p>&#x8D2D;&#x4E70;&#x6B21;&#x6570;(F)&#x3001;&#x8D2D;&#x4E70;&#x91D1;&#x989D;(M)</p>
          </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x89C4;&#x5219;&#x6807;&#x7B7E;</td>
      <td style="text-align:left">
        <p>&#x6839;&#x636E;&#x4E1A;&#x52A1;&#x7ECF;&#x9A8C;&#xFF0C;</p>
        <p>&#x4EBA;&#x5DE5;&#x6216;&#x534A;&#x4EBA;&#x5DE5;&#x901A;&#x8FC7;&#x89C4;&#x5219;&#x8BA1;&#x7B97;&#x751F;&#x6210;</p>
      </td>
      <td style="text-align:left">
        <p>&#x4EBA;&#x529B;&#x6210;&#x672C;&#x9AD8;&#x3001;&#x6570;&#x91CF;&#x5C11;&#x3001;</p>
        <p>&#x4E1A;&#x52A1;&#x4FE1;&#x606F;&#x5927;</p>
      </td>
      <td style="text-align:left">
        <p>&#x6839;&#x636E;RFM&#x8BA1;&#x7B97;&#x6807;&#x7B7E;&#x6309;&#x4E1A;&#x52A1;</p>
        <p>&#x9700;&#x6C42;&#x6839;&#x636E;&#x89C4;&#x5219;&#x8BB2;&#x7528;&#x6237;&#x8FDB;&#x884C;</p>
        <p>&#x5206;&#x5C42;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x7B97;&#x6CD5;&#x6807;&#x7B7E;</td>
      <td style="text-align:left">
        <p>&#x5927;&#x90E8;&#x5206;&#x4F9D;&#x8D56;&#x7B97;&#x6CD5;&#x8BA1;&#x7B97;&#xFF0C;</p>
        <p>&#x9700;&#x8981;&#x4EBA;&#x5DE5;&#x53C2;&#x4E0E;&#x8C03;&#x53C2;&#x548C;&#x4E1A;&#x52A1;&#x6548;&#x679C;&#x9A8C;&#x8BC1;</p>
      </td>
      <td style="text-align:left">
        <p>&#x8BA1;&#x7B97;&#x6210;&#x672C;&#x9AD8;&#x3001;&#x6570;&#x91CF;&#x591A;&#x3001;</p>
        <p>&#x4E1A;&#x52A1;&#x6548;&#x679C;&#x9700;&#x8981;&#x9A8C;&#x8BC1;</p>
      </td>
      <td style="text-align:left">
        <p>&#x6839;&#x636E;&#x7528;&#x6237;&#x7279;&#x5F81;&#x548C;&#x884C;&#x4E3A;</p>
        <p>&#x9884;&#x6D4B;&#x7528;&#x6237;&#x8D2D;&#x4E70;&#x610F;&#x5411;</p>
      </td>
    </tr>
  </tbody>
</table>



标签可以帮助我们更加全面的描述一个用户，使业务人员能够前所未有的 看清用户。

但这并不意味着标签需要越多越好。出于计算成本和管理成本考量，我们应结合业务场景和业务需求，考虑什么样的标签能在业务操作中帮助我们更好的完成业务目标，并依据此目标进行标签的创建。

{% hint style="info" %}
根据GrowingIO 的行业经验 ：  
許多人_**错误的**_ 的认为跟踪更多、更丰富的标签有助于更好地了解客户。通常情况下，数据丰富，但洞察力较差。

一些细分市场最成功的客户仅限于跟踪少数重要数据，以帮助他们回答同样重要的业务问题。  
企业内部的标签体系往往有上百上千个，但对业务产生要效益的标签往往约10% 。
{% endhint %}

{% hint style="success" %}
目前GrowingIO提供了4种标签计算模型，

分别为

* 累计值/平均值/占比标签
* 最大值/最小值的事件属性标签
* 最初/最终的事件属性标签
* 分层标签

这4种标签主要用于解决 `计算标签`和`规则标签`的使用场景。
{% endhint %}







