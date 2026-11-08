---
title: 终端输出色彩测试 Terminal output color test
date: 2026-11-08
draft: false
description: Terminal output color test
categories: Article
tags: Develop, Linux, Bash
---
2026/01/18/ 17:11

https://i1.hdslb.com/bfs/new_dyn/4fbb3f2aac335e7302aba47169468c1f3691003162659491.jpg

apt 2048 里找到的文件，需要自取

#!/bin/bash

echo "[8 colors] => ^[[4#m"

for color in {0..7} ; do

  #Display the color

  number=$(printf " %-5d " "$color")

  echo -en "\033[4${color}m${number}\033[0m"

  #Display 8 colors per line

  if [ $((($color + 1) % 8)) == 0 ] ; then

    echo #New line

  fi

done

echo "[16 colors] => ^[[48;5;#m"

for color in {0..15} ; do

  #Display the color

  number=$(printf " %-5d " "$color")

  echo -en "\033[48;5;${color}m${number}\033[0m"

  #Display 8 colors per line

  if [ $((($color + 1) % 8)) == 0 ] ; then

    echo #New line

  fi

done

echo "[216 colors] => ^[[48;5;#m"

for color in {16..231} ; do

  #Display the color

  number=$(printf " %-7d " "$color")

  echo -en "\033[48;5;${color}m${number}\033[0m"

  #Display 6 colors per line

  if [ $((($color - 15) % 6)) == 0 ] ; then

    echo #New line

  fi

done

echo "[24 shades of gray] => ^[[48;5;#m"

for color in {232..255} ; do

  #Display the color

  number=$(printf " %-3d " "$color")

  echo -en "\033[48;5;${color}m${number}\033[0m"

  #Display 12 colors per line

  if [ $((($color - 231) % 12)) == 0 ] ; then

    echo #New line

  fi

done