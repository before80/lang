+++
title = "<errno.h>"
date = 2025-04-14T09:38:27+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/errno](https://zh.cppreference.com/w/c/header/errno)

​	此标头是[错误处理](https://zh.cppreference.com/w/c/error)库的一部分。

## 错误号码

| [errno](https://zh.cppreference.com/w/c/error/errno)         | 展开成 POSIX 兼容的线程局域错误编号变量 (宏变量) |
| ------------------------------------------------------------ | ------------------------------------------------ |
| [E2BIG, EACCES, ..., EXDEV](https://zh.cppreference.com/w/c/error/errno_macros) | 标准 POSIX 兼容的错误条件宏 (宏常量)             |

## 概要

```c
#define EDOM   /* 由实现定义 */
#define EILSEQ /* 由实现定义 */
#define ERANGE /* 由实现定义 */
 
#define errno  /* 由实现定义 */
 
// 仅当实现定义了 __STDC_LIB_EXT1__，并且用户代码
// 在对 <errno.h> 的所有包含前定义了 __STDC_WANT_LIB_EXT1__：
#ifdef __STDC_WANT_LIB_EXT1__
#define __STDC_LIB_EXT1__  /* 由实现定义 */
#define errno_t            /* 由实现定义 */
#endif
```
