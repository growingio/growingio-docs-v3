# 维度分类上传

## 获取认证码

旧版本上传接口使用 cs1-cs20 的方式上传用户属性，对应的签名计算中 keyArray 为 参数 `cs2`的值，多条用`逗号`拼接，如：1234,1235。 加密 Message 为 `ai=$projectKeyId&cs=$keyArray`如 Java：

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

### URL

[https://data.growingio.com/saas/{ai}/company](https://data.growingio.com/saas/{ai}/company)

### 请求类型

POST

### 参数说明

{% tabs %}
{% tab title="请求参数" %}
| 请求头参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| Access-Token | string | 是 | Public Key，项目公钥。 |
| Content-Type | string | 是 | application/json |

| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| ai | string | 是 | 项目 ID。 |

| 查询参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| auth | string | 是 | 针对每条数据独立生成的认证 |

| body参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| cs2 | string | 是 | 用户属性2，且为需要分类用户变量的标识符。 |
| cs3 | string | 否 | 用户属性3。 |
| cs4 | string | 否 | 用户属性4. |
{% endtab %}
{% endtabs %}

