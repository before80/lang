+++
title = "nullptr_t"
date = 2025-04-14T15:50:16+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/types/nullptr_t](https://zh.cppreference.com/w/c/types/nullptr_t)

| 在标头 `<stddef.h>` 定义             |      |          |
| ------------------------------------ | ---- | -------- |
| `typedef typeof(nullptr) nullptr_t;` |      | (C23 起) |

​	`nullptr_t` 是预定义空指针常量 [`nullptr`]({{< ref "/c/language/expressions/nullptr" >}}) 的类型。它是自身并非指针类型的单独类型。它能[隐式转换到]({{< ref "/c/language/expressions/conversion" >}})任何指针类型或 bool，而结果分别为该类型的空指针值或 false。除了 `nullptr_t` 自身，没有其他类型能转换或显式转型成 `nullptr_t`。

​	`sizeof(nullptr_t)` 与 `alignof(nullptr_t)` 分别等于 `sizeof(void*)` 与 `alignof(void*)`。

`nullptr_t` 仅有一个合法值，即 `nullptr`。`nullptr` 的对象表示与 `(void*)0` 的相同。若[左值转换]({{< ref "/c/language/expressions/conversion#.E5.B7.A6.E5.80.BC.E8.BD.AC.E6.8D.A2" >}})产生拥有不同对象表示的 `nullptr_t` 值，则行为未定义。

## 示例

​	演示 `nullptr_t` 为单独的类型。

```c
#include <stddef.h>
#include <stdio.h>
 
#define DETECT_NULL_POINTER_CONSTANT(e) \
    _Generic(e,                         \
        void* : puts("void*"),          \
        nullptr_t : puts("nullptr_t"),  \
        default : puts("other")         \
    )
 
int main()
{
    DETECT_NULL_POINTER_CONSTANT(((void*)0));
    DETECT_NULL_POINTER_CONSTANT(0);
    DETECT_NULL_POINTER_CONSTANT(nullptr);
}
```

输出：

```txt
void*
other
nullptr_t
```

## 参阅

| [NULL]({{< ref "/c/types/NULL" >}})           | 实现定义的空指针常量 (宏常量) |
| ------------------------------------------------------------ | ----------------------------- |
| **nullptr_t** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/nullptr_t)** |                               |
