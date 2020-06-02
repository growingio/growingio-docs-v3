# 细查用户

## 操作步骤

一. 在顶部导航栏选择“**用户分析 &gt; 用户细查”**，默认展示今日访问用户的用户列表。

{% hint style="success" %}
在用户分群界面，单击进入设定好的某个用户分群后，最下方会列出该群体的所有用户。单击任意一个用户名，即可进入该用户的用户细查页面。
{% endhint %}

![](../../../../.gitbook/assets/image%20%2865%29.png)

二. 在左上方下拉框中选择需要细查用户的用户分群，下方列表展示分群内的用户群体。

{% hint style="success" %}
如没有预先创建分群，也可在此页面单击右上角的**创建分群**，来创建用户分群。
{% endhint %}

三. 单击需要细查的用户ID，进入此用户的细查页面。

**用户细查的界面主要分为四部分：**

![](../../../../.gitbook/assets/image%20%2860%29.png)

> 用户属性

该板块位于界面右上方，展示了用户头像、用户ID、地区、上次访问的设备、最近30天访问次数及最后登录时间。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LIF8-rHaklO4CKVNwXV-LIF8XBmCJE8nKonuij-insights2.jpg)

上次访问设备： 指用户最后一次访问时使用的手持设备，当使用 PC 访问的时，显示的是 Web.

浏览器使用情况：是指用户在30天内使用浏览器的概况。这是一个比例图，分别表示了用户最常使用浏览器的比率。 当比率为：100% 的时候，表示用户仅使用某一种浏览器访问。

> 用**户活跃度趋势图**

这个图反映了用户一段时间内在您产品内的活跃度。其中横坐标表示日期，纵坐标是当天用户所产生的事件总数量。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LIF8-rHaklO4CKVNwXV-LIF8jMLsBGmT8AVQflFinsights3.png)

活跃度趋势图默认显示最近30天的数据，您也可以在右上角的日历中选择任意时间段（不超过30天）来查看活跃度。

除了通过日历选择时间段，您还可以直接在柱图中通过鼠标直接框选一个时间段来放大查看：

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LIF8-rHaklO4CKVNwXV-LIF8ph6i7H8SRfnSfusinsights4.png)

您还可以直接点击某一天的柱图来看这位用户在这一天的事件总数分布：

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LIF8-rHaklO4CKVNwXV-LIF96bSL_rLLxY_rzZBinsights5.png)

继续点击柱图可以继续放大，观察到小时级别、分钟级别甚至秒级别的用户动态。

无论通过日历来选择时间段，或通过框选或点击来放大时间段的时候，“用户访问轨迹” 都会根据这里的时间段而显示对应时间段的行为流。

> 用户访问轨迹

在这里展示了该用户在您的产品内的所有使用行为，这些行为包括打开页面和点击/输入/选择/提交四种互动行为，可以在最上方的“事件筛选”中切换。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LIF0u6WCVRBQ10Sd5QZ-LIF25kvL7GVwOjj6oEuimage.png)

默认会按照日期从近到远的顺序来显示行为轨迹，即最先显示今天的行为轨迹，然后显示昨天的，前天的，更早的行为……

而在一天之内，所有的行为是按照时间顺序从先到后排列的，即在同一天之内，第一行的行为表示用户的第一个行为。例如，在下图的示例中，这位用户先打开了“Growing \| Growing”页面，然后在5秒后点击了“新建”，而不是反过来。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LIF0u6WCVRBQ10Sd5QZ-LIF29byzG9f4EnvQ-Lwimage.png)

所有的行为流中，“访问开始”和“访问结束”都表示一次会话（session）的开始和结束。

除了使用“事件筛选”外，还可以使用最顶部的搜索框来找出特定行为。在搜索框中输入并按回车即可筛选出相应的行为，关键词将会自动以高亮形式出现。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LIF0u6WCVRBQ10Sd5QZ-LIF2CiVMVdae570EfXEimage.png)

> 事件详情

当在“用户访问轨迹”中点击任意一条行为记录，右侧的“事件详情”中将会显示该事件的更多信息。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LIF0u6WCVRBQ10Sd5QZ-LIF2HUHvNzztDdaXdK3image.png)

（上图左为一次打开页面事件的详情，右为一次点击事件的详情）

如果这条记录中相应的页面或点击的元素是曾经被“圈选”过的，那么则会在事件详情中显示【定义】，即这个对应的元素在圈选时保存的标签名字。如果没有被圈选过，则不会显示定义。

