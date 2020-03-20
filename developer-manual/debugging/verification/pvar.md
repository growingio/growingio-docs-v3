---
description: 验证“页面级变量”数据。
---

# pvar（页面级变量）事件

> 场景：在商品详情页，设置“商品名称”、“商品品类”作为页面级变量。

**页面级变量配置方式示例**

| 标识符 | 名称 | 描述 |
| :--- | :--- | :--- |
| skuName\_pvar | 商品名称 | 商品名称 |
| skuCategory\_pvar | 商品品类 | 商品品类，例如裙子、鞋靴等 |

**对应的代码**

此示例中的页面级变量为“商品名称（skuName\_pvar）”、“商品品类（skuCategory\_pvar）”，在商品详情页面上设置了这两个页面级变量。

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
      <td style="text-align:left">gio(&apos;page.set&apos;, key, value);&#x6216;gio(&apos;page.set&apos;,
        pageLevelVariables);</td>
      <td style="text-align:left">gio(&apos;page.set&apos;, {&apos;skuName_pvar&apos;: &apos;&#x5973;&#x58EB;&#x4E2D;&#x8DDF;&#x51C9;&#x978B;&apos;,
        &apos;skuCategory_pvar&apos;: &apos;&#x978B;&#x9774;&apos;});</td>
    </tr>
    <tr>
      <td style="text-align:left">Android SDK</td>
      <td style="text-align:left">
        <p>GrowingIO.getInstance().setPageVariable(<code>Activity</code> activity, <code>String</code>key, <code>String</code> value);</p>
        <p>&#x6216;</p>
        <p>GrowingIO.getInstance().setPageVariable(<code>Activity</code> activity, <code>JSONObject</code> pageLevelVariables);</p>
      </td>
      <td style="text-align:left">
        <p>JSONObject jsonObject = new JSONObject(); jsonObject.put(&quot;skuName_pvar&quot;,
          &quot;&#x5973;&#x58EB;&#x4E2D;&#x8DDF;&#x51C9;&#x978B;&quot;); jsonObject.put(&quot;skuCategory_pvar&quot;,
          &quot;&#x978B;&#x9774;&quot;);</p>
        <p>GrowingIO.getInstance().setPageVariable(GoodsDetailActivity, jsonObject);</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">iOS SDK</td>
      <td style="text-align:left">
        <p>+ (void)setPageVariableWithKey:(NSString *)key andStringValue:(NSString
          *)stringValue toViewController:(UIViewController*)viewController;</p>
        <p>&#x6216;</p>
        <p>+ (void)setPageVariable:(NSDictionary&lt;NSString *, NSObject *&gt; *)variable
          toViewController: (UIViewController *)viewController;</p>
      </td>
      <td style="text-align:left">[Growing setPageVariable:@{@&quot;skuName_pvar&quot;:@&quot;&#x5973;&#x58EB;&#x4E2D;&#x8DDF;&#x51C9;&#x978B;&quot;,
        @&quot;skuCategory_pvar&quot;:@&quot;&#x978B;&#x9774;&quot;} toViewController:GoodsDetailViewController];</td>
    </tr>
  </tbody>
</table>**数据验证方法**

在对应的应用（网站、Android 或者 iOS App）中打开设置了页面级变量的商品详情页，通过 Debugger 工具验证数据准确性

按照如下流程图验证

![](../../../.gitbook/assets/pvar1x2.png)

在本例中，如下图的数据请求说明打点代码生效

![](../../../.gitbook/assets/pvar.png)

\*\*\*\*

\*\*\*\*

\*\*\*\*

\*\*\*\*

