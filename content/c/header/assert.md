+++
title = "<assert.h>"
date = 2025-04-13T21:00:15+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/assert](https://zh.cppreference.com/w/c/header/assert)

​	This header is part of the [error handling](https://zh.cppreference.com/w/c/error) library.

## 宏

| [assert](https://zh.cppreference.com/w/c/error/assert) | 若用户指定的条件非true，则异常终止程序。可以在发行版本禁用。 (宏函数) |
| ------------------------------------------------------ | ------------------------------------------------------------ |

## 概要

```c
#if __STDC_VERSION__ >= 202311L
#   define __STDC_VERSION_ASSERT_H__ 202311L
#   ifdef NDEBUG
#       define assert(...) ((void)0)
#   else
#       define assert(...) /* 由实现定义 */
#   endif
#else
#   ifdef NDEBUG
#       define assert(condition) ((void)0)
#   else
#       define assert(condition) /* 由实现定义 */
#   endif
#endif
```
