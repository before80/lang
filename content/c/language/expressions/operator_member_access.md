+++
title = "成员访问运算符"
date = 2025-04-12T20:42:14+08:00
weight = 150
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/operator_member_access](https://zh.cppreference.com/w/c/language/operator_member_access)

​	成员访问运算符允许访问其操作数的成员。

| 运算符 |       运算符名       |  示例  |                             描述                             |
| :----: | :------------------: | :----: | :----------------------------------------------------------: |
|  `[]`  |       数组下标       | `a[b]` |                   访问数组 a 的第 b 个元素                   |
|  `*`   |      指针解引用      |  `*a`  |           解引用指针 a 以访问其所指向的对象或函数            |
|  `&`   |         取址         |  `&a`  |                 创建指向对象或函数 a 的指针                  |
|  `.`   |       成员访问       | `a.b`  | 访问[结构体]({{< ref "/c/language/declarations/struct" >}})或[联合体]({{< ref "/c/language/declarations/union" >}}) a 的成员 b |
|  `->`  | 通过指针进行成员访问 | `a->b` | 访问 a 所指向的[结构体]({{< ref "/c/language/declarations/struct" >}})或[联合体]({{< ref "/c/language/declarations/union" >}}) 的成员 b |

## 下标

​	数组下标运算符的形式为：

| *指针表达式* `[` *整数表达式* `]` | (1)  |
| --------------------------------- | ---- |
| *整数表达式* `[` *指针表达式* `]` | (2)  |

​	其中

| *指针表达式* | -    | 指向完整对象的指针类型的[表达式]({{< ref "/c/language/expressions" >}}) |
| ------------ | ---- | ------------------------------------------------------------ |
| *整数表达式* | -    | 整数类型的[表达式]({{< ref "/c/language/expressions" >}}) |

​	下标运算符表达式为[左值表达式]({{< ref "/c/language/expressions/value_category" >}})，其类型为 *指针表达式* 所指向的对象的类型。

​	按照定义，下标运算符 `E1[E2]` 严格等同于 `*((E1)+(E2))`。若 *指针表达式* 为数组表达式，则它经历[左值到右值转换]({{< ref "/c/language/expressions/conversion" >}})并成为指向数组首元素的指针。

​	根据[指针与整数间加法]({{< ref "/c/language/expressions/operator_arithmetic" >}})的定义，其结果是下标等于 *整数表达式* 的结果的数组元素（或若 *指针表达式* 指向某数组的第 i 个元素，则结果的下标为 i 加上 *整数表达式* 的结果）。

> 注意
>
> ​	多维数组上的细节见[数组]({{< ref "/c/language/declarations/array" >}})。

```c
#include <stdio.h>
int main(void)
{
    int a[3] = {1,2,3};
    printf("%d %d\n", a[2],  // n == 3
                      2[a]); // 同上， n == 3
    a[2] = 7; // 下标表达式是左值
 
    int n[2][3] = {1,2,3,4,5,6};
    int (*p)[3] = &n[1]; // n 的元素为数组
    printf("%d %d %d\n", (*p)[0], p[0][1], p[0][2]); // 通过 p 访问 n[1][]
    int x = n[1][2]; // 再次应用 [] 到数组 n[1]
    printf("%d\n", x);
 
    printf("%c %c\n", "abc"[2], 2["abc"]); // 字符串字面量亦是数组
}
```

​	输出：

```txt
3 3
4 5 6
6
c c
```

## 解引用

​	*解引用*或*间接*表达式的形式为：

`*` *指针表达式*

其中

| *指针表达式* | -    | 任何指针类型的[表达式]({{< ref "/c/language/expressions" >}}) |
| ------------ | ---- | ------------------------------------------------------------ |

​	若 *指针表达式* 为指向函数指针，则解引用运算符的结果为该函数的函数指代符。

​	若 *指针表达式* 为指向对象指针，则结果为指代被指向对象的[左值表达式]({{< ref "/c/language/expressions/value_category" >}})。

​	解引用空指针、指向在生存期外的对象的指针（悬垂指针）、错误对齐的指针或拥有不确定值的指针是未定义行为，除非如在 &*E 中一般，通过应用取址运算符到解引用运算符的结果，将它取消。

```c
#include <stdio.h>
int main(void)
{
    int n = 1;
    int* p = &n;
    printf("*p = %d\n", *p); // *p 的值即为存储于 n 的值
    *p = 7; // *p 是左值
    printf("*p = %d\n", *p);
}
```

​	输出：

```
*p = 1
*p = 7
```

## 取址

​	取址运算符的形式为

| `&` *函数*                    | (1)  |
| ----------------------------- | ---- |
| `&` *左值表达式*              | (2)  |
| `&` `*` *表达式*              | (3)  |
| `&` *表达式* `[` *表达式* `]` | (4)  |

1) 函数地址
2) 对象地址
3) 特殊情况：`&` 与 `*` 彼此抵消，均不求值
4) 特殊情况：`&` 与 `[]` 中隐含的 `*` 抵消，只求值 `[]` 中隐含的加法

​	其中

| *左值表达式* | -    | 非[位域]({{< ref "/c/language/declarations/bit_field" >}})且无 [register]({{< ref "/c/language/declarations/storage_duration" >}}) 存储类的任何类型的[左值]({{< ref "/c/language/expressions/value_category" >}})表达式 |
| ------------ | ---- | ------------------------------------------------------------ |

​	取址运算符产生其操作数的[非左值]({{< ref "/c/language/expressions/value_category" >}})地址，适于初始化指向操作数类型的指针。若操作数为函数指代符 ((1))，则结果为指向函数指针。若操作数为对象 ((2))，则结果为指向对象指针。

​	若操作数为解引用运算符，则不进行动作（故可以应用 &* 到空指针），但结果并非左值。

​	若操作数是数组下标表达式，则不进行数组到指针转换和加法外的动作，故 &a[N] 对大小为 N 的数组合法（可以获得尾后一位置指针，不能解引用它，但此表达式中解引用被取消）。

```c
int f(char c) { return c;}
int main(void)
{
   int n = 1;
   int *p = &n; // 对象 n 的地址
   int (*fp)(char) = &f; // 函数 f 的地址
   int a[3] = {1,2,3};
   int *beg=a, *end=&a[3]; // 同 end = n+3
}
```

## 成员访问

​	成员访问运算符的形式为：

*表达式* `.` *成员名*

​	其中

| *表达式* | -    | [结构体]({{< ref "/c/language/declarations/struct" >}})或[联合体]({{< ref "/c/language/declarations/union" >}})类型的表达式 |
| -------- | ---- | ------------------------------------------------------------ |
| *成员名* | -    | 指名 *表达式* 所指带的结构体或联合体的成员的[标识符]({{< ref "/c/language/basic_concepts/identifier" >}}) |

​	成员访问表达式指代其左运算数所指代的[结构体]({{< ref "/c/language/declarations/struct" >}})或[联合体]({{< ref "/c/language/declarations/union" >}})中所指名的成员。它拥有与其左运算数相同的[值类别]({{< ref "/c/language/expressions/value_category" >}})。

​	若左操作数为 [const]({{< ref "/c/language/declarations/const" >}}) 或 [volatile]({{< ref "/c/language/declarations/volatile" >}}) 限定，则结果亦有限定。若左操作数为[原子对象]({{< ref "/c/language/declarations/atomic" >}})，则行为未定义。

> 注意
>
> ​	除了指名结构体或联合体类型的标识符，下列表达式亦可拥有结构体或联合体类型：[赋值]({{< ref "/c/language/expressions/operator_assignment" >}})、[函数调用]({{< ref "/c/language/expressions/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8" >}})、[逗号运算符]({{< ref "/c/language/expressions/operator_other#.E9.80.97.E5.8F.B7.E8.BF.90.E7.AE.97.E7.AC.A6" >}})、[条件运算符]({{< ref "/c/language/expressions/operator_other#.E6.9D.A1.E4.BB.B6.E8.BF.90.E7.AE.97.E7.AC.A6" >}})和[复合字面量]({{< ref "/c/language/expressions/compound_literal" >}})。

```c
#include <stdio.h>
struct s {int x;};
struct s f(void) { return (struct s){1}; }
int main(void)
{
    struct s s;
    s.x = 1; // OK ：更改 s 的成员
    int n = f().x; // f() 为 struct s 类型的表达式
//  f().x = 1; // 错误：此成员访问表达式非左值
 
    const struct s sc;
//  sc.x = 3;  // 错误：sc.x 为 const，不能被赋值
 
    union { int x; double d; } u = {1};
    u.d = 0.1; // 更改联合体的活跃成员
}
```

## 通过指针进行成员访问

​	成员访问表达式的形式为：

*表达式* `->` *成员名*

​	其中

| *表达式* | -    | 指向[结构体]({{< ref "/c/language/declarations/struct" >}})或[联合体]({{< ref "/c/language/declarations/union" >}})的[指针]({{< ref "/c/language/declarations/pointer" >}})类型的表达式 |
| -------- | ---- | ------------------------------------------------------------ |
| *成员名* | -    | 指名 *表达式* 所指向的结构体或联合体的成员的[标识符]({{< ref "/c/language/basic_concepts/identifier" >}}) |

​	通过指针进行成员访问的表达式指代其左操作数所指向的[结构体]({{< ref "/c/language/declarations/struct" >}})或[联合体]({{< ref "/c/language/declarations/union" >}})类型中被指名的成员。其值类别始终为[左值]({{< ref "/c/language/expressions/value_category" >}})。

​	若左操作数所指向的类型有 [const]({{< ref "/c/language/declarations/const" >}}) 或 [volatile]({{< ref "/c/language/declarations/volatile" >}}) 限定，则结果亦有限定。若左操作数所指向的类型为[原子类型]({{< ref "/c/language/declarations/atomic" >}})，则行为未定义。

```
#include <stdio.h>
struct s {int x;};
int main(void)
{
    struct s s={1}, *p = &s;
    p->x = 7; // 通过指针更改 s.x 的值
    printf("%d\n", p->x); // 打印 7
}
```

## 缺陷报告

​	下列更改行为的缺陷报告追溯地应用于以前出版的 C 标准。

| 缺陷报告                                                     | 应用于 | 出版时的行为             | 正确行为   |
| ------------------------------------------------------------ | ------ | ------------------------ | ---------- |
| [DR 076](https://www.open-std.org/jtc1/sc22/wg14/www/docs/dr_076.html) | C89    | `&` 无法取消不必要的间接 | 使之能取消 |

## 参阅

**成员访问运算符**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/operator_member_access)**
