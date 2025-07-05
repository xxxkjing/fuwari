---
title: 【博客】关于这个博客
draft: false
published: 2025-04-09
category: 博客
tags:
  - 生活
  - 通知
---
# 你好，世界！

> 这个是本博客的第一篇文章

经过数个月在搭建博客，一直在纠结于主题，最终还是选择了这个。 高中生，学业繁忙，不一定长期更新

# 博客书写平台

[PagesCMS](https://pagescms.org)

参考配置文件：

```yaml
media:
  input: public
  output: /
content:
  - name: editor
    label: Posts
    type: collection
    path: src/content/posts
    view:
      fields: [ title, date, draft ]
    fields:
      - { name: title, label: Title, type: string, required: true }
      - { name: draft, label: Draft, type: boolean, default: true }
      - name: published
        label: Date
        type: date
        options:
          format: yyyy-MM-dd 
        required: true
      - name: category
        label: Category
        type: string
      - name: tags
        label: Tags
        type: string
        list:
          min: 1
          max: 6
      - name: imageupload
        label: Upload Images
        type: object
        list: true
        fields:
          - name: addimage
            label: Add Images
            type: image
            options:
              input: public/Assets
              output: /Assets/
              categories: [image]
      - { name: body, label: Text, type: rich-text } 
```

# 个人备注：

[2FA](https://2faotp.cn/)