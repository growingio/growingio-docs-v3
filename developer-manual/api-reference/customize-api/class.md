# 维度分类上传

## 获取认证码

认证方式与用户属性上传类似，其中 keyArray 为 `variable_name` 的值，多条使用`逗号`分隔，如：1234,1235。 加密 Message 为 `ai=$projectId&$variable_name=$keyArray` （注意variable\_name为实际变量名称）。

{% code title="JAVA" %}
```java
public String authToken(String projectKeyId, String variableName, String secretKey, String keyArray) throws Exception {
    String message = "ai="+projectKeyId+"&"+variableName+"="+keyArray;
    Mac hmac = Mac.getInstance("HmacSHA256");
    hmac.init(new SecretKeySpec(secretKey.getBytes("UTF-8"), "HmacSHA256"));
    byte[] signature = hmac.doFinal(message.getBytes("UTF-8"));
    return Hex.encodeHexString(signature);
}
```
{% endcode %}

## 接口定义

#### URL

https://data.growingio.com/{ai}/classification/{variable\_name}

#### 请求类型

POST

{% tabs %}
{% tab title="请求参数" %}
| 请求头参数 | 类型 | 是否必传 | 说 |
| :--- | :--- | :--- | :--- |
| Access-Token | string | 是 | Public Key，项目公钥 |
| Content-Type | string | 是 | application/json |

| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| ai | string | 是 | 项目ID。 |
| variable\_name | string | 是 | 用户变量标识符。 |

| 查询参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| auth | string | 是 | 针对数据生成的认证，计算方式与上述类似。 |

| body名称 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| variable\_name | string | 是 | 在GrowingIO系统内定义的用户属性，且为需要分类用户变量的标识符（如companyId） |
| userProperty1 | string | 否 | 在GrowingIO系统内定义的用户属性（如companyName） |
| userProperty2 | string | 否 | 在GrowingIO系统内定义的用户属性（如companyClass） |

{% hint style="success" %}
body内的variable\_name、userProperty1-N为您在GrowingIO系统内定义的用户属性的key。类似用户属性上传，支持是用户组的方式一次性上传多条数据，一次性最多上传100条，body限制大小为2M。
{% endhint %}
{% endtab %}

{% tab title="返回示例" %}
200：OK
{% endtab %}
{% endtabs %}



