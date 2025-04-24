
+++
title = "<complex.h> (C99)"
date = 2025-04-24T19:11:50+08:00
weight = 10
type = "docs"
description = "复数算术"
isCJKLanguage = true
draft = false

+++

## 类型




## 枚举




## 宏



### I

原址：[https://zh.cppreference.com/w/c/numeric/complex/I](https://zh.cppreference.com/w/c/numeric/complex/I)

作用：复数或虚数单位常量 i  (宏常量)

备注：
```c
// 在标头 <complex.h> 定义
#define I /* 未指明 */// (C99 起)
```

​	`I` 宏展开成 [_Complex_I](https://zh.cppreference.com/w/c/numeric/complex/Complex_I) 或 [_Imaginary_I](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I)。若实现不支持虚数类型，则该宏始终展开成 [_Complex_I](https://zh.cppreference.com/w/c/numeric/complex/Complex_I)。

​	程序可以取消定义，并在其后重定义宏 `I`。

**注意**

​	该宏名字不是 `i`，虽然这是数学上的虚数单位名称。因为 `i` 已经用于大量 C 程序中，例如作为循环变量。

​	宏 `I` 常用于组成复数，通过如 `x + y*I` 的表达式。 若 `I` 被定义成 [_Complex_I](https://zh.cppreference.com/w/c/numeric/complex/Complex_I)，则该表达式在 `y` 为 `-0.0` 时创建虚部为 `+0.0` 的值，这对拥有分支的复变函数有显著影响。宏 [CMPLX](https://zh.cppreference.com/w/c/numeric/complex/CMPLX) 提供精确构造复数的方法。

​	GCC 提供了一种不可移植的扩展，它允许通过在实数字面量后指定后缀 `i`：`1.0fi`、`1.0i` 及 `1.0li` 是 GNU C 中的虚数单位。C++14 起，类似的方式是标准 C++ 的一部分（`1.0if`、`1.0i` 及 `1.0il` 是 C++ 中的虚数单位）。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    printf("I = %.1f%+.1fi\n", creal(I), cimag(I));
 
    double complex z1 = I * I;     // 虚数单位平方
    printf("I * I = %.1f%+.1fi\n", creal(z1), cimag(z1));
 
    double complex z = 1.0 + 2.0*I; // 在 C11 前组成复数的通常途径
    printf("z = %.1f%+.1fi\n", creal(z), cimag(z));
}
```

​	输出：

```txt
I = 0.0+1.0i
I * I = -1.0+0.0i
z = 1.0+2.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.1/6 I （第 188 页）

  - G.6/1 I （第 537 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.1/4 I （第 170 页）

  - G.6/1 I （第 472 页）

**参阅**

| [_Imaginary_I (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I) | 虚数单位常量 i (宏常量)       |
| ------------------------------------------------------------ | ----------------------------- |
| [_Complex_I (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/Complex_I) | 复数单位常量 i (宏常量)       |
| [CMPLX (C11)<br />CMPLXF (C11)<br />CMPLXL (C11)<br />](https://zh.cppreference.com/w/c/numeric/complex/CMPLX) | 由实部和虚部构建复数 (宏函数) |
| **operator""i** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/operator""i)** |                               |





### _Complex_I

原址：[https://zh.cppreference.com/w/c/numeric/complex/Complex_I](https://zh.cppreference.com/w/c/numeric/complex/Complex_I)

作用：复数单位常量 i   (宏常量)

备注：
```c
// 在标头 <complex.h> 定义
#define _Complex_I /* 未指明 */// (C99 起)
```

​	`_Complex_I` 宏展开成类型 `const float _Complex` 的值，其值为虚数单位。

**注意**

​	可在 I 不可用，譬如程序已取消定义它时使用此宏。

​	与 [_Imaginary_I](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I) 及 [CMPLX](https://zh.cppreference.com/w/c/numeric/complex/CMPLX) 不同，用此宏构造复数会失去虚部的零的符号位。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
#undef I
#define J _Complex_I // 可用于重定义 I
 
int main(void)
{
    // 可用于构建复数
    double complex z = 1.0 + 2.0 * _Complex_I;
    printf("1.0 + 2.0 * _Complex_I = %.1f%+.1fi\n", creal(z), cimag(z));
 
    // 可能不会保留零的符号
    double complex z2 = 0.0 + -0.0 * _Complex_I;
    printf("0.0 + -0.0 * _Complex_I = %.1f%+.1fi\n", creal(z2), cimag(z2));
}
```

​	可能的输出：

```txt
1.0 + 2.0 * _Complex_I = 1.0+2.0i
0.0 + -0.0 * _Complex_I = 0.0+0.0i
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.3.1/4 _Complex_I （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.3.1/4 _Complex_I （第 136 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.1/4 _Complex_I （第 188 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.1/2 _Complex_I （第 170 页）

**参阅**

| [_Imaginary_I (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I) | 虚数单位常量 i (宏常量)       |
| ------------------------------------------------------------ | ----------------------------- |
| [I (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/I) | 复数或虚数单位常量 i (宏常量) |





### _Imaginary_I

原址：[https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I)

作用：虚数单位常量 i  (宏常量)

备注：
```c
// 在标头 <complex.h> 定义
#define _Imaginary_I /* 未指明 */// (C99 起)
```

​	`_Imaginary_I` 宏展开成类型 `const float _Imaginary` 的值，其值为虚数单位。

​	和 C 中的任何纯虚数支持一样，仅当支持虚数时才定义此宏。

推荐定义了 `__STDC_IEC_559_COMPLEX__` 的编译器支持虚数，但并不强制要求。POSIX 推荐检查是否定义宏 `_Imaginary_I` 以鉴别是否支持虚数。(C99 起)(C11 前)

​	若定义了 `__STDC_IEC_559_COMPLEX__`，则支持虚数。 (C11 起)

**注意**

​	此宏允许从其实部和虚部精确地构成复数，例如用 `(double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex))((double)x + _Imaginary_I * (double)y)`。此模式在 C11 中作为 `[CMPLX](http://zh.cppreference.com/w/c/numeric/complex/CMPLX)` 标准化。注意若使用了 `[_Complex_I](http://zh.cppreference.com/w/c/numeric/complex/Complex_I)`，则允许此表达式在虚数位置将负零转变成正零。

**示例**

```c
#include <stdio.h>
#include <complex.h>
#include <math.h>
 
int main(void)
{
    double complex z1 = 0.0 + INFINITY * _Imaginary_I;
    printf("z1 = %.1f%+.1fi\n", creal(z1), cimag(z1));
 
    double complex z2 = 0.0 + INFINITY * _Complex_I;
    printf("z2 = %.1f%+.1fi\n", creal(z2), cimag(z2));
}
```

​	输出：

```txt
z = 0.0-0.0i 
z2 = NaN+Infi
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.1/5 _Imaginary_I （第 188 页）

  - G.6/1 _Imaginary_I （第 537 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.1/3 _Imaginary_I （第 170 页）

  - G.6/1 _Imaginary_I （第 472 页）

**参阅**

| [_Complex_I (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/Complex_I) | 复数单位常量 i (宏常量)       |
| ------------------------------------------------------------ | ----------------------------- |
| [I (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/I) | 复数或虚数单位常量 i (宏常量) |





### __STDC_VERSION_COMPLEX_H__

原址：

作用：

备注：





### complex

原址：[https://zh.cppreference.com/w/c/numeric/complex/complex](https://zh.cppreference.com/w/c/numeric/complex/complex)

作用：复数类型宏  (关键词宏)

备注：
```c
// 在标头 <complex.h> 定义
#define complex _Complex// (C99 起)
```

​	此宏展开成用于标识[复数类型](https://zh.cppreference.com/w/c/language/arithmetic_types#.E5.A4.8D.E6.B5.AE.E7.82.B9.E7.B1.BB.E5.9E.8B)的类型指定符。

​	程序可以取消定义，随后也可以重定义 **complex** 宏。

**示例**

```c
#include <stdio.h>
#include <complex.h>
#include <math.h>
 
void print_complex(const char* note, complex z)
{
    printf("%s %f%+f*i\n", note, creal(z), cimag(z));
}
 
int main(void)
{
    double complex z = -1.0 + 2.0*I;
    print_complex("z  =", z);
    print_complex("z\u00B2 =", z * z);
    double complex z2 = ccos(2.0 * carg(z)) + csin(2.0 * carg(z))*I;
    print_complex("z\u00B2 =", cabs(z) * cabs(z) * z2);
}
```

​	输出：

```txt
z  = -1.000000+2.000000*i
z² = -3.000000-4.000000*i
z² = -3.000000-4.000000*i
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.3.1/4 complex （第 136 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.1/4 complex （第 188 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.1/2 complex （第 170 页）

**参阅**

| [imaginary (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/imaginary) | 虚数类型宏 (关键词宏) |
| ------------------------------------------------------------ | --------------------- |
|                                                              |                       |





### imaginary

原址：[https://zh.cppreference.com/w/c/numeric/complex/imaginary](https://zh.cppreference.com/w/c/numeric/complex/imaginary)

作用：虚数类型宏  (关键词宏)

备注：
```c
// 在标头 <complex.h> 定义
#define imaginary _Imaginary// (C99 起)
```

​	此宏展开成关键词 [_Imaginary](https://zh.cppreference.com/w/c/keyword/_Imaginary)。

​	这是一个便利宏，使你能用 `float imaginary`、`double imaginary` 及 `long double imaginary` 作为书写三种纯虚数 C 类型 `float _Imaginary`、`double _Imaginary` 以及 `long double _Imaginary` 的代用方式。

​	同 C 中的任意纯虚数支持，仅若支持虚数才定义此宏。

​	推荐编译器定义 `__STDC_IEC_559_COMPLEX__`，但并不强制要求其支持虚数。POSIX 推荐检查是否定义宏 `[_Imaginary_I](http://zh.cppreference.com/w/c/numeric/complex/Imaginary_I)` 以鉴别是否支持虚数。 (C99 起)(C11 前)

​	若定义 `__STDC_IEC_559_COMPLEX__`，则支持虚数。 (C11 起)

**注解**

​	允许程序取消定义，而且可在之后重定义 `imaginary` 宏。

​	如今，只有 Oracle C 编译器已知实现了虚部类型。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double imaginary i = 2.0*I; // 纯虚数
    double f = 1.0; // 纯实数
    double complex z = f + i; // 复数
    printf("z = %.1f%+.1fi\n", creal(z), cimag(z));
}
```

​	输出：

```txt
z = 1.0+2.0i
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.3.1/5 imaginary （第 136 页）

  - G.6/1 imaginary （第 391-392 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.1/5 imaginary （第 188 页）

  - G.6/1 imaginary （第 537 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.1/3 imaginary （第 170 页）

  - G.6/1 imaginary （第 472 页）

**参阅**

| [complex (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/complex) | 复数类型宏 (关键词宏) |
| ------------------------------------------------------------ | --------------------- |
|                                                              |                       |






## 函数



### CMPLX

原址：[https://zh.cppreference.com/w/c/numeric/complex/CMPLX](https://zh.cppreference.com/w/c/numeric/complex/CMPLX)

作用：由实部和虚部构建复数  (宏函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       CMPLXF( float real, float imag );// (C11 起)
double complex      CMPLX( double real, double imag );// (C11 起)
long double complex CMPLXL( long double real, long double imag );// (C11 起)
```

​	每个宏都展开成求值为指定复数类型的值的表达式，其实部值为（转换到指定实参类型的）`real`，其虚部值为（转换到指定实参类型的）`imag`。

​	该表达式适合用作有静态或线程存储期的对象的初始化式，只要表达式 `real` 和 `imag` 都同样适合。

**参数**

| real | -    | 待返回复数的实部 |
| ---- | ---- | ---------------- |
| imag | -    | 待返回复数的虚部 |

**返回值**

​	以 `real` 和 `imag` 为实部和虚部组合成的复数。

**注意**

​	这些宏的定义按照如同虚数类型有支持进行（即使不支持且并未实际定义 [_Imaginary_I](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I)），且如同定义如下：

```c
#define CMPLX(x, y) ((double complex)((double)(x) + _Imaginary_I * (double)(y)))
#define CMPLXF(x, y) ((float complex)((float)(x) + _Imaginary_I * (float)(y)))
#define CMPLXL(x, y) ((long double complex)((long double)(x) + \
                      _Imaginary_I * (long double)(y)))
```

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = CMPLX(0.0, -0.0);
    printf("z = %.1f%+.1fi\n", creal(z), cimag(z));
}
```

​	输出：

```txt
z = 0.0-0.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.3 The CMPLX macros （第 197 页）

**参阅**

| [_Imaginary_I (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I) | 虚数单位常量 i (宏常量) |
| ------------------------------------------------------------ | ----------------------- |
| **complex** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/complex)** |                         |





### CMPLXF

原址：[https://zh.cppreference.com/w/c/numeric/complex/CMPLX](https://zh.cppreference.com/w/c/numeric/complex/CMPLX)

作用：由实部和虚部构建复数  (宏函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       CMPLXF( float real, float imag );// (C11 起)
double complex      CMPLX( double real, double imag );// (C11 起)
long double complex CMPLXL( long double real, long double imag );// (C11 起)
```

​	每个宏都展开成求值为指定复数类型的值的表达式，其实部值为（转换到指定实参类型的）`real`，其虚部值为（转换到指定实参类型的）`imag`。

​	该表达式适合用作有静态或线程存储期的对象的初始化式，只要表达式 `real` 和 `imag` 都同样适合。

**参数**

| real | -    | 待返回复数的实部 |
| ---- | ---- | ---------------- |
| imag | -    | 待返回复数的虚部 |

**返回值**

​	以 `real` 和 `imag` 为实部和虚部组合成的复数。

**注意**

​	这些宏的定义按照如同虚数类型有支持进行（即使不支持且并未实际定义 [_Imaginary_I](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I)），且如同定义如下：

```c
#define CMPLX(x, y) ((double complex)((double)(x) + _Imaginary_I * (double)(y)))
#define CMPLXF(x, y) ((float complex)((float)(x) + _Imaginary_I * (float)(y)))
#define CMPLXL(x, y) ((long double complex)((long double)(x) + \
                      _Imaginary_I * (long double)(y)))
```

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = CMPLX(0.0, -0.0);
    printf("z = %.1f%+.1fi\n", creal(z), cimag(z));
}
```

​	输出：

```txt
z = 0.0-0.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.3 The CMPLX macros （第 197 页）

**参阅**

| [_Imaginary_I (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I) | 虚数单位常量 i (宏常量) |
| ------------------------------------------------------------ | ----------------------- |
| **complex** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/complex)** |                         |





### CMPLXL

原址：[https://zh.cppreference.com/w/c/numeric/complex/CMPLX](https://zh.cppreference.com/w/c/numeric/complex/CMPLX)

作用：由实部和虚部构建复数  (宏函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       CMPLXF( float real, float imag );// (C11 起)
double complex      CMPLX( double real, double imag );// (C11 起)
long double complex CMPLXL( long double real, long double imag );// (C11 起)
```

​	每个宏都展开成求值为指定复数类型的值的表达式，其实部值为（转换到指定实参类型的）`real`，其虚部值为（转换到指定实参类型的）`imag`。

​	该表达式适合用作有静态或线程存储期的对象的初始化式，只要表达式 `real` 和 `imag` 都同样适合。

**参数**

| real | -    | 待返回复数的实部 |
| ---- | ---- | ---------------- |
| imag | -    | 待返回复数的虚部 |

**返回值**

​	以 `real` 和 `imag` 为实部和虚部组合成的复数。

**注意**

​	这些宏的定义按照如同虚数类型有支持进行（即使不支持且并未实际定义 [_Imaginary_I](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I)），且如同定义如下：

```c
#define CMPLX(x, y) ((double complex)((double)(x) + _Imaginary_I * (double)(y)))
#define CMPLXF(x, y) ((float complex)((float)(x) + _Imaginary_I * (float)(y)))
#define CMPLXL(x, y) ((long double complex)((long double)(x) + \
                      _Imaginary_I * (long double)(y)))
```

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = CMPLX(0.0, -0.0);
    printf("z = %.1f%+.1fi\n", creal(z), cimag(z));
}
```

​	输出：

```txt
z = 0.0-0.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.3 The CMPLX macros （第 197 页）

**参阅**

| [_Imaginary_I (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I) | 虚数单位常量 i (宏常量) |
| ------------------------------------------------------------ | ----------------------- |
| **complex** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/complex)** |                         |





### cabs

原址：[https://zh.cppreference.com/w/c/numeric/complex/cabs](https://zh.cppreference.com/w/c/numeric/complex/cabs)

作用：计算复数的模（绝对值）  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float       cabsf( float complex z );// (1)(C99 起)
double      cabs( double complex z );// (2)(C99 起)
long double cabsl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define fabs( z )// (4)(C99 起)
```

1-3) 计算复数 `z` 的绝对值。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 或 `long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 类型，则调用 `cabsl`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 或 `float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 类型，则调用 `cabsf`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 或 `double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 类型，则调用 `cabs`。对于实数和整数类型，调用对应版本的 [fabs](https://zh.cppreference.com/w/c/numeric/math/fabs)。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 的绝对值（范数、模）。

​	如同函数实现为 `[hypot](http://zh.cppreference.com/w/c/numeric/math/hypot)([creal](http://zh.cppreference.com/w/c/numeric/complex/creal)(z), [cimag](http://zh.cppreference.com/w/c/numeric/complex/cimag)(z))` 一般处理错误和特殊情况。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = 1.0 + 1.0*I;
    printf("%.1f%+.1fi cartesian is rho=%f theta=%f polar\n",
           creal(z), cimag(z), cabs(z), carg(z));
}
```

​	输出：

```txt
1.0+1.0i cartesian is rho=1.414214 theta=0.785398 polar
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.8.1 The cabs functions （第 195 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.8.1 The cabs functions （第 177 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [carg (C99)<br />cargf (C99)<br />cargl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/carg) | 计算复数的辐角 (函数)                              |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [abs <br />labs <br />llabs (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/abs) | 计算整数的绝对值（\|x\|\|x\|） (函数)              |
| [fabs <br />fabsf (C99)<br />fabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fabs) | 计算浮点数的绝对值（\|x\|\|x\|） (函数)            |
| [hypot (C99)<br />hypotf (C99)<br />hypotl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/hypot) | 计算两个给定数平方和的平方根（√x2+y2x2+y2） (函数) |
| **abs** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/abs)** |                                                    |





### cabsf

原址：[https://zh.cppreference.com/w/c/numeric/complex/cabs](https://zh.cppreference.com/w/c/numeric/complex/cabs)

作用：计算复数的模（绝对值）  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float       cabsf( float complex z );// (1)(C99 起)
double      cabs( double complex z );// (2)(C99 起)
long double cabsl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define fabs( z )// (4)(C99 起)
```

1-3) 计算复数 `z` 的绝对值。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 或 `long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 类型，则调用 `cabsl`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 或 `float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 类型，则调用 `cabsf`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 或 `double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 类型，则调用 `cabs`。对于实数和整数类型，调用对应版本的 [fabs](https://zh.cppreference.com/w/c/numeric/math/fabs)。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 的绝对值（范数、模）。

​	如同函数实现为 `[hypot](http://zh.cppreference.com/w/c/numeric/math/hypot)([creal](http://zh.cppreference.com/w/c/numeric/complex/creal)(z), [cimag](http://zh.cppreference.com/w/c/numeric/complex/cimag)(z))` 一般处理错误和特殊情况。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = 1.0 + 1.0*I;
    printf("%.1f%+.1fi cartesian is rho=%f theta=%f polar\n",
           creal(z), cimag(z), cabs(z), carg(z));
}
```

​	输出：

```txt
1.0+1.0i cartesian is rho=1.414214 theta=0.785398 polar
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.8.1 The cabs functions （第 195 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.8.1 The cabs functions （第 177 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [carg (C99)<br />cargf (C99)<br />cargl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/carg) | 计算复数的辐角 (函数)                              |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [abs <br />labs <br />llabs (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/abs) | 计算整数的绝对值（\|x\|\|x\|） (函数)              |
| [fabs <br />fabsf (C99)<br />fabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fabs) | 计算浮点数的绝对值（\|x\|\|x\|） (函数)            |
| [hypot (C99)<br />hypotf (C99)<br />hypotl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/hypot) | 计算两个给定数平方和的平方根（√x2+y2x2+y2） (函数) |
| **abs** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/abs)** |                                                    |





### cabsl

原址：[https://zh.cppreference.com/w/c/numeric/complex/cabs](https://zh.cppreference.com/w/c/numeric/complex/cabs)

作用：计算复数的模（绝对值）  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float       cabsf( float complex z );// (1)(C99 起)
double      cabs( double complex z );// (2)(C99 起)
long double cabsl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define fabs( z )// (4)(C99 起)
```

1-3) 计算复数 `z` 的绝对值。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 或 `long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 类型，则调用 `cabsl`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 或 `float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 类型，则调用 `cabsf`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 或 `double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 类型，则调用 `cabs`。对于实数和整数类型，调用对应版本的 [fabs](https://zh.cppreference.com/w/c/numeric/math/fabs)。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 的绝对值（范数、模）。

​	如同函数实现为 `[hypot](http://zh.cppreference.com/w/c/numeric/math/hypot)([creal](http://zh.cppreference.com/w/c/numeric/complex/creal)(z), [cimag](http://zh.cppreference.com/w/c/numeric/complex/cimag)(z))` 一般处理错误和特殊情况。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = 1.0 + 1.0*I;
    printf("%.1f%+.1fi cartesian is rho=%f theta=%f polar\n",
           creal(z), cimag(z), cabs(z), carg(z));
}
```

​	输出：

```txt
1.0+1.0i cartesian is rho=1.414214 theta=0.785398 polar
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.8.1 The cabs functions （第 195 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.8.1 The cabs functions （第 177 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [carg (C99)<br />cargf (C99)<br />cargl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/carg) | 计算复数的辐角 (函数)                              |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [abs <br />labs <br />llabs (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/abs) | 计算整数的绝对值（\|x\|\|x\|） (函数)              |
| [fabs <br />fabsf (C99)<br />fabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fabs) | 计算浮点数的绝对值（\|x\|\|x\|） (函数)            |
| [hypot (C99)<br />hypotf (C99)<br />hypotl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/hypot) | 计算两个给定数平方和的平方根（√x2+y2x2+y2） (函数) |
| **abs** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/abs)** |                                                    |





### cacos

原址：[https://zh.cppreference.com/w/c/numeric/complex/cacos](https://zh.cppreference.com/w/c/numeric/complex/cacos)

作用：计算复数反余弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       cacosf( float complex z );// (1)(C99 起)
double complex      cacos( double complex z );// (2)(C99 起)
long double complex cacosl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define acos( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复弧（反）余弦，分支切割在沿实轴的区间 *[−1,+1]* 外。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacosl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacos`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacosf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`acosf`、`[acos](http://zh.cppreference.com/w/c/numeric/math/acos)`、`acosl`）。若 `z` 为虚数，则宏调用对应的复数版本。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 的复弧（反）余弦，其定义域为沿虚轴无界，沿实轴在区间 [0; π] 上的条带。

**错误处理**及特殊值

​	报告的错误与 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `cacos([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(cacos(z))`
- 若 `z` 为 `±0+0i`，则结果为 `π/2-0i`
- 若 `z` 为 `±0+NaNi`，则结果为 `π/2+NaNi`
- 若 `z` 为 `x+∞i`（对于任何有限 x），则结果为 `π/2-∞i`
- 若 `z` 为 `x+NaNi`（对于任何有限非零 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 。
- 若 `z` 为 `-∞+yi`（对于任何有限正 y），则结果为 `π-∞i`
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），则结果为 `+0-∞i`
- 若 `z` 为 `-∞+∞i`，则结果为 `3π/4-∞i`
- 若 `z` 为 `+∞+∞i`，则结果为 `π/4-∞i`
- 若 `z` 为 `±∞+NaNi`，则结果为 `NaN±∞i`（虚部符号未指定）
- 若 `z` 为 `NaN+yi`（对于任何有限 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+∞i`，则结果为 `NaN-∞i`
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**注解**

​	反余弦（或弧余弦）是多值函数，要求复平面上的分支切割。约定将分支切割置于实轴的线段 *(-∞,-1)* 和 *(1,∞)* 上。

弧（反）余弦主值的数学定义是 

acos z = 

| 1    |
| ---- |
| 2    |

π + *i*ln(*i*z + √1-z2
)

。

​	对于任何 z， *acos(z) = π - acos(-z)*。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = cacos(-2);
    printf("cacos(-2+0i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = cacos(conj(-2)); // 或 CMPLX(-2, -0.0)
    printf("cacos(-2-0i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    // 对于任何 z，acos(z) = pi - acos(-z)
    double pi = acos(-1);
    double complex z3 = ccos(pi-z2);
    printf("ccos(pi - cacos(-2-0i) = %f%+fi\n", creal(z3), cimag(z3));
}
```

​	输出：

```txt
cacos(-2+0i) = 3.141593-1.316958i
cacos(-2-0i) (the other side of the cut) = 3.141593+1.316958i
ccos(pi - cacos(-2-0i) = 2.000000+0.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.1 The cacos functions （第 190 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.1.1 The cacos functions （第 539 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.1 The cacos functions （第 172 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.1.1 The cacos functions （第 474 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [casin (C99)<br />casinf (C99)<br />casinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casin) | 计算复数反正弦 (函数)               |
| ------------------------------------------------------------ | ----------------------------------- |
| [catan (C99)<br />catanf (C99)<br />catanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catan) | 计算复数反正切 (函数)               |
| [ccos (C99)<br />ccosf (C99)<br />ccosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccos) | 计算复数余弦 (函数)                 |
| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡x） (函数) |
| **acos** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/acos)** |                                     |





### cacosf

原址：[https://zh.cppreference.com/w/c/numeric/complex/cacos](https://zh.cppreference.com/w/c/numeric/complex/cacos)

作用：计算复数反余弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       cacosf( float complex z );// (1)(C99 起)
double complex      cacos( double complex z );// (2)(C99 起)
long double complex cacosl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define acos( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复弧（反）余弦，分支切割在沿实轴的区间 *[−1,+1]* 外。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacosl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacos`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacosf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`acosf`、`[acos](http://zh.cppreference.com/w/c/numeric/math/acos)`、`acosl`）。若 `z` 为虚数，则宏调用对应的复数版本。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 的复弧（反）余弦，其定义域为沿虚轴无界，沿实轴在区间 [0; π] 上的条带。

**错误处理**及特殊值

​	报告的错误与 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `cacos([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(cacos(z))`
- 若 `z` 为 `±0+0i`，则结果为 `π/2-0i`
- 若 `z` 为 `±0+NaNi`，则结果为 `π/2+NaNi`
- 若 `z` 为 `x+∞i`（对于任何有限 x），则结果为 `π/2-∞i`
- 若 `z` 为 `x+NaNi`（对于任何有限非零 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 。
- 若 `z` 为 `-∞+yi`（对于任何有限正 y），则结果为 `π-∞i`
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），则结果为 `+0-∞i`
- 若 `z` 为 `-∞+∞i`，则结果为 `3π/4-∞i`
- 若 `z` 为 `+∞+∞i`，则结果为 `π/4-∞i`
- 若 `z` 为 `±∞+NaNi`，则结果为 `NaN±∞i`（虚部符号未指定）
- 若 `z` 为 `NaN+yi`（对于任何有限 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+∞i`，则结果为 `NaN-∞i`
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**注解**

​	反余弦（或弧余弦）是多值函数，要求复平面上的分支切割。约定将分支切割置于实轴的线段 *(-∞,-1)* 和 *(1,∞)* 上。

弧（反）余弦主值的数学定义是 

acos z = 

| 1    |
| ---- |
| 2    |

π + *i*ln(*i*z + √1-z2
)

。

​	对于任何 z， *acos(z) = π - acos(-z)*。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = cacos(-2);
    printf("cacos(-2+0i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = cacos(conj(-2)); // 或 CMPLX(-2, -0.0)
    printf("cacos(-2-0i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    // 对于任何 z，acos(z) = pi - acos(-z)
    double pi = acos(-1);
    double complex z3 = ccos(pi-z2);
    printf("ccos(pi - cacos(-2-0i) = %f%+fi\n", creal(z3), cimag(z3));
}
```

​	输出：

```txt
cacos(-2+0i) = 3.141593-1.316958i
cacos(-2-0i) (the other side of the cut) = 3.141593+1.316958i
ccos(pi - cacos(-2-0i) = 2.000000+0.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.1 The cacos functions （第 190 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.1.1 The cacos functions （第 539 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.1 The cacos functions （第 172 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.1.1 The cacos functions （第 474 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [casin (C99)<br />casinf (C99)<br />casinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casin) | 计算复数反正弦 (函数)               |
| ------------------------------------------------------------ | ----------------------------------- |
| [catan (C99)<br />catanf (C99)<br />catanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catan) | 计算复数反正切 (函数)               |
| [ccos (C99)<br />ccosf (C99)<br />ccosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccos) | 计算复数余弦 (函数)                 |
| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡x） (函数) |
| **acos** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/acos)** |                                     |





### cacosh

原址：[https://zh.cppreference.com/w/c/numeric/complex/cacosh](https://zh.cppreference.com/w/c/numeric/complex/cacosh)

作用：计算复数反双曲余弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       cacoshf( float complex z );// (1)(C99 起)
double complex      cacosh( double complex z );// (2)(C99 起)
long double complex cacoshl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define acosh( z )// (4)(C99 起)
```

1-3) 计算复数值 `z` 的复反双曲余弦，分支切割在沿实轴小于 1 的值上。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacoshl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacosh`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacoshf`。若 `z` 为实数或整数，则宏调用对应的实函数（`acoshf`、`[acosh](http://zh.cppreference.com/w/c/numeric/math/acosh)`、`acoshl`）。若 `z` 为虚数，则宏调用对应的复数版本，而返回类型为复数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	`z` 的复反双曲余弦，定义域沿实轴在区间 *[0; ∞)* 中，而沿虚轴在区间 *[−iπ; +iπ]* 中。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `cacosh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(cacosh(z))`
- 若 `z` 为 `±0+0i`，则结果为 `+0+iπ/2`
- 若 `z` 为 `+x+∞i`（对于任何有限 x），则结果为 `+∞+iπ/2`
- 若 `z` 为 `+x+NaNi`（对于任何非零有限 x），结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `0+NaNi`，则结果为 `NaN±iπ/2`，其中虚部符号未指定
- 若 `z` 为 `-∞+yi`（对于任何有限正 y），则结果为 `+∞+iπ`
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），则结果为 `+∞+0i`
- 若 `z` 为 `-∞+∞i`，则结果为 `+∞+3iπ/4`
- 若 `z` 为 `+∞+∞i`，则结果为 `+∞+iπ/4`
- 若 `z` 为 `±∞+NaNi`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+yi`（对于任何有限 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 。
- 若 `z` 为 `NaN+∞i`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**注意**

​	虽然 C 标准命名此函数为“复弧双曲余弦”，但双曲函数的反函数是面积函数。其实参为双曲扇形的面积，而非弧长。正确名称是“复反双曲余弦”，和更少见的“复面积双曲余弦”。

​	反双曲余弦是多值函数，在复平面上要求分支切割。约定将分支切割置于实轴的线段 *(-∞,+1)* 上。

​	复反双曲余弦主值的数学定义是 *acosh z = ln(z + √z+1 √z-1)*。

对于任何 z，

acosh(z) = 

| √z-1 |
| ---- |
| √1-z |

 acos(z)

，或在复平面上半部简单地为 *i acos(z)*。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = cacosh(0.5);
    printf("cacosh(+0.5+0i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = conj(0.5); // 或 C11 中的 cacosh(CMPLX(0.5, -0.0))
    printf("cacosh(+0.5-0i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    // 在上半平面，acosh(z) = i*acos(z) 
    double complex z3 = casinh(1+I);
    printf("casinh(1+1i) = %f%+fi\n", creal(z3), cimag(z3));
    double complex z4 = I*casin(1+I);
    printf("I*asin(1+1i) = %f%+fi\n", creal(z4), cimag(z4));
}
```

​	输出：

```txt
cacosh(+0.5+0i) = 0.000000-1.047198i
cacosh(+0.5-0i) (the other side of the cut) = 0.500000-0.000000i
casinh(1+1i) = 1.061275+0.666239i
I*asin(1+1i) = -1.061275+0.666239i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.1 The cacosh functions （第 192 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.1 The cacosh functions （第 539-540 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.1 The cacosh functions （第 174 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.1 The cacosh functions （第 474-475 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数)                   |
| ------------------------------------------------------------ | --------------------------------------- |
| [casinh (C99)<br />casinhf (C99)<br />casinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casinh) | 计算复数反双曲正弦 (函数)               |
| [catanh (C99)<br />catanhf (C99)<br />catanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catanh) | 计算复数反双曲正切 (函数)               |
| [ccosh (C99)<br />ccoshf (C99)<br />ccoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccosh) | 计算复双曲余弦 (函数)                   |
| [acosh (C99)<br />acoshf (C99)<br />acoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acosh) | 计算反双曲余弦（arcoshxarcosh⁡x） (函数) |
| **acosh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/acosh)** |                                         |





### cacoshf

原址：[https://zh.cppreference.com/w/c/numeric/complex/cacosh](https://zh.cppreference.com/w/c/numeric/complex/cacosh)

作用：计算复数反双曲余弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       cacoshf( float complex z );// (1)(C99 起)
double complex      cacosh( double complex z );// (2)(C99 起)
long double complex cacoshl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define acosh( z )// (4)(C99 起)
```

1-3) 计算复数值 `z` 的复反双曲余弦，分支切割在沿实轴小于 1 的值上。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacoshl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacosh`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacoshf`。若 `z` 为实数或整数，则宏调用对应的实函数（`acoshf`、`[acosh](http://zh.cppreference.com/w/c/numeric/math/acosh)`、`acoshl`）。若 `z` 为虚数，则宏调用对应的复数版本，而返回类型为复数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	`z` 的复反双曲余弦，定义域沿实轴在区间 *[0; ∞)* 中，而沿虚轴在区间 *[−iπ; +iπ]* 中。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `cacosh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(cacosh(z))`
- 若 `z` 为 `±0+0i`，则结果为 `+0+iπ/2`
- 若 `z` 为 `+x+∞i`（对于任何有限 x），则结果为 `+∞+iπ/2`
- 若 `z` 为 `+x+NaNi`（对于任何非零有限 x），结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `0+NaNi`，则结果为 `NaN±iπ/2`，其中虚部符号未指定
- 若 `z` 为 `-∞+yi`（对于任何有限正 y），则结果为 `+∞+iπ`
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），则结果为 `+∞+0i`
- 若 `z` 为 `-∞+∞i`，则结果为 `+∞+3iπ/4`
- 若 `z` 为 `+∞+∞i`，则结果为 `+∞+iπ/4`
- 若 `z` 为 `±∞+NaNi`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+yi`（对于任何有限 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 。
- 若 `z` 为 `NaN+∞i`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**注意**

​	虽然 C 标准命名此函数为“复弧双曲余弦”，但双曲函数的反函数是面积函数。其实参为双曲扇形的面积，而非弧长。正确名称是“复反双曲余弦”，和更少见的“复面积双曲余弦”。

​	反双曲余弦是多值函数，在复平面上要求分支切割。约定将分支切割置于实轴的线段 *(-∞,+1)* 上。

​	复反双曲余弦主值的数学定义是 *acosh z = ln(z + √z+1 √z-1)*。

对于任何 z，

acosh(z) = 

| √z-1 |
| ---- |
| √1-z |

 acos(z)

，或在复平面上半部简单地为 *i acos(z)*。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = cacosh(0.5);
    printf("cacosh(+0.5+0i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = conj(0.5); // 或 C11 中的 cacosh(CMPLX(0.5, -0.0))
    printf("cacosh(+0.5-0i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    // 在上半平面，acosh(z) = i*acos(z) 
    double complex z3 = casinh(1+I);
    printf("casinh(1+1i) = %f%+fi\n", creal(z3), cimag(z3));
    double complex z4 = I*casin(1+I);
    printf("I*asin(1+1i) = %f%+fi\n", creal(z4), cimag(z4));
}
```

​	输出：

```txt
cacosh(+0.5+0i) = 0.000000-1.047198i
cacosh(+0.5-0i) (the other side of the cut) = 0.500000-0.000000i
casinh(1+1i) = 1.061275+0.666239i
I*asin(1+1i) = -1.061275+0.666239i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.1 The cacosh functions （第 192 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.1 The cacosh functions （第 539-540 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.1 The cacosh functions （第 174 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.1 The cacosh functions （第 474-475 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数)                   |
| ------------------------------------------------------------ | --------------------------------------- |
| [casinh (C99)<br />casinhf (C99)<br />casinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casinh) | 计算复数反双曲正弦 (函数)               |
| [catanh (C99)<br />catanhf (C99)<br />catanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catanh) | 计算复数反双曲正切 (函数)               |
| [ccosh (C99)<br />ccoshf (C99)<br />ccoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccosh) | 计算复双曲余弦 (函数)                   |
| [acosh (C99)<br />acoshf (C99)<br />acoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acosh) | 计算反双曲余弦（arcoshxarcosh⁡x） (函数) |
| **acosh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/acosh)** |                                         |





### cacoshl

原址：[https://zh.cppreference.com/w/c/numeric/complex/cacosh](https://zh.cppreference.com/w/c/numeric/complex/cacosh)

作用：计算复数反双曲余弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       cacoshf( float complex z );// (1)(C99 起)
double complex      cacosh( double complex z );// (2)(C99 起)
long double complex cacoshl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define acosh( z )// (4)(C99 起)
```

1-3) 计算复数值 `z` 的复反双曲余弦，分支切割在沿实轴小于 1 的值上。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacoshl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacosh`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacoshf`。若 `z` 为实数或整数，则宏调用对应的实函数（`acoshf`、`[acosh](http://zh.cppreference.com/w/c/numeric/math/acosh)`、`acoshl`）。若 `z` 为虚数，则宏调用对应的复数版本，而返回类型为复数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	`z` 的复反双曲余弦，定义域沿实轴在区间 *[0; ∞)* 中，而沿虚轴在区间 *[−iπ; +iπ]* 中。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `cacosh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(cacosh(z))`
- 若 `z` 为 `±0+0i`，则结果为 `+0+iπ/2`
- 若 `z` 为 `+x+∞i`（对于任何有限 x），则结果为 `+∞+iπ/2`
- 若 `z` 为 `+x+NaNi`（对于任何非零有限 x），结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `0+NaNi`，则结果为 `NaN±iπ/2`，其中虚部符号未指定
- 若 `z` 为 `-∞+yi`（对于任何有限正 y），则结果为 `+∞+iπ`
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），则结果为 `+∞+0i`
- 若 `z` 为 `-∞+∞i`，则结果为 `+∞+3iπ/4`
- 若 `z` 为 `+∞+∞i`，则结果为 `+∞+iπ/4`
- 若 `z` 为 `±∞+NaNi`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+yi`（对于任何有限 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 。
- 若 `z` 为 `NaN+∞i`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**注意**

​	虽然 C 标准命名此函数为“复弧双曲余弦”，但双曲函数的反函数是面积函数。其实参为双曲扇形的面积，而非弧长。正确名称是“复反双曲余弦”，和更少见的“复面积双曲余弦”。

​	反双曲余弦是多值函数，在复平面上要求分支切割。约定将分支切割置于实轴的线段 *(-∞,+1)* 上。

​	复反双曲余弦主值的数学定义是 *acosh z = ln(z + √z+1 √z-1)*。

对于任何 z，

acosh(z) = 

| √z-1 |
| ---- |
| √1-z |

 acos(z)

，或在复平面上半部简单地为 *i acos(z)*。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = cacosh(0.5);
    printf("cacosh(+0.5+0i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = conj(0.5); // 或 C11 中的 cacosh(CMPLX(0.5, -0.0))
    printf("cacosh(+0.5-0i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    // 在上半平面，acosh(z) = i*acos(z) 
    double complex z3 = casinh(1+I);
    printf("casinh(1+1i) = %f%+fi\n", creal(z3), cimag(z3));
    double complex z4 = I*casin(1+I);
    printf("I*asin(1+1i) = %f%+fi\n", creal(z4), cimag(z4));
}
```

​	输出：

```txt
cacosh(+0.5+0i) = 0.000000-1.047198i
cacosh(+0.5-0i) (the other side of the cut) = 0.500000-0.000000i
casinh(1+1i) = 1.061275+0.666239i
I*asin(1+1i) = -1.061275+0.666239i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.1 The cacosh functions （第 192 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.1 The cacosh functions （第 539-540 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.1 The cacosh functions （第 174 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.1 The cacosh functions （第 474-475 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数)                   |
| ------------------------------------------------------------ | --------------------------------------- |
| [casinh (C99)<br />casinhf (C99)<br />casinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casinh) | 计算复数反双曲正弦 (函数)               |
| [catanh (C99)<br />catanhf (C99)<br />catanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catanh) | 计算复数反双曲正切 (函数)               |
| [ccosh (C99)<br />ccoshf (C99)<br />ccoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccosh) | 计算复双曲余弦 (函数)                   |
| [acosh (C99)<br />acoshf (C99)<br />acoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acosh) | 计算反双曲余弦（arcoshxarcosh⁡x） (函数) |
| **acosh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/acosh)** |                                         |





### cacosl

原址：[https://zh.cppreference.com/w/c/numeric/complex/cacos](https://zh.cppreference.com/w/c/numeric/complex/cacos)

作用：计算复数反余弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       cacosf( float complex z );// (1)(C99 起)
double complex      cacos( double complex z );// (2)(C99 起)
long double complex cacosl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define acos( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复弧（反）余弦，分支切割在沿实轴的区间 *[−1,+1]* 外。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacosl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacos`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cacosf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`acosf`、`[acos](http://zh.cppreference.com/w/c/numeric/math/acos)`、`acosl`）。若 `z` 为虚数，则宏调用对应的复数版本。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 的复弧（反）余弦，其定义域为沿虚轴无界，沿实轴在区间 [0; π] 上的条带。

**错误处理**及特殊值

​	报告的错误与 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `cacos([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(cacos(z))`
- 若 `z` 为 `±0+0i`，则结果为 `π/2-0i`
- 若 `z` 为 `±0+NaNi`，则结果为 `π/2+NaNi`
- 若 `z` 为 `x+∞i`（对于任何有限 x），则结果为 `π/2-∞i`
- 若 `z` 为 `x+NaNi`（对于任何有限非零 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 。
- 若 `z` 为 `-∞+yi`（对于任何有限正 y），则结果为 `π-∞i`
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），则结果为 `+0-∞i`
- 若 `z` 为 `-∞+∞i`，则结果为 `3π/4-∞i`
- 若 `z` 为 `+∞+∞i`，则结果为 `π/4-∞i`
- 若 `z` 为 `±∞+NaNi`，则结果为 `NaN±∞i`（虚部符号未指定）
- 若 `z` 为 `NaN+yi`（对于任何有限 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+∞i`，则结果为 `NaN-∞i`
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**注解**

​	反余弦（或弧余弦）是多值函数，要求复平面上的分支切割。约定将分支切割置于实轴的线段 *(-∞,-1)* 和 *(1,∞)* 上。

弧（反）余弦主值的数学定义是 

acos z = 

| 1    |
| ---- |
| 2    |

π + *i*ln(*i*z + √1-z2
)

。

​	对于任何 z， *acos(z) = π - acos(-z)*。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = cacos(-2);
    printf("cacos(-2+0i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = cacos(conj(-2)); // 或 CMPLX(-2, -0.0)
    printf("cacos(-2-0i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    // 对于任何 z，acos(z) = pi - acos(-z)
    double pi = acos(-1);
    double complex z3 = ccos(pi-z2);
    printf("ccos(pi - cacos(-2-0i) = %f%+fi\n", creal(z3), cimag(z3));
}
```

​	输出：

```txt
cacos(-2+0i) = 3.141593-1.316958i
cacos(-2-0i) (the other side of the cut) = 3.141593+1.316958i
ccos(pi - cacos(-2-0i) = 2.000000+0.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.1 The cacos functions （第 190 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.1.1 The cacos functions （第 539 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.1 The cacos functions （第 172 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.1.1 The cacos functions （第 474 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [casin (C99)<br />casinf (C99)<br />casinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casin) | 计算复数反正弦 (函数)               |
| ------------------------------------------------------------ | ----------------------------------- |
| [catan (C99)<br />catanf (C99)<br />catanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catan) | 计算复数反正切 (函数)               |
| [ccos (C99)<br />ccosf (C99)<br />ccosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccos) | 计算复数余弦 (函数)                 |
| [acos <br />acosf (C99)<br />acosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/acos) | 计算反余弦（arccosxarccos⁡x） (函数) |
| **acos** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/acos)** |                                     |





### carg

原址：[https://zh.cppreference.com/w/c/numeric/complex/carg](https://zh.cppreference.com/w/c/numeric/complex/carg)

作用：计算复数的辐角  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float       cargf( float complex z );// (1)(C99 起)
double      carg( double complex z );// (2)(C99 起)
long double cargl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define carg( z )// (4)(C99 起)
```

1-3) 计算 `z` 的辐角（又称相位角），沿负实轴切割分支。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `long double` 类型，则调用 `cargl`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `float` 类型，则调用 `cargf`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)`、`double` 或任何整数类型，则调用 `carg`。

**参数**

| z    | -    | 复参数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `z` 在 *[−π; π]* 区间中的相位角。

​	如同函数实现为 `[atan2](http://zh.cppreference.com/w/c/numeric/math/atan2)([cimag](http://zh.cppreference.com/w/c/numeric/complex/cimag)(z), [creal](http://zh.cppreference.com/w/c/numeric/complex/creal)(z))` 一般处理错误和特殊情况。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void) 
{
    double complex z1 = 1.0+0.0*I;
    printf("phase angle of %.1f%+.1fi is %f\n", creal(z1), cimag(z1), carg(z1));
 
    double complex z2 = 0.0+1.0*I;
    printf("phase angle of %.1f%+.1fi is %f\n", creal(z2), cimag(z2), carg(z2));
 
    double complex z3 = -1.0+0.0*I;
    printf("phase angle of %.1f%+.1fi is %f\n", creal(z3), cimag(z3), carg(z3));
 
    double complex z4 = conj(z3); // 或 CMPLX(-1, -0.0)
    printf("phase angle of %.1f%+.1fi (the other side of the cut) is %f\n",
             creal(z4), cimag(z4), carg(z4));
}
```

​	输出：

```txt
phase angle of 1.0+0.0i is 0.000000
phase angle of 0.0+1.0i is 1.570796
phase angle of -1.0+0.0i is 3.141593
phase angle of -1.0-0.0i (the other side of the cut) is -3.141593
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.1 The carg functions （第 196 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.9.1 The carg functions （第 178 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cabs (C99)<br />cabsf (C99)<br />cabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cabs) | 计算复数的模（绝对值） (函数)     |
| ------------------------------------------------------------ | --------------------------------- |
| [atan2 <br />atan2f (C99)<br />atan2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan2) | 计算反正切，以符号确定象限 (函数) |
| **arg** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/arg)** |                                   |





### cargf

原址：[https://zh.cppreference.com/w/c/numeric/complex/carg](https://zh.cppreference.com/w/c/numeric/complex/carg)

作用：计算复数的辐角  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float       cargf( float complex z );// (1)(C99 起)
double      carg( double complex z );// (2)(C99 起)
long double cargl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define carg( z )// (4)(C99 起)
```

1-3) 计算 `z` 的辐角（又称相位角），沿负实轴切割分支。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `long double` 类型，则调用 `cargl`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `float` 类型，则调用 `cargf`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)`、`double` 或任何整数类型，则调用 `carg`。

**参数**

| z    | -    | 复参数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `z` 在 *[−π; π]* 区间中的相位角。

​	如同函数实现为 `[atan2](http://zh.cppreference.com/w/c/numeric/math/atan2)([cimag](http://zh.cppreference.com/w/c/numeric/complex/cimag)(z), [creal](http://zh.cppreference.com/w/c/numeric/complex/creal)(z))` 一般处理错误和特殊情况。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void) 
{
    double complex z1 = 1.0+0.0*I;
    printf("phase angle of %.1f%+.1fi is %f\n", creal(z1), cimag(z1), carg(z1));
 
    double complex z2 = 0.0+1.0*I;
    printf("phase angle of %.1f%+.1fi is %f\n", creal(z2), cimag(z2), carg(z2));
 
    double complex z3 = -1.0+0.0*I;
    printf("phase angle of %.1f%+.1fi is %f\n", creal(z3), cimag(z3), carg(z3));
 
    double complex z4 = conj(z3); // 或 CMPLX(-1, -0.0)
    printf("phase angle of %.1f%+.1fi (the other side of the cut) is %f\n",
             creal(z4), cimag(z4), carg(z4));
}
```

​	输出：

```txt
phase angle of 1.0+0.0i is 0.000000
phase angle of 0.0+1.0i is 1.570796
phase angle of -1.0+0.0i is 3.141593
phase angle of -1.0-0.0i (the other side of the cut) is -3.141593
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.1 The carg functions （第 196 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.9.1 The carg functions （第 178 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cabs (C99)<br />cabsf (C99)<br />cabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cabs) | 计算复数的模（绝对值） (函数)     |
| ------------------------------------------------------------ | --------------------------------- |
| [atan2 <br />atan2f (C99)<br />atan2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan2) | 计算反正切，以符号确定象限 (函数) |
| **arg** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/arg)** |                                   |





### cargl

原址：[https://zh.cppreference.com/w/c/numeric/complex/carg](https://zh.cppreference.com/w/c/numeric/complex/carg)

作用：计算复数的辐角  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float       cargf( float complex z );// (1)(C99 起)
double      carg( double complex z );// (2)(C99 起)
long double cargl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define carg( z )// (4)(C99 起)
```

1-3) 计算 `z` 的辐角（又称相位角），沿负实轴切割分支。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `long double` 类型，则调用 `cargl`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `float` 类型，则调用 `cargf`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)`、`double` 或任何整数类型，则调用 `carg`。

**参数**

| z    | -    | 复参数 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若不出现错误，则返回 `z` 在 *[−π; π]* 区间中的相位角。

​	如同函数实现为 `[atan2](http://zh.cppreference.com/w/c/numeric/math/atan2)([cimag](http://zh.cppreference.com/w/c/numeric/complex/cimag)(z), [creal](http://zh.cppreference.com/w/c/numeric/complex/creal)(z))` 一般处理错误和特殊情况。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void) 
{
    double complex z1 = 1.0+0.0*I;
    printf("phase angle of %.1f%+.1fi is %f\n", creal(z1), cimag(z1), carg(z1));
 
    double complex z2 = 0.0+1.0*I;
    printf("phase angle of %.1f%+.1fi is %f\n", creal(z2), cimag(z2), carg(z2));
 
    double complex z3 = -1.0+0.0*I;
    printf("phase angle of %.1f%+.1fi is %f\n", creal(z3), cimag(z3), carg(z3));
 
    double complex z4 = conj(z3); // 或 CMPLX(-1, -0.0)
    printf("phase angle of %.1f%+.1fi (the other side of the cut) is %f\n",
             creal(z4), cimag(z4), carg(z4));
}
```

​	输出：

```txt
phase angle of 1.0+0.0i is 0.000000
phase angle of 0.0+1.0i is 1.570796
phase angle of -1.0+0.0i is 3.141593
phase angle of -1.0-0.0i (the other side of the cut) is -3.141593
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.1 The carg functions （第 196 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.9.1 The carg functions （第 178 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cabs (C99)<br />cabsf (C99)<br />cabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cabs) | 计算复数的模（绝对值） (函数)     |
| ------------------------------------------------------------ | --------------------------------- |
| [atan2 <br />atan2f (C99)<br />atan2l (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan2) | 计算反正切，以符号确定象限 (函数) |
| **arg** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/arg)** |                                   |





### casin

原址：[https://zh.cppreference.com/w/c/numeric/complex/casin](https://zh.cppreference.com/w/c/numeric/complex/casin)

作用：计算复数反正弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       casinf( float complex z );// (1)(C99 起)
double complex      casin( double complex z );// (2)(C99 起)
long double complex casinl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define asin( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复反正弦，分支切割线在沿实轴的 *[−1,+1]* 区间外。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `casinl`，若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `casin`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `casinf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`asinf`、`[asin](http://zh.cppreference.com/w/c/numeric/math/asin)`、`asinl`）。若 `z` 为虚数，则宏调用函数 [asinh](https://zh.cppreference.com/w/c/numeric/math/asinh) 的对应实数版本，实现公式 arcsin(iy)=iarsinh(y)arcsin⁡(iy)=iarsinh(y)，而宏的返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 在沿虚轴无界、沿实轴在区间 *[−π/2; +π/2]* 中的条状范围中的复反正弦。

​	如同运算以 `-I * [casinh](http://zh.cppreference.com/w/c/numeric/complex/casinh)(I*z)` 实现一般处理错误和特殊情况。

**注解**

​	反正弦（或弧正弦）是多值函数，且在复平面上要求分支切割。约定将分支切割线置于实轴上的区间 *(-∞,-1)* 和 *(1,∞)* 上。

​	反正弦主值的数学定义是 arcsinz=−iln(iz+√1−z2)arcsin⁡z=−iln⁡(iz+1−z2)。

对于任何 z，arcsin(z)=arccos(−z)−π2arcsin⁡(z)=arccos⁡(−z)−π2。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = casin(-2);
    printf("casin(-2+0i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = casin(conj(-2)); // 或 CMPLX(-2, -0.0)
    printf("casin(-2-0i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    // 对于任何 z，asin(z) = acos(-z) - pi/2
    double pi = acos(-1);
    double complex z3 = csin(cacos(conj(-2))-pi/2);
    printf("csin(cacos(-2-0i)-pi/2) = %f%+fi\n", creal(z3), cimag(z3));
}
```

​	输出：

```txt
casin(-2+0i) = -1.570796+1.316958i
casin(-2-0i) (the other side of the cut) = -1.570796-1.316958i
csin(cacos(-2-0i)-pi/2) = 2.000000+0.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.2 The casin functions （第 190 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.2 The casin functions （第 172 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数)               |
| ------------------------------------------------------------ | ----------------------------------- |
| [catan (C99)<br />catanf (C99)<br />catanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catan) | 计算复数反正切 (函数)               |
| [csin (C99)<br />csinf (C99)<br />csinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csin) | 计算复数正弦 (函数)                 |
| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡x） (函数) |
| **asin** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/asin)** |                                     |





### casinf

原址：[https://zh.cppreference.com/w/c/numeric/complex/casin](https://zh.cppreference.com/w/c/numeric/complex/casin)

作用：计算复数反正弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       casinf( float complex z );// (1)(C99 起)
double complex      casin( double complex z );// (2)(C99 起)
long double complex casinl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define asin( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复反正弦，分支切割线在沿实轴的 *[−1,+1]* 区间外。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `casinl`，若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `casin`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `casinf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`asinf`、`[asin](http://zh.cppreference.com/w/c/numeric/math/asin)`、`asinl`）。若 `z` 为虚数，则宏调用函数 [asinh](https://zh.cppreference.com/w/c/numeric/math/asinh) 的对应实数版本，实现公式 arcsin(iy)=iarsinh(y)arcsin⁡(iy)=iarsinh(y)，而宏的返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 在沿虚轴无界、沿实轴在区间 *[−π/2; +π/2]* 中的条状范围中的复反正弦。

​	如同运算以 `-I * [casinh](http://zh.cppreference.com/w/c/numeric/complex/casinh)(I*z)` 实现一般处理错误和特殊情况。

**注解**

​	反正弦（或弧正弦）是多值函数，且在复平面上要求分支切割。约定将分支切割线置于实轴上的区间 *(-∞,-1)* 和 *(1,∞)* 上。

​	反正弦主值的数学定义是 arcsinz=−iln(iz+√1−z2)arcsin⁡z=−iln⁡(iz+1−z2)。

对于任何 z，arcsin(z)=arccos(−z)−π2arcsin⁡(z)=arccos⁡(−z)−π2。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = casin(-2);
    printf("casin(-2+0i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = casin(conj(-2)); // 或 CMPLX(-2, -0.0)
    printf("casin(-2-0i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    // 对于任何 z，asin(z) = acos(-z) - pi/2
    double pi = acos(-1);
    double complex z3 = csin(cacos(conj(-2))-pi/2);
    printf("csin(cacos(-2-0i)-pi/2) = %f%+fi\n", creal(z3), cimag(z3));
}
```

​	输出：

```txt
casin(-2+0i) = -1.570796+1.316958i
casin(-2-0i) (the other side of the cut) = -1.570796-1.316958i
csin(cacos(-2-0i)-pi/2) = 2.000000+0.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.2 The casin functions （第 190 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.2 The casin functions （第 172 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数)               |
| ------------------------------------------------------------ | ----------------------------------- |
| [catan (C99)<br />catanf (C99)<br />catanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catan) | 计算复数反正切 (函数)               |
| [csin (C99)<br />csinf (C99)<br />csinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csin) | 计算复数正弦 (函数)                 |
| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡x） (函数) |
| **asin** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/asin)** |                                     |





### casinh

原址：[https://zh.cppreference.com/w/c/numeric/complex/casinh](https://zh.cppreference.com/w/c/numeric/complex/casinh)

作用：计算复数反双曲正弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       casinhf( float complex z );// (1)(C99 起)
double complex      casinh( double complex z );// (2)(C99 起)
long double complex casinhl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define asinh( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复反双曲正弦，分支切割在沿虚轴的 *[−i; +i]* 区间外。

4） 泛型宏：若 `z` 拥有类型 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `casinhl`。若 `z` 拥有类型 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `casinh`，若 `z` 拥有类型 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `casinhf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`asinhf`、`[asinh](http://zh.cppreference.com/w/c/numeric/math/asinh)`、`asinhl`）。若 `z` 为虚数，则宏调用函数 [asin](https://zh.cppreference.com/w/c/numeric/math/asin) 的对应实数版本，实现公式 *asinh(iy) = i asin(y)*，而返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 的复反双曲正弦，其定义域为沿实轴数学上无界，沿虚轴在区间 *[−iπ/2; +iπ/2]* 中的条带。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `casinh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(casinh(z))`
- `casinh(-z) == -casinh(z)`
- 若 `z` 为 `+0+0i`，则结果为 `+0+0i`
- 若 `z` 为 `x+∞i`（对于任何有限正 x），则结果为 `+∞+π/2`
- 若 `z` 为 `x+NaNi`（对于任何有限 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），结果为 `+∞+0i`
- 若 `z` 为 `+∞+∞i`，则结果为 `+∞+iπ/4`
- 若 `z` 为 `+∞+NaNi`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+0i`，则结果为 `NaN+0i`
- 若 `z` 为 `NaN+yi`（对于任何有限非零 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+∞i`，则结果为 `±∞+NaNi`（实部符号未指定）
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**注意**

​	虽然 C 标准命名此函数为“复弧双曲正弦”函数，但双曲函数的反函数仍是面积函数。其参数是双曲扇形的面积，而非弧长。正确的名称是“复反双曲正弦”或较不常用的“复面积双曲正弦”。

​	反双曲正弦是多值函数，而在复平面上要求分支切割。约定将分支置于虚轴的线段 *(-\*i*∞,-\*i*)* 和 *(\*i*,\*i*∞)* 上。

​	反双曲正弦主值的数学定义是 *asinh z = ln(z + √1+z2
)*。

对于任何 z，

asinh(z) = 

| asin(iz) |
| -------- |
| i        |

。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = casinh(0+2*I);
    printf("casinh(+0+2i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = casinh(-conj(2*I)); // 或 C11 中的 casinh(CMPLX(-0.0, 2))
    printf("casinh(-0+2i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    // 对于任何 z，asinh(z) = asin(iz)/i
    double complex z3 = casinh(1+2*I);
    printf("casinh(1+2i) = %f%+fi\n", creal(z3), cimag(z3));
    double complex z4 = casin((1+2*I)*I)/I;
    printf("casin(i * (1+2i))/i = %f%+fi\n", creal(z4), cimag(z4));
}
```

​	输出：

```txt
casinh(+0+2i) = 1.316958+1.570796i
casinh(-0+2i) (the other side of the cut) = -1.316958+1.570796i
casinh(1+2i) = 1.469352+1.063440i
casin(i * (1+2i))/i =  1.469352+1.063440i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.2 The casinh functions （第 192-193 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.2 The casinh functions （第 540 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.2 The casinh functions （第 174-175 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.2 The casinh functions （第 475 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cacosh (C99)<br />cacoshf (C99)<br />cacoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacosh) | 计算复数反双曲余弦 (函数)               |
| ------------------------------------------------------------ | --------------------------------------- |
| [catanh (C99)<br />catanhf (C99)<br />catanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catanh) | 计算复数反双曲正切 (函数)               |
| [csinh (C99)<br />csinhf (C99)<br />csinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csinh) | 计算复数双曲正弦 (函数)                 |
| [asinh (C99)<br />asinhf (C99)<br />asinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asinh) | 计算反双曲正弦（arsinhxarsinh⁡x） (函数) |
| **asinh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/asinh)** |                                         |





### casinhf

原址：[https://zh.cppreference.com/w/c/numeric/complex/casinh](https://zh.cppreference.com/w/c/numeric/complex/casinh)

作用：计算复数反双曲正弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       casinhf( float complex z );// (1)(C99 起)
double complex      casinh( double complex z );// (2)(C99 起)
long double complex casinhl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define asinh( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复反双曲正弦，分支切割在沿虚轴的 *[−i; +i]* 区间外。

4） 泛型宏：若 `z` 拥有类型 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `casinhl`。若 `z` 拥有类型 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `casinh`，若 `z` 拥有类型 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `casinhf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`asinhf`、`[asinh](http://zh.cppreference.com/w/c/numeric/math/asinh)`、`asinhl`）。若 `z` 为虚数，则宏调用函数 [asin](https://zh.cppreference.com/w/c/numeric/math/asin) 的对应实数版本，实现公式 *asinh(iy) = i asin(y)*，而返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 的复反双曲正弦，其定义域为沿实轴数学上无界，沿虚轴在区间 *[−iπ/2; +iπ/2]* 中的条带。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `casinh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(casinh(z))`
- `casinh(-z) == -casinh(z)`
- 若 `z` 为 `+0+0i`，则结果为 `+0+0i`
- 若 `z` 为 `x+∞i`（对于任何有限正 x），则结果为 `+∞+π/2`
- 若 `z` 为 `x+NaNi`（对于任何有限 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），结果为 `+∞+0i`
- 若 `z` 为 `+∞+∞i`，则结果为 `+∞+iπ/4`
- 若 `z` 为 `+∞+NaNi`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+0i`，则结果为 `NaN+0i`
- 若 `z` 为 `NaN+yi`（对于任何有限非零 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+∞i`，则结果为 `±∞+NaNi`（实部符号未指定）
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**注意**

​	虽然 C 标准命名此函数为“复弧双曲正弦”函数，但双曲函数的反函数仍是面积函数。其参数是双曲扇形的面积，而非弧长。正确的名称是“复反双曲正弦”或较不常用的“复面积双曲正弦”。

​	反双曲正弦是多值函数，而在复平面上要求分支切割。约定将分支置于虚轴的线段 *(-\*i*∞,-\*i*)* 和 *(\*i*,\*i*∞)* 上。

​	反双曲正弦主值的数学定义是 *asinh z = ln(z + √1+z2
)*。

对于任何 z，

asinh(z) = 

| asin(iz) |
| -------- |
| i        |

。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = casinh(0+2*I);
    printf("casinh(+0+2i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = casinh(-conj(2*I)); // 或 C11 中的 casinh(CMPLX(-0.0, 2))
    printf("casinh(-0+2i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    // 对于任何 z，asinh(z) = asin(iz)/i
    double complex z3 = casinh(1+2*I);
    printf("casinh(1+2i) = %f%+fi\n", creal(z3), cimag(z3));
    double complex z4 = casin((1+2*I)*I)/I;
    printf("casin(i * (1+2i))/i = %f%+fi\n", creal(z4), cimag(z4));
}
```

​	输出：

```txt
casinh(+0+2i) = 1.316958+1.570796i
casinh(-0+2i) (the other side of the cut) = -1.316958+1.570796i
casinh(1+2i) = 1.469352+1.063440i
casin(i * (1+2i))/i =  1.469352+1.063440i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.2 The casinh functions （第 192-193 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.2 The casinh functions （第 540 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.2 The casinh functions （第 174-175 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.2 The casinh functions （第 475 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cacosh (C99)<br />cacoshf (C99)<br />cacoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacosh) | 计算复数反双曲余弦 (函数)               |
| ------------------------------------------------------------ | --------------------------------------- |
| [catanh (C99)<br />catanhf (C99)<br />catanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catanh) | 计算复数反双曲正切 (函数)               |
| [csinh (C99)<br />csinhf (C99)<br />csinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csinh) | 计算复数双曲正弦 (函数)                 |
| [asinh (C99)<br />asinhf (C99)<br />asinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asinh) | 计算反双曲正弦（arsinhxarsinh⁡x） (函数) |
| **asinh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/asinh)** |                                         |





### casinhl

原址：[https://zh.cppreference.com/w/c/numeric/complex/casinh](https://zh.cppreference.com/w/c/numeric/complex/casinh)

作用：计算复数反双曲正弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       casinhf( float complex z );// (1)(C99 起)
double complex      casinh( double complex z );// (2)(C99 起)
long double complex casinhl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define asinh( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复反双曲正弦，分支切割在沿虚轴的 *[−i; +i]* 区间外。

4） 泛型宏：若 `z` 拥有类型 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `casinhl`。若 `z` 拥有类型 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `casinh`，若 `z` 拥有类型 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `casinhf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`asinhf`、`[asinh](http://zh.cppreference.com/w/c/numeric/math/asinh)`、`asinhl`）。若 `z` 为虚数，则宏调用函数 [asin](https://zh.cppreference.com/w/c/numeric/math/asin) 的对应实数版本，实现公式 *asinh(iy) = i asin(y)*，而返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 的复反双曲正弦，其定义域为沿实轴数学上无界，沿虚轴在区间 *[−iπ/2; +iπ/2]* 中的条带。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `casinh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(casinh(z))`
- `casinh(-z) == -casinh(z)`
- 若 `z` 为 `+0+0i`，则结果为 `+0+0i`
- 若 `z` 为 `x+∞i`（对于任何有限正 x），则结果为 `+∞+π/2`
- 若 `z` 为 `x+NaNi`（对于任何有限 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），结果为 `+∞+0i`
- 若 `z` 为 `+∞+∞i`，则结果为 `+∞+iπ/4`
- 若 `z` 为 `+∞+NaNi`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+0i`，则结果为 `NaN+0i`
- 若 `z` 为 `NaN+yi`（对于任何有限非零 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+∞i`，则结果为 `±∞+NaNi`（实部符号未指定）
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**注意**

​	虽然 C 标准命名此函数为“复弧双曲正弦”函数，但双曲函数的反函数仍是面积函数。其参数是双曲扇形的面积，而非弧长。正确的名称是“复反双曲正弦”或较不常用的“复面积双曲正弦”。

​	反双曲正弦是多值函数，而在复平面上要求分支切割。约定将分支置于虚轴的线段 *(-\*i*∞,-\*i*)* 和 *(\*i*,\*i*∞)* 上。

​	反双曲正弦主值的数学定义是 *asinh z = ln(z + √1+z2
)*。

对于任何 z，

asinh(z) = 

| asin(iz) |
| -------- |
| i        |

。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = casinh(0+2*I);
    printf("casinh(+0+2i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = casinh(-conj(2*I)); // 或 C11 中的 casinh(CMPLX(-0.0, 2))
    printf("casinh(-0+2i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    // 对于任何 z，asinh(z) = asin(iz)/i
    double complex z3 = casinh(1+2*I);
    printf("casinh(1+2i) = %f%+fi\n", creal(z3), cimag(z3));
    double complex z4 = casin((1+2*I)*I)/I;
    printf("casin(i * (1+2i))/i = %f%+fi\n", creal(z4), cimag(z4));
}
```

​	输出：

```txt
casinh(+0+2i) = 1.316958+1.570796i
casinh(-0+2i) (the other side of the cut) = -1.316958+1.570796i
casinh(1+2i) = 1.469352+1.063440i
casin(i * (1+2i))/i =  1.469352+1.063440i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.2 The casinh functions （第 192-193 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.2 The casinh functions （第 540 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.2 The casinh functions （第 174-175 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.2 The casinh functions （第 475 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cacosh (C99)<br />cacoshf (C99)<br />cacoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacosh) | 计算复数反双曲余弦 (函数)               |
| ------------------------------------------------------------ | --------------------------------------- |
| [catanh (C99)<br />catanhf (C99)<br />catanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catanh) | 计算复数反双曲正切 (函数)               |
| [csinh (C99)<br />csinhf (C99)<br />csinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csinh) | 计算复数双曲正弦 (函数)                 |
| [asinh (C99)<br />asinhf (C99)<br />asinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asinh) | 计算反双曲正弦（arsinhxarsinh⁡x） (函数) |
| **asinh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/asinh)** |                                         |





### casinl

原址：[https://zh.cppreference.com/w/c/numeric/complex/casin](https://zh.cppreference.com/w/c/numeric/complex/casin)

作用：计算复数反正弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       casinf( float complex z );// (1)(C99 起)
double complex      casin( double complex z );// (2)(C99 起)
long double complex casinl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define asin( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复反正弦，分支切割线在沿实轴的 *[−1,+1]* 区间外。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `casinl`，若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `casin`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `casinf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`asinf`、`[asin](http://zh.cppreference.com/w/c/numeric/math/asin)`、`asinl`）。若 `z` 为虚数，则宏调用函数 [asinh](https://zh.cppreference.com/w/c/numeric/math/asinh) 的对应实数版本，实现公式 arcsin(iy)=iarsinh(y)arcsin⁡(iy)=iarsinh(y)，而宏的返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 在沿虚轴无界、沿实轴在区间 *[−π/2; +π/2]* 中的条状范围中的复反正弦。

​	如同运算以 `-I * [casinh](http://zh.cppreference.com/w/c/numeric/complex/casinh)(I*z)` 实现一般处理错误和特殊情况。

**注解**

​	反正弦（或弧正弦）是多值函数，且在复平面上要求分支切割。约定将分支切割线置于实轴上的区间 *(-∞,-1)* 和 *(1,∞)* 上。

​	反正弦主值的数学定义是 arcsinz=−iln(iz+√1−z2)arcsin⁡z=−iln⁡(iz+1−z2)。

对于任何 z，arcsin(z)=arccos(−z)−π2arcsin⁡(z)=arccos⁡(−z)−π2。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = casin(-2);
    printf("casin(-2+0i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = casin(conj(-2)); // 或 CMPLX(-2, -0.0)
    printf("casin(-2-0i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    // 对于任何 z，asin(z) = acos(-z) - pi/2
    double pi = acos(-1);
    double complex z3 = csin(cacos(conj(-2))-pi/2);
    printf("csin(cacos(-2-0i)-pi/2) = %f%+fi\n", creal(z3), cimag(z3));
}
```

​	输出：

```txt
casin(-2+0i) = -1.570796+1.316958i
casin(-2-0i) (the other side of the cut) = -1.570796-1.316958i
csin(cacos(-2-0i)-pi/2) = 2.000000+0.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.2 The casin functions （第 190 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.2 The casin functions （第 172 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数)               |
| ------------------------------------------------------------ | ----------------------------------- |
| [catan (C99)<br />catanf (C99)<br />catanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catan) | 计算复数反正切 (函数)               |
| [csin (C99)<br />csinf (C99)<br />csinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csin) | 计算复数正弦 (函数)                 |
| [asin <br />asinf (C99)<br />asinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/asin) | 计算反正弦（arcsinxarcsin⁡x） (函数) |
| **asin** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/asin)** |                                     |





### catan

原址：[https://zh.cppreference.com/w/c/numeric/complex/catan](https://zh.cppreference.com/w/c/numeric/complex/catan)

作用：计算复数反正切  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       catanf( float complex z );// (1)(C99 起)
double complex      catan( double complex z );// (2)(C99 起)
long double complex catanl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define atan( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复弧（反）正切，分支切割在沿虚轴的 *[−i,+i]* 区间外。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catanl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catan`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catanf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`atanf`、`[atan](http://zh.cppreference.com/w/c/numeric/math/atan)`、`atanl`）。若 `z` 为虚数，则宏调用函数 [atanh](https://zh.cppreference.com/w/c/numeric/math/atanh) 的对应实数版本，实现公式 *atan(iy) = i atanh(y)*，而宏的返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不发生错误，则返回 `z` 的复弧（反）正切，在沿虚轴无界，沿实轴在区间 *[−π/2; +π/2]* 内的条状范围中。

​	按照如同以 `-I * [catanh](http://zh.cppreference.com/w/c/numeric/complex/catanh)(I*z)` 实现运算一般处理错误和特殊情况。

**注意**

​	反正切（或弧正切）是多值函数而要求复平面上的分支切割。约定分支切割置于虚轴的线段 *(-∞i,-i)* 和 *(+i,+∞i)* 上。

反正切主值的数学定义是 

atan z = -

| 1    |
| ---- |
| 2    |

 i [ln(1 - iz) - ln (1 + iz]

。

**示例**

```c
#include <stdio.h>
#include <float.h>
#include <complex.h>
 
int main(void)
{
    double complex z = catan(2*I);
    printf("catan(+0+2i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = catan(-conj(2*I)); // 或 CMPLX(-0.0, 2)
    printf("catan(-0+2i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    double complex z3 = 2*catan(2*I*DBL_MAX); // 或 CMPLX(0, INFINITY)
    printf("2*catan(+0+i*Inf) = %f%+fi\n", creal(z3), cimag(z3));
}
```

​	输出：

```txt
catan(+0+2i) = 1.570796+0.549306i
catan(-0+2i) (the other side of the cut) = -1.570796+0.549306i
2*catan(+0+i*Inf) = 3.141593+0.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.3 The catan functions （第 191 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.3 The catan functions （第 173 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [casin (C99)<br />casinf (C99)<br />casinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casin) | 计算复数反正弦 (函数)               |
| ------------------------------------------------------------ | ----------------------------------- |
| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数)               |
| [ctan (C99)<br />ctanf (C99)<br />ctanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctan) | 计算复数正切 (函数)                 |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡x） (函数) |
| **atan** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/atan)** |                                     |





### catanf

原址：[https://zh.cppreference.com/w/c/numeric/complex/catan](https://zh.cppreference.com/w/c/numeric/complex/catan)

作用：计算复数反正切  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       catanf( float complex z );// (1)(C99 起)
double complex      catan( double complex z );// (2)(C99 起)
long double complex catanl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define atan( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复弧（反）正切，分支切割在沿虚轴的 *[−i,+i]* 区间外。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catanl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catan`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catanf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`atanf`、`[atan](http://zh.cppreference.com/w/c/numeric/math/atan)`、`atanl`）。若 `z` 为虚数，则宏调用函数 [atanh](https://zh.cppreference.com/w/c/numeric/math/atanh) 的对应实数版本，实现公式 *atan(iy) = i atanh(y)*，而宏的返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不发生错误，则返回 `z` 的复弧（反）正切，在沿虚轴无界，沿实轴在区间 *[−π/2; +π/2]* 内的条状范围中。

​	按照如同以 `-I * [catanh](http://zh.cppreference.com/w/c/numeric/complex/catanh)(I*z)` 实现运算一般处理错误和特殊情况。

**注意**

​	反正切（或弧正切）是多值函数而要求复平面上的分支切割。约定分支切割置于虚轴的线段 *(-∞i,-i)* 和 *(+i,+∞i)* 上。

反正切主值的数学定义是 

atan z = -

| 1    |
| ---- |
| 2    |

 i [ln(1 - iz) - ln (1 + iz]

。

**示例**

```c
#include <stdio.h>
#include <float.h>
#include <complex.h>
 
int main(void)
{
    double complex z = catan(2*I);
    printf("catan(+0+2i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = catan(-conj(2*I)); // 或 CMPLX(-0.0, 2)
    printf("catan(-0+2i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    double complex z3 = 2*catan(2*I*DBL_MAX); // 或 CMPLX(0, INFINITY)
    printf("2*catan(+0+i*Inf) = %f%+fi\n", creal(z3), cimag(z3));
}
```

​	输出：

```txt
catan(+0+2i) = 1.570796+0.549306i
catan(-0+2i) (the other side of the cut) = -1.570796+0.549306i
2*catan(+0+i*Inf) = 3.141593+0.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.3 The catan functions （第 191 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.3 The catan functions （第 173 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [casin (C99)<br />casinf (C99)<br />casinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casin) | 计算复数反正弦 (函数)               |
| ------------------------------------------------------------ | ----------------------------------- |
| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数)               |
| [ctan (C99)<br />ctanf (C99)<br />ctanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctan) | 计算复数正切 (函数)                 |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡x） (函数) |
| **atan** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/atan)** |                                     |





### catanh

原址：[https://zh.cppreference.com/w/c/numeric/complex/catanh](https://zh.cppreference.com/w/c/numeric/complex/catanh)

作用：计算复数反双曲正切  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       catanhf( float complex z );// (1)(C99 起)
double complex      catanh( double complex z );// (2)(C99 起)
long double complex catanhl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define atanh( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复反双曲正切，其分支切割为沿实轴的 *[−1; +1]* 区间外部。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catanhl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catanh`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catanhf`。若 `z` 为实数或整数，则该宏调用对应的实函数（`atanhf`、`[atanh](http://zh.cppreference.com/w/c/numeric/math/atanh)`、`atanhl`）。若为虚数 `z`，则该宏调用 `[atan](http://zh.cppreference.com/w/c/numeric/math/atan)` 的对应实数版本，实现等式 *atanh(iy) = i atan(y)*，而返回类型是虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不发生错误，则返回 `z` 的复反双曲正切，范围在数学上为沿着实轴无界的半条，沿着虚轴为区间 *[−iπ/2; +iπ/2]* 。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `catanh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(catanh(z))`
- `catanh(-z) == -catanh(z)`
- 若 `z` 为 `+0+0i`，则结果为 `+0+0i`
- 若 `z` 为 `+0+NaNi`，则结果为 `+0+NaNi`
- 若 `z` 为 `+1+0i`，则结果为 `+∞+0i` 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+∞i`（对于任何有限正 x），则结果为 `+0+iπ/2`
- 若 `z` 为 `x+NaNi`（对于任何有限非零的 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+yi`（对于任何有限的 y），则结果为 `+0+iπ/2`
- 若 `z` 为 `+∞+∞i`，则结果为 `+0+iπ/2`
- 若 `z` 为 `+∞+NaNi`，则结果为 `+0+NaNi`
- 若 `z` 为 `NaN+yi`（对于任何有限的 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+∞i`，则结果为 `±0+iπ/2`（实部的符号未指定）
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**注意**

​	虽然 C 标准命名此函数为“复弧双曲正切”，但双曲函数的反函数却是面积函数。其参数是双曲扇形的面积，而非弧长。正确的名称是“复反双曲正切”，和较少见的“复面积双曲正切”。

​	反双曲正切是多值函数，并要求复平面上的分支切割。我们约定将分支切割置于实轴的划分线 *(-∞,-1]* 和 *[+1,+∞)*。

反双曲正切的主值的数学定义是 

atanh z = 

| ln(1+z)-ln(z-1) |
| --------------- |
| 2               |

。 对于任何 z，

atanh(z) = 

| atan(iz) |
| -------- |
| i        |

。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = catanh(2);
    printf("catanh(+2+0i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = catanh(conj(2)); // 或 C11 中的 catanh(CMPLX(2, -0.0))
    printf("catanh(+2-0i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    // 对于任何 z，atanh(z) = atan(iz)/i
    double complex z3 = catanh(1+2*I);
    printf("catanh(1+2i) = %f%+fi\n", creal(z3), cimag(z3));
    double complex z4 = catan((1+2*I)*I)/I;
    printf("catan(i * (1+2i))/i = %f%+fi\n", creal(z4), cimag(z4));
}
```

​	输出：

```txt
catanh(+2+0i) = 0.549306+1.570796i
catanh(+2-0i) (the other side of the cut) = 0.549306-1.570796i
catanh(1+2i) = 0.173287+1.178097i
catan(i * (1+2i))/i = 0.173287+1.178097i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.3 The catanh functions （第 193 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.3 The catanh functions （第 540-541 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.3 The catanh functions （第 175 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.3 The catanh functions （第 475-476 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [casinh (C99)<br />casinhf (C99)<br />casinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casinh) | 计算复数反双曲正弦 (函数)               |
| ------------------------------------------------------------ | --------------------------------------- |
| [cacosh (C99)<br />cacoshf (C99)<br />cacoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacosh) | 计算复数反双曲余弦 (函数)               |
| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)                 |
| [atanh (C99)<br />atanhf (C99)<br />atanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atanh) | 计算反双曲正切（artanhxartanh⁡x） (函数) |
| **atanh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/atanh)** |                                         |





### catanhf

原址：[https://zh.cppreference.com/w/c/numeric/complex/catanh](https://zh.cppreference.com/w/c/numeric/complex/catanh)

作用：计算复数反双曲正切  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       catanhf( float complex z );// (1)(C99 起)
double complex      catanh( double complex z );// (2)(C99 起)
long double complex catanhl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define atanh( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复反双曲正切，其分支切割为沿实轴的 *[−1; +1]* 区间外部。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catanhl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catanh`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catanhf`。若 `z` 为实数或整数，则该宏调用对应的实函数（`atanhf`、`[atanh](http://zh.cppreference.com/w/c/numeric/math/atanh)`、`atanhl`）。若为虚数 `z`，则该宏调用 `[atan](http://zh.cppreference.com/w/c/numeric/math/atan)` 的对应实数版本，实现等式 *atanh(iy) = i atan(y)*，而返回类型是虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不发生错误，则返回 `z` 的复反双曲正切，范围在数学上为沿着实轴无界的半条，沿着虚轴为区间 *[−iπ/2; +iπ/2]* 。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `catanh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(catanh(z))`
- `catanh(-z) == -catanh(z)`
- 若 `z` 为 `+0+0i`，则结果为 `+0+0i`
- 若 `z` 为 `+0+NaNi`，则结果为 `+0+NaNi`
- 若 `z` 为 `+1+0i`，则结果为 `+∞+0i` 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+∞i`（对于任何有限正 x），则结果为 `+0+iπ/2`
- 若 `z` 为 `x+NaNi`（对于任何有限非零的 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+yi`（对于任何有限的 y），则结果为 `+0+iπ/2`
- 若 `z` 为 `+∞+∞i`，则结果为 `+0+iπ/2`
- 若 `z` 为 `+∞+NaNi`，则结果为 `+0+NaNi`
- 若 `z` 为 `NaN+yi`（对于任何有限的 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+∞i`，则结果为 `±0+iπ/2`（实部的符号未指定）
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**注意**

​	虽然 C 标准命名此函数为“复弧双曲正切”，但双曲函数的反函数却是面积函数。其参数是双曲扇形的面积，而非弧长。正确的名称是“复反双曲正切”，和较少见的“复面积双曲正切”。

​	反双曲正切是多值函数，并要求复平面上的分支切割。我们约定将分支切割置于实轴的划分线 *(-∞,-1]* 和 *[+1,+∞)*。

反双曲正切的主值的数学定义是 

atanh z = 

| ln(1+z)-ln(z-1) |
| --------------- |
| 2               |

。 对于任何 z，

atanh(z) = 

| atan(iz) |
| -------- |
| i        |

。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = catanh(2);
    printf("catanh(+2+0i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = catanh(conj(2)); // 或 C11 中的 catanh(CMPLX(2, -0.0))
    printf("catanh(+2-0i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    // 对于任何 z，atanh(z) = atan(iz)/i
    double complex z3 = catanh(1+2*I);
    printf("catanh(1+2i) = %f%+fi\n", creal(z3), cimag(z3));
    double complex z4 = catan((1+2*I)*I)/I;
    printf("catan(i * (1+2i))/i = %f%+fi\n", creal(z4), cimag(z4));
}
```

​	输出：

```txt
catanh(+2+0i) = 0.549306+1.570796i
catanh(+2-0i) (the other side of the cut) = 0.549306-1.570796i
catanh(1+2i) = 0.173287+1.178097i
catan(i * (1+2i))/i = 0.173287+1.178097i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.3 The catanh functions （第 193 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.3 The catanh functions （第 540-541 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.3 The catanh functions （第 175 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.3 The catanh functions （第 475-476 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [casinh (C99)<br />casinhf (C99)<br />casinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casinh) | 计算复数反双曲正弦 (函数)               |
| ------------------------------------------------------------ | --------------------------------------- |
| [cacosh (C99)<br />cacoshf (C99)<br />cacoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacosh) | 计算复数反双曲余弦 (函数)               |
| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)                 |
| [atanh (C99)<br />atanhf (C99)<br />atanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atanh) | 计算反双曲正切（artanhxartanh⁡x） (函数) |
| **atanh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/atanh)** |                                         |





### catanhl

原址：[https://zh.cppreference.com/w/c/numeric/complex/catanh](https://zh.cppreference.com/w/c/numeric/complex/catanh)

作用：计算复数反双曲正切  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       catanhf( float complex z );// (1)(C99 起)
double complex      catanh( double complex z );// (2)(C99 起)
long double complex catanhl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define atanh( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复反双曲正切，其分支切割为沿实轴的 *[−1; +1]* 区间外部。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catanhl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catanh`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catanhf`。若 `z` 为实数或整数，则该宏调用对应的实函数（`atanhf`、`[atanh](http://zh.cppreference.com/w/c/numeric/math/atanh)`、`atanhl`）。若为虚数 `z`，则该宏调用 `[atan](http://zh.cppreference.com/w/c/numeric/math/atan)` 的对应实数版本，实现等式 *atanh(iy) = i atan(y)*，而返回类型是虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不发生错误，则返回 `z` 的复反双曲正切，范围在数学上为沿着实轴无界的半条，沿着虚轴为区间 *[−iπ/2; +iπ/2]* 。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `catanh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(catanh(z))`
- `catanh(-z) == -catanh(z)`
- 若 `z` 为 `+0+0i`，则结果为 `+0+0i`
- 若 `z` 为 `+0+NaNi`，则结果为 `+0+NaNi`
- 若 `z` 为 `+1+0i`，则结果为 `+∞+0i` 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+∞i`（对于任何有限正 x），则结果为 `+0+iπ/2`
- 若 `z` 为 `x+NaNi`（对于任何有限非零的 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+yi`（对于任何有限的 y），则结果为 `+0+iπ/2`
- 若 `z` 为 `+∞+∞i`，则结果为 `+0+iπ/2`
- 若 `z` 为 `+∞+NaNi`，则结果为 `+0+NaNi`
- 若 `z` 为 `NaN+yi`（对于任何有限的 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+∞i`，则结果为 `±0+iπ/2`（实部的符号未指定）
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**注意**

​	虽然 C 标准命名此函数为“复弧双曲正切”，但双曲函数的反函数却是面积函数。其参数是双曲扇形的面积，而非弧长。正确的名称是“复反双曲正切”，和较少见的“复面积双曲正切”。

​	反双曲正切是多值函数，并要求复平面上的分支切割。我们约定将分支切割置于实轴的划分线 *(-∞,-1]* 和 *[+1,+∞)*。

反双曲正切的主值的数学定义是 

atanh z = 

| ln(1+z)-ln(z-1) |
| --------------- |
| 2               |

。 对于任何 z，

atanh(z) = 

| atan(iz) |
| -------- |
| i        |

。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = catanh(2);
    printf("catanh(+2+0i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = catanh(conj(2)); // 或 C11 中的 catanh(CMPLX(2, -0.0))
    printf("catanh(+2-0i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    // 对于任何 z，atanh(z) = atan(iz)/i
    double complex z3 = catanh(1+2*I);
    printf("catanh(1+2i) = %f%+fi\n", creal(z3), cimag(z3));
    double complex z4 = catan((1+2*I)*I)/I;
    printf("catan(i * (1+2i))/i = %f%+fi\n", creal(z4), cimag(z4));
}
```

​	输出：

```txt
catanh(+2+0i) = 0.549306+1.570796i
catanh(+2-0i) (the other side of the cut) = 0.549306-1.570796i
catanh(1+2i) = 0.173287+1.178097i
catan(i * (1+2i))/i = 0.173287+1.178097i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.3 The catanh functions （第 193 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.3 The catanh functions （第 540-541 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.3 The catanh functions （第 175 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.3 The catanh functions （第 475-476 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [casinh (C99)<br />casinhf (C99)<br />casinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casinh) | 计算复数反双曲正弦 (函数)               |
| ------------------------------------------------------------ | --------------------------------------- |
| [cacosh (C99)<br />cacoshf (C99)<br />cacoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacosh) | 计算复数反双曲余弦 (函数)               |
| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)                 |
| [atanh (C99)<br />atanhf (C99)<br />atanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atanh) | 计算反双曲正切（artanhxartanh⁡x） (函数) |
| **atanh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/atanh)** |                                         |





### catanl

原址：[https://zh.cppreference.com/w/c/numeric/complex/catan](https://zh.cppreference.com/w/c/numeric/complex/catan)

作用：计算复数反正切  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       catanf( float complex z );// (1)(C99 起)
double complex      catan( double complex z );// (2)(C99 起)
long double complex catanl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define atan( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复弧（反）正切，分支切割在沿虚轴的 *[−i,+i]* 区间外。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catanl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catan`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `catanf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`atanf`、`[atan](http://zh.cppreference.com/w/c/numeric/math/atan)`、`atanl`）。若 `z` 为虚数，则宏调用函数 [atanh](https://zh.cppreference.com/w/c/numeric/math/atanh) 的对应实数版本，实现公式 *atan(iy) = i atanh(y)*，而宏的返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不发生错误，则返回 `z` 的复弧（反）正切，在沿虚轴无界，沿实轴在区间 *[−π/2; +π/2]* 内的条状范围中。

​	按照如同以 `-I * [catanh](http://zh.cppreference.com/w/c/numeric/complex/catanh)(I*z)` 实现运算一般处理错误和特殊情况。

**注意**

​	反正切（或弧正切）是多值函数而要求复平面上的分支切割。约定分支切割置于虚轴的线段 *(-∞i,-i)* 和 *(+i,+∞i)* 上。

反正切主值的数学定义是 

atan z = -

| 1    |
| ---- |
| 2    |

 i [ln(1 - iz) - ln (1 + iz]

。

**示例**

```c
#include <stdio.h>
#include <float.h>
#include <complex.h>
 
int main(void)
{
    double complex z = catan(2*I);
    printf("catan(+0+2i) = %f%+fi\n", creal(z), cimag(z));
 
    double complex z2 = catan(-conj(2*I)); // 或 CMPLX(-0.0, 2)
    printf("catan(-0+2i) (the other side of the cut) = %f%+fi\n", creal(z2), cimag(z2));
 
    double complex z3 = 2*catan(2*I*DBL_MAX); // 或 CMPLX(0, INFINITY)
    printf("2*catan(+0+i*Inf) = %f%+fi\n", creal(z3), cimag(z3));
}
```

​	输出：

```txt
catan(+0+2i) = 1.570796+0.549306i
catan(-0+2i) (the other side of the cut) = -1.570796+0.549306i
2*catan(+0+i*Inf) = 3.141593+0.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.3 The catan functions （第 191 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.3 The catan functions （第 173 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [casin (C99)<br />casinf (C99)<br />casinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casin) | 计算复数反正弦 (函数)               |
| ------------------------------------------------------------ | ----------------------------------- |
| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数)               |
| [ctan (C99)<br />ctanf (C99)<br />ctanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctan) | 计算复数正切 (函数)                 |
| [atan <br />atanf (C99)<br />atanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/atan) | 计算反正切（arctanxarctan⁡x） (函数) |
| **atan** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/atan)** |                                     |





### ccos

原址：[https://zh.cppreference.com/w/c/numeric/complex/ccos](https://zh.cppreference.com/w/c/numeric/complex/ccos)

作用：计算复数余弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       ccosf( float complex z );// (1)(C99 起)
double complex      ccos( double complex z );// (2)(C99 起)
long double complex ccosl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cos( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复余弦。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccosl`，若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccos`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccosf`。若 `z` 为实数或整数，则此宏调用对应的实函数（`cosf`、`[cos](http://zh.cppreference.com/w/c/numeric/math/cos)`、`cosl`）。若 `z` 是虚数，则此宏调用对应版本的 [cosh](https://zh.cppreference.com/w/c/numeric/math/cosh) 函数，实现公式 *cos(iy) = cosh(y)*，而返回类型是实数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若无错误发生，则返回 `z` 的复余弦。

​	错误和特殊情况如同操作以 `[ccosh](http://zh.cppreference.com/w/c/numeric/complex/ccosh)(I*z)` 实现一般。

**注意**

​	余弦在复平面上是整函数，而且无分支切割。

余弦的数学定义是 

cos z = 

| eiz +e-iz |
| --------- |
| 2         |

。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = ccos(1);  // 表现如同沿着实轴的实余弦
    printf("cos(1+0i) = %f%+fi ( cos(1)=%f)\n", creal(z), cimag(z), cos(1));
 
    double complex z2 = ccos(I); // 表现如同沿着虚轴的实 cosh
    printf("cos(0+1i) = %f%+fi (cosh(1)=%f)\n", creal(z2), cimag(z2), cosh(1));
}
```

​	输出：

```txt
cos(1+0i) = 0.540302-0.000000i ( cos(1)=0.540302)
cos(0+1i) = 1.543081-0.000000i (cosh(1)=1.543081)
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.4 The ccos functions （第 191 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.4 The ccos functions （第 173 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [csin (C99)<br />csinf (C99)<br />csinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csin) | 计算复数正弦 (函数)         |
| ------------------------------------------------------------ | --------------------------- |
| [ctan (C99)<br />ctanf (C99)<br />ctanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctan) | 计算复数正切 (函数)         |
| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数)       |
| [cos <br />cosf (C99)<br />cosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cos) | 计算余弦（cosxcos⁡x） (函数) |
| **cos** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/cos)** |                             |





### ccosf

原址：[https://zh.cppreference.com/w/c/numeric/complex/ccos](https://zh.cppreference.com/w/c/numeric/complex/ccos)

作用：计算复数余弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       ccosf( float complex z );// (1)(C99 起)
double complex      ccos( double complex z );// (2)(C99 起)
long double complex ccosl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cos( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复余弦。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccosl`，若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccos`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccosf`。若 `z` 为实数或整数，则此宏调用对应的实函数（`cosf`、`[cos](http://zh.cppreference.com/w/c/numeric/math/cos)`、`cosl`）。若 `z` 是虚数，则此宏调用对应版本的 [cosh](https://zh.cppreference.com/w/c/numeric/math/cosh) 函数，实现公式 *cos(iy) = cosh(y)*，而返回类型是实数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若无错误发生，则返回 `z` 的复余弦。

​	错误和特殊情况如同操作以 `[ccosh](http://zh.cppreference.com/w/c/numeric/complex/ccosh)(I*z)` 实现一般。

**注意**

​	余弦在复平面上是整函数，而且无分支切割。

余弦的数学定义是 

cos z = 

| eiz +e-iz |
| --------- |
| 2         |

。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = ccos(1);  // 表现如同沿着实轴的实余弦
    printf("cos(1+0i) = %f%+fi ( cos(1)=%f)\n", creal(z), cimag(z), cos(1));
 
    double complex z2 = ccos(I); // 表现如同沿着虚轴的实 cosh
    printf("cos(0+1i) = %f%+fi (cosh(1)=%f)\n", creal(z2), cimag(z2), cosh(1));
}
```

​	输出：

```txt
cos(1+0i) = 0.540302-0.000000i ( cos(1)=0.540302)
cos(0+1i) = 1.543081-0.000000i (cosh(1)=1.543081)
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.4 The ccos functions （第 191 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.4 The ccos functions （第 173 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [csin (C99)<br />csinf (C99)<br />csinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csin) | 计算复数正弦 (函数)         |
| ------------------------------------------------------------ | --------------------------- |
| [ctan (C99)<br />ctanf (C99)<br />ctanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctan) | 计算复数正切 (函数)         |
| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数)       |
| [cos <br />cosf (C99)<br />cosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cos) | 计算余弦（cosxcos⁡x） (函数) |
| **cos** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/cos)** |                             |





### ccosh

原址：[https://zh.cppreference.com/w/c/numeric/complex/ccosh](https://zh.cppreference.com/w/c/numeric/complex/ccosh)

作用：计算复双曲余弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       ccoshf( float complex z );// (1)(C99 起)
double complex      ccosh( double complex z );// (2)(C99 起)
long double complex ccoshl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cosh( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复双曲余弦。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccoshl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccosh`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccoshf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`coshf`、`[cosh](http://zh.cppreference.com/w/c/numeric/math/cosh)`、`coshl`）。若 `z` 为虚数，则宏调用函数 [cos](https://zh.cppreference.com/w/c/numeric/math/cos) 的对应实数版本，实现公式 *cosh(iy) = cos(y)*，而返回类型为实数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不发生错误，则返回 `z` 的复双曲余弦。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则，

- `ccosh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(ccosh(z))`
- `ccosh(z) == ccosh(-z)`
- 若 `z` 为 `+0+0i`，则结果为 `1+0i`
- 若 `z` 为 `+0+∞i`，则结果为 `NaN±0i`（虚部符号未指定）并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+0+NaNi`，则结果为 `NaN±0i`（虚部符号未指定）
- 若 `z` 为 `x+∞i`（对于任何有限非零 x），则结果为 `NaN+NaNi` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+NaNi`（对于任何有限非零 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+0i`，则结果为 `+∞+0i`
- 若 `z` 为 `+∞+yi`（对于任何有限非零 y），则结果为 `+∞cis(y)`
- 若 `z` 为 `+∞+∞i`，则结果为 `±∞+NaNi`（实部符号未指定）并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+NaN`，则结果为 `+∞+NaN`
- 若 `z` 为 `NaN+0i`，则结果为 `NaN±0i`（虚部符号未指定）
- 若 `z` 为 `NaN+yi`（对于任何有限非零 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

​	其中 *cis(y)* 为 *cos(y) + i sin(y)*。

**注意**

双曲余弦的数学定义是 

cosh z = 

| ez +e-z |
| ------- |
| 2       |

。

​	双曲余弦在复平面上是整函数，而无分支切割。它相对于虚部是周期的，周期为 2πi。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = ccosh(1);  // 表现如沿实轴的实 cosh
    printf("cosh(1+0i) = %f%+fi (cosh(1)=%f)\n", creal(z), cimag(z), cosh(1));
 
    double complex z2 = ccosh(I); // 表现如沿虚轴的实余弦
    printf("cosh(0+1i) = %f%+fi ( cos(1)=%f)\n", creal(z2), cimag(z2), cos(1));
}
```

​	输出：

```txt
cosh(1+0i) = 1.543081+0.000000i (cosh(1)=1.543081)
cosh(0+1i) = 0.540302+0.000000i ( cos(1)=0.540302)
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.4 The ccosh functions （第 193 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.4 The ccosh functions （第 541 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.4 The ccosh functions （第 175 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.4 The ccosh functions （第 476 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [csinh (C99)<br />csinhf (C99)<br />csinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csinh) | 计算复数双曲正弦 (函数)           |
| ------------------------------------------------------------ | --------------------------------- |
| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)           |
| [cacosh (C99)<br />cacoshf (C99)<br />cacoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacosh) | 计算复数反双曲余弦 (函数)         |
| [cosh <br />coshf (C99)<br />coshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cosh) | 计算双曲余弦（coshxcosh⁡x） (函数) |
| **cosh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/cosh)** |                                   |





### ccoshf

原址：[https://zh.cppreference.com/w/c/numeric/complex/ccosh](https://zh.cppreference.com/w/c/numeric/complex/ccosh)

作用：计算复双曲余弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       ccoshf( float complex z );// (1)(C99 起)
double complex      ccosh( double complex z );// (2)(C99 起)
long double complex ccoshl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cosh( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复双曲余弦。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccoshl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccosh`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccoshf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`coshf`、`[cosh](http://zh.cppreference.com/w/c/numeric/math/cosh)`、`coshl`）。若 `z` 为虚数，则宏调用函数 [cos](https://zh.cppreference.com/w/c/numeric/math/cos) 的对应实数版本，实现公式 *cosh(iy) = cos(y)*，而返回类型为实数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不发生错误，则返回 `z` 的复双曲余弦。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则，

- `ccosh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(ccosh(z))`
- `ccosh(z) == ccosh(-z)`
- 若 `z` 为 `+0+0i`，则结果为 `1+0i`
- 若 `z` 为 `+0+∞i`，则结果为 `NaN±0i`（虚部符号未指定）并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+0+NaNi`，则结果为 `NaN±0i`（虚部符号未指定）
- 若 `z` 为 `x+∞i`（对于任何有限非零 x），则结果为 `NaN+NaNi` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+NaNi`（对于任何有限非零 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+0i`，则结果为 `+∞+0i`
- 若 `z` 为 `+∞+yi`（对于任何有限非零 y），则结果为 `+∞cis(y)`
- 若 `z` 为 `+∞+∞i`，则结果为 `±∞+NaNi`（实部符号未指定）并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+NaN`，则结果为 `+∞+NaN`
- 若 `z` 为 `NaN+0i`，则结果为 `NaN±0i`（虚部符号未指定）
- 若 `z` 为 `NaN+yi`（对于任何有限非零 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

​	其中 *cis(y)* 为 *cos(y) + i sin(y)*。

**注意**

双曲余弦的数学定义是 

cosh z = 

| ez +e-z |
| ------- |
| 2       |

。

​	双曲余弦在复平面上是整函数，而无分支切割。它相对于虚部是周期的，周期为 2πi。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = ccosh(1);  // 表现如沿实轴的实 cosh
    printf("cosh(1+0i) = %f%+fi (cosh(1)=%f)\n", creal(z), cimag(z), cosh(1));
 
    double complex z2 = ccosh(I); // 表现如沿虚轴的实余弦
    printf("cosh(0+1i) = %f%+fi ( cos(1)=%f)\n", creal(z2), cimag(z2), cos(1));
}
```

​	输出：

```txt
cosh(1+0i) = 1.543081+0.000000i (cosh(1)=1.543081)
cosh(0+1i) = 0.540302+0.000000i ( cos(1)=0.540302)
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.4 The ccosh functions （第 193 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.4 The ccosh functions （第 541 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.4 The ccosh functions （第 175 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.4 The ccosh functions （第 476 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [csinh (C99)<br />csinhf (C99)<br />csinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csinh) | 计算复数双曲正弦 (函数)           |
| ------------------------------------------------------------ | --------------------------------- |
| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)           |
| [cacosh (C99)<br />cacoshf (C99)<br />cacoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacosh) | 计算复数反双曲余弦 (函数)         |
| [cosh <br />coshf (C99)<br />coshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cosh) | 计算双曲余弦（coshxcosh⁡x） (函数) |
| **cosh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/cosh)** |                                   |





### ccoshl

原址：[https://zh.cppreference.com/w/c/numeric/complex/ccosh](https://zh.cppreference.com/w/c/numeric/complex/ccosh)

作用：计算复双曲余弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       ccoshf( float complex z );// (1)(C99 起)
double complex      ccosh( double complex z );// (2)(C99 起)
long double complex ccoshl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cosh( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复双曲余弦。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccoshl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccosh`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccoshf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`coshf`、`[cosh](http://zh.cppreference.com/w/c/numeric/math/cosh)`、`coshl`）。若 `z` 为虚数，则宏调用函数 [cos](https://zh.cppreference.com/w/c/numeric/math/cos) 的对应实数版本，实现公式 *cosh(iy) = cos(y)*，而返回类型为实数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不发生错误，则返回 `z` 的复双曲余弦。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则，

- `ccosh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(ccosh(z))`
- `ccosh(z) == ccosh(-z)`
- 若 `z` 为 `+0+0i`，则结果为 `1+0i`
- 若 `z` 为 `+0+∞i`，则结果为 `NaN±0i`（虚部符号未指定）并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+0+NaNi`，则结果为 `NaN±0i`（虚部符号未指定）
- 若 `z` 为 `x+∞i`（对于任何有限非零 x），则结果为 `NaN+NaNi` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+NaNi`（对于任何有限非零 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+0i`，则结果为 `+∞+0i`
- 若 `z` 为 `+∞+yi`（对于任何有限非零 y），则结果为 `+∞cis(y)`
- 若 `z` 为 `+∞+∞i`，则结果为 `±∞+NaNi`（实部符号未指定）并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+NaN`，则结果为 `+∞+NaN`
- 若 `z` 为 `NaN+0i`，则结果为 `NaN±0i`（虚部符号未指定）
- 若 `z` 为 `NaN+yi`（对于任何有限非零 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

​	其中 *cis(y)* 为 *cos(y) + i sin(y)*。

**注意**

双曲余弦的数学定义是 

cosh z = 

| ez +e-z |
| ------- |
| 2       |

。

​	双曲余弦在复平面上是整函数，而无分支切割。它相对于虚部是周期的，周期为 2πi。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = ccosh(1);  // 表现如沿实轴的实 cosh
    printf("cosh(1+0i) = %f%+fi (cosh(1)=%f)\n", creal(z), cimag(z), cosh(1));
 
    double complex z2 = ccosh(I); // 表现如沿虚轴的实余弦
    printf("cosh(0+1i) = %f%+fi ( cos(1)=%f)\n", creal(z2), cimag(z2), cos(1));
}
```

​	输出：

```txt
cosh(1+0i) = 1.543081+0.000000i (cosh(1)=1.543081)
cosh(0+1i) = 0.540302+0.000000i ( cos(1)=0.540302)
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.4 The ccosh functions （第 193 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.4 The ccosh functions （第 541 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.4 The ccosh functions （第 175 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.4 The ccosh functions （第 476 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [csinh (C99)<br />csinhf (C99)<br />csinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csinh) | 计算复数双曲正弦 (函数)           |
| ------------------------------------------------------------ | --------------------------------- |
| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)           |
| [cacosh (C99)<br />cacoshf (C99)<br />cacoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacosh) | 计算复数反双曲余弦 (函数)         |
| [cosh <br />coshf (C99)<br />coshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cosh) | 计算双曲余弦（coshxcosh⁡x） (函数) |
| **cosh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/cosh)** |                                   |





### ccosl

原址：[https://zh.cppreference.com/w/c/numeric/complex/ccos](https://zh.cppreference.com/w/c/numeric/complex/ccos)

作用：计算复数余弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       ccosf( float complex z );// (1)(C99 起)
double complex      ccos( double complex z );// (2)(C99 起)
long double complex ccosl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cos( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复余弦。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccosl`，若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccos`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ccosf`。若 `z` 为实数或整数，则此宏调用对应的实函数（`cosf`、`[cos](http://zh.cppreference.com/w/c/numeric/math/cos)`、`cosl`）。若 `z` 是虚数，则此宏调用对应版本的 [cosh](https://zh.cppreference.com/w/c/numeric/math/cosh) 函数，实现公式 *cos(iy) = cosh(y)*，而返回类型是实数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若无错误发生，则返回 `z` 的复余弦。

​	错误和特殊情况如同操作以 `[ccosh](http://zh.cppreference.com/w/c/numeric/complex/ccosh)(I*z)` 实现一般。

**注意**

​	余弦在复平面上是整函数，而且无分支切割。

余弦的数学定义是 

cos z = 

| eiz +e-iz |
| --------- |
| 2         |

。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = ccos(1);  // 表现如同沿着实轴的实余弦
    printf("cos(1+0i) = %f%+fi ( cos(1)=%f)\n", creal(z), cimag(z), cos(1));
 
    double complex z2 = ccos(I); // 表现如同沿着虚轴的实 cosh
    printf("cos(0+1i) = %f%+fi (cosh(1)=%f)\n", creal(z2), cimag(z2), cosh(1));
}
```

​	输出：

```txt
cos(1+0i) = 0.540302-0.000000i ( cos(1)=0.540302)
cos(0+1i) = 1.543081-0.000000i (cosh(1)=1.543081)
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.4 The ccos functions （第 191 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.4 The ccos functions （第 173 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [csin (C99)<br />csinf (C99)<br />csinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csin) | 计算复数正弦 (函数)         |
| ------------------------------------------------------------ | --------------------------- |
| [ctan (C99)<br />ctanf (C99)<br />ctanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctan) | 计算复数正切 (函数)         |
| [cacos (C99)<br />cacosf (C99)<br />cacosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cacos) | 计算复数反余弦 (函数)       |
| [cos <br />cosf (C99)<br />cosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/cos) | 计算余弦（cosxcos⁡x） (函数) |
| **cos** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/cos)** |                             |





### cexp

原址：[https://zh.cppreference.com/w/c/numeric/complex/cexp](https://zh.cppreference.com/w/c/numeric/complex/cexp)

作用：计算复数的 e 底指数  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       cexpf( float complex z );// (1)(C99 起)
double complex      cexp( double complex z );// (2)(C99 起)
long double complex cexpl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define exp( z )// (4)(C99 起)
```

1-3) 计算复数的 `z` 的以 *e* 为底的指数。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cexpl`，若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cexp`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cexpf`。若 `z` 是实浮点数或整数，则该宏调用对应的实函数（`expf`、`[exp](http://zh.cppreference.com/w/c/numeric/math/exp)`、`expl`）。若 `z` 是虚数，则调用对应的复参数版本。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 *e* 的 `z` 次幂，ezez。

**错误处理**及特殊值

​	报告的错误与 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持IEEE浮点算术，则

- `cexp([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(cexp(z))`
- 若 `z` 为 `±0+0i`，则结果是 `1+0i`
- 若 `z` 为 `x+∞i`（对于任何有限 x），则结果是 `NaN+NaNi` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+NaNi`（对于任何有限 x），则结果是 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+0i`，则结果是`+∞+0i`
- 若 `z` 为 `-∞+yi`（对任何有限 y），则结果是 `+0cis(y)`
- 若 `z` 为 `+∞+yi`（对于任何有限非零 y），则结果是 `+∞cis(y)`
- 若 `z` 为 `-∞+∞i`，则结果是 `±0±0i`（符号未指定）
- 若 `z` 为 `+∞+∞i`，则结果是 `±∞+NaNi` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)（实部符号未指定）
- 若 `z` 为 `-∞+NaNi`，则结果是 `±0±0i`（符号未指定）
- 若 `z` 为 `+∞+NaNi`，则结果是 `±∞+NaNi`（实部符号未指定）
- 若 `z` 为 `NaN+0i`，则结果是 `NaN+0i`
- 若 `z` 为 `NaN+yi`（对于任意非零 y），则结果是 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+NaNi`，则结果是 `NaN+NaNi`

​	其中 cis(y)cis(y) 为 cos(y)+isin(y)cos⁡(y)+isin⁡(y)。

**注解**

​	对于 z=x+iyz=x+iy，复指数函数 ezez 等于 excis(y)excis(y)，或 ex(cos(y)+isin(y))ex(cos⁡(y)+isin⁡(y))。

​	指数函数在复平面上是*整函数*且无分支切割。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double PI = acos(-1);
    double complex z = cexp(I * PI); // 欧拉公式
    printf("exp(i*pi) = %.1f%+.1fi\n", creal(z), cimag(z));
 
}
```

​	输出：

```txt
exp(i*pi) = -1.0+0.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.7.1 The cexp functions （第 194 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.3.1 The cexp functions （第 543 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.7.1 The cexp functions （第 176 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.3.1 The cexp functions （第 478 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [clog (C99)<br />clogf (C99)<br />clogl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/clog) | 计算复数的自然对数 (函数)          |
| ------------------------------------------------------------ | ---------------------------------- |
| [exp <br />expf (C99)<br />expl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp) | 计算 *e* 的给定次幂（exex） (函数) |
| **exp** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/exp)** |                                    |





### cexpf

原址：[https://zh.cppreference.com/w/c/numeric/complex/cexp](https://zh.cppreference.com/w/c/numeric/complex/cexp)

作用：计算复数的 e 底指数  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       cexpf( float complex z );// (1)(C99 起)
double complex      cexp( double complex z );// (2)(C99 起)
long double complex cexpl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define exp( z )// (4)(C99 起)
```

1-3) 计算复数的 `z` 的以 *e* 为底的指数。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cexpl`，若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cexp`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cexpf`。若 `z` 是实浮点数或整数，则该宏调用对应的实函数（`expf`、`[exp](http://zh.cppreference.com/w/c/numeric/math/exp)`、`expl`）。若 `z` 是虚数，则调用对应的复参数版本。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 *e* 的 `z` 次幂，ezez。

**错误处理**及特殊值

​	报告的错误与 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持IEEE浮点算术，则

- `cexp([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(cexp(z))`
- 若 `z` 为 `±0+0i`，则结果是 `1+0i`
- 若 `z` 为 `x+∞i`（对于任何有限 x），则结果是 `NaN+NaNi` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+NaNi`（对于任何有限 x），则结果是 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+0i`，则结果是`+∞+0i`
- 若 `z` 为 `-∞+yi`（对任何有限 y），则结果是 `+0cis(y)`
- 若 `z` 为 `+∞+yi`（对于任何有限非零 y），则结果是 `+∞cis(y)`
- 若 `z` 为 `-∞+∞i`，则结果是 `±0±0i`（符号未指定）
- 若 `z` 为 `+∞+∞i`，则结果是 `±∞+NaNi` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)（实部符号未指定）
- 若 `z` 为 `-∞+NaNi`，则结果是 `±0±0i`（符号未指定）
- 若 `z` 为 `+∞+NaNi`，则结果是 `±∞+NaNi`（实部符号未指定）
- 若 `z` 为 `NaN+0i`，则结果是 `NaN+0i`
- 若 `z` 为 `NaN+yi`（对于任意非零 y），则结果是 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+NaNi`，则结果是 `NaN+NaNi`

​	其中 cis(y)cis(y) 为 cos(y)+isin(y)cos⁡(y)+isin⁡(y)。

**注解**

​	对于 z=x+iyz=x+iy，复指数函数 ezez 等于 excis(y)excis(y)，或 ex(cos(y)+isin(y))ex(cos⁡(y)+isin⁡(y))。

​	指数函数在复平面上是*整函数*且无分支切割。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double PI = acos(-1);
    double complex z = cexp(I * PI); // 欧拉公式
    printf("exp(i*pi) = %.1f%+.1fi\n", creal(z), cimag(z));
 
}
```

​	输出：

```txt
exp(i*pi) = -1.0+0.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.7.1 The cexp functions （第 194 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.3.1 The cexp functions （第 543 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.7.1 The cexp functions （第 176 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.3.1 The cexp functions （第 478 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [clog (C99)<br />clogf (C99)<br />clogl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/clog) | 计算复数的自然对数 (函数)          |
| ------------------------------------------------------------ | ---------------------------------- |
| [exp <br />expf (C99)<br />expl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp) | 计算 *e* 的给定次幂（exex） (函数) |
| **exp** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/exp)** |                                    |





### cexpl

原址：[https://zh.cppreference.com/w/c/numeric/complex/cexp](https://zh.cppreference.com/w/c/numeric/complex/cexp)

作用：计算复数的 e 底指数  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       cexpf( float complex z );// (1)(C99 起)
double complex      cexp( double complex z );// (2)(C99 起)
long double complex cexpl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define exp( z )// (4)(C99 起)
```

1-3) 计算复数的 `z` 的以 *e* 为底的指数。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cexpl`，若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cexp`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cexpf`。若 `z` 是实浮点数或整数，则该宏调用对应的实函数（`expf`、`[exp](http://zh.cppreference.com/w/c/numeric/math/exp)`、`expl`）。若 `z` 是虚数，则调用对应的复参数版本。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 *e* 的 `z` 次幂，ezez。

**错误处理**及特殊值

​	报告的错误与 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持IEEE浮点算术，则

- `cexp([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(cexp(z))`
- 若 `z` 为 `±0+0i`，则结果是 `1+0i`
- 若 `z` 为 `x+∞i`（对于任何有限 x），则结果是 `NaN+NaNi` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+NaNi`（对于任何有限 x），则结果是 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+0i`，则结果是`+∞+0i`
- 若 `z` 为 `-∞+yi`（对任何有限 y），则结果是 `+0cis(y)`
- 若 `z` 为 `+∞+yi`（对于任何有限非零 y），则结果是 `+∞cis(y)`
- 若 `z` 为 `-∞+∞i`，则结果是 `±0±0i`（符号未指定）
- 若 `z` 为 `+∞+∞i`，则结果是 `±∞+NaNi` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)（实部符号未指定）
- 若 `z` 为 `-∞+NaNi`，则结果是 `±0±0i`（符号未指定）
- 若 `z` 为 `+∞+NaNi`，则结果是 `±∞+NaNi`（实部符号未指定）
- 若 `z` 为 `NaN+0i`，则结果是 `NaN+0i`
- 若 `z` 为 `NaN+yi`（对于任意非零 y），则结果是 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+NaNi`，则结果是 `NaN+NaNi`

​	其中 cis(y)cis(y) 为 cos(y)+isin(y)cos⁡(y)+isin⁡(y)。

**注解**

​	对于 z=x+iyz=x+iy，复指数函数 ezez 等于 excis(y)excis(y)，或 ex(cos(y)+isin(y))ex(cos⁡(y)+isin⁡(y))。

​	指数函数在复平面上是*整函数*且无分支切割。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double PI = acos(-1);
    double complex z = cexp(I * PI); // 欧拉公式
    printf("exp(i*pi) = %.1f%+.1fi\n", creal(z), cimag(z));
 
}
```

​	输出：

```txt
exp(i*pi) = -1.0+0.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.7.1 The cexp functions （第 194 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.3.1 The cexp functions （第 543 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.7.1 The cexp functions （第 176 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.3.1 The cexp functions （第 478 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [clog (C99)<br />clogf (C99)<br />clogl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/clog) | 计算复数的自然对数 (函数)          |
| ------------------------------------------------------------ | ---------------------------------- |
| [exp <br />expf (C99)<br />expl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/exp) | 计算 *e* 的给定次幂（exex） (函数) |
| **exp** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/exp)** |                                    |





### cimag

原址：[https://zh.cppreference.com/w/c/numeric/complex/cimag](https://zh.cppreference.com/w/c/numeric/complex/cimag)

作用：计算复数的虚部  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float       cimagf( float complex z );// (1)(C99 起)
double      cimag( double complex z );// (2)(C99 起)
long double cimagl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cimag( z )// (4)(C99 起)
```

1-3) 返回 `z` 的虚部。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `long double` 类型，则调用 `cimagl`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `float` 类型，则调用 `cimagf`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)`、`double` 或任何整数类型，则调用 `cimag`。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	`z` 的虚部。

​	此函数对所有可行输入完全指明，而且不受制于任何描述于 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

**注意**

​	对于任何复数变量 `z`，`z == [creal](http://zh.cppreference.com/w/c/numeric/complex/creal)(z) + I*cimag(z)`。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{    
    double complex z = 1.0 + 2.0*I;
    printf("%f%+fi\n", creal(z), cimag(z));
}
```

​	输出：

```txt
1.000000+2.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.2 The cimag functions （第 197 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.9.2 The cimag functions （第 178-179 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [creal (C99)<br />crealf (C99)<br />creall (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/creal) | 计算复数的实部 (函数) |
| ------------------------------------------------------------ | --------------------- |
| **imag** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/imag2)** |                       |





### cimagf

原址：[https://zh.cppreference.com/w/c/numeric/complex/cimag](https://zh.cppreference.com/w/c/numeric/complex/cimag)

作用：计算复数的虚部  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float       cimagf( float complex z );// (1)(C99 起)
double      cimag( double complex z );// (2)(C99 起)
long double cimagl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cimag( z )// (4)(C99 起)
```

1-3) 返回 `z` 的虚部。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `long double` 类型，则调用 `cimagl`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `float` 类型，则调用 `cimagf`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)`、`double` 或任何整数类型，则调用 `cimag`。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	`z` 的虚部。

​	此函数对所有可行输入完全指明，而且不受制于任何描述于 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

**注意**

​	对于任何复数变量 `z`，`z == [creal](http://zh.cppreference.com/w/c/numeric/complex/creal)(z) + I*cimag(z)`。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{    
    double complex z = 1.0 + 2.0*I;
    printf("%f%+fi\n", creal(z), cimag(z));
}
```

​	输出：

```txt
1.000000+2.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.2 The cimag functions （第 197 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.9.2 The cimag functions （第 178-179 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [creal (C99)<br />crealf (C99)<br />creall (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/creal) | 计算复数的实部 (函数) |
| ------------------------------------------------------------ | --------------------- |
| **imag** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/imag2)** |                       |





### cimagl

原址：[https://zh.cppreference.com/w/c/numeric/complex/cimag](https://zh.cppreference.com/w/c/numeric/complex/cimag)

作用：计算复数的虚部  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float       cimagf( float complex z );// (1)(C99 起)
double      cimag( double complex z );// (2)(C99 起)
long double cimagl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cimag( z )// (4)(C99 起)
```

1-3) 返回 `z` 的虚部。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `long double` 类型，则调用 `cimagl`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `float` 类型，则调用 `cimagf`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)`、`double` 或任何整数类型，则调用 `cimag`。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	`z` 的虚部。

​	此函数对所有可行输入完全指明，而且不受制于任何描述于 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

**注意**

​	对于任何复数变量 `z`，`z == [creal](http://zh.cppreference.com/w/c/numeric/complex/creal)(z) + I*cimag(z)`。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{    
    double complex z = 1.0 + 2.0*I;
    printf("%f%+fi\n", creal(z), cimag(z));
}
```

​	输出：

```txt
1.000000+2.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.2 The cimag functions （第 197 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.9.2 The cimag functions （第 178-179 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [creal (C99)<br />crealf (C99)<br />creall (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/creal) | 计算复数的实部 (函数) |
| ------------------------------------------------------------ | --------------------- |
| **imag** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/imag2)** |                       |





### clog

原址：[https://zh.cppreference.com/w/c/numeric/complex/clog](https://zh.cppreference.com/w/c/numeric/complex/clog)

作用：计算复数的自然对数  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       clogf( float complex z );// (1)(C99 起)
double complex      clog( double complex z );// (2)(C99 起)
long double complex clogl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define log( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复自然（底 *e*）对数，分支切割线沿负实轴。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `clogl`，若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `clog`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `clogf`。若 `z` 为实数或整数，则该宏调用对应的实数函数（`logf`、`[log](http://zh.cppreference.com/w/c/numeric/math/log)`、`logl`）。若 `z` 为虚数，则调用对应的复数版本。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不发生错误，则返回 `z` 的复自然对数，其定义域为沿虚轴在区间 *[−iπ, +iπ]* 中，沿实轴为数学上无界的条带。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- 考虑虚部符号，函数连续到分支切割上
- `clog([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(clog(z))`
- 若 `z` 为 `-0+0i`，则结果为 `-∞+πi` 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+0+0i`，则结果为 `-∞+0i` 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+∞i`（对于任何有限 x），则结果为 `+∞+πi/2`
- 若 `z` 为 `x+NaNi`（对于任何有限 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `-∞+yi`（对于任何有限正 y），则结果为 `+∞+πi`
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），则结果为 `+∞+0i`
- 若 `z` 为 `-∞+∞i`，则结果为 `+∞+3πi/4`
- 若 `z` 为 `+∞+∞i`，则结果为 `+∞+πi/4`
- 若 `z` 为 `±∞+NaNi`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+yi`（对于任何有限 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+∞i`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**注意**

​	拥有极坐标表示 *(r,θ)* 的复数 *z* 的自然对数等于 *ln r + i(θ+2nπ)*，其主值为 *ln r + iθ*。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = clog(I); // r = 1, θ = pi/2
    printf("2*log(i) = %.1f%+fi\n", creal(2*z), cimag(2*z));
 
    double complex z2 = clog(sqrt(2)/2 + sqrt(2)/2*I); // r = 1, θ = pi/4
    printf("4*log(sqrt(2)/2+sqrt(2)i/2) = %.1f%+fi\n", creal(4*z2), cimag(4*z2));
 
    double complex z3 = clog(-1); // r = 1, θ = pi
    printf("log(-1+0i) = %.1f%+fi\n", creal(z3), cimag(z3));
 
    double complex z4 = clog(conj(-1)); // 或 C11 中的 clog(CMPLX(-1, -0.0))
    printf("log(-1-0i) (the other side of the cut) = %.1f%+fi\n", creal(z4), cimag(z4));
}
```

​	输出：

```txt
2*log(i) = 0.0+3.141593i
4*log(sqrt(2)/2+sqrt(2)i/2) = 0.0+3.141593i
log(-1+0i) = 0.0+3.141593i
log(-1-0i) (the other side of the cut) = 0.0-3.141593i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.7.2 The clog functions （第 195 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.3.2 The clog functions （第 543-544 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.7.2 The clog functions （第 176-177 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.3.2 The clog functions （第 478-479 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cexp (C99)<br />cexpf (C99)<br />cexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cexp) | 计算复数的 e 底指数 (函数)                |
| ------------------------------------------------------------ | ----------------------------------------- |
| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡x） (函数) |
| **log** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/log)** |                                           |





### clogf

原址：[https://zh.cppreference.com/w/c/numeric/complex/clog](https://zh.cppreference.com/w/c/numeric/complex/clog)

作用：计算复数的自然对数  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       clogf( float complex z );// (1)(C99 起)
double complex      clog( double complex z );// (2)(C99 起)
long double complex clogl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define log( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复自然（底 *e*）对数，分支切割线沿负实轴。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `clogl`，若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `clog`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `clogf`。若 `z` 为实数或整数，则该宏调用对应的实数函数（`logf`、`[log](http://zh.cppreference.com/w/c/numeric/math/log)`、`logl`）。若 `z` 为虚数，则调用对应的复数版本。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不发生错误，则返回 `z` 的复自然对数，其定义域为沿虚轴在区间 *[−iπ, +iπ]* 中，沿实轴为数学上无界的条带。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- 考虑虚部符号，函数连续到分支切割上
- `clog([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(clog(z))`
- 若 `z` 为 `-0+0i`，则结果为 `-∞+πi` 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+0+0i`，则结果为 `-∞+0i` 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+∞i`（对于任何有限 x），则结果为 `+∞+πi/2`
- 若 `z` 为 `x+NaNi`（对于任何有限 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `-∞+yi`（对于任何有限正 y），则结果为 `+∞+πi`
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），则结果为 `+∞+0i`
- 若 `z` 为 `-∞+∞i`，则结果为 `+∞+3πi/4`
- 若 `z` 为 `+∞+∞i`，则结果为 `+∞+πi/4`
- 若 `z` 为 `±∞+NaNi`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+yi`（对于任何有限 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+∞i`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**注意**

​	拥有极坐标表示 *(r,θ)* 的复数 *z* 的自然对数等于 *ln r + i(θ+2nπ)*，其主值为 *ln r + iθ*。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = clog(I); // r = 1, θ = pi/2
    printf("2*log(i) = %.1f%+fi\n", creal(2*z), cimag(2*z));
 
    double complex z2 = clog(sqrt(2)/2 + sqrt(2)/2*I); // r = 1, θ = pi/4
    printf("4*log(sqrt(2)/2+sqrt(2)i/2) = %.1f%+fi\n", creal(4*z2), cimag(4*z2));
 
    double complex z3 = clog(-1); // r = 1, θ = pi
    printf("log(-1+0i) = %.1f%+fi\n", creal(z3), cimag(z3));
 
    double complex z4 = clog(conj(-1)); // 或 C11 中的 clog(CMPLX(-1, -0.0))
    printf("log(-1-0i) (the other side of the cut) = %.1f%+fi\n", creal(z4), cimag(z4));
}
```

​	输出：

```txt
2*log(i) = 0.0+3.141593i
4*log(sqrt(2)/2+sqrt(2)i/2) = 0.0+3.141593i
log(-1+0i) = 0.0+3.141593i
log(-1-0i) (the other side of the cut) = 0.0-3.141593i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.7.2 The clog functions （第 195 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.3.2 The clog functions （第 543-544 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.7.2 The clog functions （第 176-177 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.3.2 The clog functions （第 478-479 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cexp (C99)<br />cexpf (C99)<br />cexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cexp) | 计算复数的 e 底指数 (函数)                |
| ------------------------------------------------------------ | ----------------------------------------- |
| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡x） (函数) |
| **log** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/log)** |                                           |





### clogl

原址：[https://zh.cppreference.com/w/c/numeric/complex/clog](https://zh.cppreference.com/w/c/numeric/complex/clog)

作用：计算复数的自然对数  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       clogf( float complex z );// (1)(C99 起)
double complex      clog( double complex z );// (2)(C99 起)
long double complex clogl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define log( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复自然（底 *e*）对数，分支切割线沿负实轴。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `clogl`，若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `clog`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `clogf`。若 `z` 为实数或整数，则该宏调用对应的实数函数（`logf`、`[log](http://zh.cppreference.com/w/c/numeric/math/log)`、`logl`）。若 `z` 为虚数，则调用对应的复数版本。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不发生错误，则返回 `z` 的复自然对数，其定义域为沿虚轴在区间 *[−iπ, +iπ]* 中，沿实轴为数学上无界的条带。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- 考虑虚部符号，函数连续到分支切割上
- `clog([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(clog(z))`
- 若 `z` 为 `-0+0i`，则结果为 `-∞+πi` 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+0+0i`，则结果为 `-∞+0i` 并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+∞i`（对于任何有限 x），则结果为 `+∞+πi/2`
- 若 `z` 为 `x+NaNi`（对于任何有限 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `-∞+yi`（对于任何有限正 y），则结果为 `+∞+πi`
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），则结果为 `+∞+0i`
- 若 `z` 为 `-∞+∞i`，则结果为 `+∞+3πi/4`
- 若 `z` 为 `+∞+∞i`，则结果为 `+∞+πi/4`
- 若 `z` 为 `±∞+NaNi`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+yi`（对于任何有限 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+∞i`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**注意**

​	拥有极坐标表示 *(r,θ)* 的复数 *z* 的自然对数等于 *ln r + i(θ+2nπ)*，其主值为 *ln r + iθ*。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = clog(I); // r = 1, θ = pi/2
    printf("2*log(i) = %.1f%+fi\n", creal(2*z), cimag(2*z));
 
    double complex z2 = clog(sqrt(2)/2 + sqrt(2)/2*I); // r = 1, θ = pi/4
    printf("4*log(sqrt(2)/2+sqrt(2)i/2) = %.1f%+fi\n", creal(4*z2), cimag(4*z2));
 
    double complex z3 = clog(-1); // r = 1, θ = pi
    printf("log(-1+0i) = %.1f%+fi\n", creal(z3), cimag(z3));
 
    double complex z4 = clog(conj(-1)); // 或 C11 中的 clog(CMPLX(-1, -0.0))
    printf("log(-1-0i) (the other side of the cut) = %.1f%+fi\n", creal(z4), cimag(z4));
}
```

​	输出：

```txt
2*log(i) = 0.0+3.141593i
4*log(sqrt(2)/2+sqrt(2)i/2) = 0.0+3.141593i
log(-1+0i) = 0.0+3.141593i
log(-1-0i) (the other side of the cut) = 0.0-3.141593i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.7.2 The clog functions （第 195 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.3.2 The clog functions （第 543-544 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.7.2 The clog functions （第 176-177 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.3.2 The clog functions （第 478-479 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cexp (C99)<br />cexpf (C99)<br />cexpl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cexp) | 计算复数的 e 底指数 (函数)                |
| ------------------------------------------------------------ | ----------------------------------------- |
| [log <br />logf (C99)<br />logl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/log) | 计算自然对数（底为 *e*）（lnxln⁡x） (函数) |
| **log** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/log)** |                                           |





### conj

原址：[https://zh.cppreference.com/w/c/numeric/complex/conj](https://zh.cppreference.com/w/c/numeric/complex/conj)

作用：计算共轭复数  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       conjf( float complex z );// (1)(C99 起)
double complex      conj( double complex z );// (2)(C99 起)
long double complex conjl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define conj( z )// (4)(C99 起)
```

1-3) 通过反转虚部的符号计算 `z` 的[共轭复数](https://en.wikipedia.org/wiki/Complex_conjugate)。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `long double` 类型，则调用 `conjl`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `float` 类型，则调用 `conjf`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)`、`double` 或任何整数类型，则调用 `conj`。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	`z` 的共轭复数。

**注意**

​	在不把 I 实现为 [_Imaginary_I](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I) 的 C99 实现上，可用 `conj` 获得拥有负零虚部的复数。C11 中，宏 [CMPLX](https://zh.cppreference.com/w/c/numeric/complex/CMPLX) 用于此目的。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = 1.0 + 2.0*I;
    double complex z2 = conj(z);
    printf("The conjugate of %.1f%+.1fi is %.1f%+.1fi\n",
            creal(z), cimag(z), creal(z2), cimag(z2));
 
    printf("Their product is %.1f%+.1fi\n", creal(z*z2), cimag(z*z2));
}
```

​	输出：

```txt
The conjugate of 1.0+2.0i is 1.0-2.0i
Their product is 5.0+0.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.4 The conj functions （第 198 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.9.3 The conj functions （第 179 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

**conj** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/conj)**





### conjf

原址：[https://zh.cppreference.com/w/c/numeric/complex/conj](https://zh.cppreference.com/w/c/numeric/complex/conj)

作用：计算共轭复数  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       conjf( float complex z );// (1)(C99 起)
double complex      conj( double complex z );// (2)(C99 起)
long double complex conjl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define conj( z )// (4)(C99 起)
```

1-3) 通过反转虚部的符号计算 `z` 的[共轭复数](https://en.wikipedia.org/wiki/Complex_conjugate)。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `long double` 类型，则调用 `conjl`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `float` 类型，则调用 `conjf`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)`、`double` 或任何整数类型，则调用 `conj`。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	`z` 的共轭复数。

**注意**

​	在不把 I 实现为 [_Imaginary_I](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I) 的 C99 实现上，可用 `conj` 获得拥有负零虚部的复数。C11 中，宏 [CMPLX](https://zh.cppreference.com/w/c/numeric/complex/CMPLX) 用于此目的。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = 1.0 + 2.0*I;
    double complex z2 = conj(z);
    printf("The conjugate of %.1f%+.1fi is %.1f%+.1fi\n",
            creal(z), cimag(z), creal(z2), cimag(z2));
 
    printf("Their product is %.1f%+.1fi\n", creal(z*z2), cimag(z*z2));
}
```

​	输出：

```txt
The conjugate of 1.0+2.0i is 1.0-2.0i
Their product is 5.0+0.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.4 The conj functions （第 198 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.9.3 The conj functions （第 179 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

**conj** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/conj)**





### conjl

原址：[https://zh.cppreference.com/w/c/numeric/complex/conj](https://zh.cppreference.com/w/c/numeric/complex/conj)

作用：计算共轭复数  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       conjf( float complex z );// (1)(C99 起)
double complex      conj( double complex z );// (2)(C99 起)
long double complex conjl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define conj( z )// (4)(C99 起)
```

1-3) 通过反转虚部的符号计算 `z` 的[共轭复数](https://en.wikipedia.org/wiki/Complex_conjugate)。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `long double` 类型，则调用 `conjl`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `float` 类型，则调用 `conjf`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)`、`double` 或任何整数类型，则调用 `conj`。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	`z` 的共轭复数。

**注意**

​	在不把 I 实现为 [_Imaginary_I](https://zh.cppreference.com/w/c/numeric/complex/Imaginary_I) 的 C99 实现上，可用 `conj` 获得拥有负零虚部的复数。C11 中，宏 [CMPLX](https://zh.cppreference.com/w/c/numeric/complex/CMPLX) 用于此目的。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z = 1.0 + 2.0*I;
    double complex z2 = conj(z);
    printf("The conjugate of %.1f%+.1fi is %.1f%+.1fi\n",
            creal(z), cimag(z), creal(z2), cimag(z2));
 
    printf("Their product is %.1f%+.1fi\n", creal(z*z2), cimag(z*z2));
}
```

​	输出：

```txt
The conjugate of 1.0+2.0i is 1.0-2.0i
Their product is 5.0+0.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.4 The conj functions （第 198 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.9.3 The conj functions （第 179 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

**conj** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/conj)**





### cpow

原址：[https://zh.cppreference.com/w/c/numeric/complex/cpow](https://zh.cppreference.com/w/c/numeric/complex/cpow)

作用：计算复数幂函数  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       cpowf( float complex x, float complex y );// (1)(C99 起)
double complex      cpow( double complex x, double complex y );// (2)(C99 起)
long double complex cpowl( long double complex x, long double complex y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define pow( x, y )// (4)(C99 起)
```

1-3) 计算复幂函数 xy
，首个形参分支切割线沿负实轴。

4） 泛型宏。若任何实参拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cpowl`。若任何实参拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cpow`，若任何实参拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cpowf`。若实参为实数或整数，则宏调用对应的实函数（`powf`、`[pow](http://zh.cppreference.com/w/c/numeric/math/pow)`、`powl`）。若实参为虚数，则调用对应的复数版本。

**参数**

| x, y | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回复数幂 *xy
*。

​	错误和特殊情况按照如同以 `[cexp](http://zh.cppreference.com/w/c/numeric/complex/cexp)(y*[clog](http://zh.cppreference.com/w/c/numeric/complex/clog)(x))` 实现运算一般处理，但允许实现更细致地处理特殊情况。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{    
    double complex z = cpow(1.0+2.0*I, 2);
    printf("(1+2i)^2 = %.1f%+.1fi\n", creal(z), cimag(z));
 
    double complex z2 = cpow(-1, 0.5);
    printf("(-1+0i)^0.5 = %.1f%+.1fi\n", creal(z2), cimag(z2));
 
    double complex z3 = cpow(conj(-1), 0.5); // 切割的另一侧
    printf("(-1-0i)^0.5 = %.1f%+.1fi\n", creal(z3), cimag(z3));
 
    double complex z4 = cpow(I, I); // i^i = exp(-pi/2)
    printf("i^i = %f%+fi\n", creal(z4), cimag(z4));
}
```

​	输出：

```txt
(1+2i)^2 = -3.0+4.0i
(-1+0i)^0.5 = 0.0+1.0i
(-1-0i)^0.5 = 0.0-1.0i
i^i = 0.207880+0.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.8.2 The cpow functions （第 195-196 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.4.1 The cpow functions （第 544 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.8.2 The cpow functions （第 177 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.4.1 The cpow functions （第 479 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [csqrt (C99)<br />csqrtf (C99)<br />csqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csqrt) | 计算复数平方根 (函数)               |
| ------------------------------------------------------------ | ----------------------------------- |
| [pow <br />powf (C99)<br />powl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/pow) | 计算一个数的给定次幂（xyxy） (函数) |
| **pow** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/pow)** |                                     |





### cpowf

原址：[https://zh.cppreference.com/w/c/numeric/complex/cpow](https://zh.cppreference.com/w/c/numeric/complex/cpow)

作用：计算复数幂函数  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       cpowf( float complex x, float complex y );// (1)(C99 起)
double complex      cpow( double complex x, double complex y );// (2)(C99 起)
long double complex cpowl( long double complex x, long double complex y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define pow( x, y )// (4)(C99 起)
```

1-3) 计算复幂函数 xy
，首个形参分支切割线沿负实轴。

4） 泛型宏。若任何实参拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cpowl`。若任何实参拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cpow`，若任何实参拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cpowf`。若实参为实数或整数，则宏调用对应的实函数（`powf`、`[pow](http://zh.cppreference.com/w/c/numeric/math/pow)`、`powl`）。若实参为虚数，则调用对应的复数版本。

**参数**

| x, y | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回复数幂 *xy
*。

​	错误和特殊情况按照如同以 `[cexp](http://zh.cppreference.com/w/c/numeric/complex/cexp)(y*[clog](http://zh.cppreference.com/w/c/numeric/complex/clog)(x))` 实现运算一般处理，但允许实现更细致地处理特殊情况。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{    
    double complex z = cpow(1.0+2.0*I, 2);
    printf("(1+2i)^2 = %.1f%+.1fi\n", creal(z), cimag(z));
 
    double complex z2 = cpow(-1, 0.5);
    printf("(-1+0i)^0.5 = %.1f%+.1fi\n", creal(z2), cimag(z2));
 
    double complex z3 = cpow(conj(-1), 0.5); // 切割的另一侧
    printf("(-1-0i)^0.5 = %.1f%+.1fi\n", creal(z3), cimag(z3));
 
    double complex z4 = cpow(I, I); // i^i = exp(-pi/2)
    printf("i^i = %f%+fi\n", creal(z4), cimag(z4));
}
```

​	输出：

```txt
(1+2i)^2 = -3.0+4.0i
(-1+0i)^0.5 = 0.0+1.0i
(-1-0i)^0.5 = 0.0-1.0i
i^i = 0.207880+0.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.8.2 The cpow functions （第 195-196 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.4.1 The cpow functions （第 544 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.8.2 The cpow functions （第 177 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.4.1 The cpow functions （第 479 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [csqrt (C99)<br />csqrtf (C99)<br />csqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csqrt) | 计算复数平方根 (函数)               |
| ------------------------------------------------------------ | ----------------------------------- |
| [pow <br />powf (C99)<br />powl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/pow) | 计算一个数的给定次幂（xyxy） (函数) |
| **pow** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/pow)** |                                     |





### cpowl

原址：[https://zh.cppreference.com/w/c/numeric/complex/cpow](https://zh.cppreference.com/w/c/numeric/complex/cpow)

作用：计算复数幂函数  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       cpowf( float complex x, float complex y );// (1)(C99 起)
double complex      cpow( double complex x, double complex y );// (2)(C99 起)
long double complex cpowl( long double complex x, long double complex y );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define pow( x, y )// (4)(C99 起)
```

1-3) 计算复幂函数 xy
，首个形参分支切割线沿负实轴。

4） 泛型宏。若任何实参拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cpowl`。若任何实参拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cpow`，若任何实参拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `cpowf`。若实参为实数或整数，则宏调用对应的实函数（`powf`、`[pow](http://zh.cppreference.com/w/c/numeric/math/pow)`、`powl`）。若实参为虚数，则调用对应的复数版本。

**参数**

| x, y | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回复数幂 *xy
*。

​	错误和特殊情况按照如同以 `[cexp](http://zh.cppreference.com/w/c/numeric/complex/cexp)(y*[clog](http://zh.cppreference.com/w/c/numeric/complex/clog)(x))` 实现运算一般处理，但允许实现更细致地处理特殊情况。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{    
    double complex z = cpow(1.0+2.0*I, 2);
    printf("(1+2i)^2 = %.1f%+.1fi\n", creal(z), cimag(z));
 
    double complex z2 = cpow(-1, 0.5);
    printf("(-1+0i)^0.5 = %.1f%+.1fi\n", creal(z2), cimag(z2));
 
    double complex z3 = cpow(conj(-1), 0.5); // 切割的另一侧
    printf("(-1-0i)^0.5 = %.1f%+.1fi\n", creal(z3), cimag(z3));
 
    double complex z4 = cpow(I, I); // i^i = exp(-pi/2)
    printf("i^i = %f%+fi\n", creal(z4), cimag(z4));
}
```

​	输出：

```txt
(1+2i)^2 = -3.0+4.0i
(-1+0i)^0.5 = 0.0+1.0i
(-1-0i)^0.5 = 0.0-1.0i
i^i = 0.207880+0.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.8.2 The cpow functions （第 195-196 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.4.1 The cpow functions （第 544 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.8.2 The cpow functions （第 177 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.4.1 The cpow functions （第 479 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [csqrt (C99)<br />csqrtf (C99)<br />csqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csqrt) | 计算复数平方根 (函数)               |
| ------------------------------------------------------------ | ----------------------------------- |
| [pow <br />powf (C99)<br />powl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/pow) | 计算一个数的给定次幂（xyxy） (函数) |
| **pow** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/pow)** |                                     |





### cproj

原址：[https://zh.cppreference.com/w/c/numeric/complex/cproj](https://zh.cppreference.com/w/c/numeric/complex/cproj)

作用：计算黎曼球上的投影  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       cprojf( float complex z );// (1)(C99 起)
double complex      cproj( double complex z );// (2)(C99 起)
long double complex cprojl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cproj( z )// (4)(C99 起)
```

1-3) 计算 `z` 在黎曼球面上的投影。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `long double` 类型，则调用 `cprojl`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `float` 类型，则调用 `cprojf`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)`、`double` 或任何整数类型，则调用 `cproj`。

​	对于绝大多数 `z`，`cproj(z)==z`，但所有复无穷大，即使是一部为无穷大而另一部为 NaN 者，都变为正实无穷大，`INFINITY+0.0*I` 或 `INFINITY-0.0*I`。虚部（零）的符号为 `[cimag](http://zh.cppreference.com/w/c/numeric/complex/cimag)(z)` 的符号。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	`z` 在黎曼球面上的投影。

​	此函数为所有可行输入完整指定，并且不受制于任何描述于 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

**注解**

​	`cproj` 函数通过将所有无穷大映射到一（给出或采用虚部零的符号），帮助用户模拟黎曼球面，而且它应该在任何操作，特别是比较之前使用，比较可能对任何其他无穷大给出虚假结果。

**示例**

```c
#include <stdio.h>
#include <complex.h>
#include <math.h>
 
int main(void)
{
    double complex z1 = cproj(1 + 2*I);
    printf("cproj(1+2i) = %.1f%+.1fi\n", creal(z1),cimag(z1));
 
    double complex z2 = cproj(INFINITY+2.0*I);
    printf("cproj(Inf+2i) = %.1f%+.1fi\n", creal(z2),cimag(z2));
 
    double complex z3 = cproj(INFINITY-2.0*I);
    printf("cproj(Inf-2i) = %.1f%+.1fi\n", creal(z3),cimag(z3));
}
```

​	输出：

```txt
cproj(1+2i) = 1.0+2.0i
cproj(Inf+2i) = inf+0.0i
cproj(Inf-2i) = inf-0.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.5 The cproj functions （第 198 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.9.4 The cproj functions （第 179 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

**proj** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/proj)**





### cprojf

原址：[https://zh.cppreference.com/w/c/numeric/complex/cproj](https://zh.cppreference.com/w/c/numeric/complex/cproj)

作用：计算黎曼球上的投影  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       cprojf( float complex z );// (1)(C99 起)
double complex      cproj( double complex z );// (2)(C99 起)
long double complex cprojl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cproj( z )// (4)(C99 起)
```

1-3) 计算 `z` 在黎曼球面上的投影。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `long double` 类型，则调用 `cprojl`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `float` 类型，则调用 `cprojf`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)`、`double` 或任何整数类型，则调用 `cproj`。

​	对于绝大多数 `z`，`cproj(z)==z`，但所有复无穷大，即使是一部为无穷大而另一部为 NaN 者，都变为正实无穷大，`INFINITY+0.0*I` 或 `INFINITY-0.0*I`。虚部（零）的符号为 `[cimag](http://zh.cppreference.com/w/c/numeric/complex/cimag)(z)` 的符号。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	`z` 在黎曼球面上的投影。

​	此函数为所有可行输入完整指定，并且不受制于任何描述于 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

**注解**

​	`cproj` 函数通过将所有无穷大映射到一（给出或采用虚部零的符号），帮助用户模拟黎曼球面，而且它应该在任何操作，特别是比较之前使用，比较可能对任何其他无穷大给出虚假结果。

**示例**

```c
#include <stdio.h>
#include <complex.h>
#include <math.h>
 
int main(void)
{
    double complex z1 = cproj(1 + 2*I);
    printf("cproj(1+2i) = %.1f%+.1fi\n", creal(z1),cimag(z1));
 
    double complex z2 = cproj(INFINITY+2.0*I);
    printf("cproj(Inf+2i) = %.1f%+.1fi\n", creal(z2),cimag(z2));
 
    double complex z3 = cproj(INFINITY-2.0*I);
    printf("cproj(Inf-2i) = %.1f%+.1fi\n", creal(z3),cimag(z3));
}
```

​	输出：

```txt
cproj(1+2i) = 1.0+2.0i
cproj(Inf+2i) = inf+0.0i
cproj(Inf-2i) = inf-0.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.5 The cproj functions （第 198 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.9.4 The cproj functions （第 179 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

**proj** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/proj)**





### cprojl

原址：[https://zh.cppreference.com/w/c/numeric/complex/cproj](https://zh.cppreference.com/w/c/numeric/complex/cproj)

作用：计算黎曼球上的投影  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       cprojf( float complex z );// (1)(C99 起)
double complex      cproj( double complex z );// (2)(C99 起)
long double complex cprojl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define cproj( z )// (4)(C99 起)
```

1-3) 计算 `z` 在黎曼球面上的投影。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `long double` 类型，则调用 `cprojl`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `float` 类型，则调用 `cprojf`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)`、`double` 或任何整数类型，则调用 `cproj`。

​	对于绝大多数 `z`，`cproj(z)==z`，但所有复无穷大，即使是一部为无穷大而另一部为 NaN 者，都变为正实无穷大，`INFINITY+0.0*I` 或 `INFINITY-0.0*I`。虚部（零）的符号为 `[cimag](http://zh.cppreference.com/w/c/numeric/complex/cimag)(z)` 的符号。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	`z` 在黎曼球面上的投影。

​	此函数为所有可行输入完整指定，并且不受制于任何描述于 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

**注解**

​	`cproj` 函数通过将所有无穷大映射到一（给出或采用虚部零的符号），帮助用户模拟黎曼球面，而且它应该在任何操作，特别是比较之前使用，比较可能对任何其他无穷大给出虚假结果。

**示例**

```c
#include <stdio.h>
#include <complex.h>
#include <math.h>
 
int main(void)
{
    double complex z1 = cproj(1 + 2*I);
    printf("cproj(1+2i) = %.1f%+.1fi\n", creal(z1),cimag(z1));
 
    double complex z2 = cproj(INFINITY+2.0*I);
    printf("cproj(Inf+2i) = %.1f%+.1fi\n", creal(z2),cimag(z2));
 
    double complex z3 = cproj(INFINITY-2.0*I);
    printf("cproj(Inf-2i) = %.1f%+.1fi\n", creal(z3),cimag(z3));
}
```

​	输出：

```txt
cproj(1+2i) = 1.0+2.0i
cproj(Inf+2i) = inf+0.0i
cproj(Inf-2i) = inf-0.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.5 The cproj functions （第 198 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.9.4 The cproj functions （第 179 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

**proj** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/proj)**





### creal

原址：[https://zh.cppreference.com/w/c/numeric/complex/creal](https://zh.cppreference.com/w/c/numeric/complex/creal)

作用：计算复数的实部  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float       crealf( float complex z );// (1)(C99 起)
double      creal( double complex z );// (2)(C99 起)
long double creall( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define creal( z )// (4)(C99 起)
```

1-3) 返回 `z` 的实部。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `long double` 类型，则调用 `creall`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `float` 类型，则调用 `crealf`。若`z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `double` 类型，或任何整数类型，则调用 `creal`。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	`z` 的实部

​	此函数对所有可能输入指明，而且不受制于任何描述于 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

**注意**

​	对于任何复变量 `z`，`z == creal(z) + I*[cimag](http://zh.cppreference.com/w/c/numeric/complex/cimag)(z)`。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{    
    double complex z = 1.0 + 2.0*I;
    printf("%f%+fi\n", creal(z), cimag(z));
}
```

​	输出：

```txt
1.000000+2.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.6 The creal functions （第 198-199 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.9.5 The creal functions （第 180 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cimag (C99)<br />cimagf (C99)<br />cimagl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cimag) | 计算复数的虚部 (函数) |
| ------------------------------------------------------------ | --------------------- |
| **real** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/real2)** |                       |





### crealf

原址：[https://zh.cppreference.com/w/c/numeric/complex/creal](https://zh.cppreference.com/w/c/numeric/complex/creal)

作用：计算复数的实部  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float       crealf( float complex z );// (1)(C99 起)
double      creal( double complex z );// (2)(C99 起)
long double creall( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define creal( z )// (4)(C99 起)
```

1-3) 返回 `z` 的实部。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `long double` 类型，则调用 `creall`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `float` 类型，则调用 `crealf`。若`z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `double` 类型，或任何整数类型，则调用 `creal`。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	`z` 的实部

​	此函数对所有可能输入指明，而且不受制于任何描述于 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

**注意**

​	对于任何复变量 `z`，`z == creal(z) + I*[cimag](http://zh.cppreference.com/w/c/numeric/complex/cimag)(z)`。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{    
    double complex z = 1.0 + 2.0*I;
    printf("%f%+fi\n", creal(z), cimag(z));
}
```

​	输出：

```txt
1.000000+2.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.6 The creal functions （第 198-199 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.9.5 The creal functions （第 180 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cimag (C99)<br />cimagf (C99)<br />cimagl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cimag) | 计算复数的虚部 (函数) |
| ------------------------------------------------------------ | --------------------- |
| **real** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/real2)** |                       |





### creall

原址：[https://zh.cppreference.com/w/c/numeric/complex/creal](https://zh.cppreference.com/w/c/numeric/complex/creal)

作用：计算复数的实部  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float       crealf( float complex z );// (1)(C99 起)
double      creal( double complex z );// (2)(C99 起)
long double creall( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define creal( z )// (4)(C99 起)
```

1-3) 返回 `z` 的实部。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `long double` 类型，则调用 `creall`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `float` 类型，则调用 `crealf`。若`z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`、`double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)` 或 `double` 类型，或任何整数类型，则调用 `creal`。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	`z` 的实部

​	此函数对所有可能输入指明，而且不受制于任何描述于 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 的错误。

**注意**

​	对于任何复变量 `z`，`z == creal(z) + I*[cimag](http://zh.cppreference.com/w/c/numeric/complex/cimag)(z)`。

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{    
    double complex z = 1.0 + 2.0*I;
    printf("%f%+fi\n", creal(z), cimag(z));
}
```

​	输出：

```txt
1.000000+2.000000i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.9.6 The creal functions （第 198-199 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.9.5 The creal functions （第 180 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cimag (C99)<br />cimagf (C99)<br />cimagl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cimag) | 计算复数的虚部 (函数) |
| ------------------------------------------------------------ | --------------------- |
| **real** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/real2)** |                       |





### csin

原址：[https://zh.cppreference.com/w/c/numeric/complex/csin](https://zh.cppreference.com/w/c/numeric/complex/csin)

作用：计算复数正弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       csinf( float complex z );// (1)(C99 起)
double complex      csin( double complex z );// (2)(C99 起)
long double complex csinl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define sin( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复正弦。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csinl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csin`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csinf`。若 `z` 为实数或整数，则该宏调用对应的实数函数（`sinf`、`[sin](http://zh.cppreference.com/w/c/numeric/math/sin)`、`sinl`）。若 `z` 是虚数，则该宏调用函数 [sinh](https://zh.cppreference.com/w/c/numeric/math/sinh) 的对应实数版本，实现公式 *sin(iy) = i sinh(y)*，且宏的返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若无错误发生，则为 `z` 的复正弦。

​	错误和特殊情况的处理如同运算以 `-I * [csinh](http://zh.cppreference.com/w/c/numeric/complex/csinh)(I*z)` 实现。

**注意**

​	正弦在复平面上是整函数，而且没有分支切割。

正弦的数学定义是 

sin z = 

| eiz -e-iz |
| --------- |
| 2i        |

。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = csin(1);  // 表现如同沿着实轴的实数正弦
    printf("sin(1+0i) = %f%+fi ( sin(1)=%f)\n", creal(z), cimag(z), sin(1));
 
    double complex z2 = csin(I); // 表现如同沿着虚轴的sinh
    printf("sin(0+1i) = %f%+fi (sinh(1)=%f)\n", creal(z2), cimag(z2), sinh(1));
}
```

​	输出：

```txt
sin(1+0i) = 0.841471+0.000000i ( sin(1)=0.841471)
sin(0+1i) = 0.000000+1.175201i (sinh(1)=1.175201)
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.3.5.5 The csin functions （第 138-139 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - G.7 Type-generic math <tgmath.h> （第 397 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.5 The csin functions （第 191-192 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.5 The csin functions （第 173 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [ccos (C99)<br />ccosf (C99)<br />ccosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccos) | 计算复数余弦 (函数)         |
| ------------------------------------------------------------ | --------------------------- |
| [ctan (C99)<br />ctanf (C99)<br />ctanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctan) | 计算复数正切 (函数)         |
| [casin (C99)<br />casinf (C99)<br />casinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casin) | 计算复数反正弦 (函数)       |
| [sin <br />sinf (C99)<br />sinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sin) | 计算正弦（sinxsin⁡x） (函数) |
| **sin** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/sin)** |                             |





### csinf

原址：[https://zh.cppreference.com/w/c/numeric/complex/csin](https://zh.cppreference.com/w/c/numeric/complex/csin)

作用：计算复数正弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       csinf( float complex z );// (1)(C99 起)
double complex      csin( double complex z );// (2)(C99 起)
long double complex csinl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define sin( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复正弦。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csinl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csin`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csinf`。若 `z` 为实数或整数，则该宏调用对应的实数函数（`sinf`、`[sin](http://zh.cppreference.com/w/c/numeric/math/sin)`、`sinl`）。若 `z` 是虚数，则该宏调用函数 [sinh](https://zh.cppreference.com/w/c/numeric/math/sinh) 的对应实数版本，实现公式 *sin(iy) = i sinh(y)*，且宏的返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若无错误发生，则为 `z` 的复正弦。

​	错误和特殊情况的处理如同运算以 `-I * [csinh](http://zh.cppreference.com/w/c/numeric/complex/csinh)(I*z)` 实现。

**注意**

​	正弦在复平面上是整函数，而且没有分支切割。

正弦的数学定义是 

sin z = 

| eiz -e-iz |
| --------- |
| 2i        |

。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = csin(1);  // 表现如同沿着实轴的实数正弦
    printf("sin(1+0i) = %f%+fi ( sin(1)=%f)\n", creal(z), cimag(z), sin(1));
 
    double complex z2 = csin(I); // 表现如同沿着虚轴的sinh
    printf("sin(0+1i) = %f%+fi (sinh(1)=%f)\n", creal(z2), cimag(z2), sinh(1));
}
```

​	输出：

```txt
sin(1+0i) = 0.841471+0.000000i ( sin(1)=0.841471)
sin(0+1i) = 0.000000+1.175201i (sinh(1)=1.175201)
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.3.5.5 The csin functions （第 138-139 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - G.7 Type-generic math <tgmath.h> （第 397 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.5 The csin functions （第 191-192 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.5 The csin functions （第 173 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [ccos (C99)<br />ccosf (C99)<br />ccosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccos) | 计算复数余弦 (函数)         |
| ------------------------------------------------------------ | --------------------------- |
| [ctan (C99)<br />ctanf (C99)<br />ctanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctan) | 计算复数正切 (函数)         |
| [casin (C99)<br />casinf (C99)<br />casinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casin) | 计算复数反正弦 (函数)       |
| [sin <br />sinf (C99)<br />sinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sin) | 计算正弦（sinxsin⁡x） (函数) |
| **sin** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/sin)** |                             |





### csinh

原址：[https://zh.cppreference.com/w/c/numeric/complex/csinh](https://zh.cppreference.com/w/c/numeric/complex/csinh)

作用：计算复数双曲正弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       csinhf( float complex z );// (1)(C99 起)
double complex      csinh( double complex z );// (2)(C99 起)
long double complex csinhl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define sinh( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复双曲正弦。

4） 泛型宏：若 `z` 的类型为 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `csinl`。若 `z` 的类型为 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `csin`。若 `z` 的类型为 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `csinf`。若 `z` 为实数或整数，则该宏调用对应的实函数（`sinf`、`[sin](http://zh.cppreference.com/w/c/numeric/math/sin)`、`sinl`）。若 `z` 为虚数，则该宏调用函数 [sinh](https://zh.cppreference.com/w/c/numeric/math/sinh) 的对应实版本，实现公式 *sinh(iy) = i sin(y)*，而返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若未出现错误，则返回值为 `z` 的复双曲正弦。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `csinh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(csinh(z))`
- `csinh(z) == -csinh(-z)`
- 若 `z` 为 `+0+0i`，则结果为 `+0+0i`
- 若 `z` 为 `+0+∞i`，则结果为 `±0+NaNi`（实部符号未指定）并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+0+NaNi`，则结果为 `±0+NaNi`
- 若 `z` 为 `x+∞i`（对于任何有限正 x），则结果为 `NaN+NaNi` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+NaNi`（对于任何有限正 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+0i`，则结果为 `+∞+0i`
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），则结果为 `+∞cis(y)`
- 若 `z` 为 `+∞+∞i`，则结果为 `±∞+NaNi`（实部符号未指定）并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+NaNi`，则结果为 `±∞+NaNi`（实部符号未指定）
- 若 `z` 为 `NaN+0i`，则结果为 `NaN+0i`
- 若 `z` 为 `NaN+yi`（对于任何有限非零 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

​	其中 *cis(y)* 为 *cos(y) + i sin(y)*。

**注意**

双曲正弦的数学定义是 

sinh z = 

| ez -e-z |
| ------- |
| 2       |

。

​	双曲正弦在复平面上是整函数而无分支切割。它相对于虚部是周期的，周期为 2πi。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = csinh(1);  // 表现类似沿实轴的实 sinh
    printf("sinh(1+0i) = %f%+fi (sinh(1)=%f)\n", creal(z), cimag(z), sinh(1));
 
    double complex z2 = csinh(I); // 表现类似沿虚轴的正弦
    printf("sinh(0+1i) = %f%+fi ( sin(1)=%f)\n", creal(z2), cimag(z2), sin(1));
}
```

​	输出：

```txt
sinh(1+0i) = 1.175201+0.000000i (sinh(1)=1.175201)
sinh(0+1i) = 0.000000+0.841471i ( sin(1)=0.841471)
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.5 The csinh functions （第 194 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.5 The csinh functions （第 541-542 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.5 The csinh functions （第 175-176 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.5 The csinh functions （第 476-477 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [ccosh (C99)<br />ccoshf (C99)<br />ccoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccosh) | 计算复双曲余弦 (函数)             |
| ------------------------------------------------------------ | --------------------------------- |
| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)           |
| [casinh (C99)<br />casinhf (C99)<br />casinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casinh) | 计算复数反双曲正弦 (函数)         |
| [sinh <br />sinhf (C99)<br />sinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sinh) | 计算双曲正弦（sinhxsinh⁡x） (函数) |
| **sinh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/sinh)** |                                   |





### csinhf

原址：[https://zh.cppreference.com/w/c/numeric/complex/csinh](https://zh.cppreference.com/w/c/numeric/complex/csinh)

作用：计算复数双曲正弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       csinhf( float complex z );// (1)(C99 起)
double complex      csinh( double complex z );// (2)(C99 起)
long double complex csinhl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define sinh( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复双曲正弦。

4） 泛型宏：若 `z` 的类型为 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `csinl`。若 `z` 的类型为 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `csin`。若 `z` 的类型为 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `csinf`。若 `z` 为实数或整数，则该宏调用对应的实函数（`sinf`、`[sin](http://zh.cppreference.com/w/c/numeric/math/sin)`、`sinl`）。若 `z` 为虚数，则该宏调用函数 [sinh](https://zh.cppreference.com/w/c/numeric/math/sinh) 的对应实版本，实现公式 *sinh(iy) = i sin(y)*，而返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若未出现错误，则返回值为 `z` 的复双曲正弦。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `csinh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(csinh(z))`
- `csinh(z) == -csinh(-z)`
- 若 `z` 为 `+0+0i`，则结果为 `+0+0i`
- 若 `z` 为 `+0+∞i`，则结果为 `±0+NaNi`（实部符号未指定）并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+0+NaNi`，则结果为 `±0+NaNi`
- 若 `z` 为 `x+∞i`（对于任何有限正 x），则结果为 `NaN+NaNi` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+NaNi`（对于任何有限正 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+0i`，则结果为 `+∞+0i`
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），则结果为 `+∞cis(y)`
- 若 `z` 为 `+∞+∞i`，则结果为 `±∞+NaNi`（实部符号未指定）并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+NaNi`，则结果为 `±∞+NaNi`（实部符号未指定）
- 若 `z` 为 `NaN+0i`，则结果为 `NaN+0i`
- 若 `z` 为 `NaN+yi`（对于任何有限非零 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

​	其中 *cis(y)* 为 *cos(y) + i sin(y)*。

**注意**

双曲正弦的数学定义是 

sinh z = 

| ez -e-z |
| ------- |
| 2       |

。

​	双曲正弦在复平面上是整函数而无分支切割。它相对于虚部是周期的，周期为 2πi。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = csinh(1);  // 表现类似沿实轴的实 sinh
    printf("sinh(1+0i) = %f%+fi (sinh(1)=%f)\n", creal(z), cimag(z), sinh(1));
 
    double complex z2 = csinh(I); // 表现类似沿虚轴的正弦
    printf("sinh(0+1i) = %f%+fi ( sin(1)=%f)\n", creal(z2), cimag(z2), sin(1));
}
```

​	输出：

```txt
sinh(1+0i) = 1.175201+0.000000i (sinh(1)=1.175201)
sinh(0+1i) = 0.000000+0.841471i ( sin(1)=0.841471)
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.5 The csinh functions （第 194 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.5 The csinh functions （第 541-542 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.5 The csinh functions （第 175-176 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.5 The csinh functions （第 476-477 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [ccosh (C99)<br />ccoshf (C99)<br />ccoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccosh) | 计算复双曲余弦 (函数)             |
| ------------------------------------------------------------ | --------------------------------- |
| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)           |
| [casinh (C99)<br />casinhf (C99)<br />casinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casinh) | 计算复数反双曲正弦 (函数)         |
| [sinh <br />sinhf (C99)<br />sinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sinh) | 计算双曲正弦（sinhxsinh⁡x） (函数) |
| **sinh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/sinh)** |                                   |





### csinhl

原址：[https://zh.cppreference.com/w/c/numeric/complex/csinh](https://zh.cppreference.com/w/c/numeric/complex/csinh)

作用：计算复数双曲正弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       csinhf( float complex z );// (1)(C99 起)
double complex      csinh( double complex z );// (2)(C99 起)
long double complex csinhl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define sinh( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复双曲正弦。

4） 泛型宏：若 `z` 的类型为 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `csinl`。若 `z` 的类型为 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `csin`。若 `z` 的类型为 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)`，则调用 `csinf`。若 `z` 为实数或整数，则该宏调用对应的实函数（`sinf`、`[sin](http://zh.cppreference.com/w/c/numeric/math/sin)`、`sinl`）。若 `z` 为虚数，则该宏调用函数 [sinh](https://zh.cppreference.com/w/c/numeric/math/sinh) 的对应实版本，实现公式 *sinh(iy) = i sin(y)*，而返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若未出现错误，则返回值为 `z` 的复双曲正弦。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `csinh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(csinh(z))`
- `csinh(z) == -csinh(-z)`
- 若 `z` 为 `+0+0i`，则结果为 `+0+0i`
- 若 `z` 为 `+0+∞i`，则结果为 `±0+NaNi`（实部符号未指定）并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+0+NaNi`，则结果为 `±0+NaNi`
- 若 `z` 为 `x+∞i`（对于任何有限正 x），则结果为 `NaN+NaNi` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+NaNi`（对于任何有限正 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+0i`，则结果为 `+∞+0i`
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），则结果为 `+∞cis(y)`
- 若 `z` 为 `+∞+∞i`，则结果为 `±∞+NaNi`（实部符号未指定）并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+NaNi`，则结果为 `±∞+NaNi`（实部符号未指定）
- 若 `z` 为 `NaN+0i`，则结果为 `NaN+0i`
- 若 `z` 为 `NaN+yi`（对于任何有限非零 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

​	其中 *cis(y)* 为 *cos(y) + i sin(y)*。

**注意**

双曲正弦的数学定义是 

sinh z = 

| ez -e-z |
| ------- |
| 2       |

。

​	双曲正弦在复平面上是整函数而无分支切割。它相对于虚部是周期的，周期为 2πi。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = csinh(1);  // 表现类似沿实轴的实 sinh
    printf("sinh(1+0i) = %f%+fi (sinh(1)=%f)\n", creal(z), cimag(z), sinh(1));
 
    double complex z2 = csinh(I); // 表现类似沿虚轴的正弦
    printf("sinh(0+1i) = %f%+fi ( sin(1)=%f)\n", creal(z2), cimag(z2), sin(1));
}
```

​	输出：

```txt
sinh(1+0i) = 1.175201+0.000000i (sinh(1)=1.175201)
sinh(0+1i) = 0.000000+0.841471i ( sin(1)=0.841471)
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.5 The csinh functions （第 194 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.5 The csinh functions （第 541-542 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.5 The csinh functions （第 175-176 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.5 The csinh functions （第 476-477 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [ccosh (C99)<br />ccoshf (C99)<br />ccoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccosh) | 计算复双曲余弦 (函数)             |
| ------------------------------------------------------------ | --------------------------------- |
| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)           |
| [casinh (C99)<br />casinhf (C99)<br />casinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casinh) | 计算复数反双曲正弦 (函数)         |
| [sinh <br />sinhf (C99)<br />sinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sinh) | 计算双曲正弦（sinhxsinh⁡x） (函数) |
| **sinh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/sinh)** |                                   |





### csinl

原址：[https://zh.cppreference.com/w/c/numeric/complex/csin](https://zh.cppreference.com/w/c/numeric/complex/csin)

作用：计算复数正弦  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       csinf( float complex z );// (1)(C99 起)
double complex      csin( double complex z );// (2)(C99 起)
long double complex csinl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define sin( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复正弦。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csinl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csin`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csinf`。若 `z` 为实数或整数，则该宏调用对应的实数函数（`sinf`、`[sin](http://zh.cppreference.com/w/c/numeric/math/sin)`、`sinl`）。若 `z` 是虚数，则该宏调用函数 [sinh](https://zh.cppreference.com/w/c/numeric/math/sinh) 的对应实数版本，实现公式 *sin(iy) = i sinh(y)*，且宏的返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若无错误发生，则为 `z` 的复正弦。

​	错误和特殊情况的处理如同运算以 `-I * [csinh](http://zh.cppreference.com/w/c/numeric/complex/csinh)(I*z)` 实现。

**注意**

​	正弦在复平面上是整函数，而且没有分支切割。

正弦的数学定义是 

sin z = 

| eiz -e-iz |
| --------- |
| 2i        |

。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = csin(1);  // 表现如同沿着实轴的实数正弦
    printf("sin(1+0i) = %f%+fi ( sin(1)=%f)\n", creal(z), cimag(z), sin(1));
 
    double complex z2 = csin(I); // 表现如同沿着虚轴的sinh
    printf("sin(0+1i) = %f%+fi (sinh(1)=%f)\n", creal(z2), cimag(z2), sinh(1));
}
```

​	输出：

```txt
sin(1+0i) = 0.841471+0.000000i ( sin(1)=0.841471)
sin(0+1i) = 0.000000+1.175201i (sinh(1)=1.175201)
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.3.5.5 The csin functions （第 138-139 页）

  - 7.25 Type-generic math <tgmath.h> （第 272-273 页）

  - G.7 Type-generic math <tgmath.h> （第 397 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.5 The csin functions （第 191-192 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.5 The csin functions （第 173 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [ccos (C99)<br />ccosf (C99)<br />ccosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccos) | 计算复数余弦 (函数)         |
| ------------------------------------------------------------ | --------------------------- |
| [ctan (C99)<br />ctanf (C99)<br />ctanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctan) | 计算复数正切 (函数)         |
| [casin (C99)<br />casinf (C99)<br />casinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/casin) | 计算复数反正弦 (函数)       |
| [sin <br />sinf (C99)<br />sinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sin) | 计算正弦（sinxsin⁡x） (函数) |
| **sin** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/sin)** |                             |





### csqrt

原址：[https://zh.cppreference.com/w/c/numeric/complex/csqrt](https://zh.cppreference.com/w/c/numeric/complex/csqrt)

作用：计算复数平方根  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       csqrtf( float complex z );// (1)(C99 起)
double complex      csqrt( double complex z );// (2)(C99 起)
long double complex csqrtl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define sqrt( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复平方根，分支切割线沿负实轴。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csqrtl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csqrt`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csqrtf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`sqrtf`、`[sqrt](http://zh.cppreference.com/w/c/numeric/math/sqrt)`、`sqrtl`）。若 `z` 为虚数，则调用对应的复数版本。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 的平方根，在包含虚轴的右半平面中（沿实轴为 *[0; +∞)*，而沿虚轴为 *(−∞; +∞)*）。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- 考虑虚部符号，函数连续到分支切割上。
- `csqrt([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(csqrt(z))`
- 若 `z` 为 `±0+0i`，则结果为 `+0+0i`
- 若 `z` 为 `x+∞i`，则结果为 `+∞+∞i`，即使 x 为 NaN
- 若 `z` 为 `x+NaNi`，则结果为 `NaN+NaNi`（除非 x 为 ±∞）并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `-∞+yi`，则对于有限正 y 结果为 `+0+∞i`
- 若 `z` 为 `+∞+yi`，则对于有限正 y 结果为 `+∞+0i)`
- 若 `z` 为 `-∞+NaNi`，则结果为 `NaN±∞i`（虚部符号未指定）
- 若 `z` 为 `+∞+NaNi`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+yi`，则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z1 = csqrt(-4);
    printf("Square root of -4 is %.1f%+.1fi\n", creal(z1), cimag(z1));
 
    double complex z2 = csqrt(conj(-4)); // 或 C11 中的 CMPLX(-4, -0.0)
    printf("Square root of -4-0i, the other side of the cut, is "
           "%.1f%+.1fi\n", creal(z2), cimag(z2));
}
```

​	输出：

```txt
Square root of -4 is 0.0+2.0i
Square root of -4-0i, the other side of the cut, is 0.0-2.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.8.3 The csqrt functions （第 196 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.4.2 The csqrt functions （第 544 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.8.3 The csqrt functions （第 178 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.4.2 The csqrt functions （第 479 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cpow (C99)<br />cpowf (C99)<br />cpowl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cpow) | 计算复数幂函数 (函数)    |
| ------------------------------------------------------------ | ------------------------ |
| [sqrt <br />sqrtf (C99)<br />sqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sqrt) | 计算平方根（√xx） (函数) |
| **sqrt** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/sqrt)** |                          |





### csqrtf

原址：[https://zh.cppreference.com/w/c/numeric/complex/csqrt](https://zh.cppreference.com/w/c/numeric/complex/csqrt)

作用：计算复数平方根  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       csqrtf( float complex z );// (1)(C99 起)
double complex      csqrt( double complex z );// (2)(C99 起)
long double complex csqrtl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define sqrt( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复平方根，分支切割线沿负实轴。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csqrtl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csqrt`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csqrtf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`sqrtf`、`[sqrt](http://zh.cppreference.com/w/c/numeric/math/sqrt)`、`sqrtl`）。若 `z` 为虚数，则调用对应的复数版本。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 的平方根，在包含虚轴的右半平面中（沿实轴为 *[0; +∞)*，而沿虚轴为 *(−∞; +∞)*）。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- 考虑虚部符号，函数连续到分支切割上。
- `csqrt([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(csqrt(z))`
- 若 `z` 为 `±0+0i`，则结果为 `+0+0i`
- 若 `z` 为 `x+∞i`，则结果为 `+∞+∞i`，即使 x 为 NaN
- 若 `z` 为 `x+NaNi`，则结果为 `NaN+NaNi`（除非 x 为 ±∞）并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `-∞+yi`，则对于有限正 y 结果为 `+0+∞i`
- 若 `z` 为 `+∞+yi`，则对于有限正 y 结果为 `+∞+0i)`
- 若 `z` 为 `-∞+NaNi`，则结果为 `NaN±∞i`（虚部符号未指定）
- 若 `z` 为 `+∞+NaNi`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+yi`，则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z1 = csqrt(-4);
    printf("Square root of -4 is %.1f%+.1fi\n", creal(z1), cimag(z1));
 
    double complex z2 = csqrt(conj(-4)); // 或 C11 中的 CMPLX(-4, -0.0)
    printf("Square root of -4-0i, the other side of the cut, is "
           "%.1f%+.1fi\n", creal(z2), cimag(z2));
}
```

​	输出：

```txt
Square root of -4 is 0.0+2.0i
Square root of -4-0i, the other side of the cut, is 0.0-2.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.8.3 The csqrt functions （第 196 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.4.2 The csqrt functions （第 544 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.8.3 The csqrt functions （第 178 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.4.2 The csqrt functions （第 479 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cpow (C99)<br />cpowf (C99)<br />cpowl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cpow) | 计算复数幂函数 (函数)    |
| ------------------------------------------------------------ | ------------------------ |
| [sqrt <br />sqrtf (C99)<br />sqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sqrt) | 计算平方根（√xx） (函数) |
| **sqrt** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/sqrt)** |                          |





### csqrtl

原址：[https://zh.cppreference.com/w/c/numeric/complex/csqrt](https://zh.cppreference.com/w/c/numeric/complex/csqrt)

作用：计算复数平方根  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       csqrtf( float complex z );// (1)(C99 起)
double complex      csqrt( double complex z );// (2)(C99 起)
long double complex csqrtl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define sqrt( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复平方根，分支切割线沿负实轴。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csqrtl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csqrt`，若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `csqrtf`。若 `z` 为实数或整数，则宏调用对应的实数函数（`sqrtf`、`[sqrt](http://zh.cppreference.com/w/c/numeric/math/sqrt)`、`sqrtl`）。若 `z` 为虚数，则调用对应的复数版本。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 的平方根，在包含虚轴的右半平面中（沿实轴为 *[0; +∞)*，而沿虚轴为 *(−∞; +∞)*）。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- 考虑虚部符号，函数连续到分支切割上。
- `csqrt([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(csqrt(z))`
- 若 `z` 为 `±0+0i`，则结果为 `+0+0i`
- 若 `z` 为 `x+∞i`，则结果为 `+∞+∞i`，即使 x 为 NaN
- 若 `z` 为 `x+NaNi`，则结果为 `NaN+NaNi`（除非 x 为 ±∞）并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `-∞+yi`，则对于有限正 y 结果为 `+0+∞i`
- 若 `z` 为 `+∞+yi`，则对于有限正 y 结果为 `+∞+0i)`
- 若 `z` 为 `-∞+NaNi`，则结果为 `NaN±∞i`（虚部符号未指定）
- 若 `z` 为 `+∞+NaNi`，则结果为 `+∞+NaNi`
- 若 `z` 为 `NaN+yi`，则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

**示例**

```c
#include <stdio.h>
#include <complex.h>
 
int main(void)
{
    double complex z1 = csqrt(-4);
    printf("Square root of -4 is %.1f%+.1fi\n", creal(z1), cimag(z1));
 
    double complex z2 = csqrt(conj(-4)); // 或 C11 中的 CMPLX(-4, -0.0)
    printf("Square root of -4-0i, the other side of the cut, is "
           "%.1f%+.1fi\n", creal(z2), cimag(z2));
}
```

​	输出：

```txt
Square root of -4 is 0.0+2.0i
Square root of -4-0i, the other side of the cut, is 0.0-2.0i
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.8.3 The csqrt functions （第 196 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.4.2 The csqrt functions （第 544 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.8.3 The csqrt functions （第 178 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.4.2 The csqrt functions （第 479 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [cpow (C99)<br />cpowf (C99)<br />cpowl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cpow) | 计算复数幂函数 (函数)    |
| ------------------------------------------------------------ | ------------------------ |
| [sqrt <br />sqrtf (C99)<br />sqrtl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/sqrt) | 计算平方根（√xx） (函数) |
| **sqrt** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/sqrt)** |                          |





### ctan

原址：[https://zh.cppreference.com/w/c/numeric/complex/ctan](https://zh.cppreference.com/w/c/numeric/complex/ctan)

作用：计算复数正切  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       ctanf( float complex z );// (1)(C99 起)
double complex      ctan( double complex z );// (2)(C99 起)
long double complex ctanl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define tan( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复正切。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctanl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctan`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctanf`。若 `z` 为实数或整数，则该宏调用对应的实函数（`tanf`、`[tan](http://zh.cppreference.com/w/c/numeric/math/tan)`、`tanl`）。若 `z` 为虚数，则该宏调用函数 [tanh](https://zh.cppreference.com/w/c/numeric/math/tanh) 的对应实版本，实现公式 *tan(iy) = i tanh(y)*，而返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若无错误发生，则返回 `z` 的复正切。

​	错误和特殊情况如同运算实现为 `-i * [ctanh](http://zh.cppreference.com/w/c/numeric/complex/ctanh)(i*z)` 一般处理，其中 `i` 是虚数单位。

**注意**

​	正切是复平面上的解析函数，而无分支切割。它对于实部是周期的，周期为 πi，而且沿实轴有一阶极点，位于坐标 *(π(1/2 + n), 0)*。然而无常用浮点表示能准确表示 π/2，故而没有值使得极点错误出现。

正切的数学定义是 

tan z = 

| i(e-iz -eiz ) |
| ------------- |
| e-iz +eiz     |

。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = ctan(1);  // 表现类似沿实轴的实正切
    printf("tan(1+0i) = %f%+fi ( tan(1)=%f)\n", creal(z), cimag(z), tan(1));
 
    double complex z2 = ctan(I); // 表现类似沿虚轴的 tanh
    printf("tan(0+1i) = %f%+fi (tanh(1)=%f)\n", creal(z2), cimag(z2), tanh(1));
}
```

​	输出：

```txt
tan(1+0i) = 1.557408+0.000000i ( tan(1)=1.557408)
tan(0+1i) = 0.000000+0.761594i (tanh(1)=0.761594)
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.6 The ctan functions （第 192 页）

  - 7.25 Type-generic complex <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.6 The ctan functions （第 174 页）

  - 7.22 Type-generic complex <tgcomplex.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)     |
| ------------------------------------------------------------ | --------------------------- |
| [csin (C99)<br />csinf (C99)<br />csinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csin) | 计算复数正弦 (函数)         |
| [ccos (C99)<br />ccosf (C99)<br />ccosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccos) | 计算复数余弦 (函数)         |
| [catan (C99)<br />catanf (C99)<br />catanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catan) | 计算复数反正切 (函数)       |
| [tan <br />tanf (C99)<br />tanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tan) | 计算正切（tanxtan⁡x） (函数) |
| **tan** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/tan)** |                             |





### ctanf

原址：[https://zh.cppreference.com/w/c/numeric/complex/ctan](https://zh.cppreference.com/w/c/numeric/complex/ctan)

作用：计算复数正切  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       ctanf( float complex z );// (1)(C99 起)
double complex      ctan( double complex z );// (2)(C99 起)
long double complex ctanl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define tan( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复正切。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctanl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctan`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctanf`。若 `z` 为实数或整数，则该宏调用对应的实函数（`tanf`、`[tan](http://zh.cppreference.com/w/c/numeric/math/tan)`、`tanl`）。若 `z` 为虚数，则该宏调用函数 [tanh](https://zh.cppreference.com/w/c/numeric/math/tanh) 的对应实版本，实现公式 *tan(iy) = i tanh(y)*，而返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若无错误发生，则返回 `z` 的复正切。

​	错误和特殊情况如同运算实现为 `-i * [ctanh](http://zh.cppreference.com/w/c/numeric/complex/ctanh)(i*z)` 一般处理，其中 `i` 是虚数单位。

**注意**

​	正切是复平面上的解析函数，而无分支切割。它对于实部是周期的，周期为 πi，而且沿实轴有一阶极点，位于坐标 *(π(1/2 + n), 0)*。然而无常用浮点表示能准确表示 π/2，故而没有值使得极点错误出现。

正切的数学定义是 

tan z = 

| i(e-iz -eiz ) |
| ------------- |
| e-iz +eiz     |

。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = ctan(1);  // 表现类似沿实轴的实正切
    printf("tan(1+0i) = %f%+fi ( tan(1)=%f)\n", creal(z), cimag(z), tan(1));
 
    double complex z2 = ctan(I); // 表现类似沿虚轴的 tanh
    printf("tan(0+1i) = %f%+fi (tanh(1)=%f)\n", creal(z2), cimag(z2), tanh(1));
}
```

​	输出：

```txt
tan(1+0i) = 1.557408+0.000000i ( tan(1)=1.557408)
tan(0+1i) = 0.000000+0.761594i (tanh(1)=0.761594)
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.6 The ctan functions （第 192 页）

  - 7.25 Type-generic complex <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.6 The ctan functions （第 174 页）

  - 7.22 Type-generic complex <tgcomplex.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)     |
| ------------------------------------------------------------ | --------------------------- |
| [csin (C99)<br />csinf (C99)<br />csinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csin) | 计算复数正弦 (函数)         |
| [ccos (C99)<br />ccosf (C99)<br />ccosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccos) | 计算复数余弦 (函数)         |
| [catan (C99)<br />catanf (C99)<br />catanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catan) | 计算复数反正切 (函数)       |
| [tan <br />tanf (C99)<br />tanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tan) | 计算正切（tanxtan⁡x） (函数) |
| **tan** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/tan)** |                             |





### ctanh

原址：[https://zh.cppreference.com/w/c/numeric/complex/ctanh](https://zh.cppreference.com/w/c/numeric/complex/ctanh)

作用：计算复数双曲正切  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       ctanhf( float complex z );// (1)(C99 起)
double complex      ctanh( double complex z );// (2)(C99 起)
long double complex ctanhl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define tanh( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复双曲正切。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctanhl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctanh`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctanhf`。若 `z` 为实数或整数，则宏调用对应的实函数（`tanhf`、`[tanh](http://zh.cppreference.com/w/c/numeric/math/tanh)`、`tanhl`）。若 `z` 为虚数，则宏调用函数 [tan](https://zh.cppreference.com/w/c/numeric/math/tan) 的对应实数版本，实现公式 *tanh(iy) = i tan(y)*，而返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 的复双曲正切。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `ctanh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(ctanh(z))`
- `ctanh(-z) == -ctanh(z)`
- 若 `z` 为 `+0+0i`，则结果为 `+0+0i`
- 若 `z` 为 `x+∞i`（对于任何[[1\]](https://zh.cppreference.com/w/c/numeric/complex/ctanh#cite_note-1)有限 x），结果为 `NaN+NaNi` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+NaN`（对于任何[[2\]](https://zh.cppreference.com/w/c/numeric/complex/ctanh#cite_note-2)有限 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），则结果为 `1+0i`
- 若 `z` 为 `+∞+∞i`，则结果为 `1±0i`（虚部符号未指定）
- 若 `z` 为 `+∞+NaNi`，则结果为 `1±0i`（虚部符号未指定）
- 若 `z` 为 `NaN+0i`，则结果为 `NaN+0i`
- 若 `z` 为 `NaN+yi`（对于任何非零 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

1. [↑](https://zh.cppreference.com/w/c/numeric/complex/ctanh#cite_ref-1) 由 [DR471](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1892.htm#dr_471)，这只对非零 x 成立。若 `z` 为 `0+∞i`，则结果应为 `0+NaNi`。
2. [↑](https://zh.cppreference.com/w/c/numeric/complex/ctanh#cite_ref-2) 由 [DR471](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1892.htm#dr_471)，这只对非零 x 成立。若 `z` 为 `0+NaNi`，则结果应为 `0+NaNi` 。

**注意**

双曲正切的数学定义是 

tanh z = 

| ez -e-z |
| ------- |
| ez +e-z |

。

​	双曲正切是复平面上的解析函数且无分支切割。它对于虚部是周期的，周期为 πi，而且沿虚轴有一阶极点，位于坐标 *(0, π(1/2 + n))*。然而无常用浮点表示能准确表示 π/2，故没有参数值能导致极点错误。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = ctanh(1);  // 表现类似沿实轴的 tanh
    printf("tanh(1+0i) = %f%+fi (tanh(1)=%f)\n", creal(z), cimag(z), tanh(1));
 
    double complex z2 = ctanh(I); // 表现类似沿虚轴的正切
    printf("tanh(0+1i) = %f%+fi ( tan(1)=%f)\n", creal(z2), cimag(z2), tan(1));
}
```

​	输出：

```txt
tanh(1+0i) = 0.761594+0.000000i (tanh(1)=0.761594)
tanh(0+1i) = 0.000000+1.557408i ( tan(1)=1.557408)
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.6 The ctanh functions （第 194 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.6 The ctanh functions （第 542 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.6 The ctanh functions （第 176 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.6 The ctanh functions （第 477 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [csinh (C99)<br />csinhf (C99)<br />csinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csinh) | 计算复数双曲正弦 (函数)           |
| ------------------------------------------------------------ | --------------------------------- |
| [ccosh (C99)<br />ccoshf (C99)<br />ccoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccosh) | 计算复双曲余弦 (函数)             |
| [catanh (C99)<br />catanhf (C99)<br />catanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catanh) | 计算复数反双曲正切 (函数)         |
| [tanh <br />tanhf (C99)<br />tanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tanh) | 计算双曲正切（tanhxtanh⁡x） (函数) |
| **tanh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/tanh)** |                                   |





### ctanhf

原址：[https://zh.cppreference.com/w/c/numeric/complex/ctanh](https://zh.cppreference.com/w/c/numeric/complex/ctanh)

作用：计算复数双曲正切  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       ctanhf( float complex z );// (1)(C99 起)
double complex      ctanh( double complex z );// (2)(C99 起)
long double complex ctanhl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define tanh( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复双曲正切。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctanhl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctanh`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctanhf`。若 `z` 为实数或整数，则宏调用对应的实函数（`tanhf`、`[tanh](http://zh.cppreference.com/w/c/numeric/math/tanh)`、`tanhl`）。若 `z` 为虚数，则宏调用函数 [tan](https://zh.cppreference.com/w/c/numeric/math/tan) 的对应实数版本，实现公式 *tanh(iy) = i tan(y)*，而返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 的复双曲正切。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `ctanh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(ctanh(z))`
- `ctanh(-z) == -ctanh(z)`
- 若 `z` 为 `+0+0i`，则结果为 `+0+0i`
- 若 `z` 为 `x+∞i`（对于任何[[1\]](https://zh.cppreference.com/w/c/numeric/complex/ctanh#cite_note-1)有限 x），结果为 `NaN+NaNi` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+NaN`（对于任何[[2\]](https://zh.cppreference.com/w/c/numeric/complex/ctanh#cite_note-2)有限 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），则结果为 `1+0i`
- 若 `z` 为 `+∞+∞i`，则结果为 `1±0i`（虚部符号未指定）
- 若 `z` 为 `+∞+NaNi`，则结果为 `1±0i`（虚部符号未指定）
- 若 `z` 为 `NaN+0i`，则结果为 `NaN+0i`
- 若 `z` 为 `NaN+yi`（对于任何非零 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

1. [↑](https://zh.cppreference.com/w/c/numeric/complex/ctanh#cite_ref-1) 由 [DR471](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1892.htm#dr_471)，这只对非零 x 成立。若 `z` 为 `0+∞i`，则结果应为 `0+NaNi`。
2. [↑](https://zh.cppreference.com/w/c/numeric/complex/ctanh#cite_ref-2) 由 [DR471](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1892.htm#dr_471)，这只对非零 x 成立。若 `z` 为 `0+NaNi`，则结果应为 `0+NaNi` 。

**注意**

双曲正切的数学定义是 

tanh z = 

| ez -e-z |
| ------- |
| ez +e-z |

。

​	双曲正切是复平面上的解析函数且无分支切割。它对于虚部是周期的，周期为 πi，而且沿虚轴有一阶极点，位于坐标 *(0, π(1/2 + n))*。然而无常用浮点表示能准确表示 π/2，故没有参数值能导致极点错误。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = ctanh(1);  // 表现类似沿实轴的 tanh
    printf("tanh(1+0i) = %f%+fi (tanh(1)=%f)\n", creal(z), cimag(z), tanh(1));
 
    double complex z2 = ctanh(I); // 表现类似沿虚轴的正切
    printf("tanh(0+1i) = %f%+fi ( tan(1)=%f)\n", creal(z2), cimag(z2), tan(1));
}
```

​	输出：

```txt
tanh(1+0i) = 0.761594+0.000000i (tanh(1)=0.761594)
tanh(0+1i) = 0.000000+1.557408i ( tan(1)=1.557408)
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.6 The ctanh functions （第 194 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.6 The ctanh functions （第 542 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.6 The ctanh functions （第 176 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.6 The ctanh functions （第 477 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [csinh (C99)<br />csinhf (C99)<br />csinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csinh) | 计算复数双曲正弦 (函数)           |
| ------------------------------------------------------------ | --------------------------------- |
| [ccosh (C99)<br />ccoshf (C99)<br />ccoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccosh) | 计算复双曲余弦 (函数)             |
| [catanh (C99)<br />catanhf (C99)<br />catanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catanh) | 计算复数反双曲正切 (函数)         |
| [tanh <br />tanhf (C99)<br />tanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tanh) | 计算双曲正切（tanhxtanh⁡x） (函数) |
| **tanh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/tanh)** |                                   |





### ctanhl

原址：[https://zh.cppreference.com/w/c/numeric/complex/ctanh](https://zh.cppreference.com/w/c/numeric/complex/ctanh)

作用：计算复数双曲正切  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       ctanhf( float complex z );// (1)(C99 起)
double complex      ctanh( double complex z );// (2)(C99 起)
long double complex ctanhl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define tanh( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复双曲正切。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctanhl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctanh`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctanhf`。若 `z` 为实数或整数，则宏调用对应的实函数（`tanhf`、`[tanh](http://zh.cppreference.com/w/c/numeric/math/tanh)`、`tanhl`）。若 `z` 为虚数，则宏调用函数 [tan](https://zh.cppreference.com/w/c/numeric/math/tan) 的对应实数版本，实现公式 *tanh(iy) = i tan(y)*，而返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若不出现错误，则返回 `z` 的复双曲正切。

**错误处理**及特殊值

​	报告的错误与 [math_errhandling](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 一致。

​	若实现支持 IEEE 浮点算术，则

- `ctanh([conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(z)) == [conj](http://zh.cppreference.com/w/c/numeric/complex/conj)(ctanh(z))`
- `ctanh(-z) == -ctanh(z)`
- 若 `z` 为 `+0+0i`，则结果为 `+0+0i`
- 若 `z` 为 `x+∞i`（对于任何[[1\]](https://zh.cppreference.com/w/c/numeric/complex/ctanh#cite_note-1)有限 x），结果为 `NaN+NaNi` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `x+NaN`（对于任何[[2\]](https://zh.cppreference.com/w/c/numeric/complex/ctanh#cite_note-2)有限 x），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `+∞+yi`（对于任何有限正 y），则结果为 `1+0i`
- 若 `z` 为 `+∞+∞i`，则结果为 `1±0i`（虚部符号未指定）
- 若 `z` 为 `+∞+NaNi`，则结果为 `1±0i`（虚部符号未指定）
- 若 `z` 为 `NaN+0i`，则结果为 `NaN+0i`
- 若 `z` 为 `NaN+yi`（对于任何非零 y），则结果为 `NaN+NaNi` 并可能引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 若 `z` 为 `NaN+NaNi`，则结果为 `NaN+NaNi`

1. [↑](https://zh.cppreference.com/w/c/numeric/complex/ctanh#cite_ref-1) 由 [DR471](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1892.htm#dr_471)，这只对非零 x 成立。若 `z` 为 `0+∞i`，则结果应为 `0+NaNi`。
2. [↑](https://zh.cppreference.com/w/c/numeric/complex/ctanh#cite_ref-2) 由 [DR471](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1892.htm#dr_471)，这只对非零 x 成立。若 `z` 为 `0+NaNi`，则结果应为 `0+NaNi` 。

**注意**

双曲正切的数学定义是 

tanh z = 

| ez -e-z |
| ------- |
| ez +e-z |

。

​	双曲正切是复平面上的解析函数且无分支切割。它对于虚部是周期的，周期为 πi，而且沿虚轴有一阶极点，位于坐标 *(0, π(1/2 + n))*。然而无常用浮点表示能准确表示 π/2，故没有参数值能导致极点错误。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = ctanh(1);  // 表现类似沿实轴的 tanh
    printf("tanh(1+0i) = %f%+fi (tanh(1)=%f)\n", creal(z), cimag(z), tanh(1));
 
    double complex z2 = ctanh(I); // 表现类似沿虚轴的正切
    printf("tanh(0+1i) = %f%+fi ( tan(1)=%f)\n", creal(z2), cimag(z2), tan(1));
}
```

​	输出：

```txt
tanh(1+0i) = 0.761594+0.000000i (tanh(1)=0.761594)
tanh(0+1i) = 0.000000+1.557408i ( tan(1)=1.557408)
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.6.6 The ctanh functions （第 194 页）

  - 7.25 Type-generic math <tgmath.h> （第 373-375 页）

  - G.6.2.6 The ctanh functions （第 542 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.6.6 The ctanh functions （第 176 页）

  - 7.22 Type-generic math <tgmath.h> （第 335-337 页）

  - G.6.2.6 The ctanh functions （第 477 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [csinh (C99)<br />csinhf (C99)<br />csinhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csinh) | 计算复数双曲正弦 (函数)           |
| ------------------------------------------------------------ | --------------------------------- |
| [ccosh (C99)<br />ccoshf (C99)<br />ccoshl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccosh) | 计算复双曲余弦 (函数)             |
| [catanh (C99)<br />catanhf (C99)<br />catanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catanh) | 计算复数反双曲正切 (函数)         |
| [tanh <br />tanhf (C99)<br />tanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tanh) | 计算双曲正切（tanhxtanh⁡x） (函数) |
| **tanh** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/tanh)** |                                   |





### ctanl

原址：[https://zh.cppreference.com/w/c/numeric/complex/ctan](https://zh.cppreference.com/w/c/numeric/complex/ctan)

作用：计算复数正切  (函数)

备注：
```c
// 在标头 <complex.h> 定义
float complex       ctanf( float complex z );// (1)(C99 起)
double complex      ctan( double complex z );// (2)(C99 起)
long double complex ctanl( long double complex z );// (3)(C99 起)
// 在标头 <tgmath.h> 定义
#define tan( z )// (4)(C99 起)
```

1-3) 计算 `z` 的复正切。

4） 泛型宏：若 `z` 拥有 `long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctanl`。若 `z` 拥有 `double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctan`。若 `z` 拥有 `float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)` 类型，则调用 `ctanf`。若 `z` 为实数或整数，则该宏调用对应的实函数（`tanf`、`[tan](http://zh.cppreference.com/w/c/numeric/math/tan)`、`tanl`）。若 `z` 为虚数，则该宏调用函数 [tanh](https://zh.cppreference.com/w/c/numeric/math/tanh) 的对应实版本，实现公式 *tan(iy) = i tanh(y)*，而返回类型为虚数。

**参数**

| z    | -    | 复数实参 |
| ---- | ---- | -------- |
|      |      |          |

**返回值**

​	若无错误发生，则返回 `z` 的复正切。

​	错误和特殊情况如同运算实现为 `-i * [ctanh](http://zh.cppreference.com/w/c/numeric/complex/ctanh)(i*z)` 一般处理，其中 `i` 是虚数单位。

**注意**

​	正切是复平面上的解析函数，而无分支切割。它对于实部是周期的，周期为 πi，而且沿实轴有一阶极点，位于坐标 *(π(1/2 + n), 0)*。然而无常用浮点表示能准确表示 π/2，故而没有值使得极点错误出现。

正切的数学定义是 

tan z = 

| i(e-iz -eiz ) |
| ------------- |
| e-iz +eiz     |

。

**示例**

```c
#include <stdio.h>
#include <math.h>
#include <complex.h>
 
int main(void)
{
    double complex z = ctan(1);  // 表现类似沿实轴的实正切
    printf("tan(1+0i) = %f%+fi ( tan(1)=%f)\n", creal(z), cimag(z), tan(1));
 
    double complex z2 = ctan(I); // 表现类似沿虚轴的 tanh
    printf("tan(0+1i) = %f%+fi (tanh(1)=%f)\n", creal(z2), cimag(z2), tanh(1));
}
```

​	输出：

```txt
tan(1+0i) = 1.557408+0.000000i ( tan(1)=1.557408)
tan(0+1i) = 0.000000+0.761594i (tanh(1)=0.761594)
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.3.5.6 The ctan functions （第 192 页）

  - 7.25 Type-generic complex <tgmath.h> （第 373-375 页）

  - G.7 Type-generic math <tgmath.h> （第 545 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.3.5.6 The ctan functions （第 174 页）

  - 7.22 Type-generic complex <tgcomplex.h> （第 335-337 页）

  - G.7 Type-generic math <tgmath.h> （第 480 页）

**参阅**

| [ctanh (C99)<br />ctanhf (C99)<br />ctanhl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | 计算复数双曲正切 (函数)     |
| ------------------------------------------------------------ | --------------------------- |
| [csin (C99)<br />csinf (C99)<br />csinl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/csin) | 计算复数正弦 (函数)         |
| [ccos (C99)<br />ccosf (C99)<br />ccosl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/ccos) | 计算复数余弦 (函数)         |
| [catan (C99)<br />catanf (C99)<br />catanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/catan) | 计算复数反正切 (函数)       |
| [tan <br />tanf (C99)<br />tanl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/tan) | 计算正切（tanxtan⁡x） (函数) |
| **tan** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/complex/tan)** |                             |






