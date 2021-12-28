# 导出数据处理建议

## 数据格式

导出数据皆为csv格式：

* 分隔符： ,
* 包围符："
* 转义符：\\

## 处理建议

{% tabs %}
{% tab title="Spark处理" %}
建议下载数据后，将下载的压缩文件放于hdfs的以日期建立目录结构，同一小时或者同一天的数据放在同一目录下，然后通过spark streaming的fileStream接口监控根目录，读取变动的文件内容。

```
streamingContext.fileStream[KeyClass, ValueClass, InputFormatClass](dataDirectory)
```

在依赖中添加：

```
groupId: com.databricksartifactId: spark-csv_2.10version: 1.4.0
```

具体数据操作参考spark-csv([https://github.com/databricks/spark-csv](https://github.com/databricks/spark-csv))
{% endtab %}

{% tab title="Scala/Java程序处理示例" %}
推荐使用 `org.apache.commons.csv` 来处理下载到本地的数据文件，如下面的例子：

```java
import java.io.{BufferedReader, File, FileInputStream, InputStreamReader}
import org.apache.commons.csv.{CSVFormat, CSVParser, QuoteMode}
import scala.collection.JavaConverters._
​
object Test extends App {
  val file = new File("xxx")
  val br = new BufferedReader(new InputStreamReader(new FileInputStream(file)))
  val csvFileFormat = CSVFormat.DEFAULT.withEscape('\\').withQuote('"')
  val csvParser = new CSVParser(br, csvFileFormat)
  val records = csvParser.getRecords
​
  for (record <- records.asScala) {
    val sb = new StringBuilder()
    val length = record.size()
    (0 until length).foreach(i => {
      sb.append(record.get(i))
      sb.append(",")
    })
    println(sb.toString)
  }
}
```
{% endtab %}

{% tab title="Python处理建议示例" %}
```
import csv
​
with open(FILE_NAME, "rb") as f:
    reader = csv.reader(f, quotechar='"', escapechar='\\')
    for line in reader:
        print(line)
```
{% endtab %}
{% endtabs %}

## 导入到数据仓库示例

{% tabs %}
{% tab title="导入到Hive" %}
1. 使用Hive新建外部表，如下图所示。
2. 使用hadoop fs -put /xx.csv /tmp/test\_export/ 将csv放到外部表目录下。

```
CREATE EXTERNAL TABLE TEST_EXPORT
(
sessionId STRING,
time BIGINT,
sendTime BIGINT,
pageTime BIGINT,
domain STRING,
page STRING,
queryParameters STRING,
eventName STRING,
eventNumber DOUBLE,
eventVariable map<string, string>,
loginUserId STRING
)
ROW FORMAT SERDE 'org.apache.hadoop.hive.serde2.OpenCSVSerde'
STORED AS TEXTFILE
location '/tmp/test_export'
tblproperties ("skip.header.line.count"="1", "quote.delim"="\"", "escape.delim"="\\")
```
{% endtab %}

{% tab title="利用Spark导入到其他数据仓库" %}
1. 获取DataFrame，代码如下。
2. 使用databricks提供的函数Load到Hive数据库(这里省去spark和hive的配置)，如： df.select("sessionId", "time", "sendTime", "pageTime", "domain", "page", "queryParameters", "eventName", "eventNumber", "eventVariable", "loginUserId").write.mode("append").insertInto("TEXT\_EXPORT")

```
val df = spark.read
    .option("header","true")
    .option("escape", "\\")
    .option("quote", "\"")
    .csv("filePath")
```
{% endtab %}
{% endtabs %}

## **使用Content-Length进行文件完整性校验 ** <a href="md-5-jin-hang-wen-jian-wan-zheng-xing-xiao-yan" id="md-5-jin-hang-wen-jian-wan-zheng-xing-xiao-yan"></a>

### _**生效日期 : 2020/10/29 21:00:00 开始**_

用户如果对文件完整性有担心，可以对[原始数据导出 API](./)第三步下载时response的headers中的value值**Content-Length**和下载文件的大小进行校验。若校验未通过，可重启第三步，轮询获取，若校验通过，可以解压缩，如果解压出现异常，可重启第三步，轮询获取。
