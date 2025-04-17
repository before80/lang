+++
title = "标点"
date = 2025-04-11T19:57:43+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/punctuators](https://zh.cppreference.com/w/c/language/punctuators)

​	这些是 C 中的标点符号。每个符号的含义在链接的页面中详述。

## `{` `}`

- 在[结构体]({{< ref "/c/language/declarations/struct" >}})或[联合体]({{< ref "/c/language/declarations/union" >}})定义中划分出*结构体声明列表*。
- 在[枚举]({{< ref "/c/language/declarations/enum" >}})定义中划分出枚举项列表。
- 划分出[复合语句]({{< ref "/c/language/statements#.E5.A4.8D.E5.90.88.E8.AF.AD.E5.8F.A5" >}})。复合语句可以是[函数定义]({{< ref "/c/language/functions/function_definition" >}})的一部分。
- [初始化]({{< ref "/c/language/initialization" >}})时，划分出初始化式列表。

## `[` `]`

- [下标运算符]({{< ref "/c/language/expressions/operator_member_access#.E4.B8.8B.E6.A0.87" >}})。
- [声明]({{< ref "/c/language/declarations" >}})或[类型标识]({{< ref "/c/language/basic_concepts/type#.E7.B1.BB.E5.9E.8B.E5.90.8D" >}})中，[数组声明符]({{< ref "/c/language/declarations#Declarators" >}})的一部分。
- [初始化]({{< ref "/c/language/initialization" >}})时，引入数组元素的指派符。(C99 起)
- [属性说明符]({{< ref "/c/language/declarations/attributes" >}})中，划分出属性。(C23 起)

## `#`

- 引入[预处理指令]({{< ref "/c/language/preprocessor" >}})。
- [用于字符串化的预处理运算符]({{< ref "/c/language/preprocessor/replace#.23_.E4.B8.8E_.23.23_.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。

## `##`

- [用于记号粘贴的预处理运算符]({{< ref "/c/language/preprocessor/replace#.23_.E4.B8.8E_.23.23_.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。

## `(` `)`

- 表达式中指定[分组]({{< ref "/c/language/expressions#.E5.88.9D.E7.AD.89.E8.A1.A8.E8.BE.BE.E5.BC.8F" >}})，改变结合顺序。
- [函数调用运算符]({{< ref "/c/language/expressions/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8" >}})。
- [`sizeof`]({{< ref "/c/language/expressions/sizeof" >}})、[`_Alignof`]({{< ref "/c/language/expressions/_Alignof" >}})(C11 起)、[`typeof`](https://zh.cppreference.com/w/c/language/typeof) 或 [`typeof_unqual`](https://zh.cppreference.com/w/c/language/typeof_unqual) (C23 起)表达式中划分出操作数。
- [显式类型转换]({{< ref "/c/language/expressions/cast" >}})中划分出类型标识。
- [复合字面量]({{< ref "/c/language/expressions/compound_literal" >}})中划分出类型标识。(C99 起)
- [声明]({{< ref "/c/language/declarations" >}})或[类型标识]({{< ref "/c/language/basic_concepts/type#.E7.B1.BB.E5.9E.8B.E5.90.8D" >}})中指定分组，改变结合顺序。
- [函数声明符]({{< ref "/c/language/functions/function_declaration" >}})（[声明]({{< ref "/c/language/declarations" >}})或[类型标识]({{< ref "/c/language/basic_concepts/type#.E7.B1.BB.E5.9E.8B.E5.90.8D" >}})）中划分出形参列表。
- [`if`]({{< ref "/c/language/statements/if" >}})、[`switch`]({{< ref "/c/language/statements/switch" >}})、[`while`]({{< ref "/c/language/statements/while" >}})、[`do-while`]({{< ref "/c/language/statements/do" >}}) 或 [`for`]({{< ref "/c/language/statements/for" >}}) 语句中，划分出控制子句。
- [仿函数宏定义]({{< ref "/c/language/preprocessor/replace#.E4.BB.BF.E5.87.BD.E6.95.B0.E5.AE.8F" >}})中，划分出宏形参。
- [仿函数宏调用]({{< ref "/c/language/preprocessor/replace#.E4.BB.BF.E5.87.BD.E6.95.B0.E5.AE.8F" >}})中，划分出宏实参，或避免将逗号被判读为实参分隔符。
- `defined`、`__has_include`、`__has_embed` 或 `__has_c_attribute`(C23 起) 预处理运算符的一部分。
- [泛型选择表达式]({{< ref "/c/language/expressions/generic" >}})的一部分。(C11 起)
- [`_Atomic`]({{< ref "/c/language/declarations/atomic" >}}) 类型说明符中,划分出类型标识。(C11 起)
- [静态断言声明]({{< ref "/c/language/declarations/_Static_assert" >}})中，划分出操作数。(C11 起)
- [`_Alignas`]({{< ref "/c/language/declarations/_Alignas" >}}) 说明符中，划分出操作数。(C11 起)
- [属性]({{< ref "/c/language/declarations/attributes" >}})中, 划分出操作数。(C23 起)
- 位精确整数类型名（_BitInt(N)）中，划分出大小。(C23 起)
- 可变宏定义中的 [`__VA_OPT__`]({{< ref "/c/language/preprocessor/replace" >}}) 替换的一部分。(C23 起)
- [#embed 指令]({{< ref "/c/language/preprocessor/embed" >}})和 __has_embed 预处理器表达式中使用的预处理器形参中，划分出预处理器形参子句。(C23 起)

## `;`

- 如下语法的结束：

  - [语句]({{< ref "/c/language/statements" >}}) (含 for 循环的初始化子句)

  - [声明]({{< ref "/c/language/declarations" >}})或*结构体声明列表*

- 分隔 [for 语句]({{< ref "/c/language/statements/for" >}})中的第二和第三子句。

## `:`

- [条件运算符]({{< ref "/c/language/expressions/operator_other#.E6.9D.A1.E4.BB.B6.E8.BF.90.E7.AE.97.E7.AC.A6" >}})的一部分。
- [标签声明]({{< ref "/c/language/statements#.E6.A0.87.E7.AD.BE" >}})的一部分。
- [位域成员声明]({{< ref "/c/language/declarations/bit_field" >}})中，引入宽度。
- 引入[枚举基类型]({{< ref "/c/language/declarations/enum" >}})，指定枚举的底层类型。(C23 起)
- [泛型关联]({{< ref "/c/language/expressions/generic" >}})中，分隔类型标识或 default 和待选表达式。(C11 起)

## `...`

- 函数声明符的[形参列表]({{< ref "/c/language/functions/function_declaration#.E5.BD.A2.E5.8F.82.E5.88.97.E8.A1.A8" >}})中, 标志[变参函数]({{< ref "/c/language/functions/variadic" >}})。
- [宏定义]({{< ref "/c/language/preprocessor/replace" >}})中, 标志变参宏。 (C99 起)

## `?`

- [条件运算符]({{< ref "/c/language/expressions/operator_other#.E6.9D.A1.E4.BB.B6.E8.BF.90.E7.AE.97.E7.AC.A6" >}})的一部分。

## `::`

- 在[属性]({{< ref "/c/language/declarations/attributes" >}})中指示属性作用域。(C23 起)
- 在预处理器有前缀形参（[#embed]({{< ref "/c/language/preprocessor/embed" >}}) 和 __has_embed 所使用）中，指定作用域。(C23 起)

### `.`

- [成员访问运算符]({{< ref "/c/language/expressions/operator_member_access#.E6.88.90.E5.91.98.E8.AE.BF.E9.97.AE" >}})。
- 在[初始化]({{< ref "/c/language/initialization" >}})时，引入结构体/联合体成员指派符。(C99 起)

## `->`

- [成员访问运算符]({{< ref "/c/language/expressions/operator_member_access#.E9.80.9A.E8.BF.87.E6.8C.87.E9.92.88.E8.BF.9B.E8.A1.8C.E6.88.90.E5.91.98.E8.AE.BF.E9.97.AE" >}})。

## `~`

- [一元补运算符（又称逐位非运算符）]({{< ref "/c/language/expressions/operator_arithmetic#.E9.80.90.E4.BD.8D.E9.80.BB.E8.BE.91" >}})。

## `!`

- [逻辑非运算符]({{< ref "/c/language/expressions/operator_logical#.E9.80.BB.E8.BE.91.E9.9D.9E" >}})。

## `+`

- [一元加法运算符（正号）]({{< ref "/c/language/expressions/operator_arithmetic#.E4.B8.80.E5.85.83.E7.AE.97.E6.9C.AF" >}})。
- [二元加法运算符]({{< ref "/c/language/expressions/operator_arithmetic#.E5.8A.A0.E6.B3.95.E6.80.A7.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。

## `-`

- [一元减法运算符（负号）]({{< ref "/c/language/expressions/operator_arithmetic#.E4.B8.80.E5.85.83.E7.AE.97.E6.9C.AF" >}})。
- [二元减法运算符]({{< ref "/c/language/expressions/operator_arithmetic#.E5.8A.A0.E6.B3.95.E6.80.A7.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。

## `*`

- [间接引用运算符（也称解引用运算符）]({{< ref "/c/language/expressions/operator_member_access#.E8.A7.A3.E5.BC.95.E7.94.A8" >}})。
- [乘法运算符]({{< ref "/c/language/expressions/operator_arithmetic#.E4.B9.98.E6.B3.95.E6.80.A7.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。
- [声明符]({{< ref "/c/language/declarations#.E5.A3.B0.E6.98.8E.E7.AC.A6" >}})或[类型标识]({{< ref "/c/language/basic_concepts/type#.E7.B1.BB.E5.9E.8B.E5.90.8D" >}})中的指针运算符或成员指针运算符。
- 在[函数声明]({{< ref "/c/language/functions/function_declaration" >}})的变长数组声明中的数组长度占位符。(C99 起)

## `/`

- [除法运算符]({{< ref "/c/language/expressions/operator_arithmetic#.E4.B9.98.E6.B3.95.E6.80.A7.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。

## `%`

- [取余运算符（取模运算符）]({{< ref "/c/language/expressions/operator_arithmetic#.E4.B9.98.E6.B3.95.E6.80.A7.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。

## `^`

- [逐位异或运算符]({{< ref "/c/language/expressions/operator_arithmetic#.E9.80.90.E4.BD.8D.E9.80.BB.E8.BE.91" >}})。

## `&`

- [取地址运算符]({{< ref "/c/language/expressions/operator_member_access#.E5.8F.96.E5.9D.80" >}})。
- [逐位与运算符]({{< ref "/c/language/expressions/operator_arithmetic#.E9.80.90.E4.BD.8D.E9.80.BB.E8.BE.91" >}})。

## `|`

- [逐位或运算符]({{< ref "/c/language/expressions/operator_arithmetic#.E9.80.90.E4.BD.8D.E9.80.BB.E8.BE.91" >}})。

## `=`

- [简单赋值运算符]({{< ref "/c/language/expressions/operator_assignment#.E7.AE.80.E5.8D.95.E8.B5.8B.E5.80.BC" >}})。
- 在[初始化]({{< ref "/c/language/initialization" >}})中，分隔对象和初始化式列表。
- 在[枚举定义]({{< ref "/c/language/declarations/enum" >}})中引入枚举常量的值。

## `+=`

- [复合赋值运算符]({{< ref "/c/language/expressions/operator_assignment#.E5.A4.8D.E5.90.88.E8.B5.8B.E5.80.BC" >}})。

## `-=`

- [复合赋值运算符]({{< ref "/c/language/expressions/operator_assignment#.E5.A4.8D.E5.90.88.E8.B5.8B.E5.80.BC" >}})。

## `*=`

- [复合赋值运算符]({{< ref "/c/language/expressions/operator_assignment#.E5.A4.8D.E5.90.88.E8.B5.8B.E5.80.BC" >}})。

## `/=`

- [复合赋值运算符]({{< ref "/c/language/expressions/operator_assignment#.E5.A4.8D.E5.90.88.E8.B5.8B.E5.80.BC" >}})。

## `%=`

- [复合赋值运算符]({{< ref "/c/language/expressions/operator_assignment#.E5.A4.8D.E5.90.88.E8.B5.8B.E5.80.BC" >}})。

## `^=`

- [复合赋值运算符]({{< ref "/c/language/expressions/operator_assignment#.E5.A4.8D.E5.90.88.E8.B5.8B.E5.80.BC" >}})。

## `&=`

- [复合赋值运算符]({{< ref "/c/language/expressions/operator_assignment#.E5.A4.8D.E5.90.88.E8.B5.8B.E5.80.BC" >}})。

## `|=`

- [复合赋值运算符]({{< ref "/c/language/expressions/operator_assignment#.E5.A4.8D.E5.90.88.E8.B5.8B.E5.80.BC" >}})。

## `==`

- [等于运算符]({{< ref "/c/language/expressions/operator_comparison#.E7.9B.B8.E7.AD.89.E6.80.A7.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。

## `!=`

- [不等于运算符]({{< ref "/c/language/expressions/operator_comparison#.E7.9B.B8.E7.AD.89.E6.80.A7.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。

## `<`

- [小于运算符]({{< ref "/c/language/expressions/operator_comparison#.E5.85.B3.E7.B3.BB.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。

- 引入以下情况中的头文件名

  - [#include 指令]({{< ref "/c/language/preprocessor/include" >}})

  - [__has_include 预处理表达式]({{< ref "/c/language/preprocessor/include" >}}) (C23 起)

  - [#embed 指令]({{< ref "/c/language/preprocessor/embed" >}}) (C23 起)

  - [__has_embed 预处理表达式]({{< ref "/c/language/preprocessor/embed" >}}) (C23 起)

  - [`#pragma` 指令](https://zh.cppreference.com/w/c/preprocessor/impl)中由实现定义的位置

## `>`

- [大于运算符]({{< ref "/c/language/expressions/operator_comparison#.E5.85.B3.E7.B3.BB.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。

- 指定以下情况中的头文件名结束

  - [#include 指令]({{< ref "/c/language/preprocessor/include" >}})

  - [__has_include 预处理表达式]({{< ref "/c/language/preprocessor/include" >}}) (C23 起)

  - [#embed 指令]({{< ref "/c/language/preprocessor/embed" >}}) (C23 起)

  - [__has_embed 预处理表达式]({{< ref "/c/language/preprocessor/embed" >}}) (C23 起)

  - [`#pragma` 指令](https://zh.cppreference.com/w/c/preprocessor/impl)中由实现定义的位置

## `<=`

- [小于等于运算符]({{< ref "/c/language/expressions/operator_comparison#.E5.85.B3.E7.B3.BB.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。

## `>=`

- [大于等于运算符]({{< ref "/c/language/expressions/operator_comparison#.E5.85.B3.E7.B3.BB.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。

## `&&`

- [逻辑与运算符]({{< ref "/c/language/expressions/operator_logical#.E9.80.BB.E8.BE.91.E4.B8.8E" >}})。

## `||`

- [逻辑或运算符]({{< ref "/c/language/expressions/operator_logical#.E9.80.BB.E8.BE.91.E6.88.96" >}})。

## `<<`

- [移位运算符]({{< ref "/c/language/expressions/operator_arithmetic#.E7.A7.BB.E4.BD.8D.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。

## `>>`

- [移位运算符]({{< ref "/c/language/expressions/operator_arithmetic#.E7.A7.BB.E4.BD.8D.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。

## `<<=`

- [复合赋值运算符]({{< ref "/c/language/expressions/operator_assignment#.E5.A4.8D.E5.90.88.E8.B5.8B.E5.80.BC" >}})。

## `>>=`

- [复合赋值运算符]({{< ref "/c/language/expressions/operator_assignment#.E5.A4.8D.E5.90.88.E8.B5.8B.E5.80.BC" >}})。

## `++`

- [自增运算符]({{< ref "/c/language/expressions/operator_incdec" >}})。

## `--`

- [自减运算符]({{< ref "/c/language/expressions/operator_incdec" >}})。

## `,`

- [逗号运算符]({{< ref "/c/language/expressions/operator_other#.E9.80.97.E5.8F.B7.E8.BF.90.E7.AE.97.E7.AC.A6" >}})。

- 以下列表的列表分隔符：

  - [声明]({{< ref "/c/language/declarations" >}})中的声明符列表

  - [初始化]({{< ref "/c/language/initialization" >}})，包括[复合字面量]({{< ref "/c/language/expressions/compound_literal" >}})(C99 起)中的初始化式列表

  - [函数调用]({{< ref "/c/language/expressions/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8" >}})中的实参列表

  - [枚举]({{< ref "/c/language/declarations/enum" >}})声明中的枚举项列表

  - 函数形参列表

  - [仿函数宏定义]({{< ref "/c/language/preprocessor/replace#.E4.BB.BF.E5.87.BD.E6.95.B0.E5.AE.8F" >}})中的宏形参列表

  - [仿函数宏调用]({{< ref "/c/language/preprocessor/replace#.E4.BB.BF.E5.87.BD.E6.95.B0.E5.AE.8F" >}})中的宏实参列表，除非出现于内部括号对之内

  - [泛型选择表达式]({{< ref "/c/language/expressions/generic" >}})中泛型关联列表 (C11 起)

  - [属性]({{< ref "/c/language/declarations/attributes" >}})列表 (C23 起)

- [静态断言声明]({{< ref "/c/language/declarations/_Static_assert" >}})中分隔各实参。(C11 起)
- [泛型选择表达式]({{< ref "/c/language/expressions/generic" >}})中，分隔控制表达式和泛型关联列表。(C11 起)



## 参阅

[代用表示](https://zh.cppreference.com/w/c/language/operator_alternative) (C95) 某些运算符的代用拼写

**标点**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/punctuators)**
