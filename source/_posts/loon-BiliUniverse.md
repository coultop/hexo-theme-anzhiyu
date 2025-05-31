---
title: "LOON实现哔哩哔哩自动换区"
highlight_shrink: false
tags:
  - LOON
categories: loon
description: 添加大量外挂标签样式。
top_img: "https://pixpro.coul.top/i/2025/04/17/813706.webp"
cover: "https://pixpro.coul.top/i/2025/04/17/813706.webp"
swiper_index: 6
abbrlink: loon-bilibili-auto-region
date: 2025-5-115 15:55:44
comments:
copyright: true
copyright_author: 罐頭
copyright_author_href: https://blog.coul.top/
copyright_url: 
katex:
ai: 
---

{% note blue 'anzhiyufont anzhiyu-icon-bullhorn' simple %}
`loon实现哔哩哔哩自动换区`源自于[🪐 BiliUniverseBiliUniverse](https://biliuniverse.io/index.html)，转载请注明来自[罐頭](https://blog.coul.top)
{% endnote %}
**如图所示,ios实现自动换区**
{% image https://pixpro.coul.top/i/2025/04/18/743734.gif, width=1200px %}

{% tip info %}🪐 哔哩万象{% endtip %}
ⓘ 配置完插件后食用loon即可哔哩哔哩自动换区，无需手动选择。

# ⚙️ Enhanced 

## 简介

· 自定义哔哩哔哩app 界面按钮与标签页的排列与显示

## 使用方式
**·基础: 直接使用**

· 采用默认配置
**·进阶: 配合Loon设置面板或Surge参数设置功能进行个性化设置**

· 提供一定的自定义设置，如首页选择、底部导航栏选择等
**·高级: 配合BoxJs及订阅使用**

{% folding green, ℹ️ 用前须知：使用BoxJs进行配置将被视为专业用户，官方不受理因使用BoxJs配置导致的各种问题 %}
**1.安装BoxJs插件并更新引用资源或脚本:**
· 安装方法及下载链接详见: 🧰 BoxJs
**2.在BoxJs的配置面板中进行个性化设置:**
· 浏览器访问BoxJs.com
· 在应用页面点开📺 BiliBili折叠
· 在📺 BiliBili: Enhanced根据需要填写您的设置信息
{% endfolding %}

## 功能列表
**首页页面**
· 标签页: 自定义启用的首页标签页
· 数量不限，但建议不超过7个
· 默认标签页: 选择启动APP时默认展示的标签页
· 需选择已启用的标签页，否则默认为第一个标签页
· 顶栏左侧按钮（用户头像）: 选择该按钮的作用
· BiliBili粉色版无法修改
· 顶栏右侧按钮: 选择启用的按钮
**底部导航栏**
· 自定义启用的底部导航栏
· 最多6个
· 超过6个则只会显示前6个选项
· iPadOS 版不支持自定义底部导航栏
**我的页面**
· 自定义启用的我的菜单选项
**分类页面**
· 自定义启用的分类菜单选项

## 安装链接

#### 一键安装📥

[点击一键安装](loon://import?plugin=https%3A%2F%2Fgithub.com%2FBiliUniverse%2FEnhanced%2Freleases%2Flatest%2Fdownload%2FBiliBili.Enhanced.plugin)
#### 手动安装

##### 安装路径
配置 > 插件 > 插件
#### 插件地址📦
https://github.com/BiliUniverse/Enhanced/releases/latest/download/BiliBili.Enhanced.plugin

## 默认设置
**首页**
**默认标签页: 推荐**
**标签页**
 直播
 推荐
 热门
 番剧
 动画
 影视
 校园
 数码
 韩综
**顶栏（左侧）按钮（用户头像）**
 用户中心-我的
 短视频
**顶栏（右侧）按钮**
 游戏中心
 会员购
 消息
**底部导航栏**
 首页
 频道
 动态
 发布
 节目
 会员购
 消息
 我的


# 🌐 Global
{% note info simple %}ℹ️ 用前须知 使用前，请务必检查默认配置是否与您的实际情况相符
如不符，请参考使用方式正确选择要启用的地区和填写对应地区的策略组或节点名称{% endnote %}
## 简介

**· 自动识别 BiliBili 番剧影视限制区域，并使用预设线路进行连接**
· 无需内置 BiliBili 策略组与分流规则
· 点开任意地区限制的番剧或影视内容，直接播放
· 局域网环境下，多设备同时观看不同地区内容，互不影响
**· 自定义搜索地区，快捷返回各区搜索结果**

## 使用方式
**基础: 直接使用（采用默认配置）**

采用默认配置
如果与您配置文件中的策略组或节点名称不符，请参考进阶或高级使用方式进行修改
**进阶: 配合Loon设置面板或Surge参数设置功能进行个性化设置**

提供一定的自定义设置，如强制 CDN 主机名类型选择、启用自动识别与分流功能的地区选择等
**高级: 配合BoxJs及订阅使用**

{% folding green, ℹ️ 用前须知：使用BoxJs进行配置将被视为专业用户，官方不受理因使用BoxJs配置导致的各种问题 %}
**1.安装BoxJs插件并更新引用资源或脚本:**
· 安装方法及下载链接详见: 🧰 BoxJs
**2.在BoxJs的配置面板中进行个性化设置:**
· 浏览器访问BoxJs.com
· 在应用页面点开📺 BiliBili折叠
· 在📺 BiliBili: Global根据需要填写您的设置信息
{% endfolding %}

## 功能列表
**强制 CDN 主机名类型**
此选项不限于媒体流的解析结果，搜索等其他返回的内容如图片音频也受此选项影响
选择返回域名的情况下，对于本身无域名只有IP的返回结果无效
**启用自动识别与分流功能的地区**
务必与代理软件策略相对应
**搜索时自定义搜索地区**
搜索关键词 + 空格 + 地区名称
如：电锯人 🇭🇰 或 辉夜 台湾 或 尼尔 港
支持的地区关键词有：
中国大陆：CN CHN 中 中国 🇨🇳
中国香港：HK HKG 港 香港 🇭🇰
中国澳门：澳 澳门 🇲🇴
中国台湾：TW TWN 台 台湾 🇹🇼
东南亚（国际版）：SEA 东南亚 🇺🇳 TH 泰 泰国 🇹🇭 SG 新 新加坡 🇸🇬 MY 马 马来西亚 🇲🇾
东南亚（国际版）未来可能细分
国际版已拆分独立

{% video https://permalink.dogevideo.com/player/get.mp4?vcode=004451ac1455d074&userId=11181&flsign=dd27c720ce870739f938523698987dc7&ext=.mp4 %}

## 安装链接
#### 一键安装📥
[点击一键安装](loon://import?plugin=https%3A%2F%2Fgithub.com%2FBiliUniverse%2FGlobal%2Freleases%2Flatest%2Fdownload%2FBiliBili.Global.plugin)
#### 手动安装
##### 安装路径
配置 > 插件 > 插件
#### 插件地址📦
https://github.com/BiliUniverse/Global/releases/latest/download/BiliBili.Global.plugin

## 默认设置
**强制 CDN 主机名类型**
 IP: 返回远端DNS解析地址（强烈不推荐！严重影响域名分流规则与CDN重定向）
 HTTP: 返回HTTP域名（推荐，免去重定向时MitM操作）
 HTTPS: 返回HTTPS域名（不推荐，重定向时需对指定域名启用MitM）
**启用自动识别与分流功能的地区**
 🇨🇳中国大陆
 🇭🇰中国香港
 🇲🇴中国澳门
 🇹🇼中国台湾
[🇨🇳中国大陆] 代理策略名称: DIRECT
[🇭🇰中国香港] 代理策略名称: 🇭🇰香港
[🇲🇴中国澳门] 代理策略名称: 🇲🇴澳门
[🇹🇼中国台湾] 代理策略名称: 🇹🇼台湾

# 🔀 Redirect🔀 重定向
{% note warning simple %}⚠️ 兼容性 本脚本需要使用重定向主机名功能
不支持重定向主机名功能的 VPN 无法使用本脚本{% endnote %}
## 简介

· 自定义重定向 BiliBili 视频源所使用的服务器主机名，加速视频加载速度

## 使用方式
**· 基础: 直接使用**

· 采用默认配置
**· 进阶: 配合Loon设置面板或Surge参数设置功能进行个性化设置**

· 提供一定的自定义设置，如Host选择等
**· 高级: 配合BoxJs及订阅使用**
{% folding green, ℹ️ 用前须知：使用BoxJs进行配置将被视为专业用户，官方不受理因使用BoxJs配置导致的各种问题 %}
**1.安装BoxJs插件并更新引用资源或脚本:**
· 安装方法及下载链接详见: 🧰 BoxJs
**2.在BoxJs的配置面板中进行个性化设置:**
· 浏览器访问BoxJs.com
· 在应用页面点开📺 BiliBili折叠
· 在📺 BiliBili: 🔀 Redirect根据需要填写您的设置信息
{% endfolding %}

## 安装链接
#### 一键安装📥
[点击一键安装](loon://import?plugin=https%3A%2F%2Fgithub.com%2FBiliUniverse%2FRedirect%2Freleases%2Flatest%2Fdownload%2FBiliBili.Redirect.plugin)
#### 手动安装
##### 安装路径
配置 > 插件 > 插件
#### 插件地址📦
https://github.com/BiliUniverse/Redirect/releases/latest/download/BiliBili.Redirect.plugin

## 默认设置
**[主机名] 重定向 Akamaized CDN (港澳台)**
 · 阿里云 CDN
 · 腾讯云 CDN
 · 华为云 CDN
**[主机名] 重定向 BStar CDN (国际版)**
 · 阿里云 CDN
 · 腾讯云 CDN
 · 华为云 CDN
**[主机名] 重定向 PCDN (中国大陆)**
 · 阿里云 CDN
 · 腾讯云 CDN
 · 华为云 CDN
**[主机名] 重定向 MCDN (中国大陆)**
 · proxy-tf-all-ws.bilivideo.com

# 🛡️ ADBlock

## 简介

· 自定义去除哔哩哔哩app 内广告与不适元素
## 使用方式
**· 基础: 直接使用（采用默认配置）**

· 采用默认配置
**· 进阶: 配合Loon设置面板或Surge参数设置功能进行个性化设置**

· 提供一定的自定义设置，如强制 CDN 主机名类型选择、启用自动识别与分流功能的地区选择等
**· 高级: 配合BoxJs及订阅使用**
{% folding green, ℹ️ 用前须知：使用BoxJs进行配置将被视为专业用户，官方不受理因使用BoxJs配置导致的各种问题 %}
**1.安装BoxJs插件并更新引用资源或脚本:**
· 安装方法及下载链接详见: 🧰 BoxJs
**2.在BoxJs的配置面板中进行个性化设置:**
· 浏览器访问BoxJs.com
· 在应用页面点开📺 BiliBili折叠
· 在📺 BiliBili: 🛡️ ADBlock根据需要填写您的设置信息
{% endfolding %}

## 功能列表
· 自定义去除哔哩哔哩app内广告与不适元素
## 安装链接

#### 一键安装📥
[点击一键安装](loon://import?plugin=https%3A%2F%2Fgithub.com%2FBiliUniverse%2FADBlock%2Freleases%2Flatest%2Fdownload%2FBiliBili.ADBlock.plugin)
#### 手动安装
##### 安装路径
配置 > 插件 > 插件
#### 插件地址📦
https://github.com/BiliUniverse/ADBlock/releases/latest/download/BiliBili.ADBlock.plugin

## 默认设置
 [开屏] 去除广告
 [推荐] 去除广告
 [推荐] 去除“活动大图”
 [推荐] 去除竖屏视频
 [推荐] 屏蔽UP主直播推广
 [首页] 去除短视频流广告
 [搜索] 去除广告
 [搜索] 去除“热搜”
 [番剧电影] 去除广告
 [直播] 去除广告
 [动态] 去除“热门话题”
 [动态] 去除“最常访问”
 [动态] 去除广告卡片
 [用户投稿] 去除视频广告
 [弹幕] 去除交互式弹幕
 [弹幕] 替换大会员弹幕
 [评论] 去除广告