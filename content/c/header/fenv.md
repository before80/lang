+++
title = "<fenv.h>"
date = 2025-04-14T09:39:26+08:00
weight = 60
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/fenv](https://zh.cppreference.com/w/c/header/fenv)

​	此标头是[浮点数环境](https://zh.cppreference.com/w/c/numeric/fenv)库的一部分。

### 类型

| 在标头 `<fenv.h>` 定义 |                                    |
| ---------------------- | ---------------------------------- |
| fenv_t                 | 表示整个浮点数环境的类型           |
| fexcept_t              | 表示所有浮点数状态标志的汇集的类型 |

### 函数

| [feclearexcept (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feclearexcept) | 清除指定的浮点数异常状态标志 (函数)                          |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [fetestexcept (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/fetestexcept) | 确认设置了哪些浮点数异常状态标志 (函数)                      |
| [feraiseexcept (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feraiseexcept) | 引发指定的浮点数异常 (函数)                                  |
| [fegetexceptflag (C99)<br />fesetexceptflag (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feexceptflag) | 将指定的浮点数异常状态标志从指定的浮点数环境获取，再设置到指定浮点数环境的操作。 (函数) |
| [fegetround (C99)<br />fesetround (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feround) | 获得或设置数字的舍入方向 (函数)                              |
| [fegetenv (C99)<br />fesetenv (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feenv) | 保存或恢复当前浮点数环境，包括异常的标志和数字的舍弃模式 (函数) |
| [feholdexcept (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feholdexcept) | 保存当前环境的异常状态标志，再清除所有异常状态标志，并忽略所有未来错误 (函数) |
| [feupdateenv (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feupdateenv) | 恢复之前保存的浮点数环境，并引发之前已经引发过的异常，使其存在于当前内存环境中 (函数) |

### 宏

| [FE_ALL_EXCEPT (C99)<br />FE_DIVBYZERO (C99)<br />FE_INEXACT<br />FE_INVALID<br />FE_OVERFLOW<br />FE_UNDERFLOW<br />](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) | 浮点数异常 (宏常量)     |
| ------------------------------------------------------------ | ----------------------- |
| [FE_DOWNWARD (C99)<br />FE_TONEAREST (C99)<br />FE_TOWARDZERO<br />FE_UPWARD<br />](https://zh.cppreference.com/w/c/numeric/fenv/FE_round) | 浮点数舍入方向 (宏常量) |
| [FE_DFL_ENV (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/FE_DFL_ENV) | 默认浮点数环境 (宏常量) |

## 概要

```c
#define __STDC_VERSION_FENV_H__ 202311L
 
#define FE_ALL_EXCEPT         /* 见描述 */
#define FE_DIVBYZERO          /* 见描述 */
#define FE_INEXACT            /* 见描述 */
#define FE_INVALID            /* 见描述 */
#define FE_OVERFLOW           /* 见描述 */
#define FE_UNDERFLOW          /* 见描述 */
#define FE_DOWNWARD           /* 见描述 */
#define FE_TONEARESTFROMZERO  /* 见描述 */
#define FE_TONEAREST          /* 见描述 */
#define FE_TOWARDZERO         /* 见描述 */
#define FE_UPWARD             /* 见描述 */
#define FE_DFL_ENV            /* 见描述 */
#define FE_DFL_MODE           /* 见描述 */
 
#define fenv_t                /* 见描述 */
#define fexcept_t             /* 见描述 */
#define femode_t              /* 见描述 */
 
#pragma STDC FENV_ACCESS      /*on-off-switch*/
#pragma STDC FENV_ROUND       direction
#pragma STDC FENV_ROUND       FE_DYNAMIC
 
// 函数
int feclearexcept(int excepts);
int fegetexceptflag(fexcept_t* flagp, int excepts);
int feraiseexcept(int excepts);
int fesetexcept(int excepts);
int fesetexceptflag(const fexcept_t* flagp, int excepts);
int fetestexceptflag(const fexcept_t* flagp, int excepts);
int fetestexcept(int excepts);
int fegetmode(femode_t* modep);
int fegetround(void);
int fesetmode(const femode_t* modep);
int fesetround(int rnd);
int fegetenv(fenv_t* envp);
int feholdexcept(fenv_t* envp);
int fesetenv(const fenv_t* envp);
int feupdateenv(const fenv_t* envp);
 
// 仅当实现定义了 __STDC_IEC_60559_DFP__：
#define FE_DEC_DOWNWARD            /* 由实现定义 */
#define FE_DEC_TONEARESTFROMZERO   /* 由实现定义 */
#define FE_DEC_TONEAREST           /* 由实现定义 */
#define FE_DEC_TOWARDZERO          /* 由实现定义 */
#define FE_DEC_UPWARD              /* 由实现定义 */
 
#pragma STDC FENV_DEC_ROUND /*dec-direction*/
int fe_dec_getround(void);
int fe_dec_setround(int rnd);
 
// 仅当实现遵循 F.2.2 的推荐实践：
#define FE_SNANS_ALWAYS_SIGNAL /* 由实现定义 */
```