# V3接口概述

## V3接口说明 <a href="tong-ji-shu-ju-dao-chu-fen-lei" id="tong-ji-shu-ju-dao-chu-fen-lei"></a>

V3接口与 [统计数据导出API](../statistics-api/) 区别主要是交互方式由同步改为异步。

V3接口适用于图表数据较大的场景，通过异步交互的方式，避免了客户端长期持有http连接的弊病。

V3接口还重新定义了url的规范，后续GrowingIO所有的Open API都将遵循这个新的规范。

V3接口目前还在持续补充，很快会覆盖现有的 [统计数据导出API](../statistics-api/) 。

## V3接口交互方式 <a href="tong-ji-shu-ju-dao-chu-fen-lei" id="tong-ji-shu-ju-dao-chu-fen-lei"></a>

![](<../../../.gitbook/assets/image (126).png>)

## 统计数据V3接口导出分类 <a href="tong-ji-shu-ju-dao-chu-fen-lei" id="tong-ji-shu-ju-dao-chu-fen-lei"></a>

| 统计数据导出分类 | 相关接口 | 使用限制 |
| -------- | ---- | ---- |

| 事件分析下载 | [​获取事件分析数据​](definition/getevent.md) | <ul><li>单图下载每秒限速2次</li><li>单张图表单次下载数据量上限为20万条</li></ul> |
| ------ | ------------------------------------ | ------------------------------------------------------- |

| 漏斗分析下载 | [​获取漏斗分析数据​](definition/getfunnel.md) | 单图下载每秒限速2次 |
| ------ | ------------------------------------- | ---------- |

| 留存分析下载 | [​获取留存分析数据​](definition/getretention.md) | 单图下载每秒限速2次 |
| ------ | ---------------------------------------- | ---------- |

| 分布分析下载 | [获取分布分析数据](definition/huo-qu-fen-bu-fen-xi-shu-ju.md) | 单图下载每秒限速2次 |
| ------ | ----------------------------------------------------- | ---------- |

| 获取用户分群下载链接 | [获取用户分群的下载链接](definition/get-segmentations.md) | 下载每秒限速2次 |
| ---------- | ---------------------------------------------- | -------- |

| 获取用户标签下载链接 | [获取用户标签的下载链接](definition/huo-qu-yong-hu-biao-qian-de-xia-zai-lian-jie.md) | 下载每秒限速2次 |
| ---------- | ------------------------------------------------------------------------- | -------- |

* 本章节中API 的 project\_uid（项目UID）、dashboard\_id（看板ID）、chart\_id（事件分析单图ID）、funnel\_id（漏斗分析单图ID）、frequency\_id（分布分析单图ID）、retention\_id（留存分析单图ID） 字段，均可在项目页面url中找到，如："[https://www.growingio.com/admin/projects/nxog09md/dashboard/YoX28w7R](https://www.growingio.com/admin/projects/nxog09md/dashboard/YoX28w7R)" 中的 "nxog09md" 和 "YoX28w7R" 分别是 project\_id 和dashboard\_id。
  * dashboard\_id获取方式
    * 在项目URL中获取
    * 通过[获取看板列表](../statistics-api/definition/get-charts.md)API根据project\_id获取所有看板信息。
  * chart\_id、funnel\_id、frequency\_id、retention\_id的获取方式
    * 在项目URL中获取；
    * 通过[获取看板中的图表信息](../statistics-api/definition/get-chartinfo.md)API，根据dashboard\_id获取当前看板的所有图表信息，返回的信息中会包含图表ID，图表类型等信息。
  * segmentation\_id的获取方式
    * 通过[获取分群列表](../statistics-api/definition/get-segm.md)；
    * 在项目URL中获取。
  * tag\_id的获取方式
    * 在项目URL中获取；
* 统计数据导出的延迟一般为 30 分钟，比如导出早上 8 点到 9 点之间的数据时，一般需要 9:30 才能统计完毕。另外，每天凌晨因为需要运行天级别的统计任务，此时前一天的统计数据大概有 3-4 小时的延迟，建议在早上6点后进行导出任务。
* dashboard\_id 通过URL获取图示：

![](<../../../.gitbook/assets/image (142).png>)

* chart\_id、funnel\_id、frequency\_id、retention\_id 通过URL获取图示：

![](<../../../.gitbook/assets/image (141).png>)

* tag\_id通过URL获取图示：

![](<../../../.gitbook/assets/image (146).png>)

