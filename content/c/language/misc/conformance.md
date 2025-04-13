+++
title = "遵从性"
date = 2025-04-13T14:17:12+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/conformance](https://zh.cppreference.com/w/c/language/conformance)

​	*遵从性 (conformance)* 有三重定义：

- *严格遵从程序* - 仅使用良定义的语言构造，即拥有单一行为的构造。它不包含未指定、未定义或实现定义的行为，且不超过任何最小实现极限。
- *遵从程序* - 可为遵从实现所接受。
- 遵从实现 -
  - 遵从的有宿主实现应当接受任何严格遵从程序。
  - 遵从的自立实现应当接受任何将库章（第 7 章）中指定的库特性限制到自立的标准库头文件（见后述）的内容的严格遵从程序。
  - 遵从实现可拥有扩展（包括额外的库函数），只要它们不改变任何严格遵从程序的行为。

## 解释

​	标准不在翻译单元上定义任何最小实现极限。有宿主环境拥有操作系统；自立环境无操作系统。运行于有宿主环境中的程序可使用任何库章节（第 7 章）中描述的特性；运行于自立环境中的程序可使用第 4 章所要求的库特性子集。

### 自立的标准库头文件

​	要求为自立实现提供每个完全自立的标准库头文件中的所有标准库特性。

有些标准库头文件是条件性自立的。(C23 起)

- 若实现预定义了宏 `__STDC_IEC_60559_BFP__` 或 `__STDC_IEC_60559_DFP__`，则 [`<math.h>`](https://zh.cppreference.com/w/c/header/math) 与 [`<fenv.h>`](https://zh.cppreference.com/w/c/header/fenv) 为完全自立的头文件。然而，在独立环境中，仅当程序不设置 [`FENV_ACCESS`](https://zh.cppreference.com/w/c/preprocessor/impl#.E6.A0.87.E5.87.86.E8.AF.AD.E7.94.A8) 语用为 `ON` 才要求这些头文件中的函数行为良定义。

有些标准库头文件是部分自立的。(C23 起)

- 在 [`<stdlib.h>`](https://zh.cppreference.com/w/c/header/stdlib) 中， [`memalignment`](https://zh.cppreference.com/w/c/program/memalignment) 是独立的。另外，如果预定义了 `__STDC_IEC_60559_BFP__` 或 `__STDC_IEC_60559_DFP__`，则供数值转换函数（`atoX`、`strtoX` 及 `strfromX`）也是独立的，然而仅当程序不设置 [`FENV_ACCESS`](https://zh.cppreference.com/w/c/preprocessor/impl#.E6.A0.87.E5.87.86.E8.AF.AD.E7.94.A8) 语用为 `ON` 才要求其行为良定义。不要求自立实现提供 [`<stdlib.h>`](https://zh.cppreference.com/w/c/header/stdlib) 中的其他组件。
- 在 [`<string.h>`](https://zh.cppreference.com/w/c/header/string) 中，不要求自立实现提供 [`strdup`](https://zh.cppreference.com/w/c/string/byte/strdup)、[`strndup`](https://zh.cppreference.com/w/c/string/byte/strndup)、[strcoll](https://zh.cppreference.com/w/c/string/byte/strcoll)、[strtok](https://zh.cppreference.com/w/c/string/byte/strtok)、[strxfrm](https://zh.cppreference.com/w/c/string/byte/strxfrm) 及 [strerror](https://zh.cppreference.com/w/c/string/byte/strerror)。



### 完全自立的标准库头文件

| [`<float.h>`](https://zh.cppreference.com/w/c/header/float)  | [浮点类型的极限](https://zh.cppreference.com/w/c/types/limits#.E6.B5.AE.E7.82.B9.E7.B1.BB.E5.9E.8B.E7.9A.84.E6.9E.81.E9.99.90) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [`<iso646.h> `](https://zh.cppreference.com/w/c/header/iso646) (C95 起) | [运算符的替代写法](https://zh.cppreference.com/w/c/language/operator_alternative) |
| [`<limits.h>`](https://zh.cppreference.com/w/c/header/limits) | [整数类型的范围](https://zh.cppreference.com/w/c/types/limits#.E6.95.B4.E6.95.B0.E7.B1.BB.E5.9E.8B.E7.9A.84.E8.8C.83.E5.9B.B4) |
| [`<stdalign.h>`](https://zh.cppreference.com/w/c/header/stdalign) (C11 起) | [`alignas` 与 `alignof`](https://zh.cppreference.com/w/c/types) 便利宏 |
| [`<stdarg.h>`](https://zh.cppreference.com/w/c/header/stdarg) | [可变参数](https://zh.cppreference.com/w/c/variadic)         |
| [`<stdbool.h> `](https://zh.cppreference.com/w/c/header/stdbool) (C99 起) | [布尔类型的宏](https://zh.cppreference.com/w/c/types)        |
| [`<stddef.h>`](https://zh.cppreference.com/w/c/header/stddef) | [常用宏定义](https://zh.cppreference.com/w/c/types)          |
| [`<stdint.h>`](https://zh.cppreference.com/w/c/header/stdint) (C99 起) | [定宽整数类型](https://zh.cppreference.com/w/c/types/integer) |
| [`<stdnoreturn.h>`](https://zh.cppreference.com/w/c/header/stdnoreturn) (C11 起) | [`noreturn`](https://zh.cppreference.com/w/c/types) 便利宏   |
| [`<stdbit.h> `](https://zh.cppreference.com/w/c/header/stdbit) (C23 起) | 工作于类型的字节和位表示的宏                                 |

### 条件性完全自立的标准库头文件 

| [`<fenv.h>`](https://zh.cppreference.com/w/c/header/fenv) (C23 起) | [浮点环境](https://zh.cppreference.com/w/c/numeric/fenv)     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [`<math.h>`](https://zh.cppreference.com/w/c/header/math) (C23 起) | [常用数学函数](https://zh.cppreference.com/w/c/numeric/math) |

### 部分自立的标准库头文件

| [`<stdlib.h>`](https://zh.cppreference.com/w/c/header/stdlib) (C23 起) | 基础工具：[内存管理](https://zh.cppreference.com/w/c/memory)、[程序工具](https://zh.cppreference.com/w/c/program)、[字符串转换](https://zh.cppreference.com/w/c/string)、[随机数](https://zh.cppreference.com/w/c/numeric/random)、[算法](https://zh.cppreference.com/w/c/algorithm) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [`<string.h>`](https://zh.cppreference.com/w/c/header/string) (C23 起) | [字符串处理](https://zh.cppreference.com/w/c/string/byte)    |


## 参阅

**自立与有宿主实现**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/freestanding)**
