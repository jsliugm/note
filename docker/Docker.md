# Docker

## Docker的常用命令

### 可视化

- portainer

```shell
docker run -d -p 8088:9000 --restart=always -v /var/run/docker.sock:/var/run/docker.sock --name prtainer --privileged=true portainer/portainer
```

## DockerFile

### DockerFile介绍 

![img](E:\softdev\github\note\docker\dockerfile001)

### DockerFile指令

![img](E:\softdev\github\note\docker\dockerfile002)

### DockerFile构建过程

创建dockerfile文件

```shell
FROM centos

MAINTAINER liuguangming<jsliugm@163.com>

ENV MYPATH /usr/local

WORKDIR $MYPATH

RUN yum -y install im

RUN yum -y install net-tools

EXPOSE 80

CMD echo $MYPATH

CMD echo "----end----"

CMD /bin/bash
```

构建命令：

docker build -f filepath -t imageName:tag

运行：

```shell
docker run -it mycentos:0.1
```

本地镜像的变更历史：

```shell
docker history imageid
```

CMD和ENTRYPOINT区别：

测试CMD

```shell
# dockerfile内容
FROM centos
MAINTAINER liuguangming<jsliugm@163.com>
CMD ["ls","-a"]

# 构建镜像
docker build -f cmd-test -t cmdtest . 

# run运行
docker run cmdtest                                                                                                           

# 控台输出内容
.
..
.dockerenv
bin
dev
etc
home
lib
```

测试ENTRYPOINT

```shell
# 编写dockerfile
FROM centos
ENTRYPOINT ["ls","-a"]

# 构建镜像
docker build -f entrypoint-test -t entrypointtest . 

# 运行
docker run entrypointtest -l

# 控制台输出内容

total 56
drwxr-xr-x   1 root root 4096 Apr 25 03:38 .
drwxr-xr-x   1 root root 4096 Apr 25 03:38 ..
-rwxr-xr-x   1 root root    0 Apr 25 03:38 .dockerenv
lrwxrwxrwx   1 root root    7 Nov  3  2020 bin -> usr/bin
drwxr-xr-x   5 root root  360 Apr 25 03:38 dev
drwxr-xr-x   1 root root 4096 Apr 25 03:38 etc
drwxr-xr-x   2 root root 4096 Nov  3  2020 home
lrwxrwxrwx   1 root root    7 Nov  3  2020 li

```

### 实战：tomcat镜像

```shell
# Dockerfile 
FROM centos
MAINTAINER liuguangming<xx.qq.com>
COPY readme.txt /usr/local/readme.txt
ADD jdk-8u192-linux-x64.tar.gz /usr/local/
ADD apache-tomcat-8.5.78.tar.gz /usr/local/

RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
RUN yum -y install vim
RUN yum -y install net-tools

ENV MYPATH /usr/local
WORKDIR $MYPATH

ENV JAVA_HOME /usr/local/jdk1.8.0_192
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
ENV CATALINA_HOME /usr/local/apache-tomcat-8.5.78
ENV CATALINA_BASH /usr/local/apache-tomcat-8.5.78
ENV PATH $PATH:$JAVA_HOME/bin:$CATALINA_HOME/lib;$CATALINA_HOME/bin

EXPOSE 8080

CMD /usr/local/apache-tomcat-8.5.78/bin/startup.sh && tail -f /usr/local/apache-tomcat-8.5.78/logs/catalina.out

# 构建
docker build -t centos_tomcat8_jdk1.8:0.1 .

# 启动容器
docker run -d -p 9090:8080 --name mytomcat -v /home/unniverse/docker/tomcat/webapps/test:/usr/local/apache-tomcat-8.5.78/webapps/test -v /home/universe/docker/tomcat/logs:/usr/local/apache-tomcat-8.5.78/logs centos_tomcat8_jdk1.8:0.1
```



docker run -d -p 9091:8080 --name mytomcat2 centos_tomcat8_jdk1.8:0.1

## docker网络

命令：

docker network ls

docker network inspect



### docker 自定义网络

~~docker link 过时~~

```shell
# 创建网络mynet
docker network create mynet
# 启动容器
docker run -d -p 8081:8080 --network mynet --name mytomcat1 centos_tomcat8_jdk1.8:0.1
docker run -d -p 8082:8080 --network mynet --name mytomcat2 centos_tomcat8_jdk1.8:0.1
# 进入mytomcat2
docker exec -it mytomcat2 bash
# 从mytomcat2 ping mytomcat1
ping mytomcat1
```





## Docker Compose

### 安装

https://docs.docker.com/compose/install/

```shell
DOCKER_CONFIG=${DOCKER_CONFIG:-$HOME/.docker}
mkdir -p $DOCKER_CONFIG/cli-plugins
# 不使用代理可能无法连接github
curl -SL https://github.com/docker/compose/releases/download/v2.4.1/docker-compose-linux-x86_64 -o $DOCKER_CONFIG/cli-plugins/docker-compose
# 使用代理
curl -x http://192.168.249.1:7890 -SL https://github.com/docker/compose/releases/download/v2.4.1/docker-compose-linux-x86_64 -o $DOCKER_CONFIG/cli-plugins/docker-compose

# 对二进制文件应用可执行权限：
chmod +x $DOCKER_CONFIG/cli-plugins/docker-compose
# 测试安装。
docker compose version
```

### 卸载

```shell
rm $DOCKER_CONFIG/cli-plugins/docker-compose
```

### Compose概念

一个文件：

docker-compose.yml

两个要素 :

服务（service）应用容器实例，比如mysql容器、redis容器。

工程（project）由一组关联的应用容器组成的一个完整业务单元，在docker-compose.yml文件中定义。

### Compose使用步骤



### Compose常用命令



### Compose编排微服务