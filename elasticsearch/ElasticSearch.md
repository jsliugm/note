# ElasticSearch

## 安装

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

