---
title: "Setup Ur Own Server"
date: 2022-03-28T14:09:06+08:00
draft: false
categories:
    - 服务器
tags:
    - debian
    - ufw
    - systemd
    - caddy
    - hugo
---
## 更新apt
更新apt源列表

    apt update
    apt upgrade

等待更新完成

## 安装ufw以启用http以及https
安装ufw

    apt install ufw

查看当前开放端口

    ufw status verbose

开放http以及https

    ufw allow http
    ufw allow https

