# 微信公众号集成-done

## 第一步：了解和检查你的小程序和公众号的信息 <a id="di-yi-bu-le-jie-he-jian-cha-ni-de-xiao-cheng-xu-he-gong-zhong-hao-de-xin-xi"></a>

**请确认小程序、公众号绑定微信开放平台，是否进行了企业认证，以及认证的企业主体。「重要，否则获取不到统一的微信用户 ID」。**

1. **公众号和小程序需要进行微信企业认证**
2. **公众号和小程序的认证主体需要保持一致**
3. **公众号、小程序需要进行微信开放平台的绑定**

微信仅支持企业信息认证的公众号进行第三方授权，所以 GrowingIO 进行公众号的分析，需要**公众号进行企业信息认证**；

### 查询微信企业认证 <a id="cha-xun-wei-xin-qi-ye-ren-zheng"></a>

进入微信公众号（服务号/订阅号）后台，右上角可以查看认证详情信息，如果没有认证，会显示”未认证“的字样。已认证

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LmIlvzi0Cu7jSExGzBj-LmIymK3VO-vkRl13bWvimage.png)

如果公众号还没有认证，请参考[腾讯帮助文档](https://kf.qq.com/faq/161220Brem2Q161220uUjERB.html)，进行企业认证，**同时请和其他微信应用（小程序、服务号、订阅号等）认证为一个企业主体，这样确保获取的 unionid 是一致的。**

### 查询认证的主体信息 <a id="cha-xun-ren-zheng-de-zhu-ti-xin-xi"></a>

如果公众号已认证，请在微信公众号后台「公众号设置」-「账号详情」查看主体情况；如果小程序已认证，请在微信小程序后台「设置」-「基本设置」中查看主体情况。

### 查询公众号、小程序是否绑定微信开放平台 <a id="cha-xun-gong-zhong-hao-xiao-cheng-xu-yuan-shi-fou-bang-ding-wei-xin-kai-fang-ping-tai"></a>

微信订阅号和服务号，如果想要获取统一的 unionid，需要进行**微信开放平台**的绑定，同时为了保证主体统一的小程序也获取到统一的 unionid，也请进行开放凭平台的绑定。

绑定步骤：

1. 登录\|注册微信开放平台：[https://open.weixin.qq.com](https://open.weixin.qq.com/)​
2. 进入「管理中心」，点击“公众账号”，点击“绑定公众号”、“绑定小程序”，按照步骤进行公众账号的绑定（公众号和小程序的管理员有绑定权限）。

微信开放平台后台页面

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Lmn5ePx-4cqahcZrnBG-LmnAuB8c3DDI13JqVukimage.png)

## **第二步：将小程序/微信内嵌页的 openid 和 unionid 上报到 GrowingIO** <a id="di-er-bu-jiang-xiao-cheng-xu-wei-xin-nei-qian-ye-de-openid-he-unionid-shang-bao-dao-growingio"></a>

如果您即将集成小程序或者内嵌页，请参照以下文档，确认小程序/微信内嵌页的 openid 和 unionid 在SDK 中已上报。

* ​[微信小程序SDK 上报微信 OpenID、UnionID](../../../kai-fa-zhe-wen-dang/sdkintegrated/other-sdk/minp-sdk.md#4-wei-xin-yong-hu-xin-xi-de-pei-zhi)；
* ​[内嵌页 SDK 上报微信 OpenID、UnionID](../../../kai-fa-zhe-wen-dang/sdkintegrated/other-sdk/h5-sdk.md#wei-xin-yong-hu-xin-xi-de-pei-zhi)；​

如果您项目中已经集成了 GrowingIO 小程序或者微信内嵌页应用，请麻烦工程师参照文档检查一下是否上报了微信 openid 和 unionid；或者可以在「用户分析」- 「用户细查」列表中查看是否有 openid 、unionid上报。测试数据示例

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LmIlvzi0Cu7jSExGzBj-LmJ7RQQVigjBEvb3BXwimage.png)

## **第三步：授权公众号数据集成到 GrowingIO** <a id="di-san-bu-shou-quan-gong-zhong-hao-shu-ju-ji-cheng-dao-growingio"></a>

在「数据中心」-「公众号数据集成」下，进行公众号的授权。示例

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LmIlvzi0Cu7jSExGzBj-LmJ7xq5Eal5zaOja54Vimage.png)

点击「去授权」，会直接跳转到微信公众平台；请**公众号的管理员**扫码授权后，展示授权成功，跳转回 GrowingIO。

完成集成后，等待一段时间（一般是1~2个小时左右）即可进行[微信应用用户分析](../../yong-hu-ku/scenario/wx-user.md)。

