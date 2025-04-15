+++
title = "<errno.h>"
date = 2025-04-14T23:11:56+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

## 宏

### EDOM

原址：[https://zh.cppreference.com/w/c/error/errno_macros](https://zh.cppreference.com/w/c/error/errno_macros)

```c
#define EDOM   /* 由实现定义 */
```

### EILSEQ

原址：[https://zh.cppreference.com/w/c/error/errno_macros](https://zh.cppreference.com/w/c/error/errno_macros)

```c
#define EILSEQ /* 由实现定义 */
```

### ERANGE

原址：[https://zh.cppreference.com/w/c/error/errno_macros](https://zh.cppreference.com/w/c/error/errno_macros)

```c
#define ERANGE /* 由实现定义 */
```

​	每个定义于 [`<errno.h>`](https://zh.cppreference.com/w/c/header/errno) 的宏都展开成 int 类型的整数常量表达式，并且拥有独立的正整数值。ISO C 定义了下列常量。实现可以定义更多，只要以 'E' 开始，后随数字或大写字母即可。

| 在标头 `<errno.h>` 定义 |                                 |
| ----------------------- | ------------------------------- |
| EDOM                    | 数学参数在函数定义域外 (宏常量) |
| EILSEQ(C95)             | 非法字节序列 (宏常量)           |
| ERANGE                  | 结果过大 (宏常量)               |

**注解**

​	[POSIX](https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/errno.h.html) 和 [C++ 标准库](https://zh.cppreference.com/w/cpp/error/errno_macros)定义了许多额外的错误常量，而且各个实现可能定义更多，例如 Linux 上的 errno(3) 或 BSD 和 OS X 上的 intro(2)。

**示例**

```c
#include <errno.h>
#include <math.h>
#include <stdio.h>
#include <string.h>
 
int main(void)
{
    errno = 0;
    printf("log(-1.0) = %f\n", log(-1.0));
    printf("%s\n\n", strerror(errno));
 
    errno = 0;
    printf("log(0.0)  = %f\n", log(0.0));
    printf("%s\n", strerror(errno));
}
```

可能的输出：

```txt
log(-1.0) = nan
Numerical argument out of domain
 
log(0.0)  = -inf
Numerical result out of range
```



### errno

原址：[https://zh.cppreference.com/w/c/error/errno](https://zh.cppreference.com/w/c/error/errno)

```c
#define errno /* 由实现定义 */
```

​	`errno` 是一个预处理器宏（见后述），展开成线程局域的(C11 起) int 类型可修改左值。一些标准库函数通过写入正整数到 `errno` 指定错误。通常，会将 `errno` 的值设置为错误码之一。错误码作为以字母 `E` 后随大写字母或数字开始的宏常量，列于 [``](https://zh.cppreference.com/w/c/header/errno)。

​	`errno` 的值在程序启动时为 0 ，而且无论是否出现错误，都允许库函数将正整数写入 `errno` ，不过库函数决不会将 0 存储于 `errno`。

​	库函数 [perror](https://zh.cppreference.com/w/c/io/perror) 和 [strerror](https://zh.cppreference.com/w/c/string/byte/strerror) 能用于获得对应当前 `errno` 值的错误条件的文本描述。

**注解**

​	C11 前，C 标准有矛盾的要求，称 `errno` 是宏但*亦*称“不指明 `errno` 是宏还是声明带外部链接的标识符”。C11 修正了此错误，要求必须定义它为宏（参阅 WG14 [N1338](https://open-std.org/JTC1/SC22/WG14/www/docs/n1338.htm)）。

**示例**

```c
#include <errno.h>
#include <math.h>
#include <stdio.h>
 
void show_errno(void)
{
    const char *err_info = "未知错误";
    switch (errno)
    {
        case EDOM:
            err_info = "定义域错误";
            break;
        case EILSEQ:
            err_info = "非法序列";
            break;
        case ERANGE:
            err_info = "极点或值域错误";
            break;
        case 0:
            err_info = "无错误";
    }
    fputs(err_info, stdout);
    puts("发生");
}
 
int main(void)
{
    fputs("MATH_ERRNO ", stdout);
    puts(math_errhandling & MATH_ERRNO ? "已设置" : "未设置");
 
    errno = 0;
    (void)(1.0 / 0.0);
    show_errno();
 
    errno = 0;
    (void)acos(+1.1);
    show_errno();
 
    errno = 0;
    (void)log(0.0);
    show_errno();
 
    errno = 0;
    (void)sin(0.0);
    show_errno();
}
```

可能的输出：

```txt
MATH_ERRNO 已设置
发生无错误
发生定义域错误
发生极点或值域错误
发生无错误
```

## 函数