---
title: git学习
date: 2024-01-30 18:57:47
tags: [git,linux]
categories: 学习笔记
---

# **git的使用**

##      git配置

- **安装git**

- **配置git**

  ```bash
  #全局配置config会自动将配置写在用户家目录的.gitconfig目录下
  $ git config --global user.name 'xxxx'
  $ git config --global user.email 'xxxx'
  #局部配置不加config会将配置写在当前仓库根目录/.git/config
  $ git config user.name 'xxxx'
  $ git config user.email 'xxxx'
  #配置代理端口，其中分sock5以及http/https代理
  #配置http/https代理
  git config --global http.proxy 127.0.0.1:7890
  git config --global https.proxy 127.0.0.1:7890
  #配置sock5代理
  git config --global http.proxy sock5 127.0.0.1:7890
  git config --global https.proxy sock5 127.0.0.1:7890
  #查看git配置信息,对比是否配置成功
  git config --list
  ```

## git常用指令

```bash
#首先选取一个文件夹初始化git
git init
#将想要的文件add至暂存区
git add a.txt
#如果是想要add全部文件的话
git add -all
#查看文件状态
git status
#将暂存区文件添加到本地存储库
git commit
#可选参数-m 后面加提交的注释
git commit -m'今天复习了一下git的使用'
#将本地仓库连接至远程仓库 origin为设定的远程名
git remote add origin git@github.com
#从远程仓库拉取文件 后面跟分支 一般为master或者main
git pull orgin master
#从本地仓库推送给远程仓库 加-f参数为强行推送
git push orgin master
#从别的库克隆下来 会自动生成一个remote远程名
git clone git@github.com
# 查看远程仓库
gi
```

## 代码回滚

```bash
#通过版本号回滚
git reset -hard 000091
#恢复上次提交的版本
git reset HEAD^
#恢复上上次提交的版本 以此类推
git reset HEAD^^
#查看版本号前几位
git reflog
#查看详细日志
git log
```

## 分支相关操作

```bash
#创造分支
git branch dev
#切换分支
git checkout dev
#创建并切换分支
git checkout -b dev
#查看分支
git branch
#删除分支
git branch -d dev
#分支合并 
git merge
#假如分支master 想合并分支dev
git checkout master
git merge dev
```



