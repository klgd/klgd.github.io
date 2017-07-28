---
title: centos安装php-apm
tags:
  - null
categories:
  - null
date: 2017-07-28 10:58:06
---


[php-apm](https://github.com/patrickallaert/php-apm) 是一个PHP的应用性能管理（APM）。它不需要对应用程序的代码进行任何修改，让我们方便地捕捉到错误信息，并提供错误追踪回溯，获取请求的统计内存、CPU、响应时间的统计信息，并提供可视化的展示。。

<!-- more -->

## 安装apm

### pecl安装   

>这里我只开启了Sqlite3的支持

```
[root@centos7 ~]# pecl install apm
WARNING: channel "pecl.php.net" has updated its protocols, use "pecl channel-update pecl.php.net" to update
downloading APM-2.1.3.tgz ...
Starting to download APM-2.1.3.tgz (33,188 bytes)
.....done: 33,188 bytes
14 source files, building
running: phpize
Configuring for:
PHP Api Version:         20160303
Zend Module Api No:      20160303
Zend Extension Api No:   320160303
Enable Sqlite3 support [yes] : 
Enable MariaDB/MySQL support [yes] : no
Enable Socket support [yes] : no
Enable Statsd support [yes] : no
building in /tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3
running: /tmp/pear/temp/APM/configure --with-php-config=/usr/local/php/bin/php-config --with-sqlite3 --with-mysql=no --enable-socket=no --enable-statsd=no
checking for grep that handles long lines and -e... /usr/bin/grep
checking for egrep... /usr/bin/grep -E
checking for a sed that does not truncate output... /usr/bin/sed
checking for cc... cc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for cc option to accept ISO C89... none needed
checking how to run the C preprocessor... cc -E
checking for icc... no
checking for suncc... no
checking whether cc understands -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for PHP prefix... /usr/local/php
checking for PHP includes... -I/usr/local/php/include/php -I/usr/local/php/include/php/main -I/usr/local/php/include/php/TSRM -I/usr/local/php/include/php/Zend -I/usr/local/php/include/php/ext -I/usr/local/php/include/php/ext/date/lib
checking for PHP extension directory... /usr/local/php/lib/php/extensions/no-debug-non-zts-20160303
checking for PHP installed headers prefix... /usr/local/php/include/php
checking if debug is enabled... no
checking if zts is enabled... no
checking for re2c... no
configure: WARNING: You will need re2c 0.13.4 or later if you want to regenerate PHP parsers.
checking for gawk... gawk
checking whether to enable apm support... yes, shared
checking enable support for sqlite3... yes
checking enable support for MySQL... no
checking enable support for statsd... no
checking enable support for socket... no
checking enable the debug file... no
checking set default sqlite3 default DB path... no
checking for the location of libz... no
checking for sqlite3 files in default path... found in /usr
checking for SQLite 3.*... checking for sqlite3_open in -lsqlite3... yes
checking location of default sqlite3 DB... "/var/php/apm/db"
checking for ld used by cc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from cc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if cc supports -fno-rtti -fno-exceptions... no
checking for cc option to produce PIC... -fPIC
checking if cc PIC flag -fPIC works... yes
checking if cc static flag -static works... no
checking if cc supports -c -o file.o... yes
checking whether the cc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no

creating libtool
appending configuration tag "CXX" to libtool
configure: creating ./config.status
config.status: creating config.h
running: make
/bin/sh /tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/libtool --mode=compile cc  -I. -I/tmp/pear/temp/APM -DPHP_ATOM_INC -I/tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/include -I/tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/main -I/tmp/pear/temp/APM -I/usr/local/php/include/php -I/usr/local/php/include/php/main -I/usr/local/php/include/php/TSRM -I/usr/local/php/include/php/Zend -I/usr/local/php/include/php/ext -I/usr/local/php/include/php/ext/date/lib  -DHAVE_CONFIG_H  -g -O2   -c /tmp/pear/temp/APM/apm.c -o apm.lo
mkdir .libs
 cc -I. -I/tmp/pear/temp/APM -DPHP_ATOM_INC -I/tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/include -I/tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/main -I/tmp/pear/temp/APM -I/usr/local/php/include/php -I/usr/local/php/include/php/main -I/usr/local/php/include/php/TSRM -I/usr/local/php/include/php/Zend -I/usr/local/php/include/php/ext -I/usr/local/php/include/php/ext/date/lib -DHAVE_CONFIG_H -g -O2 -c /tmp/pear/temp/APM/apm.c  -fPIC -DPIC -o .libs/apm.o
/bin/sh /tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/libtool --mode=compile cc  -I. -I/tmp/pear/temp/APM -DPHP_ATOM_INC -I/tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/include -I/tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/main -I/tmp/pear/temp/APM -I/usr/local/php/include/php -I/usr/local/php/include/php/main -I/usr/local/php/include/php/TSRM -I/usr/local/php/include/php/Zend -I/usr/local/php/include/php/ext -I/usr/local/php/include/php/ext/date/lib  -DHAVE_CONFIG_H  -g -O2   -c /tmp/pear/temp/APM/backtrace.c -o backtrace.lo
 cc -I. -I/tmp/pear/temp/APM -DPHP_ATOM_INC -I/tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/include -I/tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/main -I/tmp/pear/temp/APM -I/usr/local/php/include/php -I/usr/local/php/include/php/main -I/usr/local/php/include/php/TSRM -I/usr/local/php/include/php/Zend -I/usr/local/php/include/php/ext -I/usr/local/php/include/php/ext/date/lib -DHAVE_CONFIG_H -g -O2 -c /tmp/pear/temp/APM/backtrace.c  -fPIC -DPIC -o .libs/backtrace.o
/bin/sh /tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/libtool --mode=compile cc  -I. -I/tmp/pear/temp/APM -DPHP_ATOM_INC -I/tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/include -I/tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/main -I/tmp/pear/temp/APM -I/usr/local/php/include/php -I/usr/local/php/include/php/main -I/usr/local/php/include/php/TSRM -I/usr/local/php/include/php/Zend -I/usr/local/php/include/php/ext -I/usr/local/php/include/php/ext/date/lib  -DHAVE_CONFIG_H  -g -O2   -c /tmp/pear/temp/APM/driver_sqlite3.c -o driver_sqlite3.lo
 cc -I. -I/tmp/pear/temp/APM -DPHP_ATOM_INC -I/tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/include -I/tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/main -I/tmp/pear/temp/APM -I/usr/local/php/include/php -I/usr/local/php/include/php/main -I/usr/local/php/include/php/TSRM -I/usr/local/php/include/php/Zend -I/usr/local/php/include/php/ext -I/usr/local/php/include/php/ext/date/lib -DHAVE_CONFIG_H -g -O2 -c /tmp/pear/temp/APM/driver_sqlite3.c  -fPIC -DPIC -o .libs/driver_sqlite3.o
/bin/sh /tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/libtool --mode=link cc -DPHP_ATOM_INC -I/tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/include -I/tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/main -I/tmp/pear/temp/APM -I/usr/local/php/include/php -I/usr/local/php/include/php/main -I/usr/local/php/include/php/TSRM -I/usr/local/php/include/php/Zend -I/usr/local/php/include/php/ext -I/usr/local/php/include/php/ext/date/lib  -DHAVE_CONFIG_H  -g -O2   -o apm.la -export-dynamic -avoid-version -prefer-pic -module -rpath /tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/modules  apm.lo backtrace.lo driver_sqlite3.lo -lsqlite3
cc -shared  .libs/apm.o .libs/backtrace.o .libs/driver_sqlite3.o  -lsqlite3  -Wl,-soname -Wl,apm.so -o .libs/apm.so
creating apm.la
(cd .libs && rm -f apm.la && ln -s ../apm.la apm.la)
/bin/sh /tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/libtool --mode=install cp ./apm.la /tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/modules
cp ./.libs/apm.so /tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/modules/apm.so
cp ./.libs/apm.lai /tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/modules/apm.la
PATH="$PATH:/sbin" ldconfig -n /tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/modules
----------------------------------------------------------------------
Libraries have been installed in:
   /tmp/pear/temp/pear-build-rootNsvyxI/APM-2.1.3/modules

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------

Build complete.
Don't forget to run 'make test'.

running: make INSTALL_ROOT="/tmp/pear/temp/pear-build-rootNsvyxI/install-APM-2.1.3" install
Installing shared extensions:     /tmp/pear/temp/pear-build-rootNsvyxI/install-APM-2.1.3/usr/local/php/lib/php/extensions/no-debug-non-zts-20160303/
running: find "/tmp/pear/temp/pear-build-rootNsvyxI/install-APM-2.1.3" | xargs ls -dils
100818730   0 drwxr-xr-x 3 root root     17 7月  28 10:39 /tmp/pear/temp/pear-build-rootNsvyxI/install-APM-2.1.3
 68835720   0 drwxr-xr-x 3 root root     19 7月  28 10:39 /tmp/pear/temp/pear-build-rootNsvyxI/install-APM-2.1.3/usr
101659046   0 drwxr-xr-x 3 root root     17 7月  28 10:39 /tmp/pear/temp/pear-build-rootNsvyxI/install-APM-2.1.3/usr/local
   581135   0 drwxr-xr-x 3 root root     17 7月  28 10:39 /tmp/pear/temp/pear-build-rootNsvyxI/install-APM-2.1.3/usr/local/php
 34343477   0 drwxr-xr-x 3 root root     17 7月  28 10:39 /tmp/pear/temp/pear-build-rootNsvyxI/install-APM-2.1.3/usr/local/php/lib
 68835722   0 drwxr-xr-x 3 root root     24 7月  28 10:39 /tmp/pear/temp/pear-build-rootNsvyxI/install-APM-2.1.3/usr/local/php/lib/php
101844652   0 drwxr-xr-x 3 root root     39 7月  28 10:39 /tmp/pear/temp/pear-build-rootNsvyxI/install-APM-2.1.3/usr/local/php/lib/php/extensions
   969759   0 drwxr-xr-x 2 root root     20 7月  28 10:39 /tmp/pear/temp/pear-build-rootNsvyxI/install-APM-2.1.3/usr/local/php/lib/php/extensions/no-debug-non-zts-20160303
   969761 152 -rwxr-xr-x 1 root root 154232 7月  28 10:39 /tmp/pear/temp/pear-build-rootNsvyxI/install-APM-2.1.3/usr/local/php/lib/php/extensions/no-debug-non-zts-20160303/apm.so

Build process completed successfully
Installing '/usr/local/php/lib/php/extensions/no-debug-non-zts-20160303/apm.so'
install ok: channel://pecl.php.net/APM-2.1.3
Extension apm enabled in php.ini

```

如果出现了如下错误：

```
checking set default sqlite3 default DB path... no
checking for the location of libz... no
checking for sqlite3 files in default path... not found
configure: error: Please reinstall the sqlite
```

请先安装`sqlite-devel`

```
yum -y install sqlite-devel
```

修改php.ini， apm.so依赖于json.so，如果之前没有加载，则应先加载

```
[apm]
extension="apm.so"
apm.sqlite_enabled=1
apm.sqlite_stats_enabled=1
; The directory containing the "events" file
apm.sqlite_db_path="/var/php/apm/db/"
; Error reporting level specific to the SQLite3 driver, same level as for PHP's *error_reporting*
apm.sqlite_error_reporting=E_ALL|E_STRICT
```

然后重启` php-fpm`

## 可视化 web前端

php-apm提供了一个可视化数据的web前端 [https://github.com/patrickallaert/php-apm-web](https://github.com/patrickallaert/php-apm-web)


将 [https://github.com/patrickallaert/php-apm-web/archive/master.zip](https://github.com/patrickallaert/php-apm-web/archive/master.zip) 解压到web服务器，或者使用git clone：

```
git clone https://github.com/patrickallaert/php-apm-web.git apm-web
```

配置`config/db.php`

```
return new PDO("sqlite:/var/php/apm/db/events");
```

页面效果：   

![](http://aker8img.qiniudn.com/58f901ee-67e5-42c1-89da-1c1f5123755c)


![](http://aker8img.qiniudn.com/204fd245-bd62-4704-9a74-3782422f0493)


![](http://aker8img.qiniudn.com/a1f757ab-150c-469a-983d-cba527b32685)
