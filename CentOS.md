# CentOS

## 阿里源

```shell
sudo mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
sudo wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
sudo yum makecache
sudo yum -y update
```

## 安装chrome

在目录 /etc/yum.repos.d/ 下新建文件 google-chrome.repo

```shell
cd /ect/yum.repos.d/
vim google-chrome.repo
```

内容为：

[google-chrome]
name=google-chrome
baseurl=http://dl.google.com/linux/chrome/rpm/stable/$basearch
enabled=1
gpgcheck=1
gpgkey=https://dl-ssl.google.com/linux/linux_signing_key.pub

```shell
yum -y install google-chrome-stable --nogpgcheck
```

chrome driver ？

