+++
title = "_Noreturn 函数说明符 (C11 起)(C23 弃用)"
date = 2025-04-13T14:02:22+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/_Noreturn](https://zh.cppreference.com/w/c/language/_Noreturn)

​	指明函数不会返回到其调用点。

## 语法

| `_Noreturn` *函数声明* |      | (C11 起)(C23 弃用) |
| ---------------------- | ---- | ------------------ |

## 解释

​	`_Noreturn` 关键词出现于函数声明中，指定函数不会由于执行到 `return` 语句或抵达函数体结尾而返回（可能通过执行 [longjmp](https://zh.cppreference.com/w/c/program/longjmp) 返回）。若声明为 `_Noreturn` 的函数返回，则行为未定义。若编译器能检测此错误，则推荐编译器予以诊断。

​	`_Noreturn` 说明符可以在同一函数声明中出现多于一次，行为与只出现一次相同。

​	此说明符通常通过便利宏 [`noreturn`](https://zh.cppreference.com/w/c/types) 使用，该宏于头文件 `<stdnoreturn.h>` 提供。(C23 起)

​	`_Noreturn` 函数说明符被弃用。应该用 `[[noreturn]]` 属性代替。宏 `noreturn` 亦被弃用。(C23 起)

## 关键词

[`_Noreturn`](https://zh.cppreference.com/w/c/keyword/_Noreturn)

## 标准库

​	下列标准库中的函数为 `noreturn`：

- [abort()](https://zh.cppreference.com/w/c/program/abort)
- [exit()](https://zh.cppreference.com/w/c/program/exit)
- [_Exit()](https://zh.cppreference.com/w/c/program/_Exit)
- [quick_exit()](https://zh.cppreference.com/w/c/program/quick_exit)
- [thrd_exit()](https://zh.cppreference.com/w/c/thread/thrd_exit)
- [longjmp()](https://zh.cppreference.com/w/c/program/longjmp)

## 示例

```c
#include <stdio.h>
#include <stdlib.h>
#include <stdnoreturn.h>
 
// 在 i <= 0 时导致未定义行为
// 在 i > 0 时退出
noreturn void exit_now(int i) // 或 _Noreturn void exit_now(int i)
{
    if (i > 0)
        exit(i);
}
 
int main(void)
{
  puts("Preparing to exit...");
  exit_now(2);
  puts("This code is never executed.");
}
```

输出：

```txt
Preparing to exit...
```

## 参阅

| `[[noreturn]]`(C23)<br />`[[_Noreturn]]`(C23)(弃用){{{notes}}} | 指定函数不会返回 (属性指示符) |
| ------------------------------------------------------------ | ----------------------------- |
| **`[[noreturn]]`** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/attributes/noreturn)** |                               |