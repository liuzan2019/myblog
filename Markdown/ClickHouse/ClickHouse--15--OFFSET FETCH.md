学习链接

https://clickhouse.com/docs/en/sql-reference/statements/select/offset

语法

```sql
OFFSET offset_row_count {ROW | ROWS}] [FETCH {FIRST | NEXT} fetch_row_count {ROW | ROWS} {ONLY | WITH TIES}]
```

`OFFSET`：从查询结果集返回记录行前，明确需要跳过的行数

`FETCH`：明确返回最大的记录行数

`ONLY`：用于返回被`OFFSET`忽略行后面的数据行，这种情况下和`LIMIT`是一样的

```sql
--这两个语句等价
SELECT * FROM test_fetch ORDER BY a OFFSET 1 ROW FETCH FIRST 3 ROWS ONLY;

SELECT * FROM test_fetch ORDER BY a LIMIT 3 OFFSET 1;
```

`WITH TIES`：用于`ORDER BY`返回结果集后，返回最后一个位置额外的数据行