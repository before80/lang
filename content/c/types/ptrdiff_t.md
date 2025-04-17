+++
title = "ptrdiff_t"
date = 2025-04-14T15:48:12+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/types/ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)

| 在标头 `<stddef.h>` 定义 |      |      |
| ------------------------ | ---- | ---- |

​	`typedef /* 由实现定义 */ ptrdiff_t;`

​	`ptrdiff_t` 是[二个指针相减]({{< ref "/c/language/expressions/operator_arithmetic#.E6.8C.87.E9.92.88.E7.AE.97.E6.9C.AF" >}})结果所拥有的有符号整数类型。

| `ptrdiff_t` 的位宽不小于 17。 | (C99 起) (C23 前) |
| ----------------------------- | ----------------- |
| `ptrdiff_t` 的位宽不小于 16。 | (C23 起)          |

## 注解

​	若可能出现负值，则使用 `ptrdiff_t` 进行指针算术和数组索引。使用其他类型（如 int）的程序，可能会在譬如在 64 位系统上，当下标超过 [INT_MAX]({{< ref "/c/types/limits" >}}) 时，或若依赖 32 位模算术时失败。

​	只有指向同一数组中的元素（包括指向数组尾后一个位置）的指针可以相减。

​	若数组足够大（大于 [PTRDIFF_MAX]({{< ref "/c/types/limits" >}}) 个元素，但等于或小于 [SIZE_MAX]({{< ref "/c/types/limits" >}}) 个字节），则两个指针间的距离可能无法以 **ptrdiff_t** 表示，这两个指针相减的结果未定义。

​	对于短于 [PTRDIFF_MAX]({{< ref "/c/types/limits" >}}) 的 char 数组，`ptrdiff_t` 表现为 [size_t]({{< ref "/c/types/size_t" >}}) 的有符号对应类型：它能存储任何类型的数组大小，而且在大多数平台上是 `intptr_t` 的同义词。

## 可能的实现

```c
typedef typeof((int*)nullptr - (int*)nullptr) ptrdiff_t; // C23 起合法
```

## 示例

```c
#include <stddef.h>
#include <stdint.h>
#include <stdio.h>
 
int main(void)
{
    const size_t N = 100;
    int numbers[N];
 
    printf("PTRDIFF_MAX = %ld\n", PTRDIFF_MAX);
    int *p1 = &numbers[18], *p2 = &numbers[23];
    ptrdiff_t diff = p2 - p1;
    printf("p2-p1 = %td\n", diff);
}
```

可能的输出：

```txt
PTRDIFF_MAX = 9223372036854775807
p2-p1 = 5
```

## 参阅

| [size_t]({{< ref "/c/types/size_t" >}})       | [`sizeof`]({{< ref "/c/language/expressions/sizeof" >}}) 运算符返回的无符号整数类型 (typedef) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [offsetof]({{< ref "/c/types/offsetof" >}})   | 从结构体类型的起始到指定成员的字节偏移 (宏函数)              |
| **ptrdiff_t** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/ptrdiff_t)** |                                                              |
