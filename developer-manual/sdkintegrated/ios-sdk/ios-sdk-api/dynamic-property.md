# 动态添加属性说明

{% hint style="success" %}
SDK版本要求：iOS 无埋点SDK &gt;=2.x
{% endhint %}

## 1. UIView 增加属性

```java
// 手动标识该view不要追踪
@property (nonatomic, assign) BOOL growingAttributesDonotTrack; 
​
// 手动标识该view不要追踪它的值，默认是NO，特别的UITextView，UITextField，
//UISearchBar默认是YES
//对button、label无效
@property (nonatomic, assign) BOOL growingAttributesDonotTrackValue; 
​
//手动标识该view的取值  比如banner广告条的id 可以放在banner按钮的任意view上
@property (nonatomic, copy)   NSString *growingAttributesValue; 
​
// 手动标识SDCycleScrollView组件的bannerIds  如若使用,请在创建SDCycleScrollView实例对象后,
//立即赋值;(如果不进行手动设置,SDK默认会采集banner的imageName或者imageURL)
@property (nonatomic, strong)  NSArray<NSString *> *growingSDCycleBannerIds;
​
 // 手动标识该view的附加属性  该值可被子节点继承
@property (nonatomic, copy)   NSString* growingAttributesInfo;
```

## 2. UIViewController 增加属性

```java
// 手动标识该vc的附加属性  该值可被子节点继承
@property (nonatomic, copy)   NSString* growingAttributesInfo; 
​
// 手动标识该页面的标题，必须在该UIViewController显示之前设置
@property (nonatomic, copy)   NSString* growingAttributesPageName;
```

