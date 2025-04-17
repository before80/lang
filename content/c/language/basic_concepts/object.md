+++
title = "对象与对齐"
date = 2025-04-11T23:18:21+08:00
weight = 110
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/object](https://zh.cppreference.com/w/c/language/object)

​	C 程序创建、销毁、访问并操作对象。

​	C 中，一个对象是执行环境中[数据存储]({{< ref "/c/language/basic_concepts/memory_model" >}})的一个区域，其内容可以表示*值*（值是对象的内容转译为特定[类型](https://zh.cppreference.com/w/c/language/types)时的含义）。

​	每个对象拥有：

- 大小（可由 [`sizeof`]({{< ref "/c/language/expressions/sizeof" >}}) 确定）
- 对齐要求（可由 [`_Alignof`]({{< ref "/c/language/expressions/_Alignof" >}})(C23 前)[`alignof`](https://zh.cppreference.com/w/c/language/alignof)(C23 起) 确定）(C11 起)
- [存储期]({{< ref "/c/language/declarations/storage_duration" >}})（自动、静态、分配、线程局域）
- [生存期]({{< ref "/c/language/basic_concepts/lifetime" >}})（等于存储期或临时）
- 有效类型（见下）
- 值（可以是不确定的）
- 可选项，表示该对象的[标识符]({{< ref "/c/language/basic_concepts/identifier" >}})

​	对象由[声明]({{< ref "/c/language/declarations" >}})、[分配函数]({{< ref "/c/memory" >}})、[字符串字面量]({{< ref "/c/language/expressions/string_literal" >}})、[复合字面量]({{< ref "/c/language/expressions/compound_literal" >}})，及返回[拥有数组类型的结构体或联合体]({{< ref "/c/language/basic_concepts/lifetime" >}})的非左值表达式创建。

## 对象表示

​	除了[位域]({{< ref "/c/language/declarations/bit_field" >}})，每个对象都是由一个或更多字节组成的，每个字节由 [CHAR_BIT]({{< ref "/c/types/limits" >}}) 位组成，而且每个对象可以用 [memcpy](https://zh.cppreference.com/w/c/string/byte/memcpy) 复制到 unsigned char[n] 类型的对象中，这里 `n` 是对象的大小。生成的数组内容被称为*对象表示*。

​	若两对象拥有相同的对象表示，则它们比较相等（除了它们是浮点数 NaN 的情况）。逆命题非真：两个比较相等的对象可以拥有不同的对象表示，因为并非对象表示的每一位都需要参与其值。这些位可以用于填充以满足对齐要求，等同性检测，指示陷阱表示等。

​	若一个对象表示不表示该对象类型的任何值，则它被称为*陷阱表示*。以异于字符类型左值表达式读取的方式访问陷阱表示是未定义行为。结构体或联合体的值始终不是陷阱表示，即使任何一个成员的值是陷阱表示。

​	对于 `char`、`signed char`、`unsigned char` 类型的对象，对象表示的每一位都要求参与其值表示，而且每种可能的位模式都表示不同的值（不允许填充位、陷阱位或多重表示）。

​	[整数类型]({{< ref "/c/language/basic_concepts/arithmetic_types#.E6.95.B4.E6.95.B0.E7.B1.BB.E5.9E.8B" >}})（short、int、long、long long）对象占用多个字节时，这些字节的用法是实现定义的，不过二种有主导地位的实现是*大端 (big-endian)*（POWER、Sparc、Itanium）和*小端 (little-endian)*（x86、x86-64）：大端平台将最高位字节存储于整数所占据的存储区域的最低地址，小端平台将最低位字节存储于最低地址。细节见[端序](https://en.wikipedia.org/wiki/Endianness)。参阅下方示例。

​	尽管大多数实现都不允许整数的陷阱表示、填充位或多重表示，也还存在例外；例如 Itanium 上的整数类型值[就可以是陷阱表示](https://web.archive.org/web/20170830125905/https://blogs.msdn.microsoft.com/oldnewthing/20040119-00/?p=41003)。

## 有效类型

​	每个对象都拥有*有效类型*，它决定何种[左值]({{< ref "/c/language/expressions/value_category" >}})访问合法，何种违反严格别名使用规则。

​	若对象是由[声明]({{< ref "/c/language/declarations" >}})创建的，则该对象的声明类型即是对象的*有效类型*。

​	若对象由[分配函数]({{< ref "/c/memory" >}})（包含 [realloc](https://zh.cppreference.com/w/c/memory/realloc)）创建，则它没有声明类型。这种对象以下列方式获得有效类型：

- 首次通过拥有异于字符类型的类型的左值写入该对象，无论何时该左值的类型都会成为该对象该次写入和所有后继读取的*有效类型*。
- [memcpy](https://zh.cppreference.com/w/c/string/byte/memcpy) 或 [memmove](https://zh.cppreference.com/w/c/string/byte/memmove) 复制另一个对象到该对象，无论何时源对象的有效类型（若它有）都会成为该对象该次写入和所有后继读取的*有效类型*。
- 任何其他对无声明类型的对象的访问，有效类型是访问所用的左值类型。

## 严格别名使用

​	给定一个拥有*有效类型* `T1` 的对象，使用相异类型的 `T2` 左值表达式（典型的是解引用指针）访问它是未定义行为，除非：

- `T2` 和 `T1` 是[兼容类型](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)。
- `T2` 是与 `T1` [兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)的类型的 cvr 限定版本。
- `T2` 是与 `T1` [兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)的类型的有符号或无符号版本。
- `T2` 是聚合体或联合体类型，其成员中包含一个前述类型（递归地包括子聚合体或被包含联合体的成员）。
- `T2` 是字符类型（`char`、`signed char` 或 `unsigned char`）。

```c
int i = 7;
char* pc = (char*)(&i);
if(pc[0] == '\x7') { // 通过 char 别名使用是 OK 的
    puts("This system is little-endian");
} else {
    puts("This system is big-endian");
}
 
float* pf = (float*)(&i);
float d = *pf; // UB：float 左值 *p 不能用来访问 int
```

这些规则控制接受二个指针的函数，在通过一个指针写入后，是否必须重读取另一个：

```c
// int* 与 double* 不能别名使用
void f1(int *pi, double *pd, double d)
{
    // 从 *pi 的读取可以只做一次，在循环前
    for (int i = 0; i < *pi; i++) *pd++ = d;
}
struct S { int a, b; };
 
// int* 和 struct S* 可以别名使用，因为 S 拥有 int 类型的成员
void f2(int *pi, struct S *ps, struct S s)
{
    // 从 *pi 的读取必须在每次通过 *ps 写入后进行
    for (int i = 0; i < *pi; i++)
        *ps++ = s;
}
```

> 注意 
>
> ​	[restrict 限定符]({{< ref "/c/language/declarations/restrict" >}})可用于指示二个指针不用作别名使用，即使规则允许它们如此。

> 注意
>
> ​	类型双关也可以通过[联合体]({{< ref "/c/language/declarations/union" >}})的非活跃成员进行。

## 对齐

​	每个完整[对象类型](https://zh.cppreference.com/w/c/language/types#.E7.B1.BB.E5.9E.8B.E7.BB.84.E5.88.AB)拥有一个称作*对齐要求*的属性，它是一个 [size_t]({{< ref "/c/types/size_t" >}}) 类型的整数值，表示此类型对象可以分配的相继地址之间的字节数。合法的对齐值是二的非负数次幂。

​	类型的对齐要求可以通过 [`_Alignof`]({{< ref "/c/language/expressions/_Alignof" >}})(C23 前)[`alignof`](https://zh.cppreference.com/w/c/language/alignof)(C23 起) 获得。(C11 起)

​	为了满足结构体所有对象的对齐要求，一些成员后面可能会插入填充位。

```c
#include <stdalign.h>
#include <stdio.h>
 
// struct S 的对象可以分配于任何地址
// 因为 S.a 和 S.b 可以分配于任何地址
struct S
{
    char a; // 成员对象大小：1，对齐：1
    char b; // 成员对象大小：1，对齐：1
}; // 结构体对象大小：2，对齐：1
 
// struct X 的对象必须分配于 4字节边界
// 因为 X.n 必须分配于 4 字节边界
// 因为 int 的对齐要求（通常）是 4
struct X
{
    int n;  // 成员对象大小：4，对齐：4
    char c; // 成员对象大小：1，对齐：1
    // 剩余的三个字节进行空位填充
}; // 结构体对象大小：8，对齐：4
 
int main(void)
{
    printf("sizeof(struct S) = %zu\n", sizeof(struct S));
    printf("alignof(struct S) = %zu\n", alignof(struct S));
    printf("sizeof(struct X) = %zu\n", sizeof(struct X));
    printf("alignof(struct X) = %zu\n", alignof(struct X));
}
```

可能的输出：

```txt
sizeof(struct S) = 2
alignof(struct S) = 1
sizeof(struct X) = 8
alignof(struct X) = 4
```

​	每个对象类型将其对齐要求强加于该类型的每个对象。所有类型中，最严格（最大）的基础对齐是 [max_align_t]({{< ref "/c/types/max_align_t" >}}) 的对齐。最弱（最小）的对齐是字符类型（char、signed char 及 unsigned char）的对齐，且等于 1。最严格（最大）的*基础对齐*是实现定义的，并等于 [max_align_t]({{< ref "/c/types/max_align_t" >}}) 的对齐(C11 起)。

​	基础对齐对于所有类型的存储期的对象都得到支持。

​	若用 [`_Alignof`]({{< ref "/c/language/expressions/_Alignof" >}})(C23 前)[`alignof`](https://zh.cppreference.com/w/c/language/alignof)(C23 起) 令一个对象的对齐严格于（大于）[max_align_t]({{< ref "/c/types/max_align_t" >}})，则它拥有*扩展对齐要求*。成员拥有扩展对齐的结构体或联合体是*过对齐类型*。是否支持过对齐类型是实现定义的，而且对于每种[存储期]({{< ref "/c/language/declarations/storage_duration" >}})的支持可以不同。若结构体或联合体 `S` 无任何过拥有对齐类型，或用指定扩展对齐的对齐说明符声明的成员，则 `S` 拥有基础对齐。每个[算术]({{< ref "/c/language/basic_concepts/arithmetic_types" >}})或[指针]({{< ref "/c/language/declarations/pointer" >}})类型的[原子]({{< ref "/c/language/declarations/atomic" >}})版本均拥有基础对齐。(C11 起)

## 缺陷报告

​	下列更改行为的缺陷报告追溯地应用于以前出版的 C 标准。

| 缺陷报告                                                     | 应用于 | 出版时的行为                                     | 正确行为         |
| ------------------------------------------------------------ | ------ | ------------------------------------------------ | ---------------- |
| [DR 445](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_445) | C11    | 一个类型可能在不涉及 _Alignas 的情况下有扩展对齐 | 它必须有基础对齐 |

## 参阅

**对象**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/object)**
