---
title: "LOON打破界限，畅享自由"
highlight_shrink: false
tags:
  - LOON
categories: loon
description: 添加大量外挂标签样式。
top_img: "https://pixpro.coul.top/i/2025/04/17/663617.webp"
cover: "https://pixpro.coul.top/i/2025/04/17/663617.webp"
swiper_index: 6
abbrlink: loon-iringo

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
`loon打破界限，畅享自由`源自于[ iRingo](https://nsringo.github.io/index.html)，转载请注明来自[罐頭](https://blog.coul.top)
{% endnote %}

# 🌤 WeatherKit
{% note warning modern %} ⚠️ 最低支持
iOS 18 beta (22A5282m)
iPadOS 18 beta (22A5282m)
macOS 15 beta (24A5264n)
tvOS 18 beta (22J5290l)
visionOS 2 beta (22N5252n)
watchOS 11 beta (22R5284o)
{% endnote %} 

{% note info modern %}ℹ️ 用前须知
如果您想在配对的 Watch 上使用
则 ⌚️ 也需安装相同的 MitM 证书
{% endnote %}
## 简介
### 解锁全部天气数据类型
### 替换「空气质量」数据
### 添加「未来一小时降水强度」信息

{% note success modern %} ✅ 小提示
   未来一小时降未来一小时降水强度面板仅在此城市未来一小时内有降水的情况下显示。
   降水通知仅在城市位于您天气 app 的关注列表中，并于关注列表右上角的通知中，开启此城市的未来一小时降水强度通知，且此城市的降水您还并未主动获知（主动查看或显示在小组件上均为已获知）的情况下，才会进行降水通知。
{% endnote %}
## 配置方法
**基础: 直接使用**

**采用[默认配置]()**
进阶: 配合Loon设置面板或Surge参数设置功能进行个性化设置

**提供一定的自定义设置，如数据源选择、需要替换的供应商选择等**
高级: 配合BoxJs及订阅使用

{% folding green, ℹ️ 用前须知：使用BoxJs进行配置将被视为专业用户，官方不受理因使用BoxJs配置导致的各种问题 %}
**1. 安装BoxJs插件并更新引用资源或脚本:**
· 安装方法及下载链接详见: 🧰 BoxJs
**2. 在BoxJs的配置面板中进行个性化设置:**
1.浏览器访问BoxJs.com
2.在应用页面点开 iRingo折叠
3.在🌤 WeatherKit根据需要填写您的设置信息
{% endfolding %}

{% note success flat %}✅ 小提示
1.彩云天气的分钟级降水接口权限不对普通开发者开放，需要额外采购，请勿在此脚本中填写使用普通开发者token
2.和风天气的昨日空气质量对比接口权限仅对付费订阅用户开放，请勿在此脚本中填写使用普通开发者token
{% endnote %}

## 功能列表
**· 解锁全部天气数据类型**
**· 未来一小时降水强度与降水通知**
彩云天气 （默认，可选 Token）
和风天气 （需要 Token）
默认为增补模式，不会替换已有降水数据，仅补充无数据城市
**· 空气质量数据**
彩云天气 （默认，支持昨日同时段对比，可选 Token）
和风天气 （支持昨日对比，需要 Token）
WAQI （可选 Token）
默认为增补模式，不会替换已有空气质量数据，仅补充无数据城市
**· 空气质量标准换算**
默认开启，将中国空气质量标准换算为最新美国空气质量标准

## 安装链接

#### 一键安装📥
[点击一键安装](loon://import?plugin=https%3A%2F%2Fgithub.com%2FNSRingo%2FWeatherKit%2Freleases%2Flatest%2Fdownload%2FiRingo.WeatherKit.plugin)
#### 手动安装
##### 安装路径
配置 > 插件 > 插件
#### 插件地址📦
https://github.com/NSRingo/WeatherKit/releases/latest/download/iRingo.WeatherKit.plugin

# 📍 定位

{% note info flat %}ℹ️ 用前须知
仅  的 app 及 framework 使用此方式获取用户位置信息
第三方 app 不使用此方式获取用户位置信息
{% endnote %}

## 简介
### 自定义「定位服务」通过基于网络的地区检测结果始终为用户设置的地区

## 解锁步骤
{% timeline 第 1 步,purple %}
<!-- timeline 启用📍 定位模块 -->

📍 定位的地区不应该设置为🇨🇳CN
浏览器访问 https://gspe1-ssl.ls.apple.com/pep/gcc ，页面显示的两个字母即为当前修改的地区代码
<!-- endtimeline -->

{% endtimeline %}

{% timeline 第 2 步,purple %}
<!-- timeline 打开✈️飞行模式，同时保持Wi-Fi或有线网络连接 -->

· 未装有 SIM 卡的 iOS/iPadOS/macOS 设备，可省略✈️飞行模式相关步骤。
· 当存在移动蜂窝网络时，不触发此检测方式，将直接采用基于SIM卡的移动设备网络代码「MCC / MNC」进行检测
· 基于 SIM 卡的移动设备网络代码「MCC / MNC」检测不在此模块解决范围
<!-- endtimeline -->

{% endtimeline %}

{% timeline 第 3 步,purple %}
<!-- timeline 重新冷启动一次地图 app -->

· 指后台无地图应用时，重开地图app
在 Loon 的仪表-最近请求中应观察到:
在 Surge 的工具-最近请求中应观察到:
在 Quantumult X 的网络活动中应观察到:
  基于网络的地区检测的 https://gspe1-ssl.ls.apple.com/pep/gcc 链接，且流量抓取结果为当前修改的地区代码
<!-- endtimeline -->

{% endtimeline %}

{% timeline 第 4 步,purple %}
<!-- timeline 关闭✈️飞行模式 -->


<!-- endtimeline -->

{% endtimeline %}

## 配置方法
**· 基础: 直接使用**

**· 采用默认配置**
进阶: 配合Loon设置面板或Surge参数设置功能进行个性化设置

**· 提供一定的自定义设置，如数据源选择、需要替换的供应商选择等**
高级: 配合BoxJs及订阅使用

{% folding green, ℹ️ 用前须知：使用BoxJs进行配置将被视为专业用户，官方不受理因使用BoxJs配置导致的各种问题 %}
**1.安装BoxJs插件并更新引用资源或脚本:**
· 安装方法及下载链接详见: 🧰 BoxJs
**2.在BoxJs的配置面板中进行个性化设置:**
· 浏览器访问BoxJs.com
· 在应用页面点开 iRingo折叠
· 在📍 定位根据需要填写您的设置信息
{% endfolding %}

## 功能列表
**修改PEP 地区代码(GCC, Geo Country Code)检测结果**
**终结点(Endpoint): https://gspe1-ssl.ls.apple.com/pep/gcc**
**已知影响的功能**
 强制更改基于网络的地区检测结果至模块指定地区
 协助激活Apple News
 协助激活「来自APPLE的内容\来自APPLE的建议\Siri建议」(激活后不需要保持定位服务模块一直启用)
 指南针的海拔经纬度功能
 询问Siri切换为国际版(维基百科)
 SIM卡设备会因「MCC / MNC」检测回退至国内版(百度百科)
**已知附带影响**
 天气的数据源
 Siri建议的服务器分配
 iTunes Store的CDN分配
 Apple Music的版权问题
 Apple Maps的地区版本
 Apple News的可用性判断(可通过其他模块单独修改)
 待发现

## 安装链接

#### 一键安装📥
[点击一键安装](loon://import?plugin=https%3A%2F%2Fgithub.com%2FNSRingo%2FGeoServices%2Freleases%2Flatest%2Fdownload%2FiRingo.Location.plugin)
#### 手动安装
##### 安装路径
配置 > 插件 > 插件
#### 插件地址📦
https://github.com/NSRingo/GeoServices/releases/latest/download/iRingo.Location.plugin

# 🗺 地图

{% note info no-icon %}ℹ️ 用前须知
iOS 15.1起，指南针的海拔与经纬度受动态(Dynamic)配置文件控制
{% endnote %}
{% note info no-icon %}ℹ️ 用前须知
如果您想在配对的 Watch 上使用
则 ⌚️ 也需安装相同的 MitM 证书
{% endnote %}

## 简介
全面自定义Mapsapp，添加国际版功能，自定义服务版本
默认为高德版地图增加国际版功能:
添加3D 卫星图像与地球卫星图像（含夜景）
启用四处看看(Look Around)功能
{% note success flat %}✅ 小提示
修改生效后将会抹去左下角高德地图logo，但并不代表当前是或不是高德地图。
具体地图版本取决于[动态配置]的设置
{% endnote %}

## 解锁步骤
{% timeline 第 1 步,purple %}
<!-- timeline 启用🗺 地图模块 -->


<!-- endtimeline -->

{% endtimeline %}

{% timeline 第 2 步,purple %}
<!-- timeline 重新冷启动一次地图 app -->

**指后台无地图应用时，重开地图app**
· 在 Loon 的仪表-最近请求中应观察到:
· 在 Surge 的工具-最近请求中应观察到:
· 在 Quantumult X 的网络活动中应观察到:
1.基于网络的地区检测的 https://gspe1-ssl.ls.apple.com/pep/gcc 链接，且流量抓取结果为当前修改的地区代码
2.检测设备信息的 https://configuration.ls.apple.com/config/defaults 链接
<!-- endtimeline -->

{% endtimeline %}

{% timeline 第 3 步,purple %}
<!-- timeline  -->

**点击右上角选取地图-卫星，观察是否存在下列特征:**
· 将地图拉至最远，是否显示完整的地球球体模型及昼夜交替的卫星图像
· 将地图拉至最远，选取地图最下方注释显示 iRingo: 📍 GEOResourceManifest字样及最后更新配置文件的时间
**搜索并查看巴黎或东京或纽约等世界主要城市，观察是否存在下列特征:**
· 选取地图-卫星时，右上角显示3D按钮
· 点击并放大卫星图像后，可查看拥有真实建模及贴图的 3D 建筑物
· 选取地图-探索时，左下角显示四处看看(Look Around)按钮
· 点击四处看看(Look Around)按钮，可查看拥有真实拍摄的 3D 街景
<!-- endtimeline -->

{% endtimeline %}

{% timeline 第 4 步,purple %}
<!-- timeline 正常使用 Maps -->

<!-- endtimeline -->

{% endtimeline %}

## 使用说明
**启用坐标功能与指南针经纬度:**
[定位漂移]改为Apple（🈶️坐标，使用🇺🇳WGS-84坐标）
**查看不同地区与版本的卫星图像**
仅查看🇨🇳中国（不含🇹🇼中国台湾地区）最新2D 卫星图像
[卫星图像]改为🇨🇳中国四维
查看🇨🇳中国（不含🇹🇼中国台湾地区）最新2D 卫星图像与🇺🇳国际主要城市的3D 卫星图像
[卫星图像]改为混合(默认)
查看🇨🇳中国过期2D 卫星图像与🇺🇳国际非主要城市的2D 卫星图像与🇺🇳国际主要城市的3D 卫星图像
[卫星图像]改为🇺🇳DigitalGlobe
**启用俯瞰(Flyover)功能**
[调度器]改为Apple（维基百科/Yelp/Booking）（非必需，如非此选项，则无俯瞰(Flyover)按钮，但可在3D卫星地图下手动俯瞰）
[卫星图像]改为混合或🇺🇳DigitalGlobe（🇨🇳:2D | 🇺🇳:3D）
[飞行俯瞰]改为🇺🇳Apple（🇨🇳:🈚️ | 🇺🇳:🈶️）
**启用四处看看(Look Around)功能**
[四处看看]改为🇺🇳Apple（🇨🇳:🈚️ | 🇺🇳:🈶️）
**注：⌚️ WATCH部分功能有单独的设置面板，不随📍 定位模块内的配置而变更**

## 配置方法
**基础: 直接使用**

采用默认配置
**进阶: 配合Loon设置面板或Surge参数设置功能进行个性化设置**

提供一定的自定义设置，如数据源选择、需要替换的供应商选择等
**高级: 配合BoxJs及订阅使用**
{% folding green, ℹ️ 用前须知：使用BoxJs进行配置将被视为专业用户，官方不受理因使用BoxJs配置导致的各种问题 %}
**安装BoxJs插件并更新引用资源或脚本:**
安装方法及下载链接详见: 🧰 BoxJs
**在BoxJs的配置面板中进行个性化设置:**
浏览器访问BoxJs.com
在应用页面点开 iRingo折叠
在🗺 地图根据需要填写您的设置信息
{% endfolding %}

## 功能列表

**修改默认(Defaults)配置**
终结点(Endpoint): https://configuration.ls.apple.com/config/defaults
已知启用的功能
地图-路线-步行-现实世界中的路线
地图-路线-步行-导航准确性
地图-为“地图”提供助力-评分与照片
地图-为“地图”提供助力-显示评分和照片建议
**指定通告(Announcements)配置版本**
终结点(Endpoint): https://gspe35-ssl.ls.apple.com/config/announcements
已知影响的功能
 无已知影响
**指定动态(Dynamic)配置版本**
终结点(Endpoint): https://gspe35-ssl.ls.apple.com/geo_manifest/dynamic/config
**指定调度器(Dispatcher)API版本**
终结点(Endpoint):
国际版: https://gsp-ssl.ls.apple.com/dispatcher.arpc
高德版: https://dispatcher.is.autonavi.com/dispatcher
已知影响的功能
 地图内公共指南(来自第三方机构的城市与景点旅游指南)
 地图内查询与搜索功能
 地图内地标与地点的基础信息
 地图内兴趣点(POI)的高级信息(来自大众点评或Yelp等第三方的商户信息)
**指定导航与ETA(Directions & ETA)API版本**
终结点(Endpoint):
国际版: https://gsp-ssl.ls.apple.com/directions.arpc
高德版: https://direction2.is.autonavi.com/direction
已知影响的功能
 地图的导航功能
指定评分和照片(Rating and Photo, RAP)API版本
指定定位漂移(Location Shift)API版本
终结点(Endpoint):
高德版: https://shift.is.autonavi.com/localshift
**指定瓦片地图(Tiles Map)数据源**
终结点(Endpoint):
国际版: https://gspe19-ssl.ls.apple.com/tile.vf
高德版: https://gspe19-cn-ssl.ls.apple.com/tiles
已知影响的功能
 地图的图层数据
**指定卫星图像(Satellite Map)数据源**
**指定交通状况(Traffic)数据源**
终结点(Endpoint):
国际版: https://gspe12-ssl.ls.apple.com/traffic
高德版: https://gspe12-cn-ssl.ls.apple.com/traffic
已知影响的功能
 地图的交通浏览与路况信息
**指定兴趣点(Point of Interest, POI)数据源**
**指定飞行俯瞰(Flyover)数据源**
**指定四处看看(Look Around)数据源**

## 安装链接

#### 一键安装📥
[点击一键安装](loon://import?plugin=https%3A%2F%2Fgithub.com%2FNSRingo%2FGeoServices%2Freleases%2Flatest%2Fdownload%2FiRingo.Maps.plugin)
##### 安装路径
配置 > 插件 > 插件
#### 插件地址📦
https://github.com/NSRingo/GeoServices/releases/latest/download/iRingo.Maps.plugin

# ⭕ Siri
{% note success flat %}✅ Siri 请求 
iOS 18、macOS 15、watchOS 11 及以上版本此功能名为Siri 请求
Siri 请求使用的连接为guzzoni.smoot.apple.com
可以通过 MitM 改写
{% endnote %}
{% note danger flat %}❌ 询问 Siri 
iOS 17、macOS 14、watchOS 10 及以下版本此功能名为询问 Siri
询问 Siri使用的连接为guzzoni.apple.com
不可以通过 MitM 改写
{% endnote %}
## 简介
**将「Siri 知识」卡片改为国际版**
百度百科改为维基百科
**将「Siri 请求」的国家与地区改为🇸🇬 新加坡**
国家与地区代码改为SG
获取更多的「Siri 请求」功能
**将「Siri 请求」响应语言改为简体中文**
Siri 使用始终简体中文回答您

## 功能列表
{% note simple %} {% endnote %}

## 配置方法
**基础: 直接使用**

采用默认配置
**进阶: 配合Loon设置面板或Surge参数设置功能进行个性化设置**

提供一定的自定义设置，如国家与地区代码选择、区域选择等
**高级: 配合BoxJs及订阅使用**
{% note info flat %}ℹ️ 用前须知：使用BoxJs进行配置将被视为专业用户，官方不受理因使用BoxJs配置导致的各种问题 
**安装BoxJs插件并更新引用资源或脚本:**
安装方法及下载链接详见: 🧰 BoxJs
**在BoxJs的配置面板中进行个性化设置:**
浏览器访问BoxJs.com
在应用页面点开 iRingo折叠
在⭕ Siri根据需要填写您的设置信息
{% endnote %}

## 安装链接

#### 一键安装📥
[点击一键安装](loon://import?plugin=https%3A%2F%2Fgithub.com%2FNSRingo%2FSiri%2Freleases%2Flatest%2Fdownload%2FiRingo.Siri.plugin)
#### 手动安装
##### 安装路径
配置 > 插件 > 插件
#### 插件地址📦
https://github.com/NSRingo/Siri/releases/latest/download/iRingo.Siri.plugin

# 📺 TV
{% note default modern %}⚠️ 不支持 🇨🇳 中国大陆 的 App Store 账号{% endnote %}
## 简介
**自定义TV app，自选启用的板块、栏目及语言。**

## 解锁步骤
**· 如启用本模块后重新打开Apple TV未见生效，可按照下列步骤激活:**
{% timeline 第 1 步 %}
<!-- timeline 启用📺 TV模块 打开TVapp (app又名: TV或视频) -->


<!-- endtimeline -->

{% endtimeline %}

{% timeline 第 2 步 %}
<!-- timeline 观察是否存在下列特征: -->

**iOS/iPadOS:**
iOS 17.2 前:
观察立即观看页面是否有儿童一个二级入口
观察标签栏是否为立即观看、原创内容、商店、体育节目、资料库五个标签页
iOS 17.2 后:
立即观看被主页代替，顶端采用动态展示栏，此特征失效
标签栏固定为主页、原创内容(Apple TV+)、商店、资料库、搜索五个标签页，此特征失效
**macOS/tvOS: 查看标签栏是否有立即观看、tv+、商店、体育节目、儿童、资料库六个标签页按钮**
{% note simple %}此项目的目的是为了解锁其他地区地区账号的功能，不建议美区账号用户使用
如您的账号已经是美区账号，则可能启用前后并无差异{% endnote %}
<!-- endtimeline -->

{% endtimeline %}

{% timeline 第 3 步 %}
<!-- timeline 如不存在上述特征，可尝试以下操作强制刷新配置文件: 打开TV app(TV或视频) 点击右上角头像 点击退出登录 重新输入Apple ID与密码登入 -->

{% note simple %}此时应在Surge的最近请求或Quantumult X的网络活动中观察到:
TV app的https://uts-api.itunes.apple.com/uts/v3/configitions链接{% endnote %}
<!-- endtimeline -->

{% endtimeline %}

{% timeline 第 4 步 %}
<!-- timeline 如没有请冷启动一次TVapp (app又名: TV或视频) -->


<!-- endtimeline -->

{% endtimeline %}

## 配置方法
**· 基础: 直接使用**

· 采用默认配置
**· 进阶: 配合Loon设置面板或Surge参数设置功能进行个性化设置**

· 提供一定的自定义设置，如内置规则的分流策略选择、国家或地区代码选择等
**· 高级: 配合BoxJs及订阅使用**

{% folding green, ℹ️ 用前须知：使用BoxJs进行配置将被视为专业用户，官方不受理因使用BoxJs配置导致的各种问题 %}
安装BoxJs插件并更新引用资源或脚本:
安装方法及下载链接详见: 🧰 BoxJs
在BoxJs的配置面板中进行个性化设置:
浏览器访问BoxJs.com
在应用页面点开 iRingo折叠
在📺 TV根据需要填写您的设置信息
{% endfolding %}

## 功能列表
**混合区域支持**
· 默认混合账号所在区(立即观看、电影)，新加坡(tv+、原创内容、搜索、人物)，美国(电视节目、体育节目、儿童)三个地区的内容
· 港澳台地区账号，拥有tv+订阅的，可以收看美区tv+的体育节目直播内容（如最新内置的MLB联赛直播）
· 转区的账号，可以通过修改影片详情页观看之前所在地区购买的电影等内容（如A区购买的电影，在B区未上架）
· 语言和字幕有地区限制的内容，可以通过修改影片详情页观看中文字幕的版本（如某账号在美区购买电影无中字，但是同ID的影片在港澳台地区提供中字，可以· 通过将影片详情页改为港澳台后播放获得中文字幕）
**多语言支持**
· 底部标签栏与栏目入口语言自适应（目前仅适配简体中文、繁体中文、英语，如需更多语言适配请PR或提供翻译文本）
· 影片详情页语言自动回退
· 可自定义语言优先级，默认顺序为简体中文（新加坡） => 繁体中文（台湾） => 英语（美国）
· 解除客户端平台限制
· 为macOS、Android TV、Web版TV app启用第三方供应商(如: Disney+,Prime Video等)影片库和服务集成
**硬件及平台**
 · macOS
 · iPad
 · iPhone
 · Apple TV (需Surge for macOS的网关模式或Loon的代理服务器等)
 · Android TV (需Surge for macOS的网关模式或Loon的代理服务器等) (Android TV效果待测试，不确定是否可用)
 · Web(待测试，不确定是否可用)
**分类页面**
 · 立即观看
 · TV+（iOS/iPadOS版客户端为原创内容）
 · 商店 (电影、电视节目为商店二级菜单)
 · 体育节目 (macOS版客户端无关注「喜爱的球队」功能和显示比分功能)
 · 儿童 (iOS版客户端为立即观看二级菜单)
 · 资料库
 · 搜索

## 安装链接

#### 一键安装📥
[点击一键安装](loon://import?plugin=https%3A%2F%2Fgithub.com%2FNSRingo%2FTV%2Freleases%2Flatest%2Fdownload%2FiRingo.TV.plugin)
#### 手动安装
##### 安装路径
配置 > 插件 > 插件
#### 插件地址📦
https://github.com/NSRingo/TV/releases/latest/download/iRingo.TV.plugin


# 📰 News
## 简介
 **解锁Newsapp 使用，并自定义部分设置与功能**
 ## 解锁步骤
 {% timeline 第 1 步 %}
<!-- timeline 启用📍 定位 + 📰 News两个模块 -->

iOS 与 iPadOS 设备，还需额外在设置-通用-语言与地区中，将地区设置改为 News 可用地区
macOS 设备，可以通过为 News app 创建替身的方式，来绕过 News app 隐藏的问题
目前，仅有美国、英国、加拿大、澳大利亚四国支持 News 服务
<!-- endtimeline -->

{% endtimeline %}

{% timeline 第 2 步 %}
<!-- timeline 根据您所使用的代理APP不同，指定相关分流策略为🇺🇸美国(或其他 News 可用地区)代理策略或节点 -->

部分代理软件所使用的模块或插件中已内置了规则集或代理规则，无需额外添加相关规则或分流，其他代理软件需要手动添加相关规则或分流并指定相关策略，具体差异请参看 安装链接 段落中的使用说明。
无分流配置的情况下，也可使用全局代理模式。
<!-- endtimeline -->

{% endtimeline %}

{% timeline 第 3 步 %}
<!-- timeline 打开✈️飞行模式，同时保持Wi-Fi或有线网络连接 -->

未装有 SIM 卡的 iOS/iPadOS/macOS 设备，可省略✈️飞行模式相关步骤。
当存在移动蜂窝网络时，不触发此检测方式，将直接采用基于SIM卡的移动设备网络代码「MCC / MNC」进行检测
装有 SIM 卡的 iOS/iPadOS 设备，也可通过卡贴或海外 SIM 卡的方式，绕过基于 SIM 卡的 MCC/MNC (移动设备网络代码)检测。
基于以上原因，推荐 Mac 或无 SIM 卡的 iPad 使用 📰 News
<!-- endtimeline -->

{% endtimeline %}

{% timeline 第 4 步 %}
<!-- timeline 重新冷启动一次地图 app -->

**指后台无地图应用时，重开地图app**
在 Loon 的仪表-最近请求中应观察到:
在 Surge 的工具-最近请求中应观察到:
在 Quantumult X 的网络活动中应观察到:
基于网络的地区检测的 https://gspe1-ssl.ls.apple.com/pep/gcc 链接，且流量抓取结果不是CN
检测设备信息的 https://configuration.ls.apple.com/config/defaults 链接
<!-- endtimeline -->

{% endtimeline %}

{% timeline 第 5 步 %}
<!-- timeline 打开News，此时应是解锁状态说明中的解锁成功状态 -->

首次加载 News 需保证 gateway.icloud.com 为海外线路
使用 News 过程中 gateway.icloud.com 无策略或线路要求
<!-- endtimeline -->

{% endtimeline %}

{% timeline 第 6 步 %}
<!-- timeline 关闭✈️飞行模式，正常使用 News -->

关闭✈️飞行模式后，如再次触发基于 SIM 卡的 MCC/MNC (移动设备网络代码)检测，则 News 会回到解锁状态说明中的解锁失效状态，此时需从第 3 步再次操作。
<!-- endtimeline -->

{% endtimeline %}

## 配置方法
**· 基础: 直接使用**

· 采用默认配置
**· 进阶: 配合Loon设置面板或Surge参数设置功能进行个性化设置**

· 提供一定的自定义设置，如内置规则的分流策略选择、国家或地区代码选择等
**· 高级: 配合BoxJs及订阅使用**
{% folding green, ℹ️ 用前须知：使用BoxJs进行配置将被视为专业用户，官方不受理因使用BoxJs配置导致的各种问题 %}
安装BoxJs插件并更新引用资源或脚本:
安装方法及下载链接详见: 🧰 BoxJs
在BoxJs的配置面板中进行个性化设置:
浏览器访问BoxJs.com
在应用页面点开 iRingo折叠
在📰 News根据需要填写您的设置信息
{% endfolding %}

## 解锁状态说明
| 锁定状态               | 解锁成功                     | 解锁失效                     |
|------------------------|------------------------------|------------------------------|
| 未通过地区检测         | 已成功通过地区检测           | 通过检测后，再次触发检测时未通过检测 |
| 请在✈️飞行模式下通过Wi-Fi或有线网络再次执行解锁步骤 | gateway.icloud.com 需走代理才能完整加载内容 | 请在✈️飞行模式下通过Wi-Fi或有线网络再次执行解锁步骤 |
| Apple News isn't supported in your current region. | **Feed Unavailable** <br> There may be a problem with the server or network. Please try again later. | **Feed Unavailable** <br> Apple News isn't supported in your current region. |
| ![](https://pixpro.coul.top/i/2025/04/20/665114.webp) | ![](https://pixpro.coul.top/i/2025/04/20/337986.webp) | ![](https://pixpro.coul.top/i/2025/04/20/367370.webp) |

## 关于新闻小组件
· 新闻小组件parsecd/1.0 ({Device}; {Version} {Build}) News/1没有地区限制，可以任意区域环境下使用
· 新闻小组件内容由Siri建议服务api*.smoot.apple.com提供，而不是新闻服务news-*.apple.com，已在🆕新版Siri_Suggestions.*中修复

## 关于体育比分与赛事关注
· 关注的球队与赛事内容由体育服务WatchListKit.framework提供，而不是新闻服务news-*.apple.com，已在🆕V3版中修复

## 安装链接
#### 一键安装📥
[点击一键安装](loon://import?plugin=https%3A%2F%2Fgithub.com%2FNSRingo%2FNews%2Freleases%2Flatest%2Fdownload%2FiRingo.News.plugin)
#### 手动安装
##### 安装路径
配置 > 插件 > 插件
#### 插件地址📦
https://github.com/NSRingo/News/releases/latest/download/iRingo.News.plugin

## 默认设置
**Proxy: 策略组**
仅Surge与Egern有此设置
默认策略组名为🇺🇸美国
使用前请先修改为自己指定的美国/英国/加拿大/澳大利亚策略组或节点
**CountryCode: 国家或地区代码**
默认国家或地区代码为US
**NewsPlusUser: [搜索] 显示 News+ 内容**
默认 true (开启)


# ✈ TestFlight
{% note warning simple %}⚠️
2024.5.13 起
 升级了 TestFlight API 鉴权方式
「多账户保存及切换」功能已失效
{% endnote %}

## 功能简介
**修改国家或区域代码**
自定义 TestFlight 登录商店地区
**多账户保存及切换**
需要使用 🧰 BoxJs 面板保存和切换账号信息
**强制启用通用应用支持**
解除 TestFlight app 的 iOS/iPadOS/macOS(AppleSilicon) 平台限制
**总是显示安装选项**
当 Testflight 无法加入时，也总是显示app详情页面的安装选项
**合并通知开关**
同步开关全平台的电子邮件通知
如关闭 iOS 的 Testflight 更新电子邮件通知，也会同时关闭 tvOS 的 Testflight 更新电子邮件通

## 配置方法
**基础: 直接使用**

采用默认配置
**进阶: 配合Loon设置面板或Surge参数设置功能进行个性化设置**

提供一定的自定义设置，如国家或地区代码选择、启用通用应用支持开关等
**高级: 配合BoxJs及订阅使用**

{% folding green, ℹ️ 用前须知：使用BoxJs进行配置将被视为专业用户，官方不受理因使用BoxJs配置导致的各种问题 %}
**安装BoxJs插件并更新引用资源或脚本:**
安装方法及下载链接详见: 🧰 BoxJs
**在BoxJs的配置面板中进行个性化设置:**
浏览器访问BoxJs.com
在应用页面点开 iRingo折叠
在✈ TestFlight根据需要填写您的设置信息
{% endfolding %}

## 安装链接
#### 一键安装📥
[点击一键安装](loon://import?plugin=https%3A%2F%2Fgithub.com%2FNSRingo%2FTestFlight%2Freleases%2Flatest%2Fdownload%2FiRingo.TestFlight.plugin)
#### 手动安装
##### 安装路径
配置 > 插件 > 插件
#### 插件地址📦
https://github.com/NSRingo/TestFlight/releases/latest/download/iRingo.TestFlight.plugin

## 默认设置
**CountryCode: 国家或区域代码**
默认值: US (🇺🇸美国)
**MultiAccount: 多账户保存及切换**
默认值: false (关闭)
**Universal: 启用通用应用支持**
默认值: true (开启)
**AlwaysShowInstall: 总是显示安装选项**
默认值: false (关闭)
**MergeNotifications: 合并通知开关**
默认值: false (关闭)

# ⌚️ Watch
## 简介
### 为 Watch 提供单独的自定义设置
# 解锁步骤
## 为🧭 指南针解锁经纬度与海拔功能
## 第 1 步
启用🗺 地图模块

## 第 2 步
### 按照🗺 地图#配置方法中的 高级: 配合BoxJs及订阅使用 进行安装

浏览器访问BoxJs.com
点击底栏的应用
点开 iRingo分类
点开⌚️ Watch栏目
[URL信息集] 定位漂移改为Apple（🈶️坐标，使用🇺🇳WGS-84坐标）
保存设置
## 第 3 步
### 重新冷启动一次地图 app

### 指后台无地图应用时，重开地图app
在 Loon 的仪表-最近请求中应观察到:
在 Surge 的工具-最近请求中应观察到:
在 Quantumult X 的网络活动中应观察到:
基于网络的地区检测的 https://gspe1-ssl.ls.apple.com/pep/gcc 链接，且流量抓取结果为当前修改的地区代码
检测设备信息的 https://configuration.ls.apple.com/config/defaults 链接
## 第 4 步
### 重新冷启动一次🧭 指南针 app