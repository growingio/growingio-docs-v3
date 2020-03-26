# 埋点数据上传API

### url

[https://api.growingio.com/v3/{ai}/s2s/cstm?stm={sendingTime}](https://api.growingio.com/v3/{ai}/s2s/cstm?stm={sendingTime})

### 请求类型

POST

### 参数说明与示例

{% tabs %}
{% tab title="请求参数" %}
| 路径参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| ai | string | 是 | 项目ID。 |
| sendingTime | string | 是 | 发送时间时间戳（毫秒） |

| body参数 | 类型 | 是否必传 | 说明 |
| :--- | :--- | :--- | :--- |
| cs1 | string | 是 | 用户登录ID。 |
| tm | double | 是 | 事件发生时间时间戳（毫秒）。 |
| n | string | 是 | 事件标识。 |
| var | map{key:value} | 否 | 所有的自定义事件变量。 |
| t | string | 是 | 事件类型，此处固定为cstm。 |
{% endtab %}

{% tab title="body示例" %}
单条事件发送

```text
[      
  {            
    "cs1":"9128391",    
    "tm":1434556935000,    
    "t":"cstm",    
    "n":"BuyProduct",    
    "var":{      
      "product_name":"苹果",      
      "product_classify":"水果",      
      "product_price":14    
    }
  }
]
```

多条事件发送

```text
[      
  {            
    "cs1":"9128391",    
    "tm":1434556935000,    
    "t":"cstm",    
    "n":"BuyProduct",    
    "var":{      
      "product_name":"苹果",      
      "product_classify":"水果",      
      "product_price":14    
    }
  },   
  {            
    "cs1":"9128391",    
    "tm":1434556935000,    
    "t":"cstm",    
    "n":"BuyProduct",    
    "var":{      
      "product_name":"苹果",      
      "product_classify":"水果",      
      "product_price":14    
    }
  },   
  {            
    "cs1":"9128391",    
    "tm":1434556935000,    
    "t":"cstm",    
    "n":"BuyProduct",    
    "var":{      
      "product_name":"苹果",      
      "product_classify":"水果",      
      "product_price":14    
    }
  }
]
```
{% endtab %}
{% endtabs %}

## 程序调试 <a id="cheng-xu-tiao-shi"></a>

GrowingIO建议您按照如下步骤进行埋点数据的开发联调

1. 在GrowingIO的网站中创建自定义事件以及对应的自定义事件变量。
2. 参考接口文档，编写一段程序上传一个事件，确保收到了200的HTTP状态
3. 在GrowingIO产品中使用您创建的埋点数据创建一个实时的图表
4. 如果可以在实时产品中看到您的埋点数据统计，则代表您的埋点创建成功

## 常见问题

#### 1. 为什么在GrowingIO中无法看到我上报的数据？

答：因为服务器端埋点事件无法关联访问用户，所以需要将目标用户修改为“全部登录用户“才能看到数据

