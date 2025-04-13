+++
title = "volatile 类型限定符"
date = 2025-04-13T10:51:51+08:00
weight = 90
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/volatile](https://zh.cppreference.com/w/c/language/volatile)

​	C [类型系统](https://zh.cppreference.com/w/c/language/type)中每一个独立的类型都有数个该类型的*限定* ﻿版本，对应 [`const`](https://zh.cppreference.com/w/c/language/const)、`volatile` 及对于指向对象指针的 [`restrict`](https://zh.cppreference.com/w/c/language/restrict) 限定符中的一个、两个或全部三个。此页面描述 `volatile` 限定符的效果。

​	每一个通过对 volatile 限定类型左值表达式的访问（读与写），对于优化意图都认作可观察副效应，从而严格按照抽象机器的规则求值（即所有写入会在下一个定序点之前的某时完成）。这表明在单个执行线程内，volatile 访问不能被优化掉，亦不能与另一个被[定序点](https://zh.cppreference.com/w/c/language/eval_order)分隔了 volatile 访问的可观察副效应之间进行重排。

​	从非 volatile 值到 volatile 值的转换没有效果。欲使用 volatile 语义访问非 volatile 对象，必须先将其地址转换成指向 volatile 类型的指针，再通过该指针访问该对象。

​	任何通过非 volatile 左值结果，对拥有 volatile 限定类型的对象尝试读或写会导致未定义行为：

```c
volatile int n = 1; // volatile 限定类型的对象
int* p = (int*)&n;
int val = *p; // 未定义行为
```

​	volatile 限定的结构体或联合体类型，其成员会获取其所属类型的限定（当通过 `.` 或 `->` 运算符时）：

```c
struct s { int i; const int ci; } s;
// s.i 类型是 int，s.ci 的类型是 const int
volatile struct s vs;
// vs.i 和 vs.ci 的类型各是 volatile int 和 const volatile int
```

​	若以 volatile 类型限定符声明数组类型（通过使用 [`typedef`](https://zh.cppreference.com/w/c/language/typedef)），则数组类型无 volatile 限定，但其元素类型有。(C23 前)

​	始终认为数组类型与其元素类型同等地拥有 volatile 限定。(C23 起)


```c
typedef int A[2][3];
volatile A a = {{4, 5, 6}, {7, 8, 9}}; // volatile int 的数组的数组
int* pi = a[0]; // 错误：a[0] 拥有 volatile int* 类型
void *unqual_ptr = a; // C23 前 OK；C23 起错误
// 注：clang 即使在 C89-C17 模式也应用 C++/C23 中的规则
```

​	若函数类型声明具有 volatile 类型限定（通过使用 [`typedef`](https://zh.cppreference.com/w/c/language/typedef)），则行为未定义。

​	在函数声明中，关键词 `volatile` 可以出现于用以声明数组类型的函数形参的方括号内。它对数组所转换得的指针类型赋予限定。下列两个声明声明同一函数：(C99 起)

```c
void f(double x[volatile], const double y[volatile]);
void f(double * volatile x, const double * volatile y);
```

​	指向非 volatile 类型的指针可以隐式转换成指向同一或[兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)类型的 volatile 限定版本的指针。逆向转换需要使用转换表达式进行。

```c
int* p = 0;
volatile int* vp = p; // OK：添加限定符（int 到 volatile int）
p = vp; // 错误：丢弃限定符（volatile int 到 int）
p = (int*)vp; // OK：类型转换
```

> 注意
>
> ​	指向 `T` 的指针的指针不可转换成指向 `volatile T` 的指针的指针；对于要兼容的两个类型，它们的限定必须相同：
>
> ```c
> char *p = 0;
> volatile char vpp = &p; // 错误： char* 和 volatile char* 不是兼容类型
> char * volatile *pvp = &p; // OK，添加限定符（char* 到 char* volatile）
> ```
>



## `volatile` 的用法

1) [`static`](https://zh.cppreference.com/w/c/language/storage_duration) `volatile` 对象模仿映射于内存的 I/O 端口，而 `static` `const` `volatile` 对象模仿映射于内存的输入端口，例如实时时钟：

```c
volatile short *ttyport = (volatile short*)TTYPORT_ADDR;
for(int i = 0; i < N; ++i)
    *ttyport = a[i]; // *ttyport 是 volatile short 类型的左值
```

2) [sig_atomic_t](https://zh.cppreference.com/w/c/program/sig_atomic_t) 类型的 `static` `volatile` 对象用于与 [signal](https://zh.cppreference.com/w/c/program/signal) 处理函数交流。
3) 含有对 [setjmp](https://zh.cppreference.com/w/c/program/setjmp) 宏调用的函数中的局部 `volatile` 变量，是在 [longjmp](https://zh.cppreference.com/w/c/program/longjmp) 返回后仅有保证恢复其值的局部变量。
4) 另外，volatile 变量可用于禁用某些优化形式，例如禁用死存储消除，或为微基准测试禁用常量折叠。

> 注意 
>
> ​	volatile 变量不适合线程间交流；它们不提供原子性、同步或内存定序。读取一个被另一线程未经同步地修改的 volatile 变量，或两个未同步的线程的共时修改，对于一些数据竞争是未定义行为。

## 关键词

[`volatile`](https://zh.cppreference.com/w/c/keyword/volatile)

## 示例

​	展示用 volatile 禁用优化

```c
#include <stdio.h>
#include <time.h>
 
int main(void)
{
    clock_t t = clock();
    double d = 0.0;
    for (int n = 0; n < 10000; ++n)
        for (int m = 0; m < 10000; ++m)
            d += d * n * m; // 读写非 volatile 对象
    printf("Modified a non-volatile variable 100m times. "
           "Time used: %.2f seconds\n",
           (double)(clock() - t)/CLOCKS_PER_SEC);
 
    t = clock();
    volatile double vd = 0.0;
    for (int n = 0; n < 10000; ++n)
        for (int m = 0; m < 10000; ++m) {
            double prod = vd * n * m; // 读 volatile 对象
            vd += prod; // 读写 volatile 对象
        } 
    printf("Modified a volatile variable 100m times. "
           "Time used: %.2f seconds\n",
           (double)(clock() - t)/CLOCKS_PER_SEC);
}
```

​	可能的输出：

```txt
Modified a non-volatile variable 100m times. Time used: 0.00 seconds
Modified a volatile variable 100m times. Time used: 0.79 seconds
```

## 参阅

cv（`const` 与 `volatile`）类型限定符的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/cv)