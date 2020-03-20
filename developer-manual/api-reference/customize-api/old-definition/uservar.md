# 用户变量上传

## 获取认证码

旧版本上传接口使用 cs1-cs20 的方式上传用户属性，对应的签名计算中 keyArray 为1234,1235。加密 Message 为 `ai=$projectKeyId&cs=$keyArray`

如 Java：

```java
public String authToken(String projectKeyId, String secretKey, String keyArray) throws Exception {
    String message = "ai="+projectKeyId+"&cs="+keyArray;
    Mac hmac = Mac.getInstance("HmacSHA256");
    hmac.init(new SecretKeySpec(secretKey.getBytes("UTF-8"), "HmacSHA256"));
    byte[] signature = hmac.doFinal(message.getBytes("UTF-8"));
    return Hex.encodeHexString(signature);
}
```

## 接口定义

#### URL

https://data.growingio.com/saas/{ai}/user

#### 请求类型

POST

#### 参数说明

{% tabs %}
{% tab title="请求参数" %}
| 请求头参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| Access-Token | string | 是 | Public Key，项目公钥 |

| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| ai | string | 是 | 项目ID |

| 查询参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| auth | string | 是 | 针对每条数据独立生成的认证，详细见本页面的获取认证码页签。 |

<table>
  <thead>
    <tr>
      <th style="text-align:left">body&#x53C2;&#x6570;</th>
      <th style="text-align:left">&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x662F;&#x5426;&#x5FC5;&#x4F20;</th>
      <th style="text-align:left">&#x8BF4;&#x660E;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">cs1</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x767B;&#x5F55;&#x7528;&#x6237;ID&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">cs2</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">
        <p>&#x7528;&#x6237;&#x5C5E;&#x6027;2&#x3002;</p>
        <p>&#x65E7;&#x7248;&#x672C;&#x4E0A;&#x4F20;&#x63A5;&#x53E3;&#x4F7F;&#x7528;cs1-cs20&#x7684;&#x5B57;&#x6BB5;&#x4E0A;&#x4F20;&#x7528;&#x6237;&#x5C5E;&#x6027;&#x3002;</p>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}
{% endtabs %}

