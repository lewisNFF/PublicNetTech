sshfs
======================
我们可以使用ssh登录机器，使用sftp上下载文件。很多工具集成了两者，可以非常方便地让我们可以朝目标主机上下载数据。

公网有一台VPS主机，硬盘比较小，随便一放就可以放满。家里的PC的硬盘倒是很大，这两个能不能结合一下。 把家里的硬盘映射到VPS主机，让主机想读写本地文件一样读写家里的PC的硬盘呢？答案是可以。    
本文讲解如何映射硬盘到VPS。

##原理图


## 首先得先了解frp
教程请参考[github frp中文文档](https://github.com/fatedier/frp/blob/master/README_zh.md)


## 挂载文件系统
```
sshfs -p 6022 -o reconnect,transform_symlinks pi@localhost:/home/pi/Documents ./pi-dir
```

