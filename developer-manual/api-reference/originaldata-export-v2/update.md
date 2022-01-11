# 升级说明

## 升级方法

请联系客户成功经理进行原始数据导出API版本升级。

## 注意事项

如果您已经从1.0升级到了2.0，请注意如下事项：

* 从API2.0接口开通那一刻起，API1.0接口依旧可以继续使用，但是**`一个月`**之后就会失效，请您在过渡期内尽快升级您的使用代码。
* API2.0接口从开通的那一刻起就开始生效，比如您于`2018-08-01 10:30:00`升级到了API2.0接口，那么API2.0接口就可以下载`2018-08-01 11:00:00`之后的数据了，但是之前的数据还需要通过API1.0去获取。
* 在过渡期内，仍可以关闭API2.0接口，继续使用API1.0。过渡期结束后，无法降级。

## 新旧版本接口对比

{% tabs %}
{% tab title="URL" %}
2.0 接口格式：

```
https://www.growingio.com/v2/insights/{export_type}/{data_type}/{ai}/{export_date}.json
```

1.0 接口格式：

```
https://www.growingio.com/insights/{ai}/{date}.json
```
{% endtab %}

{% tab title="响应示例" %}
2.0 接口返回数据格式：

```
{
  "status”:"FINISHED",
  "downloadLinks":[
    "link1",
    "link2"
  ],
  "exportType":"",
  "dataType":"",
  "exportDate":"",
  "exportVersion":"",
  "requestTime":"",
  "errorMsg":""
}
```

1.0接口返回数据格式

```
{
  "status":"FINISHED",
  "downlinks":[
    "link1",
    "link2"
  ]
}
```
{% endtab %}

{% tab title="数据文件导出形式" %}
2.0 提供的事件类型：

visit、page、action、action\_tag、custom\_event（原custom\_attr）、ads\_track\_click、ads\_track\_activation、pvar（新增）、evar（新增）、vstr（新增）一共10种类型的事件

1.0 提供的数据类型：

visit、page、action、action\_tag、custom\_attr、ads\_track\_click、ads\_track\_activation一共7种类型的事件
{% endtab %}

{% tab title="数据格式" %}
数据格式变化请参考各个版本的字段说明章节。
{% endtab %}
{% endtabs %}
