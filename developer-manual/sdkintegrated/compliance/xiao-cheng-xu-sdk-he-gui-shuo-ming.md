# 小程序 SDK 合规说明

请使用最新 GrowingIO 小程序SDK [稳定版本](../mini-program-sdk/3.7-ji-yi-xia/change-log.md) 及以上

## 收集的数据

按照 GDPR 的界定，GrowingIO 属于数据处理方，这是因为 GrowingIO 会按照客户的指示代表客户收集和处理数据。我们的客户则是数据控制方，他们拥有所有相关权利，可以使用接口随时控制是否开启数据收集和处理。

收集信息是为了您的网站向所有用户提供更好的服务。GrowingIO 小程序 SDK 将会收集小程序运行相关的环境信息，包括微信版本号，小程序场景值，设备信息，网络信息。使用 localstorage 来存储 SDK 自动生成的访问用户ID。采集的用户信息都是客户小程序需要请求用户授权的，譬如： openid，微信头像，昵称，定位。

## 合规步骤 <a href="#he-gui-bu-zhou" id="he-gui-bu-zhou"></a>

### 隐私保护指引 <a href="#yin-si-bao-hu-zhi-yin" id="yin-si-bao-hu-zhi-yin"></a>

请参考[微信小程序用户隐私保护](https://developers.weixin.qq.com/miniprogram/dev/framework/user-privacy/)

### GDPR <a href="#gdpr" id="gdpr"></a>

[​General Data Protection Regulation 欧盟通用数据保护条例](https://zh.wikipedia.org/wiki/%E6%AD%90%E7%9B%9F%E4%B8%80%E8%88%AC%E8%B3%87%E6%96%99%E4%BF%9D%E8%AD%B7%E8%A6%8F%E7%AF%84)​

GrowingIO 作为数据处理方，为符合 GDPR，小程序 SDK 提供设置接口，可在用户未同意隐私协议时，初始化时将`dataCollect`设置为 `false` ，禁止数据采集；\
在用户同意隐私协议后，调用`setDataCollect`设置为 `true`，开启数据采集。

{% hint style="info" %}
SDK版本>=3.7.3
{% endhint %}

```
​gio('init', ' GrowingIO 项目ID', '你的小程序AppID', {
  version: '1.0.0',
  dataCollect: false  
});

// 如果用户未同意隐私协议，弹出隐私协议弹框，用户同意隐私协议后，设置开启数据采集。
gio('setDataCollect', true);

// 如果同意隐私协议，设置开启数据采集。可写在 app.js 的 onshow 方法中
gio('setDataCollect', true);
```

## 常见问题 <a href="#chang-jian-wen-ti" id="chang-jian-wen-ti"></a>

### Q：dataCollect 设置 false 之后，发现事件数据不上报 <a href="#qdatacollect-she-zhi-false-zhi-hou-fa-xian-shi-jian-shu-ju-bu-shang-bao" id="qdatacollect-she-zhi-false-zhi-hou-fa-xian-shi-jian-shu-ju-bu-shang-bao"></a>

A：SDK关闭数据采集 dataCollect 设置 false 时，所有事件都不采集。只有开启了数据采集 dataCollect 为 ture 时，事件数据才会采集上报
