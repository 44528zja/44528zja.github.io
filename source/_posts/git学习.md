---
title: git学习
date: 2024-01-30 18:57:47
tags: git linux
categories: 学习笔记
---

# **git的使用**

##      git配置

- 安装git

- 配置git

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



