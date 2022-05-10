# 自定义数据上传API

## 设置登录**用户**ID

当用户登录之后，可以通过 `setUserId` 接口上报登录用户ID，用于在 GrowingIO 平台标记登录用户，后续可使用该登录用户ID分析这个登录用户的行为数据。

**接口定义**

```java
gio('setUserId', userId)
```

**参数说明**

| 名称     | 类型     | 是否必须 | 说明     |
| ------ | ------ | ---- | ------ |
| userId | string | 是    | 登录用户ID |

**示例代码**

```java
gio('setUserId', 'test_userId');
```

## 清除登录用户ID

当用户退出登录之后调用`clearUserId`，清除已经设置的登录用户ID。

```java
gio('clearUserId');
```

## 预置自定义事件

GrowingIO 预置了两个小程序的标准自定义事件：分享到群聊或好友信息和程序错误，接入SDK即可以使用。

**微信小程序分享到好友或群聊信息**

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LGNxeGABUADKiTWTaEM%2F-LH66a23TIvbEtQOPKyt%2F-LH675ymMloYtj1u3JVJ%2Fimage.png?alt=media\&token=025a5cfb-90eb-45ee-aa58-767c0380bae1)

**程序错误**

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LGNxeGABUADKiTWTaEM%2F-LH66a23TIvbEtQOPKyt%2F-LH67LAaMuVbR\_KxSYVc%2Fimage.png?alt=media\&token=0708739e-4cae-4315-b633-e9aeb2e25ca2)

## 设置访问用户变量

当用户未登录时，定义用户属性变量。在添加所需要发送的事件代码之前，需要在GrowingIO”**数据中心** > **数据管理** > **变量** > **用户变量**的访问用户变量页签下置用户变量。

**接口定义**

```java
gio('setVisitor', properties: object);
```

**参数说明**

| 名称         | 类型     | 是否必须 | 说明                |
| ---------- | ------ | ---- | ----------------- |
| properties | Object | 是    | 访问用户级变量，用户额外的信息参数 |

**代码示例**

{% hint style="warning" %}
变量value的数据类型需与【数据中心/数据管理】定义保持一致，否则上报数据将无法正确解析，导致数据丢失。
{% endhint %}

```java
// 假设初始化后把 gio 对象放在 App 的 globalData 里面
// 比如在针对不同的用户做某个 Campaign 的 A/B 测试
getApp().globalData.gio('setVisitor', { 
  campaign_id: 3, 
  campaign_group: 'A 组用户'
});
```

## 设置登录用户变量

发送登录用户的信息。在添加所需要发送的事件代码之前，需要在GrowingIO”**数据中心** > **数据管理** > **变量** > **用户变量**的登录用户变量页签下置用户变量。

**接口定义**

```java
gio('setUser', properties: object)
```

**参数说明**

| 名称         | 类型     | 是否必须 | 说明               |
| ---------- | ------ | ---- | ---------------- |
| properties | Object | 是    | 登录用户变量，用户额外的信息参数 |

**代码示例**

{% hint style="warning" %}
变量value的数据类型需与【数据中心/数据管理】定义保持一致，否则上报数据将无法正确解析，导致数据丢失。
{% endhint %}

```java
// 假设初始化后把 gio 对象放在 App 的 globalData 里面
getApp().globalData.gio('setUser', {
  age: 30, 
  level: '高级用户', 
  company: 'GrowingIO', 
  title: '工程师'
});
```

## 设置页面级变量

发送页面级别的信息。在添加所需要发送的事件代码之前，需要在GrowingIO”**数据中心** > **数据管理** > **变量** > **事件变量**的页面级变量页签下设置页面级变量。

**接口定义**

```java
gio('setPage', properties: object)
```

**参数说明**

| 名称         | 类型     | 是否必须 | 说明              |
| ---------- | ------ | ---- | --------------- |
| properties | Object | 是    | 页面级变量，页面额外的信息参数 |

**代码示例**

{% hint style="warning" %}
变量value的数据类型需与【数据中心/数据管理】定义保持一致，否则上报数据将无法正确解析，导致数据丢失。
{% endhint %}

```java
// 假设初始化后把 gio 对象放在 App 的 globalData 里面
// 推荐在 Page#onShow 处理这个事件
// 下面假设我在 GrowingIO 后台已经配置了两个页面级变量 pageName 和 type
Page({
  onShow() {
    getApp().globalData.gio('setPage', { 
      pageName: '电影列表页', 
      type: this.data.type
    });
  }
}
```

## 设置转化变量

发送一个转化变量用于高级归因分析。在添加所需要发送的事件代码之前，需要在GrowingIO”**数据中心** > **数据管理** > **变量** > **转化变量**下配置转化变量。

设置一个转化信息用于高级归因分析，目前支持归因方式有最初归因、最终归因和线性归因。

{% hint style="success" %}
举个例子，如果一个用户是先后通过`活动A`、`活动B`、`活动C`来访问小程序，最后在某次后续几天后的访问购买了某个商品。如果把活动A/B/C分别设置为转化变量`campaign`的值，那么：

* 最初归因：这个购买行为是由 A 贡献的；
* 最终归因：这次购买行为是 C 贡献的；
* 线性归因：这次购买行为是 A/B/C 各占 1/3 贡献。
{% endhint %}

**接口定义**

```java
gio('setEvar', properties: object)
```

**参数说明**

| 参数名称       | 类型     | 是否必须 | 说明         |
| ---------- | ------ | ---- | ---------- |
| properties | Object | 是    | 转化级变量和转化信息 |

**代码示例**

{% hint style="warning" %}
变量value的数据类型需与【数据中心/数据管理】定义保持一致，否则上报数据将无法正确解析，导致数据丢失。
{% endhint %}

```java
// 假设初始化后把 gio 对象放在 App 的 globalData 里面
getApp().globalData.gio('setEvar', { 
  campaign: '活动A'
});
```

## 设置埋点事件和事件级变量

手动发送一个自定义事件。在添加所需要发送的事件代码之前，需要在GrowingIO”**数据中心** > **数据管理** > **事件** > **埋点事件“**下配置埋点事件，在**变量** > **事件变量**下配置事件级变量。

**接口定义**

```java
gio('track', eventName: string, properties: object);
```

**参数说明**

| 名称         | 类型     | 是否必须 | 说明                      |
| ---------- | ------ | ---- | ----------------------- |
| eventName  | string | 是    | 事件标识符。                  |
| properties | Object | 否    | 事件级变量，即事件发生时所伴随的维度信息参数。 |

**代码示例**

{% hint style="warning" %}
变量value的数据类型需与【数据中心/数据管理】定义保持一致，否则上报数据将无法正确解析，导致数据丢失。
{% endhint %}

```java
// 假设初始化后把 gio 对象放在 App 的 globalData 里面
// 在 Page 的 clickBanner 函数里添加以下代码
Page({
  clickBanner(e) {
    getApp().globalData.gio('track', 'clickBanner', { 
      id: movie.id, 
      title: movie.title, 
      index: e.currentTarget.dataset.index 
    });
  }
})
```

## 设置位置信息

当用户访问至某一功能需要位置信息时，可以手动调用小程序Api获取地理位置接口，赋值给SDK，自动补发VISIT，采集位置信息，提升用户地域分布的分析准确性。同时您需要配置项目的`permission`字段[参考文档](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#permission)和对应的权限申请[参考文档](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.getLocation.html)。

_**2022年4月18日起，微信官方对****`getLocation`****进行了权限限制，因此SDK废弃了与getLocation有关的逻辑，并新增****`setLocation`****来代替此功能。**_

_****_

**接口定义**

```java
gio('setLocation', latitude, longitude); 
```

**参数说明**[**​**](https://growingio.github.io/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#%E5%8F%82%E6%95%B0%E8%AF%B4%E6%98%8E-3)

| 名称          | 类型       | 说明                         |
| ----------- | -------- | -------------------------- |
| `latitude`  | `number` | 必填；纬度，范围为 -90\~90，负数表示南纬   |
| `longitude` | `number` | 必填；经度，范围为 -180\~180，负数表示西经 |



**示例**[**​**](https://growingio.github.io/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#%E7%A4%BA%E4%BE%8B-5)

```
gio('setLocation', 30.23902949389956, 120.14519080902102);
// 调用后会自动补发带位置信息的vst事件  
```
