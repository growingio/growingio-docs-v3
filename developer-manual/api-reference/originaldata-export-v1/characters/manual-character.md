# 埋点事件与变量字段

{% tabs %}
{% tab title="custom_attr" %}
| sendTime  | 发送时间   | bigint | 数据发送过来的时间      | ​示例                                                                                 |
| --------- | ------ | ------ | -------------- | ----------------------------------------------------------------------------------- |
| eventname | 埋点事件名称 | string | 用户定义的埋点事件名称    | 管理平台内定义                                                                             |
| attribute | 埋点事件属性 | string | 埋点事件属性为json字符串 | 以`_` 开头的字段为growingio相关定义字段，包括\_sessionId，\_userId，\_domain，\_eventTime等，其他为客户自定义的字段 |
{% endtab %}

{% tab title="custom_attr内attribute字段说明" %}
| 列名          | 字段名称         | 字段格式            | 字段说明                                                          | 值(example)                                    |
| ----------- | ------------ | --------------- | ------------------------------------------------------------- | --------------------------------------------- |
| \_userId    | 用户ID         | string(36)      | 针对单个用户生成的唯一id                                                 | 例如，web网站生成一个有效期三年的cookie值，mobile则为机器唯一标识码     |
| \_sessionId | 会话ID         | string(36)      | "web: 30分钟过期的session值，代表一次会话。mobile: app退出30秒后再进入，刷新session值" | ​                                             |
| \_eventTime | 事件发生时间       | bigint          | 事件实际发生的时间                                                     | ​                                             |
| \_domain    | 域名           | string(100)     | 用户访问的网站域名                                                     | www.growingio.com                             |
| \_path      | 路径           | string(512)     | 网站路径                                                          | /login                                        |
| \_query     | 访问事件的query信息 | string(512)     | 访问时的链接中的query，与前面的domain，path一起构建完整的链接                        | ​                                             |
| \_cs1       | 自定义用户信息字段1   | string(200)     | 客户平台的登陆用户id：cs1，如果客户安装sdk时设置过cs1字段（上传用户属性字段集cs，cs1用于设置用户id）   | cs1默认用于标记登陆用户ID， userid:12345                 |
| xxx         | 用户打点字段       | string / double | 客户自定义的打点字段，这部分字段最多有30个字段                                      | 所有自定义的打点字段，不同的事件有不同的定义，需要客户根据eventName自定义解析处理 |
{% endtab %}
{% endtabs %}
