+++
title = "<stdbool.h>"
date = 2025-04-14T14:44:53+08:00
weight = 180
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/stdbool](https://zh.cppreference.com/w/c/header/stdbool)

​	此标头提供用于[布尔类型](https://zh.cppreference.com/w/c/types)的宏。

## 宏

| bool (C99)<br /> | 便利宏，展开为 [`<Boo>`](https://zh.cppreference.com/w/c/language/arithmetic_types#.E5.B8.83.E5.B0.94.E7.B1.BB.E5.9E.8B) (关键词宏) |
| ---------------- | ------------------------------------------------------------ |

## 宏常量

| true (C99)<br />                            | 展开为整数常量 1 (宏常量) |
| ------------------------------------------- | ------------------------- |
| false (C99)<br />                           | 展开为整数常量 0 (宏常量) |
| `__bool_true_false_are_defined` (C99)<br /> | 展开为整数常量 1 (宏常量) |

## 概要

```c
#if __STDC_VERSION__ < 202311l
#define bool _Bool
#define true 1
#define false 0
#endif
 
#define __bool_true_false_are_defined 1
```