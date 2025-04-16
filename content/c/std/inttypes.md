+++
title = "<inttypes.h>"
date = 2025-04-16T12:09:12+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

## 类型



## 宏



## 函数










### imaxabs

原址：[https://zh.cppreference.com/w/c/numeric/math/abs](https://zh.cppreference.com/w/c/numeric/math/abs)

```c
int        abs( int n );
long       labs( long n );
long long llabs( long long n ); // (C99 起)
```

​	计算整数的绝对值。若返回类型无法表示结果，则行为未定义。

**参数**

| n    | -    | 整数值 |
| ---- | ---- | ------ |

**返回值**

​	n 的绝对值（即 `|n|`），若它能被表示。

**注解**

​	在补码系统中，最小负值的绝对值处于对应整数范围外，例如对于 32 位补码类型 int，[INT_MIN](https://zh.cppreference.com/w/c/types/limits) 为 -2147483648，但其绝对值应有的结果是 2147483648，大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)（其值为 2147483647）。

**示例**



```c
#include <limits.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    printf("abs(+3) = %d\n", abs(+3));
    printf("abs(-3) = %d\n", abs(-3));
 
//  printf("%+d\n", abs(INT_MIN)); // 在补码系统上是未定义行为
}
```

​	输出：

```txt
abs(+3) = 3
abs(-3) = 3
```




### imaxdiv

原址：[https://zh.cppreference.com/w/c/numeric/math/div](https://zh.cppreference.com/w/c/numeric/math/div)

```c
div_t     div( int x, int y ); // (1)	
ldiv_t    ldiv( long x, long y ); // (2)	
lldiv_t   lldiv( long long x, long long y ); // (3)	(C99 起)
```

​	计算分子 `x` 除以分母 `y` 的商和余数。

| ​	同时计算商和余数。商为舍弃小数部分（向零取整）的代数商。余数满足 quot * y + rem == x。 | (C99 前) |
| ------------------------------------------------------------ | -------- |
| ​	同时计算商（表达式 x / y 的结果）和余数（表达式 x % y 的结果）。 | (C99 起) |

**参数**

| x, y | -    | 整数值 |
| ---- | ---- | ------ |

**返回值**

​	若余数和商都能表示成对应类型的对象（分别为 int、long、long long、[intmax_t](http://zh.cppreference.com/w/c/types/integer)），则将两者作为返回作为定义如下的 `div_t`、`ldiv_t`、`lldiv_t`、`imaxdiv_t` 类型对象返回：

**div_t**

```c
struct div_t { int quot; int rem; };
```

​	或

```c
struct div_t { int rem; int quot; };
```

**ldiv_t**

```c
struct ldiv_t { long quot; long rem; };
```

​	或

```c
struct ldiv_t { long rem; long quot; };
```

**lldiv_t**

```c
struct lldiv_t { long long quot; long long rem; };
```

​	或

```c
struct lldiv_t { long long rem; long long quot; };
```

**imaxdiv_t**

```c
struct imaxdiv_t { intmax_t quot; intmax_t rem; };
```

​	或

```c
struct imaxdiv_t { intmax_t rem; intmax_t quot; };
```

​	若余数或商无法表示，则行为未定义。

**注意**

​	C99 前，若操作数之一为负，则内建的除法和取余运算符中的商取整方向和余数符号是实现定义的，但它在 `div` 和 `ldiv` 中良好定义。

​	多数平台上，单条 CPU 指令可同时获得商和余数，而此函数可以活用这点，尽管编译器通常能在适合处合并临近的 / 和 %。

**示例**



```c
#include <assert.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
#include <stdlib.h>
 
void reverse(char* first, char* last)
{
    for (--last; first < last; ++first, --last)
    {
        char c = *last;
        *last = *first;
        *first = c;
    }
}
 
// 缓冲区溢出的情况下返回空缓冲区
char* itoa(int n, int base, char* buf, size_t buf_size)
{
    assert(2 <= base && base <= 16 && buf && buf_size);
    div_t dv = {.quot = n};
    char* p = buf;
    do
    {
        if (!--buf_size)
            return (*buf = '\0'), buf;
        dv = div(dv.quot, base);
        *p++ = "0123456789abcdef"[abs(dv.rem)];
    }
    while(dv.quot);
    if (n < 0)
        *p++ = '-';
    *p = '\0';
    reverse(buf, p);
    return buf;
}
 
int main(void)
{
    char buf[16];
    printf("%s\n", itoa(0, 2, buf, sizeof buf));
    printf("%s\n", itoa(007, 3, buf, sizeof buf));
    printf("%s\n", itoa(12346, 10, buf, sizeof buf));
    printf("%s\n", itoa(-12346, 10, buf, sizeof buf));
    printf("%s\n", itoa(-42, 2, buf, sizeof buf));
    printf("%s\n", itoa(INT_MAX, 16, buf, sizeof buf));
    printf("%s\n", itoa(INT_MIN, 16, buf, sizeof buf));
}
```

​	可能的输出：

```txt
0
21
12346
-12346
-101010
7fffffff
-80000000
```




### strtoimax

原址：[https://zh.cppreference.com/w/c/string/byte/strtoimax](https://zh.cppreference.com/w/c/string/byte/strtoimax)

```c
intmax_t strtoimax( const char* restrict nptr,
                    char** restrict endptr, int base ); // (1)	(C99 起)
uintmax_t strtoumax( const char* restrict nptr,
                     char** restrict endptr, int base ); // (2)	(C99 起)
```

​	转译 nptr 所指向的字节字符串中的一个整数。

​	舍弃所有空白符（以调用 [`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) 鉴别），直到找到首个非空白符，然后取尽可能多的字符组成合法的*底 n* （其中 n=`base`）的整数表示，并将它们转换成一个整数。合法的整数由下列部分组成：

- (可选)正或负号
- (可选)指示八进制底的前缀（`0`）（仅当底为 8 或 0 时应用）
- (可选)指示十六进制底的前缀（`0x` 或 `0X`）（仅当底为 16 或 0 时应用）
- 数字序列

​	底的合法集是 `{0, 2, 3, ..., 36}`。合法数字集对于底 2 整数是 `{0, 1}`，对于底 3 整数是 `{0, 1, 2}`，以此类推。对于大于 `10` 的底，合法数字包含字母字符，从对于底 `11` 整数的 `Aa` 到对于底 `36` 整数的 `Zz`。忽略字符大小写。

​	当前安装的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)可能接受另外的数字格式。

​	如果 `base` 是 0，那么自动检测数值进制：如果前缀是 `0`，那么底是八进制，如果前缀是 `0x` 或 `0X`，那么底是十六进制，否则底是十进制。

​	如果符号是输入序列的一部分，那么对从数字序列计算得来的数字值取反，如同用结果类型的[一元减](https://zh.cppreference.com/w/c/language/operator_arithmetic#.E4.B8.80.E5.85.83.E7.AE.97.E6.9C.AF)。

​	此函数设置 endptr 所指向的指针指向最后一个转译字符的后一字符。若 endptr 为空指针，则忽略它。

​	若 nptr 为空字符串或无期待的形式，则不进行转换，并（若 enptr 非空指针）将 nptr 存储于 endptr 所指向的对象。

**参数**

| nptr   | -    | 指向要被转译的空终止字符串的指针 |
| ------ | ---- | -------------------------------- |
| endptr | -    | 指向指向字符的指针的指针         |
| base   | -    | 被转译整数的*底*                 |

**返回值**

- 若成功，则返回对应 `str` 内容的整数。
- 若整数落在对应的返回类型范围外，则发生值域错误（设置 [errno](https://zh.cppreference.com/w/c/error/errno) 为 [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros)），并返回 [INTMAX_MAX](https://zh.cppreference.com/w/c/types/integer)、[INTMAX_MIN](https://zh.cppreference.com/w/c/types/integer)、[UINTMAX_MAX](https://zh.cppreference.com/w/c/types/integer) 或 0 中的最接近者。
- 若无法进行转换，则返回 0。

**示例**



```c
#include <errno.h>
#include <inttypes.h>
#include <stdio.h>
#include <string.h>
 
int main(void)
{
    char* endptr = NULL;
 
    printf("%ld\n", strtoimax(" -123junk",&endptr,10)); // 底 10
    printf("%ld\n", strtoimax("11111111",&endptr,2));   // 底 2
    printf("%ld\n", strtoimax("XyZ",&endptr,36));       // 底 36
    printf("%ld\n", strtoimax("010",&endptr,0));        // 八进制自动检测
    printf("%ld\n", strtoimax("10",&endptr,0));         // 十进制自动检测
    printf("%ld\n", strtoimax("0x10",&endptr,0));       // 十六进制自动检测
 
    // 值域错误：LONG_MAX+1 --> LONG_MAX
    errno = 0;
    printf("%ld\n", strtoimax("9223372036854775808", &endptr, 10));
    printf("%s\n", strerror(errno));
}
```

​	输出：

```txt
-123
255
44027
8
10
16
9223372036854775807
Numerical result out of range
```


### strtoumax

原址：[https://zh.cppreference.com/w/c/string/byte/strtoimax](https://zh.cppreference.com/w/c/string/byte/strtoimax)

```c
intmax_t strtoimax( const char* restrict nptr,
                    char** restrict endptr, int base ); // (1)	(C99 起)
uintmax_t strtoumax( const char* restrict nptr,
                     char** restrict endptr, int base ); // (2)	(C99 起)
```

参见：[strtoimax](#strtoimax)


### wcstoimax

原址：[https://zh.cppreference.com/w/c/string/wide/wcstoimax](https://zh.cppreference.com/w/c/string/wide/wcstoimax)

```c
intmax_t wcstoimax( const wchar_t *restrict nptr,
                    wchar_t **restrict endptr, int base ); // (C99 起)
uintmax_t wcstoumax( const wchar_t *restrict nptr,
                     wchar_t **restrict endptr, int base ); // (C99 起)
```

​	转译 `nptr` 所指向的宽字符串中的整数值。

​	舍弃所有空白符（以调用 [`<swspac>`](https://zh.cppreference.com/w/c/string/wide/iswspace) 鉴别），直到找到首个非空白符，然后取尽可能多的字符组成合法的*底 n* （其中 n=`base`）的无符号整数表示，并将它们转换成一个整数。合法的无符号整数由下列部分组成：

- (可选)正或负号
- (可选)指示八进制底的前缀（`0`）（仅当底为 8 或 0 时应用）
- (可选)指示十六进制底的前缀（`0x` 或 `0X`）（仅当底为 16 或 0 时应用）
- 数字序列

​	底的合法集是 `{0, 2, 3, ..., 36}`。合法数字集对于底 2 整数是 `{0, 1}`，对于底 3 整数是 `{0, 1, 2}`，以此类推。对于大于 `10` 的底，合法数字包含字母字符，从对于底 `11` 整数的 `Aa` 到对于底 `36` 整数的 `Zz`。忽略字符大小写。

​	当前安装的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)可能接受另外的数字格式。

​	如果 `base` 是 0，那么自动检测数值进制：如果前缀是 `0`，那么底是八进制，如果前缀是 `0x` 或 `0X`，那么底是十六进制，否则底是十进制。

​	如果符号是输入序列的一部分，那么对从数字序列计算得来的数字值取反，如同用结果类型的[一元减](https://zh.cppreference.com/w/c/language/operator_arithmetic#.E4.B8.80.E5.85.83.E7.AE.97.E6.9C.AF)，它对无符号整数应用回绕规则。

​	函数将 `endptr` 所指向的指针设为指向最后转译的宽字符的后一宽字符。若 `endptr` 为空指针，则忽略它。

**参数**

| nptr   | -    | 指向待转译的空终止宽字符串的指针 |
| ------ | ---- | -------------------------------- |
| endptr | -    | 指向宽字符指针的指针             |
| base   | -    | 转译整数值的*底*                 |

**返回值**

​	成功时返回对应于 `str` 内容的整数值。若转得的值落在对应类型之外，则出现值域错误，并返回 [INTMAX_MAX](https://zh.cppreference.com/w/c/types/integer)、[INTMAX_MIN](https://zh.cppreference.com/w/c/types/integer)、[UINTMAX_MAX](https://zh.cppreference.com/w/c/types/integer) 或 0 中的最接近者。若无法进行转换，则返回 0。

**示例**



```c
#include <errno.h>
#include <inttypes.h>
#include <stdio.h>
#include <string.h>
#include <wchar.h>
 
int main(void)
{
  wchar_t* endptr;
 
  wprintf(L"%ld\n", wcstoimax(L" -123junk", &endptr, 10)); // 十进制
  wprintf(L"%ld\n", wcstoimax(L"11111111", &endptr, 2));   // 二进制
  wprintf(L"%ld\n", wcstoimax(L"XyZ", &endptr, 36));       // 三十六进制
  wprintf(L"%ld\n", wcstoimax(L"010", &endptr, 0));        // 八进制自动检测
  wprintf(L"%ld\n", wcstoimax(L"10", &endptr, 0));         // 十进制自动检测
  wprintf(L"%ld\n", wcstoimax(L"0x10", &endptr, 0));       // 十六进制自动检测
 
  // 值域错误
  // LONG_MAX+1 --> LONG_MAX
  errno = 0;
  wprintf(L"%ld\n", wcstoimax(L"9223372036854775808", &endptr, 10));
  wprintf(L"%s\n", strerror(errno));
}
```

​	输出：

```txt
-123
255
44027
8
10
16
9223372036854775807
Numerical result out of range
```


### wcstoumax

原址：[https://zh.cppreference.com/w/c/string/wide/wcstoimax](https://zh.cppreference.com/w/c/string/wide/wcstoimax)

```c
intmax_t wcstoimax( const wchar_t *restrict nptr,
                    wchar_t **restrict endptr, int base ); // (C99 起)
uintmax_t wcstoumax( const wchar_t *restrict nptr,
                     wchar_t **restrict endptr, int base ); // (C99 起)
```

参见：[wcstoimax](#wcstoimax)
