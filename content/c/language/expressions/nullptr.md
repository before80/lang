+++
title = "预定义空指针常量"
date = 2025-04-12T20:25:46+08:00
weight = 110
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/nullptr](https://zh.cppreference.com/w/c/language/nullptr)

### 语法

| `nullptr` | (C23 起) |
| --------- | -------- |

## 解释

​	关键词 `nullptr` 代表预定义的空指针常量。它是 [nullptr_t](https://zh.cppreference.com/w/c/types/nullptr_t) 类型的[非左值](https://zh.cppreference.com/w/c/language/value_category#.E9.9D.9E.E5.B7.A6.E5.80.BC.E5.AF.B9.E8.B1.A1.E8.A1.A8.E8.BE.BE.E5.BC.8F)。nullptr 能[转换](https://zh.cppreference.com/w/c/language/conversion)到指针类型或 bool，结果分别为该类型的空指针值或 false。

## 关键词

[`nullptr`](https://zh.cppreference.com/w/c/keyword/nullptr)

## 示例

​	演示 nullptr 的副本亦能用作空指针常量。

```c
#include <stddef.h>
#include <stdio.h>
 
void g(int*)
{
    puts("Function g called");
}
 
#define DETECT_NULL_POINTER_CONSTANT(e) \
    _Generic(e,                         \
        void* : puts("void*"),          \
        nullptr_t : puts("nullptr_t"),  \
        default : puts("integer")       \
    )
 
int main()
{
    g(nullptr); // OK
    g(NULL); // OK
    g(0); // OK
 
    auto cloned_nullptr = nullptr;
    g(cloned_nullptr); // OK
 
    [[maybe_unused]] auto cloned_NULL = NULL;
//  g(cloned_NULL); // 由实现定义：可能 OK
 
    [[maybe_unused]] auto cloned_zero = 0;
//  g(cloned_zero); // 错误
 
    DETECT_NULL_POINTER_CONSTANT(((void*)0));
    DETECT_NULL_POINTER_CONSTANT(0);
    DETECT_NULL_POINTER_CONSTANT(nullptr);
    DETECT_NULL_POINTER_CONSTANT(NULL); // 实现定义
}
```

​	可能的输出：

```txt
Function g called
Function g called
Function g called
Function g called
void*
integer
nullptr_t
void*
```

## 参阅

| [NULL](https://zh.cppreference.com/w/c/types/NULL)           | 实现定义的空指针常量 (宏常量)               |
| ------------------------------------------------------------ | ------------------------------------------- |
| [nullptr_t](https://zh.cppreference.com/w/c/types/nullptr_t)(C23) | 预定义空指针常量 `nullptr` 的类型 (typedef) |
| nullptr 的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/nullptr) |                                             |