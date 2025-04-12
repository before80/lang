+++
title = "C 关键词"
date = 2025-04-12T09:00:38+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/keyword](https://zh.cppreference.com/w/c/keyword)

​	这是 C 中保留的关键词列表。因为语言使用这些关键词，故不可重定义它们。其例外是，它们在 [*attribute-token*](https://zh.cppreference.com/w/c/language/attributes) 中并不被保留使用。(C23 起)

| [`alignas`](https://zh.cppreference.com/w/c/keyword/alignas) (C23) | [`extern`](https://zh.cppreference.com/w/c/keyword/extern)   | [`sizeof`](https://zh.cppreference.com/w/c/keyword/sizeof)   | [`_Alignas`](https://zh.cppreference.com/w/c/keyword/_Alignas) (C11)(C23 弃用) |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [`alignof`](https://zh.cppreference.com/w/c/keyword/alignof) (C23) | [`false`](https://zh.cppreference.com/w/c/keyword/false) (C23) | [`static`](https://zh.cppreference.com/w/c/keyword/static)   | [`_Alignof`](https://zh.cppreference.com/w/c/keyword/_Alignof) (C11)(C23 弃用) |
| [`auto`](https://zh.cppreference.com/w/c/keyword/auto)       | [`float`](https://zh.cppreference.com/w/c/keyword/float)     | [`static_assert`](https://zh.cppreference.com/w/c/keyword/static_assert) (C23) | [`_Atomic`](https://zh.cppreference.com/w/c/keyword/_Atomic) (C11) |
| [`bool`](https://zh.cppreference.com/w/c/keyword/bool) (C23) | [`for`](https://zh.cppreference.com/w/c/keyword/for)         | [`struct`](https://zh.cppreference.com/w/c/keyword/struct)   | [`_BitInt`](https://zh.cppreference.com/mwiki/index.php?title=c/keyword/_BitInt&action=edit&redlink=1) (C23) |
| [`break`](https://zh.cppreference.com/w/c/keyword/break)     | [`goto`](https://zh.cppreference.com/w/c/keyword/goto)       | [`switch`](https://zh.cppreference.com/w/c/keyword/switch)   | [`_Bool`](https://zh.cppreference.com/w/c/keyword/_Bool) (C99)(C23 弃用) |
| [`case`](https://zh.cppreference.com/w/c/keyword/case)       | [`if`](https://zh.cppreference.com/w/c/keyword/if)           | [`thread_local`](https://zh.cppreference.com/w/c/keyword/thread_local) (C23) | [`_Complex`](https://zh.cppreference.com/w/c/keyword/_Complex) (C99) |
| [`char`](https://zh.cppreference.com/w/c/keyword/char)       | [`inline`](https://zh.cppreference.com/w/c/keyword/inline) (C99) | [`true`](https://zh.cppreference.com/w/c/keyword/true) (C23) | [`_Decimal128`](https://zh.cppreference.com/w/c/keyword/_Decimal128) (C23) |
| [`const`](https://zh.cppreference.com/w/c/keyword/const)     | [`int`](https://zh.cppreference.com/w/c/keyword/int)         | [`typedef`](https://zh.cppreference.com/w/c/keyword/typedef) | [`_Decimal32`](https://zh.cppreference.com/w/c/keyword/_Decimal32) (C23) |
| [`constexpr`](https://zh.cppreference.com/w/c/keyword/constexpr) (C23) | [`long`](https://zh.cppreference.com/w/c/keyword/long)       | [`typeof`](https://zh.cppreference.com/w/c/keyword/typeof) (C23) | [`_Decimal64`](https://zh.cppreference.com/w/c/keyword/_Decimal64) (C23) |
| [`continue`](https://zh.cppreference.com/w/c/keyword/continue) | [`nullptr`](https://zh.cppreference.com/w/c/keyword/nullptr) (C23) | [`typeof_unqual`](https://zh.cppreference.com/w/c/keyword/typeof_unqual) (C23) | [`_Generic`](https://zh.cppreference.com/w/c/keyword/_Generic) (C11) |
| [`default`](https://zh.cppreference.com/w/c/keyword/default) | [`register`](https://zh.cppreference.com/w/c/keyword/register) | [`union`](https://zh.cppreference.com/w/c/keyword/union)     | [`_Imaginary`](https://zh.cppreference.com/w/c/keyword/_Imaginary) (C99) |
| [`do`](https://zh.cppreference.com/w/c/keyword/do)           | [`restrict`](https://zh.cppreference.com/w/c/keyword/restrict) (C99) | [`unsigned`](https://zh.cppreference.com/w/c/keyword/unsigned) | [`_Noreturn`](https://zh.cppreference.com/w/c/keyword/_Noreturn) (C11)(C23 弃用) |
| [`double`](https://zh.cppreference.com/w/c/keyword/double)   | [`return`](https://zh.cppreference.com/w/c/keyword/return)   | [`void`](https://zh.cppreference.com/w/c/keyword/void)       | [`_Static_assert`](https://zh.cppreference.com/w/c/keyword/_Static_assert) (C11)(C23 弃用) |
| [`else`](https://zh.cppreference.com/w/c/keyword/else)       | [`short`](https://zh.cppreference.com/w/c/keyword/short)     | [`volatile`](https://zh.cppreference.com/w/c/keyword/volatile) | [`_Thread_local`](https://zh.cppreference.com/w/c/keyword/_Thread_local) (C11)(C23 弃用) |
| [`enum`](https://zh.cppreference.com/w/c/keyword/enum)       | [`signed`](https://zh.cppreference.com/w/c/keyword/signed)   | [`while`](https://zh.cppreference.com/w/c/keyword/while)     |                                                              |



​	最常见的以下划线开头的关键词通常通过其便利宏来使用：

| **关键词**                                                   | **用作**                                                     | **定义于**    |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------- |
| [`_Alignas`](https://zh.cppreference.com/w/c/keyword/_Alignas) (C11)(C23 弃用) | [`alignas`](https://zh.cppreference.com/w/c/types) (C23 )    | stdalign.h    |
| [`_Alignof`](https://zh.cppreference.com/w/c/keyword/_Alignof) (C11)(C23 弃用) | [`alignof`](https://zh.cppreference.com/w/c/types) (C23 )    | stdalign.h    |
| [`_Atomic`](https://zh.cppreference.com/w/c/keyword/_Atomic) (C11) | [`atomic_bool, atomic_int, ...`](https://zh.cppreference.com/w/c/thread) | stdatomic.h   |
| [`_BitInt`](https://zh.cppreference.com/mwiki/index.php?title=c/keyword/_BitInt&action=edit&redlink=1) (C23) | （无宏）                                                     |               |
| [`_Bool`](https://zh.cppreference.com/w/c/keyword/_Bool) (C99)(C23 弃用) | [`bool`](https://zh.cppreference.com/w/c/types) (C23 )       | stdbool.h     |
| [`_Complex`](https://zh.cppreference.com/w/c/keyword/_Complex) (C99) | [`complex`](https://zh.cppreference.com/w/c/numeric/complex/complex) | complex.h     |
| [`_Decimal128`](https://zh.cppreference.com/w/c/keyword/_Decimal128) (C23) | （无宏）                                                     |               |
| [`_Decimal32`](https://zh.cppreference.com/w/c/keyword/_Decimal32) (C23) | （无宏）                                                     |               |
| [`_Decimal64`](https://zh.cppreference.com/w/c/keyword/_Decimal64) (C23) | （无宏）                                                     |               |
| [`_Generic`](https://zh.cppreference.com/w/c/keyword/_Generic) (C11) | （无宏）                                                     |               |
| [`_Imaginary`](https://zh.cppreference.com/w/c/keyword/_Imaginary) (C99) | [`imaginary`](https://zh.cppreference.com/w/c/numeric/complex/imaginary) | complex.h     |
| [`_Noreturn`](https://zh.cppreference.com/w/c/keyword/_Noreturn) (C11)(C23 弃用) | [`noreturn`](https://zh.cppreference.com/w/c/types)          | stdnoreturn.h |
| [`_Static_assert`](https://zh.cppreference.com/w/c/keyword/_Static_assert) (C11)(C23 弃用) | [`static_assert`](https://zh.cppreference.com/w/c/error/static_assert) (C23 ) | assert.h      |
| [`_Thread_local`](https://zh.cppreference.com/w/c/keyword/_Thread_local) (C11)(C23 弃用) | [`thread_local`](https://zh.cppreference.com/w/c/thread/thread_local) (C23 ) | threads.h     |

​	一些关键词被弃用，出于兼容目的仍然作为对应关键词的代用拼写保留，可以在任何可以使用该关键词的地方使用。

| **关键词**            | **代用拼写**                     |
| --------------------- | -------------------------------- |
| `alignas` (C23)       | `_Alignas` (C11)(C23 弃用)       |
| `alignof` (C23)       | `_Alignof` (C11)(C23 弃用)       |
| `bool` (C23)          | `_Bool` (C99)(C23 弃用)          |
| `static_assert` (C23) | `_Static_assert` (C11)(C23 弃用) |
| `thread_local` (C23)  | `_Thread_local` (C11)(C23 弃用)  |

​	这些关键词的拼写、它们的替代形式，以及 `true` 和 `false` 是否实现为预定义宏是未指定的。

​	每个以双下划线 `__` 或单下划线 `_` 后随大写字母为首的名称都是受保留的：细节见[标识符](https://zh.cppreference.com/w/c/language/identifier#.E4.BF.9D.E7.95.99.E6.A0.87.E8.AF.86.E7.AC.A6)。

> 注意
>
> ​	合字符 `<%`、`%>`、`<:`、`:>`、`%:` 以及 `%:%:` 提供[表示标准记号的代用表示法](https://zh.cppreference.com/w/c/language/operator_alternative)。

​	下列记号在用于[预处理器](https://zh.cppreference.com/w/c/preprocessor)指令语境*之内* ﻿时，为预处理器所识别：

| [`if`](https://zh.cppreference.com/w/c/preprocessor/conditional) | [`ifdef`](https://zh.cppreference.com/w/c/preprocessor/conditional) | [`include`](https://zh.cppreference.com/w/c/preprocessor/include) | [`defined`](https://zh.cppreference.com/w/c/preprocessor/conditional) |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [`elif`](https://zh.cppreference.com/w/c/preprocessor/conditional) | [`ifndef`](https://zh.cppreference.com/w/c/preprocessor/conditional) | [`embed`](https://zh.cppreference.com/w/c/preprocessor/embed) (C23) | [`__has_include`](https://zh.cppreference.com/w/c/preprocessor/include) (C23) |
| [`else`](https://zh.cppreference.com/w/c/preprocessor/conditional) | [`elifdef`](https://zh.cppreference.com/w/c/preprocessor/conditional) (C23 起) | [`line`](https://zh.cppreference.com/w/c/preprocessor/line)  | [`__has_embed`](https://zh.cppreference.com/w/c/preprocessor/embed) (C23) |
| [`endif`](https://zh.cppreference.com/w/c/preprocessor/conditional) | [`elifndef`](https://zh.cppreference.com/w/c/preprocessor/conditional) (C23 起) | [`error`](https://zh.cppreference.com/w/c/preprocessor/error) | [`__has_c_attribute`](https://zh.cppreference.com/w/c/language/attributes#.E5.B1.9E.E6.80.A7.E6.B5.8B.E8.AF.95) (C23) |
|                                                              | [`define`](https://zh.cppreference.com/w/c/preprocessor/replace) | [`warning`](https://zh.cppreference.com/w/c/preprocessor/error) (C23) |                                                              |
|                                                              | [`undef`](https://zh.cppreference.com/w/c/preprocessor/replace) | [`pragma`](https://zh.cppreference.com/w/c/preprocessor/impl) |                                                              |

​	下列记号用于预处理器指令的语境*之外* ﻿时，为预处理器所识别：

[`_Pragma`](https://zh.cppreference.com/w/c/preprocessor/impl)(C99)

​	下列的额外关键词被分类为扩展，并且为条件性支持：

[`asm`](https://zh.cppreference.com/w/c/language/asm)   

[`fortran`](https://zh.cppreference.com/w/c/keyword/fortran)

## 参阅

**C++ 关键词**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/keyword)**