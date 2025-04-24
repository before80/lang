
+++
title = "<stdio.h>"
date = 2025-04-24T18:43:06+08:00
weight = 210
type = "docs"
description = "输入/输出"
isCJKLanguage = true
draft = false

+++

## 类型



### FILE

原址：[http://zh.cppreference.com/w/c/io](http://zh.cppreference.com/w/c/io)

作用：

备注：
​	[`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 头文件提供了通用的文件操作支持，并提供了具有窄字符输入/输出功能的函数。

​	[`<wchar.h>`](https://zh.cppreference.com/w/c/header/wchar) 头文件提供了具有宽字符输入/输出功能的函数。

​	I/O 流由 **FILE** 类型的对象表示，该对象只能通过 `FILE*` 类型的指针访问及操作。每个流都与外部的物理设备（文件、标准输入流、打印机、序列端口等）相关联。

### 类型

| 在标头 `<stdio.h>` 定义                                   |                                                              |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| [FILE<br />](https://zh.cppreference.com/w/c/io/FILE)     | 对象类型，能够保存控制 C I/O 流所需的全部信息 (typedef)      |
| [fpos_t<br />](https://zh.cppreference.com/w/c/io/fpos_t) | 非数组完整对象类型，足以唯一指定文件的位置和多字节解析状态 (typedef) |

### 预定义标准流

| 在标头 `<stdio.h>` 定义                                    |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [stdin<br />stdout<br />stderr<br />](https://zh.cppreference.com/w/c/io/std_streams) | 与标准输入流关联的 `FILE*` 类型表达式 与标准输出流关联的 `FILE*` 类型表达式 与标准错误输出流关联的 `FILE*` 类型表达式 (宏常量) |

### 函数

| 文件访问                                                     |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 在标头 `<stdio.h>` 定义                                    |                                                              |
| [fopen <br />fopen_s (C11)<br />](https://zh.cppreference.com/w/c/io/fopen) | 打开文件 (函数)                                              |
| [freopen <br />freopen_s (C11)<br />](https://zh.cppreference.com/w/c/io/freopen) | 以不同名称打开既存的文件流 (函数)                            |
| [fclose<br />](https://zh.cppreference.com/w/c/io/fclose)  | 关闭文件 (函数)                                              |
| [fflush<br />](https://zh.cppreference.com/w/c/io/fflush)  | 将输出流与实际文件同步 (函数)                                |
| [setbuf<br />](https://zh.cppreference.com/w/c/io/setbuf)  | 为文件流设置缓冲区 (函数)                                    |
| [setvbuf<br />](https://zh.cppreference.com/w/c/io/setvbuf) | 为文件流设置缓冲区和其大小 (函数)                            |
| 在标头 `<wchar.h>` 定义                                    |                                                              |
| [fwide (C95)<br />](https://zh.cppreference.com/w/c/io/fwide) | 将文件流在宽字符 I/O 和窄字符 I/O 间切换 (函数)              |
| 直接输入/输出                                                |                                                              |
| 在标头 `<stdio.h>` 定义                                    |                                                              |
| [fread<br />](https://zh.cppreference.com/w/c/io/fread)    | 从文件读取 (函数)                                            |
| [fwrite<br />](https://zh.cppreference.com/w/c/io/fwrite)  | 写入到文件 (函数)                                            |
| 无格式输入/输出                                              |                                                              |
| 窄字符                                                       |                                                              |
| 在标头 `<stdio.h>` 定义                                    |                                                              |
| [fgetc<br />getc<br />](https://zh.cppreference.com/w/c/io/fgetc) | 从文件流获取一个字符 (函数)                                  |
| [fgets<br />](https://zh.cppreference.com/w/c/io/fgets)    | 从文件流获取一个字符串 (函数)                                |
| [fputc<br />putc<br />](https://zh.cppreference.com/w/c/io/fputc) | 将一个字符写入文件流 (函数)                                  |
| [fputs<br />](https://zh.cppreference.com/w/c/io/fputs)    | 将一个字符串写入文件流 (函数)                                |
| [getchar<br />](https://zh.cppreference.com/w/c/io/getchar) | 从 **stdin** 读取一个字符 (函数)                             |
| [gets (C11 移除)<br />gets_s (C11 移除)<br />](https://zh.cppreference.com/w/c/io/gets) | 从 **stdin** 读取一个字符串 (函数)                           |
| [putchar<br />](https://zh.cppreference.com/w/c/io/putchar) | 将一个字符写入 **stdout** (函数)                             |
| [puts<br />](https://zh.cppreference.com/w/c/io/puts)      | 将一个字符串写入 **stdout** (函数)                           |
| [ungetc<br />](https://zh.cppreference.com/w/c/io/ungetc)  | 将一个字符送回文件流 (函数)                                  |
| 宽字符                                                       |                                                              |
| 在标头 `<wchar.h>` 定义                                    |                                                              |
| [fgetwc (C95)<br />getwc (C95)<br />](https://zh.cppreference.com/w/c/io/fgetwc) | 从文件流获取一个宽字符 (函数)                                |
| [fgetws (C95)<br />](https://zh.cppreference.com/w/c/io/fgetws) | 从文件流获取一个宽字符串 (函数)                              |
| [fputwc (C95)<br />putwc (C95)<br />](https://zh.cppreference.com/w/c/io/fputwc) | 将一个宽字符写入文件流 (函数)                                |
| [fputws (C95)<br />](https://zh.cppreference.com/w/c/io/fputws) | 将一个宽字符串写入文件流 (函数)                              |
| [getwchar (C95)<br />](https://zh.cppreference.com/w/c/io/getwchar) | 从 **stdin** 读取一个宽字符 (函数)                           |
| [putwchar (C95)<br />](https://zh.cppreference.com/w/c/io/putwchar) | 将一个宽字符写入 **stdout** (函数)                           |
| [ungetwc (C95)<br />](https://zh.cppreference.com/w/c/io/ungetwc) | 将一个宽字符送回文件流 (函数)                                |
| 有格式输入/输出                                              |                                                              |
| 窄字符                                                       |                                                              |
| 在标头 `<stdio.h>` 定义                                    |                                                              |
| [scanf <br />fscanf <br />sscanf <br />scanf_s (C11)<br />fscanf_s (C11)<br />sscanf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fscanf) | 从**stdin**、文件流或缓冲区读取格式化输入 (函数)             |
| [vscanf (C99)<br />vfscanf (C99)<br />vsscanf (C99)<br />vscanf_s (C99)<br />vfscanf_s (C99)<br />vsscanf_s (C99)<br />](https://zh.cppreference.com/w/c/io/vfscanf) | 从 **stdin**、文件流或缓冲区读取格式化输入 使用可变参数列表 (函数) |
| [printf <br />fprintf <br />sprintf <br />snprintf (C99)<br />printf_s (C99)<br />fprintf_s (C11)<br />sprintf_s (C11)<br />snprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fprintf) | 打印格式化输出到 **stdout**、文件流或缓冲区 (函数)           |
| [vprintf <br />vfprintf <br />vsprintf <br />vsnprintf (C99)<br />vprintf_s (C99)<br />vfprintf_s (C11)<br />vsprintf_s (C11)<br />vsnprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/vfprintf) | 打印格式化输出到 **stdout**、文件流或缓冲区 使用可变参数列表 (函数) |
| 宽字符                                                       |                                                              |
| 在标头 `<wchar.h>` 定义                                    |                                                              |
| [wscanf (C95)<br />fwscanf (C95)<br />swscanf (C95)<br />wscanf_s (C95)<br />fwscanf_s (C95)<br />swscanf_s (C95)<br />](https://zh.cppreference.com/w/c/io/fwscanf) | 从 **stdin**、文件流或缓冲区读取格式化宽字符输入 (函数)      |
| [vwscanf (C99)<br />vfwscanf (C99)<br />vswscanf (C99)<br />vwscanf_s (C99)<br />vfwscanf_s (C99)<br />vswscanf_s (C99)<br />](https://zh.cppreference.com/w/c/io/vfwscanf) | 从 **stdin**、文件流或缓冲区读取格式化宽字符输入 使用可变参数列表 (函数) |
| [wprintf (C95)<br />fwprintf (C95)<br />swprintf (C95)<br />wprintf_s (C95)<br />fwprintf_s (C95)<br />swprintf_s (C95)<br />snwprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fwprintf) | 打印格式化宽字符输出到 **stdout**、文件流或缓冲区 (函数)     |
| [vwprintf (C95)<br />vfwprintf (C95)<br />vswprintf (C95)<br />vwprintf_s (C95)<br />vfwprintf_s (C95)<br />vswprintf_s (C95)<br />vsnwprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/vfwprintf) | 打印格式化宽字符输出到 **stdout**、文件流或缓冲区 使用可变参数列表 (函数) |
| 文件定位                                                     |                                                              |
| 在标头 `<stdio.h>` 定义                                    |                                                              |
| [ftell<br />](https://zh.cppreference.com/w/c/io/ftell)    | 返回当前的文件位置指示值 (函数)                              |
| [fgetpos<br />](https://zh.cppreference.com/w/c/io/fgetpos) | 获取文件位置指示器 (函数)                                    |
| [fseek<br />](https://zh.cppreference.com/w/c/io/fseek)    | 将文件位置指示符移动到文件中的指定位置 (函数)                |
| [fsetpos<br />](https://zh.cppreference.com/w/c/io/fsetpos) | 将文件位置指示器移动到文件中的指定位置 (函数)                |
| [rewind<br />](https://zh.cppreference.com/w/c/io/rewind)  | 将文件位置指示器移动到文件首 (函数)                          |
| 错误处理                                                     |                                                              |
| 在标头 `<stdio.h>` 定义                                    |                                                              |
| [clearerr<br />](https://zh.cppreference.com/w/c/io/clearerr) | 清除错误 (函数)                                              |
| [feof<br />](https://zh.cppreference.com/w/c/io/feof)      | 检查文件结尾 (函数)                                          |
| [ferror<br />](https://zh.cppreference.com/w/c/io/ferror)  | 检查文件错误 (函数)                                          |
| [perror<br />](https://zh.cppreference.com/w/c/io/perror)  | 显示对应当前错误的字符串到 **stderr** (函数)                 |
| 对文件的操作                                                 |                                                              |
| 在标头 `<stdio.h>` 定义                                    |                                                              |
| [remove<br />](https://zh.cppreference.com/w/c/io/remove)  | 删除文件 (函数)                                              |
| [rename<br />](https://zh.cppreference.com/w/c/io/rename)  | 重命名文件 (函数)                                            |
| [tmpfile <br />tmpfile_s (C11)<br />](https://zh.cppreference.com/w/c/io/tmpfile) | 返回指向临时文件的指针 (函数)                                |
| [tmpnam <br />tmpnam_s (C11)<br />](https://zh.cppreference.com/w/c/io/tmpnam) | 返回唯一的文件名 (函数)                                      |

### 宏常量

| 在标头 `<stdio.h>` 定义                        |                                                              |
| ------------------------------------------------ | ------------------------------------------------------------ |
| EOF<br />                                      | `int` 类型的负数整数常量表达式 (宏常量)                      |
| FOPEN_MAX<br />                                | 能同时打开的最大文件数 (宏常量)                              |
| FILENAME_MAX<br />                             | 保有最长受支持文件名所需的 `char` 数组大小 (宏常量)          |
| BUFSIZ<br />                                   | [setbuf](https://zh.cppreference.com/w/c/io/setbuf) 所用的缓冲区大小 (宏常量) |
| _IOFBF<br />_IOLBF<br />_IONBF<br />       | 指示全缓冲 I/O 的 [setvbuf](https://zh.cppreference.com/w/c/io/setvbuf) 参数 指示行缓冲 I/O 的 [setvbuf](https://zh.cppreference.com/w/c/io/setvbuf) 参数 指示无缓冲 I/O 的 [setvbuf](https://zh.cppreference.com/w/c/io/setvbuf) 参数 (宏常量) |
| SEEK_SET<br />SEEK_CUR<br />SEEK_END<br /> | 指示从文件首开始寻位的 [fseek](https://zh.cppreference.com/w/c/io/fseek) 参数 指示从文件当前位置开始寻位的 [fseek](https://zh.cppreference.com/w/c/io/fseek) 参数 指示从文件尾开始寻位的 [fseek](https://zh.cppreference.com/w/c/io/fseek) 参数 (宏常量) |
| TMP_MAX <br />TMP_MAX_S (C11)<br />          | [tmpnam](https://zh.cppreference.com/w/c/io/tmpnam) 所能生成的独有文件名的最大数量 tmpnam_s 所能生成的独有文件名的最大数量 (宏常量) |
| L_tmpnam <br />L_tmpnam_s (C11)<br />        | 保有 [tmpnam](https://zh.cppreference.com/w/c/io/tmpnam) 结果所需的 `char` 数组大小 保有 tmpnam_s 结果所需的 `char` 数组大小 (宏常量) |

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21 Input/output <stdio.h> （第 TBD 页）

  - 7.29 Extended multibyte and wide character utilities <wchar.h> （第 TBD 页）

  - 7.31.11 Input/output <stdio.h> （第 TBD 页）

  - 7.31.16 Extended multibyte and wide character utilities <wchar.h> （第 TBD 页）

  - K.3.5 Input/output <stdio.h> （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21 Input/output <stdio.h> （第 TBD 页）

  - 7.29 Extended multibyte and wide character utilities <wchar.h> （第 TBD 页）

  - 7.31.11 Input/output <stdio.h> （第 TBD 页）

  - 7.31.16 Extended multibyte and wide character utilities <wchar.h> （第 TBD 页）

  - K.3.5 Input/output <stdio.h> （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21 Input/output <stdio.h> （第 296-339 页）

  - 7.29 Extended multibyte and wide character utilities <wchar.h> （第 402-446 页）

  - 7.31.11 Input/output <stdio.h> （第 456 页）

  - 7.31.16 Extended multibyte and wide character utilities <wchar.h> （第 456 页）

  - K.3.5 Input/output <stdio.h> （第 586-603 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19 Input/output <stdio.h> （第 262-305 页）

  - 7.24 Extended multibyte and wide character utilities <wchar.h> （第 348-392 页）

  - 7.26.9 Input/output <stdio.h> （第 402 页）

  - 7.26.12 Extended multibyte and wide character utilities <wchar.h> （第 402 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9 INPUT/OUTPUT <stdio.h>

  - 4.13.6 Input/output <stdio.h>

**参阅**

**C 风格文件输入/输出**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c)**





### errno_t

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### fpos_t

原址：[http://zh.cppreference.com/w/c/io](http://zh.cppreference.com/w/c/io)

作用：

备注：





### rsize_t

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### size_t

原址：[http://zh.cppreference.com/w/c/types/size_t](http://zh.cppreference.com/w/c/types/size_t)

作用：

备注：






## 枚举




## 宏



### BUFSIZ

原址：

作用：

备注：





### EOF

原址：

作用：

备注：





### FILENAME_MAX

原址：

作用：

备注：





### FOPEN_MAX

原址：

作用：

备注：





### L_tmpnam

原址：

作用：

备注：





### L_tmpnam_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### NULL

原址：

作用：

备注：





### SEEK_CUR

原址：

作用：

备注：





### SEEK_END

原址：

作用：

备注：





### SEEK_SET

原址：

作用：

备注：





### TMP_MAX

原址：

作用：

备注：





### TMP_MAX_S

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### _IOFBF

原址：

作用：

备注：





### _IOLBF

原址：

作用：

备注：





### _IONBF

原址：

作用：

备注：





### _PRINTF_NAN_LEN_MAX

原址：

作用：

备注：





### __STDC_VERSION_STDIO_H__

原址：

作用：

备注：





### stderr

原址：

作用：

备注：





### stdin

原址：

作用：

备注：





### stdout

原址：

作用：

备注：






## 函数



### clearerr

原址：[http://zh.cppreference.com/w/c/io/clearerr](http://zh.cppreference.com/w/c/io/clearerr)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
void clearerr( FILE *stream );
```

​	重置给定文件流的错误标志和 [`EOF`](https://zh.cppreference.com/w/c/io#.E5.AE.8F.E5.B8.B8.E9.87.8F) 指示器。

**参数**

| stream | -    | 要重置错误标志的文件流 |
| ------ | ---- | ---------------------- |
|        |      |                        |

**返回值**

​	（无）

**示例**

```c
#include <stdio.h>
#include <assert.h>
 
int main(void)
{
    FILE* tmpf = tmpfile();
    fputs("cppreference.com\n", tmpf);
    rewind(tmpf);
    int ch;
    for (int ch; (ch = fgetc(tmpf)) != EOF; putchar(ch)) { }
 
    assert(feof(tmpf)); // 此循环期待以 EOF 终止
    puts("End of file reached");
 
    clearerr(tmpf);  // 清除 EOF
 
    puts(feof(tmpf) ? "EOF indicator set"
                    : "EOF indicator cleared");
 
 
}
```

​	输出：

```txt
cppreference.com
End of file reached
EOF indicator cleared
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.10.1 The clearerr function （第 246 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.10.1 The clearerr function （第 338 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.10.1 The clearerr function （第 304 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.10.1 The clearerr function

**参阅**

| [feof<br />](https://zh.cppreference.com/w/c/io/feof)      | 检查文件结尾 (函数)                                          |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [perror<br />](https://zh.cppreference.com/w/c/io/perror)  | 显示对应当前错误的字符串到 [stderr](https://zh.cppreference.com/w/c/io) (函数) |
| [ferror<br />](https://zh.cppreference.com/w/c/io/ferror)  | 检查文件错误 (函数)                                          |
| **clearerr** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/clearerr)** |                                                              |





### fclose

原址：[http://zh.cppreference.com/w/c/io/fclose](http://zh.cppreference.com/w/c/io/fclose)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int fclose( FILE* stream );
```

​	关闭给定的文件流。冲入任何未写入的缓冲数据到 OS 。舍弃任何未读取的缓冲数据。

​	无论操作是否成功，流都不再关联到文件，且由 [setbuf](https://zh.cppreference.com/w/c/io/setbuf) 或 [setvbuf](https://zh.cppreference.com/w/c/io/setvbuf) 分配的缓冲区若存在，则亦被解除关联，并且若使用自动分配则被解分配。

​	若在 `fclose` 返回后使用指针 `stream` 的值则行为未定义。

**参数**

| stream | -    | 需要关闭的文件流 |
| ------ | ---- | ---------------- |
|        |      |                  |

**返回值**

​	成功时为 `0`，否则为 [EOF](https://zh.cppreference.com/w/c/io)。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.5.1 The fclose function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.5.1 The fclose function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.5.1 The fclose function （第 304 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.5.1 The fclose function （第 270 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.5.1 The fclose function

**参阅**

| [fopen <br />fopen_s (C11)<br />](https://zh.cppreference.com/w/c/io/fopen) | 打开文件 (函数)                   |
| ------------------------------------------------------------ | --------------------------------- |
| [freopen <br />freopen_s (C11)<br />](https://zh.cppreference.com/w/c/io/freopen) | 以不同名称打开既存的文件流 (函数) |
| **fclose** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fclose)** |                                   |





### feof

原址：[http://zh.cppreference.com/w/c/io/feof](http://zh.cppreference.com/w/c/io/feof)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int feof( FILE *stream );
```

​	检查是否已抵达给定文件流的结尾。

**参数**

| stream | -    | 要检验的文件流 |
| ------ | ---- | -------------- |
|        |      |                |

**返回值**

​	若已抵达流尾则为非零值，否则为 `0`

**注意**

​	此函数仅报告最近一次 I/O 操作所报告的流状态，而不检验关联的数据源。例如，若最近一次 I/O 是抵达文件最后字节的 [fgetc](https://zh.cppreference.com/w/c/io/fgetc) ，则 `feof` 返回零。下个 [fgetc](https://zh.cppreference.com/w/c/io/fgetc) 失败并更改流状态为*文件尾*。然后 `feof` 才返回非零。

​	典型用法中，输入流处理在任何错误时停止；而 `feof` 和 [ferror](https://zh.cppreference.com/w/c/io/ferror) 用于区别不同错误条件。

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

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.10.2 The feof function （第 339 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.10.2 The feof function （第 305 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.10.2 The feof function

**参阅**

| [clearerr<br />](https://zh.cppreference.com/w/c/io/clearerr) | 清除错误 (函数)                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [perror<br />](https://zh.cppreference.com/w/c/io/perror)  | 显示对应当前错误的字符串到 [stderr](https://zh.cppreference.com/w/c/io) (函数) |
| [ferror<br />](https://zh.cppreference.com/w/c/io/ferror)  | 检查文件错误 (函数)                                          |
| **feof** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/feof)** |                                                              |





### ferror

原址：[http://zh.cppreference.com/w/c/io/ferror](http://zh.cppreference.com/w/c/io/ferror)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int ferror( FILE *stream );
```

​	检查给定文件流的错误。

**参数**

| stream | -    | 要检查的文件流 |
| ------ | ---- | -------------- |
|        |      |                |

**返回值**

​	若文件流已出现错误则为非零值，否则为 `0`

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
#include <locale.h>
#include <wchar.h>
 
int main(void)
{
    char* fname = tmpnam(NULL);
    FILE* f = fopen(fname, "wb");
    fputs("\xff\xff\n", f); // 不是合法的 UTF-8 序列
    fclose(f);
 
    setlocale(LC_ALL, "en_US.utf8");
    f = fopen(fname, "rb");
    wint_t ch;
    while ((ch=fgetwc(f)) != WEOF) // 试图读作 UTF-8 而失败
          printf("%#x ", ch);
 
    if (feof(f))
        puts("EOF indicator set");
    if (ferror(f))
        puts("Error indicator set");
}
```

​	输出：

```txt
Error indicator set
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.10.3 The ferror function （第 339 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.10.3 The ferror function （第 305 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.10.3 The ferror function

**参阅**

| [clearerr<br />](https://zh.cppreference.com/w/c/io/clearerr) | 清除错误 (函数)                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [feof<br />](https://zh.cppreference.com/w/c/io/feof)      | 检查文件结尾 (函数)                                          |
| [perror<br />](https://zh.cppreference.com/w/c/io/perror)  | 显示对应当前错误的字符串到 [stderr](https://zh.cppreference.com/w/c/io) (函数) |
| **ferror** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/ferror)** |                                                              |





### fflush

原址：[http://zh.cppreference.com/w/c/io/fflush](http://zh.cppreference.com/w/c/io/fflush)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int fflush( FILE* stream );
```

​	对于输出流（及最后操作为输出的更新流），从 `stream` 的缓冲区写入未写的数据到关联的输出设备。

​	对于输入流（及最后操作为输入的更新流），行为未定义。

​	若 `stream` 是空指针，则冲入所有输出流，包括操作于库包内者，或在其他情况下程序无法直接访问者。

**参数**

| stream | -    | 要写出的文件流 |
| ------ | ---- | -------------- |
|        |      |                |

**返回值**

​	成功时返回零。否则返回 [EOF](https://zh.cppreference.com/w/c/io) 并设置文件流的错误指示器。

**注解**

​	POSIX 通过定义 `fflush` 对输入流的效果[扩展它的规定](http://pubs.opengroup.org/onlinepubs/9699919799/functions/fflush.html)，只要该流还表示一个文件或另一个可定位设备：该情况下重寻位 POSIX 文件指针以匹配 C 流指针（这有效地撤销任何读缓冲），并舍弃任何尚未回读的 [ungetc](https://zh.cppreference.com/w/c/io/ungetc) 或 [ungetwc](https://zh.cppreference.com/w/c/io/ungetwc) 的效果。

​	微软（Microsoft）也通过定义 `fflush` 对输入流的效果扩展它的规定：在 Visual Studio 2013 及以前的版本中，[放弃输入缓冲区](https://docs.microsoft.com/en-us/previous-versions/visualstudio/visual-studio-2013/9yky46tz(v=vs.120))；在 Visual Studio 2015 及以后的版本中，[无影响并保留缓冲区](https://msdn.microsoft.com/en-us/library/9yky46tz.aspx)。

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.5.2 The fflush function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.5.2 The fflush function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.5.2 The fflush function （第 305 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.5.2 The fflush function （第 270-271 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.5.2 The fflush function

**参阅**

| [fopen <br />fopen_s (C11)<br />](https://zh.cppreference.com/w/c/io/fopen) | 打开文件 (函数) |
| ------------------------------------------------------------ | --------------- |
| [fclose<br />](https://zh.cppreference.com/w/c/io/fclose)  | 关闭文件 (函数) |
| **fflush** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fflush)** |                 |





### fgetc

原址：[http://zh.cppreference.com/w/c/io/fgetc](http://zh.cppreference.com/w/c/io/fgetc)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int fgetc( FILE* stream );// (1)
int getc( FILE* stream );// (2)
```

1） 从给定的输入流读取下一个字符。

2） 同 `fgetc`，但若 `getc` 实现为宏，则它可能求值 `stream` 多于一次，所以实参始终不应为带有副作用的表达式。

**参数**

| stream | -    | 读取字符的来源 |
| ------ | ---- | -------------- |
|        |      |                |

**返回值**

​	成功时，返回作为 `unsigned char` 获得并转换为 `int` 的字符。 失败时，返回 [EOF](https://zh.cppreference.com/w/c/io)。

​	若文件尾条件导致失败，则另外设置 `stream` 上的*文件尾*指示器（见 [feof()](https://zh.cppreference.com/w/c/io/feof)）。若某些其他错误导致失败，则设置 `stream` 上的*错误*指示器（见 [ferror()](https://zh.cppreference.com/w/c/io/ferror)）。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.7.1 The fgetc function （第 TBD 页）

  - 7.21.7.5 The getc function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.7.1 The fgetc function （第 240-241 页）

  - 7.21.7.5 The getc function （第 242 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.7.1 The fgetc function （第 330 页）

  - 7.21.7.5 The getc function （第 332 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.7.1 The fgetc function （第 296 页）

  - 7.19.7.5 The getc function （第 297-298 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.7.1 The fgetc function

  - 4.9.7.5 The getc function

**参阅**

| [getchar<br />](https://zh.cppreference.com/w/c/io/getchar) | 从 [stdin](https://zh.cppreference.com/w/c/io) 读取一个字符 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [gets (C11 移除)<br />gets_s (C11 移除)<br />](https://zh.cppreference.com/w/c/io/gets) | 从 [stdin](https://zh.cppreference.com/w/c/io) 读取一个字符串 (函数) |
| [fputc<br />putc<br />](https://zh.cppreference.com/w/c/io/fputc) | 将一个字符写入文件流 (函数)                                  |
| [ungetc<br />](https://zh.cppreference.com/w/c/io/ungetc)  | 将一个字符送回文件流 (函数)                                  |
| **fgetc, getc** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fgetc)** |                                                              |





### fgetpos

原址：[http://zh.cppreference.com/w/c/io/fgetpos](http://zh.cppreference.com/w/c/io/fgetpos)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int fgetpos( FILE*          stream, fpos_t*          pos );// (C99 前)
int fgetpos( FILE* restrict stream, fpos_t* restrict pos );// (C99 起)
```

​	获得文件流 `stream` 的文件位置指示器和当前分析状态（若存在），并将它们存储于 `pos` 所指向的对象。存储的值仅在作为 [fsetpos](https://zh.cppreference.com/w/c/io/fsetpos) 的输入的情况有意义。

**参数**

| stream | -    | 要检验的文件流                                               |
| ------ | ---- | ------------------------------------------------------------ |
| pos    | -    | 指向要存储文件位置指示器到的 [fpos_t](https://zh.cppreference.com/w/c/io) 对象的指针 |

**返回值**

​	成功时为 `0`，否则非零值。

**示例**

```c
#include <assert.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    // 准备保有 4 个 double 类型值的文件
    enum {SIZE = 4};
    FILE* fp = fopen("test.bin", "wb");
    assert(fp);
    int rc = fwrite((double[SIZE]){1.1, 2.2, 3.3, 4.4}, sizeof(double), SIZE, fp);
    assert(rc == SIZE);
    fclose(fp);
 
    // 演示使用 fsetpos 返回到文件起始
    fp = fopen("test.bin", "rb");
    fpos_t pos;
    fgetpos(fp, &pos);               // 存储文件起始于 pos
    double d;
    rc = fread(&d, sizeof d, 1, fp); // 读取首个 double
    assert(rc == 1);
    printf("文件中的第一个值: %.1f\n", d);
    fsetpos(fp,&pos);                // 移动文件位置回文件起始
    rc = fread(&d, sizeof d, 1, fp); // 再次读取首个 double
    assert(rc == 1);
    printf("再次读取文件中的第一个值: %.1f\n", d);
    fclose(fp);
 
    // 演示错误处理
    rc = fsetpos(stdin, &pos);
    if(rc)
        perror("无法对 stdin fsetpos");
}
```

​	输出：

```txt
文件中的第一个值: 1.1
再次读取文件中的第一个值: 1.1
无法对 stdin fsetpos: Illegal seek
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.9.1 The fgetpos function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.9.1 The fgetpos function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.9.1 The fgetpos function （第 336 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.9.1 The fgetpos function （第 302 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.9.1 The fgetpos function

**参阅**

| [ftell<br />](https://zh.cppreference.com/w/c/io/ftell)    | 返回当前的文件位置指示值 (函数)               |
| ------------------------------------------------------------ | --------------------------------------------- |
| [fseek<br />](https://zh.cppreference.com/w/c/io/fseek)    | 将文件位置指示符移动到文件中的指定位置 (函数) |
| [fsetpos<br />](https://zh.cppreference.com/w/c/io/fsetpos) | 将文件位置指示器移动到文件中的指定位置 (函数) |
| **fgetpos** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fgetpos)** |                                               |





### fgets

原址：[http://zh.cppreference.com/w/c/io/fgets](http://zh.cppreference.com/w/c/io/fgets)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
char* fgets( char*          str, int count, FILE*          stream );// (C99 前)
char* fgets( char* restrict str, int count, FILE* restrict stream );// (C99 起)
```

​	从给定文件流读取最多 `count - 1` 个字符并将它们存储于 `str` 所指向的字符数组。若文件尾出现或发现换行符则终止分析，后一情况下 `str` 将包含一个换行符。若读入字节且无错误发生，则紧随写入到 `str` 的最后一个字符后写入空字符。

**参数**

| str    | -    | 指向 char 数组元素的指针                  |
| ------ | ---- | ----------------------------------------- |
| count  | -    | 写入的最大字符数（典型的为 `str` 的长度） |
| stream | -    | 读取数据来源的文件流                      |

**返回值**

​	成功时为 `str`，失败时为空指针。

​	若遇到文件尾条件导致了失败，则设置 `stream` 上的*文件尾*指示器（见 [feof()](https://zh.cppreference.com/w/c/io/feof)）。这仅若它导致未读取字符才是失败，该情况下返回空指针且不改变 `str` 所指向数组的内容（即不以空字符覆写首字节）。

​	若某些其他错误导致了失败，则设置 `stream` 上的*错误*指示器（见 [ferror()](https://zh.cppreference.com/w/c/io/ferror)）。`str` 所指向的数组内容是不确定的（甚至可以不是空终止）。

**注解**

​	[POSIX 额外要求](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fgets.html)若 `fgets` 发生读取错误则设置 [errno](https://zh.cppreference.com/w/c/error/errno)。

​	尽管标准规范在 `count <= 1` 的情况下[不明](https://stackoverflow.com/questions/23388620)，常见的实现

- 若 `count < 1` 则不做任何事并报告错误，
- 若 `count == 1`，则

  - 某些实现不做任何事并报告错误，
  - 其他实现不读内容，存储零于 `str[0]` 并报告成功

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.7.2 The fgets function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.7.2 The fgets function （第 241 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.7.2 The fgets function （第 331 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.7.2 The fgets function （第 296 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.7.2 The fgets function

**参阅**

| [scanf <br />fscanf <br />sscanf <br />scanf_s (C11)<br />fscanf_s (C11)<br />sscanf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fscanf) | 从[stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [gets (C11 移除)<br />gets_s (C11 移除)<br />](https://zh.cppreference.com/w/c/io/gets) | 从 [stdin](https://zh.cppreference.com/w/c/io) 读取一个字符串 (函数) |
| [fputs<br />](https://zh.cppreference.com/w/c/io/fputs)    | 将一个字符串写入文件流 (函数)                                |
| [getline (动态内存 TR)<br />getwline (动态内存 TR)<br />getdelim<br />getwdelim<br />](https://zh.cppreference.com/w/c/experimental/dynamic/getline) | 从流读入至动态改变大小的缓冲区，直到分隔符/行尾 (函数)       |
| **fgets** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fgets)** |                                                              |





### fopen

原址：[http://zh.cppreference.com/w/c/io/fopen](http://zh.cppreference.com/w/c/io/fopen)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
// (1)
FILE *fopen( const char *filename, const char *mode );// (C99 前)
FILE *fopen( const char *restrict filename, const char *restrict mode );// (C99 起)
errno_t fopen_s( FILE *restrict *restrict streamptr,
                 const char *restrict filename,

                 const char *restrict mode );// (2)(C11 起)
```

1） 打开 `filename` 所指示的文件，并返回指向关联到该文件的文件流的指针。 `mode` 用于确定文件访问模式。

2） 同(1)，除了指向文件流的指针被写入 `streamptr` ，还在运行时检测下列错误，并调用当前安装的[约束处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)函数：

  - `streamptr` 是空指针
  - `filename` 是空指针
  - `mode` 是空指针

​	同所有边界检查函数，`fopen_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。

**参数**

| filename  | -    | 关联到文件系统的文件名                                       |
| --------- | ---- | ------------------------------------------------------------ |
| mode      | -    | 确定访问模式的空终止字符串[文件访问模式](https://zh.cppreference.com/w/c/io/fopen#.E6.96.87.E4.BB.B6.E8.AE.BF.E9.97.AE.E6.A0.87.E8.AE.B0) |
| streamptr | -    | 指向存储函数结果的指针的指针（输出参数）                     |

### 文件访问标记

|                     文件访问 模式字符串                      |   含义   |      解释       | 若文件已存在的动作 | 若文件不存在的动作 |
| :----------------------------------------------------------: | :------: | :-------------: | :----------------: | :----------------: |
|                            `"r"`                             |    读    | 打开文件以读取  |       从头读       |      打开失败      |
|                            `"w"`                             |    写    | 创建文件以写入  |      销毁内容      |     创建新文件     |
|                            `"a"`                             |   后附   |   后附到文件    |      写到结尾      |     创建新文件     |
|                            `"r+"`                            |  读扩展  | 打开文件以读/写 |       从头读       |        错误        |
|                            `"w+"`                            |  写扩展  | 创建文件以读/写 |      销毁内容      |     创建新文件     |
|                            `"a+"`                            | 后附扩展 | 打开文件以读/写 |      写到结尾      |     创建新文件     |
| 可以可选地指定文件访问模式标记 `"b"` 来以二进制模式打开文件。此标在 POSIX 上没有效果，而在 Windows 系统上，它禁用了对 ``'\n'`` 和 `'**\x1A**'` 特殊处理。 在附加文件访问模式下，数据被写入到文件尾，而不考虑文件位置指示器的当前位置。 |          |                 |                    |                    |
| 如果模式不是以上所列字符串之一，则其行为未定义。一些实现会定义额外支持的模式（比如 [Windows](https://docs.microsoft.com/en-us/cpp/c-runtime-library/reference/fopen-wfopen)）。 |          |                 |                    |                    |
| 在更新模式（`'+'`）中，输入和输出均可进行，然而输出不应直接紧随输入，而中间无对 [fflush](https://zh.cppreference.com/w/c/io/fflush)、[fseek](https://zh.cppreference.com/w/c/io/fseek)、[fsetpos](https://zh.cppreference.com/w/c/io/fsetpos) 或 [rewind](https://zh.cppreference.com/w/c/io/rewind) 的调用，且输入不应直接紧随输出，而中间无对 [fseek](https://zh.cppreference.com/w/c/io/fseek)、[fsetpos](https://zh.cppreference.com/w/c/io/fsetpos) 或 [rewind](https://zh.cppreference.com/w/c/io/rewind) 的调用，除非输入操作遇到文件尾。在更新模式中，允许各实现在即便指定了文本模式时仍使用二进制模式。 |          |                 |                    |                    |
| 文件访问模式标记 `"x"` 可以可选地后附于 `"w"` 或 `"w+"` 指定符。若文件存在，则此标记强制函数失败，而不重写它。(C11) |          |                 |                    |                    |
| 使用 fopen_s 或 freopen_s 时，任何以 `"w"` 或 `"a"` 创建的文件的文件访问许可均禁止其他用户访问它。文件访问模式标签 `"u"` 可以可选地前附于任何以 `"w"` 或 `"a"` 开始的指定符，以启用默认的 **fopen** 许可。(C11) |          |                 |                    |                    |

**返回值**

1） 若成功，则返回指向新文件流的指针。流为完全缓冲，除非 `filename` 表示一个交互设备。错误时，返回空指针。 [POSIX 要求](http://pubs.opengroup.org/onlinepubs/9699919799/functions/fopen.html)此情况下必须设置 [errno](https://zh.cppreference.com/w/c/error/errno) 。

2） 若成功，则返回零并将新文件流指针写入 `*streamptr` 。错误时，返回非零错误码并将空指针写入 `*streamptr` （除非 `streamptr` 自身也是空指针）。

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

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.5.3 The fopen function （第 223-224 页）

  - K.3.5.2.1 The fopen_s function （第 428-429 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.5.3 The fopen function （第 305-306 页）

  - K.3.5.2.1 The fopen_s function （第 588-590 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.5.3 The fopen function （第 271-272 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.5.3 The fopen function

**参阅**

| [fclose<br />](https://zh.cppreference.com/w/c/io/fclose)  | 关闭文件 (函数)                   |
| ------------------------------------------------------------ | --------------------------------- |
| [fflush<br />](https://zh.cppreference.com/w/c/io/fflush)  | 将输出流与实际文件同步 (函数)     |
| [freopen <br />freopen_s (C11)<br />](https://zh.cppreference.com/w/c/io/freopen) | 以不同名称打开既存的文件流 (函数) |
| **fopen** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fopen)** |                                   |





### fopen_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### fprintf

原址：[http://zh.cppreference.com/w/c/io/fprintf](http://zh.cppreference.com/w/c/io/fprintf)

作用：

备注：





### fprintf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### fputc

原址：[http://zh.cppreference.com/w/c/io/fputc](http://zh.cppreference.com/w/c/io/fputc)

作用：

备注：





### fputs

原址：[http://zh.cppreference.com/w/c/io/fputs](http://zh.cppreference.com/w/c/io/fputs)

作用：

备注：





### fread

原址：[http://zh.cppreference.com/w/c/io/fread](http://zh.cppreference.com/w/c/io/fread)

作用：

备注：





### freopen

原址：[http://zh.cppreference.com/w/c/io/freopen](http://zh.cppreference.com/w/c/io/freopen)

作用：

备注：





### freopen_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### fscanf

原址：[http://zh.cppreference.com/w/c/io/fscanf](http://zh.cppreference.com/w/c/io/fscanf)

作用：

备注：





### fscanf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### fseek

原址：[http://zh.cppreference.com/w/c/io/fseek](http://zh.cppreference.com/w/c/io/fseek)

作用：

备注：





### fsetpos

原址：[http://zh.cppreference.com/w/c/io/fsetpos](http://zh.cppreference.com/w/c/io/fsetpos)

作用：

备注：





### ftell

原址：[http://zh.cppreference.com/w/c/io/ftell](http://zh.cppreference.com/w/c/io/ftell)

作用：

备注：





### fwrite

原址：[http://zh.cppreference.com/w/c/io/fwrite](http://zh.cppreference.com/w/c/io/fwrite)

作用：

备注：





### getc

原址：[http://zh.cppreference.com/w/c/io/fgetc](http://zh.cppreference.com/w/c/io/fgetc)

作用：

备注：





### getchar

原址：[http://zh.cppreference.com/w/c/io/getchar](http://zh.cppreference.com/w/c/io/getchar)

作用：

备注：





### gets_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### perror

原址：[http://zh.cppreference.com/w/c/io/perror](http://zh.cppreference.com/w/c/io/perror)

作用：

备注：





### printf

原址：[http://zh.cppreference.com/w/c/io/fprintf](http://zh.cppreference.com/w/c/io/fprintf)

作用：

备注：





### printf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### putc

原址：[http://zh.cppreference.com/w/c/io/fputc](http://zh.cppreference.com/w/c/io/fputc)

作用：

备注：





### putchar

原址：[http://zh.cppreference.com/w/c/io/putchar](http://zh.cppreference.com/w/c/io/putchar)

作用：

备注：





### puts

原址：[http://zh.cppreference.com/w/c/io/puts](http://zh.cppreference.com/w/c/io/puts)

作用：

备注：





### remove

原址：[http://zh.cppreference.com/w/c/io/remove](http://zh.cppreference.com/w/c/io/remove)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int remove( const char *pathname );
```

​	删除 `pathname` 所指向的字符串所标识的文件。

​	若当前有任何进程打开了此文件，则此函数行为是实现定义的。POSIX 系统解链接文件名（目录项），但在该文件仍被任何进程打开，以及仍存在指向该文件的硬链接时，不回收它所使用的文件系统空间。Windows 不允许在这种情况下删除该文件。

**参数**

| pathname | -    | 指向空终止字符串的指针，字符串含标识待删除文件的路径 |
| -------- | ---- | ---------------------------------------------------- |
|          |      |                                                      |

**返回值**

​	成功时为 `0`，错误时为非零值。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.4.1 The remove function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.4.1 The remove function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.4.1 The remove function （第 302 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.4.1 The remove function （第 268 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.4.1 The remove function

**参阅**

| [rename<br />](https://zh.cppreference.com/w/c/io/rename)  | 重命名文件 (函数) |
| ------------------------------------------------------------ | ----------------- |
| **remove** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/remove)** |                   |





### rename

原址：[http://zh.cppreference.com/w/c/io/rename](http://zh.cppreference.com/w/c/io/rename)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int rename( const char* old_filename, const char* new_filename );
```

​	更改文件的文件名。该文件以 `old_filename` 所指向的字符串标识。新文件名以 `new_filename` 所指向的字符串标识。

​	若 `new_filename` 存在，则行为是实现定义的。

**参数**

| old_filename | -    | 指向包含标识要重命名的文件的路径的空终止字符串的指针 |
| ------------ | ---- | ---------------------------------------------------- |
| new_filename | -    | 指向包含文件新路径的空终止字符串的指针               |

**返回值**

​	成功时为 `0` ，失败时为非零值。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.4.2 The rename function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.4.2 The rename function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.4.2 The rename function （第 302-303 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.4.2 The rename function （第 268-269 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.4.2 The rename function

**参阅**

| [remove<br />](https://zh.cppreference.com/w/c/io/remove)  | 删除文件 (函数) |
| ------------------------------------------------------------ | --------------- |
| **rename** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/rename)** |                 |





### rewind

原址：[http://zh.cppreference.com/w/c/io/rewind](http://zh.cppreference.com/w/c/io/rewind)

作用：

备注：





### scanf

原址：[http://zh.cppreference.com/w/c/io/fscanf](http://zh.cppreference.com/w/c/io/fscanf)

作用：

备注：





### scanf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### setbuf

原址：[http://zh.cppreference.com/w/c/io/setbuf](http://zh.cppreference.com/w/c/io/setbuf)

作用：

备注：





### setvbuf

原址：[http://zh.cppreference.com/w/c/io/setvbuf](http://zh.cppreference.com/w/c/io/setvbuf)

作用：

备注：





### snprintf

原址：[http://zh.cppreference.com/w/c/io/fprintf](http://zh.cppreference.com/w/c/io/fprintf)

作用：

备注：





### snprintf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### sprintf

原址：[http://zh.cppreference.com/w/c/io/fprintf](http://zh.cppreference.com/w/c/io/fprintf)

作用：

备注：





### sprintf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### sscanf

原址：[http://zh.cppreference.com/w/c/io/fscanf](http://zh.cppreference.com/w/c/io/fscanf)

作用：

备注：





### sscanf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### tmpfile

原址：[http://zh.cppreference.com/w/c/io/tmpfile](http://zh.cppreference.com/w/c/io/tmpfile)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
FILE *tmpfile( void );// (1)
errno_t tmpfile_s( FILE* restrict* restrict streamptr );// (2)(C11 起)
```

1） 创建并打开一个临时文件。该文件作为二进制文件、更新模式（如同为 [fopen](https://zh.cppreference.com/w/c/io/fopen) 以 `"wb+"` 模式）打开。该文件的文件名保证在文件系统中唯一。至少可以在程序的生存期内能打开 [TMP_MAX](https://zh.cppreference.com/w/c/io) 个文件（此极限可能与 [tmpnam](https://zh.cppreference.com/w/c/io/tmpnam) 共享，并可能为 [FOPEN_MAX](https://zh.cppreference.com/w/c/io) 所进一步限制）。

2） 同 (1)，但至少可以打开 TMP_MAX_S 个文件（此极限可能与 tmpnam_s 共享），而若 `streamptr` 为空指针，则调用当前安装的[制约处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)函数。

​	此函数创建的临时文件在程序正常退出时被关闭并删除。它在程序异常终止时是否被删除是实现定义的。

**参数**

1） （无）

2） 指向此函数调用将要更新的指针的指针

**返回值**

1） 指向与文件关联的文件流的指针，或若出现错误则为空指针。

2） 若成功创建并打开文件则为零，若未创建或打开文件，或若 `streamptr` 为空指针则为非零。另外，成功时存储指向关联文件流的指针到 `*streamptr`，而错误时存储空指针值到 `*streamptr`。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.4.3 The tmpfile function （第 TBD 页）

  - K.3.5.1.1 The tmpfile_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.4.3 The tmpfile function （第 222 页）

  - K.3.5.1.1 The tmpfile_s function （第 427 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.4.3 The tmpfile function （第 303 页）

  - K.3.5.1.1 The tmpfile_s function （第 586-587 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.4.3 The tmpfile function （第 269 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.4.3 The tmpfile function

**参阅**

| [tmpnam <br />tmpnam_s (C11)<br />](https://zh.cppreference.com/w/c/io/tmpnam) | 返回唯一的文件名 (函数) |
| ------------------------------------------------------------ | ----------------------- |
| **tmpfile** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/tmpfile)** |                         |





### tmpfile_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### tmpnam

原址：[http://zh.cppreference.com/w/c/io/tmpnam](http://zh.cppreference.com/w/c/io/tmpnam)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
char *tmpnam( char *filename );// (1)
errno_t tmpnam_s(char *filename_s, rsize_t maxsize);// (2)(C11 起)
#define TMP_MAX        /* 未指明 */
#define TMP_MAX_S      /* 未指明 */// (C11 起)
#define L_tmpnam       /* 未指明 */
#define L_tmpnam_s     /* 未指明 */// (C11 起)
```

1） 创建独有的合法文件名（长度不长于 [L_tmpnam](https://zh.cppreference.com/w/c/io)）并将它存储于 `filename` 所指向的字符串。此函数足以生成至多 [TMP_MAX](https://zh.cppreference.com/w/c/io) 个独有文件名，但它们中的一部分甚至全部可能正在文件系统中使用，从而不适合作为返回值。

2） 同 (1)，但至多可以创建 TMP_MAX_S 个长度不长于 L_tmpnam_s 的文件名，而且在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `filename_s` 是空指针
  - `maxsize` 大于 `RSIZE_MAX`
  - `maxsize` 小于生成文件名字符串的长度

​	`tmpnam` 和 `tmpnam_s` 修改静态状态（可能会在这些函数间共享），而且不要求是线程安全的。

**参数**

| filename   | -    | 指向足以保有至少 [L_tmpnam](https://zh.cppreference.com/w/c/io) 字节的字符数组的指针，将以数组为结果缓冲区。若传递空指针，则返回指向内部静态缓冲区的指针。 |
| ---------- | ---- | ------------------------------------------------------------ |
| filename_s | -    | 指向足以保有至少 L_tmpnam_s 字节的字符数组的指针，将以数组为结果缓冲区。 |
| maxsize    | -    | 允许函数写入的最大字节数（典型地为 `filename_s` 数组的大小）。 |

**返回值**

1） 若 `filename` 不是空指针则为 `filename` 。否则为指向内部静态缓冲区的指针。若不能生成适合的文件名，则返回空指针。

2） 成功时返回零并将文件名写入 `filename_s` 。失败时，返回非零并将空字符写入 `filename_s[0]` （仅若 `filename_s` 非空且 `maxsize` 非零且不大于 RSIZE_MAX ）。

**注解**

​	尽管 `tmpnam` 所生成的文件名难以猜测，却可能是另一个进程在 `tmpnam` 返回的时刻和此函程序试图使用返回的名称创建文件之间创建的文件的名称。标准函数 [tmpfile](https://zh.cppreference.com/w/c/io/tmpfile) 和 POSIX 函数 [`mkstemp`](https://pubs.opengroup.org/onlinepubs/9699919799/functions/mkdtemp.html) 无此问题（仅使用 C 标准库创建一个独有的目录仍然要求使用 `tmpnam` ）。

​	POSIX 系统额外定义名称类似的函数 `<code>tempnam`</code> ，它提供对目录的选择（默认是可选定义的宏 `<code>P_tmpdir`</code> ）。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.4.4 The tmpnam function （第 TBD 页）

  - K.3.5.1.2 The tmpnam_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.4.4 The tmpnam function （第 222 页）

  - K.3.5.1.2 The tmpnam_s function （第 427-428 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.4.4 The tmpnam function （第 303-304 页）

  - K.3.5.1.2 The tmpnam_s function （第 587-588 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.4.4 The tmpnam function （第 269-270 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.4.4 The tmpnam function

**参阅**

| [tmpfile <br />tmpfile_s (C11)<br />](https://zh.cppreference.com/w/c/io/tmpfile) | 返回指向临时文件的指针 (函数) |
| ------------------------------------------------------------ | ----------------------------- |
| **tmpnam** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/tmpnam)** |                               |





### tmpnam_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### ungetc

原址：[http://zh.cppreference.com/w/c/io/ungetc](http://zh.cppreference.com/w/c/io/ungetc)

作用：

备注：





### vfprintf

原址：[http://zh.cppreference.com/w/c/io/vfprintf](http://zh.cppreference.com/w/c/io/vfprintf)

作用：

备注：





### vfprintf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### vfscanf

原址：[http://zh.cppreference.com/w/c/io/vfscanf](http://zh.cppreference.com/w/c/io/vfscanf)

作用：

备注：





### vfscanf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### vprintf

原址：[http://zh.cppreference.com/w/c/io/vfprintf](http://zh.cppreference.com/w/c/io/vfprintf)

作用：

备注：





### vprintf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### vscanf

原址：[http://zh.cppreference.com/w/c/io/vfscanf](http://zh.cppreference.com/w/c/io/vfscanf)

作用：

备注：





### vscanf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### vsnprintf

原址：[http://zh.cppreference.com/w/c/io/vfprintf](http://zh.cppreference.com/w/c/io/vfprintf)

作用：

备注：





### vsnprintf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### vsprintf

原址：[http://zh.cppreference.com/w/c/io/vfprintf](http://zh.cppreference.com/w/c/io/vfprintf)

作用：

备注：





### vsprintf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### vsscanf

原址：[http://zh.cppreference.com/w/c/io/vfscanf](http://zh.cppreference.com/w/c/io/vfscanf)

作用：

备注：





### vsscanf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：







