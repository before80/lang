+++
title = "<signal.h>"
date = 2025-04-14T14:32:48+08:00
weight = 130
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/signal](https://zh.cppreference.com/w/c/header/signal)

​	此标头是[程序支持](https://zh.cppreference.com/w/c/program)库的一部分。

## 类型

| [sig_atomic_t<br />](https://zh.cppreference.com/w/c/program/sig_atomic_t) | 可以从异步信号处理函数中将之当做原子实体进行访问的整数类型 (typedef) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
|                                                              |                                                              |

## 宏

| [SIGABRT<br />SIGFPE<br />SIGILL<br />SIGINT<br />SIGSEGV<br />SIGTERM<br />](https://zh.cppreference.com/w/c/program/SIG_types) | 定义信号类型 (宏常量)     |
| ------------------------------------------------------------ | ------------------------- |
| [SIG_DFL<br />SIG_IGN<br />](https://zh.cppreference.com/w/c/program/SIG_strategies) | 定义信号处理策略 (宏常量) |
| [SIG_ERR<br />](https://zh.cppreference.com/w/c/program/SIG_ERR) | 遇到错误 (宏常量)         |

## 函数

| [signal<br />](https://zh.cppreference.com/w/c/program/signal) | 为特定的信号设置信号处理函数 (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [raise<br />](https://zh.cppreference.com/w/c/program/raise) | 运行特定信号的信号处理函数 (函数)   |

## 概要

```c
typedef sig_atomic_t /* 见描述 */;
 
void (*signal(int sig, void (*func)(int)))(int);
int raise(int sig);
 
#define SIG_DFL  /* 见描述 */
#define SIG_ERR  /* 见描述 */
#define SIG_IGN  /* 见描述 */
#define SIGABRT  /* 见描述 */
#define SIGFPE   /* 见描述 */
#define SIGILL   /* 见描述 */
#define SIGINT   /* 见描述 */
#define SIGSEGV  /* 见描述 */
#define SIGTERM  /* 见描述 */
```
