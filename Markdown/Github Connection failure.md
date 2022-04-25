## 学习链接：

https://www.cnblogs.com/marchxd/p/15513569.html

## 背景

Github网站打不开

## 解决办法

host文件地址：C:\Windows\System32\drivers\etc

在host文件中添加如下内容：

```text
15.164.81.167 github.com
52.192.72.89 github.com
127.0.0.1 update.netsarang.com
127.0.0.1 www.netsarang.com
127.0.0.1 www.netsarang.co.kr
127.0.0.1 sales.netsarang.com
127.0.0.1 transact.netsarang.com
```

