+++
title = "stdlib.h"
date = 2025-04-14T16:54:35+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

## 宏

### EXIT_SUCCESS 

原址：[https://zh.cppreference.com/w/c/program/EXIT_status](https://zh.cppreference.com/w/c/program/EXIT_status)

```c
#define EXIT_SUCCESS /* 由实现定义 */
```



### EXIT_FAILURE 

原址：[https://zh.cppreference.com/w/c/program/EXIT_status](https://zh.cppreference.com/w/c/program/EXIT_status)

```c
#define EXIT_FAILURE /* 由实现定义 */
```

​	`EXIT_SUCCESS` 和 `EXIT_FAILURE` 宏展开成能用作 [exit](https://zh.cppreference.com/w/c/program/exit) 的实参的整数常量表达式（从而作为从 [`main` 函数](https://zh.cppreference.com/w/c/language/main_function)返回的值），并指示程序执行状态。

| 常量           | 说明         |
| -------------- | ------------ |
| `EXIT_SUCCESS` | 程序执行成功 |
| `EXIT_FAILURE` | 程序执行失败 |

**注解**

`EXIT_SUCCESS` 和值零都能指示程序执行成功的状态，尽管并不要求 `EXIT_SUCCESS` 等于零。

示例

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    FILE* fp = fopen("data.txt","r");
    if (fp == NULL)
    {
       fprintf(stderr,"fopen() failed in file %s at line # %d", __FILE__, __LINE__);
       exit(EXIT_FAILURE);
    }
 
    /* 正常进程持续至此。 */
    fclose(fp);
    printf("Normal Return\n");
 
    return EXIT_SUCCESS;
}
```

​	输出：

```txt
fopen() failed in file main.cpp at line # 9
```

## 函数

### _Exit

原址：[https://zh.cppreference.com/w/c/program/_Exit](https://zh.cppreference.com/w/c/program/_Exit)

```c
void _Exit( int exit_code ); // (C99 起)(C11 前)
_Noreturn void _Exit( int exit_code );// (C11 起)(C23 前)
[[noreturn]] void _Exit( int exit_code );// (C23 起)
```

​	导致发生程序正常终止，但不完全清理资源。

​	不调用传递给 [at_quick_exit()](https://zh.cppreference.com/w/c/program/at_quick_exit) 或 [atexit()](https://zh.cppreference.com/w/c/program/atexit) 的函数。是否将未写入数据冲入打开的流、关闭打开的流或移除临时文件是实现定义的。

​	若 `exit_code` 为 0 或 [EXIT_SUCCESS](https://zh.cppreference.com/w/c/program/EXIT_status)，则将指示成功终止的状态返回给宿主环境。若 `exit_code` 为 [EXIT_FAILURE](https://zh.cppreference.com/w/c/program/EXIT_status)，则返回指示*不成功*终止的实现定义状态。其他情况下返回实现定义的状态值。

**参数**

| exit_code | -    | 程序的退出状态 |
| --------- | ---- | -------------- |

**返回值**

（无）

**示例**

```c
#include <stdlib.h>
#include <stdio.h>
 
/* _Exit 不调用 atexit 所注册的函数。 */
void f1(void)
{
    puts("pushed first");
}
 
void f2(void)
{
    puts("pushed second");
}
 
int main(void)
{
    printf("Enter main()\n");
    atexit(f1);
    atexit(f2);
    fflush(stdout);   /* _Exit 可能不冲入未写入的缓冲数据 */
    _Exit(0);
}
```

输出：

```txt
Enter main()
```



### abort 

原址：[https://zh.cppreference.com/w/c/program/abort](https://zh.cppreference.com/w/c/program/abort)

```c
void abort(void); // (C11 前)
_Noreturn void abort(void); // (C11 起) (C23 前)
[[noreturn]] void abort(void); // (C23 起)
```

​	导致程序异常终止，除非传递给 [signal](https://zh.cppreference.com/w/c/program/signal) 的信号处理函数正在捕捉 [SIGABRT](https://zh.cppreference.com/w/c/program/SIG_types) 且该处理函数不返回。

​	不调用传递给 [atexit()](https://zh.cppreference.com/w/c/program/atexit) 的函数。是否关闭打开的资源，例如文件，是实现定义的。向宿主环境返回指示不成功执行的实现定义状态。

**参数**

（无）

**返回值**

（无）

**注解**

​	POSIX [指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/abort.html) `abort()` 函数撤除阻塞，或忽略 `SIGABRT` 信号。

​	某些编译器内建子程序，例如 [`__builtin_trap`](https://gcc.gnu.org/onlinedocs/gcc/Other-Builtins.html)（gcc、clang 及 icc）或 [`__fastfail`](https://learn.microsoft.com/en-us/cpp/intrinsics/fastfail)/[`__debugbreak`](https://learn.microsoft.com/en-us/cpp/intrinsics/debugbreak)（msvc），能用于尽可能快地终止程序。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void) 
{
    FILE *fp = fopen("data.txt","r");
    if (fp == NULL)
    {
        fprintf(stderr, "error opening file data.txt in function main()\n");
        abort();
    }
 
    /* 正常处理持续至此。 */
    fclose(fp);
    printf("Normal Return\n");
    return 0;
}
```

​	输出：

```txt
error opening file data.txt in function main()
```

### at_quick_exit <- (C11 起)

原址：[https://zh.cppreference.com/w/c/program/at_quick_exit](https://zh.cppreference.com/w/c/program/at_quick_exit)

```c
int at_quick_exit( void (*func)(void) ); (C11 起)
```

​	注册 `func` 所指向的函数，使它在程序快速终止（通过 [quick_exit](https://zh.cppreference.com/w/c/program/quick_exit)）时得到调用。

​	`at_quick_exit` 是线程安全的：从多个线程调用此函数不会导入数据竞争。实现应当支持注册至少 32 个函数。确切的极限是由实现定义的。

​	所注册的函数在[程序正常终止](https://zh.cppreference.com/w/c/program/exit)时并不会被调用。如果需要函数在这种情况下被调用，必须使用 [atexit](https://zh.cppreference.com/w/c/program/atexit)。

**参数**

| func | -    | 指向要在程序快速终止调用的函数的指针 |
| ---- | ---- | ------------------------------------ |

**返回值**

若注册成功则为 0，否则为非零值。

**示例**

```c
#include <stdlib.h>
#include <stdio.h>
 
void f1(void)
{
    puts("pushed first");
    fflush(stdout);
}
 
void f2(void)
{
    puts("pushed second");
}
 
int main(void)
{
    at_quick_exit(f1);
    at_quick_exit(f2);
    quick_exit(0);
}
```

输出：

```txt
pushed second
pushed first
```

### atexit

原址：[https://zh.cppreference.com/w/c/program/atexit](https://zh.cppreference.com/w/c/program/atexit)

```c
int atexit( void (*func)(void) );
```

​	注册 `func` 所指向的函数，使它在程序正常终止（通过 [exit()](https://zh.cppreference.com/w/c/program/exit) 或从 `main()` 返回）时得到调用。将以注册顺序的逆序调用这些函数，即首先执行最后调用的函数。

​	可以注册同一函数多于一次。

​	实现保证支持注册至少 32 个函数。确切的极限是由实现定义的。

**参数**

| func | -    | 指向要在程序正常终止时调用的函数的指针 |
| ---- | ---- | -------------------------------------- |

**返回值**

若注册成功则为 0，否则为非零值。

**示例**

```c
#include <stdlib.h>
#include <stdio.h>
 
void f1(void)
{
    puts("f1");
}
 
void f2(void)
{
    puts("f2");
}
 
int main(void)
{
    if ( ! atexit(f1) && ! atexit(f2) && ! atexit(f2) )
        return EXIT_SUCCESS ;
 
    // atexit registration failed
    return EXIT_FAILURE ;
 
}   // <- 若注册成功则会调用 f2, f2, f1
```

输出：

```txt
f2
f2
f1
```

### exit

原址：[https://zh.cppreference.com/w/c/program/exit](https://zh.cppreference.com/w/c/program/exit)

```c
void exit( int exit_code ); // (C11 前)
_Noreturn void exit( int exit_code ); // (C11 起) (C23 前)
[[noreturn]] void exit( int exit_code ); // (C23 起)
```

​	导致发生正常程序终止。

​	进行几个清理步骤：

- 以注册的逆序调用传递给 [atexit](https://zh.cppreference.com/w/c/program/atexit) 的函数
- 冲入并关闭所有 C 流
- 移除 [tmpfile](https://zh.cppreference.com/w/c/io/tmpfile) 创建的文件
- 将控制返回给宿主环境。若 `exit_code` 为零或 [EXIT_SUCCESS](https://zh.cppreference.com/w/c/program/EXIT_status)，则返回指示成功终止的实现定义状态。若 `exit_code` 为 [EXIT_FAILURE](https://zh.cppreference.com/w/c/program/EXIT_status)，则返回指示不成功终止的实现定义状态。其他情况下返回实现定义的状态值。

**注解**

​	不调用由 [at_quick_exit](https://zh.cppreference.com/w/c/program/at_quick_exit) 注册的函数。

​	若程序调用 `exit` 多于一次，或它调用 `exit` 和 [quick_exit](https://zh.cppreference.com/w/c/program/quick_exit)，则行为未定义。

​	若在调用由 [atexit](https://zh.cppreference.com/w/c/program/atexit) 注册的函数期间，以 [longjmp](https://zh.cppreference.com/w/c/program/longjmp) 退出该函数，则行为未定义。

​	从 [`main` 函数](https://zh.cppreference.com/w/c/language/main_function)返回时，无论是通过 `return` 语句还是抵达函数尾，都会将 return 语句的实参（或若使用隐式返回，则为 0）作为 `exit_code` 传递并执行 `exit()`。

**参数**

| exit_code | -    | 程序的退出状态 |
| --------- | ---- | -------------- |

**返回值**

（无）

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    FILE *fp = fopen("data.txt","r");
    if (fp == NULL)
    {
       fprintf(stderr, "error opening file data.txt in function main()\n");
       exit( EXIT_FAILURE );
    }
    fclose(fp);
    printf("Normal Return\n");
    return EXIT_SUCCESS ;
}
```

可能的输出：

```txt
error opening file data.txt in function main()
```



### getenv

原址：[https://zh.cppreference.com/w/c/program/getenv](https://zh.cppreference.com/w/c/program/getenv)

```c
char *getenv( const char *name ); // 1
```

### getenv_s <- (C11 起)

原址：[https://zh.cppreference.com/w/c/program/getenv](https://zh.cppreference.com/w/c/program/getenv)

```c
errno_t getenv_s( size_t *restrict len, char *restrict value,
                  rsize_t valuesz, const char *restrict name ); // 2
```

1）在宿主指定的环境列表中，查找名为 `name` 的环境变量，并返回关联到匹配环境变量的字符串。环境变量的集合及修改它的方法是实现定义的。

 	此函数不保证是线程安全的。另一个对 `getenv` 的调用，和对 POSIX 函数 [setenv()](http://pubs.opengroup.org/onlinepubs/9699919799/functions/setenv.html)、[unsetenv()](http://pubs.opengroup.org/onlinepubs/9699919799/functions/unsetenv.html) 及[putenv()](http://pubs.opengroup.org/onlinepubs/9699919799/functions/putenv.html) 的调用，可能会使先前的调用返回的指针失效，或者修改先前调用所得的字符串。

​	 修改 `getenv` 返回的字符串会引起未定义行为。

2）同 (1)，但将环境变量的值写入用户提供的缓冲区 `value`（除非它为 `NULL`），而且将写入的字节数存储于用户提供的位置 `*len`（除非它为 `NULL`）。若环境变量未设置于环境中，则 `*len` 会被写入零（除非是 `NULL`），且 `'\0'` 会被写入 `value[0]`（除非是 `NULL`）。另外，在运行时检测下列错误并调用当前安装的[制约处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)函数

- `name` 是空指针
- `valuesz` 大于 RSIZE_MAX
- `value` 是空指针且 `valuesz` 非零

​	同所有边界检查函数，`getenv_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdlib.h>`](https://zh.cppreference.com/w/c/header/stdlib) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 `1` 才保证可用。

**参数**

| name    | -    | 标识要查找的环境变量名称的空终止字符串                       |
| ------- | ---- | ------------------------------------------------------------ |
| len     | -    | 指向用户提供的位置，`getenv_s` 将会在其中存储环境变量的长度  |
| value   | -    | 指向用户提供的字符数组，`getenv_s` 将会在其中存储环境变量内容 |
| valuesz | -    | 允许 `getenv_s` 对目标写入的最大字节数（缓冲区大小）         |

**返回值**

1) 标识环境变量的值的字符串，若找不到该环境变量则为空指针。
2) 若找到环境变量则为零，若找不到该环境变量或发生运行时强制违规，则为非零。错误的情况下，将 `*len` 写入零（除非 `len` 为空指针）。

**注解**

​	POSIX 系统上，亦可通过全局变量 `environ` 访问[环境变量](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap08.html#tag_08)，它于 `<unistd.h>` 中声明为 `extern char **environ;`，并可通过可选的 [`main` 函数](https://zh.cppreference.com/w/c/language/main_function)第三参数 `envp` 访问。

​	以空指针为 `value`，以零为 `valuesz` 调用 `getenv_s`，可用于确定保有整个结果所需的缓冲区大小。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    const char *name = "PATH";
    const char *env_p = getenv(name);
    if (env_p)
        printf("Your %s is %s\n", name, env_p);
}
```

​	可能的输出：

```txt
Your PATH is /home/gamer/.local/bin:/usr/local/bin:/usr/bin:/bin:/usr/share/games
```



### memalignment <- (C23 起)

原址：[https://zh.cppreference.com/w/c/program/memalignment](https://zh.cppreference.com/w/c/program/memalignment)

```c
size_t memalignment( const void *p ); // (C23 起)
```

​	返回提供的地址所满足的最大对齐。返回值能大于任何实现所支持的对齐值。如果 `p` 为空指针值，则返回 0 指示该指针不能用于访问任何类型的对象。

​	如果返回值大于或等于 alignof(T)，则类型 `T` 的对齐要求为该指针所满足。

​	[独立实现](https://zh.cppreference.com/w/c/language/conformance)需要提供 `memalignment`。

**参数**

| p    | -    | 要查询对齐的指针 |
| ---- | ---- | ---------------- |

**返回值**

`p` 的对齐值，或如果 `p` 为空指针值则为 0。

**注解**

​	在

- 空指针转型为整数 0，
- 指针值直接转型为虚拟地址的数值，且
- [size_t](https://zh.cppreference.com/w/c/types/size_t) 与 [uintptr_t](https://zh.cppreference.com/w/c/types/integer) 相同

的常见平台上，此函数能被实现为 return ([size_t](http://zh.cppreference.com/w/c/types/size_t))p & -([size_t](http://zh.cppreference.com/w/c/types/size_t))p;。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main()
{
    alignas(128) int i = 0;
    printf("%zu\n%zu\n", memalignment(nullptr), memalignment(&i));
}
```

可能的输出：

```txt
0
128
```

### quick_exit <- (C11 起)

原址：[https://zh.cppreference.com/w/c/program/quick_exit](https://zh.cppreference.com/w/c/program/quick_exit)

```c
_Noreturn void quick_exit( int exit_code ); // (C11 起) (C23 前)
[[noreturn]] void quick_exit( int exit_code );// (C23 起)
```

​	导致程序正常终止，而不完全清理资源。

​	以注册顺序的逆序调用传递给 [at_quick_exit](https://zh.cppreference.com/w/c/program/at_quick_exit) 的函数。调用完注册的函数后，调用 [_Exit](http://zh.cppreference.com/w/c/program/_Exit)(exit_code)。

**参数**

| exit_code | -    | 程序的退出状态 |
| --------- | ---- | -------------- |

**返回值**

（无）

**示例**

```c
#include <stdlib.h>
#include <stdio.h>
 
void f1(void)
{
    puts("pushed first");
    fflush(stdout);
}
 
void f2(void)
{
    puts("pushed second");
}
 
void f3(void)
{
    puts("won't be called");
}
 
int main(void)
{
    at_quick_exit(f1);
    at_quick_exit(f2);
    atexit(f3);
    quick_exit(0);
}
```

输出：

```txt
pushed second
pushed first
```





### system

原址：[https://zh.cppreference.com/w/c/program/system](https://zh.cppreference.com/w/c/program/system)

```c
int system( const char *command );
```

​	以参数 `command` 调用宿主环境的命令处理器。返回实现定义值（通常是被调用程序所返回的值）。

​	若 `command` 是空指针，则检查宿主环境是否有命令处理器，并若且仅若命令处理器存在才返回非零。

**参数**

| command | -    | 标识要运行于命令处理器的命令的字符串。若给出空指针，则检查其存在性 |
| ------- | ---- | ------------------------------------------------------------ |

**返回值**

​	实现定义值。若 `command` 为空指针，则当且仅当命令处理器存在才返回非零值。

**注意**

​	POSIX 系统上，可用 [`WEXITSTATUS` 和 `WSTOPSIG`](http://pubs.opengroup.org/onlinepubs/9699919799/functions/wait.html) 分解返回值。

​	相关的 POSIX 函数 [popen](http://pubs.opengroup.org/onlinepubs/9699919799/functions/popen.html) 令 `command` 生成的输出对调用方可用。

示例

​	此示例中有 unix 命令 **date +%A** 的系统调用，以及（可能安装的）**gcc** 编译器附带命令行参数（*`--version`*）的系统调用：

```c
#include <stdlib.h>
 
int main(void) {
    system("date +%A");
    system("gcc --version");
}
```

可能的输出：

```txt
Wednesday
gcc (GCC) 11.2.0
```