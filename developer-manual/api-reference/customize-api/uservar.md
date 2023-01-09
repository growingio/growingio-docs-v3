# 登录用户变量上传

## 获取认证码

为防止误传和恶意攻击， GrowingIO 服务器会对收到的每条数据做校验，因此需要在查询参数中提供校验码。

校验码生成代码见下方示例，其中 keyArray 为 loginUserId，一次性上传多条时，使用逗号隔开，如接口定义示例中，第一条 keyArray 为 `1234`，第二条为 `1234,1235`。

{% code title="java" %}
```java
/**
 * projectKeyId: 项目ID
 * secretKey: 项目私钥
 * keyArray: loginUserId用逗号拼接的字符串
*/ 

javapublic String authToken(String projectKeyId, String secretKey, String keyArray) throws Exception {
    String message = "ai="+projectKeyId+"&loginUserId="+keyArray;
    Mac hmac = Mac.getInstance("HmacSHA256");
    hmac.init(new SecretKeySpec(secretKey.getBytes("UTF-8"), "HmacSHA256"));
    byte[] signature = hmac.doFinal(message.getBytes("UTF-8"));
    return Hex.encodeHexString(signature);
}
```
{% endcode %}

{% code title="Scala" %}
```java
/**
 * projectKeyId: 项目ID
 * secretKey: 项目私钥
 * keyArray: loginUserId用逗号拼接的字符串
*/ 

def authToken(projectKeyId: String, secretKey: String, keyArray: String): String = {
  val message = s"ai=$projectKeyId&loginUserId=$keyArray"
  val hmac: Mac = Mac.getInstance("HmacSHA256")
  hmac.init(new SecretKeySpec(secretKey.getBytes("UTF-8"), "HmacSHA256"))
  val signature = hmac.doFinal(message.getBytes("UTF-8"))
  Hex.encodeHexString(signature)
}
```
{% endcode %}

{% code title="python" %}
```java
/**
 * projectKeyId: 项目ID
 * secretKey: 项目私钥
 * keyArray: loginUserId用逗号拼接的字符串
*/ 

#coding:utf-8 
import hashlib
import hmac
​
def authToken(projectKeyId,secretKey,keyArray):
    message = ("ai=" + projectKeyId + "&loginUserId=" + keyArray).encode('utf-8')
    signature = hmac.new(bytes(secretKey.encode('utf-8')), bytes(message), digestmod=hashlib.sha256).hexdigest()
    return signature
```
{% endcode %}

{% code title="php" %}
```java
/**
 * projectKeyId: 项目ID
 * secretKey: 项目私钥
 * keyArray: loginUserId用逗号拼接的字符串
*/ 

function authToken($projectKeyId, $secretKey, $keyArray)
{
   $message="ai=".$projectKeyId."&loginUserId=".$keyArray;
   return hash_hmac('sha256',$message, $secretKey, false);
}
```
{% endcode %}

## 接口定义

### URL

`https://data.growingio.com/{ai}/loginUserId`

### 请求类型

POST

{% tabs %}
{% tab title="请求参数" %}
| 请求头参数        | 类型     | 是否必传 | 说明               |
| ------------ | ------ | ---- | ---------------- |
| Access-Token | string | 是    | Public Key，项目公钥  |
| Content-Type | string | 是    | application/json |

| 查询参数 | 类型     | 是否必传 | 说明                                     |
| ---- | ------ | ---- | -------------------------------------- |
| auth | string | 是    | 认证码，针对每条数据独立生成的认证。使用独立的认证码，详细见本页获取认证码。 |

| body参数        | 类型     | 是否必传 | 说明                                             |
| ------------- | ------ | ---- | ---------------------------------------------- |
| loginUserId   | string | 是    | 登录用户ID。                                        |
| userProperty1 | string | 否    | 在GrowingIO系统内定义的用户属性（如gender），长度不超过255个字符。     |
| userproperty2 | string | 否    | 在GrowingIO系统内定义的用户属性（如user\_name），长度不超过255个字符。 |

{% hint style="success" %}
**body内的userProperty1-N为您在GrowingIO系统内定义的用户属性的key，如gender、user\_name等。支持使用数组的方式一次上传多条数据（建议单次上报条数小于100条），body大小的最大限制为2M。**
{% endhint %}
{% endtab %}

{% tab title="body示例" %}
* 一次上传一条：

```java
{
    "loginUserId":"1234",
    "user_name":"张三",
    "gender":"男"
}
```

* 一次上传多条

```java
[
{
    "loginUserId":"1234",
    "user_name":"张三",
    "gender":"男"
},
{
    "loginUserId":"1235",
    "user_name":"李四",
    "gender":"女"
}
]
```
{% endtab %}
{% endtabs %}
