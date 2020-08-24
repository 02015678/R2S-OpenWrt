## R2S 基于原生OpenWRT 的固件(AS IS, NO WARRANTY!!!)
[![NanoPi-R2S_Openwrt1907_Fat](https://github.com/02015678/R2S-OpenWrt/workflows/R2S-OpenWrt-Without-Docker/badge.svg)](https://github.com/02015678/R2S-OpenWrt/actions?query=workflow%3AR2S-OpenWrt-Without-Docker) 

### 下载地址：
https://github.com/project-openwrt/R2S-OpenWrt/releases

### 追新党可以在Action中取每日更新（可能会翻车，风险自担，需要登陆github后才能下载）：
https://github.com/project-openwrt/R2S-OpenWrt/actions

### 本地一键编译命令（注意装好依赖）：
安装依赖：
```shell
sudo -E apt-get install -y build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev libz-dev patch unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex uglifyjs git-core gcc-multilib g++-multilib p7zip p7zip-full msmtp libssl-dev texinfo libreadline-dev libglib2.0-dev xmlto qemu-utils upx libelf-dev autoconf automake libtool autopoint ccache curl wget vim nano python python3 python-pip python3-pip python-ply python3-ply haveged lrzsz device-tree-compiler scons
```
```shell
wget -O - https://raw.githubusercontent.com/friendlyarm/build-env-on-ubuntu-bionic/master/install.sh | bash
```
一键编译（测试编译环境是Ubuntu18.04）：
```shell
git clone https://github.com/project-openwrt/R2S-OpenWrt.git && cd R2S-OpenWrt && bash onekeyr2s.sh
```
### 注意事项：
0.OC至1.608GHz（未提升电压，原则上不会增加大量额外发热）。建议不要超过1.5GHz。

1.登陆IP：192.168.1.1 密码：无

2.OP内置sysupgrade升级可用

3.SSRP使用姿势： ①添加你要的订阅链接 ②再在最后加一行空行 ③右下角点一下保存并应用 ④更新所有订阅服务器节点

4.遇到上不了网的，请自行排查自己的ipv6联通情况。注意需要在防火墙自定义规则新增以下规则并重启防火墙：
```
# 定义 IPv6 WAN 接口名（Linux）
iface_linux=pppoe-wan
# 建立 IPv6 NAT
ip6table
```

5.固件分为docker版和无docker版本，docker版支持部分无线网卡和docker-ce，但由于docker的依赖问题，ssrp之类的软件存在udp转发异常的故障；无docker使用需求的，推荐使用无docker版固件。
**docker版不再维护**

6.刷写或升级后遇到任何问题，可以尝试ssh进路由器，输入fuck，回车后等待重启，或可解决

7.从2020.8.1开始重新交换 LAN WAN，解决千兆环境下IDM下载掉速的问题，用户注意！！！！！（当前靠外的是LAN，靠中心的是WAN）

8.sys灯引导时闪烁，启动后常亮，是上游的设定，有疑问请联系OP官方社区

9. 相比[QiuSimons/R2S-OpenWrt](https://github.com/QiuSimons/R2S-OpenWrt)，新增了TTYD, FileTransfer，以及统计(显示历史温度、CPU、系统负载，就像你在很多VPS控制面板上看到的那样)。但为了固件体积尽量小，并未像[songchenwen/nanopi-r2s](https://github.com/songchenwen/nanopi-r2s)安装netdata那样酷炫的监控面板。

9.预配置了部分插件，ADG的管理密码默认admin

### 版本信息：
其他模块版本：SNAPSHOT（当日最新）

LUCI版本：19.07（当日最新）

### 特性及功能：
1.O3编译（获得更高的理论性能

2.内置三款主题(默认是bootstrap，想好看和手机友好的可以选择argon)

3.插件包含：SSRP，PassWall，OpenClash，AdguardHome，BearDropper，微信推送，网易云解锁，SQM，SmartDNS，ChinaDNS，网络唤醒，DDNS，迅雷快鸟，UPNP，FullCone(防火墙中的选项，默认开启)，流量分载(防火墙中的选项，默认未开启)，SFE流量分载(也就是SFE加速，防火墙中的选项，默认开启)，BBR（默认开启），irq优化，OLED屏幕支持，京东签到，Zerotier，FRPC/FRPS，无线USB打印，流量监控

4.核心频率1.608GHz。建议不要超过1.5GHz。

### 固件预览：
<img src="https://cdn.jsdelivr.net/gh/project-openwrt/R2S-OpenWrt@master/PIC/app.png" width="1024" />

### 防呆指导：
<img src="https://cdn.jsdelivr.net/gh/project-openwrt/R2S-OpenWrt@master/PIC/offload.png" width="1024" />
<img src="https://cdn.jsdelivr.net/gh/project-openwrt/R2S-OpenWrt@master/PIC/fullcone1.png" width="1024" />
<img src="https://cdn.jsdelivr.net/gh/project-openwrt/R2S-OpenWrt@master/PIC/fullcone2.png" width="1024" />
<img src="https://cdn.jsdelivr.net/gh/project-openwrt/R2S-OpenWrt@master/PIC/fullcone3.png" width="1024" />

### OLED效果预览：
<img src="https://cdn.jsdelivr.net/gh/project-openwrt/R2S-OpenWrt@master/PIC/oled.jpg" width="1024" />
