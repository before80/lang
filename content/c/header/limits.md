+++
title = "<limits.h>"
date = 2025-04-14T10:01:14+08:00
weight = 100
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/limits](https://zh.cppreference.com/w/c/header/limits)

​	此标头是[类型支持](https://zh.cppreference.com/w/c/types)库的一部分，特别是，它是 C [数值极限](https://zh.cppreference.com/w/c/types/limits#.E6.A0.B8.E5.BF.83.E8.AF.AD.E8.A8.80.E6.95.B4.E6.95.B0.E7.B1.BB.E5.9E.8B.E7.9A.84.E6.9E.81.E9.99.90)接口的一部分。

## 核心语言整数类型的极限

| BOOL_WIDTH   (C23)                                           | `_Bool` 的位宽 (宏常量)                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| BOOL_MAX   (C29)                                             | `_Bool` 的最大值 (宏常量)                                    |
| CHAR_BIT                                                     | 字节的位数 (宏常量)                                          |
| MB_LEN_MAX                                                   | 多字节字符的最大字节数 (宏常量)                              |
| CHAR_WIDTH   (C23)                                           | char 的位宽，同 `CHAR_BIT` (宏常量)                          |
| CHAR_MIN                                                     | char 的最小值 (宏常量)                                       |
| CHAR_MAX                                                     | char 的最大值 (宏常量)                                       |
| SCHAR_WIDTH   SHRT_WIDTH   INT_WIDTH   LONG_WIDTH   LLONG_WIDTH   (C23)   (C23)   (C23)   (C23)   (C23) | 分别为 signed char、short、int、long 和 long long 的位宽 (宏常量) |
| SCHAR_MIN   SHRT_MIN   INT_MIN   LONG_MIN   LLONG_MIN               (C99) | 分别是 signed char、short、int、long 和 long long 的最小值 (宏常量) |
| SCHAR_MAX   SHRT_MAX   INT_MAX   LONG_MAX   LLONG_MAX               (C99) | 分别是 signed char、short、int、long 和 long long 的最大值 (宏常量) |
| UCHAR_WIDTH   USHRT_WIDTH   UINT_WIDTH   ULONG_WIDTH   ULLONG_WIDTH   (C23)   (C23)   (C23)   (C23)   (C23) | 分别为 unsigned char、unsigned short、unsigned int、unsigned long 和 unsigned long long 的位宽 (宏常量) |
| UCHAR_MAX   USHRT_MAX   UINT_MAX   ULONG_MAX   ULLONG_MAX               (C99) | 分别是 unsigned char、unsigned short、unsigned int、 unsigned long 和 unsigned long long 的最大值 (宏常量) |
| BITINT_MAXWIDTH   (C23)                                      | 类型说明符 `_BitInt(N)` 中的位精确整数支持的最大宽度 N，大于或等于 `ULLONG_WIDTH` (宏常量) |

## 概要

```c
#define __STDC_VERSION_LIMITS_H__ 202311L
 
#define BITINT_MAXWIDTH  /* 见描述 */
#define BOOL_MAX         /* 见描述 */
#define BOOL_WIDTH       /* 见描述 */
#define CHAR_BIT         /* 见描述 */
#define CHAR_MAX         /* 见描述 */
#define CHAR_MIN         /* 见描述 */
#define CHAR_WIDTH       /* 见描述 */
#define INT_MAX          /* 见描述 */
#define INT_MIN          /* 见描述 */
#define INT_WIDTH        /* 见描述 */
#define LLONG_MAX        /* 见描述 */
#define LLONG_MIN        /* 见描述 */
#define LLONG_WIDTH      /* 见描述 */
#define LONG_MAX         /* 见描述 */
#define LONG_MIN         /* 见描述 */
#define LONG_WIDTH       /* 见描述 */
#define MB_LEN_MAX       /* 见描述 */
#define SCHAR_MAX        /* 见描述 */
#define SCHAR_MIN        /* 见描述 */
#define SCHAR_WIDTH      /* 见描述 */
#define SHRT_MAX         /* 见描述 */
#define SHRT_MIN         /* 见描述 */
#define SHRT_WIDTH       /* 见描述 */
#define UCHAR_MAX        /* 见描述 */
#define UCHAR_WIDTH      /* 见描述 */
#define UINT_MAX         /* 见描述 */
#define UINT_WIDTH       /* 见描述 */
#define ULLONG_MAX       /* 见描述 */
#define ULLONG_WIDTH     /* 见描述 */
#define ULONG_MAX        /* 见描述 */
#define ULONG_WIDTH      /* 见描述 */
#define USHRT_MAX        /* 见描述 */
#define USHRT_WIDTH      /* 见描述 */
```