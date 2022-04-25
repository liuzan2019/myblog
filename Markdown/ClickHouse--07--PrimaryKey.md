## 学习链接：

https://clickhouse.com/docs/en/engines/table-engines/mergetree-family/mergetree#primary-keys-and-indexes-in-queries



Primary Key

表由数据部分(数据分区)组成，数据分区数据又根据主键进行排序



当数据插入表中的时候，会创建独立的数据分区，各个分区根据主键的顺序进行排序



在后台，ClickHouse会为了更高效的存储合并数据分区



## 数据两种存储形式

> 数据的存储形式由表引擎的`min_bytes_for_wide_part`和`min_rows_for_wide_part`参数控制。

1. `Wide`

   > 每个字段都存储在单独的文件中

2. `Compact`

   > 所有的字段都存储在一个文件中



## 存储形式使用情况

### `Compact`情况：

 + 数据的长度小于`min_bytes_for_wide_part`设置的值

+ 数据分区的行数小于`min_rows_for_wide_part`

### `Wide`存储情况

+ 没有设置`min_bytes_for_wide_part`和`min_rows_for_wide_part`参数

+ 不符合Compact存储情况

## Granule

> 数据分区逻辑上又分成Granule
>
> Granule是ClickHouse读取数据时的最小可见数据集
>
> Granule只会包含整数行数据，不会将数据行再分割开来
>
> Granule第一行用主键的值标记
>
> 数据分区会创建一个索引文件来存储这些标记

## Granule大小

+ Granule的大小表引擎的`index_granularity`和`index_granularity_bytes`参数限制

+ 1个Granule存储的数据行范围 [1, index_granularity] ，取决于数据行的大小，默认8192

+ 数据行的大小可以超过`index_granularity_bytes`

> 如果**单行数据**大小大于其值，则`index_granularity_bytes`等于数据行的大小

