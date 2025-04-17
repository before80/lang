+++
title = "位域"
date = 2025-04-13T10:38:10+08:00
weight = 60
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/bit_field](https://zh.cppreference.com/w/c/language/bit_field)

​	声明带有明确宽度的成员，按位数计。相邻的位域成员可能被打包，共享和分散到各个单独的字节。

​	位域声明，是使用下列[声明符]({{< ref "/c/language/declarations" >}})的[结构体]({{< ref "/c/language/declarations/struct" >}})或[联合体]({{< ref "/c/language/declarations/union" >}})的成员声明：

*标识符*(可选) `:` *宽度*

| *标识符* | -    | 正在声明的位域名称。名称是可选的：无名位域引入一个指定的填充位数 |
| -------- | ---- | ------------------------------------------------------------ |
| *宽度*   | -    | 一个拥有大于或等于零，且小于或等于底层类型位数的整数[常量表达式]({{< ref "/c/language/expressions/constant_expression" >}})。大于零时，此为此位域将占据的位数。零值仅允许用于无名位域，并拥有特殊含义：它指定结构体定义中的下个位域会从分配单元边界开始。 |

## 解释

​	位域可以拥有以下类型之一（可为 [const]({{< ref "/c/language/declarations/const" >}}) 或 [volatile]({{< ref "/c/language/declarations/volatile" >}}) 限定）：

- `unsigned int`，用于无符号位域（例如，`unsigned int b : 3;` 的范围是 `[0, 7]` ）
- `signed int`，用于有符号位域（`signed int b : 3;` 的范围是 `[-4, 3]` ）
- `int`，用于拥有实现定义符号性的位域（注意这与关键词 int 在所有其他地方的含义都不同，它们都表示“`signed int`”）。例如，`int b : 3;` 可能拥有 `[0, 7]` 或 `[-4, 3]` 范围的值。
- `_Bool`，对于单个位的位域（例如，`bool x : 1`; 的范围是 `[0, 1]`），从它转换和转换为它的[隐式转换]({{< ref "/c/language/expressions/conversion" >}})遵循布尔转换规则。(C99 起)
- 位精确整数类型（例如，`_BitInt(5) : 4`; 的范围是 `[-8, 7]` 而 `unsigned _BitInt(5) : 4`; 的范围是 `[0, 15]`）。(C23 起)

​	可接受额外的实现定义类型。位域是否可以拥有[原子]({{< ref "/c/language/declarations/atomic" >}})类型也是实现定义的。(C11 起)位域中的位数（*宽度*）限制其所能保有的值域：

```c
#include <stdio.h>
 
struct S
{
    // 三位无符号位域，
    // 允许值为 0..7
    unsigned int b : 3;
};
 
int main(void)
{
    struct S s = {7};
    ++s.b; // 无符号溢出
    printf("%d\n", s.b); // 输出： 0
}
```

​	允许将多个相邻位域打包在一起（通常如此）：

```c
#include <stdio.h>
 
struct S
{
    // 通常将占用 4 字节：
    // 5 位： b1 的值
    // 11 位：未使用
    // 6 位： b2 的值
    // 2 位： b3 的值
    // 8 位：未使用
    unsigned b1 : 5, : 11, b2 : 6, b3 : 2;
};
 
int main(void)
{
    printf("%zu\n", sizeof(struct S)); // 通常打印 4
}
```

​	拥有零*宽度* ﻿的特殊*无名位域* ﻿打破填充：它指定下个位域在始于下个分配单元的起点：

```c
#include <stdio.h>
 
struct S
{
    // 通常将占用 8 字节
    // 5 位： b1 的值
    // 27 位：未使用
    // 6 位： b2 的值
    // 15 位： b3 的值
    // 11 位：未使用
    unsigned b1 : 5;
    unsigned    : 0; // 开始新的 unsigned int
    unsigned b2 : 6;
    unsigned b3 : 15;
};
 
int main(void)
{
    printf("%zu\n", sizeof(struct S)); // 通常打印 8
}
```

​	因为位域不必在字节的起点开始，故不能取位域的地址。不可能有指向位域的指针。不能对位域使用 [`sizeof`]({{< ref "/c/language/expressions/sizeof" >}}) 和 `_Alignas`(C11 起)(C23 前)`alignas`(C23 起)(C11 起)。

## 注解

​	位域的下列用法导致*未定义行为*：

- 在位域上调用 [offsetof]({{< ref "/c/types/offsetof" >}})。

​	位域的下列属性*未指定*：

- 保有位域的分配单元的对齐。

​	位域的下列属性为*实现定义*：

- `int` 类型的位域被当做有符号或无符号。
- 是否容许除 `int`、`signed int`、`unsigned int`、`_Bool`(C99 起) 和（可能 `unsigned` 的）`_BitInt(N)`(C23 起) 类型的位域。
- 是否容许原子类型的位域。(C11 起)

- 位域是否能越过分配单元边界。
- 分配单元内位域的顺序（一些平台上位域从左往右打包，其他平台上是从右往左）。

​	尽管 `_Bool` 的对象表示的位数至少为 [CHAR_BIT]({{< ref "/c/types/limits" >}})，`_Bool` 类型位域的*宽度* ﻿不能大于 1。(C99 起)

​	C++ 编程语言中，位域的宽度能超出底层类型，并且 int 类型的位域始终为有符号。

## 参阅

位域的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/bit_field)
