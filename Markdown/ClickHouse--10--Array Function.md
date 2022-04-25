学习链接：

https://www.jianshu.com/p/5e8205edc7d9

https://clickhouse.com/docs/en/sql-reference/functions/array-functions

neighbor

作用

> 获取某一列前后相邻数据，第二个参数控制前后相邻的距离

示例

```sql
SELECT a, neighbor( a,-1 ) from (SELECT arrayJoin( [1,2,3,6,34,3,11] ) as a,'u' as  b)  

a |neighbor(a, -1)|
--+---------------+
 1|              0|
 2|              1|
 3|              2|
 6|              3|
34|              6|
 3|             34|
11|              3|

SELECT arrayJoin( [1,2,3,6,34,3,11] ) as a,'u' as  b

a |b|
--+-+
 1|u|
 2|u|
 3|u|
 6|u|
34|u|
 3|u|
11|u|
```

arrayJoin

行变列，对数组进行展开操作

arraySort

> 对数组进行排序，降序用arrayReverseSort

arrayFilter

> 过滤出数组满足条件的数据

arrayEnumerate

> 返回数组下标

arrayDifference

> 计算数组中前后两个元素的差

arrayReduce

> 对数组进行聚合操作

```sql
SELECT arrayReduce('avg', [1,2,3,6,34,3,11] )
```

arraySlice

> 对数组进行切割 ，后面两个参数分别是切割的offset和切割长度

SELECT arraySlice( [1,2,3,6,34,3,11] , -3, 2)

```sql
SELECT arraySlice( [1,2,3,6,34,3,11] , -3, 2)

arraySlice([1, 2, 3, 6, 34, 3, 11], -3, 2)|
------------------------------------------+
[34,3]                                    |
```

