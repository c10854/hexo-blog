---
title: Git学习笔记
date: 2017-09-17 14:39:28
tags: git
---
### <font color="#f46e65">设置姓名和邮箱地址</font>
```shell
$ git config --global user.name "vodka"
$ git config --global user.email "gdzhengwei@gmail.com"
```
该内容会保存到 `~/.gitconfig` 文件中

### <font color="#f46e65">提高命令输出的可读性</font>
```shell
$ git config --global color.ui auto
```
### <font color="#f46e65">创建SSH Key</font>
```shell
$ ssh-keygen -t rsa -C "your_email@example.com"
```
### <font color="#f46e65">查看秘钥</font>
```shell
$ cat ~/.ssh/id_rsa.pub
ssh-rsa    公开密钥的内容    your_email@example.com
# 测试秘钥是否有效
$ ssh -T git@github.com
```
## 基本操作
* git init ——初始化操作
* git status ——查看仓库的状态
* git add ——向暂存区中添加文件
* git commit ——保存仓库的历史记录
* git log ——查看提交日志
* git diff ——查看更改前后的差别
<br>
## 分支操作
* git branch ——显示分支一览表
* git branch new_name ——创建新分支
* git checkout branch_name ——切换到branch_name分支
* git checkout - ——切换回上一个分支 
* git merge ——合并分支
```shell
$ git checkout master
$ git merge --no-ff feature-A
```
* git log --graph ——以图表形式查看分支
* git reset --hard 相关head的哈希值
* git reflog ——查看当前仓库的操作日志