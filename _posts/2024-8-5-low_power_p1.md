---
layout: post
title: "UPF低功耗实现系列博客——1.1 低功耗设计概述"
date:   2024-8-5
tags: [low power]
comments: true
author: Shuhao
---

## 为什么需要低功耗设计？

- 便携式设备——电池寿命
- 桌面系统——高功耗
- 高功耗对系统的影响
  - 降低系统可靠性（温度升高，增加电子的迁移速度，连线的失效率上升）；
  - 降低系统性能（温度升高，降低载流子的迁移率，使得晶体管翻转时间增加，降低系统的性能）；
  - 增加生产和封装成本（高功耗需要更宽的电源线，增加面积；需要更好的散热介质）；
  - 增加系统的散热成本；
 
## 功耗类型

CMOS电路中的功耗分为动态功耗和静态功耗，公式为：

$$
P= \overbrace{   \underbrace{ \frac{1}{2}\cdot C \cdot V_{DD}^2\cdot f \cdot N_{sw}}_{翻转功耗}   +  \underbrace{ Q_{sc}\cdot V_{DD}\cdot f \cdot N_{sw}}_{短路功耗}  }^{动态功耗}+ \underbrace{\overbrace{I_{leak}\cdot V_{DD}}^{静态功耗}}_{漏电流功耗}
$$

其中$C$为负载电容，$V_{DD}$为电源电压，$f$为时钟频率，$N_{sw}$为开关次数，$Q_{sc}$为短路电荷，$I_{leak}$为漏电流。

### 动态功耗

包括翻转功耗和短路功耗。

**翻转功耗**

CMOS电路翻转过程中引起的功耗。