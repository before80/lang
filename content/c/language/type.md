+++
title = "类型"
date = 2025-04-11T20:28:11+08:00
weight = 90
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/type](https://zh.cppreference.com/w/c/language/type)

（内建类型上的更多细节参阅[算术类型](https://zh.cppreference.com/w/c/language/arithmetic_types)和 C 库所提供的[类型相关的工具列表](https://zh.cppreference.com/w/c/types)。）

​	[对象](https://zh.cppreference.com/w/c/language/object)、[函数](https://zh.cppreference.com/w/c/language/functions)和[表达式](https://zh.cppreference.com/w/c/language/expressions)拥有称为*类型* ﻿的属性，它确定存储于对象或表达式求值所得的二进制值的判读方式。

## 类型分类

​	C 类型系统由下列类型组成：

- 类型 void

- 基本类型

  - 类型 char
  - 有符号整数类型
    - 标准：`signed char`、`short`、`int`、`long`、`long long`(C99 起)
    - 位精确：`_BitInt(N)` 其中 N 为整数常量表达式，指定用于表示该类型的位数，包括符号位。每个 N 值均代表一种独立类型。(C23 起)
    - 扩展：实现定义，例如 `__int128`(C99 起)

  - 无符号整数类型
    - 标准：`_Bool`(C99 起) 、`unsigned char`、`unsigned short`、`unsigned int`、`unsigned long`、`unsigned long long`(C99 起)
    - 位精确：`unsigned _BitInt(N)` 其中 N 为整数常量表达式，指定用于表示该类型的位数。每个 N 值均代表一种独立类型。此分类中包括类型 `unsigned _BitInt(1)` 它没有对应的位精确有符号整数类型。(C23 起)
    - 扩展：实现定义，例如 `__uint128`(C99 起)
  - 浮点数类型
    - 二进制浮点数类型：`float`、`double`、`long double`
    - 十进制实浮点数类型：`_Decimal32`、`_Decimal64`、`_Decimal128`(C23 起)
    - 复数类型：`float _Complex`、`double _Complex`、`long double _Complex`(C99 起)
    - 虚数类型：`float _Imaginary`、`double _Imaginary`、`long double _Imaginary`(C99 起)

- [枚举类型](https://zh.cppreference.com/w/c/language/enum)

- 派生类型
  - [数组类型](https://zh.cppreference.com/w/c/language/array)
  - [结构体类型](https://zh.cppreference.com/w/c/language/struct)
  - [联合体类型](https://zh.cppreference.com/w/c/language/union)
  - [函数类型](https://zh.cppreference.com/w/c/language/functions)
  - [指针类型](https://zh.cppreference.com/w/c/language/pointer)
  - [原子类型](https://zh.cppreference.com/w/c/language/atomic)(C11 起)

​	对于上面列出的每个类型，可以存在数种其类型的限定版本，对应 [`const`](https://zh.cppreference.com/w/c/language/const)、[`volatile`](https://zh.cppreference.com/w/c/language/volatile) 和 [`restrict`](https://zh.cppreference.com/w/c/language/restrict) 限定符的一、二或全部三个组合（在限定符的语义所允许处）。

## 类型组别

- *对象类型*：所有不是函数类型的类型
- *字符类型*：char、signed char、unsigned char
- *整数类型*：char、有符号整数类型、无符号整数类型、枚举类型
- *实数类型*：整数类型和实浮点数类型
- [*算术类型*](https://zh.cppreference.com/w/c/language/arithmetic_types)：整数类型和浮点数类型
- *标量类型*：算术类型和指针类型以及 [nullptr_t](https://zh.cppreference.com/w/c/types/nullptr_t)(C23 起)
- *聚合类型*：数组类型和结构体类型
- *派生声明符类型*：数组类型、函数类型和指针类型

​	构造一个完整对象类型，使其对象表示中的字节数不能以 [size_t](https://zh.cppreference.com/w/c/types/size_t) 类型（即 [`sizeof`](https://zh.cppreference.com/w/c/language/sizeof) 运算符的结果类型）表示，包括在运行时构成这种 VLA 类型，(C99 起)是未定义行为。

## 兼容类型

​	C 程序中，在*不同翻译单元* ﻿中涉及同一对象或函数的声明，不必拥有相同类型。它们只需要拥有相似的类型，正式而言即*兼容类型*。同样的规则适用于函数调用和左值访问；实参类型必须与形参类型*兼容*，而左值表达式类型必须与被访问对象的类型*兼容*。

​	类型 `T` 与 `U` 兼容，条件为

- 它们是同一类型（同名或由 [`typedef`](https://zh.cppreference.com/w/c/language/typedef) 引入的别名）
- 它们是使用相同的 cvr 类型限定符限定的类型，并且被限定的类型是兼容的类型
- 它们是指针类型，并指向兼容类型
- 它们是数组类型，且
  - 其元素类型兼容，且
  - 若都拥有常量大小，则大小相同。注意：未知边界数组与任何兼容元素类型的数组兼容。VLA 与任何元素类型兼容的数组兼容。(C99 起)

- 它们都是结构体/联合体/枚举类型，且

  - (C99)若一者以标签声明，则另一者必须以同一标签声明。

  - 若它们都是完整类型，则其成员必须在数量上准确对应，各自以兼容类型声明，并各自拥有匹配的名称。

  - 另外，若它们都是枚举，则对应成员亦必须拥有相同值。

  - 另外，若它们是结构体或联合体，则
    - 对应的元素必须以同一顺序声明（仅结构体）
    - 对应的[位域](https://zh.cppreference.com/w/c/language/bit_field)必须有相同宽度。

- 一者为枚举类型，而另一者为该枚举的底层类型

- 它们是函数类型，且

  - 其返回类型兼容
  - 它们都使用形参列表，形参数量（包括省略号的使用）相同，且其对应形参，在应用数组到指针和函数到指针类型调整，及剥除顶层限定符后，拥有相同类型
  - 一个是旧式（无形参）定义，另一个有形参列表，形参列表不使用省略号，而每个形参（在函数形参类型调整后）都与默认实参提升后的对应旧式形参兼容 (C23 前)
  - 一个是旧式（无形参）声明，另一个有形参列表，形参列表不使用省略号，而所有形参（在函数形参类型调整后）不受默认实参提升影响(C23 前)

​		类型 char 既不与 signed char 兼容，也不与 unsigned char 兼容。

​		若涉及同一对象或函数的两个声明不使用兼容类型，则程序的行为未定义。

```c
// 翻译单元 1（Translation Unit 1，以下简称TU1，下同）
struct S {int a;};
extern struct S *x; // 与 TU2 的 x 兼容，但不与 TU3 的 x 兼容
 
// 翻译单元 2
struct S;
extern struct S *x; // 与两个 x 兼容
 
// 翻译单元 3
struct S {float a;};
extern struct S *x; // 与 TU2 的 x 兼容，但不与 TU1 的 x 兼容
 
// 行为未定义
```



```c
// 翻译单元 1
#include <stdio.h>
 
struct s {int i;}; // 与 TU3 的 s 兼容，但不与 TU2 的 s 兼容
extern struct s x = {0}; // 与 TU3 的 x 兼容
extern void f(void); // 与 TU2 的 f 兼容
 
int main()
{
   f();
   return x.i;
}
 
// 翻译单元 2
struct s {float f;}; // 与 TU4 的 s 兼容，但不与 TU1 的 s 兼容
extern struct s y = {3.14}; // 与 TU4 的 y 兼容
void f() // 与 TU1 的 f 兼容
{
   return;
}
 
// 翻译单元 3
struct s {int i;}; // 与 TU1 的 s 兼容，但不与 TU2 的 s 兼容
extern struct s x; // 与 TU1 的 x 兼容
 
// 翻译单元 4
struct s {float f;}; // 与 TU2 的 s 兼容，但不与 TU1 的 s 兼容
extern struct s y; // 与 TU2 的 y 兼容
 
// 行为良好定义：只有对象或函数的多个声明，而非类型自身必须拥有兼容类型
```

> **注意**
>
> ​	C++ 没有兼容类型的概念。在不同翻译单元中声明二个兼容但不等同的类型的 C 程序不是合法的 C++ 程序。

## 合成类型

​	从两个兼容的类型可以构造合成类型；它是与两个类型兼容，并满足下列条件的类型：

- 若两个类型均为数组类型，则应用下列规则：
  - 若一个类型是已知常量大小的数组，则合成类型为该大小的数组。
  - 否则，若一个类型是 VLA，其大小由表达式指定且表达式尚未求值，则需要两个类型的合成类型的程序有未定义行为。- (C99 起)
  - 否则，若一个类型为已指定大小的 VLA，则合成类型为该大小的 VLA。- (C99 起)
  - 否则，若一个类型为未指定大小的 VLA，则合成类型为未指定大小的 VLA。- (C99 起)

- 否则，两个数组类型都有未知大小，而合成类型为未知大小的数组。合成类型的元素类型是两个元素类型的合成类型。
- 若一个类型是有形参类型列表（函数原型）的函数类型，则合成类型为有该形参类型列表的函数原型。(C23 前)

- 若两个类型均为有形参类型列表的函数类型，则合成类型的形参类型列表中的每个形参类型，是对应形参的合成类型。

这些规则递归地应用到两个类型的派生来源类型。

```c
// 给定以下两个文件作用域声明：
int f(int (*)(), double (*)[3]);
int f(int (*)(char *), double (*)[]); // C23: 错误: 对于 'f' 冲突的类型
// 生成的函数合成类型为：
int f(int (*)(char *), double (*)[3]);
```

​	对于拥有内部或外部[链接](https://zh.cppreference.com/w/c/language/storage_duration)，并在其先前声明已经可见的作用域中再次声明的标识符，若先前的声明指定了内部或外部链接，则在后一声明中的标识符类型成为合成类型。

## 不完整类型

​	不完整类型是缺乏足以确定其对象大小的信息对象类型。不完整类型可以在翻译单元的某些点完整。

​	下列类型不完整：

- 类型 void。此类型不能完整。
- 大小未知的数组。之后指定大小的声明能使之完整。

```c
extern char a[]; // a 的类型不完整（这通常出现于头文件）
char a[10];      // a 的类型现在完整（这通常出现于源文件）
```

- 内容未知的结构体或联合体类型。在同一作用域的后面，定义同一结构体或联合体的内容的声明能使之完整。

```c
struct node
{
    struct node *next; // struct node 在此点不完整
}; // struct node 在此点完整
```

## 类型名

​	在除[声明](https://zh.cppreference.com/w/c/language/declarations)之外的语境中可能需要指名某个类型。这些情况下使用*类型名*，即*类型说明符* ﻿和*类型限定符* ﻿的列表，后随*声明符*（见[声明](https://zh.cppreference.com/w/c/language/declarations)），它在文法上与会用来声明此类型的单个对象或函数的列表完全相同，除了省略掉其中的标识符：

```c
int n; // 声明 int 
sizeof(int); // 使用类型名
 
int *a[3]; // 声明 3 个指向 int 指针的数组
sizeof(int *[3]); // 使用类型名
 
int (*p)[3]; // 声明指向 3 个 int 的数组的指针
sizeof(int (*)[3]); // 使用类型名
 
int (*a)[*] // （在函数参数中）声明指向 VLA 的指针
sizeof(int (*)[*]) // （在函数参数中）使用类型名
 
int *f(void); // 声明函数
sizeof(int *(void)); // 使用类型名
 
int (*p)(void); // 声明指向函数指针
sizeof(int (*)(void)); // 使用类型名
 
int (*const a[])(unsigned int, ...) = {0}; // 声明指向函数指针的数组
sizeof(int (*const [])(unsigned int, ...)); // 使用类型名
```

​	除了围绕标识符的冗余括号在类型名中有意义，并表示“不指定形参的函数”：

```c
int (n); // 声明 int 类型的 n
sizeof(int ()); // 使用类型“返回 int 的函数”
```

​	类型名用于下列场合：

- [转换](https://zh.cppreference.com/w/c/language/cast)
- [`sizeof`](https://zh.cppreference.com/w/c/language/sizeof)
- [复合字面量](https://zh.cppreference.com/w/c/language/compound_literal)(C99 起)
- [泛型选择](https://zh.cppreference.com/w/c/language/generic)
- [`_Alignof`](https://zh.cppreference.com/w/c/language/_Alignof)(C23 前) [`alignof`](https://zh.cppreference.com/w/c/language/alignof)(C23 起)  - (C11 起)
- [`_Alignas`](https://zh.cppreference.com/w/c/language/_Alignas)(C23 前)  [`alignas`](https://zh.cppreference.com/w/c/language/alignas)(C23 起) - (C11 起)
- [`_Atomic`](https://zh.cppreference.com/w/c/language/atomic)（用作类型说明符时） - (C11 起)

​	类型名可引入新类型：

```c
void* p = (void*)(struct X {int i;} *)0;
// 用于转换表达式的 "struct X {int i;}*"
// 引入新类型 "struct X"
struct X x = {1}; // struct X 现在在作用域中
```