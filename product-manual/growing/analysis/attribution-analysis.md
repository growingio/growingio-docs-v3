# 渠道归因分析

## 渠道归因分析的应用场景？

借助 GrowingIO 强大的数据采集和分析能力，分析产品，在转化归因的分析场景下，帮您深入了解用户转化路径，找到广告或渠道对用户转化的促成关系。在 GrowingIO 的归因分析中，您可以：

1. 利用多种归因模型进行灵活的归因分析，分析结论不再受限于单一归因模型；
2. 根据实际业务情况，灵活定义归因回溯时间窗口，最长支持 30 天数据回溯；
3. 在多种归因模型下，比对分析结果，了解各渠道对转化的促成情况；
4. 提供转化路径洞察分析，直接呈现用户在实际转化发生时的路径顺序。

## 产品使用

![](../../../.gitbook/assets/image%20%2857%29.png)

\*\*\*\*

**操作步骤**

Step 1:确定要分析的转化事件，例如：xx 商品下单，用户注册完成，或其他关键业务行为，当前转化事件只支持埋点事件（不包含服务端埋点）；

Step 2:选择要分析的人群  例如：新注册的用户，会员用户，通过分群功能可以灵活定义要分析的人群；

Step 3:定义转化目标发生的时间范围，当前最长支持回溯转化发生前 30 天数据；

Step 4:选择归因回溯时间范围，当前最长支持回溯转化发生前 30 天数据。



### 展示分析结果

在以上 4 步设定完成后，开始进行分析，默认会使用「首次点击归因」分析模型对数据进行计算。

![](../../../.gitbook/assets/image%20%2853%29.png)



在数据呈现方式上，默认以「推广渠道」的方式展现在当前归因模型下的转化归因结果，也可以选择切换为更详细的「触点」方式来查看转化归因结果。

**触点定义**

用户在一次转化完成时，在转化前都接触过的信息，如果该信息有促成用户达成转化目的的意义时，则称其为触点，例如广告主在进行产品推广时，通常会向用户进行广告推广，则广告被定义为触点。

{% hint style="info" %}
目前触点主要支持外部触点，对此可理解为从外部到 网站/应用 App /小程序 的链接（包括以链接生成的二维码）。关于触点和推广渠道的对照关系，可参考文末对照表。
{% endhint %}

**转化贡献度**

其计算方式为当前项中的转化次数，占转化总次数的占比，方便直观了解当前推广渠道或触点在整体中的重要程度。



### 多归因模型对比

![](../../../.gitbook/assets/image%20%2855%29.png)

归因分析支持按照实际业务需求，使用不同归因模型进行计算，同时也支持将不同归因模型下的转化归因结果数据进行对比，充分衡量各渠道或广告的效果。



### 归因模型支持情况

目前 GrowingIO 归因分析工具支持以下几种归因分析模型：

**1、首次点击归因**

在回溯期内首次触点转化功劳分配 100%。其余触点分配 0%。

**2、最终点击归因**

在回溯期内最后一次触点转化分的功劳分配 100%，其余触点分配 0%。

**3、线型归因**

在回溯周期内，一次转化被各触点平均分配。例如用户的一次转化接触了 5 个触点，那么 5 个触点中每个触点都被分配 20%。

**4、基于位置归因**

在回溯期内，用户的首次分配 40%，末次分配 40%，其余中间位平均分配 20%。



## 转化路径

![](../../../.gitbook/assets/image%20%2850%29.png)

转化路径是统计用户在发生转化前的完整的触点数据，并且将具有相同转化路径的用户进行汇总，帮您找出在当前发生的转化的用户中，最佳的转化路径。

**数据展示方式**

转化路径同样支持选择以推广渠道或触点的方式查看转化路径数据。

## 归因数据回溯与计算规则

如果您对归因分析的数据计算逻辑感兴趣，可以通过了解数据回溯规则，以及底层计算逻辑，使您对归因分析的数据结果理解更加深入。

**举例说明**

A、B、C、D、E 表示用户在发生转化前接触到广告所对应的渠道。

![](../../../.gitbook/assets/image%20%2856%29.png)

小红、小陈、小李 表示三名发生了转化的用户，但各自所接收到的广告以及查看次序不完全相同，那么在这一轮广告投放中，每个广告对于用户发生转化的促成作用是多少呢？

以上为例，三位用户分别完成下单，共三次，假设以首次点击归因模型进行计算，则 A：2次，B：1 次；假设以最终点击归因模型进行计算，则 C：1 次，D：2次。

可以看到对于同样的三名用户发生转化，在使用不同的归因模型进行分析时，可以看到完全不同的结果，通过不同归因模型的对比分析，可以充分了解各渠道在促成用户转化时的价值贡献。



![](../../../.gitbook/assets/image%20%2851%29.png)

假设小红在第一次下单转化发生后，过了一段时间经过复购推荐发生第二次转化，如上图，小红一人发生 2 次转化，两次转化将分别进行数据回溯，各次转化之间互不干扰。以首次点击归因模型计算，小红两次转化中，A：1 次，B：1 次。以最终点击归因模型计算，则 C：1 次，E：1次。

## 附表

### **\*触点、推广渠道信息提取规则**

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>&#x5206;&#x7C7B;</b>
      </th>
      <th style="text-align:left">&#x4E3E;&#x4F8B;</th>
      <th style="text-align:left">&#x89E6;&#x70B9;&#x4FE1;&#x606F;&#x63D0;&#x53D6;</th>
      <th style="text-align:left">&#x63A8;&#x5E7F;&#x6E20;&#x9053;&#x4FE1;&#x606F;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x901A;&#x8FC7; GIO&#x751F;&#x6210;&#x7684;&#x70B9;&#x51FB;&#x76D1;&#x6D4B;&#x94FE;&#x63A5;</td>
      <td
      style="text-align:left">
        <p>&#x7528;&#x6237;&#x9700;&#x8981;&#x5728;&#x5934;&#x6761;&#x8FDB;&#x884C;&#x5E7F;&#x544A;&#x6295;&#x653E;</p>
        <p>&#x9009;&#x62E9;&#x63A8;&#x5E7F;&#x6E20;&#x9053;&#x4E3A;&#xFF1A;&#x4ECA;&#x65E5;&#x5934;&#x6761;</p>
        <p>&#x70B9;&#x51FB;&#x76D1;&#x6D4B;&#x94FE;&#x63A5;&#xFF1A; gio.ren/at1/o1de3Q</p>
        <p>&#x76D1;&#x6D4B;&#x94FE;&#x63A5;&#x540D;&#x79F0;&#x4E3A;&#xFF1A;&#x5934;&#x6761;&#x53CC;&#x5341;&#x4E00;&#x4FC3;&#x9500;&#x76D1;&#x63A7;</p>
        </td>
        <td style="text-align:left">&#x5934;&#x6761;&#x53CC;&#x5341;&#x4E00;&#x4FC3;&#x9500;&#x76D1;&#x63A7;</td>
        <td
        style="text-align:left">&#x4ECA;&#x65E5;&#x5934;&#x6761;</td>
    </tr>
    <tr>
      <td style="text-align:left">UTM &#x53C2;&#x6570;</td>
      <td style="text-align:left">
        <p>&#x7528;&#x6237;&#x76F4;&#x63A5;&#x5728;&#x6295;&#x653E;&#x843D;&#x5730;&#x9875;&#x4E2D;&#x6DFB;&#x52A0;
          utm &#x53C2;&#x6570;&#xFF0C;</p>
        <p>&#x8FDB;&#x884C;&#x6295;&#x653E;</p>
        <p><a href="https://www.growingio.com/?utm_source=weixin">https://www.growingio.com/?utm_source=weixin</a>
        </p>
        <p>&amp;utm_medium=article1</p>
        <p>&amp;utm_campaign=product</p>
        <p>&amp;utm_content=0811-tool</p>
        <p>&amp;utm_term=tool</p>
      </td>
      <td style="text-align:left">
        <p>utm_source=weixin</p>
        <p>&amp;utm_medium=article1</p>
        <p>&amp;utm_campaign=product</p>
        <p>&amp;utm_content=0811-tool</p>
        <p>&amp;utm_term=tool</p>
        <p>&#xFF08;&#x6309;&#x7167;&#x7528;&#x6237;&#x5B9A;&#x4E49;&#x7684; UTM &#x503C;&#x7EC4;&#x5408;&#x76F4;&#x63A5;&#x5C55;&#x793A;&#xFF0C;&#x9650;&#x5B9A;&#x6587;&#x5B57;&#x957F;&#x5EA6;&#xFF0C;&#x8D85;&#x8FC7;&#x540E;&#x663E;&#x793A;&#x300C;...&#x300D;&#xFF09;</p>
      </td>
      <td style="text-align:left">
        <p>weixin</p>
        <p>&#xFF08;&#x5728; utm_source &#x4E0B;&#x76F4;&#x63A5;&#x53D6;&#x503C;&#xFF09;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>UTM &#x53C2;&#x6570;</p>
        <p>&#xFF08;&#x6E20;&#x9053;&#x4FE1;&#x606F;&#x672A;&#x914D;&#x7F6E;&#xFF09;</p>
      </td>
      <td style="text-align:left">
        <p>&#x7528;&#x6237;&#x76F4;&#x63A5;&#x5728;&#x6295;&#x653E;&#x843D;&#x5730;&#x9875;&#x4E2D;&#x6DFB;&#x52A0;
          utm &#x53C2;&#x6570;&#xFF0C;</p>
        <p>&#x8FDB;&#x884C;&#x6295;&#x653E;</p>
        <p><a href="https://www.growingio.com/?">https://www.growingio.com/?</a>
        </p>
        <p>utm_campaign=produc</p>
        <p>t&amp;utm_xxx=yyy</p>
      </td>
      <td style="text-align:left">
        <p>utm_campaign=product</p>
        <p>&amp;utm_xxx=yyy</p>
      </td>
      <td style="text-align:left">
        <p>&#x672A;&#x914D;&#x7F6E;</p>
        <p>&#xFF08;&#x7528;&#x6237;&#x672A;&#x914D;utm_source &#x7684;&#x503C;&#xFF09;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x641C;&#x7D22;&#x8BCD;</td>
      <td style="text-align:left">
        <p>&#x901A;&#x8FC7;&#x641C;&#x7D22;&#x5F15;&#x64CE;&#x76F4;&#x63A5;&#x76F4;&#x63A5;&#x8DF3;&#x8F6C;&#x5230;&#x7F51;&#x9875;</p>
        <p>&#x901A;&#x8FC7;&#x767E;&#x5EA6;&#x641C;&#x7D22;&#x8DF3;&#x8F6C; <a href="https://www.growingio.com/?">https://www.growingio.com/</a>
        </p>
      </td>
      <td style="text-align:left">
        <p>&#x5982;&#x679C;&#x53EF;&#x4EE5;&#x6210;&#x529F;&#x89E3;&#x6790;&#x641C;&#x7D22;&#x5F15;&#x64CE;&#x7684;&#x641C;&#x7D22;&#x8BCD;&#xFF0C;&#x5219;&#x76F4;&#x63A5;&#x5C55;&#x793A;&#x5177;&#x4F53;&#x7684;&#x641C;&#x7D22;&#x8BCD;&#xFF1B;</p>
        <p>&#x5982;&#x679C;&#x641C;&#x7D22;&#x8BCD;&#x88AB;&#x52A0;&#x5BC6;&#x6216;&#x89E3;&#x6790;&#x5931;&#x8D25;&#xFF0C;&#x5219;&#x5C55;&#x793A;&#x4E3A;&#x81EA;&#x7136;&#x6D41;&#x91CF;&#xFF0C;&#x5982;&#xFF1A;baidu
          organic</p>
      </td>
      <td style="text-align:left">
        <p>Baidu</p>
        <p>&#xFF08;&#x76F4;&#x63A5;&#x5C55;&#x793A;&#x641C;&#x7D22;&#x5F15;&#x64CE;&#x540D;&#x79F0;&#xFF09;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x5C0F;&#x7A0B;&#x5E8F;&#x7801;</td>
      <td style="text-align:left">
        <p>&#x7528;&#x6237;&#x9700;&#x8981;&#x5728;&#x7EBF;&#x4E0B;&#x505A;&#x5C0F;&#x7A0B;&#x5E8F;&#x63A8;&#x5E7F;</p>
        <p>&#x4E8C;&#x7EF4;&#x7801;&#x540D;&#x79F0;&#x4E3A;&#xFF1A;xxx &#x7EBF;&#x4E0B;&#x5730;&#x63A8;</p>
        <p>&#x5E7F;&#x544A;&#x6E20;&#x9053;&#xFF1A;&#x7EBF;&#x4E0B; BD &#x6E20;&#x9053;</p>
      </td>
      <td style="text-align:left">xxx &#x7EBF;&#x4E0B;&#x5730;&#x63A8;</td>
      <td style="text-align:left">
        <p>&#x7EBF;&#x4E0B; BD &#x6E20;&#x9053;</p>
        <p>&#xFF08;&#x5728; utm_source &#x4E0B;&#x76F4;&#x63A5;&#x53D6;&#x503C;&#xFF09;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x5C0F;&#x7A0B;&#x5E8F;&#x76D1;&#x6D4B;&#x94FE;&#x63A5;</td>
      <td style="text-align:left">
        <p>&#x7528;&#x6237;&#x9700;&#x8981;&#x5728;&#x5FAE;&#x4FE1;&#x516C;&#x4F17;&#x53F7;&#x8FDB;&#x884C;&#x5E7F;&#x544A;&#x6295;&#x653E;</p>
        <p>&#x9009;&#x62E9;&#x63A8;&#x5E7F;&#x6E20;&#x9053;&#x4E3A;&#xFF1A;&#x5FAE;&#x4FE1;&#x516C;&#x4F17;&#x53F7;&#x6587;&#x7AE0;</p>
        <p>&#x751F;&#x6210;&#x76D1;&#x6D4B;&#x94FE;&#x63A5;&#x4E3A;&#xFF1A;pages/popular/popular?aid=nom42rPz1</p>
        <p>&#x76D1;&#x6D4B;&#x94FE;&#x63A5;&#x547D;&#x540D;&#x4E3A;&#xFF1A;&#x5927;
          V &#x8D26;&#x53F7;&#x6269;&#x91CF;&#x63A8;&#x5E7F;</p>
      </td>
      <td style="text-align:left">&#x5927; V &#x8D26;&#x53F7;&#x6269;&#x91CF;&#x63A8;&#x5E7F;</td>
      <td style="text-align:left">&#x5FAE;&#x4FE1;&#x516C;&#x4F17;&#x53F7;&#x6587;&#x7AE0;</td>
    </tr>
    <tr>
      <td style="text-align:left">*&#x76F4;&#x63A5;&#x8BBF;&#x95EE;</td>
      <td style="text-align:left">&#x5F53;&#x7528;&#x6237;&#x5728;&#x8F6C;&#x5316;&#x524D;&#x672A;&#x68C0;&#x6D4B;&#x5230;&#x4EFB;&#x4F55;&#x89E6;&#x70B9;&#x6570;&#x636E;&#xFF0C;&#x5219;&#x8BB0;&#x4E3A;&#x76F4;&#x63A5;&#x8BBF;&#x95EE;</td>
      <td
      style="text-align:left">&#x76F4;&#x63A5;&#x8BBF;&#x95EE;</td>
        <td style="text-align:left">&#x76F4;&#x63A5;&#x8BBF;&#x95EE;</td>
    </tr>
  </tbody>
</table>



