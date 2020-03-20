---
description: 调用此接口，获取到的code字段值即为认证码。此认证码将作为其他业务接口的请求头参数。
---

# 申请认证码Authorization

{% hint style="success" %}
认证码使用说明：

* 获取新认证码后旧码失效。
* 认证码使用期限为自生成起30天，为防止多人使用出现的认证错误，建议每次使用都重新生成。（除接口存在并发请求的情况）
{% endhint %}

#### 请求类型

POST

#### URL

https://www.growingio.com/auth/token

{% tabs %}
{% tab title="请求参数" %}
{% hint style="info" %}
Post body 采用 raw 格式上传而不是 key-value 键值对方式上传。如：project=123abc&ai=2a1b4018cd954ec2bcc69da5138bdb96&tm=1465020309123&auth=ab3i5dazoo58314l0qqrj1aslfj1ldfaqeroqi
{% endhint %}

请求头参数如下：

| 名称 | 类型 | 是否必传 | 描述 |
| :--- | :--- | :--- | :--- |
| X-Client-Id | String | 是 | GrowingIO为各项目分配的公钥，请求时用来做身份校验的一串字符码。 |

请求body参数如下：

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x540D;&#x79F0;</th>
      <th style="text-align:left">&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x662F;&#x5426;&#x5FC5;&#x4F20;</th>
      <th style="text-align:left">&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">ai</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">GrowingIO&#x4E2D;&#x7684;&#x9879;&#x76EE;ID&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">project</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">
        <p>&#x9879;&#x76EE;UID&#x3002;</p>
        <p>&#x5728;GrowingIO&#x4E2D;&#x6253;&#x5F00;&#x9879;&#x76EE;&#xFF0C;&#x6D4F;&#x89C8;&#x5668;URL&#x4E2D;project&#x5B57;&#x6BB5;&#x540E;&#x7684;&#x503C;&#xFF0C;&#x5373;&#x4E3A;UID&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">tm</td>
      <td style="text-align:left">Long</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x7533;&#x8BF7;&#x65F6;&#x95F4;&#x6233;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">auth</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x901A;&#x8FC7;&#x8BA4;&#x8BC1;&#x7B97;&#x6CD5;&#x8BA1;&#x7B97;&#x51FA;&#x6765;&#x7684;&#x52A0;&#x5BC6;&#x7B7E;&#x540D;&#x3002;&#x83B7;&#x53D6;&#x65B9;&#x5F0F;&#x8BF7;&#x53C2;&#x8003;&#xFF1A;
        <a
        href="getauth.md">&#x83B7;&#x53D6;&#x52A0;&#x5BC6;&#x7B7E;&#x540D;auth</a>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="返回示例" %}
```text
  {
     "status":"success",
     "code":"2RhY0XZ9xyBfayAPm0aa5CoJhDJkEUcmRiBJBT6XyeIXhHrdz334Tf3I85Esm74Q"
   }
```

{% hint style="success" %}
code字段值即为认证码。
{% endhint %}
{% endtab %}
{% endtabs %}



