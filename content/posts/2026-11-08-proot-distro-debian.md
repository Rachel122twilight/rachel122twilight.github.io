---
title: Proot-Distro 安装 Debian
date: 2026-11-08
draft: false
description: Proot-Distro install Debian
categories:
  - Article
tags:
  - Linux
  - Bash
  - Program
  - Phone
  - Script
cover:
  image: /images/Images/Cover/0f42856bacd559004fab80ceb4a8e3b93691003162659491.jpg
  alt: Image
  caption: Proot-Distro install Debian - Image
  relative: false
---
*2024年4月5日 20:13*

**注意：本文主要针对 Termux 环境**

---

首先更新软件包

> pkg update&&pkg upgrade

安装proot容器

> pkg install proot-distro

列出可安装的linux发行版

> proot-distro list

选择系统并下载安装系统所需的文件，这里我用的是debian

> proot-distro install debian

下载完登录系统

> proot-distro login debian

---

照例更新软件包

> apt update&&apt upgrade

安装sudo

> apt install sudo

安装图形桌面环境，这里实例用xfce4，主要是在termux上流畅，其他不是占运存就是卡

途中会有地区选择，主要选 zh_cn.UTC UTF8

> apt install xfce4

设置语言和地区，同上

> sudo apt install tzdata locales

> sudo dpkg-reconfigure tzdata

> sudo dpkg-reconfigure locales

---

修改 ~/.profile 环境配置

填入以下内容

```
LANG=zh_CN.UTF-8

LC_CTYPE=zh_CN.UTF-8

LC_NUMERIC=zh_CN.UTF-8

LC_TIME=zh_CN.UTF-8

LC_COLLATE=zh_CN.UTF-8

LC_MONETARY=zh_CN.UTF-8

LC_MESSAGES=zh_CN.UTF-8

LC_PAPER=zh_CN.UTF-8

LC_NAME=zh_CN.UTF-8

LC_ADDRESS=zh_CN.UTF-8

LC_TELEPHONE=zh_CN.UTF-8

LC_MEASUREMENT=zh_CN.UTF-8

LC_IDENTIFICATION=zh_CN.UTF-8

```

---

安装终端，vnc服务和dbus-x11

> apt-get install xfce4-terminal tightvncserver dbus-x11 -y

下载启动vnc服务的脚本，取自AnLinux

```
wget [https://raw.githubusercontent.com/EXALAB/AnLinux-Resources/master/Scripts/DesktopEnvironment/Apt/Xfce4/xstartup](https://raw.githubusercontent.com/EXALAB/AnLinux-Resources/master/Scripts/DesktopEnvironment/Apt/Xfce4/xstartup) --no-check-certificate -P ~/.vnc/

wget [https://raw.githubusercontent.com/EXALAB/AnLinux-Resources/master/Scripts/DesktopEnvironment/Apt/Xfce4/vncserver-start](https://raw.githubusercontent.com/EXALAB/AnLinux-Resources/master/Scripts/DesktopEnvironment/Apt/Xfce4/vncserver-start) --no-check-certificate -P /usr/local/bin/

wget [https://raw.githubusercontent.com/EXALAB/AnLinux-Resources/master/Scripts/DesktopEnvironment/Apt/Xfce4/vncserver-stop](https://raw.githubusercontent.com/EXALAB/AnLinux-Resources/master/Scripts/DesktopEnvironment/Apt/Xfce4/vncserver-stop) --no-check-certificate -P /usr/local/bin/
```

给脚本加执行权限

```
chmod +x ~/.vnc/xstartup

chmod +x /usr/local/bin/vncserver-start

chmod +x /usr/local/bin/vncserver-stop
```

启动、结束vnc服务

> vncserver-start

> vncserver-stop

可选更改脚本的执行命令

```
mv "/usr/local/bin/vncserver-start" "/usr/local/bin/vncstart"

mv "/usr/local/bin/vncserver-stop" "/usr/local/bin/vncstop"
```

启动vnc服务

> vncstart

xfce的语言界面设置为中文后显示乱码的解决方法，你懂的，装个输入法就好了

> sudo apt install fcitx5



安装xfce的whisker菜单插件，你也可以不装，按个人喜好

> apt install xfce4-whiskermenu-plugin

---

系统安装和配置完毕



2024/4/5-20:50

2026/1/17-21:30

2026/11/8-19:49

windfq (Tasuda/Rachel122) 著

使用 GNU nano 7.2 和其他编辑器编写。本版本编辑部分内容。



第2次更改

2024/4/30-22:09

安装sudo和更新软件包的步骤调换



---

**严禁未经允许以任何形式转载本文，违者必究**

**It is strictly forbidden to reproduce this article in any form without permission; violators will be held accountable**