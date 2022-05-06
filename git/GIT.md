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