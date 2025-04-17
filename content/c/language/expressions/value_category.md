+++
title = "值类别"
date = 2025-04-12T16:42:20+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/value_category](https://zh.cppreference.com/w/c/language/value_category)

​	C 中每个[表达式]({{< ref "/c/language/expressions" >}})（带有实参的运算符、函数调用、常量、变量名等）以两个独立属性刻画：[类型](https://zh.cppreference.com/w/c/language/types#.E7.B1.BB.E5.9E.8B)和[值类别]({{< ref "/c/language/expressions#.E7.BB.BC.E8.BF.B0" >}})。

​	每个表达式属于三个值类别之一：左值、非左值对象（右值）以及函数指代器。

## 左值表达式

​	左值表达式是除类型 void 之外的任何[对象类型]({{< ref "/c/language/basic_concepts/type#.E7.B1.BB.E5.9E.8B.E7.BB.84.E5.88.AB" >}})，且隐含地指代一个[对象]({{< ref "/c/language/basic_concepts/object" >}})的表达式（当左值在求值时不实际指代一个对象时，行为未定义）。换言之，左值表达式求值得到*对象标识* ﻿。此值类别的名称（“左值”）是历史性的，并反映了 CPL 中，左值表达式作为赋值运算符的左运算数。

​	左值表达式可用于下列*左值语境* ﻿：

- 作为[取址运算符]({{< ref "/c/language/expressions/operator_member_access" >}})的操作数（除了指代[位域]({{< ref "/c/language/declarations/bit_field" >}})或声明为 [register]({{< ref "/c/language/declarations/storage_duration" >}}) 的左值）。
- 作为前/后[自增减运算符]({{< ref "/c/language/expressions/operator_incdec" >}})的操作数。
- 作为[成员访问]({{< ref "/c/language/expressions/operator_member_access" >}})（点）运算符的左操作数。
- 作为[赋值及复合赋值]({{< ref "/c/language/expressions/operator_assignment" >}})运算符的左操作数。

​	若将左值表达式用于除 [`sizeof`]({{< ref "/c/language/expressions/sizeof" >}})、[`_Alignof`]({{< ref "/c/language/expressions/_Alignof" >}}) 或上述的运算符之外的语境，则任何完整类型的非数组左值会经历[左值转换]({{< ref "/c/language/expressions/conversion" >}})，这模仿的是从对象位置到其值的内存加载。同样地，在用于除 `sizeof`、`_Alignof`、取址运算符或从字符串字面量初始化数组之外的语境时，数组左值会经历[数组到指针转换]({{< ref "/c/language/expressions/conversion" >}})。

​	[`const`]({{< ref "/c/language/declarations/const" >}})/[`volatile`]({{< ref "/c/language/declarations/volatile" >}})/[`restrict`]({{< ref "/c/language/declarations/restrict" >}}) 限定符和[原子]({{< ref "/c/language/declarations/atomic" >}})类型的语义仅应用于左值（左值转换将剥除限定符并移除原子属性）。

​	下列表达式是左值：

- 标识符，含具名函数形参，只要声明它们为指代对象（而非函数或枚举常量）
- [字符串字面量]({{< ref "/c/language/expressions/string_literal" >}})
- (C99) [复合字面量]({{< ref "/c/language/expressions/compound_literal" >}})
- 括号表达式，若其无括号版本是左值
- 成员访问（点）运算符的结果，若其左参数是左值
- 通过指针访问成员（`->`）运算符的结果
- 对指向对象指针运用间接使用（一元 `*`）运算符的结果
- 下标运算符的结果（`[]`）

### 可修改左值表达式

​	一个*可修改左值*是任何完整的非数组类型的、非 [const]({{< ref "/c/language/declarations/const" >}}) 限定的左值表达式，而且若它是结构体/联合体，则递归地没有任何成员为 [const]({{< ref "/c/language/declarations/const" >}}) 限定。

​	只有可修改左值表达式可用作自增减运算符的实参，赋值和复合赋值运算符的左实参。

## 非左值对象表达式

​	称为*右值* ﻿，非左值表达式是对象类型的表达式，它不指代对象，而是指代没有对象身份或存储位置的值。不能对非左值表达式取址。

​	下列表达式是非左值对象表达式：

- 整数、字符、浮点数常量
- 所有不返回左值的运算符，包括
  - 任何函数调用表达式
  - 任何转型表达式（注意看起来相似的复合字面量是左值）
  - 作用于非左值结构体/联合体的成员访问（点）运算符，f().x、(x,s1).a、(s1=s2).m
  - 所有算术、关系、逻辑及位运算符的结果
  - 自增和自减运算符（注意：前置形式在 C++ 中是左值）的结果
  - 赋值及复合赋值运算符（注意：它们在 C++ 中也是左值）的结果
  - 条件运算符（注意：在 C++ 中，如果第二和第三个操作数为相同类型的左值则为左值）
  - 逗号运算符（注意：在 C++ 中，如果第二个操作数是左值则为左值）
  - 取址运算符，即使它被用一元 `*` 运算符的结果中和



​	作为特殊情况，`void` 类型表达式被假设成非左值对象表达式，得出一个不存在表示且不要求存储的值。

> 注意
>
> ​	拥有一个数组类型成员（可以是嵌套的）的结构体/联合体右值实际上指代一个拥有[临时生存期]({{< ref "/c/language/basic_concepts/lifetime" >}})的对象。此对象可通过由索引数组元素组成的左值表达式，或解引用该数组的数组到指针转换所得的指针来访问。(C99 起)

## 函数指代符表达式

​	函数指代符（由[函数声明]({{< ref "/c/language/functions/function_declaration" >}})引入的标识符）是函数类型的表达式。当在异于取址运算符、 [`sizeof`]({{< ref "/c/language/expressions/sizeof" >}}) 及 [`_Alignof`]({{< ref "/c/language/expressions/_Alignof" >}})（后两者在作用于函数时生成编译错误）的语境中时，函数指代符始终转换成指向函数的非左值指针。注意函数调用运算符是对指向函数指针，而非对函数指代符自身定义的。

## 参阅

值类别的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/value_category)
