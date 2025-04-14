+++
title = "<float.h>"
date = 2025-04-14T09:55:00+08:00
weight = 70
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

​	此标头是[类型支持](https://zh.cppreference.com/w/c/types)库的一部分，特别是其[数值极限](https://zh.cppreference.com/w/c/types/limits)接口。

## 宏

| FLT_RADIX                                                    | 全部三种浮点数类型的表示所用的基数（整数基） (宏常量)        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| DECIMAL_DIG   (C99)                                          | 将 long double 转换为带有至少 `DECIMAL_DIG` 个数位的十进制数，再转换回 long double 为恒等转换：此为序列化/反序列化 long double 所需的十进制精度 (宏常量) |
| FLT_DECIMAL_DIG   DBL_DECIMAL_DIG   LDBL_DECIMAL_DIG   (C11) | 将 float/double/long double 转换为带有至少 `FLT_DECIMAL_DIG`/`DBL_DECIMAL_DIG`/`LDBL_DECIMAL_DIG` 个数位的十进制数，再转换回去为恒等转换：此为序列号/反序列化浮点数值所需的十进制精度。分别至少定义为 6、10 和 10，或对于 IEEE float 为 9，对于 IEEE double 为 17（另见 C++ 对应物：[`max_digits10`](https://zh.cppreference.com/w/cpp/types/numeric_limits/max_digits10)） (宏常量) |
| FLT_MIN   DBL_MIN   LDBL_MIN                                 | 分别为 float、double 和 long double 的最小正规正数值 (宏常量) |
| FLT_TRUE_MIN   DBL_TRUE_MIN   LDBL_TRUE_MIN   (C11)          | 分别为 float、double 和 long double 的最小整数值 (宏常量)    |
| FLT_MAX   DBL_MAX   LDBL_MAX                                 | 分别为 float、double 和 long double 的最大有穷值 (宏常量)    |
| FLT_EPSILON   DBL_EPSILON   LDBL_EPSILON                     | 分别为 1.0 与 float、double 和 long double 的下一个可表示值之差的绝对值 (宏常量) |
| FLT_DIG   DBL_DIG   LDBL_DIG                                 | 在“文本 → float/double/long double → 文本”往返转换中保证被保留且不会印舍入或溢出而改变的十进制数位个数（参见 C++ 对应物 [`digits10`](https://zh.cppreference.com/w/cpp/types/numeric_limits/digits10) 的详情） (宏常量) |
| FLT_MANT_DIG   DBL_MANT_DIG   LDBL_MANT_DIG                  | 分别为 float、double 和 long double 可表示且不损失精度的 `FLT_RADIX` 进制有效数字数位个数 (宏常量) |
| FLT_MIN_EXP   DBL_MIN_EXP   LDBL_MIN_EXP                     | 分别为对于 float、double 和 long double 的最小负整数，使得 `FLT_RADIX` 的该整数减一次方是该类型的正规值 (宏常量) |
| FLT_MIN_10_EXP   DBL_MIN_10_EXP   LDBL_MIN_10_EXP            | 分别为对于 float、double 和 long double 的最小负整数，使得 10 的该整数次方是该类型的正规值 (宏常量) |
| FLT_MAX_EXP   DBL_MAX_EXP   LDBL_MAX_EXP                     | 分别为对于 float、double 和 long double 的最大正整数，使得 `FLT_RADIX` 的该整数减一次方是该类型的可表示有穷值 (宏常量) |
| FLT_MAX_10_EXP   DBL_MAX_10_EXP   LDBL_MAX_10_EXP            | 分别为对于 float、double 和 long double 的最大正整数，使得 10 的该整数次方是该类型的可表示有穷值 (宏常量) |
| [FLT_ROUNDS   ](https://zh.cppreference.com/w/c/types/limits/FLT_ROUNDS) | 浮点数算术的舍入模式 (宏常量)                                |
| [FLT_EVAL_METHOD   ](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD)(C99) | 指定所有算术运算以什么精度执行 (宏常量)                      |
| FLT_HAS_SUBNORM   DBL_HAS_SUBNORM   LDBL_HAS_SUBNORM   (C11)   (C23 弃用) | 类型是否支持[非正规](https://en.wikipedia.org/wiki/Denormal_number)）数值：<br /> `-1` – 不确定, `0` – 不支持, `1` – 支持 (宏常量) |

> 本节未完成 
>
> 原因：Add macros from B.6.2, B.6.3

## 概要

```c
#define FLT_ROUNDS           /* 见定义 */
#define FLT_EVAL_METHOD      /* 见定义 */
#define FLT_HAS_SUBNORM      /* 见定义 */
#define DBL_HAS_SUBNORM      /* 见定义 */
#define LDBL_HAS_SUBNORM     /* 见定义 */
#define FLT_RADIX            /* 见定义 */
#define FLT_MANT_DIG         /* 见定义 */
#define DBL_MANT_DIG         /* 见定义 */
#define LDBL_MANT_DIG        /* 见定义 */
#define FLT_DECIMAL_DIG      /* 见定义 */
#define DBL_DECIMAL_DIG      /* 见定义 */
#define LDBL_DECIMAL_DIG     /* 见定义 */
#define DECIMAL_DIG          /* 见定义 */
#define FLT_DIG              /* 见定义 */
#define DBL_DIG              /* 见定义 */
#define LDBL_DIG             /* 见定义 */
#define FLT_MIN_EXP          /* 见定义 */
#define DBL_MIN_EXP          /* 见定义 */
#define LDBL_MIN_EXP         /* 见定义 */
#define FLT_MIN_10_EXP       /* 见定义 */
#define DBL_MIN_10_EXP       /* 见定义 */
#define LDBL_MIN_10_EXP      /* 见定义 */
#define FLT_MAX_EXP          /* 见定义 */
#define DBL_MAX_EXP          /* 见定义 */
#define LDBL_MAX_EXP         /* 见定义 */
#define FLT_MAX_10_EXP       /* 见定义 */
#define DBL_MAX_10_EXP       /* 见定义 */
#define LDBL_MAX_10_EXP      /* 见定义 */
#define FLT_MAX              /* 见定义 */
#define DBL_MAX              /* 见定义 */
#define LDBL_MAX             /* 见定义 */
#define FLT_EPSILON          /* 见定义 */
#define DBL_EPSILON          /* 见定义 */
#define LDBL_EPSILON         /* 见定义 */
#define FLT_MIN              /* 见定义 */
#define DBL_MIN              /* 见定义 */
#define LDBL_MIN             /* 见定义 */
#define FLT_TRUE_MIN         /* 见定义 */
#define DBL_TRUE_MIN         /* 见定义 */
#define LDBL_TRUE_MIN        /* 见定义 */
```