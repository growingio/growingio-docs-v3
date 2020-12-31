# 规则分群

## 计算规则

### 基础规则

* 用户做过

输入参数：{时间范围} + {事件} + {计算规则}

计算逻辑：指定时间范围活跃的用户中，指定事件符合计算规则的用户群体

![&#x8FC7;&#x53BB;7&#x5929;&#x6D3B;&#x8DC3;&#x7684;&#x7528;&#x6237; &#x4E14; &#x6D3B;&#x8DC3;&#x5929;&#x6570;&#x5927;&#x4E8E;&#x7B49;&#x4E8E;1&#x5929;](../../../../../.gitbook/assets/image%20%28129%29.png)

* 用户没做过

输入参数：{时间范围} + {事件} + {计算规则}

计算逻辑：指定时间范围活跃的用户中，没有做过指定事件的用户群体

![&#x8FC7;&#x53BB;7&#x5929;&#x6D3B;&#x8DC3;&#x7684;&#x7528;&#x6237; &#x4E14; &#x6CA1;&#x6709;&#x505A;&#x8FC7;&#x8BA2;&#x5355;&#x652F;&#x4ED8;&#x6210;&#x529F;&#x4E8B;&#x4EF6;](../../../../../.gitbook/assets/image%20%28135%29.png)

* 用户是

输入参数：{时间范围} + {用户属性} + {计算规则}

计算逻辑：指定时间范围活跃的用户中，用户属性符合计算规则的用户群体

![&#x8FC7;&#x53BB;7&#x5929;&#x6D3B;&#x8DC3;&#x7684;&#x7528;&#x6237; &#x4E14; &#x7EC4;&#x7EC7;&#x540D;&#x79F0;&#x7B49;&#x4E8E;&#x201C;GrowingIO&quot;](../../../../../.gitbook/assets/image%20%28131%29.png)

* 用户不是

输入参数：{时间范围} + {用户属性} + {计算规则}

计算逻辑：用户属性不符合计算规则的用户群体

![&#x7EC4;&#x7EC7;&#x540D;&#x79F0;&#x4E0D;&#x7B49;&#x4E8E;&#x201C;GrowingIO&quot;](../../../../../.gitbook/assets/image%20%28132%29.png)

### 逻辑规则

分群支持以下两种逻辑规则

* 且
* 或

{% hint style="success" %}
当分群第一个规则为肯定条件时\(用户做过/用户是\)，默认选择第一个肯定条件的时间范围活跃用户作为分群全集，并根据此全集计算分群用户；

当分群第一个规则为否定条件时\(用户没做过/用户不是\)，默认选择第一个肯定条件的时间范围活跃用户作为分群全集，并根据此全集计算分群用户；

当分群全部规则为否定条件时\(用户没做过/用户不是\)，默认选择第一个“用户不是”条件的时间范围活跃用户作为分群全集，并根据此全集计算分群用户。
{% endhint %}

## 常见问题

### 1. 使用否定条件时\(用户没做过/用户不是\)，为什么交换条件顺序计算结果不一致？

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5206;&#x7FA4;</th>
      <th style="text-align:left">&#x89C4;&#x5219;</th>
      <th style="text-align:left">&#x8BA1;&#x7B97;&#x7ED3;&#x679C;</th>
      <th style="text-align:left">&#x5360;&#x6BD4;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x5206;&#x7FA4;&#x4E00;</td>
      <td style="text-align:left">
        <p>&#x8FC7;&#x53BB;7&#x5929; &#x7528;&#x6237;&#x4E0D;&#x662F; &#x65B0;&#x7528;&#x6237;</p>
        <p>&#x4E14;</p>
        <p>&#x8FC7;&#x53BB;14&#x5929; &#x7528;&#x6237;&#x4E0D;&#x662F; &#x65B0;&#x7528;&#x6237;</p>
      </td>
      <td style="text-align:left">4598</td>
      <td style="text-align:left">81.38%</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x5206;&#x7FA4;&#x4E8C;</td>
      <td style="text-align:left">
        <p>&#x8FC7;&#x53BB;14&#x5929; &#x7528;&#x6237;&#x4E0D;&#x662F; &#x65B0;&#x7528;&#x6237;</p>
        <p>&#x4E14;</p>
        <p>&#x8FC7;&#x53BB;7&#x5929; &#x7528;&#x6237;&#x4E0D;&#x662F; &#x65B0;&#x7528;&#x6237;</p>
      </td>
      <td style="text-align:left">6541</td>
      <td style="text-align:left">78.41%</td>
    </tr>
  </tbody>
</table>

![](../../../../../.gitbook/assets/image%20%28127%29.png)

![](../../../../../.gitbook/assets/image%20%28134%29.png)

回顾计算规则：

> 当分群第一个规则为肯定条件时\(用户做过/用户是\)，默认选择第一个肯定条件的时间范围活跃用户作为分群全集，并根据此全集计算分群用户；
>
> 当分群第一个规则为否定条件时\(用户没做过/用户不是\)，默认选择第一个肯定条件的时间范围活跃用户作为分群全集，并根据此全集计算分群用户；
>
> 当分群全部规则为否定条件时\(用户没做过/用户不是\)，默认选择第一个“用户不是”条件的时间范围活跃用户作为分群全集，并根据此全集计算分群用户。

计算逻辑对比：

<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left">&#x5206;&#x7FA4;&#x4E00;</th>
      <th style="text-align:left">&#x5206;&#x7FA4;&#x4E8C;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x914D;&#x7F6E;&#x903B;&#x8F91;</td>
      <td style="text-align:left">
        <p>&#x8FC7;&#x53BB;7&#x5929; &#x7528;&#x6237;&#x4E0D;&#x662F; &#x65B0;&#x7528;&#x6237;</p>
        <p>&#x4E14;</p>
        <p>&#x8FC7;&#x53BB;14&#x5929; &#x7528;&#x6237;&#x4E0D;&#x662F; &#x65B0;&#x7528;&#x6237;</p>
      </td>
      <td style="text-align:left">
        <p>&#x8FC7;&#x53BB;14&#x5929; &#x7528;&#x6237;&#x4E0D;&#x662F; &#x65B0;&#x7528;&#x6237;</p>
        <p>&#x4E14;</p>
        <p>&#x8FC7;&#x53BB;7&#x5929; &#x7528;&#x6237;&#x4E0D;&#x662F; &#x65B0;&#x7528;&#x6237;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x8BA1;&#x7B97;&#x89C4;&#x5219;</td>
      <td style="text-align:left">
        <p>&#x8FC7;&#x53BB;7&#x5929;&#x6D3B;&#x8DC3;&#x7684;&#x7528;&#x6237;</p>
        <p>&#x4E14; &#x8FC7;&#x53BB;7&#x5929;&#x4E0D;&#x662F;&#x65B0;&#x7528;&#x6237;</p>
        <p>&#x4E14; &#x8FC7;&#x53BB;14&#x5929;&#x4E0D;&#x662F;&#x65B0;&#x7528;&#x6237;</p>
      </td>
      <td style="text-align:left">
        <p>&#x8FC7;&#x53BB;14&#x5929;&#x6D3B;&#x8DC3;&#x7684;&#x7528;&#x6237;</p>
        <p>&#x4E14; &#x8FC7;&#x53BB;14&#x5929;&#x4E0D;&#x662F;&#x65B0;&#x7528;&#x6237;</p>
        <p>&#x4E14; &#x8FC7;&#x53BB;7&#x5929;&#x4E0D;&#x662F;&#x65B0;&#x7528;&#x6237;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x89C4;&#x5219;&#x68B3;&#x7406;</td>
      <td style="text-align:left">
        <p>&#x8FC7;&#x53BB;7&#x5929;&#x6D3B;&#x8DC3;&#x7684;&#x7528;&#x6237;</p>
        <p>&#x4E14; &#x8FC7;&#x53BB;14&#x5929;&#x4E0D;&#x662F;&#x65B0;&#x7528;&#x6237;</p>
      </td>
      <td style="text-align:left">
        <p>&#x8FC7;&#x53BB;14&#x5929;&#x6D3B;&#x8DC3;&#x7684;&#x7528;&#x6237;</p>
        <p>&#x4E14; &#x8FC7;&#x53BB;14&#x5929;&#x4E0D;&#x662F;&#x65B0;&#x7528;&#x6237;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x8BA1;&#x7B97;&#x7ED3;&#x679C;</td>
      <td style="text-align:left">4598</td>
      <td style="text-align:left">6451</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x8BA1;&#x7B97;&#x5168;&#x96C6;</td>
      <td style="text-align:left">&#x8FC7;&#x53BB;7&#x5929;&#x6D3B;&#x8DC3;&#x7684;&#x7528;&#x6237;&#xFF1A;
        5650</td>
      <td style="text-align:left">&#x8FC7;&#x53BB;14&#x5929;&#x6D3B;&#x8DC3;&#x7684;&#x7528;&#x6237;&#xFF1A;8227</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x7528;&#x6237;&#x5360;&#x6BD4;</td>
      <td style="text-align:left">4598/5650 = 81.38%</td>
      <td style="text-align:left">6541/8227 = 78.41%</td>
    </tr>
  </tbody>
</table>

