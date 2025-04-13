+++
title = "`inline` 函数说明符"
date = 2025-04-13T13:59:19+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/inline](https://zh.cppreference.com/w/c/language/inline)

声明[内联函数](https://en.wikipedia.org/wiki/inline_function)。

## 语法

| inline *函数声明* |      | (C99 起) |
| ----------------- | ---- | -------- |

## 解释

​	`inline` 说明符的目的是提示编译器做优化，譬如[函数内联](https://en.wikipedia.org/wiki/inline_expansion)，这通常要求编译方能见到函数的定义。编译器能（并且经常）就优化的目的忽略 `inline` 说明符的存在与否。

​	若编译器进行函数内联，则它会以函数体取代所有对它的调用，以避免函数调用的开销（将数据置于栈上和取得结果），这可能会生成更大的可执行文件，因为函数可能会被重复多次。结果同[仿函数宏](https://zh.cppreference.com/w/c/preprocessor/replace)，只是用于该函数的标识符和宏指代可见于定义点的定义，而不指代调用点的定义。

​	不管是否进行内联，内联函数都保证下列语义：

​	任何拥有内部链接的函数都可以声明成 `static inline` ，没有其他限制。

​	一个非 static 的内联函数不能定义一个非 const 的函数局部 static 对象，并且不能使用文件作用域的 static 对象。

```c
static int x;
 
inline void f(void)
{
    static int n = 1; // 错误：非 const 的 static 对象在非 static 的 inline 函数中
    int k = x; // 错误：非 static 的 inline 函数访问 static 变量
}
```

​	若非 static 函数声明为 `inline` ，则必须在同一翻译单元中定义它。不使用 `extern` 的内联定义不会对外部可见，而且不会阻止其他翻译单元定义同一函数。这使得 `inline` 关键词成了 `static` 外另一种在头文件定义函数的方式，可以由同一程序的多个翻译单元包含该头文件。

​	若函数在一些翻译单元中声明为 `inline` ，它就不需要在处处皆声明为 `inline` ：至多一个单元会提供常规的非 inline 非 static 函数，或是声明为 `extern inline` 的函数。称此翻译单元提供*外部定义*。为避免未定义行为，若在表达式中使用拥有外部链接的函数名，则程序中必须存在一个外部定义，见[唯一定义规则](https://zh.cppreference.com/w/c/language/extern#.E5.94.AF.E4.B8.80.E5.AE.9A.E4.B9.89.E8.A7.84.E5.88.99)。

​	内联函数的地址始终是外部定义的地址，但当以此地址进行函数调用时，调用*内联定义*（若存在于翻译单元中）还是*外部定义*是未指定的。定义于内联定义中的 static 对象与定义于外部定义中的 static 对象有别：

```c
inline const char *saddr(void) // 用于此文件内的内联定义
{
    static const char name[] = "saddr";
    return name;
}
 
int compare_name(void)
{
    return saddr() == saddr(); // 未指定行为，调用可能是外部的
}
 
extern const char *saddr(void); // 外部定义也会生成
```

​	C 程序不应依赖于调用函数的内联版本还是外部版本，否则行为未指定。

## 关键词

[`inline`](https://zh.cppreference.com/w/c/keyword/inline)

## 注解

​	`inline` 关键词是从 C++ 吸收的，但在 C++ 中，若函数声明为内联，则它必须在每一个翻译单元声明为内联，而且每一个内联函数都必须有准确相同的定义（ C 中，定义可以相异，而依赖这些差异仅导致未指定行为）。另一方面， C++ 允许非 `const` 的函数局域 `static` 对象，而且所有来自一个内联函数不同定义版本的函数局部 `static` 对象都相同，但它们在 C 中不同。

## 示例

头文件 "test.h"

```c
#ifndef TEST_H_INCLUDED
#define TEST_H_INCLUDED
 
inline int sum (int a, int b)
{
    return a + b;
}
 
#endif
```



源文件 "sum.c"

```c
#include "test.h"
 
extern inline int sum (int a, int b); // 提供外部定义
```



源文件 "test1.c"

```c
#include <stdio.h>
#include "test.h"
 
extern int f(void);
 
int main(void)
{
    printf("%d\n", sum(1, 2) + f());
}
```



源文件 "test2.c"

```c
#include "test.h"
 
int f(void)
{
    return sum(3, 4);
}
```

输出

```txt
10
```

## 参阅

**`inline` 说明符**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/inline)**