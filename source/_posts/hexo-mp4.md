---
title: "页面头部换上MP4"
highlight_shrink: false
tags:
  - Hexo
categories: Hexo
description: 添加大量外挂标签样式。
top_img: "https://pixpro.coul.top/i/2025/05/30/594914.webp"
cover: "https://pixpro.coul.top/i/2025/05/30/594914.webp"
swiper_index: 6
abbrlink: hexo-games

date: 2025-4-21 15:55:44
comments:
copyright: true
copyright_author: 
copyright_author_href: 
copyright_url: 
katex:
ai: 
---

{% note blue 'anzhiyufont anzhiyu-icon-bullhorn' simple %}
参考[小旦](https://satera.cn/)教学，转载文章请注明来自[罐頭](https://blog.coul.top)
{% endnote %}

# 前言
如有问题下方留言
本篇拿游戏人生**games**界面举例，自己举一反三
{% tip ban %}如果还未配置游戏人生页面，点击下面页面，有石头姐出的魔改教程{% endtip %}

{% link 为博客添加一个游戏收藏页,kouseki,https://blog.kouseki.cn/posts/e7dd.html,https://blog.kouseki.cn/imgs/avatar.webp %}
## 正篇
首先找到“主题目录\anzhiyu\layout\includes\page\games.pug”
修改如下

```DIFF
-      .author-content.author-content-item.GamesPage.single(style = `background: url(${i.top_background}) left 37% / cover no-repeat !important;`)
+      .author-content.author-content-item.GamesPage.single(style = i.top_background && !i.top_background.endsWith('.mp4') ? `background: url(${i.top_background}) left 37% / cover no-repeat;` : "")
+        if i.top_background && i.top_background.endsWith('.mp4')
+          video(autoplay loop muted playsinline style="pointer-events: none; object-fit: cover; top: 50%; left: 50%; transform: translate(-50%, -50%); min-width: 100%; min-height: 100% ; width: auto; height: auto ;position: absolute;")
+            source(src=url_for(i.top_background) type="video/mp4")
+            source(src=url_for(i.top_background) type="video/mp4")
```

修改完毕，在games.yml的顶部配置项的top_background，现在也可以调用mp4视频了
```DIFF
 - title: 游戏世界
-  top_background: https://我原来是图片.png
+  top_background: https://现在这里可以是视频了.mp4
```
## 视频云
自建视频床感觉没必要了，太折腾，网上的案例和教程也是少之又少，为此我推荐大家使用免费的视频床——[多吉云](https://console.dogecloud.com/)的视频云

### 多吉云配置教程
上传视频
![](https://pixpro.coul.top/i/2025/05/30/437080.webp)
更改视频转码
![](https://pixpro.coul.top/i/2025/05/30/705371.webp)
获取视频直链
![](https://pixpro.coul.top/i/2025/05/30/426644.webp)

最后在***.yml页面文件替换top_background: 

教程结束
