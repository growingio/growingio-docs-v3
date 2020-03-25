# 分析活跃用户

## 操作步骤

一. 在顶部导航栏选择“**用户分析 &gt; 活跃用户分析”**，进入活跃用户分析页面。

二. 定义活跃用户。

例如 GrowingIO 的博客，是一个内容型产品，主要为用户提供数据分析、增长、学习等内容。 \(地址：[http://blog.growingio.com](http://blog.growingio.com/)）；针对这个博客，活跃用户的定义，是至少浏览过1 篇博客文章详情页的访问用户。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LeFqloPMUTBF0qe_llO-LeG22_TdqY4PIbQfQN8image.png)

三. 展示符合活跃定义条件的昨日、过去 7 天、过去 30 天的用户量，并且分别提供相对上周期的变化比率。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LeFqloPMUTBF0qe_llO-LeG5kl-MjnBnyvtxQSKimage.png)

## 活跃用户详细数据

完成定义用户后可生成活跃用户的详细数据表，包含以下多个部分。

### 构成和趋势 <a id="cha-kan-huo-yue-yong-hu-de-gou-cheng-he-qu-shi-yi-ji-bian-wei-bu-huo-yue-de-bian-hua"></a>

包含活跃用户趋势表、活跃用户构成趋势图、活跃用户构成占比趋势图、活跃用户下个周期转为不活跃用户的数量和构成趋势图、活跃用户转化为不活跃用户占比趋势图。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LjxYTffY8ZXoTZmXXyU-LjxcYTt4EaKXHTp098Eimage.png)

​

这个部分需要几张图一起解读，就可以非常清晰的了解活跃用户数量、构成、占比、以及在下个周期变为不活跃的变化情况和趋势。

例如： 06/10 ~ 06/16 这一周的活跃用户（至少看过一次博客详情页）是2119，其中新用户是1612，回流用户是 337，留存用户是 170。分别占比 15.9%、76.1%、8.02%；到了06/17 ~ 06/23这一周，06/10 ~ 06/16 这一周的活跃用户有 2073个变为了不活跃，其中新用户是 1573个，老用户（即留存+回流用户）是 464个。分别占06/10 ~ 06/16 这一周的活跃用户的 74.2% 和 21.9%。

选择活跃用户的时间和时间颗粒度来查看活跃用户趋势，计算构成。对于部分高频产品来说，关注颗粒度会在日级别；对于工具型，一般在周级别；对于低频型，颗粒度在月级别。

每周期的活跃用户构成包括以下三种类型：

* 回流用户：上周期不满足活跃定义，但本周期活跃的用户；
* 新增用户：本周期满足活跃定义的新用户；
* 留存用户：本周期和上周期都满足活跃定义的用户。

每周期的不活跃用户构成：

* 不活跃新用户：本周期满足活跃条件的新用户，在下周期不满足活跃条件的用户。
* 不活跃老用户：本周期满足活跃条件的老用户，在下周期不满足活跃条件的用户。

通过数据图可以看出，博客产品的较多用户都是新用户，回流用户和留存用户占比在20%多左右。在部分运营推广活动期间，新用户的数量较多。博客产品基本不能使用户每周访问（周流失率在 90%以上），不论是新用户还是老用户，流失占比都很高。

### 了解增长指数 <a id="le-jie-zeng-chang-zhi-shu"></a>

如果用一个数据展示用户增长状态，GrowingIO推荐使用“增长指数”。它展示了在每个周期（天、周、月）获取的增长用户与这个周期流失的用户的比。比率表示：流失一个活跃用户的同时 （即一个活跃用户不再满足活跃条件），会增加几个活跃用户。

**增长指数 =（当期新增用户数+当期回流用户数）/ 当期活跃但是在下周期不活跃的用户数**

当增长指数 &gt;1 时，表明即使用户量存在流失，净活跃用户量也是在增长的。 当增长指数 &lt;1 时，表明净活跃用户量在降低。 你需要关注增长指数的变化趋势，尤其是 &lt;1 时重点关注。

注：当时间颗粒度是周和月时，会存在最后一个周期没有结束的情况（例如今天是周三，但是一周结束需要到周天，所以上周的活跃用户，只有在本周周天结束的时候，才能知道有多少用户本周不再活跃了），此时数据点和线会显示为虚线。

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LeFqloPMUTBF0qe_llO-LeGBBcwoSqL4VSlAHE1image.png)

**净增用户 = \(当期新增用户数 + 当期回流用户数\) - 当期活跃但在下周期不活跃用户数**

### 拆解维度 <a id="chai-jie-bu-tong-wei-du-fen-xi-huo-yue-yong-hu-zhong-de-bu-tong-gou-cheng"></a>

分析活跃用户中的不同构成。

例如，选择回流用户，选择用访问来源拆分，可以知道不活跃用户再次活跃的用户来源。  
2的

![](https://docs.growingio.com/.gitbook/assets/-LGNxeGABUADKiTWTaEM-LeFqloPMUTBF0qe_llO-LeGFxi_JwfdalYxhtbRimage.png)

