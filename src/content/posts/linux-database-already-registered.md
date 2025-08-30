---
title: 【Linux】database already registered解决方案
draft: false
published: 2025-03-22
category: 系统
tags:
  - Linux
  - 软件源
---
## 引言

本来想要装一个\`Open Cave Adventure\`玩一玩，不知道之前怎么乱搞软件源，报了个从来没见过的错误

## 报错

```bash
➜  ~ yay -S open-adventure
 -> database already registered
```

## 分析

已经有软件的数据库注册了，说明配置文件存在重复写入，所以可以先检查配置文件

## 解决方案

### 打开配置文件

运行\`sudo vim /etc/pacman.conf\`

按\`G\`转到最后一行

### 发现问题

这里是发现发现\`sublime text\`软件数据库重复

具体是这样的：

```ini
[sublime-text]
Server = https://download.sublimetext.com/arch/stable/x86_64
Server = https://download.sublimetext.com/arch/stable/x86_64
```

其实只要删除重复行就能解决问题了

## 备注

附上Linux通用安装\`sublime text\`方法

### 先导入GPG密钥

```bash
curl -O https://download.sublimetext.com/sublimehq-pub.gpg && sudo pacman-key --add sublimehq-pub.gpg && sudo pacman-key --lsign-key 8A8F901A && rm sublimehq-pub.gpg
```

### 添加软件源

```bash
echo -e "\n[sublime-text]\nServer = https://download.sublimetext.com/arch/stable/x86_64" | sudo tee -a /etc/pacman.conf
```

### 安装软件

#### 方法一

```bash
sudo pacman -S sublime-text
```

**注意**！ 这里pacman用的是\`Arch Linux\`系的软件包管理器，一定根据自身情况修改命令，不要无脑复制粘贴

#### 方法二

```bash
sudo pacman -Syu
```

_这个是官方提供的_，但是我个人\*\*极不推荐\*\*，因为这个命令是全面升级系统，如果很久没有升级，会一下安装很多很多很多很多的软件，然后让电脑安装到爆炸（不要问我怎么知道的）