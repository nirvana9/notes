---
title: gitpages博客搭建
date: 2017-01-08 22:24:00
tags:
---

# gitpages博客搭建

**gitpages好处** 免费并且支持Markdown语法，几乎可以零基础搭建个人博客。

## Markdown简介

> Markdown 是一种轻量级标记语言，它允许人们使用易读易写的纯文本格式编写文档，然后转换成格式丰富的HTML页面。    —— [维基百科](https://zh.wikipedia.org/wiki/Markdown)

## 安装git

    sudo apt-get install git
    
## 安装nodejs环境

    sudo apt-get install nodejs npm
    
## 安装hexo

    sudo npm install -g hexo

## 使用hexo生成博客

    sudo hexo init blog
    
## 下载设置主题，这里以Next主题为例

    cd blog/themes
    git clone https://github.com/iissnan/hexo-theme-next.git next
    
编辑blog/_config.yml `theme: landscape` 为  `theme: next`

## 本地预览
执行

    hexo s
打开浏览器访问`localhost:4000`就可查看效果了

## 上传github
在blog/_config.yml 中添加下配置

    deploy:
    type: git
    repository: git@github.com:nirvana9/notes.git
    branch: gh-pages
    
然后把整个blog目录提交到github上master分支

## 生成静态页面

    hexo g

## 上传静态页面到 gh-pages分支

    hexo d
    

## 将gh-pages分支 设置为gitpages
登陆github账号，进入 `blog --> Settings --> GitHub Pages`  选择 `gh-pages` 为gitpages 分支，
访问https://username.github.io/blog/
    


    

