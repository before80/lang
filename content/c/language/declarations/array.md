+++
title = "数组声明"
date = 2025-04-13T10:18:09+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/array](https://zh.cppreference.com/w/c/language/array)

​	数组是由连续无空隙分配的，拥有特定*元素类型* ﻿的对象构成的。这些对象的数目数量（数组大小）在数组生存期间决不改变。

## 语法

​	在数组声明的[声明文法]({{< ref "/c/language/declarations" >}})中，*类型说明符* ﻿的序列指定*元素类型*（必须是一个完整对象类型），而*声明符* ﻿的形式为：

| `[` `static`(可选) *限定符* ﻿(可选) *表达式* ﻿(可选) `]` *属性说明符序列* ﻿(可选) | (1)  |      |
| ------------------------------------------------------------ | ---- | ---- |
| `[` *限定符* ﻿(可选) `static`(可选) *表达式* ﻿(可选) `]` *属性说明符序列* ﻿(可选) | (2)  |      |
| `[` *限定符* ﻿(可选) `*` `]` *属性说明符序列* ﻿(可选)          | (3)  |      |

1,2) 一般的数组声明符的语法

3)未指定大小的 VLA 的声明符（只能出现于函数原型作用域） 其中

| *表达式*         | -    | 任何无[逗号运算符]({{< ref "/c/language/expressions/operator_other#.E9.80.97.E5.8F.B7.E8.BF.90.E7.AE.97.E7.AC.A6" >}})的表达式，表明数组中的元素数量 |
| ---------------- | ---- | ------------------------------------------------------------ |
| *限定符*         | -    | [`const`]({{< ref "/c/language/declarations/const" >}})、[`restrict`]({{< ref "/c/language/declarations/restrict" >}}) 和 [`volatile`]({{< ref "/c/language/declarations/volatile" >}}) 限定符的任意混合，只允许出现于函数形参列表中；它们对数组形参所转换得到的指针类型赋予限定 |
| *属性说明符序列* | -    | (C23)可选的[属性]({{< ref "/c/language/declarations/attributes" >}})列表，应用到被声明的数组 |

```c
float fa[11], *afp[17]; // fa 是 11 个 float 组成的数组
                        // afp 是 17 个指向 float 的指针组成的数组
```

## 解释

​	数组类型有几种变体：已知常量大小的数组、变长度数组，以及未知大小数组。

### 已知常量大小数组

​	若数组声明符中的*表达式* ﻿为[整数常量表达式]({{< ref "/c/language/expressions/constant_expression#.E6.95.B4.E6.95.B0.E5.B8.B8.E9.87.8F.E8.A1.A8.E8.BE.BE.E5.BC.8F" >}})，拥有大于零的值，且元素类型是一种拥有已知常量大小的类型（即元素不是 VLA）(C99 起)，则声明符声明已知常量大小的数组：

```c
int n[10]; // 整数常量是常量表达式
char o[sizeof(double)]; // sizeof 是常量表达式
enum { MAX_SZ=100 };
int n[MAX_SZ]; // 枚举常量是常量表达式
```

​	已知常量大小的数组可以用[数组初始化器]({{< ref "/c/language/initialization/array_initialization" >}})提供它们的初始值：

```c
int a[5] = {1,2,3}; // 声明 int[5] 初始化为 1,2,3,0,0
char str[] = "abc"; // 声明 char[4] 初始化为 'a','b','c','\0'
```

| 在函数形参列表中，数组声明符中允许有额外的语法元素：关键词 `static` 及*限定符* ﻿，它们可以以任意顺序在大小表达式之前出现（即便省略大小表达式也可以出现它们）。对于函数中在数组形参的 `[` 和 `]` 中使用关键词 `static` 的情况，每次对这种函数[函数调用]({{< ref "/c/language/expressions/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8" >}})中，实际参数的值必须是一个指向数组首地址的合法指针，该数组至少有*表达式* ﻿所指定的元素数目：`void fadd(double a[static 10], const double b[static 10]) {     for (int i = 0; i < 10; i++)    {        if (a[i] < 0.0) return;        a[i] += b[i];    } } // 对 fadd 的调用可能进行编译时边界检查 // 并且允许诸如预读取 10 个 double 的优化 int main(void) {    double a[10] = {0}, b[20] = {0};    fadd(a, b); // OK    double x[5] = {0};    fadd(x, b); // 未定义行为：数组参数太小 }`若存在*限定符* ﻿，则它们对数组参数类型所转换得的指针类型赋予限定：`int f(const int a[20]) {    // 此函数中，a 类型为 const int*（指向 const int 的指针） } int g(const int a[const 20]) {    // 此函数中，a 类型为 const int* const（指向 const int 的 const 指针） }`这通常用于 [`restrict`]({{< ref "/c/language/declarations/restrict" >}}) 类型限定符：`void fadd(double a[static restrict 10],          const double b[static restrict 10]) {    for (int i = 0; i < 10; i++) // 循环可被打开或重排    {        if (a[i] < 0.0)            break;        a[i] += b[i];    } }`非常量长度数组若*表达式* ﻿不是[整数常量表达式]({{< ref "/c/language/expressions/constant_expression#.E6.95.B4.E6.95.B0.E5.B8.B8.E9.87.8F.E8.A1.A8.E8.BE.BE.E5.BC.8F" >}})，则数组声明器声明一个非常量大小的数组（VLA）。每次控制流经过该声明时，会求值*表达式* ﻿而且它必须每次求值为大于零的值），然后分配数组（对应地，VLA 的[生存期]({{< ref "/c/language/basic_concepts/lifetime" >}})在其声明离开作用域时结束）。VLA 实例的大小不会在其生存期中改变，但在另一次经过同一代码时，它可能被分配不同大小。运行此代码`#include <stdio.h>  int main(void) {   int n = 1; label:;   int a[n]; // 重分配 10 次，每次拥有不同大小   printf("The array has %zu elements\n", sizeof a / sizeof *a);   if (n++ < 10)       goto label; // 离开作用域的 VLA 结束其生存期 }`若大小是 `*` ，则声明是对于未指定大小的 VLA 的。这种声明只能出现于函数原型作用域，并声明一个完整类型的数组。其实，所有函数原型作用域中的 VLA 声明符都被处理成如同用 `*` 替换 *表达式*。`void foo(size_t x, int a[*]); void foo(size_t x, int a[x]) {    printf("%zu\n", sizeof a); // 大小同sizeof(int*) }`非常量长度数组与从它们派生的类型（指向它们的指针，等等）被通称为“可变修改类型”（VM）。任何可变修改类型的对象只能声明于块作用域或函数原型作用域中。`extern int n; int A[n];            // 错误：文件作用域 VLA extern int (*p2)[n]; // 错误：文件作用域 VM int B[100];          // OK：文件作用域的已知常量大小数组 void fvla(int m, int C[m][m]); // OK：原型作用域 VLA`VLA 必须拥有自动或分配存储期。指向 VLA 的指针，但不是 VLA 自身亦可拥有静态存储期。 VM 类型不能拥有链接。`void fvla(int m, int C[m][m]) // OK ：块作用域/自动存储期到 VLA 的指针 {    typedef int VLA[m][m]; // OK ：块作用域 VLA    int D[m];              // OK ：块作用域/自动存储期 VLA //  static int E[m]; // 错误：静态存储期 VLA //  extern int F[m]; // 错误：拥有链接的 VLA    int (*s)[m];     // OK：块作用域/自动存储期 VM    s = malloc(m * sizeof(int)); // OK：s 指向已分配存储中的 VLA //  extern int (*r)[m]; // 错误：拥有链接的 VM    static int (*q)[m] = &B; // OK：块作用域/静态存储期的 VM }`可变修改的类型不能是结构体或联合体的成员。`struct tag {    int z[n]; // 错误： VLA 结构体成员    int (*y)[n]; // 错误： VM 结构体成员 };` | (C99 起)          |
| ------------------------------------------------------------ | ----------------- |
| 若编译器定义宏常量 __STDC_NO_VLA__ 为整数常量 1 ，则不支持 VLA 或 VM 类型。 | (C11 起) (C23 前) |
| 若编译器定义宏常量 __STDC_NO_VLA__ 为整数常量 1 ，则不支持拥有自动存储期的 VLA 对象。对 VM 类型及拥有分配存储期的 VLA 的支持是强制的。 | (C23 起)          |

​	在函数形参列表中，数组声明符中允许有额外的语法元素：关键词 `static` 及*限定符* ﻿，它们可以以任意顺序在大小表达式之前出现（即便省略大小表达式也可以出现它们）。(C99 起)

​	对于函数中在数组形参的 `[` 和 `]` 中使用关键词 `static` 的情况，每次对这种函数[函数调用]({{< ref "/c/language/expressions/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8" >}})中，实际参数的值必须是一个指向数组首地址的合法指针，该数组至少有*表达式* ﻿所指定的元素数目：(C99 起)

```c
void fadd(double a[static 10], const double b[static 10])
{ 
    for (int i = 0; i < 10; i++)
    {
        if (a[i] < 0.0) return;
        a[i] += b[i];
    }
}
// 对 fadd 的调用可能进行编译时边界检查
// 并且允许诸如预读取 10 个 double 的优化
int main(void)
{
    double a[10] = {0}, b[20] = {0};
    fadd(a, b); // OK
    double x[5] = {0};
    fadd(x, b); // 未定义行为：数组参数太小
}
```

​	若存在*限定符* ﻿，则它们对数组参数类型所转换得的指针类型赋予限定：(C99 起)

```c
int f(const int a[20])
{
    // 此函数中，a 类型为 const int*（指向 const int 的指针）
}
int g(const int a[const 20])
{
    // 此函数中，a 类型为 const int* const（指向 const int 的 const 指针）
}
```

​	这通常用于 [`restrict`]({{< ref "/c/language/declarations/restrict" >}}) 类型限定符：(C99 起)

```c
void fadd(double a[static restrict 10],
          const double b[static restrict 10])
{
    for (int i = 0; i < 10; i++) // 循环可被打开或重排
    {
        if (a[i] < 0.0)
            break;
        a[i] += b[i];
    }
}
```

### 非常量长度数组 (C99 起)

​	若*表达式* ﻿不是[整数常量表达式]({{< ref "/c/language/expressions/constant_expression#.E6.95.B4.E6.95.B0.E5.B8.B8.E9.87.8F.E8.A1.A8.E8.BE.BE.E5.BC.8F" >}})，则数组声明器声明一个非常量大小的数组（VLA）。

​	每次控制流经过该声明时，会求值*表达式* ﻿而且它必须每次求值为大于零的值），然后分配数组（对应地，VLA 的[生存期]({{< ref "/c/language/basic_concepts/lifetime" >}})在其声明离开作用域时结束）。VLA 实例的大小不会在其生存期中改变，但在另一次经过同一代码时，它可能被分配不同大小。

```c
#include <stdio.h>
 
int main(void)
{
   int n = 1;
label:;
   int a[n]; // 重分配 10 次，每次拥有不同大小
   printf("The array has %zu elements\n", sizeof a / sizeof *a);
   if (n++ < 10)
       goto label; // 离开作用域的 VLA 结束其生存期
}
```

​	若大小是 `*` ，则声明是对于未指定大小的 VLA 的。这种声明只能出现于函数原型作用域，并声明一个完整类型的数组。其实，所有函数原型作用域中的 VLA 声明符都被处理成如同用 `*` 替换 *表达式*。

```c
void foo(size_t x, int a[*]);
void foo(size_t x, int a[x])
{
    printf("%zu\n", sizeof a); // 大小同sizeof(int*)
}
```

​	非常量长度数组与从它们派生的类型（指向它们的指针，等等）被通称为“可变修改类型”（VM）。任何可变修改类型的对象只能声明于块作用域或函数原型作用域中。

```c
extern int n;
int A[n];            // 错误：文件作用域 VLA
extern int (*p2)[n]; // 错误：文件作用域 VM
int B[100];          // OK：文件作用域的已知常量大小数组
void fvla(int m, int C[m][m]); // OK：原型作用域 VLA
```

​	VLA 必须拥有自动或分配存储期。指向 VLA 的指针，但不是 VLA 自身亦可拥有静态存储期。 VM 类型不能拥有链接。

```c
void fvla(int m, int C[m][m]) // OK ：块作用域/自动存储期到 VLA 的指针
{
    typedef int VLA[m][m]; // OK ：块作用域 VLA
    int D[m];              // OK ：块作用域/自动存储期 VLA
//  static int E[m]; // 错误：静态存储期 VLA
//  extern int F[m]; // 错误：拥有链接的 VLA
    int (*s)[m];     // OK：块作用域/自动存储期 VM
    s = malloc(m * sizeof(int)); // OK：s 指向已分配存储中的 VLA
//  extern int (*r)[m]; // 错误：拥有链接的 VM
    static int (*q)[m] = &B; // OK：块作用域/静态存储期的 VM
}
```

​	可变修改的类型不能是结构体或联合体的成员。

```c
struct tag
{
    int z[n]; // 错误： VLA 结构体成员
    int (*y)[n]; // 错误： VM 结构体成员
};
```

​	若编译器定义宏常量 `__STDC_NO_VLA__` 为整数常量 1 ，则不支持 VLA 或 VM 类型。 (C11 起) (C23 前)

​	若编译器定义宏常量 `__STDC_NO_VLA__` 为整数常量 1 ，则不支持拥有自动存储期的 VLA 对象。(C23 起)

​	对 VM 类型及拥有分配存储期的 VLA 的支持是强制的。(C23 起)

### 未知大小数组

​	若忽略数组声明器中的*表达式*，则它声明一个未知大小数组。除了函数形参列表中的情况（这种数组被转换成指针），以及有[初始化器]({{< ref "/c/language/initialization/array_initialization" >}})的情况之外，这种类型都是[不完整类型](https://zh.cppreference.com/w/c/language/types#.E4.B8.8D.E5.AE.8C.E6.95.B4.E7.B1.BB.E5.9E.8B)（注意，以 `*` 代替大小声明的拥有未指定大小的 VLA 是完整类型）(C99 起)：

```c
extern int x[]; // x 的类型是“边界未知的 int 数组”
int a[] = {1,2,3}; // a 的类型是“3 个 int 的数组”
```

​	

​	在 [struct]({{< ref "/c/language/declarations/struct" >}}) 定义中，未知大小数组可以作为最后一个元素出现（只要有至少一个其他具名成员），这种情况下，这是称为*柔性数组成员* ﻿的特殊情形。细节见 [struct]({{< ref "/c/language/declarations/struct" >}})：(C99 起)

```c
struct s { int n; double d[]; }; // s.d 是柔性数组成员
struct s *s1 = malloc(sizeof (struct s) + (sizeof (double) * 8)); // 如同 d 是 double d[8]
```



### 限定符

​	若数组类型声明拥有 [`const`]({{< ref "/c/language/declarations/const" >}})、[`volatile`]({{< ref "/c/language/declarations/volatile" >}})、或 [`restrict`]({{< ref "/c/language/declarations/restrict" >}})(C99 起) 限定符（可以通过使用 [`typedef`]({{< ref "/c/language/declarations/typedef" >}}) 做到），则限定的不是数组类型，而是其元素类型：(C23 前)

​	始终认为数组类型与其元素类型有等同的限定，但始终不认为数组类型有 [`_Atomic`]({{< ref "/c/language/declarations/atomic" >}}) 限定：(C23 起)

```c
typedef int A[2][3];
const A a = {{4, 5, 6}, {7, 8, 9}}; // const int 的数组的数组
int* pi = a[0]; // 错误：a[0] 类型为 const int*
void *unqual_ptr = a; // C23 前 OK；C23 起错误
// 注：clang 即使在 C89-C17 模式也应用 C++/C23 中的规则
```

​	不允许对数组类型应用 [`_Atomic`]({{< ref "/c/language/declarations/atomic" >}})，尽管允许原子类型的数组。(C11 起)

```c
typedef int A[2];
// _Atomic A a0 = {0};    // 错误
// _Atomic(A) a1 = {0};   // 错误
_Atomic int a2[2] = {0};  // OK
_Atomic(int) a3[2] = {0}; // OK
```



### 赋值

​	数组类型的对象不是[可修改左值]({{< ref "/c/language/expressions/value_category" >}})，尽管它们可以取地址，但它们不能出现于赋值运算符的左侧。不过，拥有数组成员的结构体是可修改左值，并可以赋值：

```c
int a[3] = {1,2,3}, b[3] = {4,5,6};
int (*p)[3] = &a; // OK，可以取地址
// a = b;            // 错误，a 是数组
struct { int c[3]; } s1, s2 = {3,4,5};
s1 = s2; // OK：可以对拥有数组成员的结构体赋值
```

### 数组到指针转换

​	任何数组类型的[左值表达式]({{< ref "/c/language/expressions/value_category" >}})，当用于异于

- 作为[取地址运算符]({{< ref "/c/language/expressions/operator_member_access" >}})的操作数
- 作为 [`sizeof`]({{< ref "/c/language/expressions/sizeof" >}}) 的操作数
- 作为 [`typeof`](https://zh.cppreference.com/w/c/language/typeof) 和 [`typeof_unqual`](https://zh.cppreference.com/w/c/language/typeof_unqual) 的操作数 (C23 起)
- 作为用于[数组初始化]({{< ref "/c/language/initialization/array_initialization" >}})的字符串字面量
- 作为 [`_Alignof`]({{< ref "/c/language/expressions/_Alignof" >}})(C11 起)(C23 前)[`alignof`](https://zh.cppreference.com/w/c/language/alignof)(C23 起) 的操作数(C11 起)

的语境时，会经历到指向其首元素指针的[隐式转换]({{< ref "/c/language/expressions/conversion" >}})。结果为非左值。

​	若声明数组为 [`register`]({{< ref "/c/language/declarations/storage_duration" >}})，则尝试这么做的程序的行为未定义。

```c
int a[3] = {1,2,3};
int* p = a;
printf("%zu\n", sizeof a); // 打印数组大小
printf("%zu\n", sizeof p); // 打印指针大小
```

​	当数组类型用于函数形参列表时，它会转换成对应的指针类型： `int f(int a[2])` 和 `int f(int* a)` 声明同一个函数。因为函数实际参数类型为指针类型，使用数组实参的函数调用会进行一个数组到指针转换；被调用函数无法获得实参数组的大小，必须显式传递：

```c
#include <stdio.h>
 
void f(int a[], int sz) // 实际上声明 void f(int* a, int sz)
{
    for(int i = 0; i < sz; ++i)
        printf("%d\n", a[i]);
}
 
void g(int (*a)[10]) // 不会对数组指针形参进行转换
{
    for (int i = 0; i < 10; ++i)
        printf("%d\n", (*a)[i]);
}
 
int main(void)
{
    int a[10] = {0};
    f(a, 10); // 转换成 int*，传递指针
    g(&a);    // 传递指向数组的指针（无需传递其大小）
}
```

### 多维数组

​	当数组的元素是另一个数组时，我们称数组是多维的：

```c
// 2 个元素的数组，每个元素为 3 个 int 的数组
int a[2][3] = {{1,2,3},  // 可视作行主导排列的
               {4,5,6}}; // 2x3 矩阵
```

> 注意
>
> ​	当应用数组到指针转换时，多维数组被转换成指向其首元素的指针，例如指向首行的指针：
>
> ```c
> int a[2][3]; // 2x3 矩阵
> int (*p1)[3] = a; // 指向首个 3 个元素行的指针
> int b[3][3][3]; // 3x3x3 立方体
> int (*p2)[3][3] = b; // 指向首个 3x3 平面的指针
> ```

​	若支持 VLA，则(C11 起)多维数组可以在每一维度可变修改：(C99 起)

```c
int n = 10;
int a[n][2*n];
```



## 注解

​	不允许声明零长度数组，即使一些编译器作为扩展提供它们（典型例子是 C99 前的[柔性数组成员]({{< ref "/c/language/declarations/struct" >}})实现）。

​	若 VLA 的大小*表达式* ﻿拥有副作用，则保证会正确产生副作用，除非它们是 `sizeof` 表达式的一部分，其结果不依赖副效应：

```c
int n = 5, m = 5;
size_t sz = sizeof(int (*[n++])[m++]); // n 被自增，m 可能自增也可能未自增
```

## 参阅

**数组声明**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/array)**
