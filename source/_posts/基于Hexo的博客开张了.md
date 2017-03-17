---
title: 基于Hexo的博客开张了
date: 2016-09-29 22:27:52
tags:
- Hexo
- 博客
categories:
- 杂说
---

今晚本来是打算学习一下vue的，结果看到有个东西叫：[hexo][1]，一时好奇就开始研究并了起来（好吧，我跑题了）
网上搜了几篇介绍安装的文章，然后找了 [hexo-theme-next][2] 的主题，就这样博客搭建好了。  

这里简单的说一下hexo的安装使用：   
本地必须先安装nodejs，具体步骤见[nodejs官方](https://nodejs.org)

#安装
1. 安装hexo   
`npm install -g hexo`
2. 初始化   
创建目录，如test，在test目录下，命令行执行：   
`hexo init`
3. 生成页面文件   
`hexo generate （简写： hexo g）`

#查看
本地想要查看效果，可以使用hexo server   
1. 安装server   
`npm install hexo-server --save`   
2. 安装成功后，启动server   
`hexo server`   
3. 启动后，浏览器输入[http://localhost:4000](http://localhost:4000 "http://localhost:4000")，即可访问   

#与GitHub配合
本地必须安装git   
1. 在GitHub上创建自己的仓库，名称如【klgd.github.io】   
2. 安装hexo的git包   
```npm install hexo-deployer-git --save```   
3. 配置参数，打开hexo的配置文件 _config.yml，在最后找到deploy   
根据自己的仓库情况，配置下面参数

```
deploy:
  type: git
  repository: git@github.com:klgd/klgd.github.io.git
  branch: master
```
4.执行命令，向GitHub pull hexo的页面文件   
```hexo deploy```


  [1]: https://hexo.io/
  [2]: https://github.com/iissnan/hexo-theme-next