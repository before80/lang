+++
title = "函数定义"
date = 2025-04-13T13:53:32+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/function_definition](https://zh.cppreference.com/w/c/language/function_definition)

​	函数定义将函数体（声明与语句的序列）与函数名及形参列表关联。不同于[函数声明]({{< ref "/c/language/functions/function_declaration" >}})，函数定义只允许在文件作用域（不存在嵌套函数）。

​	C 支持二种函数定义的形式：

| *属性说明符序列*(可选) *说明符与限定符* *形参列表声明符* *函数体* | (1)  |          |
| ------------------------------------------------------------ | ---- | -------- |
| *说明符与限定符* *标识符列表声明符* *声明列表* *函数体*      | (2)  | (C23 前) |

其中

| *属性说明符序列*   | -    | (C23)可选的[属性]({{< ref "/c/language/declarations/attributes" >}})列表，应用到函数 |
| ------------------ | ---- | ------------------------------------------------------------ |
| *说明符与限定符*   | -    | 下列的组合[类型说明符]({{< ref "/c/language/declarations" >}})，可由声明符修改，组成*返回类型*[存储类说明符]({{< ref "/c/language/declarations/storage_duration" >}})，确定标识符的链接（`static`、`extern` 或无）函数说明符（[`inline`]({{< ref "/c/language/functions/inline" >}})、[`_Noreturn`]({{< ref "/c/language/functions/_Noreturn" >}}) 或无） |
| *形参列表声明符*   | -    | 用[形参列表]({{< ref "/c/language/functions/function_declaration" >}})指代函数各形参的函数类型的声明符 |
| *标识符列表声明符* | -    | 用[标识符列表]({{< ref "/c/language/functions/function_declaration" >}})指代函数各形参的函数类型的声明符 |
| *声明列表*         | -    | 在 *标识符列表声明符* 中声明每个形参的声明序列。这些声明不能使用初始化式，而且仅允许 register 作为[存储类说明符]({{< ref "/c/language/declarations/storage_duration" >}})。 |
| *函数体*           | -    | [复合语句]({{< ref "/c/language/statements#.E5.A4.8D.E5.90.88.E8.AF.AD.E5.8F.A5" >}})，是花括号所包括的声明及语句序列，只要调用此函数就会被执行 |

1) 新式 (C89) 函数定义。此定义引入函数自身，并为任何将来的[函数调用表达式]({{< ref "/c/language/expressions/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8" >}})提供函数原型，强迫从实参表达式转换到声明的形参类型。

```c
int max(int a, int b)
{
    return a>b?a:b;
}
 
double g(void)
{
    return 0.1;
}
```

2) (C23 前) 旧式 (K&R) 函数定义。此定义不表现为原型，而任何将来的[函数调用表达式]({{< ref "/c/language/expressions/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8" >}})将进行默认实参提升。

```c
int max(a, b)
int a, b;
{
    return a>b?a:b;
}
double g()
{
    return 0.1;
}
```

## 解释

​	同[函数声明]({{< ref "/c/language/functions/function_declaration" >}})，函数的返回类型由 *说明符与限定符* 中的类型说明符确定，并像在[声明]({{< ref "/c/language/declarations" >}})中一样可以由 *声明符* 修改。返回类型必须是完整的非数组对象类型或 void 类型。若返回类型会有 cvr 限定，则为构造函数类型的目的，将它调整为其无限定版本。

```c
void f(char *s) { puts(s); } // 返回类型为 void
int sum(int a, int b) { return a+b; } // 返回类型为int
int (*foo(const void *p))[3] { // 返回类型是指向 3 个 int 的数组的指针
    return malloc(sizeof(int[3]));
}
```

​	同[函数声明]({{< ref "/c/language/functions/function_declaration" >}})，为构造函数类型的目的，将形参类型从函数调整到指针，从数组调整到指针，并且为确定[兼容函数类型]({{< ref "/c/language/basic_concepts/type#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B" >}})的目的，忽略所有形参类型的顶层 cvr 限定符。

​	不同于[函数声明]({{< ref "/c/language/functions/function_declaration" >}})，不允许无名形参（否则旧式 (K&R) 函数定义中会有冲突），即使不在函数中使用也必须命名它们。仅有的例外是形参列表 (void)。(C23 前)

​	函数定义中形参可以为无名，因为旧式 (K&R) 函数定义已被移除。函数体内不能以名称访问无名形参。(C23 起)

```c
int f(int, int); // 声明
// int f(int, int) { return 7; } // C23 前错误，C23 起 OK
int f(int a, int b) { return 7; } // 定义
int g(void) { return 8; } // OK：void 不声明参数
```

​	在函数体内，每个具名形参都是[左值]({{< ref "/c/language/expressions/value_category" >}})表达式，它们拥有自动[存储期]({{< ref "/c/language/declarations/storage_duration" >}})和[块作用域]({{< ref "/c/language/basic_concepts/scope" >}})。形参在内存中的布局（或者它们究竟是否存储于内存中）是未指定的：这是[调用约定](https://en.wikipedia.org/wiki/Calling_convention)的一部分。

```
int main(int ac, char **av)
{
    ac = 2; // 形参是左值
    av = (char *[]){"abc", "def", NULL};
    f(ac, av);
}
```

​	函数调用机制上的其他细节见[函数调用运算符]({{< ref "/c/language/expressions/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8" >}})，关于从函数返回，见 [return]({{< ref "/c/language/statements/return" >}}) 。

​	`__func__`在每个 *函数体* 内，拥有块作用域和静态存储期的预定义变量 `__func__` 可用，它如同通过以下方式紧跟开花括号后定义：(C99 起)

```c
static const char __func__[] = "function name";
```

​	此特殊标识符有时与[预定义宏常量]({{< ref "/c/language/preprocessor/replace" >}}) __FILE__ 及 __LINE__ 结合使用，例如为 [assert](https://zh.cppreference.com/w/c/error/assert) 所用。(C99 起)

## 注解

​	参数列表必须显式存在于声明器中，不能从 typedef 继承它

```c
typedef int p(int q, int r); // p 是类型为 int(int, int) 的函数
p f { return q + r; } // 错误
```

​	C89 中，*说明符与限定符* 是可选的，若省略它，则函数返回类型默认为 int（可由 *声明符* 修改）。另外，旧式定义不要求在 *声明列表* 中声明每个形参。任何缺少声明的参数拥有 int 类型(C99 前)

```c
max(a, b) // a 和 b 拥有 int 类型，返回类型为 int
{
    return a>b?a:b;
}
```



## 缺陷报告

下列更改行为的缺陷报告追溯地应用于以前出版的 C 标准。

| 缺陷报告                                                     | 应用于 | 出版时的行为       | 正确行为               |
| ------------------------------------------------------------ | ------ | ------------------ | ---------------------- |
| [DR 423](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_423) | C89    | 返回类型可以有限定 | 返回类型被隐式除去限定 |

## 参阅

**函数定义**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/function#.E5.87.BD.E6.95.B0.E5.AE.9A.E4.B9.89)**
