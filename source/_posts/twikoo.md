---
title: "twikoo配置教程"
highlight_shrink: false
tags:
  - twikoo
categories: twikoo
description: 添加大量外挂标签样式。
top_img: "https://pixpro.coul.top/i/2025/04/22/372298.webp"
cover: "https://pixpro.coul.top/i/2025/04/22/372298.webp"
swiper_index: 6
abbrlink: twikoo

date: 2025-4-21 15:55:44
comments:
copyright: true
copyright_author: 
copyright_author_href: 
copyright_url: 
katex:
ai: 
---

# Twikoo 部署教程

## **前言**
Twikoo 是一个简洁、安全、免费的静态网站评论系统，基于腾讯云开发。下面是 Twikoo 的部署教程，你可以根据自己的需求选择合适的[部署方式](https://twikoo.js.org/backend.html)。

### 一、腾讯云手动部署
手动部署到腾讯云云开发环境，在中国大陆访问速度较快。需要付费购买环境才能部署。
```bash
# 1. 进入云开发CloudBase活动页面，购买基础版1套餐，创建环境
# 2. 进入云开发控制台
# 3. 启用匿名登录
# 4. 将网站域名添加到 WEB 安全域名
# 5. 新建云函数 twikoo，选择空白函数和 Node.js 16.13 运行环境
# 6. 清空示例代码，复制以下代码到函数代码输入框
exports.main = require('twikoo-func').main
# 7. 创建 package.json 文件，复制以下代码并保存
{
  "dependencies": {
    "twikoo-func": "1.6.42"
  }
}
# 8. 保存并安装依赖
```

### 二、腾讯云命令行部署
虽然方便，但是仅支持按量计费环境——也就是说，一键部署的环境，当免费资源用尽后，将会产生费用。且按量计费环境无法切换为包年包月环境。免费额度数据库读操作数只有 500 次 / 天，无法支撑 Twikoo 的运行需求。
```bash
# 1. 进入云开发CloudBase活动页面，购买基础版1套餐，创建环境
# 2. 进入云开发控制台
# 3. 启用匿名登录
# 4. 将网站域名添加到 WEB 安全域名
# 5. 克隆仓库
git clone https://github.com/twikoojs/twikoo.git
cd twikoo
# 6. 安装依赖项
npm install -g yarn
yarn install
# 7. 授权云开发环境
# 8. 自动部署
yarn deploy
```

### 三、Vercel 部署
适用于想要免费部署的用户，在中国大陆访问速度较慢甚至无法访问，绑定自己的域名可以提高访问速度。
```bash
# 1. 点击链接导入 Vercel
# 2. 输入仓库名，点击 Create 创建
# 3. 选择代码托管位置，填写仓库名，点击 Continue
# 4. 点击 Deploy 一键部署
# 5. 进入 Settings - Environment Variables，添加 MONGODB_URI 环境变量
# 6. 进入 Deployments，重新部署
# 7. 进入 Overview，获取环境 ID
```

### 四、宝塔面板部署
适用于有服务器的用户，需要自行申请 HTTPS 证书。
```bash
# 1. 安装宝塔面板并登录
# 2. 安装 Docker 服务
# 3. 在应用商店中找到 Twikoo 并安装，配置域名、端口等信息
# 4. 通过浏览器访问设置的域名或 IP + 端口
```

### 五、Railway 部署
有免费额度但不足以支持一个月连续运行，部署简单，适合全球访问。
```bash
# 1. 在 Railway 申请账号，点击 New Project - Provision MongoDB
# 2. fork twikoojs/twikoo-zeabur 仓库到自己的账号
# 3. 回到 Railway，点击 New - GitHub Repo，授权 GitHub，选择 fork 的仓库
# 4. 点开环境卡片 - Variables，添加 PORT 环境变量为 8080
# 5. 添加 MongoDB 相关环境变量
# 6. 绑定域名
# 7. 配置博客 envId
```
### 六、Zeabur 部署
需要绑定支付宝或信用卡，部署简单，适合中国大陆访问，免费计划环境随时可能会被删除。
```bash
# 1. 在 Zeabur 申请账号，部署 MongoDB
# 2. fork twikoojs/twikoo-zeabur 仓库到自己的账号
# 3. 回到 Zeabur，部署源代码，授权 GitHub，选择 fork 的仓库
# 4. 部署完成后绑定域名
# 5. 配置博客 envId
```

### 七、Netlify 部署
有充足的免费额度，中国大陆访问速度不错。
```bash
# 1. 申请 MongoDB Atlas 账号，获取连接字符串
# 2. 申请 Netlify 账号，创建 Team
# 3. fork twikoojs/twikoo-netlify 仓库到自己的账号
# 4. 回到 Netlify，点击 Add new site - Import an existing project
# 5. 点击 Deploy with GitHub，选择 fork 的项目
# 6. 添加 MONGODB_URI 环境变量
# 7. 部署完成后，设置站点名获取环境 ID
```

### 八、Hugging Face 部署
免费，中国大陆访问速度不错。允许通过 Cloudflare Tunnels 自定义域名。
```bash
# 1. 申请 MongoDB Atlas 账号，获取连接字符串
# 2. 申请 Hugging Face 账号
# 3. 创建 Space，设置 SDK 为 Docker，选择 Blank 模板
# 4. 在 Settings 中添加 MONGODB_URI 环境变量
# 5. 创建 Dockerfile 文件，内容如下
FROM imaegoo/twikoo
ENV TWIKOO_PORT 7860
EXPOSE 7860
# 6. 提交文件，获取环境 ID
```

### 九、私有部署
适用于有服务器的用户，需要自行申请 HTTPS 证书。
```bash
# 1. 服务端安装 Node.js
# 2. 安装 Twikoo server
npm i -g tkserver
# 3. 根据需要配置环境变量
# 4. 启动 Twikoo server
tkserver
# 5. 访问 http://服务端IP:8080 测试服务
# 6. 配置前置代理实现 HTTPS 访问
```

## Twikoo 的基本配置
```HTMK
# Twikoo
# https://github.com/imaegoo/twikoo
twikoo:
  envId: https://twikoo.coul.top  #改成自己的域名
  region:
  visitor: false
  option:
```


## twikoo评论区图片优化代码

{% link 参考梦佬教程和代码,梦爱吃鱼,https://blog.bsgun.cn,https://lib.bsgun.cn/Hexo-static/img/favicon.ico %}
{% link 参考飞扬教程和代码,清羽 〄 飞扬,https://blog.liushen.fun,https://blog.liushen.fun/info/avatar.ico %}

在source/css/xxx.css（文件名自便）文件中添加以下代码：

```css
/* ========================twikoo美化====================== */
/* 隐藏评论者头像 */
#twikoo .tk-comments .tk-submit .tk-avatar.tk-has-avatar {
    display: none;
}

/* 下面表情和按钮那一栏的设置 */
#twikoo .tk-comments .tk-submit .tk-row.actions{
    margin-bottom: 0;
    margin-left: 0;
}

/* 个人信息和文本输入之间的空位置 */
.tk-main .tk-submit .tk-col .tk-meta-input,
#twikoo .tk-comments .tk-submit .tk-col .tk-meta-input{
    margin-bottom: 16px;
}

/* 直接固定高度，解决提交按钮有时高度不起作用的问题 */
.tk-row.actions button.el-button {
    height: 32px;
}

/* 解决图片大小超出范围问题 */
.tk-main .tk-content img {
  max-width: 100%;
  height: auto;
}

/* 输入框动态背景过渡效果 */
.twikoo .el-input__inner,
.twikoo .el-textarea__inner {
    transition: background-position-y 0.3s ease-in-out !important;
    background-repeat: no-repeat;
}

/* 焦点状态背景位移 */
.twikoo .el-input__inner:focus,
.twikoo .el-textarea__inner:focus {
    background-position-y: 100% !important; /* 更灵活的百分比定位 */
}

/* 文本域背景适配 */
.tk-input .el-textarea__inner {
    background-size: contain;
    background-position: right bottom; /* 建议添加定位 */
}

/* 圆角设置 */
.tk-meta-input input {
    border-top-right-radius: 12px;
    border-bottom-right-radius: 12px;
}

.tk-meta-input div {
    border-top-left-radius: 12px;
    border-bottom-left-radius: 12px;
}

/* 输入框样式 */
.tk-input.el-textarea textarea {
    border-radius: 12px;
    min-height: 150px !important;
    height: auto;
}

/* 宽度太窄的时候去掉预览按钮 */
@media screen and (max-width:420px) {
    .tk-main .tk-submit .tk-row.actions button.el-button.tk-preview.el-button--default.el-button--small{
        display: none;
    }
}

:root {
  --liushen-radius: 12px;
  --liushen-card-border-width: 1px;
}

/* 浅色模式颜色 */
[data-theme=light] {
  --liushen-border-color: #e3e8f7;
  --liushen-card-bg: #fff;
  --liushen-card-border: #e3e8f7;
  --style-border-always: 1px solid var(--liushen-card-border);
  --liushen-blue: #425AEF;
}

/* 深色模式颜色 */
[data-theme=dark] {
  --liushen-border-color: #42444a;
  --liushen-card-bg: #2c2c2c;
  --liushen-card-border: #42444a;
  --style-border-always: 1px solid var(--liushen-card-border);
  --liushen-blue: #0084FF;
}

/* 评论区评论大框 */
.twikoo .tk-comments-container>.tk-comment,
.twikoo .tk-comments .tk-submit {
  /* 内边距 */
  padding: 20px;
  margin-top: 0px;
  margin-bottom: 20px;
  /* 圆角 */
  border-radius: var(--liushen-radius);
  /* 背景颜色 */
  background: var(--liushen-card-bg);
  /* 变动动画时长 */
  transition: .3s;
}

/* 浅色模式评论区评论大框 */
[data-theme=light] 
.twikoo .tk-comments-container>.tk-comment,
.twikoo .tk-comments .tk-submit {
  /* 阴影 */
  box-shadow: var(--card-box-shadow);
}

/* 浅色模式评论区评论大框阴影悬浮加深 */
[data-theme=light] 
.twikoo .tk-comments-container>.tk-comment:hover,
.twikoo .tk-comments .tk-submit:hover {
  /* 阴影（浅色模式突出层次感） */
  box-shadow: var(--card-hover-box-shadow);
}

/* 黑暗模式评论区评论大框 */
[data-theme=dark] 
.twikoo .tk-comments-container>.tk-comment,
.twikoo .tk-comments .tk-submit {
  /* 边框样式 */
  border-style: solid;
  /* 边框宽度 */
  border-width: var(--liushen-card-border-width);
  /* 边框颜色 */
  border-color: var(--liushen-card-border);
}

/* 设备信息 */
.twikoo .tk-extra {
  /* 圆角 */
  border-radius: var(--liushen-radius);
  /* 背景颜色 */
  background: var(--liushen-card-bg);
  /* 内边距 */
  padding: 0.4rem;
  /* 底边距 */
  margin-bottom: 1rem;
  /* 变动动画时长 */
  transition: .3s;
}

/* 浅色模式设备信息 */
[data-theme=light] .twikoo .tk-extra {
  /* 阴影 */
  box-shadow: var(--card-box-shadow);
}

/* 浅色模式设备信息阴影悬浮加深 */
[data-theme=light] .twikoo .tk-extra:hover {
  /* 阴影 */
  box-shadow: var(--card-hover-box-shadow);
}

/* 黑暗模式设备信息 */
[data-theme=dark] .twikoo .tk-extra {
  /* 边框样式 */
  border-style: solid;
  /* 边框宽度 */
  border-width: var(--liushen-card-border-width);
  /* 边框颜色 */
  border-color: var(--liushen-card-border);
}

/* 加载更多按钮 */
.twikoo .tk-expand {
  /* 圆角 */
  border-radius: var(--liushen-radius);
}

/* 浅色模式加载更多按钮 */
[data-theme=light] .twikoo .tk-expand {
  /* 阴影 */
  box-shadow: var(--card-box-shadow);
}

/* 浅色模式加载更多按钮（鼠标悬浮时） */
[data-theme=light] .twikoo .tk-expand:hover {
  /* 阴影 */
  box-shadow: var(--card-hover-box-shadow);
  /* 背景颜色 */
  background-color: var(--btn-bg);
}

/* 黑暗模式加载更多按钮（鼠标悬浮时） */
[data-theme=dark] .twikoo .tk-expand:hover {
  /* 背景颜色 */
  background-color: var(--liushen-blue);
}

/* 黑暗模式加载更多按钮 */
[data-theme=dark] .twikoo .tk-expand {
  /* 边框样式 */
  border-style: solid;
  /* 边框宽度 */
  border-width: var(--liushen-card-border-width);
  /* 边框颜色 */
  border-color: var(--liushen-card-border);
}

/* 分类卡片移动端个人信息卡片只显示两个 */
@media screen and (max-width:570px) {
    .tk-main .tk-extras {
        display: none;
    }
}

/* 评论区按钮样式 */
.tk-row.actions button.el-button {
    border-radius: 12px !important;
}

/* 由于twikoo内部函数不宜修改，为了合适，去掉弹窗中的刷新按钮，该部分不需要，这是为了适配右键回复弹窗的内容的
#popup #twikoo .tk-comments .tk-comments-container .tk-comments-title > span:nth-child(2) > span:nth-child(1) {
	display: none;
} */

/* ========================twikoo美化====================== */

```

## 然后在主题文件中引用该CSS文件。
### 参考
```CSS
inject:
  head:
    # 评论页面优化
      - <link rel="stylesheet" href="/css/comment.css">
```

## Twikoo邮件通知模板分享
