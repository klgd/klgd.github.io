---
title: php-xhgui-tideways
tags:
  - Tideways
  - Xhgui
  - PHP
categories:
  - PHP
date: 2017-07-27 09:32:27
---

mongodb安装

tideways安装
https://tideways.io/profiler/docs/setup/installation

php mongodb tideways扩展 
配置php.ini
```
[mongodb]
extension=mongodb.so
[tideways]
extension=tideways.so
;不需要自动加载，在程序中控制就行
tideways.auto_prepend_library=0

```

mongodb数据库

```
$ mongo
 > use xhprof
 > db.results.ensureIndex( { 'meta.SERVER.REQUEST_TIME' : -1 } )
 > db.results.ensureIndex( { 'profile.main().wt' : -1 } )
 > db.results.ensureIndex( { 'profile.main().mu' : -1 } )
 > db.results.ensureIndex( { 'profile.main().cpu' : -1 } )
 > db.results.ensureIndex( { 'meta.url' : 1 } )
 ```
 
web界面
```
$ git clone https://github.com/maxincai/xhgui.git
$ cd xhgui
$ php install.php
 ```
 
 配置php
 
.user.ini
`auto_prepend_file=/home/wwwroot/xhgui/external/header.php`

https://bugs.php.net/bug.php?id=53611


config

```
'profiler.enable' => function() {
        if(!empty($_GET['debug'])){
            return True;
        }else{
            // 1%采样
            return rand(1, 100) === 42;
        }
    }
 ```