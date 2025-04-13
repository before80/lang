+++
title = "声明"
date = 2025-04-13T10:08:02+08:00
weight = 70
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/declarations](https://zh.cppreference.com/w/c/language/declarations)

​	*声明* ﻿是一种引入一个或多个[标识符](https://zh.cppreference.com/w/c/language/identifier)到程序中，并指定其含义及属性的 C 语言构造。

​	声明可以出现在任何作用域中。每个声明以分号结束（类似[语句](https://zh.cppreference.com/w/c/language/statements)），并由两(C23 前)三(C23 起)个独立部分组成：

| *说明符与限定符* *声明符与初始化器* ﻿(可选) `;`           | (1)  |          |
| -------------------------------------------------------- | ---- | -------- |
| *属性说明符序列* *说明符与限定符* *声明符与初始化器* `;` | (2)  | (C23 起) |
| *属性说明符序列* `;`                                     | (3)  | (C23 起) |

​	其中

*说明符与限定符*-任意顺序的下列内容的空白符分隔列表：

- 类型说明符：
  - void
  - [算术类型](https://zh.cppreference.com/w/c/language/arithmetic_types)名
  - [原子类型](https://zh.cppreference.com/w/c/language/atomic)名
  - 先前由 [typedef](https://zh.cppreference.com/w/c/language/typedef) 声明引入的名称
  - [`struct`](https://zh.cppreference.com/w/c/language/struct)、[`union`](https://zh.cppreference.com/w/c/language/union) 或 [`enum`](https://zh.cppreference.com/w/c/language/enum) 说明符
  - [typeof](https://zh.cppreference.com/w/c/language/typeof) 说明符 (C23 起)
- 零或一个存储类说明符：[`typedef`](https://zh.cppreference.com/w/c/language/typedef)、[`constexpr`](https://zh.cppreference.com/w/c/language/constexpr)、[`auto`](https://zh.cppreference.com/w/c/language/auto)、[register、static、extern、`_Thread_local`](https://zh.cppreference.com/w/c/language/storage_duration)
- 零或多个类型限定符：[`const`](https://zh.cppreference.com/w/c/language/const)、[`volatile`](https://zh.cppreference.com/w/c/language/volatile)、[`restrict`](https://zh.cppreference.com/w/c/language/restrict)、[_Atomic](https://zh.cppreference.com/w/c/language/atomic)
- （只在声明函数时）零或多个函数说明符：[`inline`](https://zh.cppreference.com/w/c/language/inline)、[`_Noreturn`](https://zh.cppreference.com/w/c/language/_Noreturn)
- 零或多个对齐说明符：[`_Alignas`](https://zh.cppreference.com/w/c/language/_Alignas)(C11 起)(C23 前)[`alignas`](https://zh.cppreference.com/w/c/language/alignas)(C23 起)

*声明符与初始化器*-*声明符* ﻿的逗号分隔列表（每个声明符提供附加类型信息及/或要声明的标识符）。声明符可伴随[初始化器](https://zh.cppreference.com/w/c/language/initialization)。[enum](https://zh.cppreference.com/w/c/language/enum)、[struct](https://zh.cppreference.com/w/c/language/struct) 和 [union](https://zh.cppreference.com/w/c/language/union) 声明可忽略*声明符* ﻿，这种情况下它们仅引入枚举常量和/或标签。

*属性说明符序列*-(C23)可选的[属性](https://zh.cppreference.com/w/c/language/attributes)列表，应用到被声明的实体，或若单独出现则构成属性声明。



1,2) 简单声明。引入一或多个标识符，它们代表对象、函数、结构体/联合体/枚举标签、typedef 或枚举常量。

3)属性声明。不声明任何标识符，并且若标准不指定含义则拥有实现定义的含义。

例如：

```c
int a, *b=NULL; // “int”是类型说明符，
                // “a”是声明符
                // “*b”是声明符而 NULL 是初始化器
const int *f(void); // “int”是类型说明符
                    // “const”是类型限定符
                    // “*f(void)”是声明符
enum COLOR {RED, GREEN, BLUE} c; // “enum COLOR {RED, GREEN, BLUE}”是类型说明符
                                 // “c”是声明符
```

​	一个声明引入的每个标识符类型是通过*类型说明符* ﻿所指定的类型及其*声明符* ﻿所应用的类型修饰决定的。当使用 auto 说明符时，变量的类型也可以进行推断。(C23 起)

​	[属性](https://zh.cppreference.com/w/c/language/attributes)(C23 起)可在*说明符与限定符* ﻿中出现，该情况下它们应用到前导的说明符所确定的类型。

## 声明符

​	每个声明符是下列之一：

| *标识符* *属性说明符序列* ﻿(可选)                             | (1)  |      |
| ------------------------------------------------------------ | ---- | ---- |
| `(` *声明符* `)`                                             | (2)  |      |
| `*` *属性说明符序列* ﻿(可选) *限定符* ﻿(可选) *声明符*         | (3)  |      |
| *无指针声明符* `[` `static`(可选) *限定符* ﻿(可选) *表达式* `]`*无指针声明符* `[` *限定符* ﻿(可选) `*` `]` | (4)  |      |
| *无指针声明符* `(` *形参或标识符* `)`                        | (5)  |      |

1) 此声明符引入的标识符。
2) 任何可以放入括号中的声明符；引入指向数组或指向函数指针时要求这么做。
3) [指针声明符](https://zh.cppreference.com/w/c/language/pointer)：声明 S * cvr D 声明 `D` 为 *cvr* 限定指针，指向 `S` 所确定的类型。
4) [数组声明符](https://zh.cppreference.com/w/c/language/array)：声明 S D[N] 声明 `D` 为有 `N` 个 `S` 所确定类型对象的数组。*无指针声明符* ﻿是除未被括号包围的指针声明符以外的其他任何声明符。
5) [函数声明符](https://zh.cppreference.com/w/c/language/function_declaration)：声明 S D(params) 声明 `D` 为接收参数 `params` 并返回 `S` 的函数。*无指针声明符* ﻿是除未被括号包围的指针声明符以外的其他任何声明符 。

​	此语法背后的原因，是当声明符所声明的标识符以与声明符相同的形式出现在表达式中时，它会拥有类型说明符序列所指定的类型。

```c
struct C
{
    int member; // “int”是类型说明符
                // “member”是声明符
} obj, *pObj = &obj;
// “struct C { int member; }”是类型说明符
// 声明符“obj”定义 struct C 类型的对象
// 声明符“*pObj”声明指向 struct C 的指针，
// 初始化器“= &obj”提供该指针的初值
 
int a = 1, *p = NULL, f(void), (*pf)(double);
// 类型说明符是“int”
// 声明符“a”定义一个 int 类型对象
//   初始化器“=1”提供其初值
// 声明符“*p”定义一个指向 int 指针类型的对象
//   初始化器“=NULL”提供其初值
// 声明符“f(void)”声明接受 void 并返回 int 的函数
// 声明符“(*pf)(double)”定义一个指向
//   接受 double 并返回 int 的函数的指针类型对象
 
int (*(*foo)(double))[3] = NULL;
// 类型说明符是“int”
// 1. 声明符“(*(*foo)(double))[3]”是数组声明符：
//    所声明类型是“3 个 int 的数组的 /嵌套声明符/”
// 2. 嵌套声明符是“*(*foo)(double))”，是指针声明符
//    所声明类型是“/嵌套声明符/ 指向 3 个 int 的数组的指针”
// 3. 嵌套声明符是“(*foo)(double)”，是一个函数声明符
//    所声明类型是“/嵌套声明符/ 接受 double 并返回指向 3 个 int 的数组的指针的函数”
// 4. 嵌套声明符是“(*foo)”，是一个（有括号，函数声明符所要求）指针声明符。
//    所声明类型是“/嵌套声明符/ 指向接受 double 并返回指向 3 个 int 的数组的指针的函数的指针”
// 5. 嵌套声明符是“foo”，是一个标识符。
// 该声明引入一个标识符“foo”，以指代一个对象，其类型为
// “指向接受 double 并返回指向 3 个 int 的数组的指针的函数的指针”
// 初始化器“= NULL”提供此指针的初值。
 
// 若在用于声明符形式的表达式使用“foo”，则表达式类型将是int。
int x = (*(*foo)(1.2))[0];
```

​	每个不属于其他声明符一部分的声明符结尾是一个[顺序点](https://zh.cppreference.com/w/c/language/eval_order)。

​	所有情况下，*属性说明符序列* ﻿均为可选的[属性](https://zh.cppreference.com/w/c/language/attributes)(C23 起)序列。立即出现在标识符后时，它应用到被声明的对象或函数。

## 定义

​	*定义*是一个提供所有关于其所声明标识符信息的声明。

​	每个 [enum](https://zh.cppreference.com/w/c/language/enum) 或 [typedef](https://zh.cppreference.com/w/c/language/typedef) 声明都是定义。

​	对于函数，包含函数体的声明即是[函数定义](https://zh.cppreference.com/w/c/language/function_definition)：

```c
int foo(double); // 声明
int foo(double x) { return x; } // 定义
```

​	对于对象，分配其存储的声明（[自动或静态](https://zh.cppreference.com/w/c/language/storage_duration)，但、非 extern ）即是定义，而一个不分配存储的声明（[外部声明](https://zh.cppreference.com/w/c/language/extern)）不是。

```c
extern int n; // 声明
int n = 10; // 定义
```

​	对于[结构体](https://zh.cppreference.com/w/c/language/struct)和[联合体](https://zh.cppreference.com/w/c/language/union)，指定其成员列表的声明是定义：

```c
struct X; // 声明
struct X { int n; }; // 定义
```

## 重声明

​	若另一个同一标识符的声明在同一[作用域](https://zh.cppreference.com/w/c/language/scope)的较早部分出现，则声明不可再引入同一标识符，除非

- [有链接](https://zh.cppreference.com/w/c/language/storage_duration)对象（外部或内部）的声明可以重复：

```c
extern int x;
int x = 10; // OK
extern int x; // OK
 
static int n;
static int n = 10; // OK
static int n; // OK
```

- 非 VLA [typedef](https://zh.cppreference.com/w/c/language/typedef) 可以任意重复，只要它指名同一类型：

```c
typedef int int_t;
typedef int int_t; // OK
```

- [struct](https://zh.cppreference.com/w/c/language/struct) 和 [union](https://zh.cppreference.com/w/c/language/union) 声明可以重复：

```c
struct X;
struct X { int n; };	
struct X;
```

​	这些规则会简化头文件的使用。

## 注解

​	C89 中，任何[复合语句](https://zh.cppreference.com/w/c/language/statements#.E5.A4.8D.E5.90.88.E8.AF.AD.E5.8F.A5)（块作用域）中的声明必须出现在块的开头，在任何[语句](https://zh.cppreference.com/w/c/language/statements)之前。而且，C89 中返回 int 的函数可以隐式地用[函数调用运算符](https://zh.cppreference.com/w/c/language/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8)声明，且使用旧式[函数定义](https://zh.cppreference.com/w/c/language/function_definition)时，int 类型的函数参数不必声明。(C99 前)

​	禁止空声明符；简单声明必须拥有至少一个声明符，或声明至少一个 `struct/union/enum` 标签，或引入至少一个枚举常量。

​	若声明符的任一部分是[非常量长度数组](https://zh.cppreference.com/w/c/language/array)（VLA）声明符，则整个声明符的类型被称作“可变修改类型”。根据可变修改类型定义的类型同样是可变修改的（VM）。任何可变修改类型声明只允许出现在[块作用域](https://zh.cppreference.com/w/c/language/scope)或函数原型作用域，而且不能是任何结构体或联合体的成员。尽管 VLA 只能拥有自动或分配[存储期](https://zh.cppreference.com/w/c/language/storage_duration)，一个 VM 类型，例如指向 VLA 的指针也可以有静态存储。关于 VM 类型有其他使用限制，见 [goto](https://zh.cppreference.com/w/c/language/goto)、[switch](https://zh.cppreference.com/w/c/language/switch)、[longjmp](https://zh.cppreference.com/w/c/program/longjmp)。(C99 起)

​	[_Static_assert](https://zh.cppreference.com/w/c/language/_Static_assert) 从 C 文法的视角来看，被认为是声明（故它们可以出现在任何声明能出现的地方），但它们不会引入任何新的标识符，且不遵循声明语法。(C11 起)

​	[属性](https://zh.cppreference.com/w/c/language/attributes)声明亦被认为是声明（故它们可以出现在任何声明能出现的地方），但它们不会引入任何新的标识符。单个无*属性说明符序列* ﻿的 `;` 不是属性声明，而是语句。

## 参阅

声明的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/declarations)