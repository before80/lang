+++
title = "复数算术"
date = 2025-04-15T19:09:21+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文[https://zh.cppreference.com/w/c/numeric/complex](https://zh.cppreference.com/w/c/numeric/complex)

​	若实现定义了宏常量 `__STDC_NO_COMPLEX__`，则不提供头文件 [`<complex.h>`](https://zh.cppreference.com/w/c/header/complex)、复数类型以及此处列出的所有名称。(C11 起)

​	C 编程语言从 C99 开始支持三种内建类型 `double _Complex`、`float _Complex` 及 `long double _Complex` 的复数数学运算（见 [`<Comple>`](https://zh.cppreference.com/w/c/keyword/_Complex)）。包含头文件 [`<complex.h>`](https://zh.cppreference.com/w/c/header/complex) 时，三种复数类型亦可通过 double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)、float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)、long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex) 使用。

​	除了复数类型，还支持三种虚数类型：`double _Imaginary`、`float _Imaginary` 及 `long double _Imaginary`（见 [`<Imaginar>`](https://zh.cppreference.com/w/c/keyword/_Imaginary)）。包含头文件 [`<complex.h>`](https://zh.cppreference.com/w/c/header/complex) 时，三种虚数类型亦可通过 double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)、float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary) 及 long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary) 使用。

​	标准算术运算符 `+, -, *, /` 可用于实数、复数及虚数类型的任意混合。

​		推荐定义了 `__STDC_IEC_559_COMPLEX__` 编译器支持虚数，但并非强制要求。POSIX 推荐检查是否定义宏 [_Imaginary_I](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I) 以鉴别是否支持虚数。(C99 起) (C11 前)

​		若定义了 `__STDC_IEC_559_COMPLEX__` 或 `__STDC_IEC_60559_COMPLEX__`(C23 起)，则支持虚数。(C11 起)

## 类型

| 在标头 `<complex.h>` 定义                                  |                       |
| ------------------------------------------------------------ | --------------------- |
| [imaginary (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/imaginary) | 虚数类型宏 (关键词宏) |
| [complex (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/complex) | 复数类型宏 (关键词宏) |

## 虚数常量

| [_Imaginary_I (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I) | 虚数单位常量 i (宏常量)       |
| ------------------------------------------------------------ | ----------------------------- |
| [_Complex_I (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/Complex_I) | 复数单位常量 i (宏常量)       |
| [I (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/I) | 复数或虚数单位常量 i (宏常量) |

## 操作

| [CMPLX (C11)<br />CMPLXF (C11)<br />CMPLXL (C11)<br />](https://zh.cppreference.com/w/c/numeric/complex/CMPLX) | 由实部和虚部构建复数 (宏函数) |
| ------------------------------------------------------------ | ----------------------------- |
| [creal (C99)<br />crealf (C99)<br />creall (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/creal) | 计算复数的实部 (函数)         |
| [cimag (C99)<br />cimagf (C99)<br />cimagl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cimag) | 计算复数的虚部 (函数)         |
| [cabs (C99)<br />cabsf (C99)<br />cabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cabs) | 计算复数的模（绝对值） (函数) |
| [carg (C99)<br />cargf (C99)<br />cargl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/carg) | 计算复数的辐角 (函数)         |
| [conj (C99)<br />conjf (C99)<br />conjl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/conj) | 计算共轭复数 (函数)           |
| [cproj (C99)<br />cprojf (C99)<br />cprojl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cproj) | 计算黎曼球上的投影 (函数)     |

### 指数函数

| [cexp (C99)<br />cexpf (C99)<br />cexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cexp) | 计算复数的 e 底指数 (函数) |
| ------------------------------------------------------------ | -------------------------- |
| [clog (C99)<br />clogf (C99)<br />clogl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/clog) | 计算复数的自然对数 (函数)  |

### 幂函数

| [cpow (C99)<br />cpowf (C99)<br />cpowl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cpow) | 计算复数幂函数 (函数) |
| ------------------------------------------------------------ | --------------------- |
| [csqrt (C99)<br />csqrtf (C99)<br />csqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csqrt) | 计算复数平方根 (函数) |

### 三角函数

| [csin (C99)<br />csinf (C99)<br />csinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csin) | 计算复数正弦 (函数)   |
| ------------------------------------------------------------ | --------------------- |
| [ccos (C99)<br />ccosf (C99)<br />ccosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccos) | 计算复数余弦 (函数)   |
| [ctan (C99)<br />ctanf (C99)<br />ctanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctan) | 计算复数正切 (函数)   |
| [casin (C99)<br />casinf (C99)<br />casinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casin) | 计算复数反正弦 (函数) |
| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数) |
| [catan (C99)<br />catanf (C99)<br />catanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catan) | 计算复数反正切 (函数) |

### 双曲函数

| [csinh (C99)<br />csinhf (C99)<br />csinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csinh) | 计算复数双曲正弦 (函数)   |
| ------------------------------------------------------------ | ------------------------- |
| [ccosh (C99)<br />ccoshf (C99)<br />ccoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccosh) | 计算复双曲余弦 (函数)     |
| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)   |
| [casinh (C99)<br />casinhf (C99)<br />casinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casinh) | 计算复数反双曲正弦 (函数) |
| [cacosh (C99)<br />cacoshf (C99)<br />cacoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacosh) | 计算复数反双曲余弦 (函数) |
| [catanh (C99)<br />catanhf (C99)<br />catanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catanh) | 计算复数反双曲正切 (函数) |

## 注解

​	为未来加入 [`<complex.h>`](https://zh.cppreference.com/w/c/header/complex) 而潜在(C23 起)保留下列函数名，并且在包含该头文件的程序中不可使用：`cerf`、`cerfc`、`cexp2`、`cexpm1`、`clog10`、`clog1p`、`clog2`、`clgamma`、`ctgamma`、`csinpi`、`ccospi`、`ctanpi`、`casinpi`、`cacospi`、`catanpi`、`ccompoundn`、`cpown`、`cpowr`、`crootn`、`crsqrt`、`cexp10m1`、`cexp10`、`cexp2m1`、`clog10p1`、`clog2p1`、`clogp1`(C23 起)，还有它们带 -f 及 -l 后缀的变体。

​	尽管 C 标准以“复弧双曲正弦（complex arc hyperbolic sine）”等名称指名反双曲函数，双曲函数的反函数却是面积函数。它们的生成是双曲扇形的面积，而非弧长。正确名称是“复反双曲正弦”等等。一些作者会使用“复面积双曲正弦（complex area hyperbolic sine）”等名称。

​	若两部之一是无穷大，则复数或虚数为无穷大，即使另一部分是 NaN 也是如此。

​	若两部都不是无穷大或 NaN，则复数或虚数是有限的。

​	若两部皆为正零或负零，则复数或虚数为零。

​	尽管 MSVC 确实提供了 [`<complex.h>`](https://learn.microsoft.com/en-us/cpp/c-runtime-library/complex-math-support) 标头，但它并未将复数实现为本机类型，而是实现为 `struct`，这与标准 C 复数类型不兼容，且不支持 `+、-、*、/` 等运算符。

## 示例



```c
#include <stdio.h>
#include <complex.h>
#include <tgmath.h>
 
int main(void)
{
    double complex z1 = I * I;     // 虚数单位平方
    printf("I * I = %.1f%+.1fi\n", creal(z1), cimag(z1));
 
    double complex z2 = pow(I, 2); // 虚数单位平方
    printf("pow(I, 2) = %.1f%+.1fi\n", creal(z2), cimag(z2));
 
    double PI = acos(-1);
    double complex z3 = exp(I * PI); // 欧拉公式
    printf("exp(I*PI) = %.1f%+.1fi\n", creal(z3), cimag(z3));
 
    double complex z4 = 1+2*I, z5 = 1-2*I; // 共轭
    printf("(1+2i)*(1-2i) = %.1f%+.1fi\n", creal(z4*z5), cimag(z4*z5));
}
```

​	输出：

```txt
I * I = -1.0+0.0i
pow(I, 2) = -1.0+0.0i
exp(I*PI) = -1.0+0.0i
(1+2i)*(1-2i) = 5.0+0.0i
```

## 参阅

​	**复数算术**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex)**