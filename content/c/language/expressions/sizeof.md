+++
title = "sizeof 运算符"
date = 2025-04-12T21:28:42+08:00
weight = 220
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/sizeof](https://zh.cppreference.com/w/c/language/sizeof)

​	查询对象或类型的大小。

​	在必须知道对象实际大小时使用。

## 语法

| `sizeof(` *类型* `)` | (1)  |      |
| -------------------- | ---- | ---- |
| `sizeof` *表达式*    | (2)  |      |

​	两个版本都返回 [size_t](https://zh.cppreference.com/w/c/types/size_t) 类型值。

## 解释

1) 返回 *类型* 的[对象表示](https://zh.cppreference.com/w/c/language/object#.E5.AF.B9.E8.B1.A1.E8.A1.A8.E7.A4.BA)的字节大小。
2) 返回 *表达式* 类型的对象表示的字节大小。不应用隐式转换到 *表达式*。

## 注意

​	取决于计算机架构，[字节](https://en.wikipedia.org/wiki/byte)可能由 8 或更多位构成，准确数量作为 [CHAR_BIT](https://zh.cppreference.com/w/c/types/limits) 提供。

​	`sizeof(char)`、`sizeof(signed char)` 和 `sizeof(unsigned char)` 始终返回 1。

`sizeof` 不能用于函数类型、不完整类型（含void）或[位域](https://zh.cppreference.com/w/c/language/bit_field)左值。

​	应用 `sizeof` 到 [结构体](https://zh.cppreference.com/w/c/language/struct)或[联合体](https://zh.cppreference.com/w/c/language/union)类型运算数时，结果是这种对象中的总字节数，包含内部和尾随填充。尾随填充使得若对象在数组中，则此数组中下个元素的对齐要求会得到满足，换言之，`sizeof(T)` 返回 T[] 数组中元素的大小。

​	若 *类型* 为 [VLA](https://zh.cppreference.com/w/c/language/array) 类型，而更改其表达式的值不影响 `sizeof` 的结果，则不指定是否求值该大小表达式。(C99 起)

​	除非 *表达式* 为 [VLA](https://zh.cppreference.com/w/c/language/array)，(C99 起)不求值 *表达式* 且 `sizeof` 运算符能在整数[常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)中使用。

​	若 *表达式* 的类型为[非常量长度数组](https://zh.cppreference.com/w/c/language/array)类型，则求值 *表达式*，并在运行时计算其所求值的数组大小。(C99 起)

​	任何[数组](https://zh.cppreference.com/w/c/language/array) a ，包含 VLA (C99 起)的元素数可用表达式 `sizeof a / sizeof a[0]` 确定。注意若 a 拥有指针类型（例如在函数形参类型调整的数组到指针转换后），此表达式会简单地将指针类型中的字节数除以被指向类型中的字节数。

## 关键词

[`sizeof`](https://zh.cppreference.com/w/c/keyword/sizeof)

## 示例

​	示例输出对应拥有 64 位指针和 32 位 int 的平台

```c
#include <stdio.h>
 
int main(void)
{
    short x;
    // 类型参数：
    printf("sizeof(float)          = %zu\n", sizeof(float));
    printf("sizeof(void(*)(void))  = %zu\n", sizeof(void(*)(void)));
    printf("sizeof(char[10])       = %zu\n", sizeof(char[10]));
//  printf("sizeof(void(void))     = %zu\n", sizeof(void(void))); // 错误：函数类型
//  printf("sizeof(char[])         = %zu\n", sizeof(char[])); // 错误：不完整类型
 
    // 表达式参数：
    printf("sizeof 'a'             = %zu\n", sizeof 'a'); // 'a' 的类型为 int
//  printf("sizeof main            = %zu\n", sizeof main); // 错误：函数类型
    printf("sizeof &main           = %zu\n", sizeof &main);
    printf("sizeof \"hello\"         = %zu\n", sizeof "hello"); // 类型为 char[6]
    printf("sizeof x               = %zu\n", sizeof x);   // x 的类型为 short
    printf("sizeof (x+1)           = %zu\n", sizeof(x+1)); // x+1 的类型为 int
}
```

可能的输出：

```txt
sizeof(float)          = 4
sizeof(void(*)(void))  = 8
sizeof(char[10])       = 10
sizeof 'a'             = 4
sizeof &main           = 8
sizeof "hello"         = 6
sizeof x               = 2
sizeof (x+1)           = 4
```

## 参阅

`sizeof` 运算符的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/sizeof)