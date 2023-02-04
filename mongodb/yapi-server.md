# 1、搭建虚拟机，参考：VMware虚拟机CentOS桥接实现局域网互通.md
# 2、安装需要的命令
## 2.1 安装vim命令
查看是否已安装vim命令
```shell script
rpm -qa |grep vim
```
![](https://img-blog.csdnimg.cn/0520749e932e48e29d2b57629854f263.png#pic_left)

如果缺少上图的安装包，则缺少什么就执行对应的命令例如：
```shell script
yum -y install vim-enhanced
yum -y install vim-minimal
```
如果都没有，则全部安装
```shell script
yum -y install vim*
```

## 3、
