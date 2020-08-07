# SDK性能问题

## 1. SDK编译时性能和时间消耗过大怎么办？

GrowingIO Android SDK 的编译时耗时取决于您的项目大小，我们的原理是字节码插桩\(使用Transform API\)。

从clean项目， 执行assembleDebug， 如果添加了GrowingIO的SDK， 会大约增加50%的时间， 如果执行assembleRelease， 添加GrowingIO SDK 大约会增加30%的时间。 可以看出GrowingIO确实会影响您的编译时长，尤其是在项目比较大的情况。 如果您感觉到明显的编译耗时长，我们提供了一个在开发期间 GrowingIO 不参与编译的配置，如下：

1.在 Project 项目中，gradle.properties 文件内添加

```java
# true GrowingIO 参与编译，false 不参与编译
gioenable = true
```

2.在 Module 级别的 build.gradle 文件中增加配置

```java
android {
    defaultConfig {
        resValue("string", "growingio_project_id", "您的项目ID")
        resValue("string", "growingio_url_scheme", "您的URL Scheme")
        // 增加 gioenable 的配置
        resValue("string", "growingio_enable", project.gioenable)
    }
}
```

{% hint style="danger" %}
SDK 2.7.4及以下版本不支持Instant Run，请开发者开发期间配置gioenable=false，即可使用Instant Run。
{% endhint %}

{% hint style="danger" %}
上线时，一定要将gradle.properties文件中的gioenable改为true，否则我们无法采集数据。
{% endhint %}

## 2. SDK 数据发送的策略是什么？

![](../../../../.gitbook/assets/image%20%28122%29.png)

