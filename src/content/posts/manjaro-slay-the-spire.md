---
title: 在Manjaro上游玩杀戮尖塔时的错误
draft: true
published: 2025-04-27
category: Linux
tags:
  - Game
  - Slay The Spire
  - Java
---
安装时是一直没有问题的

但是打开游戏就会Java报错：Unknown module

后来翻阅Github才知道要安装xrendr模块

在manjaro linux下安装命令为：

```bash
sudo pacman -S xorg-xrendr
```

然后就能顺利打开了