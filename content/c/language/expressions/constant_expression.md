+++
title = "常量表达式"
date = 2025-04-12T16:49:42+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/constant_expression](https://zh.cppreference.com/w/c/language/constant_expression)

​	表达式的数种变体被称为*常量表达式*。

## 预处理器常量表达式

​	[`#if` 或 `#elif`](https://zh.cppreference.com/w/c/preprocessor/conditional) 之后的表达式必须展开成

- [赋值](https://zh.cppreference.com/w/c/language/operator_assignment)、[自增、自减](https://zh.cppreference.com/w/c/language/operator_incdec)、[函数调用](https://zh.cppreference.com/w/c/language/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8)或[逗号](https://zh.cppreference.com/w/c/language/operator_other#.E9.80.97.E5.8F.B7.E8.BF.90.E7.AE.97.E7.AC.A6)以外的，参数为预处理器常量表达式的[运算符](https://zh.cppreference.com/w/c/language/expressions#.E8.BF.90.E7.AE.97.E7.AC.A6)
- [整数常量](https://zh.cppreference.com/w/c/language/integer_constant)
- [字符常量](https://zh.cppreference.com/w/c/language/character_constant)
- 特殊预处理器运算符 `defined`

​	字符常量在 `#if` 表达式中求值时，可能以源字符集、执行字符集或某个其他实现定义字符集转译。

​	`#if` 表达式中，对有符号类型以 [intmax_t](https://zh.cppreference.com/w/c/types/integer) 的语义，而对无符号类型以 [uintmax_t](https://zh.cppreference.com/w/c/types/integer) 的语义进行整数算术。(C99 起)

## 整数常量表达式

​	整数常量表达式是仅由下列内容组成的表达式

- [赋值](https://zh.cppreference.com/w/c/language/operator_assignment)、[自增、自减](https://zh.cppreference.com/w/c/language/operator_incdec)、[函数调用](https://zh.cppreference.com/w/c/language/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8)或[逗号](https://zh.cppreference.com/w/c/language/operator_other#.E9.80.97.E5.8F.B7.E8.BF.90.E7.AE.97.E7.AC.A6)以外的[运算符](https://zh.cppreference.com/w/c/language/expressions#.E8.BF.90.E7.AE.97.E7.AC.A6)，但[转换](https://zh.cppreference.com/w/c/language/cast)运算符只能转换算术类型为整数类型，除非它们是 `sizeof` 、`_Alignof`(C11 起)(C23 前)、`alignof`(C23 起) 或 `typeof/typeof_unqual`(C23 起) 运算符的操作数的一部分。
- [整数常量](https://zh.cppreference.com/w/c/language/integer_constant)
- [枚举常量](https://zh.cppreference.com/w/c/language/enum)
- [字符常量](https://zh.cppreference.com/w/c/language/character_constant)
- [浮点数常量](https://zh.cppreference.com/w/c/language/floating_constant)，但仅当其作为向整数类型转换的直接操作数
- `操作数非 VLA` 的(C99 起) [`sizeof`](https://zh.cppreference.com/w/c/language/sizeof) 运算符
- `_Alignof`(C23 前) `alignof`(C23 起) 运算符(C11 起)
- 具名的以及复合字面量常量，其为整数类型，或为算术类型且是显式转换的直接操作数 (C23 起)

​	整数常量表达式在编译时求值。下列语境要求被称为*整数常量表达式* ﻿的表达式：

- [位域](https://zh.cppreference.com/w/c/language/bit_field)的大小
- [枚举常量](https://zh.cppreference.com/w/c/language/enum)的值
- [switch 语句](https://zh.cppreference.com/w/c/language/switch)的 `case` 标号
- `非 VLA` (C99 起)数组的大小
- 整数到指针[隐式转换](https://zh.cppreference.com/w/c/language/conversion)。
- [数组指派符](https://zh.cppreference.com/w/c/language/array_initialization)的索引 (C99 起)
- [`_Static_assert`](https://zh.cppreference.com/w/c/language/_Static_assert) 的首参数[`_Alignof`](https://zh.cppreference.com/w/c/language/_Alignof)(C23 前)[`alignof`](https://zh.cppreference.com/w/c/language/alignof)(C23 起) 的整数参数 (C11 起)
- 位精确整数类型（`_BitInt(N)`）的位数 `N`  (C23 起)

## 静态初始化式

​	拥有静态和线程局域[存储期](https://zh.cppreference.com/w/c/language/storage_duration)或者以存储类说明符 constexpr 所声明(C23 起)的对象的[初始化式](https://zh.cppreference.com/w/c/language/initialization)中使用的表达式，必须是下列表达式之一

1) *算术常量表达式*，即由下列内容构成的任何算术类型表达式
   - [赋值](https://zh.cppreference.com/w/c/language/operator_assignment)、[自增、自减](https://zh.cppreference.com/w/c/language/operator_incdec)、[函数调用](https://zh.cppreference.com/w/c/language/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8)或[逗号](https://zh.cppreference.com/w/c/language/operator_other#.E9.80.97.E5.8F.B7.E8.BF.90.E7.AE.97.E7.AC.A6)以外的[运算符](https://zh.cppreference.com/w/c/language/expressions#.E8.BF.90.E7.AE.97.E7.AC.A6)，但[转换](https://zh.cppreference.com/w/c/language/cast)运算符必须转换算术类型到其他算术类型，除非它们是 `sizeof` 、`_Alignof`(C11 起)(C23 前)、`alignof`(C23 起) 或 `typeof/typeof_unqual`(C23 起) 运算符的操作数的一部分
   - [整数常量](https://zh.cppreference.com/w/c/language/integer_constant)
   - [浮点数常量](https://zh.cppreference.com/w/c/language/floating_constant)
   - [枚举常量](https://zh.cppreference.com/w/c/language/enum)
   - [字符常量](https://zh.cppreference.com/w/c/language/character_constant)
   - 操作数非 VLA 的 (C99 起)[`sizeof`](https://zh.cppreference.com/w/c/language/sizeof) 运算符
   - [`_Alignof`](https://zh.cppreference.com/w/c/language/_Alignof)(C23 前)[`alignof`](https://zh.cppreference.com/w/c/language/alignof)(C23 起) 运算符(C11 起)
   - 算术类型的具名的以及复合字面量常量 (C23 起)



2) 空指针常量（比如 [NULL](https://zh.cppreference.com/w/c/types/NULL)）
3) *地址常量表达式*，即
   - 空指针
   - 指代静态[存储期](https://zh.cppreference.com/w/c/language/storage_duration)的对象的[左值](https://zh.cppreference.com/w/c/language/value_category)，或函数指代器，通过下列方式之一转换为指针
     - 用一元取址运算符
     - 转换整数常量到指针
     - 数组到指针或函数到指针[隐式转换](https://zh.cppreference.com/w/c/language/conversion)

4. 某完整对象类型的*地址常量表达式*加或减一个*整数常量表达式*

5. *具名常量*，为以下标识符  (C23 起)

   - 枚举常量
   - 预定义常量（`true`、`false` 或 `nullptr`）
   - 以存储类说明符 `constexpr` 和对象类型声明的变量或者（递归地）在结构体或联合体类型的具名常量上应用成员访问运算符 `.` 的后缀表达式。

6. *复合字面量常量*，为 (C23 起)

   - 带有存储类说明符 `constexpr` 的[复合字面量](https://zh.cppreference.com/w/c/language/compound_literal)

   - （递归地）在结构体或联合体类型的复合字面量常量上应用成员访问运算符 `.` 的后缀表达式。

     *结构体或联合体常量*分别是具有结构体或联合体类型的具名常量或复合字面量常量。如果成员访问运算符 `.` 访问的是联合体常量的成员，则所访问的成员应当与该联合体常量的初始化式所初始化的成员相同。

7) 实现所接受的其他形式之一的常量表达式。

​	不同于整数常量表达式，不要求静态初始化器在编译时求值；编译器有将这种初始化器转变为在程序启动前调用的可执行代码的自由。

```c
static int i = 2 || 1 / 0; // 初始化 i 为值 1
```

> 本节未完成 
>
> 原因：其他小示例

​	浮点数静态初始化器的值的精度决不低于在运行时执行的同一表达式，但可以高于后者。

## 浮点数常量表达式

​	不用于静态初始化器中的浮点数类型的算术常量表达式，始终如同在运行时求值，受[当前舍入](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)影响（若 [`FENV_ACCESS`](https://zh.cppreference.com/w/c/preprocessor/impl) 为 ON），并报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误。

```c
void f(void)
{
#pragma STDC FENV_ACCESS ON
    static float x = 0.0/0.0; // 静态初始化器：不引发异常
    float w[] = { 0.0/0.0 };  // 引发异常
    float y = 0.0/0.0;        // 引发异常
    double z = 0.0/0.0;       // 引发异常
}
```

## 注解

​	若表达式求值到的值不能以其类型表示，则不能以之为常量表达式。

​	实现可以接受其他形式的常量表达式。然而，这些常量表达式不被认为是整数常量表达式、算术常量表达式或地址常量表达式，从而不能用于要求这些种类的常量表达式的语境。例如 int arr[(int)+1.0]; 声明一个 VLA。

## 参阅

**常量表达式**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/constant_expression)**