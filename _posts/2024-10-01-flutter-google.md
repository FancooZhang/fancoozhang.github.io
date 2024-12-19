---
title: Flutter 谷歌登录报错
description: Flutter开发App使用谷歌登录，显示此应用未经Google验证问题.
author: 张帆
date: 2024-10-01 11:33:00 +0800
categories: [一些坑, Flutter]
tags: [Flutter]
# pin: true
# math: true
# mermaid: true
# image:
#   path: /commons/devices-mockup.png
#   lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
#   alt: Responsive rendering of Chirpy theme on multiple devices.
---

#### 使用Flutter开发app,接入谷歌登录功能，代码开发完，在谷歌后台也配置好并且完成验证，但是谷歌登录后显示页面如下：
![1501730873339_.pic.jpg](https://upload-images.jianshu.io/upload_images/14577334-2663649a85a09ee2.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这个报错我参考了官方文档：[参考链接](https://medium.com/@seulinger/google-oauth-resolving-unverified-app-issue-on-google-cloud-oauth-consent-screen-d1079d53e7be)
通过查看官方文档，这个问题应该出在请求权限的范围不对，就是代码里请求的范围和后台配置的不一致！
然后又搜到了一个文章，这个文章里出现的问题和我一摸一样：[参考链接](https://medium.com/@seulinger/google-oauth-resolving-unverified-app-issue-on-google-cloud-oauth-consent-screen-d1079d53e7be)
#### 出错地方如下：
```sass
GoogleSignIn _googleSignIn = GoogleSignIn(
    scopes: <String>[
        'email',
      'https://www.googleapis.com/auth/contacts.readonly',//这个请求范围在谷歌后台没有配置，所以出错
      ],
    );
```

#### 因此解决办法：
1. 在代码里删除这个请求范围
2. 在后台添加这个请求范围

因为我的项目没有实际用到这个请求范围，我使用第一个方法，第二个方法会比较麻烦，这个请求范围是个敏感请求范围，需要在后台进行描述哪里使用了，并且还要上传YouTube视频链接。