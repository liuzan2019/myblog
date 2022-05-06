学习链接

https://clickhouse.com/docs/en/sql-reference/statements/select/limit-by

语法

- `LIMIT [offset_value, ]n BY expressions`
- `LIMIT n OFFSET offset_value BY expressions`

跟LIMIT 是两个不同的语句

根据expressions，跳过前offset_value条记录，选择前n个记录

案例1：

```sql
SELECT number%50 AS n FROM numbers(150) ORDER BY n LIMIT 12
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
3|
3|

--根据n的值，每个限选2个
SELECT * FROM (SELECT number%50 AS n FROM numbers(150) ORDER BY n LIMIT 12)  LIMIT 2 by n
n|
-+
0|
0|
1|
1|
2|
2|
3|
3|
```

案例2：

```sql
--建表
CREATE TABLE limit_by(id Int, val Int) ENGINE = Memory;
--插入数据
INSERT INTO limit_by VALUES (1, 10), (1, 11), (1, 12), (2, 20), (2, 21);

SELECT * FROM limit_by ORDER BY id, val LIMIT 2 BY id
┌─id─┬─val─┐
│  1 │  10 │
│  1 │  11 │
│  2 │  20 │
│  2 │  21 │
└────┴─────┘

SELECT * FROM limit_by ORDER BY id, val LIMIT 1, 2 BY id
┌─id─┬─val─┐
│  1 │  11 │
│  1 │  12 │
│  2 │  21 │
└────┴─────┘
```



Limit 和 Limit By 同时使用

```sql
SELECT
    domainWithoutWWW(URL) AS domain,
    domainWithoutWWW(REFERRER_URL) AS referrer,
    device_type,
    count() cnt
FROM hits
GROUP BY domain, referrer, device_type
ORDER BY cnt DESC
LIMIT 5 BY domain, device_type
LIMIT 100
--Limit 跟在 Limit By 后
```

