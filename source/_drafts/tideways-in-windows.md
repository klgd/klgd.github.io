---
title: tideways-in-windows
tags:
  - tideways
  - php
categories:
  - PHP
date: 2017-03-22 10:55:27
---

下载
[https://s3-eu-west-1.amazonaws.com/qafoo-profiler/downloads/testing/tideways-windows-4.0.1p3.zip](https://s3-eu-west-1.amazonaws.com/qafoo-profiler/downloads/testing/tideways-windows-4.0.1p3.zip)  


```
./daemon_windows_386.exe --address="127.0.0.1:8136"
```




复制 `php_tideways-*.dll` 到php扩展目录（ext 目录），重命名为 php_tideways.dll   

php.ini

```
extension=php_tideways.dll
tideways.connection=tcp://127.0.0.1:8136
```

安装mongodb的php扩展
https://pecl.php.net/package/mongodb


添加mongodb数据库
```
mongo
$ mongo
> use xhprof
switched to db xhprof
> db.results.ensureIndex( { 'meta.SERVER.REQUEST_TIME' : -1 } )
{
        "createdCollectionAutomatically" : true,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1,
        "operationTime" : Timestamp(0, 0)
}
> db.results.ensureIndex( { 'profile.main().wt' : -1 } )
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1,
        "operationTime" : Timestamp(0, 0)
}
> db.results.ensureIndex( { 'profile.main().mu' : -1 } )
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 3,
        "numIndexesAfter" : 4,
        "ok" : 1,
        "operationTime" : Timestamp(0, 0)
}
> db.results.ensureIndex( { 'profile.main().cpu' : -1 } )
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 4,
        "numIndexesAfter" : 5,
        "ok" : 1,
        "operationTime" : Timestamp(0, 0)
}
> db.results.ensureIndex( { 'meta.url' : 1 } )
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 5,
        "numIndexesAfter" : 6,
        "ok" : 1,
        "operationTime" : Timestamp(0, 0)
}
>
```

安装xhgui

```
git clone https://github.com/maxincai/xhgui.git
cd xhgui
php install.php
```


