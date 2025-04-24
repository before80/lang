
+++
title = "<math.h>"
date = 2025-04-24T18:07:42+08:00
weight = 100
type = "docs"
description = "常用数学函数"
isCJKLanguage = true
draft = false

+++

## 类型



### double_t

原址：[https://zh.cppreference.com/w/c/numeric/math/float_t](https://zh.cppreference.com/w/c/numeric/math/float_t)

作用：宽度至少等于 `double` 的最高效浮点类型   (typedef)

备注：
```c
// 在标头 <math.h> 定义
typedef /* 由实现定义 */ float_t// (C99 起)
typedef /* 由实现定义 */ double_t// (C99 起)
```

​	`float_t` 和 `double_t` 类型分别是至少与 `float` 和 `double` 一样宽的浮点数类型，并满足 `double_t` 至少与 `float_t` 一样宽。[FLT_EVAL_METHOD](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD) 的值确定 `float_t` 和 `double_t` 的类型。

| `FLT_EVAL_METHOD` | 解释                                                   |
| ----------------- | ------------------------------------------------------ |
| `0`               | `float_t` 和 `double_t` 分别等价于 `float` 和 `double` |
| `1`               | `float_t` 和 `double_t` 都等价于 `double`              |
| `2`               | `float_t` 和 `double_t` 都等价于 `long double`         |
| 其他              | `float_t` 和 `double_t` 均为实现定义                   |

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12 Mathematics <math.h> （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12 Mathematics <math.h> （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12 Mathematics <math.h> （第 231 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12 Mathematics <math.h> （第 212 页）

**参阅**

| [FLT_EVAL_METHOD (C99)<br />](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD) | 指定所有算术运算以什么精度执行 (宏常量) |
| ------------------------------------------------------------ | --------------------------------------- |
|                                                              |                                         |





### float_t

原址：[https://zh.cppreference.com/w/c/numeric/math/float_t](https://zh.cppreference.com/w/c/numeric/math/float_t)

作用：宽度至少等于 `float` 的最高效浮点数类型  (typedef)

备注：
```c
// 在标头 <math.h> 定义
typedef /* 由实现定义 */ float_t// (C99 起)
typedef /* 由实现定义 */ double_t// (C99 起)
```

​	`float_t` 和 `double_t` 类型分别是至少与 `float` 和 `double` 一样宽的浮点数类型，并满足 `double_t` 至少与 `float_t` 一样宽。[FLT_EVAL_METHOD](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD) 的值确定 `float_t` 和 `double_t` 的类型。

| `FLT_EVAL_METHOD` | 解释                                                   |
| ----------------- | ------------------------------------------------------ |
| `0`               | `float_t` 和 `double_t` 分别等价于 `float` 和 `double` |
| `1`               | `float_t` 和 `double_t` 都等价于 `double`              |
| `2`               | `float_t` 和 `double_t` 都等价于 `long double`         |
| 其他              | `float_t` 和 `double_t` 均为实现定义                   |

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12 Mathematics <math.h> （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12 Mathematics <math.h> （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12 Mathematics <math.h> （第 231 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12 Mathematics <math.h> （第 212 页）

**参阅**

| [FLT_EVAL_METHOD (C99)<br />](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD) | 指定所有算术运算以什么精度执行 (宏常量) |
| ------------------------------------------------------------ | --------------------------------------- |
|                                                              |                                         |






## 枚举




## 宏



### FP_FAST_FMA

原址：[https://zh.cppreference.com/w/c/numeric/math/fma](https://zh.cppreference.com/w/c/numeric/math/fma)

作用：指示 fma 函数与操作数的一次乘法和一次加法相比，执行速度相当或更快   (宏常量)

备注：
```c
// 在标头 <math.h> 定义
float       fmaf( float x, float y, float z );// (1)(C99 起)
double      fma( double x, double y, double z );// (2)(C99 起)
long double fmal( long double x, long double y, long double z );// (3)(C99 起)
#define FP_FAST_FMA  /* 由实现定义 */// (4)(C99 起)
#define FP_FAST_FMAF /* 由实现定义  */// (5)(C99 起)
#define FP_FAST_FMAL /* 由实现定义  */// (6)(C99 起)
// 在标头 <tgmath.h> 定义
#define fma( x, y, z )// (7)(C99 起)
```

1-3) 计算 `(x * y) + z`，如同用无限精度，而仅舍入一次到结果类型。

4-6) 若定义宏常量 `FP_FAST_FMA`、`FP_FAST_FMAF` 或 `FP_FAST_FMAL`，则对应函数 `fma`、`fmaf` 或 `fmal` 分别求值快于（并且精度高于）`double`、`float` 和 `long double` 实参的表达式 `x * y + z`。若定义，则这些宏求值为整数 `1`。

7） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `fmal`。否则若任何实参拥有整数类型或 `double` 类型，则调用 `fma`。否则调用`fmaf`。

**参数**

| x, y, z | -    | 浮点数 |
| ------- | ---- | ------ |
|         |      |        |

**返回值**

​	若成功，则返回 `(x * y) + z` 的值，如同计算为无限精度再舍入一次以适合目标类型（或者说是作为单次三元浮点数运算计算）。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若

   

  `x`

   

  为零而

   

  `y`

   

  为无穷大或

   

  `x`

   

  为无穷大而

   

  `y`

   

  为零，且

  - 若 `z` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
  - 若 `z` 为 NaN，则返回 NaN 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

- 若 `x * y` 为准确的无穷大且 `z` 为带相反符号的无穷大，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

- 若 `x` 或 `y` 为 NaN，则返回 NaN。

- 若 `z` 为 NaN，且 `x * y` 不是 `0 * Inf` 或 `Inf * 0`，则返回 NaN（而无 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）。

**注解**

​	此运算经常在硬件中实现为[融合乘加](https://en.wikipedia.org/wiki/Multiply–accumulate_operation) CPU 指令。若硬件支持，则期待定义相应的 `FP_FAST_FMA*` 宏，但多数实现即使在不定义这些宏时也利用该 CPU 指令。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fma.html) `x * y` 非法且 `z` 为 NaN 的情形是定义域错误。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.13.1 The fma functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.10.1 The fma functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.13.1 The fma functions （第 188-189 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.10.1 The fma functions （第 386 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.13.1 The fma functions （第 258 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.10.1 The fma functions （第 530 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.13.1 The fma functions （第 239 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.10.1 The fma functions （第 466 页）

**参阅**

| [remainder (C99)<br />remainderf (C99)<br />remainderl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remainder) | 计算浮点数除法运算的带符号余数 (函数)           |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [remquo (C99)<br />remquof (C99)<br />remquol (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remquo) | 计算除法运算的带符号余数，以及商的后三位 (函数) |
| **fma** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fma)** |                                                 |





### FP_FAST_FMAF

原址：[https://zh.cppreference.com/w/c/numeric/math/fma](https://zh.cppreference.com/w/c/numeric/math/fma)

作用：指示 fma 函数与操作数的一次乘法和一次加法相比，执行速度相当或更快   (宏常量)

备注：
```c
// 在标头 <math.h> 定义
float       fmaf( float x, float y, float z );// (1)(C99 起)
double      fma( double x, double y, double z );// (2)(C99 起)
long double fmal( long double x, long double y, long double z );// (3)(C99 起)
#define FP_FAST_FMA  /* 由实现定义 */// (4)(C99 起)
#define FP_FAST_FMAF /* 由实现定义  */// (5)(C99 起)
#define FP_FAST_FMAL /* 由实现定义  */// (6)(C99 起)
// 在标头 <tgmath.h> 定义
#define fma( x, y, z )// (7)(C99 起)
```

1-3) 计算 `(x * y) + z`，如同用无限精度，而仅舍入一次到结果类型。

4-6) 若定义宏常量 `FP_FAST_FMA`、`FP_FAST_FMAF` 或 `FP_FAST_FMAL`，则对应函数 `fma`、`fmaf` 或 `fmal` 分别求值快于（并且精度高于）`double`、`float` 和 `long double` 实参的表达式 `x * y + z`。若定义，则这些宏求值为整数 `1`。

7） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `fmal`。否则若任何实参拥有整数类型或 `double` 类型，则调用 `fma`。否则调用`fmaf`。

**参数**

| x, y, z | -    | 浮点数 |
| ------- | ---- | ------ |
|         |      |        |

**返回值**

​	若成功，则返回 `(x * y) + z` 的值，如同计算为无限精度再舍入一次以适合目标类型（或者说是作为单次三元浮点数运算计算）。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若

   

  `x`

   

  为零而

   

  `y`

   

  为无穷大或

   

  `x`

   

  为无穷大而

   

  `y`

   

  为零，且

  - 若 `z` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
  - 若 `z` 为 NaN，则返回 NaN 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

- 若 `x * y` 为准确的无穷大且 `z` 为带相反符号的无穷大，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

- 若 `x` 或 `y` 为 NaN，则返回 NaN。

- 若 `z` 为 NaN，且 `x * y` 不是 `0 * Inf` 或 `Inf * 0`，则返回 NaN（而无 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）。

**注解**

​	此运算经常在硬件中实现为[融合乘加](https://en.wikipedia.org/wiki/Multiply–accumulate_operation) CPU 指令。若硬件支持，则期待定义相应的 `FP_FAST_FMA*` 宏，但多数实现即使在不定义这些宏时也利用该 CPU 指令。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fma.html) `x * y` 非法且 `z` 为 NaN 的情形是定义域错误。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.13.1 The fma functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.10.1 The fma functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.13.1 The fma functions （第 188-189 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.10.1 The fma functions （第 386 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.13.1 The fma functions （第 258 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.10.1 The fma functions （第 530 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.13.1 The fma functions （第 239 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.10.1 The fma functions （第 466 页）

**参阅**

| [remainder (C99)<br />remainderf (C99)<br />remainderl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remainder) | 计算浮点数除法运算的带符号余数 (函数)           |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [remquo (C99)<br />remquof (C99)<br />remquol (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remquo) | 计算除法运算的带符号余数，以及商的后三位 (函数) |
| **fma** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fma)** |                                                 |





### FP_FAST_FMAL

原址：[https://zh.cppreference.com/w/c/numeric/math/fma](https://zh.cppreference.com/w/c/numeric/math/fma)

作用：指示 fma 函数与操作数的一次乘法和一次加法相比，执行速度相当或更快   (宏常量)

备注：
```c
// 在标头 <math.h> 定义
float       fmaf( float x, float y, float z );// (1)(C99 起)
double      fma( double x, double y, double z );// (2)(C99 起)
long double fmal( long double x, long double y, long double z );// (3)(C99 起)
#define FP_FAST_FMA  /* 由实现定义 */// (4)(C99 起)
#define FP_FAST_FMAF /* 由实现定义  */// (5)(C99 起)
#define FP_FAST_FMAL /* 由实现定义  */// (6)(C99 起)
// 在标头 <tgmath.h> 定义
#define fma( x, y, z )// (7)(C99 起)
```

1-3) 计算 `(x * y) + z`，如同用无限精度，而仅舍入一次到结果类型。

4-6) 若定义宏常量 `FP_FAST_FMA`、`FP_FAST_FMAF` 或 `FP_FAST_FMAL`，则对应函数 `fma`、`fmaf` 或 `fmal` 分别求值快于（并且精度高于）`double`、`float` 和 `long double` 实参的表达式 `x * y + z`。若定义，则这些宏求值为整数 `1`。

7） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `fmal`。否则若任何实参拥有整数类型或 `double` 类型，则调用 `fma`。否则调用`fmaf`。

**参数**

| x, y, z | -    | 浮点数 |
| ------- | ---- | ------ |
|         |      |        |

**返回值**

​	若成功，则返回 `(x * y) + z` 的值，如同计算为无限精度再舍入一次以适合目标类型（或者说是作为单次三元浮点数运算计算）。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若

   

  `x`

   

  为零而

   

  `y`

   

  为无穷大或

   

  `x`

   

  为无穷大而

   

  `y`

   

  为零，且

  - 若 `z` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
  - 若 `z` 为 NaN，则返回 NaN 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

- 若 `x * y` 为准确的无穷大且 `z` 为带相反符号的无穷大，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

- 若 `x` 或 `y` 为 NaN，则返回 NaN。

- 若 `z` 为 NaN，且 `x * y` 不是 `0 * Inf` 或 `Inf * 0`，则返回 NaN（而无 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）。

**注解**

​	此运算经常在硬件中实现为[融合乘加](https://en.wikipedia.org/wiki/Multiply–accumulate_operation) CPU 指令。若硬件支持，则期待定义相应的 `FP_FAST_FMA*` 宏，但多数实现即使在不定义这些宏时也利用该 CPU 指令。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fma.html) `x * y` 非法且 `z` 为 NaN 的情形是定义域错误。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.13.1 The fma functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.10.1 The fma functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.13.1 The fma functions （第 188-189 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.10.1 The fma functions （第 386 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.13.1 The fma functions （第 258 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.10.1 The fma functions （第 530 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.13.1 The fma functions （第 239 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.10.1 The fma functions （第 466 页）

**参阅**

| [remainder (C99)<br />remainderf (C99)<br />remainderl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remainder) | 计算浮点数除法运算的带符号余数 (函数)           |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [remquo (C99)<br />remquof (C99)<br />remquol (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remquo) | 计算除法运算的带符号余数，以及商的后三位 (函数) |
| **fma** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fma)** |                                                 |





### FP_ILOGB0

原址：[https://zh.cppreference.com/w/c/numeric/math/ilogb](https://zh.cppreference.com/w/c/numeric/math/ilogb)

作用：分别求值为当 x 为 0 或 NaN 时的 `ilogb(x)`  (宏常量)

备注：
```c
// 在标头 <math.h> 定义
int ilogbf( float arg );// (1)(C99 起)
int ilogb( double arg );// (2)(C99 起)
int ilogbl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define ilogb( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
#define FP_ILOGB0    /* 由实现定义 */// (5)(C99 起)
#define FP_ILOGBNAN  /* 由实现定义 */// (6)(C99 起)
```

1-3) 从浮点数实参 `arg` 提取独立于基底的无偏指数，并将它作为有符号整数返回。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `ilogbl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `ilogb`。否则调用 `ilogbf`。

5） 展开成整数常量表达式，值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 或 `-[INT_MAX](http://zh.cppreference.com/w/c/types/limits)`。

6） 展开成整数常量表达式，值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 或 `+[INT_MAX](http://zh.cppreference.com/w/c/types/limits)`。

​	正式而言，无偏指数是非零 `arg` 的 *logr|arg|* 的整数部分，作为有符号整数，其中 `r` 是 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits)。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回作为 int 值的 `arg` 的无偏指数。

​	若 `arg` 为零，则返回 FP_ILOGB0。

​	若 `arg` 为无穷大，则返回 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)。

​	若 `arg` 为 NaN，则返回 FP_ILOGBNAN。

​	若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)，则返回值未指定，且可能出现定义域或值域错误。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 为零、无穷大或 NaN ，则可能出现定义域错误或值域错误。

​	若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) ，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `arg` 为 ±0、 ±∞ 或 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 所有其他情况下，结果是准确的（决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）并且忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**注解**

​	若 `arg` 不是零、无穷大或 NaN，则返回的值准确等价于 `(int)[logb](http://zh.cppreference.com/w/c/numeric/math/logb)(arg)`。

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/ilogb.html)若 `arg` 为零、无穷大、NaN 或若正确结果在 `int` 的范围外则出现定义域错误。

​	POSIX 亦要求在 XSI 一致的系统上，正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 时返回值为 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)，而正确结果小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 时返回值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)。

​	在所有已知平台上正确结果都能表示成 `int`。对于要出现溢出的情况，[INT_MAX](https://zh.cppreference.com/w/c/types/limits) 必须小于 `[LDBL_MAX_EXP](http://zh.cppreference.com/w/c/types/limits) * log2([FLT_RADIX](http://zh.cppreference.com/w/c/types/limits))` 或 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 必须大于 `[LDBL_MIN_EXP](http://zh.cppreference.com/w/c/types/limits) - [LDBL_MANT_DIG](http://zh.cppreference.com/w/c/types/limits)) * log2([FLT_RADIX](http://zh.cppreference.com/w/c/types/limits))`。

​	`ilogb` 所返回的指数值始终比 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 所返回的小 1，因为不同的正规化要求：对于 `ilogb` 返回的指数 `e`，*|arg\*r-e
|* 在 1 与 `r` 之间（典型地在 `1` 与 `2` 之间），但 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 返回的指数 `e`，*|arg\*2-e
|* 在 `0.5` 与 `1` 之间。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12/8 Mathematics <math.h> （第 TBD 页）

  - 7.12.6.5 The ilogb functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.5 The ilogb functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/8 Mathematics <math.h> （第 TBD 页）

  - 7.12.6.5 The ilogb functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.5 The ilogb functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/8 Mathematics <math.h> （第 232 页）

  - 7.12.6.5 The ilogb functions （第 244 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.5 The ilogb functions （第 521 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/8 Mathematics <math.h> （第 213 页）

  - 7.12.6.5 The ilogb functions （第 224-225 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.5 The ilogb functions （第 458 页）

**参阅**

| [frexp <br />frexpf (C99)<br />frexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/frexp) | 将数拆分成有效数字和 *2* 的幂次 (函数)                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [logb (C99)<br />logbf (C99)<br />logbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/logb) | 提取给定数的指数（结果为浮点数） (函数)                      |
| [scalbn (C99)<br />scalbnf (C99)<br />scalbnl (C99)<br />scalbln (C99)<br />scalblnf (C99)<br />scalblnl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/scalbn) | 高效计算一个数乘 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 的幂 (函数) |
| **ilogb** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/ilogb)** |                                                              |





### FP_ILOGBNAN

原址：[https://zh.cppreference.com/w/c/numeric/math/ilogb](https://zh.cppreference.com/w/c/numeric/math/ilogb)

作用：分别求值为当 x 为 0 或 NaN 时的 `ilogb(x)`  (宏常量)

备注：
```c
// 在标头 <math.h> 定义
int ilogbf( float arg );// (1)(C99 起)
int ilogb( double arg );// (2)(C99 起)
int ilogbl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define ilogb( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
#define FP_ILOGB0    /* 由实现定义 */// (5)(C99 起)
#define FP_ILOGBNAN  /* 由实现定义 */// (6)(C99 起)
```

1-3) 从浮点数实参 `arg` 提取独立于基底的无偏指数，并将它作为有符号整数返回。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `ilogbl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `ilogb`。否则调用 `ilogbf`。

5） 展开成整数常量表达式，值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 或 `-[INT_MAX](http://zh.cppreference.com/w/c/types/limits)`。

6） 展开成整数常量表达式，值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 或 `+[INT_MAX](http://zh.cppreference.com/w/c/types/limits)`。

​	正式而言，无偏指数是非零 `arg` 的 *logr|arg|* 的整数部分，作为有符号整数，其中 `r` 是 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits)。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回作为 int 值的 `arg` 的无偏指数。

​	若 `arg` 为零，则返回 FP_ILOGB0。

​	若 `arg` 为无穷大，则返回 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)。

​	若 `arg` 为 NaN，则返回 FP_ILOGBNAN。

​	若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)，则返回值未指定，且可能出现定义域或值域错误。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 为零、无穷大或 NaN ，则可能出现定义域错误或值域错误。

​	若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) ，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `arg` 为 ±0、 ±∞ 或 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 所有其他情况下，结果是准确的（决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）并且忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**注解**

​	若 `arg` 不是零、无穷大或 NaN，则返回的值准确等价于 `(int)[logb](http://zh.cppreference.com/w/c/numeric/math/logb)(arg)`。

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/ilogb.html)若 `arg` 为零、无穷大、NaN 或若正确结果在 `int` 的范围外则出现定义域错误。

​	POSIX 亦要求在 XSI 一致的系统上，正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 时返回值为 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)，而正确结果小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 时返回值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)。

​	在所有已知平台上正确结果都能表示成 `int`。对于要出现溢出的情况，[INT_MAX](https://zh.cppreference.com/w/c/types/limits) 必须小于 `[LDBL_MAX_EXP](http://zh.cppreference.com/w/c/types/limits) * log2([FLT_RADIX](http://zh.cppreference.com/w/c/types/limits))` 或 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 必须大于 `[LDBL_MIN_EXP](http://zh.cppreference.com/w/c/types/limits) - [LDBL_MANT_DIG](http://zh.cppreference.com/w/c/types/limits)) * log2([FLT_RADIX](http://zh.cppreference.com/w/c/types/limits))`。

​	`ilogb` 所返回的指数值始终比 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 所返回的小 1，因为不同的正规化要求：对于 `ilogb` 返回的指数 `e`，*|arg\*r-e
|* 在 1 与 `r` 之间（典型地在 `1` 与 `2` 之间），但 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 返回的指数 `e`，*|arg\*2-e
|* 在 `0.5` 与 `1` 之间。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12/8 Mathematics <math.h> （第 TBD 页）

  - 7.12.6.5 The ilogb functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.5 The ilogb functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/8 Mathematics <math.h> （第 TBD 页）

  - 7.12.6.5 The ilogb functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.5 The ilogb functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/8 Mathematics <math.h> （第 232 页）

  - 7.12.6.5 The ilogb functions （第 244 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.5 The ilogb functions （第 521 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/8 Mathematics <math.h> （第 213 页）

  - 7.12.6.5 The ilogb functions （第 224-225 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.5 The ilogb functions （第 458 页）

**参阅**

| [frexp <br />frexpf (C99)<br />frexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/frexp) | 将数拆分成有效数字和 *2* 的幂次 (函数)                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [logb (C99)<br />logbf (C99)<br />logbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/logb) | 提取给定数的指数（结果为浮点数） (函数)                      |
| [scalbn (C99)<br />scalbnf (C99)<br />scalbnl (C99)<br />scalbln (C99)<br />scalblnf (C99)<br />scalblnl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/scalbn) | 高效计算一个数乘 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 的幂 (函数) |
| **ilogb** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/ilogb)** |                                                              |





### FP_INFINITE

原址：[https://zh.cppreference.com/w/c/numeric/math/FP_categories](https://zh.cppreference.com/w/c/numeric/math/FP_categories)

作用：指示浮点数类别   (宏常量)

备注：
```c
// 在标头 <math.h> 定义
#define FP_NORMAL    /* 由实现定义 */// (C99 起)
#define FP_SUBNORMAL /* 由实现定义 */// (C99 起)
#define FP_ZERO      /* 由实现定义 */// (C99 起)
#define FP_INFINITE  /* 由实现定义 */// (C99 起)
#define FP_NAN       /* 由实现定义 */// (C99 起)
```

​	`FP_NORMAL`、`FP_SUBNORMAL`、`FP_ZERO`、`FP_INFINITE`、`FP_NAN` 宏各代表一个独自的浮点数类别。它们都展开成整数常量表达式。

| 常量           | 解释                                                         |
| -------------- | ------------------------------------------------------------ |
| `FP_NORMAL`    | 指示值为*正规*，即不是无穷大、非正规、非数或零               |
| `FP_SUBNORMAL` | 指示值为[*非正规*](https://en.wikipedia.org/wiki/Subnormal_number) |
| `FP_ZERO`      | 指示值为正或负零                                             |
| `FP_INFINITE`  | 指示值无法以底层类型表示（正或负无穷大）                     |
| `FP_NAN`       | 指示值是非数（NaN）                                          |

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <float.h>
 
const char *show_classification(double x) {
    switch(fpclassify(x)) {
        case FP_INFINITE:  return "Inf";
        case FP_NAN:       return "NaN";
        case FP_NORMAL:    return "normal";
        case FP_SUBNORMAL: return "subnormal";
        case FP_ZERO:      return "zero";
        default:           return "unknown";
    }
}
int main(void)
{
    printf("1.0/0.0 is %s\n", show_classification(1/0.0));
    printf("0.0/0.0 is %s\n", show_classification(0.0/0.0));
    printf("DBL_MIN/2 is %s\n", show_classification(DBL_MIN/2));
    printf("-0.0 is %s\n", show_classification(-0.0));
    printf(" 1.0 is %s\n", show_classification(1.0));
}
```

​	输出：

```txt
1.0/0.0 is Inf
0.0/0.0 is NaN
DBL_MIN/2 is subnormal
-0.0 is zero
 1.0 is normal
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/6 FP_NORMAL, ... （第 169-170 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/6 FP_NORMAL, ... （第 232 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/6 FP_NORMAL, ... （第 213 页）

**参阅**

| [fpclassify (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fpclassify) | 对给定的浮点数分类 (宏函数) |
| ------------------------------------------------------------ | --------------------------- |
| **FP_categories** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/FP_categories)** |                             |





### FP_NAN

原址：[https://zh.cppreference.com/w/c/numeric/math/FP_categories](https://zh.cppreference.com/w/c/numeric/math/FP_categories)

作用：指示浮点数类别   (宏常量)

备注：
```c
// 在标头 <math.h> 定义
#define FP_NORMAL    /* 由实现定义 */// (C99 起)
#define FP_SUBNORMAL /* 由实现定义 */// (C99 起)
#define FP_ZERO      /* 由实现定义 */// (C99 起)
#define FP_INFINITE  /* 由实现定义 */// (C99 起)
#define FP_NAN       /* 由实现定义 */// (C99 起)
```

​	`FP_NORMAL`、`FP_SUBNORMAL`、`FP_ZERO`、`FP_INFINITE`、`FP_NAN` 宏各代表一个独自的浮点数类别。它们都展开成整数常量表达式。

| 常量           | 解释                                                         |
| -------------- | ------------------------------------------------------------ |
| `FP_NORMAL`    | 指示值为*正规*，即不是无穷大、非正规、非数或零               |
| `FP_SUBNORMAL` | 指示值为[*非正规*](https://en.wikipedia.org/wiki/Subnormal_number) |
| `FP_ZERO`      | 指示值为正或负零                                             |
| `FP_INFINITE`  | 指示值无法以底层类型表示（正或负无穷大）                     |
| `FP_NAN`       | 指示值是非数（NaN）                                          |

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <float.h>
 
const char *show_classification(double x) {
    switch(fpclassify(x)) {
        case FP_INFINITE:  return "Inf";
        case FP_NAN:       return "NaN";
        case FP_NORMAL:    return "normal";
        case FP_SUBNORMAL: return "subnormal";
        case FP_ZERO:      return "zero";
        default:           return "unknown";
    }
}
int main(void)
{
    printf("1.0/0.0 is %s\n", show_classification(1/0.0));
    printf("0.0/0.0 is %s\n", show_classification(0.0/0.0));
    printf("DBL_MIN/2 is %s\n", show_classification(DBL_MIN/2));
    printf("-0.0 is %s\n", show_classification(-0.0));
    printf(" 1.0 is %s\n", show_classification(1.0));
}
```

​	输出：

```txt
1.0/0.0 is Inf
0.0/0.0 is NaN
DBL_MIN/2 is subnormal
-0.0 is zero
 1.0 is normal
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/6 FP_NORMAL, ... （第 169-170 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/6 FP_NORMAL, ... （第 232 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/6 FP_NORMAL, ... （第 213 页）

**参阅**

| [fpclassify (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fpclassify) | 对给定的浮点数分类 (宏函数) |
| ------------------------------------------------------------ | --------------------------- |
| **FP_categories** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/FP_categories)** |                             |





### FP_NORMAL

原址：[https://zh.cppreference.com/w/c/numeric/math/FP_categories](https://zh.cppreference.com/w/c/numeric/math/FP_categories)

作用：指示浮点数类别   (宏常量)

备注：
```c
// 在标头 <math.h> 定义
#define FP_NORMAL    /* 由实现定义 */// (C99 起)
#define FP_SUBNORMAL /* 由实现定义 */// (C99 起)
#define FP_ZERO      /* 由实现定义 */// (C99 起)
#define FP_INFINITE  /* 由实现定义 */// (C99 起)
#define FP_NAN       /* 由实现定义 */// (C99 起)
```

​	`FP_NORMAL`、`FP_SUBNORMAL`、`FP_ZERO`、`FP_INFINITE`、`FP_NAN` 宏各代表一个独自的浮点数类别。它们都展开成整数常量表达式。

| 常量           | 解释                                                         |
| -------------- | ------------------------------------------------------------ |
| `FP_NORMAL`    | 指示值为*正规*，即不是无穷大、非正规、非数或零               |
| `FP_SUBNORMAL` | 指示值为[*非正规*](https://en.wikipedia.org/wiki/Subnormal_number) |
| `FP_ZERO`      | 指示值为正或负零                                             |
| `FP_INFINITE`  | 指示值无法以底层类型表示（正或负无穷大）                     |
| `FP_NAN`       | 指示值是非数（NaN）                                          |

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <float.h>
 
const char *show_classification(double x) {
    switch(fpclassify(x)) {
        case FP_INFINITE:  return "Inf";
        case FP_NAN:       return "NaN";
        case FP_NORMAL:    return "normal";
        case FP_SUBNORMAL: return "subnormal";
        case FP_ZERO:      return "zero";
        default:           return "unknown";
    }
}
int main(void)
{
    printf("1.0/0.0 is %s\n", show_classification(1/0.0));
    printf("0.0/0.0 is %s\n", show_classification(0.0/0.0));
    printf("DBL_MIN/2 is %s\n", show_classification(DBL_MIN/2));
    printf("-0.0 is %s\n", show_classification(-0.0));
    printf(" 1.0 is %s\n", show_classification(1.0));
}
```

​	输出：

```txt
1.0/0.0 is Inf
0.0/0.0 is NaN
DBL_MIN/2 is subnormal
-0.0 is zero
 1.0 is normal
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/6 FP_NORMAL, ... （第 169-170 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/6 FP_NORMAL, ... （第 232 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/6 FP_NORMAL, ... （第 213 页）

**参阅**

| [fpclassify (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fpclassify) | 对给定的浮点数分类 (宏函数) |
| ------------------------------------------------------------ | --------------------------- |
| **FP_categories** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/FP_categories)** |                             |





### FP_SUBNORMAL

原址：[https://zh.cppreference.com/w/c/numeric/math/FP_categories](https://zh.cppreference.com/w/c/numeric/math/FP_categories)

作用：指示浮点数类别   (宏常量)

备注：
```c
// 在标头 <math.h> 定义
#define FP_NORMAL    /* 由实现定义 */// (C99 起)
#define FP_SUBNORMAL /* 由实现定义 */// (C99 起)
#define FP_ZERO      /* 由实现定义 */// (C99 起)
#define FP_INFINITE  /* 由实现定义 */// (C99 起)
#define FP_NAN       /* 由实现定义 */// (C99 起)
```

​	`FP_NORMAL`、`FP_SUBNORMAL`、`FP_ZERO`、`FP_INFINITE`、`FP_NAN` 宏各代表一个独自的浮点数类别。它们都展开成整数常量表达式。

| 常量           | 解释                                                         |
| -------------- | ------------------------------------------------------------ |
| `FP_NORMAL`    | 指示值为*正规*，即不是无穷大、非正规、非数或零               |
| `FP_SUBNORMAL` | 指示值为[*非正规*](https://en.wikipedia.org/wiki/Subnormal_number) |
| `FP_ZERO`      | 指示值为正或负零                                             |
| `FP_INFINITE`  | 指示值无法以底层类型表示（正或负无穷大）                     |
| `FP_NAN`       | 指示值是非数（NaN）                                          |

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <float.h>
 
const char *show_classification(double x) {
    switch(fpclassify(x)) {
        case FP_INFINITE:  return "Inf";
        case FP_NAN:       return "NaN";
        case FP_NORMAL:    return "normal";
        case FP_SUBNORMAL: return "subnormal";
        case FP_ZERO:      return "zero";
        default:           return "unknown";
    }
}
int main(void)
{
    printf("1.0/0.0 is %s\n", show_classification(1/0.0));
    printf("0.0/0.0 is %s\n", show_classification(0.0/0.0));
    printf("DBL_MIN/2 is %s\n", show_classification(DBL_MIN/2));
    printf("-0.0 is %s\n", show_classification(-0.0));
    printf(" 1.0 is %s\n", show_classification(1.0));
}
```

​	输出：

```txt
1.0/0.0 is Inf
0.0/0.0 is NaN
DBL_MIN/2 is subnormal
-0.0 is zero
 1.0 is normal
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/6 FP_NORMAL, ... （第 169-170 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/6 FP_NORMAL, ... （第 232 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/6 FP_NORMAL, ... （第 213 页）

**参阅**

| [fpclassify (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fpclassify) | 对给定的浮点数分类 (宏函数) |
| ------------------------------------------------------------ | --------------------------- |
| **FP_categories** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/FP_categories)** |                             |





### FP_ZERO

原址：[https://zh.cppreference.com/w/c/numeric/math/FP_categories](https://zh.cppreference.com/w/c/numeric/math/FP_categories)

作用：指示浮点数类别   (宏常量)

备注：
```c
// 在标头 <math.h> 定义
#define FP_NORMAL    /* 由实现定义 */// (C99 起)
#define FP_SUBNORMAL /* 由实现定义 */// (C99 起)
#define FP_ZERO      /* 由实现定义 */// (C99 起)
#define FP_INFINITE  /* 由实现定义 */// (C99 起)
#define FP_NAN       /* 由实现定义 */// (C99 起)
```

​	`FP_NORMAL`、`FP_SUBNORMAL`、`FP_ZERO`、`FP_INFINITE`、`FP_NAN` 宏各代表一个独自的浮点数类别。它们都展开成整数常量表达式。

| 常量           | 解释                                                         |
| -------------- | ------------------------------------------------------------ |
| `FP_NORMAL`    | 指示值为*正规*，即不是无穷大、非正规、非数或零               |
| `FP_SUBNORMAL` | 指示值为[*非正规*](https://en.wikipedia.org/wiki/Subnormal_number) |
| `FP_ZERO`      | 指示值为正或负零                                             |
| `FP_INFINITE`  | 指示值无法以底层类型表示（正或负无穷大）                     |
| `FP_NAN`       | 指示值是非数（NaN）                                          |

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <float.h>
 
const char *show_classification(double x) {
    switch(fpclassify(x)) {
        case FP_INFINITE:  return "Inf";
        case FP_NAN:       return "NaN";
        case FP_NORMAL:    return "normal";
        case FP_SUBNORMAL: return "subnormal";
        case FP_ZERO:      return "zero";
        default:           return "unknown";
    }
}
int main(void)
{
    printf("1.0/0.0 is %s\n", show_classification(1/0.0));
    printf("0.0/0.0 is %s\n", show_classification(0.0/0.0));
    printf("DBL_MIN/2 is %s\n", show_classification(DBL_MIN/2));
    printf("-0.0 is %s\n", show_classification(-0.0));
    printf(" 1.0 is %s\n", show_classification(1.0));
}
```

​	输出：

```txt
1.0/0.0 is Inf
0.0/0.0 is NaN
DBL_MIN/2 is subnormal
-0.0 is zero
 1.0 is normal
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/6 FP_NORMAL, ... （第 169-170 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/6 FP_NORMAL, ... （第 232 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/6 FP_NORMAL, ... （第 213 页）

**参阅**

| [fpclassify (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fpclassify) | 对给定的浮点数分类 (宏函数) |
| ------------------------------------------------------------ | --------------------------- |
| **FP_categories** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/FP_categories)** |                             |





### HUGE_VAL

原址：[https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)

作用：分别指示过大而无法以 `float`、`double` 和 `long double` 表示的值（无穷大）  (宏常量)

备注：
```c
// 在标头 <math.h> 定义
#define HUGE_VALF /* 由实现定义 */// (C99 起)
#define HUGE_VAL  /* 由实现定义 */
#define HUGE_VALL /* 由实现定义 */// (C99 起)
```

​	`HUGE_VALF`、`HUGE_VAL` 和 `HUGE_VALL` 宏展开成正浮点数常量表达式，它们比较等于上溢情况中浮点数函数和运算符的返回值（见 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling)）。

| 常量        | 解释                                                         |
| ----------- | ------------------------------------------------------------ |
| `HUGE_VALF` | 展开成指示上溢的正 `float` 表达式                            |
| `HUGE_VAL`  | 展开成指示上溢的正 `double` 表达式，不必可表示为 `float`     |
| `HUGE_VALL` | 展开成指示上溢的正 `long double` 表达式，不必可表示为 `float` 或 `double` |

​	在支持浮点数无穷大的平台上，这些宏始终分别展开成 `float`、`double` 和 `long double` 的正无穷大。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12/3 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 TBD 页）

  - F.10/2 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/3 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 TBD 页）

  - F.10/2 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/3 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 231 页）

  - F.10/2 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 517 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/3 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 212 页）

  - F.9/2 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 454 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5 HUGE_VAL

**参阅**

| [INFINITY (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/INFINITY) | 求值为正无穷大或保证溢出 `float` 的值 (宏常量) |
| ------------------------------------------------------------ | ---------------------------------------------- |
| **HUGE_VAL** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/HUGE_VAL)** |                                                |





### HUGE_VALF

原址：[https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)

作用：分别指示过大而无法以 `float`、`double` 和 `long double` 表示的值（无穷大）  (宏常量)

备注：
```c
// 在标头 <math.h> 定义
#define HUGE_VALF /* 由实现定义 */// (C99 起)
#define HUGE_VAL  /* 由实现定义 */
#define HUGE_VALL /* 由实现定义 */// (C99 起)
```

​	`HUGE_VALF`、`HUGE_VAL` 和 `HUGE_VALL` 宏展开成正浮点数常量表达式，它们比较等于上溢情况中浮点数函数和运算符的返回值（见 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling)）。

| 常量        | 解释                                                         |
| ----------- | ------------------------------------------------------------ |
| `HUGE_VALF` | 展开成指示上溢的正 `float` 表达式                            |
| `HUGE_VAL`  | 展开成指示上溢的正 `double` 表达式，不必可表示为 `float`     |
| `HUGE_VALL` | 展开成指示上溢的正 `long double` 表达式，不必可表示为 `float` 或 `double` |

​	在支持浮点数无穷大的平台上，这些宏始终分别展开成 `float`、`double` 和 `long double` 的正无穷大。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12/3 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 TBD 页）

  - F.10/2 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/3 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 TBD 页）

  - F.10/2 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/3 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 231 页）

  - F.10/2 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 517 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/3 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 212 页）

  - F.9/2 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 454 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5 HUGE_VAL

**参阅**

| [INFINITY (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/INFINITY) | 求值为正无穷大或保证溢出 `float` 的值 (宏常量) |
| ------------------------------------------------------------ | ---------------------------------------------- |
| **HUGE_VAL** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/HUGE_VAL)** |                                                |





### HUGE_VALL

原址：[https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)

作用：分别指示过大而无法以 `float`、`double` 和 `long double` 表示的值（无穷大）  (宏常量)

备注：
```c
// 在标头 <math.h> 定义
#define HUGE_VALF /* 由实现定义 */// (C99 起)
#define HUGE_VAL  /* 由实现定义 */
#define HUGE_VALL /* 由实现定义 */// (C99 起)
```

​	`HUGE_VALF`、`HUGE_VAL` 和 `HUGE_VALL` 宏展开成正浮点数常量表达式，它们比较等于上溢情况中浮点数函数和运算符的返回值（见 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling)）。

| 常量        | 解释                                                         |
| ----------- | ------------------------------------------------------------ |
| `HUGE_VALF` | 展开成指示上溢的正 `float` 表达式                            |
| `HUGE_VAL`  | 展开成指示上溢的正 `double` 表达式，不必可表示为 `float`     |
| `HUGE_VALL` | 展开成指示上溢的正 `long double` 表达式，不必可表示为 `float` 或 `double` |

​	在支持浮点数无穷大的平台上，这些宏始终分别展开成 `float`、`double` 和 `long double` 的正无穷大。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12/3 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 TBD 页）

  - F.10/2 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/3 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 TBD 页）

  - F.10/2 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/3 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 231 页）

  - F.10/2 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 517 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/3 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 212 页）

  - F.9/2 HUGE_VAL, HUGE_VALF, HUGE_VALL （第 454 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5 HUGE_VAL

**参阅**

| [INFINITY (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/INFINITY) | 求值为正无穷大或保证溢出 `float` 的值 (宏常量) |
| ------------------------------------------------------------ | ---------------------------------------------- |
| **HUGE_VAL** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/HUGE_VAL)** |                                                |





### INFINITY

原址：[https://zh.cppreference.com/w/c/numeric/math/INFINITY](https://zh.cppreference.com/w/c/numeric/math/INFINITY)

作用：求值为正无穷大或保证溢出 `float` 的值  (宏常量)

备注：
```c
// 在标头 <math.h> 定义
#define INFINITY /* 由实现定义 */// (C99 起)
```

​	若实现支持浮点数无穷大，则宏 `INFINITY` 展开成求值为正或无符号无穷大的 `float` 类型常量表达式。

​	若实现不支持浮点数无穷大，则宏 `INFINITY` 展开成保证在编译时上溢 `float` 的正值，而此宏的使用生成编译器警告。

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

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/4 INFINITY （第 231-232 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/4 INFINITY （第 212-213 页）

**参阅**

| [isinf (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isinf) | 检查给定数是否是无穷大 (宏函数)                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [HUGE_VALF (C99)<br />HUGE_VAL (C99)<br />HUGE_VALL <br />](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL) | 分别指示过大而无法以 `float`、`double` 和 `long double` 表示的值（无穷大） (宏常量) |
| **INFINITY** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/INFINITY)** |                                                              |





### MATH_ERREXCEPT

原址：[https://zh.cppreference.com/w/c/numeric/math/math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling)

作用：定义用于常用数学函数的错误处理机制   (宏常量)

备注：
```c
// 在标头 <math.h> 定义
#define MATH_ERRNO        1// (C99 起)
#define MATH_ERREXCEPT    2// (C99 起)
#define math_errhandling  /* 由实现定义 */// (C99 起)
```

​	宏常量 `math_errhandling` 展开成 `int` 类型的表达式，要么等于 `MATH_ERRNO`，要么等于 `MATH_ERREXCEPT`，要么等于其逐位或（`MATH_ERRNO | MATH_ERREXCEPT`）。

​	`math_errhandling` 的值指示浮点数运算符和[函数](https://zh.cppreference.com/w/c/numeric/math)所进行的错误处理：

| 常量             | 解释                                                         |
| ---------------- | ------------------------------------------------------------ |
| `MATH_ERREXCEPT` | 指示使用浮点数异常：`<fenv.h>` 中至少定义了 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)、[FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 及 [FE_OVERFLOW](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。 |
| `MATH_ERRNO`     | 指明浮点数运算使用变量 [errno](https://zh.cppreference.com/w/c/error/errno) 报告错误。 |

​	若实现支持 IEEE 浮点数算术（IEC 60559），则要求 `math_errhandling & MATH_ERREXCEPT` 非零。

​	识别下列浮点数错误条件：

|        条件        |                             解释                             |                            errno                             |                          浮点数异常                          |                             示例                             |
| :----------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|     定义域错误     | 实参在该运算的数学上的定义域之外（[每个函数](https://zh.cppreference.com/w/c/numeric/math)的描述列出了要求的定义域错误） |  [EDOM](https://zh.cppreference.com/w/c/error/errno_macros)  | [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) | `[acos](http://zh.cppreference.com/w/c/numeric/math/acos)(2)` |
|      极点错误      |               函数的数学结果恰是无限大或未定义               | [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros) | [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) | `[log](http://zh.cppreference.com/w/c/numeric/math/log)(0.0)`、`1.0/0.0` |
| 上溢所致的值域错误 | 数学结果有限，但舍入后变为无限，或在向下舍入后变成最大可表示有限值 | [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros) | [FE_OVERFLOW](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) | `[pow](http://zh.cppreference.com/w/c/numeric/math/pow)([DBL_MAX](http://zh.cppreference.com/w/c/types/limits),2)` |
| 下溢所致的值域错误 |     结果非零，但因为舍入变为零，或变成非正规并有精度损失     | [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros) 或不改变（实现定义） | [FE_UNDERFLOW](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 或无（实现定义） |                       `DBL_TRUE_MIN/2`                       |
|     结果不准确     |                   结果必须被舍入到目标类型                   |                            不改变                            | [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)或无（未指定） | `[sqrt](http://zh.cppreference.com/w/c/numeric/math/sqrt)(2)`、`1.0/10.0` |

**注意**

​	通常，[FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 是否为数学库函数所引发是未指定的，但这可以显式指定于函数的描述（例如 [rint](https://zh.cppreference.com/w/c/numeric/math/rint) vs [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint)）。

​	C99 前，浮点数异常是未指定的，要求对于任何定义于错误发生 `[EDOM](http://zh.cppreference.com/w/c/error/errno_macros)`，要求对上溢和实现定义的下溢发生 `[ERANGE](http://zh.cppreference.com/w/c/error/errno_macros)`。

**示例**

```c
#include <stdio.h>
#include <fenv.h>
#include <math.h>
#include <errno.h>
#pragma STDC FENV_ACCESS ON
int main(void)
{
    printf("MATH_ERRNO is %s\n", math_errhandling & MATH_ERRNO ? "set" : "not set");
    printf("MATH_ERREXCEPT is %s\n",
           math_errhandling & MATH_ERREXCEPT ? "set" : "not set");
    feclearexcept(FE_ALL_EXCEPT);
    errno = 0;
    printf("log(0) = %f\n", log(0));
    if(errno == ERANGE)
        perror("errno == ERANGE");
    if(fetestexcept(FE_DIVBYZERO))
        puts("FE_DIVBYZERO (pole error) reported");
}
```

​	可能的输出：

```txt
MATH_ERRNO is set
MATH_ERREXCEPT is set
log(0) = -inf
errno = ERANGE: Numerical result out of range
FE_DIVBYZERO (pole error) reported
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/9 MATH_ERRNO, MATH_ERREXCEPT, math_errhandling （第 170 页）

  - F.10/4 MATH_ERREXCEPT, math_errhandling （第 377 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/9 MATH_ERRNO, MATH_ERREXCEPT, math_errhandling （第 233 页）

  - F.10/4 MATH_ERREXCEPT, math_errhandling （第 517 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/9 MATH_ERRNO, MATH_ERREXCEPT, math_errhandling （第 214 页）

  - F.9/4 MATH_ERREXCEPT, math_errhandling> （第 454 页）

**参阅**

| [FE_ALL_EXCEPT (C99)<br />FE_DIVBYZERO (C99)<br />FE_INEXACT<br />FE_INVALID<br />FE_OVERFLOW<br />FE_UNDERFLOW<br />](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) | 浮点数异常 (宏常量)                              |
| ------------------------------------------------------------ | ------------------------------------------------ |
| [errno<br />](https://zh.cppreference.com/w/c/error/errno) | 展开成 POSIX 兼容的线程局域错误编号变量 (宏变量) |
| **math_errhandling** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/math_errhandling)** |                                                  |





### MATH_ERRNO

原址：[https://zh.cppreference.com/w/c/numeric/math/math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling)

作用：定义用于常用数学函数的错误处理机制   (宏常量)

备注：
```c
// 在标头 <math.h> 定义
#define MATH_ERRNO        1// (C99 起)
#define MATH_ERREXCEPT    2// (C99 起)
#define math_errhandling  /* 由实现定义 */// (C99 起)
```

​	宏常量 `math_errhandling` 展开成 `int` 类型的表达式，要么等于 `MATH_ERRNO`，要么等于 `MATH_ERREXCEPT`，要么等于其逐位或（`MATH_ERRNO | MATH_ERREXCEPT`）。

​	`math_errhandling` 的值指示浮点数运算符和[函数](https://zh.cppreference.com/w/c/numeric/math)所进行的错误处理：

| 常量             | 解释                                                         |
| ---------------- | ------------------------------------------------------------ |
| `MATH_ERREXCEPT` | 指示使用浮点数异常：`<fenv.h>` 中至少定义了 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)、[FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 及 [FE_OVERFLOW](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。 |
| `MATH_ERRNO`     | 指明浮点数运算使用变量 [errno](https://zh.cppreference.com/w/c/error/errno) 报告错误。 |

​	若实现支持 IEEE 浮点数算术（IEC 60559），则要求 `math_errhandling & MATH_ERREXCEPT` 非零。

​	识别下列浮点数错误条件：

|        条件        |                             解释                             |                            errno                             |                          浮点数异常                          |                             示例                             |
| :----------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|     定义域错误     | 实参在该运算的数学上的定义域之外（[每个函数](https://zh.cppreference.com/w/c/numeric/math)的描述列出了要求的定义域错误） |  [EDOM](https://zh.cppreference.com/w/c/error/errno_macros)  | [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) | `[acos](http://zh.cppreference.com/w/c/numeric/math/acos)(2)` |
|      极点错误      |               函数的数学结果恰是无限大或未定义               | [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros) | [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) | `[log](http://zh.cppreference.com/w/c/numeric/math/log)(0.0)`、`1.0/0.0` |
| 上溢所致的值域错误 | 数学结果有限，但舍入后变为无限，或在向下舍入后变成最大可表示有限值 | [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros) | [FE_OVERFLOW](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) | `[pow](http://zh.cppreference.com/w/c/numeric/math/pow)([DBL_MAX](http://zh.cppreference.com/w/c/types/limits),2)` |
| 下溢所致的值域错误 |     结果非零，但因为舍入变为零，或变成非正规并有精度损失     | [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros) 或不改变（实现定义） | [FE_UNDERFLOW](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 或无（实现定义） |                       `DBL_TRUE_MIN/2`                       |
|     结果不准确     |                   结果必须被舍入到目标类型                   |                            不改变                            | [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)或无（未指定） | `[sqrt](http://zh.cppreference.com/w/c/numeric/math/sqrt)(2)`、`1.0/10.0` |

**注意**

​	通常，[FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 是否为数学库函数所引发是未指定的，但这可以显式指定于函数的描述（例如 [rint](https://zh.cppreference.com/w/c/numeric/math/rint) vs [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint)）。

​	C99 前，浮点数异常是未指定的，要求对于任何定义于错误发生 `[EDOM](http://zh.cppreference.com/w/c/error/errno_macros)`，要求对上溢和实现定义的下溢发生 `[ERANGE](http://zh.cppreference.com/w/c/error/errno_macros)`。

**示例**

```c
#include <stdio.h>
#include <fenv.h>
#include <math.h>
#include <errno.h>
#pragma STDC FENV_ACCESS ON
int main(void)
{
    printf("MATH_ERRNO is %s\n", math_errhandling & MATH_ERRNO ? "set" : "not set");
    printf("MATH_ERREXCEPT is %s\n",
           math_errhandling & MATH_ERREXCEPT ? "set" : "not set");
    feclearexcept(FE_ALL_EXCEPT);
    errno = 0;
    printf("log(0) = %f\n", log(0));
    if(errno == ERANGE)
        perror("errno == ERANGE");
    if(fetestexcept(FE_DIVBYZERO))
        puts("FE_DIVBYZERO (pole error) reported");
}
```

​	可能的输出：

```txt
MATH_ERRNO is set
MATH_ERREXCEPT is set
log(0) = -inf
errno = ERANGE: Numerical result out of range
FE_DIVBYZERO (pole error) reported
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/9 MATH_ERRNO, MATH_ERREXCEPT, math_errhandling （第 170 页）

  - F.10/4 MATH_ERREXCEPT, math_errhandling （第 377 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/9 MATH_ERRNO, MATH_ERREXCEPT, math_errhandling （第 233 页）

  - F.10/4 MATH_ERREXCEPT, math_errhandling （第 517 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/9 MATH_ERRNO, MATH_ERREXCEPT, math_errhandling （第 214 页）

  - F.9/4 MATH_ERREXCEPT, math_errhandling> （第 454 页）

**参阅**

| [FE_ALL_EXCEPT (C99)<br />FE_DIVBYZERO (C99)<br />FE_INEXACT<br />FE_INVALID<br />FE_OVERFLOW<br />FE_UNDERFLOW<br />](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) | 浮点数异常 (宏常量)                              |
| ------------------------------------------------------------ | ------------------------------------------------ |
| [errno<br />](https://zh.cppreference.com/w/c/error/errno) | 展开成 POSIX 兼容的线程局域错误编号变量 (宏变量) |
| **math_errhandling** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/math_errhandling)** |                                                  |





### NAN

原址：[https://zh.cppreference.com/w/c/numeric/math/NAN](https://zh.cppreference.com/w/c/numeric/math/NAN)

作用：求值为 `float` 类型的安静 NaN  (宏常量)

备注：
```c
// 在标头 <math.h> 定义
#define NAN /* 由实现定义 */// (C99 起)
```

​	宏 `NAN` 展开成求值为安静非数（QNaN）的 `float` 类型常量表达式。若实现不支持 QNaN，则不定义此宏。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12/5 NAN （第 TBD 页）

  - F.10/11/13 NAN （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/5 NAN （第 TBD 页）

  - F.10/11/13 NAN （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/5 NAN （第 232 页）

  - F.10/11/13 NAN （第 518 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/5 NAN （第 213 页）

  - F.9/11/13 NAN （第 455 页）

**参阅**

| [nan (C99)<br />nanf (C99)<br />nanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/nan) | 返回 NaN（非数） (函数)       |
| ------------------------------------------------------------ | ----------------------------- |
| [isnan (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isnan) | 检查给定数是否为 NaN (宏函数) |
| **NAN** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/NAN)** |                               |





### __STDC_VERSION_MATH_H__

原址：

作用：

备注：





### fpclassify

原址：[https://zh.cppreference.com/w/c/numeric/math/fpclassify](https://zh.cppreference.com/w/c/numeric/math/fpclassify)

作用：对给定的浮点数分类   (宏函数)

备注：
```c
// 在标头 <math.h> 定义
#define fpclassify(arg) /* 由实现定义 */// (C99 起)
```

​	归类浮点数 `arg` 到下列类别中：零、非正规、正规、无穷大、NaN 或实现定义类别。该宏返回整数。

​	忽略 [FLT_EVAL_METHOD](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD)：即使以多于实参类型的范围和精度对它求值，首先仍将它转换到其语义类型，然后基于该类型分类：正规的 `long double` 值可能在转换到 `double` 时变为非正规，而在转换到 `float` 时变为零。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	指明 `arg` 类别的 [FP_INFINITE](https://zh.cppreference.com/w/c/numeric/math/FP_categories)、[FP_NAN](https://zh.cppreference.com/w/c/numeric/math/FP_categories)、[FP_NORMAL](https://zh.cppreference.com/w/c/numeric/math/FP_categories)、[FP_SUBNORMAL](https://zh.cppreference.com/w/c/numeric/math/FP_categories)、[FP_ZERO](https://zh.cppreference.com/w/c/numeric/math/FP_categories) 或实现定义类型之一。

**示例**

```c
#include <float.h>
#include <math.h>
#include <stdio.h>
 
const char *show_classification(double x)
{
    switch(fpclassify(x))
    {
        case FP_INFINITE:  return "Inf";
        case FP_NAN:       return "NaN";
        case FP_NORMAL:    return "正规";
        case FP_SUBNORMAL: return "非正规";
        case FP_ZERO:      return "零";
        default:           return "未知";
    }
}
int main(void)
{
    printf("1.0/0.0 为 %s\n", show_classification(1 / 0.0));
    printf("0.0/0.0 为 %s\n", show_classification(0.0 / 0.0));
    printf("DBL_MIN/2 为 %s\n", show_classification(DBL_MIN / 2));
    printf("-0.0 为 %s\n", show_classification(-0.0));
    printf("1.0 为 %s\n", show_classification(1.0));
}
```

​	输出：

```txt
1.0/0.0 为 Inf
0.0/0.0 为 NaN
DBL_MIN/2 为 非正规
-0.0 为 零
1.0 为 正规
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.3.1 The fpclassify macro （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.3.1 The fpclassify macro （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.3.1 The fpclassify macro （第 235 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.3.1 The fpclassify macro （第 216 页）

**参阅**

| [isfinite (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isfinite) | 检查给定数是否具有有限值 (宏函数) |
| ------------------------------------------------------------ | --------------------------------- |
| [isinf (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isinf) | 检查给定数是否是无穷大 (宏函数)   |
| [isnan (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isnan) | 检查给定数是否为 NaN (宏函数)     |
| [isnormal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isnormal) | 检查给定数是否正规 (宏函数)       |
| **fpclassify** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fpclassify)** |                                   |





### isfinite

原址：[https://zh.cppreference.com/w/c/numeric/math/isfinite](https://zh.cppreference.com/w/c/numeric/math/isfinite)

作用：检查给定数是否具有有限值   (宏函数)

备注：
```c
// 在标头 <math.h> 定义
#define isfinite(arg) /* 由实现定义 */// (C99 起)
```

​	确定给定的浮点数 `arg` 是否拥有有限值，即它是正规、非正规或零，但不是无穷大或 NaN。该宏返回整数。

​	忽略 [FLT_EVAL_METHOD](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD)：即使以多于实参类型的范围和精度对它求值，首先仍将它转换到其语义类型，然后分类基于该类型。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若 `arg` 拥有有限值则返回非零整数，否则返回 `0`。

**示例**

```c
#include <float.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("isfinite(NAN)         = %d\n", isfinite(NAN));
    printf("isfinite(INFINITY)    = %d\n", isfinite(INFINITY));
    printf("isfinite(0.0)         = %d\n", isfinite(0.0));
    printf("isfinite(DBL_MIN/2.0) = %d\n", isfinite(DBL_MIN / 2.0));
    printf("isfinite(1.0)         = %d\n", isfinite(1.0));
    printf("isfinite(exp(800))    = %d\n", isfinite(exp(800)));
}
```

​	可能的输出：

```txt
isfinite(NAN)         = 0
isfinite(INFINITY)    = 0
isfinite(0.0)         = 1
isfinite(DBL_MIN/2.0) = 1
isfinite(1.0)         = 1
isfinite(exp(800))    = 0
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.3.2 The isfinite macro （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.3.2 The isfinite macro （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.3.2 The isfinite macro （第 236 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.3.2 The isfinite macro （第 216-217 页）

**参阅**

| [fpclassify (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fpclassify) | 对给定的浮点数分类 (宏函数)     |
| ------------------------------------------------------------ | ------------------------------- |
| [isinf (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isinf) | 检查给定数是否是无穷大 (宏函数) |
| [isnan (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isnan) | 检查给定数是否为 NaN (宏函数)   |
| [isnormal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isnormal) | 检查给定数是否正规 (宏函数)     |
| **isfinite** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/isfinite)** |                                 |





### isgreater

原址：[https://zh.cppreference.com/w/c/numeric/math/isgreater](https://zh.cppreference.com/w/c/numeric/math/isgreater)

作用：检查第一个浮点数实参是否大于第二个  (宏函数)

备注：
```c
// 在标头 <math.h> 定义
#define isgreater(x, y) /* 由实现定义 */// (C99 起)
```

​	确定浮点数 `x` 是否大于浮点数 `y`，而不设置浮点数异常。

**参数**

| x    | -    | 浮点数 |
| ---- | ---- | ------ |
| y    | -    | 浮点数 |

**返回值**

​	若 `x > y` 则为非零整数，否则为 `0`。

**注解**

​	若一或两个参数为 NaN，则内建的 `operator>` 对浮点数可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。此宏是 `operator>` 的“安静”版本。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("isgreater(2.0,1.0)      = %d\n", isgreater(2.0, 1.0));
    printf("isgreater(1.0,2.0)      = %d\n", isgreater(1.0, 2.0));
    printf("isgreater(INFINITY,1.0) = %d\n", isgreater(INFINITY, 1.0));
    printf("isgreater(1.0,NAN)      = %d\n", isgreater(1.0, NAN));
 
    return 0;
}
```

​	可能的输出：

```txt
isgreater(2.0,1.0)      = 1
isgreater(1.0,2.0)      = 0
isgreater(INFINITY,1.0) = 1
isgreater(1.0,NAN)      = 0
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.14.1 The isgreater macro （第 TBD 页）

  - F.10.11 Comparison macros （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.14.1 The isgreater macro （第 189 页）

  - F.10.11 Comparison macros （第 386-387 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.14.1 The isgreater macro （第 259 页）

  - F.10.11 Comparison macros （第 531 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.14.1 The isgreater macro （第 240 页）

**参阅**

| [isless (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isless) | 检查第一个浮点数实参是否小于第二个 (宏函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| **isgreater** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/isgreater)** |                                             |





### isgreaterequal

原址：[https://zh.cppreference.com/w/c/numeric/math/isgreaterequal](https://zh.cppreference.com/w/c/numeric/math/isgreaterequal)

作用：检查第一个浮点数实参是否大于等于第二个  (宏函数)

备注：
```c
// 在标头 <math.h> 定义
#define isgreaterequal(x, y) /* 由实现定义 */// (C99 起)
```

​	确定浮点数 `x` 是否大于或等于浮点数 `y`，而不设置浮点数异常。

**参数**

| x    | -    | 浮点数 |
| ---- | ---- | ------ |
| y    | -    | 浮点数 |

**返回值**

​	若 `x >= y` 则为非零整数，否则为 `0`。

**注解**

​	若一或两个参数为 NaN，则内建的 `operator>=` 对浮点数可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。此宏是 `operator>=` 的“安静”版本。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("isgreaterequal(2.0,1.0)      = %d\n", isgreaterequal(2.0, 1.0));
    printf("isgreaterequal(1.0,2.0)      = %d\n", isgreaterequal(1.0, 2.0));
    printf("isgreaterequal(1.0,1.0)      = %d\n", isgreaterequal(1.0, 1.0));
    printf("isgreaterequal(INFINITY,1.0) = %d\n", isgreaterequal(INFINITY, 1.0));
    printf("isgreaterequal(1.0,NAN)      = %d\n", isgreaterequal(1.0, NAN));
 
    return 0;
}
```

​	可能的输出：

```txt
isgreaterequal(2.0,1.0)      = 1
isgreaterequal(1.0,2.0)      = 0
isgreaterequal(1.0,1.0)      = 1
isgreaterequal(INFINITY,1.0) = 1
isgreaterequal(1.0,NAN)      = 0
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.14.2 The isgreaterequal macro （第 TBD 页）

  - F.10.11 Comparison macros （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.14.2 The isgreaterequal macro （第 TBD 页）

  - F.10.11 Comparison macros （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.14.2 The isgreaterequal macro （第 259-260 页）

  - F.10.11 Comparison macros （第 531 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.14.2 The isgreaterequal macro （第 240-241 页）

**参阅**

| [islessequal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/islessequal) | 检查第一个浮点数实参是否小于或等于第二个 (宏函数) |
| ------------------------------------------------------------ | ------------------------------------------------- |
| **isgreaterequal** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/isgreaterequal)** |                                                   |





### isinf

原址：[https://zh.cppreference.com/w/c/numeric/math/isinf](https://zh.cppreference.com/w/c/numeric/math/isinf)

作用：检查给定数是否是无穷大   (宏函数)

备注：
```c
// 在标头 <math.h> 定义
#define isinf(arg) /* 由实现定义 */// (C99 起)
```

​	确定给定的浮点数 `arg` 是否正或负无穷大。该宏返回整数。

​	忽略 [FLT_EVAL_METHOD](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD)：即使以多于实参类型的范围和精度对它求值，首先仍将它转换到其语义类型，然后分类基于该类型。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若 `arg` 拥有无穷大值则为返回非零整数，否则返回 `0` 。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <float.h>
 
int main(void)
{
    printf("isinf(NAN)         = %d\n", isinf(NAN));
    printf("isinf(INFINITY)    = %d\n", isinf(INFINITY));
    printf("isinf(0.0)         = %d\n", isinf(0.0));
    printf("isinf(DBL_MIN/2.0) = %d\n", isinf(DBL_MIN/2.0));
    printf("isinf(1.0)         = %d\n", isinf(1.0));
    printf("isinf(exp(800))    = %d\n", isinf(exp(800)));
}
```

​	可能的输出：

```txt
isinf(NAN)         = 0
isinf(INFINITY)    = 1
isinf(0.0)         = 0
isinf(DBL_MIN/2.0) = 0
isinf(1.0)         = 0
isinf(exp(800))    = 1
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.3.3 The isinf macro （第 236 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.3.3 The isinf macro （第 217 页）

**参阅**

| [fpclassify (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fpclassify) | 对给定的浮点数分类 (宏函数)       |
| ------------------------------------------------------------ | --------------------------------- |
| [isfinite (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isfinite) | 检查给定数是否具有有限值 (宏函数) |
| [isnan (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isnan) | 检查给定数是否为 NaN (宏函数)     |
| [isnormal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isnormal) | 检查给定数是否正规 (宏函数)       |
| **isinf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/isinf)** |                                   |





### isless

原址：[https://zh.cppreference.com/w/c/numeric/math/isless](https://zh.cppreference.com/w/c/numeric/math/isless)

作用：检查第一个浮点数实参是否小于第二个  (宏函数)

备注：
```c
// 在标头 <math.h> 定义
#define isless(x, y) /* 由实现定义 */// (C99 起)
```

​	确定浮点数 `x` 是否小于浮点数 `y`，而不设置浮点数异常。

**参数**

| x    | -    | 浮点数 |
| ---- | ---- | ------ |
| y    | -    | 浮点数 |

**返回值**

​	若 `x < y` 则为非零整数，否则为 `0`。

**注解**

​	若一或两个实参为 NaN，则内建的 `operator<` 对浮点数可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。此宏是 `operator<` 的“安静”版本。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("isless(2.0,1.0)      = %d\n", isless(2.0, 1.0));
    printf("isless(1.0,2.0)      = %d\n", isless(1.0, 2.0));
    printf("isless(INFINITY,1.0) = %d\n", isless(INFINITY, 1.0));
    printf("isless(1.0,NAN)      = %d\n", isless(1.0, NAN));
 
    return 0;
}
```

​	可能的输出：

```txt
isless(2.0,1.0)      = 0
isless(1.0,2.0)      = 1
isless(INFINITY,1.0) = 0
isless(1.0,NAN)      = 0
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.14.3 The isless macro （第 TBD 页）

  - F.10.11 Comparison macros （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.14.3 The isless macro （第 TBD 页）

  - F.10.11 Comparison macros （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.14.3 The isless macro （第 260 页）

  - F.10.11 Comparison macros （第 531 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.14.3 The isless macro （第 241 页）

**参阅**

| [isgreater (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isgreater) | 检查第一个浮点数实参是否大于第二个 (宏函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| **isless** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/isless)** |                                             |





### islessequal

原址：[https://zh.cppreference.com/w/c/numeric/math/islessequal](https://zh.cppreference.com/w/c/numeric/math/islessequal)

作用：检查第一个浮点数实参是否小于或等于第二个  (宏函数)

备注：
```c
// 在标头 <math.h> 定义
#define islessequal(x, y) /* 由实现定义 */// (C99 起)
```

​	确定浮点数 `x` 是否小于或等于浮点数 `y`，而不设置浮点数异常。

**参数**

| x    | -    | 浮点数 |
| ---- | ---- | ------ |
| y    | -    | 浮点数 |

**返回值**

​	若 `x <= y` 则为非零整数，否则为 `0`。

**注解**

​	若一或两个实参为 NaN，则内建的 `operator<=` 对浮点数可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。此宏是 `operator<=` 的“安静”版本。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("islessequal(2.0,1.0)      = %d\n", islessequal(2.0, 1.0));
    printf("islessequal(1.0,2.0)      = %d\n", islessequal(1.0, 2.0));
    printf("islessequal(1.0,1.0)      = %d\n", islessequal(1.0, 1.0));
    printf("islessequal(INFINITY,1.0) = %d\n", islessequal(INFINITY, 1.0));
    printf("islessequal(1.0,NAN)      = %d\n", islessequal(1.0, NAN));
 
    return 0;
}
```

​	可能的输出：

```txt
islessequal(2.0,1.0)      = 0
islessequal(1.0,2.0)      = 1
islessequal(1.0,1.0)      = 1
islessequal(INFINITY,1.0) = 0
islessequal(1.0,NAN)      = 0
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.14.4 The islessequal macro （第 TBD 页）

  - F.10.11 Comparison macros （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.14.4 The islessequal macro （第 TBD 页）

  - F.10.11 Comparison macros （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.14.4 The islessequal macro （第 260 页）

  - F.10.11 Comparison macros （第 531 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.14.4 The islessequal macro （第 241 页）

**参阅**

| [isgreaterequal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isgreaterequal) | 检查第一个浮点数实参是否大于等于第二个 (宏函数) |
| ------------------------------------------------------------ | ----------------------------------------------- |
| **islessequal** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/islessequal)** |                                                 |





### islessgreater

原址：[https://zh.cppreference.com/w/c/numeric/math/islessgreater](https://zh.cppreference.com/w/c/numeric/math/islessgreater)

作用：检查第一个浮点数实参是否小于或大于第二个  (宏函数)

备注：
```c
// 在标头 <math.h> 定义
#define islessgreater(x, y) /* 由实现定义 */// (C99 起)
```

​	确定浮点数 `x` 是否小于或大于浮点数 `y`，而不设置浮点数异常。

**参数**

| x    | -    | 浮点数 |
| ---- | ---- | ------ |
| y    | -    | 浮点数 |

**返回值**

​	若 `x < y || x > y` 则为非零整数，否则为 `0` 。

**注解**

​	若一或两个实参为 NaN，则内建的 `operator<` 和 `operator>` 可能对浮点数引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。此宏是表达式 `x < y || x > y` 的“安静”版本。宏不会对 x 和 y 求值两次。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("islessgreater(2.0,1.0)      = %d\n", islessgreater(2.0, 1.0));
    printf("islessgreater(1.0,2.0)      = %d\n", islessgreater(1.0, 2.0));
    printf("islessgreater(1.0,1.0)      = %d\n", islessgreater(1.0, 1.0));
    printf("islessgreater(INFINITY,1.0) = %d\n", islessgreater(INFINITY, 1.0));
    printf("islessgreater(1.0,NAN)      = %d\n", islessgreater(1.0, NAN));
 
    return 0;
}
```

​	可能的输出：

```txt
islessgreater(2.0,1.0)      = 1
islessgreater(1.0,2.0)      = 1
islessgreater(1.0,1.0)      = 0
islessgreater(INFINITY,1.0) = 1
islessgreater(1.0,NAN)      = 0
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.14.5 The islessgreater macro （第 TBD 页）

  - F.10.11 Comparison macros （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.14.5 The islessgreater macro （第 TBD 页）

  - F.10.11 Comparison macros （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.14.5 The islessgreater macro （第 261 页）

  - F.10.11 Comparison macros （第 531 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.14.5 The islessgreater macro （第 241-242 页）

**参阅**

| [isless (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isless) | 检查第一个浮点数实参是否小于第二个 (宏函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| [isgreater (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isgreater) | 检查第一个浮点数实参是否大于第二个 (宏函数) |
| **islessgreater** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/islessgreater)** |                                             |





### isnan

原址：[https://zh.cppreference.com/w/c/numeric/math/isnan](https://zh.cppreference.com/w/c/numeric/math/isnan)

作用：检查给定数是否为 NaN  (宏函数)

备注：
```c
// 在标头 <math.h> 定义
#define isnan(arg) /* 由实现定义 */// (C99 起)
```

​	确定给定的浮点数 `arg` 是否非数（NaN）值。该宏返回整数。

​	忽略 [FLT_EVAL_METHOD](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD)：即使以多于实参类型的范围和精度对它求值，首先仍将它转换到其语义类型，然后分类基于该类型。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若 `arg` 为 NaN 则为非零整数，否则为 `0`。

**注解**

​	有多个拥有不同符号位和载荷的不同 NaN 值，参阅 [nan](https://zh.cppreference.com/w/c/numeric/math/nan)。

​	NaN 值决不与自身或其他 NaN 值比较相等。复制 NaN 可能改变其位模式。

​	另一种测试浮点数是否 NaN 的方式是与自身比较：`bool is_nan(double x) { return x != x; }`。

**示例**

```c
#include <float.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("isnan(NAN)         = %d\n", isnan(NAN));
    printf("isnan(INFINITY)    = %d\n", isnan(INFINITY));
    printf("isnan(0.0)         = %d\n", isnan(0.0));
    printf("isnan(DBL_MIN/2.0) = %d\n", isnan(DBL_MIN / 2.0));
    printf("isnan(0.0 / 0.0)   = %d\n", isnan(0.0 / 0.0));
    printf("isnan(Inf - Inf)   = %d\n", isnan(INFINITY - INFINITY));
}
```

​	可能的输出：

```txt
isnan(NAN)         = 1
isnan(INFINITY)    = 0
isnan(0.0)         = 0
isnan(DBL_MIN/2.0) = 0
isnan(0.0 / 0.0)   = 1
isnan(Inf - Inf)   = 1
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.3.4 The isnan macro （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.3.4 The isnan macro （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.3.4 The isnan macro （第 236-237 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.3.4 The isnan macro （第 217 页）

**参阅**

| [nan (C99)<br />nanf (C99)<br />nanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/nan) | 返回 NaN（非数） (函数)           |
| ------------------------------------------------------------ | --------------------------------- |
| [fpclassify (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fpclassify) | 对给定的浮点数分类 (宏函数)       |
| [isfinite (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isfinite) | 检查给定数是否具有有限值 (宏函数) |
| [isinf (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isinf) | 检查给定数是否是无穷大 (宏函数)   |
| [isnormal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isnormal) | 检查给定数是否正规 (宏函数)       |
| [isunordered (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isunordered) | 检查两个浮点数是否无序 (宏函数)   |
| **isnan** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/isnan)** |                                   |





### isnormal

原址：[https://zh.cppreference.com/w/c/numeric/math/isnormal](https://zh.cppreference.com/w/c/numeric/math/isnormal)

作用：检查给定数是否正规   (宏函数)

备注：
```c
// 在标头 <math.h> 定义
#define isnormal(arg) /* 由实现定义 */// (C99 起)
```

​	确定给定的浮点数 `arg` 是否正规，即它不是零、非正规、无穷大或 `NaN`。该宏返回整数。

​	忽略 [FLT_EVAL_METHOD](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD)：即使以多于实参类型的范围和精度对它求值，首先仍将它转换到其语义类型，然后分类基于该类型。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若 `arg` 正规则为非零整数，否则为 `0`。

**示例**

```c
#include <float.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("isnormal(NAN)         = %d\n", isnormal(NAN));
    printf("isnormal(INFINITY)    = %d\n", isnormal(INFINITY));
    printf("isnormal(0.0)         = %d\n", isnormal(0.0));
    printf("isnormal(DBL_MIN/2.0) = %d\n", isnormal(DBL_MIN / 2.0));
    printf("isnormal(1.0)         = %d\n", isnormal(1.0));
}
```

​	输出：

```txt
isnormal(NAN)         = 0
isnormal(INFINITY)    = 0
isnormal(0.0)         = 0
isnormal(DBL_MIN/2.0) = 0
isnormal(1.0)         = 1
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.3.5 The isnormal macro （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.3.5 The isnormal macro （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.3.5 The isnormal macro （第 237 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.3.5 The isnormal macro （第 217-218 页）

**参阅**

| [fpclassify (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fpclassify) | 对给定的浮点数分类 (宏函数)       |
| ------------------------------------------------------------ | --------------------------------- |
| [isfinite (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isfinite) | 检查给定数是否具有有限值 (宏函数) |
| [isinf (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isinf) | 检查给定数是否是无穷大 (宏函数)   |
| [isnan (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isnan) | 检查给定数是否为 NaN (宏函数)     |
| **isnormal** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/isnormal)** |                                   |





### isunordered

原址：[https://zh.cppreference.com/w/c/numeric/math/isunordered](https://zh.cppreference.com/w/c/numeric/math/isunordered)

作用：检查两个浮点数是否无序  (宏函数)

备注：
```c
// 在标头 <math.h> 定义
#define isunordered(x, y) /* 由实现定义 */// (C99 起)
```

​	确定浮点数 `x` 与 `y` 是否无序，即一或两个是 NaN，从而无法有意义地彼此比较。

**参数**

| x    | -    | 浮点数 |
| ---- | ---- | ------ |
| y    | -    | 浮点数 |

**返回值**

​	若 `x` 或 `y` 为 NaN 则为非零整数，否则为 `0`。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("isunordered(NAN,1.0) = %d\n", isunordered(NAN, 1.0));
    printf("isunordered(1.0,NAN) = %d\n", isunordered(1.0, NAN));
    printf("isunordered(NAN,NAN) = %d\n", isunordered(NAN, NAN));
    printf("isunordered(1.0,0.0) = %d\n", isunordered(1.0, 0.0));
 
    return 0;
}
```

​	可能的输出：

```txt
isunordered(NAN,1.0) = 1
isunordered(1.0,NAN) = 1
isunordered(NAN,NAN) = 1
isunordered(1.0,0.0) = 0
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.14.6 The isunordered macro （第 TBD 页）

  - F.10.11 Comparison macros （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.14.6 The isunordered macro （第 TBD 页）

  - F.10.11 Comparison macros （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.14.6 The isunordered macro （第 261 页）

  - F.10.11 Comparison macros （第 531 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.14.6 The isunordered macro （第 242 页）

**参阅**

| [fpclassify (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fpclassify) | 对给定的浮点数分类 (宏函数)   |
| ------------------------------------------------------------ | ----------------------------- |
| [isnan (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isnan) | 检查给定数是否为 NaN (宏函数) |
| **isunordered** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/isunordered)** |                               |





### math_errhandling

原址：[https://zh.cppreference.com/w/c/numeric/math/math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling)

作用：定义用于常用数学函数的错误处理机制   (宏常量)

备注：
```c
// 在标头 <math.h> 定义
#define MATH_ERRNO        1// (C99 起)
#define MATH_ERREXCEPT    2// (C99 起)
#define math_errhandling  /* 由实现定义 */// (C99 起)
```

​	宏常量 `math_errhandling` 展开成 `int` 类型的表达式，要么等于 `MATH_ERRNO`，要么等于 `MATH_ERREXCEPT`，要么等于其逐位或（`MATH_ERRNO | MATH_ERREXCEPT`）。

​	`math_errhandling` 的值指示浮点数运算符和[函数](https://zh.cppreference.com/w/c/numeric/math)所进行的错误处理：

| 常量             | 解释                                                         |
| ---------------- | ------------------------------------------------------------ |
| `MATH_ERREXCEPT` | 指示使用浮点数异常：`<fenv.h>` 中至少定义了 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)、[FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 及 [FE_OVERFLOW](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。 |
| `MATH_ERRNO`     | 指明浮点数运算使用变量 [errno](https://zh.cppreference.com/w/c/error/errno) 报告错误。 |

​	若实现支持 IEEE 浮点数算术（IEC 60559），则要求 `math_errhandling & MATH_ERREXCEPT` 非零。

​	识别下列浮点数错误条件：

|        条件        |                             解释                             |                            errno                             |                          浮点数异常                          |                             示例                             |
| :----------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|     定义域错误     | 实参在该运算的数学上的定义域之外（[每个函数](https://zh.cppreference.com/w/c/numeric/math)的描述列出了要求的定义域错误） |  [EDOM](https://zh.cppreference.com/w/c/error/errno_macros)  | [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) | `[acos](http://zh.cppreference.com/w/c/numeric/math/acos)(2)` |
|      极点错误      |               函数的数学结果恰是无限大或未定义               | [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros) | [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) | `[log](http://zh.cppreference.com/w/c/numeric/math/log)(0.0)`、`1.0/0.0` |
| 上溢所致的值域错误 | 数学结果有限，但舍入后变为无限，或在向下舍入后变成最大可表示有限值 | [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros) | [FE_OVERFLOW](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) | `[pow](http://zh.cppreference.com/w/c/numeric/math/pow)([DBL_MAX](http://zh.cppreference.com/w/c/types/limits),2)` |
| 下溢所致的值域错误 |     结果非零，但因为舍入变为零，或变成非正规并有精度损失     | [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros) 或不改变（实现定义） | [FE_UNDERFLOW](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 或无（实现定义） |                       `DBL_TRUE_MIN/2`                       |
|     结果不准确     |                   结果必须被舍入到目标类型                   |                            不改变                            | [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)或无（未指定） | `[sqrt](http://zh.cppreference.com/w/c/numeric/math/sqrt)(2)`、`1.0/10.0` |

**注意**

​	通常，[FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 是否为数学库函数所引发是未指定的，但这可以显式指定于函数的描述（例如 [rint](https://zh.cppreference.com/w/c/numeric/math/rint) vs [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint)）。

​	C99 前，浮点数异常是未指定的，要求对于任何定义于错误发生 `[EDOM](http://zh.cppreference.com/w/c/error/errno_macros)`，要求对上溢和实现定义的下溢发生 `[ERANGE](http://zh.cppreference.com/w/c/error/errno_macros)`。

**示例**

```c
#include <stdio.h>
#include <fenv.h>
#include <math.h>
#include <errno.h>
#pragma STDC FENV_ACCESS ON
int main(void)
{
    printf("MATH_ERRNO is %s\n", math_errhandling & MATH_ERRNO ? "set" : "not set");
    printf("MATH_ERREXCEPT is %s\n",
           math_errhandling & MATH_ERREXCEPT ? "set" : "not set");
    feclearexcept(FE_ALL_EXCEPT);
    errno = 0;
    printf("log(0) = %f\n", log(0));
    if(errno == ERANGE)
        perror("errno == ERANGE");
    if(fetestexcept(FE_DIVBYZERO))
        puts("FE_DIVBYZERO (pole error) reported");
}
```

​	可能的输出：

```txt
MATH_ERRNO is set
MATH_ERREXCEPT is set
log(0) = -inf
errno = ERANGE: Numerical result out of range
FE_DIVBYZERO (pole error) reported
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/9 MATH_ERRNO, MATH_ERREXCEPT, math_errhandling （第 170 页）

  - F.10/4 MATH_ERREXCEPT, math_errhandling （第 377 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/9 MATH_ERRNO, MATH_ERREXCEPT, math_errhandling （第 233 页）

  - F.10/4 MATH_ERREXCEPT, math_errhandling （第 517 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/9 MATH_ERRNO, MATH_ERREXCEPT, math_errhandling （第 214 页）

  - F.9/4 MATH_ERREXCEPT, math_errhandling> （第 454 页）

**参阅**

| [FE_ALL_EXCEPT (C99)<br />FE_DIVBYZERO (C99)<br />FE_INEXACT<br />FE_INVALID<br />FE_OVERFLOW<br />FE_UNDERFLOW<br />](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) | 浮点数异常 (宏常量)                              |
| ------------------------------------------------------------ | ------------------------------------------------ |
| [errno<br />](https://zh.cppreference.com/w/c/error/errno) | 展开成 POSIX 兼容的线程局域错误编号变量 (宏变量) |
| **math_errhandling** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/math_errhandling)** |                                                  |





### signbit

原址：[https://zh.cppreference.com/w/c/numeric/math/signbit](https://zh.cppreference.com/w/c/numeric/math/signbit)

作用：检查给定数是不是负数   (宏函数)

备注：
```c
// 在标头 <math.h> 定义
#define signbit( arg ) /* 由实现定义 */// (C99 起)
```

​	确定给定的浮点数 `arg` 是否为负。该宏返回整数。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若 `arg` 为负，则返回非零整数，否则返回 `0`。

**注解**

​	此宏检测零、无穷大和 NaN 的符号。这个宏和 [copysign](https://zh.cppreference.com/w/c/numeric/math/copysign) 是检验 NaN 符号的唯二可移植方式。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("signbit(+0.0) = %d\n", signbit(+0.0));
    printf("signbit(-0.0) = %d\n", signbit(-0.0));
}
```

​	可能的输出：

```txt
signbit(+0.0) = 0
signbit(-0.0) = 128
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.3.6 The signbit macro （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.3.6 The signbit macro （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.3.6 The signbit macro （第 237 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.3.6 The signbit macro （第 218 页）

**参阅**

| [fabs <br />fabsf (C99)<br />fabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fabs) | 计算浮点数的绝对值（\|x\|\|x\|） (函数)               |
| ------------------------------------------------------------ | ----------------------------------------------------- |
| [copysign (C99)<br />copysignf (C99)<br />copysignl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/copysign) | 从一个给定值的绝对值和另一个给定值的符号产生值 (函数) |
| **signbit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/signbit)** |                                                       |






## 函数



### acos

原址：[https://zh.cppreference.com/w/c/numeric/math/acos](https://zh.cppreference.com/w/c/numeric/math/acos)

作用：计算反余弦（{\small\arccos{x} }{\small\arccos{x} }arccos(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       acosf( float arg );// (1)(C99 起)
double      acos( double arg );// (2)
long double acosl( long double arg );// (3)(C99 起)
_Decimal32  acosd32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  acosd64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 acosd128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define acos( arg )// (7)(C99 起)
```

1-6) 计算 `arg` 的弧（反）余弦主值。

7） 泛型宏：若实参拥有 `long double` 类型，则调用 `acosl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `acos`。否则调用 `acosf`。若实参为复数，则宏调用对应的复数函数（`[cacosf](http://zh.cppreference.com/w/c/numeric/complex/cacos)`、`[cacos](http://zh.cppreference.com/w/c/numeric/complex/cacos)`、`[cacosl](http://zh.cppreference.com/w/c/numeric/complex/cacos)`）。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 于范围 *[0 ; π]* 中的弧（反）余弦（*arccos(arg)*）。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 在范围 `[-1.0; 1.0]` 外则出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 *+1*，则返回值 `+0`。
- 若 *|arg| > 1*，则返回定义域错误并返回 NaN。
- 若实参 NaN，则返回 NaN。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
#include <string.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
int main(void)
{
    printf("acos(-1) = %f\n", acos(-1));
    printf("acos(0.0) = %f 2*acos(0.0) = %f\n", acos(0), 2 * acos(0));
    printf("acos(0.5) = %f 3*acos(0.5) = %f\n", acos(0.5), 3 * acos(0.5));
    printf("acos(1) = %f\n", acos(1));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("acos(1.1) = %f\n", acos(1.1));
    if (errno == EDOM)
        perror("    errno == EDOM");
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
acos(-1) = 3.141593
acos(0.0) = 1.570796 2*acos(0.0) = 3.141593
acos(0.5) = 1.047198 3*acos(0.5) = 3.141593
acos(1) = 0.000000
acos(1.1) = nan
    errno == EDOM: Numerical argument out of domain
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.1 The acos functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.1 The acos functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.1 The acos functions （第 173 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.1 The acos functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.1 The acos functions （第 238 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.1 The acos functions （第 518 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.1 The acos functions （第 218 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.1 The acos functions （第 455 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.1 The acos function

**参阅**

| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡x） (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡x） (函数) |
| [atan2 <br />atan2f (C99)<br />atan2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan2) | 计算反正切，以符号确定象限 (函数)   |
| [cos <br />cosf (C99)<br />cosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cos) | 计算余弦（cosxcos⁡x） (函数)         |
| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数)               |
| **acos** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/acos)** |                                     |





### acosf

原址：[https://zh.cppreference.com/w/c/numeric/math/acos](https://zh.cppreference.com/w/c/numeric/math/acos)

作用：计算反余弦（{\small\arccos{x} }{\small\arccos{x} }arccos(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       acosf( float arg );// (1)(C99 起)
double      acos( double arg );// (2)
long double acosl( long double arg );// (3)(C99 起)
_Decimal32  acosd32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  acosd64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 acosd128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define acos( arg )// (7)(C99 起)
```

1-6) 计算 `arg` 的弧（反）余弦主值。

7） 泛型宏：若实参拥有 `long double` 类型，则调用 `acosl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `acos`。否则调用 `acosf`。若实参为复数，则宏调用对应的复数函数（`[cacosf](http://zh.cppreference.com/w/c/numeric/complex/cacos)`、`[cacos](http://zh.cppreference.com/w/c/numeric/complex/cacos)`、`[cacosl](http://zh.cppreference.com/w/c/numeric/complex/cacos)`）。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 于范围 *[0 ; π]* 中的弧（反）余弦（*arccos(arg)*）。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 在范围 `[-1.0; 1.0]` 外则出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 *+1*，则返回值 `+0`。
- 若 *|arg| > 1*，则返回定义域错误并返回 NaN。
- 若实参 NaN，则返回 NaN。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
#include <string.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
int main(void)
{
    printf("acos(-1) = %f\n", acos(-1));
    printf("acos(0.0) = %f 2*acos(0.0) = %f\n", acos(0), 2 * acos(0));
    printf("acos(0.5) = %f 3*acos(0.5) = %f\n", acos(0.5), 3 * acos(0.5));
    printf("acos(1) = %f\n", acos(1));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("acos(1.1) = %f\n", acos(1.1));
    if (errno == EDOM)
        perror("    errno == EDOM");
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
acos(-1) = 3.141593
acos(0.0) = 1.570796 2*acos(0.0) = 3.141593
acos(0.5) = 1.047198 3*acos(0.5) = 3.141593
acos(1) = 0.000000
acos(1.1) = nan
    errno == EDOM: Numerical argument out of domain
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.1 The acos functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.1 The acos functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.1 The acos functions （第 173 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.1 The acos functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.1 The acos functions （第 238 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.1 The acos functions （第 518 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.1 The acos functions （第 218 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.1 The acos functions （第 455 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.1 The acos function

**参阅**

| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡x） (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡x） (函数) |
| [atan2 <br />atan2f (C99)<br />atan2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan2) | 计算反正切，以符号确定象限 (函数)   |
| [cos <br />cosf (C99)<br />cosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cos) | 计算余弦（cosxcos⁡x） (函数)         |
| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数)               |
| **acos** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/acos)** |                                     |





### acosh

原址：[https://zh.cppreference.com/w/c/numeric/math/acosh](https://zh.cppreference.com/w/c/numeric/math/acosh)

作用：计算反双曲余弦（{\small\operatorname{arcosh}{x} }{\small\operatorname{arcosh}{x} }arcosh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       acoshf( float arg );// (1)(C99 起)
double      acosh( double arg );// (2)(C99 起)
long double acoshl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define acosh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的反双曲余弦。

4） 泛型宏：若参数拥有 `long double` 类型，则调用 `acoshl`。否则，若参数拥有整数类型或 `double` 类型，则调用 `acosh`。否则调用 `acoshf`。若参数为复数，则宏调用对应的复数函数（`[cacoshf](http://zh.cppreference.com/w/c/numeric/complex/cacosh)`、`[cacosh](http://zh.cppreference.com/w/c/numeric/complex/cacosh)`、`[cacoshl](http://zh.cppreference.com/w/c/numeric/complex/cacosh)`）。

**参数**

| arg  | -    | 表示双曲扇形面积的浮点数 |
| ---- | ---- | ------------------------ |
|      |      |                          |

**返回值**

​	若不出现错误，则返回 `arg` 在区间 *[0, +∞]* 上的反双曲余弦（*cosh-1
(arg)* 或 *arcosh(arg)*）。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实参小于 `1`，则出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参小于 1，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回 NaN
- 若实参为 1，则返回 +0
- 若实参为 +∞，则返回 +∞
- 若实参为 NaN，则返回 NaN

**注解**

​	虽然 C 标准命名此函数为“弧双曲余弦”，但双曲函数的反函数仍是面积函数。其实参是双曲扇形的面积，而非弧长。正确的名称是“反双曲余弦”（POSIX 所用）或“面积双曲余弦”。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("acosh(1) = %f\nacosh(10) = %f\n", acosh(1), acosh(10));
    printf("acosh(DBL_MAX) = %f\nacosh(Inf) = %f\n", acosh(DBL_MAX), acosh(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("acosh(0.5) = %f\n", acosh(0.5));
    if (errno == EDOM)
        perror("    errno == EDOM");
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
acosh(1) = 0.000000
acosh(10) = 2.993223
acosh(DBL_MAX) = 710.475860
acosh(Inf) = inf
acosh(0.5) = -nan
    errno == EDOM: Numerical argument out of domain
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.1 The acosh functions （第 TBD 页）

  - 7.27 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.1 The acosh functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.1 The acosh functions （第 175 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.2.1 The acosh functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.1 The acosh functions （第 240 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.1 The acosh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.1 The acosh functions （第 221 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.1 The acosh functions （第 457 页）

**参阅**

| [asinh (C99)<br />asinhf (C99)<br />asinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asinh) | 计算反双曲正弦（arsinhxarsinh⁡x） (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| [atanh (C99)<br />atanhf (C99)<br />atanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atanh) | 计算反双曲正切（artanhxartanh⁡x） (函数) |
| [cosh <br />coshf (C99)<br />coshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cosh) | 计算双曲余弦（coshxcosh⁡x） (函数)       |
| [cacosh (C99)<br />cacoshf (C99)<br />cacoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacosh) | 计算复数反双曲余弦 (函数)               |
| **acosh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/acosh)** |                                         |

**外部链接**

[Weisstein, Eric W. “反双曲余弦”](https://mathworld.wolfram.com/InverseHyperbolicCosine.html)来自 MathWorld--A Wolfram Web Resource。





### acoshf

原址：[https://zh.cppreference.com/w/c/numeric/math/acosh](https://zh.cppreference.com/w/c/numeric/math/acosh)

作用：计算反双曲余弦（{\small\operatorname{arcosh}{x} }{\small\operatorname{arcosh}{x} }arcosh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       acoshf( float arg );// (1)(C99 起)
double      acosh( double arg );// (2)(C99 起)
long double acoshl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define acosh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的反双曲余弦。

4） 泛型宏：若参数拥有 `long double` 类型，则调用 `acoshl`。否则，若参数拥有整数类型或 `double` 类型，则调用 `acosh`。否则调用 `acoshf`。若参数为复数，则宏调用对应的复数函数（`[cacoshf](http://zh.cppreference.com/w/c/numeric/complex/cacosh)`、`[cacosh](http://zh.cppreference.com/w/c/numeric/complex/cacosh)`、`[cacoshl](http://zh.cppreference.com/w/c/numeric/complex/cacosh)`）。

**参数**

| arg  | -    | 表示双曲扇形面积的浮点数 |
| ---- | ---- | ------------------------ |
|      |      |                          |

**返回值**

​	若不出现错误，则返回 `arg` 在区间 *[0, +∞]* 上的反双曲余弦（*cosh-1
(arg)* 或 *arcosh(arg)*）。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实参小于 `1`，则出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参小于 1，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回 NaN
- 若实参为 1，则返回 +0
- 若实参为 +∞，则返回 +∞
- 若实参为 NaN，则返回 NaN

**注解**

​	虽然 C 标准命名此函数为“弧双曲余弦”，但双曲函数的反函数仍是面积函数。其实参是双曲扇形的面积，而非弧长。正确的名称是“反双曲余弦”（POSIX 所用）或“面积双曲余弦”。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("acosh(1) = %f\nacosh(10) = %f\n", acosh(1), acosh(10));
    printf("acosh(DBL_MAX) = %f\nacosh(Inf) = %f\n", acosh(DBL_MAX), acosh(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("acosh(0.5) = %f\n", acosh(0.5));
    if (errno == EDOM)
        perror("    errno == EDOM");
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
acosh(1) = 0.000000
acosh(10) = 2.993223
acosh(DBL_MAX) = 710.475860
acosh(Inf) = inf
acosh(0.5) = -nan
    errno == EDOM: Numerical argument out of domain
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.1 The acosh functions （第 TBD 页）

  - 7.27 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.1 The acosh functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.1 The acosh functions （第 175 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.2.1 The acosh functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.1 The acosh functions （第 240 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.1 The acosh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.1 The acosh functions （第 221 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.1 The acosh functions （第 457 页）

**参阅**

| [asinh (C99)<br />asinhf (C99)<br />asinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asinh) | 计算反双曲正弦（arsinhxarsinh⁡x） (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| [atanh (C99)<br />atanhf (C99)<br />atanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atanh) | 计算反双曲正切（artanhxartanh⁡x） (函数) |
| [cosh <br />coshf (C99)<br />coshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cosh) | 计算双曲余弦（coshxcosh⁡x） (函数)       |
| [cacosh (C99)<br />cacoshf (C99)<br />cacoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacosh) | 计算复数反双曲余弦 (函数)               |
| **acosh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/acosh)** |                                         |

**外部链接**

[Weisstein, Eric W. “反双曲余弦”](https://mathworld.wolfram.com/InverseHyperbolicCosine.html)来自 MathWorld--A Wolfram Web Resource。





### acoshl

原址：[https://zh.cppreference.com/w/c/numeric/math/acosh](https://zh.cppreference.com/w/c/numeric/math/acosh)

作用：计算反双曲余弦（{\small\operatorname{arcosh}{x} }{\small\operatorname{arcosh}{x} }arcosh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       acoshf( float arg );// (1)(C99 起)
double      acosh( double arg );// (2)(C99 起)
long double acoshl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define acosh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的反双曲余弦。

4） 泛型宏：若参数拥有 `long double` 类型，则调用 `acoshl`。否则，若参数拥有整数类型或 `double` 类型，则调用 `acosh`。否则调用 `acoshf`。若参数为复数，则宏调用对应的复数函数（`[cacoshf](http://zh.cppreference.com/w/c/numeric/complex/cacosh)`、`[cacosh](http://zh.cppreference.com/w/c/numeric/complex/cacosh)`、`[cacoshl](http://zh.cppreference.com/w/c/numeric/complex/cacosh)`）。

**参数**

| arg  | -    | 表示双曲扇形面积的浮点数 |
| ---- | ---- | ------------------------ |
|      |      |                          |

**返回值**

​	若不出现错误，则返回 `arg` 在区间 *[0, +∞]* 上的反双曲余弦（*cosh-1
(arg)* 或 *arcosh(arg)*）。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实参小于 `1`，则出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参小于 1，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回 NaN
- 若实参为 1，则返回 +0
- 若实参为 +∞，则返回 +∞
- 若实参为 NaN，则返回 NaN

**注解**

​	虽然 C 标准命名此函数为“弧双曲余弦”，但双曲函数的反函数仍是面积函数。其实参是双曲扇形的面积，而非弧长。正确的名称是“反双曲余弦”（POSIX 所用）或“面积双曲余弦”。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("acosh(1) = %f\nacosh(10) = %f\n", acosh(1), acosh(10));
    printf("acosh(DBL_MAX) = %f\nacosh(Inf) = %f\n", acosh(DBL_MAX), acosh(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("acosh(0.5) = %f\n", acosh(0.5));
    if (errno == EDOM)
        perror("    errno == EDOM");
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
acosh(1) = 0.000000
acosh(10) = 2.993223
acosh(DBL_MAX) = 710.475860
acosh(Inf) = inf
acosh(0.5) = -nan
    errno == EDOM: Numerical argument out of domain
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.1 The acosh functions （第 TBD 页）

  - 7.27 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.1 The acosh functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.1 The acosh functions （第 175 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.2.1 The acosh functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.1 The acosh functions （第 240 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.1 The acosh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.1 The acosh functions （第 221 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.1 The acosh functions （第 457 页）

**参阅**

| [asinh (C99)<br />asinhf (C99)<br />asinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asinh) | 计算反双曲正弦（arsinhxarsinh⁡x） (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| [atanh (C99)<br />atanhf (C99)<br />atanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atanh) | 计算反双曲正切（artanhxartanh⁡x） (函数) |
| [cosh <br />coshf (C99)<br />coshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cosh) | 计算双曲余弦（coshxcosh⁡x） (函数)       |
| [cacosh (C99)<br />cacoshf (C99)<br />cacoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacosh) | 计算复数反双曲余弦 (函数)               |
| **acosh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/acosh)** |                                         |

**外部链接**

[Weisstein, Eric W. “反双曲余弦”](https://mathworld.wolfram.com/InverseHyperbolicCosine.html)来自 MathWorld--A Wolfram Web Resource。





### acosl

原址：[https://zh.cppreference.com/w/c/numeric/math/acos](https://zh.cppreference.com/w/c/numeric/math/acos)

作用：计算反余弦（{\small\arccos{x} }{\small\arccos{x} }arccos(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       acosf( float arg );// (1)(C99 起)
double      acos( double arg );// (2)
long double acosl( long double arg );// (3)(C99 起)
_Decimal32  acosd32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  acosd64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 acosd128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define acos( arg )// (7)(C99 起)
```

1-6) 计算 `arg` 的弧（反）余弦主值。

7） 泛型宏：若实参拥有 `long double` 类型，则调用 `acosl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `acos`。否则调用 `acosf`。若实参为复数，则宏调用对应的复数函数（`[cacosf](http://zh.cppreference.com/w/c/numeric/complex/cacos)`、`[cacos](http://zh.cppreference.com/w/c/numeric/complex/cacos)`、`[cacosl](http://zh.cppreference.com/w/c/numeric/complex/cacos)`）。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 于范围 *[0 ; π]* 中的弧（反）余弦（*arccos(arg)*）。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 在范围 `[-1.0; 1.0]` 外则出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 *+1*，则返回值 `+0`。
- 若 *|arg| > 1*，则返回定义域错误并返回 NaN。
- 若实参 NaN，则返回 NaN。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
#include <string.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
int main(void)
{
    printf("acos(-1) = %f\n", acos(-1));
    printf("acos(0.0) = %f 2*acos(0.0) = %f\n", acos(0), 2 * acos(0));
    printf("acos(0.5) = %f 3*acos(0.5) = %f\n", acos(0.5), 3 * acos(0.5));
    printf("acos(1) = %f\n", acos(1));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("acos(1.1) = %f\n", acos(1.1));
    if (errno == EDOM)
        perror("    errno == EDOM");
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
acos(-1) = 3.141593
acos(0.0) = 1.570796 2*acos(0.0) = 3.141593
acos(0.5) = 1.047198 3*acos(0.5) = 3.141593
acos(1) = 0.000000
acos(1.1) = nan
    errno == EDOM: Numerical argument out of domain
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.1 The acos functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.1 The acos functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.1 The acos functions （第 173 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.1 The acos functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.1 The acos functions （第 238 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.1 The acos functions （第 518 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.1 The acos functions （第 218 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.1 The acos functions （第 455 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.1 The acos function

**参阅**

| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡x） (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡x） (函数) |
| [atan2 <br />atan2f (C99)<br />atan2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan2) | 计算反正切，以符号确定象限 (函数)   |
| [cos <br />cosf (C99)<br />cosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cos) | 计算余弦（cosxcos⁡x） (函数)         |
| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数)               |
| **acos** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/acos)** |                                     |





### asin

原址：[https://zh.cppreference.com/w/c/numeric/math/asin](https://zh.cppreference.com/w/c/numeric/math/asin)

作用：计算反正弦（{\small\arcsin{x} }{\small\arcsin{x} }arcsin(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       asinf( float arg );// (1)(C99 起)
double      asin( double arg );// (2)
long double asinl( long double arg );// (3)(C99 起)
_Decimal32  asind32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  asind64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 asind128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define asin( arg )// (7)(C99 起)
```

1-6) 计算 `arg` 的弧（反）正弦主值。

7） 泛型宏：若实参拥有 `long double` 类型，则调用 (3) `asinl`。否则，若实参拥有整数类型或 `double` 类型，则调用 (2) `asin`。否则调用 (1) `asinf`。若实参为复数，则宏调用对应的复数函数（`[casinf](http://zh.cppreference.com/w/c/numeric/complex/casin)`、`[casin](http://zh.cppreference.com/w/c/numeric/complex/casin)`、`[casinl](http://zh.cppreference.com/w/c/numeric/complex/casin)`）。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

若不出现错误，则返回 `arg` 在范围 

[-

| π    |
| ---- |
| 2    |

 ; +

| π    |
| ---- |
| 2    |

]

 中的弧（反）正弦（*arcsin(arg)*）。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 在范围 `[-1.0; 1.0]` 外则出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 ±0，则返回未修改的实参。
- 若 *|arg| > 1*，则出现定义域错误并返回 NaN。
- 若实参为 NaN，则返回 NaN。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
#include <string.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
int main(void)
{
    printf("asin( 1.0) = %+f, 2*asin( 1.0)=%+f\n", asin(1), 2 * asin(1));
    printf("asin(-0.5) = %+f, 6*asin(-0.5)=%+f\n", asin(-0.5), 6 * asin(-0.5));
 
    // 特殊值
    printf("asin(0.0) = %1f, asin(-0.0)=%f\n", asin(+0.0), asin(-0.0));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("asin(1.1) = %f\n", asin(1.1));
    if (errno == EDOM)
        perror("    errno == EDOM");
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
asin( 1.0) = +1.570796, 2*asin( 1.0)=+3.141593
asin(-0.5) = -0.523599, 6*asin(-0.5)=-3.141593
asin(0.0) = 0.000000, asin(-0.0)=-0.000000
asin(1.1) = nan
    errno == EDOM: Numerical argument out of domain
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.2 The asin functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.2 The asin functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.2 The asin functions （第 174 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.2 The asin functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.2 The asin functions （第 238 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.2 The asin functions （第 518 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.2 The asin functions （第 219 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.2 The asin functions （第 456 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.2 The asin function

**参阅**

| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡x） (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡x） (函数) |
| [atan2 <br />atan2f (C99)<br />atan2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan2) | 计算反正切，以符号确定象限 (函数)   |
| [sin <br />sinf (C99)<br />sinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sin) | 计算正弦（sinxsin⁡x） (函数)         |
| [casin (C99)<br />casinf (C99)<br />casinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casin) | 计算复数反正弦 (函数)               |
| **asin** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/asin)** |                                     |





### asinf

原址：[https://zh.cppreference.com/w/c/numeric/math/asin](https://zh.cppreference.com/w/c/numeric/math/asin)

作用：计算反正弦（{\small\arcsin{x} }{\small\arcsin{x} }arcsin(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       asinf( float arg );// (1)(C99 起)
double      asin( double arg );// (2)
long double asinl( long double arg );// (3)(C99 起)
_Decimal32  asind32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  asind64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 asind128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define asin( arg )// (7)(C99 起)
```

1-6) 计算 `arg` 的弧（反）正弦主值。

7） 泛型宏：若实参拥有 `long double` 类型，则调用 (3) `asinl`。否则，若实参拥有整数类型或 `double` 类型，则调用 (2) `asin`。否则调用 (1) `asinf`。若实参为复数，则宏调用对应的复数函数（`[casinf](http://zh.cppreference.com/w/c/numeric/complex/casin)`、`[casin](http://zh.cppreference.com/w/c/numeric/complex/casin)`、`[casinl](http://zh.cppreference.com/w/c/numeric/complex/casin)`）。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

若不出现错误，则返回 `arg` 在范围 

[-

| π    |
| ---- |
| 2    |

 ; +

| π    |
| ---- |
| 2    |

]

 中的弧（反）正弦（*arcsin(arg)*）。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 在范围 `[-1.0; 1.0]` 外则出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 ±0，则返回未修改的实参。
- 若 *|arg| > 1*，则出现定义域错误并返回 NaN。
- 若实参为 NaN，则返回 NaN。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
#include <string.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
int main(void)
{
    printf("asin( 1.0) = %+f, 2*asin( 1.0)=%+f\n", asin(1), 2 * asin(1));
    printf("asin(-0.5) = %+f, 6*asin(-0.5)=%+f\n", asin(-0.5), 6 * asin(-0.5));
 
    // 特殊值
    printf("asin(0.0) = %1f, asin(-0.0)=%f\n", asin(+0.0), asin(-0.0));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("asin(1.1) = %f\n", asin(1.1));
    if (errno == EDOM)
        perror("    errno == EDOM");
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
asin( 1.0) = +1.570796, 2*asin( 1.0)=+3.141593
asin(-0.5) = -0.523599, 6*asin(-0.5)=-3.141593
asin(0.0) = 0.000000, asin(-0.0)=-0.000000
asin(1.1) = nan
    errno == EDOM: Numerical argument out of domain
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.2 The asin functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.2 The asin functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.2 The asin functions （第 174 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.2 The asin functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.2 The asin functions （第 238 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.2 The asin functions （第 518 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.2 The asin functions （第 219 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.2 The asin functions （第 456 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.2 The asin function

**参阅**

| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡x） (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡x） (函数) |
| [atan2 <br />atan2f (C99)<br />atan2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan2) | 计算反正切，以符号确定象限 (函数)   |
| [sin <br />sinf (C99)<br />sinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sin) | 计算正弦（sinxsin⁡x） (函数)         |
| [casin (C99)<br />casinf (C99)<br />casinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casin) | 计算复数反正弦 (函数)               |
| **asin** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/asin)** |                                     |





### asinh

原址：[https://zh.cppreference.com/w/c/numeric/math/asinh](https://zh.cppreference.com/w/c/numeric/math/asinh)

作用：计算反双曲正弦（{\small\operatorname{arsinh}{x} }{\small\operatorname{arsinh}{x} }arsinh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       asinhf( float arg );// (1)(C99 起)
double      asinh( double arg );// (2)(C99 起)
long double asinhl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define asinh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的反双曲正弦。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `asinhl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `asinh`。否则调用 `asinhf`。若实参为复数，则宏调用对应的复数函数（[casinhf](https://zh.cppreference.com/w/c/numeric/complex/casinh)、[casinh](https://zh.cppreference.com/w/c/numeric/complex/casinh)、[casinhl](https://zh.cppreference.com/w/c/numeric/complex/casinh)）。

**参数**

| arg  | -    | 表示双曲扇形面积的浮点数 |
| ---- | ---- | ------------------------ |
|      |      |                          |

**返回值**

​	若不发生错误，则返回 `arg` 的反双曲正弦（*sinh-1
(arg)* 或 *arsinh(arg)*）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0 或 ±∞，则返回不修改的参数
- 若参数为 NaN，则返回 NaN

**注解**

​	虽然 C 标准命名此函数为“弧双曲正弦”，但双曲函数的反函数仍是面积函数。其实参为双曲扇形的面积，而非弧长。正确的名称是“反双曲正弦”（ POSIX 所用）或“面积双曲正弦”。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("asinh(1) = %f\nasinh(-1) = %f\n", asinh(1), asinh(-1));
    // 特殊值
    printf("asinh(+0) = %f\nasinh(-0) = %f\n", asinh(0.0), asinh(-0.0));
}
```

​	输出：

```txt
asinh(1) = 0.881374
asinh(-1) = -0.881374
asinh(+0) = 0.000000
asinh(-0) = -0.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.2 The asinh functions （第 240-241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.2 The asinh functions （第 520 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.2 The asinh functions （第 240-241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.2 The asinh functions （第 520 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.2 The asinh functions （第 240-241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.2 The asinh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.2 The asinh functions （第 221 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.2 The asinh functions （第 457 页）

**参阅**

| [acosh (C99)<br />acoshf (C99)<br />acoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acosh) | 计算反双曲余弦（arcoshxarcosh⁡x） (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| [atanh (C99)<br />atanhf (C99)<br />atanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atanh) | 计算反双曲正切（artanhxartanh⁡x） (函数) |
| [sinh <br />sinhf (C99)<br />sinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sinh) | 计算双曲正弦（sinhxsinh⁡x） (函数)       |
| [casinh (C99)<br />casinhf (C99)<br />casinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casinh) | 计算复数反双曲正弦 (函数)               |
| **asinh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/asinh)** |                                         |

**外部链接**

[Weisstein, Eric W. “反双曲正弦”](https://mathworld.wolfram.com/InverseHyperbolicSine.html)来自 MathWorld--A Wolfram Web Resource 。





### asinhf

原址：[https://zh.cppreference.com/w/c/numeric/math/asinh](https://zh.cppreference.com/w/c/numeric/math/asinh)

作用：计算反双曲正弦（{\small\operatorname{arsinh}{x} }{\small\operatorname{arsinh}{x} }arsinh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       asinhf( float arg );// (1)(C99 起)
double      asinh( double arg );// (2)(C99 起)
long double asinhl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define asinh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的反双曲正弦。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `asinhl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `asinh`。否则调用 `asinhf`。若实参为复数，则宏调用对应的复数函数（[casinhf](https://zh.cppreference.com/w/c/numeric/complex/casinh)、[casinh](https://zh.cppreference.com/w/c/numeric/complex/casinh)、[casinhl](https://zh.cppreference.com/w/c/numeric/complex/casinh)）。

**参数**

| arg  | -    | 表示双曲扇形面积的浮点数 |
| ---- | ---- | ------------------------ |
|      |      |                          |

**返回值**

​	若不发生错误，则返回 `arg` 的反双曲正弦（*sinh-1
(arg)* 或 *arsinh(arg)*）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0 或 ±∞，则返回不修改的参数
- 若参数为 NaN，则返回 NaN

**注解**

​	虽然 C 标准命名此函数为“弧双曲正弦”，但双曲函数的反函数仍是面积函数。其实参为双曲扇形的面积，而非弧长。正确的名称是“反双曲正弦”（ POSIX 所用）或“面积双曲正弦”。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("asinh(1) = %f\nasinh(-1) = %f\n", asinh(1), asinh(-1));
    // 特殊值
    printf("asinh(+0) = %f\nasinh(-0) = %f\n", asinh(0.0), asinh(-0.0));
}
```

​	输出：

```txt
asinh(1) = 0.881374
asinh(-1) = -0.881374
asinh(+0) = 0.000000
asinh(-0) = -0.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.2 The asinh functions （第 240-241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.2 The asinh functions （第 520 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.2 The asinh functions （第 240-241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.2 The asinh functions （第 520 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.2 The asinh functions （第 240-241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.2 The asinh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.2 The asinh functions （第 221 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.2 The asinh functions （第 457 页）

**参阅**

| [acosh (C99)<br />acoshf (C99)<br />acoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acosh) | 计算反双曲余弦（arcoshxarcosh⁡x） (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| [atanh (C99)<br />atanhf (C99)<br />atanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atanh) | 计算反双曲正切（artanhxartanh⁡x） (函数) |
| [sinh <br />sinhf (C99)<br />sinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sinh) | 计算双曲正弦（sinhxsinh⁡x） (函数)       |
| [casinh (C99)<br />casinhf (C99)<br />casinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casinh) | 计算复数反双曲正弦 (函数)               |
| **asinh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/asinh)** |                                         |

**外部链接**

[Weisstein, Eric W. “反双曲正弦”](https://mathworld.wolfram.com/InverseHyperbolicSine.html)来自 MathWorld--A Wolfram Web Resource 。





### asinhl

原址：[https://zh.cppreference.com/w/c/numeric/math/asinh](https://zh.cppreference.com/w/c/numeric/math/asinh)

作用：计算反双曲正弦（{\small\operatorname{arsinh}{x} }{\small\operatorname{arsinh}{x} }arsinh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       asinhf( float arg );// (1)(C99 起)
double      asinh( double arg );// (2)(C99 起)
long double asinhl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define asinh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的反双曲正弦。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `asinhl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `asinh`。否则调用 `asinhf`。若实参为复数，则宏调用对应的复数函数（[casinhf](https://zh.cppreference.com/w/c/numeric/complex/casinh)、[casinh](https://zh.cppreference.com/w/c/numeric/complex/casinh)、[casinhl](https://zh.cppreference.com/w/c/numeric/complex/casinh)）。

**参数**

| arg  | -    | 表示双曲扇形面积的浮点数 |
| ---- | ---- | ------------------------ |
|      |      |                          |

**返回值**

​	若不发生错误，则返回 `arg` 的反双曲正弦（*sinh-1
(arg)* 或 *arsinh(arg)*）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0 或 ±∞，则返回不修改的参数
- 若参数为 NaN，则返回 NaN

**注解**

​	虽然 C 标准命名此函数为“弧双曲正弦”，但双曲函数的反函数仍是面积函数。其实参为双曲扇形的面积，而非弧长。正确的名称是“反双曲正弦”（ POSIX 所用）或“面积双曲正弦”。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("asinh(1) = %f\nasinh(-1) = %f\n", asinh(1), asinh(-1));
    // 特殊值
    printf("asinh(+0) = %f\nasinh(-0) = %f\n", asinh(0.0), asinh(-0.0));
}
```

​	输出：

```txt
asinh(1) = 0.881374
asinh(-1) = -0.881374
asinh(+0) = 0.000000
asinh(-0) = -0.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.2 The asinh functions （第 240-241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.2 The asinh functions （第 520 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.2 The asinh functions （第 240-241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.2 The asinh functions （第 520 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.2 The asinh functions （第 240-241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.2 The asinh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.2 The asinh functions （第 221 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.2 The asinh functions （第 457 页）

**参阅**

| [acosh (C99)<br />acoshf (C99)<br />acoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acosh) | 计算反双曲余弦（arcoshxarcosh⁡x） (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| [atanh (C99)<br />atanhf (C99)<br />atanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atanh) | 计算反双曲正切（artanhxartanh⁡x） (函数) |
| [sinh <br />sinhf (C99)<br />sinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sinh) | 计算双曲正弦（sinhxsinh⁡x） (函数)       |
| [casinh (C99)<br />casinhf (C99)<br />casinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casinh) | 计算复数反双曲正弦 (函数)               |
| **asinh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/asinh)** |                                         |

**外部链接**

[Weisstein, Eric W. “反双曲正弦”](https://mathworld.wolfram.com/InverseHyperbolicSine.html)来自 MathWorld--A Wolfram Web Resource 。





### asinl

原址：[https://zh.cppreference.com/w/c/numeric/math/asin](https://zh.cppreference.com/w/c/numeric/math/asin)

作用：计算反正弦（{\small\arcsin{x} }{\small\arcsin{x} }arcsin(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       asinf( float arg );// (1)(C99 起)
double      asin( double arg );// (2)
long double asinl( long double arg );// (3)(C99 起)
_Decimal32  asind32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  asind64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 asind128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define asin( arg )// (7)(C99 起)
```

1-6) 计算 `arg` 的弧（反）正弦主值。

7） 泛型宏：若实参拥有 `long double` 类型，则调用 (3) `asinl`。否则，若实参拥有整数类型或 `double` 类型，则调用 (2) `asin`。否则调用 (1) `asinf`。若实参为复数，则宏调用对应的复数函数（`[casinf](http://zh.cppreference.com/w/c/numeric/complex/casin)`、`[casin](http://zh.cppreference.com/w/c/numeric/complex/casin)`、`[casinl](http://zh.cppreference.com/w/c/numeric/complex/casin)`）。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

若不出现错误，则返回 `arg` 在范围 

[-

| π    |
| ---- |
| 2    |

 ; +

| π    |
| ---- |
| 2    |

]

 中的弧（反）正弦（*arcsin(arg)*）。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 在范围 `[-1.0; 1.0]` 外则出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 ±0，则返回未修改的实参。
- 若 *|arg| > 1*，则出现定义域错误并返回 NaN。
- 若实参为 NaN，则返回 NaN。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
#include <string.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
int main(void)
{
    printf("asin( 1.0) = %+f, 2*asin( 1.0)=%+f\n", asin(1), 2 * asin(1));
    printf("asin(-0.5) = %+f, 6*asin(-0.5)=%+f\n", asin(-0.5), 6 * asin(-0.5));
 
    // 特殊值
    printf("asin(0.0) = %1f, asin(-0.0)=%f\n", asin(+0.0), asin(-0.0));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("asin(1.1) = %f\n", asin(1.1));
    if (errno == EDOM)
        perror("    errno == EDOM");
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
asin( 1.0) = +1.570796, 2*asin( 1.0)=+3.141593
asin(-0.5) = -0.523599, 6*asin(-0.5)=-3.141593
asin(0.0) = 0.000000, asin(-0.0)=-0.000000
asin(1.1) = nan
    errno == EDOM: Numerical argument out of domain
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.2 The asin functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.2 The asin functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.2 The asin functions （第 174 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.2 The asin functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.2 The asin functions （第 238 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.2 The asin functions （第 518 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.2 The asin functions （第 219 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.2 The asin functions （第 456 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.2 The asin function

**参阅**

| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡x） (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡x） (函数) |
| [atan2 <br />atan2f (C99)<br />atan2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan2) | 计算反正切，以符号确定象限 (函数)   |
| [sin <br />sinf (C99)<br />sinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sin) | 计算正弦（sinxsin⁡x） (函数)         |
| [casin (C99)<br />casinf (C99)<br />casinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casin) | 计算复数反正弦 (函数)               |
| **asin** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/asin)** |                                     |





### atan

原址：[https://zh.cppreference.com/w/c/numeric/math/atan](https://zh.cppreference.com/w/c/numeric/math/atan)

作用：计算反正切（{\small\arctan{x} }{\small\arctan{x} }arctan(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       atanf( float arg );// (1)(C99 起)
double      atan( double arg );// (2)
long double atanl( long double arg );// (3)(C99 起)
_Decimal32  atand32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  atand64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 atand128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define atan( arg )// (7)(C99 起)
```

1-6) 计算 `arg` 的弧（反）正切主值。

7） 泛型宏：若实参拥有 `long double` 类型，则调用 (3) `atanl`。否则，若实参拥有整数类型或 `double` 类型，则调用 (2) `atan`。否则调用 (1) `atanf`。若实参为复数，则宏调用对应的复数函数（[catanf](https://zh.cppreference.com/w/c/numeric/complex/catan)、[catan](https://zh.cppreference.com/w/c/numeric/complex/catan)、[catanl](https://zh.cppreference.com/w/c/numeric/complex/catan)）。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

若不出现错误，则返回 `arg` 在 

[- 

| π    |
| ---- |
| 2    |

 ; +

| π    |
| ---- |
| 2    |

]

 弧度范围中的弧（反）正切（*arctan(arg)*）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回不修改的参数
- 若参数为 +∞，则返回 +π/2
- 若参数为 -∞，则返回 -π/2
- 若参数为 NaN，则返回 NaN

**注意**

​	[POSIX 指定](http://pubs.opengroup.org/onlinepubs/9699919799/functions/atan.html)在下溢情况下，返回不修改的 `arg`，而若不支持如此，则返回不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 和 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的实现定义值。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("atan(1) = %f, 4*atan(1)=%f\n", atan(1), 4 * atan(1));
    // 特殊值
    printf("atan(Inf) = %f, 2*atan(Inf) = %f\n", atan(INFINITY), 2*atan(INFINITY));
    printf("atan(-0.0) = %+f, atan(+0.0) = %+f\n", atan(-0.0), atan(0));
}
```

​	输出：

```txt
atan(1) = 0.785398, 4*atan(1)=3.141593
atan(Inf) = 1.570796, 2*atan(Inf) = 3.141593
atan(-0.0) = -0.000000, atan(+0.0) = +0.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.3 The atan functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.3 The atan functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.3 The atan functions （第 174 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.3 The atan functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.3 The atan functions （第 238-239 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.3 The atan functions （第 519 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.3 The atan functions （第 219 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.3 The atan functions （第 456 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.3 The atan function

**参阅**

| [atan2 <br />atan2f (C99)<br />atan2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan2) | 计算反正切，以符号确定象限 (函数)   |
| ------------------------------------------------------------ | ----------------------------------- |
| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡x） (函数) |
| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡x） (函数) |
| [tan <br />tanf (C99)<br />tanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tan) | 计算正切（tanxtan⁡x） (函数)         |
| [catan (C99)<br />catanf (C99)<br />catanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catan) | 计算复数反正切 (函数)               |
| **atan** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/atan)** |                                     |





### atan2

原址：[https://zh.cppreference.com/w/c/numeric/math/atan2](https://zh.cppreference.com/w/c/numeric/math/atan2)

作用：计算反正切，以符号确定象限   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       atan2f( float y, float x );// (1)(C99 起)
double      atan2( double y, double x );// (2)
long double atan2l( long double y, long double x );// (3)(C99 起)
_Decimal32  atan2d32( _Decimal32 y, _Decimal32 x );// (4)(C23 起)
_Decimal64  atan2d64( _Decimal64 y, _Decimal64 x );// (5)(C23 起)
_Decimal128 atan2d128( _Decimal128 y, _Decimal128 x );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define atan2( y, x )// (7)(C99 起)
```

1-6) 计算 `y / x` 的弧（反）正切，以实参符号确定正确的象限。

7） 泛型宏：若任何参数拥有 `long double` 类型，则调用 `atan2l`。否则，若任何实参拥有整数类型或 `double` 类型，则调用 `atan2`。否则调用 `atan2f`。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

若不出现错误，则返回 `y/x` 在 *[-π ; +π]* 弧度范围中的弧（反）正切（

arctan(

| y    |
| ---- |
| x    |

)

）。

Y 实参

返回值

[![math-atan2.png](https://upload.cppreference.com/mwiki/images/thumb/9/91/math-atan2.png/285px-math-atan2.png)](https://zh.cppreference.com/w/File:math-atan2.png)

X 实参

​	若出现定义域错误，则返回实现定义值。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `x` 与 `y` 均为零则可能出现定义域错误。

​	若实现支持 IEEE 浮点数算术（ IEC 60559 ），则

- 若 `x` 与 `y` 均为零，则定义域错误*不出现*
- 若 `x` 与 `y` 均为零，则也不出现值域错误
- 若 `y` 为零，则不出现极点错误
- 若 `y` 为 `±0` 且 `x` 为负或 `-0`，则返回 `±π`
- 若 `y` 为 `±0` 且 `x` 为正或 `+0`，则返回 `±0`
- 若 `y` 为 `±∞` 且 `x` 有限，则返回 `±π/2`
- 若 `y` 为 `±∞` 且 `x` 为 `-∞`，则返回 `±3π/4`
- 若 `y` 为 `±∞` 且 `x` 为 `+∞`，则返回 `±π/4`
- 若 `x` 为 `±0` 且 `y` 为负，则返回 `-π/2`
- 若 `x` 为 `±0` 且 `y` 为正，则返回 `+π/2`
- 若 `x` 为 `-∞` 且 `y` 为正有限，则返回 `+π`
- 若 `x` 为 `-∞` 且 `y` 为负有限，则返回 `-π`
- 若 `x` 为 `+∞` 且 `y` 为正有限，则返回 `+0`
- 若 `x` 为 `+∞` 且 `y` 为负有限，则返回 `-0`
- 若 `x` 为 NaN 或 `y` 为 NaN，则返回 NaN

**注意**

​	`atan2(y, x)` 等价于 `[carg](http://zh.cppreference.com/w/c/numeric/complex/carg)(x + I*y)`。

​	[POSIX 指定](http://pubs.opengroup.org/onlinepubs/9699919799/functions/atan2.html)在下溢情况下，返回 `y / x`，而若不支持如此，则返回不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 和 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的实现定义值。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    // 正常用法：以两个参数的符号确定象限
    // atan2(1,1) = +pi/4，第 I 象限
    printf("(+1,+1) cartesian is (%f,%f) polar\n", hypot( 1, 1), atan2( 1, 1));
    // atan2(1, -1) = +3pi/4，第 II 象限
    printf("(+1,-1) cartesian is (%f,%f) polar\n", hypot( 1,-1), atan2( 1,-1));
    // atan2(-1,-1) = -3pi/4，第 III 象限
    printf("(-1,-1) cartesian is (%f,%f) polar\n", hypot(-1,-1), atan2(-1,-1));
    // atan2(-1,-1) = -pi/4，第 IV 象限
    printf("(-1,+1) cartesian is (%f,%f) polar\n", hypot(-1, 1), atan2(-1, 1));
 
    // 特殊值
    printf("atan2(0, 0) = %f atan2(0, -0)=%f\n", atan2(0,0), atan2(0,-0.0));
    printf("atan2(7, 0) = %f atan2(7, -0)=%f\n", atan2(7,0), atan2(7,-0.0));
}
```

​	输出：

```txt
(+1,+1) cartesian is (1.414214,0.785398) polar
(+1,-1) cartesian is (1.414214,2.356194) polar
(-1,-1) cartesian is (1.414214,-2.356194) polar
(-1,+1) cartesian is (1.414214,-0.785398) polar
atan2(0, 0) = 0.000000 atan2(0, -0)=3.141593
atan2(7, 0) = 1.570796 atan2(7, -0)=1.570796
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.4 The atan2 functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.4 The atan2 functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.4 The atan2 functions （第 174 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.4 The atan2 functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.4 The atan2 functions （第 239 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.4 The atan2 functions （第 519 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.4 The atan2 functions （第 219 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.4 The atan2 functions （第 456 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.4 The atan2 function

**参阅**

| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡x） (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡x） (函数) |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡x） (函数) |
| [carg (C99)<br />cargf (C99)<br />cargl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/carg) | 计算复数的辐角 (函数)               |
| **atan2** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/atan2)** |                                     |





### atan2f

原址：[https://zh.cppreference.com/w/c/numeric/math/atan2](https://zh.cppreference.com/w/c/numeric/math/atan2)

作用：计算反正切，以符号确定象限   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       atan2f( float y, float x );// (1)(C99 起)
double      atan2( double y, double x );// (2)
long double atan2l( long double y, long double x );// (3)(C99 起)
_Decimal32  atan2d32( _Decimal32 y, _Decimal32 x );// (4)(C23 起)
_Decimal64  atan2d64( _Decimal64 y, _Decimal64 x );// (5)(C23 起)
_Decimal128 atan2d128( _Decimal128 y, _Decimal128 x );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define atan2( y, x )// (7)(C99 起)
```

1-6) 计算 `y / x` 的弧（反）正切，以实参符号确定正确的象限。

7） 泛型宏：若任何参数拥有 `long double` 类型，则调用 `atan2l`。否则，若任何实参拥有整数类型或 `double` 类型，则调用 `atan2`。否则调用 `atan2f`。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

若不出现错误，则返回 `y/x` 在 *[-π ; +π]* 弧度范围中的弧（反）正切（

arctan(

| y    |
| ---- |
| x    |

)

）。

Y 实参

返回值

[![math-atan2.png](https://upload.cppreference.com/mwiki/images/thumb/9/91/math-atan2.png/285px-math-atan2.png)](https://zh.cppreference.com/w/File:math-atan2.png)

X 实参

​	若出现定义域错误，则返回实现定义值。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `x` 与 `y` 均为零则可能出现定义域错误。

​	若实现支持 IEEE 浮点数算术（ IEC 60559 ），则

- 若 `x` 与 `y` 均为零，则定义域错误*不出现*
- 若 `x` 与 `y` 均为零，则也不出现值域错误
- 若 `y` 为零，则不出现极点错误
- 若 `y` 为 `±0` 且 `x` 为负或 `-0`，则返回 `±π`
- 若 `y` 为 `±0` 且 `x` 为正或 `+0`，则返回 `±0`
- 若 `y` 为 `±∞` 且 `x` 有限，则返回 `±π/2`
- 若 `y` 为 `±∞` 且 `x` 为 `-∞`，则返回 `±3π/4`
- 若 `y` 为 `±∞` 且 `x` 为 `+∞`，则返回 `±π/4`
- 若 `x` 为 `±0` 且 `y` 为负，则返回 `-π/2`
- 若 `x` 为 `±0` 且 `y` 为正，则返回 `+π/2`
- 若 `x` 为 `-∞` 且 `y` 为正有限，则返回 `+π`
- 若 `x` 为 `-∞` 且 `y` 为负有限，则返回 `-π`
- 若 `x` 为 `+∞` 且 `y` 为正有限，则返回 `+0`
- 若 `x` 为 `+∞` 且 `y` 为负有限，则返回 `-0`
- 若 `x` 为 NaN 或 `y` 为 NaN，则返回 NaN

**注意**

​	`atan2(y, x)` 等价于 `[carg](http://zh.cppreference.com/w/c/numeric/complex/carg)(x + I*y)`。

​	[POSIX 指定](http://pubs.opengroup.org/onlinepubs/9699919799/functions/atan2.html)在下溢情况下，返回 `y / x`，而若不支持如此，则返回不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 和 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的实现定义值。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    // 正常用法：以两个参数的符号确定象限
    // atan2(1,1) = +pi/4，第 I 象限
    printf("(+1,+1) cartesian is (%f,%f) polar\n", hypot( 1, 1), atan2( 1, 1));
    // atan2(1, -1) = +3pi/4，第 II 象限
    printf("(+1,-1) cartesian is (%f,%f) polar\n", hypot( 1,-1), atan2( 1,-1));
    // atan2(-1,-1) = -3pi/4，第 III 象限
    printf("(-1,-1) cartesian is (%f,%f) polar\n", hypot(-1,-1), atan2(-1,-1));
    // atan2(-1,-1) = -pi/4，第 IV 象限
    printf("(-1,+1) cartesian is (%f,%f) polar\n", hypot(-1, 1), atan2(-1, 1));
 
    // 特殊值
    printf("atan2(0, 0) = %f atan2(0, -0)=%f\n", atan2(0,0), atan2(0,-0.0));
    printf("atan2(7, 0) = %f atan2(7, -0)=%f\n", atan2(7,0), atan2(7,-0.0));
}
```

​	输出：

```txt
(+1,+1) cartesian is (1.414214,0.785398) polar
(+1,-1) cartesian is (1.414214,2.356194) polar
(-1,-1) cartesian is (1.414214,-2.356194) polar
(-1,+1) cartesian is (1.414214,-0.785398) polar
atan2(0, 0) = 0.000000 atan2(0, -0)=3.141593
atan2(7, 0) = 1.570796 atan2(7, -0)=1.570796
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.4 The atan2 functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.4 The atan2 functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.4 The atan2 functions （第 174 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.4 The atan2 functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.4 The atan2 functions （第 239 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.4 The atan2 functions （第 519 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.4 The atan2 functions （第 219 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.4 The atan2 functions （第 456 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.4 The atan2 function

**参阅**

| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡x） (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡x） (函数) |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡x） (函数) |
| [carg (C99)<br />cargf (C99)<br />cargl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/carg) | 计算复数的辐角 (函数)               |
| **atan2** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/atan2)** |                                     |





### atan2l

原址：[https://zh.cppreference.com/w/c/numeric/math/atan2](https://zh.cppreference.com/w/c/numeric/math/atan2)

作用：计算反正切，以符号确定象限   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       atan2f( float y, float x );// (1)(C99 起)
double      atan2( double y, double x );// (2)
long double atan2l( long double y, long double x );// (3)(C99 起)
_Decimal32  atan2d32( _Decimal32 y, _Decimal32 x );// (4)(C23 起)
_Decimal64  atan2d64( _Decimal64 y, _Decimal64 x );// (5)(C23 起)
_Decimal128 atan2d128( _Decimal128 y, _Decimal128 x );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define atan2( y, x )// (7)(C99 起)
```

1-6) 计算 `y / x` 的弧（反）正切，以实参符号确定正确的象限。

7） 泛型宏：若任何参数拥有 `long double` 类型，则调用 `atan2l`。否则，若任何实参拥有整数类型或 `double` 类型，则调用 `atan2`。否则调用 `atan2f`。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

若不出现错误，则返回 `y/x` 在 *[-π ; +π]* 弧度范围中的弧（反）正切（

arctan(

| y    |
| ---- |
| x    |

)

）。

Y 实参

返回值

[![math-atan2.png](https://upload.cppreference.com/mwiki/images/thumb/9/91/math-atan2.png/285px-math-atan2.png)](https://zh.cppreference.com/w/File:math-atan2.png)

X 实参

​	若出现定义域错误，则返回实现定义值。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `x` 与 `y` 均为零则可能出现定义域错误。

​	若实现支持 IEEE 浮点数算术（ IEC 60559 ），则

- 若 `x` 与 `y` 均为零，则定义域错误*不出现*
- 若 `x` 与 `y` 均为零，则也不出现值域错误
- 若 `y` 为零，则不出现极点错误
- 若 `y` 为 `±0` 且 `x` 为负或 `-0`，则返回 `±π`
- 若 `y` 为 `±0` 且 `x` 为正或 `+0`，则返回 `±0`
- 若 `y` 为 `±∞` 且 `x` 有限，则返回 `±π/2`
- 若 `y` 为 `±∞` 且 `x` 为 `-∞`，则返回 `±3π/4`
- 若 `y` 为 `±∞` 且 `x` 为 `+∞`，则返回 `±π/4`
- 若 `x` 为 `±0` 且 `y` 为负，则返回 `-π/2`
- 若 `x` 为 `±0` 且 `y` 为正，则返回 `+π/2`
- 若 `x` 为 `-∞` 且 `y` 为正有限，则返回 `+π`
- 若 `x` 为 `-∞` 且 `y` 为负有限，则返回 `-π`
- 若 `x` 为 `+∞` 且 `y` 为正有限，则返回 `+0`
- 若 `x` 为 `+∞` 且 `y` 为负有限，则返回 `-0`
- 若 `x` 为 NaN 或 `y` 为 NaN，则返回 NaN

**注意**

​	`atan2(y, x)` 等价于 `[carg](http://zh.cppreference.com/w/c/numeric/complex/carg)(x + I*y)`。

​	[POSIX 指定](http://pubs.opengroup.org/onlinepubs/9699919799/functions/atan2.html)在下溢情况下，返回 `y / x`，而若不支持如此，则返回不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 和 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的实现定义值。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    // 正常用法：以两个参数的符号确定象限
    // atan2(1,1) = +pi/4，第 I 象限
    printf("(+1,+1) cartesian is (%f,%f) polar\n", hypot( 1, 1), atan2( 1, 1));
    // atan2(1, -1) = +3pi/4，第 II 象限
    printf("(+1,-1) cartesian is (%f,%f) polar\n", hypot( 1,-1), atan2( 1,-1));
    // atan2(-1,-1) = -3pi/4，第 III 象限
    printf("(-1,-1) cartesian is (%f,%f) polar\n", hypot(-1,-1), atan2(-1,-1));
    // atan2(-1,-1) = -pi/4，第 IV 象限
    printf("(-1,+1) cartesian is (%f,%f) polar\n", hypot(-1, 1), atan2(-1, 1));
 
    // 特殊值
    printf("atan2(0, 0) = %f atan2(0, -0)=%f\n", atan2(0,0), atan2(0,-0.0));
    printf("atan2(7, 0) = %f atan2(7, -0)=%f\n", atan2(7,0), atan2(7,-0.0));
}
```

​	输出：

```txt
(+1,+1) cartesian is (1.414214,0.785398) polar
(+1,-1) cartesian is (1.414214,2.356194) polar
(-1,-1) cartesian is (1.414214,-2.356194) polar
(-1,+1) cartesian is (1.414214,-0.785398) polar
atan2(0, 0) = 0.000000 atan2(0, -0)=3.141593
atan2(7, 0) = 1.570796 atan2(7, -0)=1.570796
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.4 The atan2 functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.4 The atan2 functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.4 The atan2 functions （第 174 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.4 The atan2 functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.4 The atan2 functions （第 239 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.4 The atan2 functions （第 519 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.4 The atan2 functions （第 219 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.4 The atan2 functions （第 456 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.4 The atan2 function

**参阅**

| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡x） (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡x） (函数) |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡x） (函数) |
| [carg (C99)<br />cargf (C99)<br />cargl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/carg) | 计算复数的辐角 (函数)               |
| **atan2** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/atan2)** |                                     |





### atanf

原址：[https://zh.cppreference.com/w/c/numeric/math/atan](https://zh.cppreference.com/w/c/numeric/math/atan)

作用：计算反正切（{\small\arctan{x} }{\small\arctan{x} }arctan(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       atanf( float arg );// (1)(C99 起)
double      atan( double arg );// (2)
long double atanl( long double arg );// (3)(C99 起)
_Decimal32  atand32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  atand64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 atand128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define atan( arg )// (7)(C99 起)
```

1-6) 计算 `arg` 的弧（反）正切主值。

7） 泛型宏：若实参拥有 `long double` 类型，则调用 (3) `atanl`。否则，若实参拥有整数类型或 `double` 类型，则调用 (2) `atan`。否则调用 (1) `atanf`。若实参为复数，则宏调用对应的复数函数（[catanf](https://zh.cppreference.com/w/c/numeric/complex/catan)、[catan](https://zh.cppreference.com/w/c/numeric/complex/catan)、[catanl](https://zh.cppreference.com/w/c/numeric/complex/catan)）。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

若不出现错误，则返回 `arg` 在 

[- 

| π    |
| ---- |
| 2    |

 ; +

| π    |
| ---- |
| 2    |

]

 弧度范围中的弧（反）正切（*arctan(arg)*）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回不修改的参数
- 若参数为 +∞，则返回 +π/2
- 若参数为 -∞，则返回 -π/2
- 若参数为 NaN，则返回 NaN

**注意**

​	[POSIX 指定](http://pubs.opengroup.org/onlinepubs/9699919799/functions/atan.html)在下溢情况下，返回不修改的 `arg`，而若不支持如此，则返回不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 和 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的实现定义值。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("atan(1) = %f, 4*atan(1)=%f\n", atan(1), 4 * atan(1));
    // 特殊值
    printf("atan(Inf) = %f, 2*atan(Inf) = %f\n", atan(INFINITY), 2*atan(INFINITY));
    printf("atan(-0.0) = %+f, atan(+0.0) = %+f\n", atan(-0.0), atan(0));
}
```

​	输出：

```txt
atan(1) = 0.785398, 4*atan(1)=3.141593
atan(Inf) = 1.570796, 2*atan(Inf) = 3.141593
atan(-0.0) = -0.000000, atan(+0.0) = +0.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.3 The atan functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.3 The atan functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.3 The atan functions （第 174 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.3 The atan functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.3 The atan functions （第 238-239 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.3 The atan functions （第 519 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.3 The atan functions （第 219 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.3 The atan functions （第 456 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.3 The atan function

**参阅**

| [atan2 <br />atan2f (C99)<br />atan2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan2) | 计算反正切，以符号确定象限 (函数)   |
| ------------------------------------------------------------ | ----------------------------------- |
| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡x） (函数) |
| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡x） (函数) |
| [tan <br />tanf (C99)<br />tanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tan) | 计算正切（tanxtan⁡x） (函数)         |
| [catan (C99)<br />catanf (C99)<br />catanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catan) | 计算复数反正切 (函数)               |
| **atan** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/atan)** |                                     |





### atanh

原址：[https://zh.cppreference.com/w/c/numeric/math/atanh](https://zh.cppreference.com/w/c/numeric/math/atanh)

作用：计算反双曲正切（{\small\operatorname{artanh}{x} }{\small\operatorname{artanh}{x} }artanh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       atanhf( float arg );// (1)(C99 起)
double      atanh( double arg );// (2)(C99 起)
long double atanhl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define atanh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的反双曲正切。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `atanhl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `atanh`。否则调用 `atanhf`。若实参为复数，则调用对应的复函数（[catanhf](https://zh.cppreference.com/w/c/numeric/complex/catanh)、[catanh](https://zh.cppreference.com/w/c/numeric/complex/catanh)、[catanhl](https://zh.cppreference.com/w/c/numeric/complex/catanh)）。

**参数**

| arg  | -    | 表示双曲扇形面积的浮点数 |
| ---- | ---- | ------------------------ |
|      |      |                          |

**返回值**

​	若不出现错误，则返回 `arg` 的反双曲正切（*tanh-1
(arg)* 或 *artanh(arg)*）。

​	若出现定义域错误，则返回实现定义值（若支持则为 NaN）。

​	若出现极点错误，则返回 `±[HUGE_VAL](http://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)`、`±HUGE_VALF` 或 `±HUGE_VALL`（带正确符号）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实参不在区间 `[``-1``, ``+1``]` 中，则出现值域错误。

​	若实参为 ±1，则出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 ±0，则返回不修改的实参。
- 若实参为 ±1，则返回 ±∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 。
- 若 *|arg|>1*，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若实参为 NaN，则返回 NaN 。

**注意**

​	虽然 C 标准命名此函数为“弧双曲正切”，但双曲函数的反函数是面积函数。其实参为双曲扇形的面积，而非弧。正确的名称为“反双曲正切”（POSIX 所用）或“面积双曲正切”。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/atanh.html)在下溢的情况下，返回不修改的 `arg`，而且若不支持，则返回不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 和 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的值。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("atanh(0) = %f\natanh(-0) = %f\n", atanh(0), atanh(-0.0));
    printf("atanh(0.9) = %f\n", atanh(0.9));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("atanh(-1) = %f\n", atanh(-1));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
atanh(0) = 0.000000
atanh(-0) = -0.000000
atanh(0.9) = 1.472219
atanh(-1) = -inf
    errno == ERANGE: Numerical result out of range
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.3 The atanh functions （第 241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.3 The atanh functions （第 520 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.3 The atanh functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.3 The atanh functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.3 The atanh functions （第 241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.3 The atanh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.3 The atanh functions （第 221-222 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.3 The atanh functions （第 457 页）

**参阅**

| [asinh (C99)<br />asinhf (C99)<br />asinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asinh) | 计算反双曲正弦（arsinhxarsinh⁡x） (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| [acosh (C99)<br />acoshf (C99)<br />acoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acosh) | 计算反双曲余弦（arcoshxarcosh⁡x） (函数) |
| [tanh <br />tanhf (C99)<br />tanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tanh) | 计算双曲正切（tanhxtanh⁡x） (函数)       |
| [catanh (C99)<br />catanhf (C99)<br />catanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catanh) | 计算复数反双曲正切 (函数)               |
| **atanh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/atanh)** |                                         |

**外部链接**

[Weisstein, Eric W. “反双曲正切。”](http://mathworld.wolfram.com/InverseHyperbolicTangent.html)来自 MathWorld--A Wolfram Web Resource。





### atanhf

原址：[https://zh.cppreference.com/w/c/numeric/math/atanh](https://zh.cppreference.com/w/c/numeric/math/atanh)

作用：计算反双曲正切（{\small\operatorname{artanh}{x} }{\small\operatorname{artanh}{x} }artanh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       atanhf( float arg );// (1)(C99 起)
double      atanh( double arg );// (2)(C99 起)
long double atanhl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define atanh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的反双曲正切。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `atanhl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `atanh`。否则调用 `atanhf`。若实参为复数，则调用对应的复函数（[catanhf](https://zh.cppreference.com/w/c/numeric/complex/catanh)、[catanh](https://zh.cppreference.com/w/c/numeric/complex/catanh)、[catanhl](https://zh.cppreference.com/w/c/numeric/complex/catanh)）。

**参数**

| arg  | -    | 表示双曲扇形面积的浮点数 |
| ---- | ---- | ------------------------ |
|      |      |                          |

**返回值**

​	若不出现错误，则返回 `arg` 的反双曲正切（*tanh-1
(arg)* 或 *artanh(arg)*）。

​	若出现定义域错误，则返回实现定义值（若支持则为 NaN）。

​	若出现极点错误，则返回 `±[HUGE_VAL](http://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)`、`±HUGE_VALF` 或 `±HUGE_VALL`（带正确符号）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实参不在区间 `[``-1``, ``+1``]` 中，则出现值域错误。

​	若实参为 ±1，则出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 ±0，则返回不修改的实参。
- 若实参为 ±1，则返回 ±∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 。
- 若 *|arg|>1*，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若实参为 NaN，则返回 NaN 。

**注意**

​	虽然 C 标准命名此函数为“弧双曲正切”，但双曲函数的反函数是面积函数。其实参为双曲扇形的面积，而非弧。正确的名称为“反双曲正切”（POSIX 所用）或“面积双曲正切”。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/atanh.html)在下溢的情况下，返回不修改的 `arg`，而且若不支持，则返回不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 和 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的值。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("atanh(0) = %f\natanh(-0) = %f\n", atanh(0), atanh(-0.0));
    printf("atanh(0.9) = %f\n", atanh(0.9));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("atanh(-1) = %f\n", atanh(-1));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
atanh(0) = 0.000000
atanh(-0) = -0.000000
atanh(0.9) = 1.472219
atanh(-1) = -inf
    errno == ERANGE: Numerical result out of range
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.3 The atanh functions （第 241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.3 The atanh functions （第 520 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.3 The atanh functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.3 The atanh functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.3 The atanh functions （第 241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.3 The atanh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.3 The atanh functions （第 221-222 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.3 The atanh functions （第 457 页）

**参阅**

| [asinh (C99)<br />asinhf (C99)<br />asinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asinh) | 计算反双曲正弦（arsinhxarsinh⁡x） (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| [acosh (C99)<br />acoshf (C99)<br />acoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acosh) | 计算反双曲余弦（arcoshxarcosh⁡x） (函数) |
| [tanh <br />tanhf (C99)<br />tanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tanh) | 计算双曲正切（tanhxtanh⁡x） (函数)       |
| [catanh (C99)<br />catanhf (C99)<br />catanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catanh) | 计算复数反双曲正切 (函数)               |
| **atanh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/atanh)** |                                         |

**外部链接**

[Weisstein, Eric W. “反双曲正切。”](http://mathworld.wolfram.com/InverseHyperbolicTangent.html)来自 MathWorld--A Wolfram Web Resource。





### atanhl

原址：[https://zh.cppreference.com/w/c/numeric/math/atanh](https://zh.cppreference.com/w/c/numeric/math/atanh)

作用：计算反双曲正切（{\small\operatorname{artanh}{x} }{\small\operatorname{artanh}{x} }artanh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       atanhf( float arg );// (1)(C99 起)
double      atanh( double arg );// (2)(C99 起)
long double atanhl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define atanh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的反双曲正切。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `atanhl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `atanh`。否则调用 `atanhf`。若实参为复数，则调用对应的复函数（[catanhf](https://zh.cppreference.com/w/c/numeric/complex/catanh)、[catanh](https://zh.cppreference.com/w/c/numeric/complex/catanh)、[catanhl](https://zh.cppreference.com/w/c/numeric/complex/catanh)）。

**参数**

| arg  | -    | 表示双曲扇形面积的浮点数 |
| ---- | ---- | ------------------------ |
|      |      |                          |

**返回值**

​	若不出现错误，则返回 `arg` 的反双曲正切（*tanh-1
(arg)* 或 *artanh(arg)*）。

​	若出现定义域错误，则返回实现定义值（若支持则为 NaN）。

​	若出现极点错误，则返回 `±[HUGE_VAL](http://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)`、`±HUGE_VALF` 或 `±HUGE_VALL`（带正确符号）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实参不在区间 `[``-1``, ``+1``]` 中，则出现值域错误。

​	若实参为 ±1，则出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 ±0，则返回不修改的实参。
- 若实参为 ±1，则返回 ±∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 。
- 若 *|arg|>1*，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若实参为 NaN，则返回 NaN 。

**注意**

​	虽然 C 标准命名此函数为“弧双曲正切”，但双曲函数的反函数是面积函数。其实参为双曲扇形的面积，而非弧。正确的名称为“反双曲正切”（POSIX 所用）或“面积双曲正切”。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/atanh.html)在下溢的情况下，返回不修改的 `arg`，而且若不支持，则返回不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 和 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的值。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("atanh(0) = %f\natanh(-0) = %f\n", atanh(0), atanh(-0.0));
    printf("atanh(0.9) = %f\n", atanh(0.9));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("atanh(-1) = %f\n", atanh(-1));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
atanh(0) = 0.000000
atanh(-0) = -0.000000
atanh(0.9) = 1.472219
atanh(-1) = -inf
    errno == ERANGE: Numerical result out of range
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.3 The atanh functions （第 241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.3 The atanh functions （第 520 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.3 The atanh functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.3 The atanh functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.3 The atanh functions （第 241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.3 The atanh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.3 The atanh functions （第 221-222 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.3 The atanh functions （第 457 页）

**参阅**

| [asinh (C99)<br />asinhf (C99)<br />asinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asinh) | 计算反双曲正弦（arsinhxarsinh⁡x） (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| [acosh (C99)<br />acoshf (C99)<br />acoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acosh) | 计算反双曲余弦（arcoshxarcosh⁡x） (函数) |
| [tanh <br />tanhf (C99)<br />tanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tanh) | 计算双曲正切（tanhxtanh⁡x） (函数)       |
| [catanh (C99)<br />catanhf (C99)<br />catanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catanh) | 计算复数反双曲正切 (函数)               |
| **atanh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/atanh)** |                                         |

**外部链接**

[Weisstein, Eric W. “反双曲正切。”](http://mathworld.wolfram.com/InverseHyperbolicTangent.html)来自 MathWorld--A Wolfram Web Resource。





### atanl

原址：[https://zh.cppreference.com/w/c/numeric/math/atan](https://zh.cppreference.com/w/c/numeric/math/atan)

作用：计算反正切（{\small\arctan{x} }{\small\arctan{x} }arctan(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       atanf( float arg );// (1)(C99 起)
double      atan( double arg );// (2)
long double atanl( long double arg );// (3)(C99 起)
_Decimal32  atand32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  atand64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 atand128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define atan( arg )// (7)(C99 起)
```

1-6) 计算 `arg` 的弧（反）正切主值。

7） 泛型宏：若实参拥有 `long double` 类型，则调用 (3) `atanl`。否则，若实参拥有整数类型或 `double` 类型，则调用 (2) `atan`。否则调用 (1) `atanf`。若实参为复数，则宏调用对应的复数函数（[catanf](https://zh.cppreference.com/w/c/numeric/complex/catan)、[catan](https://zh.cppreference.com/w/c/numeric/complex/catan)、[catanl](https://zh.cppreference.com/w/c/numeric/complex/catan)）。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

若不出现错误，则返回 `arg` 在 

[- 

| π    |
| ---- |
| 2    |

 ; +

| π    |
| ---- |
| 2    |

]

 弧度范围中的弧（反）正切（*arctan(arg)*）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回不修改的参数
- 若参数为 +∞，则返回 +π/2
- 若参数为 -∞，则返回 -π/2
- 若参数为 NaN，则返回 NaN

**注意**

​	[POSIX 指定](http://pubs.opengroup.org/onlinepubs/9699919799/functions/atan.html)在下溢情况下，返回不修改的 `arg`，而若不支持如此，则返回不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 和 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的实现定义值。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("atan(1) = %f, 4*atan(1)=%f\n", atan(1), 4 * atan(1));
    // 特殊值
    printf("atan(Inf) = %f, 2*atan(Inf) = %f\n", atan(INFINITY), 2*atan(INFINITY));
    printf("atan(-0.0) = %+f, atan(+0.0) = %+f\n", atan(-0.0), atan(0));
}
```

​	输出：

```txt
atan(1) = 0.785398, 4*atan(1)=3.141593
atan(Inf) = 1.570796, 2*atan(Inf) = 3.141593
atan(-0.0) = -0.000000, atan(+0.0) = +0.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.3 The atan functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.3 The atan functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.3 The atan functions （第 174 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.3 The atan functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.3 The atan functions （第 238-239 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.3 The atan functions （第 519 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.3 The atan functions （第 219 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.3 The atan functions （第 456 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.3 The atan function

**参阅**

| [atan2 <br />atan2f (C99)<br />atan2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan2) | 计算反正切，以符号确定象限 (函数)   |
| ------------------------------------------------------------ | ----------------------------------- |
| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡x） (函数) |
| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡x） (函数) |
| [tan <br />tanf (C99)<br />tanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tan) | 计算正切（tanxtan⁡x） (函数)         |
| [catan (C99)<br />catanf (C99)<br />catanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catan) | 计算复数反正切 (函数)               |
| **atan** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/atan)** |                                     |





### cbrt

原址：[https://zh.cppreference.com/w/c/numeric/math/cbrt](https://zh.cppreference.com/w/c/numeric/math/cbrt)

作用：计算立方根（\small{\sqrt[3]{x} }\small{\sqrt[3]{x} }3√x）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       cbrtf( float arg );// (1)(C99 起)
double      cbrt( double arg );// (2)(C99 起)
long double cbrtl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cbrt( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的立方根。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `cbrtl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `cbrt`。否则，调用 `cbrtf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的立方根（3√argarg3）。

​	若出现下溢所致的错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（ IEC 60559 ），则

- 若参数为 ±0 或 ±∞ ，则返回不更改的参数
- 若参数为 NaN ，则返回 NaN 。

**注解**

`cbrt(arg)` 不等价于 `[pow](http://zh.cppreference.com/w/c/numeric/math/pow)(arg, 1.0/3)`，因为有理数 1313 通常不等于 `1.0/3` 并且 [pow](https://zh.cppreference.com/w/c/numeric/math/pow) 不能求负底数的小数次幂。另外 `cbrt(arg)` 常给出比 `[pow](http://zh.cppreference.com/w/c/numeric/math/pow)(arg, 1.0/3)` 更精确的结果（见示例）。

**示例**

```c
#include <float.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("普通用法:\n"
           "cbrt(729)      = %f\n", cbrt(729));
    printf("cbrt(-0.125)   = %f\n", cbrt(-0.125));
    printf("特殊值:\n"
           "cbrt(-0)       = %f\n", cbrt(-0.0));
    printf("cbrt(+inf)     = %f\n", cbrt(INFINITY));
    printf("精度:\n"
           "cbrt(343)      = %.*f\n", DBL_DECIMAL_DIG, cbrt(343));
    printf("pow(343,1.0/3) = %.*f\n", DBL_DECIMAL_DIG, pow(343, 1.0/3));
}
```

​	可能的输出：

```txt
普通用法:
cbrt(729)      = 9.000000
cbrt(-0.125)   = -0.500000
特殊值:
cbrt(-0)       = -0.000000
cbrt(+inf)     = inf
精度:
cbrt(343)      = 7.00000000000000000
pow(343,1.0/3) = 6.99999999999999911
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.7.1 The cbrt functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.4.1 The cbrt functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.7.1 The cbrt functions （第 180-181 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.4.1 The cbrt functions （第 381- 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.7.1 The cbrt functions （第 247 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.1 The cbrt functions （第 524 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.7.1 The cbrt functions （第 228 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.4.1 The cbrt functions （第 460 页）

**参阅**

| [pow <br />powf (C99)<br />powl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/pow) | 计算一个数的给定次幂（xyxy） (函数)                |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [sqrt <br />sqrtf (C99)<br />sqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sqrt) | 计算平方根（√xx） (函数)                           |
| [hypot (C99)<br />hypotf (C99)<br />hypotl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/hypot) | 计算两个给定数平方和的平方根（√x2+y2x2+y2） (函数) |
| **cbrt** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/cbrt)** |                                                    |





### cbrtf

原址：[https://zh.cppreference.com/w/c/numeric/math/cbrt](https://zh.cppreference.com/w/c/numeric/math/cbrt)

作用：计算立方根（\small{\sqrt[3]{x} }\small{\sqrt[3]{x} }3√x）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       cbrtf( float arg );// (1)(C99 起)
double      cbrt( double arg );// (2)(C99 起)
long double cbrtl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cbrt( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的立方根。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `cbrtl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `cbrt`。否则，调用 `cbrtf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的立方根（3√argarg3）。

​	若出现下溢所致的错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（ IEC 60559 ），则

- 若参数为 ±0 或 ±∞ ，则返回不更改的参数
- 若参数为 NaN ，则返回 NaN 。

**注解**

`cbrt(arg)` 不等价于 `[pow](http://zh.cppreference.com/w/c/numeric/math/pow)(arg, 1.0/3)`，因为有理数 1313 通常不等于 `1.0/3` 并且 [pow](https://zh.cppreference.com/w/c/numeric/math/pow) 不能求负底数的小数次幂。另外 `cbrt(arg)` 常给出比 `[pow](http://zh.cppreference.com/w/c/numeric/math/pow)(arg, 1.0/3)` 更精确的结果（见示例）。

**示例**

```c
#include <float.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("普通用法:\n"
           "cbrt(729)      = %f\n", cbrt(729));
    printf("cbrt(-0.125)   = %f\n", cbrt(-0.125));
    printf("特殊值:\n"
           "cbrt(-0)       = %f\n", cbrt(-0.0));
    printf("cbrt(+inf)     = %f\n", cbrt(INFINITY));
    printf("精度:\n"
           "cbrt(343)      = %.*f\n", DBL_DECIMAL_DIG, cbrt(343));
    printf("pow(343,1.0/3) = %.*f\n", DBL_DECIMAL_DIG, pow(343, 1.0/3));
}
```

​	可能的输出：

```txt
普通用法:
cbrt(729)      = 9.000000
cbrt(-0.125)   = -0.500000
特殊值:
cbrt(-0)       = -0.000000
cbrt(+inf)     = inf
精度:
cbrt(343)      = 7.00000000000000000
pow(343,1.0/3) = 6.99999999999999911
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.7.1 The cbrt functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.4.1 The cbrt functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.7.1 The cbrt functions （第 180-181 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.4.1 The cbrt functions （第 381- 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.7.1 The cbrt functions （第 247 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.1 The cbrt functions （第 524 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.7.1 The cbrt functions （第 228 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.4.1 The cbrt functions （第 460 页）

**参阅**

| [pow <br />powf (C99)<br />powl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/pow) | 计算一个数的给定次幂（xyxy） (函数)                |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [sqrt <br />sqrtf (C99)<br />sqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sqrt) | 计算平方根（√xx） (函数)                           |
| [hypot (C99)<br />hypotf (C99)<br />hypotl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/hypot) | 计算两个给定数平方和的平方根（√x2+y2x2+y2） (函数) |
| **cbrt** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/cbrt)** |                                                    |





### cbrtl

原址：[https://zh.cppreference.com/w/c/numeric/math/cbrt](https://zh.cppreference.com/w/c/numeric/math/cbrt)

作用：计算立方根（\small{\sqrt[3]{x} }\small{\sqrt[3]{x} }3√x）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       cbrtf( float arg );// (1)(C99 起)
double      cbrt( double arg );// (2)(C99 起)
long double cbrtl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cbrt( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的立方根。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `cbrtl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `cbrt`。否则，调用 `cbrtf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的立方根（3√argarg3）。

​	若出现下溢所致的错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（ IEC 60559 ），则

- 若参数为 ±0 或 ±∞ ，则返回不更改的参数
- 若参数为 NaN ，则返回 NaN 。

**注解**

`cbrt(arg)` 不等价于 `[pow](http://zh.cppreference.com/w/c/numeric/math/pow)(arg, 1.0/3)`，因为有理数 1313 通常不等于 `1.0/3` 并且 [pow](https://zh.cppreference.com/w/c/numeric/math/pow) 不能求负底数的小数次幂。另外 `cbrt(arg)` 常给出比 `[pow](http://zh.cppreference.com/w/c/numeric/math/pow)(arg, 1.0/3)` 更精确的结果（见示例）。

**示例**

```c
#include <float.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("普通用法:\n"
           "cbrt(729)      = %f\n", cbrt(729));
    printf("cbrt(-0.125)   = %f\n", cbrt(-0.125));
    printf("特殊值:\n"
           "cbrt(-0)       = %f\n", cbrt(-0.0));
    printf("cbrt(+inf)     = %f\n", cbrt(INFINITY));
    printf("精度:\n"
           "cbrt(343)      = %.*f\n", DBL_DECIMAL_DIG, cbrt(343));
    printf("pow(343,1.0/3) = %.*f\n", DBL_DECIMAL_DIG, pow(343, 1.0/3));
}
```

​	可能的输出：

```txt
普通用法:
cbrt(729)      = 9.000000
cbrt(-0.125)   = -0.500000
特殊值:
cbrt(-0)       = -0.000000
cbrt(+inf)     = inf
精度:
cbrt(343)      = 7.00000000000000000
pow(343,1.0/3) = 6.99999999999999911
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.7.1 The cbrt functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.4.1 The cbrt functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.7.1 The cbrt functions （第 180-181 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.4.1 The cbrt functions （第 381- 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.7.1 The cbrt functions （第 247 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.1 The cbrt functions （第 524 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.7.1 The cbrt functions （第 228 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.4.1 The cbrt functions （第 460 页）

**参阅**

| [pow <br />powf (C99)<br />powl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/pow) | 计算一个数的给定次幂（xyxy） (函数)                |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [sqrt <br />sqrtf (C99)<br />sqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sqrt) | 计算平方根（√xx） (函数)                           |
| [hypot (C99)<br />hypotf (C99)<br />hypotl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/hypot) | 计算两个给定数平方和的平方根（√x2+y2x2+y2） (函数) |
| **cbrt** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/cbrt)** |                                                    |





### ceil

原址：[https://zh.cppreference.com/w/c/numeric/math/ceil](https://zh.cppreference.com/w/c/numeric/math/ceil)

作用：计算不小于给定值的最小整数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       ceilf( float arg );// (1)(C99 起)
double      ceil( double arg );// (2)
long double ceill( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define ceil( arg )// (4)(C99 起)
```

1-3) 计算不小于 `arg` 的最小整数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `ceill`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `ceil`。否则，调用 `ceilf`。

**参数**

| arg  | -    | 返回值 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回不小于 `arg` 的最小整数，即 *⌈arg⌉*。

返回值

![math-ceil.svg](https://upload.cppreference.com/mwiki/images/1/1e/math-ceil.svg)

实参

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
- 若 `arg` 为 ±∞，则返回它而不修改。
- 若 `arg` 为 ±0，则返回它而不修改。
- 若 `arg` 为 NaN，则返回 NaN。

**注意**

​	舍入非整数有限值时，可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中的最大可表示浮点数都是准确的整数，故此函数自身决不上溢；然而存储于整数对象时，结果可以溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	此函数（`double` 实参的）表现如同（除了不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的自由）实现如下

```c
#include <fenv.h>
#include <math.h>
#pragma STDC FENV_ACCESS ON
 
double ceil(double x)
{
    double result;
    int save_round = fegetround();
    fesetround(FE_UPWARD);
    result = rint(x); // 或 nearbyint
    fesetround(save_round);
    return result;
}
```

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("ceil(+2.4) = %+.1f\n", ceil(2.4));
    printf("ceil(-2.4) = %+.1f\n", ceil(-2.4));
    printf("ceil(-0.0) = %+.1f\n", ceil(-0.0));
    printf("ceil(-Inf) = %+f\n",   ceil(-INFINITY));
}
```

​	可能的输出：

```txt
ceil(+2.4) = +3.0
ceil(-2.4) = -2.0
ceil(-0.0) = -0.0
ceil(-Inf) = -inf
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.1 The ceil functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.1 The ceil functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.1 The ceil functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.1 The ceil functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.1 The ceil functions （第 251 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.1 The ceil functions （第 526 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.1 The ceil functions （第 231-232 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.1 The ceil functions （第 462-463 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.6.1 The ceil function

**参阅**

| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)                         |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数)               |
| [round (C99)<br />roundf (C99)<br />roundl (C99)<br />lround (C99)<br />lroundf (C99)<br />lroundl (C99)<br />llround (C99)<br />llroundf (C99)<br />llroundl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/round) | 取整到最接近的整数，在相邻整数正中间时取远离零的数 (函数) |
| [nearbyint (C99)<br />nearbyintf (C99)<br />nearbyintl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/nearbyint) | 用当前舍入模式取整到整数 (函数)                           |
| [rint (C99)<br />rintf (C99)<br />rintl (C99)<br />lrint (C99)<br />lrintf (C99)<br />lrintl (C99)<br />llrint (C99)<br />llrintf (C99)<br />llrintl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/rint) | 使用当前舍入模式取整到整数，若结果有误则产生异常 (函数)   |
| **ceil** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/ceil)** |                                                           |





### ceilf

原址：[https://zh.cppreference.com/w/c/numeric/math/ceil](https://zh.cppreference.com/w/c/numeric/math/ceil)

作用：计算不小于给定值的最小整数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       ceilf( float arg );// (1)(C99 起)
double      ceil( double arg );// (2)
long double ceill( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define ceil( arg )// (4)(C99 起)
```

1-3) 计算不小于 `arg` 的最小整数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `ceill`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `ceil`。否则，调用 `ceilf`。

**参数**

| arg  | -    | 返回值 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回不小于 `arg` 的最小整数，即 *⌈arg⌉*。

返回值

![math-ceil.svg](https://upload.cppreference.com/mwiki/images/1/1e/math-ceil.svg)

实参

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
- 若 `arg` 为 ±∞，则返回它而不修改。
- 若 `arg` 为 ±0，则返回它而不修改。
- 若 `arg` 为 NaN，则返回 NaN。

**注意**

​	舍入非整数有限值时，可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中的最大可表示浮点数都是准确的整数，故此函数自身决不上溢；然而存储于整数对象时，结果可以溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	此函数（`double` 实参的）表现如同（除了不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的自由）实现如下

```c
#include <fenv.h>
#include <math.h>
#pragma STDC FENV_ACCESS ON
 
double ceil(double x)
{
    double result;
    int save_round = fegetround();
    fesetround(FE_UPWARD);
    result = rint(x); // 或 nearbyint
    fesetround(save_round);
    return result;
}
```

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("ceil(+2.4) = %+.1f\n", ceil(2.4));
    printf("ceil(-2.4) = %+.1f\n", ceil(-2.4));
    printf("ceil(-0.0) = %+.1f\n", ceil(-0.0));
    printf("ceil(-Inf) = %+f\n",   ceil(-INFINITY));
}
```

​	可能的输出：

```txt
ceil(+2.4) = +3.0
ceil(-2.4) = -2.0
ceil(-0.0) = -0.0
ceil(-Inf) = -inf
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.1 The ceil functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.1 The ceil functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.1 The ceil functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.1 The ceil functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.1 The ceil functions （第 251 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.1 The ceil functions （第 526 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.1 The ceil functions （第 231-232 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.1 The ceil functions （第 462-463 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.6.1 The ceil function

**参阅**

| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)                         |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数)               |
| [round (C99)<br />roundf (C99)<br />roundl (C99)<br />lround (C99)<br />lroundf (C99)<br />lroundl (C99)<br />llround (C99)<br />llroundf (C99)<br />llroundl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/round) | 取整到最接近的整数，在相邻整数正中间时取远离零的数 (函数) |
| [nearbyint (C99)<br />nearbyintf (C99)<br />nearbyintl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/nearbyint) | 用当前舍入模式取整到整数 (函数)                           |
| [rint (C99)<br />rintf (C99)<br />rintl (C99)<br />lrint (C99)<br />lrintf (C99)<br />lrintl (C99)<br />llrint (C99)<br />llrintf (C99)<br />llrintl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/rint) | 使用当前舍入模式取整到整数，若结果有误则产生异常 (函数)   |
| **ceil** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/ceil)** |                                                           |





### ceill

原址：[https://zh.cppreference.com/w/c/numeric/math/ceil](https://zh.cppreference.com/w/c/numeric/math/ceil)

作用：计算不小于给定值的最小整数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       ceilf( float arg );// (1)(C99 起)
double      ceil( double arg );// (2)
long double ceill( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define ceil( arg )// (4)(C99 起)
```

1-3) 计算不小于 `arg` 的最小整数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `ceill`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `ceil`。否则，调用 `ceilf`。

**参数**

| arg  | -    | 返回值 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回不小于 `arg` 的最小整数，即 *⌈arg⌉*。

返回值

![math-ceil.svg](https://upload.cppreference.com/mwiki/images/1/1e/math-ceil.svg)

实参

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
- 若 `arg` 为 ±∞，则返回它而不修改。
- 若 `arg` 为 ±0，则返回它而不修改。
- 若 `arg` 为 NaN，则返回 NaN。

**注意**

​	舍入非整数有限值时，可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中的最大可表示浮点数都是准确的整数，故此函数自身决不上溢；然而存储于整数对象时，结果可以溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	此函数（`double` 实参的）表现如同（除了不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的自由）实现如下

```c
#include <fenv.h>
#include <math.h>
#pragma STDC FENV_ACCESS ON
 
double ceil(double x)
{
    double result;
    int save_round = fegetround();
    fesetround(FE_UPWARD);
    result = rint(x); // 或 nearbyint
    fesetround(save_round);
    return result;
}
```

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("ceil(+2.4) = %+.1f\n", ceil(2.4));
    printf("ceil(-2.4) = %+.1f\n", ceil(-2.4));
    printf("ceil(-0.0) = %+.1f\n", ceil(-0.0));
    printf("ceil(-Inf) = %+f\n",   ceil(-INFINITY));
}
```

​	可能的输出：

```txt
ceil(+2.4) = +3.0
ceil(-2.4) = -2.0
ceil(-0.0) = -0.0
ceil(-Inf) = -inf
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.1 The ceil functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.1 The ceil functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.1 The ceil functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.1 The ceil functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.1 The ceil functions （第 251 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.1 The ceil functions （第 526 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.1 The ceil functions （第 231-232 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.1 The ceil functions （第 462-463 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.6.1 The ceil function

**参阅**

| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)                         |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数)               |
| [round (C99)<br />roundf (C99)<br />roundl (C99)<br />lround (C99)<br />lroundf (C99)<br />lroundl (C99)<br />llround (C99)<br />llroundf (C99)<br />llroundl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/round) | 取整到最接近的整数，在相邻整数正中间时取远离零的数 (函数) |
| [nearbyint (C99)<br />nearbyintf (C99)<br />nearbyintl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/nearbyint) | 用当前舍入模式取整到整数 (函数)                           |
| [rint (C99)<br />rintf (C99)<br />rintl (C99)<br />lrint (C99)<br />lrintf (C99)<br />lrintl (C99)<br />llrint (C99)<br />llrintf (C99)<br />llrintl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/rint) | 使用当前舍入模式取整到整数，若结果有误则产生异常 (函数)   |
| **ceil** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/ceil)** |                                                           |





### copysign

原址：[https://zh.cppreference.com/w/c/numeric/math/copysign](https://zh.cppreference.com/w/c/numeric/math/copysign)

作用：从一个给定值的绝对值和另一个给定值的符号产生值   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       copysignf( float x, float y );// (1)(C99 起)
double      copysign( double x, double y );// (2)(C99 起)
long double copysignl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define copysign(x, y)// (4)(C99 起)
```

1-3) 以 `x` 的绝对值和 `y` 的符号合成浮点数。

4） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `copysignl`。否则，若任何实参拥有整数类型或 `double` 类型，则调用 `copysign`。否则，调用 `copysignf`。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回拥有 `x` 的绝对值和 `y` 的符号的浮点数。

​	若 `x` 为 NaN，则返回拥有 `y` 的符号的 NaN。

​	若 `y` 为 -0，则仅若实现支持与算术运算一致的有符号零，结果才为负。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 返回值是准确的（决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)），且与当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)独立。

**注意**

​	`copysign` 是操纵 NaN 值符号的唯一可移植方式（为检验 NaN 的符号，亦可用 [signbit](https://zh.cppreference.com/w/c/numeric/math/signbit)）。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("copysign(1.0,+2.0)      = %+.1f\n", copysign(1.0,+2.0));
    printf("copysign(1.0,-2.0)      = %+.1f\n", copysign(1.0,-2.0));
    printf("copysign(INFINITY,-2.0) = %f\n",    copysign(INFINITY,-2.0));
    printf("copysign(NAN,-2.0)      = %f\n",    copysign(NAN,-2.0));
}
```

​	可能的输出：

```txt
copysign(1.0,+2.0)      = +1.0
copysign(1.0,-2.0)      = -1.0
copysign(INFINITY,-2.0) = -inf
copysign(NAN,-2.0)      = -nan
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.11.1 The copysign functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.8.1 The copysign functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.11.1 The copysign functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.8.1 The copysign functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.11.1 The copysign functions （第 255 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.8.1 The copysign functions （第 529 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.11.1 The copysign functions （第 236 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.8.1 The copysign functions （第 465 页）

**参阅**

| [fabs <br />fabsf (C99)<br />fabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fabs) | 计算浮点数的绝对值（\|x\|\|x\|） (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| [signbit (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/signbit) | 检查给定数是不是负数 (宏函数)           |
| **copysign** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/copysign)** |                                         |





### copysignf

原址：[https://zh.cppreference.com/w/c/numeric/math/copysign](https://zh.cppreference.com/w/c/numeric/math/copysign)

作用：从一个给定值的绝对值和另一个给定值的符号产生值   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       copysignf( float x, float y );// (1)(C99 起)
double      copysign( double x, double y );// (2)(C99 起)
long double copysignl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define copysign(x, y)// (4)(C99 起)
```

1-3) 以 `x` 的绝对值和 `y` 的符号合成浮点数。

4） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `copysignl`。否则，若任何实参拥有整数类型或 `double` 类型，则调用 `copysign`。否则，调用 `copysignf`。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回拥有 `x` 的绝对值和 `y` 的符号的浮点数。

​	若 `x` 为 NaN，则返回拥有 `y` 的符号的 NaN。

​	若 `y` 为 -0，则仅若实现支持与算术运算一致的有符号零，结果才为负。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 返回值是准确的（决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)），且与当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)独立。

**注意**

​	`copysign` 是操纵 NaN 值符号的唯一可移植方式（为检验 NaN 的符号，亦可用 [signbit](https://zh.cppreference.com/w/c/numeric/math/signbit)）。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("copysign(1.0,+2.0)      = %+.1f\n", copysign(1.0,+2.0));
    printf("copysign(1.0,-2.0)      = %+.1f\n", copysign(1.0,-2.0));
    printf("copysign(INFINITY,-2.0) = %f\n",    copysign(INFINITY,-2.0));
    printf("copysign(NAN,-2.0)      = %f\n",    copysign(NAN,-2.0));
}
```

​	可能的输出：

```txt
copysign(1.0,+2.0)      = +1.0
copysign(1.0,-2.0)      = -1.0
copysign(INFINITY,-2.0) = -inf
copysign(NAN,-2.0)      = -nan
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.11.1 The copysign functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.8.1 The copysign functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.11.1 The copysign functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.8.1 The copysign functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.11.1 The copysign functions （第 255 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.8.1 The copysign functions （第 529 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.11.1 The copysign functions （第 236 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.8.1 The copysign functions （第 465 页）

**参阅**

| [fabs <br />fabsf (C99)<br />fabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fabs) | 计算浮点数的绝对值（\|x\|\|x\|） (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| [signbit (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/signbit) | 检查给定数是不是负数 (宏函数)           |
| **copysign** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/copysign)** |                                         |





### copysignl

原址：[https://zh.cppreference.com/w/c/numeric/math/copysign](https://zh.cppreference.com/w/c/numeric/math/copysign)

作用：从一个给定值的绝对值和另一个给定值的符号产生值   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       copysignf( float x, float y );// (1)(C99 起)
double      copysign( double x, double y );// (2)(C99 起)
long double copysignl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define copysign(x, y)// (4)(C99 起)
```

1-3) 以 `x` 的绝对值和 `y` 的符号合成浮点数。

4） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `copysignl`。否则，若任何实参拥有整数类型或 `double` 类型，则调用 `copysign`。否则，调用 `copysignf`。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回拥有 `x` 的绝对值和 `y` 的符号的浮点数。

​	若 `x` 为 NaN，则返回拥有 `y` 的符号的 NaN。

​	若 `y` 为 -0，则仅若实现支持与算术运算一致的有符号零，结果才为负。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 返回值是准确的（决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)），且与当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)独立。

**注意**

​	`copysign` 是操纵 NaN 值符号的唯一可移植方式（为检验 NaN 的符号，亦可用 [signbit](https://zh.cppreference.com/w/c/numeric/math/signbit)）。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("copysign(1.0,+2.0)      = %+.1f\n", copysign(1.0,+2.0));
    printf("copysign(1.0,-2.0)      = %+.1f\n", copysign(1.0,-2.0));
    printf("copysign(INFINITY,-2.0) = %f\n",    copysign(INFINITY,-2.0));
    printf("copysign(NAN,-2.0)      = %f\n",    copysign(NAN,-2.0));
}
```

​	可能的输出：

```txt
copysign(1.0,+2.0)      = +1.0
copysign(1.0,-2.0)      = -1.0
copysign(INFINITY,-2.0) = -inf
copysign(NAN,-2.0)      = -nan
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.11.1 The copysign functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.8.1 The copysign functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.11.1 The copysign functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.8.1 The copysign functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.11.1 The copysign functions （第 255 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.8.1 The copysign functions （第 529 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.11.1 The copysign functions （第 236 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.8.1 The copysign functions （第 465 页）

**参阅**

| [fabs <br />fabsf (C99)<br />fabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fabs) | 计算浮点数的绝对值（\|x\|\|x\|） (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| [signbit (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/signbit) | 检查给定数是不是负数 (宏函数)           |
| **copysign** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/copysign)** |                                         |





### cos

原址：[https://zh.cppreference.com/w/c/numeric/math/cos](https://zh.cppreference.com/w/c/numeric/math/cos)

作用：计算余弦（{\small\cos{x} }{\small\cos{x} }cos(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       cosf( float arg );// (1)(C99 起)
double      cos( double arg );// (2)
long double cosl( long double arg );// (3)(C99 起)
_Decimal32  cosd32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  cosd64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 cosd128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define cos( arg )// (7)(C99 起)
```

1-6) 计算 `arg` （以弧度计量）的余弦。

7） 泛型宏：若实参拥有 `long double` 类型，则调用 `cosl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `cos`。否则，调用 `cosf`、若实参为复数，则该宏调用对应的复函数（`[ccosf](http://zh.cppreference.com/w/c/numeric/complex/ccos)`、`[ccos](http://zh.cppreference.com/w/c/numeric/complex/ccos)`、`[ccosl](http://zh.cppreference.com/w/c/numeric/complex/ccos)`）。

**参数**

| arg  | -    | 以弧度表示角的浮点数 |
| ---- | ---- | -------------------- |
|      |      |                      |

**返回值**

​	若不出现错误，则返回 `arg` 的余弦（*cos(arg)*），在范围 *[-1 ; +1]* 中。

​	若 `arg` 的绝对值很大，则结果可能只有少量或没有效数字。 (C99 前)

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确的结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），

- 则若参数为 ±0，则结果为 1.0
- 若参数为 ±∞，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若参数为 NaN，则返回 NaN

**注意**

​	参数为无穷大的情况不被指定为 C 中的定义域错误，但被定义为 [POSIX 中的定义域错误](http://pubs.opengroup.org/onlinepubs/9699919799/functions/cos.html)。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
int main(void)
{
    const double pi = acos(-1);
 
    // 典型用法
    printf("cos(pi/3) = %f\n", cos(pi / 3));
    printf("cos(pi/2) = %f\n", cos(pi / 2));
    printf("cos(-3*pi/4) = %f\n", cos(-3 * pi / 4));
 
    // 特殊值
    printf("cos(+0) = %f\n", cos(0.0));
    printf("cos(-0) = %f\n", cos(-0.0));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("cos(INFINITY) = %f\n", cos(INFINITY));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
cos(pi/3) = 0.500000
cos(pi/2) = 0.000000
cos(-3*pi/4) = -0.707107
cos(+0) = 1.000000
cos(-0) = 1.000000
cos(INFINITY) = -nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.5 The cos functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.5 The cos functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.5 The cos functions （第 174 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.5 The cos functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.5 The cos functions （第 239 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.5 The cos functions （第 519 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.5 The cos functions （第 220 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.5 The cos functions （第 456 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.5 The cos function

**参阅**

| [sin <br />sinf (C99)<br />sinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sin) | 计算正弦（sinxsin⁡x） (函数)         |
| ------------------------------------------------------------ | ----------------------------------- |
| [tan <br />tanf (C99)<br />tanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tan) | 计算正切（tanxtan⁡x） (函数)         |
| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡x） (函数) |
| [ccos (C99)<br />ccosf (C99)<br />ccosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccos) | 计算复数余弦 (函数)                 |
| **cos** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/cos)** |                                     |





### cosf

原址：[https://zh.cppreference.com/w/c/numeric/math/cos](https://zh.cppreference.com/w/c/numeric/math/cos)

作用：计算余弦（{\small\cos{x} }{\small\cos{x} }cos(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       cosf( float arg );// (1)(C99 起)
double      cos( double arg );// (2)
long double cosl( long double arg );// (3)(C99 起)
_Decimal32  cosd32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  cosd64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 cosd128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define cos( arg )// (7)(C99 起)
```

1-6) 计算 `arg` （以弧度计量）的余弦。

7） 泛型宏：若实参拥有 `long double` 类型，则调用 `cosl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `cos`。否则，调用 `cosf`、若实参为复数，则该宏调用对应的复函数（`[ccosf](http://zh.cppreference.com/w/c/numeric/complex/ccos)`、`[ccos](http://zh.cppreference.com/w/c/numeric/complex/ccos)`、`[ccosl](http://zh.cppreference.com/w/c/numeric/complex/ccos)`）。

**参数**

| arg  | -    | 以弧度表示角的浮点数 |
| ---- | ---- | -------------------- |
|      |      |                      |

**返回值**

​	若不出现错误，则返回 `arg` 的余弦（*cos(arg)*），在范围 *[-1 ; +1]* 中。

​	若 `arg` 的绝对值很大，则结果可能只有少量或没有效数字。 (C99 前)

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确的结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），

- 则若参数为 ±0，则结果为 1.0
- 若参数为 ±∞，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若参数为 NaN，则返回 NaN

**注意**

​	参数为无穷大的情况不被指定为 C 中的定义域错误，但被定义为 [POSIX 中的定义域错误](http://pubs.opengroup.org/onlinepubs/9699919799/functions/cos.html)。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
int main(void)
{
    const double pi = acos(-1);
 
    // 典型用法
    printf("cos(pi/3) = %f\n", cos(pi / 3));
    printf("cos(pi/2) = %f\n", cos(pi / 2));
    printf("cos(-3*pi/4) = %f\n", cos(-3 * pi / 4));
 
    // 特殊值
    printf("cos(+0) = %f\n", cos(0.0));
    printf("cos(-0) = %f\n", cos(-0.0));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("cos(INFINITY) = %f\n", cos(INFINITY));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
cos(pi/3) = 0.500000
cos(pi/2) = 0.000000
cos(-3*pi/4) = -0.707107
cos(+0) = 1.000000
cos(-0) = 1.000000
cos(INFINITY) = -nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.5 The cos functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.5 The cos functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.5 The cos functions （第 174 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.5 The cos functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.5 The cos functions （第 239 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.5 The cos functions （第 519 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.5 The cos functions （第 220 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.5 The cos functions （第 456 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.5 The cos function

**参阅**

| [sin <br />sinf (C99)<br />sinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sin) | 计算正弦（sinxsin⁡x） (函数)         |
| ------------------------------------------------------------ | ----------------------------------- |
| [tan <br />tanf (C99)<br />tanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tan) | 计算正切（tanxtan⁡x） (函数)         |
| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡x） (函数) |
| [ccos (C99)<br />ccosf (C99)<br />ccosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccos) | 计算复数余弦 (函数)                 |
| **cos** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/cos)** |                                     |





### cosh

原址：[https://zh.cppreference.com/w/c/numeric/math/cosh](https://zh.cppreference.com/w/c/numeric/math/cosh)

作用：计算双曲余弦（{\small\cosh{x} }{\small\cosh{x} }cosh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       coshf( float arg );// (1)(C99 起)
double      cosh( double arg );// (2)
long double coshl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cosh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的双曲余弦。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `coshl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `cosh`。否则调用 `coshf`。若实参为复数，则宏调用对应的复数函数（`[ccoshf](http://zh.cppreference.com/w/c/numeric/complex/ccosh)`、`[ccosh](http://zh.cppreference.com/w/c/numeric/complex/ccosh)`、`[ccoshl](http://zh.cppreference.com/w/c/numeric/complex/ccosh)`）。

**参数**

| arg  | -    | 表示双曲角的浮点数 |
| ---- | ---- | ------------------ |
|      |      |                    |

**返回值**

若不出现错误，则返回 `arg` 的双曲余弦（*cosh(arg)* 或 

| earg +e-arg |
| ----------- |
| 2           |

）。

​	若出现上溢所致的值域错误，则返回 `+HUGE_VAL`、`+HUGE_VALF` 或 `+HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 1
- 若参数为 ±∞，则返回 +∞
- 若参数为 NaN，则返回 NaN

**注意**

​	对于 IEEE 兼容的 `double` 类型，若 *|arg| > 710.5*，则 `cosh(arg)` 上溢。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
// #pragma STDC FENV_ACCESS ON
int main(void)
{
    printf("cosh(1) = %f\ncosh(-1)= %f\n", cosh(1), cosh(-1));
    printf("log(sinh(1) + cosh(1))=%f\n", log(sinh(1) + cosh(1)));
    // 特殊值
    printf("cosh(+0) = %f\ncosh(-0) = %f\n", cosh(0.0), cosh(-0.0));
    // 错误处理
    errno=0;
    feclearexcept(FE_ALL_EXCEPT);
    printf("cosh(710.5) = %f\n", cosh(710.5));
    if(errno == ERANGE)
        perror("    errno == ERANGE");
    if(fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
cosh(1) = 1.543081
cosh(-1)= 1.543081
log(sinh(1) + cosh(1))=1.000000
cosh(+0) = 1.000000
cosh(-0) = 1.000000
cosh(710.5) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.4 The cosh functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.4 The cosh functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.4 The cosh functions （第 176 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.2.4 The cosh functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.4 The cosh functions （第 241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.4 The cosh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.4 The cosh functions （第 222 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.4 The cosh functions （第 457 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.3.1 The cosh function

**参阅**

| [sinh <br />sinhf (C99)<br />sinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sinh) | 计算双曲正弦（sinhxsinh⁡x） (函数)       |
| ------------------------------------------------------------ | --------------------------------------- |
| [tanh <br />tanhf (C99)<br />tanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tanh) | 计算双曲正切（tanhxtanh⁡x） (函数)       |
| [acosh (C99)<br />acoshf (C99)<br />acoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acosh) | 计算反双曲余弦（arcoshxarcosh⁡x） (函数) |
| [ccosh (C99)<br />ccoshf (C99)<br />ccoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccosh) | 计算复双曲余弦 (函数)                   |
| **cosh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/cosh)** |                                         |





### coshf

原址：[https://zh.cppreference.com/w/c/numeric/math/cosh](https://zh.cppreference.com/w/c/numeric/math/cosh)

作用：计算双曲余弦（{\small\cosh{x} }{\small\cosh{x} }cosh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       coshf( float arg );// (1)(C99 起)
double      cosh( double arg );// (2)
long double coshl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cosh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的双曲余弦。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `coshl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `cosh`。否则调用 `coshf`。若实参为复数，则宏调用对应的复数函数（`[ccoshf](http://zh.cppreference.com/w/c/numeric/complex/ccosh)`、`[ccosh](http://zh.cppreference.com/w/c/numeric/complex/ccosh)`、`[ccoshl](http://zh.cppreference.com/w/c/numeric/complex/ccosh)`）。

**参数**

| arg  | -    | 表示双曲角的浮点数 |
| ---- | ---- | ------------------ |
|      |      |                    |

**返回值**

若不出现错误，则返回 `arg` 的双曲余弦（*cosh(arg)* 或 

| earg +e-arg |
| ----------- |
| 2           |

）。

​	若出现上溢所致的值域错误，则返回 `+HUGE_VAL`、`+HUGE_VALF` 或 `+HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 1
- 若参数为 ±∞，则返回 +∞
- 若参数为 NaN，则返回 NaN

**注意**

​	对于 IEEE 兼容的 `double` 类型，若 *|arg| > 710.5*，则 `cosh(arg)` 上溢。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
// #pragma STDC FENV_ACCESS ON
int main(void)
{
    printf("cosh(1) = %f\ncosh(-1)= %f\n", cosh(1), cosh(-1));
    printf("log(sinh(1) + cosh(1))=%f\n", log(sinh(1) + cosh(1)));
    // 特殊值
    printf("cosh(+0) = %f\ncosh(-0) = %f\n", cosh(0.0), cosh(-0.0));
    // 错误处理
    errno=0;
    feclearexcept(FE_ALL_EXCEPT);
    printf("cosh(710.5) = %f\n", cosh(710.5));
    if(errno == ERANGE)
        perror("    errno == ERANGE");
    if(fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
cosh(1) = 1.543081
cosh(-1)= 1.543081
log(sinh(1) + cosh(1))=1.000000
cosh(+0) = 1.000000
cosh(-0) = 1.000000
cosh(710.5) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.4 The cosh functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.4 The cosh functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.4 The cosh functions （第 176 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.2.4 The cosh functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.4 The cosh functions （第 241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.4 The cosh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.4 The cosh functions （第 222 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.4 The cosh functions （第 457 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.3.1 The cosh function

**参阅**

| [sinh <br />sinhf (C99)<br />sinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sinh) | 计算双曲正弦（sinhxsinh⁡x） (函数)       |
| ------------------------------------------------------------ | --------------------------------------- |
| [tanh <br />tanhf (C99)<br />tanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tanh) | 计算双曲正切（tanhxtanh⁡x） (函数)       |
| [acosh (C99)<br />acoshf (C99)<br />acoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acosh) | 计算反双曲余弦（arcoshxarcosh⁡x） (函数) |
| [ccosh (C99)<br />ccoshf (C99)<br />ccoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccosh) | 计算复双曲余弦 (函数)                   |
| **cosh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/cosh)** |                                         |





### coshl

原址：[https://zh.cppreference.com/w/c/numeric/math/cosh](https://zh.cppreference.com/w/c/numeric/math/cosh)

作用：计算双曲余弦（{\small\cosh{x} }{\small\cosh{x} }cosh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       coshf( float arg );// (1)(C99 起)
double      cosh( double arg );// (2)
long double coshl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cosh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的双曲余弦。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `coshl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `cosh`。否则调用 `coshf`。若实参为复数，则宏调用对应的复数函数（`[ccoshf](http://zh.cppreference.com/w/c/numeric/complex/ccosh)`、`[ccosh](http://zh.cppreference.com/w/c/numeric/complex/ccosh)`、`[ccoshl](http://zh.cppreference.com/w/c/numeric/complex/ccosh)`）。

**参数**

| arg  | -    | 表示双曲角的浮点数 |
| ---- | ---- | ------------------ |
|      |      |                    |

**返回值**

若不出现错误，则返回 `arg` 的双曲余弦（*cosh(arg)* 或 

| earg +e-arg |
| ----------- |
| 2           |

）。

​	若出现上溢所致的值域错误，则返回 `+HUGE_VAL`、`+HUGE_VALF` 或 `+HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 1
- 若参数为 ±∞，则返回 +∞
- 若参数为 NaN，则返回 NaN

**注意**

​	对于 IEEE 兼容的 `double` 类型，若 *|arg| > 710.5*，则 `cosh(arg)` 上溢。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
// #pragma STDC FENV_ACCESS ON
int main(void)
{
    printf("cosh(1) = %f\ncosh(-1)= %f\n", cosh(1), cosh(-1));
    printf("log(sinh(1) + cosh(1))=%f\n", log(sinh(1) + cosh(1)));
    // 特殊值
    printf("cosh(+0) = %f\ncosh(-0) = %f\n", cosh(0.0), cosh(-0.0));
    // 错误处理
    errno=0;
    feclearexcept(FE_ALL_EXCEPT);
    printf("cosh(710.5) = %f\n", cosh(710.5));
    if(errno == ERANGE)
        perror("    errno == ERANGE");
    if(fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
cosh(1) = 1.543081
cosh(-1)= 1.543081
log(sinh(1) + cosh(1))=1.000000
cosh(+0) = 1.000000
cosh(-0) = 1.000000
cosh(710.5) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.4 The cosh functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.4 The cosh functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.4 The cosh functions （第 176 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.2.4 The cosh functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.4 The cosh functions （第 241 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.4 The cosh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.4 The cosh functions （第 222 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.4 The cosh functions （第 457 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.3.1 The cosh function

**参阅**

| [sinh <br />sinhf (C99)<br />sinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sinh) | 计算双曲正弦（sinhxsinh⁡x） (函数)       |
| ------------------------------------------------------------ | --------------------------------------- |
| [tanh <br />tanhf (C99)<br />tanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tanh) | 计算双曲正切（tanhxtanh⁡x） (函数)       |
| [acosh (C99)<br />acoshf (C99)<br />acoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acosh) | 计算反双曲余弦（arcoshxarcosh⁡x） (函数) |
| [ccosh (C99)<br />ccoshf (C99)<br />ccoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccosh) | 计算复双曲余弦 (函数)                   |
| **cosh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/cosh)** |                                         |





### cosl

原址：[https://zh.cppreference.com/w/c/numeric/math/cos](https://zh.cppreference.com/w/c/numeric/math/cos)

作用：计算余弦（{\small\cos{x} }{\small\cos{x} }cos(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       cosf( float arg );// (1)(C99 起)
double      cos( double arg );// (2)
long double cosl( long double arg );// (3)(C99 起)
_Decimal32  cosd32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  cosd64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 cosd128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define cos( arg )// (7)(C99 起)
```

1-6) 计算 `arg` （以弧度计量）的余弦。

7） 泛型宏：若实参拥有 `long double` 类型，则调用 `cosl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `cos`。否则，调用 `cosf`、若实参为复数，则该宏调用对应的复函数（`[ccosf](http://zh.cppreference.com/w/c/numeric/complex/ccos)`、`[ccos](http://zh.cppreference.com/w/c/numeric/complex/ccos)`、`[ccosl](http://zh.cppreference.com/w/c/numeric/complex/ccos)`）。

**参数**

| arg  | -    | 以弧度表示角的浮点数 |
| ---- | ---- | -------------------- |
|      |      |                      |

**返回值**

​	若不出现错误，则返回 `arg` 的余弦（*cos(arg)*），在范围 *[-1 ; +1]* 中。

​	若 `arg` 的绝对值很大，则结果可能只有少量或没有效数字。 (C99 前)

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确的结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），

- 则若参数为 ±0，则结果为 1.0
- 若参数为 ±∞，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若参数为 NaN，则返回 NaN

**注意**

​	参数为无穷大的情况不被指定为 C 中的定义域错误，但被定义为 [POSIX 中的定义域错误](http://pubs.opengroup.org/onlinepubs/9699919799/functions/cos.html)。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
int main(void)
{
    const double pi = acos(-1);
 
    // 典型用法
    printf("cos(pi/3) = %f\n", cos(pi / 3));
    printf("cos(pi/2) = %f\n", cos(pi / 2));
    printf("cos(-3*pi/4) = %f\n", cos(-3 * pi / 4));
 
    // 特殊值
    printf("cos(+0) = %f\n", cos(0.0));
    printf("cos(-0) = %f\n", cos(-0.0));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("cos(INFINITY) = %f\n", cos(INFINITY));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
cos(pi/3) = 0.500000
cos(pi/2) = 0.000000
cos(-3*pi/4) = -0.707107
cos(+0) = 1.000000
cos(-0) = 1.000000
cos(INFINITY) = -nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.5 The cos functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.5 The cos functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.5 The cos functions （第 174 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.5 The cos functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.5 The cos functions （第 239 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.5 The cos functions （第 519 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.5 The cos functions （第 220 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.5 The cos functions （第 456 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.5 The cos function

**参阅**

| [sin <br />sinf (C99)<br />sinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sin) | 计算正弦（sinxsin⁡x） (函数)         |
| ------------------------------------------------------------ | ----------------------------------- |
| [tan <br />tanf (C99)<br />tanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tan) | 计算正切（tanxtan⁡x） (函数)         |
| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡x） (函数) |
| [ccos (C99)<br />ccosf (C99)<br />ccosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccos) | 计算复数余弦 (函数)                 |
| **cos** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/cos)** |                                     |





### erf

原址：[https://zh.cppreference.com/w/c/numeric/math/erf](https://zh.cppreference.com/w/c/numeric/math/erf)

作用：计算误差函数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       erff( float arg );// (1)(C99 起)
double      erf( double arg );// (2)(C99 起)
long double erfl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define erf( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的[误差函数](https://en.wikipedia.org/wiki/Error_function)。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `erfl`。否则若 `arg` 拥有整数类型或 `double` 类型，则调用 `erf`。否则调用 `erff`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

若不出现错误，则返回 `arg` 的误差函数的值，即 2√π∫arg0e−t2dt2π∫0arge−t2dt。 若因下溢出现值域错误，则返回（舍入后的）正确结果，即 2⋅arg√π2⋅argπ。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 ±0
- 若参数为 ±∞，则返回 ±1
- 若参数为 NaN，则返回 NaN

**注解**

​	若 `|arg| < [DBL_MIN](http://zh.cppreference.com/w/c/types/limits)*([sqrt](http://zh.cppreference.com/w/c/numeric/math/sqrt)(π)/2)` 则保证下溢。

{\operatorname{erf}(\frac{x}{\sigma \sqrt{2} }){\operatorname{erf}(\frac{x}{\sigma \sqrt{2} }) 是测量结果小于与平均数相差 xx 的值的概率，其误差服从标准差为 σσ 的正态分布。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
double phi(double x1, double x2)
{
    return (erf(x2 / sqrt(2)) - erf(x1 / sqrt(2))) / 2;
}
 
int main(void)
{
    puts("正态变量概率:");
    for (int n = -4; n < 4; ++n)
        printf("[%2d:%2d]: %5.2f%%\n", n, n + 1, 100 * phi(n, n + 1));
 
    puts("特殊值:");
    printf("erf(-0) = %f\n", erf(-0.0));
    printf("erf(Inf) = %f\n", erf(INFINITY));
}
```

​	输出：

```txt
正态变量概率:
[-4:-3]:  0.13%
[-3:-2]:  2.14%
[-2:-1]: 13.59%
[-1: 0]: 34.13%
[ 0: 1]: 34.13%
[ 1: 2]: 13.59%
[ 2: 3]:  2.14%
[ 3: 4]:  0.13%
特殊值:
erf(-0) = -0.000000
erf(Inf) = 1.000000
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.8.1 The erf functions （第 249 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.1 The erf functions （第 525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.8.1 The erf functions （第 230 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.5.1 The erf functions （第 462 页）

**参阅**

| [erfc (C99)<br />erfcf (C99)<br />erfcl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/erfc) | 计算补误差函数 (函数) |
| ------------------------------------------------------------ | --------------------- |
| **erf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/erf)** |                       |

**外部链接**

[Weisstein, Eric W. "Erf."](https://mathworld.wolfram.com/Erf.html) From MathWorld--A Wolfram Web Resource。





### erfc

原址：[https://zh.cppreference.com/w/c/numeric/math/erfc](https://zh.cppreference.com/w/c/numeric/math/erfc)

作用：计算补误差函数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       erfcf( float arg );// (1)(C99 起)
double      erfc( double arg );// (2)(C99 起)
long double erfcl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define erfc( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的[补误差函数](https://en.wikipedia.org/wiki/Complementary_error_function)，即 `1.0-erf(arg)`，但对于大的 `arg` 无精度损失。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `erfcl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `erfc`。否则，调用 `erfcf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

若不出现错误，则返回 `arg` 的补误差函数的值，即 2√π∫∞arge−t2dt2π∫arg∞e−t2dt 或 1−erf(arg)1−erf⁡(arg)。

​	若出现源于下溢的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 +∞，则返回 +0
- 若参数为 -∞，则返回 2
- 若参数为 NaN，则返回 NaN

**注解**

​	对于 IEEE 兼容的 `double` 类型，若 `arg` > 26.55 则保证下溢。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
double normalCDF(double x) // Phi(-∞, x) 又称为 N(x)
{
    return erfc(-x / sqrt(2)) / 2;
}
int main(void)
{
    puts("正态累积分布函数:");
    for (double n = 0; n < 1; n += 0.1)
        printf("normalCDF(%.2f) %5.2f%%\n", n, 100 * normalCDF(n));
 
    printf("特殊值:\n"
           "erfc(-Inf) = %f\n"
           "erfc(Inf) = %f\n",
           erfc(-INFINITY),
           erfc(INFINITY));
}
```

​	输出：

```txt
正态累积分布函数:
normalCDF(0.00) 50.00%
normalCDF(0.10) 53.98%
normalCDF(0.20) 57.93%
normalCDF(0.30) 61.79%
normalCDF(0.40) 65.54%
normalCDF(0.50) 69.15%
normalCDF(0.60) 72.57%
normalCDF(0.70) 75.80%
normalCDF(0.80) 78.81%
normalCDF(0.90) 81.59%
normalCDF(1.00) 84.13%
special values:
erfc(-Inf) = 2.000000
erfc(Inf) = 0.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.8.2 The erfc functions （第 249-250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.2 The erfc functions （第 525 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.8.2 The erfc functions （第 249-250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.2 The erfc functions （第 525 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.8.2 The erfc functions （第 249-250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.2 The erfc functions （第 525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.8.2 The erfc functions （第 230 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.5.2 The erfc functions （第 462 页）

**参阅**

| [erf (C99)<br />erff (C99)<br />erfl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/erf) | 计算误差函数 (函数) |
| ------------------------------------------------------------ | ------------------- |
| **erfc** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/erfc)** |                     |

**外部链接**

[Weisstein, Eric W. "Erfc."](https://mathworld.wolfram.com/Erfc.html) 来自 MathWorld--A Wolfram Web Resource。





### erfcf

原址：[https://zh.cppreference.com/w/c/numeric/math/erfc](https://zh.cppreference.com/w/c/numeric/math/erfc)

作用：计算补误差函数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       erfcf( float arg );// (1)(C99 起)
double      erfc( double arg );// (2)(C99 起)
long double erfcl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define erfc( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的[补误差函数](https://en.wikipedia.org/wiki/Complementary_error_function)，即 `1.0-erf(arg)`，但对于大的 `arg` 无精度损失。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `erfcl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `erfc`。否则，调用 `erfcf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

若不出现错误，则返回 `arg` 的补误差函数的值，即 2√π∫∞arge−t2dt2π∫arg∞e−t2dt 或 1−erf(arg)1−erf⁡(arg)。

​	若出现源于下溢的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 +∞，则返回 +0
- 若参数为 -∞，则返回 2
- 若参数为 NaN，则返回 NaN

**注解**

​	对于 IEEE 兼容的 `double` 类型，若 `arg` > 26.55 则保证下溢。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
double normalCDF(double x) // Phi(-∞, x) 又称为 N(x)
{
    return erfc(-x / sqrt(2)) / 2;
}
int main(void)
{
    puts("正态累积分布函数:");
    for (double n = 0; n < 1; n += 0.1)
        printf("normalCDF(%.2f) %5.2f%%\n", n, 100 * normalCDF(n));
 
    printf("特殊值:\n"
           "erfc(-Inf) = %f\n"
           "erfc(Inf) = %f\n",
           erfc(-INFINITY),
           erfc(INFINITY));
}
```

​	输出：

```txt
正态累积分布函数:
normalCDF(0.00) 50.00%
normalCDF(0.10) 53.98%
normalCDF(0.20) 57.93%
normalCDF(0.30) 61.79%
normalCDF(0.40) 65.54%
normalCDF(0.50) 69.15%
normalCDF(0.60) 72.57%
normalCDF(0.70) 75.80%
normalCDF(0.80) 78.81%
normalCDF(0.90) 81.59%
normalCDF(1.00) 84.13%
special values:
erfc(-Inf) = 2.000000
erfc(Inf) = 0.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.8.2 The erfc functions （第 249-250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.2 The erfc functions （第 525 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.8.2 The erfc functions （第 249-250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.2 The erfc functions （第 525 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.8.2 The erfc functions （第 249-250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.2 The erfc functions （第 525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.8.2 The erfc functions （第 230 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.5.2 The erfc functions （第 462 页）

**参阅**

| [erf (C99)<br />erff (C99)<br />erfl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/erf) | 计算误差函数 (函数) |
| ------------------------------------------------------------ | ------------------- |
| **erfc** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/erfc)** |                     |

**外部链接**

[Weisstein, Eric W. "Erfc."](https://mathworld.wolfram.com/Erfc.html) 来自 MathWorld--A Wolfram Web Resource。





### erfcl

原址：[https://zh.cppreference.com/w/c/numeric/math/erfc](https://zh.cppreference.com/w/c/numeric/math/erfc)

作用：计算补误差函数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       erfcf( float arg );// (1)(C99 起)
double      erfc( double arg );// (2)(C99 起)
long double erfcl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define erfc( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的[补误差函数](https://en.wikipedia.org/wiki/Complementary_error_function)，即 `1.0-erf(arg)`，但对于大的 `arg` 无精度损失。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `erfcl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `erfc`。否则，调用 `erfcf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

若不出现错误，则返回 `arg` 的补误差函数的值，即 2√π∫∞arge−t2dt2π∫arg∞e−t2dt 或 1−erf(arg)1−erf⁡(arg)。

​	若出现源于下溢的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 +∞，则返回 +0
- 若参数为 -∞，则返回 2
- 若参数为 NaN，则返回 NaN

**注解**

​	对于 IEEE 兼容的 `double` 类型，若 `arg` > 26.55 则保证下溢。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
double normalCDF(double x) // Phi(-∞, x) 又称为 N(x)
{
    return erfc(-x / sqrt(2)) / 2;
}
int main(void)
{
    puts("正态累积分布函数:");
    for (double n = 0; n < 1; n += 0.1)
        printf("normalCDF(%.2f) %5.2f%%\n", n, 100 * normalCDF(n));
 
    printf("特殊值:\n"
           "erfc(-Inf) = %f\n"
           "erfc(Inf) = %f\n",
           erfc(-INFINITY),
           erfc(INFINITY));
}
```

​	输出：

```txt
正态累积分布函数:
normalCDF(0.00) 50.00%
normalCDF(0.10) 53.98%
normalCDF(0.20) 57.93%
normalCDF(0.30) 61.79%
normalCDF(0.40) 65.54%
normalCDF(0.50) 69.15%
normalCDF(0.60) 72.57%
normalCDF(0.70) 75.80%
normalCDF(0.80) 78.81%
normalCDF(0.90) 81.59%
normalCDF(1.00) 84.13%
special values:
erfc(-Inf) = 2.000000
erfc(Inf) = 0.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.8.2 The erfc functions （第 249-250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.2 The erfc functions （第 525 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.8.2 The erfc functions （第 249-250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.2 The erfc functions （第 525 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.8.2 The erfc functions （第 249-250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.2 The erfc functions （第 525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.8.2 The erfc functions （第 230 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.5.2 The erfc functions （第 462 页）

**参阅**

| [erf (C99)<br />erff (C99)<br />erfl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/erf) | 计算误差函数 (函数) |
| ------------------------------------------------------------ | ------------------- |
| **erfc** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/erfc)** |                     |

**外部链接**

[Weisstein, Eric W. "Erfc."](https://mathworld.wolfram.com/Erfc.html) 来自 MathWorld--A Wolfram Web Resource。





### erff

原址：[https://zh.cppreference.com/w/c/numeric/math/erf](https://zh.cppreference.com/w/c/numeric/math/erf)

作用：计算误差函数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       erff( float arg );// (1)(C99 起)
double      erf( double arg );// (2)(C99 起)
long double erfl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define erf( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的[误差函数](https://en.wikipedia.org/wiki/Error_function)。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `erfl`。否则若 `arg` 拥有整数类型或 `double` 类型，则调用 `erf`。否则调用 `erff`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

若不出现错误，则返回 `arg` 的误差函数的值，即 2√π∫arg0e−t2dt2π∫0arge−t2dt。 若因下溢出现值域错误，则返回（舍入后的）正确结果，即 2⋅arg√π2⋅argπ。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 ±0
- 若参数为 ±∞，则返回 ±1
- 若参数为 NaN，则返回 NaN

**注解**

​	若 `|arg| < [DBL_MIN](http://zh.cppreference.com/w/c/types/limits)*([sqrt](http://zh.cppreference.com/w/c/numeric/math/sqrt)(π)/2)` 则保证下溢。

{\operatorname{erf}(\frac{x}{\sigma \sqrt{2} }){\operatorname{erf}(\frac{x}{\sigma \sqrt{2} }) 是测量结果小于与平均数相差 xx 的值的概率，其误差服从标准差为 σσ 的正态分布。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
double phi(double x1, double x2)
{
    return (erf(x2 / sqrt(2)) - erf(x1 / sqrt(2))) / 2;
}
 
int main(void)
{
    puts("正态变量概率:");
    for (int n = -4; n < 4; ++n)
        printf("[%2d:%2d]: %5.2f%%\n", n, n + 1, 100 * phi(n, n + 1));
 
    puts("特殊值:");
    printf("erf(-0) = %f\n", erf(-0.0));
    printf("erf(Inf) = %f\n", erf(INFINITY));
}
```

​	输出：

```txt
正态变量概率:
[-4:-3]:  0.13%
[-3:-2]:  2.14%
[-2:-1]: 13.59%
[-1: 0]: 34.13%
[ 0: 1]: 34.13%
[ 1: 2]: 13.59%
[ 2: 3]:  2.14%
[ 3: 4]:  0.13%
特殊值:
erf(-0) = -0.000000
erf(Inf) = 1.000000
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.8.1 The erf functions （第 249 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.1 The erf functions （第 525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.8.1 The erf functions （第 230 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.5.1 The erf functions （第 462 页）

**参阅**

| [erfc (C99)<br />erfcf (C99)<br />erfcl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/erfc) | 计算补误差函数 (函数) |
| ------------------------------------------------------------ | --------------------- |
| **erf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/erf)** |                       |

**外部链接**

[Weisstein, Eric W. "Erf."](https://mathworld.wolfram.com/Erf.html) From MathWorld--A Wolfram Web Resource。





### erfl

原址：[https://zh.cppreference.com/w/c/numeric/math/erf](https://zh.cppreference.com/w/c/numeric/math/erf)

作用：计算误差函数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       erff( float arg );// (1)(C99 起)
double      erf( double arg );// (2)(C99 起)
long double erfl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define erf( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的[误差函数](https://en.wikipedia.org/wiki/Error_function)。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `erfl`。否则若 `arg` 拥有整数类型或 `double` 类型，则调用 `erf`。否则调用 `erff`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

若不出现错误，则返回 `arg` 的误差函数的值，即 2√π∫arg0e−t2dt2π∫0arge−t2dt。 若因下溢出现值域错误，则返回（舍入后的）正确结果，即 2⋅arg√π2⋅argπ。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 ±0
- 若参数为 ±∞，则返回 ±1
- 若参数为 NaN，则返回 NaN

**注解**

​	若 `|arg| < [DBL_MIN](http://zh.cppreference.com/w/c/types/limits)*([sqrt](http://zh.cppreference.com/w/c/numeric/math/sqrt)(π)/2)` 则保证下溢。

{\operatorname{erf}(\frac{x}{\sigma \sqrt{2} }){\operatorname{erf}(\frac{x}{\sigma \sqrt{2} }) 是测量结果小于与平均数相差 xx 的值的概率，其误差服从标准差为 σσ 的正态分布。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
double phi(double x1, double x2)
{
    return (erf(x2 / sqrt(2)) - erf(x1 / sqrt(2))) / 2;
}
 
int main(void)
{
    puts("正态变量概率:");
    for (int n = -4; n < 4; ++n)
        printf("[%2d:%2d]: %5.2f%%\n", n, n + 1, 100 * phi(n, n + 1));
 
    puts("特殊值:");
    printf("erf(-0) = %f\n", erf(-0.0));
    printf("erf(Inf) = %f\n", erf(INFINITY));
}
```

​	输出：

```txt
正态变量概率:
[-4:-3]:  0.13%
[-3:-2]:  2.14%
[-2:-1]: 13.59%
[-1: 0]: 34.13%
[ 0: 1]: 34.13%
[ 1: 2]: 13.59%
[ 2: 3]:  2.14%
[ 3: 4]:  0.13%
特殊值:
erf(-0) = -0.000000
erf(Inf) = 1.000000
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.8.1 The erf functions （第 249 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.1 The erf functions （第 525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.8.1 The erf functions （第 230 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.5.1 The erf functions （第 462 页）

**参阅**

| [erfc (C99)<br />erfcf (C99)<br />erfcl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/erfc) | 计算补误差函数 (函数) |
| ------------------------------------------------------------ | --------------------- |
| **erf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/erf)** |                       |

**外部链接**

[Weisstein, Eric W. "Erf."](https://mathworld.wolfram.com/Erf.html) From MathWorld--A Wolfram Web Resource。





### exp

原址：[https://zh.cppreference.com/w/c/numeric/math/exp](https://zh.cppreference.com/w/c/numeric/math/exp)

作用：计算 e 的给定次幂（{\small e^x}{\small e^x}ex）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       expf( float arg );// (1)(C99 起)
double      exp( double arg );// (2)
long double expl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define exp( arg )// (4)(C99 起)
```

1-3) 计算 *e*（[欧拉数](https://en.wikipedia.org/wiki/E_(mathematical_constant))，`2.7182818...`）的 `arg` 次幂。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `expl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `exp`。否则调用 `expf`。若 `arg` 为复数或虚数，则宏调用对应的复数函数（`[cexpf](http://zh.cppreference.com/w/c/numeric/complex/cexp)`、`[cexp](http://zh.cppreference.com/w/c/numeric/complex/cexp)`、`[cexpl](http://zh.cppreference.com/w/c/numeric/complex/cexp)`）。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的底 *e* 指数（*earg
*）。

​	若出现上溢所致的值域错误，则返回 `+HUGE_VAL`、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 1
- 若参数为 -∞，则返回 +0
- 若参数为 +∞，则返回 +∞
- 若参数为 NaN，则返回 NaN

**注意**

​	对于 IEEE 兼容的 `double` 类型，若 *709.8 < arg* 则保证上溢，而若 *arg < -708.4* 则保证下溢。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("exp(1) = %f\n", exp(1));
    printf("FV of $100, continuously compounded at 3%% for 1 year = %f\n",
            100*exp(0.03));
    // 特殊值
    printf("exp(-0) = %f\n", exp(-0.0));
    printf("exp(-Inf) = %f\n", exp(-INFINITY));
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("exp(710) = %f\n", exp(710));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
exp(1) = 2.718282
FV of $100, continuously compounded at 3% for 1 year = 103.045453
exp(-0) = 1.000000
exp(-Inf) = 0.000000
exp(710) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.1 The exp functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.1 The exp functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.1 The exp functions （第 175 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.1 The exp functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.1 The exp functions （第 242 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.1 The exp functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.1 The exp functions （第 223 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.1 The exp functions （第 458 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.1 The exp function

**参阅**

| [exp2 (C99)<br />exp2f (C99)<br />exp2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp2) | 计算 *2* 的给定次幂（2x2x） (函数)         |
| ------------------------------------------------------------ | ------------------------------------------ |
| [expm1 (C99)<br />expm1f (C99)<br />expm1l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/expm1) | 计算 *e* 的给定次幂减一（ex−1ex−1） (函数) |
| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡x） (函数)  |
| [cexp (C99)<br />cexpf (C99)<br />cexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cexp) | 计算复数的 e 底指数 (函数)                 |
| **exp** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/exp)** |                                            |





### exp2

原址：[https://zh.cppreference.com/w/c/numeric/math/exp2](https://zh.cppreference.com/w/c/numeric/math/exp2)

作用：计算 2 的给定次幂（{\small 2^x}{\small 2^x}2x）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       exp2f( float n );// (1)(C99 起)
double      exp2( double n );// (2)(C99 起)
long double exp2l( long double n );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define exp2( n )// (4)(C99 起)
```

1-3) 计算 2 的给定 `n` 次幂。

4） 泛型宏，若 `n` 拥有 `long double` 类型，则调用 `exp2l`。否则，若 `n` 用有整数类型或 `double` 类型，则调用 `exp2`。否则调用 `exp2f`。

**参数**

| n    | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `n` 的底 *2* 指数（*2n
*）。

​	若出现上溢所致的值域错误，则返回 [+HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 1
- 若参数为 -∞，则返回 +0
- 若参数为 +∞，则返回 +∞
- 若参数为 NaN，则返回 NaN

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
#pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("exp2(5) = %f\n", exp2(5));
    printf("exp2(0.5) = %f\n", exp2(0.5));
    printf("exp2(-4) = %f\n", exp2(-4));
    // 特殊值
    printf("exp2(-0.9) = %f\n", exp2(-0.9));
    printf("exp2(-Inf) = %f\n", exp2(-INFINITY));
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("exp2(1024) = %f\n", exp2(1024));
    if(errno == ERANGE)
        perror("    errno == ERANGE");
    if(fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
exp2(5) = 32.000000
exp2(0.5) = 1.414214
exp2(-4) = 0.062500
exp2(-0.9) = 0.535887
exp2(-Inf) = 0.000000
exp2(1024) = Inf
    errno == ERANGE: Result too large
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.2 The exp2 functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.2 The exp2 functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.2 The exp2 functions （第 177 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.2 The exp2 functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.2 The exp2 functions （第 242-243 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.2 The exp2 functions （第 521 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.2 The exp2 functions （第 223 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.2 The exp2 functions （第 458 页）

**参阅**

| [exp <br />expf (C99)<br />expl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp) | 计算 *e* 的给定次幂（exex） (函数)         |
| ------------------------------------------------------------ | ------------------------------------------ |
| [expm1 (C99)<br />expm1f (C99)<br />expm1l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/expm1) | 计算 *e* 的给定次幂减一（ex−1ex−1） (函数) |
| [log2 (C99)<br />log2f (C99)<br />log2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log2) | 计算底为 *2* 的对数（log2xlog2⁡x） (函数)   |
| **exp2** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/exp2)** |                                            |





### exp2f

原址：[https://zh.cppreference.com/w/c/numeric/math/exp2](https://zh.cppreference.com/w/c/numeric/math/exp2)

作用：计算 2 的给定次幂（{\small 2^x}{\small 2^x}2x）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       exp2f( float n );// (1)(C99 起)
double      exp2( double n );// (2)(C99 起)
long double exp2l( long double n );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define exp2( n )// (4)(C99 起)
```

1-3) 计算 2 的给定 `n` 次幂。

4） 泛型宏，若 `n` 拥有 `long double` 类型，则调用 `exp2l`。否则，若 `n` 用有整数类型或 `double` 类型，则调用 `exp2`。否则调用 `exp2f`。

**参数**

| n    | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `n` 的底 *2* 指数（*2n
*）。

​	若出现上溢所致的值域错误，则返回 [+HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 1
- 若参数为 -∞，则返回 +0
- 若参数为 +∞，则返回 +∞
- 若参数为 NaN，则返回 NaN

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
#pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("exp2(5) = %f\n", exp2(5));
    printf("exp2(0.5) = %f\n", exp2(0.5));
    printf("exp2(-4) = %f\n", exp2(-4));
    // 特殊值
    printf("exp2(-0.9) = %f\n", exp2(-0.9));
    printf("exp2(-Inf) = %f\n", exp2(-INFINITY));
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("exp2(1024) = %f\n", exp2(1024));
    if(errno == ERANGE)
        perror("    errno == ERANGE");
    if(fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
exp2(5) = 32.000000
exp2(0.5) = 1.414214
exp2(-4) = 0.062500
exp2(-0.9) = 0.535887
exp2(-Inf) = 0.000000
exp2(1024) = Inf
    errno == ERANGE: Result too large
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.2 The exp2 functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.2 The exp2 functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.2 The exp2 functions （第 177 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.2 The exp2 functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.2 The exp2 functions （第 242-243 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.2 The exp2 functions （第 521 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.2 The exp2 functions （第 223 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.2 The exp2 functions （第 458 页）

**参阅**

| [exp <br />expf (C99)<br />expl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp) | 计算 *e* 的给定次幂（exex） (函数)         |
| ------------------------------------------------------------ | ------------------------------------------ |
| [expm1 (C99)<br />expm1f (C99)<br />expm1l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/expm1) | 计算 *e* 的给定次幂减一（ex−1ex−1） (函数) |
| [log2 (C99)<br />log2f (C99)<br />log2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log2) | 计算底为 *2* 的对数（log2xlog2⁡x） (函数)   |
| **exp2** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/exp2)** |                                            |





### exp2l

原址：[https://zh.cppreference.com/w/c/numeric/math/exp2](https://zh.cppreference.com/w/c/numeric/math/exp2)

作用：计算 2 的给定次幂（{\small 2^x}{\small 2^x}2x）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       exp2f( float n );// (1)(C99 起)
double      exp2( double n );// (2)(C99 起)
long double exp2l( long double n );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define exp2( n )// (4)(C99 起)
```

1-3) 计算 2 的给定 `n` 次幂。

4） 泛型宏，若 `n` 拥有 `long double` 类型，则调用 `exp2l`。否则，若 `n` 用有整数类型或 `double` 类型，则调用 `exp2`。否则调用 `exp2f`。

**参数**

| n    | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `n` 的底 *2* 指数（*2n
*）。

​	若出现上溢所致的值域错误，则返回 [+HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 1
- 若参数为 -∞，则返回 +0
- 若参数为 +∞，则返回 +∞
- 若参数为 NaN，则返回 NaN

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
#pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("exp2(5) = %f\n", exp2(5));
    printf("exp2(0.5) = %f\n", exp2(0.5));
    printf("exp2(-4) = %f\n", exp2(-4));
    // 特殊值
    printf("exp2(-0.9) = %f\n", exp2(-0.9));
    printf("exp2(-Inf) = %f\n", exp2(-INFINITY));
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("exp2(1024) = %f\n", exp2(1024));
    if(errno == ERANGE)
        perror("    errno == ERANGE");
    if(fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
exp2(5) = 32.000000
exp2(0.5) = 1.414214
exp2(-4) = 0.062500
exp2(-0.9) = 0.535887
exp2(-Inf) = 0.000000
exp2(1024) = Inf
    errno == ERANGE: Result too large
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.2 The exp2 functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.2 The exp2 functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.2 The exp2 functions （第 177 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.2 The exp2 functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.2 The exp2 functions （第 242-243 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.2 The exp2 functions （第 521 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.2 The exp2 functions （第 223 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.2 The exp2 functions （第 458 页）

**参阅**

| [exp <br />expf (C99)<br />expl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp) | 计算 *e* 的给定次幂（exex） (函数)         |
| ------------------------------------------------------------ | ------------------------------------------ |
| [expm1 (C99)<br />expm1f (C99)<br />expm1l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/expm1) | 计算 *e* 的给定次幂减一（ex−1ex−1） (函数) |
| [log2 (C99)<br />log2f (C99)<br />log2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log2) | 计算底为 *2* 的对数（log2xlog2⁡x） (函数)   |
| **exp2** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/exp2)** |                                            |





### expf

原址：[https://zh.cppreference.com/w/c/numeric/math/exp](https://zh.cppreference.com/w/c/numeric/math/exp)

作用：计算 e 的给定次幂（{\small e^x}{\small e^x}ex）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       expf( float arg );// (1)(C99 起)
double      exp( double arg );// (2)
long double expl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define exp( arg )// (4)(C99 起)
```

1-3) 计算 *e*（[欧拉数](https://en.wikipedia.org/wiki/E_(mathematical_constant))，`2.7182818...`）的 `arg` 次幂。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `expl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `exp`。否则调用 `expf`。若 `arg` 为复数或虚数，则宏调用对应的复数函数（`[cexpf](http://zh.cppreference.com/w/c/numeric/complex/cexp)`、`[cexp](http://zh.cppreference.com/w/c/numeric/complex/cexp)`、`[cexpl](http://zh.cppreference.com/w/c/numeric/complex/cexp)`）。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的底 *e* 指数（*earg
*）。

​	若出现上溢所致的值域错误，则返回 `+HUGE_VAL`、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 1
- 若参数为 -∞，则返回 +0
- 若参数为 +∞，则返回 +∞
- 若参数为 NaN，则返回 NaN

**注意**

​	对于 IEEE 兼容的 `double` 类型，若 *709.8 < arg* 则保证上溢，而若 *arg < -708.4* 则保证下溢。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("exp(1) = %f\n", exp(1));
    printf("FV of $100, continuously compounded at 3%% for 1 year = %f\n",
            100*exp(0.03));
    // 特殊值
    printf("exp(-0) = %f\n", exp(-0.0));
    printf("exp(-Inf) = %f\n", exp(-INFINITY));
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("exp(710) = %f\n", exp(710));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
exp(1) = 2.718282
FV of $100, continuously compounded at 3% for 1 year = 103.045453
exp(-0) = 1.000000
exp(-Inf) = 0.000000
exp(710) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.1 The exp functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.1 The exp functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.1 The exp functions （第 175 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.1 The exp functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.1 The exp functions （第 242 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.1 The exp functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.1 The exp functions （第 223 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.1 The exp functions （第 458 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.1 The exp function

**参阅**

| [exp2 (C99)<br />exp2f (C99)<br />exp2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp2) | 计算 *2* 的给定次幂（2x2x） (函数)         |
| ------------------------------------------------------------ | ------------------------------------------ |
| [expm1 (C99)<br />expm1f (C99)<br />expm1l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/expm1) | 计算 *e* 的给定次幂减一（ex−1ex−1） (函数) |
| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡x） (函数)  |
| [cexp (C99)<br />cexpf (C99)<br />cexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cexp) | 计算复数的 e 底指数 (函数)                 |
| **exp** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/exp)** |                                            |





### expl

原址：[https://zh.cppreference.com/w/c/numeric/math/exp](https://zh.cppreference.com/w/c/numeric/math/exp)

作用：计算 e 的给定次幂（{\small e^x}{\small e^x}ex）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       expf( float arg );// (1)(C99 起)
double      exp( double arg );// (2)
long double expl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define exp( arg )// (4)(C99 起)
```

1-3) 计算 *e*（[欧拉数](https://en.wikipedia.org/wiki/E_(mathematical_constant))，`2.7182818...`）的 `arg` 次幂。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `expl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `exp`。否则调用 `expf`。若 `arg` 为复数或虚数，则宏调用对应的复数函数（`[cexpf](http://zh.cppreference.com/w/c/numeric/complex/cexp)`、`[cexp](http://zh.cppreference.com/w/c/numeric/complex/cexp)`、`[cexpl](http://zh.cppreference.com/w/c/numeric/complex/cexp)`）。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的底 *e* 指数（*earg
*）。

​	若出现上溢所致的值域错误，则返回 `+HUGE_VAL`、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 1
- 若参数为 -∞，则返回 +0
- 若参数为 +∞，则返回 +∞
- 若参数为 NaN，则返回 NaN

**注意**

​	对于 IEEE 兼容的 `double` 类型，若 *709.8 < arg* 则保证上溢，而若 *arg < -708.4* 则保证下溢。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("exp(1) = %f\n", exp(1));
    printf("FV of $100, continuously compounded at 3%% for 1 year = %f\n",
            100*exp(0.03));
    // 特殊值
    printf("exp(-0) = %f\n", exp(-0.0));
    printf("exp(-Inf) = %f\n", exp(-INFINITY));
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("exp(710) = %f\n", exp(710));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
exp(1) = 2.718282
FV of $100, continuously compounded at 3% for 1 year = 103.045453
exp(-0) = 1.000000
exp(-Inf) = 0.000000
exp(710) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.1 The exp functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.1 The exp functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.1 The exp functions （第 175 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.1 The exp functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.1 The exp functions （第 242 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.1 The exp functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.1 The exp functions （第 223 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.1 The exp functions （第 458 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.1 The exp function

**参阅**

| [exp2 (C99)<br />exp2f (C99)<br />exp2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp2) | 计算 *2* 的给定次幂（2x2x） (函数)         |
| ------------------------------------------------------------ | ------------------------------------------ |
| [expm1 (C99)<br />expm1f (C99)<br />expm1l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/expm1) | 计算 *e* 的给定次幂减一（ex−1ex−1） (函数) |
| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡x） (函数)  |
| [cexp (C99)<br />cexpf (C99)<br />cexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cexp) | 计算复数的 e 底指数 (函数)                 |
| **exp** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/exp)** |                                            |





### expm1

原址：[https://zh.cppreference.com/w/c/numeric/math/expm1](https://zh.cppreference.com/w/c/numeric/math/expm1)

作用：计算 e 的给定次幂减一（{\small e^x-1}{\small e^x-1}ex-1）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       expm1f( float arg );// (1)(C99 起)
double      expm1( double arg );// (2)(C99 起)
long double expm1l( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define expm1( arg )// (4)(C99 起)
```

1-3) 计算 *e*（欧拉数，`2.7182818`）的给定 `arg` 次幂减 `1.0`。若 `arg` 接近零，则此函数比表达式 `[exp](http://zh.cppreference.com/w/c/numeric/math/exp)(arg)-1.0` 更精确。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `expm1l`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `expm1`。否则调用 `expm1f`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误则返回 *earg
-1*。

​	若出现上溢所致的值域错误，则返回 [+HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 math_errhandling 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回不修改的参数
- 若参数为 -∞，则返回 -1
- 若参数为 +∞，则返回 +∞
- 若参数为 NaN，则返回 NaN

**注意**

​	函数 `expm1` 和 [log1p](https://zh.cppreference.com/w/c/numeric/math/log1p) 对于金融计算有用：例如在计算小的日利率时：*(1+x)n
-1* 能表示为 `expm1(n * [log1p](http://zh.cppreference.com/w/c/numeric/math/log1p)(x))`。这些函数亦简化书写精确的反双曲函数。

​	对于 IEEE 兼容的 `double` 类型，若 *709.8 < arg* 则保证上溢。

**注意**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
int main(void)
{
    printf("expm1(1) = %f\n", expm1(1));
    printf("Interest earned in 2 days on $100, compounded daily at 1%%\n"
           " on a 30/360 calendar = %f\n",
           100*expm1(2*log1p(0.01/360)));
    printf("exp(1e-16)-1 = %g, but expm1(1e-16) = %g\n",
           exp(1e-16)-1, expm1(1e-16));
    // 特殊值
    printf("expm1(-0) = %f\n", expm1(-0.0));
    printf("expm1(-Inf) = %f\n", expm1(-INFINITY));
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("expm1(710) = %f\n", expm1(710));
    if(errno == ERANGE)
        perror("    errno == ERANGE");
    if(fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
expm1(1) = 1.718282
Interest earned in 2 days on $100, compounded daily at 1%
 on a 30/360 calendar = 0.005556
exp(1e-16)-1 = 0, but expm1(1e-16) = 1e-16
expm1(-0) = -0.000000
expm1(-Inf) = -1.000000
expm1(710) = inf
    errno == ERANGE: Result too large
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.3 The expm1 functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.3 The expm1 functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.3 The expm1 functions （第 177 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.3 The expm1 functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.3 The expm1 functions （第 243 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.3 The expm1 functions （第 521 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.3 The expm1 functions （第 223-224 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.3 The expm1 functions （第 458 页）

**参阅**

| [exp <br />expf (C99)<br />expl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp) | 计算 *e* 的给定次幂（exex） (函数)                           |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [exp2 (C99)<br />exp2f (C99)<br />exp2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp2) | 计算 *2* 的给定次幂（2x2x） (函数)                           |
| [log1p (C99)<br />log1pf (C99)<br />log1pl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log1p) | 计算给定数加 1 的自然对数（底为 *e*）（ln(1+x)ln⁡(1+x)） (函数) |
| **expm1** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/expm1)** |                                                              |





### expm1f

原址：[https://zh.cppreference.com/w/c/numeric/math/expm1](https://zh.cppreference.com/w/c/numeric/math/expm1)

作用：计算 e 的给定次幂减一（{\small e^x-1}{\small e^x-1}ex-1）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       expm1f( float arg );// (1)(C99 起)
double      expm1( double arg );// (2)(C99 起)
long double expm1l( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define expm1( arg )// (4)(C99 起)
```

1-3) 计算 *e*（欧拉数，`2.7182818`）的给定 `arg` 次幂减 `1.0`。若 `arg` 接近零，则此函数比表达式 `[exp](http://zh.cppreference.com/w/c/numeric/math/exp)(arg)-1.0` 更精确。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `expm1l`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `expm1`。否则调用 `expm1f`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误则返回 *earg
-1*。

​	若出现上溢所致的值域错误，则返回 [+HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 math_errhandling 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回不修改的参数
- 若参数为 -∞，则返回 -1
- 若参数为 +∞，则返回 +∞
- 若参数为 NaN，则返回 NaN

**注意**

​	函数 `expm1` 和 [log1p](https://zh.cppreference.com/w/c/numeric/math/log1p) 对于金融计算有用：例如在计算小的日利率时：*(1+x)n
-1* 能表示为 `expm1(n * [log1p](http://zh.cppreference.com/w/c/numeric/math/log1p)(x))`。这些函数亦简化书写精确的反双曲函数。

​	对于 IEEE 兼容的 `double` 类型，若 *709.8 < arg* 则保证上溢。

**注意**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
int main(void)
{
    printf("expm1(1) = %f\n", expm1(1));
    printf("Interest earned in 2 days on $100, compounded daily at 1%%\n"
           " on a 30/360 calendar = %f\n",
           100*expm1(2*log1p(0.01/360)));
    printf("exp(1e-16)-1 = %g, but expm1(1e-16) = %g\n",
           exp(1e-16)-1, expm1(1e-16));
    // 特殊值
    printf("expm1(-0) = %f\n", expm1(-0.0));
    printf("expm1(-Inf) = %f\n", expm1(-INFINITY));
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("expm1(710) = %f\n", expm1(710));
    if(errno == ERANGE)
        perror("    errno == ERANGE");
    if(fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
expm1(1) = 1.718282
Interest earned in 2 days on $100, compounded daily at 1%
 on a 30/360 calendar = 0.005556
exp(1e-16)-1 = 0, but expm1(1e-16) = 1e-16
expm1(-0) = -0.000000
expm1(-Inf) = -1.000000
expm1(710) = inf
    errno == ERANGE: Result too large
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.3 The expm1 functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.3 The expm1 functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.3 The expm1 functions （第 177 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.3 The expm1 functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.3 The expm1 functions （第 243 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.3 The expm1 functions （第 521 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.3 The expm1 functions （第 223-224 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.3 The expm1 functions （第 458 页）

**参阅**

| [exp <br />expf (C99)<br />expl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp) | 计算 *e* 的给定次幂（exex） (函数)                           |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [exp2 (C99)<br />exp2f (C99)<br />exp2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp2) | 计算 *2* 的给定次幂（2x2x） (函数)                           |
| [log1p (C99)<br />log1pf (C99)<br />log1pl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log1p) | 计算给定数加 1 的自然对数（底为 *e*）（ln(1+x)ln⁡(1+x)） (函数) |
| **expm1** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/expm1)** |                                                              |





### expm1l

原址：[https://zh.cppreference.com/w/c/numeric/math/expm1](https://zh.cppreference.com/w/c/numeric/math/expm1)

作用：计算 e 的给定次幂减一（{\small e^x-1}{\small e^x-1}ex-1）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       expm1f( float arg );// (1)(C99 起)
double      expm1( double arg );// (2)(C99 起)
long double expm1l( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define expm1( arg )// (4)(C99 起)
```

1-3) 计算 *e*（欧拉数，`2.7182818`）的给定 `arg` 次幂减 `1.0`。若 `arg` 接近零，则此函数比表达式 `[exp](http://zh.cppreference.com/w/c/numeric/math/exp)(arg)-1.0` 更精确。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `expm1l`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `expm1`。否则调用 `expm1f`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误则返回 *earg
-1*。

​	若出现上溢所致的值域错误，则返回 [+HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 math_errhandling 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回不修改的参数
- 若参数为 -∞，则返回 -1
- 若参数为 +∞，则返回 +∞
- 若参数为 NaN，则返回 NaN

**注意**

​	函数 `expm1` 和 [log1p](https://zh.cppreference.com/w/c/numeric/math/log1p) 对于金融计算有用：例如在计算小的日利率时：*(1+x)n
-1* 能表示为 `expm1(n * [log1p](http://zh.cppreference.com/w/c/numeric/math/log1p)(x))`。这些函数亦简化书写精确的反双曲函数。

​	对于 IEEE 兼容的 `double` 类型，若 *709.8 < arg* 则保证上溢。

**注意**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
int main(void)
{
    printf("expm1(1) = %f\n", expm1(1));
    printf("Interest earned in 2 days on $100, compounded daily at 1%%\n"
           " on a 30/360 calendar = %f\n",
           100*expm1(2*log1p(0.01/360)));
    printf("exp(1e-16)-1 = %g, but expm1(1e-16) = %g\n",
           exp(1e-16)-1, expm1(1e-16));
    // 特殊值
    printf("expm1(-0) = %f\n", expm1(-0.0));
    printf("expm1(-Inf) = %f\n", expm1(-INFINITY));
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("expm1(710) = %f\n", expm1(710));
    if(errno == ERANGE)
        perror("    errno == ERANGE");
    if(fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
expm1(1) = 1.718282
Interest earned in 2 days on $100, compounded daily at 1%
 on a 30/360 calendar = 0.005556
exp(1e-16)-1 = 0, but expm1(1e-16) = 1e-16
expm1(-0) = -0.000000
expm1(-Inf) = -1.000000
expm1(710) = inf
    errno == ERANGE: Result too large
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.3 The expm1 functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.3 The expm1 functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.3 The expm1 functions （第 177 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.3 The expm1 functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.3 The expm1 functions （第 243 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.3 The expm1 functions （第 521 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.3 The expm1 functions （第 223-224 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.3 The expm1 functions （第 458 页）

**参阅**

| [exp <br />expf (C99)<br />expl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp) | 计算 *e* 的给定次幂（exex） (函数)                           |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [exp2 (C99)<br />exp2f (C99)<br />exp2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp2) | 计算 *2* 的给定次幂（2x2x） (函数)                           |
| [log1p (C99)<br />log1pf (C99)<br />log1pl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log1p) | 计算给定数加 1 的自然对数（底为 *e*）（ln(1+x)ln⁡(1+x)） (函数) |
| **expm1** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/expm1)** |                                                              |





### fabs

原址：[https://zh.cppreference.com/w/c/numeric/math/fabs](https://zh.cppreference.com/w/c/numeric/math/fabs)

作用：计算浮点数的绝对值（|x|\small{|x|}|x|）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fabsf( float arg );// (1)(C99 起)
double      fabs( double arg );// (2)
long double fabsl( long double arg );// (3)(C99 起)
_Decimal32  fabsd32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  fabsd64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 fabsd128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define fabs( arith )// (7)(C99 起)
```

1-6) 计算浮点数 `arg` 的绝对值。

​	当且仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）才声明带有十进制浮点数形参的函数。 (C23 起)

7） 泛型宏：若实参拥有 `_Decimal128`、`_Decimal64`、`_Decimal32`、(C23 起)`long double`、`double` 或 `float` 类型，则分别调用 `fabsd128`、`fabsd64`、`fabsd32`、(C23 起)`fabsl`、`fabs` 或 `fabsf`。否则若实参拥有整数类型，则调用 `fabs`。否则若实参为复数，则宏调用对应的复函数（[cabsf](https://zh.cppreference.com/w/c/numeric/complex/cabs)、[cabs](https://zh.cppreference.com/w/c/numeric/complex/cabs)、[cabsl](https://zh.cppreference.com/w/c/numeric/complex/cabs)）。否则行为未定义。

**参数**

| arg   | -    | 浮点数       |
| ----- | ---- | ------------ |
| arith | -    | 浮点数或整数 |

**返回值**

​	若成功，则返回 `arg` 的绝对值（|arg||arg|）。值是准确的，且不依赖任何舍入模式。

**错误处理**

​	此函数不受制于任何指定于 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误条件。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 +0。
- 若参数为 ±∞，则返回 +∞。
- 若参数为 NaN，则返回 NaN。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
#define PI 3.14159
 
// 此数值积分假定所有面积均为正。
double integrate(double f(double),
                 double a, double b, // 假定 a < b
                 unsigned steps) // 假定 steps > 0
{
    const double dx = (b - a) / steps;
    double sum = 0.0;
    for (double x = a; x < b; x += dx)
        sum += fabs(f(x));
    return dx * sum;
}
 
int main(void)
{
    printf("fabs(+3) = %f\n", fabs(+3.0));
    printf("fabs(-3) = %f\n", fabs(-3.0));
    // 特殊值
    printf("fabs(-0) = %f\n", fabs(-0.0));
    printf("fabs(-Inf) = %f\n", fabs(-INFINITY));
 
    printf("Area under sin(x) in [-PI, PI] = %f\n", integrate(sin, -PI, PI, 5101));
}
```

​	输出：

```txt
fabs(+3) = 3.000000
fabs(-3) = 3.000000
fabs(-0) = 0.000000
fabs(-Inf) = inf
Area under sin(x) in [-PI, PI] = 4.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.7.2 The fabs functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.4.2 The fabs functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.7.2 The fabs functions （第 181 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.4.2 The fabs functions （第 382 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.7.2 The fabs functions （第 248 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.2 The fabs functions （第 524 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.7.2 The fabs functions （第 228-229 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.4.2 The fabs functions （第 460 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.6.2 The fabs function

**参阅**

| [abs <br />labs <br />llabs (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/abs) | 计算整数的绝对值（\|x\|\|x\|） (函数)                 |
| ------------------------------------------------------------ | ----------------------------------------------------- |
| [copysign (C99)<br />copysignf (C99)<br />copysignl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/copysign) | 从一个给定值的绝对值和另一个给定值的符号产生值 (函数) |
| [signbit (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/signbit) | 检查给定数是不是负数 (宏函数)                         |
| [cabs (C99)<br />cabsf (C99)<br />cabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cabs) | 计算复数的模（绝对值） (函数)                         |
| **fabs** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fabs)** |                                                       |





### fabsf

原址：[https://zh.cppreference.com/w/c/numeric/math/fabs](https://zh.cppreference.com/w/c/numeric/math/fabs)

作用：计算浮点数的绝对值（|x|\small{|x|}|x|）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fabsf( float arg );// (1)(C99 起)
double      fabs( double arg );// (2)
long double fabsl( long double arg );// (3)(C99 起)
_Decimal32  fabsd32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  fabsd64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 fabsd128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define fabs( arith )// (7)(C99 起)
```

1-6) 计算浮点数 `arg` 的绝对值。

​	当且仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）才声明带有十进制浮点数形参的函数。 (C23 起)

7） 泛型宏：若实参拥有 `_Decimal128`、`_Decimal64`、`_Decimal32`、(C23 起)`long double`、`double` 或 `float` 类型，则分别调用 `fabsd128`、`fabsd64`、`fabsd32`、(C23 起)`fabsl`、`fabs` 或 `fabsf`。否则若实参拥有整数类型，则调用 `fabs`。否则若实参为复数，则宏调用对应的复函数（[cabsf](https://zh.cppreference.com/w/c/numeric/complex/cabs)、[cabs](https://zh.cppreference.com/w/c/numeric/complex/cabs)、[cabsl](https://zh.cppreference.com/w/c/numeric/complex/cabs)）。否则行为未定义。

**参数**

| arg   | -    | 浮点数       |
| ----- | ---- | ------------ |
| arith | -    | 浮点数或整数 |

**返回值**

​	若成功，则返回 `arg` 的绝对值（|arg||arg|）。值是准确的，且不依赖任何舍入模式。

**错误处理**

​	此函数不受制于任何指定于 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误条件。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 +0。
- 若参数为 ±∞，则返回 +∞。
- 若参数为 NaN，则返回 NaN。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
#define PI 3.14159
 
// 此数值积分假定所有面积均为正。
double integrate(double f(double),
                 double a, double b, // 假定 a < b
                 unsigned steps) // 假定 steps > 0
{
    const double dx = (b - a) / steps;
    double sum = 0.0;
    for (double x = a; x < b; x += dx)
        sum += fabs(f(x));
    return dx * sum;
}
 
int main(void)
{
    printf("fabs(+3) = %f\n", fabs(+3.0));
    printf("fabs(-3) = %f\n", fabs(-3.0));
    // 特殊值
    printf("fabs(-0) = %f\n", fabs(-0.0));
    printf("fabs(-Inf) = %f\n", fabs(-INFINITY));
 
    printf("Area under sin(x) in [-PI, PI] = %f\n", integrate(sin, -PI, PI, 5101));
}
```

​	输出：

```txt
fabs(+3) = 3.000000
fabs(-3) = 3.000000
fabs(-0) = 0.000000
fabs(-Inf) = inf
Area under sin(x) in [-PI, PI] = 4.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.7.2 The fabs functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.4.2 The fabs functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.7.2 The fabs functions （第 181 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.4.2 The fabs functions （第 382 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.7.2 The fabs functions （第 248 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.2 The fabs functions （第 524 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.7.2 The fabs functions （第 228-229 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.4.2 The fabs functions （第 460 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.6.2 The fabs function

**参阅**

| [abs <br />labs <br />llabs (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/abs) | 计算整数的绝对值（\|x\|\|x\|） (函数)                 |
| ------------------------------------------------------------ | ----------------------------------------------------- |
| [copysign (C99)<br />copysignf (C99)<br />copysignl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/copysign) | 从一个给定值的绝对值和另一个给定值的符号产生值 (函数) |
| [signbit (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/signbit) | 检查给定数是不是负数 (宏函数)                         |
| [cabs (C99)<br />cabsf (C99)<br />cabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cabs) | 计算复数的模（绝对值） (函数)                         |
| **fabs** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fabs)** |                                                       |





### fabsl

原址：[https://zh.cppreference.com/w/c/numeric/math/fabs](https://zh.cppreference.com/w/c/numeric/math/fabs)

作用：计算浮点数的绝对值（|x|\small{|x|}|x|）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fabsf( float arg );// (1)(C99 起)
double      fabs( double arg );// (2)
long double fabsl( long double arg );// (3)(C99 起)
_Decimal32  fabsd32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  fabsd64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 fabsd128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define fabs( arith )// (7)(C99 起)
```

1-6) 计算浮点数 `arg` 的绝对值。

​	当且仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）才声明带有十进制浮点数形参的函数。 (C23 起)

7） 泛型宏：若实参拥有 `_Decimal128`、`_Decimal64`、`_Decimal32`、(C23 起)`long double`、`double` 或 `float` 类型，则分别调用 `fabsd128`、`fabsd64`、`fabsd32`、(C23 起)`fabsl`、`fabs` 或 `fabsf`。否则若实参拥有整数类型，则调用 `fabs`。否则若实参为复数，则宏调用对应的复函数（[cabsf](https://zh.cppreference.com/w/c/numeric/complex/cabs)、[cabs](https://zh.cppreference.com/w/c/numeric/complex/cabs)、[cabsl](https://zh.cppreference.com/w/c/numeric/complex/cabs)）。否则行为未定义。

**参数**

| arg   | -    | 浮点数       |
| ----- | ---- | ------------ |
| arith | -    | 浮点数或整数 |

**返回值**

​	若成功，则返回 `arg` 的绝对值（|arg||arg|）。值是准确的，且不依赖任何舍入模式。

**错误处理**

​	此函数不受制于任何指定于 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误条件。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 +0。
- 若参数为 ±∞，则返回 +∞。
- 若参数为 NaN，则返回 NaN。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
#define PI 3.14159
 
// 此数值积分假定所有面积均为正。
double integrate(double f(double),
                 double a, double b, // 假定 a < b
                 unsigned steps) // 假定 steps > 0
{
    const double dx = (b - a) / steps;
    double sum = 0.0;
    for (double x = a; x < b; x += dx)
        sum += fabs(f(x));
    return dx * sum;
}
 
int main(void)
{
    printf("fabs(+3) = %f\n", fabs(+3.0));
    printf("fabs(-3) = %f\n", fabs(-3.0));
    // 特殊值
    printf("fabs(-0) = %f\n", fabs(-0.0));
    printf("fabs(-Inf) = %f\n", fabs(-INFINITY));
 
    printf("Area under sin(x) in [-PI, PI] = %f\n", integrate(sin, -PI, PI, 5101));
}
```

​	输出：

```txt
fabs(+3) = 3.000000
fabs(-3) = 3.000000
fabs(-0) = 0.000000
fabs(-Inf) = inf
Area under sin(x) in [-PI, PI] = 4.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.7.2 The fabs functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.4.2 The fabs functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.7.2 The fabs functions （第 181 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.4.2 The fabs functions （第 382 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.7.2 The fabs functions （第 248 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.2 The fabs functions （第 524 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.7.2 The fabs functions （第 228-229 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.4.2 The fabs functions （第 460 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.6.2 The fabs function

**参阅**

| [abs <br />labs <br />llabs (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/abs) | 计算整数的绝对值（\|x\|\|x\|） (函数)                 |
| ------------------------------------------------------------ | ----------------------------------------------------- |
| [copysign (C99)<br />copysignf (C99)<br />copysignl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/copysign) | 从一个给定值的绝对值和另一个给定值的符号产生值 (函数) |
| [signbit (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/signbit) | 检查给定数是不是负数 (宏函数)                         |
| [cabs (C99)<br />cabsf (C99)<br />cabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cabs) | 计算复数的模（绝对值） (函数)                         |
| **fabs** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fabs)** |                                                       |





### fdim

原址：[https://zh.cppreference.com/w/c/numeric/math/fdim](https://zh.cppreference.com/w/c/numeric/math/fdim)

作用：确定两个浮点数的非负数差（max{\small\max{(0, x-y)} }max(0, x-y)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fdimf( float x, float y );// (1)(C99 起)
double      fdim( double x, double y );// (2)(C99 起)
long double fdiml( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define fdim( x, y )// (4)(C99 起)
```

1-3) 返回 `x` 与 `y` 间的正差，即若 `x>y` 则返回 `x-y`，否则（若 `x≤y`）返回 +0。

4） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `fdiml`。否则，若任何实参拥有整数类型或 `double` 类型，则调用 `fdim`。否则调用 `fdimf`。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若成功，则返回 `x` 与 `y` 间的正差。

​	若出现上溢所致的值域错误，则返回 [+HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若任一实参为 NaN，则返回 NaN。

**注意**

​	等价于 `[fmax](http://zh.cppreference.com/w/c/numeric/math/fmax)(x-y, 0)`，除了 NaN 处理要求。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("fdim(4, 1) = %f, fdim(1, 4)=%f\n", fdim(4,1), fdim(1,4));
    printf("fdim(4,-1) = %f, fdim(1,-4)=%f\n", fdim(4,-1), fdim(1,-4));
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("fdim(1e308, -1e308) = %f\n", fdim(1e308, -1e308));
    if(errno == ERANGE)
        perror("    errno == ERANGE");
    if(fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
fdim(4, 1) = 3.000000, fdim(1, 4)=0.000000
fdim(4,-1) = 5.000000, fdim(1,-4)=5.000000
fdim(1e308, -1e308) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.12.1 The fdim functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.9.1 The fdim functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.12.1 The fdim functions （第 187-188 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.9.1 The fdim functions （第 386 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.12.1 The fdim functions （第 257 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.9.1 The fdim functions （第 530 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.12.1 The fdim functions （第 238 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.9.1 The fdim functions （第 466 页）

**参阅**

| [abs <br />labs <br />llabs (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/abs) | 计算整数的绝对值（\|x\|\|x\|） (函数) |
| ------------------------------------------------------------ | ------------------------------------- |
| [fmax (C99)<br />fmaxf (C99)<br />fmaxl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmax) | 确定两个浮点数的较大者 (函数)         |
| **fdim** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fdim)** |                                       |





### fdimf

原址：[https://zh.cppreference.com/w/c/numeric/math/fdim](https://zh.cppreference.com/w/c/numeric/math/fdim)

作用：确定两个浮点数的非负数差（max{\small\max{(0, x-y)} }max(0, x-y)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fdimf( float x, float y );// (1)(C99 起)
double      fdim( double x, double y );// (2)(C99 起)
long double fdiml( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define fdim( x, y )// (4)(C99 起)
```

1-3) 返回 `x` 与 `y` 间的正差，即若 `x>y` 则返回 `x-y`，否则（若 `x≤y`）返回 +0。

4） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `fdiml`。否则，若任何实参拥有整数类型或 `double` 类型，则调用 `fdim`。否则调用 `fdimf`。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若成功，则返回 `x` 与 `y` 间的正差。

​	若出现上溢所致的值域错误，则返回 [+HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若任一实参为 NaN，则返回 NaN。

**注意**

​	等价于 `[fmax](http://zh.cppreference.com/w/c/numeric/math/fmax)(x-y, 0)`，除了 NaN 处理要求。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("fdim(4, 1) = %f, fdim(1, 4)=%f\n", fdim(4,1), fdim(1,4));
    printf("fdim(4,-1) = %f, fdim(1,-4)=%f\n", fdim(4,-1), fdim(1,-4));
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("fdim(1e308, -1e308) = %f\n", fdim(1e308, -1e308));
    if(errno == ERANGE)
        perror("    errno == ERANGE");
    if(fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
fdim(4, 1) = 3.000000, fdim(1, 4)=0.000000
fdim(4,-1) = 5.000000, fdim(1,-4)=5.000000
fdim(1e308, -1e308) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.12.1 The fdim functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.9.1 The fdim functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.12.1 The fdim functions （第 187-188 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.9.1 The fdim functions （第 386 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.12.1 The fdim functions （第 257 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.9.1 The fdim functions （第 530 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.12.1 The fdim functions （第 238 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.9.1 The fdim functions （第 466 页）

**参阅**

| [abs <br />labs <br />llabs (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/abs) | 计算整数的绝对值（\|x\|\|x\|） (函数) |
| ------------------------------------------------------------ | ------------------------------------- |
| [fmax (C99)<br />fmaxf (C99)<br />fmaxl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmax) | 确定两个浮点数的较大者 (函数)         |
| **fdim** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fdim)** |                                       |





### fdiml

原址：[https://zh.cppreference.com/w/c/numeric/math/fdim](https://zh.cppreference.com/w/c/numeric/math/fdim)

作用：确定两个浮点数的非负数差（max{\small\max{(0, x-y)} }max(0, x-y)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fdimf( float x, float y );// (1)(C99 起)
double      fdim( double x, double y );// (2)(C99 起)
long double fdiml( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define fdim( x, y )// (4)(C99 起)
```

1-3) 返回 `x` 与 `y` 间的正差，即若 `x>y` 则返回 `x-y`，否则（若 `x≤y`）返回 +0。

4） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `fdiml`。否则，若任何实参拥有整数类型或 `double` 类型，则调用 `fdim`。否则调用 `fdimf`。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若成功，则返回 `x` 与 `y` 间的正差。

​	若出现上溢所致的值域错误，则返回 [+HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若任一实参为 NaN，则返回 NaN。

**注意**

​	等价于 `[fmax](http://zh.cppreference.com/w/c/numeric/math/fmax)(x-y, 0)`，除了 NaN 处理要求。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("fdim(4, 1) = %f, fdim(1, 4)=%f\n", fdim(4,1), fdim(1,4));
    printf("fdim(4,-1) = %f, fdim(1,-4)=%f\n", fdim(4,-1), fdim(1,-4));
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("fdim(1e308, -1e308) = %f\n", fdim(1e308, -1e308));
    if(errno == ERANGE)
        perror("    errno == ERANGE");
    if(fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
fdim(4, 1) = 3.000000, fdim(1, 4)=0.000000
fdim(4,-1) = 5.000000, fdim(1,-4)=5.000000
fdim(1e308, -1e308) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.12.1 The fdim functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.9.1 The fdim functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.12.1 The fdim functions （第 187-188 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.9.1 The fdim functions （第 386 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.12.1 The fdim functions （第 257 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.9.1 The fdim functions （第 530 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.12.1 The fdim functions （第 238 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.9.1 The fdim functions （第 466 页）

**参阅**

| [abs <br />labs <br />llabs (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/abs) | 计算整数的绝对值（\|x\|\|x\|） (函数) |
| ------------------------------------------------------------ | ------------------------------------- |
| [fmax (C99)<br />fmaxf (C99)<br />fmaxl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmax) | 确定两个浮点数的较大者 (函数)         |
| **fdim** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fdim)** |                                       |





### floor

原址：[https://zh.cppreference.com/w/c/numeric/math/floor](https://zh.cppreference.com/w/c/numeric/math/floor)

作用：计算不大于给定值的最大整数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       floorf( float arg );// (1)(C99 起)
double      floor( double arg );// (2)
long double floorl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define floor( arg )// (4)(C99 起)
```

1-3) 计算不大于 `arg` 的最大整数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `floorl`。否则，若 `arg` 用有整数类型或 `double` 类型，则调用 `floor`。否则调用 `floorf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回不大于 `arg` 的最大整数，即 *⌊arg⌋*。

返回值

![math-floor.svg](https://upload.cppreference.com/mwiki/images/7/72/math-floor.svg)

参数

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 当前[舍入方式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
- 若 `arg` 为 ±∞，则返回不修改的参数。
- 若 `arg` 为 ±0，则返回不修改的参数。
- 若 `arg` 为 NaN，则返回 NaN。

**注解**

​	在舍入非整数有限值时可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数准确地为整数，故此函数自身决不上溢；然而存储于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("floor(+2.7) = %+.1f\n", floor(2.7));
    printf("floor(-2.7) = %+.1f\n", floor(-2.7));
    printf("floor(-0.0) = %+.1f\n", floor(-0.0));
    printf("floor(-Inf) = %+f\n",   floor(-INFINITY));
}
```

​	可能的输出：

```txt
floor(+2.7) = +2.0
floor(-2.7) = -3.0
floor(-0.0) = -0.0
floor(-Inf) = -inf
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.2 The floor functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.2 The floor functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.2 The floor functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.2 The floor functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.2 The floor functions （第 251 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.2 The floor functions （第 526 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.2 The floor functions （第 232 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.2 The floor functions （第 463 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.6.3 The floor function

**参阅**

| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)                         |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数)               |
| [round (C99)<br />roundf (C99)<br />roundl (C99)<br />lround (C99)<br />lroundf (C99)<br />lroundl (C99)<br />llround (C99)<br />llroundf (C99)<br />llroundl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/round) | 取整到最接近的整数，在相邻整数正中间时取远离零的数 (函数) |
| **floor** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/floor)** |                                                           |





### floorf

原址：[https://zh.cppreference.com/w/c/numeric/math/floor](https://zh.cppreference.com/w/c/numeric/math/floor)

作用：计算不大于给定值的最大整数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       floorf( float arg );// (1)(C99 起)
double      floor( double arg );// (2)
long double floorl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define floor( arg )// (4)(C99 起)
```

1-3) 计算不大于 `arg` 的最大整数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `floorl`。否则，若 `arg` 用有整数类型或 `double` 类型，则调用 `floor`。否则调用 `floorf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回不大于 `arg` 的最大整数，即 *⌊arg⌋*。

返回值

![math-floor.svg](https://upload.cppreference.com/mwiki/images/7/72/math-floor.svg)

参数

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 当前[舍入方式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
- 若 `arg` 为 ±∞，则返回不修改的参数。
- 若 `arg` 为 ±0，则返回不修改的参数。
- 若 `arg` 为 NaN，则返回 NaN。

**注解**

​	在舍入非整数有限值时可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数准确地为整数，故此函数自身决不上溢；然而存储于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("floor(+2.7) = %+.1f\n", floor(2.7));
    printf("floor(-2.7) = %+.1f\n", floor(-2.7));
    printf("floor(-0.0) = %+.1f\n", floor(-0.0));
    printf("floor(-Inf) = %+f\n",   floor(-INFINITY));
}
```

​	可能的输出：

```txt
floor(+2.7) = +2.0
floor(-2.7) = -3.0
floor(-0.0) = -0.0
floor(-Inf) = -inf
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.2 The floor functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.2 The floor functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.2 The floor functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.2 The floor functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.2 The floor functions （第 251 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.2 The floor functions （第 526 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.2 The floor functions （第 232 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.2 The floor functions （第 463 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.6.3 The floor function

**参阅**

| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)                         |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数)               |
| [round (C99)<br />roundf (C99)<br />roundl (C99)<br />lround (C99)<br />lroundf (C99)<br />lroundl (C99)<br />llround (C99)<br />llroundf (C99)<br />llroundl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/round) | 取整到最接近的整数，在相邻整数正中间时取远离零的数 (函数) |
| **floor** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/floor)** |                                                           |





### floorl

原址：[https://zh.cppreference.com/w/c/numeric/math/floor](https://zh.cppreference.com/w/c/numeric/math/floor)

作用：计算不大于给定值的最大整数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       floorf( float arg );// (1)(C99 起)
double      floor( double arg );// (2)
long double floorl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define floor( arg )// (4)(C99 起)
```

1-3) 计算不大于 `arg` 的最大整数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `floorl`。否则，若 `arg` 用有整数类型或 `double` 类型，则调用 `floor`。否则调用 `floorf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回不大于 `arg` 的最大整数，即 *⌊arg⌋*。

返回值

![math-floor.svg](https://upload.cppreference.com/mwiki/images/7/72/math-floor.svg)

参数

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 当前[舍入方式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
- 若 `arg` 为 ±∞，则返回不修改的参数。
- 若 `arg` 为 ±0，则返回不修改的参数。
- 若 `arg` 为 NaN，则返回 NaN。

**注解**

​	在舍入非整数有限值时可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数准确地为整数，故此函数自身决不上溢；然而存储于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("floor(+2.7) = %+.1f\n", floor(2.7));
    printf("floor(-2.7) = %+.1f\n", floor(-2.7));
    printf("floor(-0.0) = %+.1f\n", floor(-0.0));
    printf("floor(-Inf) = %+f\n",   floor(-INFINITY));
}
```

​	可能的输出：

```txt
floor(+2.7) = +2.0
floor(-2.7) = -3.0
floor(-0.0) = -0.0
floor(-Inf) = -inf
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.2 The floor functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.2 The floor functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.2 The floor functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.2 The floor functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.2 The floor functions （第 251 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.2 The floor functions （第 526 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.2 The floor functions （第 232 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.2 The floor functions （第 463 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.6.3 The floor function

**参阅**

| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)                         |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数)               |
| [round (C99)<br />roundf (C99)<br />roundl (C99)<br />lround (C99)<br />lroundf (C99)<br />lroundl (C99)<br />llround (C99)<br />llroundf (C99)<br />llroundl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/round) | 取整到最接近的整数，在相邻整数正中间时取远离零的数 (函数) |
| **floor** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/floor)** |                                                           |





### fma

原址：[https://zh.cppreference.com/w/c/numeric/math/fma](https://zh.cppreference.com/w/c/numeric/math/fma)

作用：计算结合的乘加运算   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fmaf( float x, float y, float z );// (1)(C99 起)
double      fma( double x, double y, double z );// (2)(C99 起)
long double fmal( long double x, long double y, long double z );// (3)(C99 起)
#define FP_FAST_FMA  /* 由实现定义 */// (4)(C99 起)
#define FP_FAST_FMAF /* 由实现定义  */// (5)(C99 起)
#define FP_FAST_FMAL /* 由实现定义  */// (6)(C99 起)
// 在标头 <tgmath.h> 定义
#define fma( x, y, z )// (7)(C99 起)
```

1-3) 计算 `(x * y) + z`，如同用无限精度，而仅舍入一次到结果类型。

4-6) 若定义宏常量 `FP_FAST_FMA`、`FP_FAST_FMAF` 或 `FP_FAST_FMAL`，则对应函数 `fma`、`fmaf` 或 `fmal` 分别求值快于（并且精度高于）`double`、`float` 和 `long double` 实参的表达式 `x * y + z`。若定义，则这些宏求值为整数 `1`。

7） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `fmal`。否则若任何实参拥有整数类型或 `double` 类型，则调用 `fma`。否则调用`fmaf`。

**参数**

| x, y, z | -    | 浮点数 |
| ------- | ---- | ------ |
|         |      |        |

**返回值**

​	若成功，则返回 `(x * y) + z` 的值，如同计算为无限精度再舍入一次以适合目标类型（或者说是作为单次三元浮点数运算计算）。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若

   

  `x`

   

  为零而

   

  `y`

   

  为无穷大或

   

  `x`

   

  为无穷大而

   

  `y`

   

  为零，且

  - 若 `z` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
  - 若 `z` 为 NaN，则返回 NaN 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

- 若 `x * y` 为准确的无穷大且 `z` 为带相反符号的无穷大，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

- 若 `x` 或 `y` 为 NaN，则返回 NaN。

- 若 `z` 为 NaN，且 `x * y` 不是 `0 * Inf` 或 `Inf * 0`，则返回 NaN（而无 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）。

**注解**

​	此运算经常在硬件中实现为[融合乘加](https://en.wikipedia.org/wiki/Multiply–accumulate_operation) CPU 指令。若硬件支持，则期待定义相应的 `FP_FAST_FMA*` 宏，但多数实现即使在不定义这些宏时也利用该 CPU 指令。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fma.html) `x * y` 非法且 `z` 为 NaN 的情形是定义域错误。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.13.1 The fma functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.10.1 The fma functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.13.1 The fma functions （第 188-189 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.10.1 The fma functions （第 386 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.13.1 The fma functions （第 258 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.10.1 The fma functions （第 530 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.13.1 The fma functions （第 239 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.10.1 The fma functions （第 466 页）

**参阅**

| [remainder (C99)<br />remainderf (C99)<br />remainderl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remainder) | 计算浮点数除法运算的带符号余数 (函数)           |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [remquo (C99)<br />remquof (C99)<br />remquol (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remquo) | 计算除法运算的带符号余数，以及商的后三位 (函数) |
| **fma** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fma)** |                                                 |





### fmaf

原址：[https://zh.cppreference.com/w/c/numeric/math/fma](https://zh.cppreference.com/w/c/numeric/math/fma)

作用：计算结合的乘加运算   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fmaf( float x, float y, float z );// (1)(C99 起)
double      fma( double x, double y, double z );// (2)(C99 起)
long double fmal( long double x, long double y, long double z );// (3)(C99 起)
#define FP_FAST_FMA  /* 由实现定义 */// (4)(C99 起)
#define FP_FAST_FMAF /* 由实现定义  */// (5)(C99 起)
#define FP_FAST_FMAL /* 由实现定义  */// (6)(C99 起)
// 在标头 <tgmath.h> 定义
#define fma( x, y, z )// (7)(C99 起)
```

1-3) 计算 `(x * y) + z`，如同用无限精度，而仅舍入一次到结果类型。

4-6) 若定义宏常量 `FP_FAST_FMA`、`FP_FAST_FMAF` 或 `FP_FAST_FMAL`，则对应函数 `fma`、`fmaf` 或 `fmal` 分别求值快于（并且精度高于）`double`、`float` 和 `long double` 实参的表达式 `x * y + z`。若定义，则这些宏求值为整数 `1`。

7） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `fmal`。否则若任何实参拥有整数类型或 `double` 类型，则调用 `fma`。否则调用`fmaf`。

**参数**

| x, y, z | -    | 浮点数 |
| ------- | ---- | ------ |
|         |      |        |

**返回值**

​	若成功，则返回 `(x * y) + z` 的值，如同计算为无限精度再舍入一次以适合目标类型（或者说是作为单次三元浮点数运算计算）。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若

   

  `x`

   

  为零而

   

  `y`

   

  为无穷大或

   

  `x`

   

  为无穷大而

   

  `y`

   

  为零，且

  - 若 `z` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
  - 若 `z` 为 NaN，则返回 NaN 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

- 若 `x * y` 为准确的无穷大且 `z` 为带相反符号的无穷大，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

- 若 `x` 或 `y` 为 NaN，则返回 NaN。

- 若 `z` 为 NaN，且 `x * y` 不是 `0 * Inf` 或 `Inf * 0`，则返回 NaN（而无 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）。

**注解**

​	此运算经常在硬件中实现为[融合乘加](https://en.wikipedia.org/wiki/Multiply–accumulate_operation) CPU 指令。若硬件支持，则期待定义相应的 `FP_FAST_FMA*` 宏，但多数实现即使在不定义这些宏时也利用该 CPU 指令。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fma.html) `x * y` 非法且 `z` 为 NaN 的情形是定义域错误。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.13.1 The fma functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.10.1 The fma functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.13.1 The fma functions （第 188-189 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.10.1 The fma functions （第 386 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.13.1 The fma functions （第 258 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.10.1 The fma functions （第 530 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.13.1 The fma functions （第 239 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.10.1 The fma functions （第 466 页）

**参阅**

| [remainder (C99)<br />remainderf (C99)<br />remainderl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remainder) | 计算浮点数除法运算的带符号余数 (函数)           |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [remquo (C99)<br />remquof (C99)<br />remquol (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remquo) | 计算除法运算的带符号余数，以及商的后三位 (函数) |
| **fma** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fma)** |                                                 |





### fmal

原址：[https://zh.cppreference.com/w/c/numeric/math/fma](https://zh.cppreference.com/w/c/numeric/math/fma)

作用：计算结合的乘加运算   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fmaf( float x, float y, float z );// (1)(C99 起)
double      fma( double x, double y, double z );// (2)(C99 起)
long double fmal( long double x, long double y, long double z );// (3)(C99 起)
#define FP_FAST_FMA  /* 由实现定义 */// (4)(C99 起)
#define FP_FAST_FMAF /* 由实现定义  */// (5)(C99 起)
#define FP_FAST_FMAL /* 由实现定义  */// (6)(C99 起)
// 在标头 <tgmath.h> 定义
#define fma( x, y, z )// (7)(C99 起)
```

1-3) 计算 `(x * y) + z`，如同用无限精度，而仅舍入一次到结果类型。

4-6) 若定义宏常量 `FP_FAST_FMA`、`FP_FAST_FMAF` 或 `FP_FAST_FMAL`，则对应函数 `fma`、`fmaf` 或 `fmal` 分别求值快于（并且精度高于）`double`、`float` 和 `long double` 实参的表达式 `x * y + z`。若定义，则这些宏求值为整数 `1`。

7） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `fmal`。否则若任何实参拥有整数类型或 `double` 类型，则调用 `fma`。否则调用`fmaf`。

**参数**

| x, y, z | -    | 浮点数 |
| ------- | ---- | ------ |
|         |      |        |

**返回值**

​	若成功，则返回 `(x * y) + z` 的值，如同计算为无限精度再舍入一次以适合目标类型（或者说是作为单次三元浮点数运算计算）。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若

   

  `x`

   

  为零而

   

  `y`

   

  为无穷大或

   

  `x`

   

  为无穷大而

   

  `y`

   

  为零，且

  - 若 `z` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
  - 若 `z` 为 NaN，则返回 NaN 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

- 若 `x * y` 为准确的无穷大且 `z` 为带相反符号的无穷大，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

- 若 `x` 或 `y` 为 NaN，则返回 NaN。

- 若 `z` 为 NaN，且 `x * y` 不是 `0 * Inf` 或 `Inf * 0`，则返回 NaN（而无 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）。

**注解**

​	此运算经常在硬件中实现为[融合乘加](https://en.wikipedia.org/wiki/Multiply–accumulate_operation) CPU 指令。若硬件支持，则期待定义相应的 `FP_FAST_FMA*` 宏，但多数实现即使在不定义这些宏时也利用该 CPU 指令。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fma.html) `x * y` 非法且 `z` 为 NaN 的情形是定义域错误。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.13.1 The fma functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.10.1 The fma functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.13.1 The fma functions （第 188-189 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.10.1 The fma functions （第 386 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.13.1 The fma functions （第 258 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.10.1 The fma functions （第 530 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.13.1 The fma functions （第 239 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.10.1 The fma functions （第 466 页）

**参阅**

| [remainder (C99)<br />remainderf (C99)<br />remainderl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remainder) | 计算浮点数除法运算的带符号余数 (函数)           |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [remquo (C99)<br />remquof (C99)<br />remquol (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remquo) | 计算除法运算的带符号余数，以及商的后三位 (函数) |
| **fma** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fma)** |                                                 |





### fmax

原址：[https://zh.cppreference.com/w/c/numeric/math/fmax](https://zh.cppreference.com/w/c/numeric/math/fmax)

作用：确定两个浮点数的较大者   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fmaxf( float x, float y );// (1)(C99 起)
double      fmax( double x, double y );// (2)(C99 起)
long double fmaxl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define fmax( x, y )// (4)(C99 起)
```

1-3) 返回二个浮点数实参的较大者，把 NaNs 当做缺失数据（在 NaN 和数值间选择数值）。

4） 泛型宏：若任一参数拥有 `long double` 类型，则调用 `fmaxl`。否则，若任一实参拥有整数类型或 `double` 类型，则调用 `fmax`。否则调用 `fmaxf`。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若成功，则返回二个浮点数的较大者。返回值准确且不依赖任何舍入模式。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误条件。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若两个实参之一为 NaN，则返回另一实参的值
- 仅若两个实参均为 NaN，才返回 NaN

**注意**

​	不要求此函数对零的符号敏感，尽管某些实现额外强制若一个实参是 +0 而另一个是 -0，则返回 +0。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("fmax(2,1)    = %f\n", fmax(2,1));
    printf("fmax(-Inf,0) = %f\n", fmax(-INFINITY,0));
    printf("fmax(NaN,-1) = %f\n", fmax(NAN,-1));
}
```

​	输出：

```txt
fmax(2,1)    = 2.000000
fmax(-Inf,0) = 0.000000
fmax(NaN,-1) = -1.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.12.2 The fmax functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.9.2 The fmax functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.12.2 The fmax functions （第 188 页）

  - 7.25 Type-generic math <tgmath.h> （第 397 页）

  - F.10.9.2 The fmax functions （第 386 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.12.2 The fmax functions （第 257-258 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.9.2 The fmax functions （第 530 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.12.2 The fmax functions （第 238-239 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.9.2 The fmax functions （第 466 页）

**参阅**

| [isgreater (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isgreater) | 检查第一个浮点数实参是否大于第二个 (宏函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| [fmin (C99)<br />fminf (C99)<br />fminl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmin) | 确定两个浮点数的较小者 (函数)               |
| **fmax** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fmax)** |                                             |





### fmaxf

原址：[https://zh.cppreference.com/w/c/numeric/math/fmax](https://zh.cppreference.com/w/c/numeric/math/fmax)

作用：确定两个浮点数的较大者   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fmaxf( float x, float y );// (1)(C99 起)
double      fmax( double x, double y );// (2)(C99 起)
long double fmaxl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define fmax( x, y )// (4)(C99 起)
```

1-3) 返回二个浮点数实参的较大者，把 NaNs 当做缺失数据（在 NaN 和数值间选择数值）。

4） 泛型宏：若任一参数拥有 `long double` 类型，则调用 `fmaxl`。否则，若任一实参拥有整数类型或 `double` 类型，则调用 `fmax`。否则调用 `fmaxf`。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若成功，则返回二个浮点数的较大者。返回值准确且不依赖任何舍入模式。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误条件。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若两个实参之一为 NaN，则返回另一实参的值
- 仅若两个实参均为 NaN，才返回 NaN

**注意**

​	不要求此函数对零的符号敏感，尽管某些实现额外强制若一个实参是 +0 而另一个是 -0，则返回 +0。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("fmax(2,1)    = %f\n", fmax(2,1));
    printf("fmax(-Inf,0) = %f\n", fmax(-INFINITY,0));
    printf("fmax(NaN,-1) = %f\n", fmax(NAN,-1));
}
```

​	输出：

```txt
fmax(2,1)    = 2.000000
fmax(-Inf,0) = 0.000000
fmax(NaN,-1) = -1.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.12.2 The fmax functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.9.2 The fmax functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.12.2 The fmax functions （第 188 页）

  - 7.25 Type-generic math <tgmath.h> （第 397 页）

  - F.10.9.2 The fmax functions （第 386 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.12.2 The fmax functions （第 257-258 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.9.2 The fmax functions （第 530 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.12.2 The fmax functions （第 238-239 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.9.2 The fmax functions （第 466 页）

**参阅**

| [isgreater (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isgreater) | 检查第一个浮点数实参是否大于第二个 (宏函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| [fmin (C99)<br />fminf (C99)<br />fminl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmin) | 确定两个浮点数的较小者 (函数)               |
| **fmax** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fmax)** |                                             |





### fmaxl

原址：[https://zh.cppreference.com/w/c/numeric/math/fmax](https://zh.cppreference.com/w/c/numeric/math/fmax)

作用：确定两个浮点数的较大者   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fmaxf( float x, float y );// (1)(C99 起)
double      fmax( double x, double y );// (2)(C99 起)
long double fmaxl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define fmax( x, y )// (4)(C99 起)
```

1-3) 返回二个浮点数实参的较大者，把 NaNs 当做缺失数据（在 NaN 和数值间选择数值）。

4） 泛型宏：若任一参数拥有 `long double` 类型，则调用 `fmaxl`。否则，若任一实参拥有整数类型或 `double` 类型，则调用 `fmax`。否则调用 `fmaxf`。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若成功，则返回二个浮点数的较大者。返回值准确且不依赖任何舍入模式。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误条件。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若两个实参之一为 NaN，则返回另一实参的值
- 仅若两个实参均为 NaN，才返回 NaN

**注意**

​	不要求此函数对零的符号敏感，尽管某些实现额外强制若一个实参是 +0 而另一个是 -0，则返回 +0。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("fmax(2,1)    = %f\n", fmax(2,1));
    printf("fmax(-Inf,0) = %f\n", fmax(-INFINITY,0));
    printf("fmax(NaN,-1) = %f\n", fmax(NAN,-1));
}
```

​	输出：

```txt
fmax(2,1)    = 2.000000
fmax(-Inf,0) = 0.000000
fmax(NaN,-1) = -1.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.12.2 The fmax functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.9.2 The fmax functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.12.2 The fmax functions （第 188 页）

  - 7.25 Type-generic math <tgmath.h> （第 397 页）

  - F.10.9.2 The fmax functions （第 386 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.12.2 The fmax functions （第 257-258 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.9.2 The fmax functions （第 530 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.12.2 The fmax functions （第 238-239 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.9.2 The fmax functions （第 466 页）

**参阅**

| [isgreater (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isgreater) | 检查第一个浮点数实参是否大于第二个 (宏函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| [fmin (C99)<br />fminf (C99)<br />fminl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmin) | 确定两个浮点数的较小者 (函数)               |
| **fmax** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fmax)** |                                             |





### fmin

原址：[https://zh.cppreference.com/w/c/numeric/math/fmin](https://zh.cppreference.com/w/c/numeric/math/fmin)

作用：确定两个浮点数的较小者   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fminf( float x, float y );// (1)(C99 起)
double      fmin( double x, double y );// (2)(C99 起)
long double fminl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define fmin( x, y )// (4)(C99 起)
```

1-3) 返回二个浮点数参数的较小者，把 NaNs 当做缺失数据（在 NaN 和数值间选择数值）。

4） 泛型宏：若任一实参拥有 `long double` 类型，则调用 `fmaxl`。否则，若任一实参拥有整数类型或 `double` 类型，则调用 `fmax`。否则调用 `fmaxf` 。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若成功，则返回两个浮点数的较小者。返回值准确且不依赖任何舍入模式。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误条件。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若两个参数之一为 NaN，则返回另一实参的值
- 仅若两个参数均为 NaN，才返回 NaN

**注解**

​	不要求此函数对零的符号敏感，尽管某些实现额外强制若一个实参是 +0 而另一个是 -0，则返回 -0。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("fmin(2,1)    = %f\n", fmin(2, 1));
    printf("fmin(-Inf,0) = %f\n", fmin(-INFINITY, 0));
    printf("fmin(NaN,-1) = %f\n", fmin(NAN, -1));
}
```

​	可能的输出：

```txt
fmin(2,1)    = 1.000000
fmin(-Inf,0) = -inf
fmin(NaN,-1) = -1.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.12.3 The fmin functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.9.3 The fmin functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.12.3 The fmin functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.9.3 The fmin functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.12.3 The fmin functions （第 258 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.9.3 The fmin functions （第 530 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.12.3 The fmin functions （第 239 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.9.3 The fmin functions （第 466 页）

**参阅**

| [isless (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isless) | 检查第一个浮点数实参是否小于第二个 (宏函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| [fmax (C99)<br />fmaxf (C99)<br />fmaxl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmax) | 确定两个浮点数的较大者 (函数)               |
| **fmin** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fmin)** |                                             |





### fminf

原址：[https://zh.cppreference.com/w/c/numeric/math/fmin](https://zh.cppreference.com/w/c/numeric/math/fmin)

作用：确定两个浮点数的较小者   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fminf( float x, float y );// (1)(C99 起)
double      fmin( double x, double y );// (2)(C99 起)
long double fminl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define fmin( x, y )// (4)(C99 起)
```

1-3) 返回二个浮点数参数的较小者，把 NaNs 当做缺失数据（在 NaN 和数值间选择数值）。

4） 泛型宏：若任一实参拥有 `long double` 类型，则调用 `fmaxl`。否则，若任一实参拥有整数类型或 `double` 类型，则调用 `fmax`。否则调用 `fmaxf` 。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若成功，则返回两个浮点数的较小者。返回值准确且不依赖任何舍入模式。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误条件。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若两个参数之一为 NaN，则返回另一实参的值
- 仅若两个参数均为 NaN，才返回 NaN

**注解**

​	不要求此函数对零的符号敏感，尽管某些实现额外强制若一个实参是 +0 而另一个是 -0，则返回 -0。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("fmin(2,1)    = %f\n", fmin(2, 1));
    printf("fmin(-Inf,0) = %f\n", fmin(-INFINITY, 0));
    printf("fmin(NaN,-1) = %f\n", fmin(NAN, -1));
}
```

​	可能的输出：

```txt
fmin(2,1)    = 1.000000
fmin(-Inf,0) = -inf
fmin(NaN,-1) = -1.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.12.3 The fmin functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.9.3 The fmin functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.12.3 The fmin functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.9.3 The fmin functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.12.3 The fmin functions （第 258 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.9.3 The fmin functions （第 530 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.12.3 The fmin functions （第 239 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.9.3 The fmin functions （第 466 页）

**参阅**

| [isless (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isless) | 检查第一个浮点数实参是否小于第二个 (宏函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| [fmax (C99)<br />fmaxf (C99)<br />fmaxl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmax) | 确定两个浮点数的较大者 (函数)               |
| **fmin** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fmin)** |                                             |





### fminl

原址：[https://zh.cppreference.com/w/c/numeric/math/fmin](https://zh.cppreference.com/w/c/numeric/math/fmin)

作用：确定两个浮点数的较小者   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fminf( float x, float y );// (1)(C99 起)
double      fmin( double x, double y );// (2)(C99 起)
long double fminl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define fmin( x, y )// (4)(C99 起)
```

1-3) 返回二个浮点数参数的较小者，把 NaNs 当做缺失数据（在 NaN 和数值间选择数值）。

4） 泛型宏：若任一实参拥有 `long double` 类型，则调用 `fmaxl`。否则，若任一实参拥有整数类型或 `double` 类型，则调用 `fmax`。否则调用 `fmaxf` 。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若成功，则返回两个浮点数的较小者。返回值准确且不依赖任何舍入模式。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误条件。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若两个参数之一为 NaN，则返回另一实参的值
- 仅若两个参数均为 NaN，才返回 NaN

**注解**

​	不要求此函数对零的符号敏感，尽管某些实现额外强制若一个实参是 +0 而另一个是 -0，则返回 -0。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("fmin(2,1)    = %f\n", fmin(2, 1));
    printf("fmin(-Inf,0) = %f\n", fmin(-INFINITY, 0));
    printf("fmin(NaN,-1) = %f\n", fmin(NAN, -1));
}
```

​	可能的输出：

```txt
fmin(2,1)    = 1.000000
fmin(-Inf,0) = -inf
fmin(NaN,-1) = -1.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.12.3 The fmin functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.9.3 The fmin functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.12.3 The fmin functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.9.3 The fmin functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.12.3 The fmin functions （第 258 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.9.3 The fmin functions （第 530 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.12.3 The fmin functions （第 239 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.9.3 The fmin functions （第 466 页）

**参阅**

| [isless (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isless) | 检查第一个浮点数实参是否小于第二个 (宏函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| [fmax (C99)<br />fmaxf (C99)<br />fmaxl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmax) | 确定两个浮点数的较大者 (函数)               |
| **fmin** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fmin)** |                                             |





### fmod

原址：[https://zh.cppreference.com/w/c/numeric/math/fmod](https://zh.cppreference.com/w/c/numeric/math/fmod)

作用：计算浮点数除法运算的余数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fmodf( float x, float y );// (1)(C99 起)
double      fmod( double x, double y );// (2)
long double fmodl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define fmod( x, y )// (4)(C99 起)
```

1-3) 计算除法运算 `x / y` 的浮点数余数。

4） 泛型宏：若任何实参拥有 `long double` 类型则调用 `fmodl`。否则，若任何实参拥有整数类型或 `double` 类型则调用 `fmod`。否则调用 `fmodf`。

​	此函数计算的除法 `x / y` 的浮点数余数是 `x - n * y` 的准确值，其中 `n` 是截断小数部分的 `x / y`。

​	返回值与 `x` 拥有相同符号，且绝对值小于 `y`。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若成功，则返回定义于上的除法 `x / y` 的浮点数余数。

​	若出现定义域错误，则返回实现定义值（受支持的平台上为 NaN）。

​	若出现下溢所指定值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `y` 为零则可能发生定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559）：

- 若 `x` 为 ±0 且 `y` 非零，则返回 ±0。
- 若 `x` 为 ±∞ 且 `y` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `y` 为 ±0 且 `x` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `y` 为 ±∞ 且 `x` 有限，则返回 `x`。
- 若任一实参为 NaN，则返回 NaN。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fmod.html)若 `x` 为无穷大或 `y` 为零则出现定义域错误。

​	`fmod`，但不是 [remainder](https://zh.cppreference.com/w/c/numeric/math/remainder)，适于安静地包装浮点数类型到无符号整数类型：`(0.0 <= (y = fmod( [rint](http://zh.cppreference.com/w/c/numeric/math/rint)(x), 65536.0 )) ? y : 65536.0 + y)` 在范围 `[``-0.0``, ``65535.0``]` 内，它对应 `unsigned short`，但 `[remainder](http://zh.cppreference.com/w/c/numeric/math/remainder)([rint](http://zh.cppreference.com/w/c/numeric/math/rint)(x), 65536.0)` 在范围 `[``-32767.0``, ``+32768.0``]` 内，它在 `signed short` 的范围外。

​	`fmod` 的 `double` 版本表现为如同实现如下：

```c
double fmod(double x, double y)
{
#pragma STDC FENV_ACCESS ON
    double result = remainder(fabs(x), (y = fabs(y)));
    if (signbit(result))
        result += y;
    return copysign(result, x);
}
```

**示例**

```c
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("fmod(+5.1, +3.0) = %.1f\n", fmod(5.1, 3));
    printf("fmod(-5.1, +3.0) = %.1f\n", fmod(-5.1, 3));
    printf("fmod(+5.1, -3.0) = %.1f\n", fmod(5.1, -3));
    printf("fmod(-5.1, -3.0) = %.1f\n", fmod(-5.1, -3));
 
    // 特殊值
    printf("fmod(+0.0, 1.0) = %.1f\n", fmod(0, 1));
    printf("fmod(-0.0, 1.0) = %.1f\n", fmod(-0.0, 1));
    printf("fmod(+5.1, Inf) = %.1f\n", fmod(5.1, INFINITY));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("fmod(+5.1, 0) = %.1f\n", fmod(5.1, 0));
    if(fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
fmod(+5.1, +3.0) = 2.1
fmod(-5.1, +3.0) = -2.1
fmod(+5.1, -3.0) = 2.1
fmod(-5.1, -3.0) = -2.1
fmod(+0.0, 1.0) = 0.0
fmod(-0.0, 1.0) = -0.0
fmod(+5.1, Inf) = 5.1
fmod(+5.1, 0) = nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.10.1 The fmod functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.7.1 The fmod functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.10.1 The fmod functions （第 185 页）

  - 7.25 Type-generic math <tgmath.h> （第 274-275 页）

  - F.10.7.1 The fmod functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.10.1 The fmod functions （第 254 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.7.1 The fmod functions （第 528 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.10.1 The fmod functions （第 235 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.7.1 The fmod functions （第 465 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.6.4 The fmod function

**参阅**

| [div <br />ldiv <br />lldiv (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/div) | 计算整数除法的商和余数 (函数)                   |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [remainder (C99)<br />remainderf (C99)<br />remainderl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remainder) | 计算浮点数除法运算的带符号余数 (函数)           |
| [remquo (C99)<br />remquof (C99)<br />remquol (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remquo) | 计算除法运算的带符号余数，以及商的后三位 (函数) |
| **fmod** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fmod)** |                                                 |





### fmodf

原址：[https://zh.cppreference.com/w/c/numeric/math/fmod](https://zh.cppreference.com/w/c/numeric/math/fmod)

作用：计算浮点数除法运算的余数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fmodf( float x, float y );// (1)(C99 起)
double      fmod( double x, double y );// (2)
long double fmodl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define fmod( x, y )// (4)(C99 起)
```

1-3) 计算除法运算 `x / y` 的浮点数余数。

4） 泛型宏：若任何实参拥有 `long double` 类型则调用 `fmodl`。否则，若任何实参拥有整数类型或 `double` 类型则调用 `fmod`。否则调用 `fmodf`。

​	此函数计算的除法 `x / y` 的浮点数余数是 `x - n * y` 的准确值，其中 `n` 是截断小数部分的 `x / y`。

​	返回值与 `x` 拥有相同符号，且绝对值小于 `y`。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若成功，则返回定义于上的除法 `x / y` 的浮点数余数。

​	若出现定义域错误，则返回实现定义值（受支持的平台上为 NaN）。

​	若出现下溢所指定值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `y` 为零则可能发生定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559）：

- 若 `x` 为 ±0 且 `y` 非零，则返回 ±0。
- 若 `x` 为 ±∞ 且 `y` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `y` 为 ±0 且 `x` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `y` 为 ±∞ 且 `x` 有限，则返回 `x`。
- 若任一实参为 NaN，则返回 NaN。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fmod.html)若 `x` 为无穷大或 `y` 为零则出现定义域错误。

​	`fmod`，但不是 [remainder](https://zh.cppreference.com/w/c/numeric/math/remainder)，适于安静地包装浮点数类型到无符号整数类型：`(0.0 <= (y = fmod( [rint](http://zh.cppreference.com/w/c/numeric/math/rint)(x), 65536.0 )) ? y : 65536.0 + y)` 在范围 `[``-0.0``, ``65535.0``]` 内，它对应 `unsigned short`，但 `[remainder](http://zh.cppreference.com/w/c/numeric/math/remainder)([rint](http://zh.cppreference.com/w/c/numeric/math/rint)(x), 65536.0)` 在范围 `[``-32767.0``, ``+32768.0``]` 内，它在 `signed short` 的范围外。

​	`fmod` 的 `double` 版本表现为如同实现如下：

```c
double fmod(double x, double y)
{
#pragma STDC FENV_ACCESS ON
    double result = remainder(fabs(x), (y = fabs(y)));
    if (signbit(result))
        result += y;
    return copysign(result, x);
}
```

**示例**

```c
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("fmod(+5.1, +3.0) = %.1f\n", fmod(5.1, 3));
    printf("fmod(-5.1, +3.0) = %.1f\n", fmod(-5.1, 3));
    printf("fmod(+5.1, -3.0) = %.1f\n", fmod(5.1, -3));
    printf("fmod(-5.1, -3.0) = %.1f\n", fmod(-5.1, -3));
 
    // 特殊值
    printf("fmod(+0.0, 1.0) = %.1f\n", fmod(0, 1));
    printf("fmod(-0.0, 1.0) = %.1f\n", fmod(-0.0, 1));
    printf("fmod(+5.1, Inf) = %.1f\n", fmod(5.1, INFINITY));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("fmod(+5.1, 0) = %.1f\n", fmod(5.1, 0));
    if(fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
fmod(+5.1, +3.0) = 2.1
fmod(-5.1, +3.0) = -2.1
fmod(+5.1, -3.0) = 2.1
fmod(-5.1, -3.0) = -2.1
fmod(+0.0, 1.0) = 0.0
fmod(-0.0, 1.0) = -0.0
fmod(+5.1, Inf) = 5.1
fmod(+5.1, 0) = nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.10.1 The fmod functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.7.1 The fmod functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.10.1 The fmod functions （第 185 页）

  - 7.25 Type-generic math <tgmath.h> （第 274-275 页）

  - F.10.7.1 The fmod functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.10.1 The fmod functions （第 254 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.7.1 The fmod functions （第 528 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.10.1 The fmod functions （第 235 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.7.1 The fmod functions （第 465 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.6.4 The fmod function

**参阅**

| [div <br />ldiv <br />lldiv (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/div) | 计算整数除法的商和余数 (函数)                   |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [remainder (C99)<br />remainderf (C99)<br />remainderl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remainder) | 计算浮点数除法运算的带符号余数 (函数)           |
| [remquo (C99)<br />remquof (C99)<br />remquol (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remquo) | 计算除法运算的带符号余数，以及商的后三位 (函数) |
| **fmod** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fmod)** |                                                 |





### fmodl

原址：[https://zh.cppreference.com/w/c/numeric/math/fmod](https://zh.cppreference.com/w/c/numeric/math/fmod)

作用：计算浮点数除法运算的余数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       fmodf( float x, float y );// (1)(C99 起)
double      fmod( double x, double y );// (2)
long double fmodl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define fmod( x, y )// (4)(C99 起)
```

1-3) 计算除法运算 `x / y` 的浮点数余数。

4） 泛型宏：若任何实参拥有 `long double` 类型则调用 `fmodl`。否则，若任何实参拥有整数类型或 `double` 类型则调用 `fmod`。否则调用 `fmodf`。

​	此函数计算的除法 `x / y` 的浮点数余数是 `x - n * y` 的准确值，其中 `n` 是截断小数部分的 `x / y`。

​	返回值与 `x` 拥有相同符号，且绝对值小于 `y`。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若成功，则返回定义于上的除法 `x / y` 的浮点数余数。

​	若出现定义域错误，则返回实现定义值（受支持的平台上为 NaN）。

​	若出现下溢所指定值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `y` 为零则可能发生定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559）：

- 若 `x` 为 ±0 且 `y` 非零，则返回 ±0。
- 若 `x` 为 ±∞ 且 `y` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `y` 为 ±0 且 `x` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `y` 为 ±∞ 且 `x` 有限，则返回 `x`。
- 若任一实参为 NaN，则返回 NaN。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fmod.html)若 `x` 为无穷大或 `y` 为零则出现定义域错误。

​	`fmod`，但不是 [remainder](https://zh.cppreference.com/w/c/numeric/math/remainder)，适于安静地包装浮点数类型到无符号整数类型：`(0.0 <= (y = fmod( [rint](http://zh.cppreference.com/w/c/numeric/math/rint)(x), 65536.0 )) ? y : 65536.0 + y)` 在范围 `[``-0.0``, ``65535.0``]` 内，它对应 `unsigned short`，但 `[remainder](http://zh.cppreference.com/w/c/numeric/math/remainder)([rint](http://zh.cppreference.com/w/c/numeric/math/rint)(x), 65536.0)` 在范围 `[``-32767.0``, ``+32768.0``]` 内，它在 `signed short` 的范围外。

​	`fmod` 的 `double` 版本表现为如同实现如下：

```c
double fmod(double x, double y)
{
#pragma STDC FENV_ACCESS ON
    double result = remainder(fabs(x), (y = fabs(y)));
    if (signbit(result))
        result += y;
    return copysign(result, x);
}
```

**示例**

```c
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("fmod(+5.1, +3.0) = %.1f\n", fmod(5.1, 3));
    printf("fmod(-5.1, +3.0) = %.1f\n", fmod(-5.1, 3));
    printf("fmod(+5.1, -3.0) = %.1f\n", fmod(5.1, -3));
    printf("fmod(-5.1, -3.0) = %.1f\n", fmod(-5.1, -3));
 
    // 特殊值
    printf("fmod(+0.0, 1.0) = %.1f\n", fmod(0, 1));
    printf("fmod(-0.0, 1.0) = %.1f\n", fmod(-0.0, 1));
    printf("fmod(+5.1, Inf) = %.1f\n", fmod(5.1, INFINITY));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("fmod(+5.1, 0) = %.1f\n", fmod(5.1, 0));
    if(fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
fmod(+5.1, +3.0) = 2.1
fmod(-5.1, +3.0) = -2.1
fmod(+5.1, -3.0) = 2.1
fmod(-5.1, -3.0) = -2.1
fmod(+0.0, 1.0) = 0.0
fmod(-0.0, 1.0) = -0.0
fmod(+5.1, Inf) = 5.1
fmod(+5.1, 0) = nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.10.1 The fmod functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.7.1 The fmod functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.10.1 The fmod functions （第 185 页）

  - 7.25 Type-generic math <tgmath.h> （第 274-275 页）

  - F.10.7.1 The fmod functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.10.1 The fmod functions （第 254 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.7.1 The fmod functions （第 528 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.10.1 The fmod functions （第 235 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.7.1 The fmod functions （第 465 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.6.4 The fmod function

**参阅**

| [div <br />ldiv <br />lldiv (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/div) | 计算整数除法的商和余数 (函数)                   |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [remainder (C99)<br />remainderf (C99)<br />remainderl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remainder) | 计算浮点数除法运算的带符号余数 (函数)           |
| [remquo (C99)<br />remquof (C99)<br />remquol (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remquo) | 计算除法运算的带符号余数，以及商的后三位 (函数) |
| **fmod** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/fmod)** |                                                 |





### frexp

原址：[https://zh.cppreference.com/w/c/numeric/math/frexp](https://zh.cppreference.com/w/c/numeric/math/frexp)

作用：将数拆分成有效数字和 2 的幂次  (函数)

备注：
```c
// 在标头 <math.h> 定义
float       frexpf( float arg, int* exp );// (1)(C99 起)
double      frexp( double arg, int* exp );// (2)
long double frexpl( long double arg, int* exp );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define frexp( arg, exp )// (4)(C99 起)
```

1-3) 分解给定的浮点数 `x` 为正规化小数和二的整数幂。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `frexpl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `frexp`。否则调用 `frexpf`。

**参数**

| arg  | -    | 浮点数                       |
| ---- | ---- | ---------------------------- |
| exp  | -    | 指向要存储指数到的整数的指针 |

**返回值**

​	若 `arg` 为零，则返回零并存储零于 `*exp`。

​	否则（若 `arg` 非零），若不出现错误，则返回范围 `(-1;-0.5], [0.5; 1)` 中的值 `x`，并存储整数为 `*[exp](http://zh.cppreference.com/w/c/numeric/math/exp)`，满足 *x×2(\*exp)
=arg*。

​	若存储于 `*exp` 的值在 `int` 范围外，则行为未指定。

​	若 `arg` 不是浮点数，则行为未指定。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若 `arg` 为 ±0，则返回不修改的参数，并存储 `0` 于 `*[exp](http://zh.cppreference.com/w/c/numeric/math/exp)`。
- 若 `arg` 为 ±∞，则返回它，并存储未指定值于 `*[exp](http://zh.cppreference.com/w/c/numeric/math/exp)`。
- 若 `arg` 为 NaN，则返回 NaN，并存储未指定值于 `*[exp](http://zh.cppreference.com/w/c/numeric/math/exp)`。
- 不引发浮点数异常。
- 若 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 为 `2`（或 2 的幂），则返回值准确，忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**注解**

​	二进制系统（其中 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 为 `2`）上，`frexp` 可实现为

```
{
    *exp = (value == 0) ? 0 : (int)(1 + logb(value));
    return scalbn(value, -(*exp));
}
```

​	函数 `frexp` 与其对偶 [ldexp](https://zh.cppreference.com/w/c/numeric/math/ldexp) 能一起用于操纵浮点数的表示，而无需直接的位操作。

**示例**

```c
#include <float.h>
#include <math.h>
#include <stdio.h>
 
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
}
```

​	可能的输出：

```txt
给定数值 123.45 十六进制为 0x1.edccccccccccdp+6，
modf() 计算 123 + 0.45
frexp() 计算 0.964453 * 2^7
logb()/ilogb() 计算 1.92891 * 2^6
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.4 The frexp functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.4 The frexp functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.4 The frexp functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.4 The frexp functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.4 The frexp functions （第 243 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.4 The frexp functions （第 521 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.4 The frexp functions （第 224 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.4 The frexp functions （第 458 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.2 The frexp function

**参阅**

| [ldexp <br />ldexpf (C99)<br />ldexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ldexp) | 将数乘以 *2* 的幂 (函数)                |
| ------------------------------------------------------------ | --------------------------------------- |
| [logb (C99)<br />logbf (C99)<br />logbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/logb) | 提取给定数的指数（结果为浮点数） (函数) |
| [ilogb (C99)<br />ilogbf (C99)<br />ilogbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ilogb) | 提取给定数的指数（结果为整数） (函数)   |
| [modf <br />modff (C99)<br />modfl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/modf) | 把一个数拆分成整数和小数部分 (函数)     |
| **frexp** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/frexp)** |                                         |





### frexpf

原址：[https://zh.cppreference.com/w/c/numeric/math/frexp](https://zh.cppreference.com/w/c/numeric/math/frexp)

作用：将数拆分成有效数字和 2 的幂次  (函数)

备注：
```c
// 在标头 <math.h> 定义
float       frexpf( float arg, int* exp );// (1)(C99 起)
double      frexp( double arg, int* exp );// (2)
long double frexpl( long double arg, int* exp );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define frexp( arg, exp )// (4)(C99 起)
```

1-3) 分解给定的浮点数 `x` 为正规化小数和二的整数幂。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `frexpl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `frexp`。否则调用 `frexpf`。

**参数**

| arg  | -    | 浮点数                       |
| ---- | ---- | ---------------------------- |
| exp  | -    | 指向要存储指数到的整数的指针 |

**返回值**

​	若 `arg` 为零，则返回零并存储零于 `*exp`。

​	否则（若 `arg` 非零），若不出现错误，则返回范围 `(-1;-0.5], [0.5; 1)` 中的值 `x`，并存储整数为 `*[exp](http://zh.cppreference.com/w/c/numeric/math/exp)`，满足 *x×2(\*exp)
=arg*。

​	若存储于 `*exp` 的值在 `int` 范围外，则行为未指定。

​	若 `arg` 不是浮点数，则行为未指定。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若 `arg` 为 ±0，则返回不修改的参数，并存储 `0` 于 `*[exp](http://zh.cppreference.com/w/c/numeric/math/exp)`。
- 若 `arg` 为 ±∞，则返回它，并存储未指定值于 `*[exp](http://zh.cppreference.com/w/c/numeric/math/exp)`。
- 若 `arg` 为 NaN，则返回 NaN，并存储未指定值于 `*[exp](http://zh.cppreference.com/w/c/numeric/math/exp)`。
- 不引发浮点数异常。
- 若 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 为 `2`（或 2 的幂），则返回值准确，忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**注解**

​	二进制系统（其中 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 为 `2`）上，`frexp` 可实现为

```
{
    *exp = (value == 0) ? 0 : (int)(1 + logb(value));
    return scalbn(value, -(*exp));
}
```

​	函数 `frexp` 与其对偶 [ldexp](https://zh.cppreference.com/w/c/numeric/math/ldexp) 能一起用于操纵浮点数的表示，而无需直接的位操作。

**示例**

```c
#include <float.h>
#include <math.h>
#include <stdio.h>
 
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
}
```

​	可能的输出：

```txt
给定数值 123.45 十六进制为 0x1.edccccccccccdp+6，
modf() 计算 123 + 0.45
frexp() 计算 0.964453 * 2^7
logb()/ilogb() 计算 1.92891 * 2^6
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.4 The frexp functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.4 The frexp functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.4 The frexp functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.4 The frexp functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.4 The frexp functions （第 243 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.4 The frexp functions （第 521 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.4 The frexp functions （第 224 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.4 The frexp functions （第 458 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.2 The frexp function

**参阅**

| [ldexp <br />ldexpf (C99)<br />ldexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ldexp) | 将数乘以 *2* 的幂 (函数)                |
| ------------------------------------------------------------ | --------------------------------------- |
| [logb (C99)<br />logbf (C99)<br />logbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/logb) | 提取给定数的指数（结果为浮点数） (函数) |
| [ilogb (C99)<br />ilogbf (C99)<br />ilogbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ilogb) | 提取给定数的指数（结果为整数） (函数)   |
| [modf <br />modff (C99)<br />modfl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/modf) | 把一个数拆分成整数和小数部分 (函数)     |
| **frexp** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/frexp)** |                                         |





### frexpl

原址：[https://zh.cppreference.com/w/c/numeric/math/frexp](https://zh.cppreference.com/w/c/numeric/math/frexp)

作用：将数拆分成有效数字和 2 的幂次  (函数)

备注：
```c
// 在标头 <math.h> 定义
float       frexpf( float arg, int* exp );// (1)(C99 起)
double      frexp( double arg, int* exp );// (2)
long double frexpl( long double arg, int* exp );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define frexp( arg, exp )// (4)(C99 起)
```

1-3) 分解给定的浮点数 `x` 为正规化小数和二的整数幂。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `frexpl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `frexp`。否则调用 `frexpf`。

**参数**

| arg  | -    | 浮点数                       |
| ---- | ---- | ---------------------------- |
| exp  | -    | 指向要存储指数到的整数的指针 |

**返回值**

​	若 `arg` 为零，则返回零并存储零于 `*exp`。

​	否则（若 `arg` 非零），若不出现错误，则返回范围 `(-1;-0.5], [0.5; 1)` 中的值 `x`，并存储整数为 `*[exp](http://zh.cppreference.com/w/c/numeric/math/exp)`，满足 *x×2(\*exp)
=arg*。

​	若存储于 `*exp` 的值在 `int` 范围外，则行为未指定。

​	若 `arg` 不是浮点数，则行为未指定。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若 `arg` 为 ±0，则返回不修改的参数，并存储 `0` 于 `*[exp](http://zh.cppreference.com/w/c/numeric/math/exp)`。
- 若 `arg` 为 ±∞，则返回它，并存储未指定值于 `*[exp](http://zh.cppreference.com/w/c/numeric/math/exp)`。
- 若 `arg` 为 NaN，则返回 NaN，并存储未指定值于 `*[exp](http://zh.cppreference.com/w/c/numeric/math/exp)`。
- 不引发浮点数异常。
- 若 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 为 `2`（或 2 的幂），则返回值准确，忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**注解**

​	二进制系统（其中 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 为 `2`）上，`frexp` 可实现为

```
{
    *exp = (value == 0) ? 0 : (int)(1 + logb(value));
    return scalbn(value, -(*exp));
}
```

​	函数 `frexp` 与其对偶 [ldexp](https://zh.cppreference.com/w/c/numeric/math/ldexp) 能一起用于操纵浮点数的表示，而无需直接的位操作。

**示例**

```c
#include <float.h>
#include <math.h>
#include <stdio.h>
 
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
}
```

​	可能的输出：

```txt
给定数值 123.45 十六进制为 0x1.edccccccccccdp+6，
modf() 计算 123 + 0.45
frexp() 计算 0.964453 * 2^7
logb()/ilogb() 计算 1.92891 * 2^6
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.4 The frexp functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.4 The frexp functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.4 The frexp functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.4 The frexp functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.4 The frexp functions （第 243 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.4 The frexp functions （第 521 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.4 The frexp functions （第 224 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.4 The frexp functions （第 458 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.2 The frexp function

**参阅**

| [ldexp <br />ldexpf (C99)<br />ldexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ldexp) | 将数乘以 *2* 的幂 (函数)                |
| ------------------------------------------------------------ | --------------------------------------- |
| [logb (C99)<br />logbf (C99)<br />logbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/logb) | 提取给定数的指数（结果为浮点数） (函数) |
| [ilogb (C99)<br />ilogbf (C99)<br />ilogbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ilogb) | 提取给定数的指数（结果为整数） (函数)   |
| [modf <br />modff (C99)<br />modfl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/modf) | 把一个数拆分成整数和小数部分 (函数)     |
| **frexp** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/frexp)** |                                         |





### hypot

原址：[https://zh.cppreference.com/w/c/numeric/math/hypot](https://zh.cppreference.com/w/c/numeric/math/hypot)

作用：计算两个给定数平方和的平方根（\scriptsize{\sqrt{x^2+y^2} }\scriptsize{\sqrt{x^2+y^2} }√x2+y2）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       hypotf( float x, float y );// (1)(C99 起)
double      hypot( double x, double y );// (2)(C99 起)
long double hypotl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define hypot( x, y )// (4)(C99 起)
```

1-3) 计算 `x` 与 `y` 平方和的平方根，而不会在计算的中间阶段有过度的上溢或下溢。

4） 泛型宏：若任何实参拥有 `long double` 类型，则调用函数的 `long double` 版本。否则，若任何实参拥有整数类型或 `double` 类型，则调用函数的 `double` 版本。否则，调用函数的 `float` 版本。

​	此函数计算的值是直角边长度为 `x` 和 `y` 的直角三角形的斜边长，或点 `(x, y)` 距原点 `(0, 0)` 的距离，或复数 `x+*i*y` 的绝对值。

**参数**

| x    | -    | 浮点数 |
| ---- | ---- | ------ |
| y    | -    | 浮点数 |

**返回值**

​	若不出现错误，则返回直角三角形的斜边，√x2+y2x2+y2。

​	若出现上溢所致的值域错误，则返回 [+HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- `hypot(x, y)`、`hypot(y, x)` 及 `hypot(x, -y)` 等价
- 若实参之一为 ±0，则 `hypot` 等价于以非零实参调用 `[fabs](http://zh.cppreference.com/w/c/numeric/math/fabs)`
- 若实参之一为 ±∞，则 `hypot` 返回 +∞，即使另一参数为 NaN
- 否则，若任何实参为 NaN，则返回 NaN

**注解**

​	实现通常保证小于 1 ulp（[最后位置单位](https://en.wikipedia.org/wiki/Unit_in_the_last_place)）的精度：[GNU](https://sourceware.org/git/?p=glibc.git;a=blob_plain;f=sysdeps/ieee754/dbl-64/e_hypot.c)、[BSD](https://www.freebsd.org/cgi/cvsweb.cgi/src/lib/msun/src/e_hypot.c?rev=1.13.4.2;content-type=text%2Fplain)。

​	`hypot(x, y)` 等价于 `[cabs](http://zh.cppreference.com/w/c/numeric/complex/cabs)(x + I*y)`。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/hypot.html)仅若两个实参均为非正规且正确结果亦为非正规才可以出现下溢（这禁止朴素实现）。

​	`hypot(INFINITY, NAN)` 返回 +∞，但 `[sqrt](http://zh.cppreference.com/w/c/numeric/math/sqrt)(INFINITY * INFINITY + NAN * NAN)` 返回 NaN。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    // 典型用法
    printf("笛卡尔坐标 (1,1) 是极坐标 (%f,%f)\n", hypot(1,1), atan2(1, 1));
    // 特殊值
    printf("hypot(NAN,INFINITY) = %f\n", hypot(NAN, INFINITY));
 
    // 错误处理
    errno = 0;
    feclearexcept(FE_ALL_EXCEPT);
    printf("hypot(DBL_MAX,DBL_MAX) = %f\n", hypot(DBL_MAX, DBL_MAX));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
笛卡尔坐标 (1,1) 是极坐标 (1.414214,0.785398)
hypot(NAN,INFINITY) = inf
hypot(DBL_MAX,DBL_MAX) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.7.3 The hypot functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.4.3 The hypot functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.7.3 The hypot functions （第 181 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.4.3 The hypot functions （第 382 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.7.3 The hypot functions （第 248 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.3 The hypot functions （第 524 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.7.3 The hypot functions （第 229 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.4.3 The hypot functions （第 461 页）

**参阅**

| [pow <br />powf (C99)<br />powl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/pow) | 计算一个数的给定次幂（xyxy） (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [sqrt <br />sqrtf (C99)<br />sqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sqrt) | 计算平方根（√xx） (函数)            |
| [cbrt (C99)<br />cbrtf (C99)<br />cbrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cbrt) | 计算立方根（3√xx3） (函数)          |
| [cabs (C99)<br />cabsf (C99)<br />cabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cabs) | 计算复数的模（绝对值） (函数)       |
| **hypot** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/hypot)** |                                     |





### hypotf

原址：[https://zh.cppreference.com/w/c/numeric/math/hypot](https://zh.cppreference.com/w/c/numeric/math/hypot)

作用：计算两个给定数平方和的平方根（\scriptsize{\sqrt{x^2+y^2} }\scriptsize{\sqrt{x^2+y^2} }√x2+y2）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       hypotf( float x, float y );// (1)(C99 起)
double      hypot( double x, double y );// (2)(C99 起)
long double hypotl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define hypot( x, y )// (4)(C99 起)
```

1-3) 计算 `x` 与 `y` 平方和的平方根，而不会在计算的中间阶段有过度的上溢或下溢。

4） 泛型宏：若任何实参拥有 `long double` 类型，则调用函数的 `long double` 版本。否则，若任何实参拥有整数类型或 `double` 类型，则调用函数的 `double` 版本。否则，调用函数的 `float` 版本。

​	此函数计算的值是直角边长度为 `x` 和 `y` 的直角三角形的斜边长，或点 `(x, y)` 距原点 `(0, 0)` 的距离，或复数 `x+*i*y` 的绝对值。

**参数**

| x    | -    | 浮点数 |
| ---- | ---- | ------ |
| y    | -    | 浮点数 |

**返回值**

​	若不出现错误，则返回直角三角形的斜边，√x2+y2x2+y2。

​	若出现上溢所致的值域错误，则返回 [+HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- `hypot(x, y)`、`hypot(y, x)` 及 `hypot(x, -y)` 等价
- 若实参之一为 ±0，则 `hypot` 等价于以非零实参调用 `[fabs](http://zh.cppreference.com/w/c/numeric/math/fabs)`
- 若实参之一为 ±∞，则 `hypot` 返回 +∞，即使另一参数为 NaN
- 否则，若任何实参为 NaN，则返回 NaN

**注解**

​	实现通常保证小于 1 ulp（[最后位置单位](https://en.wikipedia.org/wiki/Unit_in_the_last_place)）的精度：[GNU](https://sourceware.org/git/?p=glibc.git;a=blob_plain;f=sysdeps/ieee754/dbl-64/e_hypot.c)、[BSD](https://www.freebsd.org/cgi/cvsweb.cgi/src/lib/msun/src/e_hypot.c?rev=1.13.4.2;content-type=text%2Fplain)。

​	`hypot(x, y)` 等价于 `[cabs](http://zh.cppreference.com/w/c/numeric/complex/cabs)(x + I*y)`。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/hypot.html)仅若两个实参均为非正规且正确结果亦为非正规才可以出现下溢（这禁止朴素实现）。

​	`hypot(INFINITY, NAN)` 返回 +∞，但 `[sqrt](http://zh.cppreference.com/w/c/numeric/math/sqrt)(INFINITY * INFINITY + NAN * NAN)` 返回 NaN。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    // 典型用法
    printf("笛卡尔坐标 (1,1) 是极坐标 (%f,%f)\n", hypot(1,1), atan2(1, 1));
    // 特殊值
    printf("hypot(NAN,INFINITY) = %f\n", hypot(NAN, INFINITY));
 
    // 错误处理
    errno = 0;
    feclearexcept(FE_ALL_EXCEPT);
    printf("hypot(DBL_MAX,DBL_MAX) = %f\n", hypot(DBL_MAX, DBL_MAX));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
笛卡尔坐标 (1,1) 是极坐标 (1.414214,0.785398)
hypot(NAN,INFINITY) = inf
hypot(DBL_MAX,DBL_MAX) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.7.3 The hypot functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.4.3 The hypot functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.7.3 The hypot functions （第 181 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.4.3 The hypot functions （第 382 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.7.3 The hypot functions （第 248 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.3 The hypot functions （第 524 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.7.3 The hypot functions （第 229 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.4.3 The hypot functions （第 461 页）

**参阅**

| [pow <br />powf (C99)<br />powl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/pow) | 计算一个数的给定次幂（xyxy） (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [sqrt <br />sqrtf (C99)<br />sqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sqrt) | 计算平方根（√xx） (函数)            |
| [cbrt (C99)<br />cbrtf (C99)<br />cbrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cbrt) | 计算立方根（3√xx3） (函数)          |
| [cabs (C99)<br />cabsf (C99)<br />cabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cabs) | 计算复数的模（绝对值） (函数)       |
| **hypot** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/hypot)** |                                     |





### hypotl

原址：[https://zh.cppreference.com/w/c/numeric/math/hypot](https://zh.cppreference.com/w/c/numeric/math/hypot)

作用：计算两个给定数平方和的平方根（\scriptsize{\sqrt{x^2+y^2} }\scriptsize{\sqrt{x^2+y^2} }√x2+y2）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       hypotf( float x, float y );// (1)(C99 起)
double      hypot( double x, double y );// (2)(C99 起)
long double hypotl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define hypot( x, y )// (4)(C99 起)
```

1-3) 计算 `x` 与 `y` 平方和的平方根，而不会在计算的中间阶段有过度的上溢或下溢。

4） 泛型宏：若任何实参拥有 `long double` 类型，则调用函数的 `long double` 版本。否则，若任何实参拥有整数类型或 `double` 类型，则调用函数的 `double` 版本。否则，调用函数的 `float` 版本。

​	此函数计算的值是直角边长度为 `x` 和 `y` 的直角三角形的斜边长，或点 `(x, y)` 距原点 `(0, 0)` 的距离，或复数 `x+*i*y` 的绝对值。

**参数**

| x    | -    | 浮点数 |
| ---- | ---- | ------ |
| y    | -    | 浮点数 |

**返回值**

​	若不出现错误，则返回直角三角形的斜边，√x2+y2x2+y2。

​	若出现上溢所致的值域错误，则返回 [+HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- `hypot(x, y)`、`hypot(y, x)` 及 `hypot(x, -y)` 等价
- 若实参之一为 ±0，则 `hypot` 等价于以非零实参调用 `[fabs](http://zh.cppreference.com/w/c/numeric/math/fabs)`
- 若实参之一为 ±∞，则 `hypot` 返回 +∞，即使另一参数为 NaN
- 否则，若任何实参为 NaN，则返回 NaN

**注解**

​	实现通常保证小于 1 ulp（[最后位置单位](https://en.wikipedia.org/wiki/Unit_in_the_last_place)）的精度：[GNU](https://sourceware.org/git/?p=glibc.git;a=blob_plain;f=sysdeps/ieee754/dbl-64/e_hypot.c)、[BSD](https://www.freebsd.org/cgi/cvsweb.cgi/src/lib/msun/src/e_hypot.c?rev=1.13.4.2;content-type=text%2Fplain)。

​	`hypot(x, y)` 等价于 `[cabs](http://zh.cppreference.com/w/c/numeric/complex/cabs)(x + I*y)`。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/hypot.html)仅若两个实参均为非正规且正确结果亦为非正规才可以出现下溢（这禁止朴素实现）。

​	`hypot(INFINITY, NAN)` 返回 +∞，但 `[sqrt](http://zh.cppreference.com/w/c/numeric/math/sqrt)(INFINITY * INFINITY + NAN * NAN)` 返回 NaN。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    // 典型用法
    printf("笛卡尔坐标 (1,1) 是极坐标 (%f,%f)\n", hypot(1,1), atan2(1, 1));
    // 特殊值
    printf("hypot(NAN,INFINITY) = %f\n", hypot(NAN, INFINITY));
 
    // 错误处理
    errno = 0;
    feclearexcept(FE_ALL_EXCEPT);
    printf("hypot(DBL_MAX,DBL_MAX) = %f\n", hypot(DBL_MAX, DBL_MAX));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
笛卡尔坐标 (1,1) 是极坐标 (1.414214,0.785398)
hypot(NAN,INFINITY) = inf
hypot(DBL_MAX,DBL_MAX) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.7.3 The hypot functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.4.3 The hypot functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.7.3 The hypot functions （第 181 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.4.3 The hypot functions （第 382 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.7.3 The hypot functions （第 248 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.3 The hypot functions （第 524 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.7.3 The hypot functions （第 229 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.4.3 The hypot functions （第 461 页）

**参阅**

| [pow <br />powf (C99)<br />powl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/pow) | 计算一个数的给定次幂（xyxy） (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [sqrt <br />sqrtf (C99)<br />sqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sqrt) | 计算平方根（√xx） (函数)            |
| [cbrt (C99)<br />cbrtf (C99)<br />cbrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cbrt) | 计算立方根（3√xx3） (函数)          |
| [cabs (C99)<br />cabsf (C99)<br />cabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cabs) | 计算复数的模（绝对值） (函数)       |
| **hypot** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/hypot)** |                                     |





### ilogb

原址：[https://zh.cppreference.com/w/c/numeric/math/ilogb](https://zh.cppreference.com/w/c/numeric/math/ilogb)

作用：提取给定数的指数（结果为整数）   (函数)

备注：
```c
// 在标头 <math.h> 定义
int ilogbf( float arg );// (1)(C99 起)
int ilogb( double arg );// (2)(C99 起)
int ilogbl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define ilogb( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
#define FP_ILOGB0    /* 由实现定义 */// (5)(C99 起)
#define FP_ILOGBNAN  /* 由实现定义 */// (6)(C99 起)
```

1-3) 从浮点数实参 `arg` 提取独立于基底的无偏指数，并将它作为有符号整数返回。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `ilogbl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `ilogb`。否则调用 `ilogbf`。

5） 展开成整数常量表达式，值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 或 `-[INT_MAX](http://zh.cppreference.com/w/c/types/limits)`。

6） 展开成整数常量表达式，值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 或 `+[INT_MAX](http://zh.cppreference.com/w/c/types/limits)`。

​	正式而言，无偏指数是非零 `arg` 的 *logr|arg|* 的整数部分，作为有符号整数，其中 `r` 是 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits)。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回作为 int 值的 `arg` 的无偏指数。

​	若 `arg` 为零，则返回 FP_ILOGB0。

​	若 `arg` 为无穷大，则返回 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)。

​	若 `arg` 为 NaN，则返回 FP_ILOGBNAN。

​	若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)，则返回值未指定，且可能出现定义域或值域错误。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 为零、无穷大或 NaN ，则可能出现定义域错误或值域错误。

​	若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) ，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `arg` 为 ±0、 ±∞ 或 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 所有其他情况下，结果是准确的（决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）并且忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**注解**

​	若 `arg` 不是零、无穷大或 NaN，则返回的值准确等价于 `(int)[logb](http://zh.cppreference.com/w/c/numeric/math/logb)(arg)`。

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/ilogb.html)若 `arg` 为零、无穷大、NaN 或若正确结果在 `int` 的范围外则出现定义域错误。

​	POSIX 亦要求在 XSI 一致的系统上，正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 时返回值为 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)，而正确结果小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 时返回值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)。

​	在所有已知平台上正确结果都能表示成 `int`。对于要出现溢出的情况，[INT_MAX](https://zh.cppreference.com/w/c/types/limits) 必须小于 `[LDBL_MAX_EXP](http://zh.cppreference.com/w/c/types/limits) * log2([FLT_RADIX](http://zh.cppreference.com/w/c/types/limits))` 或 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 必须大于 `[LDBL_MIN_EXP](http://zh.cppreference.com/w/c/types/limits) - [LDBL_MANT_DIG](http://zh.cppreference.com/w/c/types/limits)) * log2([FLT_RADIX](http://zh.cppreference.com/w/c/types/limits))`。

​	`ilogb` 所返回的指数值始终比 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 所返回的小 1，因为不同的正规化要求：对于 `ilogb` 返回的指数 `e`，*|arg\*r-e
|* 在 1 与 `r` 之间（典型地在 `1` 与 `2` 之间），但 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 返回的指数 `e`，*|arg\*2-e
|* 在 `0.5` 与 `1` 之间。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12/8 Mathematics <math.h> （第 TBD 页）

  - 7.12.6.5 The ilogb functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.5 The ilogb functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/8 Mathematics <math.h> （第 TBD 页）

  - 7.12.6.5 The ilogb functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.5 The ilogb functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/8 Mathematics <math.h> （第 232 页）

  - 7.12.6.5 The ilogb functions （第 244 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.5 The ilogb functions （第 521 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/8 Mathematics <math.h> （第 213 页）

  - 7.12.6.5 The ilogb functions （第 224-225 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.5 The ilogb functions （第 458 页）

**参阅**

| [frexp <br />frexpf (C99)<br />frexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/frexp) | 将数拆分成有效数字和 *2* 的幂次 (函数)                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [logb (C99)<br />logbf (C99)<br />logbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/logb) | 提取给定数的指数（结果为浮点数） (函数)                      |
| [scalbn (C99)<br />scalbnf (C99)<br />scalbnl (C99)<br />scalbln (C99)<br />scalblnf (C99)<br />scalblnl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/scalbn) | 高效计算一个数乘 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 的幂 (函数) |
| **ilogb** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/ilogb)** |                                                              |





### ilogbf

原址：[https://zh.cppreference.com/w/c/numeric/math/ilogb](https://zh.cppreference.com/w/c/numeric/math/ilogb)

作用：提取给定数的指数（结果为整数）   (函数)

备注：
```c
// 在标头 <math.h> 定义
int ilogbf( float arg );// (1)(C99 起)
int ilogb( double arg );// (2)(C99 起)
int ilogbl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define ilogb( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
#define FP_ILOGB0    /* 由实现定义 */// (5)(C99 起)
#define FP_ILOGBNAN  /* 由实现定义 */// (6)(C99 起)
```

1-3) 从浮点数实参 `arg` 提取独立于基底的无偏指数，并将它作为有符号整数返回。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `ilogbl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `ilogb`。否则调用 `ilogbf`。

5） 展开成整数常量表达式，值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 或 `-[INT_MAX](http://zh.cppreference.com/w/c/types/limits)`。

6） 展开成整数常量表达式，值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 或 `+[INT_MAX](http://zh.cppreference.com/w/c/types/limits)`。

​	正式而言，无偏指数是非零 `arg` 的 *logr|arg|* 的整数部分，作为有符号整数，其中 `r` 是 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits)。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回作为 int 值的 `arg` 的无偏指数。

​	若 `arg` 为零，则返回 FP_ILOGB0。

​	若 `arg` 为无穷大，则返回 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)。

​	若 `arg` 为 NaN，则返回 FP_ILOGBNAN。

​	若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)，则返回值未指定，且可能出现定义域或值域错误。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 为零、无穷大或 NaN ，则可能出现定义域错误或值域错误。

​	若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) ，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `arg` 为 ±0、 ±∞ 或 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 所有其他情况下，结果是准确的（决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）并且忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**注解**

​	若 `arg` 不是零、无穷大或 NaN，则返回的值准确等价于 `(int)[logb](http://zh.cppreference.com/w/c/numeric/math/logb)(arg)`。

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/ilogb.html)若 `arg` 为零、无穷大、NaN 或若正确结果在 `int` 的范围外则出现定义域错误。

​	POSIX 亦要求在 XSI 一致的系统上，正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 时返回值为 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)，而正确结果小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 时返回值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)。

​	在所有已知平台上正确结果都能表示成 `int`。对于要出现溢出的情况，[INT_MAX](https://zh.cppreference.com/w/c/types/limits) 必须小于 `[LDBL_MAX_EXP](http://zh.cppreference.com/w/c/types/limits) * log2([FLT_RADIX](http://zh.cppreference.com/w/c/types/limits))` 或 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 必须大于 `[LDBL_MIN_EXP](http://zh.cppreference.com/w/c/types/limits) - [LDBL_MANT_DIG](http://zh.cppreference.com/w/c/types/limits)) * log2([FLT_RADIX](http://zh.cppreference.com/w/c/types/limits))`。

​	`ilogb` 所返回的指数值始终比 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 所返回的小 1，因为不同的正规化要求：对于 `ilogb` 返回的指数 `e`，*|arg\*r-e
|* 在 1 与 `r` 之间（典型地在 `1` 与 `2` 之间），但 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 返回的指数 `e`，*|arg\*2-e
|* 在 `0.5` 与 `1` 之间。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12/8 Mathematics <math.h> （第 TBD 页）

  - 7.12.6.5 The ilogb functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.5 The ilogb functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/8 Mathematics <math.h> （第 TBD 页）

  - 7.12.6.5 The ilogb functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.5 The ilogb functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/8 Mathematics <math.h> （第 232 页）

  - 7.12.6.5 The ilogb functions （第 244 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.5 The ilogb functions （第 521 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/8 Mathematics <math.h> （第 213 页）

  - 7.12.6.5 The ilogb functions （第 224-225 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.5 The ilogb functions （第 458 页）

**参阅**

| [frexp <br />frexpf (C99)<br />frexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/frexp) | 将数拆分成有效数字和 *2* 的幂次 (函数)                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [logb (C99)<br />logbf (C99)<br />logbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/logb) | 提取给定数的指数（结果为浮点数） (函数)                      |
| [scalbn (C99)<br />scalbnf (C99)<br />scalbnl (C99)<br />scalbln (C99)<br />scalblnf (C99)<br />scalblnl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/scalbn) | 高效计算一个数乘 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 的幂 (函数) |
| **ilogb** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/ilogb)** |                                                              |





### ilogbl

原址：[https://zh.cppreference.com/w/c/numeric/math/ilogb](https://zh.cppreference.com/w/c/numeric/math/ilogb)

作用：提取给定数的指数（结果为整数）   (函数)

备注：
```c
// 在标头 <math.h> 定义
int ilogbf( float arg );// (1)(C99 起)
int ilogb( double arg );// (2)(C99 起)
int ilogbl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define ilogb( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
#define FP_ILOGB0    /* 由实现定义 */// (5)(C99 起)
#define FP_ILOGBNAN  /* 由实现定义 */// (6)(C99 起)
```

1-3) 从浮点数实参 `arg` 提取独立于基底的无偏指数，并将它作为有符号整数返回。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `ilogbl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `ilogb`。否则调用 `ilogbf`。

5） 展开成整数常量表达式，值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 或 `-[INT_MAX](http://zh.cppreference.com/w/c/types/limits)`。

6） 展开成整数常量表达式，值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 或 `+[INT_MAX](http://zh.cppreference.com/w/c/types/limits)`。

​	正式而言，无偏指数是非零 `arg` 的 *logr|arg|* 的整数部分，作为有符号整数，其中 `r` 是 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits)。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回作为 int 值的 `arg` 的无偏指数。

​	若 `arg` 为零，则返回 FP_ILOGB0。

​	若 `arg` 为无穷大，则返回 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)。

​	若 `arg` 为 NaN，则返回 FP_ILOGBNAN。

​	若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)，则返回值未指定，且可能出现定义域或值域错误。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 为零、无穷大或 NaN ，则可能出现定义域错误或值域错误。

​	若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) ，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 或小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `arg` 为 ±0、 ±∞ 或 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 所有其他情况下，结果是准确的（决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）并且忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**注解**

​	若 `arg` 不是零、无穷大或 NaN，则返回的值准确等价于 `(int)[logb](http://zh.cppreference.com/w/c/numeric/math/logb)(arg)`。

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/ilogb.html)若 `arg` 为零、无穷大、NaN 或若正确结果在 `int` 的范围外则出现定义域错误。

​	POSIX 亦要求在 XSI 一致的系统上，正确结果大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 时返回值为 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)，而正确结果小于 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 时返回值为 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)。

​	在所有已知平台上正确结果都能表示成 `int`。对于要出现溢出的情况，[INT_MAX](https://zh.cppreference.com/w/c/types/limits) 必须小于 `[LDBL_MAX_EXP](http://zh.cppreference.com/w/c/types/limits) * log2([FLT_RADIX](http://zh.cppreference.com/w/c/types/limits))` 或 [INT_MIN](https://zh.cppreference.com/w/c/types/limits) 必须大于 `[LDBL_MIN_EXP](http://zh.cppreference.com/w/c/types/limits) - [LDBL_MANT_DIG](http://zh.cppreference.com/w/c/types/limits)) * log2([FLT_RADIX](http://zh.cppreference.com/w/c/types/limits))`。

​	`ilogb` 所返回的指数值始终比 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 所返回的小 1，因为不同的正规化要求：对于 `ilogb` 返回的指数 `e`，*|arg\*r-e
|* 在 1 与 `r` 之间（典型地在 `1` 与 `2` 之间），但 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 返回的指数 `e`，*|arg\*2-e
|* 在 `0.5` 与 `1` 之间。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12/8 Mathematics <math.h> （第 TBD 页）

  - 7.12.6.5 The ilogb functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.5 The ilogb functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12/8 Mathematics <math.h> （第 TBD 页）

  - 7.12.6.5 The ilogb functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.5 The ilogb functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12/8 Mathematics <math.h> （第 232 页）

  - 7.12.6.5 The ilogb functions （第 244 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.5 The ilogb functions （第 521 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12/8 Mathematics <math.h> （第 213 页）

  - 7.12.6.5 The ilogb functions （第 224-225 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.5 The ilogb functions （第 458 页）

**参阅**

| [frexp <br />frexpf (C99)<br />frexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/frexp) | 将数拆分成有效数字和 *2* 的幂次 (函数)                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [logb (C99)<br />logbf (C99)<br />logbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/logb) | 提取给定数的指数（结果为浮点数） (函数)                      |
| [scalbn (C99)<br />scalbnf (C99)<br />scalbnl (C99)<br />scalbln (C99)<br />scalblnf (C99)<br />scalblnl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/scalbn) | 高效计算一个数乘 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 的幂 (函数) |
| **ilogb** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/ilogb)** |                                                              |





### ldexp

原址：[https://zh.cppreference.com/w/c/numeric/math/ldexp](https://zh.cppreference.com/w/c/numeric/math/ldexp)

作用：将数乘以 2 的幂  (函数)

备注：
```c
// 在标头 <math.h> 定义
float       ldexpf( float arg, int exp );// (1)(C99 起)
double      ldexp( double arg, int exp );// (2)
long double ldexpl( long double arg, int exp );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define ldexp( arg, exp )// (4)(C99 起)
```

1-3) 将浮点数 `arg` 乘以 `2` 的 `[exp](http://zh.cppreference.com/w/c/numeric/math/exp)` 次幂。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `ldexpl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `ldexp`。否则调用 `ldexpf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
| exp  | -    | 整数   |

**返回值**

​	若不出现错误，则返回 `arg` 乘 2 的 `[exp](http://zh.cppreference.com/w/c/numeric/math/exp)` 次幂（*arg×2exp
*）。

​	若出现上溢所致的值域错误，则返回 `±HUGE_VAL`、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)，除非出现值域错误（结果准确）
- 忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，除非出现值域错误
- 若 `arg` 为 ±0，则返回不修改的参数
- 若 `arg` 为 ±∞，则返回不修改的参数
- 若 `[exp](http://zh.cppreference.com/w/c/numeric/math/exp)` 为 0，则返回不修改的 `arg`
- 若 `arg` 为 NaN，则返回 NaN

**注解**

​	二进制系统上（其中 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 为 `2`），`ldexp` 等价于 [scalbn](https://zh.cppreference.com/w/c/numeric/math/scalbn)。

​	函数 `ldexp`（“加载指数”）与其对偶 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 能一同用于操纵浮点数的表示，而无需直接的位操作。

​	多数实现上，`ldexp` 效率低于用通常算术运算符乘或除以二的幂。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("ldexp(7, -4) = %f\n", ldexp(7, -4));
    printf("ldexp(1, -1074) = %g (double 的最小非正规正值)\n",
            ldexp(1, -1074));
    printf("ldexp(nextafter(1,0), 1024) = %g (double 的最大有限值)\n",
            ldexp(nextafter(1,0), 1024));
    // 特殊值
    printf("ldexp(-0, 10) = %f\n", ldexp(-0.0, 10));
    printf("ldexp(-Inf, -1) = %f\n", ldexp(-INFINITY, -1));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("ldexp(1, 1024) = %f\n", ldexp(1, 1024));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
ldexp(7, -4) = 0.437500
ldexp(1, -1074) = 4.94066e-324 (double 的最小非正规正值)
ldexp(nextafter(1,0), 1024) = 1.79769e+308 (double 的最大有限值)
ldexp(-0, 10) = -0.000000
ldexp(-Inf, -1) = -inf
ldexp(1, 1024) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.6 The ldexp functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.6 The ldexp functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.6 The ldexp functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.6 The ldexp functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.6 The ldexp functions （第 244 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.6 The ldexp functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.6 The ldexp functions （第 225 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.6 The ldexp functions （第 459 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.3 The ldexp function

**参阅**

| [frexp <br />frexpf (C99)<br />frexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/frexp) | 将数拆分成有效数字和 *2* 的幂次 (函数)                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [scalbn (C99)<br />scalbnf (C99)<br />scalbnl (C99)<br />scalbln (C99)<br />scalblnf (C99)<br />scalblnl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/scalbn) | 高效计算一个数乘 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 的幂 (函数) |
| **ldexp** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/ldexp)** |                                                              |





### ldexpf

原址：[https://zh.cppreference.com/w/c/numeric/math/ldexp](https://zh.cppreference.com/w/c/numeric/math/ldexp)

作用：将数乘以 2 的幂  (函数)

备注：
```c
// 在标头 <math.h> 定义
float       ldexpf( float arg, int exp );// (1)(C99 起)
double      ldexp( double arg, int exp );// (2)
long double ldexpl( long double arg, int exp );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define ldexp( arg, exp )// (4)(C99 起)
```

1-3) 将浮点数 `arg` 乘以 `2` 的 `[exp](http://zh.cppreference.com/w/c/numeric/math/exp)` 次幂。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `ldexpl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `ldexp`。否则调用 `ldexpf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
| exp  | -    | 整数   |

**返回值**

​	若不出现错误，则返回 `arg` 乘 2 的 `[exp](http://zh.cppreference.com/w/c/numeric/math/exp)` 次幂（*arg×2exp
*）。

​	若出现上溢所致的值域错误，则返回 `±HUGE_VAL`、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)，除非出现值域错误（结果准确）
- 忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，除非出现值域错误
- 若 `arg` 为 ±0，则返回不修改的参数
- 若 `arg` 为 ±∞，则返回不修改的参数
- 若 `[exp](http://zh.cppreference.com/w/c/numeric/math/exp)` 为 0，则返回不修改的 `arg`
- 若 `arg` 为 NaN，则返回 NaN

**注解**

​	二进制系统上（其中 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 为 `2`），`ldexp` 等价于 [scalbn](https://zh.cppreference.com/w/c/numeric/math/scalbn)。

​	函数 `ldexp`（“加载指数”）与其对偶 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 能一同用于操纵浮点数的表示，而无需直接的位操作。

​	多数实现上，`ldexp` 效率低于用通常算术运算符乘或除以二的幂。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("ldexp(7, -4) = %f\n", ldexp(7, -4));
    printf("ldexp(1, -1074) = %g (double 的最小非正规正值)\n",
            ldexp(1, -1074));
    printf("ldexp(nextafter(1,0), 1024) = %g (double 的最大有限值)\n",
            ldexp(nextafter(1,0), 1024));
    // 特殊值
    printf("ldexp(-0, 10) = %f\n", ldexp(-0.0, 10));
    printf("ldexp(-Inf, -1) = %f\n", ldexp(-INFINITY, -1));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("ldexp(1, 1024) = %f\n", ldexp(1, 1024));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
ldexp(7, -4) = 0.437500
ldexp(1, -1074) = 4.94066e-324 (double 的最小非正规正值)
ldexp(nextafter(1,0), 1024) = 1.79769e+308 (double 的最大有限值)
ldexp(-0, 10) = -0.000000
ldexp(-Inf, -1) = -inf
ldexp(1, 1024) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.6 The ldexp functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.6 The ldexp functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.6 The ldexp functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.6 The ldexp functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.6 The ldexp functions （第 244 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.6 The ldexp functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.6 The ldexp functions （第 225 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.6 The ldexp functions （第 459 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.3 The ldexp function

**参阅**

| [frexp <br />frexpf (C99)<br />frexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/frexp) | 将数拆分成有效数字和 *2* 的幂次 (函数)                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [scalbn (C99)<br />scalbnf (C99)<br />scalbnl (C99)<br />scalbln (C99)<br />scalblnf (C99)<br />scalblnl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/scalbn) | 高效计算一个数乘 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 的幂 (函数) |
| **ldexp** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/ldexp)** |                                                              |





### ldexpl

原址：[https://zh.cppreference.com/w/c/numeric/math/ldexp](https://zh.cppreference.com/w/c/numeric/math/ldexp)

作用：将数乘以 2 的幂  (函数)

备注：
```c
// 在标头 <math.h> 定义
float       ldexpf( float arg, int exp );// (1)(C99 起)
double      ldexp( double arg, int exp );// (2)
long double ldexpl( long double arg, int exp );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define ldexp( arg, exp )// (4)(C99 起)
```

1-3) 将浮点数 `arg` 乘以 `2` 的 `[exp](http://zh.cppreference.com/w/c/numeric/math/exp)` 次幂。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `ldexpl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `ldexp`。否则调用 `ldexpf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
| exp  | -    | 整数   |

**返回值**

​	若不出现错误，则返回 `arg` 乘 2 的 `[exp](http://zh.cppreference.com/w/c/numeric/math/exp)` 次幂（*arg×2exp
*）。

​	若出现上溢所致的值域错误，则返回 `±HUGE_VAL`、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)，除非出现值域错误（结果准确）
- 忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，除非出现值域错误
- 若 `arg` 为 ±0，则返回不修改的参数
- 若 `arg` 为 ±∞，则返回不修改的参数
- 若 `[exp](http://zh.cppreference.com/w/c/numeric/math/exp)` 为 0，则返回不修改的 `arg`
- 若 `arg` 为 NaN，则返回 NaN

**注解**

​	二进制系统上（其中 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 为 `2`），`ldexp` 等价于 [scalbn](https://zh.cppreference.com/w/c/numeric/math/scalbn)。

​	函数 `ldexp`（“加载指数”）与其对偶 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 能一同用于操纵浮点数的表示，而无需直接的位操作。

​	多数实现上，`ldexp` 效率低于用通常算术运算符乘或除以二的幂。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("ldexp(7, -4) = %f\n", ldexp(7, -4));
    printf("ldexp(1, -1074) = %g (double 的最小非正规正值)\n",
            ldexp(1, -1074));
    printf("ldexp(nextafter(1,0), 1024) = %g (double 的最大有限值)\n",
            ldexp(nextafter(1,0), 1024));
    // 特殊值
    printf("ldexp(-0, 10) = %f\n", ldexp(-0.0, 10));
    printf("ldexp(-Inf, -1) = %f\n", ldexp(-INFINITY, -1));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("ldexp(1, 1024) = %f\n", ldexp(1, 1024));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
ldexp(7, -4) = 0.437500
ldexp(1, -1074) = 4.94066e-324 (double 的最小非正规正值)
ldexp(nextafter(1,0), 1024) = 1.79769e+308 (double 的最大有限值)
ldexp(-0, 10) = -0.000000
ldexp(-Inf, -1) = -inf
ldexp(1, 1024) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.6 The ldexp functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.6 The ldexp functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.6 The ldexp functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.6 The ldexp functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.6 The ldexp functions （第 244 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.6 The ldexp functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.6 The ldexp functions （第 225 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.6 The ldexp functions （第 459 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.3 The ldexp function

**参阅**

| [frexp <br />frexpf (C99)<br />frexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/frexp) | 将数拆分成有效数字和 *2* 的幂次 (函数)                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [scalbn (C99)<br />scalbnf (C99)<br />scalbnl (C99)<br />scalbln (C99)<br />scalblnf (C99)<br />scalblnl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/scalbn) | 高效计算一个数乘 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 的幂 (函数) |
| **ldexp** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/ldexp)** |                                                              |





### lgamma

原址：[https://zh.cppreference.com/w/c/numeric/math/lgamma](https://zh.cppreference.com/w/c/numeric/math/lgamma)

作用：计算伽马函数的自然对数（底为 e）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       lgammaf( float arg );// (1)(C99 起)
double      lgamma( double arg );// (2)(C99 起)
long double lgammal( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define lgamma( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的[伽马函数](https://en.wikipedia.org/wiki/Gamma_function)绝对值的自然对数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `lgammal`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `lgamma`。否则调用`lgammaf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的伽马函数的自然对数，即 loge|∫∞0targ−1e−tdt|loge⁡|∫0∞targ−1e−tdt|。

​	若出现极点错误，则返回 [+HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 为零或为小于零的整数，则可能出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 1，则返回 +0。
- 若实参为 2，则返回 +0。
- 若实参为 ±0，则返回 +∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若实参为负整数，则返回 +∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若实参为 ±∞，则返回 +∞。
- 若实参为 NaN，则返回 NaN。

**注解**

​	若 `arg` 为自然数，则 `lgamma(arg)` 是 `arg-1` 阶乘的自然对数。

​	[lgamma 的 POSIX 版本](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lgamma.html)不是线程安全的：每次执行函数都会存储 `arg` 的伽马函数的符号于静态外部变量 `signgam`。一些实现提供 `lgamma_r`，它接收指向 singgam 的用户提供存储的指针为第二参数，而且是线程安全的。

​	多数实现中有名为 `gamma` 的非标准函数，但其定义不一致。例如，`gamma` 的 glibc 和 4.2BSD 版本执行 `lgamma`，但 `gamma` 的 4.4BSD 版本执行 `tgamma`。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("lgamma(10) = %f, log(9!) = %f\n", lgamma(10),
                                              log(2 * 3 * 4 * 5 * 6 * 7 * 8 * 9));
    const double pi = acos(-1);
    printf("lgamma(0.5) = %f, log(sqrt(pi)) = %f\n", log(sqrt(pi)), lgamma(0.5));
    // 特殊值
    printf("lgamma(1) = %f\n", lgamma(1));
    printf("lgamma(+Inf) = %f\n", lgamma(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("lgamma(0) = %f\n", lgamma(0));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
lgamma(10) = 12.801827, log(9!)=12.801827
lgamma(0.5) = 0.572365, log(sqrt(pi)) = 0.572365
lgamma(1) = 0.000000
lgamma(+Inf) = inf
lgamma(0) = inf
    errno == ERANGE: Numerical result out of range
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.8.3 The lgamma functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.5.3 The lgamma functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.8.3 The lgamma functions （第 182 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.5.3 The lgamma functions （第 383 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.8.3 The lgamma functions （第 250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.3 The lgamma functions （第 525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.8.3 The lgamma functions （第 231 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.5.3 The lgamma functions （第 462 页）

**参阅**

| [tgamma (C99)<br />tgammaf (C99)<br />tgammal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tgamma) | 计算伽马函数 (函数) |
| ------------------------------------------------------------ | ------------------- |
| **lgamma** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/lgamma)** |                     |

**外部链接**

​	[Weisstein, Eric W. “对数伽马函数”](http://mathworld.wolfram.com/LogGammaFunction.html)来自 MathWorld--A Wolfram Web Resource。





### lgammaf

原址：[https://zh.cppreference.com/w/c/numeric/math/lgamma](https://zh.cppreference.com/w/c/numeric/math/lgamma)

作用：计算伽马函数的自然对数（底为 e）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       lgammaf( float arg );// (1)(C99 起)
double      lgamma( double arg );// (2)(C99 起)
long double lgammal( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define lgamma( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的[伽马函数](https://en.wikipedia.org/wiki/Gamma_function)绝对值的自然对数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `lgammal`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `lgamma`。否则调用`lgammaf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的伽马函数的自然对数，即 loge|∫∞0targ−1e−tdt|loge⁡|∫0∞targ−1e−tdt|。

​	若出现极点错误，则返回 [+HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 为零或为小于零的整数，则可能出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 1，则返回 +0。
- 若实参为 2，则返回 +0。
- 若实参为 ±0，则返回 +∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若实参为负整数，则返回 +∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若实参为 ±∞，则返回 +∞。
- 若实参为 NaN，则返回 NaN。

**注解**

​	若 `arg` 为自然数，则 `lgamma(arg)` 是 `arg-1` 阶乘的自然对数。

​	[lgamma 的 POSIX 版本](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lgamma.html)不是线程安全的：每次执行函数都会存储 `arg` 的伽马函数的符号于静态外部变量 `signgam`。一些实现提供 `lgamma_r`，它接收指向 singgam 的用户提供存储的指针为第二参数，而且是线程安全的。

​	多数实现中有名为 `gamma` 的非标准函数，但其定义不一致。例如，`gamma` 的 glibc 和 4.2BSD 版本执行 `lgamma`，但 `gamma` 的 4.4BSD 版本执行 `tgamma`。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("lgamma(10) = %f, log(9!) = %f\n", lgamma(10),
                                              log(2 * 3 * 4 * 5 * 6 * 7 * 8 * 9));
    const double pi = acos(-1);
    printf("lgamma(0.5) = %f, log(sqrt(pi)) = %f\n", log(sqrt(pi)), lgamma(0.5));
    // 特殊值
    printf("lgamma(1) = %f\n", lgamma(1));
    printf("lgamma(+Inf) = %f\n", lgamma(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("lgamma(0) = %f\n", lgamma(0));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
lgamma(10) = 12.801827, log(9!)=12.801827
lgamma(0.5) = 0.572365, log(sqrt(pi)) = 0.572365
lgamma(1) = 0.000000
lgamma(+Inf) = inf
lgamma(0) = inf
    errno == ERANGE: Numerical result out of range
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.8.3 The lgamma functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.5.3 The lgamma functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.8.3 The lgamma functions （第 182 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.5.3 The lgamma functions （第 383 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.8.3 The lgamma functions （第 250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.3 The lgamma functions （第 525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.8.3 The lgamma functions （第 231 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.5.3 The lgamma functions （第 462 页）

**参阅**

| [tgamma (C99)<br />tgammaf (C99)<br />tgammal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tgamma) | 计算伽马函数 (函数) |
| ------------------------------------------------------------ | ------------------- |
| **lgamma** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/lgamma)** |                     |

**外部链接**

​	[Weisstein, Eric W. “对数伽马函数”](http://mathworld.wolfram.com/LogGammaFunction.html)来自 MathWorld--A Wolfram Web Resource。





### lgammal

原址：[https://zh.cppreference.com/w/c/numeric/math/lgamma](https://zh.cppreference.com/w/c/numeric/math/lgamma)

作用：计算伽马函数的自然对数（底为 e）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       lgammaf( float arg );// (1)(C99 起)
double      lgamma( double arg );// (2)(C99 起)
long double lgammal( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define lgamma( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的[伽马函数](https://en.wikipedia.org/wiki/Gamma_function)绝对值的自然对数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `lgammal`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `lgamma`。否则调用`lgammaf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的伽马函数的自然对数，即 loge|∫∞0targ−1e−tdt|loge⁡|∫0∞targ−1e−tdt|。

​	若出现极点错误，则返回 [+HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`+HUGE_VALF` 或 `+HUGE_VALL`。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 为零或为小于零的整数，则可能出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 1，则返回 +0。
- 若实参为 2，则返回 +0。
- 若实参为 ±0，则返回 +∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若实参为负整数，则返回 +∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若实参为 ±∞，则返回 +∞。
- 若实参为 NaN，则返回 NaN。

**注解**

​	若 `arg` 为自然数，则 `lgamma(arg)` 是 `arg-1` 阶乘的自然对数。

​	[lgamma 的 POSIX 版本](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lgamma.html)不是线程安全的：每次执行函数都会存储 `arg` 的伽马函数的符号于静态外部变量 `signgam`。一些实现提供 `lgamma_r`，它接收指向 singgam 的用户提供存储的指针为第二参数，而且是线程安全的。

​	多数实现中有名为 `gamma` 的非标准函数，但其定义不一致。例如，`gamma` 的 glibc 和 4.2BSD 版本执行 `lgamma`，但 `gamma` 的 4.4BSD 版本执行 `tgamma`。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("lgamma(10) = %f, log(9!) = %f\n", lgamma(10),
                                              log(2 * 3 * 4 * 5 * 6 * 7 * 8 * 9));
    const double pi = acos(-1);
    printf("lgamma(0.5) = %f, log(sqrt(pi)) = %f\n", log(sqrt(pi)), lgamma(0.5));
    // 特殊值
    printf("lgamma(1) = %f\n", lgamma(1));
    printf("lgamma(+Inf) = %f\n", lgamma(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("lgamma(0) = %f\n", lgamma(0));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
lgamma(10) = 12.801827, log(9!)=12.801827
lgamma(0.5) = 0.572365, log(sqrt(pi)) = 0.572365
lgamma(1) = 0.000000
lgamma(+Inf) = inf
lgamma(0) = inf
    errno == ERANGE: Numerical result out of range
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.8.3 The lgamma functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.5.3 The lgamma functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.8.3 The lgamma functions （第 182 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.5.3 The lgamma functions （第 383 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.8.3 The lgamma functions （第 250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.3 The lgamma functions （第 525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.8.3 The lgamma functions （第 231 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.5.3 The lgamma functions （第 462 页）

**参阅**

| [tgamma (C99)<br />tgammaf (C99)<br />tgammal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tgamma) | 计算伽马函数 (函数) |
| ------------------------------------------------------------ | ------------------- |
| **lgamma** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/lgamma)** |                     |

**外部链接**

​	[Weisstein, Eric W. “对数伽马函数”](http://mathworld.wolfram.com/LogGammaFunction.html)来自 MathWorld--A Wolfram Web Resource。





### llrint

原址：[https://zh.cppreference.com/w/c/numeric/math/rint](https://zh.cppreference.com/w/c/numeric/math/rint)

作用：使用当前舍入模式取整到整数，若结果有误则产生异常   (函数)

备注：
```c
// 在标头 <math.h> 定义
float rintf( float arg );// (1)(C99 起)
double rint( double arg );// (2)(C99 起)
long double rintl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define rint( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
long lrintf( float arg );// (5)(C99 起)
long lrint( double arg );// (6)(C99 起)
long lrintl( long double arg );// (7)(C99 起)
// 在标头 <tgmath.h> 定义
#define lrint( arg )// (8)(C99 起)
// 在标头 <math.h> 定义
long long llrintf( float arg );// (9)(C99 起)
long long llrint( double arg );// (10)(C99 起)
long long llrintl( long double arg );// (11)(C99 起)
// 在标头 <tgmath.h> 定义
#define llrint( arg )// (12)(C99 起)
```

1-3) 用[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，舍入浮点数实参 `arg` 为整数（以浮点数格式）。

5-7, 9-11) 用[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，舍入浮点数实参 `arg` 为整数。

4,8,12) 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `rintl`、`lrintl`、`llrintl`。否则若 `arg` 拥有整数或 `double` 类型，则调用 `rint`、`lrint`、`llrint`。否则分别调用 `rintf`、`lrintf`、`llrintf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则为 `arg` 按照[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)的最接近整数。

**错误处理**

​	报告 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `lrint` 或 `llrint` 的结果在返回类型的可表示范围外，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若 `arg` 为 ±∞，则返回未修改的实参
- 若 `arg` 为 ±0，则返回未修改的实参
- 若 `arg` 为 NaN，则返回 NaN

- 若 `arg` 为 ±∞，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值
- 若舍入结果在返回类型范围外，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值
- 若 `arg` 为 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值

**注解**

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lrint.html) `lrint` 或 `llrint` 引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的所有情况都是定义域错误。

​	如 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 所指定，`rint` 在舍入非整数有限值时可以（但不在非 IEEE 浮点数平台上要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	`rint` 和 [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint) 间仅有的区别是 [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint) 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数都是准确的整数，故 `rint` 自身决不上溢；然而在存储结果于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	若当前舍入模式为……

- [FE_DOWNWARD](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [floor](https://zh.cppreference.com/w/c/numeric/math/floor)。
- [FE_UPWARD](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [ceil](https://zh.cppreference.com/w/c/numeric/math/ceil)。
- [FE_TOWARDZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [trunc](https://zh.cppreference.com/w/c/numeric/math/trunc)。
- [FE_TONEAREST](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 在中点情况和 [round](https://zh.cppreference.com/w/c/numeric/math/round) 的区别是前者始终舍入到偶数，而非远离零。

**示例**

```c
#include <fenv.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
#pragma STDC FENV_ACCESS ON
    fesetround(FE_TONEAREST);
    printf("向临近舍入（半值舍入为偶数）:\n"
           "rint(+2.3) = %+.1f  ", rint(2.3));
    printf("rint(+2.5) = %+.1f  ", rint(2.5));
    printf("rint(+3.5) = %+.1f\n", rint(3.5));
    printf("rint(-2.3) = %+.1f  ", rint(-2.3));
    printf("rint(-2.5) = %+.1f  ", rint(-2.5));
    printf("rint(-3.5) = %+.1f\n", rint(-3.5));
 
    fesetround(FE_DOWNWARD);
    printf("向下舍入: \nrint(+2.3) = %+.1f  ", rint(2.3));
    printf("rint(+2.5) = %+.1f  ", rint(2.5));
    printf("rint(+3.5) = %+.1f\n", rint(3.5));
    printf("rint(-2.3) = %+.1f  ", rint(-2.3));
    printf("rint(-2.5) = %+.1f  ", rint(-2.5));
    printf("rint(-3.5) = %+.1f\n", rint(-3.5));
    printf("用 lrint 向下舍入: \nlrint(+2.3) = %ld  ", lrint(2.3));
    printf("lrint(+2.5) = %ld  ", lrint(2.5));
    printf("lrint(+3.5) = %ld\n", lrint(3.5));
    printf("lrint(-2.3) = %ld  ", lrint(-2.3));
    printf("lrint(-2.5) = %ld  ", lrint(-2.5));
    printf("lrint(-3.5) = %ld\n", lrint(-3.5));
 
    printf("lrint(-0.0) = %ld\n", lrint(-0.0));
    printf("lrint(-Inf) = %ld\n", lrint(-INFINITY)); // 引发 FE_INVALID
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("rint(1.1) = %.1f\n", rint(1.1));
    if (fetestexcept(FE_INEXACT))
        puts("    FE_INEXACT was raised");
 
    feclearexcept(FE_ALL_EXCEPT);
    printf("lrint(LONG_MIN-2048.0) = %ld\n", lrint(LONG_MIN-2048.0));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID was raised");
}
```

​	可能的输出：

```txt
向临近舍入（半值舍入为偶数）:
rint(+2.3) = +2.0  rint(+2.5) = +2.0  rint(+3.5) = +4.0
rint(-2.3) = -2.0  rint(-2.5) = -2.0  rint(-3.5) = -4.0
向下舍入: 
rint(+2.3) = +2.0  rint(+2.5) = +2.0  rint(+3.5) = +3.0
rint(-2.3) = -3.0  rint(-2.5) = -3.0  rint(-3.5) = -4.0
用 lrint 向下舍入: 
lrint(+2.3) = 2  lrint(+2.5) = 2  lrint(+3.5) = 3
lrint(-2.3) = -3  lrint(-2.5) = -3  lrint(-3.5) = -4
lrint(-0.0) = 0
lrint(-Inf) = -9223372036854775808
rint(1.1) = 1.0
    FE_INEXACT was raised
lrint(LONG_MIN-2048.0) = -9223372036854775808
    FE_INVALID was raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.4 The rint functions （第 TBD 页）

  - 7.12.9.5 The lrint and llrint functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.4 The rint functions （第 TBD 页）

  - F.10.6.5 The lrint and llrint functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.4 The rint functions （第 184 页）

  - 7.12.9.5 The lrint and llrint functions （第 184 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.6.4 The rint functions （第 384 页）

  - F.10.6.5 The lrint and llrint functions （第 384 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.4 The rint functions （第 252 页）

  - 7.12.9.5 The lrint and llrint functions （第 252 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.4 The rint functions （第 527 页）

  - F.10.6.5 The lrint and llrint functions （第 527 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.4 The rint functions （第 232-233 页）

  - 7.12.9.5 The lrint and llrint functions （第 233 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.4 The rint functions （第 463 页）

  - F.9.6.5 The lrint and llrint functions （第 463 页）

**参阅**

| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| [nearbyint (C99)<br />nearbyintf (C99)<br />nearbyintl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/nearbyint) | 用当前舍入模式取整到整数 (函数)             |
| [fegetround (C99)<br />fesetround (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feround) | 获得或设置数字的舍入方向 (函数)             |
| **rint** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/rint)** |                                             |





### llrintf

原址：[https://zh.cppreference.com/w/c/numeric/math/rint](https://zh.cppreference.com/w/c/numeric/math/rint)

作用：使用当前舍入模式取整到整数，若结果有误则产生异常   (函数)

备注：
```c
// 在标头 <math.h> 定义
float rintf( float arg );// (1)(C99 起)
double rint( double arg );// (2)(C99 起)
long double rintl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define rint( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
long lrintf( float arg );// (5)(C99 起)
long lrint( double arg );// (6)(C99 起)
long lrintl( long double arg );// (7)(C99 起)
// 在标头 <tgmath.h> 定义
#define lrint( arg )// (8)(C99 起)
// 在标头 <math.h> 定义
long long llrintf( float arg );// (9)(C99 起)
long long llrint( double arg );// (10)(C99 起)
long long llrintl( long double arg );// (11)(C99 起)
// 在标头 <tgmath.h> 定义
#define llrint( arg )// (12)(C99 起)
```

1-3) 用[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，舍入浮点数实参 `arg` 为整数（以浮点数格式）。

5-7, 9-11) 用[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，舍入浮点数实参 `arg` 为整数。

4,8,12) 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `rintl`、`lrintl`、`llrintl`。否则若 `arg` 拥有整数或 `double` 类型，则调用 `rint`、`lrint`、`llrint`。否则分别调用 `rintf`、`lrintf`、`llrintf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则为 `arg` 按照[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)的最接近整数。

**错误处理**

​	报告 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `lrint` 或 `llrint` 的结果在返回类型的可表示范围外，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若 `arg` 为 ±∞，则返回未修改的实参
- 若 `arg` 为 ±0，则返回未修改的实参
- 若 `arg` 为 NaN，则返回 NaN

- 若 `arg` 为 ±∞，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值
- 若舍入结果在返回类型范围外，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值
- 若 `arg` 为 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值

**注解**

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lrint.html) `lrint` 或 `llrint` 引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的所有情况都是定义域错误。

​	如 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 所指定，`rint` 在舍入非整数有限值时可以（但不在非 IEEE 浮点数平台上要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	`rint` 和 [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint) 间仅有的区别是 [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint) 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数都是准确的整数，故 `rint` 自身决不上溢；然而在存储结果于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	若当前舍入模式为……

- [FE_DOWNWARD](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [floor](https://zh.cppreference.com/w/c/numeric/math/floor)。
- [FE_UPWARD](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [ceil](https://zh.cppreference.com/w/c/numeric/math/ceil)。
- [FE_TOWARDZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [trunc](https://zh.cppreference.com/w/c/numeric/math/trunc)。
- [FE_TONEAREST](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 在中点情况和 [round](https://zh.cppreference.com/w/c/numeric/math/round) 的区别是前者始终舍入到偶数，而非远离零。

**示例**

```c
#include <fenv.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
#pragma STDC FENV_ACCESS ON
    fesetround(FE_TONEAREST);
    printf("向临近舍入（半值舍入为偶数）:\n"
           "rint(+2.3) = %+.1f  ", rint(2.3));
    printf("rint(+2.5) = %+.1f  ", rint(2.5));
    printf("rint(+3.5) = %+.1f\n", rint(3.5));
    printf("rint(-2.3) = %+.1f  ", rint(-2.3));
    printf("rint(-2.5) = %+.1f  ", rint(-2.5));
    printf("rint(-3.5) = %+.1f\n", rint(-3.5));
 
    fesetround(FE_DOWNWARD);
    printf("向下舍入: \nrint(+2.3) = %+.1f  ", rint(2.3));
    printf("rint(+2.5) = %+.1f  ", rint(2.5));
    printf("rint(+3.5) = %+.1f\n", rint(3.5));
    printf("rint(-2.3) = %+.1f  ", rint(-2.3));
    printf("rint(-2.5) = %+.1f  ", rint(-2.5));
    printf("rint(-3.5) = %+.1f\n", rint(-3.5));
    printf("用 lrint 向下舍入: \nlrint(+2.3) = %ld  ", lrint(2.3));
    printf("lrint(+2.5) = %ld  ", lrint(2.5));
    printf("lrint(+3.5) = %ld\n", lrint(3.5));
    printf("lrint(-2.3) = %ld  ", lrint(-2.3));
    printf("lrint(-2.5) = %ld  ", lrint(-2.5));
    printf("lrint(-3.5) = %ld\n", lrint(-3.5));
 
    printf("lrint(-0.0) = %ld\n", lrint(-0.0));
    printf("lrint(-Inf) = %ld\n", lrint(-INFINITY)); // 引发 FE_INVALID
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("rint(1.1) = %.1f\n", rint(1.1));
    if (fetestexcept(FE_INEXACT))
        puts("    FE_INEXACT was raised");
 
    feclearexcept(FE_ALL_EXCEPT);
    printf("lrint(LONG_MIN-2048.0) = %ld\n", lrint(LONG_MIN-2048.0));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID was raised");
}
```

​	可能的输出：

```txt
向临近舍入（半值舍入为偶数）:
rint(+2.3) = +2.0  rint(+2.5) = +2.0  rint(+3.5) = +4.0
rint(-2.3) = -2.0  rint(-2.5) = -2.0  rint(-3.5) = -4.0
向下舍入: 
rint(+2.3) = +2.0  rint(+2.5) = +2.0  rint(+3.5) = +3.0
rint(-2.3) = -3.0  rint(-2.5) = -3.0  rint(-3.5) = -4.0
用 lrint 向下舍入: 
lrint(+2.3) = 2  lrint(+2.5) = 2  lrint(+3.5) = 3
lrint(-2.3) = -3  lrint(-2.5) = -3  lrint(-3.5) = -4
lrint(-0.0) = 0
lrint(-Inf) = -9223372036854775808
rint(1.1) = 1.0
    FE_INEXACT was raised
lrint(LONG_MIN-2048.0) = -9223372036854775808
    FE_INVALID was raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.4 The rint functions （第 TBD 页）

  - 7.12.9.5 The lrint and llrint functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.4 The rint functions （第 TBD 页）

  - F.10.6.5 The lrint and llrint functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.4 The rint functions （第 184 页）

  - 7.12.9.5 The lrint and llrint functions （第 184 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.6.4 The rint functions （第 384 页）

  - F.10.6.5 The lrint and llrint functions （第 384 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.4 The rint functions （第 252 页）

  - 7.12.9.5 The lrint and llrint functions （第 252 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.4 The rint functions （第 527 页）

  - F.10.6.5 The lrint and llrint functions （第 527 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.4 The rint functions （第 232-233 页）

  - 7.12.9.5 The lrint and llrint functions （第 233 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.4 The rint functions （第 463 页）

  - F.9.6.5 The lrint and llrint functions （第 463 页）

**参阅**

| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| [nearbyint (C99)<br />nearbyintf (C99)<br />nearbyintl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/nearbyint) | 用当前舍入模式取整到整数 (函数)             |
| [fegetround (C99)<br />fesetround (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feround) | 获得或设置数字的舍入方向 (函数)             |
| **rint** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/rint)** |                                             |





### llrintl

原址：[https://zh.cppreference.com/w/c/numeric/math/rint](https://zh.cppreference.com/w/c/numeric/math/rint)

作用：使用当前舍入模式取整到整数，若结果有误则产生异常   (函数)

备注：
```c
// 在标头 <math.h> 定义
float rintf( float arg );// (1)(C99 起)
double rint( double arg );// (2)(C99 起)
long double rintl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define rint( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
long lrintf( float arg );// (5)(C99 起)
long lrint( double arg );// (6)(C99 起)
long lrintl( long double arg );// (7)(C99 起)
// 在标头 <tgmath.h> 定义
#define lrint( arg )// (8)(C99 起)
// 在标头 <math.h> 定义
long long llrintf( float arg );// (9)(C99 起)
long long llrint( double arg );// (10)(C99 起)
long long llrintl( long double arg );// (11)(C99 起)
// 在标头 <tgmath.h> 定义
#define llrint( arg )// (12)(C99 起)
```

1-3) 用[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，舍入浮点数实参 `arg` 为整数（以浮点数格式）。

5-7, 9-11) 用[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，舍入浮点数实参 `arg` 为整数。

4,8,12) 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `rintl`、`lrintl`、`llrintl`。否则若 `arg` 拥有整数或 `double` 类型，则调用 `rint`、`lrint`、`llrint`。否则分别调用 `rintf`、`lrintf`、`llrintf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则为 `arg` 按照[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)的最接近整数。

**错误处理**

​	报告 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `lrint` 或 `llrint` 的结果在返回类型的可表示范围外，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若 `arg` 为 ±∞，则返回未修改的实参
- 若 `arg` 为 ±0，则返回未修改的实参
- 若 `arg` 为 NaN，则返回 NaN

- 若 `arg` 为 ±∞，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值
- 若舍入结果在返回类型范围外，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值
- 若 `arg` 为 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值

**注解**

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lrint.html) `lrint` 或 `llrint` 引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的所有情况都是定义域错误。

​	如 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 所指定，`rint` 在舍入非整数有限值时可以（但不在非 IEEE 浮点数平台上要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	`rint` 和 [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint) 间仅有的区别是 [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint) 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数都是准确的整数，故 `rint` 自身决不上溢；然而在存储结果于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	若当前舍入模式为……

- [FE_DOWNWARD](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [floor](https://zh.cppreference.com/w/c/numeric/math/floor)。
- [FE_UPWARD](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [ceil](https://zh.cppreference.com/w/c/numeric/math/ceil)。
- [FE_TOWARDZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [trunc](https://zh.cppreference.com/w/c/numeric/math/trunc)。
- [FE_TONEAREST](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 在中点情况和 [round](https://zh.cppreference.com/w/c/numeric/math/round) 的区别是前者始终舍入到偶数，而非远离零。

**示例**

```c
#include <fenv.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
#pragma STDC FENV_ACCESS ON
    fesetround(FE_TONEAREST);
    printf("向临近舍入（半值舍入为偶数）:\n"
           "rint(+2.3) = %+.1f  ", rint(2.3));
    printf("rint(+2.5) = %+.1f  ", rint(2.5));
    printf("rint(+3.5) = %+.1f\n", rint(3.5));
    printf("rint(-2.3) = %+.1f  ", rint(-2.3));
    printf("rint(-2.5) = %+.1f  ", rint(-2.5));
    printf("rint(-3.5) = %+.1f\n", rint(-3.5));
 
    fesetround(FE_DOWNWARD);
    printf("向下舍入: \nrint(+2.3) = %+.1f  ", rint(2.3));
    printf("rint(+2.5) = %+.1f  ", rint(2.5));
    printf("rint(+3.5) = %+.1f\n", rint(3.5));
    printf("rint(-2.3) = %+.1f  ", rint(-2.3));
    printf("rint(-2.5) = %+.1f  ", rint(-2.5));
    printf("rint(-3.5) = %+.1f\n", rint(-3.5));
    printf("用 lrint 向下舍入: \nlrint(+2.3) = %ld  ", lrint(2.3));
    printf("lrint(+2.5) = %ld  ", lrint(2.5));
    printf("lrint(+3.5) = %ld\n", lrint(3.5));
    printf("lrint(-2.3) = %ld  ", lrint(-2.3));
    printf("lrint(-2.5) = %ld  ", lrint(-2.5));
    printf("lrint(-3.5) = %ld\n", lrint(-3.5));
 
    printf("lrint(-0.0) = %ld\n", lrint(-0.0));
    printf("lrint(-Inf) = %ld\n", lrint(-INFINITY)); // 引发 FE_INVALID
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("rint(1.1) = %.1f\n", rint(1.1));
    if (fetestexcept(FE_INEXACT))
        puts("    FE_INEXACT was raised");
 
    feclearexcept(FE_ALL_EXCEPT);
    printf("lrint(LONG_MIN-2048.0) = %ld\n", lrint(LONG_MIN-2048.0));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID was raised");
}
```

​	可能的输出：

```txt
向临近舍入（半值舍入为偶数）:
rint(+2.3) = +2.0  rint(+2.5) = +2.0  rint(+3.5) = +4.0
rint(-2.3) = -2.0  rint(-2.5) = -2.0  rint(-3.5) = -4.0
向下舍入: 
rint(+2.3) = +2.0  rint(+2.5) = +2.0  rint(+3.5) = +3.0
rint(-2.3) = -3.0  rint(-2.5) = -3.0  rint(-3.5) = -4.0
用 lrint 向下舍入: 
lrint(+2.3) = 2  lrint(+2.5) = 2  lrint(+3.5) = 3
lrint(-2.3) = -3  lrint(-2.5) = -3  lrint(-3.5) = -4
lrint(-0.0) = 0
lrint(-Inf) = -9223372036854775808
rint(1.1) = 1.0
    FE_INEXACT was raised
lrint(LONG_MIN-2048.0) = -9223372036854775808
    FE_INVALID was raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.4 The rint functions （第 TBD 页）

  - 7.12.9.5 The lrint and llrint functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.4 The rint functions （第 TBD 页）

  - F.10.6.5 The lrint and llrint functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.4 The rint functions （第 184 页）

  - 7.12.9.5 The lrint and llrint functions （第 184 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.6.4 The rint functions （第 384 页）

  - F.10.6.5 The lrint and llrint functions （第 384 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.4 The rint functions （第 252 页）

  - 7.12.9.5 The lrint and llrint functions （第 252 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.4 The rint functions （第 527 页）

  - F.10.6.5 The lrint and llrint functions （第 527 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.4 The rint functions （第 232-233 页）

  - 7.12.9.5 The lrint and llrint functions （第 233 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.4 The rint functions （第 463 页）

  - F.9.6.5 The lrint and llrint functions （第 463 页）

**参阅**

| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| [nearbyint (C99)<br />nearbyintf (C99)<br />nearbyintl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/nearbyint) | 用当前舍入模式取整到整数 (函数)             |
| [fegetround (C99)<br />fesetround (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feround) | 获得或设置数字的舍入方向 (函数)             |
| **rint** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/rint)** |                                             |





### llround

原址：[https://zh.cppreference.com/w/c/numeric/math/round](https://zh.cppreference.com/w/c/numeric/math/round)

作用：取整到最接近的整数，在相邻整数正中间时取远离零的数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       roundf( float arg );// (1)(C99 起)
double      round( double arg );// (2)(C99 起)
long double roundl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define round( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
long      lroundf( float arg );// (5)(C99 起)
long      lround( double arg );// (6)(C99 起)
long      lroundl( long double arg );// (7)(C99 起)
// 在标头 <tgmath.h> 定义
#define lround( arg )// (8)(C99 起)
// 在标头 <math.h> 定义
long long llroundf( float arg );// (9)(C99 起)
long long llround( double arg );// (10)(C99 起)
long long llroundl( long double arg );// (11)(C99 起)
// 在标头 <tgmath.h> 定义
#define llround( arg )// (12)(C99 起)
```

1-3) 计算与 `arg` 最邻近的整数（以浮点数格式），中点情况取远离零者，无关乎当前舍入模式。

5-7, 9-11) 计算与 `arg` 最邻近的整数（以整数格式），中点情况取远离零者，无关乎当前舍入模式。

4,8,12) 泛型宏：若 `arg` 拥有 `long double` 类型，则分别调用 `roundl`、`lroundl`、`llroundl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则分别调用 `round`、`lround`、`llround`。否则分别调用 `roundf`、`lroundf`、`llroundf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则与返回 `arg` 的最邻近整数，中点情况取远离零者，

返回值

![math-round away zero.svg](https://upload.cppreference.com/mwiki/images/7/7c/math-round_away_zero.svg)

实参

​	若出现定义域错误，则返回实现定义值。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `lround` 或 `llround` 的结果在返回类型的可表示范围外，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），

  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则返回未修改的该值。
  - 若 `arg` 为 ±0，则返回未修改的该值。
  - 若 `arg` 为 NaN，则返回 NaN。
  - 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若舍入结果在返回类型的范围外，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若 `arg` 为 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。

**注解**

​	`round` 在舍入非整数有限值时，可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数均为准确的整数，故 `round` 自身决不上溢；然而在存储于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lround.html) `lround` 或 `llround` 引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的所有情况都是定义域错误。

​	`round` 的 `double` 版本如同实现如下：

```c
#include <math.h>
double round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
```

**示例**

```c
#include <assert.h>
#include <fenv.h>
#include <float.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
double custom_round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
 
void test_custom_round()
{
    const double sample[] =
    {
        0.0, 2.3, 2.5 - DBL_EPSILON, 2.5, 2.5 + DBL_EPSILON, 2.7, INFINITY
    };
    for (size_t t = 0; t < sizeof sample / sizeof(double); ++t)
        assert(round(+sample[t]) == custom_round(+sample[t]) &&
               round(-sample[t]) == custom_round(-sample[t]));
}
 
int main(void)
{
    // round
    printf("round(+2.3) = %+.1f  ", round(2.3));
    printf("round(+2.5) = %+.1f  ", round(2.5));
    printf("round(+2.7) = %+.1f\n", round(2.7));
    printf("round(-2.3) = %+.1f  ", round(-2.3));
    printf("round(-2.5) = %+.1f  ", round(-2.5));
    printf("round(-2.7) = %+.1f\n", round(-2.7));
 
    printf("round(-0.0) = %+.1f\n", round(-0.0));
    printf("round(-Inf) = %+f\n",   round(-INFINITY));
 
    test_custom_round();
 
    // lround
    printf("lround(+2.3) = %+ld  ", lround(2.3));
    printf("lround(+2.5) = %+ld  ", lround(2.5));
    printf("lround(+2.7) = %+ld\n", lround(2.7));
    printf("lround(-2.3) = %+ld  ", lround(-2.3));
    printf("lround(-2.5) = %+ld  ", lround(-2.5));
    printf("lround(-2.7) = %+ld\n", lround(-2.7));
 
    printf("lround(-0.0) = %+ld\n", lround(-0.0));
    printf("lround(-Inf) = %+ld\n", lround(-INFINITY)); // 引发 FE_INVALID
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("lround(LONG_MAX+1.5) = %ld\n", lround(LONG_MAX + 1.5));
    if (fetestexcept(FE_INVALID))
        puts("    引发了 FE_INVALID");
}
```

​	可能的输出：

```txt
round(+2.3) = +2.0  round(+2.5) = +3.0  round(+2.7) = +3.0
round(-2.3) = -2.0  round(-2.5) = -3.0  round(-2.7) = -3.0
round(-0.0) = -0.0
round(-Inf) = -inf
lround(+2.3) = +2  lround(+2.5) = +3  lround(+2.7) = +3
lround(-2.3) = -2  lround(-2.5) = -3  lround(-2.7) = -3
lround(-0.0) = +0
lround(-Inf) = -9223372036854775808
lround(LONG_MAX+1.5) = -9223372036854775808
    引发了 FE_INVALID
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.6 The round functions （第 TBD 页）

  - 7.12.9.7 The lround and llround functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.6 The round functions （第 TBD 页）

  - F.10.6.7 The lround and llround functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.6 The round functions （第 184 页）

  - 7.12.9.7 The lround and llround functions （第 184-185 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.6.6 The round functions （第 384 页）

  - F.10.6.7 The lround and llround functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.6 The round functions （第 253 页）

  - 7.12.9.7 The lround and llround functions （第 253 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.6 The round functions （第 527 页）

  - F.10.6.7 The lround and llround functions （第 528 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.6 The round functions （第 233 页）

  - 7.12.9.7 The lround and llround functions （第 234 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.6 The round functions （第 464 页）

  - F.9.6.7 The lround and llround functions （第 464 页）

**参阅**

| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)           |
| ------------------------------------------------------------ | ------------------------------------------- |
| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)           |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| **round** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/round)** |                                             |





### llroundf

原址：[https://zh.cppreference.com/w/c/numeric/math/round](https://zh.cppreference.com/w/c/numeric/math/round)

作用：取整到最接近的整数，在相邻整数正中间时取远离零的数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       roundf( float arg );// (1)(C99 起)
double      round( double arg );// (2)(C99 起)
long double roundl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define round( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
long      lroundf( float arg );// (5)(C99 起)
long      lround( double arg );// (6)(C99 起)
long      lroundl( long double arg );// (7)(C99 起)
// 在标头 <tgmath.h> 定义
#define lround( arg )// (8)(C99 起)
// 在标头 <math.h> 定义
long long llroundf( float arg );// (9)(C99 起)
long long llround( double arg );// (10)(C99 起)
long long llroundl( long double arg );// (11)(C99 起)
// 在标头 <tgmath.h> 定义
#define llround( arg )// (12)(C99 起)
```

1-3) 计算与 `arg` 最邻近的整数（以浮点数格式），中点情况取远离零者，无关乎当前舍入模式。

5-7, 9-11) 计算与 `arg` 最邻近的整数（以整数格式），中点情况取远离零者，无关乎当前舍入模式。

4,8,12) 泛型宏：若 `arg` 拥有 `long double` 类型，则分别调用 `roundl`、`lroundl`、`llroundl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则分别调用 `round`、`lround`、`llround`。否则分别调用 `roundf`、`lroundf`、`llroundf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则与返回 `arg` 的最邻近整数，中点情况取远离零者，

返回值

![math-round away zero.svg](https://upload.cppreference.com/mwiki/images/7/7c/math-round_away_zero.svg)

实参

​	若出现定义域错误，则返回实现定义值。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `lround` 或 `llround` 的结果在返回类型的可表示范围外，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），

  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则返回未修改的该值。
  - 若 `arg` 为 ±0，则返回未修改的该值。
  - 若 `arg` 为 NaN，则返回 NaN。
  - 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若舍入结果在返回类型的范围外，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若 `arg` 为 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。

**注解**

​	`round` 在舍入非整数有限值时，可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数均为准确的整数，故 `round` 自身决不上溢；然而在存储于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lround.html) `lround` 或 `llround` 引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的所有情况都是定义域错误。

​	`round` 的 `double` 版本如同实现如下：

```c
#include <math.h>
double round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
```

**示例**

```c
#include <assert.h>
#include <fenv.h>
#include <float.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
double custom_round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
 
void test_custom_round()
{
    const double sample[] =
    {
        0.0, 2.3, 2.5 - DBL_EPSILON, 2.5, 2.5 + DBL_EPSILON, 2.7, INFINITY
    };
    for (size_t t = 0; t < sizeof sample / sizeof(double); ++t)
        assert(round(+sample[t]) == custom_round(+sample[t]) &&
               round(-sample[t]) == custom_round(-sample[t]));
}
 
int main(void)
{
    // round
    printf("round(+2.3) = %+.1f  ", round(2.3));
    printf("round(+2.5) = %+.1f  ", round(2.5));
    printf("round(+2.7) = %+.1f\n", round(2.7));
    printf("round(-2.3) = %+.1f  ", round(-2.3));
    printf("round(-2.5) = %+.1f  ", round(-2.5));
    printf("round(-2.7) = %+.1f\n", round(-2.7));
 
    printf("round(-0.0) = %+.1f\n", round(-0.0));
    printf("round(-Inf) = %+f\n",   round(-INFINITY));
 
    test_custom_round();
 
    // lround
    printf("lround(+2.3) = %+ld  ", lround(2.3));
    printf("lround(+2.5) = %+ld  ", lround(2.5));
    printf("lround(+2.7) = %+ld\n", lround(2.7));
    printf("lround(-2.3) = %+ld  ", lround(-2.3));
    printf("lround(-2.5) = %+ld  ", lround(-2.5));
    printf("lround(-2.7) = %+ld\n", lround(-2.7));
 
    printf("lround(-0.0) = %+ld\n", lround(-0.0));
    printf("lround(-Inf) = %+ld\n", lround(-INFINITY)); // 引发 FE_INVALID
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("lround(LONG_MAX+1.5) = %ld\n", lround(LONG_MAX + 1.5));
    if (fetestexcept(FE_INVALID))
        puts("    引发了 FE_INVALID");
}
```

​	可能的输出：

```txt
round(+2.3) = +2.0  round(+2.5) = +3.0  round(+2.7) = +3.0
round(-2.3) = -2.0  round(-2.5) = -3.0  round(-2.7) = -3.0
round(-0.0) = -0.0
round(-Inf) = -inf
lround(+2.3) = +2  lround(+2.5) = +3  lround(+2.7) = +3
lround(-2.3) = -2  lround(-2.5) = -3  lround(-2.7) = -3
lround(-0.0) = +0
lround(-Inf) = -9223372036854775808
lround(LONG_MAX+1.5) = -9223372036854775808
    引发了 FE_INVALID
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.6 The round functions （第 TBD 页）

  - 7.12.9.7 The lround and llround functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.6 The round functions （第 TBD 页）

  - F.10.6.7 The lround and llround functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.6 The round functions （第 184 页）

  - 7.12.9.7 The lround and llround functions （第 184-185 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.6.6 The round functions （第 384 页）

  - F.10.6.7 The lround and llround functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.6 The round functions （第 253 页）

  - 7.12.9.7 The lround and llround functions （第 253 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.6 The round functions （第 527 页）

  - F.10.6.7 The lround and llround functions （第 528 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.6 The round functions （第 233 页）

  - 7.12.9.7 The lround and llround functions （第 234 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.6 The round functions （第 464 页）

  - F.9.6.7 The lround and llround functions （第 464 页）

**参阅**

| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)           |
| ------------------------------------------------------------ | ------------------------------------------- |
| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)           |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| **round** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/round)** |                                             |





### llroundl

原址：[https://zh.cppreference.com/w/c/numeric/math/round](https://zh.cppreference.com/w/c/numeric/math/round)

作用：取整到最接近的整数，在相邻整数正中间时取远离零的数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       roundf( float arg );// (1)(C99 起)
double      round( double arg );// (2)(C99 起)
long double roundl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define round( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
long      lroundf( float arg );// (5)(C99 起)
long      lround( double arg );// (6)(C99 起)
long      lroundl( long double arg );// (7)(C99 起)
// 在标头 <tgmath.h> 定义
#define lround( arg )// (8)(C99 起)
// 在标头 <math.h> 定义
long long llroundf( float arg );// (9)(C99 起)
long long llround( double arg );// (10)(C99 起)
long long llroundl( long double arg );// (11)(C99 起)
// 在标头 <tgmath.h> 定义
#define llround( arg )// (12)(C99 起)
```

1-3) 计算与 `arg` 最邻近的整数（以浮点数格式），中点情况取远离零者，无关乎当前舍入模式。

5-7, 9-11) 计算与 `arg` 最邻近的整数（以整数格式），中点情况取远离零者，无关乎当前舍入模式。

4,8,12) 泛型宏：若 `arg` 拥有 `long double` 类型，则分别调用 `roundl`、`lroundl`、`llroundl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则分别调用 `round`、`lround`、`llround`。否则分别调用 `roundf`、`lroundf`、`llroundf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则与返回 `arg` 的最邻近整数，中点情况取远离零者，

返回值

![math-round away zero.svg](https://upload.cppreference.com/mwiki/images/7/7c/math-round_away_zero.svg)

实参

​	若出现定义域错误，则返回实现定义值。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `lround` 或 `llround` 的结果在返回类型的可表示范围外，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），

  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则返回未修改的该值。
  - 若 `arg` 为 ±0，则返回未修改的该值。
  - 若 `arg` 为 NaN，则返回 NaN。
  - 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若舍入结果在返回类型的范围外，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若 `arg` 为 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。

**注解**

​	`round` 在舍入非整数有限值时，可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数均为准确的整数，故 `round` 自身决不上溢；然而在存储于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lround.html) `lround` 或 `llround` 引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的所有情况都是定义域错误。

​	`round` 的 `double` 版本如同实现如下：

```c
#include <math.h>
double round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
```

**示例**

```c
#include <assert.h>
#include <fenv.h>
#include <float.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
double custom_round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
 
void test_custom_round()
{
    const double sample[] =
    {
        0.0, 2.3, 2.5 - DBL_EPSILON, 2.5, 2.5 + DBL_EPSILON, 2.7, INFINITY
    };
    for (size_t t = 0; t < sizeof sample / sizeof(double); ++t)
        assert(round(+sample[t]) == custom_round(+sample[t]) &&
               round(-sample[t]) == custom_round(-sample[t]));
}
 
int main(void)
{
    // round
    printf("round(+2.3) = %+.1f  ", round(2.3));
    printf("round(+2.5) = %+.1f  ", round(2.5));
    printf("round(+2.7) = %+.1f\n", round(2.7));
    printf("round(-2.3) = %+.1f  ", round(-2.3));
    printf("round(-2.5) = %+.1f  ", round(-2.5));
    printf("round(-2.7) = %+.1f\n", round(-2.7));
 
    printf("round(-0.0) = %+.1f\n", round(-0.0));
    printf("round(-Inf) = %+f\n",   round(-INFINITY));
 
    test_custom_round();
 
    // lround
    printf("lround(+2.3) = %+ld  ", lround(2.3));
    printf("lround(+2.5) = %+ld  ", lround(2.5));
    printf("lround(+2.7) = %+ld\n", lround(2.7));
    printf("lround(-2.3) = %+ld  ", lround(-2.3));
    printf("lround(-2.5) = %+ld  ", lround(-2.5));
    printf("lround(-2.7) = %+ld\n", lround(-2.7));
 
    printf("lround(-0.0) = %+ld\n", lround(-0.0));
    printf("lround(-Inf) = %+ld\n", lround(-INFINITY)); // 引发 FE_INVALID
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("lround(LONG_MAX+1.5) = %ld\n", lround(LONG_MAX + 1.5));
    if (fetestexcept(FE_INVALID))
        puts("    引发了 FE_INVALID");
}
```

​	可能的输出：

```txt
round(+2.3) = +2.0  round(+2.5) = +3.0  round(+2.7) = +3.0
round(-2.3) = -2.0  round(-2.5) = -3.0  round(-2.7) = -3.0
round(-0.0) = -0.0
round(-Inf) = -inf
lround(+2.3) = +2  lround(+2.5) = +3  lround(+2.7) = +3
lround(-2.3) = -2  lround(-2.5) = -3  lround(-2.7) = -3
lround(-0.0) = +0
lround(-Inf) = -9223372036854775808
lround(LONG_MAX+1.5) = -9223372036854775808
    引发了 FE_INVALID
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.6 The round functions （第 TBD 页）

  - 7.12.9.7 The lround and llround functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.6 The round functions （第 TBD 页）

  - F.10.6.7 The lround and llround functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.6 The round functions （第 184 页）

  - 7.12.9.7 The lround and llround functions （第 184-185 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.6.6 The round functions （第 384 页）

  - F.10.6.7 The lround and llround functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.6 The round functions （第 253 页）

  - 7.12.9.7 The lround and llround functions （第 253 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.6 The round functions （第 527 页）

  - F.10.6.7 The lround and llround functions （第 528 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.6 The round functions （第 233 页）

  - 7.12.9.7 The lround and llround functions （第 234 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.6 The round functions （第 464 页）

  - F.9.6.7 The lround and llround functions （第 464 页）

**参阅**

| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)           |
| ------------------------------------------------------------ | ------------------------------------------- |
| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)           |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| **round** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/round)** |                                             |





### log

原址：[https://zh.cppreference.com/w/c/numeric/math/log](https://zh.cppreference.com/w/c/numeric/math/log)

作用：计算自然对数（底为 e）（{\small \ln{x} }{\small \ln{x} }ln(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       logf( float arg );// (1)(C99 起)
double      log( double arg );// (2)
long double logl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define log( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的自然（底 *e*）对数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `logl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `log`。否则，调用 `logf`。若 `arg` 为复数或序数，则宏调用对应的复数函数（`[clogf](http://zh.cppreference.com/w/c/numeric/complex/clog)`、`[clog](http://zh.cppreference.com/w/c/numeric/complex/clog)`、`[clogl](http://zh.cppreference.com/w/c/numeric/complex/clog)`）。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的自然（底 *e*）对数（*ln(arg)* 或 *loge(arg)*）。

​	若出现定义域错误，则返回实现定义值（支持的平台上为 NaN）。

​	若出现极点错误，则返回 [-HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`-HUGE_VALF` 或 `-HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 小于零则出现定义域错误。

​	若 `arg` 为零则可能出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 -∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 1，则返回 +0。
- 若参数为负数，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 +∞，则返回 +∞。
- 若参数为 NaN，则返回 NaN。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("log(1) = %f\n", log(1));
    printf("125 的以 5 为底对数 = %f\n", log(125)/log(5));
    // 特殊值
    printf("log(1) = %f\n", log(1));
    printf("log(+Inf) = %f\n", log(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("log(0) = %f\n", log(0));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	输出：

```txt
log(1) = 0.000000
125 的以 5 为底对数 = 3.000000
log(1) = 0.000000
log(+Inf) = inf
log(0) = -inf
    errno == ERANGE: Numerical result out of range
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.7 The log functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.7 The log functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.7 The log functions （第 178-179 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.7 The log functions （第 380 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.7 The log functions （第 244-245 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.7 The log functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.7 The log functions （第 225 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.7 The log functions （第 459 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.4 The log function

**参阅**

| [log10 <br />log10f (C99)<br />log10l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log10) | 计算常用对数 （底为 *10*）（log10xlog10⁡x） (函数)            |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [log2 (C99)<br />log2f (C99)<br />log2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log2) | 计算底为 *2* 的对数（log2xlog2⁡x） (函数)                     |
| [log1p (C99)<br />log1pf (C99)<br />log1pl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log1p) | 计算给定数加 1 的自然对数（底为 *e*）（ln(1+x)ln⁡(1+x)） (函数) |
| [exp <br />expf (C99)<br />expl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp) | 计算 *e* 的给定次幂（exex） (函数)                           |
| [clog (C99)<br />clogf (C99)<br />clogl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/clog) | 计算复数的自然对数 (函数)                                    |
| **log** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/log)** |                                                              |





### log10

原址：[https://zh.cppreference.com/w/c/numeric/math/log10](https://zh.cppreference.com/w/c/numeric/math/log10)

作用：计算常用对数 （底为 10）（{\small \log_{10}{x} }{\small \log_{10}{x} }log10(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       log10f( float arg );// (1)(C99 起)
double      log10( double arg );// (2)
long double log10l( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define log10( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的常用（以 *10* 为底）对数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `log10l`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `log10`。否则调用 `log10f`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的常用（底 *10*）对数（*log10(arg)* 或 *lg(arg)*）。

​	若出现定义域错误，则返回实现定义值（支持的平台上为 NaN）。

​	若出现极点错误，则返回 [-HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`-HUGE_VALF` 或 `-HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 小于零则出现定义域错误。

​	若 `arg` 为零则可能出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 -∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 1，则返回 +0。
- 若参数为负数，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 +∞，则返回 +∞。
- 若参数为 NaN，则返回 NaN。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("log10(1000) = %f\n", log10(1000));
    printf("log10(0.001) = %f\n", log10(0.001));
    printf("125 的以 5 为底对数 = %f\n", log10(125) / log10(5));
    // 特殊值
    printf("log10(1) = %f\n", log10(1));
    printf("log10(+Inf) = %f\n", log10(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("log10(0) = %f\n", log10(0));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
log10(1000) = 3.000000
log10(0.001) = -3.000000
125 的以 5 为底对数 = 3.000000
log10(1) = 0.000000
log10(+Inf) = inf
log10(0) = -inf
    errno == ERANGE: Numerical result out of range
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.8 The log10 functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.8 The log10 functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.8 The log10 functions （第 179 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.8 The log10 functions （第 380 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.8 The log10 functions （第 245 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.8 The log10 functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.8 The log10 functions （第 225-226 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.8 The log10 functions （第 459 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.5 The log10 function

**参阅**

| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡x） (函数)                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [log2 (C99)<br />log2f (C99)<br />log2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log2) | 计算底为 *2* 的对数（log2xlog2⁡x） (函数)                     |
| [log1p (C99)<br />log1pf (C99)<br />log1pl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log1p) | 计算给定数加 1 的自然对数（底为 *e*）（ln(1+x)ln⁡(1+x)） (函数) |
| **log10** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/log10)** |                                                              |





### log10f

原址：[https://zh.cppreference.com/w/c/numeric/math/log10](https://zh.cppreference.com/w/c/numeric/math/log10)

作用：计算常用对数 （底为 10）（{\small \log_{10}{x} }{\small \log_{10}{x} }log10(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       log10f( float arg );// (1)(C99 起)
double      log10( double arg );// (2)
long double log10l( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define log10( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的常用（以 *10* 为底）对数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `log10l`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `log10`。否则调用 `log10f`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的常用（底 *10*）对数（*log10(arg)* 或 *lg(arg)*）。

​	若出现定义域错误，则返回实现定义值（支持的平台上为 NaN）。

​	若出现极点错误，则返回 [-HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`-HUGE_VALF` 或 `-HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 小于零则出现定义域错误。

​	若 `arg` 为零则可能出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 -∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 1，则返回 +0。
- 若参数为负数，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 +∞，则返回 +∞。
- 若参数为 NaN，则返回 NaN。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("log10(1000) = %f\n", log10(1000));
    printf("log10(0.001) = %f\n", log10(0.001));
    printf("125 的以 5 为底对数 = %f\n", log10(125) / log10(5));
    // 特殊值
    printf("log10(1) = %f\n", log10(1));
    printf("log10(+Inf) = %f\n", log10(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("log10(0) = %f\n", log10(0));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
log10(1000) = 3.000000
log10(0.001) = -3.000000
125 的以 5 为底对数 = 3.000000
log10(1) = 0.000000
log10(+Inf) = inf
log10(0) = -inf
    errno == ERANGE: Numerical result out of range
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.8 The log10 functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.8 The log10 functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.8 The log10 functions （第 179 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.8 The log10 functions （第 380 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.8 The log10 functions （第 245 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.8 The log10 functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.8 The log10 functions （第 225-226 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.8 The log10 functions （第 459 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.5 The log10 function

**参阅**

| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡x） (函数)                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [log2 (C99)<br />log2f (C99)<br />log2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log2) | 计算底为 *2* 的对数（log2xlog2⁡x） (函数)                     |
| [log1p (C99)<br />log1pf (C99)<br />log1pl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log1p) | 计算给定数加 1 的自然对数（底为 *e*）（ln(1+x)ln⁡(1+x)） (函数) |
| **log10** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/log10)** |                                                              |





### log10l

原址：[https://zh.cppreference.com/w/c/numeric/math/log10](https://zh.cppreference.com/w/c/numeric/math/log10)

作用：计算常用对数 （底为 10）（{\small \log_{10}{x} }{\small \log_{10}{x} }log10(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       log10f( float arg );// (1)(C99 起)
double      log10( double arg );// (2)
long double log10l( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define log10( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的常用（以 *10* 为底）对数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `log10l`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `log10`。否则调用 `log10f`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的常用（底 *10*）对数（*log10(arg)* 或 *lg(arg)*）。

​	若出现定义域错误，则返回实现定义值（支持的平台上为 NaN）。

​	若出现极点错误，则返回 [-HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`-HUGE_VALF` 或 `-HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 小于零则出现定义域错误。

​	若 `arg` 为零则可能出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 -∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 1，则返回 +0。
- 若参数为负数，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 +∞，则返回 +∞。
- 若参数为 NaN，则返回 NaN。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("log10(1000) = %f\n", log10(1000));
    printf("log10(0.001) = %f\n", log10(0.001));
    printf("125 的以 5 为底对数 = %f\n", log10(125) / log10(5));
    // 特殊值
    printf("log10(1) = %f\n", log10(1));
    printf("log10(+Inf) = %f\n", log10(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("log10(0) = %f\n", log10(0));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
log10(1000) = 3.000000
log10(0.001) = -3.000000
125 的以 5 为底对数 = 3.000000
log10(1) = 0.000000
log10(+Inf) = inf
log10(0) = -inf
    errno == ERANGE: Numerical result out of range
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.8 The log10 functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.8 The log10 functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.8 The log10 functions （第 179 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.8 The log10 functions （第 380 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.8 The log10 functions （第 245 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.8 The log10 functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.8 The log10 functions （第 225-226 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.8 The log10 functions （第 459 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.5 The log10 function

**参阅**

| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡x） (函数)                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [log2 (C99)<br />log2f (C99)<br />log2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log2) | 计算底为 *2* 的对数（log2xlog2⁡x） (函数)                     |
| [log1p (C99)<br />log1pf (C99)<br />log1pl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log1p) | 计算给定数加 1 的自然对数（底为 *e*）（ln(1+x)ln⁡(1+x)） (函数) |
| **log10** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/log10)** |                                                              |





### log1p

原址：[https://zh.cppreference.com/w/c/numeric/math/log1p](https://zh.cppreference.com/w/c/numeric/math/log1p)

作用：计算给定数加 1 的自然对数（底为 e）（{\small \ln{(1+x)} }{\small \ln{(1+x)} }ln(1+x)）  (函数)

备注：
```c
// 在标头 <math.h> 定义
float       log1pf( float arg );// (1)(C99 起)
double      log1p( double arg );// (2)(C99 起)
long double log1pl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define log1p( arg )// (4)(C99 起)
```

1-3) 计算 `1 + arg` 的自然（以 `e` 为底）对数。若 `arg` 接近零，则此函数比表达式 `[log](http://zh.cppreference.com/w/c/numeric/math/log)(1 +arg)` 更精确。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `log1pl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `log1p`。否则调用 `log1pf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误则返回 *ln(1 + arg)*。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现极点错误，则返回 [-HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`-HUGE_VALF` 或 `-HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 小于 *-1* 则出现定义域错误。

​	若 `arg` 为 *-1* 则可能出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 ±0，则返回不修改的参数。
- 若实参为 -1，则返回 -∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若实参小于 -1，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若实参为 +∞，则返回 +∞。
- 若实参为 NaN，则返回 NaN。

**注意**

​	函数 `expm1` 和 **log1p** 对于金融计算有用：例如在计算小的日利率时：*(1+x)n
-1* 能表示为 `[expm1](http://zh.cppreference.com/w/c/numeric/math/expm1)(n * log1p(x))`。这些函数亦简化书写精确的反双曲函数。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("log1p(0) = %f\n", log1p(0));
    printf("以 30/360 日历计算，复合日利率 1%%，则 $100 经 2 日获利 = %f\n",
           100*expm1(2*log1p(0.01/360)));
    printf("log(1+1e-16) = %g, 但 log1p(1e-16) = %g\n",
           log(1+1e-16), log1p(1e-16));
 
    // 特殊值
    printf("log1p(-0) = %f\n", log1p(-0.0));
    printf("log1p(+Inf) = %f\n", log1p(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("log1p(-1) = %f\n", log1p(-1));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
log1p(0) = 0.000000
以 30/360 日历计算，复合日利率 1%，则 $100 经 2 日获利 = 0.005556
log(1+1e-16) = 0, but log1p(1e-16) = 1e-16
log1p(-0) = -0.000000
log1p(+Inf) = Inf
log1p(-1) = -Inf
    errno == ERANGE: Result too large
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.9 The log1p functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.9 The log1p functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.9 The log1p functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.9 The log1p functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.9 The log1p functions （第 245 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.9 The log1p functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.9 The log1p functions （第 226 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.9 The log1p functions （第 459 页）

**参阅**

| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡x） (函数)         |
| ------------------------------------------------------------ | ------------------------------------------------- |
| [log10 <br />log10f (C99)<br />log10l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log10) | 计算常用对数 （底为 *10*）（log10xlog10⁡x） (函数) |
| [log2 (C99)<br />log2f (C99)<br />log2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log2) | 计算底为 *2* 的对数（log2xlog2⁡x） (函数)          |
| [expm1 (C99)<br />expm1f (C99)<br />expm1l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/expm1) | 计算 *e* 的给定次幂减一（ex−1ex−1） (函数)        |
| **log1p** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/log1p)** |                                                   |





### log1pf

原址：[https://zh.cppreference.com/w/c/numeric/math/log1p](https://zh.cppreference.com/w/c/numeric/math/log1p)

作用：计算给定数加 1 的自然对数（底为 e）（{\small \ln{(1+x)} }{\small \ln{(1+x)} }ln(1+x)）  (函数)

备注：
```c
// 在标头 <math.h> 定义
float       log1pf( float arg );// (1)(C99 起)
double      log1p( double arg );// (2)(C99 起)
long double log1pl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define log1p( arg )// (4)(C99 起)
```

1-3) 计算 `1 + arg` 的自然（以 `e` 为底）对数。若 `arg` 接近零，则此函数比表达式 `[log](http://zh.cppreference.com/w/c/numeric/math/log)(1 +arg)` 更精确。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `log1pl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `log1p`。否则调用 `log1pf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误则返回 *ln(1 + arg)*。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现极点错误，则返回 [-HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`-HUGE_VALF` 或 `-HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 小于 *-1* 则出现定义域错误。

​	若 `arg` 为 *-1* 则可能出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 ±0，则返回不修改的参数。
- 若实参为 -1，则返回 -∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若实参小于 -1，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若实参为 +∞，则返回 +∞。
- 若实参为 NaN，则返回 NaN。

**注意**

​	函数 `expm1` 和 **log1p** 对于金融计算有用：例如在计算小的日利率时：*(1+x)n
-1* 能表示为 `[expm1](http://zh.cppreference.com/w/c/numeric/math/expm1)(n * log1p(x))`。这些函数亦简化书写精确的反双曲函数。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("log1p(0) = %f\n", log1p(0));
    printf("以 30/360 日历计算，复合日利率 1%%，则 $100 经 2 日获利 = %f\n",
           100*expm1(2*log1p(0.01/360)));
    printf("log(1+1e-16) = %g, 但 log1p(1e-16) = %g\n",
           log(1+1e-16), log1p(1e-16));
 
    // 特殊值
    printf("log1p(-0) = %f\n", log1p(-0.0));
    printf("log1p(+Inf) = %f\n", log1p(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("log1p(-1) = %f\n", log1p(-1));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
log1p(0) = 0.000000
以 30/360 日历计算，复合日利率 1%，则 $100 经 2 日获利 = 0.005556
log(1+1e-16) = 0, but log1p(1e-16) = 1e-16
log1p(-0) = -0.000000
log1p(+Inf) = Inf
log1p(-1) = -Inf
    errno == ERANGE: Result too large
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.9 The log1p functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.9 The log1p functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.9 The log1p functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.9 The log1p functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.9 The log1p functions （第 245 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.9 The log1p functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.9 The log1p functions （第 226 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.9 The log1p functions （第 459 页）

**参阅**

| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡x） (函数)         |
| ------------------------------------------------------------ | ------------------------------------------------- |
| [log10 <br />log10f (C99)<br />log10l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log10) | 计算常用对数 （底为 *10*）（log10xlog10⁡x） (函数) |
| [log2 (C99)<br />log2f (C99)<br />log2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log2) | 计算底为 *2* 的对数（log2xlog2⁡x） (函数)          |
| [expm1 (C99)<br />expm1f (C99)<br />expm1l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/expm1) | 计算 *e* 的给定次幂减一（ex−1ex−1） (函数)        |
| **log1p** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/log1p)** |                                                   |





### log1pl

原址：[https://zh.cppreference.com/w/c/numeric/math/log1p](https://zh.cppreference.com/w/c/numeric/math/log1p)

作用：计算给定数加 1 的自然对数（底为 e）（{\small \ln{(1+x)} }{\small \ln{(1+x)} }ln(1+x)）  (函数)

备注：
```c
// 在标头 <math.h> 定义
float       log1pf( float arg );// (1)(C99 起)
double      log1p( double arg );// (2)(C99 起)
long double log1pl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define log1p( arg )// (4)(C99 起)
```

1-3) 计算 `1 + arg` 的自然（以 `e` 为底）对数。若 `arg` 接近零，则此函数比表达式 `[log](http://zh.cppreference.com/w/c/numeric/math/log)(1 +arg)` 更精确。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `log1pl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `log1p`。否则调用 `log1pf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误则返回 *ln(1 + arg)*。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现极点错误，则返回 [-HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`-HUGE_VALF` 或 `-HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 小于 *-1* 则出现定义域错误。

​	若 `arg` 为 *-1* 则可能出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 ±0，则返回不修改的参数。
- 若实参为 -1，则返回 -∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若实参小于 -1，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若实参为 +∞，则返回 +∞。
- 若实参为 NaN，则返回 NaN。

**注意**

​	函数 `expm1` 和 **log1p** 对于金融计算有用：例如在计算小的日利率时：*(1+x)n
-1* 能表示为 `[expm1](http://zh.cppreference.com/w/c/numeric/math/expm1)(n * log1p(x))`。这些函数亦简化书写精确的反双曲函数。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("log1p(0) = %f\n", log1p(0));
    printf("以 30/360 日历计算，复合日利率 1%%，则 $100 经 2 日获利 = %f\n",
           100*expm1(2*log1p(0.01/360)));
    printf("log(1+1e-16) = %g, 但 log1p(1e-16) = %g\n",
           log(1+1e-16), log1p(1e-16));
 
    // 特殊值
    printf("log1p(-0) = %f\n", log1p(-0.0));
    printf("log1p(+Inf) = %f\n", log1p(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("log1p(-1) = %f\n", log1p(-1));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
log1p(0) = 0.000000
以 30/360 日历计算，复合日利率 1%，则 $100 经 2 日获利 = 0.005556
log(1+1e-16) = 0, but log1p(1e-16) = 1e-16
log1p(-0) = -0.000000
log1p(+Inf) = Inf
log1p(-1) = -Inf
    errno == ERANGE: Result too large
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.9 The log1p functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.9 The log1p functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.9 The log1p functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.9 The log1p functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.9 The log1p functions （第 245 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.9 The log1p functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.9 The log1p functions （第 226 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.9 The log1p functions （第 459 页）

**参阅**

| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡x） (函数)         |
| ------------------------------------------------------------ | ------------------------------------------------- |
| [log10 <br />log10f (C99)<br />log10l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log10) | 计算常用对数 （底为 *10*）（log10xlog10⁡x） (函数) |
| [log2 (C99)<br />log2f (C99)<br />log2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log2) | 计算底为 *2* 的对数（log2xlog2⁡x） (函数)          |
| [expm1 (C99)<br />expm1f (C99)<br />expm1l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/expm1) | 计算 *e* 的给定次幂减一（ex−1ex−1） (函数)        |
| **log1p** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/log1p)** |                                                   |





### log2

原址：[https://zh.cppreference.com/w/c/numeric/math/log2](https://zh.cppreference.com/w/c/numeric/math/log2)

作用：计算底为 2 的对数（{\small \log_{2}{x} }{\small \log_{2}{x} }log2(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       log2f( float arg );// (1)(C99 起)
double      log2( double arg );// (2)(C99 起)
long double log2l( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define log2( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的底 *2* 对数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `log2l`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `log2`。否则调用 `log2f`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的底 *2* 对数（*log2(arg)* 或 *lb(arg)*）。

​	若出现定义域错误，则返回实现定义值（支持的平台上为 NaN）。

​	若出现极点错误，则返回 [-HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`-HUGE_VALF` 或 `-HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 小于零则出现定义域错误。

​	若 `arg` 为零则可能出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 -∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 1，则返回 +0。
- 若参数为负数，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 +∞，则返回 +∞。
- 若参数为 NaN，则返回 NaN。

**注意**

​	对于整数 `arg`，二进制对数能转译成输入中最高位 1 的零底下标。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <float.h>
#include <errno.h>
#include <fenv.h>
// #pragma STDC FENV_ACCESS ON
int main(void)
{
    printf("log2(65536) = %f\n", log2(65536));
    printf("log2(0.125) = %f\n", log2(0.125));
    printf("log2(0x020f) = %f (highest set bit is in position 9)\n", log2(0x020f));
    printf("base-5 logarithm of 125 = %f\n", log2(125)/log2(5));
    // 特殊值
    printf("log2(1) = %f\n", log2(1));
    printf("log2(+Inf) = %f\n", log2(INFINITY));
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("log2(0) = %f\n", log2(0));
    if(errno == ERANGE) perror("    errno == ERANGE");
    if(fetestexcept(FE_DIVBYZERO)) puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
log2(65536) = 16.000000
log2(0.125) = -3.000000
log2(0x020f) = 9.041659 (highest set bit is in position 9)
base-5 logarithm of 125 = 3.000000
log2(1) = 0.000000
log2(+Inf) = inf
log2(0) = -inf
    errno == ERANGE: Numerical result out of range
    FE_DIVBYZERO raised
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.10 The log2 functions （第 179 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.10 The log2 functions （第 381 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.10 The log2 functions （第 246 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.10 The log2 functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.10 The log2 functions （第 226 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.10 The log2 functions （第 459 页）

**参阅**

| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡x） (函数)                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [log10 <br />log10f (C99)<br />log10l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log10) | 计算常用对数 （底为 *10*）（log10xlog10⁡x） (函数)            |
| [log1p (C99)<br />log1pf (C99)<br />log1pl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log1p) | 计算给定数加 1 的自然对数（底为 *e*）（ln(1+x)ln⁡(1+x)） (函数) |
| [exp2 (C99)<br />exp2f (C99)<br />exp2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp2) | 计算 *2* 的给定次幂（2x2x） (函数)                           |
| **log2** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/log2)** |                                                              |





### log2f

原址：[https://zh.cppreference.com/w/c/numeric/math/log2](https://zh.cppreference.com/w/c/numeric/math/log2)

作用：计算底为 2 的对数（{\small \log_{2}{x} }{\small \log_{2}{x} }log2(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       log2f( float arg );// (1)(C99 起)
double      log2( double arg );// (2)(C99 起)
long double log2l( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define log2( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的底 *2* 对数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `log2l`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `log2`。否则调用 `log2f`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的底 *2* 对数（*log2(arg)* 或 *lb(arg)*）。

​	若出现定义域错误，则返回实现定义值（支持的平台上为 NaN）。

​	若出现极点错误，则返回 [-HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`-HUGE_VALF` 或 `-HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 小于零则出现定义域错误。

​	若 `arg` 为零则可能出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 -∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 1，则返回 +0。
- 若参数为负数，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 +∞，则返回 +∞。
- 若参数为 NaN，则返回 NaN。

**注意**

​	对于整数 `arg`，二进制对数能转译成输入中最高位 1 的零底下标。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <float.h>
#include <errno.h>
#include <fenv.h>
// #pragma STDC FENV_ACCESS ON
int main(void)
{
    printf("log2(65536) = %f\n", log2(65536));
    printf("log2(0.125) = %f\n", log2(0.125));
    printf("log2(0x020f) = %f (highest set bit is in position 9)\n", log2(0x020f));
    printf("base-5 logarithm of 125 = %f\n", log2(125)/log2(5));
    // 特殊值
    printf("log2(1) = %f\n", log2(1));
    printf("log2(+Inf) = %f\n", log2(INFINITY));
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("log2(0) = %f\n", log2(0));
    if(errno == ERANGE) perror("    errno == ERANGE");
    if(fetestexcept(FE_DIVBYZERO)) puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
log2(65536) = 16.000000
log2(0.125) = -3.000000
log2(0x020f) = 9.041659 (highest set bit is in position 9)
base-5 logarithm of 125 = 3.000000
log2(1) = 0.000000
log2(+Inf) = inf
log2(0) = -inf
    errno == ERANGE: Numerical result out of range
    FE_DIVBYZERO raised
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.10 The log2 functions （第 179 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.10 The log2 functions （第 381 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.10 The log2 functions （第 246 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.10 The log2 functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.10 The log2 functions （第 226 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.10 The log2 functions （第 459 页）

**参阅**

| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡x） (函数)                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [log10 <br />log10f (C99)<br />log10l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log10) | 计算常用对数 （底为 *10*）（log10xlog10⁡x） (函数)            |
| [log1p (C99)<br />log1pf (C99)<br />log1pl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log1p) | 计算给定数加 1 的自然对数（底为 *e*）（ln(1+x)ln⁡(1+x)） (函数) |
| [exp2 (C99)<br />exp2f (C99)<br />exp2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp2) | 计算 *2* 的给定次幂（2x2x） (函数)                           |
| **log2** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/log2)** |                                                              |





### log2l

原址：[https://zh.cppreference.com/w/c/numeric/math/log2](https://zh.cppreference.com/w/c/numeric/math/log2)

作用：计算底为 2 的对数（{\small \log_{2}{x} }{\small \log_{2}{x} }log2(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       log2f( float arg );// (1)(C99 起)
double      log2( double arg );// (2)(C99 起)
long double log2l( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define log2( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的底 *2* 对数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `log2l`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `log2`。否则调用 `log2f`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的底 *2* 对数（*log2(arg)* 或 *lb(arg)*）。

​	若出现定义域错误，则返回实现定义值（支持的平台上为 NaN）。

​	若出现极点错误，则返回 [-HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`-HUGE_VALF` 或 `-HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 小于零则出现定义域错误。

​	若 `arg` 为零则可能出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 -∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 1，则返回 +0。
- 若参数为负数，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 +∞，则返回 +∞。
- 若参数为 NaN，则返回 NaN。

**注意**

​	对于整数 `arg`，二进制对数能转译成输入中最高位 1 的零底下标。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <float.h>
#include <errno.h>
#include <fenv.h>
// #pragma STDC FENV_ACCESS ON
int main(void)
{
    printf("log2(65536) = %f\n", log2(65536));
    printf("log2(0.125) = %f\n", log2(0.125));
    printf("log2(0x020f) = %f (highest set bit is in position 9)\n", log2(0x020f));
    printf("base-5 logarithm of 125 = %f\n", log2(125)/log2(5));
    // 特殊值
    printf("log2(1) = %f\n", log2(1));
    printf("log2(+Inf) = %f\n", log2(INFINITY));
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("log2(0) = %f\n", log2(0));
    if(errno == ERANGE) perror("    errno == ERANGE");
    if(fetestexcept(FE_DIVBYZERO)) puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
log2(65536) = 16.000000
log2(0.125) = -3.000000
log2(0x020f) = 9.041659 (highest set bit is in position 9)
base-5 logarithm of 125 = 3.000000
log2(1) = 0.000000
log2(+Inf) = inf
log2(0) = -inf
    errno == ERANGE: Numerical result out of range
    FE_DIVBYZERO raised
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.10 The log2 functions （第 179 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.10 The log2 functions （第 381 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.10 The log2 functions （第 246 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.10 The log2 functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.10 The log2 functions （第 226 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.10 The log2 functions （第 459 页）

**参阅**

| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡x） (函数)                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [log10 <br />log10f (C99)<br />log10l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log10) | 计算常用对数 （底为 *10*）（log10xlog10⁡x） (函数)            |
| [log1p (C99)<br />log1pf (C99)<br />log1pl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log1p) | 计算给定数加 1 的自然对数（底为 *e*）（ln(1+x)ln⁡(1+x)） (函数) |
| [exp2 (C99)<br />exp2f (C99)<br />exp2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp2) | 计算 *2* 的给定次幂（2x2x） (函数)                           |
| **log2** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/log2)** |                                                              |





### logb

原址：[https://zh.cppreference.com/w/c/numeric/math/logb](https://zh.cppreference.com/w/c/numeric/math/logb)

作用：提取给定数的指数（结果为浮点数）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       logbf( float arg );// (1)(C99 起)
double      logb( double arg );// (2)(C99 起)
long double logbl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define logb( arg )// (4)(C99 起)
```

1-3) 从浮点数实参 `arg` 提取独立于基底的无偏指数，并将它作为浮点数返回。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `logbl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `logb`。否则调用 `logbf`。

​	正式而言，无偏指数是非零 `arg` 的 *logr|arg|* 的有符号整数部分（此函数作为浮点数返回），其中 `r` 是 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits)。若 `arg` 为非正规，则当做它如同已正规化。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回作为有符号浮点数的 `arg` 的无偏指数。

​	若出现定义域错误，则返回实现定义值。

​	若出现极点错误，则返回 [-HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`-HUGE_VALF` 或 `-HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 为零则可能出现定义域或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若 `arg` 为 ±0，则返回 -∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `arg` 为 ±∞，则返回 +∞。
- 若 `arg` 为 NaN，则返回 NaN。
- 所有其他情况下，结果是准确的（决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）且忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/logb.html)若 `arg` 为 ±0 则出现极点错误。

​	`logb` 所返回的指数值始终比 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 所返回的小 `1`，因为不同的正规化要求：对于 `logb` 返回的指数 `e`，*|arg\*r-e
|* 在 `1` 与 `r` 之间（典型地在 `1` 与 `2` 之间），但 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 返回的指数 `e`，*|arg\*2-e
|* 在 `0.5` 与 `1` 之间。

**示例**

​	比较不同的浮点数分解函数。

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
 
    i = logb(f);
    printf("logb()/logb() 计算 %f * %d^%d\n", f/scalbn(1.0, i), FLT_RADIX, i);
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("logb(0) = %f\n", logb(0));
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
给定数值 123.45 十六进制为 0x1.edccccccccccdp+6，
modf() 计算 123 + 0.45
frexp() 计算 0.964453 * 2^7
logb()/logb() 计算 1.928906 * 2^6
logb(0) = -Inf
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.11 The logb functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.11 The logb functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.11 The logb functions （第 179-180 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.11 The logb functions （第 381 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.11 The logb functions （第 246 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.11 The logb functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.11 The logb functions （第 227 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.11 The logb functions （第 459 页）

**参阅**

| [frexp <br />frexpf (C99)<br />frexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/frexp) | 将数拆分成有效数字和 *2* 的幂次 (函数)                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ilogb (C99)<br />ilogbf (C99)<br />ilogbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ilogb) | 提取给定数的指数（结果为整数） (函数)                        |
| [scalbn (C99)<br />scalbnf (C99)<br />scalbnl (C99)<br />scalbln (C99)<br />scalblnf (C99)<br />scalblnl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/scalbn) | 高效计算一个数乘 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 的幂 (函数) |
| **logb** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/logb)** |                                                              |





### logbf

原址：[https://zh.cppreference.com/w/c/numeric/math/logb](https://zh.cppreference.com/w/c/numeric/math/logb)

作用：提取给定数的指数（结果为浮点数）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       logbf( float arg );// (1)(C99 起)
double      logb( double arg );// (2)(C99 起)
long double logbl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define logb( arg )// (4)(C99 起)
```

1-3) 从浮点数实参 `arg` 提取独立于基底的无偏指数，并将它作为浮点数返回。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `logbl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `logb`。否则调用 `logbf`。

​	正式而言，无偏指数是非零 `arg` 的 *logr|arg|* 的有符号整数部分（此函数作为浮点数返回），其中 `r` 是 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits)。若 `arg` 为非正规，则当做它如同已正规化。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回作为有符号浮点数的 `arg` 的无偏指数。

​	若出现定义域错误，则返回实现定义值。

​	若出现极点错误，则返回 [-HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`-HUGE_VALF` 或 `-HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 为零则可能出现定义域或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若 `arg` 为 ±0，则返回 -∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `arg` 为 ±∞，则返回 +∞。
- 若 `arg` 为 NaN，则返回 NaN。
- 所有其他情况下，结果是准确的（决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）且忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/logb.html)若 `arg` 为 ±0 则出现极点错误。

​	`logb` 所返回的指数值始终比 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 所返回的小 `1`，因为不同的正规化要求：对于 `logb` 返回的指数 `e`，*|arg\*r-e
|* 在 `1` 与 `r` 之间（典型地在 `1` 与 `2` 之间），但 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 返回的指数 `e`，*|arg\*2-e
|* 在 `0.5` 与 `1` 之间。

**示例**

​	比较不同的浮点数分解函数。

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
 
    i = logb(f);
    printf("logb()/logb() 计算 %f * %d^%d\n", f/scalbn(1.0, i), FLT_RADIX, i);
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("logb(0) = %f\n", logb(0));
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
给定数值 123.45 十六进制为 0x1.edccccccccccdp+6，
modf() 计算 123 + 0.45
frexp() 计算 0.964453 * 2^7
logb()/logb() 计算 1.928906 * 2^6
logb(0) = -Inf
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.11 The logb functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.11 The logb functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.11 The logb functions （第 179-180 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.11 The logb functions （第 381 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.11 The logb functions （第 246 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.11 The logb functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.11 The logb functions （第 227 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.11 The logb functions （第 459 页）

**参阅**

| [frexp <br />frexpf (C99)<br />frexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/frexp) | 将数拆分成有效数字和 *2* 的幂次 (函数)                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ilogb (C99)<br />ilogbf (C99)<br />ilogbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ilogb) | 提取给定数的指数（结果为整数） (函数)                        |
| [scalbn (C99)<br />scalbnf (C99)<br />scalbnl (C99)<br />scalbln (C99)<br />scalblnf (C99)<br />scalblnl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/scalbn) | 高效计算一个数乘 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 的幂 (函数) |
| **logb** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/logb)** |                                                              |





### logbl

原址：[https://zh.cppreference.com/w/c/numeric/math/logb](https://zh.cppreference.com/w/c/numeric/math/logb)

作用：提取给定数的指数（结果为浮点数）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       logbf( float arg );// (1)(C99 起)
double      logb( double arg );// (2)(C99 起)
long double logbl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define logb( arg )// (4)(C99 起)
```

1-3) 从浮点数实参 `arg` 提取独立于基底的无偏指数，并将它作为浮点数返回。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `logbl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `logb`。否则调用 `logbf`。

​	正式而言，无偏指数是非零 `arg` 的 *logr|arg|* 的有符号整数部分（此函数作为浮点数返回），其中 `r` 是 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits)。若 `arg` 为非正规，则当做它如同已正规化。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回作为有符号浮点数的 `arg` 的无偏指数。

​	若出现定义域错误，则返回实现定义值。

​	若出现极点错误，则返回 [-HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`-HUGE_VALF` 或 `-HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 为零则可能出现定义域或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若 `arg` 为 ±0，则返回 -∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `arg` 为 ±∞，则返回 +∞。
- 若 `arg` 为 NaN，则返回 NaN。
- 所有其他情况下，结果是准确的（决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)）且忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/logb.html)若 `arg` 为 ±0 则出现极点错误。

​	`logb` 所返回的指数值始终比 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 所返回的小 `1`，因为不同的正规化要求：对于 `logb` 返回的指数 `e`，*|arg\*r-e
|* 在 `1` 与 `r` 之间（典型地在 `1` 与 `2` 之间），但 [frexp](https://zh.cppreference.com/w/c/numeric/math/frexp) 返回的指数 `e`，*|arg\*2-e
|* 在 `0.5` 与 `1` 之间。

**示例**

​	比较不同的浮点数分解函数。

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
 
    i = logb(f);
    printf("logb()/logb() 计算 %f * %d^%d\n", f/scalbn(1.0, i), FLT_RADIX, i);
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("logb(0) = %f\n", logb(0));
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
给定数值 123.45 十六进制为 0x1.edccccccccccdp+6，
modf() 计算 123 + 0.45
frexp() 计算 0.964453 * 2^7
logb()/logb() 计算 1.928906 * 2^6
logb(0) = -Inf
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.11 The logb functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.11 The logb functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.11 The logb functions （第 179-180 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.11 The logb functions （第 381 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.11 The logb functions （第 246 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.11 The logb functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.11 The logb functions （第 227 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.11 The logb functions （第 459 页）

**参阅**

| [frexp <br />frexpf (C99)<br />frexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/frexp) | 将数拆分成有效数字和 *2* 的幂次 (函数)                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ilogb (C99)<br />ilogbf (C99)<br />ilogbl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ilogb) | 提取给定数的指数（结果为整数） (函数)                        |
| [scalbn (C99)<br />scalbnf (C99)<br />scalbnl (C99)<br />scalbln (C99)<br />scalblnf (C99)<br />scalblnl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/scalbn) | 高效计算一个数乘 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 的幂 (函数) |
| **logb** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/logb)** |                                                              |





### logf

原址：[https://zh.cppreference.com/w/c/numeric/math/log](https://zh.cppreference.com/w/c/numeric/math/log)

作用：计算自然对数（底为 e）（{\small \ln{x} }{\small \ln{x} }ln(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       logf( float arg );// (1)(C99 起)
double      log( double arg );// (2)
long double logl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define log( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的自然（底 *e*）对数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `logl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `log`。否则，调用 `logf`。若 `arg` 为复数或序数，则宏调用对应的复数函数（`[clogf](http://zh.cppreference.com/w/c/numeric/complex/clog)`、`[clog](http://zh.cppreference.com/w/c/numeric/complex/clog)`、`[clogl](http://zh.cppreference.com/w/c/numeric/complex/clog)`）。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的自然（底 *e*）对数（*ln(arg)* 或 *loge(arg)*）。

​	若出现定义域错误，则返回实现定义值（支持的平台上为 NaN）。

​	若出现极点错误，则返回 [-HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`-HUGE_VALF` 或 `-HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 小于零则出现定义域错误。

​	若 `arg` 为零则可能出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 -∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 1，则返回 +0。
- 若参数为负数，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 +∞，则返回 +∞。
- 若参数为 NaN，则返回 NaN。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("log(1) = %f\n", log(1));
    printf("125 的以 5 为底对数 = %f\n", log(125)/log(5));
    // 特殊值
    printf("log(1) = %f\n", log(1));
    printf("log(+Inf) = %f\n", log(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("log(0) = %f\n", log(0));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	输出：

```txt
log(1) = 0.000000
125 的以 5 为底对数 = 3.000000
log(1) = 0.000000
log(+Inf) = inf
log(0) = -inf
    errno == ERANGE: Numerical result out of range
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.7 The log functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.7 The log functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.7 The log functions （第 178-179 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.7 The log functions （第 380 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.7 The log functions （第 244-245 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.7 The log functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.7 The log functions （第 225 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.7 The log functions （第 459 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.4 The log function

**参阅**

| [log10 <br />log10f (C99)<br />log10l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log10) | 计算常用对数 （底为 *10*）（log10xlog10⁡x） (函数)            |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [log2 (C99)<br />log2f (C99)<br />log2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log2) | 计算底为 *2* 的对数（log2xlog2⁡x） (函数)                     |
| [log1p (C99)<br />log1pf (C99)<br />log1pl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log1p) | 计算给定数加 1 的自然对数（底为 *e*）（ln(1+x)ln⁡(1+x)） (函数) |
| [exp <br />expf (C99)<br />expl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp) | 计算 *e* 的给定次幂（exex） (函数)                           |
| [clog (C99)<br />clogf (C99)<br />clogl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/clog) | 计算复数的自然对数 (函数)                                    |
| **log** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/log)** |                                                              |





### logl

原址：[https://zh.cppreference.com/w/c/numeric/math/log](https://zh.cppreference.com/w/c/numeric/math/log)

作用：计算自然对数（底为 e）（{\small \ln{x} }{\small \ln{x} }ln(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       logf( float arg );// (1)(C99 起)
double      log( double arg );// (2)
long double logl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define log( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的自然（底 *e*）对数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `logl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `log`。否则，调用 `logf`。若 `arg` 为复数或序数，则宏调用对应的复数函数（`[clogf](http://zh.cppreference.com/w/c/numeric/complex/clog)`、`[clog](http://zh.cppreference.com/w/c/numeric/complex/clog)`、`[clogl](http://zh.cppreference.com/w/c/numeric/complex/clog)`）。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的自然（底 *e*）对数（*ln(arg)* 或 *loge(arg)*）。

​	若出现定义域错误，则返回实现定义值（支持的平台上为 NaN）。

​	若出现极点错误，则返回 [-HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`-HUGE_VALF` 或 `-HUGE_VALL`。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 小于零则出现定义域错误。

​	若 `arg` 为零则可能出现极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 -∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 1，则返回 +0。
- 若参数为负数，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若参数为 +∞，则返回 +∞。
- 若参数为 NaN，则返回 NaN。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("log(1) = %f\n", log(1));
    printf("125 的以 5 为底对数 = %f\n", log(125)/log(5));
    // 特殊值
    printf("log(1) = %f\n", log(1));
    printf("log(+Inf) = %f\n", log(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("log(0) = %f\n", log(0));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	输出：

```txt
log(1) = 0.000000
125 的以 5 为底对数 = 3.000000
log(1) = 0.000000
log(+Inf) = inf
log(0) = -inf
    errno == ERANGE: Numerical result out of range
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.7 The log functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.3.7 The log functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.7 The log functions （第 178-179 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.3.7 The log functions （第 380 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.7 The log functions （第 244-245 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.3.7 The log functions （第 522 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.7 The log functions （第 225 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.3.7 The log functions （第 459 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.4 The log function

**参阅**

| [log10 <br />log10f (C99)<br />log10l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log10) | 计算常用对数 （底为 *10*）（log10xlog10⁡x） (函数)            |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [log2 (C99)<br />log2f (C99)<br />log2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log2) | 计算底为 *2* 的对数（log2xlog2⁡x） (函数)                     |
| [log1p (C99)<br />log1pf (C99)<br />log1pl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log1p) | 计算给定数加 1 的自然对数（底为 *e*）（ln(1+x)ln⁡(1+x)） (函数) |
| [exp <br />expf (C99)<br />expl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp) | 计算 *e* 的给定次幂（exex） (函数)                           |
| [clog (C99)<br />clogf (C99)<br />clogl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/clog) | 计算复数的自然对数 (函数)                                    |
| **log** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/log)** |                                                              |





### lrint

原址：[https://zh.cppreference.com/w/c/numeric/math/rint](https://zh.cppreference.com/w/c/numeric/math/rint)

作用：使用当前舍入模式取整到整数，若结果有误则产生异常   (函数)

备注：
```c
// 在标头 <math.h> 定义
float rintf( float arg );// (1)(C99 起)
double rint( double arg );// (2)(C99 起)
long double rintl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define rint( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
long lrintf( float arg );// (5)(C99 起)
long lrint( double arg );// (6)(C99 起)
long lrintl( long double arg );// (7)(C99 起)
// 在标头 <tgmath.h> 定义
#define lrint( arg )// (8)(C99 起)
// 在标头 <math.h> 定义
long long llrintf( float arg );// (9)(C99 起)
long long llrint( double arg );// (10)(C99 起)
long long llrintl( long double arg );// (11)(C99 起)
// 在标头 <tgmath.h> 定义
#define llrint( arg )// (12)(C99 起)
```

1-3) 用[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，舍入浮点数实参 `arg` 为整数（以浮点数格式）。

5-7, 9-11) 用[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，舍入浮点数实参 `arg` 为整数。

4,8,12) 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `rintl`、`lrintl`、`llrintl`。否则若 `arg` 拥有整数或 `double` 类型，则调用 `rint`、`lrint`、`llrint`。否则分别调用 `rintf`、`lrintf`、`llrintf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则为 `arg` 按照[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)的最接近整数。

**错误处理**

​	报告 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `lrint` 或 `llrint` 的结果在返回类型的可表示范围外，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若 `arg` 为 ±∞，则返回未修改的实参
- 若 `arg` 为 ±0，则返回未修改的实参
- 若 `arg` 为 NaN，则返回 NaN

- 若 `arg` 为 ±∞，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值
- 若舍入结果在返回类型范围外，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值
- 若 `arg` 为 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值

**注解**

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lrint.html) `lrint` 或 `llrint` 引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的所有情况都是定义域错误。

​	如 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 所指定，`rint` 在舍入非整数有限值时可以（但不在非 IEEE 浮点数平台上要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	`rint` 和 [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint) 间仅有的区别是 [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint) 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数都是准确的整数，故 `rint` 自身决不上溢；然而在存储结果于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	若当前舍入模式为……

- [FE_DOWNWARD](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [floor](https://zh.cppreference.com/w/c/numeric/math/floor)。
- [FE_UPWARD](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [ceil](https://zh.cppreference.com/w/c/numeric/math/ceil)。
- [FE_TOWARDZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [trunc](https://zh.cppreference.com/w/c/numeric/math/trunc)。
- [FE_TONEAREST](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 在中点情况和 [round](https://zh.cppreference.com/w/c/numeric/math/round) 的区别是前者始终舍入到偶数，而非远离零。

**示例**

```c
#include <fenv.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
#pragma STDC FENV_ACCESS ON
    fesetround(FE_TONEAREST);
    printf("向临近舍入（半值舍入为偶数）:\n"
           "rint(+2.3) = %+.1f  ", rint(2.3));
    printf("rint(+2.5) = %+.1f  ", rint(2.5));
    printf("rint(+3.5) = %+.1f\n", rint(3.5));
    printf("rint(-2.3) = %+.1f  ", rint(-2.3));
    printf("rint(-2.5) = %+.1f  ", rint(-2.5));
    printf("rint(-3.5) = %+.1f\n", rint(-3.5));
 
    fesetround(FE_DOWNWARD);
    printf("向下舍入: \nrint(+2.3) = %+.1f  ", rint(2.3));
    printf("rint(+2.5) = %+.1f  ", rint(2.5));
    printf("rint(+3.5) = %+.1f\n", rint(3.5));
    printf("rint(-2.3) = %+.1f  ", rint(-2.3));
    printf("rint(-2.5) = %+.1f  ", rint(-2.5));
    printf("rint(-3.5) = %+.1f\n", rint(-3.5));
    printf("用 lrint 向下舍入: \nlrint(+2.3) = %ld  ", lrint(2.3));
    printf("lrint(+2.5) = %ld  ", lrint(2.5));
    printf("lrint(+3.5) = %ld\n", lrint(3.5));
    printf("lrint(-2.3) = %ld  ", lrint(-2.3));
    printf("lrint(-2.5) = %ld  ", lrint(-2.5));
    printf("lrint(-3.5) = %ld\n", lrint(-3.5));
 
    printf("lrint(-0.0) = %ld\n", lrint(-0.0));
    printf("lrint(-Inf) = %ld\n", lrint(-INFINITY)); // 引发 FE_INVALID
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("rint(1.1) = %.1f\n", rint(1.1));
    if (fetestexcept(FE_INEXACT))
        puts("    FE_INEXACT was raised");
 
    feclearexcept(FE_ALL_EXCEPT);
    printf("lrint(LONG_MIN-2048.0) = %ld\n", lrint(LONG_MIN-2048.0));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID was raised");
}
```

​	可能的输出：

```txt
向临近舍入（半值舍入为偶数）:
rint(+2.3) = +2.0  rint(+2.5) = +2.0  rint(+3.5) = +4.0
rint(-2.3) = -2.0  rint(-2.5) = -2.0  rint(-3.5) = -4.0
向下舍入: 
rint(+2.3) = +2.0  rint(+2.5) = +2.0  rint(+3.5) = +3.0
rint(-2.3) = -3.0  rint(-2.5) = -3.0  rint(-3.5) = -4.0
用 lrint 向下舍入: 
lrint(+2.3) = 2  lrint(+2.5) = 2  lrint(+3.5) = 3
lrint(-2.3) = -3  lrint(-2.5) = -3  lrint(-3.5) = -4
lrint(-0.0) = 0
lrint(-Inf) = -9223372036854775808
rint(1.1) = 1.0
    FE_INEXACT was raised
lrint(LONG_MIN-2048.0) = -9223372036854775808
    FE_INVALID was raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.4 The rint functions （第 TBD 页）

  - 7.12.9.5 The lrint and llrint functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.4 The rint functions （第 TBD 页）

  - F.10.6.5 The lrint and llrint functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.4 The rint functions （第 184 页）

  - 7.12.9.5 The lrint and llrint functions （第 184 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.6.4 The rint functions （第 384 页）

  - F.10.6.5 The lrint and llrint functions （第 384 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.4 The rint functions （第 252 页）

  - 7.12.9.5 The lrint and llrint functions （第 252 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.4 The rint functions （第 527 页）

  - F.10.6.5 The lrint and llrint functions （第 527 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.4 The rint functions （第 232-233 页）

  - 7.12.9.5 The lrint and llrint functions （第 233 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.4 The rint functions （第 463 页）

  - F.9.6.5 The lrint and llrint functions （第 463 页）

**参阅**

| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| [nearbyint (C99)<br />nearbyintf (C99)<br />nearbyintl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/nearbyint) | 用当前舍入模式取整到整数 (函数)             |
| [fegetround (C99)<br />fesetround (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feround) | 获得或设置数字的舍入方向 (函数)             |
| **rint** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/rint)** |                                             |





### lrintf

原址：[https://zh.cppreference.com/w/c/numeric/math/rint](https://zh.cppreference.com/w/c/numeric/math/rint)

作用：使用当前舍入模式取整到整数，若结果有误则产生异常   (函数)

备注：
```c
// 在标头 <math.h> 定义
float rintf( float arg );// (1)(C99 起)
double rint( double arg );// (2)(C99 起)
long double rintl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define rint( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
long lrintf( float arg );// (5)(C99 起)
long lrint( double arg );// (6)(C99 起)
long lrintl( long double arg );// (7)(C99 起)
// 在标头 <tgmath.h> 定义
#define lrint( arg )// (8)(C99 起)
// 在标头 <math.h> 定义
long long llrintf( float arg );// (9)(C99 起)
long long llrint( double arg );// (10)(C99 起)
long long llrintl( long double arg );// (11)(C99 起)
// 在标头 <tgmath.h> 定义
#define llrint( arg )// (12)(C99 起)
```

1-3) 用[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，舍入浮点数实参 `arg` 为整数（以浮点数格式）。

5-7, 9-11) 用[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，舍入浮点数实参 `arg` 为整数。

4,8,12) 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `rintl`、`lrintl`、`llrintl`。否则若 `arg` 拥有整数或 `double` 类型，则调用 `rint`、`lrint`、`llrint`。否则分别调用 `rintf`、`lrintf`、`llrintf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则为 `arg` 按照[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)的最接近整数。

**错误处理**

​	报告 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `lrint` 或 `llrint` 的结果在返回类型的可表示范围外，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若 `arg` 为 ±∞，则返回未修改的实参
- 若 `arg` 为 ±0，则返回未修改的实参
- 若 `arg` 为 NaN，则返回 NaN

- 若 `arg` 为 ±∞，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值
- 若舍入结果在返回类型范围外，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值
- 若 `arg` 为 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值

**注解**

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lrint.html) `lrint` 或 `llrint` 引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的所有情况都是定义域错误。

​	如 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 所指定，`rint` 在舍入非整数有限值时可以（但不在非 IEEE 浮点数平台上要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	`rint` 和 [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint) 间仅有的区别是 [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint) 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数都是准确的整数，故 `rint` 自身决不上溢；然而在存储结果于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	若当前舍入模式为……

- [FE_DOWNWARD](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [floor](https://zh.cppreference.com/w/c/numeric/math/floor)。
- [FE_UPWARD](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [ceil](https://zh.cppreference.com/w/c/numeric/math/ceil)。
- [FE_TOWARDZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [trunc](https://zh.cppreference.com/w/c/numeric/math/trunc)。
- [FE_TONEAREST](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 在中点情况和 [round](https://zh.cppreference.com/w/c/numeric/math/round) 的区别是前者始终舍入到偶数，而非远离零。

**示例**

```c
#include <fenv.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
#pragma STDC FENV_ACCESS ON
    fesetround(FE_TONEAREST);
    printf("向临近舍入（半值舍入为偶数）:\n"
           "rint(+2.3) = %+.1f  ", rint(2.3));
    printf("rint(+2.5) = %+.1f  ", rint(2.5));
    printf("rint(+3.5) = %+.1f\n", rint(3.5));
    printf("rint(-2.3) = %+.1f  ", rint(-2.3));
    printf("rint(-2.5) = %+.1f  ", rint(-2.5));
    printf("rint(-3.5) = %+.1f\n", rint(-3.5));
 
    fesetround(FE_DOWNWARD);
    printf("向下舍入: \nrint(+2.3) = %+.1f  ", rint(2.3));
    printf("rint(+2.5) = %+.1f  ", rint(2.5));
    printf("rint(+3.5) = %+.1f\n", rint(3.5));
    printf("rint(-2.3) = %+.1f  ", rint(-2.3));
    printf("rint(-2.5) = %+.1f  ", rint(-2.5));
    printf("rint(-3.5) = %+.1f\n", rint(-3.5));
    printf("用 lrint 向下舍入: \nlrint(+2.3) = %ld  ", lrint(2.3));
    printf("lrint(+2.5) = %ld  ", lrint(2.5));
    printf("lrint(+3.5) = %ld\n", lrint(3.5));
    printf("lrint(-2.3) = %ld  ", lrint(-2.3));
    printf("lrint(-2.5) = %ld  ", lrint(-2.5));
    printf("lrint(-3.5) = %ld\n", lrint(-3.5));
 
    printf("lrint(-0.0) = %ld\n", lrint(-0.0));
    printf("lrint(-Inf) = %ld\n", lrint(-INFINITY)); // 引发 FE_INVALID
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("rint(1.1) = %.1f\n", rint(1.1));
    if (fetestexcept(FE_INEXACT))
        puts("    FE_INEXACT was raised");
 
    feclearexcept(FE_ALL_EXCEPT);
    printf("lrint(LONG_MIN-2048.0) = %ld\n", lrint(LONG_MIN-2048.0));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID was raised");
}
```

​	可能的输出：

```txt
向临近舍入（半值舍入为偶数）:
rint(+2.3) = +2.0  rint(+2.5) = +2.0  rint(+3.5) = +4.0
rint(-2.3) = -2.0  rint(-2.5) = -2.0  rint(-3.5) = -4.0
向下舍入: 
rint(+2.3) = +2.0  rint(+2.5) = +2.0  rint(+3.5) = +3.0
rint(-2.3) = -3.0  rint(-2.5) = -3.0  rint(-3.5) = -4.0
用 lrint 向下舍入: 
lrint(+2.3) = 2  lrint(+2.5) = 2  lrint(+3.5) = 3
lrint(-2.3) = -3  lrint(-2.5) = -3  lrint(-3.5) = -4
lrint(-0.0) = 0
lrint(-Inf) = -9223372036854775808
rint(1.1) = 1.0
    FE_INEXACT was raised
lrint(LONG_MIN-2048.0) = -9223372036854775808
    FE_INVALID was raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.4 The rint functions （第 TBD 页）

  - 7.12.9.5 The lrint and llrint functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.4 The rint functions （第 TBD 页）

  - F.10.6.5 The lrint and llrint functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.4 The rint functions （第 184 页）

  - 7.12.9.5 The lrint and llrint functions （第 184 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.6.4 The rint functions （第 384 页）

  - F.10.6.5 The lrint and llrint functions （第 384 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.4 The rint functions （第 252 页）

  - 7.12.9.5 The lrint and llrint functions （第 252 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.4 The rint functions （第 527 页）

  - F.10.6.5 The lrint and llrint functions （第 527 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.4 The rint functions （第 232-233 页）

  - 7.12.9.5 The lrint and llrint functions （第 233 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.4 The rint functions （第 463 页）

  - F.9.6.5 The lrint and llrint functions （第 463 页）

**参阅**

| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| [nearbyint (C99)<br />nearbyintf (C99)<br />nearbyintl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/nearbyint) | 用当前舍入模式取整到整数 (函数)             |
| [fegetround (C99)<br />fesetround (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feround) | 获得或设置数字的舍入方向 (函数)             |
| **rint** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/rint)** |                                             |





### lrintl

原址：[https://zh.cppreference.com/w/c/numeric/math/rint](https://zh.cppreference.com/w/c/numeric/math/rint)

作用：使用当前舍入模式取整到整数，若结果有误则产生异常   (函数)

备注：
```c
// 在标头 <math.h> 定义
float rintf( float arg );// (1)(C99 起)
double rint( double arg );// (2)(C99 起)
long double rintl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define rint( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
long lrintf( float arg );// (5)(C99 起)
long lrint( double arg );// (6)(C99 起)
long lrintl( long double arg );// (7)(C99 起)
// 在标头 <tgmath.h> 定义
#define lrint( arg )// (8)(C99 起)
// 在标头 <math.h> 定义
long long llrintf( float arg );// (9)(C99 起)
long long llrint( double arg );// (10)(C99 起)
long long llrintl( long double arg );// (11)(C99 起)
// 在标头 <tgmath.h> 定义
#define llrint( arg )// (12)(C99 起)
```

1-3) 用[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，舍入浮点数实参 `arg` 为整数（以浮点数格式）。

5-7, 9-11) 用[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，舍入浮点数实参 `arg` 为整数。

4,8,12) 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `rintl`、`lrintl`、`llrintl`。否则若 `arg` 拥有整数或 `double` 类型，则调用 `rint`、`lrint`、`llrint`。否则分别调用 `rintf`、`lrintf`、`llrintf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则为 `arg` 按照[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)的最接近整数。

**错误处理**

​	报告 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `lrint` 或 `llrint` 的结果在返回类型的可表示范围外，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若 `arg` 为 ±∞，则返回未修改的实参
- 若 `arg` 为 ±0，则返回未修改的实参
- 若 `arg` 为 NaN，则返回 NaN

- 若 `arg` 为 ±∞，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值
- 若舍入结果在返回类型范围外，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值
- 若 `arg` 为 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值

**注解**

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lrint.html) `lrint` 或 `llrint` 引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的所有情况都是定义域错误。

​	如 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 所指定，`rint` 在舍入非整数有限值时可以（但不在非 IEEE 浮点数平台上要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	`rint` 和 [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint) 间仅有的区别是 [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint) 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数都是准确的整数，故 `rint` 自身决不上溢；然而在存储结果于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	若当前舍入模式为……

- [FE_DOWNWARD](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [floor](https://zh.cppreference.com/w/c/numeric/math/floor)。
- [FE_UPWARD](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [ceil](https://zh.cppreference.com/w/c/numeric/math/ceil)。
- [FE_TOWARDZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 等价于 [trunc](https://zh.cppreference.com/w/c/numeric/math/trunc)。
- [FE_TONEAREST](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则 `rint` 在中点情况和 [round](https://zh.cppreference.com/w/c/numeric/math/round) 的区别是前者始终舍入到偶数，而非远离零。

**示例**

```c
#include <fenv.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
#pragma STDC FENV_ACCESS ON
    fesetround(FE_TONEAREST);
    printf("向临近舍入（半值舍入为偶数）:\n"
           "rint(+2.3) = %+.1f  ", rint(2.3));
    printf("rint(+2.5) = %+.1f  ", rint(2.5));
    printf("rint(+3.5) = %+.1f\n", rint(3.5));
    printf("rint(-2.3) = %+.1f  ", rint(-2.3));
    printf("rint(-2.5) = %+.1f  ", rint(-2.5));
    printf("rint(-3.5) = %+.1f\n", rint(-3.5));
 
    fesetround(FE_DOWNWARD);
    printf("向下舍入: \nrint(+2.3) = %+.1f  ", rint(2.3));
    printf("rint(+2.5) = %+.1f  ", rint(2.5));
    printf("rint(+3.5) = %+.1f\n", rint(3.5));
    printf("rint(-2.3) = %+.1f  ", rint(-2.3));
    printf("rint(-2.5) = %+.1f  ", rint(-2.5));
    printf("rint(-3.5) = %+.1f\n", rint(-3.5));
    printf("用 lrint 向下舍入: \nlrint(+2.3) = %ld  ", lrint(2.3));
    printf("lrint(+2.5) = %ld  ", lrint(2.5));
    printf("lrint(+3.5) = %ld\n", lrint(3.5));
    printf("lrint(-2.3) = %ld  ", lrint(-2.3));
    printf("lrint(-2.5) = %ld  ", lrint(-2.5));
    printf("lrint(-3.5) = %ld\n", lrint(-3.5));
 
    printf("lrint(-0.0) = %ld\n", lrint(-0.0));
    printf("lrint(-Inf) = %ld\n", lrint(-INFINITY)); // 引发 FE_INVALID
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("rint(1.1) = %.1f\n", rint(1.1));
    if (fetestexcept(FE_INEXACT))
        puts("    FE_INEXACT was raised");
 
    feclearexcept(FE_ALL_EXCEPT);
    printf("lrint(LONG_MIN-2048.0) = %ld\n", lrint(LONG_MIN-2048.0));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID was raised");
}
```

​	可能的输出：

```txt
向临近舍入（半值舍入为偶数）:
rint(+2.3) = +2.0  rint(+2.5) = +2.0  rint(+3.5) = +4.0
rint(-2.3) = -2.0  rint(-2.5) = -2.0  rint(-3.5) = -4.0
向下舍入: 
rint(+2.3) = +2.0  rint(+2.5) = +2.0  rint(+3.5) = +3.0
rint(-2.3) = -3.0  rint(-2.5) = -3.0  rint(-3.5) = -4.0
用 lrint 向下舍入: 
lrint(+2.3) = 2  lrint(+2.5) = 2  lrint(+3.5) = 3
lrint(-2.3) = -3  lrint(-2.5) = -3  lrint(-3.5) = -4
lrint(-0.0) = 0
lrint(-Inf) = -9223372036854775808
rint(1.1) = 1.0
    FE_INEXACT was raised
lrint(LONG_MIN-2048.0) = -9223372036854775808
    FE_INVALID was raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.4 The rint functions （第 TBD 页）

  - 7.12.9.5 The lrint and llrint functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.4 The rint functions （第 TBD 页）

  - F.10.6.5 The lrint and llrint functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.4 The rint functions （第 184 页）

  - 7.12.9.5 The lrint and llrint functions （第 184 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.6.4 The rint functions （第 384 页）

  - F.10.6.5 The lrint and llrint functions （第 384 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.4 The rint functions （第 252 页）

  - 7.12.9.5 The lrint and llrint functions （第 252 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.4 The rint functions （第 527 页）

  - F.10.6.5 The lrint and llrint functions （第 527 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.4 The rint functions （第 232-233 页）

  - 7.12.9.5 The lrint and llrint functions （第 233 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.4 The rint functions （第 463 页）

  - F.9.6.5 The lrint and llrint functions （第 463 页）

**参阅**

| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| [nearbyint (C99)<br />nearbyintf (C99)<br />nearbyintl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/nearbyint) | 用当前舍入模式取整到整数 (函数)             |
| [fegetround (C99)<br />fesetround (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feround) | 获得或设置数字的舍入方向 (函数)             |
| **rint** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/rint)** |                                             |





### lround

原址：[https://zh.cppreference.com/w/c/numeric/math/round](https://zh.cppreference.com/w/c/numeric/math/round)

作用：取整到最接近的整数，在相邻整数正中间时取远离零的数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       roundf( float arg );// (1)(C99 起)
double      round( double arg );// (2)(C99 起)
long double roundl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define round( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
long      lroundf( float arg );// (5)(C99 起)
long      lround( double arg );// (6)(C99 起)
long      lroundl( long double arg );// (7)(C99 起)
// 在标头 <tgmath.h> 定义
#define lround( arg )// (8)(C99 起)
// 在标头 <math.h> 定义
long long llroundf( float arg );// (9)(C99 起)
long long llround( double arg );// (10)(C99 起)
long long llroundl( long double arg );// (11)(C99 起)
// 在标头 <tgmath.h> 定义
#define llround( arg )// (12)(C99 起)
```

1-3) 计算与 `arg` 最邻近的整数（以浮点数格式），中点情况取远离零者，无关乎当前舍入模式。

5-7, 9-11) 计算与 `arg` 最邻近的整数（以整数格式），中点情况取远离零者，无关乎当前舍入模式。

4,8,12) 泛型宏：若 `arg` 拥有 `long double` 类型，则分别调用 `roundl`、`lroundl`、`llroundl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则分别调用 `round`、`lround`、`llround`。否则分别调用 `roundf`、`lroundf`、`llroundf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则与返回 `arg` 的最邻近整数，中点情况取远离零者，

返回值

![math-round away zero.svg](https://upload.cppreference.com/mwiki/images/7/7c/math-round_away_zero.svg)

实参

​	若出现定义域错误，则返回实现定义值。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `lround` 或 `llround` 的结果在返回类型的可表示范围外，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），

  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则返回未修改的该值。
  - 若 `arg` 为 ±0，则返回未修改的该值。
  - 若 `arg` 为 NaN，则返回 NaN。
  - 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若舍入结果在返回类型的范围外，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若 `arg` 为 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。

**注解**

​	`round` 在舍入非整数有限值时，可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数均为准确的整数，故 `round` 自身决不上溢；然而在存储于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lround.html) `lround` 或 `llround` 引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的所有情况都是定义域错误。

​	`round` 的 `double` 版本如同实现如下：

```c
#include <math.h>
double round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
```

**示例**

```c
#include <assert.h>
#include <fenv.h>
#include <float.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
double custom_round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
 
void test_custom_round()
{
    const double sample[] =
    {
        0.0, 2.3, 2.5 - DBL_EPSILON, 2.5, 2.5 + DBL_EPSILON, 2.7, INFINITY
    };
    for (size_t t = 0; t < sizeof sample / sizeof(double); ++t)
        assert(round(+sample[t]) == custom_round(+sample[t]) &&
               round(-sample[t]) == custom_round(-sample[t]));
}
 
int main(void)
{
    // round
    printf("round(+2.3) = %+.1f  ", round(2.3));
    printf("round(+2.5) = %+.1f  ", round(2.5));
    printf("round(+2.7) = %+.1f\n", round(2.7));
    printf("round(-2.3) = %+.1f  ", round(-2.3));
    printf("round(-2.5) = %+.1f  ", round(-2.5));
    printf("round(-2.7) = %+.1f\n", round(-2.7));
 
    printf("round(-0.0) = %+.1f\n", round(-0.0));
    printf("round(-Inf) = %+f\n",   round(-INFINITY));
 
    test_custom_round();
 
    // lround
    printf("lround(+2.3) = %+ld  ", lround(2.3));
    printf("lround(+2.5) = %+ld  ", lround(2.5));
    printf("lround(+2.7) = %+ld\n", lround(2.7));
    printf("lround(-2.3) = %+ld  ", lround(-2.3));
    printf("lround(-2.5) = %+ld  ", lround(-2.5));
    printf("lround(-2.7) = %+ld\n", lround(-2.7));
 
    printf("lround(-0.0) = %+ld\n", lround(-0.0));
    printf("lround(-Inf) = %+ld\n", lround(-INFINITY)); // 引发 FE_INVALID
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("lround(LONG_MAX+1.5) = %ld\n", lround(LONG_MAX + 1.5));
    if (fetestexcept(FE_INVALID))
        puts("    引发了 FE_INVALID");
}
```

​	可能的输出：

```txt
round(+2.3) = +2.0  round(+2.5) = +3.0  round(+2.7) = +3.0
round(-2.3) = -2.0  round(-2.5) = -3.0  round(-2.7) = -3.0
round(-0.0) = -0.0
round(-Inf) = -inf
lround(+2.3) = +2  lround(+2.5) = +3  lround(+2.7) = +3
lround(-2.3) = -2  lround(-2.5) = -3  lround(-2.7) = -3
lround(-0.0) = +0
lround(-Inf) = -9223372036854775808
lround(LONG_MAX+1.5) = -9223372036854775808
    引发了 FE_INVALID
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.6 The round functions （第 TBD 页）

  - 7.12.9.7 The lround and llround functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.6 The round functions （第 TBD 页）

  - F.10.6.7 The lround and llround functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.6 The round functions （第 184 页）

  - 7.12.9.7 The lround and llround functions （第 184-185 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.6.6 The round functions （第 384 页）

  - F.10.6.7 The lround and llround functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.6 The round functions （第 253 页）

  - 7.12.9.7 The lround and llround functions （第 253 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.6 The round functions （第 527 页）

  - F.10.6.7 The lround and llround functions （第 528 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.6 The round functions （第 233 页）

  - 7.12.9.7 The lround and llround functions （第 234 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.6 The round functions （第 464 页）

  - F.9.6.7 The lround and llround functions （第 464 页）

**参阅**

| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)           |
| ------------------------------------------------------------ | ------------------------------------------- |
| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)           |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| **round** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/round)** |                                             |





### lroundf

原址：[https://zh.cppreference.com/w/c/numeric/math/round](https://zh.cppreference.com/w/c/numeric/math/round)

作用：取整到最接近的整数，在相邻整数正中间时取远离零的数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       roundf( float arg );// (1)(C99 起)
double      round( double arg );// (2)(C99 起)
long double roundl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define round( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
long      lroundf( float arg );// (5)(C99 起)
long      lround( double arg );// (6)(C99 起)
long      lroundl( long double arg );// (7)(C99 起)
// 在标头 <tgmath.h> 定义
#define lround( arg )// (8)(C99 起)
// 在标头 <math.h> 定义
long long llroundf( float arg );// (9)(C99 起)
long long llround( double arg );// (10)(C99 起)
long long llroundl( long double arg );// (11)(C99 起)
// 在标头 <tgmath.h> 定义
#define llround( arg )// (12)(C99 起)
```

1-3) 计算与 `arg` 最邻近的整数（以浮点数格式），中点情况取远离零者，无关乎当前舍入模式。

5-7, 9-11) 计算与 `arg` 最邻近的整数（以整数格式），中点情况取远离零者，无关乎当前舍入模式。

4,8,12) 泛型宏：若 `arg` 拥有 `long double` 类型，则分别调用 `roundl`、`lroundl`、`llroundl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则分别调用 `round`、`lround`、`llround`。否则分别调用 `roundf`、`lroundf`、`llroundf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则与返回 `arg` 的最邻近整数，中点情况取远离零者，

返回值

![math-round away zero.svg](https://upload.cppreference.com/mwiki/images/7/7c/math-round_away_zero.svg)

实参

​	若出现定义域错误，则返回实现定义值。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `lround` 或 `llround` 的结果在返回类型的可表示范围外，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），

  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则返回未修改的该值。
  - 若 `arg` 为 ±0，则返回未修改的该值。
  - 若 `arg` 为 NaN，则返回 NaN。
  - 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若舍入结果在返回类型的范围外，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若 `arg` 为 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。

**注解**

​	`round` 在舍入非整数有限值时，可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数均为准确的整数，故 `round` 自身决不上溢；然而在存储于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lround.html) `lround` 或 `llround` 引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的所有情况都是定义域错误。

​	`round` 的 `double` 版本如同实现如下：

```c
#include <math.h>
double round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
```

**示例**

```c
#include <assert.h>
#include <fenv.h>
#include <float.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
double custom_round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
 
void test_custom_round()
{
    const double sample[] =
    {
        0.0, 2.3, 2.5 - DBL_EPSILON, 2.5, 2.5 + DBL_EPSILON, 2.7, INFINITY
    };
    for (size_t t = 0; t < sizeof sample / sizeof(double); ++t)
        assert(round(+sample[t]) == custom_round(+sample[t]) &&
               round(-sample[t]) == custom_round(-sample[t]));
}
 
int main(void)
{
    // round
    printf("round(+2.3) = %+.1f  ", round(2.3));
    printf("round(+2.5) = %+.1f  ", round(2.5));
    printf("round(+2.7) = %+.1f\n", round(2.7));
    printf("round(-2.3) = %+.1f  ", round(-2.3));
    printf("round(-2.5) = %+.1f  ", round(-2.5));
    printf("round(-2.7) = %+.1f\n", round(-2.7));
 
    printf("round(-0.0) = %+.1f\n", round(-0.0));
    printf("round(-Inf) = %+f\n",   round(-INFINITY));
 
    test_custom_round();
 
    // lround
    printf("lround(+2.3) = %+ld  ", lround(2.3));
    printf("lround(+2.5) = %+ld  ", lround(2.5));
    printf("lround(+2.7) = %+ld\n", lround(2.7));
    printf("lround(-2.3) = %+ld  ", lround(-2.3));
    printf("lround(-2.5) = %+ld  ", lround(-2.5));
    printf("lround(-2.7) = %+ld\n", lround(-2.7));
 
    printf("lround(-0.0) = %+ld\n", lround(-0.0));
    printf("lround(-Inf) = %+ld\n", lround(-INFINITY)); // 引发 FE_INVALID
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("lround(LONG_MAX+1.5) = %ld\n", lround(LONG_MAX + 1.5));
    if (fetestexcept(FE_INVALID))
        puts("    引发了 FE_INVALID");
}
```

​	可能的输出：

```txt
round(+2.3) = +2.0  round(+2.5) = +3.0  round(+2.7) = +3.0
round(-2.3) = -2.0  round(-2.5) = -3.0  round(-2.7) = -3.0
round(-0.0) = -0.0
round(-Inf) = -inf
lround(+2.3) = +2  lround(+2.5) = +3  lround(+2.7) = +3
lround(-2.3) = -2  lround(-2.5) = -3  lround(-2.7) = -3
lround(-0.0) = +0
lround(-Inf) = -9223372036854775808
lround(LONG_MAX+1.5) = -9223372036854775808
    引发了 FE_INVALID
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.6 The round functions （第 TBD 页）

  - 7.12.9.7 The lround and llround functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.6 The round functions （第 TBD 页）

  - F.10.6.7 The lround and llround functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.6 The round functions （第 184 页）

  - 7.12.9.7 The lround and llround functions （第 184-185 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.6.6 The round functions （第 384 页）

  - F.10.6.7 The lround and llround functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.6 The round functions （第 253 页）

  - 7.12.9.7 The lround and llround functions （第 253 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.6 The round functions （第 527 页）

  - F.10.6.7 The lround and llround functions （第 528 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.6 The round functions （第 233 页）

  - 7.12.9.7 The lround and llround functions （第 234 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.6 The round functions （第 464 页）

  - F.9.6.7 The lround and llround functions （第 464 页）

**参阅**

| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)           |
| ------------------------------------------------------------ | ------------------------------------------- |
| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)           |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| **round** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/round)** |                                             |





### lroundl

原址：[https://zh.cppreference.com/w/c/numeric/math/round](https://zh.cppreference.com/w/c/numeric/math/round)

作用：取整到最接近的整数，在相邻整数正中间时取远离零的数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       roundf( float arg );// (1)(C99 起)
double      round( double arg );// (2)(C99 起)
long double roundl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define round( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
long      lroundf( float arg );// (5)(C99 起)
long      lround( double arg );// (6)(C99 起)
long      lroundl( long double arg );// (7)(C99 起)
// 在标头 <tgmath.h> 定义
#define lround( arg )// (8)(C99 起)
// 在标头 <math.h> 定义
long long llroundf( float arg );// (9)(C99 起)
long long llround( double arg );// (10)(C99 起)
long long llroundl( long double arg );// (11)(C99 起)
// 在标头 <tgmath.h> 定义
#define llround( arg )// (12)(C99 起)
```

1-3) 计算与 `arg` 最邻近的整数（以浮点数格式），中点情况取远离零者，无关乎当前舍入模式。

5-7, 9-11) 计算与 `arg` 最邻近的整数（以整数格式），中点情况取远离零者，无关乎当前舍入模式。

4,8,12) 泛型宏：若 `arg` 拥有 `long double` 类型，则分别调用 `roundl`、`lroundl`、`llroundl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则分别调用 `round`、`lround`、`llround`。否则分别调用 `roundf`、`lroundf`、`llroundf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则与返回 `arg` 的最邻近整数，中点情况取远离零者，

返回值

![math-round away zero.svg](https://upload.cppreference.com/mwiki/images/7/7c/math-round_away_zero.svg)

实参

​	若出现定义域错误，则返回实现定义值。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `lround` 或 `llround` 的结果在返回类型的可表示范围外，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），

  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则返回未修改的该值。
  - 若 `arg` 为 ±0，则返回未修改的该值。
  - 若 `arg` 为 NaN，则返回 NaN。
  - 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若舍入结果在返回类型的范围外，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若 `arg` 为 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。

**注解**

​	`round` 在舍入非整数有限值时，可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数均为准确的整数，故 `round` 自身决不上溢；然而在存储于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lround.html) `lround` 或 `llround` 引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的所有情况都是定义域错误。

​	`round` 的 `double` 版本如同实现如下：

```c
#include <math.h>
double round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
```

**示例**

```c
#include <assert.h>
#include <fenv.h>
#include <float.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
double custom_round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
 
void test_custom_round()
{
    const double sample[] =
    {
        0.0, 2.3, 2.5 - DBL_EPSILON, 2.5, 2.5 + DBL_EPSILON, 2.7, INFINITY
    };
    for (size_t t = 0; t < sizeof sample / sizeof(double); ++t)
        assert(round(+sample[t]) == custom_round(+sample[t]) &&
               round(-sample[t]) == custom_round(-sample[t]));
}
 
int main(void)
{
    // round
    printf("round(+2.3) = %+.1f  ", round(2.3));
    printf("round(+2.5) = %+.1f  ", round(2.5));
    printf("round(+2.7) = %+.1f\n", round(2.7));
    printf("round(-2.3) = %+.1f  ", round(-2.3));
    printf("round(-2.5) = %+.1f  ", round(-2.5));
    printf("round(-2.7) = %+.1f\n", round(-2.7));
 
    printf("round(-0.0) = %+.1f\n", round(-0.0));
    printf("round(-Inf) = %+f\n",   round(-INFINITY));
 
    test_custom_round();
 
    // lround
    printf("lround(+2.3) = %+ld  ", lround(2.3));
    printf("lround(+2.5) = %+ld  ", lround(2.5));
    printf("lround(+2.7) = %+ld\n", lround(2.7));
    printf("lround(-2.3) = %+ld  ", lround(-2.3));
    printf("lround(-2.5) = %+ld  ", lround(-2.5));
    printf("lround(-2.7) = %+ld\n", lround(-2.7));
 
    printf("lround(-0.0) = %+ld\n", lround(-0.0));
    printf("lround(-Inf) = %+ld\n", lround(-INFINITY)); // 引发 FE_INVALID
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("lround(LONG_MAX+1.5) = %ld\n", lround(LONG_MAX + 1.5));
    if (fetestexcept(FE_INVALID))
        puts("    引发了 FE_INVALID");
}
```

​	可能的输出：

```txt
round(+2.3) = +2.0  round(+2.5) = +3.0  round(+2.7) = +3.0
round(-2.3) = -2.0  round(-2.5) = -3.0  round(-2.7) = -3.0
round(-0.0) = -0.0
round(-Inf) = -inf
lround(+2.3) = +2  lround(+2.5) = +3  lround(+2.7) = +3
lround(-2.3) = -2  lround(-2.5) = -3  lround(-2.7) = -3
lround(-0.0) = +0
lround(-Inf) = -9223372036854775808
lround(LONG_MAX+1.5) = -9223372036854775808
    引发了 FE_INVALID
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.6 The round functions （第 TBD 页）

  - 7.12.9.7 The lround and llround functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.6 The round functions （第 TBD 页）

  - F.10.6.7 The lround and llround functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.6 The round functions （第 184 页）

  - 7.12.9.7 The lround and llround functions （第 184-185 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.6.6 The round functions （第 384 页）

  - F.10.6.7 The lround and llround functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.6 The round functions （第 253 页）

  - 7.12.9.7 The lround and llround functions （第 253 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.6 The round functions （第 527 页）

  - F.10.6.7 The lround and llround functions （第 528 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.6 The round functions （第 233 页）

  - 7.12.9.7 The lround and llround functions （第 234 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.6 The round functions （第 464 页）

  - F.9.6.7 The lround and llround functions （第 464 页）

**参阅**

| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)           |
| ------------------------------------------------------------ | ------------------------------------------- |
| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)           |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| **round** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/round)** |                                             |





### modf

原址：[https://zh.cppreference.com/w/c/numeric/math/modf](https://zh.cppreference.com/w/c/numeric/math/modf)

作用：把一个数拆分成整数和小数部分   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       modff( float arg, float* iptr );// (1)(C99 起)
double      modf( double arg, double* iptr );// (2)
long double modfl( long double arg, long double* iptr );// (3)(C99 起)
```

1-3) 分解给定的浮点数 `arg` 为整数和分数部分，每个都拥有与 `arg` 相同的类型和符号。（以浮点数格式）存储整数部分于 `iptr` 所指向的对象。

**参数**

| arg  | -    | 浮点数                                 |
| ---- | ---- | -------------------------------------- |
| iptr | -    | 指向要存储整数部分的目标的浮点数的指针 |

**返回值**

​	若不出现错误，则返回与 `arg` 相同符号的 `arg` 小数部分。将整数部分放进 `iptr` 所指向的值。

​	返回值和存储于 `*iptr` 的值的和给出 `arg`（允许舍入）。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

​	若实现支持 IEE 浮点数算术（IEC 60559），则

- 若 `arg` 为 ±0，则返回 ±0，并存储 ±0 于 `*iptr`。
- 若 `arg` 为 ±∞，则返回 ±0，并存储 ±∞ 于 `*iptr`。
- 若 `arg` 为 NaN，则返回 NaN，并存储 NaN 于 `*iptr`。
- 返回值是准确的，忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**注解**

​	此函数表现为如同实现如下：

```c
double modf(double value, double *iptr)
{
#pragma STDC FENV_ACCESS ON
    int save_round = fegetround();
    fesetround(FE_TOWARDZERO);
    *iptr = std::nearbyint(value);
    fesetround(save_round);
    return copysign(isinf(value) ? 0.0 : value - (*iptr), value);
}
```

**示例**

```c
#include <float.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    double f = 123.45;
    printf("给定数值 %.2f 十六进制为 %a，\n", f, f);
 
    double f3;
    double f2 = modf(f, &f3);
    printf("modf() 计算 %.2f + %.2f\n", f3, f2);
 
    int i;
    f2 = frexp(f, &i);
    printf("frexp() 计算 %f * 2^%d\n", f2, i);
 
    i = ilogb(f);
    printf("logb()/ilogb() 计算 %f * %d^%d\n", f / scalbn(1.0, i), FLT_RADIX, i);
 
    // 特殊值
    f2 = modf(-0.0, &f3);
    printf("modf(-0) 计算 %.2f + %.2f\n", f3, f2);
    f2 = modf(-INFINITY, &f3);
    printf("modf(-Inf) 计算 %.2f + %.2f\n", f3, f2);
}
```

​	可能的输出：

```txt
给定数值 123.45 十六进制为 0x1.edccccccccccdp+6，
modf() 计算 123.00 + 0.45
frexp() 计算 0.964453 * 2^7
logb()/ilogb() 计算 1.92891 * 2^6
modf(-0) 计算 -0.00 + -0.00
modf(-Inf) 计算 -INF + -0.00
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.12 The modf functions （第 TBD 页）

  - F.10.3.12 The modf functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.12 The modf functions （第 TBD 页）

  - F.10.3.12 The modf functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.12 The modf functions （第 246-247 页）

  - F.10.3.12 The modf functions （第 523 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.12 The modf functions （第 227 页）

  - F.9.3.12 The modf functions （第 460 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.6 The modf function

**参阅**

| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| **modf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/modf)** |                                             |





### modff

原址：[https://zh.cppreference.com/w/c/numeric/math/modf](https://zh.cppreference.com/w/c/numeric/math/modf)

作用：把一个数拆分成整数和小数部分   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       modff( float arg, float* iptr );// (1)(C99 起)
double      modf( double arg, double* iptr );// (2)
long double modfl( long double arg, long double* iptr );// (3)(C99 起)
```

1-3) 分解给定的浮点数 `arg` 为整数和分数部分，每个都拥有与 `arg` 相同的类型和符号。（以浮点数格式）存储整数部分于 `iptr` 所指向的对象。

**参数**

| arg  | -    | 浮点数                                 |
| ---- | ---- | -------------------------------------- |
| iptr | -    | 指向要存储整数部分的目标的浮点数的指针 |

**返回值**

​	若不出现错误，则返回与 `arg` 相同符号的 `arg` 小数部分。将整数部分放进 `iptr` 所指向的值。

​	返回值和存储于 `*iptr` 的值的和给出 `arg`（允许舍入）。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

​	若实现支持 IEE 浮点数算术（IEC 60559），则

- 若 `arg` 为 ±0，则返回 ±0，并存储 ±0 于 `*iptr`。
- 若 `arg` 为 ±∞，则返回 ±0，并存储 ±∞ 于 `*iptr`。
- 若 `arg` 为 NaN，则返回 NaN，并存储 NaN 于 `*iptr`。
- 返回值是准确的，忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**注解**

​	此函数表现为如同实现如下：

```c
double modf(double value, double *iptr)
{
#pragma STDC FENV_ACCESS ON
    int save_round = fegetround();
    fesetround(FE_TOWARDZERO);
    *iptr = std::nearbyint(value);
    fesetround(save_round);
    return copysign(isinf(value) ? 0.0 : value - (*iptr), value);
}
```

**示例**

```c
#include <float.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    double f = 123.45;
    printf("给定数值 %.2f 十六进制为 %a，\n", f, f);
 
    double f3;
    double f2 = modf(f, &f3);
    printf("modf() 计算 %.2f + %.2f\n", f3, f2);
 
    int i;
    f2 = frexp(f, &i);
    printf("frexp() 计算 %f * 2^%d\n", f2, i);
 
    i = ilogb(f);
    printf("logb()/ilogb() 计算 %f * %d^%d\n", f / scalbn(1.0, i), FLT_RADIX, i);
 
    // 特殊值
    f2 = modf(-0.0, &f3);
    printf("modf(-0) 计算 %.2f + %.2f\n", f3, f2);
    f2 = modf(-INFINITY, &f3);
    printf("modf(-Inf) 计算 %.2f + %.2f\n", f3, f2);
}
```

​	可能的输出：

```txt
给定数值 123.45 十六进制为 0x1.edccccccccccdp+6，
modf() 计算 123.00 + 0.45
frexp() 计算 0.964453 * 2^7
logb()/ilogb() 计算 1.92891 * 2^6
modf(-0) 计算 -0.00 + -0.00
modf(-Inf) 计算 -INF + -0.00
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.12 The modf functions （第 TBD 页）

  - F.10.3.12 The modf functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.12 The modf functions （第 TBD 页）

  - F.10.3.12 The modf functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.12 The modf functions （第 246-247 页）

  - F.10.3.12 The modf functions （第 523 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.12 The modf functions （第 227 页）

  - F.9.3.12 The modf functions （第 460 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.6 The modf function

**参阅**

| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| **modf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/modf)** |                                             |





### modfl

原址：[https://zh.cppreference.com/w/c/numeric/math/modf](https://zh.cppreference.com/w/c/numeric/math/modf)

作用：把一个数拆分成整数和小数部分   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       modff( float arg, float* iptr );// (1)(C99 起)
double      modf( double arg, double* iptr );// (2)
long double modfl( long double arg, long double* iptr );// (3)(C99 起)
```

1-3) 分解给定的浮点数 `arg` 为整数和分数部分，每个都拥有与 `arg` 相同的类型和符号。（以浮点数格式）存储整数部分于 `iptr` 所指向的对象。

**参数**

| arg  | -    | 浮点数                                 |
| ---- | ---- | -------------------------------------- |
| iptr | -    | 指向要存储整数部分的目标的浮点数的指针 |

**返回值**

​	若不出现错误，则返回与 `arg` 相同符号的 `arg` 小数部分。将整数部分放进 `iptr` 所指向的值。

​	返回值和存储于 `*iptr` 的值的和给出 `arg`（允许舍入）。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

​	若实现支持 IEE 浮点数算术（IEC 60559），则

- 若 `arg` 为 ±0，则返回 ±0，并存储 ±0 于 `*iptr`。
- 若 `arg` 为 ±∞，则返回 ±0，并存储 ±∞ 于 `*iptr`。
- 若 `arg` 为 NaN，则返回 NaN，并存储 NaN 于 `*iptr`。
- 返回值是准确的，忽略[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**注解**

​	此函数表现为如同实现如下：

```c
double modf(double value, double *iptr)
{
#pragma STDC FENV_ACCESS ON
    int save_round = fegetround();
    fesetround(FE_TOWARDZERO);
    *iptr = std::nearbyint(value);
    fesetround(save_round);
    return copysign(isinf(value) ? 0.0 : value - (*iptr), value);
}
```

**示例**

```c
#include <float.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    double f = 123.45;
    printf("给定数值 %.2f 十六进制为 %a，\n", f, f);
 
    double f3;
    double f2 = modf(f, &f3);
    printf("modf() 计算 %.2f + %.2f\n", f3, f2);
 
    int i;
    f2 = frexp(f, &i);
    printf("frexp() 计算 %f * 2^%d\n", f2, i);
 
    i = ilogb(f);
    printf("logb()/ilogb() 计算 %f * %d^%d\n", f / scalbn(1.0, i), FLT_RADIX, i);
 
    // 特殊值
    f2 = modf(-0.0, &f3);
    printf("modf(-0) 计算 %.2f + %.2f\n", f3, f2);
    f2 = modf(-INFINITY, &f3);
    printf("modf(-Inf) 计算 %.2f + %.2f\n", f3, f2);
}
```

​	可能的输出：

```txt
给定数值 123.45 十六进制为 0x1.edccccccccccdp+6，
modf() 计算 123.00 + 0.45
frexp() 计算 0.964453 * 2^7
logb()/ilogb() 计算 1.92891 * 2^6
modf(-0) 计算 -0.00 + -0.00
modf(-Inf) 计算 -INF + -0.00
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.6.12 The modf functions （第 TBD 页）

  - F.10.3.12 The modf functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.6.12 The modf functions （第 TBD 页）

  - F.10.3.12 The modf functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.6.12 The modf functions （第 246-247 页）

  - F.10.3.12 The modf functions （第 523 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.6.12 The modf functions （第 227 页）

  - F.9.3.12 The modf functions （第 460 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.4.6 The modf function

**参阅**

| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| ------------------------------------------------------------ | ------------------------------------------- |
| **modf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/modf)** |                                             |





### nan

原址：[https://zh.cppreference.com/w/c/numeric/math/nan](https://zh.cppreference.com/w/c/numeric/math/nan)

作用：返回 NaN（非数）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       nanf( const char* arg );// (1)(C99 起)
double      nan( const char* arg );// (2)(C99 起)
long double nanl( const char* arg );// (3)(C99 起)
_Decimal32  nand32( const char* arg );// (4)(C23 起)
_Decimal64  nand64( const char* arg );// (5)(C23 起)
_Decimal128 nand128( const char* arg );// (6)(C23 起)
```

​	转换实现定义的字符串 `arg` 为对应的安静 NaN 值，分别如同以下列方式调用 [strtod](https://zh.cppreference.com/w/c/string/byte/strtof)、[strtof](https://zh.cppreference.com/w/c/string/byte/strtof) 或 [strtold](https://zh.cppreference.com/w/c/string/byte/strtof)：

- 调用 `nan("n-字符序列")`，其中 *n-字符序列* 是数字、拉丁字母和下划线的序列，等价于调用 `*/\*strtoX\*/*("NAN(n-字符序列)", (char**)[NULL](http://zh.cppreference.com/w/c/types/NULL));`。
- 调用 `nan("")` 等价于调用 `*/\*strtoX\*/*("NAN()", (char**)[NULL](http://zh.cppreference.com/w/c/types/NULL));`。
- 调用 `nan("字符串")`，其中 `字符串` 既非 *n-字符序列* 亦非空字符串，等价于调用 `*/\*strtoX\*/*("NAN", (char**)[NULL](http://zh.cppreference.com/w/c/types/NULL));`。

1） 解析函数为 [strtof](https://zh.cppreference.com/w/c/string/byte/strtof)。

2） 解析函数为 [strtod](https://zh.cppreference.com/w/c/string/byte/strtof)。

3） 解析函数为 [strtold](https://zh.cppreference.com/w/c/string/byte/strtof)。

4） 解析函数为 strtod32。

5） 解析函数为 strtod64。

6） 解析函数为 strtod128。

​	当且仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明返回十进制浮点数的各函数。 (C23 起)

**参数**

| arg  | -    | 标识 NaN 内容的窄字符串 |
| ---- | ---- | ----------------------- |
|      |      |                         |

**返回值**

​	对应标识字符串 `arg` 的安静 NaN 值，或若实现不支持安静 NaN 则为零。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则它也支持安静 NaN。

**错误处理**

​	此函数不受制于任何指定于 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误条件。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <stdint.h>
#include <inttypes.h>
#include <string.h>
 
int main(void)
{
    double f1 = nan("1");
    uint64_t f1n; memcpy(&f1n, &f1, sizeof f1);
    printf("nan(\"1\")   = %f (%" PRIx64 ")\n", f1, f1n);
 
    double f2 = nan("2");
    uint64_t f2n; memcpy(&f2n, &f2, sizeof f2);
    printf("nan(\"2\")   = %f (%" PRIx64 ")\n", f2, f2n);
 
    double f3 = nan("0xF");
    uint64_t f3n; memcpy(&f3n, &f3, sizeof f3);
    printf("nan(\"0xF\") = %f (%" PRIx64 ")\n", f3, f3n);
}
```

​	可能的输出：

```txt
nan("1")   = nan (7ff8000000000001)
nan("2")   = nan (7ff8000000000002)
nan("0xF") = nan (7ff800000000000f)
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.11.2 The nan functions （第 186-187 页）

  - F.10.8.2 The nan functions （第 386 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.11.2 The nan functions （第 256 页）

  - F.10.8.2 The nan functions （第 529 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.11.2 The nan functions （第 237 页）

  - F.9.8.2 The fabs functions （第 465 页）

**参阅**

| [isnan (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isnan) | 检查给定数是否为 NaN (宏函数)          |
| ------------------------------------------------------------ | -------------------------------------- |
| [NAN (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/NAN) | 求值为 `float` 类型的安静 NaN (宏常量) |
| **nanf, nan, nanl** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/nan)** |                                        |





### nanf

原址：[https://zh.cppreference.com/w/c/numeric/math/nan](https://zh.cppreference.com/w/c/numeric/math/nan)

作用：返回 NaN（非数）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       nanf( const char* arg );// (1)(C99 起)
double      nan( const char* arg );// (2)(C99 起)
long double nanl( const char* arg );// (3)(C99 起)
_Decimal32  nand32( const char* arg );// (4)(C23 起)
_Decimal64  nand64( const char* arg );// (5)(C23 起)
_Decimal128 nand128( const char* arg );// (6)(C23 起)
```

​	转换实现定义的字符串 `arg` 为对应的安静 NaN 值，分别如同以下列方式调用 [strtod](https://zh.cppreference.com/w/c/string/byte/strtof)、[strtof](https://zh.cppreference.com/w/c/string/byte/strtof) 或 [strtold](https://zh.cppreference.com/w/c/string/byte/strtof)：

- 调用 `nan("n-字符序列")`，其中 *n-字符序列* 是数字、拉丁字母和下划线的序列，等价于调用 `*/\*strtoX\*/*("NAN(n-字符序列)", (char**)[NULL](http://zh.cppreference.com/w/c/types/NULL));`。
- 调用 `nan("")` 等价于调用 `*/\*strtoX\*/*("NAN()", (char**)[NULL](http://zh.cppreference.com/w/c/types/NULL));`。
- 调用 `nan("字符串")`，其中 `字符串` 既非 *n-字符序列* 亦非空字符串，等价于调用 `*/\*strtoX\*/*("NAN", (char**)[NULL](http://zh.cppreference.com/w/c/types/NULL));`。

1） 解析函数为 [strtof](https://zh.cppreference.com/w/c/string/byte/strtof)。

2） 解析函数为 [strtod](https://zh.cppreference.com/w/c/string/byte/strtof)。

3） 解析函数为 [strtold](https://zh.cppreference.com/w/c/string/byte/strtof)。

4） 解析函数为 strtod32。

5） 解析函数为 strtod64。

6） 解析函数为 strtod128。

​	当且仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明返回十进制浮点数的各函数。 (C23 起)

**参数**

| arg  | -    | 标识 NaN 内容的窄字符串 |
| ---- | ---- | ----------------------- |
|      |      |                         |

**返回值**

​	对应标识字符串 `arg` 的安静 NaN 值，或若实现不支持安静 NaN 则为零。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则它也支持安静 NaN。

**错误处理**

​	此函数不受制于任何指定于 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误条件。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <stdint.h>
#include <inttypes.h>
#include <string.h>
 
int main(void)
{
    double f1 = nan("1");
    uint64_t f1n; memcpy(&f1n, &f1, sizeof f1);
    printf("nan(\"1\")   = %f (%" PRIx64 ")\n", f1, f1n);
 
    double f2 = nan("2");
    uint64_t f2n; memcpy(&f2n, &f2, sizeof f2);
    printf("nan(\"2\")   = %f (%" PRIx64 ")\n", f2, f2n);
 
    double f3 = nan("0xF");
    uint64_t f3n; memcpy(&f3n, &f3, sizeof f3);
    printf("nan(\"0xF\") = %f (%" PRIx64 ")\n", f3, f3n);
}
```

​	可能的输出：

```txt
nan("1")   = nan (7ff8000000000001)
nan("2")   = nan (7ff8000000000002)
nan("0xF") = nan (7ff800000000000f)
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.11.2 The nan functions （第 186-187 页）

  - F.10.8.2 The nan functions （第 386 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.11.2 The nan functions （第 256 页）

  - F.10.8.2 The nan functions （第 529 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.11.2 The nan functions （第 237 页）

  - F.9.8.2 The fabs functions （第 465 页）

**参阅**

| [isnan (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isnan) | 检查给定数是否为 NaN (宏函数)          |
| ------------------------------------------------------------ | -------------------------------------- |
| [NAN (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/NAN) | 求值为 `float` 类型的安静 NaN (宏常量) |
| **nanf, nan, nanl** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/nan)** |                                        |





### nanl

原址：[https://zh.cppreference.com/w/c/numeric/math/nan](https://zh.cppreference.com/w/c/numeric/math/nan)

作用：返回 NaN（非数）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       nanf( const char* arg );// (1)(C99 起)
double      nan( const char* arg );// (2)(C99 起)
long double nanl( const char* arg );// (3)(C99 起)
_Decimal32  nand32( const char* arg );// (4)(C23 起)
_Decimal64  nand64( const char* arg );// (5)(C23 起)
_Decimal128 nand128( const char* arg );// (6)(C23 起)
```

​	转换实现定义的字符串 `arg` 为对应的安静 NaN 值，分别如同以下列方式调用 [strtod](https://zh.cppreference.com/w/c/string/byte/strtof)、[strtof](https://zh.cppreference.com/w/c/string/byte/strtof) 或 [strtold](https://zh.cppreference.com/w/c/string/byte/strtof)：

- 调用 `nan("n-字符序列")`，其中 *n-字符序列* 是数字、拉丁字母和下划线的序列，等价于调用 `*/\*strtoX\*/*("NAN(n-字符序列)", (char**)[NULL](http://zh.cppreference.com/w/c/types/NULL));`。
- 调用 `nan("")` 等价于调用 `*/\*strtoX\*/*("NAN()", (char**)[NULL](http://zh.cppreference.com/w/c/types/NULL));`。
- 调用 `nan("字符串")`，其中 `字符串` 既非 *n-字符序列* 亦非空字符串，等价于调用 `*/\*strtoX\*/*("NAN", (char**)[NULL](http://zh.cppreference.com/w/c/types/NULL));`。

1） 解析函数为 [strtof](https://zh.cppreference.com/w/c/string/byte/strtof)。

2） 解析函数为 [strtod](https://zh.cppreference.com/w/c/string/byte/strtof)。

3） 解析函数为 [strtold](https://zh.cppreference.com/w/c/string/byte/strtof)。

4） 解析函数为 strtod32。

5） 解析函数为 strtod64。

6） 解析函数为 strtod128。

​	当且仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明返回十进制浮点数的各函数。 (C23 起)

**参数**

| arg  | -    | 标识 NaN 内容的窄字符串 |
| ---- | ---- | ----------------------- |
|      |      |                         |

**返回值**

​	对应标识字符串 `arg` 的安静 NaN 值，或若实现不支持安静 NaN 则为零。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则它也支持安静 NaN。

**错误处理**

​	此函数不受制于任何指定于 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误条件。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <stdint.h>
#include <inttypes.h>
#include <string.h>
 
int main(void)
{
    double f1 = nan("1");
    uint64_t f1n; memcpy(&f1n, &f1, sizeof f1);
    printf("nan(\"1\")   = %f (%" PRIx64 ")\n", f1, f1n);
 
    double f2 = nan("2");
    uint64_t f2n; memcpy(&f2n, &f2, sizeof f2);
    printf("nan(\"2\")   = %f (%" PRIx64 ")\n", f2, f2n);
 
    double f3 = nan("0xF");
    uint64_t f3n; memcpy(&f3n, &f3, sizeof f3);
    printf("nan(\"0xF\") = %f (%" PRIx64 ")\n", f3, f3n);
}
```

​	可能的输出：

```txt
nan("1")   = nan (7ff8000000000001)
nan("2")   = nan (7ff8000000000002)
nan("0xF") = nan (7ff800000000000f)
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.11.2 The nan functions （第 186-187 页）

  - F.10.8.2 The nan functions （第 386 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.11.2 The nan functions （第 256 页）

  - F.10.8.2 The nan functions （第 529 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.11.2 The nan functions （第 237 页）

  - F.9.8.2 The fabs functions （第 465 页）

**参阅**

| [isnan (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/isnan) | 检查给定数是否为 NaN (宏函数)          |
| ------------------------------------------------------------ | -------------------------------------- |
| [NAN (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/NAN) | 求值为 `float` 类型的安静 NaN (宏常量) |
| **nanf, nan, nanl** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/nan)** |                                        |





### nearbyint

原址：[https://zh.cppreference.com/w/c/numeric/math/nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint)

作用：用当前舍入模式取整到整数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       nearbyintf( float arg );// (1)(C99 起)
double      nearbyint( double arg );// (2)(C99 起)
long double nearbyintl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define nearbyint( arg )// (4)(C99 起)
```

1-3) 以[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，舍入浮点数实参 `arg` 到浮点数格式的整数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `nearbyintl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `nearbyint`。否则调用 `nearbyintf`。

**参数**值

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	返回 `arg` 按照[当前舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)的最接近整数。

**错误处理**

​	此函数不受制于任何指定于 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `arg` 为 ±∞，则返回不修改的参数
- 若 `arg` 为 ±0，则返回不修改的参数
- 若 `arg` 为 NaN，则返回 NaN

**展开**

​	`nearbyint` 和 [rint](https://zh.cppreference.com/w/c/numeric/math/rint) 之间仅有的区别是 `nearbyint` 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数都是整数，故 `nearbyint` 自身决不溢出；然而存储结果于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	若当前舍入模式为 [FE_TONEAREST](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，则此函数在中点情况向偶数舍入（同 [rint](https://zh.cppreference.com/w/c/numeric/math/rint)，但不同于 [round](https://zh.cppreference.com/w/c/numeric/math/round)）。

**示例**

```c
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
// #pragma STDC FENV_ACCESS ON
    fesetround(FE_TONEAREST);
    printf("舍入到临近:\nnearbyint(+2.3) = %+.1f  ", nearbyint(2.3));
    printf("nearbyint(+2.5) = %+.1f  ", nearbyint(2.5));
    printf("nearbyint(+3.5) = %+.1f\n", nearbyint(3.5));
    printf("nearbyint(-2.3) = %+.1f  ", nearbyint(-2.3));
    printf("nearbyint(-2.5) = %+.1f  ", nearbyint(-2.5));
    printf("nearbyint(-3.5) = %+.1f\n", nearbyint(-3.5));
 
    fesetround(FE_DOWNWARD);
    printf("向下舍入:\nnearbyint(+2.3) = %+.1f  ", nearbyint(2.3));
    printf("nearbyint(+2.5) = %+.1f  ", nearbyint(2.5));
    printf("nearbyint(+3.5) = %+.1f\n", nearbyint(3.5));
    printf("nearbyint(-2.3) = %+.1f  ", nearbyint(-2.3));
    printf("nearbyint(-2.5) = %+.1f  ", nearbyint(-2.5));
    printf("nearbyint(-3.5) = %+.1f\n", nearbyint(-3.5));
 
    printf("nearbyint(-0.0) = %+.1f\n", nearbyint(-0.0));
    printf("nearbyint(-Inf) = %+.1f\n", nearbyint(-INFINITY));
}
```

​	输出：

```txt
舍入到临近:
nearbyint(+2.3) = +2.0  nearbyint(+2.5) = +2.0  nearbyint(+3.5) = +4.0
nearbyint(-2.3) = -2.0  nearbyint(-2.5) = -2.0  nearbyint(-3.5) = -4.0
向下舍入:
nearbyint(+2.3) = +2.0  nearbyint(+2.5) = +2.0  nearbyint(+3.5) = +3.0
nearbyint(-2.3) = -3.0  nearbyint(-2.5) = -3.0  nearbyint(-3.5) = -4.0
nearbyint(-0.0) = -0.0
nearbyint(-Inf) = -inf
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.3 The nearbyint functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.3 The nearbyint functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.3 The nearbyint functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.3 The nearbyint functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.3 The nearbyint functions （第 251-252 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.3 The nearbyint functions （第 526 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.3 The nearbyint functions （第 232 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.3 The nearbyint functions （第 463 页）

**参阅**

| [rint (C99)<br />rintf (C99)<br />rintl (C99)<br />lrint (C99)<br />lrintf (C99)<br />lrintl (C99)<br />llrint (C99)<br />llrintf (C99)<br />llrintl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/rint) | 使用当前舍入模式取整到整数，若结果有误则产生异常 (函数)   |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [round (C99)<br />roundf (C99)<br />roundl (C99)<br />lround (C99)<br />lroundf (C99)<br />lroundl (C99)<br />llround (C99)<br />llroundf (C99)<br />llroundl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/round) | 取整到最接近的整数，在相邻整数正中间时取远离零的数 (函数) |
| [fegetround (C99)<br />fesetround (C99)<br />](https://zh.cppreference.com/w/c/numeric/fenv/feround) | 获得或设置数字的舍入方向 (函数)                           |
| **nearbyint** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/nearbyint)** |                                                           |





### nearbyintf

原址：[https://zh.cppreference.com/w/c/numeric/math/nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint)

作用：用当前舍入模式取整到整数   (函数)

备注：





### nearbyintl

原址：[https://zh.cppreference.com/w/c/numeric/math/nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint)

作用：用当前舍入模式取整到整数   (函数)

备注：





### nextafter

原址：[https://zh.cppreference.com/w/c/numeric/math/nextafter](https://zh.cppreference.com/w/c/numeric/math/nextafter)

作用：确定到给定值方向的下一个可表示的浮点数   (函数)

备注：





### nextafterf

原址：[https://zh.cppreference.com/w/c/numeric/math/nextafter](https://zh.cppreference.com/w/c/numeric/math/nextafter)

作用：确定到给定值方向的下一个可表示的浮点数   (函数)

备注：





### nextafterl

原址：[https://zh.cppreference.com/w/c/numeric/math/nextafter](https://zh.cppreference.com/w/c/numeric/math/nextafter)

作用：确定到给定值方向的下一个可表示的浮点数   (函数)

备注：





### nexttoward

原址：[https://zh.cppreference.com/w/c/numeric/math/nextafter](https://zh.cppreference.com/w/c/numeric/math/nextafter)

作用：确定到给定值方向的下一个可表示的浮点数   (函数)

备注：





### nexttowardf

原址：[https://zh.cppreference.com/w/c/numeric/math/nextafter](https://zh.cppreference.com/w/c/numeric/math/nextafter)

作用：确定到给定值方向的下一个可表示的浮点数   (函数)

备注：





### nexttowardl

原址：[https://zh.cppreference.com/w/c/numeric/math/nextafter](https://zh.cppreference.com/w/c/numeric/math/nextafter)

作用：确定到给定值方向的下一个可表示的浮点数   (函数)

备注：





### pow

原址：[https://zh.cppreference.com/w/c/numeric/math/pow](https://zh.cppreference.com/w/c/numeric/math/pow)

作用：计算一个数的给定次幂（\small{x^y}\small{x^y}xy）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float powf( float base, float exponent );// (1)(C99 起)
double pow( double base, double exponent );// (2)
long double powl( long double base, long double exponent );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define pow( base, exponent )// (4)(C99 起)
```

1-3) 计算 `base` 的 `exponent` 次幂。

4） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `powl`。否则，若任何实参拥有整数类型或 `double` 类型，则调用 `pow`。否则调用 `powf`。若至少一个实参为复数或虚数，则宏调用对应的复函数（`[cpowf](http://zh.cppreference.com/w/c/numeric/complex/cpow)`、`[cpow](http://zh.cppreference.com/w/c/numeric/complex/cpow)`、`[cpowl](http://zh.cppreference.com/w/c/numeric/complex/cpow)`）。

**参数**

| base     | -    | 作为底的浮点数   |
| -------- | ---- | ---------------- |
| exponent | -    | 作为指数的浮点数 |

**返回值**

​	若不出现错误，则返回 `base` 的 `exponent` 次幂（*baseexponent
*）。

​	若出现定义域错误，则返回实现定义值（支持的平台上为 NaN）。

​	若出现极点错误或上溢所致的值域错误，则返回 `±[HUGE_VAL](http://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)`、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `base` 有限且为负，且 `exponent` 有限且为非整数，则出现定义域错误，并可能出现值域错误。

​	若 `base` 为零且 `exponent` 为零，则可能出现定义域错误。

​	若 `base` 为零且 `exponent` 为负，则可能出现定义域错误或极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- `pow(+0, exponent)`，其中 `exponent` 为负奇数，返回 `+∞` 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- `pow(-0, exponent)`，其中 `exponent` 为负奇数，返回 `-∞` 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- `pow(±0, exponent)`，其中 `exponent` 为有限负数，且为偶数或非整数，则返回 +∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- `pow(±0, -∞)` 返回 +∞ 并可能引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)(C23 前)
- `pow(+0, exponent)`，其中 `exponent` 为正奇数，返回 +0
- `pow(-0, exponent)`，其中 `exponent` 为正奇数，返回 -0
- `pow(±0, exponent)`，其中 `exponent` 为正非整数或正偶数，返回 +0
- `pow(-1, ±∞)` 返回 `1`
- `pow(+1, exponent)` 对于任何 `exponent` 返回 `1`，即使 `exponent` 为 `NaN`
- `pow(base, ±0)` 对于任何 `base` 返回 `1`，即使 `base` 为 `NaN`
- `pow(base, exponent)` 返回 `NaN` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)，若 `base` 为有限负数且 `exponent` 为有限非整数。
- `pow(base, -∞)` 对任何 `|base|<1` 返回 +∞
- `pow(base, -∞)` 对任何 `|base|>1` 返回 +0
- `pow(base, +∞)` 对任何 `|base|<1` 返回 +0
- `pow(base, +∞)` 对任何 `|base|>1` 返回 +∞
- `pow(-∞, exponent)` 返回 -0，若 `exponent` 为负奇整数
- `pow(-∞, exponent)` 返回 +0，若 `exponent` 为负非整数或负偶数
- `pow(-∞, exponent)` 返回 -∞，若 `exponent` 为正奇整数
- `pow(-∞, exponent)` 返回 +∞，若 `exponent` 为正非整数或正偶数
- `pow(+∞, exponent)` 对任何 `exponent` 返回 +0
- `pow(+∞, exponent)` 对任何 `exponent` 返回 +∞
- 除了指定于上处，若任何实参为 NaN，则返回 NaN

**注解**

​	尽管 `pow` 不能获得负数的开方根，也为 `exponent` 为 `1 / 3` 的常用情况提供了 [cbrt](https://zh.cppreference.com/w/c/numeric/math/cbrt) 。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    // 典型使用
    printf("pow(2, 10) = %f\n", pow(2,10));
    printf("pow(2, 0.5) = %f\n", pow(2,0.5));
    printf("pow(-2, -3) = %f\n", pow(-2,-3));
 
    // 特殊值
    printf("pow(-1, NAN) = %f\n", pow(-1,NAN));
    printf("pow(+1, NAN) = %f\n", pow(+1,NAN));
    printf("pow(INFINITY, 2) = %f\n", pow(INFINITY, 2));
    printf("pow(INFINITY, -1) = %f\n", pow(INFINITY, -1));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("pow(-1, 1/3) = %f\n", pow(-1, 1.0 / 3));
    if (errno == EDOM)
        perror("    errno == EDOM");
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
 
    feclearexcept(FE_ALL_EXCEPT);
    printf("pow(-0, -3) = %f\n", pow(-0.0, -3));
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
pow(2, 10) = 1024.000000
pow(2, 0.5) = 1.414214
pow(-2, -3) = -0.125000
pow(-1, NAN) = nan
pow(+1, NAN) = 1.000000
pow(INFINITY, 2) = inf
pow(INFINITY, -1) = 0.000000
pow(-1, 1/3) = -nan
    errno == EDOM: Numerical argument out of domain
    FE_INVALID raised
pow(-0, -3) = -inf
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.7.5 The pow functions

  - 7.27 Type-generic math <tgmath.h>

  - F.10.4.5 The pow functions （第 524-525 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.7.4 The pow functions （第 248-249 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.4 The pow functions （第 524-525 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.7.4 The pow functions （第 248-249 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.4 The pow functions （第 524-525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.7.4 The pow functions （第 229 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.4.4 The pow functions （第 461 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.5.1 The pow function

**参阅**

| [sqrt <br />sqrtf (C99)<br />sqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sqrt) | 计算平方根（√xx） (函数)                           |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [cbrt (C99)<br />cbrtf (C99)<br />cbrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cbrt) | 计算立方根（3√xx3） (函数)                         |
| [hypot (C99)<br />hypotf (C99)<br />hypotl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/hypot) | 计算两个给定数平方和的平方根（√x2+y2x2+y2） (函数) |
| [cpow (C99)<br />cpowf (C99)<br />cpowl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cpow) | 计算复数幂函数 (函数)                              |
| **pow** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/pow)** |                                                    |





### powf

原址：[https://zh.cppreference.com/w/c/numeric/math/pow](https://zh.cppreference.com/w/c/numeric/math/pow)

作用：计算一个数的给定次幂（\small{x^y}\small{x^y}xy）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float powf( float base, float exponent );// (1)(C99 起)
double pow( double base, double exponent );// (2)
long double powl( long double base, long double exponent );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define pow( base, exponent )// (4)(C99 起)
```

1-3) 计算 `base` 的 `exponent` 次幂。

4） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `powl`。否则，若任何实参拥有整数类型或 `double` 类型，则调用 `pow`。否则调用 `powf`。若至少一个实参为复数或虚数，则宏调用对应的复函数（`[cpowf](http://zh.cppreference.com/w/c/numeric/complex/cpow)`、`[cpow](http://zh.cppreference.com/w/c/numeric/complex/cpow)`、`[cpowl](http://zh.cppreference.com/w/c/numeric/complex/cpow)`）。

**参数**

| base     | -    | 作为底的浮点数   |
| -------- | ---- | ---------------- |
| exponent | -    | 作为指数的浮点数 |

**返回值**

​	若不出现错误，则返回 `base` 的 `exponent` 次幂（*baseexponent
*）。

​	若出现定义域错误，则返回实现定义值（支持的平台上为 NaN）。

​	若出现极点错误或上溢所致的值域错误，则返回 `±[HUGE_VAL](http://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)`、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `base` 有限且为负，且 `exponent` 有限且为非整数，则出现定义域错误，并可能出现值域错误。

​	若 `base` 为零且 `exponent` 为零，则可能出现定义域错误。

​	若 `base` 为零且 `exponent` 为负，则可能出现定义域错误或极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- `pow(+0, exponent)`，其中 `exponent` 为负奇数，返回 `+∞` 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- `pow(-0, exponent)`，其中 `exponent` 为负奇数，返回 `-∞` 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- `pow(±0, exponent)`，其中 `exponent` 为有限负数，且为偶数或非整数，则返回 +∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- `pow(±0, -∞)` 返回 +∞ 并可能引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)(C23 前)
- `pow(+0, exponent)`，其中 `exponent` 为正奇数，返回 +0
- `pow(-0, exponent)`，其中 `exponent` 为正奇数，返回 -0
- `pow(±0, exponent)`，其中 `exponent` 为正非整数或正偶数，返回 +0
- `pow(-1, ±∞)` 返回 `1`
- `pow(+1, exponent)` 对于任何 `exponent` 返回 `1`，即使 `exponent` 为 `NaN`
- `pow(base, ±0)` 对于任何 `base` 返回 `1`，即使 `base` 为 `NaN`
- `pow(base, exponent)` 返回 `NaN` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)，若 `base` 为有限负数且 `exponent` 为有限非整数。
- `pow(base, -∞)` 对任何 `|base|<1` 返回 +∞
- `pow(base, -∞)` 对任何 `|base|>1` 返回 +0
- `pow(base, +∞)` 对任何 `|base|<1` 返回 +0
- `pow(base, +∞)` 对任何 `|base|>1` 返回 +∞
- `pow(-∞, exponent)` 返回 -0，若 `exponent` 为负奇整数
- `pow(-∞, exponent)` 返回 +0，若 `exponent` 为负非整数或负偶数
- `pow(-∞, exponent)` 返回 -∞，若 `exponent` 为正奇整数
- `pow(-∞, exponent)` 返回 +∞，若 `exponent` 为正非整数或正偶数
- `pow(+∞, exponent)` 对任何 `exponent` 返回 +0
- `pow(+∞, exponent)` 对任何 `exponent` 返回 +∞
- 除了指定于上处，若任何实参为 NaN，则返回 NaN

**注解**

​	尽管 `pow` 不能获得负数的开方根，也为 `exponent` 为 `1 / 3` 的常用情况提供了 [cbrt](https://zh.cppreference.com/w/c/numeric/math/cbrt) 。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    // 典型使用
    printf("pow(2, 10) = %f\n", pow(2,10));
    printf("pow(2, 0.5) = %f\n", pow(2,0.5));
    printf("pow(-2, -3) = %f\n", pow(-2,-3));
 
    // 特殊值
    printf("pow(-1, NAN) = %f\n", pow(-1,NAN));
    printf("pow(+1, NAN) = %f\n", pow(+1,NAN));
    printf("pow(INFINITY, 2) = %f\n", pow(INFINITY, 2));
    printf("pow(INFINITY, -1) = %f\n", pow(INFINITY, -1));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("pow(-1, 1/3) = %f\n", pow(-1, 1.0 / 3));
    if (errno == EDOM)
        perror("    errno == EDOM");
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
 
    feclearexcept(FE_ALL_EXCEPT);
    printf("pow(-0, -3) = %f\n", pow(-0.0, -3));
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
pow(2, 10) = 1024.000000
pow(2, 0.5) = 1.414214
pow(-2, -3) = -0.125000
pow(-1, NAN) = nan
pow(+1, NAN) = 1.000000
pow(INFINITY, 2) = inf
pow(INFINITY, -1) = 0.000000
pow(-1, 1/3) = -nan
    errno == EDOM: Numerical argument out of domain
    FE_INVALID raised
pow(-0, -3) = -inf
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.7.5 The pow functions

  - 7.27 Type-generic math <tgmath.h>

  - F.10.4.5 The pow functions （第 524-525 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.7.4 The pow functions （第 248-249 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.4 The pow functions （第 524-525 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.7.4 The pow functions （第 248-249 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.4 The pow functions （第 524-525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.7.4 The pow functions （第 229 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.4.4 The pow functions （第 461 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.5.1 The pow function

**参阅**

| [sqrt <br />sqrtf (C99)<br />sqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sqrt) | 计算平方根（√xx） (函数)                           |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [cbrt (C99)<br />cbrtf (C99)<br />cbrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cbrt) | 计算立方根（3√xx3） (函数)                         |
| [hypot (C99)<br />hypotf (C99)<br />hypotl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/hypot) | 计算两个给定数平方和的平方根（√x2+y2x2+y2） (函数) |
| [cpow (C99)<br />cpowf (C99)<br />cpowl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cpow) | 计算复数幂函数 (函数)                              |
| **pow** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/pow)** |                                                    |





### powl

原址：[https://zh.cppreference.com/w/c/numeric/math/pow](https://zh.cppreference.com/w/c/numeric/math/pow)

作用：计算一个数的给定次幂（\small{x^y}\small{x^y}xy）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float powf( float base, float exponent );// (1)(C99 起)
double pow( double base, double exponent );// (2)
long double powl( long double base, long double exponent );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define pow( base, exponent )// (4)(C99 起)
```

1-3) 计算 `base` 的 `exponent` 次幂。

4） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `powl`。否则，若任何实参拥有整数类型或 `double` 类型，则调用 `pow`。否则调用 `powf`。若至少一个实参为复数或虚数，则宏调用对应的复函数（`[cpowf](http://zh.cppreference.com/w/c/numeric/complex/cpow)`、`[cpow](http://zh.cppreference.com/w/c/numeric/complex/cpow)`、`[cpowl](http://zh.cppreference.com/w/c/numeric/complex/cpow)`）。

**参数**

| base     | -    | 作为底的浮点数   |
| -------- | ---- | ---------------- |
| exponent | -    | 作为指数的浮点数 |

**返回值**

​	若不出现错误，则返回 `base` 的 `exponent` 次幂（*baseexponent
*）。

​	若出现定义域错误，则返回实现定义值（支持的平台上为 NaN）。

​	若出现极点错误或上溢所致的值域错误，则返回 `±[HUGE_VAL](http://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)`、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `base` 有限且为负，且 `exponent` 有限且为非整数，则出现定义域错误，并可能出现值域错误。

​	若 `base` 为零且 `exponent` 为零，则可能出现定义域错误。

​	若 `base` 为零且 `exponent` 为负，则可能出现定义域错误或极点错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- `pow(+0, exponent)`，其中 `exponent` 为负奇数，返回 `+∞` 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- `pow(-0, exponent)`，其中 `exponent` 为负奇数，返回 `-∞` 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- `pow(±0, exponent)`，其中 `exponent` 为有限负数，且为偶数或非整数，则返回 +∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- `pow(±0, -∞)` 返回 +∞ 并可能引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)(C23 前)
- `pow(+0, exponent)`，其中 `exponent` 为正奇数，返回 +0
- `pow(-0, exponent)`，其中 `exponent` 为正奇数，返回 -0
- `pow(±0, exponent)`，其中 `exponent` 为正非整数或正偶数，返回 +0
- `pow(-1, ±∞)` 返回 `1`
- `pow(+1, exponent)` 对于任何 `exponent` 返回 `1`，即使 `exponent` 为 `NaN`
- `pow(base, ±0)` 对于任何 `base` 返回 `1`，即使 `base` 为 `NaN`
- `pow(base, exponent)` 返回 `NaN` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)，若 `base` 为有限负数且 `exponent` 为有限非整数。
- `pow(base, -∞)` 对任何 `|base|<1` 返回 +∞
- `pow(base, -∞)` 对任何 `|base|>1` 返回 +0
- `pow(base, +∞)` 对任何 `|base|<1` 返回 +0
- `pow(base, +∞)` 对任何 `|base|>1` 返回 +∞
- `pow(-∞, exponent)` 返回 -0，若 `exponent` 为负奇整数
- `pow(-∞, exponent)` 返回 +0，若 `exponent` 为负非整数或负偶数
- `pow(-∞, exponent)` 返回 -∞，若 `exponent` 为正奇整数
- `pow(-∞, exponent)` 返回 +∞，若 `exponent` 为正非整数或正偶数
- `pow(+∞, exponent)` 对任何 `exponent` 返回 +0
- `pow(+∞, exponent)` 对任何 `exponent` 返回 +∞
- 除了指定于上处，若任何实参为 NaN，则返回 NaN

**注解**

​	尽管 `pow` 不能获得负数的开方根，也为 `exponent` 为 `1 / 3` 的常用情况提供了 [cbrt](https://zh.cppreference.com/w/c/numeric/math/cbrt) 。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    // 典型使用
    printf("pow(2, 10) = %f\n", pow(2,10));
    printf("pow(2, 0.5) = %f\n", pow(2,0.5));
    printf("pow(-2, -3) = %f\n", pow(-2,-3));
 
    // 特殊值
    printf("pow(-1, NAN) = %f\n", pow(-1,NAN));
    printf("pow(+1, NAN) = %f\n", pow(+1,NAN));
    printf("pow(INFINITY, 2) = %f\n", pow(INFINITY, 2));
    printf("pow(INFINITY, -1) = %f\n", pow(INFINITY, -1));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("pow(-1, 1/3) = %f\n", pow(-1, 1.0 / 3));
    if (errno == EDOM)
        perror("    errno == EDOM");
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
 
    feclearexcept(FE_ALL_EXCEPT);
    printf("pow(-0, -3) = %f\n", pow(-0.0, -3));
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
}
```

​	可能的输出：

```txt
pow(2, 10) = 1024.000000
pow(2, 0.5) = 1.414214
pow(-2, -3) = -0.125000
pow(-1, NAN) = nan
pow(+1, NAN) = 1.000000
pow(INFINITY, 2) = inf
pow(INFINITY, -1) = 0.000000
pow(-1, 1/3) = -nan
    errno == EDOM: Numerical argument out of domain
    FE_INVALID raised
pow(-0, -3) = -inf
    FE_DIVBYZERO raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.7.5 The pow functions

  - 7.27 Type-generic math <tgmath.h>

  - F.10.4.5 The pow functions （第 524-525 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.7.4 The pow functions （第 248-249 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.4 The pow functions （第 524-525 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.7.4 The pow functions （第 248-249 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.4 The pow functions （第 524-525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.7.4 The pow functions （第 229 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.4.4 The pow functions （第 461 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.5.1 The pow function

**参阅**

| [sqrt <br />sqrtf (C99)<br />sqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sqrt) | 计算平方根（√xx） (函数)                           |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [cbrt (C99)<br />cbrtf (C99)<br />cbrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cbrt) | 计算立方根（3√xx3） (函数)                         |
| [hypot (C99)<br />hypotf (C99)<br />hypotl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/hypot) | 计算两个给定数平方和的平方根（√x2+y2x2+y2） (函数) |
| [cpow (C99)<br />cpowf (C99)<br />cpowl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cpow) | 计算复数幂函数 (函数)                              |
| **pow** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/pow)** |                                                    |





### remainder

原址：[https://zh.cppreference.com/w/c/numeric/math/remainder](https://zh.cppreference.com/w/c/numeric/math/remainder)

作用：计算浮点数除法运算的带符号余数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       remainderf( float x, float y );// (1)(C99 起)
double      remainder( double x, double y );// (2)(C99 起)
long double remainderl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define remainder( x, y )// (4)(C99 起)
```

1-3) 计算浮点数除法运算 `x/y` 的 IEEE 余数。

4） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `remainderl`。否则若任何实参拥有整数类型或 `double` 类型，则调用 `remainder`。否则调用 `remainderf`。

​	此函数所计算的除法运算 `x/y` 的 IEEE 浮点数余数，准确地为值 `x - n * y`，其中值 `n` 是最接近 `x/y` 准确值的整数。*|n-x/y| = ½* 时，选择作为偶数的 `n`。

​	与 std::fmod() 相反，不保证返回值拥有与 `x` 相同的符号。

​	若返回值是 `0`，则它拥有与 `x` 相同的符号。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若成功，则返回如上定义的除法 `x / y` 的 IEEE 浮点数余数。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现下溢所致的值域错误，则返回正确结果。

​	若 `y` 为零但不出现定义域错误，则返回零。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `y` 为零则可能出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
- 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)，结果始终准确。
- 若 `x` 为 ±∞ 且 `y` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `y` 为 ±0 且 `x` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若任一实参为 NaN，则返回 NaN。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/remainder.html)若 `x` 为无穷大或 `y` 为零则出现定义域错误。

​	[fmod](https://zh.cppreference.com/w/c/numeric/math/fmod)，但不是 `remainder`，适于安静地包装浮点数类型到无符号整数类型：`(0.0 <= (y = [fmod](http://zh.cppreference.com/w/c/numeric/math/fmod)( [rint](http://zh.cppreference.com/w/c/numeric/math/rint)(x), 65536.0 )) ? y : 65536.0 + y)` 在范围 `[``-0.0``, ``65535.0``]` 内，它对应 `unsigned short`，但 `remainder([rint](http://zh.cppreference.com/w/c/numeric/math/rint)(x), 65536.0)` 在范围 `[``-32767.0``, ``+32768.0``]` 内，它在 `signed short` 的范围外。

**示例**

```c
#include <fenv.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("remainder(+5.1, +3.0) = %.1f\n", remainder(5.1,3));
    printf("remainder(-5.1, +3.0) = %.1f\n", remainder(-5.1,3));
    printf("remainder(+5.1, -3.0) = %.1f\n", remainder(5.1,-3));
    printf("remainder(-5.1, -3.0) = %.1f\n", remainder(-5.1,-3));
 
    // 特殊值
    printf("remainder(-0.0, 1.0) = %.1f\n", remainder(-0.0, 1));
    printf("remainder(+5.1, Inf) = %.1f\n", remainder(5.1, INFINITY));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("remainder(+5.1, 0) = %.1f\n", remainder(5.1, 0));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	输出：

```txt
remainder(+5.1, +3.0) = -0.9
remainder(-5.1, +3.0) = 0.9
remainder(+5.1, -3.0) = -0.9
remainder(-5.1, -3.0) = 0.9
remainder(+0.0, 1.0) = 0.0
remainder(-0.0, 1.0) = -0.0
remainder(+5.1, Inf) = 5.1
remainder(+5.1, 0) = -nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.10.2 The remainder functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.7.2 The remainder functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.10.2 The remainder functions （第 185-186 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.7.2 The remainder functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.10.2 The remainder functions （第 254-255 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.7.2 The remainder functions （第 529 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.10.2 The remainder functions （第 235 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.7.2 The remainder functions （第 465 页）

**参阅**

| [div <br />ldiv <br />lldiv (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/div) | 计算整数除法的商和余数 (函数)                   |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [fmod <br />fmodf (C99)<br />fmodl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmod) | 计算浮点数除法运算的余数 (函数)                 |
| [remquo (C99)<br />remquof (C99)<br />remquol (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remquo) | 计算除法运算的带符号余数，以及商的后三位 (函数) |
| **remainder** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/remainder)** |                                                 |





### remainderf

原址：[https://zh.cppreference.com/w/c/numeric/math/remainder](https://zh.cppreference.com/w/c/numeric/math/remainder)

作用：计算浮点数除法运算的带符号余数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       remainderf( float x, float y );// (1)(C99 起)
double      remainder( double x, double y );// (2)(C99 起)
long double remainderl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define remainder( x, y )// (4)(C99 起)
```

1-3) 计算浮点数除法运算 `x/y` 的 IEEE 余数。

4） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `remainderl`。否则若任何实参拥有整数类型或 `double` 类型，则调用 `remainder`。否则调用 `remainderf`。

​	此函数所计算的除法运算 `x/y` 的 IEEE 浮点数余数，准确地为值 `x - n * y`，其中值 `n` 是最接近 `x/y` 准确值的整数。*|n-x/y| = ½* 时，选择作为偶数的 `n`。

​	与 std::fmod() 相反，不保证返回值拥有与 `x` 相同的符号。

​	若返回值是 `0`，则它拥有与 `x` 相同的符号。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若成功，则返回如上定义的除法 `x / y` 的 IEEE 浮点数余数。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现下溢所致的值域错误，则返回正确结果。

​	若 `y` 为零但不出现定义域错误，则返回零。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `y` 为零则可能出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
- 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)，结果始终准确。
- 若 `x` 为 ±∞ 且 `y` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `y` 为 ±0 且 `x` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若任一实参为 NaN，则返回 NaN。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/remainder.html)若 `x` 为无穷大或 `y` 为零则出现定义域错误。

​	[fmod](https://zh.cppreference.com/w/c/numeric/math/fmod)，但不是 `remainder`，适于安静地包装浮点数类型到无符号整数类型：`(0.0 <= (y = [fmod](http://zh.cppreference.com/w/c/numeric/math/fmod)( [rint](http://zh.cppreference.com/w/c/numeric/math/rint)(x), 65536.0 )) ? y : 65536.0 + y)` 在范围 `[``-0.0``, ``65535.0``]` 内，它对应 `unsigned short`，但 `remainder([rint](http://zh.cppreference.com/w/c/numeric/math/rint)(x), 65536.0)` 在范围 `[``-32767.0``, ``+32768.0``]` 内，它在 `signed short` 的范围外。

**示例**

```c
#include <fenv.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("remainder(+5.1, +3.0) = %.1f\n", remainder(5.1,3));
    printf("remainder(-5.1, +3.0) = %.1f\n", remainder(-5.1,3));
    printf("remainder(+5.1, -3.0) = %.1f\n", remainder(5.1,-3));
    printf("remainder(-5.1, -3.0) = %.1f\n", remainder(-5.1,-3));
 
    // 特殊值
    printf("remainder(-0.0, 1.0) = %.1f\n", remainder(-0.0, 1));
    printf("remainder(+5.1, Inf) = %.1f\n", remainder(5.1, INFINITY));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("remainder(+5.1, 0) = %.1f\n", remainder(5.1, 0));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	输出：

```txt
remainder(+5.1, +3.0) = -0.9
remainder(-5.1, +3.0) = 0.9
remainder(+5.1, -3.0) = -0.9
remainder(-5.1, -3.0) = 0.9
remainder(+0.0, 1.0) = 0.0
remainder(-0.0, 1.0) = -0.0
remainder(+5.1, Inf) = 5.1
remainder(+5.1, 0) = -nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.10.2 The remainder functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.7.2 The remainder functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.10.2 The remainder functions （第 185-186 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.7.2 The remainder functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.10.2 The remainder functions （第 254-255 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.7.2 The remainder functions （第 529 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.10.2 The remainder functions （第 235 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.7.2 The remainder functions （第 465 页）

**参阅**

| [div <br />ldiv <br />lldiv (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/div) | 计算整数除法的商和余数 (函数)                   |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [fmod <br />fmodf (C99)<br />fmodl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmod) | 计算浮点数除法运算的余数 (函数)                 |
| [remquo (C99)<br />remquof (C99)<br />remquol (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remquo) | 计算除法运算的带符号余数，以及商的后三位 (函数) |
| **remainder** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/remainder)** |                                                 |





### remainderl

原址：[https://zh.cppreference.com/w/c/numeric/math/remainder](https://zh.cppreference.com/w/c/numeric/math/remainder)

作用：计算浮点数除法运算的带符号余数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       remainderf( float x, float y );// (1)(C99 起)
double      remainder( double x, double y );// (2)(C99 起)
long double remainderl( long double x, long double y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define remainder( x, y )// (4)(C99 起)
```

1-3) 计算浮点数除法运算 `x/y` 的 IEEE 余数。

4） 泛型宏：若任何实参拥有 `long double` 类型，则调用 `remainderl`。否则若任何实参拥有整数类型或 `double` 类型，则调用 `remainder`。否则调用 `remainderf`。

​	此函数所计算的除法运算 `x/y` 的 IEEE 浮点数余数，准确地为值 `x - n * y`，其中值 `n` 是最接近 `x/y` 准确值的整数。*|n-x/y| = ½* 时，选择作为偶数的 `n`。

​	与 std::fmod() 相反，不保证返回值拥有与 `x` 相同的符号。

​	若返回值是 `0`，则它拥有与 `x` 相同的符号。

**参数**

| x, y | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若成功，则返回如上定义的除法 `x / y` 的 IEEE 浮点数余数。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现下溢所致的值域错误，则返回正确结果。

​	若 `y` 为零但不出现定义域错误，则返回零。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `y` 为零则可能出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
- 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)，结果始终准确。
- 若 `x` 为 ±∞ 且 `y` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `y` 为 ±0 且 `x` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若任一实参为 NaN，则返回 NaN。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/remainder.html)若 `x` 为无穷大或 `y` 为零则出现定义域错误。

​	[fmod](https://zh.cppreference.com/w/c/numeric/math/fmod)，但不是 `remainder`，适于安静地包装浮点数类型到无符号整数类型：`(0.0 <= (y = [fmod](http://zh.cppreference.com/w/c/numeric/math/fmod)( [rint](http://zh.cppreference.com/w/c/numeric/math/rint)(x), 65536.0 )) ? y : 65536.0 + y)` 在范围 `[``-0.0``, ``65535.0``]` 内，它对应 `unsigned short`，但 `remainder([rint](http://zh.cppreference.com/w/c/numeric/math/rint)(x), 65536.0)` 在范围 `[``-32767.0``, ``+32768.0``]` 内，它在 `signed short` 的范围外。

**示例**

```c
#include <fenv.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("remainder(+5.1, +3.0) = %.1f\n", remainder(5.1,3));
    printf("remainder(-5.1, +3.0) = %.1f\n", remainder(-5.1,3));
    printf("remainder(+5.1, -3.0) = %.1f\n", remainder(5.1,-3));
    printf("remainder(-5.1, -3.0) = %.1f\n", remainder(-5.1,-3));
 
    // 特殊值
    printf("remainder(-0.0, 1.0) = %.1f\n", remainder(-0.0, 1));
    printf("remainder(+5.1, Inf) = %.1f\n", remainder(5.1, INFINITY));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("remainder(+5.1, 0) = %.1f\n", remainder(5.1, 0));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	输出：

```txt
remainder(+5.1, +3.0) = -0.9
remainder(-5.1, +3.0) = 0.9
remainder(+5.1, -3.0) = -0.9
remainder(-5.1, -3.0) = 0.9
remainder(+0.0, 1.0) = 0.0
remainder(-0.0, 1.0) = -0.0
remainder(+5.1, Inf) = 5.1
remainder(+5.1, 0) = -nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.10.2 The remainder functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.7.2 The remainder functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.10.2 The remainder functions （第 185-186 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.7.2 The remainder functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.10.2 The remainder functions （第 254-255 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.7.2 The remainder functions （第 529 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.10.2 The remainder functions （第 235 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.7.2 The remainder functions （第 465 页）

**参阅**

| [div <br />ldiv <br />lldiv (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/div) | 计算整数除法的商和余数 (函数)                   |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [fmod <br />fmodf (C99)<br />fmodl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmod) | 计算浮点数除法运算的余数 (函数)                 |
| [remquo (C99)<br />remquof (C99)<br />remquol (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remquo) | 计算除法运算的带符号余数，以及商的后三位 (函数) |
| **remainder** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/remainder)** |                                                 |





### remquo

原址：[https://zh.cppreference.com/w/c/numeric/math/remquo](https://zh.cppreference.com/w/c/numeric/math/remquo)

作用：计算除法运算的带符号余数，以及商的后三位   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       remquof( float x, float y, int *quo );// (1)(C99 起)
double      remquo( double x, double y, int *quo );// (2)(C99 起)
long double remquol( long double x, long double y, int *quo );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define remquo( x, y, quo )// (4)(C99 起)
```

1-3) 计算除法运算 `x/y` 的浮点数余数，如 [remainder()](https://zh.cppreference.com/w/c/numeric/math/remainder) 函数所为。另外，将存储 `x/y` 的至少最低三位及符号于 `quo`，这足以确定结果在周期中的八分位。

4） 泛型宏：若任何非指针实参拥有 `long double` 类型，则调用 `remquol`。否则，若任何非指针实参拥有整数类型或 `double` 类型，则调用 `remquo`。否则，调用 `remquof`。

**参数**

| x, y | -    | 浮点数                                    |
| ---- | ---- | ----------------------------------------- |
| quo  | -    | 指向存储 `x/y` 的符号和某些位的整数的指针 |

**返回值**

​	若成功，则返回定义于 [remainder](https://zh.cppreference.com/w/c/numeric/math/remainder) 的 `x/y` 的余数，并存储 `x/y` 的符号和至少后三位有效数字于 `*quo`（正式而言，存储的值的符号是 `x/y` 的符号，而绝对值与 `x/y` 的整数商的绝对值对于 *modulo 2n
\* 同余，其中 *n* 是实现定义的大于或等于 *3* 的整数）。

​	若 `y` 为零，则存储于 `*quo` 的值未指定。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现下溢所致的值域错误，则若支持非正规值则返回正确结果。

​	若 `y` 为零，但不出现定义域错误，则返回零。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `y` 为零则可能出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
- 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `x` 为 ±∞ 且 `y` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `y` 为 ±0 且 `x` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `x` 或 `y` 为 NaN，则返回 NaN。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/remquo.html)若 `x` 为无穷大或 `y` 为零则出现定义域错误。

​	此函数在实现可准确表示为浮点数的周期函数时有用：对非常大的 `x` 计算 *sin(πx)* 时，直接调用 [sin](https://zh.cppreference.com/w/c/numeric/math/sin) 可能导致巨大误差，但若首先以 `remquo` 减小实参，则商的低位可用来确定结果在周期中的八分位，同时余数可用来计算拥有高精度的值。

​	某些平台上硬件支持此运算（而例如在 Intel CPU 上，`FPREM1` 在完成时于商中准确保留 3 位精度）。

**示例**

```c
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
double cos_pi_x_naive(double x)
{
    double pi = acos(-1);
    return cos(pi * x);
}
 
// 周期为 2，值为 (0;0.5) 正，(0.5;1.5) 负，(1.5,2) 正
double cos_pi_x_smart(double x)
{
    const double pi = acos(-1);
    int extremum;
    double rem = remquo(x, 1, &extremum);
    extremum = (unsigned)extremum % 2; // 保留 1 位以确定最近极值
    return extremum ? -cos(pi * rem) : cos(pi * rem);
}
 
int main(void)
{
    printf("cos(pi * 0.25) = %f\n", cos_pi_x_naive(0.25));
    printf("cos(pi * 1.25) = %f\n", cos_pi_x_naive(1.25));
    printf("cos(pi * 1000000000000.25) = %f\n", cos_pi_x_naive(1000000000000.25));
    printf("cos(pi * 1000000000001.25) = %f\n", cos_pi_x_naive(1000000000001.25));
    printf("cos(pi * 1000000000000.25) = %f\n", cos_pi_x_smart(1000000000000.25));
    printf("cos(pi * 1000000000001.25) = %f\n", cos_pi_x_smart(1000000000001.25));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    int quo;
    printf("remquo(+Inf, 1) = %.1f\n", remquo(INFINITY, 1, &quo));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
cos(pi * 0.25) = 0.707107
cos(pi * 1.25) = -0.707107
cos(pi * 1000000000000.25) = 0.707123
cos(pi * 1000000000001.25) = -0.707117
cos(pi * 1000000000000.25) = 0.707107
cos(pi * 1000000000001.25) = -0.707107 
remquo(+Inf, 1) = -nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.10.3 The remquo functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.7.3 The remquo functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.10.3 The remquo functions （第 186 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.7.3 The remquo functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.10.3 The remquo functions （第 255 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.7.3 The remquo functions （第 529 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.10.3 The remquo functions （第 236 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.7.3 The remquo functions （第 465 页）

**参阅**

| [div <br />ldiv <br />lldiv (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/div) | 计算整数除法的商和余数 (函数)         |
| ------------------------------------------------------------ | ------------------------------------- |
| [fmod <br />fmodf (C99)<br />fmodl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmod) | 计算浮点数除法运算的余数 (函数)       |
| [remainder (C99)<br />remainderf (C99)<br />remainderl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remainder) | 计算浮点数除法运算的带符号余数 (函数) |
| **remquo** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/remquo)** |                                       |





### remquof

原址：[https://zh.cppreference.com/w/c/numeric/math/remquo](https://zh.cppreference.com/w/c/numeric/math/remquo)

作用：计算除法运算的带符号余数，以及商的后三位   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       remquof( float x, float y, int *quo );// (1)(C99 起)
double      remquo( double x, double y, int *quo );// (2)(C99 起)
long double remquol( long double x, long double y, int *quo );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define remquo( x, y, quo )// (4)(C99 起)
```

1-3) 计算除法运算 `x/y` 的浮点数余数，如 [remainder()](https://zh.cppreference.com/w/c/numeric/math/remainder) 函数所为。另外，将存储 `x/y` 的至少最低三位及符号于 `quo`，这足以确定结果在周期中的八分位。

4） 泛型宏：若任何非指针实参拥有 `long double` 类型，则调用 `remquol`。否则，若任何非指针实参拥有整数类型或 `double` 类型，则调用 `remquo`。否则，调用 `remquof`。

**参数**

| x, y | -    | 浮点数                                    |
| ---- | ---- | ----------------------------------------- |
| quo  | -    | 指向存储 `x/y` 的符号和某些位的整数的指针 |

**返回值**

​	若成功，则返回定义于 [remainder](https://zh.cppreference.com/w/c/numeric/math/remainder) 的 `x/y` 的余数，并存储 `x/y` 的符号和至少后三位有效数字于 `*quo`（正式而言，存储的值的符号是 `x/y` 的符号，而绝对值与 `x/y` 的整数商的绝对值对于 *modulo 2n
\* 同余，其中 *n* 是实现定义的大于或等于 *3* 的整数）。

​	若 `y` 为零，则存储于 `*quo` 的值未指定。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现下溢所致的值域错误，则若支持非正规值则返回正确结果。

​	若 `y` 为零，但不出现定义域错误，则返回零。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `y` 为零则可能出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
- 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `x` 为 ±∞ 且 `y` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `y` 为 ±0 且 `x` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `x` 或 `y` 为 NaN，则返回 NaN。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/remquo.html)若 `x` 为无穷大或 `y` 为零则出现定义域错误。

​	此函数在实现可准确表示为浮点数的周期函数时有用：对非常大的 `x` 计算 *sin(πx)* 时，直接调用 [sin](https://zh.cppreference.com/w/c/numeric/math/sin) 可能导致巨大误差，但若首先以 `remquo` 减小实参，则商的低位可用来确定结果在周期中的八分位，同时余数可用来计算拥有高精度的值。

​	某些平台上硬件支持此运算（而例如在 Intel CPU 上，`FPREM1` 在完成时于商中准确保留 3 位精度）。

**示例**

```c
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
double cos_pi_x_naive(double x)
{
    double pi = acos(-1);
    return cos(pi * x);
}
 
// 周期为 2，值为 (0;0.5) 正，(0.5;1.5) 负，(1.5,2) 正
double cos_pi_x_smart(double x)
{
    const double pi = acos(-1);
    int extremum;
    double rem = remquo(x, 1, &extremum);
    extremum = (unsigned)extremum % 2; // 保留 1 位以确定最近极值
    return extremum ? -cos(pi * rem) : cos(pi * rem);
}
 
int main(void)
{
    printf("cos(pi * 0.25) = %f\n", cos_pi_x_naive(0.25));
    printf("cos(pi * 1.25) = %f\n", cos_pi_x_naive(1.25));
    printf("cos(pi * 1000000000000.25) = %f\n", cos_pi_x_naive(1000000000000.25));
    printf("cos(pi * 1000000000001.25) = %f\n", cos_pi_x_naive(1000000000001.25));
    printf("cos(pi * 1000000000000.25) = %f\n", cos_pi_x_smart(1000000000000.25));
    printf("cos(pi * 1000000000001.25) = %f\n", cos_pi_x_smart(1000000000001.25));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    int quo;
    printf("remquo(+Inf, 1) = %.1f\n", remquo(INFINITY, 1, &quo));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
cos(pi * 0.25) = 0.707107
cos(pi * 1.25) = -0.707107
cos(pi * 1000000000000.25) = 0.707123
cos(pi * 1000000000001.25) = -0.707117
cos(pi * 1000000000000.25) = 0.707107
cos(pi * 1000000000001.25) = -0.707107 
remquo(+Inf, 1) = -nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.10.3 The remquo functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.7.3 The remquo functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.10.3 The remquo functions （第 186 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.7.3 The remquo functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.10.3 The remquo functions （第 255 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.7.3 The remquo functions （第 529 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.10.3 The remquo functions （第 236 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.7.3 The remquo functions （第 465 页）

**参阅**

| [div <br />ldiv <br />lldiv (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/div) | 计算整数除法的商和余数 (函数)         |
| ------------------------------------------------------------ | ------------------------------------- |
| [fmod <br />fmodf (C99)<br />fmodl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmod) | 计算浮点数除法运算的余数 (函数)       |
| [remainder (C99)<br />remainderf (C99)<br />remainderl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remainder) | 计算浮点数除法运算的带符号余数 (函数) |
| **remquo** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/remquo)** |                                       |





### remquol

原址：[https://zh.cppreference.com/w/c/numeric/math/remquo](https://zh.cppreference.com/w/c/numeric/math/remquo)

作用：计算除法运算的带符号余数，以及商的后三位   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       remquof( float x, float y, int *quo );// (1)(C99 起)
double      remquo( double x, double y, int *quo );// (2)(C99 起)
long double remquol( long double x, long double y, int *quo );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define remquo( x, y, quo )// (4)(C99 起)
```

1-3) 计算除法运算 `x/y` 的浮点数余数，如 [remainder()](https://zh.cppreference.com/w/c/numeric/math/remainder) 函数所为。另外，将存储 `x/y` 的至少最低三位及符号于 `quo`，这足以确定结果在周期中的八分位。

4） 泛型宏：若任何非指针实参拥有 `long double` 类型，则调用 `remquol`。否则，若任何非指针实参拥有整数类型或 `double` 类型，则调用 `remquo`。否则，调用 `remquof`。

**参数**

| x, y | -    | 浮点数                                    |
| ---- | ---- | ----------------------------------------- |
| quo  | -    | 指向存储 `x/y` 的符号和某些位的整数的指针 |

**返回值**

​	若成功，则返回定义于 [remainder](https://zh.cppreference.com/w/c/numeric/math/remainder) 的 `x/y` 的余数，并存储 `x/y` 的符号和至少后三位有效数字于 `*quo`（正式而言，存储的值的符号是 `x/y` 的符号，而绝对值与 `x/y` 的整数商的绝对值对于 *modulo 2n
\* 同余，其中 *n* 是实现定义的大于或等于 *3* 的整数）。

​	若 `y` 为零，则存储于 `*quo` 的值未指定。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现下溢所致的值域错误，则若支持非正规值则返回正确结果。

​	若 `y` 为零，但不出现定义域错误，则返回零。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `y` 为零则可能出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
- 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `x` 为 ±∞ 且 `y` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `y` 为 ±0 且 `x` 非 NaN，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
- 若 `x` 或 `y` 为 NaN，则返回 NaN。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/remquo.html)若 `x` 为无穷大或 `y` 为零则出现定义域错误。

​	此函数在实现可准确表示为浮点数的周期函数时有用：对非常大的 `x` 计算 *sin(πx)* 时，直接调用 [sin](https://zh.cppreference.com/w/c/numeric/math/sin) 可能导致巨大误差，但若首先以 `remquo` 减小实参，则商的低位可用来确定结果在周期中的八分位，同时余数可用来计算拥有高精度的值。

​	某些平台上硬件支持此运算（而例如在 Intel CPU 上，`FPREM1` 在完成时于商中准确保留 3 位精度）。

**示例**

```c
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
double cos_pi_x_naive(double x)
{
    double pi = acos(-1);
    return cos(pi * x);
}
 
// 周期为 2，值为 (0;0.5) 正，(0.5;1.5) 负，(1.5,2) 正
double cos_pi_x_smart(double x)
{
    const double pi = acos(-1);
    int extremum;
    double rem = remquo(x, 1, &extremum);
    extremum = (unsigned)extremum % 2; // 保留 1 位以确定最近极值
    return extremum ? -cos(pi * rem) : cos(pi * rem);
}
 
int main(void)
{
    printf("cos(pi * 0.25) = %f\n", cos_pi_x_naive(0.25));
    printf("cos(pi * 1.25) = %f\n", cos_pi_x_naive(1.25));
    printf("cos(pi * 1000000000000.25) = %f\n", cos_pi_x_naive(1000000000000.25));
    printf("cos(pi * 1000000000001.25) = %f\n", cos_pi_x_naive(1000000000001.25));
    printf("cos(pi * 1000000000000.25) = %f\n", cos_pi_x_smart(1000000000000.25));
    printf("cos(pi * 1000000000001.25) = %f\n", cos_pi_x_smart(1000000000001.25));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    int quo;
    printf("remquo(+Inf, 1) = %.1f\n", remquo(INFINITY, 1, &quo));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
cos(pi * 0.25) = 0.707107
cos(pi * 1.25) = -0.707107
cos(pi * 1000000000000.25) = 0.707123
cos(pi * 1000000000001.25) = -0.707117
cos(pi * 1000000000000.25) = 0.707107
cos(pi * 1000000000001.25) = -0.707107 
remquo(+Inf, 1) = -nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.10.3 The remquo functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.7.3 The remquo functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.10.3 The remquo functions （第 186 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.7.3 The remquo functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.10.3 The remquo functions （第 255 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.7.3 The remquo functions （第 529 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.10.3 The remquo functions （第 236 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.7.3 The remquo functions （第 465 页）

**参阅**

| [div <br />ldiv <br />lldiv (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/div) | 计算整数除法的商和余数 (函数)         |
| ------------------------------------------------------------ | ------------------------------------- |
| [fmod <br />fmodf (C99)<br />fmodl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmod) | 计算浮点数除法运算的余数 (函数)       |
| [remainder (C99)<br />remainderf (C99)<br />remainderl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remainder) | 计算浮点数除法运算的带符号余数 (函数) |
| **remquo** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/remquo)** |                                       |





### rint

原址：[https://zh.cppreference.com/w/c/numeric/math/rint](https://zh.cppreference.com/w/c/numeric/math/rint)

作用：使用当前舍入模式取整到整数，若结果有误则产生异常   (函数)

备注：





### rintf

原址：[https://zh.cppreference.com/w/c/numeric/math/rint](https://zh.cppreference.com/w/c/numeric/math/rint)

作用：使用当前舍入模式取整到整数，若结果有误则产生异常   (函数)

备注：





### rintl

原址：[https://zh.cppreference.com/w/c/numeric/math/rint](https://zh.cppreference.com/w/c/numeric/math/rint)

作用：使用当前舍入模式取整到整数，若结果有误则产生异常   (函数)

备注：





### round

原址：[https://zh.cppreference.com/w/c/numeric/math/round](https://zh.cppreference.com/w/c/numeric/math/round)

作用：取整到最接近的整数，在相邻整数正中间时取远离零的数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       roundf( float arg );// (1)(C99 起)
double      round( double arg );// (2)(C99 起)
long double roundl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define round( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
long      lroundf( float arg );// (5)(C99 起)
long      lround( double arg );// (6)(C99 起)
long      lroundl( long double arg );// (7)(C99 起)
// 在标头 <tgmath.h> 定义
#define lround( arg )// (8)(C99 起)
// 在标头 <math.h> 定义
long long llroundf( float arg );// (9)(C99 起)
long long llround( double arg );// (10)(C99 起)
long long llroundl( long double arg );// (11)(C99 起)
// 在标头 <tgmath.h> 定义
#define llround( arg )// (12)(C99 起)
```

1-3) 计算与 `arg` 最邻近的整数（以浮点数格式），中点情况取远离零者，无关乎当前舍入模式。

5-7, 9-11) 计算与 `arg` 最邻近的整数（以整数格式），中点情况取远离零者，无关乎当前舍入模式。

4,8,12) 泛型宏：若 `arg` 拥有 `long double` 类型，则分别调用 `roundl`、`lroundl`、`llroundl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则分别调用 `round`、`lround`、`llround`。否则分别调用 `roundf`、`lroundf`、`llroundf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则与返回 `arg` 的最邻近整数，中点情况取远离零者，

返回值

![math-round away zero.svg](https://upload.cppreference.com/mwiki/images/7/7c/math-round_away_zero.svg)

实参

​	若出现定义域错误，则返回实现定义值。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `lround` 或 `llround` 的结果在返回类型的可表示范围外，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），

  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则返回未修改的该值。
  - 若 `arg` 为 ±0，则返回未修改的该值。
  - 若 `arg` 为 NaN，则返回 NaN。
  - 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若舍入结果在返回类型的范围外，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若 `arg` 为 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。

**注解**

​	`round` 在舍入非整数有限值时，可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数均为准确的整数，故 `round` 自身决不上溢；然而在存储于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lround.html) `lround` 或 `llround` 引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的所有情况都是定义域错误。

​	`round` 的 `double` 版本如同实现如下：

```c
#include <math.h>
double round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
```

**示例**

```c
#include <assert.h>
#include <fenv.h>
#include <float.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
double custom_round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
 
void test_custom_round()
{
    const double sample[] =
    {
        0.0, 2.3, 2.5 - DBL_EPSILON, 2.5, 2.5 + DBL_EPSILON, 2.7, INFINITY
    };
    for (size_t t = 0; t < sizeof sample / sizeof(double); ++t)
        assert(round(+sample[t]) == custom_round(+sample[t]) &&
               round(-sample[t]) == custom_round(-sample[t]));
}
 
int main(void)
{
    // round
    printf("round(+2.3) = %+.1f  ", round(2.3));
    printf("round(+2.5) = %+.1f  ", round(2.5));
    printf("round(+2.7) = %+.1f\n", round(2.7));
    printf("round(-2.3) = %+.1f  ", round(-2.3));
    printf("round(-2.5) = %+.1f  ", round(-2.5));
    printf("round(-2.7) = %+.1f\n", round(-2.7));
 
    printf("round(-0.0) = %+.1f\n", round(-0.0));
    printf("round(-Inf) = %+f\n",   round(-INFINITY));
 
    test_custom_round();
 
    // lround
    printf("lround(+2.3) = %+ld  ", lround(2.3));
    printf("lround(+2.5) = %+ld  ", lround(2.5));
    printf("lround(+2.7) = %+ld\n", lround(2.7));
    printf("lround(-2.3) = %+ld  ", lround(-2.3));
    printf("lround(-2.5) = %+ld  ", lround(-2.5));
    printf("lround(-2.7) = %+ld\n", lround(-2.7));
 
    printf("lround(-0.0) = %+ld\n", lround(-0.0));
    printf("lround(-Inf) = %+ld\n", lround(-INFINITY)); // 引发 FE_INVALID
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("lround(LONG_MAX+1.5) = %ld\n", lround(LONG_MAX + 1.5));
    if (fetestexcept(FE_INVALID))
        puts("    引发了 FE_INVALID");
}
```

​	可能的输出：

```txt
round(+2.3) = +2.0  round(+2.5) = +3.0  round(+2.7) = +3.0
round(-2.3) = -2.0  round(-2.5) = -3.0  round(-2.7) = -3.0
round(-0.0) = -0.0
round(-Inf) = -inf
lround(+2.3) = +2  lround(+2.5) = +3  lround(+2.7) = +3
lround(-2.3) = -2  lround(-2.5) = -3  lround(-2.7) = -3
lround(-0.0) = +0
lround(-Inf) = -9223372036854775808
lround(LONG_MAX+1.5) = -9223372036854775808
    引发了 FE_INVALID
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.6 The round functions （第 TBD 页）

  - 7.12.9.7 The lround and llround functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.6 The round functions （第 TBD 页）

  - F.10.6.7 The lround and llround functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.6 The round functions （第 184 页）

  - 7.12.9.7 The lround and llround functions （第 184-185 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.6.6 The round functions （第 384 页）

  - F.10.6.7 The lround and llround functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.6 The round functions （第 253 页）

  - 7.12.9.7 The lround and llround functions （第 253 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.6 The round functions （第 527 页）

  - F.10.6.7 The lround and llround functions （第 528 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.6 The round functions （第 233 页）

  - 7.12.9.7 The lround and llround functions （第 234 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.6 The round functions （第 464 页）

  - F.9.6.7 The lround and llround functions （第 464 页）

**参阅**

| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)           |
| ------------------------------------------------------------ | ------------------------------------------- |
| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)           |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| **round** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/round)** |                                             |





### roundf

原址：[https://zh.cppreference.com/w/c/numeric/math/round](https://zh.cppreference.com/w/c/numeric/math/round)

作用：取整到最接近的整数，在相邻整数正中间时取远离零的数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       roundf( float arg );// (1)(C99 起)
double      round( double arg );// (2)(C99 起)
long double roundl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define round( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
long      lroundf( float arg );// (5)(C99 起)
long      lround( double arg );// (6)(C99 起)
long      lroundl( long double arg );// (7)(C99 起)
// 在标头 <tgmath.h> 定义
#define lround( arg )// (8)(C99 起)
// 在标头 <math.h> 定义
long long llroundf( float arg );// (9)(C99 起)
long long llround( double arg );// (10)(C99 起)
long long llroundl( long double arg );// (11)(C99 起)
// 在标头 <tgmath.h> 定义
#define llround( arg )// (12)(C99 起)
```

1-3) 计算与 `arg` 最邻近的整数（以浮点数格式），中点情况取远离零者，无关乎当前舍入模式。

5-7, 9-11) 计算与 `arg` 最邻近的整数（以整数格式），中点情况取远离零者，无关乎当前舍入模式。

4,8,12) 泛型宏：若 `arg` 拥有 `long double` 类型，则分别调用 `roundl`、`lroundl`、`llroundl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则分别调用 `round`、`lround`、`llround`。否则分别调用 `roundf`、`lroundf`、`llroundf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则与返回 `arg` 的最邻近整数，中点情况取远离零者，

返回值

![math-round away zero.svg](https://upload.cppreference.com/mwiki/images/7/7c/math-round_away_zero.svg)

实参

​	若出现定义域错误，则返回实现定义值。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `lround` 或 `llround` 的结果在返回类型的可表示范围外，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），

  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则返回未修改的该值。
  - 若 `arg` 为 ±0，则返回未修改的该值。
  - 若 `arg` 为 NaN，则返回 NaN。
  - 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若舍入结果在返回类型的范围外，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若 `arg` 为 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。

**注解**

​	`round` 在舍入非整数有限值时，可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数均为准确的整数，故 `round` 自身决不上溢；然而在存储于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lround.html) `lround` 或 `llround` 引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的所有情况都是定义域错误。

​	`round` 的 `double` 版本如同实现如下：

```c
#include <math.h>
double round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
```

**示例**

```c
#include <assert.h>
#include <fenv.h>
#include <float.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
double custom_round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
 
void test_custom_round()
{
    const double sample[] =
    {
        0.0, 2.3, 2.5 - DBL_EPSILON, 2.5, 2.5 + DBL_EPSILON, 2.7, INFINITY
    };
    for (size_t t = 0; t < sizeof sample / sizeof(double); ++t)
        assert(round(+sample[t]) == custom_round(+sample[t]) &&
               round(-sample[t]) == custom_round(-sample[t]));
}
 
int main(void)
{
    // round
    printf("round(+2.3) = %+.1f  ", round(2.3));
    printf("round(+2.5) = %+.1f  ", round(2.5));
    printf("round(+2.7) = %+.1f\n", round(2.7));
    printf("round(-2.3) = %+.1f  ", round(-2.3));
    printf("round(-2.5) = %+.1f  ", round(-2.5));
    printf("round(-2.7) = %+.1f\n", round(-2.7));
 
    printf("round(-0.0) = %+.1f\n", round(-0.0));
    printf("round(-Inf) = %+f\n",   round(-INFINITY));
 
    test_custom_round();
 
    // lround
    printf("lround(+2.3) = %+ld  ", lround(2.3));
    printf("lround(+2.5) = %+ld  ", lround(2.5));
    printf("lround(+2.7) = %+ld\n", lround(2.7));
    printf("lround(-2.3) = %+ld  ", lround(-2.3));
    printf("lround(-2.5) = %+ld  ", lround(-2.5));
    printf("lround(-2.7) = %+ld\n", lround(-2.7));
 
    printf("lround(-0.0) = %+ld\n", lround(-0.0));
    printf("lround(-Inf) = %+ld\n", lround(-INFINITY)); // 引发 FE_INVALID
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("lround(LONG_MAX+1.5) = %ld\n", lround(LONG_MAX + 1.5));
    if (fetestexcept(FE_INVALID))
        puts("    引发了 FE_INVALID");
}
```

​	可能的输出：

```txt
round(+2.3) = +2.0  round(+2.5) = +3.0  round(+2.7) = +3.0
round(-2.3) = -2.0  round(-2.5) = -3.0  round(-2.7) = -3.0
round(-0.0) = -0.0
round(-Inf) = -inf
lround(+2.3) = +2  lround(+2.5) = +3  lround(+2.7) = +3
lround(-2.3) = -2  lround(-2.5) = -3  lround(-2.7) = -3
lround(-0.0) = +0
lround(-Inf) = -9223372036854775808
lround(LONG_MAX+1.5) = -9223372036854775808
    引发了 FE_INVALID
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.6 The round functions （第 TBD 页）

  - 7.12.9.7 The lround and llround functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.6 The round functions （第 TBD 页）

  - F.10.6.7 The lround and llround functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.6 The round functions （第 184 页）

  - 7.12.9.7 The lround and llround functions （第 184-185 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.6.6 The round functions （第 384 页）

  - F.10.6.7 The lround and llround functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.6 The round functions （第 253 页）

  - 7.12.9.7 The lround and llround functions （第 253 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.6 The round functions （第 527 页）

  - F.10.6.7 The lround and llround functions （第 528 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.6 The round functions （第 233 页）

  - 7.12.9.7 The lround and llround functions （第 234 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.6 The round functions （第 464 页）

  - F.9.6.7 The lround and llround functions （第 464 页）

**参阅**

| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)           |
| ------------------------------------------------------------ | ------------------------------------------- |
| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)           |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| **round** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/round)** |                                             |





### roundl

原址：[https://zh.cppreference.com/w/c/numeric/math/round](https://zh.cppreference.com/w/c/numeric/math/round)

作用：取整到最接近的整数，在相邻整数正中间时取远离零的数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       roundf( float arg );// (1)(C99 起)
double      round( double arg );// (2)(C99 起)
long double roundl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define round( arg )// (4)(C99 起)
// 在标头 <math.h> 定义
long      lroundf( float arg );// (5)(C99 起)
long      lround( double arg );// (6)(C99 起)
long      lroundl( long double arg );// (7)(C99 起)
// 在标头 <tgmath.h> 定义
#define lround( arg )// (8)(C99 起)
// 在标头 <math.h> 定义
long long llroundf( float arg );// (9)(C99 起)
long long llround( double arg );// (10)(C99 起)
long long llroundl( long double arg );// (11)(C99 起)
// 在标头 <tgmath.h> 定义
#define llround( arg )// (12)(C99 起)
```

1-3) 计算与 `arg` 最邻近的整数（以浮点数格式），中点情况取远离零者，无关乎当前舍入模式。

5-7, 9-11) 计算与 `arg` 最邻近的整数（以整数格式），中点情况取远离零者，无关乎当前舍入模式。

4,8,12) 泛型宏：若 `arg` 拥有 `long double` 类型，则分别调用 `roundl`、`lroundl`、`llroundl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则分别调用 `round`、`lround`、`llround`。否则分别调用 `roundf`、`lroundf`、`llroundf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则与返回 `arg` 的最邻近整数，中点情况取远离零者，

返回值

![math-round away zero.svg](https://upload.cppreference.com/mwiki/images/7/7c/math-round_away_zero.svg)

实参

​	若出现定义域错误，则返回实现定义值。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `lround` 或 `llround` 的结果在返回类型的可表示范围外，则可能出现定义域错误或值域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），

  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则返回未修改的该值。
  - 若 `arg` 为 ±0，则返回未修改的该值。
  - 若 `arg` 为 NaN，则返回 NaN。
  - 决不引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。
  - 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
  - 若 `arg` 为 ±∞，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若舍入结果在返回类型的范围外，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。
  - 若 `arg` 为 NaN，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回实现定义值。

**注解**

​	`round` 在舍入非整数有限值时，可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数均为准确的整数，故 `round` 自身决不上溢；然而在存储于整数对象时，结果可能溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/lround.html) `lround` 或 `llround` 引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 的所有情况都是定义域错误。

​	`round` 的 `double` 版本如同实现如下：

```c
#include <math.h>
double round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
```

**示例**

```c
#include <assert.h>
#include <fenv.h>
#include <float.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
double custom_round(double x)
{
    return signbit(x) ? ceil(x - 0.5) : floor(x + 0.5);
}
 
void test_custom_round()
{
    const double sample[] =
    {
        0.0, 2.3, 2.5 - DBL_EPSILON, 2.5, 2.5 + DBL_EPSILON, 2.7, INFINITY
    };
    for (size_t t = 0; t < sizeof sample / sizeof(double); ++t)
        assert(round(+sample[t]) == custom_round(+sample[t]) &&
               round(-sample[t]) == custom_round(-sample[t]));
}
 
int main(void)
{
    // round
    printf("round(+2.3) = %+.1f  ", round(2.3));
    printf("round(+2.5) = %+.1f  ", round(2.5));
    printf("round(+2.7) = %+.1f\n", round(2.7));
    printf("round(-2.3) = %+.1f  ", round(-2.3));
    printf("round(-2.5) = %+.1f  ", round(-2.5));
    printf("round(-2.7) = %+.1f\n", round(-2.7));
 
    printf("round(-0.0) = %+.1f\n", round(-0.0));
    printf("round(-Inf) = %+f\n",   round(-INFINITY));
 
    test_custom_round();
 
    // lround
    printf("lround(+2.3) = %+ld  ", lround(2.3));
    printf("lround(+2.5) = %+ld  ", lround(2.5));
    printf("lround(+2.7) = %+ld\n", lround(2.7));
    printf("lround(-2.3) = %+ld  ", lround(-2.3));
    printf("lround(-2.5) = %+ld  ", lround(-2.5));
    printf("lround(-2.7) = %+ld\n", lround(-2.7));
 
    printf("lround(-0.0) = %+ld\n", lround(-0.0));
    printf("lround(-Inf) = %+ld\n", lround(-INFINITY)); // 引发 FE_INVALID
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("lround(LONG_MAX+1.5) = %ld\n", lround(LONG_MAX + 1.5));
    if (fetestexcept(FE_INVALID))
        puts("    引发了 FE_INVALID");
}
```

​	可能的输出：

```txt
round(+2.3) = +2.0  round(+2.5) = +3.0  round(+2.7) = +3.0
round(-2.3) = -2.0  round(-2.5) = -3.0  round(-2.7) = -3.0
round(-0.0) = -0.0
round(-Inf) = -inf
lround(+2.3) = +2  lround(+2.5) = +3  lround(+2.7) = +3
lround(-2.3) = -2  lround(-2.5) = -3  lround(-2.7) = -3
lround(-0.0) = +0
lround(-Inf) = -9223372036854775808
lround(LONG_MAX+1.5) = -9223372036854775808
    引发了 FE_INVALID
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.9.6 The round functions （第 TBD 页）

  - 7.12.9.7 The lround and llround functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.6.6 The round functions （第 TBD 页）

  - F.10.6.7 The lround and llround functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.9.6 The round functions （第 184 页）

  - 7.12.9.7 The lround and llround functions （第 184-185 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.6.6 The round functions （第 384 页）

  - F.10.6.7 The lround and llround functions （第 385 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.6 The round functions （第 253 页）

  - 7.12.9.7 The lround and llround functions （第 253 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.6 The round functions （第 527 页）

  - F.10.6.7 The lround and llround functions （第 528 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.6 The round functions （第 233 页）

  - 7.12.9.7 The lround and llround functions （第 234 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.6 The round functions （第 464 页）

  - F.9.6.7 The lround and llround functions （第 464 页）

**参阅**

| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)           |
| ------------------------------------------------------------ | ------------------------------------------- |
| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)           |
| [trunc (C99)<br />truncf (C99)<br />truncl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/trunc) | 取整到绝对值不大于给定值的最接近整数 (函数) |
| **round** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/round)** |                                             |





### scalbln

原址：[https://zh.cppreference.com/w/c/numeric/math/scalbn](https://zh.cppreference.com/w/c/numeric/math/scalbn)

作用：高效计算一个数乘 FLT_RADIX 的幂   (函数)

备注：





### scalblnf

原址：[https://zh.cppreference.com/w/c/numeric/math/scalbn](https://zh.cppreference.com/w/c/numeric/math/scalbn)

作用：高效计算一个数乘 FLT_RADIX 的幂   (函数)

备注：





### scalblnl

原址：[https://zh.cppreference.com/w/c/numeric/math/scalbn](https://zh.cppreference.com/w/c/numeric/math/scalbn)

作用：高效计算一个数乘 FLT_RADIX 的幂   (函数)

备注：





### scalbn

原址：[https://zh.cppreference.com/w/c/numeric/math/scalbn](https://zh.cppreference.com/w/c/numeric/math/scalbn)

作用：高效计算一个数乘 FLT_RADIX 的幂   (函数)

备注：





### scalbnf

原址：[https://zh.cppreference.com/w/c/numeric/math/scalbn](https://zh.cppreference.com/w/c/numeric/math/scalbn)

作用：高效计算一个数乘 FLT_RADIX 的幂   (函数)

备注：





### scalbnl

原址：[https://zh.cppreference.com/w/c/numeric/math/scalbn](https://zh.cppreference.com/w/c/numeric/math/scalbn)

作用：高效计算一个数乘 FLT_RADIX 的幂   (函数)

备注：





### sin

原址：[https://zh.cppreference.com/w/c/numeric/math/sin](https://zh.cppreference.com/w/c/numeric/math/sin)

作用：计算正弦（{\small\sin{x} }{\small\sin{x} }sin(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       sinf( float arg );// (1)(C99 起)
double      sin( double arg );// (2)
long double sinl( long double arg );// (3)(C99 起)
_Decimal32  sind32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  sind64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 sind128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define sin( arg )// (7)(C99 起)
```

1-3) 计算 `arg`（以弧度度量）的正弦。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `sinl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `sin`。否则调用 `sinf` 。若实参是复数，则该宏调用对应的复函数（`[csinf](http://zh.cppreference.com/w/c/numeric/complex/csin)`、`[csin](http://zh.cppreference.com/w/c/numeric/complex/csin)`、`[csinl](http://zh.cppreference.com/w/c/numeric/complex/csin)`）。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| arg  | -    | 以弧度表示角的浮点数 |
| ---- | ---- | -------------------- |
|      |      |                      |

**返回值**

​	若不发生错误，则返回 `arg` 的正弦（*sin(arg)*），值域为 *[-1 ; +1]*。

​	若 `arg` 的绝对值很大，结果可能拥有少量或无有效数字。 (C99 前)

​	若发生定义域错误，则返回实现定义的值（受支持的平台上为 NaN ）。

​	若发生下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数是 ±0，则返回未修改的实参
- 若参数是 ±∞，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若参数是 NaN，则返回 NaN

**注意**

​	实参为无穷大的情况， C 中不指定为定义域错误，但它被指定为 [POSIX 中的定义域错误](http://pubs.opengroup.org/onlinepubs/9699919799/functions/sin.html)。

​	POSIX 亦指定在溢出的情况下，返回不修改的 `arg`，而且若不支持如此，则返回实现定义的不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 及 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的值。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
int main(void)
{
    const double pi = acos(-1);
 
    // 典型使用
    printf("sin(pi/6) = %f\n", sin(pi / 6));
    printf("sin(pi/2) = %f\n", sin(pi / 2));
    printf("sin(-3*pi/4) = %f\n", sin(-3 * pi / 4));
 
    // 特殊值
    printf("sin(+0) = %f\n", sin(0.0));
    printf("sin(-0) = %f\n", sin(-0.0));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("sin(INFINITY) = %f\n", sin(INFINITY));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
sin(pi/6) = 0.500000
sin(pi/2) = 1.000000
sin(-3*pi/4) = -0.707107
sin(+0) = 0.000000
sin(-0) = -0.000000
sin(INFINITY) = -nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.6 The sin functions （第 TBD 页）

  - 7.27 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.6 The sin functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.6 The sin functions （第 175 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.6 The sin functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.6 The sin functions （第 239-240 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.6 The sin functions （第 519 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.6 The sin functions （第 220 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.6 The sin functions （第 456 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.6 The sin function

**参阅**

| [cos <br />cosf (C99)<br />cosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cos) | 计算余弦（cosxcos⁡x） (函数)         |
| ------------------------------------------------------------ | ----------------------------------- |
| [tan <br />tanf (C99)<br />tanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tan) | 计算正切（tanxtan⁡x） (函数)         |
| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡x） (函数) |
| [csin (C99)<br />csinf (C99)<br />csinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csin) | 计算复数正弦 (函数)                 |
| **sin** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/sin)** |                                     |





### sinf

原址：[https://zh.cppreference.com/w/c/numeric/math/sin](https://zh.cppreference.com/w/c/numeric/math/sin)

作用：计算正弦（{\small\sin{x} }{\small\sin{x} }sin(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       sinf( float arg );// (1)(C99 起)
double      sin( double arg );// (2)
long double sinl( long double arg );// (3)(C99 起)
_Decimal32  sind32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  sind64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 sind128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define sin( arg )// (7)(C99 起)
```

1-3) 计算 `arg`（以弧度度量）的正弦。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `sinl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `sin`。否则调用 `sinf` 。若实参是复数，则该宏调用对应的复函数（`[csinf](http://zh.cppreference.com/w/c/numeric/complex/csin)`、`[csin](http://zh.cppreference.com/w/c/numeric/complex/csin)`、`[csinl](http://zh.cppreference.com/w/c/numeric/complex/csin)`）。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| arg  | -    | 以弧度表示角的浮点数 |
| ---- | ---- | -------------------- |
|      |      |                      |

**返回值**

​	若不发生错误，则返回 `arg` 的正弦（*sin(arg)*），值域为 *[-1 ; +1]*。

​	若 `arg` 的绝对值很大，结果可能拥有少量或无有效数字。 (C99 前)

​	若发生定义域错误，则返回实现定义的值（受支持的平台上为 NaN ）。

​	若发生下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数是 ±0，则返回未修改的实参
- 若参数是 ±∞，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若参数是 NaN，则返回 NaN

**注意**

​	实参为无穷大的情况， C 中不指定为定义域错误，但它被指定为 [POSIX 中的定义域错误](http://pubs.opengroup.org/onlinepubs/9699919799/functions/sin.html)。

​	POSIX 亦指定在溢出的情况下，返回不修改的 `arg`，而且若不支持如此，则返回实现定义的不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 及 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的值。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
int main(void)
{
    const double pi = acos(-1);
 
    // 典型使用
    printf("sin(pi/6) = %f\n", sin(pi / 6));
    printf("sin(pi/2) = %f\n", sin(pi / 2));
    printf("sin(-3*pi/4) = %f\n", sin(-3 * pi / 4));
 
    // 特殊值
    printf("sin(+0) = %f\n", sin(0.0));
    printf("sin(-0) = %f\n", sin(-0.0));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("sin(INFINITY) = %f\n", sin(INFINITY));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
sin(pi/6) = 0.500000
sin(pi/2) = 1.000000
sin(-3*pi/4) = -0.707107
sin(+0) = 0.000000
sin(-0) = -0.000000
sin(INFINITY) = -nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.6 The sin functions （第 TBD 页）

  - 7.27 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.6 The sin functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.6 The sin functions （第 175 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.6 The sin functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.6 The sin functions （第 239-240 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.6 The sin functions （第 519 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.6 The sin functions （第 220 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.6 The sin functions （第 456 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.6 The sin function

**参阅**

| [cos <br />cosf (C99)<br />cosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cos) | 计算余弦（cosxcos⁡x） (函数)         |
| ------------------------------------------------------------ | ----------------------------------- |
| [tan <br />tanf (C99)<br />tanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tan) | 计算正切（tanxtan⁡x） (函数)         |
| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡x） (函数) |
| [csin (C99)<br />csinf (C99)<br />csinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csin) | 计算复数正弦 (函数)                 |
| **sin** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/sin)** |                                     |





### sinh

原址：[https://zh.cppreference.com/w/c/numeric/math/sinh](https://zh.cppreference.com/w/c/numeric/math/sinh)

作用：计算双曲正弦（{\small\sinh{x} }{\small\sinh{x} }sinh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       sinhf( float arg );// (1)(C99 起)
double      sinh( double arg );// (2)
long double sinhl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define sinh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的双曲正弦。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `sinhl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `sinh`。否则调用 `sinhf`。若实参为复数，则宏调用对应的复数函数（`[csinhf](http://zh.cppreference.com/w/c/numeric/complex/csinh)`、`[csinh](http://zh.cppreference.com/w/c/numeric/complex/csinh)`、`[csinhl](http://zh.cppreference.com/w/c/numeric/complex/csinh)`）。

**参数**

| arg  | -    | 表示双曲角的浮点数 |
| ---- | ---- | ------------------ |
|      |      |                    |

**返回值**

若不出现错误，则返回 `arg` 的双曲正弦（*sinh(arg)* 或 

| earg -e-arg |
| ----------- |
| 2           |

）。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 ±0 或 ±∞，则返回未修改的实参
- 若实参为 NaN，则返回 NaN

**注解**

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/sinh.html)在下溢情况下，返回不修改的 `arg`，而若不支持如此，则返回不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 和 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的实现定义值。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("sinh(1) = %f\nsinh(-1)=%f\n", sinh(1), sinh(-1));
    printf("log(sinh(1) + cosh(1))=%f\n", log(sinh(1) + cosh(1)));
 
    // 特殊值
    printf("sinh(+0) = %f\nsinh(-0)=%f\n", sinh(0.0), sinh(-0.0));
 
    // 错误处理
    errno=0; feclearexcept(FE_ALL_EXCEPT);
    printf("sinh(710.5) = %f\n", sinh(710.5));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
sinh(1) = 1.175201
sinh(-1)=-1.175201
log(sinh(1) + cosh(1))=1.000000
sinh(+0) = 0.000000
sinh(-0)=-0.000000
sinh(710.5) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.5 The sinh functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.5 The sinh functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.5 The sinh functions （第 176 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.2.5 The sinh functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.5 The sinh functions （第 241-242 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.5 The sinh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.5 The sinh functions （第 222 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.5 The sinh functions （第 457 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.3.2 The sinh function

**参阅**

| [cosh <br />coshf (C99)<br />coshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cosh) | 计算双曲余弦（coshxcosh⁡x） (函数)       |
| ------------------------------------------------------------ | --------------------------------------- |
| [tanh <br />tanhf (C99)<br />tanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tanh) | 计算双曲正切（tanhxtanh⁡x） (函数)       |
| [asinh (C99)<br />asinhf (C99)<br />asinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asinh) | 计算反双曲正弦（arsinhxarsinh⁡x） (函数) |
| [csinh (C99)<br />csinhf (C99)<br />csinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csinh) | 计算复数双曲正弦 (函数)                 |
| **sinh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/sinh)** |                                         |





### sinhf

原址：[https://zh.cppreference.com/w/c/numeric/math/sinh](https://zh.cppreference.com/w/c/numeric/math/sinh)

作用：计算双曲正弦（{\small\sinh{x} }{\small\sinh{x} }sinh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       sinhf( float arg );// (1)(C99 起)
double      sinh( double arg );// (2)
long double sinhl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define sinh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的双曲正弦。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `sinhl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `sinh`。否则调用 `sinhf`。若实参为复数，则宏调用对应的复数函数（`[csinhf](http://zh.cppreference.com/w/c/numeric/complex/csinh)`、`[csinh](http://zh.cppreference.com/w/c/numeric/complex/csinh)`、`[csinhl](http://zh.cppreference.com/w/c/numeric/complex/csinh)`）。

**参数**

| arg  | -    | 表示双曲角的浮点数 |
| ---- | ---- | ------------------ |
|      |      |                    |

**返回值**

若不出现错误，则返回 `arg` 的双曲正弦（*sinh(arg)* 或 

| earg -e-arg |
| ----------- |
| 2           |

）。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 ±0 或 ±∞，则返回未修改的实参
- 若实参为 NaN，则返回 NaN

**注解**

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/sinh.html)在下溢情况下，返回不修改的 `arg`，而若不支持如此，则返回不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 和 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的实现定义值。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("sinh(1) = %f\nsinh(-1)=%f\n", sinh(1), sinh(-1));
    printf("log(sinh(1) + cosh(1))=%f\n", log(sinh(1) + cosh(1)));
 
    // 特殊值
    printf("sinh(+0) = %f\nsinh(-0)=%f\n", sinh(0.0), sinh(-0.0));
 
    // 错误处理
    errno=0; feclearexcept(FE_ALL_EXCEPT);
    printf("sinh(710.5) = %f\n", sinh(710.5));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
sinh(1) = 1.175201
sinh(-1)=-1.175201
log(sinh(1) + cosh(1))=1.000000
sinh(+0) = 0.000000
sinh(-0)=-0.000000
sinh(710.5) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.5 The sinh functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.5 The sinh functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.5 The sinh functions （第 176 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.2.5 The sinh functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.5 The sinh functions （第 241-242 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.5 The sinh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.5 The sinh functions （第 222 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.5 The sinh functions （第 457 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.3.2 The sinh function

**参阅**

| [cosh <br />coshf (C99)<br />coshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cosh) | 计算双曲余弦（coshxcosh⁡x） (函数)       |
| ------------------------------------------------------------ | --------------------------------------- |
| [tanh <br />tanhf (C99)<br />tanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tanh) | 计算双曲正切（tanhxtanh⁡x） (函数)       |
| [asinh (C99)<br />asinhf (C99)<br />asinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asinh) | 计算反双曲正弦（arsinhxarsinh⁡x） (函数) |
| [csinh (C99)<br />csinhf (C99)<br />csinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csinh) | 计算复数双曲正弦 (函数)                 |
| **sinh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/sinh)** |                                         |





### sinhl

原址：[https://zh.cppreference.com/w/c/numeric/math/sinh](https://zh.cppreference.com/w/c/numeric/math/sinh)

作用：计算双曲正弦（{\small\sinh{x} }{\small\sinh{x} }sinh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       sinhf( float arg );// (1)(C99 起)
double      sinh( double arg );// (2)
long double sinhl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define sinh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的双曲正弦。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `sinhl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `sinh`。否则调用 `sinhf`。若实参为复数，则宏调用对应的复数函数（`[csinhf](http://zh.cppreference.com/w/c/numeric/complex/csinh)`、`[csinh](http://zh.cppreference.com/w/c/numeric/complex/csinh)`、`[csinhl](http://zh.cppreference.com/w/c/numeric/complex/csinh)`）。

**参数**

| arg  | -    | 表示双曲角的浮点数 |
| ---- | ---- | ------------------ |
|      |      |                    |

**返回值**

若不出现错误，则返回 `arg` 的双曲正弦（*sinh(arg)* 或 

| earg -e-arg |
| ----------- |
| 2           |

）。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参为 ±0 或 ±∞，则返回未修改的实参
- 若实参为 NaN，则返回 NaN

**注解**

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/sinh.html)在下溢情况下，返回不修改的 `arg`，而若不支持如此，则返回不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 和 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的实现定义值。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("sinh(1) = %f\nsinh(-1)=%f\n", sinh(1), sinh(-1));
    printf("log(sinh(1) + cosh(1))=%f\n", log(sinh(1) + cosh(1)));
 
    // 特殊值
    printf("sinh(+0) = %f\nsinh(-0)=%f\n", sinh(0.0), sinh(-0.0));
 
    // 错误处理
    errno=0; feclearexcept(FE_ALL_EXCEPT);
    printf("sinh(710.5) = %f\n", sinh(710.5));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    if (fetestexcept(FE_OVERFLOW))
        puts("    FE_OVERFLOW raised");
}
```

​	可能的输出：

```txt
sinh(1) = 1.175201
sinh(-1)=-1.175201
log(sinh(1) + cosh(1))=1.000000
sinh(+0) = 0.000000
sinh(-0)=-0.000000
sinh(710.5) = inf
    errno == ERANGE: Numerical result out of range
    FE_OVERFLOW raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.5 The sinh functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.5 The sinh functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.5 The sinh functions （第 176 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.2.5 The sinh functions （第 379 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.5 The sinh functions （第 241-242 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.5 The sinh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.5 The sinh functions （第 222 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.5 The sinh functions （第 457 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.3.2 The sinh function

**参阅**

| [cosh <br />coshf (C99)<br />coshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cosh) | 计算双曲余弦（coshxcosh⁡x） (函数)       |
| ------------------------------------------------------------ | --------------------------------------- |
| [tanh <br />tanhf (C99)<br />tanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tanh) | 计算双曲正切（tanhxtanh⁡x） (函数)       |
| [asinh (C99)<br />asinhf (C99)<br />asinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asinh) | 计算反双曲正弦（arsinhxarsinh⁡x） (函数) |
| [csinh (C99)<br />csinhf (C99)<br />csinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csinh) | 计算复数双曲正弦 (函数)                 |
| **sinh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/sinh)** |                                         |





### sinl

原址：[https://zh.cppreference.com/w/c/numeric/math/sin](https://zh.cppreference.com/w/c/numeric/math/sin)

作用：计算正弦（{\small\sin{x} }{\small\sin{x} }sin(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       sinf( float arg );// (1)(C99 起)
double      sin( double arg );// (2)
long double sinl( long double arg );// (3)(C99 起)
_Decimal32  sind32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  sind64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 sind128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define sin( arg )// (7)(C99 起)
```

1-3) 计算 `arg`（以弧度度量）的正弦。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `sinl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `sin`。否则调用 `sinf` 。若实参是复数，则该宏调用对应的复函数（`[csinf](http://zh.cppreference.com/w/c/numeric/complex/csin)`、`[csin](http://zh.cppreference.com/w/c/numeric/complex/csin)`、`[csinl](http://zh.cppreference.com/w/c/numeric/complex/csin)`）。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| arg  | -    | 以弧度表示角的浮点数 |
| ---- | ---- | -------------------- |
|      |      |                      |

**返回值**

​	若不发生错误，则返回 `arg` 的正弦（*sin(arg)*），值域为 *[-1 ; +1]*。

​	若 `arg` 的绝对值很大，结果可能拥有少量或无有效数字。 (C99 前)

​	若发生定义域错误，则返回实现定义的值（受支持的平台上为 NaN ）。

​	若发生下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数是 ±0，则返回未修改的实参
- 若参数是 ±∞，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若参数是 NaN，则返回 NaN

**注意**

​	实参为无穷大的情况， C 中不指定为定义域错误，但它被指定为 [POSIX 中的定义域错误](http://pubs.opengroup.org/onlinepubs/9699919799/functions/sin.html)。

​	POSIX 亦指定在溢出的情况下，返回不修改的 `arg`，而且若不支持如此，则返回实现定义的不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 及 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的值。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
int main(void)
{
    const double pi = acos(-1);
 
    // 典型使用
    printf("sin(pi/6) = %f\n", sin(pi / 6));
    printf("sin(pi/2) = %f\n", sin(pi / 2));
    printf("sin(-3*pi/4) = %f\n", sin(-3 * pi / 4));
 
    // 特殊值
    printf("sin(+0) = %f\n", sin(0.0));
    printf("sin(-0) = %f\n", sin(-0.0));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("sin(INFINITY) = %f\n", sin(INFINITY));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
sin(pi/6) = 0.500000
sin(pi/2) = 1.000000
sin(-3*pi/4) = -0.707107
sin(+0) = 0.000000
sin(-0) = -0.000000
sin(INFINITY) = -nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.6 The sin functions （第 TBD 页）

  - 7.27 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.6 The sin functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.6 The sin functions （第 175 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.6 The sin functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.6 The sin functions （第 239-240 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.6 The sin functions （第 519 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.6 The sin functions （第 220 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.6 The sin functions （第 456 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.6 The sin function

**参阅**

| [cos <br />cosf (C99)<br />cosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cos) | 计算余弦（cosxcos⁡x） (函数)         |
| ------------------------------------------------------------ | ----------------------------------- |
| [tan <br />tanf (C99)<br />tanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tan) | 计算正切（tanxtan⁡x） (函数)         |
| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡x） (函数) |
| [csin (C99)<br />csinf (C99)<br />csinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csin) | 计算复数正弦 (函数)                 |
| **sin** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/sin)** |                                     |





### sqrt

原址：[https://zh.cppreference.com/w/c/numeric/math/sqrt](https://zh.cppreference.com/w/c/numeric/math/sqrt)

作用：计算平方根（\small{\sqrt{x} }\small{\sqrt{x} }√x）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       sqrtf( float arg );// (1)(C99 起)
double      sqrt( double arg );// (2)
long double sqrtl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define sqrt( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的平方根。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `sqrtl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `sqrt`。否则调用 `sqrtf`。若 `arg` 为复数或虚数，则宏调用对应复数函数（`[csqrtf](http://zh.cppreference.com/w/c/numeric/complex/csqrt)`、`[csqrt](http://zh.cppreference.com/w/c/numeric/complex/csqrt)`、`[csqrtl](http://zh.cppreference.com/w/c/numeric/complex/csqrt)`）。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的平方根（√argarg）。

​	若出现定义域错误，则返回实现定义值（支持的平台上为 NaN）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 小于零则出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参小于 -0，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回 NaN。
- 若实参为 +∞ 或 ±0，则返回不修改的参数。
- 若实参为 NaN，则返回 NaN。

**注解**

​	IEEE 标准要求 `sqrt` 为准确。其他要求为准确的运算只有[算术运算符](https://zh.cppreference.com/w/c/language/operator_arithmetic)和函数 [fma](https://zh.cppreference.com/w/c/numeric/math/fma)。舍入到返回类型后（用默认舍入模式），`sqrt` 的结果与无限精度结果不可辨别。换言之，误差小于 0.5 ulp。其他函数，含 [pow](https://zh.cppreference.com/w/c/numeric/math/pow)，不受这种制约。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    // 正常使用
    printf("sqrt(100) = %f\n", sqrt(100));
    printf("sqrt(2) = %f\n", sqrt(2));
    printf("黄金比 = %f\n", (1 + sqrt(5)) / 2);
 
    // 特殊值
    printf("sqrt(-0) = %f\n", sqrt(-0.0));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("sqrt(-1.0) = %f\n", sqrt(-1));
    if (errno == EDOM)
        perror("    errno == EDOM");
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID was raised");
}
```

​	可能的输出：

```txt
sqrt(100) = 10.000000
sqrt(2) = 1.414214
黄金比 = 1.618034
sqrt(-0) = -0.000000
sqrt(-1.0) = -nan
    errno = EDOM: Numerical argument out of domain
    FE_INVALID was raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.7.5 The sqrt functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.4.5 The sqrt functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.7.5 The sqrt functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.4.5 The sqrt functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.7.5 The sqrt functions （第 249 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.5 The sqrt functions （第 525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.7.5 The sqrt functions （第 229-230 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.4.5 The sqrt functions （第 462 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.5.2 The sqrt function

**参阅**

| [pow <br />powf (C99)<br />powl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/pow) | 计算一个数的给定次幂（xyxy） (函数)                |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [cbrt (C99)<br />cbrtf (C99)<br />cbrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cbrt) | 计算立方根（3√xx3） (函数)                         |
| [hypot (C99)<br />hypotf (C99)<br />hypotl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/hypot) | 计算两个给定数平方和的平方根（√x2+y2x2+y2） (函数) |
| [csqrt (C99)<br />csqrtf (C99)<br />csqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csqrt) | 计算复数平方根 (函数)                              |
| **sqrt** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/sqrt)** |                                                    |





### sqrtf

原址：[https://zh.cppreference.com/w/c/numeric/math/sqrt](https://zh.cppreference.com/w/c/numeric/math/sqrt)

作用：计算平方根（\small{\sqrt{x} }\small{\sqrt{x} }√x）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       sqrtf( float arg );// (1)(C99 起)
double      sqrt( double arg );// (2)
long double sqrtl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define sqrt( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的平方根。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `sqrtl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `sqrt`。否则调用 `sqrtf`。若 `arg` 为复数或虚数，则宏调用对应复数函数（`[csqrtf](http://zh.cppreference.com/w/c/numeric/complex/csqrt)`、`[csqrt](http://zh.cppreference.com/w/c/numeric/complex/csqrt)`、`[csqrtl](http://zh.cppreference.com/w/c/numeric/complex/csqrt)`）。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的平方根（√argarg）。

​	若出现定义域错误，则返回实现定义值（支持的平台上为 NaN）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 小于零则出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参小于 -0，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回 NaN。
- 若实参为 +∞ 或 ±0，则返回不修改的参数。
- 若实参为 NaN，则返回 NaN。

**注解**

​	IEEE 标准要求 `sqrt` 为准确。其他要求为准确的运算只有[算术运算符](https://zh.cppreference.com/w/c/language/operator_arithmetic)和函数 [fma](https://zh.cppreference.com/w/c/numeric/math/fma)。舍入到返回类型后（用默认舍入模式），`sqrt` 的结果与无限精度结果不可辨别。换言之，误差小于 0.5 ulp。其他函数，含 [pow](https://zh.cppreference.com/w/c/numeric/math/pow)，不受这种制约。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    // 正常使用
    printf("sqrt(100) = %f\n", sqrt(100));
    printf("sqrt(2) = %f\n", sqrt(2));
    printf("黄金比 = %f\n", (1 + sqrt(5)) / 2);
 
    // 特殊值
    printf("sqrt(-0) = %f\n", sqrt(-0.0));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("sqrt(-1.0) = %f\n", sqrt(-1));
    if (errno == EDOM)
        perror("    errno == EDOM");
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID was raised");
}
```

​	可能的输出：

```txt
sqrt(100) = 10.000000
sqrt(2) = 1.414214
黄金比 = 1.618034
sqrt(-0) = -0.000000
sqrt(-1.0) = -nan
    errno = EDOM: Numerical argument out of domain
    FE_INVALID was raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.7.5 The sqrt functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.4.5 The sqrt functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.7.5 The sqrt functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.4.5 The sqrt functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.7.5 The sqrt functions （第 249 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.5 The sqrt functions （第 525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.7.5 The sqrt functions （第 229-230 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.4.5 The sqrt functions （第 462 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.5.2 The sqrt function

**参阅**

| [pow <br />powf (C99)<br />powl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/pow) | 计算一个数的给定次幂（xyxy） (函数)                |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [cbrt (C99)<br />cbrtf (C99)<br />cbrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cbrt) | 计算立方根（3√xx3） (函数)                         |
| [hypot (C99)<br />hypotf (C99)<br />hypotl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/hypot) | 计算两个给定数平方和的平方根（√x2+y2x2+y2） (函数) |
| [csqrt (C99)<br />csqrtf (C99)<br />csqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csqrt) | 计算复数平方根 (函数)                              |
| **sqrt** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/sqrt)** |                                                    |





### sqrtl

原址：[https://zh.cppreference.com/w/c/numeric/math/sqrt](https://zh.cppreference.com/w/c/numeric/math/sqrt)

作用：计算平方根（\small{\sqrt{x} }\small{\sqrt{x} }√x）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       sqrtf( float arg );// (1)(C99 起)
double      sqrt( double arg );// (2)
long double sqrtl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define sqrt( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的平方根。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `sqrtl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `sqrt`。否则调用 `sqrtf`。若 `arg` 为复数或虚数，则宏调用对应复数函数（`[csqrtf](http://zh.cppreference.com/w/c/numeric/complex/csqrt)`、`[csqrt](http://zh.cppreference.com/w/c/numeric/complex/csqrt)`、`[csqrtl](http://zh.cppreference.com/w/c/numeric/complex/csqrt)`）。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的平方根（√argarg）。

​	若出现定义域错误，则返回实现定义值（支持的平台上为 NaN）。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若 `arg` 小于零则出现定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若实参小于 -0，则引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 并返回 NaN。
- 若实参为 +∞ 或 ±0，则返回不修改的参数。
- 若实参为 NaN，则返回 NaN。

**注解**

​	IEEE 标准要求 `sqrt` 为准确。其他要求为准确的运算只有[算术运算符](https://zh.cppreference.com/w/c/language/operator_arithmetic)和函数 [fma](https://zh.cppreference.com/w/c/numeric/math/fma)。舍入到返回类型后（用默认舍入模式），`sqrt` 的结果与无限精度结果不可辨别。换言之，误差小于 0.5 ulp。其他函数，含 [pow](https://zh.cppreference.com/w/c/numeric/math/pow)，不受这种制约。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    // 正常使用
    printf("sqrt(100) = %f\n", sqrt(100));
    printf("sqrt(2) = %f\n", sqrt(2));
    printf("黄金比 = %f\n", (1 + sqrt(5)) / 2);
 
    // 特殊值
    printf("sqrt(-0) = %f\n", sqrt(-0.0));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("sqrt(-1.0) = %f\n", sqrt(-1));
    if (errno == EDOM)
        perror("    errno == EDOM");
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID was raised");
}
```

​	可能的输出：

```txt
sqrt(100) = 10.000000
sqrt(2) = 1.414214
黄金比 = 1.618034
sqrt(-0) = -0.000000
sqrt(-1.0) = -nan
    errno = EDOM: Numerical argument out of domain
    FE_INVALID was raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.7.5 The sqrt functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.4.5 The sqrt functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.7.5 The sqrt functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.4.5 The sqrt functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.7.5 The sqrt functions （第 249 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.4.5 The sqrt functions （第 525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.7.5 The sqrt functions （第 229-230 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.4.5 The sqrt functions （第 462 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.5.2 The sqrt function

**参阅**

| [pow <br />powf (C99)<br />powl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/pow) | 计算一个数的给定次幂（xyxy） (函数)                |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [cbrt (C99)<br />cbrtf (C99)<br />cbrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cbrt) | 计算立方根（3√xx3） (函数)                         |
| [hypot (C99)<br />hypotf (C99)<br />hypotl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/hypot) | 计算两个给定数平方和的平方根（√x2+y2x2+y2） (函数) |
| [csqrt (C99)<br />csqrtf (C99)<br />csqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csqrt) | 计算复数平方根 (函数)                              |
| **sqrt** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/sqrt)** |                                                    |





### tan

原址：[https://zh.cppreference.com/w/c/numeric/math/tan](https://zh.cppreference.com/w/c/numeric/math/tan)

作用：计算正切（{\small\tan{x} }{\small\tan{x} }tan(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       tanf( float arg );// (1)(C99 起)
double      tan( double arg );// (2)
long double tanl( long double arg );// (3)(C99 起)
_Decimal32  tand32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  tand64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 tand128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define tan( arg )// (7)(C99 起)
```

1-6) 计算 `arg`（以弧度度量）的正切。

7） 泛型宏：若实参拥有 `long double` 类型，则调用 (3)（`tanl`）。否则，若实参拥有整数类型或 `double` 类型，则调用 (2)（`tan`）。否则调用 (1)（`tanf`）。若实参为复数，则宏调用对应的复数函数（[ctanf](https://zh.cppreference.com/w/c/numeric/complex/ctan)、[ctan](https://zh.cppreference.com/w/c/numeric/complex/ctan)、[ctanl](https://zh.cppreference.com/w/c/numeric/complex/ctan)）。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| arg  | -    | 以弧度表示角的浮点数 |
| ---- | ---- | -------------------- |
|      |      |                      |

**返回值**

​	若不出现错误，则返回 `arg` 的正切（*tan(arg)*）。

​	若 `arg` 的绝对值很大，则结果可能有较少或无有效数字。 (C99 前)

​	若出现定义域错误，则返回实现定义值（受支持平台为 NaN）。

​	若发生下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算数（IEC 60559），则

- 若实参为 ±0，则返回不修改的参数
- 若实参为 ±∞，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若实参为 NaN，则返回 NaN

**注意**

​	实参为无限大的情况，在 C 中未被指定为定义域错误，但它被定义为 [POSIX 中的定义域错误](http://pubs.opengroup.org/onlinepubs/9699919799/functions/tan.html)。

​	函数在 *π(1/2 + n)* 有数学上的极点；然而无常用浮点数表示能准确表示 `π/2`，故而没有值使得极点错误出现。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
int main(void)
{
    const double pi = acos(-1);
 
    // 典型用法
    printf("tan(pi*1/4) = %+f\n", tan(pi * 1 / 4)); //   45°
    printf("tan(pi*3/4) = %+f\n", tan(pi * 3 / 4)); //  135°
    printf("tan(pi*5/4) = %+f\n", tan(pi * 5 / 4)); // -135°
    printf("tan(pi*7/4) = %+f\n", tan(pi * 7 / 4)); //  -45°
 
    // 特殊值
    printf("tan(+0) = %f\n", tan(0.0));
    printf("tan(-0) = %f\n", tan(-0.0));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("tan(INFINITY) = %f\n", tan(INFINITY));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
tan  (pi/4) = +1.000000
tan(3*pi/4) = -1.000000
tan(5*pi/4) = +1.000000
tan(7*pi/4) = -1.000000
tan(+0) = 0.000000
tan(-0) = -0.000000
tan(INFINITY) = -nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.7 The tan functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.7 The tan functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.7 The tan functions （第 175 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.7 The tan functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.7 The tan functions （第 240 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.7 The tan functions （第 519 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.7 The tan functions （第 220 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.7 The tan functions （第 457 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.7 The tan function

**参阅**

| [sin <br />sinf (C99)<br />sinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sin) | 计算正弦（sinxsin⁡x） (函数)         |
| ------------------------------------------------------------ | ----------------------------------- |
| [cos <br />cosf (C99)<br />cosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cos) | 计算余弦（cosxcos⁡x） (函数)         |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡x） (函数) |
| [ctan (C99)<br />ctanf (C99)<br />ctanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctan) | 计算复数正切 (函数)                 |
| **tan** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/tan)** |                                     |





### tanf

原址：[https://zh.cppreference.com/w/c/numeric/math/tan](https://zh.cppreference.com/w/c/numeric/math/tan)

作用：计算正切（{\small\tan{x} }{\small\tan{x} }tan(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       tanf( float arg );// (1)(C99 起)
double      tan( double arg );// (2)
long double tanl( long double arg );// (3)(C99 起)
_Decimal32  tand32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  tand64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 tand128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define tan( arg )// (7)(C99 起)
```

1-6) 计算 `arg`（以弧度度量）的正切。

7） 泛型宏：若实参拥有 `long double` 类型，则调用 (3)（`tanl`）。否则，若实参拥有整数类型或 `double` 类型，则调用 (2)（`tan`）。否则调用 (1)（`tanf`）。若实参为复数，则宏调用对应的复数函数（[ctanf](https://zh.cppreference.com/w/c/numeric/complex/ctan)、[ctan](https://zh.cppreference.com/w/c/numeric/complex/ctan)、[ctanl](https://zh.cppreference.com/w/c/numeric/complex/ctan)）。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| arg  | -    | 以弧度表示角的浮点数 |
| ---- | ---- | -------------------- |
|      |      |                      |

**返回值**

​	若不出现错误，则返回 `arg` 的正切（*tan(arg)*）。

​	若 `arg` 的绝对值很大，则结果可能有较少或无有效数字。 (C99 前)

​	若出现定义域错误，则返回实现定义值（受支持平台为 NaN）。

​	若发生下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算数（IEC 60559），则

- 若实参为 ±0，则返回不修改的参数
- 若实参为 ±∞，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若实参为 NaN，则返回 NaN

**注意**

​	实参为无限大的情况，在 C 中未被指定为定义域错误，但它被定义为 [POSIX 中的定义域错误](http://pubs.opengroup.org/onlinepubs/9699919799/functions/tan.html)。

​	函数在 *π(1/2 + n)* 有数学上的极点；然而无常用浮点数表示能准确表示 `π/2`，故而没有值使得极点错误出现。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
int main(void)
{
    const double pi = acos(-1);
 
    // 典型用法
    printf("tan(pi*1/4) = %+f\n", tan(pi * 1 / 4)); //   45°
    printf("tan(pi*3/4) = %+f\n", tan(pi * 3 / 4)); //  135°
    printf("tan(pi*5/4) = %+f\n", tan(pi * 5 / 4)); // -135°
    printf("tan(pi*7/4) = %+f\n", tan(pi * 7 / 4)); //  -45°
 
    // 特殊值
    printf("tan(+0) = %f\n", tan(0.0));
    printf("tan(-0) = %f\n", tan(-0.0));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("tan(INFINITY) = %f\n", tan(INFINITY));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
tan  (pi/4) = +1.000000
tan(3*pi/4) = -1.000000
tan(5*pi/4) = +1.000000
tan(7*pi/4) = -1.000000
tan(+0) = 0.000000
tan(-0) = -0.000000
tan(INFINITY) = -nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.7 The tan functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.7 The tan functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.7 The tan functions （第 175 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.7 The tan functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.7 The tan functions （第 240 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.7 The tan functions （第 519 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.7 The tan functions （第 220 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.7 The tan functions （第 457 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.7 The tan function

**参阅**

| [sin <br />sinf (C99)<br />sinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sin) | 计算正弦（sinxsin⁡x） (函数)         |
| ------------------------------------------------------------ | ----------------------------------- |
| [cos <br />cosf (C99)<br />cosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cos) | 计算余弦（cosxcos⁡x） (函数)         |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡x） (函数) |
| [ctan (C99)<br />ctanf (C99)<br />ctanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctan) | 计算复数正切 (函数)                 |
| **tan** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/tan)** |                                     |





### tanh

原址：[https://zh.cppreference.com/w/c/numeric/math/tanh](https://zh.cppreference.com/w/c/numeric/math/tanh)

作用：计算双曲正切（{\small\tanh{x} }{\small\tanh{x} }tanh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       tanhf( float arg );// (1)(C99 起)
double      tanh( double arg );// (2)
long double tanhl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define tanh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的双曲正切。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `tanhl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `tanh`。否则调用 `tanhf` 若实参为复数，则宏调用对应的复数函数（`[ctanhf](http://zh.cppreference.com/w/c/numeric/complex/ctanh)`、`[ctanh](http://zh.cppreference.com/w/c/numeric/complex/ctanh)`、`[ctanhl](http://zh.cppreference.com/w/c/numeric/complex/ctanh)`）。

**参数**

| arg  | -    | 表示双曲角的浮点数 |
| ---- | ---- | ------------------ |
|      |      |                    |

**返回值**

若不出现错误，则返回 `arg` 的双曲正切（*tanh(arg)* 或 

| earg -e-arg |
| ----------- |
| earg +e-arg |

）。

​	若发生下溢所致的错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 ±0
- 若参数为 ±∞，则返回 ±1
- 若参数为 NaN，则返回 NaN

**注解**

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/tanh.html)在下溢的情况中，返回不修改的 `arg`，而且若不支持这么做，则返回不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 和 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的实现定义值。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("tanh(1) = %f\ntanh(-1) = %f\n", tanh(1), tanh(-1));
    printf("tanh(0.1)*sinh(0.2)-cosh(0.2) = %f\n", tanh(0.1) * sinh(0.2) - cosh(0.2));
    // 特殊值
    printf("tanh(+0) = %f\ntanh(-0) = %f\n", tanh(0.0), tanh(-0.0));
}
```

​	输出：

```txt
tanh(1) = 0.761594
tanh(-1) = -0.761594
tanh(0.1)*sinh(0.2)-cosh(0.2) = -1.000000
tanh(+0) = 0.000000
tanh(-0) = -0.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.6 The tanh functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.6 The tanh functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.6 The tanh functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.6 The tanh functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.6 The tanh functions （第 242 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.6 The tanh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.6 The tanh functions （第 222-223 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.6 The tanh functions （第 457 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.3.3 The tanh function

**参阅**

| [sinh <br />sinhf (C99)<br />sinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sinh) | 计算双曲正弦（sinhxsinh⁡x） (函数)       |
| ------------------------------------------------------------ | --------------------------------------- |
| [cosh <br />coshf (C99)<br />coshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cosh) | 计算双曲余弦（coshxcosh⁡x） (函数)       |
| [atanh (C99)<br />atanhf (C99)<br />atanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atanh) | 计算反双曲正切（artanhxartanh⁡x） (函数) |
| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)                 |
| **tanh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/tanh)** |                                         |





### tanhf

原址：[https://zh.cppreference.com/w/c/numeric/math/tanh](https://zh.cppreference.com/w/c/numeric/math/tanh)

作用：计算双曲正切（{\small\tanh{x} }{\small\tanh{x} }tanh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       tanhf( float arg );// (1)(C99 起)
double      tanh( double arg );// (2)
long double tanhl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define tanh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的双曲正切。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `tanhl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `tanh`。否则调用 `tanhf` 若实参为复数，则宏调用对应的复数函数（`[ctanhf](http://zh.cppreference.com/w/c/numeric/complex/ctanh)`、`[ctanh](http://zh.cppreference.com/w/c/numeric/complex/ctanh)`、`[ctanhl](http://zh.cppreference.com/w/c/numeric/complex/ctanh)`）。

**参数**

| arg  | -    | 表示双曲角的浮点数 |
| ---- | ---- | ------------------ |
|      |      |                    |

**返回值**

若不出现错误，则返回 `arg` 的双曲正切（*tanh(arg)* 或 

| earg -e-arg |
| ----------- |
| earg +e-arg |

）。

​	若发生下溢所致的错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 ±0
- 若参数为 ±∞，则返回 ±1
- 若参数为 NaN，则返回 NaN

**注解**

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/tanh.html)在下溢的情况中，返回不修改的 `arg`，而且若不支持这么做，则返回不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 和 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的实现定义值。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("tanh(1) = %f\ntanh(-1) = %f\n", tanh(1), tanh(-1));
    printf("tanh(0.1)*sinh(0.2)-cosh(0.2) = %f\n", tanh(0.1) * sinh(0.2) - cosh(0.2));
    // 特殊值
    printf("tanh(+0) = %f\ntanh(-0) = %f\n", tanh(0.0), tanh(-0.0));
}
```

​	输出：

```txt
tanh(1) = 0.761594
tanh(-1) = -0.761594
tanh(0.1)*sinh(0.2)-cosh(0.2) = -1.000000
tanh(+0) = 0.000000
tanh(-0) = -0.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.6 The tanh functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.6 The tanh functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.6 The tanh functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.6 The tanh functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.6 The tanh functions （第 242 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.6 The tanh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.6 The tanh functions （第 222-223 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.6 The tanh functions （第 457 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.3.3 The tanh function

**参阅**

| [sinh <br />sinhf (C99)<br />sinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sinh) | 计算双曲正弦（sinhxsinh⁡x） (函数)       |
| ------------------------------------------------------------ | --------------------------------------- |
| [cosh <br />coshf (C99)<br />coshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cosh) | 计算双曲余弦（coshxcosh⁡x） (函数)       |
| [atanh (C99)<br />atanhf (C99)<br />atanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atanh) | 计算反双曲正切（artanhxartanh⁡x） (函数) |
| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)                 |
| **tanh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/tanh)** |                                         |





### tanhl

原址：[https://zh.cppreference.com/w/c/numeric/math/tanh](https://zh.cppreference.com/w/c/numeric/math/tanh)

作用：计算双曲正切（{\small\tanh{x} }{\small\tanh{x} }tanh(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       tanhf( float arg );// (1)(C99 起)
double      tanh( double arg );// (2)
long double tanhl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define tanh( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的双曲正切。

4） 泛型宏：若实参拥有 `long double` 类型，则调用 `tanhl`。否则，若实参拥有整数类型或 `double` 类型，则调用 `tanh`。否则调用 `tanhf` 若实参为复数，则宏调用对应的复数函数（`[ctanhf](http://zh.cppreference.com/w/c/numeric/complex/ctanh)`、`[ctanh](http://zh.cppreference.com/w/c/numeric/complex/ctanh)`、`[ctanhl](http://zh.cppreference.com/w/c/numeric/complex/ctanh)`）。

**参数**

| arg  | -    | 表示双曲角的浮点数 |
| ---- | ---- | ------------------ |
|      |      |                    |

**返回值**

若不出现错误，则返回 `arg` 的双曲正切（*tanh(arg)* 或 

| earg -e-arg |
| ----------- |
| earg +e-arg |

）。

​	若发生下溢所致的错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 ±0
- 若参数为 ±∞，则返回 ±1
- 若参数为 NaN，则返回 NaN

**注解**

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/tanh.html)在下溢的情况中，返回不修改的 `arg`，而且若不支持这么做，则返回不大于 [DBL_MIN](https://zh.cppreference.com/w/c/types/limits)、[FLT_MIN](https://zh.cppreference.com/w/c/types/limits) 和 [LDBL_MIN](https://zh.cppreference.com/w/c/types/limits) 的实现定义值。

**示例**

```c
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("tanh(1) = %f\ntanh(-1) = %f\n", tanh(1), tanh(-1));
    printf("tanh(0.1)*sinh(0.2)-cosh(0.2) = %f\n", tanh(0.1) * sinh(0.2) - cosh(0.2));
    // 特殊值
    printf("tanh(+0) = %f\ntanh(-0) = %f\n", tanh(0.0), tanh(-0.0));
}
```

​	输出：

```txt
tanh(1) = 0.761594
tanh(-1) = -0.761594
tanh(0.1)*sinh(0.2)-cosh(0.2) = -1.000000
tanh(+0) = 0.000000
tanh(-0) = -0.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.5.6 The tanh functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.6 The tanh functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.5.6 The tanh functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.2.6 The tanh functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.5.6 The tanh functions （第 242 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.2.6 The tanh functions （第 520 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.5.6 The tanh functions （第 222-223 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.2.6 The tanh functions （第 457 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.3.3 The tanh function

**参阅**

| [sinh <br />sinhf (C99)<br />sinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sinh) | 计算双曲正弦（sinhxsinh⁡x） (函数)       |
| ------------------------------------------------------------ | --------------------------------------- |
| [cosh <br />coshf (C99)<br />coshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cosh) | 计算双曲余弦（coshxcosh⁡x） (函数)       |
| [atanh (C99)<br />atanhf (C99)<br />atanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atanh) | 计算反双曲正切（artanhxartanh⁡x） (函数) |
| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)                 |
| **tanh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/tanh)** |                                         |





### tanl

原址：[https://zh.cppreference.com/w/c/numeric/math/tan](https://zh.cppreference.com/w/c/numeric/math/tan)

作用：计算正切（{\small\tan{x} }{\small\tan{x} }tan(x)）   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       tanf( float arg );// (1)(C99 起)
double      tan( double arg );// (2)
long double tanl( long double arg );// (3)(C99 起)
_Decimal32  tand32( _Decimal32 arg );// (4)(C23 起)
_Decimal64  tand64( _Decimal64 arg );// (5)(C23 起)
_Decimal128 tand128( _Decimal128 arg );// (6)(C23 起)
// 在标头 <tgmath.h> 定义
#define tan( arg )// (7)(C99 起)
```

1-6) 计算 `arg`（以弧度度量）的正切。

7） 泛型宏：若实参拥有 `long double` 类型，则调用 (3)（`tanl`）。否则，若实参拥有整数类型或 `double` 类型，则调用 (2)（`tan`）。否则调用 (1)（`tanf`）。若实参为复数，则宏调用对应的复数函数（[ctanf](https://zh.cppreference.com/w/c/numeric/complex/ctan)、[ctan](https://zh.cppreference.com/w/c/numeric/complex/ctan)、[ctanl](https://zh.cppreference.com/w/c/numeric/complex/ctan)）。

​	仅当实现预定义了 `__STDC_IEC_60559_DFP__`（即实现支持十进制浮点数）时，声明函数 (4-6)。 (C23 起)

**参数**

| arg  | -    | 以弧度表示角的浮点数 |
| ---- | ---- | -------------------- |
|      |      |                      |

**返回值**

​	若不出现错误，则返回 `arg` 的正切（*tan(arg)*）。

​	若 `arg` 的绝对值很大，则结果可能有较少或无有效数字。 (C99 前)

​	若出现定义域错误，则返回实现定义值（受支持平台为 NaN）。

​	若发生下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算数（IEC 60559），则

- 若实参为 ±0，则返回不修改的参数
- 若实参为 ±∞，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若实参为 NaN，则返回 NaN

**注意**

​	实参为无限大的情况，在 C 中未被指定为定义域错误，但它被定义为 [POSIX 中的定义域错误](http://pubs.opengroup.org/onlinepubs/9699919799/functions/tan.html)。

​	函数在 *π(1/2 + n)* 有数学上的极点；然而无常用浮点数表示能准确表示 `π/2`，故而没有值使得极点错误出现。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <math.h>
#include <stdio.h>
 
#ifndef __GNUC__
#pragma STDC FENV_ACCESS ON
#endif
 
int main(void)
{
    const double pi = acos(-1);
 
    // 典型用法
    printf("tan(pi*1/4) = %+f\n", tan(pi * 1 / 4)); //   45°
    printf("tan(pi*3/4) = %+f\n", tan(pi * 3 / 4)); //  135°
    printf("tan(pi*5/4) = %+f\n", tan(pi * 5 / 4)); // -135°
    printf("tan(pi*7/4) = %+f\n", tan(pi * 7 / 4)); //  -45°
 
    // 特殊值
    printf("tan(+0) = %f\n", tan(0.0));
    printf("tan(-0) = %f\n", tan(-0.0));
 
    // 错误处理
    feclearexcept(FE_ALL_EXCEPT);
    printf("tan(INFINITY) = %f\n", tan(INFINITY));
    if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
tan  (pi/4) = +1.000000
tan(3*pi/4) = -1.000000
tan(5*pi/4) = +1.000000
tan(7*pi/4) = -1.000000
tan(+0) = 0.000000
tan(-0) = -0.000000
tan(INFINITY) = -nan
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.4.7 The tan functions （第 TBD 页）

  - 7.25 Type-generic math <tgmath.h> （第 TBD 页）

  - F.10.1.7 The tan functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.4.7 The tan functions （第 175 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - F.10.1.7 The tan functions （第 378 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.4.7 The tan functions （第 240 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.1.7 The tan functions （第 519 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.4.7 The tan functions （第 220 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.1.7 The tan functions （第 457 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.5.2.7 The tan function

**参阅**

| [sin <br />sinf (C99)<br />sinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sin) | 计算正弦（sinxsin⁡x） (函数)         |
| ------------------------------------------------------------ | ----------------------------------- |
| [cos <br />cosf (C99)<br />cosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cos) | 计算余弦（cosxcos⁡x） (函数)         |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡x） (函数) |
| [ctan (C99)<br />ctanf (C99)<br />ctanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctan) | 计算复数正切 (函数)                 |
| **tan** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/tan)** |                                     |





### tgamma

原址：[https://zh.cppreference.com/w/c/numeric/math/tgamma](https://zh.cppreference.com/w/c/numeric/math/tgamma)

作用：计算伽马函数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       tgammaf( float arg );// (1)(C99 起)
double      tgamma( double arg );// (2)(C99 起)
long double tgammal( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define tgamma( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的[伽马函数](https://en.wikipedia.org/wiki/Gamma_function)。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `tgammal`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `tgamma`。否则调用 `tgammaf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的 Γ 函数值，即 Γ(arg)=∫∞0targ−1e−tdtΓ(arg)=∫0∞targ−1e−tdt。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现极点错误，则返回 `[HUGE_VAL](http://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)`、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误

​	若 `arg` 为零或为小于零的整数，则可能出现极点或定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 ±∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若参数为负整数，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若参数为 -∞，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若参数为 +∞，则返回 +∞
- 若参数为 NaN，则返回 NaN

**注解**

​	若 `arg` 为自然数，则 `tgamma(arg)` 为 `arg-1` 的阶乘。许多实现若参数是足够小的整数，则计算准确的整数域阶乘。

​	对于 IEEE 兼容的 `double` 类型，若 `0 < x < 1/DBL_MAX` 或 `x > 171.7` 则发生上溢。

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/tgamma.html)若实参为零则出现极点错误，但在实参为负整数时出现定义域错误。它亦指定在将来，对于负整数，定义域错误可能被替换成浮点数错误（这些情况下返回值将从 NaN 更改为 ±∞）。

​	多数实现中有名为 `gamma` 的非标准函数，但其定义不一致。例如，`gamma` 的 glibc 和 4.2BSD 版本执行 `lgamma`，但 `gamma` 的 4.4BSD 版本执行 `tgamma`。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("tgamma(10) = %f, 9!=%f\n", tgamma(10), 2 * 3 * 4 * 5 * 6 * 7 * 8 * 9.0);
    printf("tgamma(0.5) = %f, sqrt(pi) = %f\n", sqrt(acos(-1)), tgamma(0.5));
 
    // 特殊值
    printf("tgamma(+Inf) = %f\n", tgamma(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("tgamma(-1) = %f\n", tgamma(-1));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    else
        if (errno == EDOM)   perror("    errno == EDOM");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
    else if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
tgamma(10) = 362880.000000, 9!=362880.000000
tgamma(0.5) = 1.772454, sqrt(pi) = 1.772454
tgamma(+Inf) = inf
tgamma(-1) = nan
    errno == EDOM: Numerical argument out of domain
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.8.4 The tgamma functions （第 250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.4 The tgamma functions （第 525 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.8.4 The tgamma functions （第 250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.4 The tgamma functions （第 525 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.8.4 The tgamma functions （第 250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.4 The tgamma functions （第 525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.8.4 The tgamma functions （第 231 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.5.4 The tgamma functions （第 462 页）

**参阅**

| [lgamma (C99)<br />lgammaf (C99)<br />lgammal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/lgamma) | 计算伽马函数的自然对数（底为 *e*） (函数) |
| ------------------------------------------------------------ | ----------------------------------------- |
| **tgamma** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/tgamma)** |                                           |

**外部链接**

​	[Weisstein, Eric W. “伽马函数”](https://mathworld.wolfram.com/GammaFunction.html)来自 MathWorld--A Wolfram Web Resource。





### tgammaf

原址：[https://zh.cppreference.com/w/c/numeric/math/tgamma](https://zh.cppreference.com/w/c/numeric/math/tgamma)

作用：计算伽马函数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       tgammaf( float arg );// (1)(C99 起)
double      tgamma( double arg );// (2)(C99 起)
long double tgammal( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define tgamma( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的[伽马函数](https://en.wikipedia.org/wiki/Gamma_function)。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `tgammal`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `tgamma`。否则调用 `tgammaf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的 Γ 函数值，即 Γ(arg)=∫∞0targ−1e−tdtΓ(arg)=∫0∞targ−1e−tdt。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现极点错误，则返回 `[HUGE_VAL](http://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)`、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误

​	若 `arg` 为零或为小于零的整数，则可能出现极点或定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 ±∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若参数为负整数，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若参数为 -∞，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若参数为 +∞，则返回 +∞
- 若参数为 NaN，则返回 NaN

**注解**

​	若 `arg` 为自然数，则 `tgamma(arg)` 为 `arg-1` 的阶乘。许多实现若参数是足够小的整数，则计算准确的整数域阶乘。

​	对于 IEEE 兼容的 `double` 类型，若 `0 < x < 1/DBL_MAX` 或 `x > 171.7` 则发生上溢。

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/tgamma.html)若实参为零则出现极点错误，但在实参为负整数时出现定义域错误。它亦指定在将来，对于负整数，定义域错误可能被替换成浮点数错误（这些情况下返回值将从 NaN 更改为 ±∞）。

​	多数实现中有名为 `gamma` 的非标准函数，但其定义不一致。例如，`gamma` 的 glibc 和 4.2BSD 版本执行 `lgamma`，但 `gamma` 的 4.4BSD 版本执行 `tgamma`。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("tgamma(10) = %f, 9!=%f\n", tgamma(10), 2 * 3 * 4 * 5 * 6 * 7 * 8 * 9.0);
    printf("tgamma(0.5) = %f, sqrt(pi) = %f\n", sqrt(acos(-1)), tgamma(0.5));
 
    // 特殊值
    printf("tgamma(+Inf) = %f\n", tgamma(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("tgamma(-1) = %f\n", tgamma(-1));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    else
        if (errno == EDOM)   perror("    errno == EDOM");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
    else if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
tgamma(10) = 362880.000000, 9!=362880.000000
tgamma(0.5) = 1.772454, sqrt(pi) = 1.772454
tgamma(+Inf) = inf
tgamma(-1) = nan
    errno == EDOM: Numerical argument out of domain
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.8.4 The tgamma functions （第 250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.4 The tgamma functions （第 525 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.8.4 The tgamma functions （第 250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.4 The tgamma functions （第 525 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.8.4 The tgamma functions （第 250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.4 The tgamma functions （第 525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.8.4 The tgamma functions （第 231 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.5.4 The tgamma functions （第 462 页）

**参阅**

| [lgamma (C99)<br />lgammaf (C99)<br />lgammal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/lgamma) | 计算伽马函数的自然对数（底为 *e*） (函数) |
| ------------------------------------------------------------ | ----------------------------------------- |
| **tgamma** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/tgamma)** |                                           |

**外部链接**

​	[Weisstein, Eric W. “伽马函数”](https://mathworld.wolfram.com/GammaFunction.html)来自 MathWorld--A Wolfram Web Resource。





### tgammal

原址：[https://zh.cppreference.com/w/c/numeric/math/tgamma](https://zh.cppreference.com/w/c/numeric/math/tgamma)

作用：计算伽马函数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       tgammaf( float arg );// (1)(C99 起)
double      tgamma( double arg );// (2)(C99 起)
long double tgammal( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define tgamma( arg )// (4)(C99 起)
```

1-3) 计算 `arg` 的[伽马函数](https://en.wikipedia.org/wiki/Gamma_function)。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `tgammal`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `tgamma`。否则调用 `tgammaf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `arg` 的 Γ 函数值，即 Γ(arg)=∫∞0targ−1e−tdtΓ(arg)=∫0∞targ−1e−tdt。

​	若出现定义域错误，则返回实现定义值（受支持平台上为 NaN）。

​	若出现极点错误，则返回 `[HUGE_VAL](http://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)`、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现上溢所致的值域错误，则返回 [±HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、`±HUGE_VALF` 或 `±HUGE_VALL`。

​	若出现下溢所致的值域错误，则返回（舍入后的）正确结果。

**错误处理**

​	报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误

​	若 `arg` 为零或为小于零的整数，则可能出现极点或定义域错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 若参数为 ±0，则返回 ±∞ 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若参数为负整数，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若参数为 -∞，则返回 NaN 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若参数为 +∞，则返回 +∞
- 若参数为 NaN，则返回 NaN

**注解**

​	若 `arg` 为自然数，则 `tgamma(arg)` 为 `arg-1` 的阶乘。许多实现若参数是足够小的整数，则计算准确的整数域阶乘。

​	对于 IEEE 兼容的 `double` 类型，若 `0 < x < 1/DBL_MAX` 或 `x > 171.7` 则发生上溢。

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/tgamma.html)若实参为零则出现极点错误，但在实参为负整数时出现定义域错误。它亦指定在将来，对于负整数，定义域错误可能被替换成浮点数错误（这些情况下返回值将从 NaN 更改为 ±∞）。

​	多数实现中有名为 `gamma` 的非标准函数，但其定义不一致。例如，`gamma` 的 glibc 和 4.2BSD 版本执行 `lgamma`，但 `gamma` 的 4.4BSD 版本执行 `tgamma`。

**示例**

```c
#include <errno.h>
#include <fenv.h>
#include <float.h>
#include <math.h>
#include <stdio.h>
// #pragma STDC FENV_ACCESS ON
 
int main(void)
{
    printf("tgamma(10) = %f, 9!=%f\n", tgamma(10), 2 * 3 * 4 * 5 * 6 * 7 * 8 * 9.0);
    printf("tgamma(0.5) = %f, sqrt(pi) = %f\n", sqrt(acos(-1)), tgamma(0.5));
 
    // 特殊值
    printf("tgamma(+Inf) = %f\n", tgamma(INFINITY));
 
    // 错误处理
    errno = 0; feclearexcept(FE_ALL_EXCEPT);
    printf("tgamma(-1) = %f\n", tgamma(-1));
    if (errno == ERANGE)
        perror("    errno == ERANGE");
    else
        if (errno == EDOM)   perror("    errno == EDOM");
    if (fetestexcept(FE_DIVBYZERO))
        puts("    FE_DIVBYZERO raised");
    else if (fetestexcept(FE_INVALID))
        puts("    FE_INVALID raised");
}
```

​	可能的输出：

```txt
tgamma(10) = 362880.000000, 9!=362880.000000
tgamma(0.5) = 1.772454, sqrt(pi) = 1.772454
tgamma(+Inf) = inf
tgamma(-1) = nan
    errno == EDOM: Numerical argument out of domain
    FE_INVALID raised
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.12.8.4 The tgamma functions （第 250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.4 The tgamma functions （第 525 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.12.8.4 The tgamma functions （第 250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.4 The tgamma functions （第 525 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.8.4 The tgamma functions （第 250 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.5.4 The tgamma functions （第 525 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.8.4 The tgamma functions （第 231 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.5.4 The tgamma functions （第 462 页）

**参阅**

| [lgamma (C99)<br />lgammaf (C99)<br />lgammal (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/lgamma) | 计算伽马函数的自然对数（底为 *e*） (函数) |
| ------------------------------------------------------------ | ----------------------------------------- |
| **tgamma** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/tgamma)** |                                           |

**外部链接**

​	[Weisstein, Eric W. “伽马函数”](https://mathworld.wolfram.com/GammaFunction.html)来自 MathWorld--A Wolfram Web Resource。





### trunc

原址：[https://zh.cppreference.com/w/c/numeric/math/trunc](https://zh.cppreference.com/w/c/numeric/math/trunc)

作用：取整到绝对值不大于给定值的最接近整数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       truncf( float arg );// (1)(C99 起)
double      trunc( double arg );// (2)(C99 起)
long double truncl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define trunc( arg )// (4)(C99 起)
```

1-3) 计算绝对值不大于 `arg` 的最接近整数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `truncl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `trunc`。否则，调用 `truncf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不发生错误，则返回绝对值不大于 `arg` 的最接近整数（换言之，将 `arg` 向零舍入）。

返回值

![math-trunc.svg](https://upload.cppreference.com/mwiki/images/7/70/math-trunc.svg)

参数

**错误处理**

​	报告 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
- 若 `arg` 为 ±∞，则返回未修改的实参。
- 若 `arg` 为 ±0，则返回未修改的实参。
- 若 arg 为 NaN，则返回 NaN

**注意**

​	截断非整数有限值时可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数均为准确的整数，故此函数自身决不上溢；然而存储结果于整数对象时，结果可以溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	从浮点数到整数类型的隐式转换始终向零舍入，但它被限制于能表示成目标类型的值。

**示例**

```c
#include <math.h>
#include <stdio.h>
int main(void)
{
    printf("trunc(+2.7) = %+.1f\n", trunc(2.7));
    printf("trunc(-2.7) = %+.1f\n", trunc(-2.7));
    printf("trunc(-0.0) = %+.1f\n", trunc(-0.0));
    printf("trunc(-Inf) = %+f\n",   trunc(-INFINITY));
}
```

​	可能的输出：

```txt
trunc(+2.7) = +2.0
trunc(-2.7) = -2.0
trunc(-0.0) = -0.0
trunc(-Inf) = -inf
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.8 The trunc functions （第 253-254 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.8 The trunc functions （第 528 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.8 The trunc functions （第 234 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.8 The trunc functions （第 464 页）

**参阅**

| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)                         |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)                         |
| [round (C99)<br />roundf (C99)<br />roundl (C99)<br />lround (C99)<br />lroundf (C99)<br />lroundl (C99)<br />llround (C99)<br />llroundf (C99)<br />llroundl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/round) | 取整到最接近的整数，在相邻整数正中间时取远离零的数 (函数) |
| **trunc** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/trunc)** |                                                           |





### truncf

原址：[https://zh.cppreference.com/w/c/numeric/math/trunc](https://zh.cppreference.com/w/c/numeric/math/trunc)

作用：取整到绝对值不大于给定值的最接近整数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       truncf( float arg );// (1)(C99 起)
double      trunc( double arg );// (2)(C99 起)
long double truncl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define trunc( arg )// (4)(C99 起)
```

1-3) 计算绝对值不大于 `arg` 的最接近整数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `truncl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `trunc`。否则，调用 `truncf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不发生错误，则返回绝对值不大于 `arg` 的最接近整数（换言之，将 `arg` 向零舍入）。

返回值

![math-trunc.svg](https://upload.cppreference.com/mwiki/images/7/70/math-trunc.svg)

参数

**错误处理**

​	报告 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
- 若 `arg` 为 ±∞，则返回未修改的实参。
- 若 `arg` 为 ±0，则返回未修改的实参。
- 若 arg 为 NaN，则返回 NaN

**注意**

​	截断非整数有限值时可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数均为准确的整数，故此函数自身决不上溢；然而存储结果于整数对象时，结果可以溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	从浮点数到整数类型的隐式转换始终向零舍入，但它被限制于能表示成目标类型的值。

**示例**

```c
#include <math.h>
#include <stdio.h>
int main(void)
{
    printf("trunc(+2.7) = %+.1f\n", trunc(2.7));
    printf("trunc(-2.7) = %+.1f\n", trunc(-2.7));
    printf("trunc(-0.0) = %+.1f\n", trunc(-0.0));
    printf("trunc(-Inf) = %+f\n",   trunc(-INFINITY));
}
```

​	可能的输出：

```txt
trunc(+2.7) = +2.0
trunc(-2.7) = -2.0
trunc(-0.0) = -0.0
trunc(-Inf) = -inf
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.8 The trunc functions （第 253-254 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.8 The trunc functions （第 528 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.8 The trunc functions （第 234 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.8 The trunc functions （第 464 页）

**参阅**

| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)                         |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)                         |
| [round (C99)<br />roundf (C99)<br />roundl (C99)<br />lround (C99)<br />lroundf (C99)<br />lroundl (C99)<br />llround (C99)<br />llroundf (C99)<br />llroundl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/round) | 取整到最接近的整数，在相邻整数正中间时取远离零的数 (函数) |
| **trunc** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/trunc)** |                                                           |





### truncl

原址：[https://zh.cppreference.com/w/c/numeric/math/trunc](https://zh.cppreference.com/w/c/numeric/math/trunc)

作用：取整到绝对值不大于给定值的最接近整数   (函数)

备注：
```c
// 在标头 <math.h> 定义
float       truncf( float arg );// (1)(C99 起)
double      trunc( double arg );// (2)(C99 起)
long double truncl( long double arg );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define trunc( arg )// (4)(C99 起)
```

1-3) 计算绝对值不大于 `arg` 的最接近整数。

4） 泛型宏：若 `arg` 拥有 `long double` 类型，则调用 `truncl`。否则，若 `arg` 拥有整数类型或 `double` 类型，则调用 `trunc`。否则，调用 `truncf`。

**参数**

| arg  | -    | 浮点数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不发生错误，则返回绝对值不大于 `arg` 的最接近整数（换言之，将 `arg` 向零舍入）。

返回值

![math-trunc.svg](https://upload.cppreference.com/mwiki/images/7/70/math-trunc.svg)

参数

**错误处理**

​	报告 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

​	若实现支持 IEEE 浮点数算术（IEC 60559），则

- 当前[舍入模式](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)无效。
- 若 `arg` 为 ±∞，则返回未修改的实参。
- 若 `arg` 为 ±0，则返回未修改的实参。
- 若 arg 为 NaN，则返回 NaN

**注意**

​	截断非整数有限值时可以（但不要求）引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。

​	所有标准浮点数格式中，最大可表示浮点数均为准确的整数，故此函数自身决不上溢；然而存储结果于整数对象时，结果可以溢出任何整数类型（包含 [intmax_t](https://zh.cppreference.com/w/c/types/integer)）。

​	从浮点数到整数类型的隐式转换始终向零舍入，但它被限制于能表示成目标类型的值。

**示例**

```c
#include <math.h>
#include <stdio.h>
int main(void)
{
    printf("trunc(+2.7) = %+.1f\n", trunc(2.7));
    printf("trunc(-2.7) = %+.1f\n", trunc(-2.7));
    printf("trunc(-0.0) = %+.1f\n", trunc(-0.0));
    printf("trunc(-Inf) = %+f\n",   trunc(-INFINITY));
}
```

​	可能的输出：

```txt
trunc(+2.7) = +2.0
trunc(-2.7) = -2.0
trunc(-0.0) = -0.0
trunc(-Inf) = -inf
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.12.9.8 The trunc functions （第 253-254 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - F.10.6.8 The trunc functions （第 528 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.12.9.8 The trunc functions （第 234 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - F.9.6.8 The trunc functions （第 464 页）

**参阅**

| [floor <br />floorf (C99)<br />floorl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/floor) | 计算不大于给定值的最大整数 (函数)                         |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [ceil <br />ceilf (C99)<br />ceill (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/ceil) | 计算不小于给定值的最小整数 (函数)                         |
| [round (C99)<br />roundf (C99)<br />roundl (C99)<br />lround (C99)<br />lroundf (C99)<br />lroundl (C99)<br />llround (C99)<br />llroundf (C99)<br />llroundl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/round) | 取整到最接近的整数，在相邻整数正中间时取远离零的数 (函数) |
| **trunc** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/trunc)** |                                                           |





