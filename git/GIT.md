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

![image-20220506111051360](E:\softdev\github\note\git\git001.png)