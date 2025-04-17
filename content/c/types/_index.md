+++
title = "类型支持"
date = 2025-04-14T15:41:59+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/types](https://zh.cppreference.com/w/c/types)

​	参阅[类型系统综述](https://zh.cppreference.com/w/c/language/types)及[语言定义的算术类型]({{< ref "/c/language/basic_concepts/arithmetic_types" >}})。

## 基本类型

### 额外基本类型及便利宏

| 在标头 `<stddef.h>` 定义                                     |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [size_t]({{< ref "/c/types/size_t" >}})       | [`sizeof`]({{< ref "/c/language/expressions/sizeof" >}}) 运算符返回的无符号整数类型 (typedef) |
| [ptrdiff_t]({{< ref "/c/types/ptrdiff_t" >}}) | 两个指针相减返回的有符号整数类型 (typedef)                   |
| [nullptr_t]({{< ref "/c/types/nullptr_t" >}})(C23) | 预定义空指针常量 [`nullptr`]({{< ref "/c/language/expressions/nullptr" >}}) 的类型 (typedef) |
| [NULL]({{< ref "/c/types/NULL" >}})           | 实现定义的空指针常量 (宏常量)                                |
| [max_align_t]({{< ref "/c/types/max_align_t" >}})(C11) | 对齐要求不小于任何其他标量类型的类型 (typedef)               |
| [offsetof]({{< ref "/c/types/offsetof" >}})   | 从结构体类型的起始到指定成员的字节偏移 (宏函数)              |
| 在标头 `<stdbool.h>` 定义                                    |                                                              |
| bool(C99)(C23 移除)                                          | 便利宏，展开成 [`_Bool`]({{< ref "/c/language/keyword/_Bool" >}}) (关键词宏) |
| true(C99)(C23 移除)                                          | 展开成整数常量 1 (宏常量)                                    |
| false(C99)(C23 移除)                                         | 展开成整数常量 0 (宏常量)                                    |
| `__bool_true_false_are_defined`(C99)(C23 弃用)               | 展开成整数常量 1 (宏常量)                                    |
| 在标头 `<stdalign.h>` 定义                                   |                                                              |
| alignas(C11)(C23 移除)                                       | 便利宏，展开成关键词 [`_Alignas`]({{< ref "/c/language/keyword/_Alignas" >}}) (关键词宏) |
| alignof(C11)(C23 移除)                                       | 便利宏，展开成关键词 [`_Alignof`]({{< ref "/c/language/keyword/_Alignof" >}}) (关键词宏) |
| `__alignas_is_defined`(C11)(C23 移除)                        | 展开成整数常量 1 (宏常量)                                    |
| `__alignof_is_defined`(C11)(C23 移除)                        | 展开成整数常量 1 (宏常量)                                    |
| 在标头 `<stdnoreturn.h>` 定义                                |                                                              |
| noreturn(C11)(C23 弃用)                                      | 便利宏，展开成 [`_Noreturn`]({{< ref "/c/language/keyword/_Noreturn" >}}) (关键词宏) |

### 定宽整数类型

​	[定宽整数类型]({{< ref "/c/types/integer" >}}) (C99 起)

### 数值极限

​	[数值极限]({{< ref "/c/types/limits" >}})

## 注解

​	`true` 与 `false` 的类型为 `int` 而非 `_Bool`。程序可以解除定义，并且可以在之后重新定义宏 bool、true 与 false。然而这种能力是一项弃用的特性。(C99 起) (C23 前)

​	`true` 与 `false` 的类型为 `bool`。`bool`、`_Bool`、`true` 或 `false` 的任何一个是否实现为预定义宏是未指定的。若 `bool`、`true` 或 `false`（但不含 `_Bool`）被定义为预定义宏，则程序可以解除定义，并且可以在之后重新定义它。(C23 起)

## 示例

```c
#include <stdalign.h>
#include <stdbool.h>
#include <stdio.h>
 
int main(void)
{
    printf("%d %d %d\n", true && false, true || false, !false);
    printf("%d %d\n", true ^ true, true + true);
    printf("%zu\n", alignof(short));
}
```

可能的输出：

```txt
0 1 1
0 2
2
```
