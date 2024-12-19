---
title: Flutter打包web,开启本地服务
description: 将flutter项目打包web，并开启本地服务在本地预览.
author: 张帆
date: 2024-10-05 13:10:00 +0800
categories: [一些学习, Flutter]
tags: [Flutter]
# pin: true
# math: true
# mermaid: true
# image:
#   path: /commons/devices-mockup.png
#   lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
#   alt: Responsive rendering of Chirpy theme on multiple devices.
---

### 打包运行web
第一步：使已有flutter项目，支持web，在控制台 cd到项目目录
```sass
flutter config --enable-web
```
第二步，在项目根目录执行flutter create .注意有个英文符号点！
```sass
flutter create .
```
第三步，执行flutter build web就能看到web目录创建成功了。
```sass
flutter build web
```
如果想在Chrome浏览器运行：
```sass
flutter run -d chrome
```
### 开启本地服务：
1. 安装python3
2. 终端进入到对应的web文件夹下
3. 执行python3 -m http.server 8000
4. 在浏览器中http://localhost:8000/#/
