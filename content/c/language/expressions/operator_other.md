+++
title = "其他运算符"
date = 2025-04-12T21:19:36+08:00
weight = 210
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/operator_other](https://zh.cppreference.com/w/c/language/operator_other)

​	汇集并不适合任何其他主要类别的运算符。

> 本节未完成 
>
> 原因：为这个和其他表格考虑更通用的，覆盖多个专题的 ToC

|       运算符        |                           运算符名                           |       示例       |                             描述                             |
| :-----------------: | :----------------------------------------------------------: | :--------------: | :----------------------------------------------------------: |
|       `(...)`       | [函数调用]({{< ref "/c/language/expressions/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8" >}}) |     `f(...)`     |                    以零或更多实参调用 f()                    |
|         `,`         | [逗号运算符]({{< ref "/c/language/expressions/operator_other#.E9.80.97.E5.8F.B7.E8.BF.90.E7.AE.97.E7.AC.A6" >}}) |      `a, b`      | 求值表达式 a，舍弃其返回值并完成任何副效应，然后求值表达式 b，返回此求值的类型和结果 |
|      `(type)`       |    [转型]({{< ref "/c/language/expressions/cast" >}})     |    `(type)a`     |                     转型 a 的类型为 type                     |
|        `? :`        | [条件运算符]({{< ref "/c/language/expressions/operator_other#.E6.9D.A1.E4.BB.B6.E8.BF.90.E7.AE.97.E7.AC.A6" >}}) |   `a ? b : c`    | 若 a 逻辑上为真（不求值为零）则求值表达式 b，否则求值表达式 c |
|      `sizeof`       | [sizeof 运算符]({{< ref "/c/language/expressions/sizeof" >}}) |    `sizeof a`    |                         a 的字节大小                         |
| `_Alignof` (C11 起) | [_Alignof 运算符]({{< ref "/c/language/expressions/_Alignof" >}}) | `_Alignof(type)` |                       type 的对齐要求                        |
|      `typeof`       | [typeof 运算符](https://zh.cppreference.com/w/c/language/typeof) |   `typeof(a)`    |                           a 的类型                           |

## 函数调用

​	函数调用表达式拥有形式：

*表达式* `(` *实参列表* ﻿(可选) `)`

​	其中

| *表达式*   | -    | 任何指向函数指针类型的表达式（在[左值转换]({{< ref "/c/language/expressions/conversion#.E5.B7.A6.E5.80.BC.E8.BD.AC.E6.8D.A2" >}})后） |
| ---------- | ---- | ------------------------------------------------------------ |
| *实参列表* | -    | 任何完整对象类型的表达式（不能是逗号运算符）的逗号分隔列表。调用不接受实参的函数时可以省略。 |

​	函数调用表达式的行为，取决于所调用的函数的原型是否在调用点[处于作用域中]({{< ref "/c/language/basic_concepts/scope" >}})。

### 调用有原型函数

1) 形参数量必须等于实参数量（除非使用省略号形参）。

2) 必须存在[如同赋值的隐式转换]({{< ref "/c/language/expressions/conversion" >}})，将对应实参的无限定类型转换为形参类型。

    另外，对于每个在 `[` 和 `]` 间使用关键词 `static` 的[数组类型]({{< ref "/c/language/declarations/array" >}})形参，实参表达式所指代的数组元素数，必须不少于形参的大小表达式中指定的数量。(C99 起)

3) [以未指定顺序无序地]({{< ref "/c/language/expressions/eval_order" >}})求值各实参。

4) 进行[赋值]({{< ref "/c/language/expressions/operator_assignment" >}})，复制每个实参到对应的函数形参，忽略形参类型及其可能为递归的元素或成员上的类型限定符，若存在（注意：函数能修改其形参，而这些修改不影响实参，C 函数调用只有按值调用）。

   - 若有[尾随省略号]({{< ref "/c/language/functions/variadic" >}})形参，则在剩余实参上进行[默认实参提升](https://zh.cppreference.com/mwiki/index.php?title=conversion&action=edit&redlink=1)，这使得它们可由 va_list 访问。

5) 执行函数，而其返回值成为函数调用表达式的值（若函数返回 void，则函数调用表达式为 void 表达式）。

```c
void f(char* p, int x) {}
int main(void)
{
    f("abc", 3.14); // 数组到指针和 float 到 int 转换
}
```

### 调用无原型函数

1. [以未指定顺序无定序地]({{< ref "/c/language/expressions/eval_order" >}})求值各实参。

2. 在每个实参表达式上进行[默认实参提升]({{< ref "/c/language/expressions/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87" >}})。

3. 进行[赋值]({{< ref "/c/language/expressions/operator_assignment" >}})，复制每个实参到对应的函数形参，忽略形参类型及其可能为递归的元素或成员上的类型限定符，若存在。

4. 执行函数，而其所返回的值成为函数调用表达式的值（若函数返回 void，则函数调用表达式为 void 表达式）

   ```c
   void f(); // 无原型
   int main(void)
   {
       f(1, 1.0f); // UB，除非定义 f 为接收一个 int 和一个 double
   }
   void f(int a, double c) {}
   ```

   

​	以下情况下调用无原型函数的行为未定义

- 实参数量不匹配形参数量
- 提升后的实参类型与提升后形参类型不[兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)，除了
  - 若实参的值以两个类型均可表示，则认为相同整数类型的有符号和无符号版本兼容。
  - 认为指向 void 指针和指向（可有 cvr 限定的）字符类型指针兼容

### 注解

​	指代所调用的函数的 *表达式* 和所有实参的求值，互相之间[无定序]({{< ref "/c/language/expressions/eval_order" >}})（但在函数开始执行前有一个序列点）

```c
(*pf[f1()]) (f2(), f3() + f4()); // 可以以任何顺序调用 f1、f2、f3、f4
```

​	尽管函数调用只对指向函数指针定义，它亦能作用于函数指代符，因为[函数到指针隐式转换]({{< ref "/c/language/expressions/conversion#.E5.87.BD.E6.95.B0.E5.88.B0.E6.8C.87.E9.92.88.E8.BD.AC.E6.8D.A2" >}})。

```c
int f(void) { return 1; }
int (*pf)(void) = f;
 
int main(void)
{
    f();    // 转换 f 为指针，然后调用
    (&f)(); // 创建指向函数指针，然后调用
 
    pf();    // 调用函数
    (*pf)(); // 获得函数指代器，转换为指针，然后滴啊用、
 
    (f)(); // 转换为指针，获得函数，重复 4 次，然后调用
    (pf)(); // 亦 OK
}
```

​	必须用在作用域中的原型调用忽略不使用实参的函数，如 [printf](https://zh.cppreference.com/w/c/io/fprintf)（这种函数的原型需要使用[尾随省略号]({{< ref "/c/language/functions/variadic" >}})形参），以避免未定义行为。

​	当前准备函数形参的语义的标准遣词是有缺陷的，因为它指定在调用时形参从实参赋值，这错误地拒绝了 const 限定的形参或成员类型，并且不恰当地应用了在许多平台上对于函数形参无法实现的 volatile 语义。C11 后的缺陷报告 [DR427](https://open-std.org/JTC1/SC22/WG14/www/docs/n2396.htm#dr_427) 提议将该语义从赋值改为初始化，但被作为非缺陷关闭。

​	其 *表达式* 完全由一个标识符组成，而未声明该标识符的函数调用表达式，表现为通过将该标识符声明如下：(C99 前)

```c
extern int identifier(); // 返回 int 且无原型
```

​	故下列完整程序在 C89 中合法：(C99 前)

```c
main() {
    int n = atoi("123"); // 隐式声明 atoi 为 int atoi()
}
```



## 逗号运算符

​	逗号运算符表达式的形式为：

*lhs* `,` *rhs*

其中

| *lhs* | -    | 任何表达式                                                   |
| ----- | ---- | ------------------------------------------------------------ |
| *rhs* | -    | 除了另一逗号运算符外的任何表达式（换言之，逗号运算符的[结合性]({{< ref "/c/language/expressions/operator_precedence" >}})为从左到右） |

​	首先，求值左运算数 *lhs* 并舍弃其结果值。

​	然后，发生[序列点]({{< ref "/c/language/expressions/eval_order" >}})，从而 *lhs* 的所有副效应完成。

​	然后，求值右运算数 *rhs*，而逗号运算符作为[非左值]({{< ref "/c/language/expressions/value_category" >}})返回其结果。

## 注意

​	*lhs* 的类型可为 void（即可为对返回 void 的函数的调用，或能为 [转型]({{< ref "/c/language/expressions/cast" >}})到 void 的表达式）。

​	逗号运算符在 C++ 中可为左值，但 C 中决不是。

​	逗号运算符可返回结构体（其他返回结构体的表达式仅有复合字面量、函数调用、赋值和条件运算符）。

​	下列语境中，逗号运算符不能出现于表达式的顶层，因为逗号有不同含义：

- 函数调用中的实参列表
- 初始化式表达式或[初始化式列表]({{< ref "/c/language/initialization" >}})
- [泛型选择]({{< ref "/c/language/expressions/generic" >}})

​	若必须在这种语境中使用逗号运算符，则必须加括号：

```c
// int n = 2,3; // 错误：认为逗号开始下个声明器
// int a[2] = {1,2,3}; // 错误：初始化器多于元素
int n = (2,3), a[2] = {(1,2),3}; // OK
 
f(a, (t=3, t+2), c); // OK：存储 3 于 t，然后以三个参数调用 f
```

​	数组边界中亦禁止顶层逗号

```c
// int a[2,3]; // 错误
int a[(2,3)]; // OK：大小为 3 的 VLA 数组（因为 (2, 3) 不是常量表达式，故为 VLA）
```

​	[常量表达式]({{< ref "/c/language/expressions/constant_expression" >}})中不允许逗号，不管它是否出现于顶层

```c
// static int n = (1,2); // 错误：常量表达式不能调用逗号运算符
```

## 转型运算符

​	见[转型运算符]({{< ref "/c/language/expressions/cast" >}})

## 条件运算符

​	条件运算符表达式的形式为：

*条件* `?` *表达式真* `:` *表达式假*

其中

| *条件*     | -    | 标量类型的表达式                   |
| ---------- | ---- | ---------------------------------- |
| *表达式真* | -    | 当条件比较不等于零时将求值的表达式 |
| *表达式假* | -    | 当条件比较等于零时将求值的表达式   |

​	仅允许下列表达式为 *表达式真* 和 *表达式假*

- 两个任何[算术]({{< ref "/c/language/basic_concepts/arithmetic_types" >}})类型的表达式
- 两个相同[结构体]({{< ref "/c/language/declarations/struct" >}})或[联合体]({{< ref "/c/language/declarations/union" >}})类型的表达式
- 两个 void 类型的表达式
- 两个指针类型的表达式，指向[兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)的类型，忽略 cvr 限定符
- 两个 [nullptr_t]({{< ref "/c/types/nullptr_t" >}}) 类型的表达式(C23 起)

- 一个表达式是指针而另一个是空指针常量（例如 [NULL]({{< ref "/c/types/NULL" >}})）或 [nullptr_t]({{< ref "/c/types/nullptr_t" >}}) 值(C23 起)
- 一个表达式是指向对象指针而另一个是指向（可有限定）的 void 指针
  1. 首先，求值 *条件*。此求值后有[序列点]({{< ref "/c/language/expressions/eval_order" >}})。
  2. 若 *条件* 的结果比较不等于零，则执行 *表达式真*，否则执行 *表达式假*。
  3. 进行从结果到*公共类型*的[转换]({{< ref "/c/language/expressions/conversion" >}})，转换定义如下：
     1. 若表达式拥有算术类型，则公共类型为[一般算术转换]({{< ref "/c/language/expressions/conversion#.E4.B8.80.E8.88.AC.E7.AE.97.E6.9C.AF.E8.BD.AC.E6.8D.A2" >}})后的类型
     2. 若表达式拥有结构体/联合体类型，则公共类型为结构体/联合体类型
     3. 若表达式都是 void，则整个条件运算符表达式就是 void 表达式
     4. 若一个表达式为指针而另一个是空指针常量或 [nullptr_t]({{< ref "/c/types/nullptr_t" >}}) 值(C23 起)，则类型为该指针的类型
     5. 若两个表达式都是指针，则结果为指向合并两个被指向类型的 cvr 限定符的类型的指针（即若一个指针是 `const int*` 而另一个是 `volatile int*`，则结果为 `const volatile int*`），而假如类型不同，则被指向类型为两类型的[合成类型](https://zh.cppreference.com/w/c/language/types#.E5.90.88.E6.88.90.E7.B1.BB.E5.9E.8B)。
     6. 若一个表达式是指向 void 指针，则结果为指向具有合并的 cvr 限定符的 void 的指针。
     7. 若两者均拥有 [nullptr_t]({{< ref "/c/types/nullptr_t" >}}) 类型，则共同类型亦为 [nullptr_t]({{< ref "/c/types/nullptr_t" >}})(C23 起)

```c
#define ICE(x) (sizeof(*(1 ? ((void*)((x) * 0l)) : (int*)1)))
 
// 若 x 是整数常量表达式，则宏展开成
 
 sizeof( 1 ? NULL : (int *) 1)  // (void *)((x)*0l)) -> NULL
 
// 按照第 (4) 点这进一步转换成
 
 sizeof(int)
 
// 若 x 不是整数常量表达式，则宏按照第 (6) 点展开成
 
 (sizeof(*(void *)(x))           // 因不完整类型而错误
```

### 注解

​	条件运算符决不是[左值表达式]({{< ref "/c/language/expressions/value_category" >}})，尽管它可以返回结构体/联合体类型的对象。其他可以返回结构体的表达式仅有[赋值]({{< ref "/c/language/expressions/operator_assignment" >}})、[逗号]({{< ref "/c/language/expressions/operator_other#.E9.80.97.E5.8F.B7.E8.BF.90.E7.AE.97.E7.AC.A6" >}})、[函数调用]({{< ref "/c/language/expressions/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8" >}})和[复合字面量]({{< ref "/c/language/expressions/compound_literal" >}})。

> 注意 
>
> ​	C++ 中它可以为左值表达式。

​	此运算符和赋值的相对优先级上的细节见[运算符优先级]({{< ref "/c/language/expressions/operator_precedence" >}})。

​	条件运算符拥有从右到左结合性，这允许链式写法

```c
#include <assert.h>
 
enum vehicle { bus, airplane, train, car, horse, feet };
 
enum vehicle choose(char arg)
{
    return arg == 'B' ? bus      :
           arg == 'A' ? airplane :
           arg == 'T' ? train    :
           arg == 'C' ? car      :
           arg == 'H' ? horse    :
                        feet     ;
}
 
int main(void)
{
    assert(choose('H') == horse && choose('F') == feet);
}
```

## `sizeof` 运算符

​	见 [sizeof 运算符]({{< ref "/c/language/expressions/sizeof" >}})

## `_Alignof` 运算符

​	见 [_Alignof 运算符]({{< ref "/c/language/expressions/_Alignof" >}})

## `typeof` 运算符

​	见 [typeof 运算符](https://zh.cppreference.com/w/c/language/typeof)

## 参阅

其他运算符的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/operator_other)
