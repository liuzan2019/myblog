创建表字段使用comment添加描述（不能使用双引号）

```sql
create table app_insight_new.comment_test(
name String not null comment '名字',
create_date datetime not null comment '创建日期'
)ENGINE = MergeTree
PARTITION BY toYYYYMM(create_date)
ORDER BY name;
```

