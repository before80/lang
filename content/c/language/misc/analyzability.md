+++
title = "可分析性"
date = 2025-04-13T14:44:02+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/analyzability](https://zh.cppreference.com/w/c/language/analyzability)

​	C 语言的此扩展限制某些未定义行为潜在执行结果，这会提升程序的静态语法分析的有效性。只有编译器定义了[预定义宏常量]({{< ref "/c/language/preprocessor/replace" >}}) `__STDC_ANALYZABLE__` (C11)，可分析性 (analyzability) 才保证可用。

​	若编译器支持可分析性，任何行为未定义的语言或库构造可以进一步分为*严格*未定义行为和*有界*未定义行为，且所有有界 UB 的情况以下文方式限制。

## 严格未定义行为

​	严格 UB 是可能在任何对象之外进行内存写入或易失内存读的未定义行为。拥有严格未定义行为的程序可能存在安全漏洞。

仅下列未定义行为是严格的：

- 在[生存期]({{< ref "/c/language/basic_concepts/lifetime" >}})外访问对象（例如：通过悬垂指针）
- 写入声明为不[兼容类型](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)的对象
- 通过与所指向函数类型不[兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)的函数指针调用函数
- 求值[左值表达式]({{< ref "/c/language/expressions/value_category" >}})，但其不指代一个对象
- 试图修改[字符串字面量]({{< ref "/c/language/expressions/string_literal" >}})
- [解引用]({{< ref "/c/language/expressions/operator_member_access" >}})无效（空的、不确定的等）或[尾后]({{< ref "/c/language/expressions/operator_arithmetic" >}})指针
- 通过非 const 指针修改 [const 对象]({{< ref "/c/language/declarations/const" >}})
- 以无效实参调用标准库函数或标准库宏
- 以不期待的实参类型调用变参数的标准库函数（例如：以不匹配其转换指定符的参数调用 [printf](https://zh.cppreference.com/w/c/io/fprintf)）
- 当调用 [longjmp](https://zh.cppreference.com/w/c/program/longjmp) 时，调用作用域以上没有 [setjmp](https://zh.cppreference.com/w/c/program/setjmp)，该调用跨线程，或者是在动态修改（VM）类型的作用域中调用
- 使用已被 [free](https://zh.cppreference.com/w/c/memory/free) 或 [realloc](https://zh.cppreference.com/w/c/memory/realloc) 解分配的指针
- 任何[字符串]({{< ref "/c/string/byte" >}})或[宽字符串]({{< ref "/c/string/wide" >}})库函数访问数组时发生越界

## 有界未定义行为

​	有界 UB 是不进行非法内存写操作的未定义行为，但它可能触发陷阱、产生或存储不确定值。

- 任何不列作严格的未定义行为是有界的，包括：
  - 多线程数据竞争
  - 使用拥有自动存储期的[不确定值]({{< ref "/c/language/initialization" >}})
  - 违规使用[严格别名]({{< ref "/c/language/basic_concepts/object#.E4.B8.A5.E6.A0.BC.E5.88.AB.E5.90.8D.E4.BD.BF.E7.94.A8" >}})
  - 访问[错误对齐]({{< ref "/c/language/basic_concepts/object#.E5.AF.B9.E9.BD.90" >}})的对象
  - 有符号整数溢出
  - [无定序副作用]({{< ref "/c/language/expressions/eval_order" >}})之间修改了相同标量或者修改并读取相同标量
  - 浮点到整数或指针到整数[转换]({{< ref "/c/language/expressions/conversion" >}})溢出
  - 以负值或过大位数[逐位左移]({{< ref "/c/language/expressions/operator_arithmetic" >}})
  - 除以零的[整除]({{< ref "/c/language/expressions/operator_arithmetic" >}})
  - 使用 void 表达式
  - 直接[赋值]({{< ref "/c/language/expressions/operator_assignment" >}})或 [memcpy](https://zh.cppreference.com/w/c/string/byte/memcpy) 并未严格内存重叠的对象
  - 违规使用 [restrict]({{< ref "/c/language/declarations/restrict" >}})
  - 等等……所有不在严格列表中的未定义行为。



## 注意

​	有界未定义行为禁用某些优化：启用可分析性的编译过程会保留源代码因果关系，某些未定义行为[可能会违犯]({{< ref "/c/language/basic_concepts/as_if" >}})它。

​	可分析性扩展，允许以实现定义行为的形式在触发陷阱时调用[运行时制约处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)。
