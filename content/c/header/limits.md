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

​	此标头是[类型支持]({{< ref "/c/types" >}})库的一部分，特别是，它是 C [数值极限]({{< ref "/c/types/limits#.E6.A0.B8.E5.BF.83.E8.AF.AD.E8.A8.80.E6.95.B4.E6.95.B0.E7.B1.BB.E5.9E.8B.E7.9A.84.E6.9E.81.E9.99.90" >}})接口的一部分。

## 核心语言整数类型的极限

| BOOL_WIDTH (C23)<br />                                       | `_Bool` 的位宽 (宏常量)                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| BOOL_MAX (C29)<br />                                         | `_Bool` 的最大值 (宏常量)                                    |
| CHAR_BIT<br />                                               | 字节的位数 (宏常量)                                          |
| MB_LEN_MAX<br />                                             | 多字节字符的最大字节数 (宏常量)                              |
| CHAR_WIDTH (C23)<br />                                       | char 的位宽，同 `CHAR_BIT` (宏常量)                          |
| CHAR_MIN<br />                                               | char 的最小值 (宏常量)                                       |
| CHAR_MAX<br />                                               | char 的最大值 (宏常量)                                       |
| SCHAR_WIDTH (C23)<br />SHRT_WIDTH (C23)<br />INT_WIDTH (C23)<br />LONG_WIDTH (C23)<br />LLONG_WIDTH (C23)<br /> | 分别为 signed char、short、int、long 和 long long 的位宽 (宏常量) |
| SCHAR_MIN <br />SHRT_MIN <br />INT_MIN <br />LONG_MIN <br />LLONG_MIN (C99)<br /> | 分别是 signed char、short、int、long 和 long long 的最小值 (宏常量) |
| SCHAR_MAX <br />SHRT_MAX <br />INT_MAX <br />LONG_MAX <br />LLONG_MAX (C99)<br /> | 分别是 signed char、short、int、long 和 long long 的最大值 (宏常量) |
| UCHAR_WIDTH (C23)<br />USHRT_WIDTH (C23)<br />UINT_WIDTH (C23)<br />ULONG_WIDTH (C23)<br />ULLONG_WIDTH (C23)<br /> | 分别为 unsigned char、unsigned short、unsigned int、unsigned long 和 unsigned long long 的位宽 (宏常量) |
| UCHAR_MAX <br />USHRT_MAX <br />UINT_MAX <br />ULONG_MAX <br />ULLONG_MAX (C99)<br /> | 分别是 unsigned char、unsigned short、unsigned int、 unsigned long 和 unsigned long long 的最大值 (宏常量) |
| BITINT_MAXWIDTH (C23)<br />                                  | 类型说明符 `_BitInt(N)` 中的位精确整数支持的最大宽度 N，大于或等于 `ULLONG_WIDTH` (宏常量) |

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
