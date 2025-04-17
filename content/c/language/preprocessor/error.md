+++
title = "诊断指令"
date = 2025-04-12T12:24:54+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/preprocessor/error](https://zh.cppreference.com/w/c/preprocessor/error)

​	显示给定的错误消息并使得程序非良构，或给定的警告消息而不影响程序的合法性(C23 起)。

## 语法

| `#error` *诊断消息*   | (1)  |          |
| --------------------- | ---- | -------- |
| `#warning` *诊断消息* | (2)  | (C23 起) |

## 解释

1) 实现在遇到 `#error` 指令后，显示消息 *诊断消息*，并令程序非良构（停止编译）。
2) 同 (1)，但不影响程序的合法性并且编译继续。

​	*诊断消息* 可由多个词组成，不必在引号中。

## 注解

​	在其于 C23 的标准化前，`#warning` 已经被许多编译器作为遵从的扩展提供。

## 示例

```c
#if __STDC__ != 1
#  error "不是遵从标准的编译器"
#endif
 
#if __STDC_VERSION__ >= 202311L
#  warning "使用标准功能特性 #warning"
#endif
 
#include <stdio.h>
int main (void)
{
    printf("所用编译器遵从 ISO C 标准！！");
}
```

可能的输出：

```txt
所用编译器遵从 ISO C 标准！！
```

## 参阅

​	**诊断指令**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/preprocessor/error)**
