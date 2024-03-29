# 用户标签 - Beta

{% hint style="warning" %}
灰度beta功能 ，如需体验试用，请联系客户经理 。
{% endhint %}

## 简介

标签是用户行为和特征的抽象与描述。

目的為： 使大量业务价值低的数据 转变 :arrow\_right: 为更有价值的业务信息 。

在特定业务场景下，标签可以让我们快速的了解**`一个用户`**或**`一群用户`**的特征。

{% hint style="info" %}
举例：

如在电销场景下，我们的客服人员需要了解目标用户的性别、年龄、常住城市、家庭成员数量、历史购买记录、最近浏览偏好等标签信息。这些信息可以帮助客服人员在脑海中快速形成一个鲜活的人物形象，帮助客服人员在与客户的交谈中更好的组织语言、挖掘并满足客户需求。&#x20;
{% endhint %}



## 基础概念

按照`业务特征`划分，标签可以分为人口属性标签、交易属性标签、兴趣偏好标签等。

按照`创建方式`划分，标签可以分为属性标签、计算标签、分层标签和算法标签。

| 标签分类   | 描述                                      | 特点                               | 举例                                                         |
| ------ | --------------------------------------- | -------------------------------- | ---------------------------------------------------------- |
| 属性标签   | <p>根据企业沉淀的用户信息，</p><p>加工转换生成</p>        | 数量少、业务信息大                        | <p>根据身份证号生成标签。如</p><p>年龄、性别、是否是生日、</p><p>出生省市等</p>         |
| 计算标签   | 根据用户的行为和特征计算生成                          | 数量多、业务信息小                        | <p>根据购买事件计算生成</p><p>最近购买距今天数(R)、</p><p>购买次数(F)、购买金额(M)</p> |
| 规则标签   | <p>根据业务经验，</p><p>人工或半人工通过规则计算生成</p>     | <p>人力成本高、数量少、</p><p>业务信息大</p>    | <p>根据RFM计算标签按业务</p><p>需求根据规则讲用户进行</p><p>分层</p>             |
| 算法标签   | <p>大部分依赖算法计算，</p><p>需要人工参与调参和业务效果验证</p> | <p>计算成本高、数量多、</p><p>业务效果需要验证</p> | <p>根据用户特征和行为</p><p>预测用户购买意向</p>                            |



标签可以帮助我们更加全面的描述一个用户，使业务人员能够前所未有的 看清用户。

但这并不意味着标签需要越多越好。出于计算成本和管理成本考量，我们应结合业务场景和业务需求，考虑什么样的标签能在业务操作中帮助我们更好的完成业务目标，并依据此目标进行标签的创建。

{% hint style="info" %}
根据GrowingIO 的行业经验 ：\
許多人_**错误的**_ 的认为跟踪更多、更丰富的标签有助于更好地了解客户。通常情况下，数据丰富，但洞察力较差。

一些细分市场最成功的客户仅限于跟踪少数重要数据，以帮助他们回答同样重要的业务问题。\
企业内部的标签体系往往有上百上千个，但对业务产生要效益的标签往往约10% 。
{% endhint %}

{% hint style="success" %}
目前GrowingIO提供了4种标签计算模型，

分别为

* 累计值/平均值/占比标签
* 最大值/最小值的事件属性标签
* 最初/最终的事件属性标签
* 分层标签

这4种标签主要用于解决 `计算标签`和`规则标签`的使用场景。
{% endhint %}





