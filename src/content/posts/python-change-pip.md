---
title: 【Python】pip换源
draft: false
published: 2025-07-29
category: 代码
tags:
  - 编程环境
  - Python
  - 软件源
description: 最简单、最快捷的Python换源教程
---
# 单次换源

只需要打开终端输入以下命令：

```bash
pip install your-package -i https://mirrors.aliyun.com/pypi/simple/
```

其中的 \`your-package\` 要替换成自己需要安装的库

# 全局换源

只需要打开终端输入以下命令：

```bash
pip config --site set global.index-url https://mirrors.aliyun.com/pypi/simple/
```

就会写入 pip 的配置文件中，下载软件速度提高

# 备注

几个常用的软件源：

*   阿里云：[**https://mirrors.aliyun.com/pypi/simple/**](https://mirrors.aliyun.com/pypi/simple/)[](https://mirrors.aliyun.com/pypi/simple/%EF%BF%BC%E8%B1%86%E7%93%A3%EF%BC%9Ahttps://pypi.douban.com/simple/%EF%BF%BC%E4%B8%AD%E7%A7%91%E5%A4%A7%EF%BC%9Ahttps://pypi.mirrors.ustc.edu.cn/simple/)
    
*   豆瓣：[**https://pypi.douban.com/simple/**](https://pypi.douban.com/simple/)
    
*   中科大：[**https://pypi.mirrors.ustc.edu.cn/simple/**](https://pypi.mirrors.ustc.edu.cn/simple/)
    

### 特别备注

清华源似乎不能使用了，在复制网上教程时须注意