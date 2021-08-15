---

layout: post
title: "Mathematica 复习"
subtitle: ''
date: 2020-11-27 23:00:00
author: "Mike Lyou"
#header-style: text
header-img: "img/post-bg-table.jpg"
mathjax: true
catalog: true
copyright-statement: CC BY-NC-SA
hidden: false
excerpt: 因为每次都要打开帮助查看用法，决定写一份简短的总结。
tags:
 - Software
 - Language/Wolfram-Mathematica

---

<!-- more -->

### Plot 函数

- 基础用法：

$$
\operatorname{Plot}\left[f(x),\left\{x, x_{\min }, x_{\max }\right\}\right]
$$

​	范例: `Plot[Sin[x], {x, 0, 6 Pi}]`

- 可以同时绘制多个函数：

$$
\operatorname{Plot}\left[\left\{f_{1}(x), f_{2}(x), \ldots\right\},\left\{x, x_{\min }, x_{\max }\right\}\right]
$$

​	范例：`Plot[{Sin[x], Sin[2 x], Sin[3 x]}, {x, 0, 2 Pi}]`

**选项:**

- 显示图例	`PlotLegends -> "Expressions"`

- 标注曲线（贴紧曲线）`PlotLabels -> "Expressions"`

- 不绘制轴 `Axes -> False`

  只绘制某个轴 `Axes -> {False, True}`

- 指定每个轴的标签  `AxesLabel -> {x, Sinc[x]}`

  （也可使用 `Automatic` 自动添加轴标签）

- 指定轴原点 `AxesOrigin -> {1, 2}` （也可使用`Automatic`）

- 显示剪切区域 `ClippingStyle -> Automatic` （有更多选项）

- 填充 `Filling` （略）

- 为整个绘图添加标签（标题）`PlotLabel -> "title"`

