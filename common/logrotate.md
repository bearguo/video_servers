# logrotate 日志转储工具
logrotate是Linux提供的自带日志转储工具，默认配置为每天运行一次，在`/etc/cron.daily`文件夹中有配置

# 配置文件位置
`/etc/logrotate.d/`

# 使用方法
`man logrotate`

# 配置文件格式
下面是SRS的日志转储配置：
```shell
/usr/local/srs/objs/srs.log {
    su root root
    rotate 7
    missingok
    daily
    size 50M
    dateext
    dateformat -%Y-%m-%d
    copytruncate
}
```

