tuple用作

临时的字段分组

lambda方法的某些形式函数

查询结果tuple情况

json格式之外的其他文本，值都是在括号中用逗号分隔

json格式时，输出一个方括号的数组

创建tuple

tuple(T1, T2, ...)

```sql
SELECT tuple(1,'a') AS x, toTypeName(x)

┌─x───────┬─toTypeName(tuple(1, 'a'))─┐
│ (1,'a') │ Tuple(UInt8, String)      │
└─────────┴───────────────────────────┘
```

获取tuple的元素的值

```sql
CREATE TABLE named_tuples (`a` Tuple(s String, i Int64)) ENGINE = Memory;
INSERT INTO named_tuples VALUES (('y', 10)), (('x',-10));

--通过tuple的元素的名字获取value
SELECT a.s FROM named_tuples; 
┌─a.s─┐
│ y   │
│ x   │
└─────┘

--通过tuple的元素的下表获取value，下表从1开始
SELECT a.2 FROM named_tuples;

┌─tupleElement(a, 2)─┐
│                 10 │
│                -10 │
└────────────────────┘
```