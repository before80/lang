+++
title = "标识符"
date = 2025-04-11T20:03:25+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/identifier](https://zh.cppreference.com/w/c/language/identifier)

​	*标识符*是数字、下划线、小写及大写拉丁字母和以 `\u` 及 `\U` [转义](https://zh.cppreference.com/w/c/language/escape)记号指定的，属于 [XID_Continue](https://www.unicode.org/reports/tr31/#Table_Lexical_Classes_for_Identifiers) 类的(C23 起) Unicode 字符(C99 起)的任意长度序列。合法的标识符必须以非数字字符（拉丁字母、下划线或 Unicode 非数字字符(C99 起)(C23 前)或属于 [XID_Start](https://www.unicode.org/reports/tr31/#Table_Lexical_Classes_for_Identifiers) 类的 Unicode 字符(C23 起)）开始。标识符大小写有别（小写和大写字母不同）。每个标识符都应遵守[规范形式 C](https://www.unicode.org/charts/normalization/)。(C23 起)

> ​	是否在标识符中允许未处理（未转义）的 Unicode 字符是实现定义的：(C99 起) (C23 前)
>
> ```c
> char *\U0001f431 = "cat"; // 受支持
> char *🐱 = "cat"; // 由实现定义
>                   // （比如，Clang 可用，但版本 10 前的 GCC 不可）
>                   // C23 中这两种都非良构。Emoji 并非 XID_Start 字符
> ```
>
> ​	由实现定义的字符，其在 [ISO/IEC 10646](https://unicode.org/L2/L2010/10038-fcd10646-main.pdf)（Unicode）中的对应代码点具有 XID_Start 或 XID_Continue 属性，可分别作为标识符开头或第一个字符之后的字符。(C23 起)

​	标识符能指代下列类型的实体：

- [对象]({{< ref "/c/language/basic_concepts/object" >}})
- [函数]({{< ref "/c/language/functions" >}})
- 标签（[struct]({{< ref "/c/language/declarations/struct" >}})、[union]({{< ref "/c/language/declarations/union" >}}) 或[枚举]({{< ref "/c/language/declarations/enum" >}})）
- 结构体或联合体成员
- 枚举常量
- [typedef]({{< ref "/c/language/declarations/typedef" >}}) 名
- [标号]({{< ref "/c/language/statements#.E6.A0.87.E5.8F.B7" >}})名
- [宏]({{< ref "/c/language/preprocessor/replace" >}})名
- [宏形参]({{< ref "/c/language/preprocessor/replace" >}})名

​	宏名或宏形参名以外的每个标识符都拥有[作用域]({{< ref "/c/language/basic_concepts/scope" >}})，属于一个[命名空间]({{< ref "/c/language/basic_concepts/name_space" >}})，并且可以拥有[链接]({{< ref "/c/language/declarations/storage_duration" >}})。相同的标识符可以在程序的相异点指代相异实体，或若实体在不同的命名空间中，则可在相同点指代相异实体。

## 保留标识符

​	下列标识符被*保留*，而且不可在程序中声明（这么做会引起未定义行为）：

1. 作为[关键词]({{< ref "/c/language/keyword" >}})的标识符不能用于其他目的。具体而言，不允许 `#define` 或 `#undef` 等同于关键词的标识符。
2. 所有以一个下划线开始的外部标识符。
3. 所有以一个下划线后随一个大写字母或另一下划线开始的标识符（这些保留标识符允许库使用大量幕后的非外部宏及函数）。
4. 标准库所定义的所有外部标识符（在有宿主环境中）。这表示不允许用户提供的外部名称匹配任何库名称，即使是声明等同于库函数的函数也不允许。
5. 声明为由实现使用或由标准库未来使用所保留的标识符（见后述）。
6. 声明为被潜在保留并且为实现所提供的标识符（见后述）。 (C23 起)

​	所有其他标识符均可用。能使用未被保留或潜在保留(C23 起)的标识符，而无需担心从一个编译器和库移动程序到另一个时发生意料之外的冲突。

> **注意**
>
> ​	C++ 中，在任何位置有双下划线的标识符都被保留；C 中，只有以双下划线开始的标识符被保留。

### 库中的保留与潜在保留标识符

​	标准库保留其所提供的每个标识符。拥有[外部链接]({{< ref "/c/language/declarations/storage_duration" >}})的保留标识符（例如每个标准函数的名字）受到保留，无关乎包含哪个头文件。其他保留标识符在包含任何其所关联的头文件时被保留。

> ​	潜在保留的标识符有意为实现和未来标准版本保留。若潜在保留的标识符为实现所提供，则它变为保留标识符。
>
> ​	仅允许实现提供作为函数名保留的潜在保留标识符的[外部定义]({{< ref "/c/language/declarations/extern" >}})。(C23 起)
>
> ​	实现不提供的潜在保留标识符不被保留。能声明或定义它们而无未定义行为。然而，这种用法是不可移植的。

​	下列标识符为实现或标准库的未来使用保留或潜在保留(C23 起)。

- 函数名，全部为潜在保留(C23 起)

  - [`<complex.h>`](https://zh.cppreference.com/w/c/numeric/complex) 中，`cerf`、`cerfc`、`cexp2`、`cexpm1`、`clog10`、`clog1p`、`clog2`、`clgamma`、`ctgamma`、`csinpi`、`ccospi`、`ctanpi`、`casinpi`、`cacospi`、`catanpi`、`ccompoundn`、`cpown`、`cpowr`、`crootn`、`crsqrt`、`cexp10m1`、`cexp10`、`cexp2m1`、`clog10p1`、`clog2p1`、`clogp1`(C23 起) 及其 -f 和 -l 后缀变体 (C99 起)
  - [`<ctype.h>`]({{< ref "/c/string/byte" >}}) 和 [`<wctype.h>`]({{< ref "/c/string/wide" >}})(C95 起) 中，以 `is` 或 `to` 后随一个小写字母开始的名字
  - [`<stdlib.h>`]({{< ref "/c/string/byte" >}}) 和 [`<inttypes.h>`]({{< ref "/c/types/integer" >}})(C23 起) 中，以 `str` 或 `wcs`(C23 起) 后随一个小写字母开始的名字
  - [`<math.h>`](https://zh.cppreference.com/w/c/numeric/math) 中，以 `cr_` 开始的名字 (C23 起)
  - [`<wchar.h>`]({{< ref "/c/string/wide" >}}) 中，以 `wcs` 后随一个小写字母开始的名字 (C95 起)
  - [`<stdatomic.h>`](https://zh.cppreference.com/w/c/thread) 中，以 `atomic_` 后随一个小写字母开始的名字 (C11 起)
  - [`<threads.h>`](https://zh.cppreference.com/w/c/thread) 中，以 `cnd_`、`mtx_`、`thrd_` 或 `tss_` 后随一个小写字母开始的名字 (C11 起)

  

- typedef 名，全部为潜在保留(C23 起)

  - [`<stdint.h>`]({{< ref "/c/types/integer" >}}) 中，以 `int` 或 `uint` 开始并以 `_t` 结束的名字 (C99 起)
  - [`<stdatomic.h>`](https://zh.cppreference.com/w/c/thread) 中，以 `atomic_` 或 `memory_` 后随一个小写字母开始的名字 (C11 起)
  - [`<threads.h>`](https://zh.cppreference.com/w/c/thread) 中，以 `cnd_`、`mtx_`、`thrd_` 或 `tss_` 后随一个小写字母开始的名字 (C11 起)

- 宏名

  - [`<errno.h>`](https://zh.cppreference.com/w/c/error/errno_macros) 中，以 `E` 后随一个数字或大写字母开始的名字
  - [`<fenv.h>`](https://zh.cppreference.com/w/c/numeric/fenv) 中，以 `FE_` 后随一个大写字母开始的名字 (C99 起)
  - [`<float.h>`]({{< ref "/c/types/limits" >}}) 中，以 `DBL_`、`DEC32_`、`DEC64_`、`DEC128_`、`DEC_`、`FLT_` 或 `LDBL_` 后随一个大写字母开始的名字；这些标识符为潜在保留 (C23 起)
  - [`<stdint.h>`]({{< ref "/c/types/integer" >}}) 中，以 `INT` 或 `UINT` 开始并以 `_MAX`、`_MIN`、`_WIDTH`(C23 起) 或 `_C` 结束的名字；这些标识符为潜在保留(C23 起) (C99 起)
  - [`<inttypes.h>`]({{< ref "/c/types/integer" >}}) 中，以 `PRI` 或 `SCN` 后随一个小写字母或字母 `X` 开始的名字；这些标识符为潜在保留(C23 起) (C99 起)
  - [`<locale.h>`](https://zh.cppreference.com/w/c/locale/LC_categories) 中，以 `LC_` 后随一个大写字母开始的名字
  - [`<math.h>`](https://zh.cppreference.com/w/c/numeric/math) 中，以 `FP_` 后随一个大写字母开始的名字 (C23 起)
  - [`<math.h>`](https://zh.cppreference.com/w/c/numeric/math) 中，以 `MATH_` 后随一个大写字母开始的名字；这些标识符为潜在保留 (C23 起)
  - [`<signal.h>`](https://zh.cppreference.com/w/c/program) 中，以 `SIG` 或 `SIG_` 后随一个大写字母开始的名字
  - [`<time.h>`](https://zh.cppreference.com/w/c/chrono/timespec_get) 中，以 `TIME_` 后随一个大写字母开始的名字 (C11 起)
  - [`<stdatomic.h>`](https://zh.cppreference.com/w/c/thread) 中，以 `ATOMIC_` 后随一个大写字母开始的名字；这些标识符为潜在保留(C23 起) (C11 起)

- 枚举常量，全部为潜在保留(C23 起)

  - [`<stdatomic.h>`](https://zh.cppreference.com/w/c/thread) 中，以 `memory_order_` 后随一个小写字母开始的名字 (C11 起)
  - [`<threads.h>`](https://zh.cppreference.com/w/c/thread) 中，以 `cnd_`、`mtx_`、`thrd_` 或 `tss_` 后随一个小写字母开始的名字 (C11 起)

> ​	推荐实现在声明或定义潜在保留标识符时警告，除了当
>
> - 声明为实现所提供的拥有外部链接的标识符的非定义声明，且 (C23 起)
> - 声明中使用的类型与定义中的[兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)。

## 翻译限制

​	尽管标识符长度上无特定的限制，一些早期编译器还是在标识符中的有效起始字符数上有限制，而链接器在带[外部链接]({{< ref "/c/language/declarations/storage_duration" >}})的名称上加上了更严格的限制。C 要求任何服从标准的实现支持下列极限：

- 内部标识符或宏名中 31 个有效起始字符(C99 前)

- 外部标识符中 6 个有效起始字符(C99 前)

- 一个翻译单元中 511 个外部标识符(C99 前)

- 一个块中声明 127 个拥有块作用域的标识符(C99 前)

- 一个预处理翻译单元中同时定义 1024 个宏标识符(C99 前)
- 内部标识符或宏名中 63 个有效起始字符(C99 起)
- 外部标识符中 31 个有效起始字符(C99 起)
- 一个翻译单元中 4095 个外部标识符(C99 起)
- 一个块中声明 511 个拥有块作用域的标识符(C99 起)
- 一个预处理翻译单元中同时定义 4095 个宏标识符(C99 起)

## 参阅

**标识符**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/identifiers)**
