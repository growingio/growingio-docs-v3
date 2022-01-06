# 用户分群更新API

适用分群类型：CSV上传。

## URL

[https://www.growingio.com/v3/projects/{project\_uid}/user-warehouse/segmentations/{segmentation\_id}](https://www.growingio.com/v3/projects/%7Bproject\_uid%7D/user-warehouse/segmentations/%7Bsegmentation\_id%7D)

## 请求类型

PUT

## 请求头部

公共头部请参考[公共请求头参数](authenticate.md)。

## 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数             | 类型     | 是否必传 | 说明                                                              |
| ---------------- | ------ | ---- | --------------------------------------------------------------- |
| segmentation\_id | string | 是    | 用户分群ID，可使用[获取分群列表API](statistics-api/definition/get-segm.md)获取。 |

| body参数  | 类型     | 是否必传 | 说明                                                               |
| ------- | ------ | ---- | ---------------------------------------------------------------- |
| idtype  | string | 是    | <p>用户ID类型：<br>cs1：登录用户ID<br>openid：openid<br>unionid：unionid</p> |
| content | array  | 是    | 用户ID列表                                                           |


{% endtab %}

{% tab title="body示例" %}
```
{
  "idtype":"cs1",
  "content":[
          "1",
          "2"
  ]
}
```
{% endtab %}

{% tab title="响应示例" %}
```
// 更新成功
200：OK
"分群【xxx】更新成功。"

//更新失败  
400：Bad Request
{
    "message": "分群的类型和idtype不匹配",
    "errors": [
        {
            "code": "bad_request",
            "message": "错误访问"
        }
    ]
}
```
{% endtab %}
{% endtabs %}

