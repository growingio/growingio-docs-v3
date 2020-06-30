# 删除原始数据

为符合 GDPR 规范，GrowingIO 提供删除用户原始数据的功能。

{% hint style="info" %}
* visitUserId 是 GrowingIO SDK 生成的 cookie，您可以从导出的原始数据中获得。
* 删除用户数据后，该部分用户的细节数据\(包括用户细查数据、以该部分用户ID做数据查询\) 都不会保留在GrowingIO平台；但汇总数据（比如 "访问用户量" ）不会受影响。
* 汇总数据不受影响的原因：GrowingIO收到该用户数据后启动汇总数据计算，这个过程是不可逆的。删除用户数据请求是在用户数据发送至GrowingIO之后的操作，该请求不会影响前置的汇总数据计算。请您知晓，汇总数据不受影响跟GDPR的要求没有任何相悖。
{% endhint %}

## 获取认证码

为防止误传和恶意攻击，GrowingIO服务器会对收到的每条数据做校验，因此需要在query参数中提供校验码auth。校验码生成代码见下方示例，其中的keyArray 为visitUserId，一次性上传多条时，使用逗号隔开，如上方示例中，keyArray为`abcdef,bcdefg`

{% code title="Java" %}
```java
public String authToken(String projectKeyId, String secretKey, String keyArray) throws Exception {
    String message = "projectId="+projectKeyId+"&visitUserId="+keyArray;
    Mac hmac = Mac.getInstance("HmacSHA256");
    hmac.init(new SecretKeySpec(secretKey.getBytes("UTF-8"), "HmacSHA256"));
    byte[] signature = hmac.doFinal(message.getBytes("UTF-8"));
    return Hex.encodeHexString(signature);
}
```
{% endcode %}

## 接口定义

删除用户原始数据。

### URL

`https://data.growingio.com/{ai}/deleteVisitor?auth={auth_token}`

### 请求类型

POST

### 参数说明

{% tabs %}
{% tab title="参数说明" %}
| 请求头参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| Access-Token | string | 是 | Public Key，项目公钥 |
| Content-Type | string | 否 | application/json |

| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| ai | string | 是 | 项目ID。 |

| 查询参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| auth | string | 是 | 针对每条数据独立生成的认证。参考[获取验证码](../customize-api/uservar.md#huo-qu-ren-zheng-ma) |

| body参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| visitUserId | array | 是 | 用户ID。 |
{% endtab %}

{% tab title="body示例" %}
```text
{
  "visitUserId":["abcdef","bcdefg",...]
}
```
{% endtab %}
{% endtabs %}

