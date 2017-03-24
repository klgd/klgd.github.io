---
title: win7下安装MongoDB
tags:
  - MongoDB
  - win7
categories:
  - MongoDB
date: 2017-03-22 10:12:57
---


1. 首先到[官方网站](https://www.mongodb.org/dl/win32/ "MongoDB")下载安装包   
我是win7 64位系统，所有选择下载 [http://downloads.mongodb.org/win32/mongodb-win32-x86_64-latest.zip](http://downloads.mongodb.org/win32/mongodb-win32-x86_64-latest.zip)   

2. 解压到D:\MongoDB目录   
为了可以在全局命令行使用mongodb，我们将“D:\MongoDB\bin”添加到环境变量中   

3.  --dbpath指定数据库存放目录   
在D:\MongoDB目录下新建data目录，然后命令行执行
```
mongod --dbpath "D:\MongoDB\data"
```

执行后，命令行窗口会打印一些启动信息，最后一行显示为如下信息时表示启动成功了

>2017-03-22T10:34:33.937+0800 I NETWORK  [thread1] waiting for connections on port 27017

4. 连接MongoDB   

打开另一个命令行 
```
mongo
```
看到如下类似信息，表示连接成功了
```
MongoDB shell version v3.5.4-106-g914bbbd
connecting to: mongodb://127.0.0.1:27017
MongoDB server version: 3.5.4-106-g914bbbd
Welcome to the MongoDB shell.
For interactive help, type "help".
For more comprehensive documentation, see
        http://docs.mongodb.org/
Questions? Try the support group
        http://groups.google.com/group/mongodb-user
Server has startup warnings:
2017-03-22T10:41:04.084+0800 I CONTROL  [initandlisten]
2017-03-22T10:41:04.085+0800 I CONTROL  [initandlisten] ** NOTE: This is a development version (3.5.4-106-g914bbbd) of M
ongoDB.
2017-03-22T10:41:04.086+0800 I CONTROL  [initandlisten] **       Not recommended for production.
2017-03-22T10:41:04.087+0800 I CONTROL  [initandlisten]
2017-03-22T10:41:04.090+0800 I CONTROL  [initandlisten] ** WARNING: Access control is not enabled for the database.
2017-03-22T10:41:04.091+0800 I CONTROL  [initandlisten] **          Read and write access to data and configuration is u
nrestricted.
2017-03-22T10:41:04.093+0800 I CONTROL  [initandlisten]
2017-03-22T10:41:04.094+0800 I CONTROL  [initandlisten] Hotfix KB2731284 or later update is not installed, will zero-out
 data files.
2017-03-22T10:41:04.100+0800 I CONTROL  [initandlisten]
>
```
