学习链接：

https://clickhouse.com/docs/en/sql-reference/statements/select/limit

语法

返回前 m 条数据

```sql
LIMIT m 
```

跳过前 n 条数据后，返回 m 条数据

```sql
LIMIT n, m
或者
LIMIT m OFFSET n
```

根据order by字段，如果第m行和后面的值相同，则后面相同的行一并显示
```sql
LIMIT n, m WITH TIES

SELECT * FROM (SELECT number%50 AS n FROM numbers(150)) ORDER BY n LIMIT 10
n|
-+
0|
0|
0|
1|
1|
1|
2|
2|
2|
3|

SELECT * FROM (SELECT number%50 AS n FROM numbers(150)) ORDER BY n LIMIT 5 WITH TIES 
n|
-+
0|
0|
0|
1|
1|
1|

SELECT * FROM (SELECT number%50 AS n FROM numbers(150)) ORDER BY n LIMIT 4, 5 WITH TIES 
n|
-+
1|
1|
2|
2|
2|

SELECT * FROM (SELECT number%50 AS n FROM numbers(150)) ORDER BY n LIMIT 4, 3 WITH TIES 
n|
-+
1|
1|
2|
2|
2|
```

