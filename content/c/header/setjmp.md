+++
title = "<setjmp.h>"
date = 2025-04-14T13:57:06+08:00
weight = 130
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：

​	此标头是[程序支持工具](https://zh.cppreference.com/w/c/program#.E9.9D.9E.E5.B1.80.E9.83.A8.E8.B7.B3.E8.BD.AC)库的一部分。

## 类型

| [jmp_buf<br />](https://zh.cppreference.com/w/c/program/jmp_buf) | 执行上下文的类型 (typedef) |
| ------------------------------------------------------------ | -------------------------- |

## 宏

| [setjmp<br />](https://zh.cppreference.com/w/c/program/setjmp) | 保存上下文 (宏函数) |
| ------------------------------------------------------------ | ------------------- |

## 函数

| [longjmp<br />](https://zh.cppreference.com/w/c/program/longjmp) | 跳转到指定位置 (函数) |
| ------------------------------------------------------------ | --------------------- |

## 概要

```c
#define __STDC_VERSION_SETJMP_H__ 202311L
 
typedef /* 未指明 */ jmp_buf;
 
int setjmp(jmp_buf env);
[[noreturn]] void longjmp(jmp_buf env, int val);
```
