+++
title = "源文件包含"
date = 2025-04-12T12:19:16+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/preprocessor/include](https://zh.cppreference.com/w/c/preprocessor/include)

​	包含另一源文件，到当前源文件中紧跟指令下一行的位置。

## 语法

|                                                              |      |          |
| ------------------------------------------------------------ | ---- | -------- |
| `#include <` *h-字符序列* `>` *换行*                         | (1)  |          |
| `#include "` *q-字符序列* `"` *换行*                         | (2)  |          |
| `#include` *pp-tokens* *换行*                                | (3)  |          |
| `__has_include` `(` `"` *q-字符序列* `"` `)` <br />`__has_include` `(` `<` *h-字符序列* `>` `)` | (4)  | (C23 起) |
| `__has_include` `(` *字符串字面量* `)` <br />`__has_include` `(` `<` *h-预处理记号序列* `>` `)` | (5)  | (C23 起) |

1) 搜索由 *h-字符序列* 所标定的头文件，并以该头文件的整个内容替换该指令。
2) 搜索由 *q-字符序列* 所标定的源文件，并以该源文件的整个内容替换该指令。它可能回退为 (1) 并将 *q-字符序列* 当做头文件标识。
3) 若 (1) 和 (2) 均未能匹配，则对 *预处理记号序列* 进行宏替换。替换后的指令再次尝试与 (1) 或 (2) 进行匹配。
4) 检查是否有头文件或源文件可被包含。
5) 若 (4) 未能匹配，则对 *h-预处理记号序列* 进行宏替换。替换后的指令再次尝试与 (4) 进行匹配。

| *换行*             | -    | 换行字符                                                     |
| ------------------ | ---- | ------------------------------------------------------------ |
| *h-字符序列*       | -    | 一个或更多 *h-字符* 的序列，出现以下任何字符导致未定义行为：<br />字符 `'`<br />字符 `"`<br />字符 `\` <br />字符序列 `//`<br />字符序列 `/*` |
| *h-字符*           | -    | [源字符集](https://zh.cppreference.com/w/c/language/translation_phases#.E9.98.B6.E6.AE.B5_5)中除了换行和 > 的任意成员 |
| *q-字符序列*       | -    | 一个或更多 *q-字符* 的序列，出现以下任何字符导致未定义行为：<br />字符 `'`<br />字符 `"`<br />字符 `\` <br />字符序列 `//`<br />字符序列 `/*` |
| *q-字符*           | -    | [源字符集](https://zh.cppreference.com/w/c/language/translation_phases#.E9.98.B6.E6.AE.B5_5)中除了换行和 `"` 的任意成员 |
| *预处理记号序列*   | -    | 一个或更多[预处理记号](https://zh.cppreference.com/w/c/language/translation_phases#.E9.98.B6.E6.AE.B5_3)的序列 |
| *字符串字面量*     | -    | [字符串字面量](https://zh.cppreference.com/w/c/language/string_literal) |
| *h-预处理记号序列* | -    | 一个或更多除了 > 外的[预处理记号](https://zh.cppreference.com/w/c/language/translation_phases#.E9.98.B6.E6.AE.B5_3)的序列 |

## 解释

1) 以由实现定义的方式搜索由 *h-字符序列* 所标定的文件。此语法的意图为搜索处于实现控制下的文件。典型实现仅搜索标准包含目录。标准 C 程序库被隐含包括在这些标准包含目录之中。用户通常可以通过编译器选项来控制标准包含目录。
2) 以由实现定义的方式搜索由 *q-字符序列* 所标定的文件。此语法的意图为搜索未处于实现控制下的文件。典型实现首先搜索当前文件所处的目录，仅当未找到文件时，再与 (1) 一样搜索标准包含目录。
3) 以普通文本相同的方式处理指令中 `include` 之后的各预处理记号（亦即将各个已定义的宏名替换为其预处理记号替换列表）。经过所有替换之后所得的指令，应当与之前两种形式之一相匹配。 如何将预处理记号对 < 和 > 或一对 " 字符之间的预处理记号的序列合并为一个头文件名的方法，是由实现定义的。
4) 如同语法 (3) 中的 *预处理记号序列* 一样搜索由 *h-字符序列* 或 *q-字符序列* 所标定的头文件或源文件，但不进行进一步的宏展开。如果该指令无法满足 #include 指令的语法规定，则程序非良构。如果对源文件的搜索成功，则 `__has_include` 表达式求值为 1，而若搜索失败，则为 ​0​。
5) 仅当语法 (4) 未能匹配时才考虑这种形式，这种情况下以普通文本一样处理各预处理记号。

​	在找不到文件的情况下，程序为病式。

可以在 [`#if`](https://zh.cppreference.com/w/c/preprocessor/conditional) 和 [`#elif`](https://zh.cppreference.com/w/c/preprocessor/conditional) 的表达式中展开 `__has_include`。它被 [`#ifdef`](https://zh.cppreference.com/w/c/preprocessor/conditional)、[` #ifndef`](https://zh.cppreference.com/w/c/preprocessor/conditional)、[` #elifdef`](https://zh.cppreference.com/w/c/preprocessor/conditional)、[` #elifndef`](https://zh.cppreference.com/w/c/preprocessor/conditional) 和 [`defined`](https://zh.cppreference.com/w/c/preprocessor/conditional) 当做已定义的宏，但不能用在别处。(C23 起)

## 注解

​	典型实现对语法 (1) 仅搜索标准包含目录。标准 C 程序库被隐含包括在这些标准包含目录之中。用户通常可以通过编译器选项来控制标准包含目录。

​	语法 (2) 的意图为搜索未处于实现控制下的文件。典型实现首先搜索当前文件所处的目录，然后回退到 (1)。

​	当包含一个文件时，对其进行[阶段](https://zh.cppreference.com/w/c/language/translation_phases) 1-4 的处理，其中可能（递归地）包含并展开嵌套的其他 `#include` 指令，直到由实现定义的嵌套极限为止。为了避免重复包含相同文件和文件（可能传递地）包含自身时发生无限递归，通常会使用*头文件防护*：将整个头文件包围于

```c
#ifndef FOO_H_INCLUDED /* 唯一映射到此文件名的任何名字 */
#define FOO_H_INCLUDED
// 此文件的内容在此
#endif
```

​	许多编译器还实现了具有类似效果的非标准[`语用`](https://zh.cppreference.com/w/c/preprocessor/impl) #pragma once：它在相同文件已被包含过时禁止再次处理该文件，其中以特定于操作系统的方式确定文件身份。

​	`__has_include` 结果为 1 仅表示存在具有指定名字的头文件或源文件。它并不意味着当包含该头文件或源文件时，不会导致错误或能够包含任何有用之物。

## 示例

本节未完成 

原因：暂无示例

## 参阅

| [c/header](https://zh.cppreference.com/w/c/header) C 标准库头文件列表 |
| ------------------------------------------------------------ |
| 源文件包含的 [C++ 文档](https://zh.cppreference.com/w/cpp/preprocessor/include) |