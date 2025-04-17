+++
title = "<math.h>"
date = 2025-04-17T12:11:06+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false
math = true

+++

## 类型

### double_t

原址：[https://zh.cppreference.com/w/c/numeric/math/float_t](https://zh.cppreference.com/w/c/numeric/math/float_t)

```c
typedef /* 由实现定义 */ float_t // (C99 起)
typedef /* 由实现定义 */ double_t // (C99 起)
```

​	float_t 和 double_t 类型分别是至少与 float 和 double 一样宽的浮点数类型，并满足 double_t 至少与 float_t 一样宽。[FLT_EVAL_METHOD](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD) 的值确定 float_t 和 double_t 的类型。

| `FLT_EVAL_METHOD` | 解释                                           |
| ----------------- | ---------------------------------------------- |
| 0                 | float_t 和 double_t 分别等价于 float 和 double |
| 1                 | float_t 和 double_t 都等价于 double            |
| 2                 | float_t 和 double_t 都等价于 long double       |
| 其他              | float_t 和 double_t 均为实现定义               |

**示例**



```c
#include <float.h>
#include <math.h>
#include <stdio.h>
 
#define SHOW(expr) printf("%s = %d\n", #expr, (int)(expr))
 
int main(void)
{
    SHOW(FLT_EVAL_METHOD);
    SHOW(sizeof(float));
    SHOW(sizeof(float_t));
    SHOW(sizeof(double));
    SHOW(sizeof(double_t));
}
```

​	可能的输出：

```txt
FLT_EVAL_METHOD = 1
sizeof(float) = 4
sizeof(float_t) = 8
sizeof(double) = 8
sizeof(double_t) = 8
```


### float_t

原址：[https://zh.cppreference.com/w/c/numeric/math/float_t](https://zh.cppreference.com/w/c/numeric/math/float_t)

```c
typedef /* 由实现定义 */ float_t // (C99 起)
typedef /* 由实现定义 */ double_t // (C99 起)
```

参见：[double_t](#double_t)


## 宏

### FP_FAST_FMA

原址：

```c
```




### FP_FAST_FMAF

原址：

```c
```




### FP_FAST_FMAL

原址：

```c
```




### FP_ILOGB0

原址：

```c
```




### FP_ILOGBNAN

原址：

```c
```




### FP_INFINITE

原址：

```c
```




### FP_NAN

原址：

```c
```




### FP_NORMAL

原址：

```c
```




### FP_SUBNORMAL

原址：

```c
```




### FP_ZERO

原址：

```c
```




### HUGE_VAL

原址：[https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)

```c
#define HUGE_VALF /* 由实现定义 */ // (C99 起)
#define HUGE_VAL  /* 由实现定义 */
#define HUGE_VALL /* 由实现定义 */ // (C99 起)
```

​	`HUGE_VALF`、`HUGE_VAL` 和 `HUGE_VALL` 宏展开成正浮点数常量表达式，它们比较等于上溢情况中浮点数函数和运算符的返回值（见 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling)）。

| 常量        | 解释                                                         |
| ----------- | ------------------------------------------------------------ |
| `HUGE_VALF` | 展开成指示上溢的正 float 表达式                              |
| `HUGE_VAL`  | 展开成指示上溢的正 double 表达式，不必可表示为 float         |
| `HUGE_VALL` | 展开成指示上溢的正 long double 表达式，不必可表示为 float 或 double |

​	在支持浮点数无穷大的平台上，这些宏始终分别展开成 float、double 和 long double 的正无穷大。

**示例**



```c
#include <math.h>
#include <stdio.h>
int main(void)
{
    const double result = 1.0/0.0;
    printf("1.0/0.0 == %f\n", result);
    if (result == HUGE_VAL)
        puts("1.0/0.0 == HUGE_VAL");
}
```

​	可能的输出：

```txt
1.0/0.0 == inf
1.0/0.0 == HUGE_VAL
```


### HUGE_VALF

原址：[https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)

```c
#define HUGE_VALF /* 由实现定义 */ // (C99 起)
#define HUGE_VAL  /* 由实现定义 */
#define HUGE_VALL /* 由实现定义 */ // (C99 起)
```

​	参见：[HUGE_VAL](#huge_val)


### HUGE_VALL

原址：[https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)

```c
#define HUGE_VALF /* 由实现定义 */ // (C99 起)
#define HUGE_VAL  /* 由实现定义 */
#define HUGE_VALL /* 由实现定义 */ // (C99 起)
```

​	参见：[HUGE_VAL](#huge_val)


### INFINITY

原址：[https://zh.cppreference.com/w/c/numeric/math/INFINITY](https://zh.cppreference.com/w/c/numeric/math/INFINITY)

```c
#define INFINITY /* 由实现定义 */ // (C99 起)
```

​	若实现支持浮点数无穷大，则宏 `INFINITY` 展开成求值为正或无符号无穷大的 float 类型常量表达式。

​	若实现不支持浮点数无穷大，则宏 `INFINITY` 展开成保证在编译时上溢 float 的正值，而此宏的使用生成编译器警告。

​	用于打印无穷大的风格是实现定义的。

**示例**

​	显示用于打印无穷大的风格及其 IEEE 格式。



```c
#include <stdio.h>
#include <math.h>
#include <stdint.h>
#include <inttypes.h>
#include <string.h>
 
int main(void)
{
    double f = INFINITY;
    uint64_t fn; memcpy(&fn, &f, sizeof f);
    printf("INFINITY:   %f %" PRIx64 "\n", f, fn);
}
```

​	可能的输出：

```txt
INFINITY:   inf 7ff0000000000000
```


### MATH_ERREXCEPT

原址：

```c
```




### MATH_ERRNO

原址：

```c
```




### NAN

原址：[https://zh.cppreference.com/w/c/numeric/math/NAN](https://zh.cppreference.com/w/c/numeric/math/NAN)

```c
#define NAN /* 由实现定义 */ // (C99 起)
```

​	宏 `NAN` 展开成求值为安静非数（QNaN）的 float 类型常量表达式。若实现不支持 QNaN，则不定义此宏。

​	用于打印 NaN 的风格是实现定义的。

**注意**

​	有许多不同的 NaN 值，区别于其载荷与其符号位。宏 `NAN` 所生成的 NaN 的载荷与符号位的内容是实现定义的。

**示例**

​	显示用于打印 NaN 的风格和 IEEE 格式。



```c
#include <inttypes.h>
#include <math.h>
#include <stdint.h>
#include <stdio.h>
#include <string.h>
 
int main(void)
{
    const double f = NAN;
    uint64_t fn;
    memcpy(&fn, &f, sizeof f);
    printf("NAN:   %f %" PRIx64 "\n", f, fn);
}
```

​	可能的输出：

```txt
NAN:   nan 7ff8000000000000
```


### math_errhandling

原址：

```c
```




## 函数
### acos

原址：

```c
```




### acosf

原址：

```c
```




### acosh

原址：

```c
```




### acoshf

原址：

```c
```




### acoshl

原址：

```c
```




### acosl

原址：

```c
```




### asin

原址：

```c
```




### asinf

原址：

```c
```




### asinh

原址：

```c
```




### asinhf

原址：

```c
```




### asinhl

原址：

```c
```




### asinl

原址：

```c
```




### atan

原址：

```c
```




### atan2

原址：

```c
```




### atan2f

原址：

```c
```




### atan2l

原址：

```c
```




### atanf

原址：

```c
```




### atanh

原址：

```c
```




### atanhf

原址：

```c
```




### atanhl

原址：

```c
```




### atanl

原址：

```c
```




### cbrt

原址：

```c
```




### cbrtf

原址：

```c
```




### cbrtl

原址：

```c
```




### ceil

原址：

```c
```




### ceilf

原址：

```c
```




### ceill

原址：

```c
```




### copysign

原址：

```c
```




### copysignf

原址：

```c
```




### copysignl

原址：

```c
```




### cos

原址：

```c
```




### cosf

原址：

```c
```




### cosh

原址：

```c
```




### coshf

原址：

```c
```




### coshl

原址：

```c
```




### cosl

原址：

```c
```




### erf

原址：

```c
```




### erfc

原址：

```c
```




### erfcf

原址：

```c
```




### erfcl

原址：

```c
```




### erff

原址：

```c
```




### erfl

原址：

```c
```




### exp

原址：

```c
```




### exp2

原址：

```c
```




### exp2f

原址：

```c
```




### exp2l

原址：

```c
```




### expf

原址：

```c
```




### expl

原址：

```c
```




### expm1

原址：

```c
```




### expm1f

原址：

```c
```




### expm1l

原址：

```c
```




### fabs

原址：

```c
```




### fabsf

原址：

```c
```




### fabsl

原址：

```c
```




### fdim

原址：

```c
```




### fdimf

原址：

```c
```




### fdiml

原址：

```c
```




### floor

原址：

```c
```




### floorf

原址：

```c
```




### floorl

原址：

```c
```




### fma

原址：[https://zh.cppreference.com/w/c/numeric/math/fma](https://zh.cppreference.com/w/c/numeric/math/fma)

```c
float       fmaf( float x, float y, float z ); // (1)	(C99 起)
double      fma( double x, double y, double z ); // (2)	(C99 起)
long double fmal( long double x, long double y, long double z ); // (3)	(C99 起)
#define FP_FAST_FMA  /* 由实现定义 */ // (4)	(C99 起)
#define FP_FAST_FMAF /* 由实现定义  */ // (5)	(C99 起)
#define FP_FAST_FMAL /* 由实现定义  */ // (6)	(C99 起)
// 在标头 <tgmath.h> 定义
#define fma( x, y, z ) // (7)	(C99 起)
```

1-3）计算 `(x * y) + z`，如同用无限精度，而仅舍入一次到结果类型。

4-6） 若定义宏常量 `FP_FAST_FMA`、`FP_FAST_FMAF` 或 `FP_FAST_FMAL`，则对应函数 `fma`、`fmaf` 或 `fmal` 分别求值快于（并且精度高于）double、float 和 long double 实参的表达式 `x * y + z`。若定义，则这些宏求值为整数 1。

7）泛型宏：若任何实参拥有 long double 类型，则调用 `fmal`。否则若任何实参拥有整数类型或 double 类型，则调用 `fma`。否则调用`fmaf`。

**参数**

| x, y, z | -    | 浮点数 |
| ------- | ---- | ------ |

**返回值**

​	若成功，则返回 `(x * y) + z` 的值，如同计算为无限精度再舍入一次以适合目标类型（或者说是作为单次三元浮点数运算计算）。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若`x`为零而`y`为无穷大或`x`为无穷大而`y`为零，且
  - 若 `z` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
  - 若 `z` 为 NaN，则返回 NaN 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `x * y` 为准确的无穷大且 z 为带相反符号的无穷大，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `x` 或 `y` 为 NaN，则返回 NaN。
- 若 z 为 NaN，且 `x * y` 不是 `0 * Inf` 或 `Inf * 0`，则返回 NaN（而无 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）。

**注解**

​	此运算经常在硬件中实现为[融合乘加](https://en.wikipedia.org/wiki/Multiply–accumulate_operation) CPU 指令。若硬件支持，则期待定义相应的 `FP_FAST_FMA*` 宏，但多数实现即使在不定义这些宏时也利用该 CPU 指令。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fma.html) `x * y` 非法且 z 为 NaN 的情形是定义域错误。

​	由于其无限的中间精度，`fma` 是其他正确舍入数学运算，如 [sqrt](https://zh.cppreference.com/w/c/numeric/math/sqrt) 或甚至除法（在 CPU 不支持的平台上，例如 [Itanium](https://en.wikipedia.org/wiki/Itanium)）的常用构建块。

​	同所有浮点数表达式，表达式 `(x*y) + z` 可编译为融合乘加，除非 [#pragma](https://zh.cppreference.com/w/cpp/preprocessor/impl) `STDC FP_CONTRACT` 为关闭。

**示例**



```c
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    // 演示 fma 和内建运算符间的区别
    double in = 0.1;
    printf("0.1 double is %.23f (%a)\n", in, in);
    printf("0.1*10 is 1.0000000000000000555112 (0x8.0000000000002p-3),"
           " or 1.0 if rounded to double\n");
    double expr_result = 0.1 * 10 - 1;
    printf("0.1 * 10 - 1 = %g : 1 subtracted after "
           "intermediate rounding to 1.0\n", expr_result);
    double fma_result = fma(0.1, 10, -1);
    printf("fma(0.1, 10, -1) = %g (%a)\n", fma_result, fma_result);
 
    // fma 用于 double-double
    printf("\nin double-double arithmetic, 0.1 * 10 is representable as ");
    double high = 0.1 * 10;
    double low = fma(0.1, 10, -high);
    printf("%g + %g\n\n", high, low);
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("fma(+Inf, 10, -Inf) = %f\n", fma(INFINITY, 10, -INFINITY));
    if(fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
0.1 double is 0.10000000000000000555112 (0x1.999999999999ap-4)
0.1*10 is 1.0000000000000000555112 (0x8.0000000000002p-3), or 1.0 if rounded to double
0.1 * 10 - 1 = 0 : 1 subtracted after intermediate rounding to 1.0
fma(0.1, 10, -1) = 5.55112e-17 (0x1p-54)
 
in double-double arithmetic, 0.1 * 10 is representable as 1 + 5.55112e-17
 
fma(+Inf, 10, -Inf) = -nan
    FE_INVALID raised
```


### fmaf

原址：[https://zh.cppreference.com/w/c/numeric/math/fma](https://zh.cppreference.com/w/c/numeric/math/fma)

```c
float       fmaf( float x, float y, float z ); // (1)	(C99 起)
double      fma( double x, double y, double z ); // (2)	(C99 起)
long double fmal( long double x, long double y, long double z ); // (3)	(C99 起)
#define FP_FAST_FMA  /* 由实现定义 */ // (4)	(C99 起)
#define FP_FAST_FMAF /* 由实现定义  */ // (5)	(C99 起)
#define FP_FAST_FMAL /* 由实现定义  */ // (6)	(C99 起)
// 在标头 <tgmath.h> 定义
#define fma( x, y, z ) // (7)	(C99 起)
```

​	参见：[fma](#fma)


### fmal

原址：[https://zh.cppreference.com/w/c/numeric/math/fma](https://zh.cppreference.com/w/c/numeric/math/fma)

```c
float       fmaf( float x, float y, float z ); // (1)	(C99 起)
double      fma( double x, double y, double z ); // (2)	(C99 起)
long double fmal( long double x, long double y, long double z ); // (3)	(C99 起)
#define FP_FAST_FMA  /* 由实现定义 */ // (4)	(C99 起)
#define FP_FAST_FMAF /* 由实现定义  */ // (5)	(C99 起)
#define FP_FAST_FMAL /* 由实现定义  */ // (6)	(C99 起)
// 在标头 <tgmath.h> 定义
#define fma( x, y, z ) // (7)	(C99 起)
```

​	参见：[fma](#fma)


### fmax

原址：

```c
```




### fmaxf

原址：

```c
```




### fmaxl

原址：

```c
```




### fmin

原址：

```c
```




### fminf

原址：

```c
```




### fminl

原址：

```c
```




### fmod

原址：

```c
```




### fmodf

原址：

```c
```




### fmodl

原址：

```c
```




### fpclassify

原址：

```c
```




### frexp

原址：

```c
```




### frexpf

原址：

```c
```




### frexpl

原址：

```c
```




### hypot

原址：

```c
```




### hypotf

原址：

```c
```




### hypotl

原址：

```c
```




### ilogb

原址：[https://zh.cppreference.com/w/c/numeric/math/ilogb](https://zh.cppreference.com/w/c/numeric/math/ilogb)

```c
int ilogbf( float arg ); // (1)	(C99 起)
int ilogb( double arg ); // (2)	(C99 起)
int ilogbl( long double arg ); // (3)	(C99 起)
// 在标头 <tgmath.h> 定义
#define ilogb( arg ) // (4)	(C99 起)
// 在标头 <math.h> 定义
#define FP_ILOGB0    /* 由实现定义 */ // (5)	(C99 起)
#define FP_ILOGBNAN  /* 由实现定义 */ // (6)	(C99 起)
```

1-3） 从浮点数实参 arg 提取独立于基底的无偏指数，并将它作为有符号整数返回。

4）泛型宏：若 arg 拥有 long double 类型，则调用 `ilogbl`。否则，若 arg 拥有整数类型或 double 类型，则调用 `ilogb`。否则调用 `ilogbf`。

5）展开成整数常量表达式，值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 或 -[INT_MAX](http://zh.cppreference.com/w/c/types/limits)。

6）展开成整数常量表达式，值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 或 +[INT_MAX](http://zh.cppreference.com/w/c/types/limits)。

​	正式而言，无偏指数是非零 arg 的 \\(log_r^{|arg|}\\) 的整数部分，作为有符号整数，其中 `r` 是 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits)。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |

**返回值**

​	若不出现错误，则返回作为 int 值的 arg 的无偏指数。

​	若 arg 为零，则返回 FP_ILOGB0。

​	若 arg 为无穷大，则返回 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)。

​	若 arg 为 NaN，则返回 FP_ILOGBNAN。

​	若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)，则返回值未指定，且可能出现定义域或值域错误。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 arg 为零、无穷大或 NaN ，则可能出现定义域错误或值域错误。

​	若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) ，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 arg 为 ±0、 ±∞ 或 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 所有其他情况下，结果是准确的（决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）并且忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**注解**

​	若 arg 不是零、无穷大或 NaN，则返回的值准确等价于 (int)[logb](http://zh.cppreference.com/w/c/numeric/math/logb)(arg)。

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/ilogb.html)若 arg 为零、无穷大、NaN 或若正确结果在 int 的范围外则出现定义域错误。

​	POSIX 亦要求在 XSI 一致的系统上，正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 时返回值为 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)，而正确结果小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 时返回值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)。

​	在所有已知平台上正确结果都能表示成 int。对于要出现溢出的情况，[INT_MAX](https://zh.cppreference.com/w/c/types/limits) 必须小于 [LDBL_MAX_EXP](http://zh.cppreference.com/w/c/types/limits) * log2([FLT_RADIX](http://zh.cppreference.com/w/c/types/limits)) 或 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 必须大于 [LDBL_MIN_EXP](http://zh.cppreference.com/w/c/types/limits) - [LDBL_MANT_DIG](http://zh.cppreference.com/w/c/types/limits)) * log2([FLT_RADIX](http://zh.cppreference.com/w/c/types/limits))。

​	`ilogb` 所返回的指数值始终比 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 所返回的小 1，因为不同的正规化要求：对于 `ilogb` 返回的指数 `e`，\\(| arg * r^{-e}|\\) 在 1 与 `r` 之间（典型地在 1 与 2 之间），但 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 返回的指数 `e`，\\(| arg * 2^{-e}|\\) 在 0.5 与 1 之间。

**示例**



```c
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    double f = 123.45;
    printf("给定数值 %.2f 十六进制为 %a，\n", f, f);
 
    double f3;
    double f2 = modf(f, &f3);
    printf("modf() 计算 %.0f + %.2f\n", f3, f2);
 
    int i;
    f2 = frexp(f, &i);
    printf("frexp() 计算 %f * 2^%d\n", f2, i);
 
    i = ilogb(f);
    printf("logb()/ilogb() 计算 %f * %d^%d\n", f/scalbn(1.0, i), FLT_RADIX, i);
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("ilogb(0) = %d\n", ilogb(0));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
给定数值 123.45 十六进制为 0x1.edccccccccccdp+6，
modf() 计算 123 + 0.45
frexp() 计算 0.964453 * 2^7
logb()/ilogb() 计算 1.92891 * 2^6
ilogb(0) = -2147483648
    FE_INVALID raised
```


### ilogbf

原址：

```c
```




### ilogbl

原址：

```c
```




### isfinite

原址：

```c
```




### isgreater

原址：

```c
```




### isgreaterequal

原址：

```c
```




### isinf

原址：

```c
```




### isless

原址：

```c
```




### islessequal

原址：

```c
```




### islessgreater

原址：

```c
```




### isnan

原址：

```c
```




### isnormal

原址：

```c
```




### isunordered

原址：

```c
```




### ldexp

原址：

```c
```




### ldexpf

原址：

```c
```




### ldexpl

原址：

```c
```




### lgamma

原址：

```c
```




### lgammaf

原址：

```c
```




### lgammal

原址：

```c
```




### llrint

原址：

```c
```




### llrintf

原址：

```c
```




### llrintl

原址：

```c
```




### llround

原址：

```c
```




### llroundf

原址：

```c
```




### llroundl

原址：

```c
```




### log

原址：

```c
```




### log10

原址：

```c
```




### log10f

原址：

```c
```




### log10l

原址：

```c
```




### log1p

原址：

```c
```




### log1pf

原址：

```c
```




### log1pl

原址：

```c
```




### log2

原址：

```c
```




### log2f

原址：

```c
```




### log2l

原址：

```c
```




### logb

原址：

```c
```




### logbf

原址：

```c
```




### logbl

原址：

```c
```




### logf

原址：

```c
```




### logl

原址：

```c
```




### lrint

原址：

```c
```




### lrintf

原址：

```c
```




### lrintl

原址：

```c
```




### lround

原址：

```c
```




### lroundf

原址：

```c
```




### lroundl

原址：

```c
```




### modf

原址：

```c
```




### modff

原址：

```c
```




### modfl

原址：

```c
```




### nan

原址：

```c
```




### nanf

原址：

```c
```




### nanl

原址：

```c
```




### nearbyint

原址：

```c
```




### nearbyintf

原址：

```c
```




### nearbyintl

原址：

```c
```




### nextafter

原址：

```c
```




### nextafterf

原址：

```c
```




### nextafterl

原址：

```c
```




### nexttoward

原址：

```c
```




### nexttowardf

原址：

```c
```




### nexttowardl

原址：

```c
```




### pow

原址：

```c
```




### powf

原址：

```c
```




### powl

原址：

```c
```




### remainder

原址：

```c
```




### remainderf

原址：

```c
```




### remainderl

原址：

```c
```




### remquo

原址：

```c
```




### remquof

原址：

```c
```




### remquol

原址：

```c
```




### rint

原址：

```c
```




### rintf

原址：

```c
```




### rintl

原址：

```c
```




### round

原址：

```c
```




### roundf

原址：

```c
```




### roundl

原址：

```c
```




### scalbln

原址：

```c
```




### scalblnf

原址：

```c
```




### scalblnl

原址：

```c
```




### scalbn

原址：

```c
```




### scalbnf

原址：

```c
```




### scalbnl

原址：

```c
```




### signbit

原址：

```c
```




### sin

原址：

```c
```




### sinf

原址：

```c
```




### sinh

原址：

```c
```




### sinhf

原址：

```c
```




### sinhl

原址：

```c
```




### sinl

原址：

```c
```




### sqrt

原址：

```c
```




### sqrtf

原址：

```c
```




### sqrtl

原址：

```c
```




### tan

原址：

```c
```




### tanf

原址：

```c
```




### tanh

原址：

```c
```




### tanhf

原址：

```c
```




### tanhl

原址：

```c
```




### tanl

原址：

```c
```




### tgamma

原址：

```c
```




### tgammaf

原址：

```c
```




### tgammal

原址：

```c
```




### trunc

原址：

```c
```




### truncf

原址：

```c
```




### truncl

原址：

```c
```



