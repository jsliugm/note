# GIT

## 同步代码到github 和 码云

打开bash

```shell
cd ~
mkdir .ssh
ssh-keygen -t rsa -C "jsliugm@gmail.com" -f "pc_github_id_rsa" 
ssh-keygen -t rsa -C "jsliugm@163.com" -f "pc_gitee_id_rsa"
```

将xxx.pub内容复制到页面ssh公钥

创建config文件，解决ssh冲突

```
vi config
# gitee
Host gitee.com
HostName gitee.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/pc_gitee_id_rsa

# github
Host github.com
HostName github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/pc_github_id_rsa
```

测试

```shell
ssh -T git@gitee.com
ssh -T git@github.com
```

关联远程库

```shell
git remote add origin sshURL
```

## 小乌龟同步远程失败问题

修改ssh client路径为git目录下的ssh.exe

![image-20220506111051360](.\git001.png)





## wincred 、manager、manager-core 有什么区别？

GPT答案：

> wincred、manager和manager-core是Git凭证存储的三种不同实现方式。这些实现方式在不同的操作系统上运行，且其区别如下：
>
> wincred：是在Windows上使用的Git凭证存储。它使用Windows凭证管理器来存储和管理凭证信息，包括用户名和密码等。如果您正在使用Windows系统，则可以使用此选项来存储Git凭证。
>
> manager：是Git凭证存储的标准实现方式，可以在多种操作系统上使用。它使用Git提供的凭证管理器来存储和管理凭证信息。此选项需要Git版本在1.7.10或更高。
>
> manager-core：是Git凭证存储的轻量级实现方式，仅限于Unix/Linux系统上使用。它不需要安装任何其他软件包，仅依赖于现有的Linux密码存储系统（例如PAM）来存储和管理凭证信息。此选项需要Git版本在2.11或更高。
>
> 总之，wincred适用于Windows操作系统，manager是标准的Git凭证存储方式，可以跨平台使用，而manager-core是在Unix/Linux系统上使用的轻量级实现方式。



代理设置

git config --global http.proxy socks5://127.0.0.1:7890
