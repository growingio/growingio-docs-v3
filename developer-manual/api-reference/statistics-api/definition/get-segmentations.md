# 获取特定分群的用户列表

### URL

https://www.growingio.com/projects/{project\_uid}/segmentations/{segmentation\_id}/users.csv

### 请求类型

GET

### 请求头参数

公共头部请参考[公共请求头参数](../../authenticate.md)。

### 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| segmentation\_id | string | 是 | 分群ID。 |
| project\_uid | string | 是 | 项目UID。 |
{% endtab %}

{% tab title="响应示例" %}
以Tab分割的csv文件格式，内容为上传用户的用户属性。

200: OK

```text
登录用户ID     登录用户变量1   
12249   GrowingIO
```

```text
访问用户ID       访问用户变量1  
12249   GrowingIO
```
{% endtab %}
{% endtabs %}

