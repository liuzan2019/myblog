INTERSECT

返回第一个查询和第二个查询的交集

两个查询需要匹配字段的数量/顺序/类型

结果可能包含重复的数据行

多个INTERSECT表达式，如果没有括号，则从左至右执行

优先级比UNION和EXCEPT语句更高

```sql
SELECT number FROM numbers(3,6)
number|
------+
     3|
     4|
     5|
     6|
     7|
     8|

SELECT number FROM numbers(1,10)
number|
------+
     1|
     2|
     3|
     4|
     5|
     6|
     7|
     8|
     9|
    10|
    

```

