# 查询监测链接（增加App下载量-推广iOS或Android单个平台）

## URL

[https://www.growingio.com/api/v1/projects/{project\_uid}/meta/normallinks](https://www.growingio.com/api/v1/projects/{project_uid}/meta/normallinks)

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


<table>
  <thead>
    <tr>
      <th style="text-align:left">productId</th>
      <th style="text-align:left">String</th>
      <th style="text-align:left">
        <p>&#x4EA7;&#x54C1;ID</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;LPdgKARN</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table><table>
  <thead>
    <tr>
      <th style="text-align:left">appId</th>
      <th style="text-align:left">String</th>
      <th style="text-align:left">
        <p>app ID</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;com.demo.app.androidsdkdemo_android</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| trackingUrl | String | 监测链接 |
| :--- | :--- | :--- |


| redirectUrl | String | 跳转链接 |
| :--- | :--- | :--- |


| impressionUrl | String | 广告展示链接 |
| :--- | :--- | :--- |


| campaignId | String | iOS广告活动ID |
| :--- | :--- | :--- |


| campaignName | String | iOS广告活动名称 |
| :--- | :--- | :--- |


| channelId | String | 渠道ID |
| :--- | :--- | :--- |


| channelName | String | 渠道名称 |
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
</table><table>
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
</table>| params | String | 腾讯社交广告参数 |
| :--- | :--- | :--- |
{% endtab %}

{% tab title="响应示例" %}
```text
[
    {
        "id": "La9BwRne",
        "linkId": "r3A5LOd",
        "name": "测试链接二",
        "projectId": "4PYJMWoM",
        "productId": "LPdgKARN",
        "appId": "com.demo.app.androidsdkdemo_android",
        "trackingUrl":"https://datayi.cn/r3A5LOd",
        "redirectUrl": null,
        "impressionUrl": null,
        "campaignId": "d4PYjoME",
        "campaignName": "大夜宵活动",
        "channelId": "GQPDxPNm",
        "channelName": "多盟",
        "status": "activated",
        "creatorId": "nPNgQkoW",
        "creatorName": "fowindhe111",
        "updaterId": "nPNgQkoW",
        "updaterName": "fowindhe111",
        "createdAt": 1521642287367,
        "updatedAt": 1521642287367,
        "params": null
    }
]
```
{% endtab %}
{% endtabs %}

