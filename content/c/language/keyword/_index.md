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

​	这是 C 中保留的关键词列表。因为语言使用这些关键词，故不可重定义它们。其例外是，它们在 [*attribute-token*]({{< ref "/c/language/declarations/attributes" >}}) 中并不被保留使用。(C23 起)

| [`alignas`]({{< ref "/c/language/keyword/alignas" >}}) (C23) | [`extern`]({{< ref "/c/language/keyword/extern" >}})   | [`sizeof`]({{< ref "/c/language/keyword/sizeof" >}})   | [`_Alignas`]({{< ref "/c/language/keyword/_Alignas" >}}) (C11)(C23 弃用) |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [`alignof`]({{< ref "/c/language/keyword/alignof" >}}) (C23) | [`false`]({{< ref "/c/language/keyword/false" >}}) (C23) | [`static`]({{< ref "/c/language/keyword/static" >}})   | [`_Alignof`]({{< ref "/c/language/keyword/_Alignof" >}}) (C11)(C23 弃用) |
| [`auto`]({{< ref "/c/language/keyword/auto" >}})       | [`float`]({{< ref "/c/language/keyword/float" >}})     | [`static_assert`]({{< ref "/c/language/keyword/static_assert" >}}) (C23) | [`_Atomic`]({{< ref "/c/language/keyword/_Atomic" >}}) (C11) |
| [`bool`]({{< ref "/c/language/keyword/bool" >}}) (C23) | [`for`]({{< ref "/c/language/keyword/for" >}})         | [`struct`]({{< ref "/c/language/keyword/struct" >}})   | [`_BitInt`](https://zh.cppreference.com/mwiki/index.php?title=c/keyword/_BitInt&action=edit&redlink=1) (C23) |
| [`break`]({{< ref "/c/language/keyword/break" >}})     | [`goto`]({{< ref "/c/language/keyword/goto" >}})       | [`switch`]({{< ref "/c/language/keyword/switch" >}})   | [`_Bool`]({{< ref "/c/language/keyword/_Bool" >}}) (C99)(C23 弃用) |
| [`case`]({{< ref "/c/language/keyword/case" >}})       | [`if`]({{< ref "/c/language/keyword/if" >}})           | [`thread_local`]({{< ref "/c/language/keyword/thread_local" >}}) (C23) | [`_Complex`]({{< ref "/c/language/keyword/_Complex" >}}) (C99) |
| [`char`]({{< ref "/c/language/keyword/char" >}})       | [`inline`]({{< ref "/c/language/keyword/inline" >}}) (C99) | [`true`]({{< ref "/c/language/keyword/true" >}}) (C23) | [`_Decimal128`]({{< ref "/c/language/keyword/_Decimal128" >}}) (C23) |
| [`const`]({{< ref "/c/language/keyword/const" >}})     | [`int`]({{< ref "/c/language/keyword/int" >}})         | [`typedef`]({{< ref "/c/language/keyword/typedef" >}}) | [`_Decimal32`]({{< ref "/c/language/keyword/_Decimal32" >}}) (C23) |
| [`constexpr`]({{< ref "/c/language/keyword/constexpr" >}}) (C23) | [`long`]({{< ref "/c/language/keyword/long" >}})       | [`typeof`]({{< ref "/c/language/keyword/typeof" >}}) (C23) | [`_Decimal64`]({{< ref "/c/language/keyword/_Decimal64" >}}) (C23) |
| [`continue`]({{< ref "/c/language/keyword/continue" >}}) | [`nullptr`]({{< ref "/c/language/keyword/nullptr" >}}) (C23) | [`typeof_unqual`]({{< ref "/c/language/keyword/typeof_unqual" >}}) (C23) | [`_Generic`]({{< ref "/c/language/keyword/_Generic" >}}) (C11) |
| [`default`]({{< ref "/c/language/keyword/default" >}}) | [`register`]({{< ref "/c/language/keyword/register" >}}) | [`union`]({{< ref "/c/language/keyword/union" >}})     | [`_Imaginary`]({{< ref "/c/language/keyword/_Imaginary" >}}) (C99) |
| [`do`]({{< ref "/c/language/keyword/do" >}})           | [`restrict`]({{< ref "/c/language/keyword/restrict" >}}) (C99) | [`unsigned`]({{< ref "/c/language/keyword/unsigned" >}}) | [`_Noreturn`]({{< ref "/c/language/keyword/_Noreturn" >}}) (C11)(C23 弃用) |
| [`double`]({{< ref "/c/language/keyword/double" >}})   | [`return`]({{< ref "/c/language/keyword/return" >}})   | [`void`]({{< ref "/c/language/keyword/void" >}})       | [`_Static_assert`]({{< ref "/c/language/keyword/_Static_assert" >}}) (C11)(C23 弃用) |
| [`else`]({{< ref "/c/language/keyword/else" >}})       | [`short`]({{< ref "/c/language/keyword/short" >}})     | [`volatile`]({{< ref "/c/language/keyword/volatile" >}}) | [`_Thread_local`]({{< ref "/c/language/keyword/_Thread_local" >}}) (C11)(C23 弃用) |
| [`enum`](https://zh.cppreference.com/w/c/keyword/enum)       | [`signed`]({{< ref "/c/language/keyword/signed" >}})   | [`while`]({{< ref "/c/language/keyword/while" >}})     |                                                              |



​	最常见的以下划线开头的关键词通常通过其便利宏来使用：

| **关键词**                                                   | **用作**                                                     | **定义于**    |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------- |
| [`_Alignas`]({{< ref "/c/language/keyword/_Alignas" >}}) (C11)(C23 弃用) | [`alignas`]({{< ref "/c/types" >}}) (C23 )    | stdalign.h    |
| [`_Alignof`]({{< ref "/c/language/keyword/_Alignof" >}}) (C11)(C23 弃用) | [`alignof`]({{< ref "/c/types" >}}) (C23 )    | stdalign.h    |
| [`_Atomic`]({{< ref "/c/language/keyword/_Atomic" >}}) (C11) | [`atomic_bool, atomic_int, ...`](https://zh.cppreference.com/w/c/thread) | stdatomic.h   |
| [`_BitInt`](https://zh.cppreference.com/mwiki/index.php?title=c/keyword/_BitInt&action=edit&redlink=1) (C23) | （无宏）                                                     |               |
| [`_Bool`]({{< ref "/c/language/keyword/_Bool" >}}) (C99)(C23 弃用) | [`bool`]({{< ref "/c/types" >}}) (C23 )       | stdbool.h     |
| [`_Complex`]({{< ref "/c/language/keyword/_Complex" >}}) (C99) | [`complex`](https://zh.cppreference.com/w/c/numeric/complex/complex) | complex.h     |
| [`_Decimal128`]({{< ref "/c/language/keyword/_Decimal128" >}}) (C23) | （无宏）                                                     |               |
| [`_Decimal32`]({{< ref "/c/language/keyword/_Decimal32" >}}) (C23) | （无宏）                                                     |               |
| [`_Decimal64`]({{< ref "/c/language/keyword/_Decimal64" >}}) (C23) | （无宏）                                                     |               |
| [`_Generic`]({{< ref "/c/language/keyword/_Generic" >}}) (C11) | （无宏）                                                     |               |
| [`_Imaginary`]({{< ref "/c/language/keyword/_Imaginary" >}}) (C99) | [`imaginary`](https://zh.cppreference.com/w/c/numeric/complex/imaginary) | complex.h     |
| [`_Noreturn`]({{< ref "/c/language/keyword/_Noreturn" >}}) (C11)(C23 弃用) | [`noreturn`]({{< ref "/c/types" >}})          | stdnoreturn.h |
| [`_Static_assert`]({{< ref "/c/language/keyword/_Static_assert" >}}) (C11)(C23 弃用) | [`static_assert`](https://zh.cppreference.com/w/c/error/static_assert) (C23 ) | assert.h      |
| [`_Thread_local`]({{< ref "/c/language/keyword/_Thread_local" >}}) (C11)(C23 弃用) | [`thread_local`](https://zh.cppreference.com/w/c/thread/thread_local) (C23 ) | threads.h     |

​	一些关键词被弃用，出于兼容目的仍然作为对应关键词的代用拼写保留，可以在任何可以使用该关键词的地方使用。

| **关键词**            | **代用拼写**                     |
| --------------------- | -------------------------------- |
| `alignas` (C23)       | `_Alignas` (C11)(C23 弃用)       |
| `alignof` (C23)       | `_Alignof` (C11)(C23 弃用)       |
| `bool` (C23)          | `_Bool` (C99)(C23 弃用)          |
| `static_assert` (C23) | `_Static_assert` (C11)(C23 弃用) |
| `thread_local` (C23)  | `_Thread_local` (C11)(C23 弃用)  |

​	这些关键词的拼写、它们的替代形式，以及 `true` 和 `false` 是否实现为预定义宏是未指定的。

​	每个以双下划线 `__` 或单下划线 `_` 后随大写字母为首的名称都是受保留的：细节见[标识符]({{< ref "/c/language/basic_concepts/identifier#.E4.BF.9D.E7.95.99.E6.A0.87.E8.AF.86.E7.AC.A6" >}})。

> 注意
>
> ​	合字符 `<%`、`%>`、`<:`、`:>`、`%:` 以及 `%:%:` 提供[表示标准记号的代用表示法](https://zh.cppreference.com/w/c/language/operator_alternative)。

​	下列记号在用于[预处理器]({{< ref "/c/language/preprocessor" >}})指令语境*之内* ﻿时，为预处理器所识别：

| [`if`]({{< ref "/c/language/preprocessor/conditional" >}}) | [`ifdef`]({{< ref "/c/language/preprocessor/conditional" >}}) | [`include`]({{< ref "/c/language/preprocessor/include" >}}) | [`defined`]({{< ref "/c/language/preprocessor/conditional" >}}) |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [`elif`]({{< ref "/c/language/preprocessor/conditional" >}}) | [`ifndef`]({{< ref "/c/language/preprocessor/conditional" >}}) | [`embed`]({{< ref "/c/language/preprocessor/embed" >}}) (C23) | [`__has_include`]({{< ref "/c/language/preprocessor/include" >}}) (C23) |
| [`else`]({{< ref "/c/language/preprocessor/conditional" >}}) | [`elifdef`]({{< ref "/c/language/preprocessor/conditional" >}}) (C23 起) | [`line`]({{< ref "/c/language/preprocessor/line" >}})  | [`__has_embed`]({{< ref "/c/language/preprocessor/embed" >}}) (C23) |
| [`endif`]({{< ref "/c/language/preprocessor/conditional" >}}) | [`elifndef`]({{< ref "/c/language/preprocessor/conditional" >}}) (C23 起) | [`error`]({{< ref "/c/language/preprocessor/error" >}}) | [`__has_c_attribute`]({{< ref "/c/language/declarations/attributes#.E5.B1.9E.E6.80.A7.E6.B5.8B.E8.AF.95" >}}) (C23) |
|                                                              | [`define`]({{< ref "/c/language/preprocessor/replace" >}}) | [`warning`]({{< ref "/c/language/preprocessor/error" >}}) (C23) |                                                              |
|                                                              | [`undef`]({{< ref "/c/language/preprocessor/replace" >}}) | [`pragma`](https://zh.cppreference.com/w/c/preprocessor/impl) |                                                              |

​	下列记号用于预处理器指令的语境*之外* ﻿时，为预处理器所识别：

[`_Pragma`](https://zh.cppreference.com/w/c/preprocessor/impl)(C99)

​	下列的额外关键词被分类为扩展，并且为条件性支持：

[`asm`]({{< ref "/c/language/misc/asm" >}})   

[`fortran`]({{< ref "/c/language/keyword/fortran" >}})

## 参阅

**C++ 关键词**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/keyword)**
