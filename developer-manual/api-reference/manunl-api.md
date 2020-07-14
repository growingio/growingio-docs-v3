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

## 程序调试

GrowingIO建议您按照如下步骤进行埋点数据的开发联调

1. 在GrowingIO的网站中创建自定义事件以及对应的自定义事件变量。
2. 参考接口文档，编写一段程序上传一个事件，确保收到了200的HTTP状态
3. 在GrowingIO产品中使用您创建的埋点数据创建一个实时的图表
4. 如果可以在实时产品中看到您的埋点数据统计，则代表您的埋点创建成功

## 自动关联访问用户ID

自2020年4月22日起，所有通过服务端上传的埋点事件，GrowingIO将自动关联对应的访问用户ID。

关联规则如下：

* 服务端上传的埋点事件，会从该登录用户ID过去4个小时内的页面浏览事件中搜索对应的访问用户ID并与之关联。
* 如果过去4个小时内没有页面浏览事件，GrowingIO无法关联访问用户ID，从而该事件无法使用相关的维度进行分析（包括：位置维度、设备维度、访问用户变量等）

带来的好处：

* 服务端埋点事件可以用更多的维度进行分析
* 服务端埋点事件可以与其他事件一起出现在用户细查中（该功能目前还在测试，稍晚推出）
* 服务端埋点事件可以使用转化变量进行分析

## 常见问题

#### 1. 为什么在GrowingIO中无法看到我上报的数据？

答：因为服务器端埋点事件无法关联访问用户，所以需要将目标用户修改为“全部登录用户“才能看到数据

#### 2. 为什么使用**访问用户分析服务端埋点事件比登录用户少？** <a id="2-wei-shi-mo-shi-yong-fang-wen-yong-hu-fen-xi-fu-wu-duan-mai-dian-shi-jian-bi-deng-lu-yong-hu-shao"></a>

**答:** 如果服务端埋点事件发生前4个小时内该登录用户没有页面浏览事件，GrowingIO无法关联访问用户ID，从而无法使用访问用户去分析。出现这种现象的可能原因：

* 全部或部分服务端埋点事件是线下行为触发的
* 全部或部分服务端埋点事件上传时间距离客户行为超过了4个小时

