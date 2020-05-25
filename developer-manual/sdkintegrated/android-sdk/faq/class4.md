# 圈选问题

## 1. 集成 SDK 后，Activity 受影响

是否在集成 SDK 时配置 GrowingIO `<intent-filter/>` 代码块中的 Activity 中使用了 `getIntent` 呢？

解答： 请在您的逻辑中过滤掉 Gio 的 Intent ，我们的 Intent 大致格式是这样：

`growing.xxxxxxxxxxx://growing/oauth2/token?loginToken=xxxxx.........`

请您在代码逻辑中判断如果是以 `growing` 开头的 `scheme` 不处理它，代码示例：

```java
// 请注意自己判断 intent 是否为空
Uri data = intent.getData();
if (data.getScheme().startsWith("growing.")){    
    Log.d(TAG, "GrowingIO url scheme, not process");
}
```

