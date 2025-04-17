+++
title = "常用数学函数"
date = 2025-04-15T18:51:00+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文[https://zh.cppreference.com/w/c/numeric/math](https://zh.cppreference.com/w/c/numeric/math)

## 类型

| 在标头 `<stdlib.h>` 定义                                   |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [div_t<br />](https://zh.cppreference.com/w/c/numeric/math/div) | [div](https://zh.cppreference.com/w/c/numeric/math/div) 函数返回的结构体类型 (typedef) |
| [ldiv_t<br />](https://zh.cppreference.com/w/c/numeric/math/div) | [ldiv](https://zh.cppreference.com/w/c/numeric/math/div) 函数返回的结构体类型 (typedef) |
| [lldiv_t (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/div) | lldiv 函数返回的结构体类型 (typedef)                         |
| 在标头 `<inttypes.h>` 定义                                 |                                                              |
| [imaxdiv_t (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/div) | imaxdiv 函数返回的结构体类型 (typedef)                       |
| 在标头 `<math.h>` 定义                                     |                                                              |
| [float_t (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/float_t) | 宽度至少等于 float 的最高效浮点数类型 (typedef)              |
| [double_t (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/float_t) | 宽度至少等于 double 的最高效浮点类型 (typedef)               |

## 常量

| 在标头 `<math.h>` 定义                                     |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [HUGE_VALF (C99)<br />HUGE_VAL (C99)<br />HUGE_VALL <br />](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL) | 分别指示过大而无法以 float、double 和 long double 表示的值（无穷大） (宏常量) |
| [INFINITY (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/INFINITY) | 求值为正无穷大或保证溢出 float 的值 (宏常量)                 |
| [NAN (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/NAN) | 求值为 float 类型的安静 NaN (宏常量)                         |
| [FP_FAST_FMAF (C99)<br />FP_FAST_FMA (C99)<br />FP_FAST_FMAL (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fma) | 指示 fma 函数与操作数的一次乘法和一次加法相比，执行速度相当或更快 (宏常量) |
| [FP_ILOGB0 (C99)<br />FP_ILOGBNAN (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ilogb) | 分别求值为当 x 为 0 或 NaN 时的 [ilogb](http://zh.cppreference.com/w/c/numeric/math/ilogb)(x) (宏常量) |
| [math_errhandling (C99)<br />MATH_ERRNO (C99)<br />MATH_ERREXCEPT (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) | 定义用于常用数学函数的错误处理机制 (宏常量)                  |
|                                                              |                                                              |

### 分类

| [FP_NORMAL (C99)<br />FP_SUBNORMAL (C99)<br />FP_ZERO (C99)<br />FP_INFINITE (C99)<br />FP_NAN (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/FP_categories) | 指示浮点数类别 (宏常量) |
| ------------------------------------------------------------ | ----------------------- |
|                                                              |                         |

## 函数

| 在标头 `<stdlib.h>` 定义                                     |                                       |
| ------------------------------------------------------------ | ------------------------------------- |
| [abs <br />labs <br />llabs (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/abs) | 计算整数的绝对值（\|x\|\|�\|） (函数) |
| [div <br />ldiv <br />lldiv (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/div) | 计算整数除法的商和余数 (函数)         |
| 在标头 `<inttypes.h>` 定义                                   |                                       |
| [imaxabs (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/abs) | 计算整数的绝对值（\|x\|\|�\|） (函数) |
| [imaxdiv (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/div) | 计算整数除法的商和余数 (函数)         |
| 在标头 `<math.h>` 定义                                       |                                       |

### 基本运算

| [fabs <br />fabsf (C99)<br />fabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fabs) | 计算浮点数的绝对值（\|x\|\|�\|） (函数)                 |
| ------------------------------------------------------------ | ------------------------------------------------------- |
| [fmod <br />fmodf (C99)<br />fmodl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmod) | 计算浮点数除法运算的余数 (函数)                         |
| [remainder (C99)<br />remainderf (C99)<br />remainderl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remainder) | 计算浮点数除法运算的带符号余数 (函数)                   |
| [remquo (C99)<br />remquof (C99)<br />remquol (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remquo) | 计算除法运算的带符号余数，以及商的后三位 (函数)         |
| [fma (C99)<br />fmaf (C99)<br />fmal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fma) | 计算结合的乘加运算 (函数)                               |
| [fmax (C99)<br />fmaxf (C99)<br />fmaxl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmax) | 确定两个浮点数的较大者 (函数)                           |
| [fmin (C99)<br />fminf (C99)<br />fminl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmin) | 确定两个浮点数的较小者 (函数)                           |
| [fdim (C99)<br />fdimf (C99)<br />fdiml (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fdim) | 确定两个浮点数的非负数差（max(0,x−y)max(0,�−�)） (函数) |
| [nan (C99)<br />nanf (C99)<br />nanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/nan) | 返回 NaN（非数） (函数)                                 |

### 指数函数

| [exp <br />expf (C99)<br />expl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp) | 计算 *e* 的给定次幂（ex��） (函数)                           |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [exp2 (C99)<br />exp2f (C99)<br />exp2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp2) | 计算 *2* 的给定次幂（2x2�） (函数)                           |
| [expm1 (C99)<br />expm1f (C99)<br />expm1l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/expm1) | 计算 *e* 的给定次幂减一（ex−1��−1） (函数)                   |
| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡�） (函数)                    |
| [log10 <br />log10f (C99)<br />log10l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log10) | 计算常用对数 （底为 *10*）（log10xlog10⁡�） (函数)            |
| [log2 (C99)<br />log2f (C99)<br />log2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log2) | 计算底为 *2* 的对数（log2xlog2⁡�） (函数)                     |
| [log1p (C99)<br />log1pf (C99)<br />log1pl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log1p) | 计算给定数加 1 的自然对数（底为 *e*）（ln(1+x)ln⁡(1+�)） (函数) |

### 幂函数

| [pow <br />powf (C99)<br />powl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/pow) | 计算一个数的给定次幂（xy��） (函数)                |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [sqrt <br />sqrtf (C99)<br />sqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sqrt) | 计算平方根（√x�） (函数)                           |
| [cbrt (C99)<br />cbrtf (C99)<br />cbrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cbrt) | 计算立方根（3√x�3） (函数)                         |
| [hypot (C99)<br />hypotf (C99)<br />hypotl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/hypot) | 计算两个给定数平方和的平方根（√x2+y2�2+�2） (函数) |

### 三角函数

| [sin <br />sinf (C99)<br />sinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sin) | 计算正弦（sinxsin⁡�） (函数)         |
| ------------------------------------------------------------ | ----------------------------------- |
| [cos <br />cosf (C99)<br />cosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cos) | 计算余弦（cosxcos⁡�） (函数)         |
| [tan <br />tanf (C99)<br />tanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tan) | 计算正切（tanxtan⁡�） (函数)         |
| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡�） (函数) |
| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡�） (函数) |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡�） (函数) |
| [atan2 <br />atan2f (C99)<br />atan2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan2) | 计算反正切，以符号确定象限 (函数)   |

### 双曲函数

| [sinh <br />sinhf (C99)<br />sinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sinh) | 计算双曲正弦（sinhxsinh⁡�） (函数)       |
| ------------------------------------------------------------ | --------------------------------------- |
| [cosh <br />coshf (C99)<br />coshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cosh) | 计算双曲余弦（coshxcosh⁡�） (函数)       |
| [tanh <br />tanhf (C99)<br />tanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tanh) | 计算双曲正切（tanhxtanh⁡�） (函数)       |
| [asinh (C99)<br />asinhf (C99)<br />asinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asinh) | 计算反双曲正弦（arsinhxarsinh⁡�） (函数) |
| [acosh (C99)<br />acoshf (C99)<br />acoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acosh) | 计算反双曲余弦（arcoshxarcosh⁡�） (函数) |
| [atanh (C99)<br />atanhf (C99)<br />atanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atanh) | 计算反双曲正切（artanhxartanh⁡�） (函数) |

### 误差及伽马函数

| [erf (C99)<br />erff (C99)<br />erfl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/erf) | 计算误差函数 (函数)                       |
| ------------------------------------------------------------ | ----------------------------------------- |
| [erfc (C99)<br />erfcf (C99)<br />erfcl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/erfc) | 计算补误差函数 (函数)                     |
| [tgamma (C99)<br />tgammaf (C99)<br />tgammal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tgamma) | 计算伽马函数 (函数)                       |
| [lgamma (C99)<br />lgammaf (C99)<br />lgammal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/lgamma) | 计算伽马函数的自然对数（底为 *e*） (函数) |

### 临近整数的浮点运算

| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)                         |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)                         |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数)               |
| [round (C99)<br />roundf (C99)<br />roundl (C99)<br />lround (C99)<br />lroundf (C99)<br />lroundl (C99)<br />llround (C99)<br />llroundf (C99)<br />llroundl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/round) | 取整到最接近的整数，在相邻整数正中间时取远离零的数 (函数) |
| [nearbyint (C99)<br />nearbyintf (C99)<br />nearbyintl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/nearbyint) | 用当前舍入模式取整到整数 (函数)                           |
| [rint (C99)<br />rintf (C99)<br />rintl (C99)<br />lrint (C99)<br />lrintf (C99)<br />lrintl (C99)<br />llrint (C99)<br />llrintf (C99)<br />llrintl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/rint) | 使用当前舍入模式取整到整数，若结果有误则产生异常 (函数)   |

### 浮点数操作函数

| [frexp <br />frexpf (C99)<br />frexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/frexp) | 将数拆分成有效数字和 *2* 的幂次 (函数)                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ldexp <br />ldexpf (C99)<br />ldexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ldexp) | 将数乘以 *2* 的幂 (函数)                                     |
| [modf <br />modff (C99)<br />modfl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/modf) | 把一个数拆分成整数和小数部分 (函数)                          |
| [scalbn (C99)<br />scalbnf (C99)<br />scalbnl (C99)<br />scalbln (C99)<br />scalblnf (C99)<br />scalblnl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/scalbn) | 高效计算一个数乘 [FLT_RADIX]({{< ref "/c/types/limits" >}}) 的幂 (函数) |
| [ilogb (C99)<br />ilogbf (C99)<br />ilogbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ilogb) | 提取给定数的指数（结果为整数） (函数)                        |
| [logb (C99)<br />logbf (C99)<br />logbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/logb) | 提取给定数的指数（结果为浮点数） (函数)                      |
| [nextafter (C99)<br />nextafterf (C99)<br />nextafterl (C99)<br />nexttoward (C99)<br />nexttowardf (C99)<br />nexttowardl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/nextafter) | 确定到给定值方向的下一个可表示的浮点数 (函数)                |
| [copysign (C99)<br />copysignf (C99)<br />copysignl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/copysign) | 从一个给定值的绝对值和另一个给定值的符号产生值 (函数)        |

### 分类及比较

| [fpclassify (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fpclassify) | 对给定的浮点数分类 (宏函数)                       |
| ------------------------------------------------------------ | ------------------------------------------------- |
| [isfinite (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isfinite) | 检查给定数是否具有有限值 (宏函数)                 |
| [isinf (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isinf) | 检查给定数是否是无穷大 (宏函数)                   |
| [isnan (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isnan) | 检查给定数是否为 NaN (宏函数)                     |
| [isnormal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isnormal) | 检查给定数是否正规 (宏函数)                       |
| [signbit (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/signbit) | 检查给定数是不是负数 (宏函数)                     |
| [isgreater (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isgreater) | 检查第一个浮点数实参是否大于第二个 (宏函数)       |
| [isgreaterequal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isgreaterequal) | 检查第一个浮点数实参是否大于等于第二个 (宏函数)   |
| [isless (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isless) | 检查第一个浮点数实参是否小于第二个 (宏函数)       |
| [islessequal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/islessequal) | 检查第一个浮点数实参是否小于或等于第二个 (宏函数) |
| [islessgreater (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/islessgreater) | 检查第一个浮点数实参是否小于或大于第二个 (宏函数) |
| [isunordered (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isunordered) | 检查两个浮点数是否无序 (宏函数)                   |

## 参阅

​	**常用数学函数**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math)**

