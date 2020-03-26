# 导出数据处理建议

## 数据处理建议

数据处理建议采用Hive或者Spark平台工具，若是需要导入自有BI平台，可能需要进一步调整数据格式（csv转成其他符合数据处理需求的格式），针对以上的需求，给出相应的数据处理建议。

{% hint style="info" %}
注意不要以逗号为分隔符进行处理，csv数据格式以引号外的逗号为分隔符。
{% endhint %}

## 处理方式

{% tabs %}
{% tab title="Spark" %}
建议下载数据后，将下载的压缩文件放于hdfs的以日期建立目录结构，同一小时或者同一天的数据放在同一目录下，然后通过spark streaming的fileStream接口监控根目录，读取变动的文件内容。

```text
streamingContext.fileStream[KeyClass, ValueClass, InputFormatClass](dataDirectory)
```

在依赖中添加：

```text
roupId: com.databricks
artifactId: spark-csv_2.10
version: 1.4.0
```

具体数据操作参考spark-csv\([https://github.com/databricks/spark-csv](https://github.com/databricks/spark-csv)\)
{% endtab %}

{% tab title="Hive" %}
可以参考Hive对CSV数据操作的支持 [https://cwiki.apache.org/confluence/display/Hive/CSV+Serde](https://cwiki.apache.org/confluence/display/Hive/CSV+Serde)​

目前暂未测试该方式～

```text
create external table xxx
```
{% endtab %}
{% endtabs %}

## 数据格式调整处理

以java为例

新建maven project，在prm.xml中添加以下依赖

```text
    <dependency>
      <groupId>org.apache.commons</groupId>
      <artifactId>commons-compress</artifactId>
      <version>1.12</version>
    </dependency>
    <!-- https://mvnrepository.com/artifact/org.apache.commons/commons-csv -->
    <dependency>
      <groupId>org.apache.commons</groupId>
      <artifactId>commons-csv</artifactId>
      <version>1.4</version>
    </dependency>
```

而后在读取数据的方法中：

```text
    GzipCompressorInputStream stream = new GzipCompressorInputStream(new BufferedInputStream(new FileInputStream("data/test.gz")));
​
    Reader reader = new InputStreamReader(stream);
    Iterable<CSVRecord> records = CSVFormat.DEFAULT.parse(reader);
    for (CSVRecord record : records) {
        System.out.println(record);
    }
```

上例中，数据读取依赖于commons-compress与commons-csv库，同样在python中有类似的数据处理库。

