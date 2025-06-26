---
title: 【Linux】在Manjaro上游玩杀戮尖塔时的错误
draft: false
published: 2025-04-27
category: Linux
tags:
  - 游戏
  - 杀戮尖塔
  - Java
---
安装时是一直没有问题的

但是打开游戏就会Java报错：

```bash
Exception in thread "LWJGL Application" java.lang.ExceptionInInitializerError
        at com.badlogic.gdx.backends.lwjgl.LwjglGraphics.setVSync(LwjglGraphics.java:558)
        at com.badlogic.gdx.backends.lwjgl.LwjglApplication$1.run(LwjglApplication.java:124)
Caused by: java.lang.ArrayIndexOutOfBoundsException: 0
        at org.lwjgl.opengl.LinuxDisplay.getAvailableDisplayModes(LinuxDisplay.java:954)
        at org.lwjgl.opengl.LinuxDisplay.init(LinuxDisplay.java:738)
        at org.lwjgl.opengl.Display.<clinit>(Display.java:138)
        ... 2 more
```

后来翻阅Github才知道要安装xrendr模块

> 参考 [Github Issue](https://github.com/ValveSoftware/steam-runtime/issues/702)

在ArchLinux搜索到软件名为\`xorg-xrendr\`

> 仓库链接 [xorg-xrendr](https://archlinux.org/packages/?name=xorg-xrandr)

所以Manjaro linux下安装命令为：

```bash
sudo pacman -S xorg-xrendr
```

然后就能顺利打开了