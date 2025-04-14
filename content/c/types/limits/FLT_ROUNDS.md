+++
title = "FLT_ROUNDS"
date = 2025-04-14T16:02:23+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/types/limits/FLT_ROUNDS](https://zh.cppreference.com/w/c/types/limits/FLT_ROUNDS)

| 在标头 `<float.h>` 定义               |      |      |
| ------------------------------------- | ---- | ---- |
| `#define FLT_ROUNDS /* 由实现定义 */` |      |      |

​	返回浮点算术运算的当前舍入方向。

​	含义相同 含义相同 含义相同 含义相同

| 值     | 解释                                                         |
| ------ | ------------------------------------------------------------ |
| `-1`   | 默认舍入方向未知                                             |
| `0`    | 向零，与 [FE_TOWARDZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_round) |
| `1`    | 向最近值，与 [FE_TONEAREST](https://zh.cppreference.com/w/c/numeric/fenv/FE_round) |
| `2`    | 向正无穷大，与 [FE_UPWARD](https://zh.cppreference.com/w/c/numeric/fenv/FE_round) |
| `3`    | 向负无穷大，与 [FE_DOWNWARD](https://zh.cppreference.com/w/c/numeric/fenv/FE_round) |
| 其他值 | 实现定义行为                                                 |

## 注意

​	可用 [fesetround](https://zh.cppreference.com/w/c/numeric/fenv/feround) 更改舍入模式，而 **FLT_ROUNDS** 反映其更改。

## 参阅

| [fegetroundfesetround](https://zh.cppreference.com/w/c/numeric/fenv/feround)(C99)(C99) | 获得或设置数字的舍入方向 (函数) |
| ------------------------------------------------------------ | ------------------------------- |
| [FE_DOWNWARDFE_TONEARESTFE_TOWARDZEROFE_UPWARD](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)(C99) | 浮点数舍入方向 (宏常量)         |
| **FLT_ROUNDS** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/climits/FLT_ROUNDS)** |                                 |