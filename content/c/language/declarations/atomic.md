+++
title = "原子类型"
date = 2025-04-13T10:45:05+08:00
weight = 70
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/atomic](https://zh.cppreference.com/w/c/language/atomic)

## 语法

| `_Atomic` `(` *类型名* `)` | (1)  | (C11 起) |
| -------------------------- | ---- | -------- |
| `_Atomic` *类型名*         | (2)  | (C11 起) |

1) 用作类型说明符；指代新的原子类型
2) 用作类型限定符；指代*类型名* ﻿的原子版本。在此用法中，它可以与 [`const`]({{< ref "/c/language/declarations/const" >}})、[`volatile`]({{< ref "/c/language/declarations/volatile" >}}) 及 [`restrict`]({{< ref "/c/language/declarations/restrict" >}}) 混合使用，但不同于其他限定符，*类型名* ﻿的原子版本可能拥有不同的大小、对齐以及对象表示。

| *类型名* | -    | 除数组或函数外的任意类型。对于 (1)，*类型名* ﻿亦不能为原子或被 cvr 限定 |
| -------- | ---- | ------------------------------------------------------------ |

​	头文件 [`<stdatomic.h>`]({{< ref "/c/header/stdatomic" >}}) 定义了[许多便利类型别名](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C)，从 [`atomic_bool`](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C) 到 [`atomic_uintmax_t`](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C)，它们简化了此关键词与内建及库类型的组合使用。

```c
_Atomic const int* p1;  // p 是指向 atomic const int 的指针
const atomic_int* p2;   // 同上
const _Atomic(int)* p3; // 同上
```

​	若编译器定义了宏常量 `__STDC_NO_ATOMICS__`，则不提供关键词 `_Atomic`。

## 解释

​	原子类型的对象是仅有的免除[数据竞争]({{< ref "/c/language/basic_concepts/memory_model" >}})的对象；即它们可以被两个线程共时修改，或被一个修改并被另一个读取。

​	每个原子对象都拥有关联于其自身的*修改顺序*，即对该对象的修改的全序。若从某个线程的视角来看，对于某原子对象 `M` 的修改 `A` [发生早于](https://zh.cppreference.com/w/c/atomic/memory_order)同一原子对象 `M` 的修改 `B`，则在 `M` 的修改顺序中 `A` 出现早于 `B`。

​	注意即使每个原子对象都有其自身的修改顺序，却并无单独的全序；不同线程可能会观测到不同原子对象有相异的修改顺序。

​	对于所有原子运算，保证有四种连贯种类：

1. 写写连贯：若原子对象 `M` 的修改操作 `A` *发生早于* `M` 的修改操作 `B`，则 `M` 的修改顺序中 `A` 出现早于 `B`。
2. 读读连贯：若原子对象 `M` 的值计算 `A` *发生早于* `M` 的值计算 `B`，且从 `M` 上的副效应 `X` 求得 `A` 值，则 `B` 所计算得的值要么是 `X` 所存储的值，要么是 `M` 上的副效应 `Y` 所存储的值，其中 `Y` 在 `M` 的修改顺序中出现晚于 `X`。
3. 读写连贯：若原子对象 `M` 的值计算 `A` *发生早于* `M` 上的操作 `B`，则从 `M` 上的副效应 `X` 求得 `A` 值，这里 `X` 在 `M` 的修改顺序中出现早于 `B`。
4. 写读连贯：若在原子对象 `M` 上的副效应 `X` *发生早于* `M` 的值计算 `B`，则求值 `B` 从 `X`，或从在 `M` 的修改顺序中出现晚于 `X` 的副效应 `Y` 求得其值。

​	一些原子运算亦是同步操作：它们可以拥有附加的释放语义、获取语义，或顺序一致语义。见 [memory_order](https://zh.cppreference.com/w/c/atomic/memory_order)。

​	内建的[自增减运算符]({{< ref "/c/language/expressions/operator_incdec" >}})和[复合赋值运算符]({{< ref "/c/language/expressions/operator_assignment" >}})是拥有完全序列一致顺序（如同用 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order)）的读-修改-写操作。若想要较不严格的同步语义，则可以用[标准库函数](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C)替代。

​	原子属性仅对[左值表达式]({{< ref "/c/language/expressions/value_category" >}})有意义。左值到右值转换（模仿从原子区域到 CPU 寄存器的内存读取）会把原子性及其他限定符剥去。

> 本节未完成 
>
> 原因：更多和 `memory_order` 及原子库页面的综述互动

## 注解

​	访问原子结构体/联合体的成员是未定义行为。

​	库类型 [sig_atomic_t](http://zh.cppreference.com/w/c/program/sig_atomic_t) 不提供线程间同步或内存定序，仅提供原子性。

[`volatile`]({{< ref "/c/language/declarations/volatile" >}}) 类型不提供线程间同步、内存定序或原子性。

​	推荐实现确保对于每个可能的类型 `T`，C 中 `_Atomic(T)` 的表示与 C++ 中 `std::atomic<T>` 的相同。用于确保原子性与内存顺序的机制应该兼容。

## 关键词

[`_Atomic`]({{< ref "/c/language/keyword/_Atomic" >}})

## 示例

```c
#include <stdatomic.h>
#include <stdio.h>
#include <threads.h>
 
atomic_int acnt;
int cnt;
 
int f(void* thr_data)
{
    for (int n = 0; n < 1000; ++n)
    {
        ++cnt;
        ++acnt;
        // 对于此例，宽松内存顺序是足够的，例如
        // atomic_fetch_add_explicit(&acnt, 1, memory_order_relaxed);
    }
    return 0;
}
 
int main(void)
{
    thrd_t thr[10];
    for (int n = 0; n < 10; ++n)
        thrd_create(&thr[n], f, NULL);
    for (int n = 0; n < 10; ++n)
        thrd_join(thr[n], NULL);
 
    printf("原子计数器为 %u\n", acnt);
    printf("非原子计数器为 %u\n", cnt);
}
```

​	可能的输出：

```txt
原子计数器为 10000
非原子计数器为 8644
```

## 参阅

| [并发支持库](https://zh.cppreference.com/w/c/thread)         |
| ------------------------------------------------------------ |
| atomic 的 [C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic) |
