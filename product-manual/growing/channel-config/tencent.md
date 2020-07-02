# 腾讯社交广告（Marking API）

#### 一、广告归因与数据展示

1、在 GrowingIO 后台，创建“腾讯社交广告”监测链接，并绑定广点通账号，并进行相应的授权；‌

2、GroiwngIO 实时将激活数据发送给广点通，广点通返回激活信息，点击时间，广告名称等信息；‌

3、GrowingIO 会根据用户的广告点击数据与激活数据做归因匹配，并将归因的结果展示在 GrowingIO 后台数据中。‌

#### **二、创建监测链接与媒体授权**

1、在GIO后台创建 App 推广链接，目标渠道选择“腾讯社交广告”，然后点击保存‌

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Lh-LJ8frL-7XyOyxJWE-Lh-LLVBJKkv4I6N-HAkimage.png)

2、点击保存后进入绑定与授权，‌

1）投放账号：填写对应的腾讯社交广告后台的登录账号（QQ号）。‌

2）投放账号ID：填写对应的腾讯社交广后台的账户ID，然后点击授权。‌

3）应用ID：填写您选取应用的对应ID，示例：iOS填写Appstore地址上面的数字。‌

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Lh-LJ8frL-7XyOyxJWE-Lh-LYG98PX0r-O1DfyMimage.png)

其中，“投放账号”和“投放账号ID”，与广点通后台相对应。‌

获取方式如下：‌

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LRQkXUuEuD5xER41iwA-LRQsE1caJLiZwqN5Z1Himage.png)

应用标识，请与广点通后台填写的“应用宝ID”或“苹果商店ID”保持一致。‌

* 图示为苹果商店ID获取方式。

‌

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LRQkXUuEuD5xER41iwA-LRQkdwds05hJHuw19rZimage.png)

3、点击授权之后再这里进行同意授权，授权成功后，在GIO后台获取监测链接‌

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LRQkXUuEuD5xER41iwA-LRQkcMxpIjuQnlj6LnPimage.png)

#### **三、转化回传联调**

1、进入腾讯广告 DMP 数据管理平台，找到以下入口![](blob:https://growingio.atlassian.net/d509f1de-cd04-4468-a2c3-c534ab4d925f#media-blob-url=true&id=8a9d65ca-6610-4e62-9598-61db53abf99b&collection=contentId-1350140247&contextId=1350140247&mimeType=image%2Fpng&name=image-20200526-090500.png&size=61589&width=1009&height=182)

![](../../../.gitbook/assets/image%20%28102%29.png)

2、找到需要联调的应用

![](blob:https://growingio.atlassian.net/f71957e3-1501-42a1-b1da-c7061c73ec9f#media-blob-url=true&id=780c972c-f9ba-4dd4-895a-5b1feeadaf01&collection=contentId-1350140247&contextId=1350140247&mimeType=image%2Fpng&name=image-20200526-090720.png&size=53700&width=933&height=274)

![](../../../.gitbook/assets/image%20%2898%29.png)

3、找到联调功能入口![](blob:https://growingio.atlassian.net/a7fc8d99-82fb-4dd2-bfa4-76c9194dcce7#media-blob-url=true&id=1489f277-74d6-4af5-8844-486a7726ce80&collection=contentId-1350140247&contextId=1350140247&mimeType=image%2Fpng&name=image-20200526-091011.png&size=94672&width=1542&height=301)

![](../../../.gitbook/assets/image%20%28103%29.png)

4、选择要联调的行为和渠道包![](blob:https://growingio.atlassian.net/99671bfd-8b48-44c2-a9b1-f6d690f21355#media-blob-url=true&id=34224b94-311e-42bc-8808-77c17dc77413&collection=contentId-1350140247&contextId=1350140247&mimeType=image%2Fpng&name=image-20200526-091052.png&size=30714&width=605&height=391)

![](../../../.gitbook/assets/image%20%28104%29.png)

5、进入联调流程按步骤进行操作![](blob:https://growingio.atlassian.net/4dfb4440-3ddd-4247-82f0-a8f01b819ce6#media-blob-url=true&id=a3cbc210-9c7c-4c85-9e20-73f974dd4e59&collection=contentId-1350140247&contextId=1350140247&mimeType=image%2Fpng&name=image-20200526-091212.png&size=158029&width=788&height=764)

![](../../../.gitbook/assets/image%20%28107%29.png)

#### 附录

腾讯联调工具帮助文档：

[https://e.qq.com/ads/adfaq/delivery/special/17/](https://e.qq.com/ads/adfaq/delivery/special/17/)  


\*\*\*\*

