## 学习链接：

https://clickhouse.com/docs/en/sql-reference/data-types/uuid

## UUID

- UUID，即通用唯一标识（universally unique identifier）
- 16字节的数字

## 插入：

没有具体指定UUDID的值时，UUID的值都是0，如下：

00000000-0000-0000-0000-000000000000

正常插入数值如下：

61f0c404-5cb3-11e7-907b-a6006ad3dba0

## 如何产生一个UUID：

使用 [generateUUIDv4](https://clickhouse.com/docs/en/sql-reference/functions/uuid-functions) 方法

## 使用函数

UUID支持String类型支持的方法，如min，max，count

不支持算术运算，如sun，avg