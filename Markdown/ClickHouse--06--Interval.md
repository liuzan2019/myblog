## 学习链接：

https://clickhouse.com/docs/en/sql-reference/data-types/special-data-types/interval

## INTERVAL

- 数据类型家族
- 表示时间和日期的间隔


## 支持的间隔类型

  - `SECOND`
  - `MINUTE`
  - `HOUR`
  - `DAY`
  - `WEEK`
  - `MONTH`
  - `QUARTER`
  - `YEAR`

### 对每一个间隔类型，都有独立的数据类型对应

```sql
SELECT toTypeName(INTERVAL 4 DAY)

┌─toTypeName(toIntervalDay(4))─┐
│ IntervalDay                  │
└──────────────────────────────┘
```

## 使用：INTERVAL关键词

```sql
SELECT now() as current_date_time, current_date_time + INTERVAL 4 DAY

┌───current_date_time─┬─plus(plus(now(), toIntervalDay(4)), toIntervalHour(3))─┐
│ 2019-10-23 11:16:28 │                                    2019-10-27 14:16:28 │
└─────────────────────┴────────────────────────────────────────────────────────┘
```

## 使用：函数toIntervalDay()

```sql
select now() + toIntervalDay(4)

┌─plus(now(),toIntervalDay(4))─┐
│ 2022-04-26 19:53:15.000      │
└──────────────────────────────┘
```

