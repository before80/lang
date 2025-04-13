+++
title = "指针声明"
date = 2025-04-13T10:15:28+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/pointer](https://zh.cppreference.com/w/c/language/pointer)

​	指针是一种对象类型，它引用函数或另一种类型的对象，可以添加限定符。指针亦可以不引用任何内容，这通过一个特定的空指针值指示。

## 语法

​	在指针声明的[声明文法](https://zh.cppreference.com/w/c/language/declarations)中，*类型说明符* ﻿序列代表所指向的类型（可以是函数或对象类型，可以是不完整类型），而*声明符* ﻿的形式为：

`*` *属性说明符序列* ﻿(可选) *限定符序列* ﻿(可选) *声明符*

其中 *声明符* 可以是命名所声明指针的标识符，包括另一个指针声明符（这指示一个指向指针的指针）：

```c
float *p, pp; // p 是指向 float 的指针
                // pp 是指向指向 float 指针的指针
int (*fp)(int); // fp 是指向类型 int(int) 为函数的指针
```

出现在 `*` 与标识符（或另一个嵌套声明符）间的*限定符序列* ﻿将被声明的限定赋予指针类型：

```c
int n;
const int * pc = &n; // pc 是指向 const int 的非 const 指针
// *pc = 2; // 错误：不能通过不带转换的 pc 修改 n
pc = NULL; // OK：pc 自身可修改
 
int * const cp = &n; // cp 是一个指向非 const 的 int 的 const 指针
*cp = 2; // OK：通过 cp 修改 n
// cp = NULL; // 错误：cp 自身不能修改
 
int * const * pcp = &cp; // 指向指向非 const 的 int 的 const 指针的非 const 指针
```

​	*属性说明符序列* ﻿(C23)为[属性](https://zh.cppreference.com/w/c/language/attributes)的可选列表，应用到被声明的指针。

## 解释

​	指针用于间接使用，这是种普遍存在的编程技巧；它们可以用于实现按引用传递语义，访问有动态[存储期](https://zh.cppreference.com/w/c/language/storage_duration)的对象，实现“可选”类型（使用空指针值），结构体间的聚合关系，回调（使用指向函数指针），泛型接口（使用指向 void 的指针）以及其他更多。

### 指向对象的指针

​	指向对象的指针可以通过应用于对象类型（可以不完整）表达式的[取值运算符](https://zh.cppreference.com/w/c/language/operator_member_access)初始化：

```
int n;
int *np = &n; // 指向 int 的指针
int *const *npp = &np; // 指向指向非 const 的 int 的 const 指针的非 const 指针
 
int a[2];
int (*ap)[2] = &a; // 指向 int 数组的指针
 
struct S { int n; } s = {1}
int* sp = &s.n; // 指向作为 s 成员的 int 的指针
```

​	指针可以出现作[间接运算符](https://zh.cppreference.com/w/c/language/operator_member_access#.E8.A7.A3.E5.BC.95.E7.94.A8)（一元 `*`）的操作数，它返回标识所指向对象的[左值](https://zh.cppreference.com/w/c/language/value_category)：

```
int n;
int* p = &n; // 指针 p 指向 n
*p = 7; // 存储 7 于 n
printf("%d\n", *p); // 左值到右值转换从 n 读取值
```

​	指向[结构体](https://zh.cppreference.com/w/c/language/struct)和[联合体](https://zh.cppreference.com/w/c/language/union)类型的对象的指针亦可作为[经由指针的成员访问](https://zh.cppreference.com/w/c/language/operator_member_access)运算符 `->` 的左操作数出现。

​	因为[数组到指针](https://zh.cppreference.com/w/c/language/array)隐式转换，指向数组首元素的指针可通过数组类型表达式初始化：

```
int a[2];
int *p = a; // 指向 a[0]
 
int b[3][3];
int (*row)[3] = b; // 指向 b[0]
```

​	有一些[加法、减法](https://zh.cppreference.com/w/c/language/operator_arithmetic)、[复合赋值](https://zh.cppreference.com/w/c/language/operator_assignment)、[自增和自减](https://zh.cppreference.com/w/c/language/operator_incdec)运算符对指向数组元素的指针有定义。

​	[比较运算符](https://zh.cppreference.com/w/c/language/operator_comparison)在一些情况下对指向对象的指针有定义：两个表示相同地址的指针比较相等，两个空指针值比较相等，比较指向同一数组的元素的指针以两个元素的数组下标进行比较，以及指向结构体成员的指针以这些成员的声明顺序进行比较。

​	许多实现亦提供对任意来源指针的[严格全序](https://en.wikipedia.org/wiki/Total_order#Strict_total_order)，例如若它们实现在连续（“平直”）的虚拟地址空间上。

### 指向函数的指针

​	指向函数的指针可由函数地址初始化。因为[函数到指针](https://zh.cppreference.com/w/c/language/conversion)转换，取址运算符是可选的：

```c
void f(int);
void (*pf1)(int) = &f;
void (*pf2)(int) = f; // 与 &f 相同
```

​	不同于函数，指向函数的指针是对象，从而能存储在数组中，被复制、赋值，作为参数传递给其他函数等等。

​	指向函数的指针可以用作[函数调用运算符](https://zh.cppreference.com/w/c/language/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8)的左操作数；这会调用所指向的函数：

```c
#include <stdio.h>
 
int f(int n)
{
    printf("%d\n", n);
    return n * n;
}
 
int main(void)
{
    int (*p)(int) = f;
    int x = p(7);
}
```

解引用函数指针产生所指向函数的函数指代符：

```c
int f();
int (*p)() = f;    // 指针 p 指向 f
(*p)(); // 通过函数指代器调用函数 f
p();    // 直接通过指针调用 f
```

​	[相等性比较运算符](https://zh.cppreference.com/w/c/language/operator_comparison)定义于指向函数的指针（若指向相同函数则它们比较相等）。

​	因为[函数类型的兼容性](https://zh.cppreference.com/w/c/language/type#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)忽略函数形参的顶层限定符，指向仅在形参的顶层限定符有区别的函数指针是可互换的：

```c
int f(int), fc(const int);
int (*pc)(const int) = f; // OK
int (*p)(int) = fc;       // OK
pc = p;                   // OK
```

### 指向 void 指针

​	指向任意类型对象的指针能[隐式转换](https://zh.cppreference.com/w/c/language/conversion)成指向 void 的指针（可选地有 [const](https://zh.cppreference.com/w/c/language/const) 或 [volatile](https://zh.cppreference.com/w/c/language/volatile) 限定），反之亦然：

```c
int n=1, *p=&n;
void* pv = p; // int* 到 void*
int* p2 = pv; // void* 到 int*
printf("%d\n", *p2); // 打印 1
```

​	指向 void 的指针用于传递未知类型的对象，这在泛型接口中常用：[malloc](https://zh.cppreference.com/w/c/memory/malloc) 返回 void*，[qsort](https://zh.cppreference.com/w/c/algorithm/qsort) 期待用户提供接受两个 const void* 实参的回调。[pthread_create](http://pubs.opengroup.org/onlinepubs/9699919799/functions/pthread_create.html) 期待用户提供接受并返回 void* 的回调。所有情况下，调用方负责在使用前将指针转换到正确的类型。

## 空指针

​	每种类型的指针都有含有一个该类型的特殊的值，称为*空指针值*。值为空的指针不指向对象或函数（解引用空指针是未定义行为），而且与所有相同类型的且值以为*空* ﻿的指针比较相等。

​	为将指针初始化为空值，或将空值赋给已存在的指针，可以使用空指针常量（[NULL](https://zh.cppreference.com/w/c/types/NULL)，或其他任何拥有值零的整数常量）。[静态初始化](https://zh.cppreference.com/w/c/language/initialization)亦将指针初始化到它们的空值。

​	空指针可以指示对象不存在，或可用于指示其他种类的错误条件。通常，接收指针实参的函数几乎总是需要检查该值是否为空，并对该情况特殊处理（例如，[free](https://zh.cppreference.com/w/c/memory/free) 在传递空指针时不做任何事）。

### 注解

​	尽管任何指向对象的指针[能被转换](https://zh.cppreference.com/w/c/language/cast)成指向其他类型对象的指针，解引用指向类型异于对象声明类型的指针几乎总是未定义行为。细节见[严格别名使用](https://zh.cppreference.com/w/c/language/object#.E4.B8.A5.E6.A0.BC.E5.88.AB.E5.90.8D.E4.BD.BF.E7.94.A8)。

​	可以指示函数，通过不会有别名使用的指针访问对象。细节见 [`restrict`](https://zh.cppreference.com/w/c/language/restrict)。(C99 起)

​	数组类型的左值表达式，在大多数语境中使用时，会经历[隐式转换](https://zh.cppreference.com/w/c/language/conversion)到指向数组首元素的指针。细节见[数组到指针转换](https://zh.cppreference.com/w/c/language/array#.E6.95.B0.E7.BB.84.E5.88.B0.E6.8C.87.E9.92.88.E8.BD.AC.E6.8D.A2)。

```c
char *str = "abc"; // "abc" 是 char[4] 类型的数组，str 是指向 'a' 的指针
```

指向 char 的指针通常[用于表示字符串](https://zh.cppreference.com/w/c/string/byte)。为表示合法的字节字符串，指针必须指向作为 char 数组元素的 char，而且在大于或等于指针所引用元素的下标的某个下标处，必须有零值的 char。

## 参阅

指针声明的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/pointer)