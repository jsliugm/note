# Hadoop

[TOC]



## 安装

### 网卡配置修改

```shell
su
vim /etc/sysconfig/network-scripts/ifcfg-ens33
```

![image-20231206163645324](D:\softdev\github\note\hadoop\image-20231206163645324.png)

### 修改主机名称

vim /etc/hostname

修改为hadoop100

### 修改hosts

vim /etc/hosts

192.168.126.100	hadoop100

192.168.126.101	hadoop101

192.168.126.102	hadoop102

192.168.126.103	hadoop103

192.168.126.104	hadoop104

192.168.126.105	hadoop105

192.168.126.106	hadoop106

192.168.126.107	hadoop107

192.168.126.108	hadoop108



### 创建用户



```shell
useradd atguigu
passwd atguigu
```

![image-20231206174320358](D:\softdev\github\note\hadoop\image-20231206174320358.png)



### 安装epel-release

yum install -y epel-release