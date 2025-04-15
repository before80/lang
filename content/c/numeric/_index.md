+++
title = "数值"
date = 2025-04-15T18:16:16+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文[https://zh.cppreference.com/w/c/numeric](https://zh.cppreference.com/w/c/numeric)

​	C 数值库包含常用数学函数和类型，还支持随机数生成。

## 常用数学函数

​	[常用数学函数](https://zh.cppreference.com/w/c/numeric/math)

​	头文件 [`<math.h>`](https://zh.cppreference.com/w/c/header/math) 提供[标准 C 库数学函数](https://zh.cppreference.com/w/c/numeric/math)，如 [fabs](https://zh.cppreference.com/w/c/numeric/math/fabs)、[sqrt](https://zh.cppreference.com/w/c/numeric/math/sqrt) 和 [sin](https://zh.cppreference.com/w/c/numeric/math/sin)。

## 浮点数环境

​	[浮点数环境](https://zh.cppreference.com/w/c/numeric/fenv)

​	头文件 [`<fenv.h>`](https://zh.cppreference.com/w/c/header/fenv) 定义[与浮点数异常状态（例如溢出和除以零）有关的标志和函数](https://zh.cppreference.com/w/c/numeric/fenv)。

伪随机数生成

[伪随机数生成](https://zh.cppreference.com/w/c/numeric/random)

​	头文件 [`<stdlib.h>`](https://zh.cppreference.com/w/c/header/stdlib) 亦包含经由 [srand](https://zh.cppreference.com/w/c/numeric/random/srand) 和 [rand](https://zh.cppreference.com/w/c/numeric/random/rand) 进行的 C 风格随机数生成。

## 复数算术

​	[复数算术](https://zh.cppreference.com/w/c/numeric/complex)

​	头文件 [`<complex.h>`](https://zh.cppreference.com/w/c/header/complex) 提供作用于[复数](https://zh.cppreference.com/w/c/numeric/complex)的类型和函数。

## 泛型数学

​	[泛型数学](https://zh.cppreference.com/w/c/numeric/tgmath)

​	头文件 [`<tgmath.h>`](https://zh.cppreference.com/w/c/header/tgmath) 为函数提供某些名为 XXX 的宏：

- 实函数：
  - float 变体 `XXXf`
  - double 变体 `XXX`
  - long double 变体 `XXXl`

- 复函数：
  - float 变体 `cXXXf`
  - double 变体 `cXXX`
  - long double 变体 `cXXXl`

## 位操纵

​	[位操纵](https://zh.cppreference.com/w/c/numeric/bit_manip) (C23 起)

​	头文件 [`<stdbit.h>`](https://zh.cppreference.com/w/c/header/stdbit) 提供作用于[字节序](https://zh.cppreference.com/w/c/numeric/bit_manip#.E5.AE.8F)和 C 对象的[字节与位表示](https://zh.cppreference.com/w/c/numeric/bit_manip#.E5.87.BD.E6.95.B0)的宏和函数。

​	

## 带检查整数算术 (C23 起)

​	提供一些用于带检查整数算术的类型通用宏：

| 在标头 `<stdckdint.h>` 定义                                |                                       |
| ------------------------------------------------------------ | ------------------------------------- |
| [ckd_add (C23)<br />](https://zh.cppreference.com/w/c/numeric/ckd_add) | 两个整数的带检查加法运算 (泛型函数宏) |
| [ckd_sub (C23)<br />](https://zh.cppreference.com/w/c/numeric/ckd_sub) | 两个整数的带检查减法运算 (泛型函数宏) |
| [ckd_mul (C23)<br />](https://zh.cppreference.com/w/c/numeric/ckd_mul) | 两个整数的带检查乘法运算 (泛型函数宏) |

## 参阅

​	**数值库**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric)**