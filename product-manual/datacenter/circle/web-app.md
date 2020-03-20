# App端数据定义（Web圈选）

## 一、介绍 <a id="yi-jie-shao"></a>

为了提供更有效率的便捷的数据定义工作，我们为你提供了在电脑上圈选手机 app 的功能：

1.通过机器学习提高元素定义的准确性，iOS 和 Android 支持 Pattern Server；

2.提供基本的热图功能，可以分别查看过去7天、昨天和今天的热图；

3.支持 H5 页面的快捷定义，同平台不同原生页面中使用的 H5 一次定义完成；

4.在电脑上进行便捷的操作，右侧动态展示区详细解释「你在定义的是什么」；

5.与 web 端圈选的 UI / UX 保持一致，降低不同平台圈选的学习成本；

6.当前设备支持范围：手机、平板电脑，以及不同设备的横屏、竖屏分别圈选。

## 二、准备工作 <a id="er-zhun-bei-gong-zuo"></a>

### **1.SDK 版本要求** <a id="1sdk-ban-ben-yao-qiu"></a>

将想要圈选的 App 升级到 2.7.0 及以上的 SDK版本。

使用横屏圈选，请将想要圈选的 App 升级到 2.8.0 及以上的 SDK 版本。

### **2.使用方法** <a id="2-shi-yong-fang-fa"></a>

通过 GrowingIO 圈选入口，在下拉列表中找到需要定义的 App，进入圈选扫码页面，使用手机扫码，选择手机中右边的按钮「 web 端圈选」即可进入电脑圈选，唤醒手机上相对应的 App （加载了 2.7.0 以上版本的 SDK ），操作手机进入到想要定义的页面进行圈选。

请确保手机和电脑在同一个 wifi 局域网下。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll135OOcbjbcP3CLlu--Ll138X5raGKPVELG7YCE5908CE4B88020WiFi.png)

### **3.查看基本信息** <a id="3-cha-kan-ji-ben-xin-xi"></a>

可以在左侧看到当前圈选的元素的包名、版本信息以及app和电脑的连接状态。

**示意1** :

在这里查找 App 版本信息和 SDK 版本

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN1lEIb39j2HWqqhE59BBE1-E69FA5E79C8BE59FBAE69CACE4BFA1E681AF.png)

**示意2 :**

圈选手机和电脑的连接状态

【连接正常】

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN1nqpHsoorIAnb0E59BBE2-E8AEBEE5A487E8BF9EE68EA5E6ADA3E5B8B8.png)

【界面暂停同步】

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN1p3HpmP7cXiqfqE59BBE3-E7958CE99DA2E69A82E5819CE5908CE6ADA5.png)

这个情况出现是因为电脑端正处于定义的过程中，此时手机端界面若发生变化，为保证定义内容准确性，会暂停界面的同步。当结束定义后会将手机端的界面再次同步至电脑端。

【设备断开连接】

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN1rVD1dhtm9kMhlE59BBE4-E8AEBEE5A487E696ADE5BC80E8BF9EE68EA5.png)

当手机端退出正在圈选的应用或无线网断开等情况出现时，可能会导致两端设备连接断开，中断圈选。如要继续圈选可重新扫码进行连接。如要结束圈选，可点击右上角“退出圈选”。

### **4.异常情况处理** <a id="4-yi-chang-qing-kuang-chu-li"></a>

如果扫码失败，可能存在图中所示原因，检查后仍然无法解决可以联系技术支持。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN1iC0bXuYE0XVZDE689ABE7A081E5A4B1E8B4A5.png)

## 三、圈选元素 <a id="san-quan-xuan-yuan-su"></a>

不管是 app 的原生元素还是 H5 页面上的元素，在 GrowingIO 元素定义的过程中，既需要定义元素本身的条件，也需要定义元素所在的页面，这两个部分在下面进行详细的介绍。

### **1.元素的限定条件** <a id="1-yuan-su-de-xian-ding-tiao-jian"></a>

当我们对一个元素进行定义时，往往是想要知道「某个按钮被点了多少次」，因为“点击”的动作在开发时加在了这个按钮上，于是你的用户点击时就会触发跳转等操作，GrowingIO 的圈选定义是基于 app 开发的实现方式，如果使用了不同的实现方式，数据的呈现往往也会有不同，但是这并不影响你定义元素的操作。

在电脑上点击你想要圈选的元素，然后查看右侧的文案，来理解自己定义的是什么。

根据不同的实现方式，对于不同元素之间的关系，主要有 3 种定义形式：

#### 情况1：多个元素共用一个“点击”动作，常见于商品列表和商品详情等 <a id="qing-kuang-1-duo-ge-yuan-su-gong-yong-yi-ge-dian-ji-dong-zuo-chang-jian-yu-shang-pin-lie-biao-he-shang-pin-xiang-qing-deng"></a>

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN1vRUFj1j-hd0sFE59BBE5-E5A49AE58583E7B4A0E585B1E794A8E4B880E4B8AAE782B9E587BBE4BA8BE4BBB6vsE78BACE7AB8BE782B9E587BBE4BA8BE4BBB6.png)

这种情况是因为在这个 app 开发的时候，就把这些元素“绑定”在了一起。你会在右侧的文案中看到“区域”的字样，可以将鼠标移到“所有元素”上面，你将会看到左侧高亮的元素，他们的点击都是一样的，圈哪个元素的数据都是一样的。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN1x3ixDVYVrTTxuE59BBE6-E58CBAE59F9FE58685E68980E69C89E58583E7B4A0.png)

我们建议你按照分析的需求来定义这样的元素。

**案例 1：**

你想要知道不同咖啡的点击情况，这里的元素有很多种“拿铁咖啡”、“23元”、“图片名称”，因为他们共用一个点击的动作，不管点到哪个元素，点击的数据都是一样的，所以你其实只需要定义任意一个元素都可以拿到这个区域的数据；

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN2-aNDPXlq9iPN5E59BBE7-E6A188E4BE8B1.png)

**案例 2:**

你想知道“拿铁咖啡”、“美式咖啡”和“馥芮白”等咖啡的点击情况，每个定义一遍太麻烦了，可以只定义一次。依然是选择“拿铁咖啡”这个元素，然后在右侧选择「不限制内容」，不管咖啡名称是什么，所有的咖啡商品都会统计进来。这时定义的这个元素，我们叫做“同类元素”。

接下来在「事件分析」中选择这个指标，通过“元素内容”维度来区分，就像定义元素时右侧下面展示的柱图一样。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN20vtXadJKCP5JBE59BBE8-E6A188E4BE8B2.png)

**案例 3:**

你想要知道这个列表不同位置的商品点击情况，也可以用与案例 2 相似的做法，选择这个区域的元素中，带有顺序标示的元素，在这里是外面的框，「不限定顺序」，统计所有位置的总数，然后也是定义“同类元素”，然后在「事件分析」中通过“元素位置”维度来区分。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN22Mzvt9UZW87snE59BBE9-E6A188E4BE8B3.png)

#### 情况2：一个元素有独立的“点击”动作，常见于菜单按钮等  <a id="qing-kuang-2-yi-ge-yuan-su-you-du-li-de-dian-ji-dong-zuo-chang-jian-yu-cai-dan-an-niu-deng"></a>

这种情况是因为在这个 app 开发的时候，给每个元素单独设置了“点击”的动作，需要单独圈选。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN2329yU84ghPme9E59BBE10-E5A49AE58583E7B4A0E585B1E794A8E4B880E4B8AAE782B9E587BBE4BA8BE4BBB6vsE78BACE7AB8BE782B9E587BBE4BA8BE4BBB6.png)

如果一个列表里既有区域圈选的元素也有单个圈选的元素，需要单独圈选单个圈选的元素，因为他们的数据是单独统计的。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN25Gvwi-kKfQAWjE59BBE11-E58D95E78BACE7BB9FE8AEA1E79A84E58583E7B4A0.png)

单个元素的圈选也可以像区域圈选一样定义同类元素，统计多个元素之和，在「事件分析」中通过“元素内容”和“元素位置”维度来区分。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN26g92IiIaRLFgrE59BBE12-E58D95E78BACE7BB9FE8AEA1E79A84E58583E7B4A0E79A84E5908CE7B1BBE58583E7B4A0.png)

【对于 H5 元素的圈选方法详见 [Web端数据定义（Web圈选）](web.md)】

#### 情况3：存在父子结构的元素 —— **容器圈选** <a id="qing-kuang-3-cun-zai-fu-zi-jie-gou-de-yuan-su-rong-qi-quan-xuan"></a>

容器元素的数据是容器内所有元素的数据之和，在 H5 页面中，a 标签和 button 标签会默认作为容器，你可以通过查看不同元素的数据，看到这种差异。

### **2.元素的所属页面** <a id="2-yuan-su-de-suo-shu-ye-mian"></a>

在定义元素的过程中，你会发现元素默认会有一个所属页面：

因为一个元素可能会同时在多个页面上，所以你可以调整元素的所属页面范围，以确保定义符合自己需要的数据。

原生元素的默认所属页面是此时元素所在的最小的页面部分，H5 元素的默认所属页面是 H5 。

在这个例子中，「加入购物车」元素在当前商品详情页的点击数据：

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN2AjvKaM520FWW1E59BBE13-E68980E5B19EE9A1B5E99DA2.png)

但是更多情况下，你其实是想统计所有页面中，不管这个按钮在哪些商品详情页，都要统计为「加入购物车」按钮的点击次数，这时就需要把元素所属页面改为所有页面。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN2C7xAJLfY4PQgvE59BBE14-E5B195E5BC80E58583E7B4A0E68980E5B19EE9A1B5E99DA2.png)

### **3.在热图模式下圈选元素** <a id="3-zai-re-tu-mo-shi-xia-quan-xuan-yuan-su"></a>

可以在圈选时开启热图模式，来查看点击热度：

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN2EwUiRgO7gkBD7E59BBE15-E698BEE7A4BAE783ADE59BBE.png)

## 四、圈选页面 <a id="si-quan-xuan-ye-mian"></a>

### **1.原生页面** <a id="1-yuan-sheng-ye-mian"></a>

在 App 中，「原生页面」其实更像是 App 的「组成部分」，每个部分上有承载着不同功能的元素，帮助用户完成在 App 中的操作。

你可以定义你关心的元素页面，以此来统计这些页面被浏览的次数。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN2GFyAB3hOdiF3_E59BBE16-E5AE9AE4B989E58E9FE7949FE9A1B5E99DA2.png)

### **2.H5 页面** <a id="2h5-ye-mian"></a>

为了更方便地定义 H5 页面，页面选择中提供快捷模式和自定义模式

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-Ll0ACUYgbwb2UH8p7yx-Ll0BN2J3H8SGmjVbaHHE59BBE17-E5AE9AE4B989H5E9A1B5E99DA2.png)

**快捷模式 ：该 H5 在本应用内的全部数据**

一个 H5 页面可能会在这个 App 的不同页面下加载出来，在这个模式下，这个 H5 不管在哪个页面被打开，只要在 App 中被浏览就统计进来。

**自定义模式：该 H5 在该原生部分下的数据**

一个 H5 页面可能会在这个 App 的不同页面下加载出来，在这个模式下，这个 H5 不管在哪个页面被打开，只统计在当前原生页面下被加载的数据。

## 五、FAQ <a id="wu-faq"></a>

**1.App 的 H5 页面圈选的数据是怎样的？** 如果只加载了 Android 和 iOS 的 SDK ，就只能是 App 圈选，H5 在 App 外面的数据是统计不到的； 如果加载了JS SDK ，是可以在 web 圈选的，App 上圈的就是在 App 的数据，web 里圈的还会包含 App 外的数据。

**2.为什么两种移动端圈选方式的数据不一样？**

H5 页面在 app 中可能会嵌套在不同的原生页面中，比如一个 H5 会嵌套在两个 fragment 里，这种情况很常见。

在「 app 上圈选 app 」的定义页面时，是定义这个 H5 在当前 fragment 的数据情况，定义 H5 页面上的元素也一样；

在「电脑端圈选 app 」的定义页面时，提供了两种模式，默认是定义这个 H5 在整个 app 中的数据情况，不区分当前嵌套的原生页面，可以手动切换到限定当前原生页面，定义 H5 页面上的元素也一样；

因为默认对 H5 页面处理不同，「电脑端圈选 app 」提供了更灵活和便捷的定义方式，当一个 H5 页面在多个原生页面中嵌套时，会有差异，可以根据需求灵活设置。

