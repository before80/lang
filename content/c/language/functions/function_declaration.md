+++
title = "函数声明"
date = 2025-04-13T13:49:57+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/function_declaration](https://zh.cppreference.com/w/c/language/function_declaration)

​	函数声明引入指代函数的[标识符]({{< ref "/c/language/basic_concepts/identifier" >}})，并可选地指定该函数的参数类型（即其*原型*）。函数声明（不同于[定义]({{< ref "/c/language/functions/function_definition" >}})）可以出现于块作用域和文件作用域中。

## 语法

​	在函数声明的[声明文法]({{< ref "/c/language/declarations" >}})中，*类型说明符* 序列，可选择地由声明式修饰，代表其*返回类型*（可以是任何异于函数和数组的类型），而 *声明符* 有三种形式：

| *非指针声明符* `(` *形参列表* `)` *属性说明符序列*(可选)   | (1)  |          |
| ---------------------------------------------------------- | ---- | -------- |
| *非指针声明符* `(` *标识符列表* `)` *属性说明符序列*(可选) | (2)  | (C23 前) |
| *非指针声明符* `(` `)` *属性说明符序列*(可选)              | (3)  |          |

​	其中

| *非指针声明符*   | -    | 除了不带括号的指针声明符以外的任何[声明符]({{< ref "/c/language/declarations#.E5.A3.B0.E6.98.8E.E7.AC.A6" >}})。包含于此声明符中的标识符成为函数指代符的标识符。 |
| ---------------- | ---- | ------------------------------------------------------------ |
| *形参列表*       | -    | 或为单一关键词 void，或为*形参*的逗号分隔列表，可以以[省略号形参]({{< ref "/c/language/functions/variadic" >}})结尾。 |
| *标识符列表*     | -    | 标识符的逗号分隔列表，仅在声明符被用作旧式[函数定义]({{< ref "/c/language/functions/function_definition" >}})的一部分的情况下可能 |
| *属性说明符序列* | -    | (C23)可选的[属性]({{< ref "/c/language/declarations/attributes" >}})列表，应用到函数类型 |

1) 新式 (C89) 函数声明。此声明不仅引入函数指代符自身，而且还为任何将来的[函数调用表达式]({{< ref "/c/language/expressions/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8" >}})提供函数原型，强制将使用的实参表达式转换成声明的形参类型，并进行编译时的实参数量检查。

```c
int max(int a, int b); // 声明
int n = max(12.01, 3.14); // OK：从 double 转换到 int
```

2) (C23 前) 旧式 (K&R) 函数定义。此声明不引入函数原型，且任何将来的[函数调用表达式]({{< ref "/c/language/expressions/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8" >}})都将进行默认实参提升，而且若实参数量不匹配形参数量则引起未定义行为。

```c
int max(a, b) 
int a, b; { return a>b?a:b; } // 定义期待 int；第二个调用是未定义行为
int n = max(true, (char)'a'); // 以二个 int 参数调用 max （提升后）
int n = max(12.01f, 3.14); // 以二个 double 参数调用 max （提升后）
```

3) 无原型函数声明。此声明不引入原型。(C23 前)新风格的函数声明，等价于 *形参列表* void。(C23 起)

## 解释

​	函数的返回类型，由 *说明符与限定符* 中的类型说明符确定，并且像在[声明]({{< ref "/c/language/declarations" >}})中一样可以由 *声明符* 修改，它必须是非数组对象类型或类型 `void`。若该函数声明不是定义，则返回类型可以[不完整]({{< ref "/c/language/basic_concepts/type#.E4.B8.8D.E5.AE.8C.E6.95.B4.E7.B1.BB.E5.9E.8B" >}})。返回类型不能有 cvr 限定：为构造函数类型的目的，调整任何有限定返回类型为其无限定版本。

```
void f(char *s);                    // 返回类型为 void
int sum(int a, int b);              // sum 的返回类型为 int.
int (*foo(const void *p))[3];       // 返回类型是指向 3 个 int 的数组的指针
 
double const bar(void);             // 声明 double(void) 类型函数
double (*barp)(void) = bar;         // OK：foop 是指向 double(void) 的指针
double const (*barpc)(void) = barp; // OK：foopc 亦为指向 double(void) 的指针
```

​	函数声明式可以与其他声明式联合，只要他们共享其类型说明符和限定符。

```c
int f(void), *fip(), (*pfi)(), *ap[3]; // 声明二个函数和二个对象
inline int g(int), n; // 错误：inline 说明符仅用于函数
typedef int array_t[3];
array_t a, h(); // 错误：数组类型不能作为函数返回类型
```

​	若函数声明符出现于任何函数外，则其引入的标识符拥有[文件作用域]({{< ref "/c/language/basic_concepts/scope" >}})和[外部链接]({{< ref "/c/language/declarations/storage_duration" >}})，除非使用 `static` 或有较前的 static 声明可见。若声明出现于另一函数内，则标识符拥有块作用域（且亦拥有外部或内部链接）。

```c
int main(void)
{
    int f(int); // 外部链接，块作用域
    f(1); // 其定义需要程序的别处可用
}
```

​	不是[函数定义]({{< ref "/c/language/functions/function_definition" >}})的一部分的声明中，(C23 前)参数不需要命名：

```c
int f(int, int); // 声明
// int f(int, int) { return 7; } // 错误，参数在定义中必须命名
// C23 起允许此定义。
```

*形参列表* 中的每个形参均是引入单个变量的[声明]({{< ref "/c/language/declarations" >}})，变量拥有下列额外属性：

- 声明符中的标识符是可选的（除非此函数声明是函数定义的一部分）(C23 前)

```c
int f(int, double); // OK
int g(int a, double b); // 也 OK
int f(int, double) { return 1; } // 错误：定义必须命名形参
// C23 起允许此定义。
```

- 对形参允许的[存储类说明符]({{< ref "/c/language/declarations/storage_duration" >}})仅有 `register`，而在非定义的函数声明中忽略它

```c
int f(static int x); // 错误
int f(int [static 10]); // OK （数组下标的 static 不是存储类说明符）
```

- 任何数组类型的形参都被调整到对应的指针类型，若数组声明符的方括号内有限定符，则它具有限定(C99 起)。

```c
int f(int[]); // 声明 int f(int*)
int g(const int[10]); // 声明 int g(const int*)
int h(int[const volatile]); // 声明 int h(int * const volatile)
int x(int[*]); // 声明 int x(int*)
```

- 任何函数类型的形参都被调整到对应的指针类型

```c
int f(char g(double)); // 声明 int f(char (*g)(double))
int h(int(void)); // 声明 int h(int (*)(void))
```

- 形参列表可以以 `, ...` 或`...`(C23 起) 终止，细节见[变参数函数]({{< ref "/c/language/functions/variadic" >}})。

```c
int f(int, ...);
```

- 形参不能拥有 void 类型（但可以拥有指向 void 指针类型）。完全由关键词 void 组成的特殊形参列表用于声明不接收实参的函数。

```c
int f(void); // OK
int g(void x); // 错误
```

- 任何出现于形参列表中，能被当成 typedef 名或形参名的标识符，都会被当做 typedef 名：int f([size_t](http://zh.cppreference.com/w/c/types/size_t), [uintptr_t](http://zh.cppreference.com/w/c/types/integer)) 被分析成新式声明符，声明一个函数，它接收二个 `size_t` 和 `uintptr_t` 类型的无名形参，而非开始定义接收二个名为“ `size_t` ”和“ `uintptr_t` ”的函数的旧式声明符。
- 形参列表可以拥有不完整类型而且可以用 VLA 记法 [*](C99 起)（但在[函数定义]({{< ref "/c/language/functions/function_definition" >}})中，在数组到指针和函数到指针调整后，形参类型必须完整）
- [属性说明符序列]({{< ref "/c/language/declarations/attributes" >}})亦能应用到函数形参。(C23 起)

​	其他函数调用机制上的细节见[函数调用运算符]({{< ref "/c/language/expressions/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8" >}})，关于从函数返回，见 [`return`]({{< ref "/c/language/statements/return" >}}) 。

## 注解

​	不同于 C++，声明符 `f()` 与 `f(void)` 拥有不同含义：声明符 `f(void)` 是新式（原型）声明符，声明函数不接收形参。声明符 `f()` 是声明函数接收*未指定*数量的形参的声明符（除非用于函数定义）(C23 起)。

```c
int f(void); // 声明：不接收参数
int g(); // 声明：接收未知参数
 
int main(void) {
    f(1); // 编译时错误
    g(2); // 未定义行为
}
 
int f(void) { return 1; ) // 实际定义
int g(a,b,c,d) int a,b,c,d; { return 2; } // 实际定义
```

和在[函数定义]({{< ref "/c/language/functions/function_definition" >}})中不同，形参列表可以从 typedef 继承

```c
typedef int p(int q, int r); // p 是函数类型 int(int, int)
p f; // 声明 int f(int, int)
```

​	C89 中，*说明符与限定符* 是可选的，且若省略它，则函数的返回类型默认为 int（可以由 *声明符* 修改）。(C99 前) 

```c
*f() { // 返回 int* 的函数
   return NULL;
}
```



## 缺陷报告

下列更改行为的缺陷报告追溯地应用于以前出版的 C 标准。

| 缺陷报告                                                     | 应用于 | 出版时的行为       | 正确行为               |
| ------------------------------------------------------------ | ------ | ------------------ | ---------------------- |
| [DR 423](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_423) | C89    | 返回类型可以有限定 | 返回类型被隐式除去限定 |

## 参阅

函数声明的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/function)
