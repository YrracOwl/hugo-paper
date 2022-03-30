---
title: "Git操作指南"
date: 2022-03-29T20:12:00+08:00
draft: false
slug: git操作指南
image: /post/git操作指南/alexander-sinn-KgLtFCgfC28-unsplash.jpg
categories:
    - 操作指南
tags:
    - git
    - 版本管理
---
## Step.01 安装或者升级git
git查看当前版本

    git --version

使用chocolatey更新git(因为链接的是远程仓库，所以会比较慢)
    
    choco install git
    
注意，当需要以管理员运行的时候，在前面加上**gsudo**命令(需要使用choco安装gsudo)

    gsudo choco install git

---
## Step.02 git全局设置
安装好git后，设置全局配置

    git config –global user.name "username"
    git config –global user.email "useremail@example.com"

注意，-global代表当前用户，-system代表当前系统，-local代表当前仓库

---
## Step.03 git的SSH设置
参考[Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/cn/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

查看git当前配置

    git config --system --list

---
## Step.04 链接到远程仓库
在想要初始化的文件夹内，按顺序运行如下命令

- 或者
    
        git init
        git remote add origin https://github.com/Example/example.git

- 或者

        git init
        git remote add origin git@github.com:Example/example.git

- 或者

        git init
        git remote add origin git@ssh.fastgit.org:Example/example.git #此为香港节点

移除 remote origin的命令如下
- 或者
        
        git remote remove origin
- 或者

        git remote set-url origin git://new.url.here

---
## Step.05 克隆Clone远程仓库
克隆自己在github上新建的仓库

    git clone git@ssh.fastgit.org:Example/example.git

## Step.06 修改后add/commit/push
修改文件后提交代码

    git add -A && git commit -m "message"

提交代码到Main分支

    git push -u origin main

![Code Your Heart](/post/git操作指南/alexander-sinn-KgLtFCgfC28-unsplash.jpg)