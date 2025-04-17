+++
title = "如同规则"
date = 2025-04-11T23:28:37+08:00
weight = 130
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/as_if](https://zh.cppreference.com/w/c/language/as_if)

​	允许进行任何以及所有的不会改变程序的可观察行为的代码变换。

## 解释

​	只要维持以下各项为真，就允许 C 编译器对程序实施任何改变：

1) 在每个[序列点]({{< ref "/c/language/expressions/eval_order" >}})，所有 [volatile]({{< ref "/c/language/declarations/volatile" >}}) 对象的值均已稳定（之前的求值已完成，新求值尚未开始）。(C11 前)
1) 对 [volatile]({{< ref "/c/language/declarations/volatile" >}}) 对象的访问（读和写），严格按照它们出现的表达式的语义发生。尤其是，它们与同一线程中的其他 [volatile]({{< ref "/c/language/declarations/volatile" >}}) 访问之间[不会重排序](https://zh.cppreference.com/w/c/atomic/memory_order)。(C11 起)

2) 程序终止时，写入文件的数据与按所写代码执行严格相同。
3) 发送给交互式设备的提示文本将于程序等待输入之前显示。
4) 如果支持语用 [`#pragma STDC FENV_ACCESS`](https://zh.cppreference.com/w/c/preprocessor/impl#.E6.A0.87.E5.87.86.E8.AF.AD.E7.94.A8) 且已设为 `ON`，则对[浮点数环境](https://zh.cppreference.com/w/c/numeric/fenv)（浮点数异常和舍入模式）的改变保证会由浮点数算术运算符和函数调用观察到，如同按所写代码执行一样，不过
   - 任何不是转型和赋值的浮点数表达式，可以与表达式的类型具有不同的浮点数类型范围和精度（参见 [FLT_EVAL_METHOD]({{< ref "/c/types/limits/FLT_EVAL_METHOD" >}})），
   - 尽管有以上规定，任何浮点数表达式的中间结果，可按如同具有无穷范围和精度计算（除非 [`#pragma STDC FP_CONTRACT`](https://zh.cppreference.com/w/c/preprocessor/impl#Standard_pragmas) 为 `OFF`）。

## 注解

本节未完成 

原因：fill out similar to [cpp/language/as_if](https://zh.cppreference.com/w/cpp/language/as_if)

## 参阅

- [求值顺序]({{< ref "/c/language/expressions/eval_order" >}})

**如同规则**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/as_if)**
