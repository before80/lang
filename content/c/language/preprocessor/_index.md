+++
title = "预处理器"
date = 2025-04-12T11:55:54+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/preprocessor](https://zh.cppreference.com/w/c/preprocessor)

​	预处理器于[翻译阶段 4](https://zh.cppreference.com/w/c/language/translation_phases#.E9.98.B6.E6.AE.B5_4) 执行，在编译之前。预处理的结果是随后将传递给实际编译器的单个文件。

## 指令

​	预处理指令控制预处理器的行为。每个指令占据一行，且拥有下列格式：

- `#` 字符
- 预处理指令（`define`、`undef`、`include`、`if`、`ifdef`、`ifndef`、`else`、`elif`、`elifdef`、`elifndef`(C23 起)、`endif`、`line`、`embed`(C23 起)、`error`、`warning`(C23 起)、`pragma` 之一）[[1\]](https://zh.cppreference.com/w/c/preprocessor#cite_note-1)
- 实参（取决于指令）
- 换行符

允许空指令（跟随换行符的 `#`），而它无效果。

## 能力

​	预处理器拥有源文件翻译能力：

- **[有条件](https://zh.cppreference.com/w/c/preprocessor/conditional)**编译源文件的某些部分（由 `#if`、`#ifdef`、`#ifndef`、`#else`、`#elif`、`elifdef`、`elifndef`(C23 起) 和 `#endif` 指令控制）。
- **[替换](https://zh.cppreference.com/w/c/preprocessor/replace)**文本宏，可以连接或加引标识符（以指令 `#define` 和 `#undef`，运算符 `#` 和 `##` 控制）。
- **[包含](https://zh.cppreference.com/w/c/preprocessor/include)**其他文件（以指令 `#include` 控制并以 `__has_include` 检查(C23 起)）。
- 导致**[错误](https://zh.cppreference.com/w/c/preprocessor/error)**或**[警告](https://zh.cppreference.com/w/c/preprocessor/error)**(C23 起)（以指令 `#error` 或 `#warning`(C23 起) 控制）。

​	能控制预处理器的下列方面：

- **[实现定义](https://zh.cppreference.com/w/c/preprocessor/impl)**行为（以指令 `#pragma` 及运算符 `_Pragma` (C99 起)控制）。
- **[文件名与行信息](https://zh.cppreference.com/w/c/preprocessor/line)**，可用于预处理器（以指令 `#line` 控制）。

## 脚注

1. [↑](https://zh.cppreference.com/w/c/preprocessor#cite_ref-1) 这些指令是标准定义的。标准不定义其他指令的行为：它们可以被忽略、拥有一些有用的含义或导致编译时错误。即使忽略，也会在预处理器完成工作时将它们从源码中移除。一种常用的非标准扩展是 [#warning](https://zh.cppreference.com/w/c/preprocessor/error) 指令，它在编译期间放出一条用户定义的消息。(C23 前)

## 示例

> 本节未完成 
>
> 原因：暂无示例
>

## 参阅

| **预定义宏符号**的 **[C 文档](https://zh.cppreference.com/w/c/preprocessor/replace#.E9.A2.84.E5.AE.9A.E4.B9.89.E5.AE.8F)** |
| ------------------------------------------------------------ |
| **宏符号索引**的 **[C 文档](https://zh.cppreference.com/w/c/symbol_index/macro)** |
| **预处理器**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/preprocessor)** |