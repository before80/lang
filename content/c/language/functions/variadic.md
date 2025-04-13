+++
title = "可变函数"
date = 2025-04-13T13:57:02+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/variadic](https://zh.cppreference.com/w/c/language/variadic)

​	变参函数是能以不同数目实参调用的函数。

​	只有有原型[函数声明](https://zh.cppreference.com/w/c/language/function_declaration)可以有变长参数。它通过 `...` 形式的形参所指定，它必须出现在形参列表最后，并且跟随至少一个具名形参之后(C23 前)。省略号形参与前驱的形参必须由 `,` 分隔。

```c
// 有原型声明
int printx(const char* fmt, ...); // 此方法声明的函数
printx("hello world");     // 可能会以一个
printx("a=%d b=%d", a, b); // 或更多实参调用
 
int printz(...); // C23 起与 C++ 中 OK
// C23 前错误： ... 必须跟随至少一个具名形参
 
// int printy(..., const char* fmt); // 错误：... 必须在末尾
// int printa(const char* fmt...);   // C 中错误：要求 ',' ；C++ 中 OK
```

​	在[函数调用](https://zh.cppreference.com/w/c/language/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8)中，每个属于变长实参列表一部分的实参会经历名为[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)的隐式转换。

​	在函数体内使用变长实参时，这些实参的值必须用 [`<stdarg.h>` 库设施](https://zh.cppreference.com/w/c/variadic)访问：

| 在标头 `<stdarg.h>` 定义                                     |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [va_start](https://zh.cppreference.com/w/c/variadic/va_start) | 令函数得以访问可变实参 (宏函数)                              |
| [va_arg](https://zh.cppreference.com/w/c/variadic/va_arg)    | 访问下一个可变函数实参 (宏函数)                              |
| [va_copy](https://zh.cppreference.com/w/c/variadic/va_copy)(C99) | 创造函数可变实参的副本 (宏函数)                              |
| [va_end](https://zh.cppreference.com/w/c/variadic/va_end)    | 结束对函数可变实参的遍历 (宏函数)                            |
| [va_list](https://zh.cppreference.com/w/c/variadic/va_list)  | 保有 `va_start`、`va_arg`、`va_end` 及 `va_copy` 所需的信息 (`typedef`) |

## 注解

​	虽然旧式（无原型）[函数声明](https://zh.cppreference.com/w/c/language/function_declaration)允许后继的函数调用使用任意参数，但不允许它们为变长参数（C89 起）。这种函数的定义必须指定固定数目的参数，并且不能使用 `stdarg.h` 中的宏。

```c
// 旧式声明，C23 中移除
int printx(); // 此方式定义的函数
printx("hello world");     // 可以以一个
printx("a=%d b=%d", a, b); // 或更多实参调用
// 上述调用行为至少有一个是未定义的，取决于函数定义所接收的形参数
```

## 示例

```c
#include <stdio.h>
#include <time.h>
#include <stdarg.h>
 
void tlog(const char* fmt,...)
{
    char msg[50];
    strftime(msg, sizeof msg, "%T", localtime(&(time_t){time(NULL)}));
    printf("[%s] ", msg);
    va_list args;
    va_start(args, fmt);
    vprintf(fmt, args);
    va_end(args);
}
 
int main(void)
{
   tlog("logging %d %d %d...\n", 1, 2, 3);
}
```

输出：

```txt
[10:21:38] logging 1 2 3...
```

## 参阅

**变长实参**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/variadic_arguments)**