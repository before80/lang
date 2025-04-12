+++
title = "_Alignof (C11 起)(C23 弃用), alignof (C23 起) 运算符"
date = 2025-04-12T21:30:00+08:00
weight = 230
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/_Alignof](https://zh.cppreference.com/w/c/language/_Alignof)

查询其运算数类型的对齐要求。

## 语法

| `_Alignof(` *类型名* `)` |      | (C11 起)(C23 弃用) |
| ------------------------ | ---- | ------------------ |
| `alignof(` *类型名* `)`  |      | (C23 起)           |

| 通常通过便利宏 [`alignof`](https://zh.cppreference.com/w/c/types) 使用此运算符，该宏于头文件 `stdalign.h` 提供。 | (C23 前) |
| ------------------------------------------------------------ | -------- |
|                                                              |          |

## 解释

返回*类型名* ﻿ 所[指名](https://zh.cppreference.com/w/c/language/types#.E7.B1.BB.E5.9E.8B.E5.90.8D)的类型的[对齐要求](https://zh.cppreference.com/w/c/language/object#.E5.AF.B9.E9.BD.90)。若*类型名* ﻿为数组类型，则结果为数组元素的对齐要求。*类型名* ﻿不能为函数类型或不完整类型。

结果是 [size_t](https://zh.cppreference.com/w/c/types/size_t) 类型整数常量。

不求值其运算数（故用作运算数的外部标识符不必有定义）。

若*类型名* ﻿为 [VLA](https://zh.cppreference.com/w/c/language/array) 类型，则不求值其大小表达式。

## 注解

作为非标准扩展，一些 C 编译器允许把 `_Alignof`(C23 前)`alignof`(C23 起) 用于表达式。

## 关键词

[`alignof`](https://zh.cppreference.com/w/c/keyword/alignof), [`_Alignof`](https://zh.cppreference.com/w/c/keyword/_Alignof)

## 示例

```
#include <stdalign.h>
#include <stddef.h>
#include <stdio.h>
 
int main(void)
{
    printf("Alignment of char = %zu\n", alignof(char));
    printf("Alignment of max_align_t = %zu\n", alignof(max_align_t));
    printf("alignof(float[10]) = %zu\n", alignof(float[10]));
    printf("alignof(struct{char c; int n;}) = %zu\n",
            alignof(struct {char c; int n;}));    
}
```

可能的输出：

```
Alignment of char = 1
Alignment of max_align_t = 16
alignof(float[10]) = 4
alignof(struct{char c; int n;}) = 4
```

### 缺陷报告

下列更改行为的缺陷报告追溯地应用于以前出版的 C 标准。

| 缺陷报告                                                     | 应用于 | 出版时的行为                                      | 正确行为 |
| ------------------------------------------------------------ | ------ | ------------------------------------------------- | -------- |
| [DR 494](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_494) | C11    | 未指明是否求值 `_Alignof` 中的 VLA 中的大小表达式 | 不求值它 |

## 参阅

| [max_align_t](https://zh.cppreference.com/w/c/types/max_align_t)(C11) | 对齐要求不小于任何其他标量类型的类型 (typedef) |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [`_Alignas`](https://zh.cppreference.com/w/c/language/_Alignas)(C23 前)[`alignas`](https://zh.cppreference.com/w/c/language/_Alignas)(C23 起) | 设置对象的对齐要求 (说明符)                    |
| **`alignof` 运算符**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/alignof)** |                                                |