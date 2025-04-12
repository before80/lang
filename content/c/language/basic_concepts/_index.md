+++
title = "基本概念"
date = 2025-04-12T08:55:29+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/basic_concepts](https://zh.cppreference.com/w/c/language/basic_concepts)

​	本节提供描述 C 程序语言时所用的专用术语的定义和概念的定义。

​	C 程序是一系列文本文件（通常是头文件和源文件），它们包含一些[声明](https://zh.cppreference.com/w/c/language/declarations)。它们会经过[翻译](https://zh.cppreference.com/w/c/language/translation_phases)变成可执行程序，在操作系统调用其[主函数](https://zh.cppreference.com/w/c/language/main_function)时被执行（除非它自己就是 OS 程序或其他*自立* ﻿程序，这种情况下入口点是实现定义的）。

​	某些词在 C 程序中拥有特别含义，它们是[关键词](https://zh.cppreference.com/w/c/keyword)。其他词可用做[标识符](https://zh.cppreference.com/w/c/language/identifier)，可用于标识[对象](https://zh.cppreference.com/w/c/language/object)、[函数](https://zh.cppreference.com/w/c/language/functions)、[结构体](https://zh.cppreference.com/w/c/language/struct)、[联合体](https://zh.cppreference.com/w/c/language/union)或[枚举](https://zh.cppreference.com/w/c/language/enum)的标签，它们的成员，[typedef](https://zh.cppreference.com/w/c/language/typedef) 名，[标号](https://zh.cppreference.com/w/c/language/statements#.E6.A0.87.E5.8F.B7)，或者[宏](https://zh.cppreference.com/w/c/preprocessor/replace)。

​	每个标识符（除了宏）仅在程序的一部分中合法，这部分被称为它的[作用域](https://zh.cppreference.com/w/c/language/scope)，并属于四种[命名空间](https://zh.cppreference.com/w/c/language/name_space)之一。一些标识符拥有[链接](https://zh.cppreference.com/w/c/language/storage_duration)，这会令它们出现于不同作用域或翻译单元时，指代同一实体。

​	函数的定义包含一系列[语句](https://zh.cppreference.com/w/c/language/statements)和[声明](https://zh.cppreference.com/w/c/language/declarations)，其中有的包含[表达式](https://zh.cppreference.com/w/c/language/expressions)，它指定程序要进行的计算。

​	[声明](https://zh.cppreference.com/w/c/language/declarations)和[表达式](https://zh.cppreference.com/w/c/language/expressions)创建、销毁、访问并操作[对象](https://zh.cppreference.com/w/c/language/object)。C 中的每个[对象](https://zh.cppreference.com/w/c/language/object)、[函数](https://zh.cppreference.com/w/c/language/functions)及[表达式](https://zh.cppreference.com/w/c/language/expressions)均关联到一种[类型](https://zh.cppreference.com/w/c/language/types)。

## 参阅

**基本概念**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/basic_concepts)**