+++
title = "_Static_assert"
date = 2025-04-13T11:11:15+08:00
weight = 150
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/_Static_assert](https://zh.cppreference.com/w/c/language/_Static_assert)

## 语法

| `_Static_assert` `(` *表达式* `,` *消息* `)` |      | (C11 起)(C23 弃用) |
| -------------------------------------------- | ---- | ------------------ |
| `static_assert` `(` *表达式* `,` *消息* `)`  |      | (C23 起)           |
| `_Static_assert` `(` *表达式* `)`            |      | (C23 起)(C23 弃用) |
| `static_assert` `(` *表达式* `)`             |      | (C23 起)           |

| *表达式* | -    | 任何[整数常量表达式](https://zh.cppreference.com/w/c/language/constant_expression) |
| -------- | ---- | ------------------------------------------------------------ |
| *消息*   | -    | 任何[字符串字面量](https://zh.cppreference.com/w/c/language/string_literal) |

​	此关键词亦可用作便利宏 [`static_assert`](https://zh.cppreference.com/w/c/error/static_assert)，于头文件 [`<assert.h>`](https://zh.cppreference.com/w/c/header/assert) 中提供。(C23 前)

​	`static_assert` 与 `_Static_assert` 效果相同。`_Static_assert` 是为兼容性保留的弃用拼写。实现亦可定义 `static_assert` 与/或 `_Static_assert` 为预定义宏，而 [`<assert.h>`](https://zh.cppreference.com/w/c/header/assert) 不再提供 `static_assert`。(C23 起)

## 解释

​	在编译时求值该常量表达式并将它与零比较。若它比较等于零，则发生编译错误，而编译器必须将*消息* ﻿作为错误消息的一部分显示（但不要求显示[基本字符集](https://zh.cppreference.com/w/c/language/charset)以外的字符）(C23 前)在提供*消息* ﻿时应该将它作为错误消息的一部分显示(C23 起)。

​	否则，若*表达式* ﻿不等于零，则什么都不发生；不生成代码。

## 关键词

[`_Static_assert`](https://zh.cppreference.com/w/c/keyword/_Static_assert), [`static_assert`](https://zh.cppreference.com/w/c/keyword/static_assert)

## 示例

```c
#include <assert.h> // C23 起不再需要
 
int main(void)
{
    // 测试数学是否正常工作，C23：
    static_assert((2 + 2) % 3 == 1, "Whoa dude, you knew!");
    // C23 之前的替代方案：
    _Static_assert(2 + 2 * 2 == 6, "Lucky guess!?");
 
    // 这会在编译时产生错误。
    // static_assert(sizeof(int) < sizeof(char), "Unmet condition!");
 
    constexpr int _42 = 2 * 3 * 2 * 3 + 2 * 3;
    static_assert(_42 == 42); // 可以省略消息字符串
 
    // const int _13 = 13;
    // 编译时错误 - 并非整数常量表达式：
    // static_assert(_13 == 13);
}
```

## 参阅

| [assert](https://zh.cppreference.com/w/c/error/assert)       | 若用户指定的条件非true，则异常终止程序。可以在发行版本禁用。 (宏函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `static_assert` 声明的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/static_assert) |                                                              |