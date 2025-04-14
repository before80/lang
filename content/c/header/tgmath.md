+++
title = "<tgmath.h>"
date = 2025-04-14T15:24:32+08:00
weight = 270
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/tgmath](https://zh.cppreference.com/w/c/header/tgmath)

​	此标头是[数值](https://zh.cppreference.com/w/c/numeric#.E6.B3.9B.E5.9E.8B.E6.95.B0.E5.AD.A6)库的一部分，并提供一套[泛型宏](https://zh.cppreference.com/w/c/numeric/tgmath)，它们基于实参类型来确定调用哪个实数函数（或适用时为复数函数）。

## 包含

| [`<math.h>`](https://zh.cppreference.com/w/c/header/math)  |
| ------------------------------------------------------------ |
| [`<complex.h>`](https://zh.cppreference.com/w/c/header/complex) |

> 本节未完成 
>
> 原因：7.28 Type-generic math <tgmath.h>

## 概要

> 本节未完成 
>
> 原因：B.27 Type-generic math <tgmath.h>

```c
#include <math.h>
#include <complex.h>
 
#define __STDC_VERSION_TGMATH_H__ 202311L
#define acos              /* 见描述 */
#define acosh             /* 见描述 */
#define acospi            /* 见描述 */
#define asin              /* 见描述 */
#define asinh             /* 见描述 */
#define asinpi            /* 见描述 */
#define atan              /* 见描述 */
#define atan2             /* 见描述 */
#define atan2pi           /* 见描述 */
#define atanh             /* 见描述 */
#define atanpi            /* 见描述 */
#define cbrt              /* 见描述 */
#define ceil              /* 见描述 */
#define compoundn         /* 见描述 */
#define copysign          /* 见描述 */
#define cos               /* 见描述 */
#define cosh              /* 见描述 */
#define cospi             /* 见描述 */
#define dadd              /* 见描述 */
#define ddiv              /* 见描述 */
#define dfma              /* 见描述 */
#define dmul              /* 见描述 */
#define dsqrt             /* 见描述 */
#define dsub              /* 见描述 */
#define erf               /* 见描述 */
#define erfc              /* 见描述 */
#define exp               /* 见描述 */
#define exp10             /* 见描述 */
#define exp10m1           /* 见描述 */
#define exp2              /* 见描述 */
#define exp2m1            /* 见描述 */
#define expm1             /* 见描述 */
#define fabs              /* 见描述 */
#define fadd              /* 见描述 */
#define fdim              /* 见描述 */
#define fdiv              /* 见描述 */
#define ffma              /* 见描述 */
#define floor             /* 见描述 */
#define fma               /* 见描述 */
#define fmax              /* 见描述 */
#define fmaximum          /* 见描述 */
#define fmaximum_mag      /* 见描述 */
#define fmaximum_mag_num  /* 见描述 */
#define fmaximum_num      /* 见描述 */
#define fmin              /* 见描述 */
#define fminimum          /* 见描述 */
#define fminimum_mag      /* 见描述 */
#define fminimum_mag_num  /* 见描述 */
#define fminimum_num      /* 见描述 */
#define fmod              /* 见描述 */
#define fmul              /* 见描述 */
#define frexp             /* 见描述 */
#define fromfp            /* 见描述 */
#define fromfpx           /* 见描述 */
#define fsqrt             /* 见描述 */
#define fsub              /* 见描述 */
#define hypot             /* 见描述 */
#define ilogb             /* 见描述 */
#define ldexp             /* 见描述 */
#define lgamma            /* 见描述 */
#define llogb             /* 见描述 */
#define llrint            /* 见描述 */
#define llround           /* 见描述 */
#define log               /* 见描述 */
#define log10             /* 见描述 */
#define log10p1           /* 见描述 */
#define log1p             /* 见描述 */
#define log2              /* 见描述 */
#define log2p1            /* 见描述 */
#define logb              /* 见描述 */
#define logp1             /* 见描述 */
#define lrint             /* 见描述 */
#define lround            /* 见描述 */
#define nearbyint         /* 见描述 */
#define nextafter         /* 见描述 */
#define nextdown          /* 见描述 */
#define nexttoward        /* 见描述 */
#define nextup            /* 见描述 */
#define pow               /* 见描述 */
#define pown              /* 见描述 */
#define powr              /* 见描述 */
#define remainder         /* 见描述 */
#define remquo            /* 见描述 */
#define rint              /* 见描述 */
#define rootn             /* 见描述 */
#define round             /* 见描述 */
#define roundeven         /* 见描述 */
#define rsqrt             /* 见描述 */
#define scalbln           /* 见描述 */
#define scalbn            /* 见描述 */
#define sin               /* 见描述 */
#define sinh              /* 见描述 */
#define sinpi             /* 见描述 */
#define sqrt              /* 见描述 */
#define tan               /* 见描述 */
#define tanh              /* 见描述 */
#define tanpi             /* 见描述 */
#define tgamma            /* 见描述 */
#define trunc             /* 见描述 */
#define ufromfp           /* 见描述 */
#define ufromfpx          /* 见描述 */
```

​	仅当实现定义了 `__STDC_NO_COMPLEX__`：

```c
#ifndef __STDC_WANT_LIB_EXT1__
#define carg  /* 见描述 */
#define cimag /* 见描述 */
#define conj  /* 见描述 */
#define cproj /* 见描述 */
#define creal /* 见描述 */
#endif
```

​	仅当实现定义了 `__STDC_IEC_60559_DFP__`：

```c
#define d32add      /* 见描述 */
#define d32div      /* 见描述 */
#define d32fma      /* 见描述 */
#define d32mul      /* 见描述 */
#define d32sqrt     /* 见描述 */
#define d32sub      /* 见描述 */
#define d64add      /* 见描述 */
#define d64div      /* 见描述 */
#define d64fma      /* 见描述 */
#define d64mul      /* 见描述 */
#define d64sqrt     /* 见描述 */
#define d64sub      /* 见描述 */
#define llquantexp  /* 见描述 */
#define quantize    /* 见描述 */
#define quantum     /* 见描述 */
#define samequantum /* 见描述 */
```

​	仅当实现定义了 `__STDC_IEC_60559_TYPES__`，并且用户代码在对 `<tgmath.h>` 的任何包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：

```c
#ifdef __STDC_WANT_IEC_60559_TYPES_EXT__
#define /*dMadd*/   /* 见描述 */
#define /*dMdiv*/   /* 见描述 */
#define /*dMfma*/   /* 见描述 */
#define /*dMmul*/   /* 见描述 */
#define /*dMsqrt*/  /* 见描述 */
#define /*dMsub*/   /* 见描述 */
#define /*dMxadd*/  /* 见描述 */
#define /*dMxdiv*/  /* 见描述 */
#define /*dMxfma*/  /* 见描述 */
#define /*dMxmul*/  /* 见描述 */
#define /*dMxsqrt*/ /* 见描述 */
#define /*dMxsub*/  /* 见描述 */
#define /*fMadd*/   /* 见描述 */
#define /*fMdiv*/   /* 见描述 */
#define /*fMfma*/   /* 见描述 */
#define /*fMmul*/   /* 见描述 */
#define /*fMsqrt*/  /* 见描述 */
#define /*fMsub*/   /* 见描述 */
#define /*fMxadd*/  /* 见描述 */
#define /*fMxdiv*/  /* 见描述 */
#define /*fMxfma*/  /* 见描述 */
#define /*fMxmul*/  /* 见描述 */
#define /*fMxsqrt*/ /* 见描述 */
#define /*fMxsub*/  /* 见描述 */
```