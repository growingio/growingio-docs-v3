# 快应用SDK

## 准备条件

获取项目ID，获取方法请参考"项目管理 &gt; 项目概览 &gt; [查看项目基本信息](../../../product-manual/sysmanage/projectmange/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

## 1. 添加跟踪代码

#### 1.下载 gio-quickapp.js 文件

把文件放在快应用应用项目里，比如 utils 目录下。

```text
curl --compressed https://assets.giocdn.com/sdk/gio-quickapp.js -o gio-quickapp.js
```

#### 2、在根目录 app.ux文件的顶部添加跟踪代码

```java
var gio = require("utils/gio-quickapp").default;
gio('init', '你的 GrowingIO 项目ID', '你的快应用ID(包名)', { version: '小程序版本' });
​
// 添加trackApp 和 trackPage 代码，如下：
// app.ux 中改写如下：
export default {
  ...
})
// 改为：
export default trackApp({
  ...
})
​
// 所有的Page页面的index.ux改写如下：
export default {
  ...
})
// 改为：
export default trackPage({
  ...
})
```

## 2. SDK参数配置

建议每次发布小程序新版本的时候，更新一下版本号 version，可以在 GrowingIO 分析不同版本的数据。除了 version 之外，还有以下额外参数可以使用。

| 参数 | 值 | 解释 |
| :--- | :--- | :--- |
| version | string | 你的小程序的版本号 |
| forceLogin | true \| false | 你的快应用是否获取用户唯一标识，默认 false |
| debug | true \| false | 是否开启调试模式，可以看到采集的数据。默认 false |

## 3. 添加接口权限

在您项目中的 manifest.json 文件中的 features 属性中添加权限声明代码。

```java
"features": [
  {"name": "system.app"},
  {"name": "system.storage"},
  {"name": "system.device"},
  {"name": "system.network"},
  {"name": "service.router"},
  {"name": "system.fetch"}
  {"name": "system.geolocation"}
];
```

## 4. 快应用 用户属性设置

#### 绑定快应用用户ID <a id="bang-ding-kuai-ying-yong-yong-hu-id"></a>

当用户在你的应用上登陆获取到 用户唯一id 后，可以用过 identify 接口绑定快应用用户ID，后续在 GrowingIO 中获取更准确的快应用访问用户量。示例代码如下：

```java
device.getUserId({
  success: function(res) {
    var userId = res.data.userId;
    // ...
    gio('identify', userId);
  }
})
```

#### 设置快应用用户信息 <a id="she-zhi-zhu-ce-yong-hu-id"></a>

```java
gio（'setVisitor', res.userInfo）;
```

#### 设置登录用户ID <a id="she-zhi-zhu-ce-yong-hu-id"></a>

当用户在你的快应用上注册以后，你的产品应用服务端会在用户数据库里添加一条记录并且分配一个 ID，可以通过 setUserId 接口设置注册用户ID，后续在 GrowingIO 中分析登录用户这个数据。示例代码如下：

```java
gio('setUserId', YOUR_USER_ID); 
```

#### 清除登录用户ID

用户退出登录时，清除登录用户ID。

```java
gio('clearUserId'); 
```

#### 设置登录用户属性 <a id="she-zhi-zhu-ce-yong-hu-xin-xi"></a>

当用户在你的快应用上传了注册用户ID后，可以通过 setUser 接口设置注册用户信息，后续在 GrowingIO 中分析这个数据。示例代码如下：

```java
gio('setUser', { id: user.id, name: user.name });
```

## 5. 自定义数据上传API

自定义数据上传API，请参考[自定义数据上传API](customize-api.md)。

## 6. 创建应用

请在添加了跟踪代码的支付宝小程序重新启动几次，发送数据给 GrowingIO。

在GrowingIO平台的创建微信小游戏应用。创建应用请参考查看[创建应用](../../../product-manual/sysmanage/projectmange/application-manage.md#chuang-jian-ying-yong)。

## 7. 验证SDK是否正常采集数据

方式一：[小程序&内嵌页Debugger](../../debugging/minpdebugger.md)

方式二：在SDK中设置了Debug模式后，在开发者工具中查看数据采集日志。

方式三：[数据校验](../../../product-manual/datacenter/datacheck.md)

##  

