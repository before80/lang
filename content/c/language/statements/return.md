+++
title = "return 语句"
date = 2025-04-12T16:25:49+08:00
weight = 90
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/return](https://zh.cppreference.com/w/c/language/return)

​	终止当前函数并返回指定值给调用方函数。

## 语法

| *属性说明符序列*(可选) `return` *表达式* `;` | (1)  |
| -------------------------------------------- | ---- |
| *属性说明符序列*(可选) `return` `;`          | (2)  |

| *表达式*         | -    | 用于初始化函数返回值的表达式                                 |
| ---------------- | ---- | ------------------------------------------------------------ |
| *属性说明符序列* | -    | (C23)可选的[属性](https://zh.cppreference.com/w/c/language/attributes)列表，应用到 `return` 语句 |

## 解释

1) 求值 *表达式*，终止当前函数，并返回 *表达式* 的结果给调用方（该返回值成为函数调用表达式的值）。仅对函数返回类型非 void 的情形合法。
2) 终止当前函数。仅对函数返回类型为 void 的情形合法。

​	若 *表达式* 的类型与函数的返回类型不同，则如同赋值给该函数返回类型的对象一般对其值进行[转换](https://zh.cppreference.com/w/c/language/conversion)，但容许对象表示间有所重叠：

```c
struct s { double i; } f(void); // 函数返回 struct s
union { struct { int f1; struct s f2; } u1;
        struct { struct s f3; int f4; } u2; } g;
struct s f(void)
{
    return g.u1.f2;
}
int main(void)
{
// g.u2.f3 = g.u1.f2; // 未定义行为（赋值中重叠）
   g.u2.f3 = f();     // 良好定义
}
```

​	若返回类型是实浮点类型，则结果可能拥有比新类型所隐含者[更大的范围和精度](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD)的表示。

​	抵达返回 void 的函数的末尾等价于 return;。若函数结果用于表达式，则抵达任何其他返回值的函数的结尾为未定义行为（允许舍弃这种返回值）。对于 `main`，见 [`main` 函数](https://zh.cppreference.com/w/c/language/main_function)。

​	在[不返回函数](https://zh.cppreference.com/w/c/language/_Noreturn)中执行 `return` 语句是未定义行为。(C11 起)

## 关键词

[`return`](https://zh.cppreference.com/w/c/keyword/return)

## 示例

> 本节未完成 
>
> 原因：改进

```c
#include <stdio.h>
 
void fa(int i)
{
    if (i == 2)
       return;
    printf("fa():   %d\n", i);
} // 隐含 return;
 
int fb(int i)
{
    if (i > 4)
       return 4;
    printf("fb():   %d\n", i);
    return 2;
}
 
int main(void)
{
    fa(2);
    fa(1);
    int i = fb(5);   // 返回值 4 用于初始化 i
    i = fb(i);       // 返回值 2 用作赋值的右运算数
    printf("main(): %d\n", i);
}
```

输出：

```txt
fa():   1
fb():   4
main(): 2
```

## 参阅

​	**`return` 语句**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/return)**