

## 学习链接：

https://clickhouse.com/docs/en/sql-reference/data-types/array

## Array(t)

- 任意数据类型的数组
- 下标从1开始

## 创建：

### 使用函数创建

```text
array(T)
```
#### 样例

```sql
SELECT array(1, 2) AS x, toTypeName(x)

结果：
┌─x─────┬─toTypeName(array(1, 2))─┐
│ [1,2] │ Array(UInt8)            │
└───────┴─────────────────────────┘
```

### 使用方括号创建

```tex
 [ ]
```
#### 样例


```sql
SELECT [1, 2] AS x, toTypeName(x)

┌─x─────┬─toTypeName([1, 2])─┐
│ [1,2] │ Array(UInt8)       │
└───────┴────────────────────┘
```



## 数据及其类型

- 最多100万个元素
- 动态创建数组，ClickHouse会将数组参数定义为可以存储所列出参数的最窄数据类型
- 如果存在NULL或 Nullable字段的值，数组元素的类型也是Nullable
- 如果不能确定数据类型，则会产生一个异常，如  "SELECT array(1, 'a')"

### 例子1：

```sql
SELECT array(1, 2, NULL) AS x, toTypeName(x)

结果：
┌─x──────────┬─toTypeName(array(1, 2, NULL))─┐
│ [1,2,NULL] │ Array(Nullable(UInt8))        │
└────────────┴───────────────────────────────┘
```

### 例子2：

```sql
SELECT array(1, 'a')

结果：
Received exception from server (version 1.1.54388):
Code: 386. DB::Exception: Received from localhost:9000, 127.0.0.1. DB::Exception: There is no supertype for types UInt8, String because some of them are String/FixedString and some of them are not.
```

## Array的大小

- 使用size0子列计算array的大小，多个维度数组使用 sizeN-1，N是想要的维度

```sql
CREATE TABLE t_arr (`arr` Array(Array(Array(UInt32)))) ENGINE = MergeTree ORDER BY tuple();

INSERT INTO t_arr VALUES ([[[12, 13, 0, 1],[12]]]);

SELECT arr.size0, arr.size1, arr.size2 FROM t_arr;
结果：
┌─arr.size0─┬─arr.size1─┬─arr.size2─┐
│         1 │ [2]       │ [[4,1]]   │
└───────────┴───────────┴───────────┘
```





