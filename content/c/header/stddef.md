+++
title = "<stddef.h>"
date = 2025-04-14T14:47:06+08:00
weight = 200
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/stddef](https://zh.cppreference.com/w/c/header/stddef)

​	此标头是[类型支持](https://zh.cppreference.com/w/c/types)库的一部分，特别是，它提供了额外的基本类型和便利宏。

## 类型

| [ptrdiff_t<br />](https://zh.cppreference.com/w/c/types/ptrdiff_t) | 两个指针相减返回的有符号整数类型 (typedef)                   |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [nullptr_t (C23)<br />](https://zh.cppreference.com/w/c/types/nullptr_t) | 预定义空指针常量 [`<ullpt>`](https://zh.cppreference.com/w/c/language/nullptr) 的类型 (typedef) |
| [max_align_t (C11)<br />](https://zh.cppreference.com/w/c/types/max_align_t) | 对齐要求不小于任何其他标量类型的类型 (typedef)               |
| [size_t<br />](https://zh.cppreference.com/w/c/types/size_t) | [`<izeo>`](https://zh.cppreference.com/w/c/language/sizeof) 运算符返回的无符号整数类型 (typedef) |

## 常量

| [NULL<br />](https://zh.cppreference.com/w/c/types/NULL) | 实现定义的空指针常量 (宏常量) |
| -------------------------------------------------------- | ----------------------------- |

## 宏

| [offsetof<br />](https://zh.cppreference.com/w/c/types/offsetof) | 从结构体类型的起始到指定成员的字节偏移 (宏函数) |
| ------------------------------------------------------------ | ----------------------------------------------- |

## 概要

```c
#define __STDC_VERSION_STDDEF_H__ 202311L
 
typedef /* 见描述 */ ptrdiff_t;
typedef /* 见描述 */ nullptr_t;
typedef /* 见描述 */ max_align_t;
typedef /* 见描述 */ wchar_t;
typedef /* 见描述 */ size_t;
 
#define NULL /* 见描述 */
#define unreachable() /* 见描述 */
#define offsetof(P, D) /* 见描述 */
```

​	仅当实现定义了 `__STDC_LIB_EXT1__` 而且用户代码在对 `stddef.h` 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：

```c
#if defined(__STDC_WANT_LIB_EXT1__)
typedef /* 见描述 */ rsize_t;
#endif
```