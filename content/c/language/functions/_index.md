+++
title = "functions"
date = 2025-04-13T13:48:17+08:00
weight = 80
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/functions](https://zh.cppreference.com/w/c/language/functions)

​	函数是将一个[标识符](https://zh.cppreference.com/w/c/language/identifier)（函数名）关联到一条[复合语句](https://zh.cppreference.com/w/c/language/statements#.E5.A4.8D.E5.90.88.E8.AF.AD.E5.8F.A5)（函数体）的 C 语言构造。每个 C 程序都从 [`main` 函数](https://zh.cppreference.com/w/c/language/main_function)开始执行，也从它或者调用其他用户定义函数或库函数终止。

```c
// 函数定义。
// 定义一个名为“ sum ”并拥有函数体“ { return x+y; } ”的函数
int sum(int x, int y) 
{
    return x + y;
}
```

​	函数由[函数声明](https://zh.cppreference.com/w/c/language/function_declaration)或[函数定义](https://zh.cppreference.com/w/c/language/function_definition)引入。

​	函数可以拥有零或更多个*形参*，它们为[函数调用运算符](https://zh.cppreference.com/w/c/language/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8)的*实参* ﻿所初始化，并且以通过其 [`return` 语句](https://zh.cppreference.com/w/c/language/return)向其调用者返回一个值。

```c
int n = sum(1, 2); // 形参 x 和 y 为实参 1 和 2 所初始化
```

​	函数体在[函数定义](https://zh.cppreference.com/w/c/language/function_definition)中提供。每个被用在表达式中的非[内联](https://zh.cppreference.com/w/c/language/inline)(C99 起)函数（除非其[不求值](https://zh.cppreference.com/w/c/language/expressions#.E4.B8.8D.E6.B1.82.E5.80.BC.E8.A1.A8.E8.BE.BE.E5.BC.8F)），必需在程序中[定义一次](https://zh.cppreference.com/w/c/language/extern#.E5.8D.95.E4.B8.80.E5.AE.9A.E4.B9.89.E8.A7.84.E5.88.99)。

​	不可以有嵌套函数（除了一些通过非标准的编译器扩展）：每个函数定义必须出现在文件作用域，而且函数无法访问来自其调用方的局部变量：

```c
int main(void) // main 函数的定义
{
    int sum(int, int); // 函数声明（可以出现于任何作用域）
    int x = 1;  // main 的局部变量
    sum(1, 2); // 函数调用
 
//    int sum(int a, int b) // 错误：不允许嵌套函数
//    {
//        return  a + b; 
//    }
}
int sum(int a, int b) // 函数定义
{
//    return x + a + b; //  错误：不能在 sum 中访问 main 的 x
    return a + b;
}
```

## 参阅

**函数声明**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/function)**