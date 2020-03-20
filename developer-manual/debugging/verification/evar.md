---
description: 验证“转化变量”数据。
---

# evar（转化变量）事件

> 场景：在购物场景中，用户可以通过首页Banner、商品列表页等方式进入某个商品详情页，进而产生下单行为，想要知道不同的前序行为对于下单的贡献，就可以将商品详情页的入口来源定义为转化变量，用于分解下单行为（埋点事件）

**转化变量配置方式示例**

| 标识符 | 名称 | 描述 | 归因 | 失效 |
| :--- | :--- | :--- | :--- | :--- |
| enterSource\_evar | 商品详情页的入口来源 | 取值包括首页Banner、商品列表页等 | 根据需求选择（不涉及数据验证） | 根据需求选择（不涉及数据验证） |

**对应的代码**

此示例中的转化变量为“商品详情页的入口来源（enterSource\_evar）”，当进入详情页时设置了这个转化变量。

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x5E73;&#x53F0;</th>
      <th style="text-align:left">&#x539F;&#x578B;</th>
      <th style="text-align:left">&#x4EE3;&#x7801;&#x793A;&#x4F8B;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">JS SDK</td>
      <td style="text-align:left">gio(&apos;evar.set&apos;, key, value);&#x6216;gio(&apos;evar.set&apos;,
        conversionVariables);</td>
      <td style="text-align:left">gio(&apos;evar.set&apos;, &apos;enterSource_evar&apos;, &apos;&#x9996;&#x9875;Banner&apos;);&#x6216;gio(&apos;evar.set&apos;,
        {&apos;enterSource_evar&apos;: &apos;&#x9996;&#x9875;Banner&apos;});</td>
    </tr>
    <tr>
      <td style="text-align:left">Android SDK</td>
      <td style="text-align:left">
        <p>GrowingIO.getInstance().setEvar(String key, String value);</p>
        <p>&#x6216;</p>
        <p>GrowingIO.getInstance().setEvar(JSONObject conversionVariables);</p>
      </td>
      <td style="text-align:left">
        <p>GrowingIO.getInstance().setEvar(&quot;enterSource_evar&quot;, &quot;&#x9996;&#x9875;Banner&quot;);</p>
        <p>&#x6216;</p>
        <p>JSONObject jsonObject = new JSONObject();</p>
        <p>jsonObject.put(&quot;enterSource_evar&quot;, &quot;&#x9996;&#x9875;Banner&quot;);</p>
        <p>GrowingIO.getInstance().setEvar(jsonObject);</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">iOS SDK</td>
      <td style="text-align:left">
        <p>+ (void)setEvarWithKey:(NSString *)key andStringValue:(NSString *)stringValue;</p>
        <p>&#x6216;</p>
        <p>+ (void)setEvar:(NSDictionary&lt;NSString *, NSObject *&gt; *)variable;</p>
      </td>
      <td style="text-align:left">
        <p>[Growing setEvarWithKey:@&quot;enterSource_evar&quot; andStringValue:@&quot;&#x9996;&#x9875;Banner&quot;];</p>
        <p>&#x6216;</p>
        <p>[Growing setEvar:@{@&quot;enterSource_evar&quot;:@&quot;&#x9996;&#x9875;Banner&quot;}];</p>
      </td>
    </tr>
  </tbody>
</table>**数据验证方法**

在对应的应用（网站、Android 或者 iOS App）中触发设置了转化变量的时机，通过 Debugger 工具验证数据准确性

按照如下流程图验证

![](../../../.gitbook/assets/evar1x2.png)

在本例中，如下图的数据请求说明打点代码生效

![](../../../.gitbook/assets/evar.png)

