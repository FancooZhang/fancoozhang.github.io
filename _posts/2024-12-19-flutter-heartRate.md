---
title: 如何通过手机摄像头测量“心率”？
description: 关于“心率”，你了解多少？“心率”是如何测量？如何过摄像头就能实现测量？看完这篇文章你应该会有些收获.
author: 张帆
date: 2024-12-19 14:33:00 +0800
categories: [一些思考, Flutter]
tags: [Flutter]
# pin: true
# math: true
# mermaid: true
# image:
#   path: /commons/devices-mockup.png
#   lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
#   alt: Responsive rendering of Chirpy theme on multiple devices.
---
前段时间工作原因，研究了下“心率”，把最近的研究在这里记录一下。

### 一 心率
#### 什么是心率？
  心率  即心搏频率，是单位时间内心脏搏动的次数；一般指每分钟的心跳次数。心率是描述心动周期快慢的指标，精确地定义是心室率 或 室率，因为心室是主要形成有效心搏量血流搏动的泵。[参考来源](https://en.wikipedia.org/wiki/Heart_rate)
 
#### 心率正常范围？
  心率是一项重要的生命参数，随年龄而变化：  
  新生儿（1-30 天大）    的心率范围通常为 100-205 bpm。  
  婴儿（1-11 个月大）    的心率范围为 100-180 bpm。  
  幼儿（1-2 岁）        的心率范围为 98-140 bpm。  
  学龄前儿童（3-4 岁）   的心率范围为 80-120 bpm。  
  学龄儿童（5 至 12 岁） 的心率范围为 75-118 bpm。  
  青少年（13 至 18 岁）  的心率范围为 60-100 bpm。  
  18岁及以上的成年人     预期的静息心率范围为 60-100 次/分。  
  [参考来源](https://health-e.in/blog/heart-rate-and-pulse-rate-difference/)


#### 测量心率的方法有哪些？
  心率可以用各种方法测量。听诊是一种常见的方法，医护人员使用听诊器聆听心音并计算每分钟心跳次数。另一种非侵入性方法是心电图 (ECG 或 EKG)，它使用贴在皮肤上的电极记录心脏的电活动。该测试提供对心律和心率的详细分析。这两种方法都安全、准确，并且常用于临床监测心血管健康。



### 二 脉搏
#### 什么是脉搏？
  脉搏  即动脉搏动，其成因是每次心室收缩向主动脉搏送血液的同时，动脉壁受到压力产生的搏动。以触诊的方法可感知浅在动脉的搏动。[参考来源](https://en.wikipedia.org/wiki/Pulse)

#### 脉搏正常范围？

| Age | Average Pulse Rate | 
| --- | --- | 
| `18-20` | 81 |  
| `21-30` | 80 |  
| `31-40` | 78 |  
| `41-50` | 75 |  
| `51-60` | 73 |  
| `61-70` | 73 |  
| `71-80` | 74 |  
| `Above 80` | 78 |  

[参考来源](https://health-e.in/blog/heart-rate-and-pulse-rate-difference/)

#### 测量脉搏的方法有哪些？
  测量脉搏率可以使用不同的方法，例如手动触诊、脉搏血氧仪以及移动应用程序和可穿戴设备。手动触诊方法包括在身体的特定部位感受脉搏，并计算在一定时间内感受到的脉搏次数。


### 三 心率和脉搏的关系和差异？
  心率和脉搏率的区别在于心率是指心脏每分钟跳动的次数，而脉搏率是指血液通过动脉的脉动速率。虽然两者都与心脏活动有关，正常情况下，脉搏和心率一致。两者都以每分钟心跳次数为单位，成年人的正常静息范围为每分钟 60-100 次。[参考来源](https://health-e.in/blog/heart-rate-and-pulse-rate-difference/)

  在异常情况下，如早搏、房颤、心律失常等，会导致心率大于脉率。
  
  根据上面的了解，我们知道在正常情况下，我们可以把脉率当作是心率来分析，接下里我们了解一下脉率怎么测量。


### 四 脉搏的测量
#### 压力传感器：压电式 、压阻式
  原理：压力信号 ->电信号->脉搏跳动的完整波形
#### 光电传感器：光电式
  原理：光信号 ->电信号->脉搏跳动的完整波形

![alt text](/assets/image.png)

#### 主要介绍：光电式测量脉搏
分为：透射式（指夹血氧仪）、反射式（手环、手表）
![alt text](/assets/image-1.png)

#### 原理： PPG([photoplethysmographic,光电容积脉搏波描记法](https://en.wikipedia.org/wiki/Photoplethysmogram)) 
当一定波长的光束照射到指端皮肤表面时，光束将通过透射或反射方式传送到光电接收器，在此过程中由于受到指，端皮肤肌肉和血液的吸收衰减作用，检测器检测到的光强度将减弱。其中皮肤、肌肉组织等对光的吸收在整个血液循环中是保持恒定不变的，而皮肤内的血液，容积在心脏作用下呈搏动性变化。当心脏收缩时外周血容量最多光吸收量也最大，检测到的光强度最小。而在心脏舒张时，正好相反，检测到的光强度最大，使光接收器接收到的光强度随之呈脉动性变化。由此可见容积脉搏血流中包含心搏功能血液流动等诸多心血管系统的重要信息，同时容积脉搏血流主要存在于外周周血管中的微动脉、毛细血管等微血管中， 所以容积脉搏血流同样包含有丰富的微循环生理病理信息 是我们研究人体循环系统重要的信息来源。由于光电容积脉搏波描记法并不需要复杂而昂贵的仪器设备，且操作简便 性能稳定 具有无创伤和适应性强等诸多优点，因而受到国内外医学界的普遍重视，引起工程科技人员的广泛兴趣 。自 1938 年 ，Hertzman 首次提出光电容积脉搏波描记法原理以来的半个多世纪中国内外的许多科研人员在此领域中做了大量的基础研究和临床应用研究工作， 应用领域亦由人体循环系统发展到呼吸系统 ，在人体血压、血流血氧 脑氧 肌氧 血糖 循环外周血管 脉率 呼吸率和呼吸容量等的无创检测中都有很好的应用前景，并由此开发出许多在临床上有实用价值的医疗仪器。
（引用论文 [光电容积脉搏波描记法原理及其在临床上的应用](https://link.zhihu.com/?target=http%3A//wenku.baidu.com/link%3Furl%3DPQu7tMi4saph7D1b32qtRMwQsnBBZAURTu733QHlqM3vgt38cg4Bam3gLAGTVV41020nffDLfIYgV7euHhZhcOfQrdk8GdDBKEU1Vq8rgFS)）

PPG 是一种非侵入性技术，它使用皮肤表面的光源和光电探测器来测量血液循环的体积变化。
为什么经常见到的都是绿光LED？
在血液这种红色液体面前，绿光的吸收率是最大的，对于数据判断是比较准确的。
1.皮肤的黑色素会吸收大量波长较短的波
2.皮肤上的水份也会吸收大量的UV和IR部分的光
3.进入皮肤组织的绿光(500nm)-- 黄光(600nm)大部分会被红细胞吸收
4.红光和接近IR的光相比其他波长的光更容易穿过皮肤组织
5.血液要比其他组织吸收更多的光
6.相比红光，绿（绿-黄）光能被氧合血红蛋白和脱氧血红蛋白吸收
研究表明绿光比红光更有优势，绿色 PPG 和 ECG 结果之间的相关性更强。 
参考文章：[Comparison of reflected green light and infrared photoplethysmography](https://ieeexplore.ieee.org/document/4649649)
Published in: [2008 30th Annual International Conference of the IEEE Engineering in Medicine and Biology Society](https://ieeexplore.ieee.org/xpl/conhome/4636107/proceeding)
除了PPG,还有IPPG/RPPG等技术，在这里不做详细描述


### 五 那么使用PPG原理，用手机来测量心率（脉率）是否可行？
#### 可行性论文：
[Heart Rate Monitoring Using PPG With Smartphone Camera](https://ieeexplore.ieee.org/document/9669735/references#references)
#### Abstract:
Methods of estimating heart rate without the use of sensor devices provides essential benefits in both the medical field as well as the other computing applications. Smartphones are the handiest devices available to everyone today. By using videos of fingertip captured with smartphone camera, heart rate (HR) can be estimated using the photoplethysmography (PPG) technique. It is based on tracking subtle color changes on the skin owing to cardiovascular activities. These color changes are invisible to the human eye but can be detected by digital cameras. The method is divided into three main steps: first, reading the video frames and processing them to obtain the PPG data, next, extracting the Blood Volume Pulse (BVP) signal, and finally, estimating the HR from the signal. In this project, the color intensity of the skin pixels is used, and filters are applied to eliminate the noise and retain only the pulses of interest. The extracted signal is fed into a convolutional regression neural network which outputs the estimated HR. The results obtained are compared with the ground truth HR obtained by using a contact PPG sensor. We obtained a Mean Absolute Error (MAE) of 7.01 beats per minute (bpm) and an error percentage of 8.3% on test data.

Published in: [2021 IEEE International Conference on Bioinformatics and Biomedicine](https://ieeexplore.ieee.org/xpl/conhome/9669261/proceeding) (BIBM)(国际生物信息学和生物医学会议 是生物信息学最有影响力的三大国际会议之一，致力于生物信息学和生物医学的跨领域研究)
当手机作为心率测量设备时，其后置摄像头充当 PPG 传感器（光电探测器），摄像头的闪光灯充当光源。
结论
缺点：和接触式PGG传感器测量相比，手机测量信号中包含大量的噪声，准确度低，普适性差
优点：成本低、方便、有一定准确性

### 六 手机APP计算心率原理和思路：

使用PPG原理，当手机作为心率测量设备时，其后置摄像头充当 PPG 传感器（光电探测器），摄像头的闪光灯充当光源。
#### 第一步采集图像数据：
  手机采集视频图片数据，保存视频每一帧图像用来分析光信号。
#### 第二步处理图像数据：
  1. 获取H值：计算每一帧的数据，转换成RGB数据，再转化为转化成HSV颜色模型数据，取H值。
  2. 使用差分阈值法对H处理和过滤（正常差分都会小于1，大于1的过滤）。
  3. 通过基音检测算法求出心率：，首先获取最大峰值，在最大峰值的左边和最右边（0.5-1.5个周期区域）分区别取峰值，比较左右峰值取更加接近最大峰值的一个值进行计算心率。


### 七 利用脉搏数据分析得到更多     
#### 脉搏波
  脉搏波 心脏的活动延动脉血管和血流向外周传播形成。
数据分析-时域分析（来自《信号与系统》 电子信息工程、通信工程专业的一门学科基础课）
脉搏波在医疗检测中的应用：血压监测、血氧检测、动脉硬化检测、脉率检测等。
![alt text](/assets/image-2.png)

#### 心率变异性（HRV）与脉率变异性（PRV）之间的关系
众多关于PRV和HRV相关性研究的结果表明，在一定条件（非剧烈运动、非特殊人群等）下，基于PPG的PRV分析可以等同于基于ECG的HRV分析，PRV与HRV的时域参数和频域参数的相关性基本上都在80%之上。
[脉率变异性估计心率变异性的可行性分析](https://wenku.baidu.com/view/1a69905782c4bb4cf7ec4afe04a1b0717ed5b37d.html?_wkts_=1732874723927&bdQuery=%E5%9F%BA%E4%BA%8E%E8%84%89%E6%90%8F%E6%B3%A2%E7%9A%84%E5%BF%83%E7%8E%87%E5%8F%98%E5%BC%82%E6%80%A7%E5%8F%AF%E8%A1%8C%E6%80%A7%E5%88%86%E6%9E%90)