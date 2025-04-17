+++
title = "标量初始化"
date = 2025-04-13T09:54:34+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/scalar_initialization](https://zh.cppreference.com/w/c/language/scalar_initialization)

​	在[初始化]({{< ref "/c/language/initialization" >}})[标量类型](https://zh.cppreference.com/w/c/language/types#.E7.B1.BB.E5.9E.8B.E7.BB.84.E5.88.AB)对象时，初始化式必须是单个表达式。

​	标量（包含布尔和枚举类型的整数类型，包含复数和虚数的浮点数类型，以及包含指向函数指针的指针类型对象）的初始化式必须是单个表达式，可选地以花括号环绕：

| `=` *表达式*         | (1)  |          |
| -------------------- | ---- | -------- |
| `=` `{` *表达式* `}` | (2)  |          |
| `=` `{` `}`          | (3)  | (C23 起) |

1,2) 求值该表达式，而其值在[如同赋值般转换]({{< ref "/c/language/expressions/conversion" >}})到对象类型后，成为被初始化对象的初值。

3)[空初始化]({{< ref "/c/language/initialization#.E7.A9.BA.E5.88.9D.E5.A7.8B.E5.8C.96" >}})对象，即对于算术或枚举类型对象初始化为数值零，或对指针类型对象初始化为空指针值。

### 注解

​	因为应用到转换到规则如同赋值，在确定 *表达式* 所转换到的类型时，忽略被声明类型上的 [`const`]({{< ref "/c/language/declarations/const" >}}) 与 [`volatile`]({{< ref "/c/language/declarations/volatile" >}}) 限定符。

​	不使用初始化式时应用的规则见[初始化]({{< ref "/c/language/initialization" >}})。

​	同所有其他初始化，在初始化静态或线程局域[存储期]({{< ref "/c/language/declarations/storage_duration" >}})的对象时，*表达式* 必须为[常量表达式]({{< ref "/c/language/expressions/constant_expression" >}})。

​	*表达式* 不能为[逗号运算符]({{< ref "/c/language/expressions/operator_other#.E9.80.97.E5.8F.B7.E8.BF.90.E7.AE.97.E7.AC.A6" >}})（除非加括号），因为顶层的逗号会被转译为下个声明符的开始。

​	在初始化浮点数类型对象时，对所有拥有自动[存储期]({{< ref "/c/language/declarations/storage_duration" >}})的对象所作的计算如同在执行时进行，并受[当前舍入](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)影响；报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的浮点数错误。对于拥有静态和线程局域存储期的对象，计算如同在编译时进行，而且不引发异常：

```c
void f(void)
{
#pragma STDC FENV_ACCESS ON
    static float v = 1.1e75; // 不引发异常：静态初始化
 
    float u[] = { 1.1e75 }; // 引发 FE_INEXACT
    float w = 1.1e75;       // 引发 FE_INEXACT
 
    double x = 1.1e75; // 可能引发 FE_INEXACT（取决于 FLT_EVAL_METHOD）
    float y = 1.1e75f; // 可能引发 FE_INEXACT（取决于 FLT_EVAL_METHOD）
 
    long double z = 1.1e75; // 不引发异常（转换是准确的）
}
```

## 示例

```c
#include <stdbool.h>
int main(void)
{
    _Bool b = true;
    const double d = 3.14;
    int k = 3.15; // 从 double 转换到 int
    int n = {12}, // 可选地花括号
       *p = &n,   // 对自动对象，非常量表达式 OK
       (*fp)(void) = main;
    enum {RED, BLUE} e = RED; // 枚举亦是标量类型
}
```
