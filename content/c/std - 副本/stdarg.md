+++
title = "<stdarg.h>"
date = 2025-04-14T22:51:57+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/variadic/va_start](https://zh.cppreference.com/w/c/variadic/va_start)

## 类型

### va_list

原址：[https://zh.cppreference.com/w/c/variadic/va_list](https://zh.cppreference.com/w/c/variadic/va_list)

```c
/* 未指明 */ va_list;
```

​	`va_list` 是一个完整对象类型，适于保有宏 va_start、va_copy、va_arg 及 va_end 所需的信息。

​	若创建 `va_list` 的实例并传递给另一个函数，且在该函数中通过 va_arg 使用它，则在调用方函数中的任何后继调用必须前接对 va_end 的调用。

传递指向 `va_list` 对象的指针给另一个函数，并于该函数返回后使用该对象是合法的。

## 宏

### va_arg

原址：[https://zh.cppreference.com/w/c/variadic/va_arg](https://zh.cppreference.com/w/c/variadic/va_arg)

```c
T va_arg( va_list ap, T );
```

​	`va_arg` 宏展开成 `T` 类型的表达式，表达式对应来自 va_list `ap` 的下个实参。

​	调用 `va_arg` 前，必须调用 va_start 或 va_copy 以初始化 `ap`，中间不能有 va_end 调用。每次调用 `va_arg` 宏都会修改 ap，令它指向下一个可变实参。

​	若 `ap` 中的下个实参（提升后）与 `T` 的类型不[兼容](https://zh.cppreference.com/w/c/language/type#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)，则行为未定义，除非：

- 一个类型是有符号整数类型，另一类型是对应的无符号整数类型，而且值可以被两类型一同表示；或
- 一个类型是指向 `void` 的指针，而另一个是指向字符类型的指针。

​	若在 `ap` 中无更多实参时调用 `va_arg`，则行为未定义。

**参数**

| ap   | -    | va_list 类型的实例  |
| ---- | ---- | ------------------- |
| T    | -    | ap 中下个参数的类型 |

展开值

​	ap 中的下个可变参数。

**示例**

```c
#include <math.h>
#include <stdarg.h>
#include <stdio.h>
 
double stddev(int count, ...)
{
    double sum = 0;
    double sum_sq = 0;
    va_list args;
    va_start(args, count);
    for (int i = 0; i < count; ++i)
    {
        double num = va_arg(args, double);
        sum += num;
        sum_sq += num*num;
    }
    va_end(args);
    return sqrt(sum_sq / count - (sum / count) * (sum / count));
}
 
int main(void) 
{
    printf("%f\n", stddev(4, 25.0, 27.3, 26.9, 25.7));
}
```

输出：

```txt
0.920258
```

### va_copy <- 99+

原址：[https://zh.cppreference.com/w/c/variadic/va_copy](https://zh.cppreference.com/w/c/variadic/va_copy)

```c
void va_copy( va_list dest, va_list src ); // (C99 起)
```

​	`va_copy` 宏把 `src` 复制到 `dest`。

​	在函数返回，或 `dest` 的任何再初始化（通过调用 va_start 或 va_copy）前，应该对 `dest` 调用 va_end。

**参数**

| dest | -    | 待初始化的 va_list 类型对象      |
| ---- | ---- | -------------------------------- |
| src  | -    | 将用以初始化 `dest` 的源 va_list |

**展开值**

​	（无）

**示例**

```c
#include <stdio.h>
#include <stdarg.h>
#include <math.h>
 
double sample_stddev(int count, ...) 
{
    /* 以 args1 计算平均数。 */
    double sum = 0;
    va_list args1;
    va_start(args1, count);
    va_list args2;
    va_copy(args2, args1);   /* 复制 va_list 对象 */
    for (int i = 0; i < count; ++i) {
        double num = va_arg(args1, double);
        sum += num;
    }
    va_end(args1);
    double mean = sum / count;
 
    /* 以args2和平均数计算标准差。 */
    double sum_sq_diff = 0;
    for (int i = 0; i < count; ++i) {
        double num = va_arg(args2, double);
        sum_sq_diff += (num-mean) * (num-mean);
    }
    va_end(args2);
    return sqrt(sum_sq_diff / count);
}
 
int main(void) 
{
    printf("%f\n", sample_stddev(4, 25.0, 27.3, 26.9, 25.7));
}
```

可能的输出：

```txt
0.920258
```

### va_end

原址：[https://zh.cppreference.com/w/c/variadic/va_end](https://zh.cppreference.com/w/c/variadic/va_end)

```c
void va_end( va_list ap );
```

​	`va_end` 宏对由 va_start 或 va_copy 的调用所初始化的 `ap` 对象进行清理。`va_end` 可以修改 `ap` 的值，使得它不再能使用。

​	若无对应的对 va_start 或 va_copy 调用，或在调用 va_start 或 va_copy 的函数返回前没有调用 `va_end`，则行为未定义。

**参数**

| ap   | -    | 待清理的 va_list 类型的实例 |
| ---- | ---- | --------------------------- |

**展开值**

（无）

### va_start

原址：[https://zh.cppreference.com/w/c/variadic/va_start](https://zh.cppreference.com/w/c/variadic/va_start)

```c
void va_start( va_list ap, parmN ); // (C23 前)
void va_start( va_list ap, ... ); // (C23 起)
```

`va_start` 宏使函数能访问跟在具名实参 `parmN` 后的(C23 前)可变参数。

应当在任何对 va_arg 的调用前，以合法的 va_list 对象 `ap` 调用 `va_start`。

​	若 `parmN` 声明带有 `register` 存储类说明符、数组类型、函数类型，或与默认参数提升结果类型不兼容的类型，则行为未定义。(C23 前)

​	仅求值首个传递给 `va_start` 的实参。任何其他实参既不被展开亦不被以任何方式使用。(C23 起)

**参数**

| ap    | -    | va_list 类型的实例       |
| ----- | ---- | ------------------------ |
| parmN | -    | 首个可变形参前的具名形参 |

**展开值**

​	（无）

**示例**

```c
#include <stdio.h>
#include <stdarg.h>
 
int add_nums(int count, ...) 
{
    int result = 0;
    va_list args;
    va_start(args, count); // C23 起能省略 count
 
    for (int i = 0; i < count; ++i) {
        result += va_arg(args, int);
    }
    va_end(args);
    return result;
}
 
#if __STDC_VERSION__ > 201710L
// 同上，C23 起合法
int add_nums_c23(...)
{
    int result = 0;
    va_list args;
    va_start(args);
 
    int count = va_arg(args, int);
    for (int i = 0; i < count; ++i) {
        result += va_arg(args, int);
    }
 
    va_end(args);
}
#endif
 
int main(void) 
{
    printf("%d\n", add_nums(4, 25, 25, 50, 50));
#if __STDC_VERSION__ > 201710L
    printf("%d\n", add_nums_C23(4, 25, 25, 50, 50));
#endif
}
```

可能的输出：

```txt
150
150
```





## 函数

