+++
title = "<stdarg.h>"
date = 2025-04-14T14:35:58+08:00
weight = 150
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/stdarg](https://zh.cppreference.com/w/c/header/stdarg)

​	此标头提供对[变参数](https://zh.cppreference.com/w/c/variadic)函数的支持。

## 类型

| [va_list<br />](https://zh.cppreference.com/w/c/variadic/va_list) | 保有 `va_start`、`va_arg`、`va_end` 及 `va_copy` 所需的信息 (typedef) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
|                                                              |                                                              |

## 宏

| [va_start<br />](https://zh.cppreference.com/w/c/variadic/va_start) | 令函数得以访问可变实参 (宏函数)   |
| ------------------------------------------------------------ | --------------------------------- |
| [va_arg<br />](https://zh.cppreference.com/w/c/variadic/va_arg) | 访问下一个可变函数实参 (宏函数)   |
| [va_copy (C99)<br />](https://zh.cppreference.com/w/c/variadic/va_copy) | 创造函数可变实参的副本 (宏函数)   |
| [va_end<br />](https://zh.cppreference.com/w/c/variadic/va_end) | 结束对函数可变实参的遍历 (宏函数) |

## 概要

```c
#define __STDC_VERSION_STDARG_H__ 202311L
 
typedef /* 未指明 */ va_list;
 
/*type*/ va_arg(va_list ap, /*type*/);
void va_copy(va_list dest, va_list src);
void va_end(va_list ap);
void va_start(va_list ap, ...);
```