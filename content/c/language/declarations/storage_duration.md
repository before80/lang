+++
title = "存储类说明符"
date = 2025-04-13T11:01:38+08:00
weight = 120
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/storage_duration](https://zh.cppreference.com/w/c/language/storage_duration)

​	指定对象和函数的*存储期（storage duration）*和*链接（linkage）*：

​	`_Thread_local`(C23 前)`thread_local`(C23 起) - 线程存储期(C11 起)

## 解释

​	存储类说明符出现于[声明]({{< ref "/c/language/declarations" >}})和[复合字面量]({{< ref "/c/language/expressions/compound_literal" >}})表达式(C23 起)中。至多可使用一个说明符，但可以将 `_Thread_local`(C23 前)[thread_local](http://zh.cppreference.com/w/c/thread/thread_local)(C23 起) 与 `static` 或 `extern` 组合以调整链接(C11 起)。存储类说明符确定其所声明的名称的两个独立属性：*存储期* ﻿与*链接*。

1) `auto` 说明符只允许用于声明于块作用域的对象（除了函数形参列表）。它指示自动存储期与无链接，也是这种声明的默认属性。
2) `register` 说明符只允许用于声明于块作用域的对象，包括函数形参列表。它指示自动存储期与无链接（即这种声明的默认属性），但另外提示优化器，若可能则将此对象的值存储于 CPU 寄存器中。无论此优化是否发生，声明为 `register` 的对象不能用作[取址运算符]({{< ref "/c/language/expressions/operator_member_access" >}})的参数，不能用 [`_Alignas`]({{< ref "/c/language/declarations/_Alignas" >}})(C23 前)[`alignas`](https://zh.cppreference.com/w/c/language/alignas)(C23 起)(C11 起)，而且 `register` 数组不能转换为指针。
3) `static` 说明符指定静态存储期（除非与 `_Thread_local` 组合）(C11 起)和内部链接（除非用于块作用域）。它能用于在文件作用域的函数，以及文件和块作用域的变量，但不能用于函数形参列表。
4) `extern` 指定静态存储期（除非与 `_Thread_local`(C23 前)[thread_local](http://zh.cppreference.com/w/c/thread/thread_local)(C23 起) 组合）(C11 起)和外部链接。它能用于文件和块作用域中的函数和对象声明（除了函数形参列表）。若 `extern` 出现在已经声明带内部链接的标识符的再声明上，则链接仍为内部。否则（若前一声明为外部、无链接或不在作用域内）链接为外部。
5) `_Thread_local`(C23 前)[thread_local](http://zh.cppreference.com/w/c/thread/thread_local)(C23 起) 指示*线程存储期*。它不能用于函数声明。若将它用在对象声明上，则它必须在同一对象的每次声明上都存在。若将它用在块作用域声明上，则必须与 `static` 或 `extern` 之一组合以决定链接。(C11 起)

​	若不提供存储类说明符，则默认为：

- 对所有函数为 `extern`
- 对在文件作用域的对象为 `extern`
- 对在块作用域的对象为 `auto`

​	对于任何用存储类说明符声明的结构体或联合体，存储期（但非链接）递归地应用到其成员。

​	在块作用域的函数声明可以使用 `extern` 或完全不使用存储类说明符。在文件作用域的函数声明可以使用 `extern` 或 `static`。

​	函数形参不能使用除 `register` 以外的存储类说明符。注意 static 在数组类型的函数形参中有特殊含义。

## 存储期

​	每个[对象]({{< ref "/c/language/basic_concepts/object" >}})都有称为*存储期* ﻿的属性，它限制对象的[生存期]({{< ref "/c/language/basic_concepts/lifetime" >}})。C 中有四种存储期：

​	*线程* ﻿存储期。存储期是创建对象的线程的整个执行过程，在启动线程时初始化存储于对象的值。每个线程拥有其自身的独立对象。若执行访问此对象的表达式的线程，不是执行其初始化的线程，则行为是实现定义的。所有声明为 `_Thread_local`(C23 前)[thread_local](http://zh.cppreference.com/w/c/thread/thread_local)(C23 起) 的对象拥有此存储期。(C11 起)

### 链接

​	链接指的是标识符（变量或函数）可从其他作用域指代的能力。若在数个作用域中声明有同一标识符的变量或函数，但不能从所有这些作用域指代它们，则会创建变量的多个实例。可识别下列几种链接：

- ***无链接***。只能从其所在的作用域指代该变量或函数。所有未声明为 `extern` 的块作用域变量都拥有此链接，所有函数形参和所有并非函数或变量的标识符也是如此。
- ***内部链接***。能从当前翻译单元的所有作用域指代该函数或变量。所有声明为 `static` 或 `constexpr`(C23 起) 的文件作用域变量都拥有此链接，所有声明为 static 的文件作用域函数也是如此（静态函数名声明仅允许出现在文件作用域）。
- ***外部链接***。能从整个程序的任何其他翻译单元指代该变量或函数。所有未声明为 `static` 或 `constexpr`(C23 起) 的文件左右变量都拥有此链接，所有未声明为 static 的文件作用域函数声明，所有块作用域函数声明，以及所有声明为 extern 的变量或函数，如果在此位置没有某个之前的带有内部链接的声明可见，就都拥有此链接。



​	若同一标识符在同一翻译单元中一同带内部和外部链接出现，则行为未定义。这在使用[试探性定义]({{< ref "/c/language/declarations/extern" >}})时有可能发生。

### 链接与库

> 本节未完成 
>
> 原因：这或许应该为 [c/language](https://zh.cppreference.com/w/c/language) 中杂项下的顶层条目？

​	带外部链接的声明常在头文件中可用，这使得所有 [#include]({{< ref "/c/language/preprocessor/include" >}}) 了该头文件的翻译单元都可以指代定义于别处的相同标识符。

​	任何出现于头文件中的带内部链接的声明，在每个包含该文件的翻译单元中产生一个分离而独立的对象。

库接口，头文件“flib.h”：

```c
#ifndef FLIB_H
#define FLIB_H
void f(void);              // 带外部链接的函数声明
extern int state;          // 带外部链接的变量声明
static const int size = 5; // 带内部链接的只读对象定义
enum { MAX = 10 };         // 常量定义
inline int sum (int a, int b) { return a + b; } // inline 函数定义
#endif // FLIB_H
```

​	库实现，源文件“flib.c”：

```c
#include "flib.h"
 
static void local_f(int s) {} // 带内部链接的定义（只用于此文件）
static int local_state;       // 带内部链接的定义（只用于此文件）
 
int state;                       // 带外部链接的定义（ main.c 使用）
void f(void) { local_f(state); } // 带外部链接的定义（ main.c 使用）
```

​	应用代码，源文件“main.c”：

```c
#include "flib.h"
 
int main(void)
{
    int x[MAX] = {size}; // 使用常量和只读变量
    state = 7;           // 修改 flib.c 中的 state
    f();                 // 调用 flib.c 中的 f()
}
```

## 关键词

[`auto`]({{< ref "/c/language/keyword/auto" >}}), [`register`]({{< ref "/c/language/keyword/register" >}}), [`static`]({{< ref "/c/language/keyword/static" >}}), [`extern`]({{< ref "/c/language/keyword/extern" >}}), [`_Thread_local`]({{< ref "/c/language/keyword/_Thread_local" >}}) [`thread_local`]({{< ref "/c/language/keyword/thread_local" >}})

## 注解

​	一般通过定义于头文件 [`<threads.h>`]({{< ref "/c/header/threads" >}}) 的便利宏 [thread_local](https://zh.cppreference.com/w/c/thread/thread_local) 使用关键词 `_Thread_local`。(C23 前)

​	C 语言文法中，[`typedef`]({{< ref "/c/language/declarations/typedef" >}}) 和 [`constexpr`](https://zh.cppreference.com/w/c/language/constexpr)(C23 起) 说明符在形式上列作存储类说明符，但并不指定存储。

​	`auto` 说明符还用于类型推断。(C23 起)

​	在文件作用域的 `const` 且非 `extern` 的名称在 C 中拥有外部链接（同所有文件作用域的默认情况），但在 C++ 中拥有内部链接。

## 示例

```c
#include <stdio.h>
#include <stdlib.h>
 
// 静态存储期
int A;
 
int main(void)
{
    printf("&A = %p\n", (void*)&A);
 
    // 自动存储期
    int A = 1;   // 隐藏全局 A
    printf("&A = %p\n", (void*)&A);
 
    // 分配存储期
    int *ptr_1 = malloc(sizeof(int));   // 开始分配存储期
    printf("address of int in allocated memory = %p\n", (void*)ptr_1);
    free(ptr_1);                        // 停止分配存储期
}
```

可能的输出：

```txt
&A = 0x600ae4
&A = 0x7ffefb064f5c
address of int in allocated memory = 0x1f28c30
```

## 参阅

存储类说明符的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/storage_duration)
