---
description: 在GrowingIO平台对用户变量进行声明和管理。
---

# 用户变量

在开始用户变量配置与定义之前，推荐您阅读[用户模型](https://growingio.gitbook.io/docs/introduction/datamodel/usermodel)文档，了解 GrowingIO 如何标记用户。

用户变量用来保存跟用户本身相关的信息。GrowingIO 支持设置登录用户和访客用户的用户属性信息。

不建议在登录用户变量中保存跟交互行为相关的信息，例如当前正在浏览的商品，当前正在查看的某一个SaaS项目。这些随着用户的交互行为会发生变化的信息，我们建议使用**页面级变量**和**转化变量**来保存。[  
](https://growingio.gitbook.io/docs/introduction/data-definition/uservar/loginuser)

{% page-ref page="../../../../introduction/data-definition/uservar/loginuser.md" %}

{% page-ref page="../../../../introduction/data-definition/uservar/visituesr.md" %}



