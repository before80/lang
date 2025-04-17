+++
title = "_Alignas (C11 起)(C23 弃用), alignas (C23 起)"
date = 2025-04-13T10:59:07+08:00
weight = 110
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/_Alignas](https://zh.cppreference.com/w/c/language/_Alignas)

​	出现于[声明]({{< ref "/c/language/declarations" >}})语法中，作为修改所声明对象的[对齐要求]({{< ref "/c/language/basic_concepts/object#.E5.AF.B9.E9.BD.90" >}})的类型说明符。

## 语法

| `_Alignas` `(` *表达式* `)` | (1)  | (C11 起) |
| --------------------------- | ---- | -------- |
| `alignas` `(` *表达式* `)`  | (2)  | (C23 起) |
| `_Alignas` `(` *类型* `)`   | (3)  | (C11 起) |
| `alignas` `(` *类型* `)`    | (4)  | (C23 起) |

| *表达式* | -    | 任何值为合法[对齐]({{< ref "/c/language/basic_concepts/object#.E5.AF.B9.E9.BD.90" >}})或零的[整数常量表达式]({{< ref "/c/language/expressions/constant_expression" >}}) |
| -------- | ---- | ------------------------------------------------------------ |
| *类型*   | -    | 任何[类型名称](https://zh.cppreference.com/w/c/language/types#.E7.B1.BB.E5.9E.8B.E5.90.8D) |

​	关键词 `_Alignas` 亦用作便利宏 [`alignas`]({{< ref "/c/types" >}})，于头文件 `<stdalign.h>` 提供。(C23 前)

## 解释

​	`_Alignas`(C23 前)`alignas`(C23 起) 说明符只能在声明不是[位域]({{< ref "/c/language/declarations/bit_field" >}})，且不拥有 [register]({{< ref "/c/language/declarations/storage_duration" >}}) 存储类的对象时使用。它不能用于函数参数声明，亦不能用于 `typedef`。

​	用于声明时，设置被声明对象的[对齐要求]({{< ref "/c/language/basic_concepts/object#.E5.AF.B9.E9.BD.90" >}})为：

1,2) *表达式* ﻿的结果，除非它是零

3,4) *类型* ﻿的对齐要求，即设置为 `_Alignof(type)`(C23 前)`alignof(type)`(C23 起)

​	除非这会减弱该类型自然拥有的对齐。

​	若*表达式* ﻿求值为零，则此指定符无效果。

​	多个 `_Alignas`(C23 前)`alignas`(C23 起) 说明符出现于同一个声明中时，使用最严格者。

​	`_Alignas`(C23 前)`alignas`(C23 起) 说明符只需要出现于对象[定义]({{< ref "/c/language/declarations#.E5.AE.9A.E4.B9.89" >}})中，但若有任何声明使用了 `_Alignas`(C23 前)`alignas`(C23 起)，则它所说明的对齐必须与其定义上的 `_Alignas`(C23 前)`alignas`(C23 起) 相同。若不同的翻译单元为同一对象说明不同对齐，则行为未定义。

## 注解

​	C++ 中，`alignas` 说明符亦可应用于声明 `class`/`struct`/`union` 类型以及枚举。这在 C 中不受支持，但可通过在成员声明中使用 `_Alignas`(C23 前)`alignas`(C23 起) 来控制 `struct` 类型的对齐。

## 关键词

[`alignas`]({{< ref "/c/language/keyword/alignas" >}}), [`_Alignas`]({{< ref "/c/language/keyword/_Alignas" >}})

## 示例

```c
#include <stdalign.h>
#include <stdio.h>
 
//  每一个 struct sse_t 类型的对象会在 16 字节边界对齐
// （注意：需要支持 DR 444 ）
struct sse_t
{
  alignas(16) float sse_data[4];
};
 
// 这种 struct data 的每一个对象都会在 128 字节边界对齐
struct data {
  char x;
  alignas(128) char cacheline[128]; // 过对齐的 char 数组对象，
                                    // 不是过对齐的 char 对象的数组
};
 
int main(void)
{
    printf("sizeof(data) = %zu (1 byte + 127 bytes padding + 128-byte array)\n",
           sizeof(struct data));
 
    printf("alignment of sse_t is %zu\n", alignof(struct sse_t));
 
    alignas(2048) struct data d; // 此 struct data 的实例会更严格地对齐
    (void)d; // 抑制 "maybe unused" 警告
}
```

输出：

```txt
sizeof(data) = 256 (1 byte + 127 bytes padding + 128-byte array)
alignment of sse_t is 16
```

## 缺陷报告

​	下列更改行为的缺陷报告追溯地应用于以前出版的 C 标准。

| 缺陷报告                                                     | 应用于 | 出版时的行为                          | 正确行为 |
| ------------------------------------------------------------ | ------ | ------------------------------------- | -------- |
| [DR 444](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_444) | C11    | 结构体与联合体成员中不允许 `_Alignas` | 允许     |

## 参阅

| [max_align_t]({{< ref "/c/types/max_align_t" >}})(C11) | 对齐要求不小于任何其他标量类型的类型 (typedef) |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [`_Alignof`]({{< ref "/c/language/expressions/_Alignof" >}})(C23 前)[`alignof`]({{< ref "/c/language/expressions/_Alignof" >}})(C23 起) | 查询对象的对齐要求 (运算符)                    |
| **`alignas` 说明符**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/alignas)** |                                                |
