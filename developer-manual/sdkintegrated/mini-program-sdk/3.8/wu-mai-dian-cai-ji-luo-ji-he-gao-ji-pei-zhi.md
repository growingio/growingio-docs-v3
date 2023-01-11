# 无埋点采集逻辑和高级配置

## 访问数据 <a href="#fang-wen-shu-ju" id="fang-wen-shu-ju"></a>

每次用户打开小程序的时候，发送一条访问事件的消息，对应的数据指标是打开次数。发送数据包含但不限于以下信息：进入页面、进入时间、场景值、来源小程序或 App、设备信息、微信应用信息、应用版本号。触发时机：onAppShow

每次用户关闭小程序的时候，关闭动作包括退出小程序回到微信、退出微信，会发送一条`应用关闭`消息，会根据这个消息来计算应用访问时长。发送数据包含但不限于以下信息：退出页面、退出时间。触发时机：onAppHide

## 页面数据 <a href="#ye-mian-shu-ju" id="ye-mian-shu-ju"></a>

每次用户访问一个新的页面，发送一条页面浏览事件的消息，对应的数据意义是页面分析。发送数据包含但不限于以下信息：页面信息、打开时间、页面来源、页面标题、页面级变量。触发时机：onPageShow

每次当用户点击转发按钮时，会弹出转发框，这时会发送一条`要转发事件的`消息。这是一个自定义事件，数据包含以下信息：事件时间、所在页面、转发动作来源、转发页面标题和转发页面路径。注意这个事件不代表用户真正转发了消息到聊天里面，而是用户触发了转发动作。如果要跟踪成功转发消息事件，建议在 onShareAppMessage 的 success callback 里面发送一个自定义事件。触发时机：onShareAppMessage

## 行为数据

对于用户在页面发生的行为，如果这个行为有绑定事件比如 bindtap，并且在您的小程序里面进行处理，那么 GrowingIO 的小程序 SDK 会自动采集这些事件，发送一条行为事件的消息。目前，我们支持的事件有 tap、longpress、confirm 和 change 事件。

### tap

tap 事件是手指触摸后马上离开时触发的事件。当 wxml 中的 view 绑定了 bindtap 事件以后，在事件处理函数执行的时候，SDK 会自动采集 tap 事件，发送数据包含但不限于以下信息：点击事件时间、事件发生所在页面、点击控件相关信息。

### longpress

longpress 事件是手指触摸后，超过350ms再离开时触发的事件。当 wxml 的 view 绑定了 bindlongpress 事件以后，在事件处理函数执行的时候，SDK 会自动采集 longpress 事件，发送数据包含但不限于以下信息：点击事件时间、事件发生所在页面、点击控件相关信息。

### change

change 事件是针对 checkbox、radio、picker-view 这些控件，当选择项发生改变时触发的事件。当 wxml 的 view 绑定了 bindchange 事件以后，在事件处理函数执行的时候，SDK 会自动采集 change 事件，发送数据包含但不限于以下信息：选择事件的发生时间、事件发生所在页面。

### submit

当点击 form表单中 form-type 为 submit 的 button  [button](https://developers.weixin.qq.com/miniprogram/dev/component/button.html) 组件时，会将表单组件中的 value 值进行提交，SDK 会自动采集 submit 事件，发送数据包含但不限于以下信息：提交事件的发生时间、事件发生所在页面。

## 采集标记[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#%E9%87%87%E9%9B%86%E6%A0%87%E8%AE%B0) <a href="#cai-ji-biao-ji" id="cai-ji-biao-ji"></a>

### 1、采集标记[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#1%E9%87%87%E9%9B%86%E6%A0%87%E8%AE%B0) <a href="#1-cai-ji-biao-ji" id="1-cai-ji-biao-ji"></a>

有时我们表单页面中可能需要获取用户选择框、单/多选框的值进行上报以准确分析用户行为。此时，我们可以通过数值采集标记 `data-growing-track` 来获取值。例：

```html
<checkbox-group bindchange='checkboxChange' data-growing-track>
    <label class='checkbox'>
        <checkbox value='GrowingIO' checked='true' /> GrowingIO
    </label>
    <label class='checkbox'>
        <checkbox value='CDP' checked='false' /> GrowingIO CDP
    </label>
</checkbox-group>
```

**免责声明警告：**

请勿尝试在密码框上标记 data-growing-track 采集数据，会明文暴露用户填写的密码信息。GrowingIO不承担由此直接或间接产生的数据风险和法律风险。

**提示**[**​**](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#%E6%8F%90%E7%A4%BA)

**3.8.0版本开始，SDK会自动忽略带有 `autoplay` 属性且值为 `true` 组件的 change 事件（例如swiper、video）。如果您期望采集它，请添加 `data-growing-track` 标记。**

### 2、补充数据标记[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#2%E8%A1%A5%E5%85%85%E6%95%B0%E6%8D%AE%E6%A0%87%E8%AE%B0) <a href="#2-bu-chong-shu-ju-biao-ji" id="2-bu-chong-shu-ju-biao-ji"></a>

#### **1）data-title**[**​**](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#1data-title)

有时SDK自动采集的节点数据并不能完全满足上报分析需要。此时，我们可以通过额外信息的标记 `data-title` 来补充SDK采集的内容。例：

```html
<button data-title="额外的上报信息">节点</button>
```

#### **2）data-index**[**​**](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#2data-index)

有时我们页面中可能存在类似列表类的Dom结构相似或一致使得SDK上报数据出现无法区分的情况。此时，我们可以通过索引标记 `data-index` 来准确描述节点信息。例：

```html
<view>
    <button data-index="1">节点1</button> 
    <button data-index="2">节点2</button> 
    <button data-index="3">节点3</button>
</view>
```

#### **3）data-src**[**​**](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#3data-src)

有时页面中有需要跳转的链接（尤其是navigator组件）时，为了上报完整的用户目标去向。此时，我们可以通过链接标记 `data-src` 来上报点击链接的目标去向。例：

```html
<navigator
    url="/pages/h5/h5?from=navigate"
    data-src="/pages/h5/h5?from=navigate"
    bindtap="onNavigatorTap"
> 
    <view >  ...  </view>
</navigator>

<view data-src="/pages/h5/h5?from=navigate" bindtap="onLinkTap"> 
    模拟一个链接
</view>
```

**注意：**\
**在有上述3种额外采集标记的节点上，必须绑定一个点击事件，SDK才能实现点击的额外数据采集。如果没有，需要您手动绑定一个空的点击事件。**

#### **4）设置页面标题**[**​**](https://growingio.github.io/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#4%E8%AE%BE%E7%BD%AE%E9%A1%B5%E9%9D%A2%E6%A0%87%E9%A2%98)

默认情况下SDK会自动采集页面title，但当SDK可能无法识别或您使用了自定义标题时，可以通过在页面的`onLoad`生命周期中调用`setNavigationBarTitle`方法来设置原生页面标题并同时指定SDK上报事件时的title值。[参考文档](https://developers.weixin.qq.com/miniprogram/dev/api/ui/navigation-bar/wx.setNavigationBarTitle.html)

示例：

```javascript
Page({
  onLoad: {
    wx.setNavigationBarTitle({
      title: 'NewTitle'
    });
  }
});
```

注：阿里(支付宝/淘宝)小程序是`setNavigationBar` [参考文档](https://opendocs.alipay.com/mini/api/xwq8e6)

**注意：**

**1）指定title仅支持 String 格式。该功能适配SDK版本>=3.8.10支持。**

**2）想要设置页面标题并同时生效于SDK时，该方法必须在onLoad中调用；如果您业务中无法调整位置，则在不影响原逻辑的情况下无法生效于SDK。**

**3）部分框架可能会建议该方法调用时机为onReady（例如uni-app）或其他生命周期中，我们实际测试中在onLoad调用并无影响，因此您可放心在onLoad中使用。**

**4）在3.8.0-rc.9版本开始，我们提供了gioPageTitle字段供基础使用，但我们发现它无法覆盖大多数场景（例如需要动态修改时），因此我们废弃了它，高版本SDK仍会为您保持基础的向下兼容，请尽快修改为setNavigationBarTitle方式。**

**提示： SDK中事件title取值优先级为 setNavigationBarTitle > data.gioPageTitle（仅保持向下兼容，不保证能取到） > 页面config.json配置 > 全局app.json中tabBar配置**

### 3、忽略采集标记[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#3%E5%BF%BD%E7%95%A5%E9%87%87%E9%9B%86%E6%A0%87%E8%AE%B0) <a href="#3-hu-lve-cai-ji-biao-ji" id="3-hu-lve-cai-ji-biao-ji"></a>

有时我们会根据业务中不同的需要使用一些自己开发的组件或第三方组件，可能会触发SDK的 `chng` 事件，但我们并不期望它发生。

此时，我们可以通过忽略采集标记 **`data-growing-ignore`** 来让SDK忽略对该组件的数据采集。

**注意标记在事件绑定的节点上，没事件绑定的节点默认不会采集。**例：

```html
<view data-growing-ignore bindtap="onLinkTap">要忽略的节点</view>
```

## 半自动埋点浏览事件[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#%E5%8D%8A%E8%87%AA%E5%8A%A8%E5%9F%8B%E7%82%B9%E6%B5%8F%E8%A7%88%E4%BA%8B%E4%BB%B6) <a href="#ban-zi-dong-mai-dian-liu-lan-shi-jian" id="ban-zi-dong-mai-dian-liu-lan-shi-jian"></a>

用户标记一个元素并提供埋点事件，SDK 负责监控指定元素，当此元素出现在屏幕可视区域中时发送用户配置的埋点事件。因此您同样需要参考埋点事件在平台上进行事件类型和变量的预定义。

### **曝光逻辑**[**​**](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#%E6%9B%9D%E5%85%89%E9%80%BB%E8%BE%91)

&#x20;   **always：只要从屏幕不可见区域到可见区域**即可计为一次曝光并上报。(默认值)

&#x20;   **once：从屏幕不可见区域到可见区域**曝光只上报一次。

### **支持范围**[**​**](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#%E6%94%AF%E6%8C%81%E8%8C%83%E5%9B%B4)

微信小程序、阿里(支付宝)小程序(基础库>=2.7.0)、百度小程序、字节跳动小程序、QQ小程序。

快应用不支持。

### **使用方法一：**

1、在需要标记的元素上添加 **`growing_collect_imp`** 样式名。

2、在节点上添加 **`data-gio-imp-track 和 data-gio-track-xxxx`**进行设置参数。

示例

```html
<view  
    class="growing_collect_imp"  
    data-gio-imp-track="imp_user_var"  
    data-gio-track-name="Mike"  
    data-gio-track-age="16"
    data-gio-track-sex="boy"
>
监听的元素，必须有内容或额外样式来让节点有实际大小
</view>
```

### **使用方法二：**[**​**](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95)

1、在需要标记的元素上添加 **`growing_collect_imp`** 样式名。

2、在节点上添加**`data-gio-imp-track`、`data-gio-imp-attrs`** 属性。

**`data-gio-imp-attrs` 允许接受一个Object或者JSON.stringify后的Object字符串，SDK会自动尝试进行格式化**。

示例

```javascript
Page({ 
    data: {    
        impAttrs: { name: 'Mike', age: '16', sex: 'boy' }
        // 或者
        impAttrs: JSON.stringify({ name: 'Mike', age: '16', sex: 'boy' })
    }
})
```

```html
<view  
    class="growing_collect_imp"  
    data-gio-imp-track="imp_user_var"  
    data-gio-imp-attrs="{{ impAttrs }}"
>
监听的元素，必须有内容或额外样式来让节点有实际大小
</view>
```

以上两种使用方法对应产生的 **cstm** 事件相当于： ↓↓↓

```javascript
gio(
    'track', 
    'imp_user_var', 
    { name: 'Mike', age: '16', sex: 'boy' }
);
```

### **单次曝光**

如果您的曝光事件只需要统计一次或触发过于频繁导致曝光事件量过大，可以在节点上添加`data-gio-imp-type="once"`并设置唯一的`节点id`，来使得曝光逻辑变为单次上报。

```html
<view
    class="growing_collect_imp"
    id="imp_1"
    data-gio-imp-type="once"
    data-gio-imp-track="imp_picture_var"
    ...
>
  监听的元素，必须有内容或额外样式来让节点有实际大小
</view>
```

### 手动更新半自动埋点监听[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/plugins/impressionTracking#%E6%89%8B%E5%8A%A8%E6%9B%B4%E6%96%B0%E5%8D%8A%E8%87%AA%E5%8A%A8%E5%9F%8B%E7%82%B9%E7%9B%91%E5%90%AC) <a href="#shou-dong-geng-xin-ban-zi-dong-mai-dian-jian-ting" id="shou-dong-geng-xin-ban-zi-dong-mai-dian-jian-ting"></a>

当您需要添加半自动埋点的节点是动态渲染时（例如根据接口数据渲染不同的内容），SDK 可能会因为无法感知节点渲染时机而失去对标记节点的监听。此时，您需要调用 `updateImpression` 手动更新 SDK 的监听来保证您的动态渲染节点能够被监听到。

**示例**[**​**](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/plugins/impressionTracking#%E7%A4%BA%E4%BE%8B)

```javascript
const { gio } = global;
Page({
  data: {
    impData: [],
  },
  onShow() {
    // 这里通过一个Promise来模拟调用接口
    const getData = new Promise((resolve) => {
      setTimeout(() => {
        resolve({ name: 'Lily', age: 18 });
      }, 3000);
    });
    getData.then((result) => {
      this.setData({ impData: result }, () => {
        // 在setData回调中调用 updateImpression 即可
        gio('updateImpression');
      });
    });
  },
});
```



**注意：**\
**1）被标记的节点必须有实际的大小，一个没有内容和样式的节点标记可能不会触发事件。**

**2）请勿在同一页面中大量标记半自动埋点浏览事件（如商品列表），可能会严重影响页面性能导致卡顿。**

**3）`data-gio-imp-type`配置项SDK版本>=3.8.4支持。**

**4）`updateImpression`** **方法SDK版本>=3.8.11支持。**

## 其他[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#%E5%85%B6%E4%BB%96) <a href="#qi-ta" id="qi-ta"></a>

#### Object参数限制[​](http://localhost:3000/growingio-sdk-docs/docs/miniprogram/3.8/commonlyApi#object%E5%8F%82%E6%95%B0%E9%99%90%E5%88%B6) <a href="#object-can-shu-xian-zhi" id="object-can-shu-xian-zhi"></a>

SDK文档中指定参数值为 **Object类型** 时，请注意以下限制：**(非指定类型值均会被替换为空字符串，长度超限均会被截断)**

**`key:` String，length <=50**

**`value:` String | number 时 length <=1000**
