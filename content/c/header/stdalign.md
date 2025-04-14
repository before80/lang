+++
title = "<stdalign.h> (C11)(C23 弃用)"
date = 2025-04-14T14:34:51+08:00
weight = 140
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/stdalign](https://zh.cppreference.com/w/c/header/stdalign)

​	此标头是[类型支持](https://zh.cppreference.com/w/c/types)库的一部分。

## 宏

| alignas (C11)<br /> | 便利宏，展开为关键词 [`<Aligna>`](https://zh.cppreference.com/w/c/keyword/_Alignas) (关键词宏) |
| ------------------- | ------------------------------------------------------------ |
| alignof (C11)<br /> | 便利宏，展开为关键词 [`<Aligno>`](https://zh.cppreference.com/w/c/keyword/_Alignof) (关键词宏) |

## 常量

| `__alignas_is_defined` (C11)<br /> | 展开为整数常量 1 (宏常量) |
| ---------------------------------- | ------------------------- |
| `__alignof_is_defined` (C11)<br /> | 展开为整数常量 1 (宏常量) |

## 概要

```
#if __STDC_VERSION__ < 202311L
#define alignas _Alignas
#define alignof _Alignof
#define __alignas_is_defined 1
#define __alignof_is_defined 1
#endif
```