# ElasticSearch

[TOC]

## 问题思考

倒排索引如何找到实际存放的位置？



## 安装

### 容器方式安装

https://hub.docker.com/_/elasticsearch

```shell
docker network create somenetwork
docker pull elasticsearch:7.8.0

docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.8.0
```



### 本地安装

官网下载直接启动，浏览器访问端口9200。

![image-20220430193323680](E:\softdev\github\note\elasticsearch\es001.png)

安装可视化界面 es head

1. 下载地址：https://github.com/mobz/elasticsearch-head/

2. 启动

   ```shell
   npm install
   npm run start
   ```

3. 解决跨域问题，配置es

   ```shell
   http.cors.enabled: true
   http.cors.allow-origin: "*"
   ```

4. 重启es



## 

## 对比传统数据库

![img](E:\softdev\github\note\elasticsearch\es004.png)

## Restful

https://www.elastic.co/guide/en/elasticsearch/reference/7.6/docs.html

### 创建索引

```shell
PUT /索引名/类型名/文档id

{请求体}
```

![image-20220505195746479](E:\softdev\github\note\elasticsearch\es002.png)

完成索引创建、数据插入。

![image-20220505200145583](E:\softdev\github\note\elasticsearch\es003.png)

### 数据类型

<img src="E:\softdev\github\note\elasticsearch\es005.png" alt="img"  />

### 自定义字段类型

![image-20220505201524679](E:\softdev\github\note\elasticsearch\es006.png)

### 获取索引结构

![image-20220505201959849](E:\softdev\github\note\elasticsearch\es007.png)



![image-20220505205815103](E:\softdev\github\note\elasticsearch\es008.png)

### 更新数据



### 默认类型

![image-20220506153154398](E:\softdev\github\note\elasticsearch\es009.png)

扩展：GET _cat/indices

### 修改文档

方法一：修改所有字段

![image-20220506153544194](E:\softdev\github\note\elasticsearch\es010.png)

方法二：只修改指定字段

![image-20220506162825329](E:\softdev\github\note\elasticsearch\es012.png)



### 获取get

![image-20220506162511553](E:\softdev\github\note\elasticsearch\es011.png)