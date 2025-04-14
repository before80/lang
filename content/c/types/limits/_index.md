+++
title = "数值极限"
date = 2025-04-14T15:56:56+08:00
weight = 70
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/types/limits](https://zh.cppreference.com/w/c/types/limits)

## 整数类型的极限

### 核心语言整数类型的极限

| 在标头 `<limits.h>` 定义                                   |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| BOOL_WIDTH (C23)<br />                                       | bool 的位数 (宏常量)                                         |
| CHAR_BIT<br />                                               | 字节的位数 (宏常量)                                          |
| MB_LEN_MAX<br />                                             | 多字节字符的最大字节数 (宏常量)                              |
| CHAR_WIDTH (C23)<br />                                       | char 的位数，同 `CHAR_BIT` (宏常量)                          |
| CHAR_MIN<br />                                               | char 的最小值 (宏常量)                                       |
| CHAR_MAX<br />                                               | char 的最大值 (宏常量)                                       |
| SCHAR_WIDTH (C23)<br />SHRT_WIDTH (C23)<br />INT_WIDTH (C23)<br />LONG_WIDTH (C23)<br />LLONG_WIDTH (C23)<br /> | 分别为 signed char、short、int、long 及 long long 的位数 (宏常量) |
| SCHAR_MIN <br />SHRT_MIN <br />INT_MIN <br />LONG_MIN <br />LLONG_MIN (C99)<br /> | 分别是 signed char、short、int、long 和 long long 的最小值 (宏常量) |
| SCHAR_MAX <br />SHRT_MAX <br />INT_MAX <br />LONG_MAX <br />LLONG_MAX (C99)<br /> | 分别是 signed char、short、int、long 和 long long 的最大值 (宏常量) |
| UCHAR_WIDTH (C23)<br />USHRT_WIDTH (C23)<br />UINT_WIDTH (C23)<br />ULONG_WIDTH (C23)<br />ULLONG_WIDTH (C23)<br /> | 分别为 unsigned char、unsigned short、unsigned int、unsigned long 及 unsigned long long 的位数 (宏常量) |
| UCHAR_MAX <br />USHRT_MAX <br />UINT_MAX <br />ULONG_MAX <br />ULLONG_MAX (C99)<br /> | 分别是 unsigned char、unsigned short、unsigned int、 unsigned long 和 unsigned long long 的最大值 (宏常量) |
| BITINT_MAXWIDTH (C23)<br />                                  | 类型说明符 _BitInt(N) 的位精确整数的声明所能支持的最大宽度 N，大于或等于 `ULLONG_WIDTH` (宏常量) |

### 库类型别名的极限

| 在标头 `<stdint.h>` 定义   |                                                              |
| ---------------------------- | ------------------------------------------------------------ |
| PTRDIFF_WIDTH (C23)<br />    | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) 类型对象的位数 (宏常量) |
| PTRDIFF_MIN (C99)<br />      | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) 的最小值 (宏常量) |
| PTRDIFF_MAX (C99)<br />      | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) 的最大值 (宏常量) |
| SIZE_WIDTH (C23)<br />       | [size_t](https://zh.cppreference.com/w/c/types/size_t) 类型对象的位数 (宏常量) |
| SIZE_MAX (C99)<br />         | [size_t](https://zh.cppreference.com/w/c/types/size_t) 的最大值 (宏常量) |
| SIG_ATOMIC_WIDTH (C23)<br /> | [sig_atomic_t](https://zh.cppreference.com/w/c/program/sig_atomic_t) 类型对象的位数 (宏常量) |
| SIG_ATOMIC_MIN (C99)<br />   | [sig_atomic_t](https://zh.cppreference.com/w/c/program/sig_atomic_t) 的最小值 (宏常量) |
| SIG_ATOMIC_MAX (C99)<br />   | [sig_atomic_t](https://zh.cppreference.com/w/c/program/sig_atomic_t) 的最大值 (宏常量) |
| WINT_WIDTH (C23)<br />       | wint_t 类型对象的位数 (宏常量)                               |
| WINT_MIN (C99)<br />         | wint_t 的最小值 (宏常量)                                     |
| WINT_MAX (C99)<br />         | wint_t 的最大值 (宏常量)                                     |
| 在标头 `<wchar.h>` 定义    |                                                              |
| 在标头 `<stdint.h>` 定义   |                                                              |
| WCHAR_WIDTH (C23)<br />      | wchar_t 类型对象的位数 (宏常量)                              |
| WCHAR_MIN (C99)<br />        | wchar_t 的最小值 (宏常量)                                    |
| WCHAR_MAX (C99)<br />        | wchar_t 的最大值 (宏常量)                                    |

### 注解

​	这些常量，除了 `CHAR_BIT` 和 `MB_LEN_MAX`，都要求其类型匹配[整型提升](https://zh.cppreference.com/w/c/language/conversion#.E6.95.B4.E6.95.B0.E6.8F.90.E5.8D.87)的结果，一如应用于它们所描述的类型的对象：`CHAR_MAX` 可能拥有类型 int 或 unsigned int，但决非 `char`。同样地 `USHRT_MAX` 可能不拥有无符号类型：其类型可能是 `int`。

​	自立实现可能缺少 typedef 名 [sig_atomic_t](https://zh.cppreference.com/w/c/program/sig_atomic_t) 和/或 `wint_t`，此情况下相应地缺少宏 `SIG_ATOMIC_*` 和/或 `WINT_*`。

### 示例

```c
#include <limits.h>
#include <stdint.h>
#include <stdio.h>
 
int main(void)
{   
    printf("CHAR_BIT       = %d\n", CHAR_BIT);
    printf("MB_LEN_MAX     = %d\n\n", MB_LEN_MAX);
 
    printf("CHAR_MIN       = %+d\n", CHAR_MIN);
    printf("CHAR_MAX       = %+d\n", CHAR_MAX);
    printf("SCHAR_MIN      = %+d\n", SCHAR_MIN);
    printf("SCHAR_MAX      = %+d\n", SCHAR_MAX);
    printf("UCHAR_MAX      = %u\n\n", UCHAR_MAX);
 
    printf("SHRT_MIN       = %+d\n", SHRT_MIN);
    printf("SHRT_MAX       = %+d\n", SHRT_MAX);
    printf("USHRT_MAX      = %u\n\n", USHRT_MAX);
 
    printf("INT_MIN        = %+d\n", INT_MIN);
    printf("INT_MAX        = %+d\n", INT_MAX);
    printf("UINT_MAX       = %u\n\n", UINT_MAX);
 
    printf("LONG_MIN       = %+ld\n", LONG_MIN);
    printf("LONG_MAX       = %+ld\n", LONG_MAX);
    printf("ULONG_MAX      = %lu\n\n", ULONG_MAX);
 
    printf("LLONG_MIN      = %+lld\n", LLONG_MIN);
    printf("LLONG_MAX      = %+lld\n", LLONG_MAX);
    printf("ULLONG_MAX     = %llu\n\n", ULLONG_MAX);
 
    printf("PTRDIFF_MIN    = %td\n", PTRDIFF_MIN);
    printf("PTRDIFF_MAX    = %+td\n", PTRDIFF_MAX);
    printf("SIZE_MAX       = %zu\n", SIZE_MAX);
    printf("SIG_ATOMIC_MIN = %+jd\n",(intmax_t)SIG_ATOMIC_MIN);
    printf("SIG_ATOMIC_MAX = %+jd\n",(intmax_t)SIG_ATOMIC_MAX);
    printf("WCHAR_MIN      = %+jd\n",(intmax_t)WCHAR_MIN);
    printf("WCHAR_MAX      = %+jd\n",(intmax_t)WCHAR_MAX);
    printf("WINT_MIN       = %jd\n", (intmax_t)WINT_MIN);
    printf("WINT_MAX       = %jd\n", (intmax_t)WINT_MAX);
}
```

可能的输出：

```txt
CHAR_BIT       = 8
MB_LEN_MAX     = 16
 
CHAR_MIN       = -128
CHAR_MAX       = +127
SCHAR_MIN      = -128
SCHAR_MAX      = +127
UCHAR_MAX      = 255
 
SHRT_MIN       = -32768
SHRT_MAX       = +32767
USHRT_MAX      = 65535
 
INT_MIN        = -2147483648
INT_MAX        = +2147483647
UINT_MAX       = 4294967295
 
LONG_MIN       = -9223372036854775808
LONG_MAX       = +9223372036854775807
ULONG_MAX      = 18446744073709551615
 
LLONG_MIN      = -9223372036854775808
LLONG_MAX      = +9223372036854775807
ULLONG_MAX     = 18446744073709551615
 
PTRDIFF_MIN    = -9223372036854775808
PTRDIFF_MAX    = +9223372036854775807
SIZE_MAX       = 18446744073709551615
SIG_ATOMIC_MIN = -2147483648
SIG_ATOMIC_MAX = +2147483647
WCHAR_MIN      = -2147483648
WCHAR_MAX      = +2147483647
WINT_MIN       = 0
WINT_MAX       = 4294967295
```

## 浮点数类型的极限

| 在标头 `<float.h>` 定义                                    |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| FLT_RADIX<br />                                              | 所有三种浮点数类型的表示中使用的底（整数基） (宏常量)        |
| DECIMAL_DIG (C99)<br />                                      | 将 long double 转换成十进制小数，再转回 long double 而保持同一值，至少需要 `DECIMAL_DIG` 位小数：此乃 long double 序列化/反序列化所需的十进制精度 (宏常量) |
| FLT_DECIMAL_DIG (C11)<br />DBL_DECIMAL_DIG (C11)<br />LDBL_DECIMAL_DIG<br /> | 将 float/double/long double 转换成十进制小数再转换回同一值，至少需要 `FLT_DECIMAL_DIG`/`DBL_DECIMAL_DIG`/`LDBL_DECIMAL_DIG` 位小数：此乃浮点数序列化/反序列化所需的十进制精度。分别定义为至少 6、10、10，而 IEEE float 为 9，IEEE double 为 17。（另见 C++ 对应物 [`max_digits10`](https://zh.cppreference.com/w/cpp/types/numeric_limits/max_digits10)） (宏常量) |
| FLT_MIN<br />DBL_MIN<br />LDBL_MIN<br />                     | 分别为 float、double 及 long double 的最小正规正值 (宏常量)  |
| FLT_TRUE_MIN (C11)<br />DBL_TRUE_MIN (C11)<br />LDBL_TRUE_MIN<br /> | 分别为 float、double 和 long double 的最小正值 (宏常量)      |
| FLT_MAX<br />DBL_MAX<br />LDBL_MAX<br />                     | 分别为 float、double 和 long double 的最大有限正值 (宏常量)  |
| FLT_EPSILON<br />DBL_EPSILON<br />LDBL_EPSILON<br />         | 分别为 1.0 与下一个可表示的float、double 和 long double 值之差 (宏常量) |
| FLT_DIG<br />DBL_DIG<br />LDBL_DIG<br />                     | 保证能从文本转换为 float/double/long double 再转换回文本，而不会发生改变或上溢出的十进制位数（细节见 C++ 对应物 [`digits10`](https://zh.cppreference.com/w/cpp/types/numeric_limits/digits10)） (宏常量) |
| FLT_MANT_DIG<br />DBL_MANT_DIG<br />LDBL_MANT_DIG<br />      | 分别为 float、double 和 long double 所能表示而不损失精度的，浮点数尾数中的 `FLT_RADIX` 进制位数 (宏常量) |
| FLT_MIN_EXP<br />DBL_MIN_EXP<br />LDBL_MIN_EXP<br />         | 分别为对应 float、double 和 long double 的最小负整数，使得 `FLT_RADIX` 的该数减一次幂为正规 (宏常量) |
| FLT_MIN_10_EXP<br />DBL_MIN_10_EXP<br />LDBL_MIN_10_EXP<br /> | 分别为对应 float、double 和 long double 的最小负整数，使得 10 的该数次幂为正规的 (宏常量) |
| FLT_MAX_EXP<br />DBL_MAX_EXP<br />LDBL_MAX_EXP<br />         | 分别为能够使 `FLT_RADIX` 的该数减一次幂为可表示的有限的 float、double 与 long double 的最大正整数 (宏常量) |
| FLT_MAX_10_EXP<br />DBL_MAX_10_EXP<br />LDBL_MAX_10_EXP<br /> | 分别为能够使 10 的该数次幂为可表示的有限的 float、double 与 long double 的最大正整数 (宏常量) |
| [FLT_ROUNDS<br />](https://zh.cppreference.com/w/c/types/limits/FLT_ROUNDS) | 浮点数算术的舍入模式，等于 float_round_style (宏常量)        |
| [FLT_EVAL_METHOD (C99)<br />](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD) | 指定所有算术运算以什么精度执行 (宏常量)                      |
| FLT_HAS_SUBNORM (C11)<br />DBL_HAS_SUBNORM (C11)<br />LDBL_HAS_SUBNORM (C23 弃用)<br /> | 类型是否支持非正规（subnormal，[denormal](https://en.wikipedia.org/wiki/Denormal_number)）数：<br />`-1` 为不确定，<br />`0` 为不支持，<br />`1` 为支持 (宏常量) |



### 示例

```c
#include <float.h>
#include <math.h>
#include <stdio.h>
 
int main(void)
{
    printf("DECIMAL_DIG     = %d\n", DECIMAL_DIG);
    printf("FLT_DECIMAL_DIG = %d\n", FLT_DECIMAL_DIG);
    printf("FLT_RADIX       = %d\n", FLT_RADIX);
    printf("FLT_MIN         = %e\n", FLT_MIN);
    printf("FLT_MAX         = %e\n", FLT_MAX);
    printf("FLT_EPSILON     = %e\n", FLT_EPSILON);
    printf("FLT_DIG         = %d\n", FLT_DIG);
    printf("FLT_MANT_DIG    = %d\n", FLT_MANT_DIG);
    printf("FLT_MIN_EXP     = %d\n", FLT_MIN_EXP);
    printf("FLT_MIN_10_EXP  = %d\n", FLT_MIN_10_EXP);
    printf("FLT_MAX_EXP     = %d\n", FLT_MAX_EXP);
    printf("FLT_MAX_10_EXP  = %d\n", FLT_MAX_10_EXP);
    printf("FLT_ROUNDS      = %d\n", FLT_ROUNDS);
    printf("FLT_EVAL_METHOD = %d\n", FLT_EVAL_METHOD);
    printf("FLT_HAS_SUBNORM = %d\n", FLT_HAS_SUBNORM);
}
```

可能的输出：

```txt
DECIMAL_DIG     = 37
FLT_DECIMAL_DIG = 9
FLT_RADIX       = 2
FLT_MIN         = 1.175494e-38
FLT_MAX         = 3.402823e+38
FLT_EPSILON     = 1.192093e-07
FLT_DIG         = 6
FLT_MANT_DIG    = 24
FLT_MIN_EXP     = -125
FLT_MIN_10_EXP  = -37
FLT_MAX_EXP     = 128
FLT_MAX_10_EXP  = 38
FLT_ROUNDS      = 1
FLT_EVAL_METHOD = 1
FLT_HAS_SUBNORM = 1
```

## 参阅

**C 数值极限接口**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/climits)**