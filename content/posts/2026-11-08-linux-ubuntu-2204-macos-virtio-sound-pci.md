---
title: Linux Ubuntu 22.04 安装 macOS 的 virtio-sound-pci 问题
date: 2026-11-08
draft: false
description: Problems Installing macOS virtio-sound-pci on Linux Ubuntu 22.04
categories:
  - A symphony of development, downloading, installation, and tutorials
tags:
  - Linux
  - macOS
  - Bash
  - Script
cover:
  image: /images/Images/Cover/7d5d60dfa234e72f95ef8edfd3b5bfff3691003162659491.png
  alt: Image
  relative: false
---
*2026年02月23日 15:27*



在 Ubuntu 22.04 发行版下使用 quickemu 安装 macOS（尤其是 Monterey 发行版）时会有 qemu 报错 virtio-sound-pci 是个不存在的参数。

这通常是因为安装在系统的 qemu 版本还没有 virtio-sound-pci 这个声卡，如果你不想编译 qemu，那么这里有个简单的办法，就是绕过它，使用其他的声卡。

到你的 quickemu 安装目录修改 quickemu 文件，然后找到第 1103 行，把 virtio-sound-pci 替换成 qemu 支持的声卡，此处使用 ich9-intel-hda。

![Before - Image](/images/Images/Picture/9b8e5d4e1996ad821952612e02da13603691003162659491.png)

![After - Image](/images/Images/Cover/7d5d60dfa234e72f95ef8edfd3b5bfff3691003162659491.png)

然后就可以运行了，此教程也适用于一些较旧的 Linux 发行版。



如果你的 quickemu 与本教程不一样，可以使用我在 GitHub Fork 的版本。

仓库链接：

[https://github.com/Rachel122twilight/quickemu](https://github.com/Rachel122twilight/quickemu)

---

**严禁未经允许以任何形式转载本文，违者必究**

**It is strictly forbidden to reproduce this article in any form without permission; violators will be held accountable**