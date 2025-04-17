+++
title = "浮点数环境"
date = 2025-04-15T19:07:04+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文[https://zh.cppreference.com/w/c/numeric/fenv](https://zh.cppreference.com/w/c/numeric/fenv)

​	浮点数环境是浮点数状态标志及实现所支持的控制模式的集合。它是线程局域的，每个线程从亲线程继承其浮点数环境的初始状态。浮点数运算会修改指示反常值或补助信息的浮点数状态标志。浮点数控制模式影响浮点运算的结果。

​	仅当设置 [`<#pragma STDC FENV_ACCES>`]({{< ref "/c/language/preprocessor/impl" >}}) 为 `ON` 时，浮点数环境的访问及修改才有意义。否则具体实现可以自由地假设浮点数控制模式始终是默认值，而且浮点数状态标志始终不被检测或修改。实际上，当前只有少数编译器，如 HP aCC、 Oracle Studio 和 IBM XL 明确支持此 `#pragma`，但总之多数编译器允许有意义地访问浮点数环境。

## 类型

| 在标头 `<fenv.h>` 定义 |                                      |
| ------------------------ | ------------------------------------ |
| fenv_t                   | 表示整体浮点数环境的类型             |
| fexcept_t                | 集中表示所有浮点数异常状态标志的类型 |

## 函数

| [feclearexcept (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feclearexcept) | 清除指定的浮点数异常状态标志 (函数)                          |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [fetestexcept (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/fetestexcept) | 确认设置了哪些浮点数异常状态标志 (函数)                      |
| [feraiseexcept (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feraiseexcept) | 引发指定的浮点数异常 (函数)                                  |
| [fegetexceptflag (C99)<br />fesetexceptflag (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feexceptflag) | 将指定的浮点数异常状态标志从指定的浮点数环境获取，再设置到指定浮点数环境的操作。 (函数) |
| [fegetround (C99)<br />fesetround (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feround) | 获得或设置数字的舍入方向 (函数)                              |
| [fegetenv (C99)<br />fesetenv (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feenv) | 保存或恢复当前浮点数环境，包括异常的标志和数字的舍弃模式 (函数) |
| [feholdexcept (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feholdexcept) | 保存当前环境的异常状态标志，再清除所有异常状态标志，并忽略所有未来错误 (函数) |
| [feupdateenv (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feupdateenv) | 恢复之前保存的浮点数环境，并引发之前已经引发过的异常，使其存在于当前内存环境中 (函数) |

## 宏

| [FE_ALL_EXCEPT (C99)<br />FE_DIVBYZERO (C99)<br />FE_INEXACT<br />FE_INVALID<br />FE_OVERFLOW<br />FE_UNDERFLOW<br />](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) | 浮点数异常 (宏常量)     |
| ------------------------------------------------------------ | ----------------------- |
| [FE_DOWNWARD (C99)<br />FE_TONEAREST (C99)<br />FE_TOWARDZERO<br />FE_UPWARD<br />](https://zh.cppreference.com/w/c/numeric/fenv/FE_round) | 浮点数舍入方向 (宏常量) |
| [FE_DFL_ENV (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/FE_DFL_ENV) | 默认浮点数环境 (宏常量) |
