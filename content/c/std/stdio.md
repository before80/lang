+++
title = " <stdio.h> "
date = 2025-04-15T19:56:16+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

## 类型





### FILE

原址：[https://zh.cppreference.com/w/c/io/FILE](https://zh.cppreference.com/w/c/io/FILE)

```c
typedef /* 未指明 */ FILE;
```

​	C 标准没有规定 `FILE` 是否为一个完整的对象类型。虽然一个有效的 `FILE` 可以被复制，但是使用指向这种副本的指针作为 I/O 函数的参数是未定义的行为。换言之 `FILE` 可能在语义上是不可复制的。

​	I/O 流能用于无格式和有格式的输入及输出。另外，处理输入输出的函数也会受到本地语言环境的影响，以便按需进行宽/多字节的转换。

**流状态**

​	除了访问设备所必须的特定于系统的信息（*例如* POSIX 文件描述符）之外，每个 `FILE` 对象还直接或间接的包含以下信息：

1. (C95)字符宽度：未设置、窄或宽。
2. (C95)多字节与宽字符间转换的分析状态（一个 [mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 类型的对象）
3. 缓冲状态：无缓冲、行缓冲、全缓冲。
4. 缓冲区，可为外部的用户提供缓冲区所替换。
5. I/O 模式：输入、输出或更新（兼具输入与输出）。
6. 二进制/文本模式指示符。
7. 文件尾状态指示符。
8. 错误状态指示符。
9. 文件位置指示符，可作为 [fpos_t](https://zh.cppreference.com/w/c/io) 类型对象访问，对于宽流包含剖析状态。
10. (C11)在多个线程读、写、寻位或查询流时避免数据竞争的再入锁。

**窄/宽字符取向**

​	新打开的流无取向。首次对 fwide 或者任何 I/O 函数的调用将建立其取向：宽 I/O 函数令流为宽取向，窄 I/O 函数令流为窄取向。一旦设置，则只能以 [freopen](https://zh.cppreference.com/w/c/io/freopen) 更改其取向。不能在宽取向流上调用窄 I/O 函数，不能在窄取向流上调用宽 I/O 函数。宽 I/O 函数，如同通过以流所描述的转换状态调用 [mbrtowc](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc) 或 [wcrtomb](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb)，进行宽与多字节字符间的转换。不同于程序中合法的多字节字符串，文件中的多字节字符可能含有嵌入的空字符，且不必然以初始迁移状态开始或结束。

​	具有宽取向的流的转换状态，是在设置流取向时所安装的 C 本地语言环境所设立的。

**二进制与文本模式**

​	*文本流*是能组合成行（零或更多字符加上终止的 `'\n'` ）的有序字符序列；行能分解成零或多个字符加一个终止的 `'\n'` （“换行”）字符。最后一行是否要求终止的 `'\n'` 是实现定义的。另外，可能必须在输入与输出时添加、切换或删除字符，以符合 OS 中的表示文本（尤其是 Windows OS 上的 C 流在输出时将 `'\n'` 转换为 `'\r\n'` ，输入时将 `'\r\n'` 转换为 `'\n'` ）。

​	仅若下列条件全为真，从文本流读取的数据才保证与先前写出到该文本流者比较相等：

- 数据由打印字符和控制字符 `'\t'` 及`/`或 `'\n'` 组成（尤其是 Windows OS 上，字符 `'\0x1A'` 终止输入）。
- 无立即为空格符所前驱的 `'\n'` 字符（当这种输出随后作为输入读入时，这种空格字符可能消失）。
- 末字符是 `'\n' `。

​	*二进制流*是能通透地记录内部数据的有序字符序列。从二进制流读取的数据始终与先前写出到该流者比较相等，除了允许实现后附不确定数量的空字符到流结尾。宽二进制流不必终止于初始迁移状态。

**注解**

​	POSIX 显式要求在流的面向变成宽时，将当前安装的 C 本地环境的 `LC_CTYPE` 刻面存储于 `FILE` 对象中； POSIX 要求将此 `LC_CTYPE` 刻面用于此流上的所有将来 I/O 直至面向被更改，无关乎任何到 [setlocale](https://zh.cppreference.com/w/c/locale/setlocale) 的后继调用。

​	有意令文本的每行均由实质上人类可读的数据组成。 POSIX 实现不辨别文本与二进制流（无 `'\n' `或任何其他字符的特殊映射）。



### errno_t

原址：

```c
typedef /* 见描述 */ errno_t;
```





### fpos_t

原址：[https://zh.cppreference.com/w/c/io/fpos_t](https://zh.cppreference.com/w/c/io/fpos_t)

```c
typedef /* 由实现定义 */ fpos_t;
```



`	fpos_t` 是非数组完整对象类型，能用于存储（由 [fgetpos](https://zh.cppreference.com/w/c/io/fgetpos) ）及恢复（由 [fsetpos](https://zh.cppreference.com/w/c/io/fsetpos) ） C 流的位置与多字节解析状态（若存在）。

​	宽面向的 C 流的多字节解析状态以 [mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 对象表示，其值由 [fgetpos](https://zh.cppreference.com/w/c/io/fgetpos) 作为 `fpos_t` 对象的值的一部分存储。(C95 起)

### rsize_t

原址：

```c
typedef /* 见描述 */ rsize_t;
```





### size_t

原址：[https://zh.cppreference.com/w/c/types/size_t](https://zh.cppreference.com/w/c/types/size_t)

```c
typedef /* 由实现定义 */ size_t;

在标头 <stddef.h> 定义
在标头 <stdio.h> 定义
在标头 <stdlib.h> 定义
在标头 <string.h> 定义
在标头 <time.h> 定义
在标头 <uchar.h> 定义 (C11 起)
在标头 <wchar.h> 定义 (C95 起)
```

​	`size_t` 是 [offsetof](https://zh.cppreference.com/w/c/types/offsetof)、[`sizeof`](https://zh.cppreference.com/w/c/language/sizeof) 和 `_Alignof`(C23 前)`alignof`(C23 起) 的结果的无符号整数类型，定义取决于[数据模型](https://zh.cppreference.com/w/c/language/arithmetic_types#.E6.95.B0.E6.8D.AE.E6.A8.A1.E5.9E.8B)。

​	`size_t` 的位宽不小于 16。(C99 起)

**注解**

​	`size_t` 能存储理论上可行的任何类型（包括数组）对象的最大大小。

​	`size_t` 通常用于数组下标和循环计数。将如 unsigned int 的其他类型用作数组下标的的程序，可能譬如在 64 位系统上，当下标超过 [UINT_MAX](https://zh.cppreference.com/w/c/types/limits) 时，或若其依赖 32 位模算术时失败。

**可能的实现**

```c
typedef typeof(sizeof(0)) size_t; // C23 起合法
```

**示例**



```c
#include <stddef.h>
#include <stdint.h>
#include <stdio.h>
 
int main(void)
{
    const size_t N = 101;
    int numbers[N];
    size_t sum = 0;
    for (size_t ndx = 0; ndx < N; ++ndx)
        sum += numbers[ndx] = ndx;
    size_t size = sizeof numbers;
    printf("sum = %zu\n", sum);
    printf("size = %zu\n", size);
    printf("SIZE_MAX = %zu\n", SIZE_MAX);
}
```

可能的输出：

```txt
sum = 5050
size = 400
SIZE_MAX = 18446744073709551615
```



## 宏





### BUFSIZ

原址：

```c

```





### EOF

原址：

```c

```





### FILENAME_MAX

原址：

```c

```





### FOPEN_MAX

原址：

```c

```





### L_tmpnam

原址：

```c

```





### L_tmpnam_s

原址：

```c

```





### NULL

原址：

```c

```





### SEEK_CUR

原址：

```c

```





### SEEK_END

原址：

```c

```





### SEEK_SET

原址：

```c

```





### TMP_MAX

原址：

```c

```





### TMP_MAX_S

原址：

```c

```





### _IOFBF

原址：

```c

```





### _IOLBF

原址：

```c

```





### _IONBF

原址：

```c

```





### _PRINTF_NAN_LEN_MAX

原址：

```c

```





### __STDC_VERSION_STDIO_H__

原址：

```c

```





### stderr

原址：

```c

```





### stdin

原址：

```c

```





### stdout

原址：

```c

```





## 函数



### clearerr

原址：

```c

```





### fclose

原址：[https://zh.cppreference.com/w/c/io/fclose](https://zh.cppreference.com/w/c/io/fclose)

```c
int fclose( FILE* stream );
```

​	关闭给定的文件流。冲入任何未写入的缓冲数据到 OS 。舍弃任何未读取的缓冲数据。

​	无论操作是否成功，流都不再关联到文件，且由 [setbuf](https://zh.cppreference.com/w/c/io/setbuf) 或 [setvbuf](https://zh.cppreference.com/w/c/io/setvbuf) 分配的缓冲区若存在，则亦被解除关联，并且若使用自动分配则被解分配。

​	若在 `fclose` 返回后使用指针 stream 的值则行为未定义。

**参数**

| stream | -    | 需要关闭的文件流 |
| ------ | ---- | ---------------- |

**返回值**

​	成功时为 0，否则为 [EOF](https://zh.cppreference.com/w/c/io)。

**示例**



```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    const char* fname = "/tmp/unique_name.txt"; // 或 tmpnam(NULL);
    int is_ok = EXIT_FAILURE;
 
    FILE* fp = fopen(fname, "w+");
    if (!fp)
    {
        perror("File opening failed");
        return is_ok;
    }
    fputs("Hello, world!\n", fp);
    rewind(fp);
 
    int c; // 注意：为处理 EOF 需要 int 而非 char
    while ((c = fgetc(fp)) != EOF) // 标准 C 的 I/O 文件读取循环
       putchar(c);
 
    if (ferror(fp))
        puts("读取时发生 I/O 错误");
    else if (feof(fp))
    {
        puts("成功抵达文件末尾");
        is_ok = EXIT_SUCCESS;
    }
 
    fclose(fp);
    remove(fname);
    return is_ok;
}
```

​	可能的输出：

```txt
Hello, world!
成功抵达文件末尾
```



### feof

原址：

```c

```





### ferror

原址：

```c

```





### fflush

原址：[https://zh.cppreference.com/w/c/io/fflush](https://zh.cppreference.com/w/c/io/fflush)

```c
int fflush( FILE* stream );
```

​	对于输出流（及最后操作为输出的更新流），从 stream 的缓冲区写入未写的数据到关联的输出设备。

​	对于输入流（及最后操作为输入的更新流），行为未定义。

​	若 `stream` 是空指针，则冲入所有输出流，包括操作于库包内者，或在其他情况下程序无法直接访问者。

**参数**

| stream | -    | 要写出的文件流 |
| ------ | ---- | -------------- |

**返回值**

​	成功时返回零。否则返回 [EOF](https://zh.cppreference.com/w/c/io) 并设置文件流的错误指示器。

**注解**

​	POSIX 通过定义 `fflush` 对输入流的效果[扩展它的规定](http://pubs.opengroup.org/onlinepubs/9699919799/functions/fflush.html)，只要该流还表示一个文件或另一个可定位设备：该情况下重寻位 POSIX 文件指针以匹配 C 流指针（这有效地撤销任何读缓冲），并舍弃任何尚未回读的 [ungetc](https://zh.cppreference.com/w/c/io/ungetc) 或 [ungetwc](https://zh.cppreference.com/w/c/io/ungetwc) 的效果。

​	微软（Microsoft）也通过定义 `fflush` 对输入流的效果扩展它的规定：在 Visual Studio 2013 及以前的版本中，[放弃输入缓冲区](https://docs.microsoft.com/en-us/previous-versions/visualstudio/visual-studio-2013/9yky46tz(v=vs.120))；在 Visual Studio 2015 及以后的版本中，[无影响并保留缓冲区](https://msdn.microsoft.com/en-us/library/9yky46tz.aspx)。



### fgetc

原址：[https://zh.cppreference.com/w/c/io/fgetc](https://zh.cppreference.com/w/c/io/fgetc)

```c
int fgetc( FILE* stream ); // (1)
int getc( FILE* stream ); // (2)
```

1）从给定的输入流读取下一个字符。

2）同 `fgetc`，但若 `getc` 实现为宏，则它可能求值 stream 多于一次，所以实参始终不应为带有副作用的表达式。

**参数**

| stream | -    | 读取字符的来源 |
| ------ | ---- | -------------- |

**返回值**

​	成功时，返回作为 unsigned char 获得并转换为 int 的字符。 失败时，返回 [EOF](https://zh.cppreference.com/w/c/io)。

​	若文件尾条件导致失败，则另外设置 stream 上的*文件尾*指示器（见 [feof()](https://zh.cppreference.com/w/c/io/feof)）。若某些其他错误导致失败，则设置 stream 上的*错误*指示器（见 [ferror()](https://zh.cppreference.com/w/c/io/ferror)）。

**示例**



```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    const char* fname = "/tmp/unique_name.txt"; // 或 tmpnam(NULL);
    int is_ok = EXIT_FAILURE;
 
    FILE* fp = fopen(fname, "w+");
    if (!fp)
    {
        perror("File opening failed");
        return is_ok;
    }
    fputs("Hello, world!\n", fp);
    rewind(fp);
 
    int c; // 注意：为处理 EOF 需要 int 而非 char
    while ((c = fgetc(fp)) != EOF) // 标准 C 的 I/O 文件读取循环
       putchar(c);
 
    if (ferror(fp))
        puts("读取时发生 I/O 错误");
    else if (feof(fp))
    {
        puts("成功抵达文件末尾");
        is_ok = EXIT_SUCCESS;
    }
 
    fclose(fp);
    remove(fname);
    return is_ok;
}
```

​	可能的输出：

```txt
Hello, world!
成功抵达文件末尾
```



### fgetpos

原址：

```c

```





### fgets

原址：[https://zh.cppreference.com/w/c/io/fgets](https://zh.cppreference.com/w/c/io/fgets)

```c
char* fgets( char*          str, int count, FILE*          stream ); // (C99 前)
char* fgets( char* restrict str, int count, FILE* restrict stream ); // (C99 起)
```

​	从给定文件流读取最多 count - 1 个字符并将它们存储于 `str` 所指向的字符数组。若文件尾出现或发现换行符则终止分析，后一情况下 `str` 将包含一个换行符。若读入字节且无错误发生，则紧随写入到 `str` 的最后一个字符后写入空字符。

**参数**

| str    | -    | 指向 char 数组元素的指针                  |
| ------ | ---- | ----------------------------------------- |
| count  | -    | 写入的最大字符数（典型的为 `str` 的长度） |
| stream | -    | 读取数据来源的文件流                      |

**返回值**

​	成功时为 `str`，失败时为空指针。

​	若遇到文件尾条件导致了失败，则设置 stream 上的*文件尾*指示器（见 [feof()](https://zh.cppreference.com/w/c/io/feof)）。这仅若它导致未读取字符才是失败，该情况下返回空指针且不改变 `str` 所指向数组的内容（即不以空字符覆写首字节）。

​	若某些其他错误导致了失败，则设置 `stream` 上的*错误*指示器（见 [ferror()](https://zh.cppreference.com/w/c/io/ferror)）。`str` 所指向的数组内容是不确定的（甚至可以不是空终止）。

**注解**

​	[POSIX 额外要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fgets.html)若 fgets 发生读取错误则设置 [errno](https://zh.cppreference.com/w/c/error/errno)。

​	尽管标准规范在 `count <= 1` 的情况下[不明](https://stackoverflow.com/questions/23388620)，常见的实现

- 若 `count < 1` 则不做任何事并报告错误，
- 若 `count == 1`，则
  - 某些实现不做任何事并报告错误，
  - 其他实现不读内容，存储零于 str[0] 并报告成功



**示例**



```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    FILE* tmpf = tmpfile();
    fputs("Alan Turing\n", tmpf);
    fputs("John von Neumann\n", tmpf);
    fputs("Alonzo Church\n", tmpf);
 
    rewind(tmpf);
 
    char buf[8];
    while (fgets(buf, sizeof buf, tmpf) != NULL)
          printf("\"%s\"\n", buf);
 
    if (feof(tmpf))
       puts("抵达文件尾");
}
```

​	输出：

```txt
"Alan Tu"
"ring
"
"John vo"
"n Neuma"
"nn
"
"Alonzo "
"Church
"
抵达文件尾
```



### fopen

原址：[https://zh.cppreference.com/w/c/io/fopen](https://zh.cppreference.com/w/c/io/fopen)

```c
FILE *fopen( const char *filename, const char *mode ); // (1) (C99 前)
FILE *fopen( const char *restrict filename, const char *restrict mode ); // (1) (C99 起)
errno_t fopen_s( FILE *restrict *restrict streamptr,
                 const char *restrict filename,
                 const char *restrict mode ); // (2) 	(C11 起)
```

1) 打开 `filename` 所指示的文件，并返回指向关联到该文件的文件流的指针。 `mode` 用于确定文件访问模式。
2) 同(1)，除了指向文件流的指针被写入 `streamptr` ，还在运行时检测下列错误，并调用当前安装的[约束处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)函数：



​	同所有边界检查函数，`fopen_s`，仅若实现定义 __STDC_LIB_EXT1__ 且用户在包含 [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 前定义 __STDC_WANT_LIB_EXT1__ 为整数常量 1 才保证可用。

**参数**

| filename  | -    | 关联到文件系统的文件名                                       |
| --------- | ---- | ------------------------------------------------------------ |
| mode      | -    | 确定访问模式的空终止字符串[文件访问模式](https://zh.cppreference.com/w/c/io/fopen#.E6.96.87.E4.BB.B6.E8.AE.BF.E9.97.AE.E6.A0.87.E8.AE.B0) |
| streamptr | -    | 指向存储函数结果的指针的指针（输出参数）                     |

**文件访问标记**

| 文件访问 模式字符串 |   含义   |      解释       | 若文件已存在的动作 | 若文件不存在的动作 |
| :-----------------: | :------: | :-------------: | :----------------: | :----------------: |
|         "r"         |    读    | 打开文件以读取  |       从头读       |      打开失败      |
|         "w"         |    写    | 创建文件以写入  |      销毁内容      |     创建新文件     |
|         "a"         |   后附   |   后附到文件    |      写到结尾      |     创建新文件     |
|        "r+"         |  读扩展  | 打开文件以读/写 |       从头读       |        错误        |
|        "w+"         |  写扩展  | 创建文件以读/写 |      销毁内容      |     创建新文件     |
|        "a+"         | 后附扩展 | 打开文件以读/写 |      写到结尾      |     创建新文件     |

​	可以可选地指定文件访问模式标记 `"b"` 来以二进制模式打开文件。此标在 POSIX 上没有效果，而在 Windows 系统上，它禁用了对 `'\n' `和 `'\x1A'` 特殊处理。 在附加文件访问模式下，数据被写入到文件尾，而不考虑文件位置指示器的当前位置。

​	如果模式不是以上所列字符串之一，则其行为未定义。一些实现会定义额外支持的模式（比如 [Windows](https://docs.microsoft.com/en-us/cpp/c-runtime-library/reference/fopen-wfopen)）。

​	在更新模式（`'+'`）中，输入和输出均可进行，然而输出不应直接紧随输入，而中间无对 [fflush](https://zh.cppreference.com/w/c/io/fflush)、[fseek](https://zh.cppreference.com/w/c/io/fseek)、[fsetpos](https://zh.cppreference.com/w/c/io/fsetpos) 或 [rewind](https://zh.cppreference.com/w/c/io/rewind) 的调用，且输入不应直接紧随输出，而中间无对 [fseek](https://zh.cppreference.com/w/c/io/fseek)、[fsetpos](https://zh.cppreference.com/w/c/io/fsetpos) 或 [rewind](https://zh.cppreference.com/w/c/io/rewind) 的调用，除非输入操作遇到文件尾。在更新模式中，允许各实现在即便指定了文本模式时仍使用二进制模式。

​	文件访问模式标记 `"x"` 可以可选地后附于 `"w"` 或 `"w+"` 指定符。若文件存在，则此标记强制函数失败，而不重写它。(C11)

​	使用 `fopen_s` 或 `freopen_s` 时，任何以 `"w"` 或 `"a"` 创建的文件的文件访问许可均禁止其他用户访问它。文件访问模式标签 `"u"` 可以可选地前附于任何以 `"w"` 或 `"a"` 开始的指定符，以启用默认的 **fopen** 许可。(C11)

**返回值**

1) 若成功，则返回指向新文件流的指针。流为完全缓冲，除非 `filename` 表示一个交互设备。错误时，返回空指针。 [POSIX 要求](http://pubs.opengroup.org/onlinepubs/9699919799/functions/fopen.html)此情况下必须设置 [errno](https://zh.cppreference.com/w/c/error/errno) 。
2) 若成功，则返回零并将新文件流指针写入 `*streamptr` 。错误时，返回非零错误码并将空指针写入 `*streamptr` （除非 `streamptr` 自身也是空指针）。

**注意**

​	`filename` 的格式是实现定义的，而且不需要表示一个文件（譬如可以是控制台或另一能通过文件系统 API 访问的设备）。在支持的平台上， `filename` 可以包含绝对或相对路径。

**示例**



```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    const char* fname = "/tmp/unique_name.txt"; // 或 tmpnam(NULL);
    int is_ok = EXIT_FAILURE;
 
    FILE* fp = fopen(fname, "w+");
    if (!fp)
    {
        perror("File opening failed");
        return is_ok;
    }
    fputs("Hello, world!\n", fp);
    rewind(fp);
 
    int c; // 注意：为处理 EOF 需要 int 而非 char
    while ((c = fgetc(fp)) != EOF) // 标准 C 的 I/O 文件读取循环
       putchar(c);
 
    if (ferror(fp))
        puts("读取时发生 I/O 错误");
    else if (feof(fp))
    {
        puts("成功抵达文件末尾");
        is_ok = EXIT_SUCCESS;
    }
 
    fclose(fp);
    remove(fname);
    return is_ok;
}
```

​	可能的输出：

```txt
Hello, world!
成功抵达文件末尾
```



### fopen_s

原址：[https://zh.cppreference.com/w/c/io/fopen](https://zh.cppreference.com/w/c/io/fopen)

```c
FILE *fopen( const char *filename, const char *mode ); // (1) (C99 前)
FILE *fopen( const char *restrict filename, const char *restrict mode ); // (1) (C99 起)
errno_t fopen_s( FILE *restrict *restrict streamptr,
                 const char *restrict filename,
                 const char *restrict mode ); // (2) 	(C11 起)
```

1) 打开 `filename` 所指示的文件，并返回指向关联到该文件的文件流的指针。 `mode` 用于确定文件访问模式。
2) 同(1)，除了指向文件流的指针被写入 `streamptr` ，还在运行时检测下列错误，并调用当前安装的[约束处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)函数：



​	同所有边界检查函数，`fopen_s`，仅若实现定义 __STDC_LIB_EXT1__ 且用户在包含 [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 前定义 __STDC_WANT_LIB_EXT1__ 为整数常量 1 才保证可用。

**参数**

| filename  | -    | 关联到文件系统的文件名                                       |
| --------- | ---- | ------------------------------------------------------------ |
| mode      | -    | 确定访问模式的空终止字符串[文件访问模式](https://zh.cppreference.com/w/c/io/fopen#.E6.96.87.E4.BB.B6.E8.AE.BF.E9.97.AE.E6.A0.87.E8.AE.B0) |
| streamptr | -    | 指向存储函数结果的指针的指针（输出参数）                     |

**文件访问标记**

| 文件访问 模式字符串 |   含义   |      解释       | 若文件已存在的动作 | 若文件不存在的动作 |
| :-----------------: | :------: | :-------------: | :----------------: | :----------------: |
|         "r"         |    读    | 打开文件以读取  |       从头读       |      打开失败      |
|         "w"         |    写    | 创建文件以写入  |      销毁内容      |     创建新文件     |
|         "a"         |   后附   |   后附到文件    |      写到结尾      |     创建新文件     |
|        "r+"         |  读扩展  | 打开文件以读/写 |       从头读       |        错误        |
|        "w+"         |  写扩展  | 创建文件以读/写 |      销毁内容      |     创建新文件     |
|        "a+"         | 后附扩展 | 打开文件以读/写 |      写到结尾      |     创建新文件     |

​	可以可选地指定文件访问模式标记 `"b"` 来以二进制模式打开文件。此标在 POSIX 上没有效果，而在 Windows 系统上，它禁用了对 `'\n' `和 `'\x1A'` 特殊处理。 在附加文件访问模式下，数据被写入到文件尾，而不考虑文件位置指示器的当前位置。

​	如果模式不是以上所列字符串之一，则其行为未定义。一些实现会定义额外支持的模式（比如 [Windows](https://docs.microsoft.com/en-us/cpp/c-runtime-library/reference/fopen-wfopen)）。

​	在更新模式（`'+'`）中，输入和输出均可进行，然而输出不应直接紧随输入，而中间无对 [fflush](https://zh.cppreference.com/w/c/io/fflush)、[fseek](https://zh.cppreference.com/w/c/io/fseek)、[fsetpos](https://zh.cppreference.com/w/c/io/fsetpos) 或 [rewind](https://zh.cppreference.com/w/c/io/rewind) 的调用，且输入不应直接紧随输出，而中间无对 [fseek](https://zh.cppreference.com/w/c/io/fseek)、[fsetpos](https://zh.cppreference.com/w/c/io/fsetpos) 或 [rewind](https://zh.cppreference.com/w/c/io/rewind) 的调用，除非输入操作遇到文件尾。在更新模式中，允许各实现在即便指定了文本模式时仍使用二进制模式。

​	文件访问模式标记 `"x"` 可以可选地后附于 `"w"` 或 `"w+"` 指定符。若文件存在，则此标记强制函数失败，而不重写它。(C11)

​	使用 `fopen_s` 或 `freopen_s` 时，任何以 `"w"` 或 `"a"` 创建的文件的文件访问许可均禁止其他用户访问它。文件访问模式标签 `"u"` 可以可选地前附于任何以 `"w"` 或 `"a"` 开始的指定符，以启用默认的 **fopen** 许可。(C11)

**返回值**

1) 若成功，则返回指向新文件流的指针。流为完全缓冲，除非 `filename` 表示一个交互设备。错误时，返回空指针。 [POSIX 要求](http://pubs.opengroup.org/onlinepubs/9699919799/functions/fopen.html)此情况下必须设置 [errno](https://zh.cppreference.com/w/c/error/errno) 。
2) 若成功，则返回零并将新文件流指针写入 `*streamptr` 。错误时，返回非零错误码并将空指针写入 `*streamptr` （除非 `streamptr` 自身也是空指针）。

**注意**

​	`filename` 的格式是实现定义的，而且不需要表示一个文件（譬如可以是控制台或另一能通过文件系统 API 访问的设备）。在支持的平台上， `filename` 可以包含绝对或相对路径。

**示例**



```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    const char* fname = "/tmp/unique_name.txt"; // 或 tmpnam(NULL);
    int is_ok = EXIT_FAILURE;
 
    FILE* fp = fopen(fname, "w+");
    if (!fp)
    {
        perror("File opening failed");
        return is_ok;
    }
    fputs("Hello, world!\n", fp);
    rewind(fp);
 
    int c; // 注意：为处理 EOF 需要 int 而非 char
    while ((c = fgetc(fp)) != EOF) // 标准 C 的 I/O 文件读取循环
       putchar(c);
 
    if (ferror(fp))
        puts("读取时发生 I/O 错误");
    else if (feof(fp))
    {
        puts("成功抵达文件末尾");
        is_ok = EXIT_SUCCESS;
    }
 
    fclose(fp);
    remove(fname);
    return is_ok;
}
```

​	可能的输出：

```txt
Hello, world!
成功抵达文件末尾
```



### fprintf

原址：[https://zh.cppreference.com/w/c/io/fprintf](https://zh.cppreference.com/w/c/io/fprintf)

```c
int printf( const char*          format, ... ); // (C99 前)
int printf( const char* restrict format, ... ); // (C99 起)
(2)	
int fprintf( FILE*          stream, const char*          format, ... ); // (C99 前)
int fprintf( FILE* restrict stream, const char* restrict format, ... ); // (C99 起)
(3)	
int sprintf( char*          buffer, const char*          format, ... ); // (C99 前)
int sprintf( char* restrict buffer, const char* restrict format, ... ); // (C99 起)
int snprintf( char* restrict buffer, size_t bufsz,
              const char* restrict format, ... ); // (4)	(C99 起)
int printf_s( const char* restrict format, ... ); // (5)	(C11 起)
int fprintf_s( FILE* restrict stream, const char* restrict format, ... ); // (6)(C11 起)
int sprintf_s( char* restrict buffer, rsize_t bufsz,
               const char* restrict format, ... ); // (7)	(C11 起)
int snprintf_s( char* restrict buffer, rsize_t bufsz,
                const char* restrict format, ... ); // (8)	(C11 起)
```

参见：[printf](#printf)



### fprintf_s

原址：[https://zh.cppreference.com/w/c/io/fprintf](https://zh.cppreference.com/w/c/io/fprintf)

```c
int printf( const char*          format, ... ); // (C99 前)
int printf( const char* restrict format, ... ); // (C99 起)
(2)	
int fprintf( FILE*          stream, const char*          format, ... ); // (C99 前)
int fprintf( FILE* restrict stream, const char* restrict format, ... ); // (C99 起)
(3)	
int sprintf( char*          buffer, const char*          format, ... ); // (C99 前)
int sprintf( char* restrict buffer, const char* restrict format, ... ); // (C99 起)
int snprintf( char* restrict buffer, size_t bufsz,
              const char* restrict format, ... ); // (4)	(C99 起)
int printf_s( const char* restrict format, ... ); // (5)	(C11 起)
int fprintf_s( FILE* restrict stream, const char* restrict format, ... ); // (6)(C11 起)
int sprintf_s( char* restrict buffer, rsize_t bufsz,
               const char* restrict format, ... ); // (7)	(C11 起)
int snprintf_s( char* restrict buffer, rsize_t bufsz,
                const char* restrict format, ... ); // (8)	(C11 起)
```

参见：[printf](#printf)



### fputc

原址：

```c

```





### fputs

原址：

```c

```





### fread

原址：

```c

```





### freopen

原址：

```c

```





### freopen_s

原址：

```c

```





### fscanf

原址：[https://zh.cppreference.com/w/c/io/fscanf](https://zh.cppreference.com/w/c/io/fscanf)

```c
int scanf( const char          *format, ... ); // (C99 前)
int scanf( const char *restrict format, ... ); // (C99 起)
(2)	
int fscanf( FILE          *stream, const char          *format, ... ); // (C99 前)
int fscanf( FILE *restrict stream, const char *restrict format, ... ); // (C99 起) (3)
int sscanf( const char          *buffer, const char          *format, ... ); // (C99 前)
int sscanf( const char *restrict buffer, const char *restrict format, ... ); // (C99 起)
int scanf_s(const char *restrict format, ...); // (4)	(C11 起)
int fscanf_s(FILE *restrict stream, const char *restrict format, ...); // (5)	(C11 起)
int sscanf_s(const char *restrict buffer, const char *restrict format, ...); // (6)	(C11 起)
```

​	从各种资源读取数据，按照 `format` 转译，并将结果存储到指定位置。

1）从 [stdin](https://zh.cppreference.com/w/c/io) 读取数据

2）从文件流 `stream` 读取数据

3）从空终止字符串 `buffer` 读取数据。抵达字符串结尾等价于 `fscanf` 的抵达文件尾条件

4-6） 同 (1-3) ，除了 `%c` 、 `%s` 及 `%[` 转换指示符要求二个参数（通常的指针和指示获取用数组大小的 `rsize_t` 类型的值，在以 `%c` 读取单个字符时可以为 `1` ），并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

- 任何指针类型的参数为空指针

- `format` 、 `stream` 或 `buffer` 为空指针

- `%c` 、 `%s` 或 `%[` 会写入的字符数，加上空终止字符，要超过提供给这些转换指示符的第二个（ `rsize_t` ）参数

- 可选，任何其他可检测错误，例如未知转换指示符

  同所有边界检查函数，`scanf_s`、`fscanf_s` 与 `sscanf_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。



**参数**

| stream | -    | 要读取的输入文件流                       |
| ------ | ---- | ---------------------------------------- |
| buffer | -    | 指向要读取的空终止字符串的指针           |
| format | -    | 指向指定读取输入方式的空终止字符串的指针 |
| ...    | -    | 各接收实参                               |

​	
格式字符串由下列内容组成

- 非空白多字节字符，除了 `%`：每个格式字符串中的这种字符处理一个来自输入流的完全相同的字符，或在它与流的下个字符比较不相等时导致函数失败。
- 空白字符：任何格式字符串中的单个空白字符处理所有来自输入的可用连续空白字符（如同通过于循环中调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 确定）。注意，格式字符串中 `\n`、`" "`、`"\t\t"` 或其他空白无区别。
- 转换指示：每个转换指示拥有下列格式：











​	下列格式指示符可用：

|                    转换指示符                     |                             解释                             |         期望的实参类型         |                                  |                              |                                |                                          |                                                              |                                                        |                                                              |              |
| :-----------------------------------------------: | :----------------------------------------------------------: | :----------------------------: | :------------------------------: | :--------------------------: | :----------------------------: | :--------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------: | :----------------------------------------------------------: | ------------ |
|                    长度修饰符→                    |                              hh                              |               h                |                无                |              l               |               ll               |                    j                     |                              z                               |                           t                            |                              L                               |              |
|                 仅从 C99 起可用→                  |                              是                              |                                |                                  |                              |               是               |                    是                    |                              是                              |                           是                           |                                                              |              |
|                        `%`                        |                        匹配字面 `%`。                        |             不适用             |              不适用              |            不适用            |             不适用             |                  不适用                  |                            不适用                            |                         不适用                         |                            不适用                            | 不适用       |
|                        `c`                        | 匹配一个**字符**或**字符**的序列。如果使用了宽度指示符，那么匹配恰好*宽度*个字符（该实参必须是指向有充足空间的数组的指针）。与 `%s` 和 `%[` 不同，它不会在数组后附加空字符。 |             不适用             |              不适用              |           `char*`            |           `wchar_t*`           |                  不适用                  |                            不适用                            |                         不适用                         |                            不适用                            | 不适用       |
|                        `s`                        | 匹配非空白字符的序列（一个**字符串**）。如果使用宽度指示符，那么至多匹配*宽度*个字符，或匹配到首个提前出现的空白符前。总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                |                                  |                              |                                |                                          |                                                              |                                                        |                                                              |              |
|                   `[`*集合* ﻿`]`                   | 匹配*集合* ﻿中的字符的一个非空字符序列。如果集合的首字符是 `^`，那么匹配所有不在集合中的字符。如果集合以 `]` 或 `^]` 开始，那么 `]` 字符也会被包含入集合。在扫描集合的非最初位置的字符 `-` 是否可以指示范围，如 `[0-9]`，由实现定义。如果使用宽度指示符，那么最多匹配到*宽度*。总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                |                                  |                              |                                |                                          |                                                              |                                                        |                                                              |              |
|                        `d`                        | 匹配一个**十进制整数**。该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 10 为 base 时期望的格式相同。 | signed char* 或 unsigned char* | signed short* 或 unsigned short* | signed int* 或 unsigned int* | signed long* 或 unsigned long* | signed long long* 或 unsigned long long* | [intmax_t](http://zh.cppreference.com/w/c/types/integer)* 或 [uintmax_t](http://zh.cppreference.com/w/c/types/integer)* | [size_t](http://zh.cppreference.com/w/c/types/size_t)* | [ptrdiff_t](http://zh.cppreference.com/w/c/types/ptrdiff_t)* | 不适用       |
|                        `i`                        | 匹配一个**整数**。该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 0 为 base 时期望的格式相同。 |                                |                                  |                              |                                |                                          |                                                              |                                                        |                                                              |              |
|                        `u`                        | 匹配一个无符号**十进制整数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 10 为 base 时期望的格式相同。 |                                |                                  |                              |                                |                                          |                                                              |                                                        |                                                              |              |
|                        `o`                        | 匹配一个无符号**八进制数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 8 为 base 时期望的格式相同。 |                                |                                  |                              |                                |                                          |                                                              |                                                        |                                                              |              |
|                      `x` `X`                      | 匹配一个无符号**十六进制整数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 16 为 base 时期望的格式相同。 |                                |                                  |                              |                                |                                          |                                                              |                                                        |                                                              |              |
|                        `n`                        | 返回**迄今读取的字符数**。不消耗输出。不增加赋值计数。如果此指示符拥有赋值抑制运算符，那么行为未定义。 |                                |                                  |                              |                                |                                          |                                                              |                                                        |                                                              |              |
| `a` (C99) `A` (C99) `e` `E` `f` `F` (C99) `g` `G` | 匹配一个**浮点数**。该数的格式与 [strtof](https://zh.cppreference.com/w/c/string/byte/strtof) 期望的格式相同。 |             不适用             |              不适用              |            float*            |            double*             |                  不适用                  |                            不适用                            |                         不适用                         |                            不适用                            | long double* |
|                        `p`                        | 匹配定义了一个**指针**的由实现定义的字符序列。`printf` 系列函数使用 `%p` 格式指示符时应该产生同样的序列。 |             不适用             |              不适用              |            void**            |             不适用             |                  不适用                  |                            不适用                            |                         不适用                         |                            不适用                            | 不适用       |
|                                                   |                                                              |                                |                                  |                              |                                |                                          |                                                              |                                                        |                                                              |              |
|                                                   |                                                              |                                |                                  |                              |                                |                                          |                                                              |                                                        |                                                              |              |

**注解**

​	对于每个 n 以外的转换指示符，不超过任何指定字段宽度，且要么恰好是转换指示符所期待，要么是其所期待的前缀的最长输入字符序列，即是从流中消耗的内容。此消耗序列后的首个字符如果存在，那么保持未读取。如果被消耗序列长度为零，或被消耗序列不能转换成上面所指定的项目，那么发生匹配失败，除非遇到文件尾、编码错误，或阻止从流输入的读取错误，此情况下此为输入失败。	

​	所有异于 `[`、`c` 和 `n` 的转换指示符，在尝试分析输入前消耗并舍弃所有前导空白字符（如同以调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 来确定）。这些被消耗的字符不计入指定的最大字段宽度。	转换指示符 `lc`、`ls` 和 `l[` 进行多字节到宽字符转换，如同如同在转换首字符前，通过用初始化为零的 [mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 对象调用 [mbrtowc](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc)。	

​	转换指示符 s 与 [ 始终在匹配字符之后存储一个空字符。目标数组的大小必须至少比指定字段宽度大一。未指定目标数组大小时，对 `%s` 或 `%[` 的使用，与 [gets](https://zh.cppreference.com/w/c/io/gets) 同样不安全。	

​	[定宽整数类型](https://zh.cppreference.com/w/c/types/integer)（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确的转换指示在标头 [<inttypes.h>](https://zh.cppreference.com/w/c/types/integer) 定义（虽然 [`<CNdMA>`](https://zh.cppreference.com/w/c/types/integer)、[`<CNuMA>`](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。	在每个转换指示符后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许存储多个字段到同一“池”变量中。	

​	在分析以无数字指数为结尾的不完整浮点数，如以转换指示符 `%f` 分析 `"100er"` 时，消耗序列 `"100e"` （可能为合法浮点数的最长前缀），并导致匹配错误（被消耗序列不能转换成浮点数），而留下 `"r"`。某些既存实现不遵守此规则并回滚，通过消耗 `"100"` 而留下 `"er"`，例如 [glibc 漏洞 1765](https://sourceware.org/bugzilla/show_bug.cgi?id=1765)。	如果转换指示非法，那么行为未定义。

**返回值**

1-3) 被成功赋值的接收参数的数量（可以为零，在首个接收用参数赋值前就发生匹配失败的情况下），或者若在首个接收用参数赋值前就发生输入失败，则为 [EOF](https://zh.cppreference.com/w/c/io)。

4-6) 同 (1-3) ，除了当发生运行时制约违规时，亦返回 [EOF](https://zh.cppreference.com/w/c/io)。

**复杂度**

​	无保证。需要注意的是，有些 `sscanf` 的实现为 *O(N)*，其中 N = [strlen](http://zh.cppreference.com/w/c/string/byte/strlen)(buffer) [[1\]](https://sourceware.org/bugzilla/show_bug.cgi?id=17577)。

**注解**

​	因为多数转换指示符首先消耗掉所有连续空白符，如下的代码

```c
scanf("%d", &a);
scanf("%d", &b);
```

​	将读取在不同行上（第二个 `%d` 会消耗第一个剩下的换行符）或同一行由空格或制表符分隔（第二个 `%d` 会消耗空格或制表符）的整数。

​	不消耗前导空白符的转换指示符，如 `%c`，可以通过在格式字符串中前置一个空白符令它如此：

```c
scanf("%d", &a);
scanf(" %c", &c); // 消耗 %d 后的所有后继空白符，然后读一个 char
```

**示例**



```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <stdio.h>
#include <stddef.h>
#include <locale.h>
 
int main(void)
{
    int i, j;
    float x, y;
    char str1[10], str2[4];
    wchar_t warr[2];
    setlocale(LC_ALL, "en_US.utf8");
 
    char input[] = "25 54.32E-1 Thompson 56789 0123 56ß水";
    /* 按下列分析：
       %d ：整数
       %f ：浮点值
       %9s ：最多有 9 个非空白符的字符串
       %2d ：两位整数（数位 5 和 6）
       %f ：浮点值（数位 7、8、9）
       %*d ：不存储于任何位置的整数
       ' ' ：所有连续空白符
       %3[0-9] ：至多有 3 个十进制数字的字符串（数位 5 和 6）
       %2lc ：两个宽字符，使用多字节到宽转换  */
    int ret = sscanf(input, "%d%f%9s%2d%f%*d %3[0-9]%2lc",
                     &i, &x, str1, &j, &y, str2, warr);
 
    printf("Converted %d fields:\n"
           "i = %d\n"
           "x = %f\n"
           "str1 = %s\n"
           "j = %d\n"
           "y = %f\n"
           "str2 = %s\n"
           "warr[0] = U+%x\n"
           "warr[1] = U+%x\n",
           ret, i, x, str1, j, y, str2, warr[0], warr[1]);
 
#ifdef __STDC_LIB_EXT1__
    int n = sscanf_s(input, "%d%f%s", &i, &x, str1, (rsize_t)sizeof str1);
    // 向 i 写入 25，向 x 写入 5.432，向 str1 写入 9 个字节 "thompson\0"，并向 n 写入 3。
#endif
}
```

​	输出：

```txt
Converted 7 fields:
i = 25
x = 5.432000
str1 = Thompson
j = 56
y = 789.000000
str2 = 56
warr[0] = U+df
warr[1] = U+6c34
```



### fscanf_s

原址：[https://zh.cppreference.com/w/c/io/fscanf](https://zh.cppreference.com/w/c/io/fscanf)

```c
int scanf( const char          *format, ... ); // (C99 前)
int scanf( const char *restrict format, ... ); // (C99 起)
(2)	
int fscanf( FILE          *stream, const char          *format, ... ); // (C99 前)
int fscanf( FILE *restrict stream, const char *restrict format, ... ); // (C99 起) (3)
int sscanf( const char          *buffer, const char          *format, ... ); // (C99 前)
int sscanf( const char *restrict buffer, const char *restrict format, ... ); // (C99 起)
int scanf_s(const char *restrict format, ...); // (4)	(C11 起)
int fscanf_s(FILE *restrict stream, const char *restrict format, ...); // (5)	(C11 起)
int sscanf_s(const char *restrict buffer, const char *restrict format, ...); // (6)	(C11 起)
```

​	参见：[fscanf](#fscanf)



### fseek

原址：

```c

```





### fsetpos

原址：

```c

```





### ftell

原址：

```c

```





### fwrite

原址：

```c

```





### getc

原址：[https://zh.cppreference.com/w/c/io/fgetc](https://zh.cppreference.com/w/c/io/fgetc)

```c
int fgetc( FILE* stream ); // (1)
int getc( FILE* stream ); // (2)
```

参见：[fgetc](#fgetc)

### getchar

原址：

```c

```





### gets_s

原址：

```c

```





### perror

原址：

```c

```





### printf

原址：[https://zh.cppreference.com/w/c/io/fprintf](https://zh.cppreference.com/w/c/io/fprintf)

```c
int printf( const char*          format, ... ); // (C99 前)
int printf( const char* restrict format, ... ); // (C99 起)
(2)	
int fprintf( FILE*          stream, const char*          format, ... ); // (C99 前)
int fprintf( FILE* restrict stream, const char* restrict format, ... ); // (C99 起)
(3)	
int sprintf( char*          buffer, const char*          format, ... ); // (C99 前)
int sprintf( char* restrict buffer, const char* restrict format, ... ); // (C99 起)
int snprintf( char* restrict buffer, size_t bufsz,
              const char* restrict format, ... ); // (4)	(C99 起)
int printf_s( const char* restrict format, ... ); // (5)	(C11 起)
int fprintf_s( FILE* restrict stream, const char* restrict format, ... ); // (6)(C11 起)
int sprintf_s( char* restrict buffer, rsize_t bufsz,
               const char* restrict format, ... ); // (7)	(C11 起)
int snprintf_s( char* restrict buffer, rsize_t bufsz,
                const char* restrict format, ... ); // (8)	(C11 起)
```

​	从给定位置加载数据，转换为字符串等价物，并写结果到各种池。

1）将结果写入输出流 [stdout](https://zh.cppreference.com/w/c/io)。

2）将结果写入输出流 stream。

3）将结果写入字符串 buffer。如果所写入的字符串（加上终止空字符）超出由 buffer 所指向的数组的大小，则行为未定义。

4）将结果写入字符串 buffer。至多写 bufsz - 1 个字符。产生的字符串会以空字符终止，除非 bufsz 为零。若 bufsz 为零，则不写入任何内容，且 buffer 可以是空指针，然而依旧计算返回值（会写入的字符数，不包含空终止符）并返回。

5-8） 同 (1-4) ，除了在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

- format 中存在转换说明符 `%n`

- 任何一个对应 `%s` 的参数是空指针

- stream、format 或 buffer 是空指针

- bufsz 为零或大于 RSIZE_MAX

- 在任何一个字符串及字符转换说明符中出现编码错误

- （仅对于 `sprintf_s` ）存储于 buffer 的字符串（包括尾随空字符）长度将超出 bufsz

  同所有边界检查函数，`printf_s`、`fprintf_s`、`sprintf_s` 与 `snprintf_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。



**参数**

| stream | -    | 要写入的输出文件流                                           |
| ------ | ---- | ------------------------------------------------------------ |
| buffer | -    | 指向要写入的字符串的指针                                     |
| bufsz  | -    | 最多会写入 bufsz - 1 个字符，再加空终止符                    |
| format | -    | 指向指定数据转换方式的空终止多字节字符串的指针               |
| ...    | -    | 指定要打印数据的参数。若任何[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)后的参数不拥有对应转换说明所期待的类型（期待类型是提升后的类型或者提升后类型的兼容类型），或若参数数量少于 format 的要求，则行为未定义。若有多于 format 要求的参数，则求值并忽略多出的参数。 |

​	**格式**字符串由普通多字节字符（除了 `%`）和转换指示构成，前者被不改动地复制到输出流。每个转换指示均拥有下列格式：

- 引入的 `%` 字符。

- (可选) 一或多个修改转换行为的标志：

  - `-`：转换结果在域内左对齐（默认为右对齐）。
  - `+`：有符号转换的符号始终前置于转换结果（默认仅当结果为负时前置负号）。
  - *空格*：如果有符号转换的结果不以符号开始，或为空，那么前置空格于结果。存在 `+` 标志时忽略*空格*。
  - `#`：进行*替用形式* ﻿的转换。确切的效果见下表，其他情况下行为未定义。
  - `0`：对于整数和浮点数转换，使用前导零代替*空格* ﻿字符填充字段。对于整数，如果显式指定了精度，那么忽略此标志。对于其他转换，使用此标志导致未定义行为。存在 `-` 标志时忽略 `0`。

- (可选) 整数或 `*`，指定最小字段宽度。如果有要求，那么结果会以*空格* ﻿字符（默认情况）填充，在右对齐时于左，左对齐时于右。使用 `*` 的情况下，以一个额外的 int 类型实参指定宽度。如果实参值是负数，那么它导致指定 `-` 标志和正的字段宽度。（注意：这是最小宽度：值决不会被截断）。

- (可选) 后随整数或 `*` 或两者皆无的 `.`，指示转换的*精度* ﻿。在使用 `*` 的情况下，*精度* ﻿由额外的 int 类型的实参指定。如果此实参的值是负数，那么它被忽略。如果既不使用数字也不使用 `*`，那么精度采用零。*精度* ﻿的确切效果见下表。

- (可选) 指定实参大小的*长度修饰符*（其与格式指示符组合，指定对应实参的类型）。

- 转换格式指示符

  

​	下列格式指示符可用：

|          转换指示符          |                             解释                             | 期望的实参类型 | 期望的实参类型 | 期望的实参类型 | 期望的实参类型 | 期望的实参类型 | 期望的实参类型 | 期望的实参类型 | 期望的实参类型 | 期望的实参类型 |
| :--------------------------: | :----------------------------------------------------------: | :------------: | :------------: | :----------: | :-----------: | :----------------: | :--------------------------------------------------------: | :----------------------------------------------------: | :----------------------------------------------------------: | ----------- |
|                   |                         长度修饰符→                          |       hh       |       h        |       无       |       l        |         ll         |                             j                              |                           z                            |                              t                               | L |
|              |                       仅从 C99 起可用→                       |       是       |                |                |                |         是         |                             是                             |                           是                           | 是 |             |
|             `%`              | 写入字面的 `%`。完整的转换指示必须是 `%%`。  |     不适用     |     不适用     |    不适用    |    不适用     |       不适用       |                           不适用                           |                         不适用                         |                            不适用                            | 不适用      |
|             `c`              | 写入**单个字符**。实参首先被转换成 unsigned char。如果使用 **l** 修饰符，那么实参首先被转换成字符串，如同通过以 wchar_t[2] 实参使用 **%ls**。 |     不适用     |     不适用     |     int      |    wint_t     |       不适用       |                           不适用                           |                         不适用                         |                            不适用                            | 不适用      |
|             `s`              | 写入**字符串**。实参必须是指向字符数组首元素的指针。*精度* ﻿指定写入最大的字符数。如果没有指定*精度*，那么写每个字节直到而不含首个空终止符。如果使用 **l** 指示符，那么实参必须是指向 wchar_t 数组首元素的指针，数组会被转换成 char 数组，如同通过以零初始化转换状态调用 [wcrtomb](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb)。 |     不适用     |     不适用     |    char*     |   wchar_t*    |       不适用       |                           不适用                           |                         不适用                         |                            不适用                            | 不适用      |
|           `d` `i`            | 转换**有符号整数**为十进制表示 *[-]dddd*。*精度* ﻿指定出现的最小数位数。默认精度是 1。如果被转换的值和精度都是 0，那么转换结果无字符。对于 `z` 修饰符，期望的实参类型是 [size_t](https://zh.cppreference.com/w/c/types/size_t) 的有符号版本。 |  signed char   |     short      |     int      |     long      |     long long      | [intmax_t](https://zh.cppreference.com/w/c/types/integer)  |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) | 不适用      |
|             `o`              | 转换**无符号整数**为八进制表示 *oooo*。*精度* ﻿指定出现数字的最小个数。默认精度是 1。如果被转换值和精度都是 0，那么转换结果无字符。在*替用实现* ﻿中精度按需增加，以写入一个前导零。在此情况下如果被转换值和精度都是 0，那么写入单个 0。 | unsigned char  | unsigned short | unsigned int | unsigned long | unsigned long long | [uintmax_t](https://zh.cppreference.com/w/c/types/integer) | [size_t](https://zh.cppreference.com/w/c/types/size_t) | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) 的无符号版本 | 不适用      |
|           `x` `X`            | 转换**无符号整数**为十六进制表示 *hhhh*。`x` 转换使用字母 `abcdef`。`X` 转换使用 `ABCDEF`。*精度*指定出现数位的最小个数。默认精度是 1。如果被转换值和精度都是 0，那么转换结果无字符。在*替用实现中* ﻿如果被转换值非零，那么结果有 `0x` 或 `0X` 前缀。 |     不适用     |                |              |               |                    |                                                            |                                                        |                                                              |             |
|             `u`              | 转换**无符号整数**为十进制表示 *dddd*。*精度* ﻿指定出现的数位最小个数。默认精度是 1。如果被转换值和精度都是 0，那么转换结果无字符。 |     不适用     |                |              |               |                    |                                                            |                                                        |                                                              |             |
|        `f` `F` (C99)         | 转换**浮点数**为 *[-]ddd.ddd* 样式的十进制记法。*精度* ﻿指定小数点字符后出现的确切数位数。默认精度是 6。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用     |     不适用     |    double    | double (C99)  |       不适用       |                           不适用                           |                         不适用                         |                            不适用                            | long double |
|           `e` `E`            | 转换**浮点数**为十进制指数记法。`e` 转换样式使用 *[-]d.ddd* ﻿`e`*±dd*。`E` 转换样式使用 *[-]d.ddd* ﻿`E`*±dd*。指数至少含两个数位，仅当需要时才使用更多数位。如果值是 0，那么指数也是 0。*精度* ﻿指定小数点字符后出现数位的最小个数。默认精度是 6。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用     |     不适用     |    不适用    |    不适用     |       不适用       |                           不适用                           |                                                        |                                                              |             |
| `a` `A`​	(C99) | 转换**浮点数**为十六进制指数记法。`a` 转换样式使用 *[-]* ﻿`0x`*h.hhh* ﻿`p`*±d*。`A` 转换样式使用 *[-]* ﻿`0X`*h.hhh* ﻿`P`*±d*。如果参数是正规化的浮点数，那么首个十六进制数位非 `0`。如果值是 0，那么指数也是 0。*精度*指定小数点字符后出现数位的最小个数。默认精度足以精确表示该值。在*替用实现*中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用     |     不适用     |    不适用    |    不适用     |       不适用       |                           不适用                           |                                                        |                                                              |             |
|           `g` `G`            | 转换**浮点数**为十进制小数或十进制指数记法，依赖于值和*精度*。`g` 转换样式将进行带样式 `e` 或 `f` 的转换。`G` 转换样式将进行带样式 `E` 或 `f`(C99 前)`F`(C99 起) 的转换。令 `P` 等于精度，如果它非零，那么精度在未指定时是 6，如果精度是 0 那么等于 1。然后，如果带样式 `E` 的转换会有指数 `X`，那么：如果 *P > X ≥ −4*，那么转换带 `f` 或 `F`(C99 起) 风格，及精度 *P − 1 − X*。否则，转换带 `e` 或 `E` 风格，及精度 *P − 1*。除非要求*替用表示*，否则末尾零会被移除，且在不留下小数部分时小数点也会被移除。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用     |     不适用     |    不适用    |    不适用     |       不适用       |                           不适用                           |                                                        |                                                              |             |
|             `n`              | 返回对函数的此调用迄今为止**写入的字符数**。结果被*写入* ﻿到实参所指向的值。该指示不可含有任何*标签*、*域宽* ﻿或*精度*。对于 `z` 修饰符，实参类型是 S*，其中 `S` 是 [size_t](http://zh.cppreference.com/w/c/types/size_t) 的有符号版本。 |  signed char*  |     short*     |     int*     |     long*     |     long long*     | [intmax_t](https://zh.cppreference.com/w/c/types/integer)* |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)* | 不适用      |
|             `p`              |          写入定义了**指针**的由实现定义的字符序列。          |     不适用     |     不适用     |    void*     |    不适用     |       不适用       |                           不适用                           |                         不适用                         |                            不适用                            | 不适用      |

**注解**

​	浮点数转换函数转换无穷大为 `inf` 或 `infinity`。由实现定义使用其中哪一个。​	非数转换成 `nan` 或 `nan(char_sequence)`。由实现定义使用其中哪一个。​	转换 `F`、`E`、`G`、`A` 替代上面输出 `INF`、`INFINITY`、`NAN`。​	用于打印 char、unsigned char、signed char、short 和 unsigned short 的转换指示符实际期待[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)后的类型，但在打印前会转换到 char、unsigned char、signed char、short 和 unsigned short。直接向函数传递这些类型的值是安全的，因为在调用变参数函数时会发生提升。​	定宽字符类型（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确转换指示在标头 [`<inttypes.h>`](https://zh.cppreference.com/w/c/header/inttypes) 定义（尽管 [PRIdMAX](https://zh.cppreference.com/w/c/types/integer)、[PRIuMAX](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。​	内存写入转换指示符 `%n` 是安全漏洞的常见目标，这里格式字符串依赖用户输入，而有边界检查的 `printf_s` 系列函数不支持此转换指示符(C11 起)。​	在每个转换指示符的行动后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许于同一变量多次存入 `%n` 的结果，并在同一此调用中打印出先前以 `%n` 存储的值。​	如果转换指示非法，那么行为未定义。

**返回值**

1,2) 传输到输出流的字符数，或若出现输出错误或编码错误（对于字符串和字符转换说明符）则为负值。

3) 写入到 buffer 的字符数（不计空终止字符），或若输出错误或编码错误（对于字符串和字符转换说明符）发生则为负值。
4) 假如忽略 bufsz 则本应写入到 buffer 的字符数（不计空终止字符），或若出现输出错误或编码错误（对于字符串和字符转换说明符）则为负值。

5,6) 传输到输出流的字符数，或若出现输出错误、运行时制约违规错误或编码错误则为负值。

7) 写入到 buffer 的字符数，不计空终止字符（只要 buffer 不是空指针且 bufsz 非零且不大于 RSIZE_MAX，就写入它），在运行时制约违规时为零，而在编码错误时为负值。
8) 假如忽略 bufsz 则本应写入 buffer 的字符数的，不包含空终止字符（只要 buffer 不是空指针而 bufsz 非零且不大于 RSIZE_MAX，就写入它），或若出现输出错误、运行时制约违规错误或编码错误则为负值。

**注解**

​	C 标准及 [POSIX](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fprintf.html) 指定 `sprintf` 及其变体的行为在参数与目标缓冲区重叠时未定义。示例：

```c
sprintf(dst, "%s and %s", dst, t); // <- 有错：未定义行为
```

​	[POSIX 规定](http://pubs.opengroup.org/onlinepubs/9699919799/functions/fprintf.html)在错误时设置 [errno](https://zh.cppreference.com/w/c/error/errno)。它还规定额外的转换指示，最值得注意的是对实参重排序的支持（紧随 `%` 后的 `n$` 指示第 `n` 个实参）。

​	以零为 bufsz 和空指针为 buffer 调用 `snprintf` 可用于决定包含输出的缓冲区大小：

```c
const char fmt[] = "sqrt(2) = %f";
int sz = snprintf(NULL, 0, fmt, sqrt(2));
char buf[sz + 1]; // 注意为终止空字符 +1
snprintf(buf, sizeof buf, fmt, sqrt(2));
```

​	同 `snprintf`，但不同于 `sprintf_s`，`snprintf_s` 会将输出截断在 `bufsz - 1` 之内。

**示例**



```c
#include <inttypes.h>
#include <stdint.h>
#include <stdio.h>
 
int main(void)
{
    const char* s = "Hello";
    printf("字符串:\n"); // 同 puts("字符串");
    printf(" 填充:\n");
    printf("\t[%10s]\n", s);
    printf("\t[%-10s]\n", s);
    printf("\t[%*s]\n", 10, s);
    printf(" 截断:\n");
    printf("\t%.4s\n", s);
    printf("\t%.*s\n", 3, s);
 
    printf("字符:\t%c %%\n", 'A');
 
    printf("整数:\n");
    printf("\t十进制:\t\t%i %d %.6i %i %.0i %+i %i\n",
                         1, 2,   3, 0,   0,  4,-4);
    printf("\t十六进制:\t%x %x %X %#x\n", 5, 10, 10, 6);
    printf("\t八进制:\t\t%o %#o %#o\n", 10, 10, 4);
 
    printf("浮点:\n");
    printf("\t舍入:\t\t%f %.0f %.32f\n", 1.5, 1.5, 1.3);
    printf("\t填充:\t\t%05.2f %.2f %5.2f\n", 1.5, 1.5, 1.5);
    printf("\t科学表示:\t%E %e\n", 1.5, 1.5);
    printf("\t十六进制:\t%a %A\n", 1.5, 1.5);
    printf("\t特殊值:\t\t0/0=%g 1/0=%g\n", 0.0/0.0, 1.0/0.0);
 
    printf("定宽类型:\n");
    printf("\t最大的 32 位值是 %" PRIu32 " 或 %#" PRIx32 "\n",
                                     UINT32_MAX,     UINT32_MAX );
}
```

​	可能的输出：

```txt
字符串:
 填充:
	[     Hello]
	[Hello     ]
	[     Hello]
 截断:
	Hell
	Hel
字符:	A %
整数:
	十进制:		1 2 000003 0  +4 -4
	十六进制:	5 a A 0x6
	八进制:		12 012 04
浮点:
	舍入:		1.500000 2 1.30000000000000004440892098500626
	填充:		01.50 1.50  1.50
	科学表示:	1.500000E+00 1.500000e+00
	十六进制:	0x1.8p+0 0X1.8P+0
	特殊值:		0/0=-nan 1/0=inf
定宽类型:
	最大的 32 位值是 4294967295 或 0xffffffff
```



### printf_s

原址：[https://zh.cppreference.com/w/c/io/fprintf](https://zh.cppreference.com/w/c/io/fprintf)

```c
int printf( const char*          format, ... ); // (C99 前)
int printf( const char* restrict format, ... ); // (C99 起)
(2)	
int fprintf( FILE*          stream, const char*          format, ... ); // (C99 前)
int fprintf( FILE* restrict stream, const char* restrict format, ... ); // (C99 起)
(3)	
int sprintf( char*          buffer, const char*          format, ... ); // (C99 前)
int sprintf( char* restrict buffer, const char* restrict format, ... ); // (C99 起)
int snprintf( char* restrict buffer, size_t bufsz,
              const char* restrict format, ... ); // (4)	(C99 起)
int printf_s( const char* restrict format, ... ); // (5)	(C11 起)
int fprintf_s( FILE* restrict stream, const char* restrict format, ... ); // (6)(C11 起)
int sprintf_s( char* restrict buffer, rsize_t bufsz,
               const char* restrict format, ... ); // (7)	(C11 起)
int snprintf_s( char* restrict buffer, rsize_t bufsz,
                const char* restrict format, ... ); // (8)	(C11 起)
```

参见：[printf](#printf)



### putc

原址：

```c

```





### putchar

原址：

```c

```





### puts

原址：

```c

```





### remove

原址：[https://zh.cppreference.com/w/c/io/remove](https://zh.cppreference.com/w/c/io/remove)

```c
int remove( const char *pathname );
```

​	删除 pathname 所指向的字符串所标识的文件。

​	若当前有任何进程打开了此文件，则此函数行为是实现定义的。POSIX 系统解链接文件名（目录项），但在该文件仍被任何进程打开，以及仍存在指向该文件的硬链接时，不回收它所使用的文件系统空间。Windows 不允许在这种情况下删除该文件。

**参数**

| pathname | -    | 指向空终止字符串的指针，字符串含标识待删除文件的路径 |
| -------- | ---- | ---------------------------------------------------- |

**返回值**

​	成功时为 0，错误时为非零值。

**注解**

​	[POSIX 指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/remove.html)了此函数行为的许多额外细节。

**示例**



```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    FILE* fp = fopen("file1.txt", "w"); // 创建文件
    if (!fp)
    {
        perror("file1.txt");
        return EXIT_FAILURE;
    }
    puts("Created file1.txt");
    fclose(fp);
 
    int rc = remove("file1.txt");
    if (rc)
    {
        perror("remove");
        return EXIT_FAILURE;
    }
    puts("Removed file1.txt");
 
    fp = fopen("file1.txt", "r"); // 错误：文件不存在
    if (!fp)
        perror("Opening removed file failed");
 
    rc = remove("file1.txt"); // 错误：文件不存在
    if (rc)
        perror("Double-remove failed");
 
    return EXIT_SUCCESS;
}
```

​	可能的输出：

```txt
Created file1.txt
Removed file1.txt
Opening removed file failed: No such file or directory
Double-remove failed: No such file or directory
```



### rename

原址：[https://zh.cppreference.com/w/c/io/rename](https://zh.cppreference.com/w/c/io/rename)

```c
int rename( const char* old_filename, const char* new_filename );
```

​	更改文件的文件名。该文件以 old_filename 所指向的字符串标识。新文件名以 new_filename 所指向的字符串标识。

​	若 new_filename 存在，则行为是实现定义的。

**参数**

| old_filename | -    | 指向包含标识要重命名的文件的路径的空终止字符串的指针 |
| ------------ | ---- | ---------------------------------------------------- |
| new_filename | -    | 指向包含文件新路径的空终止字符串的指针               |

**返回值**

​	成功时为 0 ，失败时为非零值。

**注意**

​	[POSIX](https://pubs.opengroup.org/onlinepubs/9699919799/functions/rename.html) 指定许多关于此函数语义的附加细节。

**示例**



```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    FILE* fp = fopen("from.txt", "w"); // 创建文件 "from.txt"
    if (!fp)
    {
        perror("from.txt");
        return EXIT_FAILURE;
    }
    fputc('a', fp); // 写入到 "from.txt"
    fclose(fp);
 
    int rc = rename("from.txt", "to.txt");
    if (rc)
    {
        perror("rename");
        return EXIT_FAILURE;
    }
 
    fp = fopen("to.txt", "r");
    if(!fp)
    {
        perror("to.txt");
        return EXIT_FAILURE;
    }
    printf("%c\n", fgetc(fp)); // 从 "to.txt" 读取
    fclose(fp);
 
    return EXIT_SUCCESS;
}
```

​	可能的输出：

```txt
a
```



### rewind

原址：

```c

```





### scanf

原址：[https://zh.cppreference.com/w/c/io/fscanf](https://zh.cppreference.com/w/c/io/fscanf)

```c
int scanf( const char          *format, ... ); // (C99 前)
int scanf( const char *restrict format, ... ); // (C99 起)
(2)	
int fscanf( FILE          *stream, const char          *format, ... ); // (C99 前)
int fscanf( FILE *restrict stream, const char *restrict format, ... ); // (C99 起) (3)
int sscanf( const char          *buffer, const char          *format, ... ); // (C99 前)
int sscanf( const char *restrict buffer, const char *restrict format, ... ); // (C99 起)
int scanf_s(const char *restrict format, ...); // (4)	(C11 起)
int fscanf_s(FILE *restrict stream, const char *restrict format, ...); // (5)	(C11 起)
int sscanf_s(const char *restrict buffer, const char *restrict format, ...); // (6)	(C11 起)
```

​	参见：[fscanf](#fscanf)



### scanf_s

原址：[https://zh.cppreference.com/w/c/io/fscanf](https://zh.cppreference.com/w/c/io/fscanf)

```c
int scanf( const char          *format, ... ); // (C99 前)
int scanf( const char *restrict format, ... ); // (C99 起)
(2)	
int fscanf( FILE          *stream, const char          *format, ... ); // (C99 前)
int fscanf( FILE *restrict stream, const char *restrict format, ... ); // (C99 起) (3)
int sscanf( const char          *buffer, const char          *format, ... ); // (C99 前)
int sscanf( const char *restrict buffer, const char *restrict format, ... ); // (C99 起)
int scanf_s(const char *restrict format, ...); // (4)	(C11 起)
int fscanf_s(FILE *restrict stream, const char *restrict format, ...); // (5)	(C11 起)
int sscanf_s(const char *restrict buffer, const char *restrict format, ...); // (6)	(C11 起)
```

​	参见：[fscanf](#fscanf)

### setbuf

原址：[https://zh.cppreference.com/w/c/io/setbuf](https://zh.cppreference.com/w/c/io/setbuf)

```c
void setbuf( FILE          *stream, char          *buffer ); // (C99 前)
void setbuf( FILE *restrict stream, char *restrict buffer ); // (C99 起)
#define BUFSIZ     /* 未指明 */
```

​	设置用于流操作的内部缓冲区。其长度至少应该为 `BUFSIZ` 个字符。

​	若 `buffer` 非空，则等价于 [setvbuf](http://zh.cppreference.com/w/c/io/setvbuf)(stream, buffer, [_IOFBF](http://zh.cppreference.com/w/c/io), [BUFSIZ](http://zh.cppreference.com/w/c/io)) 。

​	若 `buffer` 为空，则等价于 [setvbuf](http://zh.cppreference.com/w/c/io/setvbuf)(stream, [NULL](http://zh.cppreference.com/w/c/types/NULL), [_IONBF](http://zh.cppreference.com/w/c/io), 0) ，这会关闭缓冲。

**参数**

| stream | -    | 要设置缓冲区的文件流                                     |
| ------ | ---- | -------------------------------------------------------- |
| buffer | -    | 指向文件流所用的缓冲区的指针。若提供空指针，则关闭缓冲。 |

**返回值**

​	无。

**注解**

​	若 [BUFSIZ](https://zh.cppreference.com/w/c/io) 不是适合的缓冲区大小，则能用 [setvbuf](https://zh.cppreference.com/w/c/io/setvbuf) 更改它。

​	[setvbuf](https://zh.cppreference.com/w/c/io/setvbuf) 亦应当用于检测错误，因为 `setbuf` 不指示成功或失败。

​	此函数仅可在已将 `stream` 关联到打开的文件后，但要在任何其他操作（除了对 **setbuf**/`setvbuf` 的失败调用）前使用。

​	一个常见错误是设置 stdin 或 stdout 的缓冲区为生存期在程序终止前结束的数组：

```c
int main(void) {
    char buf[BUFSIZ];
    setbuf(stdin, buf);
} // buf 的生存期结束，未定义行为
```

**示例**

​	`setbuf` 可用于禁用流上的缓冲，以要求其立即输出。



```c
#include <stdio.h>
#include <threads.h>
 
int main(void)
{
    setbuf(stdout, NULL); // 无缓冲的 stdout
    putchar('a'); // 若 stdout 无缓冲，则 'a' 立即出现
    thrd_sleep(&(struct timespec){.tv_sec=1}, NULL); // 休眠 1 秒
    putchar('b'); 
}
```

​	输出：

```txt
ab
```



### setvbuf

原址：[https://zh.cppreference.com/w/c/io/setvbuf](https://zh.cppreference.com/w/c/io/setvbuf)

```c
int setvbuf( FILE *         stream, char *         buffer,
             int mode, size_t size ); // (C99 前)
int setvbuf( FILE *restrict stream, char *restrict buffer,
             int mode, size_t size ); // (C99 起)
#define _IOFBF     /* 未指明 */
#define _IOLBF     /* 未指明 */
#define _IONBF     /* 未指明 */
```

​	以 `mode` 所指示值更改给定文件流 `stream` 的缓冲模式。另外，

- 若 `buffer` 为空指针，则重设内部缓冲区大小为 `size` 。
- 若 `buffer` 不是空指针，则指示流使用始于 `buffer` 而大小为 `size` 的用户提供缓冲区。必须在 `buffer` 所指向的数组的[生存期](https://zh.cppreference.com/w/cpp/language/lifetime)结束前（用 [fclose](https://zh.cppreference.com/w/c/io/fclose) ）关闭流。成功调用 `setvbuf` 后，数组内容不确定，而任何使用它的尝试是未定义行为。

**参数**

| stream | -    | 要设置缓冲的文件流                                           |
| ------ | ---- | ------------------------------------------------------------ |
| buffer | -    | 指向要使用的流缓冲区的指针，或若仅更改大小和模式则为空指针   |
| mode   | -    | 使用的缓冲模式。它能是下列值之一：<br />`_IOFBF`全缓冲：当缓冲区为空时，从流读入数据。或者当缓冲区满时，向流写入数据。<br />`_IOLBF`行缓冲：每次从流中读入一行数据或向流中写入一行数据。<br />`_IONBF`无缓冲：直接从流中读入数据或直接向流中写入数据，缓冲设置无效。 |
| size   | -    | 缓冲区的大小                                                 |

**返回值**

​	成功时为 `0` ，失败时为非零。

**注意**

​	此函数仅可在已将 `stream` 关联到打开的文件后，但要在任何其他操作（除了对 [setbuf](https://zh.cppreference.com/w/c/io/setbuf)/`setvbuf` 的失败调用）前使用。

​	不是所有 `size` 字节都需要用于缓冲：实际缓冲区大小通常向下取整到 2 的倍数、页面大小的倍数等。

​	多数实现上，行缓冲仅对终端输入流可用。

​	一个常见错误是设置 stdin 或 stdout 的缓冲区为生存期在程序终止前结束的数组：

```c
int main(void) {
    char buf[BUFSIZ];
    setbuf(stdin, buf);
} // buf 的生存期结束，未定义行为
```

​	期待默认缓冲区大小 [BUFSIZ](https://zh.cppreference.com/w/c/io) 为实现上文件 I/O 的最高效缓冲区大小，但 POSIX [fstat](http://pubs.opengroup.org/onlinepubs/9699919799/functions/fstat.html) 经常提供更好的估计。

**示例**

​	在已知更好的大小时更改缓冲区大小的使用样例。（这个示例使用了一些 POSIX 函数，比如 [`fileno`](https://pubs.opengroup.org/onlinepubs/7908799/xsh/fileno.html)。另见 SO帖子：[#1](https://stackoverflow.com/questions/15749184/fileno-not-available) 和[#2](https://stackoverflow.com/questions/44622827/why-am-i-getting-error-implicit-declaration-of-function-fileno-when-i-try-t)）



```
// 使得一些 POSIX 函数可见，诸如 `int fileno(FILE*)`:
#define _POSIX_SOURCE
 
#include <stdio.h>
#include <stdlib.h>
#include <sys/stat.h>
 
int main(void)
{
    FILE* fp = fopen("/tmp/test.txt", "w+");
    if (fp == NULL)
    {
        perror("fopen");
        return EXIT_FAILURE;
    }
 
    struct stat stats;
    if (fstat(fileno(fp), &stats) == -1) // 仅限 POSIX
    {
        perror("fstat");
        return EXIT_FAILURE;
    }
 
    printf("BUFSIZ is %d, but optimal block size is %ld\n", BUFSIZ, stats.st_blksize);
    if (setvbuf(fp, NULL, _IOFBF, stats.st_blksize) != 0)
    {
        perror("setvbuf failed"); // POSIX 版本设置 errno
        return EXIT_FAILURE;
    }
 
    int ch;
    while((ch=fgetc(fp)) != EOF); // read entire file: use truss/strace to
                                  // observe the read(2) syscalls used
    while((ch=fgetc(fp)) != EOF); // 读整个文件：可用 truss/strace 观察
                                  // 所使用的 read(2) 系统调用
 
    fclose(fp);
    return EXIT_SUCCESS;
}
```

​	可能的输出：

```txt
BUFSIZ is 8192, but optimal block size is 65536
```



### snprintf

原址：[https://zh.cppreference.com/w/c/io/fprintf](https://zh.cppreference.com/w/c/io/fprintf)

```c
int printf( const char*          format, ... ); // (C99 前)
int printf( const char* restrict format, ... ); // (C99 起)
(2)	
int fprintf( FILE*          stream, const char*          format, ... ); // (C99 前)
int fprintf( FILE* restrict stream, const char* restrict format, ... ); // (C99 起)
(3)	
int sprintf( char*          buffer, const char*          format, ... ); // (C99 前)
int sprintf( char* restrict buffer, const char* restrict format, ... ); // (C99 起)
int snprintf( char* restrict buffer, size_t bufsz,
              const char* restrict format, ... ); // (4)	(C99 起)
int printf_s( const char* restrict format, ... ); // (5)	(C11 起)
int fprintf_s( FILE* restrict stream, const char* restrict format, ... ); // (6)(C11 起)
int sprintf_s( char* restrict buffer, rsize_t bufsz,
               const char* restrict format, ... ); // (7)	(C11 起)
int snprintf_s( char* restrict buffer, rsize_t bufsz,
                const char* restrict format, ... ); // (8)	(C11 起)
```

参见：[printf](#printf)



### snprintf_s

原址：[https://zh.cppreference.com/w/c/io/fprintf](https://zh.cppreference.com/w/c/io/fprintf)

```c
int printf( const char*          format, ... ); // (C99 前)
int printf( const char* restrict format, ... ); // (C99 起)
(2)	
int fprintf( FILE*          stream, const char*          format, ... ); // (C99 前)
int fprintf( FILE* restrict stream, const char* restrict format, ... ); // (C99 起)
(3)	
int sprintf( char*          buffer, const char*          format, ... ); // (C99 前)
int sprintf( char* restrict buffer, const char* restrict format, ... ); // (C99 起)
int snprintf( char* restrict buffer, size_t bufsz,
              const char* restrict format, ... ); // (4)	(C99 起)
int printf_s( const char* restrict format, ... ); // (5)	(C11 起)
int fprintf_s( FILE* restrict stream, const char* restrict format, ... ); // (6)(C11 起)
int sprintf_s( char* restrict buffer, rsize_t bufsz,
               const char* restrict format, ... ); // (7)	(C11 起)
int snprintf_s( char* restrict buffer, rsize_t bufsz,
                const char* restrict format, ... ); // (8)	(C11 起)
```

参见：[printf](#printf)



### sprintf

原址：[https://zh.cppreference.com/w/c/io/fprintf](https://zh.cppreference.com/w/c/io/fprintf)

```c
int printf( const char*          format, ... ); // (C99 前)
int printf( const char* restrict format, ... ); // (C99 起)
(2)	
int fprintf( FILE*          stream, const char*          format, ... ); // (C99 前)
int fprintf( FILE* restrict stream, const char* restrict format, ... ); // (C99 起)
(3)	
int sprintf( char*          buffer, const char*          format, ... ); // (C99 前)
int sprintf( char* restrict buffer, const char* restrict format, ... ); // (C99 起)
int snprintf( char* restrict buffer, size_t bufsz,
              const char* restrict format, ... ); // (4)	(C99 起)
int printf_s( const char* restrict format, ... ); // (5)	(C11 起)
int fprintf_s( FILE* restrict stream, const char* restrict format, ... ); // (6)(C11 起)
int sprintf_s( char* restrict buffer, rsize_t bufsz,
               const char* restrict format, ... ); // (7)	(C11 起)
int snprintf_s( char* restrict buffer, rsize_t bufsz,
                const char* restrict format, ... ); // (8)	(C11 起)
```

参见：[printf](#printf)

### sprintf_s

原址：[https://zh.cppreference.com/w/c/io/fprintf](https://zh.cppreference.com/w/c/io/fprintf)

```c
int printf( const char*          format, ... ); // (C99 前)
int printf( const char* restrict format, ... ); // (C99 起)
(2)	
int fprintf( FILE*          stream, const char*          format, ... ); // (C99 前)
int fprintf( FILE* restrict stream, const char* restrict format, ... ); // (C99 起)
(3)	
int sprintf( char*          buffer, const char*          format, ... ); // (C99 前)
int sprintf( char* restrict buffer, const char* restrict format, ... ); // (C99 起)
int snprintf( char* restrict buffer, size_t bufsz,
              const char* restrict format, ... ); // (4)	(C99 起)
int printf_s( const char* restrict format, ... ); // (5)	(C11 起)
int fprintf_s( FILE* restrict stream, const char* restrict format, ... ); // (6)(C11 起)
int sprintf_s( char* restrict buffer, rsize_t bufsz,
               const char* restrict format, ... ); // (7)	(C11 起)
int snprintf_s( char* restrict buffer, rsize_t bufsz,
                const char* restrict format, ... ); // (8)	(C11 起)
```

参见：[printf](#printf)



### sscanf

原址：[https://zh.cppreference.com/w/c/io/fscanf](https://zh.cppreference.com/w/c/io/fscanf)

```c
int scanf( const char          *format, ... ); // (C99 前)
int scanf( const char *restrict format, ... ); // (C99 起)
(2)	
int fscanf( FILE          *stream, const char          *format, ... ); // (C99 前)
int fscanf( FILE *restrict stream, const char *restrict format, ... ); // (C99 起) (3)
int sscanf( const char          *buffer, const char          *format, ... ); // (C99 前)
int sscanf( const char *restrict buffer, const char *restrict format, ... ); // (C99 起)
int scanf_s(const char *restrict format, ...); // (4)	(C11 起)
int fscanf_s(FILE *restrict stream, const char *restrict format, ...); // (5)	(C11 起)
int sscanf_s(const char *restrict buffer, const char *restrict format, ...); // (6)	(C11 起)
```

​	参见：[fscanf](#fscanf)



### sscanf_s

原址：[https://zh.cppreference.com/w/c/io/fscanf](https://zh.cppreference.com/w/c/io/fscanf)

```c
int scanf( const char          *format, ... ); // (C99 前)
int scanf( const char *restrict format, ... ); // (C99 起)
(2)	
int fscanf( FILE          *stream, const char          *format, ... ); // (C99 前)
int fscanf( FILE *restrict stream, const char *restrict format, ... ); // (C99 起) (3)
int sscanf( const char          *buffer, const char          *format, ... ); // (C99 前)
int sscanf( const char *restrict buffer, const char *restrict format, ... ); // (C99 起)
int scanf_s(const char *restrict format, ...); // (4)	(C11 起)
int fscanf_s(FILE *restrict stream, const char *restrict format, ...); // (5)	(C11 起)
int sscanf_s(const char *restrict buffer, const char *restrict format, ...); // (6)	(C11 起)
```

​	参见：[fscanf](#fscanf)

### tmpfile

原址：[https://zh.cppreference.com/w/c/io/tmpfile](https://zh.cppreference.com/w/c/io/tmpfile)

```c
FILE *tmpfile( void ); // 	(1)	
errno_t tmpfile_s( FILE* restrict* restrict streamptr ); // (2)	(C11 起)
```

1）创建并打开一个临时文件。该文件作为二进制文件、更新模式（如同为 [fopen](https://zh.cppreference.com/w/c/io/fopen) 以 "wb+" 模式）打开。该文件的文件名保证在文件系统中唯一。至少可以在程序的生存期内能打开 [TMP_MAX](https://zh.cppreference.com/w/c/io) 个文件（此极限可能与 [tmpnam](https://zh.cppreference.com/w/c/io/tmpnam) 共享，并可能为 [FOPEN_MAX](https://zh.cppreference.com/w/c/io) 所进一步限制）。

2）同 (1)，但至少可以打开 TMP_MAX_S 个文件（此极限可能与 `tmpnam_s` 共享），而若 streamptr 为空指针，则调用当前安装的[制约处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)函数。

​	同所有边界检查函数，`tmpfile_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。



​	此函数创建的临时文件在程序正常退出时被关闭并删除。它在程序异常终止时是否被删除是实现定义的。

**参数**

1）（无）

2）指向此函数调用将要更新的指针的指针

**返回值**

1）指向与文件关联的文件流的指针，或若出现错误则为空指针。

2）若成功创建并打开文件则为零，若未创建或打开文件，或若 `streamptr` 为空指针则为非零。另外，成功时存储指向关联文件流的指针到 `*streamptr`，而错误时存储空指针值到 `*streamptr`。

**注解**

​	一些实现（如老版本 Linux）上，此函数确实从文件系统上创建、打开并立即删除该文件：只要被删除文件的文件开启描述符为程序所管理，该文件就会存在，但只要它被删除，其名就不会出现于任何目录中，从而再无其他进程能打开它。一旦文件描述符被关闭，或一旦程序终止（正常或异常），该文件所占有的空间将被文件系统回收。新版本的 Linux（始于 3.11 或更新版，取决于文件系统）通过 [`open()`](https://man7.org/linux/man-pages/man2/open.2.html) 系统调用的特殊标记，一步完成这种不可见临时文件的创建。

​	一些实现（如 Windows）上要求提升的权限，因为该函数可能在系统目录中创建临时文件。

**示例**



```c
#define _POSIX_C_SOURCE 200112L
#include <stdio.h>
#include <unistd.h>
 
int main(void)
{
    printf("TMP_MAX = %d, FOPEN_MAX = %d\n", TMP_MAX, FOPEN_MAX);
    FILE* tmpf = tmpfile();
    fputs("Hello, world", tmpf);
    rewind(tmpf);
    char buf[6];
    fgets(buf, sizeof buf, tmpf);
    printf("got back from the file: '%s'\n", buf);
 
    // 展示临时文件名的 Linux 特定方法
    char fname[FILENAME_MAX], link[FILENAME_MAX] = {0};
    sprintf(fname, "/proc/self/fd/%d", fileno(tmpf));
    if (readlink(fname, link, sizeof link - 1) > 0)
        printf("File name: %s\n", link);
}
```

​	可能的输出：

```txt
TMP_MAX = 238328, FOPEN_MAX = 16
got back from the file: 'Hello'
File name: /tmp/tmpfjptPe5 (deleted)
```



### tmpfile_s <- 11+

原址：[https://zh.cppreference.com/w/c/io/tmpfile](https://zh.cppreference.com/w/c/io/tmpfile)

```c
FILE *tmpfile( void ); // 	(1)	
errno_t tmpfile_s( FILE* restrict* restrict streamptr ); // (2)	(C11 起)
```

1）创建并打开一个临时文件。该文件作为二进制文件、更新模式（如同为 [fopen](https://zh.cppreference.com/w/c/io/fopen) 以 "wb+" 模式）打开。该文件的文件名保证在文件系统中唯一。至少可以在程序的生存期内能打开 [TMP_MAX](https://zh.cppreference.com/w/c/io) 个文件（此极限可能与 [tmpnam](https://zh.cppreference.com/w/c/io/tmpnam) 共享，并可能为 [FOPEN_MAX](https://zh.cppreference.com/w/c/io) 所进一步限制）。

2）同 (1)，但至少可以打开 TMP_MAX_S 个文件（此极限可能与 `tmpnam_s` 共享），而若 streamptr 为空指针，则调用当前安装的[制约处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)函数。

​	同所有边界检查函数，`tmpfile_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。



​	此函数创建的临时文件在程序正常退出时被关闭并删除。它在程序异常终止时是否被删除是实现定义的。

**参数**

1）（无）

2）指向此函数调用将要更新的指针的指针

**返回值**

1）指向与文件关联的文件流的指针，或若出现错误则为空指针。

2）若成功创建并打开文件则为零，若未创建或打开文件，或若 `streamptr` 为空指针则为非零。另外，成功时存储指向关联文件流的指针到 `*streamptr`，而错误时存储空指针值到 `*streamptr`。

**注解**

​	一些实现（如老版本 Linux）上，此函数确实从文件系统上创建、打开并立即删除该文件：只要被删除文件的文件开启描述符为程序所管理，该文件就会存在，但只要它被删除，其名就不会出现于任何目录中，从而再无其他进程能打开它。一旦文件描述符被关闭，或一旦程序终止（正常或异常），该文件所占有的空间将被文件系统回收。新版本的 Linux（始于 3.11 或更新版，取决于文件系统）通过 [`open()`](https://man7.org/linux/man-pages/man2/open.2.html) 系统调用的特殊标记，一步完成这种不可见临时文件的创建。

​	一些实现（如 Windows）上要求提升的权限，因为该函数可能在系统目录中创建临时文件。

**示例**



```c
#define _POSIX_C_SOURCE 200112L
#include <stdio.h>
#include <unistd.h>
 
int main(void)
{
    printf("TMP_MAX = %d, FOPEN_MAX = %d\n", TMP_MAX, FOPEN_MAX);
    FILE* tmpf = tmpfile();
    fputs("Hello, world", tmpf);
    rewind(tmpf);
    char buf[6];
    fgets(buf, sizeof buf, tmpf);
    printf("got back from the file: '%s'\n", buf);
 
    // 展示临时文件名的 Linux 特定方法
    char fname[FILENAME_MAX], link[FILENAME_MAX] = {0};
    sprintf(fname, "/proc/self/fd/%d", fileno(tmpf));
    if (readlink(fname, link, sizeof link - 1) > 0)
        printf("File name: %s\n", link);
}
```

​	可能的输出：

```txt
TMP_MAX = 238328, FOPEN_MAX = 16
got back from the file: 'Hello'
File name: /tmp/tmpfjptPe5 (deleted)
```



### tmpnam

原址：[https://zh.cppreference.com/w/c/io/tmpnam](https://zh.cppreference.com/w/c/io/tmpnam)

```c
char *tmpnam( char *filename ); // (1)	
errno_t tmpnam_s(char *filename_s, rsize_t maxsize); // (2)	(C11 起)
#define TMP_MAX        /* 未指明 */
#define TMP_MAX_S      /* 未指明 */  // (C11 起)
#define L_tmpnam       /* 未指明 */
#define L_tmpnam_s     /* 未指明 */ // (C11 起)

```

1) 创建独有的合法文件名（长度不长于 [L_tmpnam](https://zh.cppreference.com/w/c/io)）并将它存储于 filename 所指向的字符串。此函数足以生成至多 [TMP_MAX](https://zh.cppreference.com/w/c/io) 个独有文件名，但它们中的一部分甚至全部可能正在文件系统中使用，从而不适合作为返回值。

2) 同 (1)，但至多可以创建 `TMP_MAX_S` 个长度不长于 L_tmpnam_s 的文件名，而且在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

   - filename_s 是空指针
   - maxsize 大于 RSIZE_MAX
   - maxsize 小于生成文件名字符串的长度

   同所有边界检查函数，`tmpnam_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。



​	`tmpnam` 和 `tmpnam_s` 修改静态状态（可能会在这些函数间共享），而且不要求是线程安全的。

**参数**

| filename   | -    | 指向足以保有至少 [L_tmpnam](https://zh.cppreference.com/w/c/io) 字节的字符数组的指针，将以数组为结果缓冲区。若传递空指针，则返回指向内部静态缓冲区的指针。 |
| ---------- | ---- | ------------------------------------------------------------ |
| filename_s | -    | 指向足以保有至少 `L_tmpnam_s` 字节的字符数组的指针，将以数组为结果缓冲区。 |
| maxsize    | -    | 允许函数写入的最大字节数（典型地为 `filename_s` 数组的大小）。 |

**返回值**

1）若 filename 不是空指针则为 filename 。否则为指向内部静态缓冲区的指针。若不能生成适合的文件名，则返回空指针。

2）成功时返回零并将文件名写入 `filename_s` 。失败时，返回非零并将空字符写入 `filename_s[0]` （仅若 `filename_s` 非空且 `maxsize` 非零且不大于 `RSIZE_MAX` ）。

**注解**

​	尽管 `tmpnam` 所生成的文件名难以猜测，却可能是另一个进程在 `tmpnam` 返回的时刻和此函程序试图使用返回的名称创建文件之间创建的文件的名称。标准函数 [tmpfile](https://zh.cppreference.com/w/c/io/tmpfile) 和 POSIX 函数 [`mkstemp`](https://pubs.opengroup.org/onlinepubs/9699919799/functions/mkdtemp.html) 无此问题（仅使用 C 标准库创建一个独有的目录仍然要求使用 `tmpnam` ）。

​	POSIX 系统额外定义名称类似的函数 `tempnam` ，它提供对目录的选择（默认是可选定义的宏 `P_tmpdir` ）。

**示例**



```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
 
int main(void)
{
    // 注意，编译器/连接器可能会发出安全警告，比如 GCC：
    // "warning: the use of `tmpnam' is dangerous, better use `mkstemp'"
    char* name1 = tmpnam(NULL);
    printf("temporary file name: %s\n", name1);
 
    char name2[L_tmpnam];
    if (tmpnam(name2))
        printf("temporary file name: %s\n", name2);
 
    // POSIX 提供了 mkstemp。
    // 由于未出现于 <stdlib.h>，可能需要以下声明。
    int mkstemp(char*);
 
    char name3[] = "/tmp/fileXXXXXX"; // 需要至少六个 'X' ^_^
    int file_descriptor = mkstemp(name3);
    if (file_descriptor != -1)
        printf("temporary file name: %s\n", name3);
    else
        perror("mkstemp");
}
```

​	可能的输出：

```txt
temporary file name: /tmp/file90dLlR
temporary file name: /tmp/fileY9LWAg
temporary file name: /tmp/filexgv8PF
```



### tmpnam_s <- 11+

原址：[https://zh.cppreference.com/w/c/io/tmpnam](https://zh.cppreference.com/w/c/io/tmpnam)

```c
char *tmpnam( char *filename ); // (1)	
errno_t tmpnam_s(char *filename_s, rsize_t maxsize); // (2)	(C11 起)
#define TMP_MAX        /* 未指明 */
#define TMP_MAX_S      /* 未指明 */  // (C11 起)
#define L_tmpnam       /* 未指明 */
#define L_tmpnam_s     /* 未指明 */ // (C11 起)

```

1) 创建独有的合法文件名（长度不长于 [L_tmpnam](https://zh.cppreference.com/w/c/io)）并将它存储于 filename 所指向的字符串。此函数足以生成至多 [TMP_MAX](https://zh.cppreference.com/w/c/io) 个独有文件名，但它们中的一部分甚至全部可能正在文件系统中使用，从而不适合作为返回值。

2) 同 (1)，但至多可以创建 `TMP_MAX_S` 个长度不长于 L_tmpnam_s 的文件名，而且在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

   - filename_s 是空指针
   - maxsize 大于 RSIZE_MAX
   - maxsize 小于生成文件名字符串的长度

   同所有边界检查函数，`tmpnam_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。



​	`tmpnam` 和 `tmpnam_s` 修改静态状态（可能会在这些函数间共享），而且不要求是线程安全的。

**参数**

| filename   | -    | 指向足以保有至少 [L_tmpnam](https://zh.cppreference.com/w/c/io) 字节的字符数组的指针，将以数组为结果缓冲区。若传递空指针，则返回指向内部静态缓冲区的指针。 |
| ---------- | ---- | ------------------------------------------------------------ |
| filename_s | -    | 指向足以保有至少 `L_tmpnam_s` 字节的字符数组的指针，将以数组为结果缓冲区。 |
| maxsize    | -    | 允许函数写入的最大字节数（典型地为 `filename_s` 数组的大小）。 |

**返回值**

1）若 filename 不是空指针则为 filename 。否则为指向内部静态缓冲区的指针。若不能生成适合的文件名，则返回空指针。

2）成功时返回零并将文件名写入 `filename_s` 。失败时，返回非零并将空字符写入 `filename_s[0]` （仅若 `filename_s` 非空且 `maxsize` 非零且不大于 `RSIZE_MAX` ）。

**注解**

​	尽管 `tmpnam` 所生成的文件名难以猜测，却可能是另一个进程在 `tmpnam` 返回的时刻和此函程序试图使用返回的名称创建文件之间创建的文件的名称。标准函数 [tmpfile](https://zh.cppreference.com/w/c/io/tmpfile) 和 POSIX 函数 [`mkstemp`](https://pubs.opengroup.org/onlinepubs/9699919799/functions/mkdtemp.html) 无此问题（仅使用 C 标准库创建一个独有的目录仍然要求使用 `tmpnam` ）。

​	POSIX 系统额外定义名称类似的函数 `tempnam` ，它提供对目录的选择（默认是可选定义的宏 `P_tmpdir` ）。

**示例**



```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
 
int main(void)
{
    // 注意，编译器/连接器可能会发出安全警告，比如 GCC：
    // "warning: the use of `tmpnam' is dangerous, better use `mkstemp'"
    char* name1 = tmpnam(NULL);
    printf("temporary file name: %s\n", name1);
 
    char name2[L_tmpnam];
    if (tmpnam(name2))
        printf("temporary file name: %s\n", name2);
 
    // POSIX 提供了 mkstemp。
    // 由于未出现于 <stdlib.h>，可能需要以下声明。
    int mkstemp(char*);
 
    char name3[] = "/tmp/fileXXXXXX"; // 需要至少六个 'X' ^_^
    int file_descriptor = mkstemp(name3);
    if (file_descriptor != -1)
        printf("temporary file name: %s\n", name3);
    else
        perror("mkstemp");
}
```

​	可能的输出：

```txt
temporary file name: /tmp/file90dLlR
temporary file name: /tmp/fileY9LWAg
temporary file name: /tmp/filexgv8PF
```



### ungetc

原址：

```c

```





### vfprintf

原址：[https://zh.cppreference.com/w/c/io/vfprintf](https://zh.cppreference.com/w/c/io/vfprintf)

```c
int vprintf( const char *format, va_list vlist ); // (C99 前)
int vprintf( const char *restrict format, va_list vlist ); // (C99 起) (2)	
int vfprintf( FILE *stream, const char *format, va_list vlist ); // (C99 前)
int vfprintf( FILE *restrict stream, const char *restrict format,
              va_list vlist ); // (C99 起) (3)	
int vsprintf( char *buffer, const char *format, va_list vlist ); // (C99 前)
int vsprintf( char *restrict buffer, const char *restrict format,
              va_list vlist ); // (C99 起)
int vsnprintf( char *restrict buffer, size_t bufsz,
               const char *restrict format, va_list vlist ); // (4)	(C99 起)
int vprintf_s( const char *restrict format, va_list vlist ); // (5)	(C11 起)
int vfprintf_s( FILE *restrict stream, const char *restrict format,
                va_list vlist ); // (6)	(C11 起)
int vsprintf_s( char *restrict buffer, rsize_t bufsz,
                const char *restrict format, va_list vlist ); // (7)	(C11 起)
int vsnprintf_s( char *restrict buffer, rsize_t bufsz,
                 const char *restrict format, va_list vlist ); // (8)	(C11 起)
```

​	从 vlist 所定义的位置加载数据，将它们转换成字符串等价物，并将结果写入各种池。

1）将结果写入 [stdout](https://zh.cppreference.com/w/c/io)。

2）将结果写入文件流 stream。

3）将结果写入字符串 buffer。

4）将结果写入字符串 buffer。至多写入 bufsz - 1 个字符。产生的字符串将以空字符终止，除非 bufsz 为零。若 bufsz 为零，则不写入任何内容，且 buffer 可为空指针，然而照样计算并返回返回值（本应写入的字节数，不包含空终止符）。

5-8) 同 (1-4)，除了在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

- format 中存在转换说明符 `%n`
- 任何一个对应 `%s` 的参数是空指针
- format 或 buffer 是空指针
- bufsz 为零或大于 RSIZE_MAX
- 任何一个字符串及字符转换说明符中出现编码错误
- （仅对于 `vsprintf_s`）存储于 buffer 的字符串（包括尾随空字符）长度将超出 bufsz

​	同所有边界检查函数，`vprintf_s`、`vfprintf_s`、`vsprintf_s` 与 `vsnprintf_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。

**参数**

| stream | -    | 要写入的输出文件流                            |
| ------ | ---- | --------------------------------------------- |
| buffer | -    | 指向要写入的字符串的指针                      |
| bufsz  | -    | 至多可以写入 bufsz - 1 个字符，再加上空终止符 |
| format | -    | 指向指定数据转译方式的空终止字符串的指针      |
| vlist  | -    | 包含要打印数据的变量参数列表                  |

​	**格式**字符串由普通多字节字符（除了 `%`）和转换指示构成，前者被不改动地复制到输出流。每个转换指示均拥有下列格式：

- 引入的 `%` 字符。

- (可选) 一或多个修改转换行为的标志：

  - `-`：转换结果在域内左对齐（默认为右对齐）。
  - `+`：有符号转换的符号始终前置于转换结果（默认仅当结果为负时前置负号）。
  - *空格*：如果有符号转换的结果不以符号开始，或为空，那么前置空格于结果。存在 `+` 标志时忽略*空格*。
  - `#`：进行*替用形式* ﻿的转换。确切的效果见下表，其他情况下行为未定义。
  - `0`：对于整数和浮点数转换，使用前导零代替*空格* ﻿字符填充字段。对于整数，如果显式指定了精度，那么忽略此标志。对于其他转换，使用此标志导致未定义行为。存在 `-` 标志时忽略 `0`。

- (可选) 整数或 `*`，指定最小字段宽度。如果有要求，那么结果会以*空格* ﻿字符（默认情况）填充，在右对齐时于左，左对齐时于右。使用 `*` 的情况下，以一个额外的 int 类型实参指定宽度。如果实参值是负数，那么它导致指定 `-` 标志和正的字段宽度。（注意：这是最小宽度：值决不会被截断）。

- (可选) 后随整数或 `*` 或两者皆无的 `.`，指示转换的*精度* ﻿。在使用 `*` 的情况下，*精度* ﻿由额外的 int 类型的实参指定。如果此实参的值是负数，那么它被忽略。如果既不使用数字也不使用 `*`，那么精度采用零。*精度* ﻿的确切效果见下表。

- (可选) 指定实参大小的*长度修饰符*（其与格式指示符组合，指定对应实参的类型）。

  

下列格式指示符可用：

|     转换指示符      |                             解释                             | 期望的实参类型 | 期望的实参类型 | 期望的实参类型 | 期望的实参类型 |   期望的实参类型   |                                                            |                                                        |                                                              |             |
| :-----------------: | :----------------------------------------------------------: | :------------: | :------------: | :------------: | :------------: | :----------------: | :--------------------------------------------------------: | :----------------------------------------------------: | :----------------------------------------------------------: | ----------- |
|                     |                         长度修饰符→                          |       hh       |       h        |       无       |       l        |         ll         |                             jz                             |                           t                            |                              L                               |             |
|                     |                       仅从 C99 起可用→                       |       是       |                |                |                |         是         |                             是                             |                           是                           |                              是                              |             |
|         `%`         |         写入字面的 `%`。完整的转换指示必须是 `%%`。          |     不适用     |     不适用     |     不适用     |     不适用     |       不适用       |                           不适用                           |                         不适用                         |                            不适用                            | 不适用      |
|         `c`         | 写入**单个字符**。实参首先被转换成 unsigned char。如果使用 **l** 修饰符，那么实参首先被转换成字符串，如同通过以 wchar_t[2] 实参使用 **%ls**。 |     不适用     |     不适用     |      int       |     wint_t     |       不适用       |                           不适用                           |                         不适用                         |                            不适用                            | 不适用      |
|         `s`         | 写入**字符串**。实参必须是指向字符数组首元素的指针。*精度* ﻿指定写入最大的字符数。如果没有指定*精度*，那么写每个字节直到而不含首个空终止符。如果使用 **l** 指示符，那么实参必须是指向 wchar_t 数组首元素的指针，数组会被转换成 char 数组，如同通过以零初始化转换状态调用 [wcrtomb](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb)。 |     不适用     |     不适用     |     char*      |    wchar_t*    |       不适用       |                           不适用                           |                         不适用                         |                            不适用                            | 不适用      |
|    `d` <br />`i`    | 转换**有符号整数**为十进制表示 *[-]dddd*。*精度* ﻿指定出现的最小数位数。默认精度是 1。如果被转换的值和精度都是 0，那么转换结果无字符。对于 `z` 修饰符，期望的实参类型是 [size_t](https://zh.cppreference.com/w/c/types/size_t) 的有符号版本。 |  signed char   |     short      |      int       |      long      |     long long      | [intmax_t](https://zh.cppreference.com/w/c/types/integer)  |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) | 不适用      |
|         `o`         | 转换**无符号整数**为八进制表示 *oooo*。*精度* ﻿指定出现数字的最小个数。默认精度是 1。如果被转换值和精度都是 0，那么转换结果无字符。在*替用实现* ﻿中精度按需增加，以写入一个前导零。在此情况下如果被转换值和精度都是 0，那么写入单个 0。 | unsigned char  | unsigned short |  unsigned int  | unsigned long  | unsigned long long | [uintmax_t](https://zh.cppreference.com/w/c/types/integer) | [size_t](https://zh.cppreference.com/w/c/types/size_t) | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) 的无符号版本 | 不适用      |
|    `x` <br />`X`    | 转换**无符号整数**为十六进制表示 *hhhh*。`x` 转换使用字母 `abcdef`。`X` 转换使用 `ABCDEF`。*精度*指定出现数位的最小个数。默认精度是 1。如果被转换值和精度都是 0，那么转换结果无字符。在*替用实现中* ﻿如果被转换值非零，那么结果有 `0x` 或 `0X` 前缀。 |     不适用     |                |                |                |                    |                                                            |                                                        |                                                              |             |
|         `u`         | 转换**无符号整数**为十进制表示 *dddd*。*精度* ﻿指定出现的数位最小个数。默认精度是 1。如果被转换值和精度都是 0，那么转换结果无字符。 |     不适用     |                |                |                |                    |                                                            |                                                        |                                                              |             |
| `f`<br /> `F` (C99) | 转换**浮点数**为 *[-]ddd.ddd* 样式的十进制记法。*精度* ﻿指定小数点字符后出现的确切数位数。默认精度是 6。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用     |     不适用     |     double     |  double (C99)  |       不适用       |                           不适用                           |                         不适用                         |                            不适用                            | long double |
|    `e` <br />`E`    | 转换**浮点数**为十进制指数记法。`e` 转换样式使用 *[-]d.ddd* ﻿`e`*±dd*。`E` 转换样式使用 *[-]d.ddd* ﻿`E`*±dd*。指数至少含两个数位，仅当需要时才使用更多数位。如果值是 0，那么指数也是 0。*精度* ﻿指定小数点字符后出现数位的最小个数。默认精度是 6。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用     |     不适用     |     不适用     |     不适用     |       不适用       |                           不适用                           |                                                        |                                                              |             |
| `a` <br />`A`(C99)  | 转换**浮点数**为十六进制指数记法。`a` 转换样式使用 *[-]* ﻿`0x`*h.hhh* ﻿`p`*±d*。`A` 转换样式使用 *[-]* ﻿`0X`*h.hhh* ﻿`P`*±d*。如果参数是正规化的浮点数，那么首个十六进制数位非 `0`。如果值是 0，那么指数也是 0。*精度*指定小数点字符后出现数位的最小个数。默认精度足以精确表示该值。在*替用实现*中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用     |     不适用     |     不适用     |     不适用     |       不适用       |                           不适用                           |                                                        |                                                              |             |
|    `g` <br />`G`    | 转换**浮点数**为十进制小数或十进制指数记法，依赖于值和*精度*。`g` 转换样式将进行带样式 `e` 或 `f` 的转换。`G` 转换样式将进行带样式 `E` 或 `f`(C99 前)`F`(C99 起) 的转换。令 `P` 等于精度，如果它非零，那么精度在未指定时是 6，如果精度是 0 那么等于 1。然后，如果带样式 `E` 的转换会有指数 `X`，那么：如果 *P > X ≥ −4*，那么转换带 `f` 或 `F`(C99 起) 风格，及精度 *P − 1 − X*。否则，转换带 `e` 或 `E` 风格，及精度 *P − 1*。除非要求*替用表示*，否则末尾零会被移除，且在不留下小数部分时小数点也会被移除。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用     |     不适用     |     不适用     |     不适用     |       不适用       |                           不适用                           |                                                        |                                                              |             |
|         `n`         | 返回对函数的此调用迄今为止**写入的字符数**。结果被*写入* ﻿到实参所指向的值。该指示不可含有任何*标签*、*域宽* ﻿或*精度*。对于 `z` 修饰符，实参类型是 `S*`，其中 `S` 是 [size_t](http://zh.cppreference.com/w/c/types/size_t) 的有符号版本。 |  signed char*  |     short*     |      int*      |     long*      |     long long*     | [intmax_t](https://zh.cppreference.com/w/c/types/integer)* |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)* | 不适用      |
|         `p`         |          写入定义了**指针**的由实现定义的字符序列。          |     不适用     |     不适用     |     void*      |     不适用     |       不适用       |                           不适用                           |                         不适用                         |                            不适用                            | 不适用      |
|                     |                                                              |                |                |                |                |                    |                                                            |                                                        |                                                              |             |
|                     |                                                              |                |                |                |                |                    |                                                            |                                                        |                                                              |             |

**注解**

​	浮点数转换函数转换无穷大为 `inf` 或 `infinity`。由实现定义使用其中哪一个。非数转换成 `nan` 或 `nan(char_sequence)`。由实现定义使用其中哪一个。

​	转换 `F`、`E`、`G`、`A` 替代上面输出 `INF`、`INFINITY`、`NAN`。用于打印 char、unsigned char、signed char、short 和 unsigned short 的转换指示符实际期待[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)后的类型，但在打印前会转换到 char、unsigned char、signed char、short 和 unsigned short。直接向函数传递这些类型的值是安全的，因为在调用变参数函数时会发生提升。

​	定宽字符类型（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确转换指示在标头 [`<inttypes.h>`](https://zh.cppreference.com/w/c/header/inttypes) 定义（尽管 [PRIdMAX](https://zh.cppreference.com/w/c/types/integer)、[PRIuMAX](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。

​	内存写入转换指示符 `%n` 是安全漏洞的常见目标，这里格式字符串依赖用户输入，而有边界检查的 `printf_s` 系列函数不支持此转换指示符(C11 起)。

​	在每个转换指示符的行动后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许于同一变量多次存入 `%n` 的结果，并在同一此调用中打印出先前以 `%n` 存储的值。如果转换指示非法，那么行为未定义。



**返回值**

1-3） 若成功则为写入的字符数，若出现错误则为负值。

4）若成功则为写入的字符数，若出现错误则为负值。若产生的字符串因 bufsz 限制被截断，函数返回假如未强加限制则本应写入的字符数（不包含空终止字节）。

5,6) 传输到输出流的字符数，或若输出错误、运行时制约违规错误、编码错误发生则为负值。

7）写入 buffer 的字符数，不计空字符（只要 buffer 不是空指针且 bufsz 非零且不大于 RSIZE_MAX，就会写入它），运行时制约违规时为零，编码错误发生时为负值。

8）不含空终止字符的（只要 buffer 不是空指针且 bufsz 非零且不大于 RSIZE_MAX，就会写入它）假如忽略 bufsz 则本应写入 buffer 的字符数，或若出现运行时制约违规或编码错误为负值。

**注解**

​	所有这些函数调用 va_arg 至少一次，返回后 vlist 的值不确定。这些函数不调用 va_end，而这必须由调用方进行。

​	不同于 `vsprintf_s`，`vsnprintf_s` 将截断结果以适应 buffer 所指向的数组。

​	[Microsoft CRT](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l) 中的 `vsnprintf_s` 实现不符合 C 标准。微软的版本有一个额外的第三形参 [size_t](http://zh.cppreference.com/w/c/types/size_t) count，它包含所要写入的不包括空终止符的最大字符数量。这个形参可能与通过形参 [size_t](http://zh.cppreference.com/w/c/types/size_t) bufsz 提供的缓冲区大小有所区别。

**示例**



```c
#include <stdarg.h>
#include <stdio.h>
#include <time.h>
 
void debug_log(const char* fmt, ...)
{
    struct timespec ts;
    timespec_get(&ts, TIME_UTC);
    char time_buf[100];
    size_t rc = strftime(time_buf, sizeof time_buf, "%D %T", gmtime(&ts.tv_sec));
    snprintf(time_buf + rc, sizeof time_buf - rc, ".%06ld UTC", ts.tv_nsec / 1000);
 
    va_list args1;
    va_start(args1, fmt);
    va_list args2;
    va_copy(args2, args1);
    char buf[1+vsnprintf(NULL, 0, fmt, args1)];
    va_end(args1);
    vsnprintf(buf, sizeof buf, fmt, args2);
    va_end(args2);
 
    printf("%s [debug]: %s\n", time_buf, buf);
}
 
int main(void)
{
    debug_log("Logging, %d, %d, %d", 1, 2, 3);
}
```

可能的输出：

```txt
02/20/15 21:58:09.072683 UTC [debug]: Logging, 1, 2, 3
```



### vfprintf_s

原址：[https://zh.cppreference.com/w/c/io/vfprintf](https://zh.cppreference.com/w/c/io/vfprintf)

```c
int vprintf( const char *format, va_list vlist ); // (C99 前)
int vprintf( const char *restrict format, va_list vlist ); // (C99 起) (2)	
int vfprintf( FILE *stream, const char *format, va_list vlist ); // (C99 前)
int vfprintf( FILE *restrict stream, const char *restrict format,
              va_list vlist ); // (C99 起) (3)	
int vsprintf( char *buffer, const char *format, va_list vlist ); // (C99 前)
int vsprintf( char *restrict buffer, const char *restrict format,
              va_list vlist ); // (C99 起)
int vsnprintf( char *restrict buffer, size_t bufsz,
               const char *restrict format, va_list vlist ); // (4)	(C99 起)
int vprintf_s( const char *restrict format, va_list vlist ); // (5)	(C11 起)
int vfprintf_s( FILE *restrict stream, const char *restrict format,
                va_list vlist ); // (6)	(C11 起)
int vsprintf_s( char *restrict buffer, rsize_t bufsz,
                const char *restrict format, va_list vlist ); // (7)	(C11 起)
int vsnprintf_s( char *restrict buffer, rsize_t bufsz,
                 const char *restrict format, va_list vlist ); // (8)	(C11 起)
```

参见：[vfpfintf](#vfpfintf)



### vfscanf

原址：[https://zh.cppreference.com/w/c/io/vfscanf](https://zh.cppreference.com/w/c/io/vfscanf)

```c
int vscanf( const char *restrict format, va_list vlist ); // (1)	(C99 起)
int vfscanf( FILE *restrict stream, const char *restrict format,
             va_list vlist ); // (2)	(C99 起)
int vsscanf( const char *restrict buffer, const char *restrict format,
             va_list vlist ); // (3)	(C99 起)
int vscanf_s(const char *restrict format, va_list vlist); // (4)	(C11 起)
int vfscanf_s( FILE *restrict stream, const char *restrict format,
               va_list vlist); // (5)	(C11 起)
int vsscanf_s( const char *restrict buffer, const char *restrict format,
               va_list vlist); // (6)	(C11 起)
```

​	从各种源读取数据，按照 `format` 转换并存储结果到 `vlist` 所定义的位置。

1）从 [stdin](https://zh.cppreference.com/w/c/io) 读取数据。

2）从文件流 `stream` 读取数据。

3）从空终止字符串 `buffer` 读取数据。抵达字符串结尾等价于 `vfscanf` 的抵达文件尾条件

4-6) 同 (1-3)，但 %c、%s 及 %[ 转换指示符要求两个参数（通常的指针和指示获取用数组大小的 rsize_t 类型值，以 %c 读取单个字符时可以为 1），并且在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

- 任何指针类型参数为空指针
- `format`、`stream` 或 `buffer` 为空指针
-  %c 、 %s 或 %[ 本会写入的字符数，加上空终止字符，要超过提供给这些转换指示符的第二个（rsize_t）参数
- 可选，任何其他可检测错误，例如未知转换指示符

​	同所有边界检查函数，`vscanf_s`、`vfscanf_s` 与 `vsscanf_s`，仅若实现定义 __STDC_LIB_EXT1__ 且用户在包含 [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 前定义 __STDC_WANT_LIB_EXT1__ 为整数常量 1 才保证可用。



**参数**

| stream | -    | 要读取的输入文件流                       |
| ------ | ---- | ---------------------------------------- |
| buffer | -    | 指向要读取的空终止字符串的指针           |
| format | -    | 指向指定读取输入方式的空终止字符串的指针 |
| vlist  | -    | 包含接收各实参的可变实参列表             |

​	
格式字符串由下列内容组成

- 非空白多字节字符，除了 `%`：每个格式字符串中的这种字符处理一个来自输入流的完全相同的字符，或在它与流的下个字符比较不相等时导致函数失败。
- 空白字符：任何格式字符串中的单个空白字符处理所有来自输入的可用连续空白字符（如同通过于循环中调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 确定）。注意，格式字符串中 `"\n"`、`" "`、`"\t\t"` 或其他空白无区别。
- 转换指示：每个转换指示拥有下列格式：
  - 引入用 % 字符
  - (可选) 赋值抑制字符 *。如果存在此选项，那么此函数不将结果赋值给任何接收用实参。
  - (可选) 指定*最大字段宽度* ﻿的整数数字（大于零），即函数进行在当前转换指示所指定的转换时，允许处理的最大字符数。注意如果没有提供宽度，那么 %s 和 %[ 可能导致缓冲区溢出。
  - (可选) 指定接收实参大小的*长度修饰符*，即实际目标类型。这影响转换准确性和溢出规则。默认目标类型对每个转换类型有所不同（见下表）。
  - 转换格式指示符。


​	下列格式指示符可用：

|                          转换指示符                          |                             解释                             |           期望的实参类型           |            期望的实参类型            |          期望的实参类型          |           期望的实参类型           |                期望的实参类型                |                        期望的实参类型                        |                     期望的实参类型                     |                        期望的实参类型                        | 期望的实参类型 |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :--------------------------------: | :----------------------------------: | :------------------------------: | :--------------------------------: | :------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------: | :----------------------------------------------------------: | -------------- |
|                                                              |                         长度修饰符→                          |                 hh                 |                  h                   |                无                |                 l                  |                      ll                      |                              j                               |                           zt                           |                              L                               |                |
|                                                              |                       仅从 C99 起可用→                       |                 是                 |                                      |                                  |                                    |                      是                      |                              是                              |                           是                           |                              是                              |                |
|                             `%`                              |                        匹配字面 `%`。                        |               不适用               |                不适用                |              不适用              |               不适用               |                    不适用                    |                            不适用                            |                         不适用                         |                            不适用                            | 不适用         |
|                             `c`                              | 匹配一个**字符**或**字符**的序列。<br />如果使用了宽度指示符，那么匹配恰好*宽度*个字符（该实参必须是指向有充足空间的数组的指针）。<br />与 %s 和 %[ 不同，它不会在数组后附加空字符。 |               不适用               |                不适用                |             `char*`              |             `wchar_t*`             |                    不适用                    |                            不适用                            |                         不适用                         |                            不适用                            | 不适用         |
|                             `s`                              | 匹配非空白字符的序列（一个**字符串**）。<br />如果使用宽度指示符，那么至多匹配*宽度*个字符，或匹配到首个提前出现的空白符前。<br />总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                        |                                                              |                |
|                        `[`*集合* ﻿`]`                         | 匹配*集合* ﻿中的字符的一个非空字符序列。<br />如果集合的首字符是 `^`，那么匹配所有不在集合中的字符。<br />如果集合以 `]` 或 `^]` 开始，那么 `]` 字符也会被包含入集合。<br />在扫描集合的非最初位置的字符 `-` 是否可以指示范围，如 `[0-9]`，由实现定义。<br />如果使用宽度指示符，那么最多匹配到*宽度*。<br />总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                        |                                                              |                |
|                             `d`                              | 匹配一个**十进制整数**。<br />该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 10 为 base 时期望的格式相同。 | `signed char*` 或 `unsigned char*` | `signed short*` 或 `unsigned short*` | `signed int*` 或 `unsigned int*` | `signed long*` 或 `unsigned long*` | `signed long long*` 或 `unsigned long long*` | [intmax_t](http://zh.cppreference.com/w/c/types/integer)* 或 [uintmax_t](http://zh.cppreference.com/w/c/types/integer)* | [size_t](http://zh.cppreference.com/w/c/types/size_t)* | [ptrdiff_t](http://zh.cppreference.com/w/c/types/ptrdiff_t)* | 不适用         |
|                             `i`                              | 匹配一个**整数**。<br />该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 0 为 base 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                        |                                                              |                |
|                             `u`                              | 匹配一个无符号**十进制整数**。<br />该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 10 为 base 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                        |                                                              |                |
|                             `o`                              | 匹配一个无符号**八进制数**。<br />该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 8 为 base 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                        |                                                              |                |
|                           `x` `X`                            | 匹配一个无符号**十六进制整数**。<br />该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 16 为 base 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                        |                                                              |                |
|                             `n`                              | 返回**迄今读取的字符数**。<br />不消耗输出。不增加赋值计数。<br />如果此指示符拥有赋值抑制运算符，那么行为未定义。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                        |                                                              |                |
| `a` (C99)<br /> `A` (C99) <br />`e` `E` `f`<br /> `F` (C99) <br />`g` `G` | 匹配一个**浮点数**。<br />该数的格式与 [strtof](https://zh.cppreference.com/w/c/string/byte/strtof) 期望的格式相同。 |               不适用               |                不适用                |             `float*`             |             `double*`              |                    不适用                    |                            不适用                            |                         不适用                         |                            不适用                            | long double*   |
|                             `p`                              | 匹配定义了一个**指针**的由实现定义的字符序列。<br />`printf` 系列函数使用 `%p` 格式指示符时应该产生同样的序列。 |               不适用               |                不适用                |             `void**`             |               不适用               |                    不适用                    |                            不适用                            |                         不适用                         |                            不适用                            | 不适用         |

**注解**

​	对于每个 n 以外的转换指示符，不超过任何指定字段宽度，且要么恰好是转换指示符所期待，要么是其所期待的前缀的最长输入字符序列，即是从流中消耗的内容。此消耗序列后的首个字符如果存在，那么保持未读取。如果被消耗序列长度为零，或被消耗序列不能转换成上面所指定的项目，那么发生匹配失败，除非遇到文件尾、编码错误，或阻止从流输入的读取错误，此情况下此为输入失败。

​	所有异于 [、c 和 n 的转换指示符，在尝试分析输入前消耗并舍弃所有前导空白字符（如同以调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 来确定）。这些被消耗的字符不计入指定的最大字段宽度。

​	转换指示符 lc、ls 和 l[ 进行多字节到宽字符转换，如同如同在转换首字符前，通过用初始化为零的 [mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 对象调用 [mbrtowc](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc)。

​	转换指示符 s 与 [ 始终在匹配字符之后存储一个空字符。目标数组的大小必须至少比指定字段宽度大一。未指定目标数组大小时，对 %s 或 %[ 的使用，与 [gets](https://zh.cppreference.com/w/c/io/gets) 同样不安全。

​	[定宽整数类型](https://zh.cppreference.com/w/c/types/integer)（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确的转换指示在标头 [<inttypes.h>](https://zh.cppreference.com/w/c/types/integer) 定义（虽然 [`<CNdMA>`](https://zh.cppreference.com/w/c/types/integer)、[`<CNuMA>`](https://zh.cppreference.com/w/c/types/integer) 等就是 %jd、%ju 等的别名）。

​	在每个转换指示符后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许存储多个字段到同一“池”变量中。

​	在分析以无数字指数为结尾的不完整浮点数，如以转换指示符 %f 分析 "100er" 时，消耗序列 "100e" （可能为合法浮点数的最长前缀），并导致匹配错误（被消耗序列不能转换成浮点数），而留下 "r"。某些既存实现不遵守此规则并回滚，通过消耗 "100" 而留下 "er"，例如 [glibc 漏洞 1765](https://sourceware.org/bugzilla/show_bug.cgi?id=1765)。

​	如果转换指示非法，那么行为未定义。

**返回值**

1-3) 成功赋值的接收参数数量，或者若输入在首个接收参数赋值前发生失败，则为 [EOF](https://zh.cppreference.com/w/c/io)。

4-6) 同 (1-3)，除了若有运行时制约违规，也返回 [EOF](https://zh.cppreference.com/w/c/io)。

**注解**

​	所有这些函数调用 va_arg 至少一次，返回后 `arg` 的值不确定。这些函数不调用 va_end ，而这必须由调用方进行。

**示例**



```c
#include <stdio.h>
#include <stdbool.h>
#include <stdarg.h>
 
bool checked_sscanf(int count, const char* buf, const char *fmt, ...)
{
    va_list ap;
    va_start(ap, fmt);
    int rc = vsscanf(buf, fmt, ap);
    va_end(ap);
    return rc == count;
}
 
int main(void)
{
    int n, m;
 
    printf("Parsing '1 2'...");
    if(checked_sscanf(2, "1 2", "%d %d", &n, &m))
        puts("success");
    else
        puts("failure");
 
    printf("Parsing '1 a'...");
    if(checked_sscanf(2, "1 a", "%d %d", &n, &m))
        puts("success");
    else
        puts("failure");
}
```

​	输出：

```txt
Parsing '1 2'...success
Parsing '1 a'...failure
```



### vfscanf_s

原址：[https://zh.cppreference.com/w/c/io/vfscanf](https://zh.cppreference.com/w/c/io/vfscanf)

```c
int vscanf( const char *restrict format, va_list vlist ); // (1)	(C99 起)
int vfscanf( FILE *restrict stream, const char *restrict format,
             va_list vlist ); // (2)	(C99 起)
int vsscanf( const char *restrict buffer, const char *restrict format,
             va_list vlist ); // (3)	(C99 起)
int vscanf_s(const char *restrict format, va_list vlist); // (4)	(C11 起)
int vfscanf_s( FILE *restrict stream, const char *restrict format,
               va_list vlist); // (5)	(C11 起)
int vsscanf_s( const char *restrict buffer, const char *restrict format,
               va_list vlist); // (6)	(C11 起)
```

参见：[vfscanf](#vfscanf)



### vprintf

原址：[https://zh.cppreference.com/w/c/io/vfprintf](https://zh.cppreference.com/w/c/io/vfprintf)

```c
int vprintf( const char *format, va_list vlist ); // (C99 前)
int vprintf( const char *restrict format, va_list vlist ); // (C99 起) (2)	
int vfprintf( FILE *stream, const char *format, va_list vlist ); // (C99 前)
int vfprintf( FILE *restrict stream, const char *restrict format,
              va_list vlist ); // (C99 起) (3)	
int vsprintf( char *buffer, const char *format, va_list vlist ); // (C99 前)
int vsprintf( char *restrict buffer, const char *restrict format,
              va_list vlist ); // (C99 起)
int vsnprintf( char *restrict buffer, size_t bufsz,
               const char *restrict format, va_list vlist ); // (4)	(C99 起)
int vprintf_s( const char *restrict format, va_list vlist ); // (5)	(C11 起)
int vfprintf_s( FILE *restrict stream, const char *restrict format,
                va_list vlist ); // (6)	(C11 起)
int vsprintf_s( char *restrict buffer, rsize_t bufsz,
                const char *restrict format, va_list vlist ); // (7)	(C11 起)
int vsnprintf_s( char *restrict buffer, rsize_t bufsz,
                 const char *restrict format, va_list vlist ); // (8)	(C11 起)
```

参见：[vfpfintf](#vfpfintf)



### vprintf_s

原址：[https://zh.cppreference.com/w/c/io/vfprintf](https://zh.cppreference.com/w/c/io/vfprintf)

```c
int vprintf( const char *format, va_list vlist ); // (C99 前)
int vprintf( const char *restrict format, va_list vlist ); // (C99 起) (2)	
int vfprintf( FILE *stream, const char *format, va_list vlist ); // (C99 前)
int vfprintf( FILE *restrict stream, const char *restrict format,
              va_list vlist ); // (C99 起) (3)	
int vsprintf( char *buffer, const char *format, va_list vlist ); // (C99 前)
int vsprintf( char *restrict buffer, const char *restrict format,
              va_list vlist ); // (C99 起)
int vsnprintf( char *restrict buffer, size_t bufsz,
               const char *restrict format, va_list vlist ); // (4)	(C99 起)
int vprintf_s( const char *restrict format, va_list vlist ); // (5)	(C11 起)
int vfprintf_s( FILE *restrict stream, const char *restrict format,
                va_list vlist ); // (6)	(C11 起)
int vsprintf_s( char *restrict buffer, rsize_t bufsz,
                const char *restrict format, va_list vlist ); // (7)	(C11 起)
int vsnprintf_s( char *restrict buffer, rsize_t bufsz,
                 const char *restrict format, va_list vlist ); // (8)	(C11 起)
```

参见：[vfpfintf](#vfpfintf)



### vscanf

原址：[https://zh.cppreference.com/w/c/io/vfscanf](https://zh.cppreference.com/w/c/io/vfscanf)

```c
int vscanf( const char *restrict format, va_list vlist ); // (1)	(C99 起)
int vfscanf( FILE *restrict stream, const char *restrict format,
             va_list vlist ); // (2)	(C99 起)
int vsscanf( const char *restrict buffer, const char *restrict format,
             va_list vlist ); // (3)	(C99 起)
int vscanf_s(const char *restrict format, va_list vlist); // (4)	(C11 起)
int vfscanf_s( FILE *restrict stream, const char *restrict format,
               va_list vlist); // (5)	(C11 起)
int vsscanf_s( const char *restrict buffer, const char *restrict format,
               va_list vlist); // (6)	(C11 起)
```

参见：[vfscanf](#vfscanf)



### vscanf_s

原址：[https://zh.cppreference.com/w/c/io/vfscanf](https://zh.cppreference.com/w/c/io/vfscanf)

```c
int vscanf( const char *restrict format, va_list vlist ); // (1)	(C99 起)
int vfscanf( FILE *restrict stream, const char *restrict format,
             va_list vlist ); // (2)	(C99 起)
int vsscanf( const char *restrict buffer, const char *restrict format,
             va_list vlist ); // (3)	(C99 起)
int vscanf_s(const char *restrict format, va_list vlist); // (4)	(C11 起)
int vfscanf_s( FILE *restrict stream, const char *restrict format,
               va_list vlist); // (5)	(C11 起)
int vsscanf_s( const char *restrict buffer, const char *restrict format,
               va_list vlist); // (6)	(C11 起)
```

参见：[vfscanf](#vfscanf)



### vsnprintf

原址：[https://zh.cppreference.com/w/c/io/vfprintf](https://zh.cppreference.com/w/c/io/vfprintf)

```c
int vprintf( const char *format, va_list vlist ); // (C99 前)
int vprintf( const char *restrict format, va_list vlist ); // (C99 起) (2)	
int vfprintf( FILE *stream, const char *format, va_list vlist ); // (C99 前)
int vfprintf( FILE *restrict stream, const char *restrict format,
              va_list vlist ); // (C99 起) (3)	
int vsprintf( char *buffer, const char *format, va_list vlist ); // (C99 前)
int vsprintf( char *restrict buffer, const char *restrict format,
              va_list vlist ); // (C99 起)
int vsnprintf( char *restrict buffer, size_t bufsz,
               const char *restrict format, va_list vlist ); // (4)	(C99 起)
int vprintf_s( const char *restrict format, va_list vlist ); // (5)	(C11 起)
int vfprintf_s( FILE *restrict stream, const char *restrict format,
                va_list vlist ); // (6)	(C11 起)
int vsprintf_s( char *restrict buffer, rsize_t bufsz,
                const char *restrict format, va_list vlist ); // (7)	(C11 起)
int vsnprintf_s( char *restrict buffer, rsize_t bufsz,
                 const char *restrict format, va_list vlist ); // (8)	(C11 起)
```

参见：[vfpfintf](#vfpfintf)



### vsnprintf_s

原址：[https://zh.cppreference.com/w/c/io/vfprintf](https://zh.cppreference.com/w/c/io/vfprintf)

```c
int vprintf( const char *format, va_list vlist ); // (C99 前)
int vprintf( const char *restrict format, va_list vlist ); // (C99 起) (2)	
int vfprintf( FILE *stream, const char *format, va_list vlist ); // (C99 前)
int vfprintf( FILE *restrict stream, const char *restrict format,
              va_list vlist ); // (C99 起) (3)	
int vsprintf( char *buffer, const char *format, va_list vlist ); // (C99 前)
int vsprintf( char *restrict buffer, const char *restrict format,
              va_list vlist ); // (C99 起)
int vsnprintf( char *restrict buffer, size_t bufsz,
               const char *restrict format, va_list vlist ); // (4)	(C99 起)
int vprintf_s( const char *restrict format, va_list vlist ); // (5)	(C11 起)
int vfprintf_s( FILE *restrict stream, const char *restrict format,
                va_list vlist ); // (6)	(C11 起)
int vsprintf_s( char *restrict buffer, rsize_t bufsz,
                const char *restrict format, va_list vlist ); // (7)	(C11 起)
int vsnprintf_s( char *restrict buffer, rsize_t bufsz,
                 const char *restrict format, va_list vlist ); // (8)	(C11 起)
```

参见：[vfpfintf](#vfpfintf)



### vsprintf

原址：[https://zh.cppreference.com/w/c/io/vfprintf](https://zh.cppreference.com/w/c/io/vfprintf)

```c
int vprintf( const char *format, va_list vlist ); // (C99 前)
int vprintf( const char *restrict format, va_list vlist ); // (C99 起) (2)	
int vfprintf( FILE *stream, const char *format, va_list vlist ); // (C99 前)
int vfprintf( FILE *restrict stream, const char *restrict format,
              va_list vlist ); // (C99 起) (3)	
int vsprintf( char *buffer, const char *format, va_list vlist ); // (C99 前)
int vsprintf( char *restrict buffer, const char *restrict format,
              va_list vlist ); // (C99 起)
int vsnprintf( char *restrict buffer, size_t bufsz,
               const char *restrict format, va_list vlist ); // (4)	(C99 起)
int vprintf_s( const char *restrict format, va_list vlist ); // (5)	(C11 起)
int vfprintf_s( FILE *restrict stream, const char *restrict format,
                va_list vlist ); // (6)	(C11 起)
int vsprintf_s( char *restrict buffer, rsize_t bufsz,
                const char *restrict format, va_list vlist ); // (7)	(C11 起)
int vsnprintf_s( char *restrict buffer, rsize_t bufsz,
                 const char *restrict format, va_list vlist ); // (8)	(C11 起)
```

参见：[vfpfintf](#vfpfintf)

```c

```





### vsprintf_s

原址：[https://zh.cppreference.com/w/c/io/vfprintf](https://zh.cppreference.com/w/c/io/vfprintf)

```c
int vprintf( const char *format, va_list vlist ); // (C99 前)
int vprintf( const char *restrict format, va_list vlist ); // (C99 起) (2)	
int vfprintf( FILE *stream, const char *format, va_list vlist ); // (C99 前)
int vfprintf( FILE *restrict stream, const char *restrict format,
              va_list vlist ); // (C99 起) (3)	
int vsprintf( char *buffer, const char *format, va_list vlist ); // (C99 前)
int vsprintf( char *restrict buffer, const char *restrict format,
              va_list vlist ); // (C99 起)
int vsnprintf( char *restrict buffer, size_t bufsz,
               const char *restrict format, va_list vlist ); // (4)	(C99 起)
int vprintf_s( const char *restrict format, va_list vlist ); // (5)	(C11 起)
int vfprintf_s( FILE *restrict stream, const char *restrict format,
                va_list vlist ); // (6)	(C11 起)
int vsprintf_s( char *restrict buffer, rsize_t bufsz,
                const char *restrict format, va_list vlist ); // (7)	(C11 起)
int vsnprintf_s( char *restrict buffer, rsize_t bufsz,
                 const char *restrict format, va_list vlist ); // (8)	(C11 起)
```

参见：[vfpfintf](#vfpfintf)



### vsscanf

原址：[https://zh.cppreference.com/w/c/io/vfscanf](https://zh.cppreference.com/w/c/io/vfscanf)

```c
int vscanf( const char *restrict format, va_list vlist ); // (1)	(C99 起)
int vfscanf( FILE *restrict stream, const char *restrict format,
             va_list vlist ); // (2)	(C99 起)
int vsscanf( const char *restrict buffer, const char *restrict format,
             va_list vlist ); // (3)	(C99 起)
int vscanf_s(const char *restrict format, va_list vlist); // (4)	(C11 起)
int vfscanf_s( FILE *restrict stream, const char *restrict format,
               va_list vlist); // (5)	(C11 起)
int vsscanf_s( const char *restrict buffer, const char *restrict format,
               va_list vlist); // (6)	(C11 起)
```

参见：[vfscanf](#vfscanf)



### vsscanf_s

原址：[https://zh.cppreference.com/w/c/io/vfscanf](https://zh.cppreference.com/w/c/io/vfscanf)

```c
int vscanf( const char *restrict format, va_list vlist ); // (1)	(C99 起)
int vfscanf( FILE *restrict stream, const char *restrict format,
             va_list vlist ); // (2)	(C99 起)
int vsscanf( const char *restrict buffer, const char *restrict format,
             va_list vlist ); // (3)	(C99 起)
int vscanf_s(const char *restrict format, va_list vlist); // (4)	(C11 起)
int vfscanf_s( FILE *restrict stream, const char *restrict format,
               va_list vlist); // (5)	(C11 起)
int vsscanf_s( const char *restrict buffer, const char *restrict format,
               va_list vlist); // (6)	(C11 起)
```

参见：[vfscanf](#vfscanf)



