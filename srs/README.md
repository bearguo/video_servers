# SRS服务器配置
## 系统最大文件打开数
```bash
$ vim /etc/systemd/system.conf #打开系统配置文件
...
DefaultLimitNOFILE=65535      #这里需要修改
#DefaultLimitAS=
#DefaultLimitNPROC=
DefaultLimitNPROC=65535   #这里也需要修改
...
$ reboot #重启后生效
$ ulimit -a #查看是否更改成功
```

## SRS切片生成HLS文件的路径挂载到内存中
**很重要！否则硬盘会被频繁读写，造成损坏**
```bash
$ vim /etc/fstab #打开磁盘挂载配置文件
# 加入一行：
tmpfs  /usr/local/srs/objs/nginx/html/live  tmpfs  defaults,size=2G,mode=0755   0  0

$ mount -a -f -v #模拟执行挂载新的配置文件，确保没有配置错误
$ mount -a #执行挂载新的配置文件
```

