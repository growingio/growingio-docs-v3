---
description: auth是通过认证算法计算出来的加密签名。
---

# 生成加密签名auth

### auth计算示例代码

{% tabs %}
{% tab title="Java版本示例代码" %}
```java
public String authToken(String secret, String project, String ai, Long tm) throws Exception {
  String message = "POST\n/auth/token\nproject="+project+"&ai="+ai+"&tm="+tm;
  Mac hmac = Mac.getInstance("HmacSHA256");
  hmac.init(new SecretKeySpec(secret.getBytes("UTF-8"), "HmacSHA256"));
  byte[] signature = hmac.doFinal(message.getBytes("UTF-8"));
  return Hex.encodeHexString(signature);
}

authToken("这里是GrowingIO给项目分配的私钥", "项目UID", "项目ID", "申请时间戳")
```
{% endtab %}

{% tab title="Scala版本示例代码" %}
```scala
import javax.crypto.Mac
import javax.crypto.spec.SecretKeySpec
import org.apache.commons.codec.binary.Hex

def authToken(secret: String, project: String, ai: String, tm: Long) = {
 val messages = s"POST\n/auth/token\nproject=$project&ai=$ai&tm=$tm"
 val hmac = Mac.getInstance("HmacSHA256")
 hmac.init(new SecretKeySpec(secret.getBytes("UTF-8"), "HmacSHA256"))
 val signature = hmac.doFinal(messages.getBytes("UTF-8"))
 Hex.encodeHexString(signature)
}

authToken("这里是 GrowingIO 给项目分配的私钥", "项目UID", "项目ID", "申请时间戳")
```
{% endtab %}

{% tab title="PHP版本示例代码" %}
```php
<?php

function authToken($secret, $project, $ai, $tm) {
    $str = "POST\n/auth/token\nproject=${project}&ai=${ai}&tm=${tm}";
    $signature = hash_hmac("sha256", $str, $secret);
    return $signature;
}

authToken("这里是 GrowingIO 给项目分配的私钥", "项目UID", "项目ID", "申请时间戳")
?>
```
{% endtab %}

{% tab title="Python版本示例代码" %}
```python
import hashlib
import hmac

def authToken(secret, project, ai, tm):
  message = ("POST\n/auth/token\nproject=" + project + "&ai=" + ai + "&tm=" + tm).encode('utf-8')
  signature = hmac.new(bytes(secret.encode('utf-8')), bytes(message), digestmod=hashlib.sha256).hexdigest()
  return signature

authToken("这里是 GrowingIO 给项目分配的私钥", "项目UID", "项目ID", "申请时间戳")
```
{% endtab %}
{% endtabs %}



