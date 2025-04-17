+++
title = "可变参数函数"
date = 2025-04-14T22:48:31+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/variadic](https://zh.cppreference.com/w/c/variadic)

​	可变参数函数是使用可变数量实参的函数（例如 [printf](https://zh.cppreference.com/w/c/io/fprintf)）。

​	可变参数函数使用在其最后一个参数后加省略号声明，例如 int [printf](http://zh.cppreference.com/w/c/io/fprintf)(const char* format, ...);。语法和自动实参转换的额外细节见[变长实参]({{< ref "/c/language/functions/variadic" >}})。

​	从函数体内使用以下工具访问可变实参：

## 类型

| [va_list](https://zh.cppreference.com/w/c/variadic/va_list) | 保有 `va_start`、`va_arg`、`va_end` 及 `va_copy` 所需的信息 (typedef) |
| ----------------------------------------------------------- | ------------------------------------------------------------ |

## 宏

| 在标头 `<stdarg.h>` 定义                                     |                                   |
| ------------------------------------------------------------ | --------------------------------- |
| [va_start](https://zh.cppreference.com/w/c/variadic/va_start) | 令函数得以访问可变实参 (宏函数)   |
| [va_arg](https://zh.cppreference.com/w/c/variadic/va_arg)    | 访问下一个可变函数实参 (宏函数)   |
| [va_copy](https://zh.cppreference.com/w/c/variadic/va_copy)(C99) | 创造函数可变实参的副本 (宏函数)   |
| [va_end](https://zh.cppreference.com/w/c/variadic/va_end)    | 结束对函数可变实参的遍历 (宏函数) |

## 示例

​	打印不同类型的值。

```c
#include <stdarg.h>
#include <stdio.h>
 
void simple_printf(const char* fmt, ...)
{
    va_list args;
 
    for (va_start(args, fmt); *fmt != '\0'; ++fmt)
    {
        switch(*fmt)
        {
            case 'd':
            {
                int i = va_arg(args, int);
                printf("%d\n", i);
                break;
            }
            case 'c':
            {
                // 将提升 'char' 类型值为 'int'
                // C 中字符常量自身为 'int' 类型
                int c = va_arg(args, int);
                printf("%c\n", c);
                break;
            }
            case 'f':
            {
                double d = va_arg(args, double);
                printf("%f\n", d);
                break;
            }
            default:
                puts("Unknown formatter!");
                goto END;
        }
    }
END: 
    va_end(args);
}
 
int main(void)
{
    simple_printf("dcff", 3, 'a', 1.969, 42.5); 
}
```

输出：

```txt
3
a
1.969000
42.50000
```
