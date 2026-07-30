---
tags:
  - 考研408/数学
  - 高等数学
  - 知识点
date: 2026-07-21
category: 概念定理/公式总结
---

# 一元函数微分学中 dx、dy、$\Delta x$ 与 $\Delta y$ 的关系

## 一、 概念定义

在微积分中，自变量的增量、自变量的微分、因变量的增量以及因变量的微分是四个核心概念：
1. **自变量增量** $\Delta x$：自变量在点 $x_0$ 处的实际变化量。
2. **自变量微分** $\text{d}x$：人为定义自变量的微分等于其增量，即：
   $$ \text{d}x = \Delta x $$
3. **因变量增量** $\Delta y$：函数在自变量变化 $\Delta x$ 时的真实改变量：
   $$ \Delta y = f(x_0 + \Delta x) - f(x_0) $$
4. **因变量微分** $\text{d}y$：当因变量增量 $\Delta y$ 可以写成 $\Delta y = A\Delta x + o(\Delta x)$（其中 $A$ 与 $\Delta x$ 无关）的形式时，称函数在点 $x_0$ 处可微，并称其线性主部 $A\Delta x$ 为因变量的微分，记作：
   $$ \text{d}y = f'(x_0)\text{d}x $$

## 二、 核心定理与公式

### 1. 恒等关系
实际增量 $\Delta y$ 与微分 $\text{d}y$ 在极限状态下的关系为：
$$ \Delta y = \text{d}y + o(\Delta x) \quad (\Delta x \to 0) $$

### 2. 近似关系
当 $|\Delta x|$ 极小时，可以通过微分近似代替实际增量：
$$ \Delta y \approx \text{d}y \quad \text{即} \quad f(x_0 + \Delta x) - f(x_0) \approx f'(x_0)\Delta x $$

### 3. 等价无穷小关系
当 $f'(x_0) \neq 0$ 且 $\Delta x \to 0$ 时，$\Delta y$ 与 $\text{d}y$ 为等价无穷小：
$$ \lim_{\Delta x \to 0} \frac{\Delta y}{\text{d}y} = 1 \implies \Delta y \sim \text{d}y \quad (\Delta x \to 0) $$

## 三、 考点与典型题型分析

### 1. 考研地位与常考方式
此部分通常在考研数学一中以选择题或填空题的形式出现，主要考查：
- 可导与可微的定义和充要关系（在一元函数中两者等价）。
- 结合极限定理分析导数或微分的存在性。
- 结合函数图形的凸凹性，考查实际增量与微分的大小比较。

### 2. 典型例题：大小比较
**【例题】**
设函数 $f(x)$ 在区间 $I$ 上二阶可导，且 $f''(x) > 0$。当自变量增量 $\Delta x > 0$ 时，试比较 $\Delta y$ 与 $\text{d}y$ 的大小关系。

**【解析】**
1. 几何法：
   - 因为 $f''(x) > 0$，所以曲线 $y = f(x)$ 是凹的，在几何上曲线位于其任意一点切线的上方。
   - 设 $P(x_0, f(x_0))$ 为曲线上一点，在此点的切线方程为 $y - f(x_0) = f'(x_0)(x - x_0)$。
   - 当自变量增加 $\Delta x > 0$ 后，曲线上点的高度为 $f(x_0 + \Delta x)$，切线上对应点的高度为 $f(x_0) + f'(x_0)\Delta x$。
   - 因为曲线位于切线上方，故有：
     $$ f(x_0 + \Delta x) > f(x_0) + f'(x_0)\Delta x $$
     $$ f(x_0 + \Delta x) - f(x_0) > f'(x_0)\Delta x $$
   - 根据定义，左边为 $\Delta y$，右边为 $\text{d}y$（因为 $\text{d}x = \Delta x > 0$），故：
     $$ \Delta y > \text{d}y $$

2. 代数法（泰勒公式/拉格朗日中值定理）：
   - 将 $f(x_0 + \Delta x)$ 在 $x_0$ 处展开到一阶泰勒公式（带拉格朗日余项）：
     $$ f(x_0 + \Delta x) = f(x_0) + f'(x_0)\Delta x + \frac{f''(\xi)}{2!}(\Delta x)^2 \quad (\xi \text{ 介于 } x_0 \text{ 与 } x_0+\Delta x \text{ 之间}) $$
   - 变形得：
     $$ \Delta y = \text{d}y + \frac{f''(\xi)}{2}(\Delta x)^2 $$
   - 因为 $f''(x) > 0$，且 $(\Delta x)^2 > 0$（无论 $\Delta x > 0$ 还是 $\Delta x < 0$），所以余项部分 $\frac{f''(\xi)}{2}(\Delta x)^2 > 0$。
   - 从而得到：
     $$ \Delta y > \text{d}y $$

### 3. 易错点总结
- **一元与多元的区别**：一元函数中“可导”即“可微”，但在多元函数中可偏导不一定可微。
- **等价无穷小的前提**：$\Delta y \sim \text{d}y$ 的前提是导数不为零。如果 $f'(x_0) = 0$，微分 $\text{d}y = 0$，此时它们不能构成等价无穷小。
