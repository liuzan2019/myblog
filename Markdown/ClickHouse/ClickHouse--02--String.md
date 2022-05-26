## 学习链接：

https://clickhouse.com/docs/en/sql-reference/data-types/string

## String的特点

String是一组字节的集合

ClickHouse中String是任意长度的，长度无限制

String 是用来替换其他数据库中VARCHAR, BLOB, CLOB和其他类型

ClickHouse没有编码的概念

## 使用

一般推荐使用UTF-8，如果你的终端也是UTF-8的编码，那你读写的时候就不用做转换

某些String相关的方法，一般都有假设String是一组UTF-8字节的变体；

比如length方法有lengthUTF8的变体方法