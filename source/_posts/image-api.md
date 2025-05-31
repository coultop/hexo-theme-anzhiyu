---
title: "随机图api教程"
highlight_shrink: false
tags:
  - 随机图
categories: 随机图
description: 添加大量外挂标签样式。
top_img: "https://pixpro.coul.top/i/2025/04/20/544624.webp"
cover: "https://pixpro.coul.top/i/2025/04/20/544624.webp"
swiper_index: 6
abbrlink: image-api

date: 2025-4-20 15:55:44
comments:
copyright: true
copyright_author: 
copyright_author_href: 
copyright_url: 
katex:
ai: 
---
# API随机获取图片代码（Redis缓存+文件变更检测）

{% note warning simple %}因为使用了Redis缓存，所以宝塔面板得安装好Redis缓存器和Redis缓存插件（打开php管理即可进行安装扩展插件）{% endnote %}

参考了[梦佬](https://blog.bsgun.cn/posts/9642fffa/)的教程文章
{% tip cogs %}API随机获取图片代码以下是一个简单的PHP代码示例，用于从文本文件中随机选择一张图片，并返回该图片的URL。该代码使用了Redis缓存和文件变更检测，以提高性能和减少IO操作。{% endtip %}
```php
<?php
// Redis配置（根据实际情况修改）
$redisConfig = [
    'host' => '127.0.0.1',
    'port' => 6379,
    'password' => '',    // 如果有密码请填写
    'database' => 0
];

// 初始化Redis连接
$redis = new Redis();
try {
    $redis->connect($redisConfig['host'], $redisConfig['port']);
    if (!empty($redisConfig['password'])) {
        $redis->auth($redisConfig['password']);
    }
    $redis->select($redisConfig['database']);
} catch (Exception $e) {
    die("Redis连接失败: " . $e->getMessage());
}

// 定义文件路径
$imgFile = __DIR__ . '/img.txt';
$counterFile = __DIR__ . '/counter.dat';

// 高性能读取图片列表（Redis缓存+文件变更检测）
$cacheKey = 'cached_pics';
$mtimeKey = 'cached_mtime';

$currentMTime = file_exists($imgFile) ? filemtime($imgFile) : 0;
$cachedMTime = $redis->get($mtimeKey);

if (!$redis->exists($cacheKey) || $currentMTime != $cachedMTime) {
    if (!file_exists($imgFile)) die('文件不存在');
    
    // 高效读取文件并过滤空行
    $pics = file($imgFile, FILE_IGNORE_NEW_LINES | FILE_SKIP_EMPTY_LINES);
    $pics = array_map('trim', $pics);
    $pics = array_filter($pics);
    
    if (empty($pics)) die('图片列表为空');
    
    // 存储到Redis（有效期1小时，按需调整）
    $redis->setex($cacheKey, 3600, serialize($pics));
    $redis->set($mtimeKey, $currentMTime);
} else {
    $pics = unserialize($redis->get($cacheKey));
}

// 原子计数器（Redis实现）
$counter = $redis->incr('visit_counter');
// 每100次写入磁盘（降低IO压力）
if ($counter % 100 === 0) {
    file_put_contents($counterFile, $counter, LOCK_EX);
}

// 高性能随机选择（避免array_rand内存问题）
$pic = $pics[random_int(0, count($pics) - 1)];

// 输出处理
if (isset($_GET['type']) && $_GET['type'] === 'json') {
    header('Content-Type: application/json');
    die(json_encode(['pic' => $pic]));
} else {
    header("Location: $pic");
    exit;
}
```
上传你的服务器或者主机空间，命名随意后缀为.php

并在同级目录上传一个为img.txt后缀的文件

PS：一个图片链接链接占一行

访问形式为 http(s)://你的域名/你的命名.php

例如 https://api.coul.top/coul.php

输出为图片
