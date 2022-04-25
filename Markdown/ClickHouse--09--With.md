## 学习链接：

https://clickhouse.com/docs/en/sql-reference/statements/select/with

## 作用：

在SELECT语句中提供使用`WITH`语句的结果

## 语法：

```sql
WITH <expression> AS <identifier>
```

```sql
WITH <identifier> AS <subquery expression>
```

## 样例：

### 常量表达式用作变量

```sql
WITH '2019-08-01 15:23:00' as ts_upper_bound
SELECT *
FROM hits
WHERE
    EventDate = toDate(ts_upper_bound) AND
    EventTime <= ts_upper_bound;
```

### 重用子查询表达式

```sql
WITH test1 AS (SELECT i + 1, j + 1 FROM test1)
SELECT * FROM test1;
```

### 使用标量子查询的值

```sql
/* this example would return TOP 10 of most huge tables */
WITH
    (
        SELECT sum(bytes)
        FROM system.parts
        WHERE active
    ) AS total_disk_usage
SELECT
    (sum(bytes) / total_disk_usage) * 100 AS table_disk_usage,
    table
FROM system.parts
GROUP BY table
ORDER BY table_disk_usage DESC
LIMIT 10;
```

### 从SELECT子句的字段列表逐出表达式结果

```sql
WITH sum(bytes) as s
SELECT
    formatReadableSize(s),
    table
FROM system.parts
GROUP BY table
ORDER BY s;
```

