---
title: "Hugo操作指南"
date: 2022-03-29T19:09:07+08:00
draft: false
slug: hugo操作指南
image: /post/hugo操作指南/rual-idyll-1339468 (小尺寸).jpg
categories:
    - 操作指南
tags:
    - hugo
    - 静态网站
---
# 官方网站
官方资源如下：
* [Hugo 官网](https://gohugo.io/)
* [Hugo 文档](https://gohugo.io/documentation/)
* [Hugo CLI](https://gohugo.io/commands/)

# 常用操作
## 查看hugo版本以及升级hugo

    hugo version
即可查看hugo版本，更新hugo时，再安装一次即可。
安装方法遵循hugo[官方安装指南](https://gohugo.io/getting-started/installing/)
## 创建新的日志
需要在根目录，带上post/，如下所示。
    
    hugo new post/test.md

查看new命令的参数，使用-h。

    hugo new -h

## 创建Bundle日志，即含有插入的图片的日志
在post/后带上文件名即可，如下所示。

    hugo new post/testBundle/testBundle.md

# 日志常见格式
在我们生成日志后，选用自己中意的编辑器进行日志的编辑。常见的日志格式如下所示。

```js
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
```
