
+++
title = "<stdarg.h>"
date = 2025-04-24T18:35:14+08:00
weight = 140
type = "docs"
description = "可变参数"
isCJKLanguage = true
draft = false

+++

## 类型



### va_list

原址：[https://zh.cppreference.com/w/c/variadic/va_list](https://zh.cppreference.com/w/c/variadic/va_list)

作用：保有 va_start、va_arg、va_end 及 va_copy 所需的信息  (typedef)

备注：
```c
// 在标头 <stdarg.h> 定义
/* 未指明 */ va_list;
```

​	`va_list` 是一个完整对象类型，适于保有宏 va_start、va_copy、va_arg 及 va_end 所需的信息。

​	若创建 `va_list` 的实例并传递给另一个函数，且在该函数中通过 va_arg 使用它，则在调用方函数中的任何后继调用必须前接对 va_end 的调用。

​	传递指向 `va_list` 对象的指针给另一个函数，并于该函数返回后使用该对象是合法的。

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.16/3 Variable arguments <stdarg.h> （第 269 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.15/3 Variable arguments <stdarg.h> （第 249 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.8 VARIABLE ARGUMENTS <stdarg.h>

**参阅**

| [va_start<br />](https://zh.cppreference.com/w/c/variadic/va_start) | 令函数得以访问可变实参 (宏函数)   |
| ------------------------------------------------------------ | --------------------------------- |
| [va_copy (C99)<br />](https://zh.cppreference.com/w/c/variadic/va_copy) | 创造函数可变实参的副本 (宏函数)   |
| [va_arg<br />](https://zh.cppreference.com/w/c/variadic/va_arg) | 访问下一个可变函数实参 (宏函数)   |
| [va_end<br />](https://zh.cppreference.com/w/c/variadic/va_end) | 结束对函数可变实参的遍历 (宏函数) |
| **va_list** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/variadic/va_list)** |                                   |






## 枚举




## 宏



### __STDC_VERSION_STDARG_H__

原址：

作用：

备注：





### va_arg

原址：[https://zh.cppreference.com/w/c/variadic/va_arg](https://zh.cppreference.com/w/c/variadic/va_arg)

作用：访问下一个可变函数实参  (宏函数)

备注：
```c
// 在标头 <stdarg.h> 定义
T va_arg( va_list ap, T );
```

​	`va_arg` 宏展开成 `T` 类型的表达式，表达式对应来自 va_list `ap` 的下个实参。

​	调用 `va_arg` 前，必须调用 va_start 或 va_copy 以初始化 `ap`，中间不能有 va_end 调用。每次调用 `va_arg` 宏都会修改 `ap`，令它指向下一个可变实参。

​	若 `ap` 中的下个实参（提升后）与 `T` 的类型不[兼容](https://zh.cppreference.com/w/c/language/type#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)，则行为未定义，除非：

- 一个类型是有符号整数类型，另一类型是对应的无符号整数类型，而且值可以被两类型一同表示；或
- 一个类型是指向 `void` 的指针，而另一个是指向字符类型的指针。

​	若在 `ap` 中无更多实参时调用 `va_arg`，则行为未定义。

**参数**

| ap   | -    | va_list 类型的实例    |
| ---- | ---- | --------------------- |
| T    | -    | `ap` 中下个参数的类型 |

### 展开值

​	`ap` 中的下个可变参数。

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

​	输出：

```txt
0.920258
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.16.2.2 The va_arg macro （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.16.1.1 The va_arg macro （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.16.1.1 The va_arg macro （第 269-270 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.15.1.1 The va_arg macro （第 249-250 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.8.1.2 The va_arg macro

**参阅**

| [va_copy (C99)<br />](https://zh.cppreference.com/w/c/variadic/va_copy) | 创造函数可变实参的副本 (宏函数)                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [va_end<br />](https://zh.cppreference.com/w/c/variadic/va_end) | 结束对函数可变实参的遍历 (宏函数)                            |
| [va_list<br />](https://zh.cppreference.com/w/c/variadic/va_list) | 保有 va_start、va_arg、va_end 及 va_copy 所需的信息 (typedef) |
| [va_start<br />](https://zh.cppreference.com/w/c/variadic/va_start) | 令函数得以访问可变实参 (宏函数)                              |
| **va_arg** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/variadic/va_arg)** |                                                              |






## 函数



### va_copy

原址：[https://zh.cppreference.com/w/c/variadic/va_copy](https://zh.cppreference.com/w/c/variadic/va_copy)

作用：创造函数可变实参的副本   (宏函数)

备注：
```c
// 在标头 <stdarg.h> 定义
void va_copy( va_list dest, va_list src );// (C99 起)
```

​	`va_copy` 宏把 `src` 复制到 `dest`。

​	在函数返回，或 `dest` 的任何再初始化（通过调用 va_start 或 va_copy）前，应该对 `dest` 调用 va_end。

**参数**

| dest | -    | 待初始化的 va_list 类型对象      |
| ---- | ---- | -------------------------------- |
| src  | -    | 将用以初始化 `dest` 的源 va_list |

### 展开值

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

​	可能的输出：

```txt
0.920258
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.16.1.2 The va_copy macro （第 270 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.15.1.2 The va_copy macro （第 250 页）

**参阅**

| [va_start<br />](https://zh.cppreference.com/w/c/variadic/va_start) | 令函数得以访问可变实参 (宏函数)                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [va_arg<br />](https://zh.cppreference.com/w/c/variadic/va_arg) | 访问下一个可变函数实参 (宏函数)                              |
| [va_end<br />](https://zh.cppreference.com/w/c/variadic/va_end) | 结束对函数可变实参的遍历 (宏函数)                            |
| [va_list<br />](https://zh.cppreference.com/w/c/variadic/va_list) | 保有 va_start、va_arg、va_end 及 va_copy 所需的信息 (typedef) |
| **va_copy** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/variadic/va_copy)** |                                                              |





### va_end

原址：[https://zh.cppreference.com/w/c/variadic/va_end](https://zh.cppreference.com/w/c/variadic/va_end)

作用：结束对函数可变实参的遍历  (宏函数)

备注：





### va_start

原址：[https://zh.cppreference.com/w/c/variadic/va_start](https://zh.cppreference.com/w/c/variadic/va_start)

作用：令函数得以访问可变实参  (宏函数)

备注：






