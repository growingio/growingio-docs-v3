# 查询监测链接（吸引用户直接打开App）

## URL

[https://www.growingio.com/api/v1/projects/{project\_uid}/meta/deeplinks](https://www.growingio.com/api/v1/projects/{project_uid}/meta/deeplinks)

## 请求类型

GET

## 请求头参数

公共头部请参考[公共请求头参数](../../authenticate.md)。

## 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |
{% endtab %}

{% tab title="返回参数" %}
| 字段名 | 字段格式 | 说明 |
| :--- | :--- | :--- |


| id | String | 资源ID |
| :--- | :--- | :--- |


| linkId | String | 监测链接ID |
| :--- | :--- | :--- |


| name | String | 监测链接名称 |
| :--- | :--- | :--- |


| projectId | String | 项目UID |
| :--- | :--- | :--- |


| productIdIos | String | iOS产品ID |
| :--- | :--- | :--- |


| productNameIos | String | iOS产品名称 |
| :--- | :--- | :--- |


| productIdAndroid | String | Android产品ID |
| :--- | :--- | :--- |


| productNameAndroid | String | Android产品名称 |
| :--- | :--- | :--- |


| trackingUrl | String | 监测链接 |
| :--- | :--- | :--- |


| downloadUrlIos | String | iOS应用下载地址 |
| :--- | :--- | :--- |


| downloadUrlAndroid | String | Android应用下载地址 |
| :--- | :--- | :--- |


| urlSchemaIos | String | iOS URL Scheme？？？应用的urlscheme |
| :--- | :--- | :--- |


| urlSchemaAndroid | String | Android URL Scheme |
| :--- | :--- | :--- |


| campaignIdIos | String | iOS广告活动ID |
| :--- | :--- | :--- |


| campaignNameIos | String | iOS广告活动名称 |
| :--- | :--- | :--- |


| campaignIdAndroid | String | Android广告活动ID |
| :--- | :--- | :--- |


| campaignNameAndroid | String | Android广告活动名称 |
| :--- | :--- | :--- |


| iosParams | String | iOS唤醒参数 |
| :--- | :--- | :--- |


| androidParams | String | Android唤醒参数 |
| :--- | :--- | :--- |


| channelId | String | 推广渠道ID |
| :--- | :--- | :--- |


| channelName | String | 推广渠道名称 |
| :--- | :--- | :--- |


| status | String | 状态 |
| :--- | :--- | :--- |


| creatorId | String | 创建人ID |
| :--- | :--- | :--- |


| creatorName | String | 创建人名称 |
| :--- | :--- | :--- |


| updaterId | String | 最后更新人ID |
| :--- | :--- | :--- |


| updaterName | String | 最后更新人名称 |
| :--- | :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">createdAt</th>
      <th style="text-align:left">Long</th>
      <th style="text-align:left">
        <p>&#x521B;&#x5EFA;&#x65F6;&#x95F4;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1521642287367</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left">updatedAt</th>
      <th style="text-align:left">Long</th>
      <th style="text-align:left">
        <p>&#x66F4;&#x65B0;&#x65F6;&#x95F4;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;1521642287367</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>
{% endtab %}

{% tab title="响应示例" %}
```text
[
    {
        "id": "GQPDxPNm",
        "linkId": "dGVr8e9",
        "name": "321deeplink",
        "projectId": "4PYJMWoM",
        "productIdIos": "xRxVp0o5",
        "productNameIos": "TestAPP",
        "productIdAndroid": "LPdgKARN",
        "productNameAndroid": "Android SDK Demo",
        "trackingUrl": "https://datayi.cn/dGVr8e9",
        "downloadUrlIos": "http://baidu.com",
        "downloadUrlAndroid": "http://growingio.com",
        "urlSchemaIos": "c35abef955cd913a",
        "urlSchemaAndroid": "8137d31f4e7b819f",
        "campaignIdIos": "j9yB1nRy",
        "campaignNameIos": "321上线",
        "campaignIdAndroid": "xoga4DRm",
        "campaignNameAndroid": "321上线验证1",
        "iosParams": null,
        "androidParams": null,
        "channelId": "34RzeX9V",
        "channelName": "123测试编辑编辑",
        "status": "activated",
        "creatorId": "nRbm8d93",
        "creatorName": "xx",
        "updaterId": "nRbm8d93",
        "updaterName": "xx",
        "createdAt": 1521642287367,
        "updatedAt": 1521642287367
    }
]
```
{% endtab %}
{% endtabs %}

