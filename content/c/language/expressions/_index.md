+++
title = "表达式"
date = 2025-04-12T16:30:59+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/expressions](https://zh.cppreference.com/w/c/language/expressions)

​	表达式是*运算符* ﻿及其*操作数* ﻿的序列，它指定一个运算。

​	表达式求值可以产生结果（例如求值 `2 + 2` 产生结果 `4` ，可能产生副效应（例如求值 [printf](http://zh.cppreference.com/w/c/io/fprintf)("%d", 4) 会将字符 `'4'` 送到标准输出流），并可以指代对象或函数。

#### 综述

- [值类别]({{< ref "/c/language/expressions/value_category" >}})（左值、非左值对象、函数指代器）将表达式以其值分类
- 实参和子表达式的[求值顺序]({{< ref "/c/language/expressions/eval_order" >}})指定以何次序获取各中间结果

## 运算符

|                          常用运算符                          |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |
| :----------------------------------------------------------: | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [赋值]({{< ref "/c/language/expressions/operator_assignment" >}}) | [自增 自减]({{< ref "/c/language/expressions/operator_incdec" >}}) | [算术]({{< ref "/c/language/expressions/operator_arithmetic" >}}) | [逻辑]({{< ref "/c/language/expressions/operator_logical" >}}) | [比较]({{< ref "/c/language/expressions/operator_comparison" >}}) | [成员 访问]({{< ref "/c/language/expressions/operator_member_access" >}}) | [其他]({{< ref "/c/language/expressions/operator_other" >}}) |
| `a = b` <br />`a += b` <br />`a -= b` <br />`a *= b` <br />`a /= b` <br />`a %= b` <br />`a &= b` <br />`a |= b` <br />`a ^= b` <br />`a <<= b` <br />`a >>= b` | `++a` <br />`--a` <br />`a++` <br />`a--`                    | `+a` <br />`-a` <br />`a + b` <br />`a - b` <br />`a * b` <br />`a / b` <br />`a % b` <br />`~a` <br />`a & b` <br />`a | b` <br />`a ^ b` <br />`a << b` <br />`a >> b` | `!a` <br />`a && b` <br />`a || b`                           | `a == b` <br />`a != b` <br />`a < b` <br />`a > b` <br />`a <= b` <br />`a >= b` | `a[b]` <br />`*a` <br />`&a` <br />`a->b`<br /> `a.b`        | `a(...)` <br />`a, b` <br />`(type) a`<br /> `a ? b : c` <br />`sizeof`  <br />`_Alignof` (C11 起)(C23 前)  <br />`alignof` (C23 起) |

- [运算符优先级]({{< ref "/c/language/expressions/operator_precedence" >}})定义运算符绑定到其实参的顺序
- [代用表示](https://zh.cppreference.com/w/c/language/operator_alternative)是一些运算符的代用写法

### 转换

- [隐式转换]({{< ref "/c/language/expressions/conversion" >}})在操作数类型不符合运算符期待时发生。
- [转换]({{< ref "/c/language/expressions/cast" >}})可用于显示将值的类型从一个转到另一个。

### 其他

- [常量表达式]({{< ref "/c/language/expressions/constant_expression" >}})可以在编译时求值，并用于编译时语境（`非 VLA` (C99 起)数组的大小、静态初始化器等）
- [泛型选择]({{< ref "/c/language/expressions/generic" >}})可以根据实参类型执行不同的表达式 (C11 起)
- 浮点数算术可能会引发浮点数异常，并报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误 (C99 起)
- 标准 [#pragma](https://zh.cppreference.com/w/c/preprocessor/impl)：`FENV_ACCESS`、`FP_CONTRACT` 及 `CX_LIMITED_RANGE` 还有[浮点数求值精度]({{< ref "/c/types/limits/FLT_EVAL_METHOD" >}})和[舍入方向](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)控制浮点数算术求值方式。 (C99 起)

## 初等表达式

​	运算符的操作数可为其他表达式，或*初等表达式*（例如 `1 + 2 * 3` 中，运算符 `+` 的操作数是子表达式 `2 * 3` 和初等表达式 `1`）。

​	初等表达式可以是下列之一：

1) 常量及字面量（例如 `2` 或 `"Hello, world"`）
2) 适合的已声明[标识符]({{< ref "/c/language/basic_concepts/identifier" >}})（例如 n 或 [printf](http://zh.cppreference.com/w/c/io/fprintf)）
3) 3) [泛型选择]({{< ref "/c/language/expressions/generic" >}}) (C11 起)

​	任何在括号中的表达式亦被分类为初等表达式：这保证括号拥有高于任何运算符的优先级。

### 常量及字面量

​	某些类型的常量值可用称为字面量（对于左值表达式）和常量（对于右值表达式）的特殊表达式嵌入到 C 程序源代码中。

- [整数常量]({{< ref "/c/language/expressions/integer_constant" >}})是十进制、八进制或十六进制的整数类型数字。
- [字符常量]({{< ref "/c/language/expressions/character_constant" >}})是 int 类型，适于转换到字符类型 `char8_t`、(C23 起)`char16_t`、`char32_t` 或(C11 起) wchar_t 的单个字符。
- [浮点数常量]({{< ref "/c/language/expressions/floating_constant" >}})是 `float`、`double` 或 `long double` 类型的值。
- 预定义常量 [true/false]({{< ref "/c/language/expressions/bool_constant" >}}) 是 `bool` 类型的值。预定义常量 [`nullptr`]({{< ref "/c/language/expressions/nullptr" >}}) 是 [nullptr_t]({{< ref "/c/types/nullptr_t" >}}) 类型的值。(C23 起)

- [字符串字面量]({{< ref "/c/language/expressions/string_literal" >}})是类型为 `char[]`、`char8_t[]`(C23 起)、`char16_t[]`、`char32_t[]` (C11 起)或 `wchar_t[]` 的一系列字符，表示空终止字符串。
- [复合字面量]({{< ref "/c/language/expressions/compound_literal" >}})是直接嵌入程序代码的结构体、联合体或数组类型的值。(C99 起)

## 不求值表达式

​	[sizeof 运算符]({{< ref "/c/language/expressions/sizeof" >}})的操作数是不求值的表达式`（除非它们是 VLA）(C99 起)`。故而 [size_t](http://zh.cppreference.com/w/c/types/size_t) n = sizeof([printf](http://zh.cppreference.com/w/c/io/fprintf)("%d", 4)); 不会进行控制台输出。

​	[`_Alignof`]({{< ref "/c/language/expressions/_Alignof" >}})(C23 前)[`alignof`](https://zh.cppreference.com/w/c/language/alignof)(C23 起) 运算符的操作数、[泛型选择]({{< ref "/c/language/expressions/generic" >}})的控制表达式及作为 `_Alignof`(C23 前)`alignof`(C23 起) 的操作数的 VLA 的大小表达式亦为不求值的表达式。

## 参阅

**表达式**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/expressions)**
