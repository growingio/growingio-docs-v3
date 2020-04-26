# QQ小程序SDK

## 准备条件

获取项目ID，获取方法请参考"项目管理 &gt; 项目概览 &gt; [查看项目基本信息](../../../product-manual/xiang-mu-guan-li/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

## 1. 添加跟踪代码

根据QQ小程序框架选择SDK并添加跟踪代码

参照小程序的开发框架，下载相应的SDK，并添加跟踪代码。

* QQ 原生框架
* Taro 框架
* uni-app 框架

{% tabs %}
{% tab title="QQ原生框架" %}
### 1.下载 gio-qq-minp.js 文件

把文件放在QQ小程序项目里，比如 utils 目录下。

```text
curl --compressed https://assets.giocdn.com/sdk/gio-qq-minp.js -o gio-qq-minp.js
```

### 2、添加跟踪代码

方式一：

在根目录 app.js 文件的顶部添加跟踪代码。

```java
var gio = require("utils/gio-qq-minp.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本' });
```

方式二：

步骤一：新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数。

```java
export default {
projectId: '你的 GrowingIO 项目ID',
appId: '你的小程序AppID',
version: '小程序版本'
...
}
```

步骤二：在根目录 app.js文件的顶部添加跟踪代码

```java
var gio = require("utils/gio-qq-minp.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}

{% tab title="Taro框架" %}
### 1.下载 gio-qq-minp.js 文件

把文件放在QQ小程序项目里，比如 utils 目录下。

```text
curl --compressed https://assets.giocdn.com/sdk/gio-qq-minp.js -o gio-qq-minp.js
```

### 2、添加跟踪代码

方式一：

在根目录 app.js 文件的顶部添加跟踪代码。

```java
import Taro from '@tarojs/taro';
var gio = require("utils/gio-qq-minp.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', taro: Taro });
```

方式二：

步骤一：新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数。

```java
import Taro from '@tarojs/taro';
export default {
projectId: '你的 GrowingIO 项目ID',
appId: '你的小程序AppID',
version: '小程序版本',
taro: Taro,
...
}
```

步骤二：在根目录 app.js文件的顶部添加跟踪代码。

```java
var gio = require("utils/gio-qq-minp.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}

{% tab title="uni-app框架" %}
### 1.下载 gio-qq-minp.js 文件

把文件放在QQ小程序项目里，比如 utils 目录下。

```text
curl --compressed https://assets.giocdn.com/sdk/gio-qq-minp.esm.js -o gio-qq-minp.js
```

### 2、添加跟踪代码

方式一：

在根目录 app.js 文件的顶部添加跟踪代码。

```java
import Vue from 'vue';
import App from './App';
App.mpType = 'app';
var gio = require("utils/gio-qq-minp.js").default;
gio('init', '你的 GrowingIO 项目ID', '你的小程序AppID', { version: '小程序版本', vue: Vue });
```

方式二：

步骤一：新建一个 gioConfig.js 文件，并且配置 gioConfig.js 文件中的 必要 配置参数。

```java
import Vue from 'vue';
export default {
projectId: '你的 GrowingIO 项目ID',
appId: '你的小程序AppID',
version: '小程序版本',
vue: Vue
...
}
```

步骤二：在根目录 app.js文件的顶部添加跟踪代码。

```java
var gio = require("utils/gio-qq-minp.js").default;
var gioConfig = require("你的 gioConfig.js 文件地址").default;
gio('setConfig', gioConfig);
```
{% endtab %}
{% endtabs %}

## 2. SDK参数配置

建议每次发布小程序新版本的时候，更新一下版本号 version，可以在 GrowingIO 分析不同版本的数据。除了 version 之外，还有以下额外参数可以使用。

| 参数 | 值 | 解释 |
| :--- | :--- | :--- |
| version | string | 你的小程序的版本号 |
| getLocation autoGet | true \| false | 是否自动获取用户的地理位置信息。默认false |
| getLocation type | wgs84 \| gcj02 | gcj02 为火星坐标系 |
| followShare | true \| false | 详细跟踪分享数据，开启后可使用分享分析功能。默认true |
| forceLogin | true \| false | 你的 QQ 小程序是否强制要求用户登陆微信获取 openid。默认 false |
| debug | true \| false | 是否开启调试模式，可以看到采集的数据。默认 false |

forceLogin 是一个需要特别注意的参数。GrowingIO 默认会在小程序里面设置用户标识符，存储在QQ Storage 里面。这个用户标识符潜在可能会被 `clearStorage` 清除掉，所以有可能不同的用户标识符对应同一个QQ里的 openid。如果你的小程序在用户打开后会去做登陆并且获取 `openid` 和/或 `unionid`，可以设置 `forceLogin` 为 true。当 forceLogin 为 true 的时候，用户标识符会使用 openid，潜在风险是如果没有设置 openid，数据不会发送，**所以请特别注意这个参数的设置**

```text
如需配置 请将 forceLogin 设为 true
```

## 3. 添加请求服务器域名

要正常采集QQ小程序的数据并发送给 GrowingIO，需要在QQ小程序里事先设置一个通讯域名，允许跟 GrowingIO API 服务器进行网络通信。具体步骤如下：

1. 登录QQ小程序后台，进入配置
2. 打开开发设置，到服务器域名配置部分
3. 在request合法域名中添加：[https://wxapi.growingio.com](https://wxapi.growingio.com)

## 4. QQ小程序 用户属性设置

作为用户行为数据分析工具，用户信息的完善会给后续的分析带来很大的帮助。在小程序中，QQ用户属性是非常重要的设置，只有完善了QQ用户属性信息，QQ的访问用户变量（如下表）才可以在分析工具中使用，交互数据定义、数据校验功能才会方便通过用户QQ相关的信息（QQ姓名和头像）定位用户。

下面是专门针对用户的接口。

### 绑定QQ用户ID

当用户在你的小程序上登陆获取到 openid 后，可以用过 identify 接口绑定QQ用户ID，后续在 GrowingIO 中获取更准确的QQ访问用户量。示例代码如下：

```java
qq.request({
  url: 'https://YOUR_HOST_NAME/wechat/code2key',
  method: 'GET',
  data: { code: res.code },
  success: function(res) {
    var openid = res.data.openid;
    var unionid = res.data.unionid;
    ...
    gio('identify', openid, unionid);
  }
})
```

### 设置QQ用户信息

当用户在你的小程序上绑定QQ信息后，可以通过 setVisitor 接口设置QQ用户信息，后续在 GrowingIO 中分析这个数据。示例代码如下：

```java
qq.getUserInfo({
  success: function(res) {
    ...
    gio('setVisitor', res.userInfo);
  }
})
```

QQ信息包含**QQ昵称**、**QQ头像**、**性别**、**QQ所填国家**、**QQ所填省份**、**QQ所填城市**。

{% hint style="info" %}
\*注：用户画像中的部分数据，只有在设置QQ用户信息后，才可以统计。
{% endhint %}

### 设置登录用户ID

当用户在你的小程序上注册以后，你的产品应用服务端会在用户数据库里添加一条记录并且分配一个 ID，可以通过 setUserId 接口设置注册用户ID，后续在 GrowingIO 中分析登录用户这个数据。示例代码如下：

```java
gio('setUserId', YOUR_USER_ID);
```

### 清除登录用户ID

用户退出登录时，清除登录用户ID。

```java
gio('clearUserId');
```

### 设置登录用户属性

当用户在你的小程序上传了注册用户ID后，可以通过 setUser 接口设置注册用户信息，后续在 GrowingIO 中分析这个数据。示例代码如下：

```java
gio('setUserId', user.id); 
gio('setUser', { id: user.id, name: user.name });
```

## 5. 自定义数据上传API

自定义数据上传API，请参考[自定义数据上传API](customize-api.md)。

## 6. 创建应用

请在添加了跟踪代码的支付宝小程序重新启动几次，发送数据给 GrowingIO。

在GrowingIO平台的创建微信小游戏应用。创建应用请参考查看[创建应用](../../../product-manual/xiang-mu-guan-li/application-manage.md#chuang-jian-ying-yong)。

## 7. 验证SDK是否正常采集数据

方式一：[小程序&内嵌页Debugger](../../debugging/minpdebugger.md)

方式二：在SDK中设置了Debug模式后，在开发者工具中查看数据采集日志。

方式三：[数据校验](../../../product-manual/shu-ju-zhong-xin/shu-ju-xiao-yan/datacheck.md)

