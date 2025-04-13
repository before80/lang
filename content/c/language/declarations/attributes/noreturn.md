+++
title = "C 属性： noreturn, _Noreturn (C23 起)"
date = 2025-04-13T11:26:00+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/attributes/noreturn](https://zh.cppreference.com/w/c/language/attributes/noreturn)

​	指示函数不会返回。

## 语法

| `[[` `noreturn` `]]` <br />`[[` `__noreturn__` `]]`   |      |        |
| ----------------------------------------------------- | ---- | ------ |
| `[[` `_Noreturn` `]]` <br />`[[` `___Noreturn__` `]]` |      | (弃用) |

## 解释

​	指示函数不会返回。

​	这个属性适用于函数名，指示函数不会由于执行返回语句或由于抵达函数体结尾而返回（它可以通过执行 [longjmp](https://zh.cppreference.com/w/c/program/longjmp) 返回）。如果有此属性的函数实际返回，则其行为未定义。如果可以检测这种情况，建议编译器予以诊断。

​	之前曾以关键词 [`_Noreturn`](https://zh.cppreference.com/w/c/language/_Noreturn) 表示，直至从 C23 起被弃用而代之以这个属性。

## 标准库

​	以下标准库函数均被声明带有 `noreturn` 属性（C23 之前，它们曾以 [`_Noreturn`](https://zh.cppreference.com/w/c/language/_Noreturn) 说明符声明）：

- [abort()](https://zh.cppreference.com/w/c/program/abort)
- [exit()](https://zh.cppreference.com/w/c/program/exit)
- [_Exit()](https://zh.cppreference.com/w/c/program/_Exit)
- [quick_exit()](https://zh.cppreference.com/w/c/program/quick_exit)
- [thrd_exit()](https://zh.cppreference.com/w/c/thread/thrd_exit)
- [longjmp()](https://zh.cppreference.com/w/c/program/longjmp)

## 参阅

`_Noreturn` 的 [C 文档](https://zh.cppreference.com/w/c/language/_Noreturn)

`[[noreturn]]` 的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/attributes/noreturn)