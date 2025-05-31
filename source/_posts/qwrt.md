---
title: "Qwrt配置教程"
highlight_shrink: false
tags:
  - Qwrt
categories: qwrt
description: 添加大量外挂标签样式。
top_img: "https://pixpro.coul.top/i/2025/04/17/295180.webp"
cover: "https://pixpro.coul.top/i/2025/04/17/295180.webp"
swiper_index: 6
abbrlink: qwrt-config

date: 2025-4-10 15:55:44
comments:
copyright: true
copyright_author: 
copyright_author_href: 
copyright_url: 
katex:
ai: 
---
{% note blue 'anzhiyufont anzhiyu-icon-bullhorn' simple %}
`Qwrt固件`如有需要，点击[固件](https://file.coul.top/%E4%B8%AD%E5%9B%BD%E7%A7%BB%E5%8A%A8%E7%BD%91%E7%9B%98/QWRT)，可自行下载安装，但**请勿用于商业用途和传播**，转载文章请注明来自[罐頭](https://blog.coul.top)
{% endnote %}
ⓘ 如果你用的是Qwrt固件，那么你可以用这个教程来配置你的路由器。

# SQM Qos智能队列配置

{% tip %}食用SQM Qos智能队列你可以启用流量整形，更好的混合(公平队列)主动列队管理(AQM)并设置网口{% endtip %}

### 在QWRT的SQM设置中，不同的队列管理算法(fq_codel、cake、sfq、pie和codel)有不同的的特点和场景，以下是这种常见的队列管理算法的介绍：

1. **fq_codel**：fq_codel是一种基于令牌桶的队列管理算法，结合了公平队列和延迟控制，通过公平队列和codel主动管理队列来减少流量竞争和网络拥塞。适合大多数家庭网络场景，能有效减少延迟。
2. **cake**：cake是一种专为WiFi设计的队列管理算法，它通过动态调整数据包传输速率来优化WiFi性能。cake支持多队列分类和优先级管理，可以自动识别和优化不同类型的流量。
3. **sfq**：sfq是一种基于随机公平队列的算法，避免单一流量占用过多宽带；简单哟有效，适合小型网络。
4. **pie**：pie是一种基于比例积分误差的算法，类似于codel，但更侧重于动态调整；通过预测队列长度来提前丢弃数据包，避免延迟增加。
5. **codel**：codel是一种基于控制延迟的算法，主动队列管理算法，专注于减少延迟，通过丢弃数据包来避免缓冲区膨胀，但没有公平队列，可能多用户场景下表现不佳。

### 队列脚本模块，用于管理网络流量脚本

1. **layer_cake.qos**食用cake作为队列管理，同时替代htb作为整形器和fq_codel作为叶子队列。允许对不同的类型流量整形，并支持优先级分类。
2. **piece_of_cake.qos**同样食用cake作为队列管理，但配置非常简单，不涉及复杂的优先级分类，直接食用cake的默认配置。
3. **simple.qos**食用默认的队列管理算法(通常是fq_codel);提供三层次优先级的带宽方案。
4. **simplest_tbf.qos**使用tbf作为简单的速率限制器，限制器上默认附加队列算法，不支持优先级
5. **simplest.qos**使用htb作为速率限制器，默认的队列管理算法，不支持优先级。


# 校园网防检测
### QWRT大雕固件大概从24，9便是决定后续所出的固件都是编译好UA2F所需的环境
{% tip ban %}可能存在的检测方式:{% endtip %}

1. 基于 IPv4 数据包包头内的 TTL 字段的检测（固定TTL）
2. 基于 HTTP 数据包请求头内的 User-Agent 字段的检测(使用UA2F)
3. 基于 IPv4 数据包包头内的 Identification 字段的检测（rkp-ipid 设置 IPID）
4. 基于网络协议栈时钟偏移的检测技术（统一时间）
5. Flash Cookie 检测技术（iptables 拒绝 AC 进行 Flash 检测 ，现在已经用不到了，flash都已经过时了，谁还用flash）
6. DPI （Deep Packet Inspection：深度包检测技术 ，非常耗费性能，学校一般不会开启，如果启用，只能走隧道加密）

### 如何安装UA2F

有一些固件（如部分新版QWRT,immortalwrt,istoreos等）它是不直接带UA2F的，那么如何使用它呢

首先刷新软件包目录或者命令行执行opkg update,然后检查已安装软件包，搜索nfqueue,如果没有任何东西，你可以换一个固件或者使用ua3f（详见https://blog.sunbk201.site/posts/ua3f/）,因为这个重要依赖是在内核编译的时候放进去的,不能通过外源安装，如果强行安装ua2f，要么提示缺依赖爆红，要么插件不起作用。

如果里面有iptables-mod-nfqueue和kmod-ipt-nfqueue 在**自定义软件源**中添加一行

src/gz openwrt_kiddin9 https://dl.openwrt.ai/packages-23.05/aarch64_cortex-a53/kiddin9

提交，然后刷新软件包，搜索ua2f,会弹出来ua2f和luci-app-ua2f,点击安装luci-app-ua2f，ua2f会自动被随着安装好，然后打开服务，然后前三项开启，后两项关闭

{% radio red, 注意：必须关闭所有软硬件流量分载（kwrt(opai编译的固件)防火墙和turboacc里面有取 %}

消勾选按钮，QWRT比如qca-nss-ecm,在系统-启动项中先关闭然后再禁用,hwnat同理，然后在Turbo ACC网络加速中禁用全锥形NAT，其他两个bbr和dns缓存可以打开）

此外，你还可以安装quickstart和luci-app-quickstart为其适配istoreos界面,方法都很类似，参见https://www.right.com.cn/forum/thread-8291884-1-1.html

{% folding cyan open, 上面环境配置好之后然后再打开防火墙，输入 %}
```txt

iptables -t nat -A PREROUTING -p udp --dport 53 -j REDIRECT --to-ports 53

iptables -t nat -A PREROUTING -p tcp --dport 53 -j REDIRECT --to-ports 53

#防时钟偏移检测

iptables -t nat -N ntp_force_local

iptables -t nat -I PREROUTING -p udp --dport 123 -j ntp_force_local

iptables -t nat -A ntp_force_local -d 0.0.0.0/8 -j RETURN

iptables -t nat -A ntp_force_local -d 127.0.0.0/8 -j RETURN

iptables -t nat -A ntp_force_local -d 192.168.0.0/16 -j RETURN

iptables -t nat -A ntp_force_local -s 192.168.0.0/16 -j DNAT --to-destination 192.168.1.1

#通过 iptables 修改 TTL 值 数字为需要的修改的ttl值

iptables -t mangle -A POSTROUTING -j TTL --ttl-set 64

#iptables 拒绝 AC 进行 Flash 检测

iptables -I FORWARD -p tcp --sport 80 --tcp-flags ACK ACK -m string --algo bm --string " src=\"http://1.1.1." -j DROP

如果你加入了IPID模块，则还要增加

#若没有加入rkp-ipid模块，此部分不需要加入

iptables -t mangle -N IPID_MOD

iptables -t mangle -A FORWARD -j IPID_MOD

iptables -t mangle -A OUTPUT -j IPID_MOD

iptables -t mangle -A IPID_MOD -d 0.0.0.0/8 -j RETURN

iptables -t mangle -A IPID_MOD -d 127.0.0.0/8 -j RETURN

#由于本校局域网是A类网，所以我将这一条注释掉了，具体要不要注释结合你所在的校园网

#iptables -t mangle -A IPID_MOD -d 10.0.0.0/8 -j RETURN

iptables -t mangle -A IPID_MOD -d 172.16.0.0/12 -j RETURN

iptables -t mangle -A IPID_MOD -d 192.168.0.0/16 -j RETURN

iptables -t mangle -A IPID_MOD -d 255.0.0.0/8 -j RETURN

iptables -t mangle -A IPID_MOD -j MARK --set-xmark 0x10/0x10

```
{% endfolding %}

最后配置一下ntp服务器


- 进入 OpenWRT 系统设置, 勾选 Enable NTP client（启用 NTP 客户端）和 Provide NTP server（作为 NTP 服务器提供服务）

- NTP server candidates（候选 NTP 服务器）四个框框分别填写 **ntp1.aliyun.com**、**time1.cloud.tencent.com**、**stdtime.gov.hk** 、**pool.ntp.org**

- 点击同步浏览器时间一次


{% tip key %}上面所有参数配置完之后输入该网站ua.233996.xyz验证防检测效果，如果一串fffffffff则成功{% endtip %}


{% folding cyan open, 如果路由器防火墙是firewall4（nftables）怎么办呢 %}
```txt
#将部分命令转换一下

nft add rule ip nat prerouting udp dport 53 counter redirect to:53

nft add rule ip nat prerouting tcp dport 53 counter redirect to:53

nft add chain ip nat ntp_force_local '{ type nat hook prerouting priority 0 ; }'

nft add rule ip nat prerouting udp dport 123 counter jump ntp_force_local

nft add rule ip nat ntp_force_local ip daddr 0.0.0.0/8 counter return

nft add rule ip nat ntp_force_local ip daddr 127.0.0.0/8 counter return

nft add rule ip nat ntp_force_local ip daddr 192.168.0.0/16 counter return

nft add rule ip nat ntp_force_local ip saddr 192.168.0.0/16 counter dnat to 192.168.1.1

nft add rule ip mangle postrouting counter ttl set 64

nft add rule ip filter forward tcp sport 80 tcp flags & ack ack counter string match " src=\"http://1.1.1." algo bm drop

```
{% endfolding %}


# 锐捷认证

**minieap**

{% radio checked, 锐捷认证有两种插件，一种是使用MentoHUST，另一种是使用minieap %}
{% tip %}并不推荐食用MentoHUST，强烈建议换用 minieap，移植方式没有太多改变，十分简单，然而性能及稳定性大幅提升{% endtip %}

{% link 这是一个实现了标准 EAP-MD5-Challenge 算法的 EAP 客户端，支持通过插件来修改标准数据包以通过特殊服务端的认证。,github-minieap,https://github.com/updateing/minieap,https://github.com/images/modules/search/mona-love-2x.png %}

## MiniEAP
=========

这是一个实现了标准 EAP-MD5-Challenge 算法的 EAP 客户端，支持通过插件来修改标准数据包以通过特殊服务端的认证。目前带有一个实现锐捷 v3 (v4) 算法的插件。本插件的认证算法来自 [Hu Yunrui 的 MentoHUST 项目](https://github.com/hyrathb/mentohust)，在此表示感谢！

### 特性

#### 通用特性

* 模块化设计
可在 `config.mk` 中直观选择所需模块。如需添加模块，直接复制一份现有的 `minieap.mk` 并按需修改即可。

* 网络帧收发由插件模块完成
可根据平台差异使用不同的插件。目前提供 `libpcap` 和 Raw Socket 两种插件。前者兼容性好，但需链接 `libpcap`，体积较大；后者不需额外动态库，但只能在 Linux 上使用。可选择任意个模块参与编译，但运行时只能选取其中之一来使用。

* 数据包修改同样由插件完成
可以在不修改主要认证流程的情况下适配各种环境。可以启用多个插件，也可将一个插件启用多次。程序会让标准 EAP 算法生成的数据包按照命令行中 `--module` 参数的顺序让数据包流经这些插件。目前提供一个锐捷 v3 认证算法插件和一个打印流经的数据包大小的示例插件。

* 所有数据包生成逻辑均采用结构体对缓冲区进行读写，拒绝 magic number 从我做起！

#### 锐捷插件特性

* 认证算法来自 [Hu Yunrui 的 MentoHUST 项目](https://github.com/hyrathb/mentohust)
* 相比原本的 MentoHUST v3 (v4) 实现，能够支持更多的字段，更容易通过验证。
* 二次认证时，支持位于修改常规字段以外的 IP 地址、网关、主 DNS 等信息，更容易通过验证。
* 所有字段都通过收集来的信息直接构造而成，不采用修改数据包模板的方式，避免各场景下偏移量不同导致的认证失败或数据包无法解析问题。
* 所有字段生成逻辑均采用结构体对缓冲区进行读写，拒绝 magic number 从我做起 x2！
* 字段中所用到的常量都有宏定义来注明其含义，定长字段的长度也通过宏定义声明，拒绝 magic number 从我做起 x3！
* 支持通过命令行来附加新的字段，也可覆盖程序生成的字段。可以在不修改代码的情况下进行适配。
* 整体程序的内存占用比 MentoHUST 小约 78%（在 256 MB 内存的 ARMv7 平台上测试）。

### 编译

1. 编辑 `config.mk`，选择所需要的模块。
在以 `if_impl` 开头的模块中，Linux 环境建议只选择 `if_impl_sockraw` 模块，其他平台建议只选择 `if_impl_libpcap` 模块。
在以 `packet_plugin` 开头的模块中，请按需要选择。
注：若选择 `if_impl_libpcap`，将自动添加 `-lpcap` 选项。

2. 本程序需要使用 `getifaddrs`。
如果您的平台没有提供此函数，可自行寻找需要的实现，并在 `include/` 中添加 `ifaddrs.h`，在 `util/ifaddrs/` 目录中添加必要的 C 文件，最后在 `config.mk` 中选中 `ifaddrs` 模块即可。

3. 如果服务器消息乱码，可将 `config.mk` 中的 `ENABLE_ICONV` 置为 1.
若平台未提供iconv相关函数，需手动链接 `libiconv` 库。

4. 执行 `make` 即可在根目录下编译出可执行文件。

注1：如需要交叉编译，可参考 `config.mk` 中的示例。

注2：如需要链接外部库，请在 `COMMON_CFLAGS`、`COMMON_LDFLAGS`、`LIBS` 中加入合适的 `-I -L -l` 等选项。

### 运行

具体选项请参阅 `minieap -h` 的输出。这里列出必需的几个选项。

* `-u 用户名`
* `-p 密码`
* `-n 网卡名`

默认的网络帧收发模块是 `if_impl_sockraw`。如果要使用其他模块，如 `libpcap`，则必须指定 `--if-impl libpcap`。

默认不使用任何数据包修改器，将只会发送单纯的标准 EAP 数据包。 **如需使用锐捷认证，则必须指定 `--module rjv3`。** 可以指定多个 `--module` 参数，程序会按参数的顺序让数据包流经这些插件。

参数格式支持如下几种：

* `-u myname`
* `--username myname`

注意：暂不支持 `-umyname` 这种形式，这在插件的命令行解析中将带来错误。

示例：在 en0 上使用锐捷认证，以 `libpcap` 作为网络帧收发模块，并且在数据包流经锐捷认证插件前后都打印出数据包的大小：

```
minieap -u 201000000 -p 15000000000 -n en0 --module printer --module rjv3 --module printer --if-impl libpcap
```

### 注意事项
{% folding cyan open, 终端执行：minieap -h 查看帮助 %}
```txt
 minieap是一个允许私有扩展的 802.1x 客户端，可通过插件实现私有部分的认证。

以下选项中，[]表示可选参数，<>表示必选参数。

        --help, -h      显示本帮助
        --kill, -k [1]  终止其他实例并退出。加任意非 0 参数表示终止其他实例后继续进行认证
        --save, -w      保存本次认证所用参数
        --username, -u <...>    用户名
        --password, -p <...>    密码
        --nic, -n <...>         要使用的网络界面名
        --stage-timeout, -t <num>       单个认证阶段的超时时间 [默认5]
        --wait-after-fail, -r <num>     认证失败后重新认证前的等待时间（但当服务器要求重新认证时将直接开始认证）[默认30]
        --max-fail, -l <num>    最大允许认证失败次数 [默认3]
        --no-auto-reauth, -x    认证掉线后不允许自动重连 [默认1]
        --daemonize, -b <0-3>   后台运行方式： [默认0]
                                0 = 不后台
                                1 = 后台运行，关闭输出
                                2 = 后台运行，输出到当前控制台
                                3 = 后台运行，输出到日志文件
        --proxy-lan-iface, -z <...>     代理认证时的 LAN 网络界面名 [默认无]
        --auth-round, -j <num>  需要认证的次数 [默认1]
        --max-retries <num>     最大超时重试的次数 [默认3]
        --pid-file <...>        PID 文件路径，设为none可禁用 [默认/var/run/minieap.pid]
        --conf-file <...>       配置文件路径 [默认/etc/minieap.conf]
        --if-impl <...>         选择此网络操作模块，仅允许选择一次 [默认为第一个可用的模块]
        --pkt-plugin <...>      启用此名称的数据包修改器，可启用多次、多个 [默认无]
        --module <...>          同上
                                当命令行选项中存在 --module 或 --pkt-plugin 时，配置文件中的所有 module= 行都将被忽略

以下是可用的网络操作模块：

    sockraw (采用RAW Socket进行通信的轻量网络接口模块)

以下是可用的数据包修改插件及其选项：

    插件名称： printer (将流经此插件的数据包内容打印出来)
        此插件无选项可用

    插件名称： rjv3 (来自 hyrathb@GitHub 的 Ruijie V3 验证算法)
        --heartbeat, -e <num>           心跳间隔秒数 [默认60]
        --eap-bcast-addr, -a <0-1>      Start 包广播地址： [默认BROADCAST_STANDARD]
                                        0 = 标准地址
                                        1 = 锐捷私有地址
        --dhcp-type, -d <0-3>           DHCP 方式： [默认DHCP_AFTER_AUTH]
                                        0 = 不使用 DHCP
                                        1 = 二次认证
                                        2 = 认证后 DHCP
                                        3 = 认证前 DHCP
        --dhcp-script, -c <...>         二次认证之间及认证完成后运行此命令 [默认无]
        --rj-option <type>:<value>[:r]  自定义认证字段，其中 type 和 value 必须为十六进制串
                                        如 --rj-option 6a:000102 表示新增一条类型为 0x6a、内容为 0x00 0x01 0x02的字段
                                        :r 表示替换内置生成的字段，如 --rj-option 6f:000102:r 表示将内置算法生成的类型为 0x6f 的字段内容替换为 0x00 0x12 0x02
                                        当命令行与配置文件中同时存在此选项时，两处的选项都将发挥作用。若认证失败，请检查配置文件中是否有错误的参数
        --service <str>                 自定义服务名 [默认internet]
        --version-str <str>             自定义版本字符串 [默认RG-SU For Linux V1.0]
        --fake-dns1 <str>               自定义主 DNS 地址（点分十进制 IPv4 格式） [默认自动获取]
        --fake-dns2 <str>               自定义次 DNS 地址（IPv4 / IPv6 不限） [默认自动获取]
        --fake-serial <str>             自定义硬盘序列号 [默认自动获取]
        --max-dhcp-count <num>          二次认证时等待 DHCP 结果的允许超时次数 [默认3]
        从 --service 到 --fake-serial（除 --fake-dns1）都是对应的 --rj-option 的简单形式，可直接使用 ASCII 字符串作为参数，不需转化为十六进制表示

注意：选项与参数之间必须用空格分开！
```
{% endfolding %}