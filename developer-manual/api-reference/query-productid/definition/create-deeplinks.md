# 新建监测链接（吸引用户直接打开App）

### URL

https://www.growingio.com/api/v1/projects/{project\_uid}/meta/deeplinks

### 请求类型

POST

### 请求头参数

公共头部请参考[公共请求头参数](../../authenticate.md)。

### 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| project\_uid | string | 是 | 项目UID。 |

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
      <td style="text-align:left">name</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x76D1;&#x6D4B;&#x94FE;&#x63A5;&#x540D;&#x79F0;&#xFF0C;&#x957F;&#x5EA6;50&#x4E2A;&#x5B57;&#x7B26;&#x5185;&#xFF0C;&#x540C;&#x4E00;&#x4E2A;&#x8D26;&#x53F7;&#x4E0B;&#x7CFB;&#x7EDF;&#x4F1A;&#x8FDB;&#x884C;&#x94FE;&#x63A5;&#x7684;&#x540C;&#x540D;&#x6821;&#x9A8C;&#xFF0C;&#x8BF7;&#x52FF;&#x91CD;&#x590D;&#x63D0;&#x4EA4;&#x540C;&#x540D;&#x94FE;&#x63A5;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">productIdAndroid</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">
        <p>Android&#x4EA7;&#x54C1;ID&#x3002;</p>
        <p>&#x4ECE;<a href="https://app.gitbook.com/@help-1/s/doc/~/edit/drafts/-LpD4UbAD2BQKUq6Kf4L/untitled/api-can-kao/guang-gao-jian-ce-lian-jie-chuang-jian-fu-wu-api/jie-kou-ding-yi/cha-xun-ying-yong-id">&#x67E5;&#x8BE2;&#x5E94;&#x7528;ID</a>&#x83B7;&#x53D6;&#xFF0C;iOS&#x548C;Android&#x81F3;&#x5C11;&#x586B;&#x4E00;&#x4E2A;&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">productIdIos</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">
        <p>iOS&#x4EA7;&#x54C1;ID&#x3002;</p>
        <p>&#x4ECE;<a href="https://app.gitbook.com/@help-1/s/doc/~/edit/drafts/-LpD4UbAD2BQKUq6Kf4L/untitled/api-can-kao/guang-gao-jian-ce-lian-jie-chuang-jian-fu-wu-api/jie-kou-ding-yi/cha-xun-ying-yong-id">&#x67E5;&#x8BE2;&#x5E94;&#x7528;ID</a>&#x83B7;&#x53D6;&#xFF0C;iOS&#x548C;Android&#x81F3;&#x5C11;&#x586B;&#x4E00;&#x4E2A;&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">channelId</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x662F;</td>
      <td style="text-align:left">&#x6E20;&#x9053;ID&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">campaignIdIos</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">
        <p>Android&#x6D3B;&#x52A8;ID&#x3002;</p>
        <p>iOS&#x548C;Android&#x81F3;&#x5C11;&#x586B;&#x4E00;&#x4E2A;&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">campaignIdAndroid</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">
        <p>iOS&#x6D3B;&#x52A8;ID&#x3002;</p>
        <p>iOS&#x548C;Android&#x81F3;&#x5C11;&#x586B;&#x4E00;&#x4E2A;&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">downloadUrlIos</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">iOS&#x5E94;&#x7528;&#x4E0B;&#x8F7D;&#x5730;&#x5740;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">downloadUrlAndroid</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">Android&#x5E94;&#x7528;&#x4E0B;&#x8F7D;&#x5730;&#x5740;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">iosParams</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">
        <p>iOS&#x5524;&#x9192;&#x53C2;&#x6570;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;{&quot;uri&quot;:&quot;key1:value1&amp;key2:value2&quot;}</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">androidParams</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">&#x5426;</td>
      <td style="text-align:left">
        <p>Android&#x5524;&#x9192;&#x53C2;&#x6570;&#x3002;</p>
        <p>&#x793A;&#x4F8B;&#xFF1A;{&quot;uri&quot;:&quot;key1:value1&amp;key2:value2&quot;}</p>
      </td>
    </tr>
  </tbody>
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

