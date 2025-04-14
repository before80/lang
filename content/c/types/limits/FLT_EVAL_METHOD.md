+++
title = "FLT_EVAL_METHOD"
date = 2025-04-14T16:03:32+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD)

| 在标头 `<float.h>` 定义                    |      |          |
| ------------------------------------------ | ---- | -------- |
| `#define FLT_EVAL_METHOD /* 由实现定义 */` |      | (C99 起) |

​	指定从浮点常量和除了赋值、转型及库函数调用外的所有运算（运算符、操作数的隐式转换）所获得的浮点值的范围和精度。

| 值               | 解释                                                         |
| ---------------- | ------------------------------------------------------------ |
| 除 `-1` 外的负值 | 实现定义行为                                                 |
| `-1`             | 默认精度未知                                                 |
| `0`              | 以所用类型的范围和精度进行所有运算和常量求值。而且，float_t 和 double_t 分别等价于 float 和 double |
| `1`              | 以 double 的范围和精度进行所有运算和常量求值。而且，float_t 和 double_t 都等价于 double |
| `2`              | 以 long double 的范围和精度进行所有运算和常量求值。而且，float_t 和 double_t 都等价于 long double |

## 注解

​	无关乎 FLT_EVAL_METHOD 的值，任何浮点表达式都可以被*缩短*，即如同所有中间结果拥有无限范围和精度一般进行（除非关闭 [`#pragma`](https://zh.cppreference.com/w/cpp/preprocessor/impl) `STDC FP_CONTRACT`）。

​	转型和复制会剥除任何额外的范围和精度：这模拟从扩展精度 `FPU` 寄存器存储值到标准大小内存位置的动作。

## 参阅

| [float_t](https://zh.cppreference.com/w/c/numeric/math/float_t)(C99) | 宽度至少等于 float 的最高效浮点数类型 (typedef) |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [double_t](https://zh.cppreference.com/w/c/numeric/math/float_t)(C99) | 宽度至少等于 double 的最高效浮点类型 (typedef)  |
| **FLT_EVAL_METHOD** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/climits/FLT_EVAL_METHOD)** |                                                 |