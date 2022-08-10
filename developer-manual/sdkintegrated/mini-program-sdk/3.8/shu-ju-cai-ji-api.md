# 数据采集API

通过 **`global.gio`** 这个全局的方法可以调用到SDK中所有开放的接口。

您可在页面头部进行解构获取**`gio`**方法。

**`const { gio } = global;（`**阿里(支付宝)小程序为 `const {`**`gio`**`} = $global;）`



## 动态修改配置接口(setOption)

由于多样的动态修改配置的需求，我们在`3.8.0`版本开始提供了统一的接口，以降低接口使用难度。设值成功返回true，设值失败返回false。

```javascript
gio('setOption', optionKey, optionValue);  // return true | false
```

### 1、开启/关闭无埋点数据采集(autotrack)

当加载了无埋点插件时，默认开启无埋点数据采集。当设置为 **`false`** 时，将不再采集 ** `clck` , `chng` , `sbmt`** 无埋点事件。未加载插件时无论 autotrack 是否开启都不会进行采集。

```javascript
gio('setOption', 'autotrack', true | false);

// <3.8.0版本的写法仍兼容，但不建议您再这么使用
// gio('setAutotrack', true | false);
```

### 2、开启/关闭数据采集(dataCollect)

默认开启数据采集。当设置为 **`false`** 时，SDK将不会采集和上报事件。由关闭修改为开启时，自动补发VISIT和当前页面的PAGE事件。

```javascript
gio('setOption', 'dataCollect', true | false);

// <3.8.0版本的写法仍兼容，但不建议您再这么使用
// gio('setDataCollect', true | false);
```

### 3、开启/关闭调试模式(debug)

默认不开启。当设置为 **`true`** 时，开启后会在开发者工具控制台输出日志。

```javascript
gio('setOption', 'debug', true | false);

// <3.8.0版本的写法仍兼容，但不建议您再这么使用
// gio('enableDebug', true | false);
```

### 4、修改请求协议(scheme)

默认为\*\*`https`\*\*，您可以在开发过程中设置为 `http` 方便与服务端进行调试。注意上生产环境前修改回 `https`。

```javascript
gio('setOption', 'scheme', 'http' | 'https');

// <3.8.0版本的写法仍兼容，但不建议您再这么使用
// gio('setTrackerScheme', 'http' | 'https');
```

## 功能接口

### 1、设置访问用户Id(identify)

访问用户Id，又称为匿名用户Id/设备Id，在微信小程序调用[登录开放接口](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/login/wx.login.html) `wx.login` 之后，获取 openId，调用 identify 设置访问用户Id。同时支持上报unionId以便进行用户分群，以及使用微信推送等高级功能。

**示例**

```javascript
gio('identify', openId[, unionId]);
```

**注意：若使用此接口需要在初始化时将 forceLogin 设置为 true。** [**参考文档**](chu-shi-hua-pei-zhi.md)****

### 2、获取访问用户Id(getDeviceId)

访问用户Id，又称为匿名用户Id/设备Id，SDK 自动生成用来定义唯一设备。如果没有初始化SDK 或者关闭采集开关可能返回值为空。

**示例**

```javascript
gio('getDeviceId');
```

**注意：**

**开启forceLogin的小程序无需调用此方法，因为您在identify的时候已经获取了openId做为访问用户Id。如果您一定要使用它，请在identify之后调用。**

### 3、设置登录用户Id(setUserId)

当用户登录之后调用`setUserId`，设置登录用户ID。

若您的小程序每次用户升级版本时无需重新登录的话，为防止用户本地缓存被清除导致的无法被识别为登录用户，建议在监测到用户为登录用户后即调用此方法。

**定义**

```javascript
gio('setUserId', userId: string/number);
```

**示例**

```javascript
gio('setUserId', '112333445');
```

### 4、清除登录用户Id(clearUserId)

当用户登出之后调用 `clearUserId`，清除已经设置的登录用户ID**。**

**示例**

```javascript
gio('clearUserId');
```

### 5、设置访问用户变量(setVisitor)

当用户未登录时，定义用户属性变量。作为用户行为数据分析工具，用户信息的完善会给后续的分析带来很大的帮助。在小程序中，微信用户属性是非常重要的设置，只有完善了微信用户属性信息，系统自带的微信访问用户变量（如下表）才可以在分析工具中使用，交互数据定义、数据校验功能才会方便通过用户微信相关的信息（微信姓名和头像）定位用户。在添加所需要发送的事件代码之前，需要在GrowingIO”**数据中心** > **数据管理** > **变量** > **用户变量**的访问用户变量页签下置用户变量。

系统自带的微信访问用户变量：

| 微信用户所在城市 |
| -------- |
| 微信用户所在省  |
| 微信用户所在国家 |
| 微信用户的性别  |

**定义**

```javascript
gio('setVisitor', properties: object);
```

**示例**

```java
gio('setVisitor', { 
  campaign_id: 3, 
  campaign_group: 'A 组用户'
});
```

### 6、设置登录用户变量(setUser)

发送登录用户的信息。在添加所需要发送的事件代码之前，需要在GrowingIO”**数据中心** > **数据管理** > **变量** > **用户变量**的登录用户变量页签下置用户变量。

**定义**

```javascript
gio('setUser', properties: object);
```

**示例**

```java
gio('setUser', {
  age: 30, 
  level: '高级用户', 
  company: 'GrowingIO', 
  title: '工程师'
});
```

### 7、设置页面级变量(setPage)

发送页面级别的信息。在添加所需要发送的事件代码之前，需要在GrowingIO”**数据中心** > **数据管理** > **变量** > **事件变量**的页面级变量页签下设置页面级变量。

**定义**

```javascript
gio('setPage', properties: object);
```

**示例**

```java
// 推荐在 Page#onShow 处理这个事件
Page({
  onShow() {
    gio('setPage', { 
      pageName: '电影列表页', 
      type: this.data.type
    });
  }
}
```

### 8、设置转化变量(setEvar)

发送一个转化变量用于高级归因分析。在添加所需要发送的事件代码之前，需要在GrowingIO”**数据中心** > **数据管理** > **变量** > **转化变量**下配置转化变量。

设置一个转化信息用于高级归因分析，目前支持归因方式有最初归因、最终归因和线性归因。

{% hint style="info" %}
举例：如果一个用户是先后通过`活动A`、`活动B`、`活动C`来访问小程序，最后在某次后续几天后的访问购买了某个商品。如果把活动A/B/C分别设置为转化变量`campaign`的值，那么：

* 最初归因：这个购买行为是由 A 贡献的；
* 最终归因：这次购买行为是 C 贡献的；
* 线性归因：这次购买行为是 A/B/C 各占 1/3 贡献。
{% endhint %}

**定义**

```javascript
gio('setEvar', properties: object);
```

**代码示例**

```java
gio('setEvar', { campaign: '活动A' });
```

### 9、设置埋点事件和事件级变量(track)

发送一个埋点事件。在添加所需要发送的事件代码之前，需要在平台中配置事件以及事件属性。埋点事件示例

**参数说明**

| 参数           | 参数类型     | 说明                                            |
| ------------ | -------- | --------------------------------------------- |
| `eventId`    | `String` | 必填；事件名，事件标识符。                                 |
| `properties` | `Object` | 选填；事件属性，当事件属性关联有维度表时，属性值为对应的维度表模型ID(记录ID)参数限制 |

**定义**

```javascript
gio('track', eventId, properties: object);
```

**示例**

```javascript
gio('track', 'order'); // 无properties
gio('track', 'order', {}); // 无properties
gio('track', 'order', { type: 'hjh' }); // 有properties
```

### 10、设置地理位置(setLocation)

当用户访问至某一功能需要位置信息时，可以手动调用小程序Api获取地理位置接口，赋值给SDK，自动补发 vst 事件，采集位置信息，提升用户地域分布的分析准确性。同时您需要配置项目的`permission`字段[参考文档](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#permission)和对应的权限申请[参考文档](https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.getLocation.html)。

_**2022年4月18日起，微信官方对****`getLocation`****进行了权限限制，因此SDK废弃了与getLocation有关的逻辑，并新增****`setLocation`****来代替此功能。**_

**参数说明**

| 参数          | 参数类型     | 说明                         |
| ----------- | -------- | -------------------------- |
| `latitude`  | `number` | 必填；纬度，范围为 -90\~90，负数表示南纬   |
| `longitude` | `number` | 必填；经度，范围为 -180\~180，负数表示西经 |

**示例**

```javascript
wx.getLocation({
  type: 'wgs84',
  success: ({ latitude, longitude }) => {
    gio('setLocation', latitude, longitude);
    // 调用后会自动补发带位置信息的VISIT事件
  }
});
```

### 11、与h5打通用户数据(getGioInfo)

当有H5页面需要获取小程序SDK采集用户数据的需求时(将H5页面采集的数据需要与小程序采集的数据做关联分析)，调用此接口可将获取以下数据。

```
giou              访问用户Id(deviceId)
gios              sessionId
giocs1            登录用户Id
gioid             最近的非空登录用户Id
gioprojectid      项目Id
gioappid          小程序appId
gioplatform       小程序平台
giodatacollect    小程序是否采集数据
```

**示例**

```javascript
gio('getGioInfo');
```

**注意：**\
**1）gio('getGioInfo') 返回的是一个 search 字符串，需要您在字符串前手动拼接 ? 或 & 符号。如果您将该字符串拼接在了hash参数中，请在内嵌页h5 sdk（>=2.1.8支持）中开启hashtag解析。**

**2）gio('getGioInfo') 获取的数据是一次性的，非动态获取，如果切换用户导致 sessionId 或 userId 等用户信息变动时，需要您销毁当前 webview 重设地址。并且使用不保留当前页面的跳转方式跳出承载 webview 的小程序页面。**

**示例**

```javascript
// js
Page({
  data: { url: '' },
  onShow() {
    // 每次onShow时设url的值，保证getGioInfo拿到的是最新值
    this.setData({ url: `https://www.growingIO.com?${gio('getGioInfo')}` });
  },
  onHide() {
    // 退出webview承载页时要销毁webview，保证下次进入时是一个拿到最新数据的全新页面
    this.setData({ url: '' });
  },
  // 如果页面中有登录，需要在登录之后重设一次url的值
  handleLogin() {
    ...
    // 登录完成后重设一次url的值，保证先销毁webview，getGioInfo拿到的是最新值
    this.setData({ url: '' }, () => {
      this.setData({ url: `https://www.growingIO.com?${gio('getGioInfo')}` });
    });
  }
})
```

```html
<!-- wxml -->
<view>
  <web-view wx:if="{{url}}" src="{{url}}"></web-view>
</view>
```

**`gio('getGioInfo')`默认获取到的数据示例：**

```javascript
// H5 页面原有的 URL为 :
'https://www.growingio.com/?foo=1#锚点'
```

```javascript
// 小程序WebView加载H5时的拼接示例为
`https://www.growingio.com/?foo=1&${gio('getGioInfo')}#锚点`
```

**H5页面集成SDK参考**[**小程序内嵌页H5SDK集成**](../../h5-sdk/)****

### 12、获取SDK当前配置(getOption)

当调试时需要获取SDK当前的配置信息状态时，可调用此接口。配置项名称不传时获取的为全量的配置信息。

**示例**

```javascript
gio('getOption', 配置项名称);

gio('getOption', 'dataCollect'); // 返回dataCollect当前在SDK中的值
gio('getOption'); // 返回所有支持查看的配置项值(即原来的vdsConfig对象)
```

### 13、获取SDK当前版本

在代码或开发者工具中直接调用 `global.gioSDKVersion` 即可获取。
