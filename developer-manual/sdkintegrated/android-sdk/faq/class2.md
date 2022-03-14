# 无埋点SDK中埋点API使用问题

## 自定义页面级变量事件发送失败？

此问题常发生在 `Activity` 中包含多个 `Fragment` 的页面中。

* 首先需要确认当前页面发送的页面访问(`page`)事件是哪个 `Fragment` ，您可以参照[这三种方式确认当前的页面访问事件](class1.md#growingio-dui-yu-yi-dong-duan-ye-mian-de-ding-yi)。
* 如果此 `Fragment` 不是您业务上认为的页面，可以使用 `ignoreFragment` 不认为此 Fragment 可以作为页面访问事件发送。
* 注意：`setPageVariable` 接口参数中的 Activity 或者 Fragment **必须为当前页面访问事件页面**，即可成功发送自定义页面事件。
