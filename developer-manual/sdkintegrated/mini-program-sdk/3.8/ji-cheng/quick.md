# 快应用

目前快应用仅支持原生开发方式。如您使用了其他开发方式，请咨询我们。

## 准备条件

1、在 GrowingIO 平台中获取项目Id，获取方法请参考"项目管理 > 项目概览 > [查看项目基本信息](../../../../../product-manual/projectmange/details.md#cha-kan-xiang-mu-ji-ben-xin-xi)"。

2、在您的小程序中获取`appId`。

3、在下列选项中选择对应的开发框架，并下载对应的SDK文件存放在项目中或使用npm的方式集成。下文中以`utils/gio`目录作为下载集成的示例目录(目录和SDK文件可自定义重命名)。

## 集成

参考示例在 app.ux 快应用主文件中添加初始化代码。添加位置参考示例代码，注意不要随意修改初始化代码位置。**SDK不支持在快应用中任意生命周期中进行初始化。**

**1、加载SDK**

快应用原生SDK下载：[https://assets.giocdn.com/sdk/minip/saas/3.8.6/gio-quickapp.js](https://assets.giocdn.com/sdk/minip/saas/3.8.6/gio-quickapp.js)

> (如果您点击链接在浏览器中直接打开了文件并不是下载文件，请尝试右键点击链接，选择 `链接存储为...` 即可正常触发下载)

**2、使用`init`方法进行初始化**

注意`init`方法所处位置在App实例之前。

**示例代码**

```javascript
// app.ux
import gio from './utils/gio/gio-quickapp.js';

gio('init', 'your GrowingIO 项目ID', 'your packageName', {
    version: 'your quickapp version',
    ...other settings
});

export default GioApp({ ... }); // 入口文件要包裹GioApp()方法

// pages/xx/index.ux
export default GioPage({ ... }); // 所有的页面文件要包裹GioPage()方法
```

## 数据校验

GrowingIO为您提供多种验证SDK是否正常采集数据的方式：

方式一：[小程序&内嵌页Debugger](../../../../debugging/minpdebugger.md)（可能会受网络等因素影响，建议使用方式二）

方式二：在SDK中设置了Debug模式后，在开发者工具中查看数据采集日志。

## 其他

**暂不支持 `表单提交事件`、`半自动采集浏览事件`、`分享事件`**

