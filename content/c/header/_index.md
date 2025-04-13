+++
title = "C 标准库标头"
date = 2025-04-13T14:46:25+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header](https://zh.cppreference.com/w/c/header)

​	C 标准库的接口由下列标头的汇集定义。

| [`<assert.h>`](https://zh.cppreference.com/w/c/header/assert) | [条件编译宏，将参数与零比较](https://zh.cppreference.com/w/c/error) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [`<complex.h>`](https://zh.cppreference.com/w/c/header/complex) (C99 起) | [复数算术](https://zh.cppreference.com/w/c/numeric/complex)  |
| [`<ctype.h>`](https://zh.cppreference.com/w/c/header/ctype)  | [用来确定包含于字符数据中的类型的函数](https://zh.cppreference.com/w/c/string/byte) |
| [`<errno.h>`](https://zh.cppreference.com/w/c/header/errno)  | [报告错误条件的宏](https://zh.cppreference.com/w/c/error)    |
| [`<fenv.h>`](https://zh.cppreference.com/w/c/header/fenv) (C99 起) | [浮点数环境](https://zh.cppreference.com/w/c/numeric/fenv)   |
| [`<float.h>`](https://zh.cppreference.com/w/c/header/float)  | [浮点数类型的极限](https://zh.cppreference.com/w/c/types/limits#.E6.B5.AE.E7.82.B9.E6.95.B0.E7.B1.BB.E5.9E.8B.E7.9A.84.E6.9E.81.E9.99.90) |
| [`<inttypes.h> `](https://zh.cppreference.com/w/c/header/inttypes) (C99 起) | [整数类型的格式转换](https://zh.cppreference.com/w/c/types/integer) |
| [`<iso646.h>`](https://zh.cppreference.com/w/c/header/iso646) (C95 起) | [运算符的替代写法](https://zh.cppreference.com/w/c/language/operator_alternative) |
| [`<limits.h>`](https://zh.cppreference.com/w/c/header/limits) | [整数类型的范围](https://zh.cppreference.com/w/c/types/limits) |
| [`<locale.h>`](https://zh.cppreference.com/w/c/header/locale) | [本地化工具](https://zh.cppreference.com/w/c/locale)         |
| [`<math.h>`](https://zh.cppreference.com/w/c/header/math)    | [常用数学函数](https://zh.cppreference.com/w/c/numeric/math) |
| [`<setjmp.h>`](https://zh.cppreference.com/w/c/header/setjmp) | [非局部跳转](https://zh.cppreference.com/w/c/program)        |
| [`<signal.h>`](https://zh.cppreference.com/w/c/header/signal) | [信号处理](https://zh.cppreference.com/w/c/program)          |
| [`<stdalign.h>`](https://zh.cppreference.com/w/c/header/stdalign) (C11 起)(C23 弃用) | [`alignas` 与 `alignof`](https://zh.cppreference.com/w/c/types) 便利宏 |
| [`<stdarg.h>`](https://zh.cppreference.com/w/c/header/stdarg) | [可变参数](https://zh.cppreference.com/w/c/variadic)         |
| [`<stdatomic.h>`](https://zh.cppreference.com/w/c/header/stdatomic) (C11 起) | [原子操作](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C) |
| [`<stdbit.h>`](https://zh.cppreference.com/w/c/header/stdbit) (C23 起) | [处理各类型的字节和位表示的宏](https://zh.cppreference.com/w/c/numeric#.E4.BD.8D.E6.93.8D.E7.BA.B5) |
| [`<stdbool.h> `](https://zh.cppreference.com/w/c/header/stdbool) (C99 起)(C23 弃用) | [布尔类型的宏](https://zh.cppreference.com/w/c/types)        |
| [`<stdckdint.h>`](https://zh.cppreference.com/mwiki/index.php?title=c/header/stdckdint&action=edit&redlink=1) (C23 起) | [实施带检查整数算术的宏](https://zh.cppreference.com/w/c/numeric#.E5.B8.A6.E6.A3.80.E6.9F.A5.E6.95.B4.E6.95.B0.E7.AE.97.E6.9C.AF) |
| [`<stddef.h>`](https://zh.cppreference.com/w/c/header/stddef) | [常用宏定义](https://zh.cppreference.com/w/c/types)          |
| [`<stdint.h>`](https://zh.cppreference.com/w/c/header/stdint) (C99 起) | [定宽整数类型](https://zh.cppreference.com/w/c/types/integer) |
| [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio)  | [输入/输出](https://zh.cppreference.com/w/c/io)              |
| [`<stdlib.h>`](https://zh.cppreference.com/w/c/header/stdlib) | 通用工具：[内存管理](https://zh.cppreference.com/w/c/memory)、[程序工具](https://zh.cppreference.com/w/c/program)、[字符串转换](https://zh.cppreference.com/w/c/string)、[随机数](https://zh.cppreference.com/w/c/numeric/random)、[算法](https://zh.cppreference.com/w/c/algorithm) |
| [`<stdmchar.h> `](https://zh.cppreference.com/w/c/header/stdmchar) (since C29) | 文本转码                                                     |
| [`<stdnoreturn.h>`](https://zh.cppreference.com/w/c/header/stdnoreturn) (C11 起)(C23 弃用) | [`noreturn`](https://zh.cppreference.com/w/c/language/_Noreturn) 便利宏 |
| [`<string.h>`](https://zh.cppreference.com/w/c/header/string) | [字符串处理](https://zh.cppreference.com/w/c/string/byte)    |
| [`<tgmath.h>`](https://zh.cppreference.com/w/c/header/tgmath) (C99 起) | [泛型数学](https://zh.cppreference.com/w/c/numeric/tgmath)（包装 math.h 和 complex.h 的宏） |
| [`<threads.h>`](https://zh.cppreference.com/w/c/header/threads) (C11 起) | [线程库](https://zh.cppreference.com/w/c/thread)             |
| [`<time.h>`](https://zh.cppreference.com/w/c/header/time)    | [时间/日期工具](https://zh.cppreference.com/w/c/chrono)      |
| [`<uchar.h> `](https://zh.cppreference.com/w/c/header/uchar) (C11 起) | [UTF-16 和 UTF-32 字符工具](https://zh.cppreference.com/w/c/string/multibyte) |
| [`<wchar.h> `](https://zh.cppreference.com/w/c/header/wchar) (C95 起) | [扩展多字节和宽字符工具](https://zh.cppreference.com/w/c/string/wide) |
| [`<wctype.h>`](https://zh.cppreference.com/w/c/header/wctype) (C95 起) | [用来确定包含于宽字符数据中的类型的函数](https://zh.cppreference.com/w/c/string/wide) |

### 功能特性测试宏 (C23 起)

​	从 C23 起，相应标头中定义了功能特性测试宏。注意，并非所有标头都含有这种宏。

|  #   |                             标头                             |              宏名              |   值    |
| :--: | :----------------------------------------------------------: | :----------------------------: | :-----: |
|  1   | [`<assert.h>`](https://zh.cppreference.com/w/c/header/assert) |  `__STDC_VERSION_ASSERT_H__`   | 202311L |
|  2   | [`<complex.h>`](https://zh.cppreference.com/w/c/header/complex) |  `__STDC_VERSION_COMPLEX_H__`  | 202311L |
|  3   | [`<ctype.h>`](https://zh.cppreference.com/w/c/header/ctype)  |             不适用             |         |
|  4   | [`<errno.h>`](https://zh.cppreference.com/w/c/header/errno)  |             不适用             |         |
|  5   |  [`<fenv.h>`](https://zh.cppreference.com/w/c/header/fenv)   |   `__STDC_VERSION_FENV_H__`    | 202311L |
|  6   | [`<float.h>`](https://zh.cppreference.com/w/c/header/float)  |   `__STDC_VERSION_FLOAT_H__`   | 202311L |
|  7   | [`<inttypes.h>`](https://zh.cppreference.com/w/c/header/inttypes) | `__STDC_VERSION_INTTYPES_H__`  | 202311L |
|  8   | [`<iso646.h>`](https://zh.cppreference.com/w/c/header/iso646) |             不适用             |         |
|  9   | [`<limits.h>`](https://zh.cppreference.com/w/c/header/limits) |  `__STDC_VERSION_LIMITS_H__`   | 202311L |
|  10  | [`<locale.h>`](https://zh.cppreference.com/w/c/header/locale) |             不适用             |         |
|  11  |  [`<math.h>`](https://zh.cppreference.com/w/c/header/math)   |   `__STDC_VERSION_MATH_H__`    | 202311L |
|  12  | [`<setjmp.h>`](https://zh.cppreference.com/w/c/header/setjmp) |  `__STDC_VERSION_SETJMP_H__`   | 202311L |
|  13  | [`<signal.h>`](https://zh.cppreference.com/w/c/header/signal) |             不适用             |         |
|  14  | [`<stdalign.h>`](https://zh.cppreference.com/w/c/header/stdalign) |             不适用             |         |
|  15  | [`<stdarg.h>`](https://zh.cppreference.com/w/c/header/stdarg) |  `__STDC_VERSION_STDARG_H__`   | 202311L |
|  16  | [`<stdatomic.h>`](https://zh.cppreference.com/w/c/header/stdatomic) | `__STDC_VERSION_STDATOMIC_H__` | 202311L |
|  17  | [`<stdbit.h>`](https://zh.cppreference.com/w/c/header/stdbit) |  `__STDC_VERSION_STDBIT_H__`   | 202311L |
|  18  | [`<stdbool.h>`](https://zh.cppreference.com/w/c/header/stdbool) |             不适用             |         |
|  19  | [`<stdckdint.h>`](https://zh.cppreference.com/mwiki/index.php?title=c/header/stdckdint&action=edit&redlink=1) | `__STDC_VERSION_STDCKDINT_H__` | 202311L |
|  20  | [`<stddef.h>`](https://zh.cppreference.com/w/c/header/stddef) |  `__STDC_VERSION_STDDEF_H__`   | 202311L |
|  21  | [`<stdint.h>`](https://zh.cppreference.com/w/c/header/stdint) |  `__STDC_VERSION_STDINT_H__`   | 202311L |
|  22  | [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio)  |   `__STDC_VERSION_STDIO_H__`   | 202311L |
|  23  | [`<stdlib.h>`](https://zh.cppreference.com/w/c/header/stdlib) |  `__STDC_VERSION_STDLIB_H__`   | 202311L |
|  24  | [`<stdmchar.h>`](https://zh.cppreference.com/w/c/header/stdmchar) | `__STDC_VERSION_STDMCHAR_H__`  | 2029??L |
|  25  | [`<stdnoreturn.h>`](https://zh.cppreference.com/w/c/header/stdnoreturn) |             不适用             |         |
|  26  | [`<string.h>`](https://zh.cppreference.com/w/c/header/string) |  `__STDC_VERSION_STRING_H__`   | 202311L |
|  27  | [`<tgmath.h>`](https://zh.cppreference.com/w/c/header/tgmath) |  `__STDC_VERSION_TGMATH_H__`   | 202311L |
|  28  | [`<threads.h>`](https://zh.cppreference.com/w/c/header/threads) |             不适用             |         |
|  29  |  [`<time.h>`](https://zh.cppreference.com/w/c/header/time)   |   `__STDC_VERSION_TIME_H__`    | 202311L |
|  30  | [`<uchar.h>`](https://zh.cppreference.com/w/c/header/uchar)  |   `__STDC_VERSION_UCHAR_H__`   | 202311L |
|  31  | [`<wchar.h>`](https://zh.cppreference.com/w/c/header/wchar)  |   `__STDC_VERSION_WCHAR_H__`   | 202311L |
|  32  | [`<wctype.h>`](https://zh.cppreference.com/w/c/header/wctype) |             不适用             |         |

## 参阅

**C++ 标准库标头**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/header)**