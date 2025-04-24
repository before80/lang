
+++
title = "<inttypes.h> (C99)"
date = 2025-04-24T18:05:55+08:00
weight = 60
type = "docs"
description = "整数类型的格式转换"
isCJKLanguage = true
draft = false

+++

## 类型




## 枚举




## 宏




## 函数



### imaxabs

原址：

作用：

备注：





### imaxdiv

原址：

作用：

备注：





### strtoimax

原址：[http://zh.cppreference.com/w/c/string/byte/strtoimax](http://zh.cppreference.com/w/c/string/byte/strtoimax)

作用：

备注：
```c
// 在标头 <inttypes.h> 定义
intmax_t strtoimax( const char* restrict nptr,
                    char** restrict endptr, int base );// (1)(C99 起)
uintmax_t strtoumax( const char* restrict nptr,
                     char** restrict endptr, int base );// (2)(C99 起)
```

​	转译 `nptr` 所指向的字节字符串中的一个整数。

​	舍弃所有空白符（以调用 [`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) 鉴别），直到找到首个非空白符，然后取尽可能多的字符组成合法的*底 n* （其中 n=`base`）的整数表示，并将它们转换成一个整数。合法的整数由下列部分组成：

- (可选)正或负号
- (可选)指示八进制底的前缀（`0`）（仅当底为 `8` 或 `0` 时应用）
- (可选)指示十六进制底的前缀（`0x` 或 `0X`）（仅当底为 `16` 或 `0` 时应用）
- 数字序列

​	底的合法集是 `{0, 2, 3, ..., 36}`。合法数字集对于底 2 整数是 `{0, 1}`，对于底 3 整数是 `{0, 1, 2}`，以此类推。对于大于 `10` 的底，合法数字包含字母字符，从对于底 `11` 整数的 `Aa` 到对于底 `36` 整数的 `Zz`。忽略字符大小写。

​	当前安装的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)可能接受另外的数字格式。

​	如果 `base` 是 `0`，那么自动检测数值进制：如果前缀是 `0`，那么底是八进制，如果前缀是 `0x` 或 `0X`，那么底是十六进制，否则底是十进制。

​	如果符号是输入序列的一部分，那么对从数字序列计算得来的数字值取反，如同用结果类型的[一元减](https://zh.cppreference.com/w/c/language/operator_arithmetic#.E4.B8.80.E5.85.83.E7.AE.97.E6.9C.AF)。

​	此函数设置 `endptr` 所指向的指针指向最后一个转译字符的后一字符。若 `endptr` 为空指针，则忽略它。

​	若 `nptr` 为空字符串或无期待的形式，则不进行转换，并（若 `enptr` 非空指针）将 `nptr` 存储于 `endptr` 所指向的对象。

**参数**

| nptr   | -    | 指向要被转译的空终止字符串的指针 |
| ------ | ---- | -------------------------------- |
| endptr | -    | 指向指向字符的指针的指针         |
| base   | -    | 被转译整数的*底*                 |

**返回值**

- 若成功，则返回对应 `str` 内容的整数。
- 若整数落在对应的返回类型范围外，则发生值域错误（设置 [errno](https://zh.cppreference.com/w/c/error/errno) 为 [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros)），并返回 [INTMAX_MAX](https://zh.cppreference.com/w/c/types/integer)、[INTMAX_MIN](https://zh.cppreference.com/w/c/types/integer)、[UINTMAX_MAX](https://zh.cppreference.com/w/c/types/integer) 或 `0` 中的最接近者。
- 若无法进行转换，则返回 `0`。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.8.2.3 The strtoimax and strtoumax functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.8.2.3 The strtoimax and strtoumax functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.8.2.3 The strtoimax and strtoumax functions （第 219 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.8.2.3 The strtoimax and strtoumax functions （第 200 页）

**参阅**

| [wcstoimax (C99)<br />wcstoumax (C99)<br />](https://zh.cppreference.com/w/c/string/wide/wcstoimax) | 转换宽字符串为 [intmax_t](https://zh.cppreference.com/w/c/types/integer) 或 [uintmax_t](https://zh.cppreference.com/w/c/types/integer) (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [strtol <br />strtoll (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtol) | 将字节字符串转换成整数 (函数)                                |
| [strtoul <br />strtoull (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtoul) | 将字节字符串转换成无符号整数 (函数)                          |
| **strtoimax, strtoumax** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strtoimax)** |                                                              |





### strtoumax

原址：[http://zh.cppreference.com/w/c/string/byte/strtoimax](http://zh.cppreference.com/w/c/string/byte/strtoimax)

作用：

备注：
```c
// 在标头 <inttypes.h> 定义
intmax_t strtoimax( const char* restrict nptr,
                    char** restrict endptr, int base );// (1)(C99 起)
uintmax_t strtoumax( const char* restrict nptr,
                     char** restrict endptr, int base );// (2)(C99 起)
```

​	转译 `nptr` 所指向的字节字符串中的一个整数。

​	舍弃所有空白符（以调用 [`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) 鉴别），直到找到首个非空白符，然后取尽可能多的字符组成合法的*底 n* （其中 n=`base`）的整数表示，并将它们转换成一个整数。合法的整数由下列部分组成：

- (可选)正或负号
- (可选)指示八进制底的前缀（`0`）（仅当底为 `8` 或 `0` 时应用）
- (可选)指示十六进制底的前缀（`0x` 或 `0X`）（仅当底为 `16` 或 `0` 时应用）
- 数字序列

​	底的合法集是 `{0, 2, 3, ..., 36}`。合法数字集对于底 2 整数是 `{0, 1}`，对于底 3 整数是 `{0, 1, 2}`，以此类推。对于大于 `10` 的底，合法数字包含字母字符，从对于底 `11` 整数的 `Aa` 到对于底 `36` 整数的 `Zz`。忽略字符大小写。

​	当前安装的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)可能接受另外的数字格式。

​	如果 `base` 是 `0`，那么自动检测数值进制：如果前缀是 `0`，那么底是八进制，如果前缀是 `0x` 或 `0X`，那么底是十六进制，否则底是十进制。

​	如果符号是输入序列的一部分，那么对从数字序列计算得来的数字值取反，如同用结果类型的[一元减](https://zh.cppreference.com/w/c/language/operator_arithmetic#.E4.B8.80.E5.85.83.E7.AE.97.E6.9C.AF)。

​	此函数设置 `endptr` 所指向的指针指向最后一个转译字符的后一字符。若 `endptr` 为空指针，则忽略它。

​	若 `nptr` 为空字符串或无期待的形式，则不进行转换，并（若 `enptr` 非空指针）将 `nptr` 存储于 `endptr` 所指向的对象。

**参数**

| nptr   | -    | 指向要被转译的空终止字符串的指针 |
| ------ | ---- | -------------------------------- |
| endptr | -    | 指向指向字符的指针的指针         |
| base   | -    | 被转译整数的*底*                 |

**返回值**

- 若成功，则返回对应 `str` 内容的整数。
- 若整数落在对应的返回类型范围外，则发生值域错误（设置 [errno](https://zh.cppreference.com/w/c/error/errno) 为 [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros)），并返回 [INTMAX_MAX](https://zh.cppreference.com/w/c/types/integer)、[INTMAX_MIN](https://zh.cppreference.com/w/c/types/integer)、[UINTMAX_MAX](https://zh.cppreference.com/w/c/types/integer) 或 `0` 中的最接近者。
- 若无法进行转换，则返回 `0`。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.8.2.3 The strtoimax and strtoumax functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.8.2.3 The strtoimax and strtoumax functions （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.8.2.3 The strtoimax and strtoumax functions （第 219 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.8.2.3 The strtoimax and strtoumax functions （第 200 页）

**参阅**

| [wcstoimax (C99)<br />wcstoumax (C99)<br />](https://zh.cppreference.com/w/c/string/wide/wcstoimax) | 转换宽字符串为 [intmax_t](https://zh.cppreference.com/w/c/types/integer) 或 [uintmax_t](https://zh.cppreference.com/w/c/types/integer) (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [strtol <br />strtoll (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtol) | 将字节字符串转换成整数 (函数)                                |
| [strtoul <br />strtoull (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtoul) | 将字节字符串转换成无符号整数 (函数)                          |
| **strtoimax, strtoumax** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strtoimax)** |                                                              |





### wcstoimax

原址：[http://zh.cppreference.com/w/c/string/wide/wcstoimax](http://zh.cppreference.com/w/c/string/wide/wcstoimax)

作用：

备注：
```c
// 在标头 <inttypes.h> 定义
intmax_t wcstoimax( const wchar_t *restrict nptr, 
                    wchar_t **restrict endptr, int base );// (C99 起)
uintmax_t wcstoumax( const wchar_t *restrict nptr,
                     wchar_t **restrict endptr, int base );// (C99 起)
```

​	转译 `nptr` 所指向的宽字符串中的整数值。

​	舍弃所有空白符（以调用 [`<swspac>`](https://zh.cppreference.com/w/c/string/wide/iswspace) 鉴别），直到找到首个非空白符，然后取尽可能多的字符组成合法的*底 n* （其中 n=`base`）的无符号整数表示，并将它们转换成一个整数。合法的无符号整数由下列部分组成：

- (可选)正或负号
- (可选)指示八进制底的前缀（`0`）（仅当底为 `8` 或 `0` 时应用）
- (可选)指示十六进制底的前缀（`0x` 或 `0X`）（仅当底为 `16` 或 `0` 时应用）
- 数字序列

​	底的合法集是 `{0, 2, 3, ..., 36}`。合法数字集对于底 2 整数是 `{0, 1}`，对于底 3 整数是 `{0, 1, 2}`，以此类推。对于大于 `10` 的底，合法数字包含字母字符，从对于底 `11` 整数的 `Aa` 到对于底 `36` 整数的 `Zz`。忽略字符大小写。

​	当前安装的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)可能接受另外的数字格式。

​	如果 `base` 是 `0`，那么自动检测数值进制：如果前缀是 `0`，那么底是八进制，如果前缀是 `0x` 或 `0X`，那么底是十六进制，否则底是十进制。

​	如果符号是输入序列的一部分，那么对从数字序列计算得来的数字值取反，如同用结果类型的[一元减](https://zh.cppreference.com/w/c/language/operator_arithmetic#.E4.B8.80.E5.85.83.E7.AE.97.E6.9C.AF)，它对无符号整数应用回绕规则。

​	函数将 `endptr` 所指向的指针设为指向最后转译的宽字符的后一宽字符。若 `endptr` 为空指针，则忽略它。

**参数**

| nptr   | -    | 指向待转译的空终止宽字符串的指针 |
| ------ | ---- | -------------------------------- |
| endptr | -    | 指向宽字符指针的指针             |
| base   | -    | 转译整数值的*底*                 |

**返回值**

​	成功时返回对应于 `str` 内容的整数值。若转得的值落在对应类型之外，则出现值域错误，并返回 [INTMAX_MAX](https://zh.cppreference.com/w/c/types/integer)、[INTMAX_MIN](https://zh.cppreference.com/w/c/types/integer)、[UINTMAX_MAX](https://zh.cppreference.com/w/c/types/integer) 或 `0` 中的最接近者。若无法进行转换，则返回 `0`。

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

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.8.2.4 The wcstoimax and wcstoumax functions （第 220 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.8.2.4 The wcstoimax and wcstoumax functions （第 201 页）

**参阅**

| [strtoimax (C99)<br />strtoumax (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtoimax) | 将字节字符串转换成 [intmax_t](https://zh.cppreference.com/w/c/types/integer) 或 [uintmax_t](https://zh.cppreference.com/w/c/types/integer) (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [wcstol (C95)<br />wcstoll (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstol) | 转换宽字符串为整数 (函数)                                    |
| [wcstoul (C95)<br />wcstoull (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstoul) | 转换宽字符串为无符号整数 (函数)                              |
| **wcstoimax, wcstoumax** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/wide/wcstoimax)** |                                                              |





### wcstoumax

原址：[http://zh.cppreference.com/w/c/string/wide/wcstoimax](http://zh.cppreference.com/w/c/string/wide/wcstoimax)

作用：

备注：
```c
// 在标头 <inttypes.h> 定义
intmax_t wcstoimax( const wchar_t *restrict nptr, 
                    wchar_t **restrict endptr, int base );// (C99 起)
uintmax_t wcstoumax( const wchar_t *restrict nptr,
                     wchar_t **restrict endptr, int base );// (C99 起)
```

​	转译 `nptr` 所指向的宽字符串中的整数值。

​	舍弃所有空白符（以调用 [`<swspac>`](https://zh.cppreference.com/w/c/string/wide/iswspace) 鉴别），直到找到首个非空白符，然后取尽可能多的字符组成合法的*底 n* （其中 n=`base`）的无符号整数表示，并将它们转换成一个整数。合法的无符号整数由下列部分组成：

- (可选)正或负号
- (可选)指示八进制底的前缀（`0`）（仅当底为 `8` 或 `0` 时应用）
- (可选)指示十六进制底的前缀（`0x` 或 `0X`）（仅当底为 `16` 或 `0` 时应用）
- 数字序列

​	底的合法集是 `{0, 2, 3, ..., 36}`。合法数字集对于底 2 整数是 `{0, 1}`，对于底 3 整数是 `{0, 1, 2}`，以此类推。对于大于 `10` 的底，合法数字包含字母字符，从对于底 `11` 整数的 `Aa` 到对于底 `36` 整数的 `Zz`。忽略字符大小写。

​	当前安装的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)可能接受另外的数字格式。

​	如果 `base` 是 `0`，那么自动检测数值进制：如果前缀是 `0`，那么底是八进制，如果前缀是 `0x` 或 `0X`，那么底是十六进制，否则底是十进制。

​	如果符号是输入序列的一部分，那么对从数字序列计算得来的数字值取反，如同用结果类型的[一元减](https://zh.cppreference.com/w/c/language/operator_arithmetic#.E4.B8.80.E5.85.83.E7.AE.97.E6.9C.AF)，它对无符号整数应用回绕规则。

​	函数将 `endptr` 所指向的指针设为指向最后转译的宽字符的后一宽字符。若 `endptr` 为空指针，则忽略它。

**参数**

| nptr   | -    | 指向待转译的空终止宽字符串的指针 |
| ------ | ---- | -------------------------------- |
| endptr | -    | 指向宽字符指针的指针             |
| base   | -    | 转译整数值的*底*                 |

**返回值**

​	成功时返回对应于 `str` 内容的整数值。若转得的值落在对应类型之外，则出现值域错误，并返回 [INTMAX_MAX](https://zh.cppreference.com/w/c/types/integer)、[INTMAX_MIN](https://zh.cppreference.com/w/c/types/integer)、[UINTMAX_MAX](https://zh.cppreference.com/w/c/types/integer) 或 `0` 中的最接近者。若无法进行转换，则返回 `0`。

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

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.8.2.4 The wcstoimax and wcstoumax functions （第 220 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.8.2.4 The wcstoimax and wcstoumax functions （第 201 页）

**参阅**

| [strtoimax (C99)<br />strtoumax (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtoimax) | 将字节字符串转换成 [intmax_t](https://zh.cppreference.com/w/c/types/integer) 或 [uintmax_t](https://zh.cppreference.com/w/c/types/integer) (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [wcstol (C95)<br />wcstoll (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstol) | 转换宽字符串为整数 (函数)                                    |
| [wcstoul (C95)<br />wcstoull (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstoul) | 转换宽字符串为无符号整数 (函数)                              |
| **wcstoimax, wcstoumax** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/wide/wcstoimax)** |                                                              |






