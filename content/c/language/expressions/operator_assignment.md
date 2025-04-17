+++
title = "赋值运算符"
date = 2025-04-12T21:10:54+08:00
weight = 190
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/operator_assignment](https://zh.cppreference.com/w/c/language/operator_assignment)

​	赋值及复合赋值运算符是二元运算符，它们用其右侧的值修改其左侧的变量。

| 运算符 |   运算符名   |   示例    |             描述             |     等价     |
| :----: | :----------: | :-------: | :--------------------------: | :----------: |
|  `=`   |   基本赋值   |  `a = b`  |         a 变得等于 b         |    不适用    |
|  `+=`  |   加法赋值   | `a += b`  |    a 变得等于 a 与 b 的和    | `a = a + b`  |
|  `-=`  |   减法赋值   | `a -= b`  |    a 变得等于 a 减 b 的差    | `a = a - b`  |
|  `*=`  |   乘法赋值   | `a *= b`  |    a 变得等于 a 与 b 的积    | `a = a * b`  |
|  `/=`  |   除法赋值   | `a /= b`  |   a 变得等于 a 除以 b的商    | `a = a / b`  |
|  `%=`  |    模赋值    | `a %= b`  |  a 变得等于 a 除以 b 的余数  | `a = a % b`  |
|  `&=`  |  逐位与赋值  | `a &= b`  |  a 变得等于 a 与 b 的逐位与  | `a = a & b`  |
|  `|=`  |  逐位或赋值  | `a |= b`  |  a 被替换为 a 与 b 的逐位或  | `a = a | b`  |
|  `^=`  | 逐位异或赋值 | `a ^= b`  | a 被替换为 a 与 b 的逐位异或 | `a = a ^ b`  |
| `<<=`  | 逐位左移赋值 | `a <<= b` |    a 被替换为 a 左移 b 位    | `a = a << b` |
| `>>=`  | 逐位右移赋值 | `a >>= b` |    a 被替换为 a 右移 b 位    | `a = a >> b` |

## 简单赋值

​	简单赋值表达式的形式为：

*lhs* `=` *rhs*

​	其中

| *lhs* | -    | 任何完整对象类型的[可修改左值]({{< ref "/c/language/expressions/value_category" >}})表达式 |
| ----- | ---- | ------------------------------------------------------------ |
| *rhs* | -    | 任何[可隐式转换]({{< ref "/c/language/expressions/conversion" >}})成 *lhs* 或与 *lhs* [兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)类型的表达式 |

​	赋值进行从 *rhs* 的值到 *lhs* 类型的[隐式转换]({{< ref "/c/language/expressions/conversion" >}})，然后用 *rhs* 转换后的值替换 *lhs* 所指代对象中的值。

​	赋值还会返回与存储于 `lhs` 中相同的值（故如 a = b = c 的表达式合法）。赋值表达式的[值类别]({{< ref "/c/language/expressions/value_category" >}})是非左值（故形如 (a = b) = c 的表达式非法）。

*rhs* 与 *lhs* 必须满足下列条件之一：

- *lhs* 与 *rhs* 拥有[兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)的 [struct]({{< ref "/c/language/declarations/struct" >}}) 或 [union]({{< ref "/c/language/declarations/union" >}}) 类型，或……
- *rhs* 必须可[隐式转换]({{< ref "/c/language/expressions/conversion" >}})成 *lhs*，这表示
  - *lhs* 与 *rhs* 均拥有[算术类型]({{< ref "/c/language/basic_concepts/arithmetic_types" >}})，此情况下 *lhs* 可有[volatile]({{< ref "/c/language/declarations/volatile" >}}) 限定或为[原子的]({{< ref "/c/language/declarations/atomic" >}})(C11 起)
  - *lhs* 与 *rhs* 均拥有指向[兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)类型（忽略限定符）的[指针]({{< ref "/c/language/declarations/pointer" >}})类型，或其中一个指针是指向 void 的指针，而该[转换]({{< ref "/c/language/expressions/conversion" >}})不向所指向类型添加限定符。*lhs* 可以为 [volatile]({{< ref "/c/language/declarations/volatile" >}}) 或 [restrict]({{< ref "/c/language/declarations/restrict" >}})(C99 起) 限定，或为[原子的]({{< ref "/c/language/declarations/atomic" >}})(C11 起)。
  - *lhs* 是（可能被限定或为原子的(C11 起)）指针，而 *rhs* 是空指针常量，如 [NULL]({{< ref "/c/types/NULL" >}}) 或 [nullptr_t]({{< ref "/c/types/nullptr_t" >}}) 值(C23 起)。
  - *lhs* 是（可能被限定或为原子的(C11 起)）_Bool 类型而 *rhs* 是指针或 [nullptr_t]({{< ref "/c/types/nullptr_t" >}}) 值(C23 起)。(C99 起)
  - *lhs* 是可能被限定或为原子的 [nullptr_t]({{< ref "/c/types/nullptr_t" >}}) 类型而 *rhs* 是 [nullptr_t]({{< ref "/c/types/nullptr_t" >}}) 类型。(C23 起)



## 注解

​	若 *rhs* 与 *lhs* 在内存中重叠（例如它们是同一联合体的成员），则行为未定义，除非重叠是严格的且两者类型[兼容]({{< ref "/c/language/basic_concepts/type#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B" >}})。

​	尽管数组不可赋值，但包裹在结构体内的数组可以赋值给另一个相同（或兼容）的结构体类型。

​	更新 *lhs* 的副效应[后序于]({{< ref "/c/language/expressions/eval_order" >}})值计算，但 *lhs* 和 *rhs* 自己并非如此，与通常一样，运算数的求值相对于彼此不定序（故如 `i = ++i` 的表达式结果未定义）。

​	赋值会剥除浮点数表达式的额外范围和精度（见 [FLT_EVAL_METHOD]({{< ref "/c/types/limits/FLT_EVAL_METHOD" >}})）。

​	C++ 中，赋值表达式是左值表达式，而 C 中不是。

```c
#include <stdio.h>
 
int main(void)
{
    // 整数
    int i = 1, j = 2, k = 3; // 初始化，并非赋值
 
    i = j = k;   // i 和 j 现在都为 3
//  (i = j) = k; // 错误：等号左侧应该为左值 （注：此写法在cpp中允许）
    printf("%d %d %d\n", i, j, k);
 
    const char c = 'A';    // 初始化，并非赋值
    const char *p = &c;    // 初始化，并非赋值
    const char cpp = &p; // 初始化，并非赋值
 
//  cpp = &p;   // 错误：char 不能转换为 const char
    *cpp = &c;  // OK：char* 能转换为 const char*
    printf("%c \n", cpp);
    cpp = 0;    // OK：空指针常量能转换为任何指针
 
    // 数组
    int arr1[2] = {1,2}, arr2[2] = {3, 4};
//  arr1 = arr2; // 错误：不能通过数组赋值
    printf("arr1[0]=%d arr1[1]=%d arr2[0]=%d arr2[1]=%d\n",
            arr1[0],   arr1[1],   arr2[0],   arr2[1]);
 
    struct { int arr[2]; } sam1 = { {5, 6} }, sam2 = { {7, 8} };
    sam1 = sam2; // OK：可对包装于结构体中的数组赋值
 
    printf("%d %d \n",sam1.arr[0],sam1.arr[1]);
}
```

输出：

```txt
3 3 3
A
arr1[0]=1 arr1[1]=2 arr2[0]=3 arr2[1]=4
7 8
```

## 复合赋值

​	复合赋值表达式的形式为：

*lhs* *op* *rhs*

其中

| *op*         | -    | one of `*=`, `/=` `%=`, `+=` `-=`, `<<=`, `>>=`, `&=`, `^=`, `|=` |
| ------------ | ---- | ------------------------------------------------------------ |
| *lhs*, *rhs* | -    | 拥有[算术类型]({{< ref "/c/language/basic_concepts/arithmetic_types" >}})的表达式（其中 *lhs* 可以有限定或是原子的），除非 *op* 是 += 或 -=，此情况允许接受指针类型并具有与 + 和 - 相同的限制 |

​	表达式 *lhs* *@=* *rhs* 与 *lhs* `=` *lhs* *@* `(` *rhs* `)` 完全相同，但只求值一次 *lhs*。

​	若 *lhs* 拥有[原子]({{< ref "/c/language/declarations/atomic" >}})类型，则运算表现为单个带内存顺序 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 的原子读修改写操作对于整数原子类型，复合赋值运算 @= 等价于：(C11 起)

```c
T1* addr = &lhs;
T2 val = rhs;
T1 old = *addr;
T1 new;
do { new = old @ val } while (!atomic_compare_exchange_strong(addr, &old, new);
```



```c
#include <stdio.h>
 
int main(void)
{
    int x = 10; 
    int hundred = 100; 
    int ten = 10; 
    int fifty = 50; 
 
    printf("%d %d %d %d\n", x, hundred, ten, fifty);
 
    hundred *= x; 
    ten     /= x; 
    fifty   %= x; 
 
    printf("%d %d %d %d\n", x, hundred, ten, fifty);
 
    return 0;
}
```

输出：

```txt
10 100 10 50
10 1000 1 0
```

## 参阅

**赋值运算符** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/operator_assignment)**
