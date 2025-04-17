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

| [`<assert.h>`]({{< ref "/c/header/assert" >}}) | [条件编译宏，将参数与零比较](https://zh.cppreference.com/w/c/error) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [`<complex.h>`]({{< ref "/c/header/complex" >}}) (C99 起) | [复数算术](https://zh.cppreference.com/w/c/numeric/complex)  |
| [`<ctype.h>`]({{< ref "/c/header/ctype" >}})  | [用来确定包含于字符数据中的类型的函数]({{< ref "/c/string/byte" >}}) |
| [`<errno.h>`]({{< ref "/c/header/errno" >}})  | [报告错误条件的宏](https://zh.cppreference.com/w/c/error)    |
| [`<fenv.h>`]({{< ref "/c/header/fenv" >}}) (C99 起) | [浮点数环境](https://zh.cppreference.com/w/c/numeric/fenv)   |
| [`<float.h>`]({{< ref "/c/header/float" >}})  | [浮点数类型的极限]({{< ref "/c/types/limits#.E6.B5.AE.E7.82.B9.E6.95.B0.E7.B1.BB.E5.9E.8B.E7.9A.84.E6.9E.81.E9.99.90" >}}) |
| [`<inttypes.h> `]({{< ref "/c/header/inttypes" >}}) (C99 起) | [整数类型的格式转换]({{< ref "/c/types/integer" >}}) |
| [`<iso646.h>`]({{< ref "/c/header/iso646" >}}) (C95 起) | [运算符的替代写法](https://zh.cppreference.com/w/c/language/operator_alternative) |
| [`<limits.h>`]({{< ref "/c/header/limits" >}}) | [整数类型的范围]({{< ref "/c/types/limits" >}}) |
| [`<locale.h>`]({{< ref "/c/header/locale" >}}) | [本地化工具](https://zh.cppreference.com/w/c/locale)         |
| [`<math.h>`](https://zh.cppreference.com/w/c/header/math)    | [常用数学函数](https://zh.cppreference.com/w/c/numeric/math) |
| [`<setjmp.h>`](https://zh.cppreference.com/w/c/header/setjmp) | [非局部跳转](https://zh.cppreference.com/w/c/program)        |
| [`<signal.h>`]({{< ref "/c/header/signal" >}}) | [信号处理](https://zh.cppreference.com/w/c/program)          |
| [`<stdalign.h>`]({{< ref "/c/header/stdalign" >}}) (C11 起)(C23 弃用) | [`alignas` 与 `alignof`]({{< ref "/c/types" >}}) 便利宏 |
| [`<stdarg.h>`]({{< ref "/c/header/stdarg" >}}) | [可变参数]({{< ref "/c/variadic" >}})         |
| [`<stdatomic.h>`]({{< ref "/c/header/stdatomic" >}}) (C11 起) | [原子操作](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C) |
| [`<stdbit.h>`]({{< ref "/c/header/stdbit" >}}) (C23 起) | [处理各类型的字节和位表示的宏](https://zh.cppreference.com/w/c/numeric#.E4.BD.8D.E6.93.8D.E7.BA.B5) |
| [`<stdbool.h> `]({{< ref "/c/header/stdbool" >}}) (C99 起)(C23 弃用) | [布尔类型的宏]({{< ref "/c/types" >}})        |
| [`<stdckdint.h>`](https://zh.cppreference.com/mwiki/index.php?title=c/header/stdckdint&action=edit&redlink=1) (C23 起) | [实施带检查整数算术的宏](https://zh.cppreference.com/w/c/numeric#.E5.B8.A6.E6.A3.80.E6.9F.A5.E6.95.B4.E6.95.B0.E7.AE.97.E6.9C.AF) |
| [`<stddef.h>`]({{< ref "/c/header/stddef" >}}) | [常用宏定义]({{< ref "/c/types" >}})          |
| [`<stdint.h>`]({{< ref "/c/header/stdint" >}}) (C99 起) | [定宽整数类型]({{< ref "/c/types/integer" >}}) |
| [`<stdio.h>`]({{< ref "/c/header/stdio" >}})  | [输入/输出](https://zh.cppreference.com/w/c/io)              |
| [`<stdlib.h>`]({{< ref "/c/header/stdlib" >}}) | 通用工具：[内存管理]({{< ref "/c/memory" >}})、[程序工具](https://zh.cppreference.com/w/c/program)、[字符串转换]({{< ref "/c/string" >}})、[随机数](https://zh.cppreference.com/w/c/numeric/random)、[算法]({{< ref "/c/algorithm" >}}) |
| [`<stdmchar.h> `](https://zh.cppreference.com/w/c/header/stdmchar) (since C29) | 文本转码                                                     |
| [`<stdnoreturn.h>`](https://zh.cppreference.com/w/c/header/stdnoreturn) (C11 起)(C23 弃用) | [`noreturn`]({{< ref "/c/language/functions/_Noreturn" >}}) 便利宏 |
| [`<string.h>`]({{< ref "/c/header/string" >}}) | [字符串处理]({{< ref "/c/string/byte" >}})    |
| [`<tgmath.h>`]({{< ref "/c/header/tgmath" >}}) (C99 起) | [泛型数学](https://zh.cppreference.com/w/c/numeric/tgmath)（包装 math.h 和 complex.h 的宏） |
| [`<threads.h>`]({{< ref "/c/header/threads" >}}) (C11 起) | [线程库](https://zh.cppreference.com/w/c/thread)             |
| [`<time.h>`]({{< ref "/c/header/time" >}})    | [时间/日期工具](https://zh.cppreference.com/w/c/chrono)      |
| [`<uchar.h> `]({{< ref "/c/header/uchar" >}}) (C11 起) | [UTF-16 和 UTF-32 字符工具]({{< ref "/c/string/multibyte" >}}) |
| [`<wchar.h> `]({{< ref "/c/header/wchar" >}}) (C95 起) | [扩展多字节和宽字符工具]({{< ref "/c/string/wide" >}}) |
| [`<wctype.h>`]({{< ref "/c/header/wctype" >}}) (C95 起) | [用来确定包含于宽字符数据中的类型的函数]({{< ref "/c/string/wide" >}}) |

### 功能特性测试宏 (C23 起)

​	从 C23 起，相应标头中定义了功能特性测试宏。注意，并非所有标头都含有这种宏。

|  #   |                             标头                             |              宏名              |   值    |
| :--: | :----------------------------------------------------------: | :----------------------------: | :-----: |
|  1   | [`<assert.h>`]({{< ref "/c/header/assert" >}}) |  `__STDC_VERSION_ASSERT_H__`   | 202311L |
|  2   | [`<complex.h>`]({{< ref "/c/header/complex" >}}) |  `__STDC_VERSION_COMPLEX_H__`  | 202311L |
|  3   | [`<ctype.h>`]({{< ref "/c/header/ctype" >}})  |             不适用             |         |
|  4   | [`<errno.h>`]({{< ref "/c/header/errno" >}})  |             不适用             |         |
|  5   |  [`<fenv.h>`]({{< ref "/c/header/fenv" >}})   |   `__STDC_VERSION_FENV_H__`    | 202311L |
|  6   | [`<float.h>`]({{< ref "/c/header/float" >}})  |   `__STDC_VERSION_FLOAT_H__`   | 202311L |
|  7   | [`<inttypes.h>`]({{< ref "/c/header/inttypes" >}}) | `__STDC_VERSION_INTTYPES_H__`  | 202311L |
|  8   | [`<iso646.h>`]({{< ref "/c/header/iso646" >}}) |             不适用             |         |
|  9   | [`<limits.h>`]({{< ref "/c/header/limits" >}}) |  `__STDC_VERSION_LIMITS_H__`   | 202311L |
|  10  | [`<locale.h>`]({{< ref "/c/header/locale" >}}) |             不适用             |         |
|  11  |  [`<math.h>`](https://zh.cppreference.com/w/c/header/math)   |   `__STDC_VERSION_MATH_H__`    | 202311L |
|  12  | [`<setjmp.h>`](https://zh.cppreference.com/w/c/header/setjmp) |  `__STDC_VERSION_SETJMP_H__`   | 202311L |
|  13  | [`<signal.h>`]({{< ref "/c/header/signal" >}}) |             不适用             |         |
|  14  | [`<stdalign.h>`]({{< ref "/c/header/stdalign" >}}) |             不适用             |         |
|  15  | [`<stdarg.h>`]({{< ref "/c/header/stdarg" >}}) |  `__STDC_VERSION_STDARG_H__`   | 202311L |
|  16  | [`<stdatomic.h>`]({{< ref "/c/header/stdatomic" >}}) | `__STDC_VERSION_STDATOMIC_H__` | 202311L |
|  17  | [`<stdbit.h>`]({{< ref "/c/header/stdbit" >}}) |  `__STDC_VERSION_STDBIT_H__`   | 202311L |
|  18  | [`<stdbool.h>`]({{< ref "/c/header/stdbool" >}}) |             不适用             |         |
|  19  | [`<stdckdint.h>`](https://zh.cppreference.com/mwiki/index.php?title=c/header/stdckdint&action=edit&redlink=1) | `__STDC_VERSION_STDCKDINT_H__` | 202311L |
|  20  | [`<stddef.h>`]({{< ref "/c/header/stddef" >}}) |  `__STDC_VERSION_STDDEF_H__`   | 202311L |
|  21  | [`<stdint.h>`]({{< ref "/c/header/stdint" >}}) |  `__STDC_VERSION_STDINT_H__`   | 202311L |
|  22  | [`<stdio.h>`]({{< ref "/c/header/stdio" >}})  |   `__STDC_VERSION_STDIO_H__`   | 202311L |
|  23  | [`<stdlib.h>`]({{< ref "/c/header/stdlib" >}}) |  `__STDC_VERSION_STDLIB_H__`   | 202311L |
|  24  | [`<stdmchar.h>`](https://zh.cppreference.com/w/c/header/stdmchar) | `__STDC_VERSION_STDMCHAR_H__`  | 2029??L |
|  25  | [`<stdnoreturn.h>`](https://zh.cppreference.com/w/c/header/stdnoreturn) |             不适用             |         |
|  26  | [`<string.h>`]({{< ref "/c/header/string" >}}) |  `__STDC_VERSION_STRING_H__`   | 202311L |
|  27  | [`<tgmath.h>`]({{< ref "/c/header/tgmath" >}}) |  `__STDC_VERSION_TGMATH_H__`   | 202311L |
|  28  | [`<threads.h>`]({{< ref "/c/header/threads" >}}) |             不适用             |         |
|  29  |  [`<time.h>`]({{< ref "/c/header/time" >}})   |   `__STDC_VERSION_TIME_H__`    | 202311L |
|  30  | [`<uchar.h>`]({{< ref "/c/header/uchar" >}})  |   `__STDC_VERSION_UCHAR_H__`   | 202311L |
|  31  | [`<wchar.h>`]({{< ref "/c/header/wchar" >}})  |   `__STDC_VERSION_WCHAR_H__`   | 202311L |
|  32  | [`<wctype.h>`]({{< ref "/c/header/wctype" >}}) |             不适用             |         |

## 参阅

**C++ 标准库标头**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/header)**
