---
title: "在本地用高帧率观看网页视频"
date: 2022-05-23T14:36:31+08:00
draft: false
slug: boosting_fps_of_video
image: rual-idyll-1339468 (小尺寸).jpg
toc: true
authors: YrracOwl
categories:
    - 提升体验
tags:
    - 猫抓
    - potplayer
    - svp4
---

## 动机
有时候在网页上观看视频，只有24FPS的视频源，做不到我们屏幕刷新率（60/144/155/175Hz）的帧速率。为了能够获得流畅的体验，可以使用猫抓+potplayer+svp4来获得这样的体验：将网页的视频，使用本地的potplayer播放，并且利用svp4插值到屏幕刷新率以获得丝滑的体验。

需要注意的是，potplayer搭配svp4，针对下载好的视频同样适用。若发现在选择伪影消除为<font color=#FF000 >**高**</font>后，视频的残影仍然较多，可以尝试<font color=#FF000 >**降低视频目标帧率**</font>。

## 猫抓
猫抓是一个网页视频、图片嗅探工具。

### 安装地址
- 在Edge Add-on中获取[猫抓](https://microsoftedge.microsoft.com/addons/detail/%E7%8C%AB%E6%8A%93/oohmdefbjalncfplafanlagojlakmjci) （<font color=#FF000 >**推荐**</font>）
- 在Chrome Extension中获取[猫抓](https://chrome.google.com/webstore/detail/%E7%8C%AB%E6%8A%93/jfedfbgedapdagkghmgibemcoggfppbb?hl=zh-CN)

### 使用方法
1. 猫抓安装好后，右键此扩展图标，选择扩展选项

![打开猫抓扩展选项](Snipaste_2022-05-23_14-50-23.png)

1. 勾选使用potplayer预览媒体

![勾选使用potplayer预览媒体](Snipaste_2022-05-23_14-52-36.png)

1. 在网页上存在视频时，次扩展图标会显示，左键点击会出现如下提示；点击最右端三个按钮可分别实现（复制播放地址、使用potplayer播放、下载视频）的功能

![选择播放图标](Snipaste_2022-05-23_14-54-40.png)

## potplayer
potplayer是一个强大且易用的多媒体播放器，其易用性和强大的功能不做赘述。

### 安装地址
Potplayer安装地址（[中文页面](https://potplayer.daum.net/?lang=zh_CN)）

### 配置potplayer
打开设置->滤镜->滤镜/解码器管理

![打开滤镜设置](Snipaste_2022-05-23_15-04-58.png)

选中滤镜优先权->添加系统滤镜->选择**AviSynth filter**->勾选强制使用->确定 （<font color=#FF000 >**推荐**</font>）

选中滤镜优先权->添加系统滤镜->选择ffdshow raw video filter->勾选强制使用->确定 （遗留配置，推荐AviSynth）

![配置potplayer滤镜](Snipaste_2022-05-23_15-04-00.png)

## svp 4 pro
svp 4 pro是一个能针对视频源进行补帧的工具，可以与多种播放器协同，实现补帧影视或者动画到屏幕刷新率以及多样刷新率的工具。

### 安装地址
svp 4 pro [正版安装地址](https://www.svp-team.com/zh/get/)。下载后一路点击next安装即可。

### 配置svp 4 pro
如下图所示，为精简配置，若电脑性能不够，可调节中间的滑块到靠近更高性能的位置。

![svp4配置1](Snipaste_2022-05-23_15-08-12.png)

点击左上角的图标，按如下所示选择，配置视频帧处理以及背景灯处理（防止切边字幕）。

![svp4配置2](Snipaste_2022-05-23_15-08-47.png)

![svp4配置3](Snipaste_2022-05-23_15-08-56.png)
## 总结
1. 启动svp 4 pro
2. 在想要用本地potplayer播放视频的网页，使用猫抓嗅探视频源，点击扩展后弹出来的播放按钮
3. 浏览器自动调用potplayer，配合svp 4 pro启动补帧

## 备注
此教程基于的版本如下：
1. 猫抓-1.0.20
2. potplayer-220420(1.7.21632)
3. svp 4 pro-4.5.0.214