+++
title = "<stdnoreturn.h> (C11)(C23 弃用)"
date = 2025-04-14T15:21:54+08:00
weight = 250
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：https://zh.cppreference.com/w/c/header/stdnoreturn

​	此标头提供一个便利宏 [`noreturn`](https://zh.cppreference.com/w/c/language/noreturn)，用于指示函数不返回到其调用点。

## 宏

| noreturn(C11)(C23 弃用) | 便利宏，展开为 [`_Noreturn`](https://zh.cppreference.com/w/c/keyword/_Noreturn) (关键词宏) |
| ----------------------- | ------------------------------------------------------------ |

### 概要

```c
#define noreturn _Noreturn
```