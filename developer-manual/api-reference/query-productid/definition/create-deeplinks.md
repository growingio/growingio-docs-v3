# 新建监测链接（吸引用户直接打开App）

## URL

[https://www.growingio.com/api/v1/projects/{project\_uid}/meta/deeplinks](https://www.growingio.com/api/v1/projects/{project_uid}/meta/deeplinks)

## 请求类型

POST

## 请求头参数

公共头部请参考[公共请求头参数](../../authenticate.md)。

## 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |

| body参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |


| name | string | 是 | 监测链接名称，长度50个字符内，同一个账号下系统会进行链接的同名校验，请勿重复提交同名链接。 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">productIdAndroid</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>Android&#x4EA7;&#x54C1;ID&#x3002;</p>
        <p>&#x4ECE;<a href="https://app.gitbook.com/@help-1/s/doc/~/edit/drafts/-LpD4UbAD2BQKUq6Kf4L/untitled/api-can-kao/guang-gao-jian-ce-lian-jie-chuang-jian-fu-wu-api/jie-kou-ding-yi/cha-xun-ying-yong-id">&#x67E5;&#x8BE2;&#x5E94;&#x7528;ID</a>&#x83B7;&#x53D6;&#xFF0C;iOS&#x548C;Android&#x81F3;&#x5C11;&#x586B;&#x4E00;&#x4E2A;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">productIdIos</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>iOS&#x4EA7;&#x54C1;ID&#x3002;</p>
        <p>&#x4ECE;<a href="https://app.gitbook.com/@help-1/s/doc/~/edit/drafts/-LpD4UbAD2BQKUq6Kf4L/untitled/api-can-kao/guang-gao-jian-ce-lian-jie-chuang-jian-fu-wu-api/jie-kou-ding-yi/cha-xun-ying-yong-id">&#x67E5;&#x8BE2;&#x5E94;&#x7528;ID</a>&#x83B7;&#x53D6;&#xFF0C;iOS&#x548C;Android&#x81F3;&#x5C11;&#x586B;&#x4E00;&#x4E2A;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| channelId | string | 是 | 渠道ID。 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">campaignIdIos</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>Android&#x6D3B;&#x52A8;ID&#x3002;</p>
        <p>iOS&#x548C;Android&#x81F3;&#x5C11;&#x586B;&#x4E00;&#x4E2A;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">campaignIdAndroid</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>iOS&#x6D3B;&#x52A8;ID&#x3002;</p>
        <p>iOS&#x548C;Android&#x81F3;&#x5C11;&#x586B;&#x4E00;&#x4E2A;&#x3002;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| downloadUrlIos | string | 否 | iOS应用下载地址。 |
| :--- | :--- | :--- | :--- |


| downloadUrlAndroid | string | 否 | Android应用下载地址。 |
| :--- | :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">iosParams</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>iOS&#x5524;&#x9192;&#x53C2;&#x6570;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;{&quot;uri&quot;:&quot;key1:value1&amp;key2:value2&quot;}</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">androidParams</th>
      <th style="text-align:left">string</th>
      <th style="text-align:left">&#x5426;</th>
      <th style="text-align:left">
        <p>Android&#x5524;&#x9192;&#x53C2;&#x6570;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;{&quot;uri&quot;:&quot;key1:value1&amp;key2:value2&quot;}</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="返回参数" %}
| 名称 | 类型 | 说明 |
| :--- | :--- | :--- |
| linkId | string | 监测链接ID |
| id | string | 资源ID。 |
| name | string | 监测链接名称 |
| trackingUrl | string | 监测链接 |
| productIdAndroid | string | Android 产品ID |
| productNameAndroid | string | 应用名称 |
| productIdIos | string | iOS 产品ID |
| productNameIos | string | 应用名称 |
| channelId | string | 渠道ID |
| channelName | string | 渠道名称 |
| campaignIdIos | string | iOS 推广活动ID |
| campaignIdAndroid | string | Android 推广活动ID |
| campaignNameIos | string | iOS 应用所属推广活动名称 |
| campaignNameAndroid | string | Android 应用所属推广活动名称 |
| downloadUrlIos | string | iOS下载链接 |
| downloadUrlAndroid | string | Android下载链接 |
| iosParams | string | iOS 唤醒参数 |
| androidParams | string | Android 唤醒参数 |
| urlSchemaIos | string | iOS URL Schema |
| urlSchemaAndroid | string | Android URL Scheme |
| status | string | 状态 |
| creatorId | string | 创建人ID |
| creatorName | string | 创建人名称 |
| updaterId | string | 最后更新人ID |
| updaterName | string | 最后更新人名称 |
| createdAt | long | 创建时间 |
| updatedAt | long | 更新时间 |
{% endtab %}

{% tab title="body示例" %}
```text
{
        "name": "0523信息流推广",
        "productIdIos": "rREJ88PL",
        "channelId": "d4PY3M9M",
        "campaignIdIos": "4RzMvWd9",
        "downloadUrlIos": "http://www.growingio.com"
}
```
{% endtab %}

{% tab title="响应示例" %}
```text
{
    "id": "LlPQka9p",
    "linkId": "d0B4MKe",
    "name": "0523信息流推广",
    "projectId": "4PYJMWoM",
    "productIdIos": "rREJ88PL",
    "productNameIos": "RnTestiOS",
    "productIdAndroid": null,
    "productNameAndroid": null,
    "trackingUrl": "https://datayi.cn/d0B4MKe",
    "downloadUrlIos": "http://www.growingio.com",
    "downloadUrlAndroid": null,
    "urlSchemaIos": "80310c35a53c9a45",
    "urlSchemaAndroid": null,
    "campaignIdIos": "4RzMvWd9",
    "campaignNameIos": "测试活动_ch",
    "campaignIdAndroid": null,
    "campaignNameAndroid": null,
    "iosParams": null,
    "androidParams": null,
    "channelId": "d4PY3M9M",
    "channelName": "打点",
    "status": "activated",
    "creatorId": "AwoVvo28",
    "creatorName": "系统",
    "updaterId": "AwoVvo28",
    "updaterName": "系统",
    "createdAt": 1566186819563,
    "updatedAt": 1566186819563
}
```
{% endtab %}
{% endtabs %}

