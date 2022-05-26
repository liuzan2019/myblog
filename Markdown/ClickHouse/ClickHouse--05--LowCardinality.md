## 学习链接：

https://clickhouse.com/docs/en/sql-reference/data-types/lowcardinality

## 作用：

改变需要字典编码数据类型的内部形式

LowCardinality是改变数据存储和数据处理规则的上层建筑。

## 语法：

```sql
LowCardinality(data_type)

data_type 可以是String/FixedString/Date/DateTime/除小数之外的数字
```

对一些数据类型来说，LowCardinality是不高效的



## 性能

- LowCardinality类型的使用效率取决于数据的多样性。

- 如果字典包含少于10000个不同的值，那么LowCardinality会有更好的读取和存储效率。

- 如果超过100000个不同值，LowCardinality的性能更差
- 允许或者限制对固定大小为8或更小的数据类型使用LowCardinality，如numeric data types and FixedString(8_bytes_or_less)



## 使用LowCardinality的结果

- 磁盘空间使用效率更高
- RAM消耗更高，取决于字典大小
- 一些方法速度更低，因为额外的编码和解码操作

