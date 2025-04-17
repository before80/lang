+++
title = "<complex.h>"
date = 2025-04-13T21:16:17+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/complex](https://zh.cppreference.com/w/c/header/complex)

​	此标头是[复数算术](https://zh.cppreference.com/w/c/numeric/complex)库的一部分。



## 类型

| [imaginary (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/imaginary) | 虚数类型宏 (关键词宏) |
| ------------------------------------------------------------ | --------------------- |
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

## 概要

```c
#define __STDC_VERSION_COMPLEX_H__ 202311L
 
#define complex       _Complex
#define imaginary     /* 由实现定义 */
#define _Imaginary_I  /* 由实现定义 */
#define _Complex_I    /* 由实现定义 */
#define I             _Complex_I
 
#pragma STDC CX_LIMITED_RANGE /*ON OFF 切换开关*/
 
double complex cacos(double complex z);
float complex cacosf(float complex z);
long double complex cacosl(long double complex z);
double complex casin(double complex z);
float complex casinf(float complex z);
long double complex casinl(long double complex z);
double complex catan(double complex z);
float complex catanf(float complex z);
long double complex catanl(long double complex z);
double complex ccos(double complex z);
float complex ccosf(float complex z);
long double complex ccosl(long double complex z);
double complex csin(double complex z);
float complex csinf(float complex z);
long double complex csinl(long double complex z);
double complex ctan(double complex z);
float complex ctanf(float complex z);
long double complex ctanl(long double complex z);
double complex cacosh(double complex z);
float complex cacoshf(float complex z);
long double complex cacoshl(long double complex z);
double complex casinh(double complex z);
float complex casinhf(float complex z);
long double complex casinhl(long double complex z);
double complex catanh(double complex z);
float complex catanhf(float complex z);
long double complex catanhl(long double complex z);
double complex ccosh(double complex z);
float complex ccoshf(float complex z);
long double complex ccoshl(long double complex z);
double complex csinh(double complex z);
float complex csinhf(float complex z);
long double complex csinhl(long double complex z);
double complex ctanh(double complex z);
float complex ctanhf(float complex z);
long double complex ctanhl(long double complex z);
double complex cexp(double complex z);
float complex cexpf(float complex z);
long double complex cexpl(long double complex z);
double complex clog(double complex z);
float complex clogf(float complex z);
long double complex clogl(long double complex z);
double cabs(double complex z);
float cabsf(float complex z);
long double cabsl(long double complex z);
double complex cpow(double complex x, double complex y);
float complex cpowf(float complex x, float complex y);
long double complex cpowl(long double complex x, long double complex y);
double complex csqrt(double complex z);
float complex csqrtf(float complex z);
long double complex csqrtl(long double complex z);
double carg(double complex z);
float cargf(float complex z);
long double cargl(long double complex z);
double cimag(double complex z);
float cimagf(float complex z);
long double cimagl(long double complex z);
double complex CMPLX(double x, double y);
float complex CMPLXF(float x, float y);
long double complex CMPLXL(long double x, long double y);
double complex conj(double complex z);
float complex conjf(float complex z);
long double complex conjl(long double complex z);
double complex cproj(double complex z);
float complex cprojf(float complex z);
long double complex cprojl(long double complex z);
double creal(double complex z);
float crealf(float complex z);
long double creall(long double complex z);
 
// 仅当实现定义了 __STDC_IEC_60559_TYPES__，同时用户代码
// 在对 <complex.h> 的所有包含之前定义了 __STDC_WANT_IEC_60559_TYPES_EXT__：
#ifdef __STDC_WANT_IEC_60559_TYPES_EXT__
/*_FloatN*/ complex /*cacosfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*cacosfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ complex /*casinfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*casinfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ complex /*catanfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*catanfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ complex /*ccosfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*ccosfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ complex /*csinfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*csinfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ complex /*ctanfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*ctanfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ complex /*cacoshfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*cacoshfNx*/( /*_FloatNx*/ complex z);
/*_FloatN*/ complex /*casinhfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*casinhfNx*/( /*_FloatNx*/ complex z);
/*_FloatN*/ complex /*catanhfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*catanhfNx*/( /*_FloatNx*/ complex z);
/*_FloatN*/ complex /*ccoshfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*ccoshfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ complex /*csinhfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*csinhfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ complex /*ctanhfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*ctanhfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ complex /*cexpfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*cexpfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ complex /*clogfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*clogfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ /*cabsfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ /*cabsfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ complex /*cpowfN*/(/*_FloatN*/ complex x, /*_FloatN*/ complex y);
/*_FloatNx*/ complex /*cpowfNx*/(/*_FloatNx*/ complex x, /*_FloatNx*/ complex y);
/*_FloatN*/ complex /*csqrtfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*csqrtfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ /*cargfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ /*cargfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ /*cimagfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ /*cimagfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ complex /*CMPLXFN*/(/*_FloatN*/ x, /*_FloatN*/ y);
/*_FloatNx*/ complex /*CMPLXFNX*/(/*_FloatNx*/ x, /*_FloatNx*/ y);
/*_FloatN*/ complex /*conjfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*conjfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ complex /*cprojfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ complex /*cprojfNx*/(/*_FloatNx*/ complex z);
/*_FloatN*/ /*crealfN*/(/*_FloatN*/ complex z);
/*_FloatNx*/ /*crealfNx*/(/*_FloatNx*/ complex z);
#endif
```
