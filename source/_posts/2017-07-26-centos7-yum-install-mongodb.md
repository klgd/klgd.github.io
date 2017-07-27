---
title: centos7下使用yum安装mongodb3.4
tags:
  - null
categories:
  - null
date: 2017-07-26 13:08:02
---


## 配置yum源

`vi /etc/yum.repos.d/mongodb-3.4.repos`

```
[mongodb-org-3.4]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/3.4/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-3.4.asc
```
<!-- more -->

这里可以修改 gpgcheck=0, 省去gpg验证

## 安装   
`yum  install -y mongodb-org`

配置文件在：/etc/mongod.conf   
数据文件在：/var/lib/mongo   
日志文件在：/var/log/mongodb   

启动mongod   
`systemctl start mongod.service`

停止mongod   
`systemctl stop mongod.service`

开机启动   
`systemctl enable mongod.service`

使用 命令  `mongo`

```
[root@centos7 ~]# mongo 127.0.0.1:27017
MongoDB shell version v3.4.6
connecting to: mongodb://127.0.0.1:27017
MongoDB server version: 3.4.6
Server has startup warnings: 
2017-07-26T11:14:38.412+0800 I CONTROL  [initandlisten] 
2017-07-26T11:14:38.412+0800 I CONTROL  [initandlisten] ** WARNING: Access control is not enabled for the database.
2017-07-26T11:14:38.412+0800 I CONTROL  [initandlisten] **          Read and write access to data and configuration is unrestricted.
2017-07-26T11:14:38.412+0800 I CONTROL  [initandlisten] 
2017-07-26T11:14:38.412+0800 I CONTROL  [initandlisten] 
2017-07-26T11:14:38.412+0800 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/enabled is 'always'.
2017-07-26T11:14:38.412+0800 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
2017-07-26T11:14:38.412+0800 I CONTROL  [initandlisten] 
2017-07-26T11:14:38.412+0800 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/defrag is 'always'.
2017-07-26T11:14:38.412+0800 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
```

