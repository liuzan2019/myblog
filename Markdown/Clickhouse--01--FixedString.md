## 学习链接：

https://clickhouse.com/docs/en/sql-reference/data-types/fixedstring

## 声明column为FixedString语法

<column_name> FixedString(N)

N为自然数

当数据的长度正好为N字节时，FixedString类型是高效的。在所有其他情况下，那么可能会降低效率。

## 使用FixedString类型字段样例：

> - IP addresses（`FixedString(16)` for IPv6）  

> - 语言码（ru_RU, en_US）

> - 货币码（USD, RUB）

> - 哈希的二进制表示(`FixedString(16)` for MD5, `FixedString(32)` for SHA256)


  UUID存储使用UUID数据类型

## 插入数据时

- 少于N 字节会使用null字节补齐
- 超过N字节会抛出异常

## 查询

查询数据时，Click House不会移除null字节

如果使用where条件，我们应该加上null字节去匹配FixedString字段值

## 样例：

如下表，name是一个FixedString(2)字段

┌─name──┐
│ b     │
└───────┘

如下SQL不会返回任何数据

SELECT \* FROM FixedStringTable WHERE a = 'b' 

正确查询如下：

SELECT * FROM FixedStringTable WHERE a = 'b\0'



