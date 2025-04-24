
+++
title = "<signal.h>"
date = 2025-04-24T18:33:46+08:00
weight = 120
type = "docs"
description = "信号处理"
isCJKLanguage = true
draft = false

+++

## 类型



### sig_atomic_t

原址：[https://zh.cppreference.com/w/c/program/sig_atomic_t](https://zh.cppreference.com/w/c/program/sig_atomic_t)

作用：可以从异步信号处理函数中将之当做原子实体进行访问的整数类型  (typedef)

备注：
```c
// 在标头 <signal.h> 定义
typedef /* 未指明 */ sig_atomic_t;
```

​	即使在进行由信号造成的异步中断时，亦能作为原子实体访问的整数类型。

**示例**

```c
#include <signal.h>
#include <stdio.h>
 
volatile sig_atomic_t gSignalStatus = 0;
 
void signal_handler(int signal)
{
    gSignalStatus = signal;
}
 
int main(void)
{
    /* 安装信号处理函数 */
    signal(SIGINT, signal_handler);
 
    printf("SignalValue:   %d\n", gSignalStatus);
    printf("Sending signal %d\n", SIGINT);
    raise(SIGINT);
    printf("SignalValue:   %d\n", gSignalStatus);
}
```

​	可能的输出：

```txt
SignalValue:   0
Sending signal 2
SignalValue:   2
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.14/2 Signal handling <signal.h> （第 194-195 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.14/2 Signal handling <signal.h> （第 265 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.14/2 Signal handling <signal.h> （第 246 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.7 SIGNAL HANDLING <signal.h>

**参阅**

| [signal<br />](https://zh.cppreference.com/w/c/program/signal) | 为特定的信号设置信号处理函数 (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| **sig_atomic_t** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/sig_atomic_t)** |                                     |






## 枚举




## 宏



### SIGABRT

原址：[https://zh.cppreference.com/w/c/program/SIG_types](https://zh.cppreference.com/w/c/program/SIG_types)

作用：定义信号类型  (宏常量)

备注：
```c
// 在标头 <signal.h> 定义
#define SIGTERM /* 由实现定义 */
#define SIGSEGV /* 由实现定义 */
#define SIGINT /* 由实现定义 */
#define SIGILL /* 由实现定义 */
#define SIGABRT /* 由实现定义 */
#define SIGFPE /* 由实现定义 */
```

​	上面每个宏常量都展开成拥有相异值的整数常量表达式，表示发送给程序的不同信号。

| 常量      | 解释                                                         |
| --------- | ------------------------------------------------------------ |
| `SIGTERM` | 发送给程序的终止请求                                         |
| `SIGSEGV` | 非法内存访问（段错误）                                       |
| `SIGINT`  | 外部中断，通常为用户所发动                                   |
| `SIGILL`  | 非法程序映像，例如非法指令                                   |
| `SIGABRT` | 异常终止条件，例如 [abort()](https://zh.cppreference.com/w/c/program/abort) 由所引发 |
| `SIGFPE`  | 错误的算术运算，如除以零                                     |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.14/3 Signal handling <signal.h> （第 193 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.14/3 Signal handling <signal.h> （第 265 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.14/3 Signal handling <signal.h> （第 246 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.7 SIGNAL HANDLING <signal.h>

**参阅**

| [signal<br />](https://zh.cppreference.com/w/c/program/signal) | 为特定的信号设置信号处理函数 (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [raise<br />](https://zh.cppreference.com/w/c/program/raise) | 运行特定信号的信号处理函数 (函数)   |
| **信号类型**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/SIG_types)** |                                     |





### SIGFPE

原址：[https://zh.cppreference.com/w/c/program/SIG_types](https://zh.cppreference.com/w/c/program/SIG_types)

作用：定义信号类型  (宏常量)

备注：
```c
// 在标头 <signal.h> 定义
#define SIGTERM /* 由实现定义 */
#define SIGSEGV /* 由实现定义 */
#define SIGINT /* 由实现定义 */
#define SIGILL /* 由实现定义 */
#define SIGABRT /* 由实现定义 */
#define SIGFPE /* 由实现定义 */
```

​	上面每个宏常量都展开成拥有相异值的整数常量表达式，表示发送给程序的不同信号。

| 常量      | 解释                                                         |
| --------- | ------------------------------------------------------------ |
| `SIGTERM` | 发送给程序的终止请求                                         |
| `SIGSEGV` | 非法内存访问（段错误）                                       |
| `SIGINT`  | 外部中断，通常为用户所发动                                   |
| `SIGILL`  | 非法程序映像，例如非法指令                                   |
| `SIGABRT` | 异常终止条件，例如 [abort()](https://zh.cppreference.com/w/c/program/abort) 由所引发 |
| `SIGFPE`  | 错误的算术运算，如除以零                                     |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.14/3 Signal handling <signal.h> （第 193 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.14/3 Signal handling <signal.h> （第 265 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.14/3 Signal handling <signal.h> （第 246 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.7 SIGNAL HANDLING <signal.h>

**参阅**

| [signal<br />](https://zh.cppreference.com/w/c/program/signal) | 为特定的信号设置信号处理函数 (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [raise<br />](https://zh.cppreference.com/w/c/program/raise) | 运行特定信号的信号处理函数 (函数)   |
| **信号类型**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/SIG_types)** |                                     |





### SIGILL

原址：[https://zh.cppreference.com/w/c/program/SIG_types](https://zh.cppreference.com/w/c/program/SIG_types)

作用：定义信号类型  (宏常量)

备注：
```c
// 在标头 <signal.h> 定义
#define SIGTERM /* 由实现定义 */
#define SIGSEGV /* 由实现定义 */
#define SIGINT /* 由实现定义 */
#define SIGILL /* 由实现定义 */
#define SIGABRT /* 由实现定义 */
#define SIGFPE /* 由实现定义 */
```

​	上面每个宏常量都展开成拥有相异值的整数常量表达式，表示发送给程序的不同信号。

| 常量      | 解释                                                         |
| --------- | ------------------------------------------------------------ |
| `SIGTERM` | 发送给程序的终止请求                                         |
| `SIGSEGV` | 非法内存访问（段错误）                                       |
| `SIGINT`  | 外部中断，通常为用户所发动                                   |
| `SIGILL`  | 非法程序映像，例如非法指令                                   |
| `SIGABRT` | 异常终止条件，例如 [abort()](https://zh.cppreference.com/w/c/program/abort) 由所引发 |
| `SIGFPE`  | 错误的算术运算，如除以零                                     |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.14/3 Signal handling <signal.h> （第 193 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.14/3 Signal handling <signal.h> （第 265 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.14/3 Signal handling <signal.h> （第 246 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.7 SIGNAL HANDLING <signal.h>

**参阅**

| [signal<br />](https://zh.cppreference.com/w/c/program/signal) | 为特定的信号设置信号处理函数 (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [raise<br />](https://zh.cppreference.com/w/c/program/raise) | 运行特定信号的信号处理函数 (函数)   |
| **信号类型**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/SIG_types)** |                                     |





### SIGINT

原址：[https://zh.cppreference.com/w/c/program/SIG_types](https://zh.cppreference.com/w/c/program/SIG_types)

作用：定义信号类型  (宏常量)

备注：
```c
// 在标头 <signal.h> 定义
#define SIGTERM /* 由实现定义 */
#define SIGSEGV /* 由实现定义 */
#define SIGINT /* 由实现定义 */
#define SIGILL /* 由实现定义 */
#define SIGABRT /* 由实现定义 */
#define SIGFPE /* 由实现定义 */
```

​	上面每个宏常量都展开成拥有相异值的整数常量表达式，表示发送给程序的不同信号。

| 常量      | 解释                                                         |
| --------- | ------------------------------------------------------------ |
| `SIGTERM` | 发送给程序的终止请求                                         |
| `SIGSEGV` | 非法内存访问（段错误）                                       |
| `SIGINT`  | 外部中断，通常为用户所发动                                   |
| `SIGILL`  | 非法程序映像，例如非法指令                                   |
| `SIGABRT` | 异常终止条件，例如 [abort()](https://zh.cppreference.com/w/c/program/abort) 由所引发 |
| `SIGFPE`  | 错误的算术运算，如除以零                                     |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.14/3 Signal handling <signal.h> （第 193 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.14/3 Signal handling <signal.h> （第 265 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.14/3 Signal handling <signal.h> （第 246 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.7 SIGNAL HANDLING <signal.h>

**参阅**

| [signal<br />](https://zh.cppreference.com/w/c/program/signal) | 为特定的信号设置信号处理函数 (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [raise<br />](https://zh.cppreference.com/w/c/program/raise) | 运行特定信号的信号处理函数 (函数)   |
| **信号类型**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/SIG_types)** |                                     |





### SIGSEGV

原址：[https://zh.cppreference.com/w/c/program/SIG_types](https://zh.cppreference.com/w/c/program/SIG_types)

作用：定义信号类型  (宏常量)

备注：
```c
// 在标头 <signal.h> 定义
#define SIGTERM /* 由实现定义 */
#define SIGSEGV /* 由实现定义 */
#define SIGINT /* 由实现定义 */
#define SIGILL /* 由实现定义 */
#define SIGABRT /* 由实现定义 */
#define SIGFPE /* 由实现定义 */
```

​	上面每个宏常量都展开成拥有相异值的整数常量表达式，表示发送给程序的不同信号。

| 常量      | 解释                                                         |
| --------- | ------------------------------------------------------------ |
| `SIGTERM` | 发送给程序的终止请求                                         |
| `SIGSEGV` | 非法内存访问（段错误）                                       |
| `SIGINT`  | 外部中断，通常为用户所发动                                   |
| `SIGILL`  | 非法程序映像，例如非法指令                                   |
| `SIGABRT` | 异常终止条件，例如 [abort()](https://zh.cppreference.com/w/c/program/abort) 由所引发 |
| `SIGFPE`  | 错误的算术运算，如除以零                                     |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.14/3 Signal handling <signal.h> （第 193 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.14/3 Signal handling <signal.h> （第 265 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.14/3 Signal handling <signal.h> （第 246 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.7 SIGNAL HANDLING <signal.h>

**参阅**

| [signal<br />](https://zh.cppreference.com/w/c/program/signal) | 为特定的信号设置信号处理函数 (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [raise<br />](https://zh.cppreference.com/w/c/program/raise) | 运行特定信号的信号处理函数 (函数)   |
| **信号类型**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/SIG_types)** |                                     |





### SIGTERM

原址：[https://zh.cppreference.com/w/c/program/SIG_types](https://zh.cppreference.com/w/c/program/SIG_types)

作用：定义信号类型  (宏常量)

备注：
```c
// 在标头 <signal.h> 定义
#define SIGTERM /* 由实现定义 */
#define SIGSEGV /* 由实现定义 */
#define SIGINT /* 由实现定义 */
#define SIGILL /* 由实现定义 */
#define SIGABRT /* 由实现定义 */
#define SIGFPE /* 由实现定义 */
```

​	上面每个宏常量都展开成拥有相异值的整数常量表达式，表示发送给程序的不同信号。

| 常量      | 解释                                                         |
| --------- | ------------------------------------------------------------ |
| `SIGTERM` | 发送给程序的终止请求                                         |
| `SIGSEGV` | 非法内存访问（段错误）                                       |
| `SIGINT`  | 外部中断，通常为用户所发动                                   |
| `SIGILL`  | 非法程序映像，例如非法指令                                   |
| `SIGABRT` | 异常终止条件，例如 [abort()](https://zh.cppreference.com/w/c/program/abort) 由所引发 |
| `SIGFPE`  | 错误的算术运算，如除以零                                     |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.14/3 Signal handling <signal.h> （第 193 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.14/3 Signal handling <signal.h> （第 265 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.14/3 Signal handling <signal.h> （第 246 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.7 SIGNAL HANDLING <signal.h>

**参阅**

| [signal<br />](https://zh.cppreference.com/w/c/program/signal) | 为特定的信号设置信号处理函数 (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [raise<br />](https://zh.cppreference.com/w/c/program/raise) | 运行特定信号的信号处理函数 (函数)   |
| **信号类型**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/SIG_types)** |                                     |





### SIG_DFL

原址：[https://zh.cppreference.com/w/c/program/SIG_strategies](https://zh.cppreference.com/w/c/program/SIG_strategies)

作用：定义信号处理策略  (宏常量)

备注：
```c
// 在标头 <signal.h> 定义
#define SIG_DFL /* 由实现定义 */
#define SIG_IGN /* 由实现定义 */
```

​	**SIG_DFL** 和 **SIG_IGN** 宏展开成不等于任何函数地址的整数表达式。宏定义用于 `[signal](http://zh.cppreference.com/w/c/program/signal)()` 函数的信号处理策略。

| 常量      | 解释         |
| --------- | ------------ |
| `SIG_DFL` | 默认信号处理 |
| `SIG_IGN` | 忽略信号     |

**示例**

```c
#include <signal.h>
#include <stdio.h>
 
int main(void)
{
    /* 使用默认信号处理 */
    raise(SIGTERM);
    printf("Exit main()\n");   /* 永不抵达 */
}
```

​	输出：

```txt
（无）
```

**示例**

```c
#include <signal.h>
#include <stdio.h>
 
int main(void)
{
    /* 忽略信号 */
    signal(SIGTERM, SIG_IGN);
    raise(SIGTERM);
    printf("Exit main()\n");
}
```

​	输出：

```txt
Exit main()
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.14/3 Signal handling <signal.h> （第 193 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.14/3 Signal handling <signal.h> （第 265 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.14/3 Signal handling <signal.h> （第 246 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.7 SIGNAL HANDLING <signal.h>

**参阅**

**SIG_DFL, SIG_IGN** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/SIG_strategies)**





### SIG_ERR

原址：[https://zh.cppreference.com/w/c/program/SIG_ERR](https://zh.cppreference.com/w/c/program/SIG_ERR)

作用：遇到错误  (宏常量)

备注：
```c
// 在标头 <signal.h> 定义
#define SIG_ERR /* 由实现定义 */
```

​	`void (*)(int)` 类型的值。当由 [signal](https://zh.cppreference.com/w/c/program/signal) 所返回时，指示出现了错误。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
#include <signal.h>
 
void signal_handler(int sig)
{
    printf("Received signal: %d\n", sig);
}
 
int main(void)
{
    /* 安装信号处理函数。 */
    if (signal(SIGTERM, signal_handler) == SIG_ERR)
    {
        printf("Error while installing a signal handler.\n");
        exit(EXIT_FAILURE);
    }
 
    printf("Sending signal %d\n", SIGTERM);
    if (raise(SIGTERM) != 0)
    {
        printf("Error while raising the SIGTERM signal.\n");
        exit(EXIT_FAILURE);
    }
 
    printf("Exit main()\n");
    return EXIT_SUCCESS;
}
```

​	输出：

```txt
Sending signal 15
Received signal 15
Exit main()
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.14/3 Signal handling <signal.h> （第 194 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.14/3 Signal handling <signal.h> （第 265 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.14/3 Signal handling <signal.h> （第 246 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.7 SIGNAL HANDLING <signal.h>

**参阅**

| [signal<br />](https://zh.cppreference.com/w/c/program/signal) | 为特定的信号设置信号处理函数 (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| **SIG_ERR** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/SIG_ERR)** |                                     |





### SIG_IGN

原址：[https://zh.cppreference.com/w/c/program/SIG_strategies](https://zh.cppreference.com/w/c/program/SIG_strategies)

作用：定义信号处理策略  (宏常量)

备注：
```c
// 在标头 <signal.h> 定义
#define SIG_DFL /* 由实现定义 */
#define SIG_IGN /* 由实现定义 */
```

​	**SIG_DFL** 和 **SIG_IGN** 宏展开成不等于任何函数地址的整数表达式。宏定义用于 `[signal](http://zh.cppreference.com/w/c/program/signal)()` 函数的信号处理策略。

| 常量      | 解释         |
| --------- | ------------ |
| `SIG_DFL` | 默认信号处理 |
| `SIG_IGN` | 忽略信号     |

**示例**

```c
#include <signal.h>
#include <stdio.h>
 
int main(void)
{
    /* 使用默认信号处理 */
    raise(SIGTERM);
    printf("Exit main()\n");   /* 永不抵达 */
}
```

​	输出：

```txt
（无）
```

**示例**

```c
#include <signal.h>
#include <stdio.h>
 
int main(void)
{
    /* 忽略信号 */
    signal(SIGTERM, SIG_IGN);
    raise(SIGTERM);
    printf("Exit main()\n");
}
```

​	输出：

```txt
Exit main()
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.14/3 Signal handling <signal.h> （第 193 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.14/3 Signal handling <signal.h> （第 265 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.14/3 Signal handling <signal.h> （第 246 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.7 SIGNAL HANDLING <signal.h>

**参阅**

**SIG_DFL, SIG_IGN** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/SIG_strategies)**






## 函数



### raise

原址：[https://zh.cppreference.com/w/c/program/raise](https://zh.cppreference.com/w/c/program/raise)

作用：运行特定信号的信号处理函数  (函数)

备注：
```c
// 在标头 <signal.h> 定义
int raise( int sig );
```

​	发送 `sig` 信号给程序。调用以 [signal()](https://zh.cppreference.com/w/c/program/signal) 指定的信号处理函数。

​	若仍未用 [signal()](https://zh.cppreference.com/w/c/program/signal) 设置用户定义的信号处理策略，则忽略信号还是调用默认处理函数是实现定义的。

**参数**

| sig  | -    | 要发送的信号。可为实现定义值或下列值之一：[SIGABRT<br />SIGFPE<br />SIGILL<br />SIGINT<br />SIGSEGV<br />SIGTERM<br />](https://zh.cppreference.com/w/c/program/SIG_types)定义信号类型 (宏常量) |
| ---- | ---- | ------------------------------------------------------------ |
|      |      |                                                              |

**返回值**

​	成功时为 `0`，失败时为非零。

**示例**

```c
#include <signal.h>
#include <stdio.h>
 
void signal_handler(int signal)
{
    printf("Received signal %d\n", signal);
}
 
int main(void)
{
    // 安装信号处理函数。
    signal(SIGTERM, signal_handler);
 
    printf("Sending signal %d\n", SIGTERM);
    raise(SIGTERM);
    printf("Exit main()\n");
}
```

​	输出：

```txt
Sending signal 15
Received signal 15
Exit main()
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.14.2.1 The raise function （第 194-195 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.14.2.1 The raise function （第 267 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.14.2.1 The raise function （第 248 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.7.2.1 The raise function

**参阅**

| [signal<br />](https://zh.cppreference.com/w/c/program/signal) | 为特定的信号设置信号处理函数 (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| **raise** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/raise)** |                                     |





### signal

原址：[https://zh.cppreference.com/w/c/program/signal](https://zh.cppreference.com/w/c/program/signal)

作用：为特定的信号设置信号处理函数  (函数)

备注：
```c
// 在标头 <signal.h> 定义
void (*signal( int sig, void (*handler) (int))) (int);
```

​	设置信号 `sig` 的错误处理函数。可将错误处理函数设置为，进行默认处理、忽略信号或调用用户定义函数。

​	当将信号处理设置为一个函数，而信号出现时，是否立即在信号处理函数开始前调用 `signal(sig, [SIG_DFL](http://zh.cppreference.com/w/c/program/SIG_strategies))` 是实现定义的。而且，实现可以在信号处理函数运行时阻止某个由实现定义的集合中的信号发生。

**参数**

| sig     | -    | 设置给信号处理函数的信号。能为实现定义的值或下列值之一：[SIGABRT<br />SIGFPE<br />SIGILL<br />SIGINT<br />SIGSEGV<br />SIGTERM<br />](https://zh.cppreference.com/w/c/program/SIG_types)定义信号类型 (宏常量) |
| ------- | ---- | ------------------------------------------------------------ |
| handler | -    | 信号处理函数。必须是下列之一：[SIG_DFL](https://zh.cppreference.com/w/c/program/SIG_strategies) 宏。将信号处理函数默认设为默认信号处理函数。[SIG_IGN](https://zh.cppreference.com/w/c/program/SIG_strategies) 宏。忽略信号。函数指针。函数签名必须等价于如下形式：`void fun(int sig);` |

**返回值**

​	成功时返回之前设置的信号处理，失败时为 [SIG_ERR](https://zh.cppreference.com/w/c/program/SIG_ERR)（一些实现上能禁用设置信号处理函数）。

### 信号处理函数

​	安装为信号处理函数的用户定义函数上，强制了下列限制。

​	若用户定义函数在处理 [SIGFPE](https://zh.cppreference.com/w/c/program/SIG_types)、[SIGILL](https://zh.cppreference.com/w/c/program/SIG_types) 或 [SIGSEGV](https://zh.cppreference.com/w/c/program/SIG_types) 时返回，则行为未定义。

​	如果作为 [abort](https://zh.cppreference.com/w/c/program/abort) 或 [raise](https://zh.cppreference.com/w/c/program/raise) 的结果调用了信号处理函数，若信号处理函数调用 [raise](https://zh.cppreference.com/w/c/program/raise)，则行为未定义。

​	若信号处理函数不是作为 [abort](https://zh.cppreference.com/w/c/program/abort) 或 [raise](https://zh.cppreference.com/w/c/program/raise) 的结果调用（换言之，信号处理是*异步的*），则在下列场合行为未定义

- 信号处理函数调用了任何标准库内的函数，除了

  - [abort](https://zh.cppreference.com/w/c/program/abort)
  - [_Exit](https://zh.cppreference.com/w/c/program/_Exit)
  - [quick_exit](https://zh.cppreference.com/w/c/program/quick_exit)
  - 以当前处理信号的编号为第一实参调用 `signal`（异步处理函数可重复注册其自身，但不能注册其他信号）。
  - 来自 [``](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C) 的原子函数，若原子参数为免锁
  - [atomic_is_lock_free](https://zh.cppreference.com/w/c/atomic/atomic_is_lock_free)（以任何类型的原子实参）

- 除了赋值给静态 `volatile [sig_atomic_t](http://zh.cppreference.com/w/c/program/sig_atomic_t)` 对象外，信号处理函数使用任何拥有静态或线程局域(C11 起)[存储期](https://zh.cppreference.com/w/c/language/storage_duration)，且非免锁[原子](https://zh.cppreference.com/w/c/language/atomic)的(C11 起)对象。

​	进入信号处理函数时，浮点环境状态和所有对象的值是未指定的，除了

- `volatile [sig_atomic_t](http://zh.cppreference.com/w/c/program/sig_atomic_t)` 类型的对象
- 免锁原子类型对象 (C11 起)
- 通过 [atomic_signal_fence](https://zh.cppreference.com/w/c/atomic/atomic_signal_fence) 使之可见的副效应 (C11 起)

​	从信号处理函数返回时，信号处理函数所修改的任何对象的值，除了 `volatile [sig_atomic_t](http://zh.cppreference.com/w/c/program/sig_atomic_t)` 及免锁原子(C11 起)对象，均为未定义。

​	若 `signal` 被用于多线程程序，则行为未定义。不要求它是线程安全的。

**注解**

​	POSIX 要求 `signal` 为线程安全的，而且能从任何信号处理函数调用[异步信号安全（async-signal-safe）库函数列表](http://pubs.opengroup.org/onlinepubs/9699919799/functions/V2_chap02.html#tag_15_04)中的函数。

​	除了 `abort` 和 `raise` 外，POSIX 还指定 `kill`、`pthread_kill` 以及 `sigqueue` 可生成同步信号。

​	POSIX 推荐用 [`sigaction`](http://pubs.opengroup.org/onlinepubs/9699919799/functions/sigaction.html) 替代 `signal`，因为其行为不明确性，以及有关执行信号处理函数时投递信号的严重的实现不一致性。

**示例**

```c
#include <signal.h>
#include <stdio.h>
 
volatile sig_atomic_t gSignalStatus;
 
void signal_handler(int signal)
{
  gSignalStatus = signal;
}
 
int main(void)
{
  signal(SIGINT, signal_handler);
 
  printf("SignalValue: %d\n", gSignalStatus);
  printf("Sending signal: %d\n", SIGINT);
  raise(SIGINT);
  printf("SignalValue: %d\n", gSignalStatus);
}
```

​	输出：

```txt
SignalValue: 0
Sending signal: 2
SignalValue: 2
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.14.1.1 The signal function （第 193-194 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.14.1.1 The signal function （第 266-267 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.14.1.1 The signal function （第 247-248 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.7.1.1 The signal function

**参阅**

| [raise<br />](https://zh.cppreference.com/w/c/program/raise) | 运行特定信号的信号处理函数 (函数) |
| ------------------------------------------------------------ | --------------------------------- |
| **signal** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/signal)** |                                   |






