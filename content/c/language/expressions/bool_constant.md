+++
title = "预定义布尔常量"
date = 2025-04-12T20:23:19+08:00
weight = 100
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/bool_constant](https://zh.cppreference.com/w/c/language/bool_constant)

## 语法

| `true`  | (1)  | (C23 起) |
| ------- | ---- | -------- |
| `false` | (2)  | (C23 起) |

## 解释

​	关键词 `true` 与 `false` 表示预定义常量。它们是 [`bool`](https://zh.cppreference.com/w/c/language/types) 类型的[非左值]({{< ref "/c/language/expressions/value_category#.E9.9D.9E.E5.B7.A6.E5.80.BC.E5.AF.B9.E8.B1.A1.E8.A1.A8.E8.BE.BE.E5.BC.8F" >}})。

## 注解

​	从 bool 到其他类型的转换见[整数转换]({{< ref "/c/language/expressions/conversion#.E6.95.B4.E6.95.B0.E8.BD.AC.E6.8D.A2" >}})，从其他类型到 bool 的转换见[布尔转换]({{< ref "/c/language/expressions/conversion#.E5.B8.83.E5.B0.94.E8.BD.AC.E6.8D.A2" >}})。

​	C23 前，`true` 与 `false` 实现为 [`<stdbool.h>`]({{< ref "/c/header/stdbool" >}}) 中提供的宏。实现亦可在 C23 中处于兼容性而将 `bool`、`true` 及 `false` 定义为预定义宏。

## 示例

```c
#include <assert.h>
 
int main()
{
     assert(true == 1 && 0 == false);
}
```



## 参阅

布尔字面量的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/bool_literal)
