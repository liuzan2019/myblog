# [Git文件提交，Windows格式与Linux格式互转设置][1]
Git在commit和checkout时CRLF都转换为LF
>```git config --global core.autocrlf true```

Git在commit时CRLF转换为LF，在checkout时不转换
>```git config --global core.autocrlf input```

Git在commit时都保留crlf
>```git config --global core.autocrlf false```

拒绝文件包含混合换行符
>```git config --global core.safecrcf true```


允许文件包含混合换行符
>```git config --global core.safecrcf false```

文件包含混合换行符时告警
>```git config --global core.safecrcf warn```


[1]:https://blog.csdn.net/huihuikuaipao_/article/details/100183521