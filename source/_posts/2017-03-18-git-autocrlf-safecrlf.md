---
title: Git中AutoCRLF与SafeCRLF的问题
date: 2017-03-18 19:31:42
tags: 
- Git
- AutoCRLF
- SafeCRLF
categories:
- Git
---


CR回车 LF换行   

| 系统 | 标识 | 转义符 |
| ------------ | ------------ | ------------ |
| Windows/Dos | CRLF | \\r\\n |
| Linux/Unix  | LF   | \\n    |
| MacOS       | CR   | \\r    |

建议：   
autocrlf=false   
safecrlf=true   
把所有文件使用LF换行符   


<!-- more -->

## AutoCRLF   

### 提交时转换为LF，检出时转换为CRLF   
```
git config --global core.autocrlf true
```

### 提交时转换为LF，检出时不转换
```
git config --global core.autocrlf input
```

### 提交检出均不转换
```
git config --global core.autocrlf false
```

## SafeCRLF

### 拒绝提交包含混合换行符的文件
```
git config --global core.safecrlf true
```

### 允许提交包含混合换行符的文件
```
git config --global core.safecrlf false
```

### 提交包含混合换行符的文件时给出警告
```
git config --global core.safecrlf warn
```

