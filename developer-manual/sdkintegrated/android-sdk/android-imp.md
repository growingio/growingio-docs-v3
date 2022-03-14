---
description: 半自动浏览事件能够携带用户添加的自定义事件和变量，当View从屏幕中出现则自动发送事件。
---

# Android半自动采集浏览事件

## 特性版本适配

请升级最新版本的SDK。

| 无埋点SDK版本 | 特性                        |
| -------- | ------------------------- |
| 2.8.5    | 添加配置当 View 可见的比例则自动触发埋点事件 |
| 2.8.4    | 支持自动采集元素内容                |
| 2.8.2    | 支持 imp 半自动埋点              |

{% hint style="warning" %}
React Native 无埋点 SDK目前不支持。
{% endhint %}

## 旧版全自动浏览事件介绍

集成无埋点 SDK 后，GIO 使用事件类型 imp（impression）采集用户浏览事件。

它的采集逻辑为 View 采集初始化完毕后在当前页面上可见，将发送 imp 事件。

注：

1. SDK标记的可见与否是针对于 View 对象的可见，所以对于列表的元素复用 View 对象的情况，不会再次发送 imp 。
2. 标记的是对象是否可见，没有将 View 是否滚动出屏幕再次出现在屏幕上的情况计算在内。**一个可见的 View 对象，只会发送一次 imp 事件，滚动出屏幕再次滚动出现，不会重复发送。**
3. View 对象和页面强关联，如果两个页面共享一个 View 对象，会认为是两个元素，发送两次 imp 事件。

综上， 虽然 SDK 能够自动采集每个 View 对象的浏览事件，但是有以下弊端：

* 在实际用户场景中并不能真正代表用户对于某个 View 的浏览次数
* 想自定义添加一些自定义变量，无法添加。

## **新版半自动浏览事件介绍** <a href="#xin-ban-ban-zi-dong-liu-lan-shi-jian-jie-shao" id="xin-ban-ban-zi-dong-liu-lan-shi-jian-jie-shao"></a>

新版方案：**用户标记一个 View 并提供自定义事件和变量，SDK 负责监控，当此 View 对象可见时发送用户配置的自定义事件和变量。**

新版用户浏览事件半自动究竟指什么？

1. 不再全量采集所有 View 的浏览事件，改为只采集用户主动标记 view 。事件类型使用自定义事件类型 **cstm** （custom），不再使用 **imp** （impression）。**需要用户在代码中埋点并且在官网配置自定义事件和变量。**
2. SDK 将 View 对象在当前屏幕是否可见，是否滚动出屏幕又再次出现纳入采集发送策略，并取消浏览事件与页面的关联。即：共享 View 对象的不同页面不会重复发送，并且 view 对象不在当前屏幕又再次滑入会再次发送。后文详细举例说明，见：[场景1](android-imp.md#chang-jing-1-bu-tong-de-ye-mian-gong-xiang-tong-yi-ge-yuan-su)。
3. **半自动指**：**用户提供 View 的自定义事件和变量内容，SDK 根据当前 view 对象是否在屏幕上可见，自动发送一个自定义事件。**即：需要用户标记 View 并且提供自定义事件和变量，SDK 在 View 对象出现在屏幕上时自动发送，不同于 track 接口发送的 cstm 事件，调用即发送。

下面我们将从三个方面介绍此方案。

### **1.** **标记View并设置自定义事件和变量** <a href="#1-biao-ji-view-bing-she-zhi-zi-ding-yi-shi-jian-he-bian-liang" id="1-biao-ji-view-bing-she-zhi-zi-ding-yi-shi-jian-he-bian-liang"></a>

在旧版无埋点 SDK 中，如果想查看某个广告位的具体某个商品的曝光次数，通过圈选广告位的 view 元素的 imp 事件是无法做到的，仍需要您埋点自定义事件。

在埋点元素曝光时，开发人员需要对 View 在当前屏幕上的可见性做逻辑判断，需要监控 View 对象是否在当前可见或者是否再次出现在屏幕上，有一定代码实施难度。

此方案将监控 View 的可见和埋点的触发时机交给 GIO SDK ， 开发者只需要将自定义事件的变量传递给 SDK 即可。

### **2.** **元素的浏览事件相对于旧版更准** <a href="#2-yuan-su-de-liu-lan-shi-jian-xiang-dui-yu-jiu-ban-geng-zhun" id="2-yuan-su-de-liu-lan-shi-jian-xiang-dui-yu-jiu-ban-geng-zhun"></a>

对于用户主动标记 imp 采集的元素，相对于旧版本自动采集会更加准确，我们举例以下两个场景来说明。

#### **场景1** **：** **不同的页面共享同一个元素** <a href="#chang-jing-1-bu-tong-de-ye-mian-gong-xiang-tong-yi-ge-yuan-su" id="chang-jing-1-bu-tong-de-ye-mian-gong-xiang-tong-yi-ge-yuan-su"></a>

![imp场景1](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LsFN-kH\_I1FhypMMhpC-LsGHzPX8zIQyxBkJeEqimage.png)

底部的导航栏在 Tab 页面中是共享元素，即切换 Tab ，底部的导航栏持续可见，在不同的 Tab 页面中是共享元素。

**旧版本：**

导航栏的 imp 事件会分别在对应的四个页面中发送，切换 Tab 页面时虽然底部导航栏持续可见，但是会重复发送。

为什么旧版本会这么统计呢？ 因为 imp 事件的归因和 page 事件强关联，切换了页面，就认为导航栏是这个页面中的元素，不支持多个页面共享元素的情况。

**新版本：**

在用户标记导航栏需要采集后，无论切换 ab 多少次，我们只会在用户第一次可见导航栏，发一次元素浏览事件。

可以认为新版本方案只关心当前元素对于用户是否可见，和页面访问事件 page 无关联。更贴近实际场景，相对旧版本更准。

#### **场景2** **：** **列表元素的展现统计** <a href="#chang-jing-2-lie-biao-yuan-su-de-zhan-xian-tong-ji" id="chang-jing-2-lie-biao-yuan-su-de-zhan-xian-tong-ji"></a>

![imp场景2](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LsFN-kH\_I1FhypMMhpC-LsGIgGsbAd0wdRHzc6Himage.png)

**旧版本：**

GIO 推荐广告位在 `ScrollView` 的最底部，需要用户滑动才能看到，但是页面初始化的时候绘制，只是当前屏幕不可见。

旧版本中只会发送一次 imp 事件，无论随着用户的滑动元素是否再次可见，只有在页面初始化的时候发送此元素的 imp 事件。

**新版本：**

随着用户的滑动手势，元素进入屏幕则触发自动埋点事件，滑动出屏幕后，再滚动回来 View 再次可见依然会发送自动埋点事件。

即为元素对于用户可见几次则发送几次事件。

新版本浏览事件采集的列表，内部的元素展现次数的统计更加准确，更符合业务场景。

### **3.** **提升用户浏览事件采集的性能** <a href="#3-ti-sheng-yong-hu-liu-lan-shi-jian-cai-ji-de-xing-neng" id="3-ti-sheng-yong-hu-liu-lan-shi-jian-cai-ji-de-xing-neng"></a>

旧版本中，无埋点 SDK 将自动采集所有 View 的信息，最终分析时不会分析所有 APP 中的 View，在APP的性能、用户流量上都是一种浪费。

新版本中，SDK 非全量采集所有列表中的元素，只采集用户配置的元素，性能有较大提升。

## 重要配置

{% hint style="info" %}
注意事项

* 注意参数是否合法，与埋点 API 一样，eventID 和事件级变量 JSONObject 都有参数限制要求。
* 在元素展示前调用GIO API，GIO 负责监听元素展示并触发事件，半自动化 IMP 方案 SDK 上传的数据类型为 cstm ，和自定义事件是同种类型，所以**需要您在官网新建对应的事件类型和变量，并且强烈建议使用数据校验工具验证埋点事件。**
* 触发 SDK 自动采集时机： 元素从当前屏幕上不可见到可见。
* 对于被追踪元素上方有其它元素遮挡的情况 ，GrowingIO 仍可能发送该元素的展示事件 （适配这种case会消耗巨大性能，暂时不兼容）。
{% endhint %}

### 标记半自动化采集View元素

#### **markImpression(ImpressionMark mark)** <a href="#markimpression-impressionmark-mark" id="markimpression-impressionmark-mark"></a>

| **参数** | 说明                                                                                                                             |
| ------ | ------------------------------------------------------------------------------------------------------------------------------ |
| mark   | <p><strong>ImpressionMark:</strong> 标记 view 的配置类；</p><p><strong>注意：</strong>运行时标记 view 对象，SDK 不存储标记对象，所以不存在标记一次，永远记录并采集的现象</p> |

| 参数                | 传参方式     | 是否必填                       | 说明                                                                                                                                                                                    |
| ----------------- | -------- | -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| view              | 构造函数传参   | 是                          | **View：**需要标记采集 imp 的 view                                                                                                                                                            |
| eventId           | 构造函数传参   | 是                          | <p><strong>String：</strong>自定义事件标识符；</p><p>非空，长度限制小于等于50；</p><p>SDK 2.4.0以下版本不支持中文，仅支持 0 到 9、a 到 z 以及下划线，并且不能以数字开头</p>                                                                |
| setVariable       | set 方法传参 | 否                          | **String**：用于在Activity范围内唯一标记View，下文有详细解释改字段的用法与原因                                                                                                                                    |
| setGlobalId       | set 方法传参 | 否                          | **String**：用于在Activity范围内唯一标记View，下文有详细解释改字段的用法与原因                                                                                                                                    |
| setDelayTimeMills | set 方法传参 | 否，默认为0（2.9.7版本开始默认值更新为500） | <p><strong>long ：</strong>检测Impression的延迟时间(ms)， 默认不延时；</p><p>是一个性能调优字段, 是允许GIO在界面改变后， 延时一段时间再次进行View的可见性检测判断. 默认为 0 是经过 GIO 性能测试的， 相信能够满足大部分场景的性能要求。 可以将此值设为 200, 300, 400, 500。</p> |

GlobalId 字段的提供主要是为了适配 RecyclerView 这类的可复用 View 对浏览定义的影响。 GIO对View的可见性跟踪默认是对象级别的跟踪，所以默认情况下用户notifyDataSetChange时(即使内容并没有改变)， 由于所有View被重新Bind， 而且由于RecyclerView的复用机制， 并不能保证复用顺序有序, 可能触发多条浏览事件发出， 这显然是不符合预期的。

例如：用户下拉刷新页面，新增了一条 item ，但是列表顺序变了和未刷新前不一致，此时可能会有多条浏览事件发出，不符合预期，所以提供 globalId 方案解决使得只发送列表中可见新出现的元素。

提供以下方法解决此问题:

**1. 调用 Adapter 的 setHasStableIds(true), 并重写 getItemId 方法:**

```javascript
Adapter adapter = new MAdapter();
adapter.setHasStableIds(true);
​
class MyAdapter extends RecyclerView.Adapter<xxx> {
    @Override
    public long getItemId(int position) {
        return position;
    }
}
```

**2. 如果不希望设置 hasStableIds， 可以在标记 markViewImpression 时使用 globalId 字段**

```javascript
...
@Override
public void onBindViewHolder(@NonNull ViewHolder holder, int position) {
    holder.left.setText("position: " + position);
    JSONObject jsonObject = new JSONObject();
    try {
        jsonObject.put("position", position);
    } catch (JSONException e) {
        e.printStackTrace();
    }
    GrowingIO.getInstance().markViewImpression(
            new ImpressionMark(holder.left, "列表项:" + position)
                    .setGlobalId(String.valueOf(position))
                    .setVariable(jsonObject)
    );
}
```

### 停止半自动采集View的浏览事件

#### **stopMarkViewImpression(View markedView)** <a href="#stopmarkviewimpression-view-markedview" id="stopmarkviewimpression-view-markedview"></a>

已经标记的View对象，通知GIO停止标记跟踪View的可见性。

| 参数   | 说明                 |
| ---- | ------------------ |
| view | **View:** 标记 view。 |

### xml的快捷配置方式

{% hint style="danger" %}
使用此方法标记View的浏览时， 请使用MobileDebugger验证， 如果没有发出， 请使用调用接口的形式。
{% endhint %}

同时提供一个在xml中配置GIO imp事件的简单配置, GIO会在视图改变时检测View的tag属性，**如果符合"gio-tag-事件名称" 标准**，此时会调用GrowingIO.getInstance().markViewImpression(new ImpressionMark(thisView, “事件名称")方法。

```javascript
<TextView
            android:text=“black_shirt"
            android:tag=“gio-tag-black_shirt”            
            android:gravity="center"            
            android:textquColor="@android:color/white"            
            android:background="@android:color/black"            
            android:layout_width="match_parent"            
            android:layout_height="300dp" />
```

上边代码片段标记的事件id为: “black\_shirt" ，需要注意的是 Android 中View的 tag可被系统， 第三方框架作为特殊的用途。

### 设置自动采集元素内容

{% hint style="info" %}
Android 无埋点 **SDK 2.8.4** 及以上支持。
{% endhint %}

#### setCollectContent <a href="#setcollectcontent" id="setcollectcontent"></a>

自动采集元素内容，事件变量为 `gio_v`。

| 参数       | 说明                                                                                                               |
| -------- | ---------------------------------------------------------------------------------------------------------------- |
| collectV | <p></p><p>boolean: 是否自动采集元素内容，默认值为 <strong>true</strong>；</p><ul><li>true 采集元素内容</li><li>false 不采集元素内容</li></ul> |

```javascript
//自动采集元素内容并发送埋点事件，默认值为 true 采集元素内容。
GrowingIO.getInstance().markViewImpression(        
                new ImpressionMark(findViewById(R.id.tv_imp_without_v), "btn_buy")
                                .setCollectContent(true)
                                );
```

### 设置半自动浏览View的可见比例

{% hint style="info" %}
Android 无埋点 **SDK 2.8.5** 及以上支持。
{% endhint %}

#### setVisibleScale <a href="#setvisiblescale" id="setvisiblescale"></a>

设置 View 的可见比例，当可见的比例大于等于 visiableScale 则自动触发埋点事件。

| 参数           | 说明                                                                                                                                                           |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| visibleScale | <p><strong>float:</strong> 参数范围在 0-1；</p><ul><li>当为 0 时为可见任意像素则触发埋点事件</li><li>当为 1 时为 View 完全可见则触发埋点事件</li></ul><p><strong>默认值为0，元素任意像素可见发送埋点事件</strong></p> |

```javascript
//当元素大于等于一半可见时，自动采集元素内容并发送埋点事件。
GrowingIO.getInstance().markViewImpression(        
            new ImpressionMark(findViewById(R.id.tv_imp_without_v), "btn_buy")           
                        .setVisibleScale((float) 0.5)
            );
```

## 常用控件代码示例

### 1. View代码示例

对于界面上普通的 View， 例如 Button、ImageView 等，demo如下：

```javascript
Button button = findViewById(R.id.add_to_cart);
GrowingIO.getInstance().markViewImpression(new ImpressionMark(button,"add_cart"));
```

### 2. Banner代码示例

```javascript
class MyAdapter extends PagerAdapter {
​
    @Override
    public void onPageSelected(int position) {
        try {
            GrowingIO.getInstance().markViewImpression(
                    new ImpressionMark(mImageViews.get(position), "Banner")
                            .setVariable(new JSONObject()
                                    .put("content", imageDescription[position])
                                    .put("id", position)
                            )
            );
        } catch (JSONException e) {
            e.printStackTrace();
        }
    }
}
```

### 3. 列表下拉刷新或者局部刷新

列表上局部刷新，或者下拉列表刷新增加个别 item 的时候，我们预期应该发送改变了内容，或者是新增内容的元素的曝光事件。

{% hint style="info" %}
代码示例参考GlobalId字段说明的代码示例。
{% endhint %}

## 常见问题

#### **1. Stop 半自动化 imp 什么时候调用**

业务场景中，不需要再关注某个已经标记采集半自动 imp 的 view 元素。

#### **2. View 是否是完全可见的时候，SDK 才会发送事件？**

默认 View 任意可见像素则自动触发埋点事件。

#### **3.当元素内容发生改变，会发送事件么？**

例如 TextView，当元素内容发生变化，不会再次发送事件。[  \
](https://docs.growingio.com/docs/sdk-integration/android-sdk/api)
