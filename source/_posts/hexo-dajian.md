---
title: "Hexo 本地搭建教程"
highlight_shrink: false
tags:
  - Hexo
categories: Hexo
description: 添加大量外挂标签样式。
top_img: "https://pixpro.coul.top/i/2025/04/21/820671.webp"
cover: "https://pixpro.coul.top/i/2025/04/21/820671.webp"
swiper_index: 6
abbrlink: hexo-dajian

date: 2025-4-21 15:55:44
comments:
copyright: true
copyright_author: 
copyright_author_href: 
copyright_url: 
katex:
ai: 
---

# Hexo 博客本地搭建与 GitHub 部署完整教程
参考了[梦佬](https://blog.bsgun.cn/posts/9642fffa/)的教程文章
---
Hexo 以其快速渲染、灵活定制、多平台部署、简洁写作体验及良好性能表现等优势，受到技术博客作者和开发者欢迎，是搭建个人博客的不错选择。
## 环境准备
 
### 必备工具
- [Node.js v18+](https://nodejs.org/)（推荐安装 LTS 版本）
- [Git](https://git-scm.com/)
- 文本编辑器（推荐 VS Code）

### 环境验证
```bash
node -v && npm -v && git --version
# 成功示例输出：
# v18.17.1
# 9.6.7
# git version 2.40.1
```
环境没问题后安装node.js淘宝镜像加速器(cnpm)
```bash
npm install -g cnpm --registry=https://registry.taobao.org
cnpm -v # 验证安装成功
```

## 安装 Hexo
环境配置好后就可以安装 Hexo了。
```bash
npm install -g hexo-cli
hexo -v # 验证安装成功
```
安装完成后，创建一个想用来存放博客的目录**hexo**，然后开始新搭建博客。
```bash
cd hexo
hexo init
hexo s
```
在运行**hexo s**后会看到hexo is running at http://localhost:4000 说明本地搭建成功。press ctrl+c to stop.

在浏览器中输入 http://localhost:4000 就可以看到默认的 Hexo 博客页面了。

