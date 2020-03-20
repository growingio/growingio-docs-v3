# API 1.x

GrowingIO 的数据分析工具本身提供了例如 “访问来源”，“关键字”，“城市”,“操作系统"，”浏览器“等等这些维度。这些维度都可以和用户创建的指标进行多维的分析。但是因为每个公司的产品都有各自的用户维度，比如客户所服务的公司，用户正在使用的产品版本等等，为了能够让数据分析变得更加的灵活，我们在 JS SDK 中提供了用户自定义维度的 API 接口:

```javascript
_vds.push(['setCS1', 'CS1的key', 'CS1的value']);
_vds.push(['setCS2', 'CS2的key', 'CS2的value']);
_vds.push(['setCS3', 'CS3的key', 'CS3的value']);
...
_vds.push(['setCS10', 'CS10的key', 'CS10的value']);
```

在 JS SDK 中，我们总计支持上传 10 个自定义维度 CS1 - CS10，**所有CS属性都必须是用户的属性，不能是订单 ID，商品ID 等和用户没有确定的关联关系的属性。**

**CS字段设置条件和限制**

1. CS 字段不能是和用户没有直接关系的属性，比如不能是订单 ID，商品 ID 等。
2. CS1 字段：在 GrowingIO 系统中用于识别注册用户的身份，因此 CS1 的 value 必须填写用户的唯一身份标示 ID。
3. CS2 字段：在 GrowingIO 系统中用于识别 SaaS 客户的租户，因此所有的 SaaS 用户必须填写租户的唯一身份标示 ID，非 SaaS 用户不做限定。
4. 对于未登录用户，不要设置任何CS字段。
5. 如果没有用到所有的CS字段，剩下的可以不设置。
6. 同一个CS字段，必须保持在各个平台意义相同。
7. CS11~CS20 不支持在 SDK 中上传，必须通过服务器上传，具体请参考 [用户变量上传 API](../../../api-reference/customize-api/)。

如下例子中，总计上传 5个用户属性，分别是：

**CS1:** user\_id:100324 

**CS2:** company\_id:943123 

**CS3:** user\_name:张溪梦 

**CS4:** company\_name:GrowingIO 

**CS5:** sales\_name:销售员小王

```javascript
    <script type='text/javascript'>
        var _vds = _vds || [];
        window._vds = _vds;
        (function(){
          _vds.push(['setAccountId', '您的项目ID']);
​
          _vds.push(['setCS1', 'user_id', '100324']);
          _vds.push(['setCS2', 'company_id', '943123']);
          _vds.push(['setCS3', 'user_name', '张溪梦']);
          _vds.push(['setCS4', 'company_name', 'GrowingIO']);
          _vds.push(['setCS5', 'sales_name', '销售员小王']);
​
          (function() {
            var vds = document.createElement('script');
            vds.type='text/javascript';
            vds.async = true;
            vds.src = ('https:' == document.location.protocol ? 'https://' : 'http://') + 'assets.growingio.com/vds.js';
            var s = document.getElementsByTagName('script')[0];
            s.parentNode.insertBefore(vds, s);
          })();
        })();
    </script>
```

{% hint style="info" %}
CS11~CS20不支持在SDK中上传，必须通过服务器上传，具体请参考 [用户变量上传 API](../../../api-reference/customize-api/)。
{% endhint %}

**在上传成功两小时后，您需要在「项目管理-项目配置-CS 配置中」进行字段配置和激活，配置成功后便可开始使用 CS 字段进行分析。** 

