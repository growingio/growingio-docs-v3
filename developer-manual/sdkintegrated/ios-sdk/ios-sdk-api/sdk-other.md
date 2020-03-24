# 埋点SDK支持的其他接口

{% hint style="info" %}
**GrowingIO 埋点 SDK 仅自动采集设备信息和您埋点内容数据，对比无埋点 SDK ，埋点 SDK 少很多 API， 请勿在埋点 SDK 中调用无埋点 SDK 接口。**
{% endhint %}

```java
1，若使用加密功能,请在UI元素初始化之前设置此函数
+ (void)setEncryptStringBlock:(NSString*(^)(NSString*string))block;
​
2，deeplink广告落地页参数回调设置
+ (void)registerDeeplinkHandler:(void(^)(NSDictionary*params, NSError*error))handler;
​
3，Universallink广告落地页参数回调设置
+ (void)registerUniversallinkHandler:(void(^)(NSDictionary*params, NSError*error))handler;
​
4，该函数请在main函数第一行调用APP启动后将不允许修改采集模式
+ (void)setAspectMode:(GrowingAspectMode)aspectMode;
+ (GrowingAspectMode)getAspectMode;

5，设置发送数据的时间间隔（单位为秒）
+ (void)setFlushInterval:(NSTimeInterval)interval;
+ (NSTimeInterval)getFlushInterval;

6，/**
 判断链接是否为deeplink链接，SDK2.8.10开始支持
 @param url 传入的网址
 @return YES:是deeplink链接 NO:不是deeplink链接
*/
+ (BOOL)isDeeplinkUrl:(NSURL *)url;

7，/**
 手动处理deeplink链接，SDK2.8.10开始支持
 @param url 传入的网址
 @param callback deeplink广告落地页参数回调, params 为解析正确时回调的参数, processTime为从app被deeplink唤起到handler回调的时间(单位秒), error 为解析错误时返回的参数.
 callback若传nil:回调结果将从method <registerDeeplinkHandler:>中设置的handler返回
 callback若不为nil:回调结果只从当前的callback中返回
 @return YES:是deeplink链接 NO:不是deeplink链接
*/
+ (BOOL)doDeeplinkByUrl:(NSURL *)url callback:(void(^)(NSDictionary *params, NSTimeInterval processTime, NSError *error))callback;
```

