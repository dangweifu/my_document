#[VMware 虚拟机 CentOS 桥接实现局域网互通](https://www.csdn.net/tags/OtDaEg1sODM3MDgtYmxvZwO0O0OO0O0O.html)
##1、修改虚拟机网络适配器为桥接模式
虚拟机网络适配器默认是NAT模式，修改为桥接模式即把虚拟机看成和主机在同一个网段的另一台物理主机

![设置](https://img-blog.csdn.net/20181024170646804?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxbXpvbml3Y2Q=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

![虚拟机设置](https://img-blog.csdn.net/20181024170707465?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxbXpvbml3Y2Q=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##2、修改桥接网卡，选择主机网卡

![编辑](https://img-blog.csdn.net/20181024171005399?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxbXpvbml3Y2Q=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

![虚拟网络编辑器](https://img-blog.csdn.net/20181024171023590?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxbXpvbml3Y2Q=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##3、修改虚拟机IP地址
Windows查看主机IP地址

![ipconfig](https://img-blog.csdn.net/20181024171453438?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxbXpvbml3Y2Q=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

CentOS查看虚拟机IP地址

![ifconfig](https://img-blog.csdn.net/20181024171755304?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxbXpvbml3Y2Q=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

注意：虚拟机可能会因为Windows宿主机防火墙原因无法ping通宿主机，最简单粗暴方式直接关闭宿主机的防火墙。其余方式请自行百度解决。

##4、安装虚拟机中没有的一些命令
###4.1 安装vim
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
###4.2 安装wget
```shell script
yum -y install wget
```