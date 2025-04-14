+++
title = "<stdlib.h>"
date = 2025-04-14T16:54:35+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

## 类型

### constraint_handler_t

```c
typedef void (*constraint_handler_t)( const char *restrict msg,
                                      void *restrict ptr,
                                      errno_t error); // (2)	(C11 起)
```

​	参见：[set_constraint_handler_s 函数](#set_constraint_handler_s)

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

​	`EXIT_SUCCESS` 和值零都能指示程序执行成功的状态，尽管并不要求 `EXIT_SUCCESS` 等于零。

**示例**

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

​	（无）

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

### abort_handler_s <- (C11 起)

原址：[https://zh.cppreference.com/w/c/error/abort_handler_s](https://zh.cppreference.com/w/c/error/abort_handler_s)

```c
void abort_handler_s( const char * restrict msg,
                      void * restrict ptr,
                      errno_t error
                    ); // (C11 起)
```

​	向 [stderr](https://zh.cppreference.com/w/c/io) 写入实现定义的消息，其中必须包含 `msg` 所指向字符串，然后调用 [abort()](https://zh.cppreference.com/w/c/program/abort) 。

​	指向此函数的指针可以传递给 [set_constraint_handler_s](https://zh.cppreference.com/w/c/error/set_constraint_handler_s) 以建立运行时制约违规处理函数。

​	同所有边界检查函数， `abort_handler_s` 仅若实现定义了 `__STDC_LIB_EXT1__` ，且用户在包含 `<stdlib.h>` 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 `1` 才保证可用。

**参数**

| msg   | -    | 指向要写到标准错误输出的消息的指针                           |
| ----- | ---- | ------------------------------------------------------------ |
| ptr   | -    | 指向实现定义的对象的指针或空指针。实现定义对象的例子，是给出检测到违规的函数名和检测到违规时的行号的对象 |
| error | -    | `errno_t` 类型的正值                                         |

**返回值**

​	无；此函数不会返回到调用方

**注意**

​	若从未调用 `set_constraint_handler_s` ，则默认处理函数是实现定义的：可以为 abort_handler_s 、 ignore_handler_s 或另外的实现定义处理函数。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <string.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
#ifdef __STDC_LIB_EXT1__
    char dst[2];
    set_constraint_handler_s(ignore_handler_s);
    int r = strcpy_s(dst, sizeof dst, "Too long!");
    printf("dst = \"%s\", r = %d\n", dst, r);
    set_constraint_handler_s(abort_handler_s);
    r = strcpy_s(dst, sizeof dst, "Too long!");
    printf("dst = \"%s\", r = %d\n", dst, r);
#endif
}
```

可能的输出：

```txt
dst = "", r = 22
abort_handler_s was called in response to a runtime-constraint violation.
 
The runtime-constraint violation was caused by the following expression in strcpy_s:
(s1max <= (s2_len=strnlen_s(s2, s1max)) ) (in string_s.c:62)
 
Note to end users: This program was terminated as a result
of a bug present in the software. Please reach out to your
software's vendor to get more help.
Aborted
```

### aligned_alloc <- (C11 起)

原址：[https://zh.cppreference.com/w/c/memory/aligned_alloc](https://zh.cppreference.com/w/c/memory/aligned_alloc)

```c
void *aligned_alloc( size_t alignment, size_t size ); // (C11 起)
```

​	分配 `size` 个字节的未初始化存储空间，按照 `alignment` 指定对齐。`size` 形参必须是 `alignment` 的整数倍。

​	`aligned_alloc` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。

​	解分配一块内存区域的先前 [free](https://zh.cppreference.com/w/c/memory/free)、 `free_sized` 及 `free_aligned_sized`(C23 起) 或 [realloc](https://zh.cppreference.com/w/c/memory/realloc) 调用*同步于*分配同一块或部分相同的内存区域的 `aligned_alloc` 调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何 `aligned_alloc` 所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。

**参数**

| alignment | -    | 指定对齐。必须是实现支持的合法对齐。 |
| --------- | ---- | ------------------------------------ |
| size      | -    | 分配的字节数。alignment 的整数倍。   |

**返回值**

​	成功时，返回指向新分配内存的指针。为避免内存泄漏，返回的指针必须用 [free()](https://zh.cppreference.com/w/c/memory/free) 或 `realloc()` 解分配。

​	失败时，返回空指针。

**注解**

​	传递不是 `alignment` 整数倍的 `size`，或传递实现不支持的 `alignment`，会令函数失败并返回空指针（出版时的 C11 指定此为未定义行为，这已经为 [DR460](https://open-std.org/JTC1/SC22/WG14/www/docs/summary.htm#dr_460) 所更正）。[N2072](https://open-std.org/JTC1/SC22/WG14/www/docs/n2072.htm) 提议移除大小限制，使之能在限制性的对齐边界分配小对象（类似 [`alignas`](https://zh.cppreference.com/w/c/language/_Alignas)）。

​	作为“实现支持”要求的例子，POSIX 函数 [`posix_memalign`](https://pubs.opengroup.org/onlinepubs/9699919799/functions/posix_memalign.html) 接受任何是二的幂且为 `sizeof(void*)` 倍数的 `alignment`，而基于 POSIX 的 `aligned_alloc` 实现继承了此项要求。

​	基础对齐始终得到支持。若 `alignment` 是二的幂且不大于 `_Alignof`([max_align_t](http://zh.cppreference.com/w/c/types/max_align_t))，则 `aligned_alloc` 可以简单地调用 [malloc](https://zh.cppreference.com/w/c/memory/malloc)。

​	常规的 [malloc](https://zh.cppreference.com/w/c/memory/malloc) 分配适用于具有任何基础对齐的对象类型的内存。`aligned_alloc` 适用于过对齐分配，例如对 [SSE](https://en.wikipedia.org/wiki/Streaming_SIMD_Extensions)、缓存线或 [VM 页](https://en.wikipedia.org/wiki/Page_(computer_memory)#Multiple_page_sizes)边界。

​	Microsoft C 运行时库不支持此函数，因为其 `std::free` 的实现[无法处理任意种类的对齐分配](https://learn.microsoft.com/en-us/cpp/standard-library/cstdlib#remarks-6)。MS CRT 提供 [`_aligned_malloc`](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/aligned-malloc) 作为替代（其结果应以 [`_aligned_free`](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/aligned-free) 释放）。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    int *p1 = malloc(10*sizeof *p1);
    printf("default-aligned addr:   %p\n", (void*)p1);
    free(p1);
 
    int *p2 = aligned_alloc(1024, 1024*sizeof *p2);
    printf("1024-byte aligned addr: %p\n", (void*)p2);
    free(p2);
}
```

可能的输出：

```txt
default-aligned addr:   0x1e40c20
1024-byte aligned addr: 0x1e41000
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

### calloc

原址：[https://zh.cppreference.com/w/c/memory/calloc](https://zh.cppreference.com/w/c/memory/calloc)

```c
void* calloc( size_t num, size_t size );
```

​	为 `num` 个 `size` 大小的对象的数组分配内存，并将分配存储中的所有字节初始化为零。

​	若分配成功，会返回指向分配内存块最低位（首位）字节的指针，它为任何具有[基础对齐](https://zh.cppreference.com/w/c/language/object#.E5.AF.B9.E9.BD.90)的对象类型适当地对齐。

​	若 `size` 为零，则行为是实现定义的（可返回空指针，或返回不可用于访问存储的非空指针）。

​	`calloc` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。解分配一块内存区域的先前 [free](https://zh.cppreference.com/w/c/memory/free)、 `free_sized` 及 `free_aligned_sized`(C23 起) 或 [realloc](https://zh.cppreference.com/w/c/memory/realloc) 调用*同步于*分配同一块或部分相同的内存区域的 `calloc` 调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何 `calloc` 所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。(C11 起)



**参数**

| num  | -    | 对象数目       |
| ---- | ---- | -------------- |
| size | -    | 每个对象的大小 |

**返回值**

​	成功时，返回指向新分配内存开头的指针。为避免内存泄漏，必须用 [free()](https://zh.cppreference.com/w/c/memory/free) 或 `realloc()` 解分配返回的指针。

​	失败时，返回空指针。

**注解**

​	因为对齐需求的缘故，分配的字节数不必等于 num * size 。

​	初始化所有位为零不保证浮点数或指针分别被初始化为 0.0 或空指针值（尽管这在所有常见平台上都为真）。

​	本来（C89中），已经为了接纳这种代码增加对零大小的支持：

```c
OBJ *p = calloc(0, sizeof(OBJ)); // “零长度”占位
...
while(1)
{ 
    p = realloc(p, c * sizeof(OBJ)); // 重分配，直至大小稳定
    ... // 可能会修改 c 或跳出循环的代码
}
```

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    int *p1 = calloc(4, sizeof(int));    // 分配并清零 4 个 int 的数组
    int *p2 = calloc(1, sizeof(int[4])); // 等价，直接命名数组类型
    int *p3 = calloc(4, sizeof *p3);     // 等价，免去重复类型名
 
    if(p2)
    {
        for(int n=0; n<4; ++n) // 打印数组
            printf("p2[%d] == %d\n", n, p2[n]);
    }
 
    free(p1);
    free(p2);
    free(p3);
}
```

输出：

```txt
p2[0] == 0
p2[1] == 0
p2[2] == 0
p2[3] == 0
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

### free

原址：[https://zh.cppreference.com/w/c/memory/free](https://zh.cppreference.com/w/c/memory/free)

```c
void free( void* ptr );
```

​	解分配之前由 [malloc()](https://zh.cppreference.com/w/c/memory/malloc)、[calloc()](https://zh.cppreference.com/w/c/memory/calloc)、`aligned_alloc()`(C11 起) 或 [realloc()](https://zh.cppreference.com/w/c/memory/realloc) 分配的空间。

​	若 `ptr` 为空指针，则函数不进行操作。

​	若 `ptr` 的值不等于之前从 [malloc()](https://zh.cppreference.com/w/c/memory/malloc)、[calloc()](https://zh.cppreference.com/w/c/memory/calloc)、[realloc()](https://zh.cppreference.com/w/c/memory/realloc) 或 aligned_alloc()(C11 起) 返回的值，则行为未定义。

​	若 `ptr` 所指代的内存区域已经被解分配，则行为未定义，即是说已经以 `ptr` 为实参调用过 `free()`、`free_sized()`、`free_aligned_sized()`(C23 起) 或 [realloc()](https://zh.cppreference.com/w/c/memory/realloc)，而且没有后继的 [malloc()](https://zh.cppreference.com/w/c/memory/malloc)、[calloc()](https://zh.cppreference.com/w/c/memory/calloc)、[realloc()](https://zh.cppreference.com/w/c/memory/realloc) 或 aligned_alloc()(C11 起) 调用以 `ptr` 为结果。

​	若在 `free()` 返回后通过指针 `ptr` 访问内存，则行为未定义（除非另一个分配函数恰好返回等于 `ptr` 的值）。

​	`free` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。解分配一块内存区域的 `free` 调用*同步于*分配同一块或部分相同的内存区域的后续任何分配函数的调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何分配函数所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。(C11 起)

**参数**

| ptr  | -    | 指向要解分配的内存的指针 |
| ---- | ---- | ------------------------ |

**返回值**

​	（无）

**注解**

​	此函数接收空指针（并对其不处理）以减少特例的数量。不管分配成功与否，分配函数返回的指针都能传递给 `free()` 。

**示例**

```c
#include <stdlib.h>
 
int main(void)
{
    int *p1 = malloc(10*sizeof *p1);
    free(p1); // 每一个分配的指针都必须释放
 
    int *p2 = calloc(10, sizeof *p2);
    int *p3 = realloc(p2, 1000*sizeof *p3);
    if(p3) // p3 非空表示 p2 已被 realloc 释放
       free(p3);
    else // p3 为空表示 p2 未被释放
       free(p2);
}
```

### free_aligned_sized <- (C23 起)

原址：[https://zh.cppreference.com/w/c/memory/free_aligned_sized](https://zh.cppreference.com/w/c/memory/free_aligned_sized)

```c
void free_aligned_sized( void* ptr, size_t alignment, size_t size ); // (C23 起)
```

​	若 ptr 为空指针或为对 aligned_alloc 的调用结果，其中 alignment 等于所请求的对齐而 size 等于所请求的分配大小，则本函数等价于 [free](http://zh.cppreference.com/w/c/memory/free)(ptr)。否则，其行为未定义。

​	[malloc](https://zh.cppreference.com/w/c/memory/malloc)、[calloc](https://zh.cppreference.com/w/c/memory/calloc) 或 [realloc](https://zh.cppreference.com/w/c/memory/realloc) 的调用结果不能传递给 `free_aligned_sized`。

​	`free_aligned_sized` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。

​	解分配一块内存区域的 `free_aligned_sized` 调用*同步于*分配同一块或部分相同的内存区域的后续任何分配函数的调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何分配函数所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。

**参数**

| ptr       | -    | 指向欲接分配内存的指针 |
| --------- | ---- | ---------------------- |
| alignment | -    | 欲解分配内存的对齐     |
| size      | -    | 欲解分配内存的大小     |

**返回值**

​	（无）

**示例**

> 本节未完成 
>
> 原因：暂无示例

### free_sized <- (C23 起)

原址：[https://zh.cppreference.com/w/c/memory/free_sized](https://zh.cppreference.com/w/c/memory/free_sized)

```c
void free_sized( void* ptr, size_t size ); // (C23 起)
```

​	解分配之前由 [malloc()](https://zh.cppreference.com/w/c/memory/malloc)、[calloc()](https://zh.cppreference.com/w/c/memory/calloc) 或 [realloc()](https://zh.cppreference.com/w/c/memory/realloc)（但非 aligned_alloc()）分配的存储空间。

> 本节未完成
>
> 原因：share wording among `free_*` family

​	`free_sized` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。

​	解分配一块内存区域的 `free_sized` 调用*同步于*分配同一块或部分相同的内存区域的后续任何分配函数的调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何分配函数所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。

**参数**

| ptr  | -    | 指向欲解分配内存的指针       |
| ---- | ---- | ---------------------------- |
| size | -    | 之前传递给分配函数的内存大小 |

**返回值**

​	（无）

**注解**

​	本节未完成

**可能的实现**

```c
void free_sized(void* ptr, size_t /*size*/)
{
    free(ptr);
}
```

**示例**

```c
#include <stddef.h>
#include <stdio.h>
#include <stdlib.h>
 
typedef struct
{
    size_t size;     // 当前的元素数
    size_t capacity; // 保留的元素数
    void** data;
} PtrVector;
 
PtrVector vector_create(size_t initial_capacity)
{
    PtrVector ret =
    {
        .capacity = initial_capacity,
        .data = (void**) malloc(initial_capacity * sizeof(void*))
    };
    return ret;
}
 
void vector_delete(PtrVector* self)
{
    free_sized(self->data, self->capacity * sizeof(void*));
}
 
void vector_push_back(PtrVector* self, void* value)
{
    if (self->size == self->capacity)
    {
        self->capacity *= 2;
        self->data = (void**) realloc(self->data, self->capacity * sizeof(void*));
    }
    self->data[self->size++] = value;
}
 
int main()
{
    int data = 42;
    float pi = 3.141592f;
    PtrVector v = vector_create(8);
    vector_push_back(&v, &data);
    vector_push_back(&v, &pi);
    printf("data[0] = %i\n", *(int*)v.data[0]);
    printf("data[1] = %f\n", *(float*)v.data[1]);
    vector_delete(&v);
}
```

输出：

```txt
data[0] = 42
data[1] = 3.141592
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

### ignore_handler_s <- (C11 起)

原址：[https://zh.cppreference.com/w/c/error/ignore_handler_s](https://zh.cppreference.com/w/c/error/ignore_handler_s)

```c
void ignore_handler_s( const char * restrict msg,
                       void * restrict ptr,
                       errno_t error
                     ); // (C11 起)
```

​	该函数只是返回到调用方，而不进行任何动作。

​	可以将指向此函数的指针传递给 [set_constraint_handler_s](https://zh.cppreference.com/w/c/error/set_constraint_handler_s) 以建立无任何动作的运行时制约违规处理函数。

​	同所有边界检查函数， `ignore_handler_s` 仅若实现定义了 `__STDC_LIB_EXT1__` ，且用户在包含 `<stdlib.h>` 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 `1` 才保证可用。



**参数**

| msg   | -    | 指向描述错误的字符串的指针                                   |
| ----- | ---- | ------------------------------------------------------------ |
| ptr   | -    | 指向实现定义的对象的指针或空指针。实现定义对象的例子有，给出检测到违规的函数的称和检测到违规时的行号的对象 |
| error | -    | 要由调用方函数返回的错误号，若它正好是返回 `errno_t` 的函数之一 |

**返回值**

​	（无）

**注意**

​	若以 `ignore_handler_s` 为运行时制约违规处理函数，则可通过检验带边界检查函数的调用结果检测违规，这对于不同函数可能不同（非零 `errno_t` ，在输出字符串的第一个字节写入了空字符，等等）。

​	若从不调用 `set_constraint_handler_s` ，则默认处理是实现定义的：它可以是 `abort_handler_s` 、 `ignore_handler_s` 或另外的实现定义处理函数。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <string.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
#ifdef __STDC_LIB_EXT1__
    char dst[2];
    set_constraint_handler_s(ignore_handler_s);
    int r = strcpy_s(dst, sizeof dst, "Too long!");
    printf("dst = \"%s\", r = %d\n", dst, r);
    set_constraint_handler_s(abort_handler_s);
    r = strcpy_s(dst, sizeof dst, "Too long!");
    printf("dst = \"%s\", r = %d\n", dst, r);
#endif
}
```

可能的输出：

```txt
dst = "", r = 22
abort_handler_s was called in response to a runtime-constraint violation.
 
The runtime-constraint violation was caused by the following expression in strcpy_s:
(s1max <= (s2_len=strnlen_s(s2, s1max)) ) (in string_s.c:62)
 
Note to end users: This program was terminated as a result
of a bug present in the software. Please reach out to your
software's vendor to get more help.
Aborted
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

### malloc

原址：[https://zh.cppreference.com/w/c/memory/malloc](https://zh.cppreference.com/w/c/memory/malloc)

```c
void* malloc( size_t size );
```

​	分配 `size` 字节的未初始化内存。

​	若分配成功，则返回为任何拥有[基础对齐](https://zh.cppreference.com/w/c/language/object#.E5.AF.B9.E9.BD.90)的对象类型对齐的指针。

​	若 `size` 为零，则 `malloc` 的行为实现是其实现（生成）时定义的。例如可返回空指针。亦可返回非空指针；但不应当[解引用](https://zh.cppreference.com/w/c/language/operator_member_access)这种指针，而且应将它传递给 [free](https://zh.cppreference.com/w/c/memory/free) 以避免内存泄漏。

​	`malloc` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。解分配一块内存区域的先前 [free](https://zh.cppreference.com/w/c/memory/free)、 `free_sized` 及 `free_aligned_sized`(C23 起) 或 [realloc](https://zh.cppreference.com/w/c/memory/realloc) 调用*同步于*分配同一块或部分相同的内存区域的 `malloc` 调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何 `malloc` 所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。(C11 起)

**参数**

| size | -    | 要分配的字节数 |
| ---- | ---- | -------------- |

**返回值**

​	成功时，返回指向新分配内存的指针。为避免内存泄漏，必须用 [free()](https://zh.cppreference.com/w/c/memory/free) 或 [realloc()](https://zh.cppreference.com/w/c/memory/realloc) 解分配返回的指针。

​	失败时，返回空指针。

**示例**

```c
#include <stdio.h>   
#include <stdlib.h> 
 
int main(void) 
{
    int *p1 = malloc(4*sizeof(int));  // 足以分配 4 个 int 的数组
    int *p2 = malloc(sizeof(int[4])); // 等价，直接命名数组类型
    int *p3 = malloc(4*sizeof *p3);   // 等价，免去重复类型名
 
    if(p1) {
        for(int n=0; n<4; ++n) // 置入数组
            p1[n] = n*n;
        for(int n=0; n<4; ++n) // 打印出来
            printf("p1[%d] == %d\n", n, p1[n]);
    }
 
    free(p1);
    free(p2);
    free(p3);
}
```

输出：

```txt
p1[0] == 0
p1[1] == 1
p1[2] == 4
p1[3] == 9
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

### realloc

原址：[https://zh.cppreference.com/w/c/memory/realloc](https://zh.cppreference.com/w/c/memory/realloc)

```c
void *realloc( void *ptr, size_t new_size );
```

​	重新分配给定的内存区域。若 `ptr` 非 NULL，则它必须是之前为 [malloc()](https://zh.cppreference.com/w/c/memory/malloc)、[calloc()](https://zh.cppreference.com/w/c/memory/calloc) 或 `realloc()` 所分配，并且仍未被 [free](https://zh.cppreference.com/w/c/memory/free) 或 `realloc` 的调用所释放。否则，结果未定义。

​	重新分配按以下二者之一执行：

a) 可能的话，扩张或收缩 ptr 所指向的现有内存区域。新旧大小中的较小者范围内的区域的内容保持不变。若扩张范围，则数组新增部分的内容是未定义的。

b) 分配一个大小为 `new_size` 字节的新内存块，并复制大小等于新旧大小中较小者的内存区域，然后释放旧内存块。

​	若无足够内存，则不释放旧内存块，并返回空指针。

​	若 ptr 为 [NULL](https://zh.cppreference.com/w/c/types/NULL)，则行为与调用 [malloc](http://zh.cppreference.com/w/c/memory/malloc)(new_size) 相同。

​	否则，

​	若 new_size 为零，则行为是实现定义的（可能返回空指针，该情况下可能或可能不释放旧内存，或可能返回某个不能用于访问存储的非空指针）。这种用法被弃用（经由 [C DR 400](https://open-std.org/JTC1/SC22/WG14/www/docs/n2396.htm#dr_400)）。(C17 起) (C23 前)

​	若 `new_size` 为零，则行为未定义。(C23 起)

​	`realloc` 是线程安全的：它表现得如同只访问通过其实参可见的内存区域，而非任何静态存储。先前令 [free](https://zh.cppreference.com/w/c/memory/free) 或 `realloc` 归还一块内存区域的调用，*同步于*任何分配函数的调用，包括分配相同或部分相同内存区域的 `realloc` 。这种同步出现于任何解分配函数所做的内存访问后，和任何 `realloc` 所做内存访问前。所有操作一块特定内存区域的分配及解分配函数拥有单独全序。(C11 起)

**参数**

| ptr      | -    | 指向需要重新分配的内存区域的指针 |
| -------- | ---- | -------------------------------- |
| new_size | -    | 数组的新大小（字节数）           |

**返回值**

​	成功时，返回指向新分配内存的指针。返回的指针必须用 [free()](https://zh.cppreference.com/w/c/memory/free) 或 `realloc()` 归还。原指针 ptr 失效，而且任何通过它的访问是未定义行为（即使重分配是就地的）。

​	失败时，返回空指针。原指针 `ptr` 保持有效，并需要通过 [free()](https://zh.cppreference.com/w/c/memory/free) 或 `realloc()` 归还。

**注解**

​	本来（C89 中），增加对零大小的支持是为了容纳这种代码：

```c
OBJ *p = calloc(0, sizeof(OBJ)); // “零长度”占位
/*...*/
while(1) { 
    p = realloc(p, c * sizeof(OBJ)); // 重分配，直至大小稳定
    /* 可能会修改 c 或跳出循环的代码 */
}
```

**示例**

```c
#include <assert.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
 
void print_storage_info(const int* next, const int* prev, int ints)
{
    if (next)
        printf("%s location: %p. Size: %d ints (%ld bytes).\n",
               (next != prev ? "New" : "Old"), (void*)next, ints, ints * sizeof(int));
    else
        printf("Allocation failed.\n");
}
 
int main(void)
{
    const int pattern[] = {1, 2, 3, 4, 5, 6, 7, 8};
    const int pattern_size = sizeof pattern / sizeof(int);
    int *next = NULL, *prev = NULL;
 
    if ((next = (int*)malloc(pattern_size * sizeof *next))) // 分配数组
    {
        memcpy(next, pattern, sizeof pattern); // 填充数组
        print_storage_info(next, prev, pattern_size);
    }
    else
        return EXIT_FAILURE;
 
    // 以如下各值作为新的存储大小，在循环中重新分配。
    const int realloc_size[] = {10, 12, 512, 32768, 65536, 32768};
 
    for (int i = 0; i != sizeof realloc_size / sizeof(int); ++i)
    {
        if ((next = (int*)realloc(prev = next, realloc_size[i] * sizeof(int))))
        {
            print_storage_info(next, prev, realloc_size[i]);
            assert(!memcmp(next, pattern, sizeof pattern));  // 持有模式内容
        }
        else // 若 realloc 失败，则需要释放原指针
        {
            free(prev);
            return EXIT_FAILURE;
        }
    }
 
    free(next); // 最后，释放存储
    return EXIT_SUCCESS;
}
```

可能的输出：

```txt
New location: 0x144c010. Size: 8 ints (32 bytes).
Old location: 0x144c010. Size: 10 ints (40 bytes).
New location: 0x144c450. Size: 12 ints (48 bytes).
Old location: 0x144c450. Size: 512 ints (2048 bytes).
Old location: 0x144c450. Size: 32768 ints (131072 bytes).
New location: 0x7f490c5bd010. Size: 65536 ints (262144 bytes).
Old location: 0x7f490c5bd010. Size: 32768 ints (131072 bytes).
```

### set_constraint_handler_s

原址：[https://zh.cppreference.com/w/c/error/set_constraint_handler_s](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)

```c
constraint_handler_t set_constraint_handler_s( constraint_handler_t handler ); // (1)	(C11 起)
```

1) 配置所有[带边界检查函数](https://zh.cppreference.com/w/c/error#.E8.BE.B9.E7.95.8C.E6.A3.80.E6.9F.A5)在发生运行时制约违规时所调用的处理函数，或恢复成默认处理函数（若 `handler` 是空指针）。
2) 指向将在运行时制约违规时调用的处理函数的指针。

​	若从不调用 `set_constraint_handler_s`，则默认处理是实现定义的：它可以是 abort_handler_s、ignore_handler_s 或另外的实现定义处理函数。

​	同所有边界检查函数， `set_constraint_handler_s, constraint_handler_t` 仅若实现定义了 `__STDC_LIB_EXT1__` ，且用户在包含 `<stdlib.h>` 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。

​	与所有带边界检查的函数一样，仅当实现定义了 `__STDC_LIB_EXT1__` 并且用户在包含 [`<stdlib.h>`](https://zh.cppreference.com/w/c/header/stdlib) 之前将 `__STDC_WANT_LIB_EXT1__` 定义为整数常量 1 时，`set_constraint_handler_s` 和 `constraint_handler_t` 才保证可用。

**参数**

| handler | -    | `constraint_handler_t` 类型的函数指针或空指针                |
| ------- | ---- | ------------------------------------------------------------ |
| msg     | -    | 指向描述错误的字符串的指针                                   |
| ptr     | -    | 指向由实现定义的对象的指针或为空指针。由实现定义的对象的例子可以给出检测到违规的函数的名字和检测到违规的行号 |
| error   | -    | 如果所调用的函数刚好是返回 `errno_t` 的函数，则是将由此函数返回的错误 |

**返回值**

​	指向先前安装的运行时制约处理函数的指针（注意：此指针决不会是空指针，因为调用 set_constraint_handler_s([NULL](http://zh.cppreference.com/w/c/types/NULL)) 会设置系统默认处理函数）。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <string.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
#ifdef __STDC_LIB_EXT1__
    char dst[2];
    set_constraint_handler_s(ignore_handler_s);
    int r = strcpy_s(dst, sizeof dst, "Too long!");
    printf("dst = \"%s\", r = %d\n", dst, r);
    set_constraint_handler_s(abort_handler_s);
    r = strcpy_s(dst, sizeof dst, "Too long!");
    printf("dst = \"%s\", r = %d\n", dst, r);
#endif
}
```

可能的输出：

```txt
dst = "", r = 22
abort_handler_s was called in response to a runtime-constraint violation.
 
The runtime-constraint violation was caused by the following expression in strcpy_s:
(s1max <= (s2_len=strnlen_s(s2, s1max)) ) (in string_s.c:62)
 
Note to end users: This program was terminated as a result
of a bug present in the software. Please reach out to your
software's vendor to get more help.
Aborted
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

**示例**

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