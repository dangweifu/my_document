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

切换到networks-scripts文件夹下

```shell script
cd /etc/sysconfig/network-scripts
```

![network-scripts](https://img-blog.csdn.net/20181024172004595?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxbXpvbml3Y2Q=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

找到对应上面的ens33配置文件,打开编辑

```shell script
vim ifcfg-ens33
```
![](https://img-blog.csdn.net/20181024172548814?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxbXpvbml3Y2Q=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

BOOTPROT0=static(静态IP)

IPADDR (虚拟机IP地址)

NETMASK (子网掩码 同主机)

GATEWAY (网关地址 同主机)

DNS (DNS 同主机)

##4、测试
测试ip设置是否生效 ping 主机IP

![](https://img-blog.csdn.net/20181024173312713?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxbXpvbml3Y2Q=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)