
+++
title = "<stdio.h>"
date = 2025-04-24T22:16:01+08:00
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

类型

| 在标头 `<stdio.h>` 定义                                   |                                                              |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| [FILE<br />](https://zh.cppreference.com/w/c/io/FILE)     | 对象类型，能够保存控制 C I/O 流所需的全部信息 (typedef)      |
| [fpos_t<br />](https://zh.cppreference.com/w/c/io/fpos_t) | 非数组完整对象类型，足以唯一指定文件的位置和多字节解析状态 (typedef) |

预定义标准流

| 在标头 `<stdio.h>` 定义                                    |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [stdin<br />stdout<br />stderr<br />](https://zh.cppreference.com/w/c/io/std_streams) | 与标准输入流关联的 `FILE*` 类型表达式 与标准输出流关联的 `FILE*` 类型表达式 与标准错误输出流关联的 `FILE*` 类型表达式 (宏常量) |

函数

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

宏常量

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
​	[`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 头文件提供了通用的文件操作支持，并提供了具有窄字符输入/输出功能的函数。

​	[`<wchar.h>`](https://zh.cppreference.com/w/c/header/wchar) 头文件提供了具有宽字符输入/输出功能的函数。

​	I/O 流由 **FILE** 类型的对象表示，该对象只能通过 `FILE*` 类型的指针访问及操作。每个流都与外部的物理设备（文件、标准输入流、打印机、序列端口等）相关联。

类型

| 在标头 `<stdio.h>` 定义                                   |                                                              |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| [FILE<br />](https://zh.cppreference.com/w/c/io/FILE)     | 对象类型，能够保存控制 C I/O 流所需的全部信息 (typedef)      |
| [fpos_t<br />](https://zh.cppreference.com/w/c/io/fpos_t) | 非数组完整对象类型，足以唯一指定文件的位置和多字节解析状态 (typedef) |

预定义标准流

| 在标头 `<stdio.h>` 定义                                    |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [stdin<br />stdout<br />stderr<br />](https://zh.cppreference.com/w/c/io/std_streams) | 与标准输入流关联的 `FILE*` 类型表达式 与标准输出流关联的 `FILE*` 类型表达式 与标准错误输出流关联的 `FILE*` 类型表达式 (宏常量) |

函数

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

宏常量

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





### rsize_t

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### size_t

原址：[http://zh.cppreference.com/w/c/types/size_t](http://zh.cppreference.com/w/c/types/size_t)

作用：

备注：
```c
// 在标头 <stddef.h> 定义
// 在标头 <stdio.h> 定义
// 在标头 <stdlib.h> 定义
// 在标头 <string.h> 定义
// 在标头 <time.h> 定义
// 在标头 <uchar.h> 定义
// 在标头 <wchar.h> 定义
typedef /* 由实现定义 */ size_t;
```

​	`size_t` 是 [offsetof](https://zh.cppreference.com/w/c/types/offsetof)、[`<izeo>`](https://zh.cppreference.com/w/c/language/sizeof) 和 `_Alignof`(C23 前)`alignof`(C23 起) 的结果的无符号整数类型，定义取决于[数据模型](https://zh.cppreference.com/w/c/language/arithmetic_types#.E6.95.B0.E6.8D.AE.E6.A8.A1.E5.9E.8B)。

​	`size_t` 的位宽不小于 16。 (C99 起)

**注解**

​	`size_t` 能存储理论上可行的任何类型（包括数组）对象的最大大小。

​	`size_t` 通常用于数组下标和循环计数。将如 `unsigned int` 的其他类型用作数组下标的的程序，可能譬如在 64 位系统上，当下标超过 [UINT_MAX](https://zh.cppreference.com/w/c/types/limits) 时，或若其依赖 32 位模算术时失败。

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

​	可能的输出：

```txt
sum = 5050
size = 400
SIZE_MAX = 18446744073709551615
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.19 Common definitions <stddef.h> （第 TBD 页）

  - 7.20.3 Limits of other integer types （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.19 Common definitions <stddef.h> （第 211 页）

  - 7.20.3 Limits of other integer types （第 215 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.19 Common definitions <stddef.h> （第 288 页）

  - 7.20.3 Limits of other integer types （第 293 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.17 Common definitions <stddef.h> （第 253 页）

  - 7.18.3 Limits of other integer types （第 258 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.1.6 Common definitions <stddef.h>

**参阅**

| [ptrdiff_t<br />](https://zh.cppreference.com/w/c/types/ptrdiff_t) | 两个指针相减返回的有符号整数类型 (typedef)      |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [offsetof<br />](https://zh.cppreference.com/w/c/types/offsetof) | 从结构体类型的起始到指定成员的字节偏移 (宏函数) |
| **size_t** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/size_t)** |                                                 |






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





### `__STDC_VERSION_STDIO_H__`

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

**文件访问标记**

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
```c
// 在标头 <stdio.h> 定义
// (1)
int printf( const char*          format, ... );// (C99 前)
int printf( const char* restrict format, ... );// (C99 起)
// (2)
int fprintf( FILE*          stream, const char*          format, ... );// (C99 前)
int fprintf( FILE* restrict stream, const char* restrict format, ... );// (C99 起)
// (3)
int sprintf( char*          buffer, const char*          format, ... );// (C99 前)
int sprintf( char* restrict buffer, const char* restrict format, ... );// (C99 起)
int snprintf( char* restrict buffer, size_t bufsz,
              const char* restrict format, ... );// (4)(C99 起)
int printf_s( const char* restrict format, ... );// (5)(C11 起)
int fprintf_s( FILE* restrict stream, const char* restrict format, ... );// (6)(C11 起)
int sprintf_s( char* restrict buffer, rsize_t bufsz,
               const char* restrict format, ... );// (7)(C11 起)
int snprintf_s( char* restrict buffer, rsize_t bufsz,
                const char* restrict format, ... );// (8)(C11 起)
```

​	从给定位置加载数据，转换为字符串等价物，并写结果到各种池。

1） 将结果写入输出流 [stdout](https://zh.cppreference.com/w/c/io)。

2） 将结果写入输出流 `stream`。

3） 将结果写入字符串 `buffer`。如果所写入的字符串（加上终止空字符）超出由 `buffer` 所指向的数组的大小，则行为未定义。

4） 将结果写入字符串 `buffer`。至多写 `bufsz - 1` 个字符。产生的字符串会以空字符终止，除非 `bufsz` 为零。若 `bufsz` 为零，则不写入任何内容，且 `buffer` 可以是空指针，然而依旧计算返回值（会写入的字符数，不包含空终止符）并返回。

5-8) 同 (1-4) ，除了在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `format` 中存在转换说明符 `%n`
  - 任何一个对应 `%s` 的参数是空指针
  - `stream`、`format` 或 `buffer` 是空指针
  - `bufsz` 为零或大于 RSIZE_MAX
  - 在任何一个字符串及字符转换说明符中出现编码错误
  - （仅对于 `sprintf_s` ）存储于 `buffer` 的字符串（包括尾随空字符）长度将超出 `bufsz`

**参数**

| stream | -    | 要写入的输出文件流                                           |
| ------ | ---- | ------------------------------------------------------------ |
| buffer | -    | 指向要写入的字符串的指针                                     |
| bufsz  | -    | 最多会写入 `bufsz - 1` 个字符，再加空终止符                  |
| format | -    | 指向指定数据转换方式的空终止多字节字符串的指针               |
| ...    | -    | 指定要打印数据的参数。若任何[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)后的参数不拥有对应转换说明所期待的类型（期待类型是提升后的类型或者提升后类型的兼容类型），或若参数数量少于 `format` 的要求，则行为未定义。若有多于 `format` 要求的参数，则求值并忽略多出的参数。 |

​	**格式**字符串由普通多字节字符（除了 `%`）和转换指示构成，前者被不改动地复制到输出流。每个转换指示均拥有下列格式：

  - 引入的 `%` 字符。

  - (可选) 一或多个修改转换行为的标志：
  - `-`：转换结果在域内左对齐（默认为右对齐）。
  - `+`：有符号转换的符号始终前置于转换结果（默认仅当结果为负时前置负号）。
  - *空格*：如果有符号转换的结果不以符号开始，或为空，那么前置空格于结果。存在 `+` 标志时忽略*空格*。
  - `#`：进行*替用形式* ﻿的转换。确切的效果见下表，其他情况下行为未定义。
  - `0`：对于整数和浮点数转换，使用前导零代替*空格* ﻿字符填充字段。对于整数，如果显式指定了精度，那么忽略此标志。对于其他转换，使用此标志导致未定义行为。存在 `-` 标志时忽略 `0`。

  - (可选) 整数或 `*`，指定最小字段宽度。如果有要求，那么结果会以*空格* ﻿字符（默认情况）填充，在右对齐时于左，左对齐时于右。使用 `*` 的情况下，以一个额外的 `int` 类型实参指定宽度。如果实参值是负数，那么它导致指定 `-` 标志和正的字段宽度。（注意：这是最小宽度：值决不会被截断）。

  - (可选) 后随整数或 `*` 或两者皆无的 `.`，指示转换的*精度* ﻿。在使用 `*` 的情况下，*精度* ﻿由额外的 `int` 类型的实参指定。如果此实参的值是负数，那么它被忽略。如果既不使用数字也不使用 `*`，那么精度采用零。*精度* ﻿的确切效果见下表。

  - (可选) 指定实参大小的*长度修饰符*（其与格式指示符组合，指定对应实参的类型）。

  - 转换格式指示符

​	下列格式指示符可用：

|                          转换指示符                          |                             解释                             | 期望的实参类型  |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :-------------: | :--------------: | :------------: | :-------------: | :------------------: | :----------------------------------------------------------: | :----------------------------------------------------: | :----------------------------------------------------------: | ------------- |
|                         长度修饰符→                          |                              hh                              |        h        |        无        |       l        |       ll        |          j           |                              z                               |                           t                            |                              L                               |               |
|                       仅从 C99 起可用→                       |                              是                              |                 |                  |                |       是        |          是          |                              是                              |                           是                           |                                                              |               |
|                             `%`                              | ​	写入字面的 `%`。完整的转换指示必须是 `%%`。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `c`                              | ​	写入**单个字符**。实参首先被转换成 `unsigned char`。如果使用 **l** 修饰符，那么实参首先被转换成字符串，如同通过以 `wchar_t[2]` 实参使用 **%ls**。 |     不适用      |      不适用      |     `int`      |     wint_t      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `s`                              | ​	写入**字符串**。实参必须是指向字符数组首元素的指针。*精度* ﻿指定写入最大的字符数。如果没有指定*精度*，那么写每个字节直到而不含首个空终止符。如果使用 **l** 指示符，那么实参必须是指向 `wchar_t` 数组首元素的指针，数组会被转换成 `char` 数组，如同通过以零初始化转换状态调用 [wcrtomb](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb)。 |     不适用      |      不适用      |    `char*`     |   `wchar_t*`    |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                           `d` `i`                            | ​	转换**有符号整数**为十进制表示 *[-]dddd*。*精度* ﻿指定出现的最小数位数。默认精度是 `1`。如果被转换的值和精度都是 `0`，那么转换结果无字符。对于 `z` 修饰符，期望的实参类型是 [size_t](https://zh.cppreference.com/w/c/types/size_t) 的有符号版本。 |  `signed char`  |     `short`      |     `int`      |     `long`      |     `long long`      |  [intmax_t](https://zh.cppreference.com/w/c/types/integer)   |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) | 不适用        |
|                             `o`                              | ​	转换**无符号整数**为八进制表示 *oooo*。*精度* ﻿指定出现数字的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现* ﻿中精度按需增加，以写入一个前导零。在此情况下如果被转换值和精度都是 `0`，那么写入单个 `0`。 | `unsigned char` | `unsigned short` | `unsigned int` | `unsigned long` | `unsigned long long` |  [uintmax_t](https://zh.cppreference.com/w/c/types/integer)  | [size_t](https://zh.cppreference.com/w/c/types/size_t) | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) 的无符号版本 | 不适用        |
|                           `x` `X`                            | ​	转换**无符号整数**为十六进制表示 *hhhh*。`x` 转换使用字母 `abcdef`。`X` 转换使用 `ABCDEF`。*精度*指定出现数位的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现中* ﻿如果被转换值非零，那么结果有 `0x` 或 `0X` 前缀。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                             `u`                              | ​	转换**无符号整数**为十进制表示 *dddd*。*精度* ﻿指定出现的数位最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                        `f` `F` (C99)                         | ​	转换**浮点数**为 *[-]ddd.ddd* 样式的十进制记法。*精度* ﻿指定小数点字符后出现的确切数位数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |    `double`    | `double` (C99)  |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | `long double` |
|                           `e` `E`                            | ​	转换**浮点数**为十进制指数记法。`e` 转换样式使用 *[-]d.ddd* ﻿`e`*±dd*。`E` 转换样式使用 *[-]d.ddd* ﻿`E`*±dd*。指数至少含两个数位，仅当需要时才使用更多数位。如果值是 `0`，那么指数也是 `0`。*精度* ﻿指定小数点字符后出现数位的最小个数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                 `a` `A`​	(C99)                 | ​	转换**浮点数**为十六进制指数记法。`a` 转换样式使用 *[-]* ﻿`0x`*h.hhh* ﻿`p`*±d*。`A` 转换样式使用 *[-]* ﻿`0X`*h.hhh* ﻿`P`*±d*。如果参数是正规化的浮点数，那么首个十六进制数位非 `0`。如果值是 `0`，那么指数也是 `0`。*精度*指定小数点字符后出现数位的最小个数。默认精度足以精确表示该值。在*替用实现*中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                           `g` `G`                            | ​	转换**浮点数**为十进制小数或十进制指数记法，依赖于值和*精度*。`g` 转换样式将进行带样式 `e` 或 `f` 的转换。`G` 转换样式将进行带样式 `E` 或 `f`(C99 前)`F`(C99 起) 的转换。令 `P` 等于精度，如果它非零，那么精度在未指定时是 `6`，如果精度是 `0` 那么等于 `1`。然后，如果带样式 `E` 的转换会有指数 `X`，那么：如果 *P > X ≥ −4*，那么转换带 `f` 或 `F`(C99 起) 风格，及精度 *P − 1 − X*。否则，转换带 `e` 或 `E` 风格，及精度 *P − 1*。除非要求*替用表示*，否则末尾零会被移除，且在不留下小数部分时小数点也会被移除。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                             `n`                              | ​	返回对函数的此调用迄今为止**写入的字符数**。结果被*写入* ﻿到实参所指向的值。该指示不可含有任何*标签*、*域宽* ﻿或*精度*。对于 `z` 修饰符，实参类型是 `S*`，其中 `S` 是 `[size_t](http://zh.cppreference.com/w/c/types/size_t)` 的有符号版本。 | `signed char*`  |     `short*`     |     `int*`     |     `long*`     |     `long long*`     | [intmax_t](https://zh.cppreference.com/w/c/types/integer)`*` |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)`*` | 不适用        |
|                             `p`                              |          写入定义了**指针**的由实现定义的字符序列。          |     不适用      |      不适用      |    `void*`     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             注解                             |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| ​	浮点数转换函数转换无穷大为 `inf` 或 `infinity`。由实现定义使用其中哪一个。​	非数转换成 `nan` 或 `nan(*char_sequence*)`。由实现定义使用其中哪一个。​	转换 `F`、`E`、`G`、`A` 替代上面输出 `INF`、`INFINITY`、`NAN`。​	用于打印 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short` 的转换指示符实际期待[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)后的类型，但在打印前会转换到 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short`。直接向函数传递这些类型的值是安全的，因为在调用变参数函数时会发生提升。​	定宽字符类型（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确转换指示在标头 [`<inttypes.h>`](https://zh.cppreference.com/w/c/header/inttypes) 定义（尽管 [PRIdMAX](https://zh.cppreference.com/w/c/types/integer)、[PRIuMAX](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。​	内存写入转换指示符 `%n` 是安全漏洞的常见目标，这里格式字符串依赖用户输入，而有边界检查的 `printf_s` 系列函数不支持此转换指示符(C11 起)。​	在每个转换指示符的行动后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许于同一变量多次存入 `%n` 的结果，并在同一此调用中打印出先前以 `%n` 存储的值。​	如果转换指示非法，那么行为未定义。 |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |

**返回值**

1,2) 传输到输出流的字符数，或若出现输出错误或编码错误（对于字符串和字符转换说明符）则为负值。

3） 写入到 `buffer` 的字符数（不计空终止字符），或若输出错误或编码错误（对于字符串和字符转换说明符）发生则为负值。

4） 假如忽略 `bufsz` 则本应写入到 `buffer` 的字符数（不计空终止字符），或若出现输出错误或编码错误（对于字符串和字符转换说明符）则为负值。

5,6) 传输到输出流的字符数，或若出现输出错误、运行时制约违规错误或编码错误则为负值。

7） 写入到 `buffer` 的字符数，不计空终止字符（只要 `buffer` 不是空指针且 `bufsz` 非零且不大于 RSIZE_MAX，就写入它），在运行时制约违规时为零，而在编码错误时为负值。

8） 假如忽略 `bufsz` 则本应写入 `buffer` 的字符数的，不包含空终止字符（只要 `buffer` 不是空指针而 `bufsz` 非零且不大于 RSIZE_MAX，就写入它），或若出现输出错误、运行时制约违规错误或编码错误则为负值。

**注解**

​	C 标准及 [POSIX](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fprintf.html) 指定 `sprintf` 及其变体的行为在参数与目标缓冲区重叠时未定义。示例：

```
sprintf(dst, "%s and %s", dst, t); // <- 有错：未定义行为
```

​	[POSIX 规定](http://pubs.opengroup.org/onlinepubs/9699919799/functions/fprintf.html)在错误时设置 [errno](https://zh.cppreference.com/w/c/error/errno)。它还规定额外的转换指示，最值得注意的是对实参重排序的支持（紧随 `%` 后的 `n$` 指示第 `n` 个实参）。

​	以零为 `bufsz` 和空指针为 `buffer` 调用 `snprintf` 可用于决定包含输出的缓冲区大小：

```
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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.6.1 The fprintf function （第 TBD 页）

  - 7.21.6.3 The printf function （第 TBD 页）

  - 7.21.6.5 The snprintf function （第 TBD 页）

  - 7.21.6.6 The sprintf function （第 TBD 页）

  - K.3.5.3.1 The fprintf_s function （第 TBD 页）

  - K.3.5.3.3 The printf_s function （第 TBD 页）

  - K.3.5.3.5 The snprintf_s function （第 TBD 页）

  - K.3.5.3.6 The sprintf_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.6.1 The fprintf function （第 225-230 页）

  - 7.21.6.3 The printf function （第 236 页）

  - 7.21.6.5 The snprintf function （第 237 页）

  - 7.21.6.6 The sprintf function （第 237 页）

  - K.3.5.3.1 The fprintf_s function （第 430 页）

  - K.3.5.3.3 The printf_s function （第 432 页）

  - K.3.5.3.5 The snprintf_s function （第 432-433 页）

  - K.3.5.3.6 The sprintf_s function （第 433 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.6.1 The fprintf function （第 309-316 页）

  - 7.21.6.3 The printf function （第 324 页）

  - 7.21.6.5 The snprintf function （第 325 页）

  - 7.21.6.6 The sprintf function （第 325-326 页）

  - K.3.5.3.1 The fprintf_s function （第 591 页）

  - K.3.5.3.3 The printf_s function （第 593-594 页）

  - K.3.5.3.5 The snprintf_s function （第 594-595 页）

  - K.3.5.3.6 The sprintf_s function （第 595-596 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.6.1 The fprintf function （第 274-282 页）

  - 7.19.6.3 The printf function （第 290 页）

  - 7.19.6.5 The snprintf function （第 290-291 页）

  - 7.19.6.6 The sprintf function （第 291 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.6.1 The fprintf function

  - 4.9.6.3 The printf function

  - 4.9.6.5 The sprintf function

**参阅**

| [wprintf (C95)<br />fwprintf (C95)<br />swprintf (C95)<br />wprintf_s (C95)<br />fwprintf_s (C95)<br />swprintf_s (C95)<br />snwprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fwprintf) | 打印格式化宽字符输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [vprintf <br />vfprintf <br />vsprintf <br />vsnprintf (C99)<br />vprintf_s (C99)<br />vfprintf_s (C11)<br />vsprintf_s (C11)<br />vsnprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/vfprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 使用可变参数列表 (函数) |
| [fputs<br />](https://zh.cppreference.com/w/c/io/fputs)    | 将一个字符串写入文件流 (函数)                                |
| [scanf <br />fscanf <br />sscanf <br />scanf_s (C11)<br />fscanf_s (C11)<br />sscanf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fscanf) | 从[stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 (函数) |
| **printf, fprintf, sprintf, snprintf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fprintf)** |                                                              |





### fprintf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### fputc

原址：[http://zh.cppreference.com/w/c/io/fputc](http://zh.cppreference.com/w/c/io/fputc)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int fputc( int ch, FILE *stream );
int putc( int ch, FILE *stream );
```

​	写入字符 `ch` 到给定输出流 `stream` 。 `putc()` 可以实现为宏并对 `stream` 求值超过一次，故对应的参数决不应是有副效应的表达式。

​	在内部，在写入前将字符转换为 `unsigned char` 。

**参数**

| ch     | -    | 要写入的字符 |
| ------ | ---- | ------------ |
| stream | -    | 输出流       |

**返回值**

​	成功时，返回被写入字符。

​	失败时，返回 [EOF](https://zh.cppreference.com/w/c/io) 并设置 stream 上的*错误*指示器（见 [ferror()](https://zh.cppreference.com/w/c/io/ferror) ）。

**示例**

​	显示带错误检查的 `putc`

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    int ret_code = 0;
    for (char c = 'a'; (ret_code != EOF) && (c != 'z'); c++)
        ret_code = putc(c, stdout);
 
    // 测试是否抵达 EOF。
    if (ret_code == EOF && ferror(stdout))
    {
        perror("putc()");
        fprintf(stderr, "putc() failed in file %s at line # %d\n",
                __FILE__, __LINE__ - 7);
        exit(EXIT_FAILURE);
    }
    putc('\n', stdout);
 
    return EXIT_SUCCESS;
}
```

​	输出：

```txt
abcdefghijklmnopqrstuvwxy
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.7.3 The fputc function （第 TBD 页）

  - 7.21.7.7 The putc function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.7.3 The fputc function （第 TBD 页）

  - 7.21.7.7 The putc function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.7.3 The fputc function （第 331 页）

  - 7.21.7.7 The putc function （第 333 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.7.3 The fputc function （第 297 页）

  - 7.19.7.8 The putc function （第 299 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.7.3 The fputc function

  - 4.9.7.8 The putc function

**参阅**

| [putchar<br />](https://zh.cppreference.com/w/c/io/putchar) | 将一个字符写入 [stdout](https://zh.cppreference.com/w/c/io) (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **fputc, putc** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fputc)** |                                                              |





### fputs

原址：[http://zh.cppreference.com/w/c/io/fputs](http://zh.cppreference.com/w/c/io/fputs)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int fputs( const char*          str, FILE*          stream );// (C99 前)
int fputs( const char* restrict str, FILE* restrict stream );// (C99 起)
```

​	将以NULL结尾的字符串 `str` 的每个字符写入到输出流 `stream`，如同通过重复执行 [fputc](https://zh.cppreference.com/w/c/io/fputc)。

​	不写入 `str` 的终止空字符。

**参数**

| str    | -    | 要写入的空终止字符串 |
| ------ | ---- | -------------------- |
| stream | -    | 输出流               |

**返回值**

​	成功时，返回非负值。

​	失败时，返回 [EOF](https://zh.cppreference.com/w/c/io) 并设置 `stream` 上的*错误*指示器（见 [ferror](https://zh.cppreference.com/w/c/io/ferror)）。

**注解**

​	相关函数 [puts](https://zh.cppreference.com/w/c/io/puts) 后附新换行符到输出，而 `fputs` 写入不修改的字符串。

​	不同的实现返回不同的非负数：一些返回最后写入的字符，一些返回写入的字符数（或若字符串长于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 则为该值），一些简单地非负常量，例如零。

**示例**

```c
#include <stdio.h>
 
int main(void)
{
    int rc = fputs("Hello World", stdout);
 
    if (rc == EOF)
       perror("fputs()"); // POSIX 要求设置 errno
}
```

​	输出：

```txt
Hello World
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.7.4 The fputs function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.7.4 The fputs function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.7.4 The fputs function （第 331-332 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.7.4 The fputs function （第 297 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.7.4 The fputs function

**参阅**

| [printf <br />fprintf <br />sprintf <br />snprintf (C99)<br />printf_s (C99)<br />fprintf_s (C11)<br />sprintf_s (C11)<br />snprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [puts<br />](https://zh.cppreference.com/w/c/io/puts)      | 将一个字符串写入 [stdout](https://zh.cppreference.com/w/c/io) (函数) |
| [fgets<br />](https://zh.cppreference.com/w/c/io/fgets)    | 从文件流获取一个字符串 (函数)                                |
| **fputs** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fputs)** |                                                              |





### fread

原址：[http://zh.cppreference.com/w/c/io/fread](http://zh.cppreference.com/w/c/io/fread)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
size_t fread( void          *buffer, size_t size, size_t count,
              FILE          *stream );// (C99 前)
size_t fread( void *restrict buffer, size_t size, size_t count, 
              FILE *restrict stream );// (C99 起)
```

​	从给定输入流 `stream` 读取至多 `count` 个对象到数组 `buffer` 中，如同以对每个对象调用 `size` 次 [fgetc](https://zh.cppreference.com/w/c/io/fgetc) ，并按顺序存储结果到转译为 `unsigned char` 数组的 `buffer` 中的相继位置。流的文件位置指示器前进读取的字符数。

​	若出现错误，则流的文件位置指示器的结果值不确定。若读入部分的元素，则元素值不确定。

**参数**

| buffer | -    | 指向要读取的数组中首个对象的指针 |
| ------ | ---- | -------------------------------- |
| size   | -    | 每个对象的字节大小               |
| count  | -    | 要读取的对象数                   |
| stream | -    | 读取来源的输入文件流             |

**返回值**

​	成功读取的对象数，若出现错误或文件尾条件，则可能小于 `count` 。

​	若 `size` 或 `count` 为零，则 `fread` 返回零且不进行其他动作。

​	`fread` 不区别文件尾和错误，而调用者必须用 [feof](https://zh.cppreference.com/w/c/io/feof) 和 [ferror](https://zh.cppreference.com/w/c/io/ferror) 鉴别出现者为何。

**示例**

```c
#include <stdio.h>
 
enum { SIZE = 5 };
int main(void)
{
    const double a[SIZE] = {1.0, 2.0, 3.0, 4.0, 5.0};
    printf("Array has size %ld bytes, element size: %ld\n", sizeof a, sizeof *a);
    FILE *fp = fopen("test.bin", "wb"); // 必须用二进制模式
    fwrite(a, sizeof *a, SIZE, fp); // 写 double 的数组
    fclose(fp);
 
    double b[SIZE];
    fp = fopen("test.bin","rb");
    const size_t ret_code = fread(b, sizeof b[0], SIZE, fp); // 读 double 的数组
    if(ret_code == SIZE)
    {
        printf("Array at %p read successfully, contents:\n", (void*)&a);
        for(int n = 0; n != SIZE; ++n)
            printf("%f ", b[n]);
        putchar('\n');
    }
    else // 错误处理
    {
       if (feof(fp))
          printf("Error reading test.bin: unexpected end of file\n");
       else if (ferror(fp))
           perror("Error reading test.bin");
    }
 
    fclose(fp);
}
```

​	可能的输出：

```txt
Array has size 40 bytes, element size: 8
Array at 0x1337f00d6960 read successfully, contents:
1.000000 2.000000 3.000000 4.000000 5.000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.8.1 The fread function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.8.1 The fread function （第 243-244 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.8.1 The fread function （第 335 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.8.1 The fread function （第 301 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.8.1 The fread function

**参阅**

| [scanf <br />fscanf <br />sscanf <br />scanf_s (C11)<br />fscanf_s (C11)<br />sscanf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fscanf) | 从[stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [fgets<br />](https://zh.cppreference.com/w/c/io/fgets)    | 从文件流获取一个字符串 (函数)                                |
| [fwrite<br />](https://zh.cppreference.com/w/c/io/fwrite)  | 写入到文件 (函数)                                            |
| **fread** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fread)** |                                                              |





### freopen

原址：[http://zh.cppreference.com/w/c/io/freopen](http://zh.cppreference.com/w/c/io/freopen)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
// (1)
FILE *freopen( const char *filename, const char *mode,
               FILE *stream );// (C99 前)
FILE *freopen( const char *restrict filename, const char *restrict mode, 
               FILE *restrict stream );// (C99 起)
errno_t freopen_s( FILE *restrict *restrict newstreamptr,
                   const char *restrict filename, const char *restrict mode,

                   FILE *restrict stream );// (2)(C11 起)
```

1） 首先，试图关闭与 `stream` 关联的文件，忽略任何错误。然后，若 `filename` 非空，则试图用 `mode` 打开 `filename` 所指定的文件，如同用 [fopen](https://zh.cppreference.com/w/c/io/fopen) ，然后将该文件与 `stream` 所指向的文件流关联。若 `filename` 为空指针，则函数试图重打开已与 `stream` 关联的文件（此情况下是否允许模式改变是实现定义的）。

2） 同 (1) ，除了以 fopen_s 中的方式处理 `mode` ，并将指向文件流的指针写入 `newstreamptr` ，还在运行时检测下列错误，并调用当前安装的[约束处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)函数：

  - `newstreamptr` 是空指针
  - `stream` 是空指针
  - `mode` 是空指针

**参数**

| filename     | -    | 要关联到文件流的文件名                                       |
| ------------ | ---- | ------------------------------------------------------------ |
| mode         | -    | 确定[文件访问模式](https://zh.cppreference.com/w/c/io/freopen#.E6.96.87.E4.BB.B6.E8.AE.BF.E9.97.AE.E6.A0.87.E8.AE.B0)的空终止字符串 |
| stream       | -    | 要修改的文件流                                               |
| newstreamptr | -    | 指向函数存储结果所用指针的指针（输出参数）                   |

**文件访问标记**

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
| 使用 fopen_s 或 freopen_s 时，任何以 `"w"` 或 `"a"` 创建的文件的文件访问许可均禁止其他用户访问它。文件访问模式标签 `"u"` 可以可选地前附于任何以 `"w"` 或 `"a"` 开始的指定符，以启用默认的 [fopen](https://zh.cppreference.com/w/c/io/fopen) 许可。(C11) |          |                 |                    |                    |

**返回值**

1） 成功时为 `stream` 值的副本，失败时为空指针。

2） 成功时为零（并将 `stream` 值的副本写入 `*newstreamptr` ），失败时为非零（并写入空指针到 `*newstreamptr` ，除非 `newstreamptr` 自身为空指针）。

**注解**

​	`freopen` 是一旦由 I/O 操作或 fwide 建立面向后，改变文件流窄/宽面向的唯一方式。

​	`freopen` 的 Microsoft CRT 版本在 `filename` 为空指针时不支持任何模式更改并将它当作错误（见[文档](https://docs.microsoft.com/en-us/cpp/c-runtime-library/reference/freopen-wfreopen)）。可行的替代方案是非标准函数 [`_setmode()`](https://docs.microsoft.com/en-us/cpp/c-runtime-library/reference/setmode) 。

**示例**

​	下列代码重定向 `stdout` 到文件。

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    puts("stdout is printed to console");
    if (freopen("redir.txt", "w", stdout) == NULL)
    {
       perror("freopen() failed");
       return EXIT_FAILURE;
    }
    puts("stdout is redirected to a file"); // 写入 redir.txt
    fclose(stdout);
    return EXIT_SUCCESS;
}
```

​	输出：

```txt
stdout is printed to console
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.5.4 The freopen function （第 224-225 页）

  - K.3.5.2.2 The freopen_s function （第 429-430 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.5.4 The freopen function （第 307 页）

  - K.3.5.2.2 The freopen_s function （第 590 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.5.4 The freopen function （第 272-273 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.5.4 The freopen function

**参阅**

| [fopen <br />fopen_s (C11)<br />](https://zh.cppreference.com/w/c/io/fopen) | 打开文件 (函数) |
| ------------------------------------------------------------ | --------------- |
| [fclose<br />](https://zh.cppreference.com/w/c/io/fclose)  | 关闭文件 (函数) |
| **freopen** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/freopen)** |                 |





### freopen_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### fscanf

原址：[http://zh.cppreference.com/w/c/io/fscanf](http://zh.cppreference.com/w/c/io/fscanf)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
// (1)
int scanf( const char          *format, ... );// (C99 前)
int scanf( const char *restrict format, ... );// (C99 起)
// (2)
int fscanf( FILE          *stream, const char          *format, ... );// (C99 前)
int fscanf( FILE *restrict stream, const char *restrict format, ... );// (C99 起)
// (3)
int sscanf( const char          *buffer, const char          *format, ... );// (C99 前)
int sscanf( const char *restrict buffer, const char *restrict format, ... );// (C99 起)
int scanf_s(const char *restrict format, ...);// (4)(C11 起)
int fscanf_s(FILE *restrict stream, const char *restrict format, ...);// (5)(C11 起)
int sscanf_s(const char *restrict buffer, const char *restrict format, ...);// (6)(C11 起)
```

​	从各种资源读取数据，按照 `format` 转译，并将结果存储到指定位置。

1） 从 [stdin](https://zh.cppreference.com/w/c/io) 读取数据

2） 从文件流 `stream` 读取数据

3） 从空终止字符串 `buffer` 读取数据。抵达字符串结尾等价于 `fscanf` 的抵达文件尾条件

4-6) 同 (1-3) ，除了 `%c` 、 `%s` 及 `%[` 转换指示符要求二个参数（通常的指针和指示获取用数组大小的 rsize_t 类型的值，在以 %c 读取单个字符时可以为 1 ），并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - 任何指针类型的参数为空指针
  - `format` 、 `stream` 或 `buffer` 为空指针
  - `%c` 、 `%s` 或 `%[` 会写入的字符数，加上空终止字符，要超过提供给这些转换指示符的第二个（ rsize_t ）参数
  - 可选，任何其他可检测错误，例如未知转换指示符

**参数**

| stream | -    | 要读取的输入文件流                       |
| ------ | ---- | ---------------------------------------- |
| buffer | -    | 指向要读取的空终止字符串的指针           |
| format | -    | 指向指定读取输入方式的空终止字符串的指针 |
| ...    | -    | 各接收实参                               |

- 非空白多字节字符，除了 `%`：每个格式字符串中的这种字符处理一个来自输入流的完全相同的字符，或在它与流的下个字符比较不相等时导致函数失败。
- 空白字符：任何格式字符串中的单个空白字符处理所有来自输入的可用连续空白字符（如同通过于循环中调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 确定）。注意，格式字符串中 ``"\n"``、`" "`、`"**\t****\t**"` 或其他空白无区别。
- 转换指示：每个转换指示拥有下列格式：

  - 引入用 `%` 字符

  - (可选) 赋值抑制字符 `*`。如果存在此选项，那么此函数不将结果赋值给任何接收用实参。

  - (可选) 指定*最大字段宽度* ﻿的整数数字（大于零），即函数进行在当前转换指示所指定的转换时，允许处理的最大字符数。注意如果没有提供宽度，那么 `%s` 和 `%[` 可能导致缓冲区溢出。

  - (可选) 指定接收实参大小的*长度修饰符*，即实际目标类型。这影响转换准确性和溢出规则。默认目标类型对每个转换类型有所不同（见下表）。

  - 转换格式指示符。

​	下列格式指示符可用：

|                          转换指示符                          |                             解释                             |           期望的实参类型           |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :--------------------------------: | :----------------------------------: | :------------------------------: | :--------------------------------: | :------------------------------------------: | :----------------------------------------------------------: | :------------------------------------------------------: | :----------------------------------------------------------: | -------------- |
|                         长度修饰符→                          |                              hh                              |                 h                  |                  无                  |                l                 |                 ll                 |                      j                       |                              z                               |                            t                             |                              L                               |                |
|                       仅从 C99 起可用→                       |                              是                              |                                    |                                      |                                  |                 是                 |                      是                      |                              是                              |                            是                            |                                                              |                |
|                             `%`                              |                      匹配字面 `%`。                      |               不适用               |                不适用                |              不适用              |               不适用               |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             `c`                              | ​	匹配一个**字符**或**字符**的序列。如果使用了宽度指示符，那么匹配恰好*宽度*个字符（该实参必须是指向有充足空间的数组的指针）。与 %s 和 %[ 不同，它不会在数组后附加空字符。 |               不适用               |                不适用                |             `char*`              |             `wchar_t*`             |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             `s`                              | ​	匹配非空白字符的序列（一个**字符串**）。如果使用宽度指示符，那么至多匹配*宽度*个字符，或匹配到首个提前出现的空白符前。总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                        `[`*集合* ﻿`]`                         | ​	匹配*集合* ﻿中的字符的一个非空字符序列。如果集合的首字符是 `^`，那么匹配所有不在集合中的字符。如果集合以 `]` 或 `^]` 开始，那么 `]` 字符也会被包含入集合。在扫描集合的非最初位置的字符 `-` 是否可以指示范围，如 `[0-9]`，由实现定义。如果使用宽度指示符，那么最多匹配到*宽度*。总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `d`                              | ​	匹配一个**十进制整数**。该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 `10` 为 `base` 时期望的格式相同。 | `signed char*` 或 `unsigned char*` | `signed short*` 或 `unsigned short*` | `signed int*` 或 `unsigned int*` | `signed long*` 或 `unsigned long*` | `signed long long*` 或 `unsigned long long*` | `[intmax_t](http://zh.cppreference.com/w/c/types/integer)*` 或 `[uintmax_t](http://zh.cppreference.com/w/c/types/integer)*` | `[size_t](http://zh.cppreference.com/w/c/types/size_t)*` | `[ptrdiff_t](http://zh.cppreference.com/w/c/types/ptrdiff_t)*` | 不适用         |
|                             `i`                              | ​	匹配一个**整数**。该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 `0` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `u`                              | ​	匹配一个无符号**十进制整数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `10` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `o`                              | ​	匹配一个无符号**八进制数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `8` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                           `x` `X`                            | ​	匹配一个无符号**十六进制整数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `16` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `n`                              | ​	返回**迄今读取的字符数**。不消耗输出。不增加赋值计数。如果此指示符拥有赋值抑制运算符，那么行为未定义。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|      `a` (C99) `A` (C99) `e` `E` `f` `F` (C99) `g` `G`       | ​	匹配一个**浮点数**。该数的格式与 [strtof](https://zh.cppreference.com/w/c/string/byte/strtof) 期望的格式相同。 |               不适用               |                不适用                |             `float*`             |             `double*`              |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | `long double*` |
|                             `p`                              | ​	匹配定义了一个**指针**的由实现定义的字符序列。`printf` 系列函数使用 `%p` 格式指示符时应该产生同样的序列。 |               不适用               |                不适用                |             `void**`             |               不适用               |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             注解                             |                                                              |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
| ​	对于每个 `n` 以外的转换指示符，不超过任何指定字段宽度，且要么恰好是转换指示符所期待，要么是其所期待的前缀的最长输入字符序列，即是从流中消耗的内容。此消耗序列后的首个字符如果存在，那么保持未读取。如果被消耗序列长度为零，或被消耗序列不能转换成上面所指定的项目，那么发生匹配失败，除非遇到文件尾、编码错误，或阻止从流输入的读取错误，此情况下此为输入失败。​	所有异于 `[`、`c` 和 `n` 的转换指示符，在尝试分析输入前消耗并舍弃所有前导空白字符（如同以调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 来确定）。这些被消耗的字符不计入指定的最大字段宽度。​	转换指示符 `lc`、`ls` 和 `l[` 进行多字节到宽字符转换，如同如同在转换首字符前，通过用初始化为零的 [mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 对象调用 [mbrtowc](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc)。​	转换指示符 `s` 与 `[` 始终在匹配字符之后存储一个空字符。目标数组的大小必须至少比指定字段宽度大一。未指定目标数组大小时，对 `%s` 或 `%[` 的使用，与 [gets](https://zh.cppreference.com/w/c/io/gets) 同样不安全。​	[定宽整数类型](https://zh.cppreference.com/w/c/types/integer)（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确的转换指示在标头 [](https://zh.cppreference.com/w/c/types/integer) 定义（虽然 [`<CNdMA>`](https://zh.cppreference.com/w/c/types/integer)、[`<CNuMA>`](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。​	在每个转换指示符后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许存储多个字段到同一“池”变量中。​	在分析以无数字指数为结尾的不完整浮点数，如以转换指示符 `%f` 分析 `"100er"` 时，消耗序列 `"100e"` （可能为合法浮点数的最长前缀），并导致匹配错误（被消耗序列不能转换成浮点数），而留下 `"r"`。某些既存实现不遵守此规则并回滚，通过消耗 `"100"` 而留下 `"er"`，例如 [glibc 漏洞 1765](https://sourceware.org/bugzilla/show_bug.cgi?id=1765)。​	如果转换指示非法，那么行为未定义。 |                                                              |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |

**返回值**

1-3) 被成功赋值的接收参数的数量（可以为零，在首个接收用参数赋值前就发生匹配失败的情况下），或者若在首个接收用参数赋值前就发生输入失败，则为 [EOF](https://zh.cppreference.com/w/c/io)。

4-6) 同 (1-3) ，除了当发生运行时制约违规时，亦返回 [EOF](https://zh.cppreference.com/w/c/io)。

**复杂度**

​	无保证。需要注意的是，有些 `sscanf` 的实现为 *O(N)*，其中 `N = [strlen](http://zh.cppreference.com/w/c/string/byte/strlen)(buffer)` [[1\]](https://sourceware.org/bugzilla/show_bug.cgi?id=17577)。

**注解**

​	因为多数转换指示符首先消耗掉所有连续空白符，如下的代码

```
scanf("%d", &a);
scanf("%d", &b);
```

​	将读取在不同行上（第二个 %d 会消耗第一个剩下的换行符）或同一行由空格或制表符分隔（第二个 %d 会消耗空格或制表符）的整数。

​	不消耗前导空白符的转换指示符，如 `%c`，可以通过在格式字符串中前置一个空白符令它如此：

```
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

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.6.2 The fscanf function （第 231-236 页）

  - 7.21.6.4 The scanf function （第 236-237 页）

  - 7.21.6.7 The sscanf function （第 238-239 页）

  - K.3.5.3.2 The fscanf_s function （第 430-431 页）

  - K.3.5.3.4 The scanf_s function （第 432 页）

  - K.3.5.3.7 The sscanf_s function （第 433 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.6.2 The fscanf function （第 317-324 页）

  - 7.21.6.4 The scanf function （第 325 页）

  - 7.21.6.7 The sscanf function （第 326 页）

  - K.3.5.3.2 The fscanf_s function （第 592-593 页）

  - K.3.5.3.4 The scanf_s function （第 594 页）

  - K.3.5.3.7 The sscanf_s function （第 596 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.6.2 The fscanf function （第 282-289 页）

  - 7.19.6.4 The scanf function （第 290 页）

  - 7.19.6.7 The sscanf function （第 291 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.6.2 The fscanf function

  - 4.9.6.4 The scanf function

  - 4.9.6.6 The sscanf function

**参阅**

| [vscanf (C99)<br />vfscanf (C99)<br />vsscanf (C99)<br />vscanf_s (C99)<br />vfscanf_s (C99)<br />vsscanf_s (C99)<br />](https://zh.cppreference.com/w/c/io/vfscanf) | 从 [stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 使用可变参数列表 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [fgets<br />](https://zh.cppreference.com/w/c/io/fgets)    | 从文件流获取一个字符串 (函数)                                |
| [printf <br />fprintf <br />sprintf <br />snprintf (C99)<br />printf_s (C99)<br />fprintf_s (C11)<br />sprintf_s (C11)<br />snprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 (函数) |
| **scanf, fscanf, sscanf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fscanf)** |                                                              |





### fscanf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### fseek

原址：[http://zh.cppreference.com/w/c/io/fseek](http://zh.cppreference.com/w/c/io/fseek)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int fseek( FILE* stream, long offset, int origin );
#define SEEK_SET    /* 未指明 */
#define SEEK_CUR    /* 未指明 */

#define SEEK_END    /* 未指明 */
```

​	设置文件流 `stream` 的文件位置指示器为 `offset` 所指向的值。

​	若 `stream` 以二进制模式打开，则新位置恰好是文件起始后（若 `origin` 为 [SEEK_SET](https://zh.cppreference.com/w/c/io)）或当前文件位置后（若 `origin` 为 [SEEK_CUR](https://zh.cppreference.com/w/c/io)），或文件结尾后（若 `origin` 为 [SEEK_END](https://zh.cppreference.com/w/c/io)）的 `offset` 字节。不要求二进制流支持 [SEEK_END](https://zh.cppreference.com/w/c/io)，尤其是当其输出中附加了空字节时。

​	若 `stream` 以文本模式打开，则仅有的受支持 `offset` 值为零（可用于任何 `origin`）和先前在关联到同一个文件的流上对 [ftell](https://zh.cppreference.com/w/c/io/ftell) 的调用的返回值（仅可用于 [SEEK_SET](https://zh.cppreference.com/w/c/io) 的 `origin`）。

​	若 `stream` 为宽取向，则文本和二进制流的限制均适用（允许 [ftell](https://zh.cppreference.com/w/c/io/ftell) 的结果与 [SEEK_SET](https://zh.cppreference.com/w/c/io) 一同使用，并允许零偏移量以 [SEEK_SET](https://zh.cppreference.com/w/c/io) 和 [SEEK_CUR](https://zh.cppreference.com/w/c/io) 但非 [SEEK_END](https://zh.cppreference.com/w/c/io) 为基准）。

​	除了更改文件位置指示器， `fseek` 还撤销 [ungetc](https://zh.cppreference.com/w/c/io/ungetc) 的效果并清除文件尾状态，如果适用。

​	若发生读或写错误，则设置流的错误指示器（ [ferror](https://zh.cppreference.com/w/c/io/ferror) ）而不影响文件位置。

**参数**

| stream | -    | 要修改的文件流                                               |
| ------ | ---- | ------------------------------------------------------------ |
| offset | -    | 相对 origin 迁移的字符数                                     |
| origin | -    | `offset` 所加上的位置。它能拥有下列值之一：[SEEK_SET](https://zh.cppreference.com/w/c/io)、[SEEK_CUR](https://zh.cppreference.com/w/c/io)、[SEEK_END](https://zh.cppreference.com/w/c/io) |

**返回值**

​	成功时为 `0` ，否则为非零。

**注解**

​	在巡位到宽流的非结尾位置后，下个对任意输出函数的调用可能令剩下的文件内容未定义，例如通过输出一个长度不同的多字节序列。

​	对于文本流，`offset` 仅有的合法值是 `0`（可应用于任意 `origin`）和先前 [ftell](https://zh.cppreference.com/w/c/io/ftell) 调用的返回值（仅可应用于 [SEEK_SET](https://zh.cppreference.com/w/c/io)）。

​	POSIX 允许在文件尾之后巡位。若在此巡位后进行输出，则任何间隙中的读取将返回零字节。在文件系统支持的场合，这会创建一个*稀疏文件*。

​	POSIX 亦要求 `fseek` 先进行 [fflush](https://zh.cppreference.com/w/c/io/fflush) ，若有任何未写入数据（但是否恢复迁移状态是实现定义的）。

​	POSIX 规定，[`fseek`](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fseek.html) 错误时应返回 `-1`，并设置 [errno](https://zh.cppreference.com/w/c/error/errno) 以标明该错误。

​	Windows 中，应使用 [`_fseeki64`](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/fseek-fseeki64) 以支持大小超过 2GiB 的文件。

**示例**

​	`fseek` 及错误检查

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    // 准备 double 值的数组。
    #define SIZE 5
    double A[SIZE] = {1.0, 2.0, 3.0, 4.0, 5.0};
 
    // 将数组写入文件。
    FILE * fp = fopen("test.bin", "wb");
    fwrite(A, sizeof(double), SIZE, fp);
    fclose (fp);
 
    // 将各 double 值读取到数组 B 中。
    double B[SIZE];
    fp = fopen("test.bin", "rb");
 
    // 设置文件位置指示器到第三个 double 值之前。
    if (fseek(fp, sizeof(double) * 2L, SEEK_SET) != 0)
    {
        fprintf(stderr, "fseek() 失败，文件 %s 行 # %d\n",
                __FILE__, __LINE__ - 2);
        fclose(fp);
        return EXIT_FAILURE;
    }
 
    int ret_code = fread(B, sizeof(double), 1, fp); // 读取一个 double 值
    printf("ret_code == %d\n", ret_code);           // 打印所读取值的数量
    printf("B[0] == %.1f\n", B[0]);                 // 打印一个值
 
    fclose(fp);
    return EXIT_SUCCESS;
}
```

​	可能的输出：

```txt
ret_code == 1
B[0] == 3.0
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.23.9.2 The fseek function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.9.2 The fseek function （第 245 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.9.2 The fseek function （第 336-337 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.9.2 The fseek function （第 302-303 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.9.2 The fseek function

**参阅**

| [fsetpos<br />](https://zh.cppreference.com/w/c/io/fsetpos) | 将文件位置指示器移动到文件中的指定位置 (函数) |
| ------------------------------------------------------------ | --------------------------------------------- |
| [fgetpos<br />](https://zh.cppreference.com/w/c/io/fgetpos) | 获取文件位置指示器 (函数)                     |
| [ftell<br />](https://zh.cppreference.com/w/c/io/ftell)    | 返回当前的文件位置指示值 (函数)               |
| [rewind<br />](https://zh.cppreference.com/w/c/io/rewind)  | 将文件位置指示器移动到文件首 (函数)           |
| **fseek** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fseek)** |                                               |





### fsetpos

原址：[http://zh.cppreference.com/w/c/io/fsetpos](http://zh.cppreference.com/w/c/io/fsetpos)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int fsetpos( FILE *stream, const fpos_t *pos );
```

​	按照 `pos` 所指向的值，设置文件流 `stream` 的文件位置指示器和多字节分析状态（若存在）。

​	调用此函数，除了建立新的分析状态和位置，还会撤销 [ungetc](https://zh.cppreference.com/w/c/io/ungetc) 的效果，且若设置了文件尾状态则清除之。

​	若读或写出现错误，则设置流的错误指示器（[ferror](https://zh.cppreference.com/w/c/io/ferror)）。

**参数**

| stream | -    | 要修改的文件流                                               |
| ------ | ---- | ------------------------------------------------------------ |
| pos    | -    | 指向 `[fpos_t](http://zh.cppreference.com/w/c/io)` 对象的指针，用作文件位置指示器的新值 |

**返回值**

​	成功时为 `0` ，否则为非零值。

**注意**

​	在寻位到宽流的非结尾位置后，下个对任何输出函数的调用可能使剩下的文件内容未定义，例如通过输出不同长度的多字节序列。

**示例**

​	`fsetpos` 带错误检查

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    // 准备一个浮点值的数组。
    #define SIZE 5
    double A[SIZE] = {1.0, 2.0, 3.0, 4.0, 5.0};
    // 写数组到文件。
    FILE * fp = fopen("test.bin", "wb");
    fwrite(A,sizeof(double),SIZE,fp);
    fclose (fp);
 
    // 读取浮点值到数组B。
    double B[SIZE];
    fp = fopen("test.bin","rb");
    fpos_t pos;
    if (fgetpos(fp,&pos)) // 当前位置：文件起始
    {
        perror("fgetpos()");
        fprintf(stderr,"fgetpos() 失败。文件 %s 行 # %d\n", __FILE__,__LINE__-3);
        exit(EXIT_FAILURE);
    }
 
    int ret_code = fread(B,sizeof(double),1,fp); // 读取一个浮点值
    // 当前位置：在读一个浮点值后
    printf("%.1f; 读取计数 = %d\n", B[0], ret_code); // 打印一个浮点值和 ret_code
 
    if (fsetpos(fp,&pos)) // 重设当前位置为文件起始
    {
        if (ferror(fp))
        {
            perror("fsetpos()");
            fprintf(stderr,"fsetpos() 失败。文件 %s 行 # %d\n", __FILE__,__LINE__-5);
            exit(EXIT_FAILURE);
        }
    }
 
    ret_code = fread(B,sizeof(double),1,fp); // 重读首个浮点值
    printf("%.1f; 读取计数 = %d\n", B[0], ret_code); // 打印一个浮点值和 ret_code
    fclose(fp);
 
    return EXIT_SUCCESS; 
}
```

​	可能的输出：

```txt
1.0; 读取计数 = 1
1.0; 读取计数 = 1
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.9.3 The fsetpos function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.9.3 The fsetpos function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.9.3 The fsetpos function （第 337 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.9.3 The fsetpos function （第 303 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.9.3 The fsetpos function

**参阅**

| [fgetpos<br />](https://zh.cppreference.com/w/c/io/fgetpos) | 获取文件位置指示器 (函数)                     |
| ------------------------------------------------------------ | --------------------------------------------- |
| [ftell<br />](https://zh.cppreference.com/w/c/io/ftell)    | 返回当前的文件位置指示值 (函数)               |
| [fseek<br />](https://zh.cppreference.com/w/c/io/fseek)    | 将文件位置指示符移动到文件中的指定位置 (函数) |
| **fsetpos** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fsetpos)** |                                               |





### ftell

原址：[http://zh.cppreference.com/w/c/io/ftell](http://zh.cppreference.com/w/c/io/ftell)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
long ftell( FILE *stream );
```

​	返回流 `stream` 的文件位置指示器。

​	若流以二进制模式打开，则由此函数获得的值是从文件开始的字节数。

​	若流以文本模式打开，则由此函数返回的值未指定，且仅若作为 [fseek()](https://zh.cppreference.com/w/c/io/fseek) 的输入才有意义。

**参数**

| stream | -    | 要检验的文件流 |
| ------ | ---- | -------------- |
|        |      |                |

**返回值**

​	成功时为文件位置指示器，若失败发生则为 `-1L` 。

​	失败时，设 `errno` 对象为实现定义的正值。

**注解**

​	Windows 中，应使用 [`_ftelli64`](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/ftell-ftelli64) 以支持大小超过 2GiB 的文件。

**示例**

​	演示 `ftell()` 带错误检查。向文件写出少量浮点数后再从中读取它们。

```c
#include <stdio.h>
#include <stdlib.h>
 
/* 如果条件不满足，则退出程序并给出错误消息。 */
void check(_Bool condition, const char* func, int line)
{
    if (condition)
        return;
    perror(func);
    fprintf(stderr, "%s failed in file %s at line # %d\n", func, __FILE__, line - 1);
    exit(EXIT_FAILURE);
}
 
int main(void)
{
    /* 准备浮点数的数组。 */
    #define SIZE 5
    double A[SIZE] = {1.1, 2.0, 3.0, 4.0, 5.0};
 
    /* 写数组到文件。 */
    const char* fname = "/tmp/test.bin";
    FILE* file = fopen(fname, "wb");
    check(file != NULL, "fopen()", __LINE__);
 
    const int write_count = fwrite(A, sizeof(double), SIZE, file);
    check(write_count == SIZE, "fwrite()", __LINE__);
 
    fclose (file);
 
    /* 读取浮点数到数组 B。 */
    double B[SIZE];
    file = fopen(fname, "rb");
    check(file != NULL, "fopen()", __LINE__);
 
    long int pos = ftell(file); /* 位置指示器在文件起始 */
    check(pos != -1L, "ftell()", __LINE__);
    printf("pos: %ld\n", pos);
 
 
    const int read_count = fread(B, sizeof(double), 1, file); /* 读取一个浮点数 */
    check(read_count == 1, "fread()", __LINE__);
 
    pos = ftell(file); /* 读取一个浮点数后的位置指示器 */
    check(pos != -1L, "ftell()", __LINE__);
    printf("pos: %ld\n", pos);
    printf("B[0]: %.1f\n", B[0]); /* 打印一个浮点数 */
 
    return EXIT_SUCCESS; 
}
```

​	可能的输出：

```txt
pos: 0
pos: 8
B[0]: 1.1
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.9.4 The ftell function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.9.4 The ftell function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.9.4 The ftell function （第 337-338 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.9.4 The ftell function （第 303-304 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.9.4 The ftell function

**参阅**

| [fgetpos<br />](https://zh.cppreference.com/w/c/io/fgetpos) | 获取文件位置指示器 (函数)                     |
| ------------------------------------------------------------ | --------------------------------------------- |
| [fseek<br />](https://zh.cppreference.com/w/c/io/fseek)    | 将文件位置指示符移动到文件中的指定位置 (函数) |
| [fsetpos<br />](https://zh.cppreference.com/w/c/io/fsetpos) | 将文件位置指示器移动到文件中的指定位置 (函数) |
| **ftell** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/ftell)** |                                               |





### fwrite

原址：[http://zh.cppreference.com/w/c/io/fwrite](http://zh.cppreference.com/w/c/io/fwrite)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
size_t fwrite( const void *buffer, size_t size, size_t count,
               FILE *stream );// (C99 前)
size_t fwrite( const void *restrict buffer, size_t size, size_t count, 
               FILE *restrict stream );// (C99 起)
```

​	从给定数组 `buffer` 向输出流 `stream` 写入 `count` 个对象。各个对象的写入，如同将每个对象解读为 `unsigned char` 数组，并对每个对象调用 `size` 次 [fputc](https://zh.cppreference.com/w/c/io/fputc) 以将那些 `unsigned char` 按顺序写入 `stream` 一般来进行。文件位置指示器前进所写入的字节数。

​	如果发生错误，则所造成的该流的文件位置指示器的值是不确定的。

**参数**

| buffer | -    | 指向数组中要被写入的首个对象的指针 |
| ------ | ---- | ---------------------------------- |
| size   | -    | 每个对象的大小                     |
| count  | -    | 要被写入的对象数                   |
| stream | -    | 指向输出流的指针                   |

**返回值**

​	成功写入的对象数，若错误发生则可能小于 `count`。

​	若 `size` 或 `count` 为零，则 `fwrite` 返回零且不进行其他动作。

**示例**

```c
#include <assert.h>
#include <stdio.h>
#include <stdlib.h>
 
enum { SIZE = 5 };
 
int main(void)
{
    double a[SIZE] = {1, 2, 3, 4, 5};
    FILE* f1 = fopen("file.bin", "wb");
    assert(f1);
    size_t r1 = fwrite(a, sizeof a[0], SIZE, f1);
    printf("wrote %zu elements out of %d requested\n", r1, SIZE);
    fclose(f1);
 
    double b[SIZE];
    FILE* f2 = fopen("file.bin", "rb");
    size_t r2 = fread(b, sizeof b[0], SIZE, f2);
    fclose(f2);
    printf("read back: ");
    for (size_t i = 0; i < r2; ++i)
        printf("%0.2f ", b[i]);
}
```

​	输出：

```txt
wrote 5 elements out of 5 requested
read back: 1.00 2.00 3.00 4.00 5.00
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.8.2 The fwrite function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.8.2 The fwrite function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.8.2 The fwrite function （第 335-336 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.8.2 The fwrite function （第 301-302 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.8.2 The fwrite function

**参阅**

| [printf <br />fprintf <br />sprintf <br />snprintf (C99)<br />printf_s (C99)<br />fprintf_s (C11)<br />sprintf_s (C11)<br />snprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [fputs<br />](https://zh.cppreference.com/w/c/io/fputs)    | 将一个字符串写入文件流 (函数)                                |
| [fread<br />](https://zh.cppreference.com/w/c/io/fread)    | 从文件读取 (函数)                                            |
| **fwrite** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fwrite)** |                                                              |





### getc

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





### getchar

原址：[http://zh.cppreference.com/w/c/io/getchar](http://zh.cppreference.com/w/c/io/getchar)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int getchar(void);
```

​	从 [stdin](https://zh.cppreference.com/w/c/io) 读取下一个字符。

​	等价于 `[getc](http://zh.cppreference.com/w/c/io/fgetc)([stdin](http://zh.cppreference.com/w/c/io))` 。

**参数**

​	（无）

**返回值**

​	成功时为获得的字符，失败时为 [EOF](https://zh.cppreference.com/w/c/io) 。

​	若失败由文件尾条件产生，则另外设置 [stdin](https://zh.cppreference.com/w/c/io) 上的*文件尾*指示器（见 [feof()](https://zh.cppreference.com/w/c/io/feof) ）。若失败由某些其他错误产生，则设置 [stdin](https://zh.cppreference.com/w/c/io) 上的*错误*指示器（见 [ferror()](https://zh.cppreference.com/w/c/io/ferror) ）。

**示例**

​	演示 `getchar` 带错误检查

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    for (int ch; (ch = getchar()) != EOF;) // 从 stdin 读/打印 "abcde"
        printf("%c", ch);
 
    // 测试抵达 EOF 的原因。
    if (feof(stdin)) // 若因文件尾条件失败
        puts("End of file reached");
    else if (ferror(stdin)) // 若因别的错误失败
    {
        perror("getchar()");
        fprintf(stderr, "getchar() failed in file %s at line # %d\n",
                __FILE__, __LINE__ - 9);
        exit(EXIT_FAILURE);
    }
 
    return EXIT_SUCCESS;
}
```

​	可能的输出：

```txt
abcde
End of file reached
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.7.6 The getchar function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.7.6 The getchar function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.7.6 The getchar function （第 332 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.7.6 The getchar function （第 298 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.7.6 The getchar function

**参阅**

| [fgetc<br />getc<br />](https://zh.cppreference.com/w/c/io/fgetc) | 从文件流获取一个字符 (函数) |
| ------------------------------------------------------------ | --------------------------- |
| **getchar** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/getchar)** |                             |





### gets_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### perror

原址：[http://zh.cppreference.com/w/c/io/perror](http://zh.cppreference.com/w/c/io/perror)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
void perror( const char *s );
```

​	打印当前存储于系统变量 [errno](https://zh.cppreference.com/w/c/error/errno) 的错误码到 [stderr](https://zh.cppreference.com/w/c/io) 。

​	通过连接下列组分构成描述：

- `s` 所指向的空终止字节字符串的内容后随 `": "` （除非 `s` 为空指针或 `s` 所指向字符为空字符）
- 实现定义的，描述存储于 `errno` 的错误码的错误消息字符串后随 ``'\n'`` 。错误消息字符串等同于 `[strerror](http://zh.cppreference.com/w/c/string/byte/strerror)(errno)` 的结果。

**参数**

| s    | -    | 指向带解释消息的空终止字符串的指针 |
| ---- | ---- | ---------------------------------- |
|      |      |                                    |

**返回值**

​	（无）

**示例**

```c
#include <stdio.h>
 
int main(void)
{
    FILE *f = fopen("non_existent", "r");
    if (f == NULL) {
        perror("fopen() failed");
    } else {
        fclose(f);
    }
}
```

​	可能的输出：

```txt
fopen() failed: No such file or directory
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.10.4 The perror function （第 339 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.10.4 The perror function （第 305 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.10.4 The perror function

**参阅**

| [strerror <br />strerror_s (C11)<br />strerrorlen_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strerror) | 返回给定错误码的文本版本 (函数) |
| ------------------------------------------------------------ | ------------------------------- |
| **perror** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/perror)** |                                 |





### printf

原址：[http://zh.cppreference.com/w/c/io/fprintf](http://zh.cppreference.com/w/c/io/fprintf)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
// (1)
int printf( const char*          format, ... );// (C99 前)
int printf( const char* restrict format, ... );// (C99 起)
// (2)
int fprintf( FILE*          stream, const char*          format, ... );// (C99 前)
int fprintf( FILE* restrict stream, const char* restrict format, ... );// (C99 起)
// (3)
int sprintf( char*          buffer, const char*          format, ... );// (C99 前)
int sprintf( char* restrict buffer, const char* restrict format, ... );// (C99 起)
int snprintf( char* restrict buffer, size_t bufsz,
              const char* restrict format, ... );// (4)(C99 起)
int printf_s( const char* restrict format, ... );// (5)(C11 起)
int fprintf_s( FILE* restrict stream, const char* restrict format, ... );// (6)(C11 起)
int sprintf_s( char* restrict buffer, rsize_t bufsz,
               const char* restrict format, ... );// (7)(C11 起)
int snprintf_s( char* restrict buffer, rsize_t bufsz,
                const char* restrict format, ... );// (8)(C11 起)
```

​	从给定位置加载数据，转换为字符串等价物，并写结果到各种池。

1） 将结果写入输出流 [stdout](https://zh.cppreference.com/w/c/io)。

2） 将结果写入输出流 `stream`。

3） 将结果写入字符串 `buffer`。如果所写入的字符串（加上终止空字符）超出由 `buffer` 所指向的数组的大小，则行为未定义。

4） 将结果写入字符串 `buffer`。至多写 `bufsz - 1` 个字符。产生的字符串会以空字符终止，除非 `bufsz` 为零。若 `bufsz` 为零，则不写入任何内容，且 `buffer` 可以是空指针，然而依旧计算返回值（会写入的字符数，不包含空终止符）并返回。

5-8) 同 (1-4) ，除了在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `format` 中存在转换说明符 `%n`
  - 任何一个对应 `%s` 的参数是空指针
  - `stream`、`format` 或 `buffer` 是空指针
  - `bufsz` 为零或大于 RSIZE_MAX
  - 在任何一个字符串及字符转换说明符中出现编码错误
  - （仅对于 `sprintf_s` ）存储于 `buffer` 的字符串（包括尾随空字符）长度将超出 `bufsz`

**参数**

| stream | -    | 要写入的输出文件流                                           |
| ------ | ---- | ------------------------------------------------------------ |
| buffer | -    | 指向要写入的字符串的指针                                     |
| bufsz  | -    | 最多会写入 `bufsz - 1` 个字符，再加空终止符                  |
| format | -    | 指向指定数据转换方式的空终止多字节字符串的指针               |
| ...    | -    | 指定要打印数据的参数。若任何[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)后的参数不拥有对应转换说明所期待的类型（期待类型是提升后的类型或者提升后类型的兼容类型），或若参数数量少于 `format` 的要求，则行为未定义。若有多于 `format` 要求的参数，则求值并忽略多出的参数。 |

​	**格式**字符串由普通多字节字符（除了 `%`）和转换指示构成，前者被不改动地复制到输出流。每个转换指示均拥有下列格式：

  - 引入的 `%` 字符。

  - (可选) 一或多个修改转换行为的标志：
  - `-`：转换结果在域内左对齐（默认为右对齐）。
  - `+`：有符号转换的符号始终前置于转换结果（默认仅当结果为负时前置负号）。
  - *空格*：如果有符号转换的结果不以符号开始，或为空，那么前置空格于结果。存在 `+` 标志时忽略*空格*。
  - `#`：进行*替用形式* ﻿的转换。确切的效果见下表，其他情况下行为未定义。
  - `0`：对于整数和浮点数转换，使用前导零代替*空格* ﻿字符填充字段。对于整数，如果显式指定了精度，那么忽略此标志。对于其他转换，使用此标志导致未定义行为。存在 `-` 标志时忽略 `0`。

  - (可选) 整数或 `*`，指定最小字段宽度。如果有要求，那么结果会以*空格* ﻿字符（默认情况）填充，在右对齐时于左，左对齐时于右。使用 `*` 的情况下，以一个额外的 `int` 类型实参指定宽度。如果实参值是负数，那么它导致指定 `-` 标志和正的字段宽度。（注意：这是最小宽度：值决不会被截断）。

  - (可选) 后随整数或 `*` 或两者皆无的 `.`，指示转换的*精度* ﻿。在使用 `*` 的情况下，*精度* ﻿由额外的 `int` 类型的实参指定。如果此实参的值是负数，那么它被忽略。如果既不使用数字也不使用 `*`，那么精度采用零。*精度* ﻿的确切效果见下表。

  - (可选) 指定实参大小的*长度修饰符*（其与格式指示符组合，指定对应实参的类型）。

  - 转换格式指示符

​	下列格式指示符可用：

|                          转换指示符                          |                             解释                             | 期望的实参类型  |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :-------------: | :--------------: | :------------: | :-------------: | :------------------: | :----------------------------------------------------------: | :----------------------------------------------------: | :----------------------------------------------------------: | ------------- |
|                         长度修饰符→                          |                              hh                              |        h        |        无        |       l        |       ll        |          j           |                              z                               |                           t                            |                              L                               |               |
|                       仅从 C99 起可用→                       |                              是                              |                 |                  |                |       是        |          是          |                              是                              |                           是                           |                                                              |               |
|                             `%`                              | ​	写入字面的 `%`。完整的转换指示必须是 `%%`。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `c`                              | ​	写入**单个字符**。实参首先被转换成 `unsigned char`。如果使用 **l** 修饰符，那么实参首先被转换成字符串，如同通过以 `wchar_t[2]` 实参使用 **%ls**。 |     不适用      |      不适用      |     `int`      |     wint_t      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `s`                              | ​	写入**字符串**。实参必须是指向字符数组首元素的指针。*精度* ﻿指定写入最大的字符数。如果没有指定*精度*，那么写每个字节直到而不含首个空终止符。如果使用 **l** 指示符，那么实参必须是指向 `wchar_t` 数组首元素的指针，数组会被转换成 `char` 数组，如同通过以零初始化转换状态调用 [wcrtomb](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb)。 |     不适用      |      不适用      |    `char*`     |   `wchar_t*`    |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                           `d` `i`                            | ​	转换**有符号整数**为十进制表示 *[-]dddd*。*精度* ﻿指定出现的最小数位数。默认精度是 `1`。如果被转换的值和精度都是 `0`，那么转换结果无字符。对于 `z` 修饰符，期望的实参类型是 [size_t](https://zh.cppreference.com/w/c/types/size_t) 的有符号版本。 |  `signed char`  |     `short`      |     `int`      |     `long`      |     `long long`      |  [intmax_t](https://zh.cppreference.com/w/c/types/integer)   |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) | 不适用        |
|                             `o`                              | ​	转换**无符号整数**为八进制表示 *oooo*。*精度* ﻿指定出现数字的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现* ﻿中精度按需增加，以写入一个前导零。在此情况下如果被转换值和精度都是 `0`，那么写入单个 `0`。 | `unsigned char` | `unsigned short` | `unsigned int` | `unsigned long` | `unsigned long long` |  [uintmax_t](https://zh.cppreference.com/w/c/types/integer)  | [size_t](https://zh.cppreference.com/w/c/types/size_t) | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) 的无符号版本 | 不适用        |
|                           `x` `X`                            | ​	转换**无符号整数**为十六进制表示 *hhhh*。`x` 转换使用字母 `abcdef`。`X` 转换使用 `ABCDEF`。*精度*指定出现数位的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现中* ﻿如果被转换值非零，那么结果有 `0x` 或 `0X` 前缀。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                             `u`                              | ​	转换**无符号整数**为十进制表示 *dddd*。*精度* ﻿指定出现的数位最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                        `f` `F` (C99)                         | ​	转换**浮点数**为 *[-]ddd.ddd* 样式的十进制记法。*精度* ﻿指定小数点字符后出现的确切数位数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |    `double`    | `double` (C99)  |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | `long double` |
|                           `e` `E`                            | ​	转换**浮点数**为十进制指数记法。`e` 转换样式使用 *[-]d.ddd* ﻿`e`*±dd*。`E` 转换样式使用 *[-]d.ddd* ﻿`E`*±dd*。指数至少含两个数位，仅当需要时才使用更多数位。如果值是 `0`，那么指数也是 `0`。*精度* ﻿指定小数点字符后出现数位的最小个数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                 `a` `A`​	(C99)                 | ​	转换**浮点数**为十六进制指数记法。`a` 转换样式使用 *[-]* ﻿`0x`*h.hhh* ﻿`p`*±d*。`A` 转换样式使用 *[-]* ﻿`0X`*h.hhh* ﻿`P`*±d*。如果参数是正规化的浮点数，那么首个十六进制数位非 `0`。如果值是 `0`，那么指数也是 `0`。*精度*指定小数点字符后出现数位的最小个数。默认精度足以精确表示该值。在*替用实现*中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                           `g` `G`                            | ​	转换**浮点数**为十进制小数或十进制指数记法，依赖于值和*精度*。`g` 转换样式将进行带样式 `e` 或 `f` 的转换。`G` 转换样式将进行带样式 `E` 或 `f`(C99 前)`F`(C99 起) 的转换。令 `P` 等于精度，如果它非零，那么精度在未指定时是 `6`，如果精度是 `0` 那么等于 `1`。然后，如果带样式 `E` 的转换会有指数 `X`，那么：如果 *P > X ≥ −4*，那么转换带 `f` 或 `F`(C99 起) 风格，及精度 *P − 1 − X*。否则，转换带 `e` 或 `E` 风格，及精度 *P − 1*。除非要求*替用表示*，否则末尾零会被移除，且在不留下小数部分时小数点也会被移除。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                             `n`                              | ​	返回对函数的此调用迄今为止**写入的字符数**。结果被*写入* ﻿到实参所指向的值。该指示不可含有任何*标签*、*域宽* ﻿或*精度*。对于 `z` 修饰符，实参类型是 `S*`，其中 `S` 是 `[size_t](http://zh.cppreference.com/w/c/types/size_t)` 的有符号版本。 | `signed char*`  |     `short*`     |     `int*`     |     `long*`     |     `long long*`     | [intmax_t](https://zh.cppreference.com/w/c/types/integer)`*` |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)`*` | 不适用        |
|                             `p`                              |          写入定义了**指针**的由实现定义的字符序列。          |     不适用      |      不适用      |    `void*`     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             注解                             |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| ​	浮点数转换函数转换无穷大为 `inf` 或 `infinity`。由实现定义使用其中哪一个。​	非数转换成 `nan` 或 `nan(*char_sequence*)`。由实现定义使用其中哪一个。​	转换 `F`、`E`、`G`、`A` 替代上面输出 `INF`、`INFINITY`、`NAN`。​	用于打印 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short` 的转换指示符实际期待[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)后的类型，但在打印前会转换到 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short`。直接向函数传递这些类型的值是安全的，因为在调用变参数函数时会发生提升。​	定宽字符类型（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确转换指示在标头 [`<inttypes.h>`](https://zh.cppreference.com/w/c/header/inttypes) 定义（尽管 [PRIdMAX](https://zh.cppreference.com/w/c/types/integer)、[PRIuMAX](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。​	内存写入转换指示符 `%n` 是安全漏洞的常见目标，这里格式字符串依赖用户输入，而有边界检查的 `printf_s` 系列函数不支持此转换指示符(C11 起)。​	在每个转换指示符的行动后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许于同一变量多次存入 `%n` 的结果，并在同一此调用中打印出先前以 `%n` 存储的值。​	如果转换指示非法，那么行为未定义。 |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |

**返回值**

1,2) 传输到输出流的字符数，或若出现输出错误或编码错误（对于字符串和字符转换说明符）则为负值。

3） 写入到 `buffer` 的字符数（不计空终止字符），或若输出错误或编码错误（对于字符串和字符转换说明符）发生则为负值。

4） 假如忽略 `bufsz` 则本应写入到 `buffer` 的字符数（不计空终止字符），或若出现输出错误或编码错误（对于字符串和字符转换说明符）则为负值。

5,6) 传输到输出流的字符数，或若出现输出错误、运行时制约违规错误或编码错误则为负值。

7） 写入到 `buffer` 的字符数，不计空终止字符（只要 `buffer` 不是空指针且 `bufsz` 非零且不大于 RSIZE_MAX，就写入它），在运行时制约违规时为零，而在编码错误时为负值。

8） 假如忽略 `bufsz` 则本应写入 `buffer` 的字符数的，不包含空终止字符（只要 `buffer` 不是空指针而 `bufsz` 非零且不大于 RSIZE_MAX，就写入它），或若出现输出错误、运行时制约违规错误或编码错误则为负值。

**注解**

​	C 标准及 [POSIX](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fprintf.html) 指定 `sprintf` 及其变体的行为在参数与目标缓冲区重叠时未定义。示例：

```
sprintf(dst, "%s and %s", dst, t); // <- 有错：未定义行为
```

​	[POSIX 规定](http://pubs.opengroup.org/onlinepubs/9699919799/functions/fprintf.html)在错误时设置 [errno](https://zh.cppreference.com/w/c/error/errno)。它还规定额外的转换指示，最值得注意的是对实参重排序的支持（紧随 `%` 后的 `n$` 指示第 `n` 个实参）。

​	以零为 `bufsz` 和空指针为 `buffer` 调用 `snprintf` 可用于决定包含输出的缓冲区大小：

```
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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.6.1 The fprintf function （第 TBD 页）

  - 7.21.6.3 The printf function （第 TBD 页）

  - 7.21.6.5 The snprintf function （第 TBD 页）

  - 7.21.6.6 The sprintf function （第 TBD 页）

  - K.3.5.3.1 The fprintf_s function （第 TBD 页）

  - K.3.5.3.3 The printf_s function （第 TBD 页）

  - K.3.5.3.5 The snprintf_s function （第 TBD 页）

  - K.3.5.3.6 The sprintf_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.6.1 The fprintf function （第 225-230 页）

  - 7.21.6.3 The printf function （第 236 页）

  - 7.21.6.5 The snprintf function （第 237 页）

  - 7.21.6.6 The sprintf function （第 237 页）

  - K.3.5.3.1 The fprintf_s function （第 430 页）

  - K.3.5.3.3 The printf_s function （第 432 页）

  - K.3.5.3.5 The snprintf_s function （第 432-433 页）

  - K.3.5.3.6 The sprintf_s function （第 433 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.6.1 The fprintf function （第 309-316 页）

  - 7.21.6.3 The printf function （第 324 页）

  - 7.21.6.5 The snprintf function （第 325 页）

  - 7.21.6.6 The sprintf function （第 325-326 页）

  - K.3.5.3.1 The fprintf_s function （第 591 页）

  - K.3.5.3.3 The printf_s function （第 593-594 页）

  - K.3.5.3.5 The snprintf_s function （第 594-595 页）

  - K.3.5.3.6 The sprintf_s function （第 595-596 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.6.1 The fprintf function （第 274-282 页）

  - 7.19.6.3 The printf function （第 290 页）

  - 7.19.6.5 The snprintf function （第 290-291 页）

  - 7.19.6.6 The sprintf function （第 291 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.6.1 The fprintf function

  - 4.9.6.3 The printf function

  - 4.9.6.5 The sprintf function

**参阅**

| [wprintf (C95)<br />fwprintf (C95)<br />swprintf (C95)<br />wprintf_s (C95)<br />fwprintf_s (C95)<br />swprintf_s (C95)<br />snwprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fwprintf) | 打印格式化宽字符输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [vprintf <br />vfprintf <br />vsprintf <br />vsnprintf (C99)<br />vprintf_s (C99)<br />vfprintf_s (C11)<br />vsprintf_s (C11)<br />vsnprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/vfprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 使用可变参数列表 (函数) |
| [fputs<br />](https://zh.cppreference.com/w/c/io/fputs)    | 将一个字符串写入文件流 (函数)                                |
| [scanf <br />fscanf <br />sscanf <br />scanf_s (C11)<br />fscanf_s (C11)<br />sscanf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fscanf) | 从[stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 (函数) |
| **printf, fprintf, sprintf, snprintf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fprintf)** |                                                              |





### printf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### putc

原址：[http://zh.cppreference.com/w/c/io/fputc](http://zh.cppreference.com/w/c/io/fputc)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int fputc( int ch, FILE *stream );
int putc( int ch, FILE *stream );
```

​	写入字符 `ch` 到给定输出流 `stream` 。 `putc()` 可以实现为宏并对 `stream` 求值超过一次，故对应的参数决不应是有副效应的表达式。

​	在内部，在写入前将字符转换为 `unsigned char` 。

**参数**

| ch     | -    | 要写入的字符 |
| ------ | ---- | ------------ |
| stream | -    | 输出流       |

**返回值**

​	成功时，返回被写入字符。

​	失败时，返回 [EOF](https://zh.cppreference.com/w/c/io) 并设置 stream 上的*错误*指示器（见 [ferror()](https://zh.cppreference.com/w/c/io/ferror) ）。

**示例**

​	显示带错误检查的 `putc`

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    int ret_code = 0;
    for (char c = 'a'; (ret_code != EOF) && (c != 'z'); c++)
        ret_code = putc(c, stdout);
 
    // 测试是否抵达 EOF。
    if (ret_code == EOF && ferror(stdout))
    {
        perror("putc()");
        fprintf(stderr, "putc() failed in file %s at line # %d\n",
                __FILE__, __LINE__ - 7);
        exit(EXIT_FAILURE);
    }
    putc('\n', stdout);
 
    return EXIT_SUCCESS;
}
```

​	输出：

```txt
abcdefghijklmnopqrstuvwxy
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.7.3 The fputc function （第 TBD 页）

  - 7.21.7.7 The putc function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.7.3 The fputc function （第 TBD 页）

  - 7.21.7.7 The putc function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.7.3 The fputc function （第 331 页）

  - 7.21.7.7 The putc function （第 333 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.7.3 The fputc function （第 297 页）

  - 7.19.7.8 The putc function （第 299 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.7.3 The fputc function

  - 4.9.7.8 The putc function

**参阅**

| [putchar<br />](https://zh.cppreference.com/w/c/io/putchar) | 将一个字符写入 [stdout](https://zh.cppreference.com/w/c/io) (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **fputc, putc** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fputc)** |                                                              |





### putchar

原址：[http://zh.cppreference.com/w/c/io/putchar](http://zh.cppreference.com/w/c/io/putchar)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int putchar( int ch );
```

​	写字符 `ch` 到 [stdout](https://zh.cppreference.com/w/c/io)。在内部，字符于写入前被转换为 `unsigned char`。

​	等价于 `[putc](http://zh.cppreference.com/w/c/io/fputc)(ch, [stdout](http://zh.cppreference.com/w/c/io))`。

**参数**

| ch   | -    | 要被写入的字符 |
| ---- | ---- | -------------- |
|      |      |                |

**返回值**

​	成功时返回写入的字符。

​	失败时返回 [EOF](https://zh.cppreference.com/w/c/io) 并设置 [stdout](https://zh.cppreference.com/w/c/io) 上的*错误*指示器（见 [ferror()](https://zh.cppreference.com/w/c/io/ferror)）。

**示例**

​	展示 `putchar` 带错误检查

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    int ret_code = 0;
    for (char c = 'a'; (ret_code != EOF) && (c != 'z'); c++)
        ret_code = putchar(c);
 
    // 测试是否抵达 EOF。
    if (ret_code == EOF && ferror(stdout))
    {
        fprintf(stderr, "putchar() failed in file %s at line # %d\n",
                __FILE__, __LINE__ - 6);
        perror("putchar()");
        exit(EXIT_FAILURE);
    }
    putchar('\n');
 
    // putchar 返回值不等于参数
    int r = 0x1070;
    printf("\n0x%x\n", r);
    r = putchar(r);
    printf("\n0x%x\n", r);
}
```

​	输出：

```txt
abcdefghijklmnopqrstuvwxy
 
0x1070
p
0x70
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.7.8 The putchar function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.7.8 The putchar function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.7.8 The putchar function （第 333 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.7.9 The putchar function （第 299 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.7.9 The putchar function

**参阅**

| [fputc<br />putc<br />](https://zh.cppreference.com/w/c/io/fputc) | 将一个字符写入文件流 (函数) |
| ------------------------------------------------------------ | --------------------------- |
| **putchar** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/putchar)** |                             |





### puts

原址：[http://zh.cppreference.com/w/c/io/puts](http://zh.cppreference.com/w/c/io/puts)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int puts( const char *str );
```

​	写入每个来自空终止字符串 `str` 的字符及附加换行符 ``'\n'`` 到输出流 [stdout](https://zh.cppreference.com/w/c/io) ，如同以重复执行 [fputc](https://zh.cppreference.com/w/c/io/fputc) 写入。

​	不写入来自 `str` 的空终止字符。

**参数**

| str  | -    | 要写入的字符串 |
| ---- | ---- | -------------- |
|      |      |                |

**返回值**

​	成功时返回非负值。

​	失败时，返回 [EOF](https://zh.cppreference.com/w/c/io) 并设置 `stdout` 的*错误*指示器（见 [ferror()](https://zh.cppreference.com/w/c/io/ferror)）。

**注意**

​	`puts` 函数后附一个换行字符到输出，而 [fputs](https://zh.cppreference.com/w/c/io/fputs) 不这么做。

​	不同的实现返回不同的非负数：一些返回最后写入的字符，一些返回写入的字符数（或若字符串长于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 则返回它），一些简单地返回非负常量。

​	在重定向 [stdout](https://zh.cppreference.com/w/c/io) 到文件时，导致 `puts` 失败的典型原因是用尽了文件系统的空间。

**示例**

```c
#include <stdio.h>
 
int main(void)
{
    int rc = puts("Hello World");
 
    if (rc == EOF)
        perror("puts()"); // POSIX 要求设置 errno
}
```

​	输出：

```txt
Hello World
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.7.9 The puts function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.7.9 The puts function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.7.9 The puts function （第 333 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.7.10 The puts function （第 299 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.7.10 The puts function

**参阅**

| [fputs<br />](https://zh.cppreference.com/w/c/io/fputs)    | 将一个字符串写入文件流 (函数)                                |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [printf <br />fprintf <br />sprintf <br />snprintf (C99)<br />printf_s (C99)<br />fprintf_s (C11)<br />sprintf_s (C11)<br />snprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 (函数) |
| **puts** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/puts)** |                                                              |





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
```c
// 在标头 <stdio.h> 定义
void rewind( FILE *stream );
```

​	移动文件位置指示器到给定文件流的起始。

​	函数等价于 `[fseek](http://zh.cppreference.com/w/c/io/fseek)(stream, 0, [SEEK_SET](http://zh.cppreference.com/w/c/io));`，但它会清除文件尾和错误指示器。

​	此函数丢弃任何来自先前对 [ungetc](https://zh.cppreference.com/w/c/io/ungetc) 调用的效果。

**参数**

| stream | -    | 要修改的文件流 |
| ------ | ---- | -------------- |
|        |      |                |

**返回值**

​	（无）

**示例**

​	此例演示如何读文件二次

```c
#include <stdio.h>
 
char str[20];
 
int main(void)
{
    FILE *f;
    char ch;
 
    f = fopen("file.txt", "w");
    for (ch = '0'; ch <= '9'; ch++) {
        fputc(ch, f);
    }
    fclose(f);
 
    f = fopen("file.txt", "r");
    fread(str, 1, 10, f);
    puts(str);
 
    rewind(f);
    fread(str, 1, 10, f);
    puts(str);
    fclose(f);
 
    return 0;
}
```

​	输出：

```txt
0123456789
0123456789
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.9.5 The rewind function （第 338 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.9.5 The rewind function （第 304 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.9.5 The rewind function

**参阅**

| [fseek<br />](https://zh.cppreference.com/w/c/io/fseek)    | 将文件位置指示符移动到文件中的指定位置 (函数) |
| ------------------------------------------------------------ | --------------------------------------------- |
| **rewind** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/rewind)** |                                               |





### scanf

原址：[http://zh.cppreference.com/w/c/io/fscanf](http://zh.cppreference.com/w/c/io/fscanf)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
// (1)
int scanf( const char          *format, ... );// (C99 前)
int scanf( const char *restrict format, ... );// (C99 起)
// (2)
int fscanf( FILE          *stream, const char          *format, ... );// (C99 前)
int fscanf( FILE *restrict stream, const char *restrict format, ... );// (C99 起)
// (3)
int sscanf( const char          *buffer, const char          *format, ... );// (C99 前)
int sscanf( const char *restrict buffer, const char *restrict format, ... );// (C99 起)
int scanf_s(const char *restrict format, ...);// (4)(C11 起)
int fscanf_s(FILE *restrict stream, const char *restrict format, ...);// (5)(C11 起)
int sscanf_s(const char *restrict buffer, const char *restrict format, ...);// (6)(C11 起)
```

​	从各种资源读取数据，按照 `format` 转译，并将结果存储到指定位置。

1） 从 [stdin](https://zh.cppreference.com/w/c/io) 读取数据

2） 从文件流 `stream` 读取数据

3） 从空终止字符串 `buffer` 读取数据。抵达字符串结尾等价于 `fscanf` 的抵达文件尾条件

4-6) 同 (1-3) ，除了 `%c` 、 `%s` 及 `%[` 转换指示符要求二个参数（通常的指针和指示获取用数组大小的 rsize_t 类型的值，在以 %c 读取单个字符时可以为 1 ），并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - 任何指针类型的参数为空指针
  - `format` 、 `stream` 或 `buffer` 为空指针
  - `%c` 、 `%s` 或 `%[` 会写入的字符数，加上空终止字符，要超过提供给这些转换指示符的第二个（ rsize_t ）参数
  - 可选，任何其他可检测错误，例如未知转换指示符

**参数**

| stream | -    | 要读取的输入文件流                       |
| ------ | ---- | ---------------------------------------- |
| buffer | -    | 指向要读取的空终止字符串的指针           |
| format | -    | 指向指定读取输入方式的空终止字符串的指针 |
| ...    | -    | 各接收实参                               |

- 非空白多字节字符，除了 `%`：每个格式字符串中的这种字符处理一个来自输入流的完全相同的字符，或在它与流的下个字符比较不相等时导致函数失败。
- 空白字符：任何格式字符串中的单个空白字符处理所有来自输入的可用连续空白字符（如同通过于循环中调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 确定）。注意，格式字符串中 ``"\n"``、`" "`、`"**\t****\t**"` 或其他空白无区别。
- 转换指示：每个转换指示拥有下列格式：

  - 引入用 `%` 字符

  - (可选) 赋值抑制字符 `*`。如果存在此选项，那么此函数不将结果赋值给任何接收用实参。

  - (可选) 指定*最大字段宽度* ﻿的整数数字（大于零），即函数进行在当前转换指示所指定的转换时，允许处理的最大字符数。注意如果没有提供宽度，那么 `%s` 和 `%[` 可能导致缓冲区溢出。

  - (可选) 指定接收实参大小的*长度修饰符*，即实际目标类型。这影响转换准确性和溢出规则。默认目标类型对每个转换类型有所不同（见下表）。

  - 转换格式指示符。

​	下列格式指示符可用：

|                          转换指示符                          |                             解释                             |           期望的实参类型           |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :--------------------------------: | :----------------------------------: | :------------------------------: | :--------------------------------: | :------------------------------------------: | :----------------------------------------------------------: | :------------------------------------------------------: | :----------------------------------------------------------: | -------------- |
|                         长度修饰符→                          |                              hh                              |                 h                  |                  无                  |                l                 |                 ll                 |                      j                       |                              z                               |                            t                             |                              L                               |                |
|                       仅从 C99 起可用→                       |                              是                              |                                    |                                      |                                  |                 是                 |                      是                      |                              是                              |                            是                            |                                                              |                |
|                             `%`                              |                      匹配字面 `%`。                      |               不适用               |                不适用                |              不适用              |               不适用               |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             `c`                              | ​	匹配一个**字符**或**字符**的序列。如果使用了宽度指示符，那么匹配恰好*宽度*个字符（该实参必须是指向有充足空间的数组的指针）。与 %s 和 %[ 不同，它不会在数组后附加空字符。 |               不适用               |                不适用                |             `char*`              |             `wchar_t*`             |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             `s`                              | ​	匹配非空白字符的序列（一个**字符串**）。如果使用宽度指示符，那么至多匹配*宽度*个字符，或匹配到首个提前出现的空白符前。总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                        `[`*集合* ﻿`]`                         | ​	匹配*集合* ﻿中的字符的一个非空字符序列。如果集合的首字符是 `^`，那么匹配所有不在集合中的字符。如果集合以 `]` 或 `^]` 开始，那么 `]` 字符也会被包含入集合。在扫描集合的非最初位置的字符 `-` 是否可以指示范围，如 `[0-9]`，由实现定义。如果使用宽度指示符，那么最多匹配到*宽度*。总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `d`                              | ​	匹配一个**十进制整数**。该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 `10` 为 `base` 时期望的格式相同。 | `signed char*` 或 `unsigned char*` | `signed short*` 或 `unsigned short*` | `signed int*` 或 `unsigned int*` | `signed long*` 或 `unsigned long*` | `signed long long*` 或 `unsigned long long*` | `[intmax_t](http://zh.cppreference.com/w/c/types/integer)*` 或 `[uintmax_t](http://zh.cppreference.com/w/c/types/integer)*` | `[size_t](http://zh.cppreference.com/w/c/types/size_t)*` | `[ptrdiff_t](http://zh.cppreference.com/w/c/types/ptrdiff_t)*` | 不适用         |
|                             `i`                              | ​	匹配一个**整数**。该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 `0` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `u`                              | ​	匹配一个无符号**十进制整数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `10` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `o`                              | ​	匹配一个无符号**八进制数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `8` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                           `x` `X`                            | ​	匹配一个无符号**十六进制整数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `16` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `n`                              | ​	返回**迄今读取的字符数**。不消耗输出。不增加赋值计数。如果此指示符拥有赋值抑制运算符，那么行为未定义。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|      `a` (C99) `A` (C99) `e` `E` `f` `F` (C99) `g` `G`       | ​	匹配一个**浮点数**。该数的格式与 [strtof](https://zh.cppreference.com/w/c/string/byte/strtof) 期望的格式相同。 |               不适用               |                不适用                |             `float*`             |             `double*`              |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | `long double*` |
|                             `p`                              | ​	匹配定义了一个**指针**的由实现定义的字符序列。`printf` 系列函数使用 `%p` 格式指示符时应该产生同样的序列。 |               不适用               |                不适用                |             `void**`             |               不适用               |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             注解                             |                                                              |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
| ​	对于每个 `n` 以外的转换指示符，不超过任何指定字段宽度，且要么恰好是转换指示符所期待，要么是其所期待的前缀的最长输入字符序列，即是从流中消耗的内容。此消耗序列后的首个字符如果存在，那么保持未读取。如果被消耗序列长度为零，或被消耗序列不能转换成上面所指定的项目，那么发生匹配失败，除非遇到文件尾、编码错误，或阻止从流输入的读取错误，此情况下此为输入失败。​	所有异于 `[`、`c` 和 `n` 的转换指示符，在尝试分析输入前消耗并舍弃所有前导空白字符（如同以调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 来确定）。这些被消耗的字符不计入指定的最大字段宽度。​	转换指示符 `lc`、`ls` 和 `l[` 进行多字节到宽字符转换，如同如同在转换首字符前，通过用初始化为零的 [mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 对象调用 [mbrtowc](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc)。​	转换指示符 `s` 与 `[` 始终在匹配字符之后存储一个空字符。目标数组的大小必须至少比指定字段宽度大一。未指定目标数组大小时，对 `%s` 或 `%[` 的使用，与 [gets](https://zh.cppreference.com/w/c/io/gets) 同样不安全。​	[定宽整数类型](https://zh.cppreference.com/w/c/types/integer)（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确的转换指示在标头 [](https://zh.cppreference.com/w/c/types/integer) 定义（虽然 [`<CNdMA>`](https://zh.cppreference.com/w/c/types/integer)、[`<CNuMA>`](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。​	在每个转换指示符后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许存储多个字段到同一“池”变量中。​	在分析以无数字指数为结尾的不完整浮点数，如以转换指示符 `%f` 分析 `"100er"` 时，消耗序列 `"100e"` （可能为合法浮点数的最长前缀），并导致匹配错误（被消耗序列不能转换成浮点数），而留下 `"r"`。某些既存实现不遵守此规则并回滚，通过消耗 `"100"` 而留下 `"er"`，例如 [glibc 漏洞 1765](https://sourceware.org/bugzilla/show_bug.cgi?id=1765)。​	如果转换指示非法，那么行为未定义。 |                                                              |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |

**返回值**

1-3) 被成功赋值的接收参数的数量（可以为零，在首个接收用参数赋值前就发生匹配失败的情况下），或者若在首个接收用参数赋值前就发生输入失败，则为 [EOF](https://zh.cppreference.com/w/c/io)。

4-6) 同 (1-3) ，除了当发生运行时制约违规时，亦返回 [EOF](https://zh.cppreference.com/w/c/io)。

**复杂度**

​	无保证。需要注意的是，有些 `sscanf` 的实现为 *O(N)*，其中 `N = [strlen](http://zh.cppreference.com/w/c/string/byte/strlen)(buffer)` [[1\]](https://sourceware.org/bugzilla/show_bug.cgi?id=17577)。

**注解**

​	因为多数转换指示符首先消耗掉所有连续空白符，如下的代码

```
scanf("%d", &a);
scanf("%d", &b);
```

​	将读取在不同行上（第二个 %d 会消耗第一个剩下的换行符）或同一行由空格或制表符分隔（第二个 %d 会消耗空格或制表符）的整数。

​	不消耗前导空白符的转换指示符，如 `%c`，可以通过在格式字符串中前置一个空白符令它如此：

```
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

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.6.2 The fscanf function （第 231-236 页）

  - 7.21.6.4 The scanf function （第 236-237 页）

  - 7.21.6.7 The sscanf function （第 238-239 页）

  - K.3.5.3.2 The fscanf_s function （第 430-431 页）

  - K.3.5.3.4 The scanf_s function （第 432 页）

  - K.3.5.3.7 The sscanf_s function （第 433 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.6.2 The fscanf function （第 317-324 页）

  - 7.21.6.4 The scanf function （第 325 页）

  - 7.21.6.7 The sscanf function （第 326 页）

  - K.3.5.3.2 The fscanf_s function （第 592-593 页）

  - K.3.5.3.4 The scanf_s function （第 594 页）

  - K.3.5.3.7 The sscanf_s function （第 596 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.6.2 The fscanf function （第 282-289 页）

  - 7.19.6.4 The scanf function （第 290 页）

  - 7.19.6.7 The sscanf function （第 291 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.6.2 The fscanf function

  - 4.9.6.4 The scanf function

  - 4.9.6.6 The sscanf function

**参阅**

| [vscanf (C99)<br />vfscanf (C99)<br />vsscanf (C99)<br />vscanf_s (C99)<br />vfscanf_s (C99)<br />vsscanf_s (C99)<br />](https://zh.cppreference.com/w/c/io/vfscanf) | 从 [stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 使用可变参数列表 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [fgets<br />](https://zh.cppreference.com/w/c/io/fgets)    | 从文件流获取一个字符串 (函数)                                |
| [printf <br />fprintf <br />sprintf <br />snprintf (C99)<br />printf_s (C99)<br />fprintf_s (C11)<br />sprintf_s (C11)<br />snprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 (函数) |
| **scanf, fscanf, sscanf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fscanf)** |                                                              |





### scanf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### setbuf

原址：[http://zh.cppreference.com/w/c/io/setbuf](http://zh.cppreference.com/w/c/io/setbuf)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
void setbuf( FILE          *stream, char          *buffer );// (C99 前)
void setbuf( FILE *restrict stream, char *restrict buffer );// (C99 起)
#define BUFSIZ     /* 未指明 */
```

​	设置用于流操作的内部缓冲区。其长度至少应该为 `BUFSIZ` 个字符。

​	若 `buffer` 非空，则等价于 `[setvbuf](http://zh.cppreference.com/w/c/io/setvbuf)(stream, buffer, [_IOFBF](http://zh.cppreference.com/w/c/io), [BUFSIZ](http://zh.cppreference.com/w/c/io))` 。

​	若 `buffer` 为空，则等价于 `[setvbuf](http://zh.cppreference.com/w/c/io/setvbuf)(stream, [NULL](http://zh.cppreference.com/w/c/types/NULL), [_IONBF](http://zh.cppreference.com/w/c/io), 0)` ，这会关闭缓冲。

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

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.5.5 The setbuf function （第 225 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.5.5 The setbuf function （第 307-308 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.5.5 The setbuf function （第 273 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.5.5 The setbuf function

**参阅**

| [setvbuf<br />](https://zh.cppreference.com/w/c/io/setvbuf) | 为文件流设置缓冲区和其大小 (函数) |
| ------------------------------------------------------------ | --------------------------------- |
| **setbuf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/setbuf)** |                                   |





### setvbuf

原址：[http://zh.cppreference.com/w/c/io/setvbuf](http://zh.cppreference.com/w/c/io/setvbuf)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int setvbuf( FILE *         stream, char *         buffer, 
             int mode, size_t size );// (C99 前)
int setvbuf( FILE *restrict stream, char *restrict buffer, 
             int mode, size_t size );// (C99 起)
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
| mode   | -    | 使用的缓冲模式。它能是下列值之一：`_IOFBF`全缓冲：当缓冲区为空时，从流读入数据。或者当缓冲区满时，向流写入数据。`_IOLBF`行缓冲：每次从流中读入一行数据或向流中写入一行数据。`_IONBF`无缓冲：直接从流中读入数据或直接向流中写入数据，缓冲设置无效。 |
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

```c
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

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.5.6 The setvbuf function （第 225 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.5.6 The setvbuf function （第 308 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.5.6 The setvbuf function （第 273-274 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.5.6 The setvbuf function

**参阅**

| [setbuf<br />](https://zh.cppreference.com/w/c/io/setbuf)  | 为文件流设置缓冲区 (函数) |
| ------------------------------------------------------------ | ------------------------- |
| **setvbuf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/setvbuf)** |                           |





### snprintf

原址：[http://zh.cppreference.com/w/c/io/fprintf](http://zh.cppreference.com/w/c/io/fprintf)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
// (1)
int printf( const char*          format, ... );// (C99 前)
int printf( const char* restrict format, ... );// (C99 起)
// (2)
int fprintf( FILE*          stream, const char*          format, ... );// (C99 前)
int fprintf( FILE* restrict stream, const char* restrict format, ... );// (C99 起)
// (3)
int sprintf( char*          buffer, const char*          format, ... );// (C99 前)
int sprintf( char* restrict buffer, const char* restrict format, ... );// (C99 起)
int snprintf( char* restrict buffer, size_t bufsz,
              const char* restrict format, ... );// (4)(C99 起)
int printf_s( const char* restrict format, ... );// (5)(C11 起)
int fprintf_s( FILE* restrict stream, const char* restrict format, ... );// (6)(C11 起)
int sprintf_s( char* restrict buffer, rsize_t bufsz,
               const char* restrict format, ... );// (7)(C11 起)
int snprintf_s( char* restrict buffer, rsize_t bufsz,
                const char* restrict format, ... );// (8)(C11 起)
```

​	从给定位置加载数据，转换为字符串等价物，并写结果到各种池。

1） 将结果写入输出流 [stdout](https://zh.cppreference.com/w/c/io)。

2） 将结果写入输出流 `stream`。

3） 将结果写入字符串 `buffer`。如果所写入的字符串（加上终止空字符）超出由 `buffer` 所指向的数组的大小，则行为未定义。

4） 将结果写入字符串 `buffer`。至多写 `bufsz - 1` 个字符。产生的字符串会以空字符终止，除非 `bufsz` 为零。若 `bufsz` 为零，则不写入任何内容，且 `buffer` 可以是空指针，然而依旧计算返回值（会写入的字符数，不包含空终止符）并返回。

5-8) 同 (1-4) ，除了在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `format` 中存在转换说明符 `%n`
  - 任何一个对应 `%s` 的参数是空指针
  - `stream`、`format` 或 `buffer` 是空指针
  - `bufsz` 为零或大于 RSIZE_MAX
  - 在任何一个字符串及字符转换说明符中出现编码错误
  - （仅对于 `sprintf_s` ）存储于 `buffer` 的字符串（包括尾随空字符）长度将超出 `bufsz`

**参数**

| stream | -    | 要写入的输出文件流                                           |
| ------ | ---- | ------------------------------------------------------------ |
| buffer | -    | 指向要写入的字符串的指针                                     |
| bufsz  | -    | 最多会写入 `bufsz - 1` 个字符，再加空终止符                  |
| format | -    | 指向指定数据转换方式的空终止多字节字符串的指针               |
| ...    | -    | 指定要打印数据的参数。若任何[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)后的参数不拥有对应转换说明所期待的类型（期待类型是提升后的类型或者提升后类型的兼容类型），或若参数数量少于 `format` 的要求，则行为未定义。若有多于 `format` 要求的参数，则求值并忽略多出的参数。 |

​	**格式**字符串由普通多字节字符（除了 `%`）和转换指示构成，前者被不改动地复制到输出流。每个转换指示均拥有下列格式：

  - 引入的 `%` 字符。

  - (可选) 一或多个修改转换行为的标志：
  - `-`：转换结果在域内左对齐（默认为右对齐）。
  - `+`：有符号转换的符号始终前置于转换结果（默认仅当结果为负时前置负号）。
  - *空格*：如果有符号转换的结果不以符号开始，或为空，那么前置空格于结果。存在 `+` 标志时忽略*空格*。
  - `#`：进行*替用形式* ﻿的转换。确切的效果见下表，其他情况下行为未定义。
  - `0`：对于整数和浮点数转换，使用前导零代替*空格* ﻿字符填充字段。对于整数，如果显式指定了精度，那么忽略此标志。对于其他转换，使用此标志导致未定义行为。存在 `-` 标志时忽略 `0`。

  - (可选) 整数或 `*`，指定最小字段宽度。如果有要求，那么结果会以*空格* ﻿字符（默认情况）填充，在右对齐时于左，左对齐时于右。使用 `*` 的情况下，以一个额外的 `int` 类型实参指定宽度。如果实参值是负数，那么它导致指定 `-` 标志和正的字段宽度。（注意：这是最小宽度：值决不会被截断）。

  - (可选) 后随整数或 `*` 或两者皆无的 `.`，指示转换的*精度* ﻿。在使用 `*` 的情况下，*精度* ﻿由额外的 `int` 类型的实参指定。如果此实参的值是负数，那么它被忽略。如果既不使用数字也不使用 `*`，那么精度采用零。*精度* ﻿的确切效果见下表。

  - (可选) 指定实参大小的*长度修饰符*（其与格式指示符组合，指定对应实参的类型）。

  - 转换格式指示符

​	下列格式指示符可用：

|                          转换指示符                          |                             解释                             | 期望的实参类型  |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :-------------: | :--------------: | :------------: | :-------------: | :------------------: | :----------------------------------------------------------: | :----------------------------------------------------: | :----------------------------------------------------------: | ------------- |
|                         长度修饰符→                          |                              hh                              |        h        |        无        |       l        |       ll        |          j           |                              z                               |                           t                            |                              L                               |               |
|                       仅从 C99 起可用→                       |                              是                              |                 |                  |                |       是        |          是          |                              是                              |                           是                           |                                                              |               |
|                             `%`                              | ​	写入字面的 `%`。完整的转换指示必须是 `%%`。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `c`                              | ​	写入**单个字符**。实参首先被转换成 `unsigned char`。如果使用 **l** 修饰符，那么实参首先被转换成字符串，如同通过以 `wchar_t[2]` 实参使用 **%ls**。 |     不适用      |      不适用      |     `int`      |     wint_t      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `s`                              | ​	写入**字符串**。实参必须是指向字符数组首元素的指针。*精度* ﻿指定写入最大的字符数。如果没有指定*精度*，那么写每个字节直到而不含首个空终止符。如果使用 **l** 指示符，那么实参必须是指向 `wchar_t` 数组首元素的指针，数组会被转换成 `char` 数组，如同通过以零初始化转换状态调用 [wcrtomb](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb)。 |     不适用      |      不适用      |    `char*`     |   `wchar_t*`    |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                           `d` `i`                            | ​	转换**有符号整数**为十进制表示 *[-]dddd*。*精度* ﻿指定出现的最小数位数。默认精度是 `1`。如果被转换的值和精度都是 `0`，那么转换结果无字符。对于 `z` 修饰符，期望的实参类型是 [size_t](https://zh.cppreference.com/w/c/types/size_t) 的有符号版本。 |  `signed char`  |     `short`      |     `int`      |     `long`      |     `long long`      |  [intmax_t](https://zh.cppreference.com/w/c/types/integer)   |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) | 不适用        |
|                             `o`                              | ​	转换**无符号整数**为八进制表示 *oooo*。*精度* ﻿指定出现数字的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现* ﻿中精度按需增加，以写入一个前导零。在此情况下如果被转换值和精度都是 `0`，那么写入单个 `0`。 | `unsigned char` | `unsigned short` | `unsigned int` | `unsigned long` | `unsigned long long` |  [uintmax_t](https://zh.cppreference.com/w/c/types/integer)  | [size_t](https://zh.cppreference.com/w/c/types/size_t) | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) 的无符号版本 | 不适用        |
|                           `x` `X`                            | ​	转换**无符号整数**为十六进制表示 *hhhh*。`x` 转换使用字母 `abcdef`。`X` 转换使用 `ABCDEF`。*精度*指定出现数位的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现中* ﻿如果被转换值非零，那么结果有 `0x` 或 `0X` 前缀。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                             `u`                              | ​	转换**无符号整数**为十进制表示 *dddd*。*精度* ﻿指定出现的数位最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                        `f` `F` (C99)                         | ​	转换**浮点数**为 *[-]ddd.ddd* 样式的十进制记法。*精度* ﻿指定小数点字符后出现的确切数位数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |    `double`    | `double` (C99)  |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | `long double` |
|                           `e` `E`                            | ​	转换**浮点数**为十进制指数记法。`e` 转换样式使用 *[-]d.ddd* ﻿`e`*±dd*。`E` 转换样式使用 *[-]d.ddd* ﻿`E`*±dd*。指数至少含两个数位，仅当需要时才使用更多数位。如果值是 `0`，那么指数也是 `0`。*精度* ﻿指定小数点字符后出现数位的最小个数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                 `a` `A`​	(C99)                 | ​	转换**浮点数**为十六进制指数记法。`a` 转换样式使用 *[-]* ﻿`0x`*h.hhh* ﻿`p`*±d*。`A` 转换样式使用 *[-]* ﻿`0X`*h.hhh* ﻿`P`*±d*。如果参数是正规化的浮点数，那么首个十六进制数位非 `0`。如果值是 `0`，那么指数也是 `0`。*精度*指定小数点字符后出现数位的最小个数。默认精度足以精确表示该值。在*替用实现*中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                           `g` `G`                            | ​	转换**浮点数**为十进制小数或十进制指数记法，依赖于值和*精度*。`g` 转换样式将进行带样式 `e` 或 `f` 的转换。`G` 转换样式将进行带样式 `E` 或 `f`(C99 前)`F`(C99 起) 的转换。令 `P` 等于精度，如果它非零，那么精度在未指定时是 `6`，如果精度是 `0` 那么等于 `1`。然后，如果带样式 `E` 的转换会有指数 `X`，那么：如果 *P > X ≥ −4*，那么转换带 `f` 或 `F`(C99 起) 风格，及精度 *P − 1 − X*。否则，转换带 `e` 或 `E` 风格，及精度 *P − 1*。除非要求*替用表示*，否则末尾零会被移除，且在不留下小数部分时小数点也会被移除。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                             `n`                              | ​	返回对函数的此调用迄今为止**写入的字符数**。结果被*写入* ﻿到实参所指向的值。该指示不可含有任何*标签*、*域宽* ﻿或*精度*。对于 `z` 修饰符，实参类型是 `S*`，其中 `S` 是 `[size_t](http://zh.cppreference.com/w/c/types/size_t)` 的有符号版本。 | `signed char*`  |     `short*`     |     `int*`     |     `long*`     |     `long long*`     | [intmax_t](https://zh.cppreference.com/w/c/types/integer)`*` |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)`*` | 不适用        |
|                             `p`                              |          写入定义了**指针**的由实现定义的字符序列。          |     不适用      |      不适用      |    `void*`     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             注解                             |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| ​	浮点数转换函数转换无穷大为 `inf` 或 `infinity`。由实现定义使用其中哪一个。​	非数转换成 `nan` 或 `nan(*char_sequence*)`。由实现定义使用其中哪一个。​	转换 `F`、`E`、`G`、`A` 替代上面输出 `INF`、`INFINITY`、`NAN`。​	用于打印 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short` 的转换指示符实际期待[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)后的类型，但在打印前会转换到 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short`。直接向函数传递这些类型的值是安全的，因为在调用变参数函数时会发生提升。​	定宽字符类型（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确转换指示在标头 [`<inttypes.h>`](https://zh.cppreference.com/w/c/header/inttypes) 定义（尽管 [PRIdMAX](https://zh.cppreference.com/w/c/types/integer)、[PRIuMAX](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。​	内存写入转换指示符 `%n` 是安全漏洞的常见目标，这里格式字符串依赖用户输入，而有边界检查的 `printf_s` 系列函数不支持此转换指示符(C11 起)。​	在每个转换指示符的行动后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许于同一变量多次存入 `%n` 的结果，并在同一此调用中打印出先前以 `%n` 存储的值。​	如果转换指示非法，那么行为未定义。 |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |

**返回值**

1,2) 传输到输出流的字符数，或若出现输出错误或编码错误（对于字符串和字符转换说明符）则为负值。

3） 写入到 `buffer` 的字符数（不计空终止字符），或若输出错误或编码错误（对于字符串和字符转换说明符）发生则为负值。

4） 假如忽略 `bufsz` 则本应写入到 `buffer` 的字符数（不计空终止字符），或若出现输出错误或编码错误（对于字符串和字符转换说明符）则为负值。

5,6) 传输到输出流的字符数，或若出现输出错误、运行时制约违规错误或编码错误则为负值。

7） 写入到 `buffer` 的字符数，不计空终止字符（只要 `buffer` 不是空指针且 `bufsz` 非零且不大于 RSIZE_MAX，就写入它），在运行时制约违规时为零，而在编码错误时为负值。

8） 假如忽略 `bufsz` 则本应写入 `buffer` 的字符数的，不包含空终止字符（只要 `buffer` 不是空指针而 `bufsz` 非零且不大于 RSIZE_MAX，就写入它），或若出现输出错误、运行时制约违规错误或编码错误则为负值。

**注解**

​	C 标准及 [POSIX](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fprintf.html) 指定 `sprintf` 及其变体的行为在参数与目标缓冲区重叠时未定义。示例：

```
sprintf(dst, "%s and %s", dst, t); // <- 有错：未定义行为
```

​	[POSIX 规定](http://pubs.opengroup.org/onlinepubs/9699919799/functions/fprintf.html)在错误时设置 [errno](https://zh.cppreference.com/w/c/error/errno)。它还规定额外的转换指示，最值得注意的是对实参重排序的支持（紧随 `%` 后的 `n$` 指示第 `n` 个实参）。

​	以零为 `bufsz` 和空指针为 `buffer` 调用 `snprintf` 可用于决定包含输出的缓冲区大小：

```
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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.6.1 The fprintf function （第 TBD 页）

  - 7.21.6.3 The printf function （第 TBD 页）

  - 7.21.6.5 The snprintf function （第 TBD 页）

  - 7.21.6.6 The sprintf function （第 TBD 页）

  - K.3.5.3.1 The fprintf_s function （第 TBD 页）

  - K.3.5.3.3 The printf_s function （第 TBD 页）

  - K.3.5.3.5 The snprintf_s function （第 TBD 页）

  - K.3.5.3.6 The sprintf_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.6.1 The fprintf function （第 225-230 页）

  - 7.21.6.3 The printf function （第 236 页）

  - 7.21.6.5 The snprintf function （第 237 页）

  - 7.21.6.6 The sprintf function （第 237 页）

  - K.3.5.3.1 The fprintf_s function （第 430 页）

  - K.3.5.3.3 The printf_s function （第 432 页）

  - K.3.5.3.5 The snprintf_s function （第 432-433 页）

  - K.3.5.3.6 The sprintf_s function （第 433 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.6.1 The fprintf function （第 309-316 页）

  - 7.21.6.3 The printf function （第 324 页）

  - 7.21.6.5 The snprintf function （第 325 页）

  - 7.21.6.6 The sprintf function （第 325-326 页）

  - K.3.5.3.1 The fprintf_s function （第 591 页）

  - K.3.5.3.3 The printf_s function （第 593-594 页）

  - K.3.5.3.5 The snprintf_s function （第 594-595 页）

  - K.3.5.3.6 The sprintf_s function （第 595-596 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.6.1 The fprintf function （第 274-282 页）

  - 7.19.6.3 The printf function （第 290 页）

  - 7.19.6.5 The snprintf function （第 290-291 页）

  - 7.19.6.6 The sprintf function （第 291 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.6.1 The fprintf function

  - 4.9.6.3 The printf function

  - 4.9.6.5 The sprintf function

**参阅**

| [wprintf (C95)<br />fwprintf (C95)<br />swprintf (C95)<br />wprintf_s (C95)<br />fwprintf_s (C95)<br />swprintf_s (C95)<br />snwprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fwprintf) | 打印格式化宽字符输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [vprintf <br />vfprintf <br />vsprintf <br />vsnprintf (C99)<br />vprintf_s (C99)<br />vfprintf_s (C11)<br />vsprintf_s (C11)<br />vsnprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/vfprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 使用可变参数列表 (函数) |
| [fputs<br />](https://zh.cppreference.com/w/c/io/fputs)    | 将一个字符串写入文件流 (函数)                                |
| [scanf <br />fscanf <br />sscanf <br />scanf_s (C11)<br />fscanf_s (C11)<br />sscanf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fscanf) | 从[stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 (函数) |
| **printf, fprintf, sprintf, snprintf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fprintf)** |                                                              |





### snprintf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### sprintf

原址：[http://zh.cppreference.com/w/c/io/fprintf](http://zh.cppreference.com/w/c/io/fprintf)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
// (1)
int printf( const char*          format, ... );// (C99 前)
int printf( const char* restrict format, ... );// (C99 起)
// (2)
int fprintf( FILE*          stream, const char*          format, ... );// (C99 前)
int fprintf( FILE* restrict stream, const char* restrict format, ... );// (C99 起)
// (3)
int sprintf( char*          buffer, const char*          format, ... );// (C99 前)
int sprintf( char* restrict buffer, const char* restrict format, ... );// (C99 起)
int snprintf( char* restrict buffer, size_t bufsz,
              const char* restrict format, ... );// (4)(C99 起)
int printf_s( const char* restrict format, ... );// (5)(C11 起)
int fprintf_s( FILE* restrict stream, const char* restrict format, ... );// (6)(C11 起)
int sprintf_s( char* restrict buffer, rsize_t bufsz,
               const char* restrict format, ... );// (7)(C11 起)
int snprintf_s( char* restrict buffer, rsize_t bufsz,
                const char* restrict format, ... );// (8)(C11 起)
```

​	从给定位置加载数据，转换为字符串等价物，并写结果到各种池。

1） 将结果写入输出流 [stdout](https://zh.cppreference.com/w/c/io)。

2） 将结果写入输出流 `stream`。

3） 将结果写入字符串 `buffer`。如果所写入的字符串（加上终止空字符）超出由 `buffer` 所指向的数组的大小，则行为未定义。

4） 将结果写入字符串 `buffer`。至多写 `bufsz - 1` 个字符。产生的字符串会以空字符终止，除非 `bufsz` 为零。若 `bufsz` 为零，则不写入任何内容，且 `buffer` 可以是空指针，然而依旧计算返回值（会写入的字符数，不包含空终止符）并返回。

5-8) 同 (1-4) ，除了在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `format` 中存在转换说明符 `%n`
  - 任何一个对应 `%s` 的参数是空指针
  - `stream`、`format` 或 `buffer` 是空指针
  - `bufsz` 为零或大于 RSIZE_MAX
  - 在任何一个字符串及字符转换说明符中出现编码错误
  - （仅对于 `sprintf_s` ）存储于 `buffer` 的字符串（包括尾随空字符）长度将超出 `bufsz`

**参数**

| stream | -    | 要写入的输出文件流                                           |
| ------ | ---- | ------------------------------------------------------------ |
| buffer | -    | 指向要写入的字符串的指针                                     |
| bufsz  | -    | 最多会写入 `bufsz - 1` 个字符，再加空终止符                  |
| format | -    | 指向指定数据转换方式的空终止多字节字符串的指针               |
| ...    | -    | 指定要打印数据的参数。若任何[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)后的参数不拥有对应转换说明所期待的类型（期待类型是提升后的类型或者提升后类型的兼容类型），或若参数数量少于 `format` 的要求，则行为未定义。若有多于 `format` 要求的参数，则求值并忽略多出的参数。 |

​	**格式**字符串由普通多字节字符（除了 `%`）和转换指示构成，前者被不改动地复制到输出流。每个转换指示均拥有下列格式：

  - 引入的 `%` 字符。

  - (可选) 一或多个修改转换行为的标志：
  - `-`：转换结果在域内左对齐（默认为右对齐）。
  - `+`：有符号转换的符号始终前置于转换结果（默认仅当结果为负时前置负号）。
  - *空格*：如果有符号转换的结果不以符号开始，或为空，那么前置空格于结果。存在 `+` 标志时忽略*空格*。
  - `#`：进行*替用形式* ﻿的转换。确切的效果见下表，其他情况下行为未定义。
  - `0`：对于整数和浮点数转换，使用前导零代替*空格* ﻿字符填充字段。对于整数，如果显式指定了精度，那么忽略此标志。对于其他转换，使用此标志导致未定义行为。存在 `-` 标志时忽略 `0`。

  - (可选) 整数或 `*`，指定最小字段宽度。如果有要求，那么结果会以*空格* ﻿字符（默认情况）填充，在右对齐时于左，左对齐时于右。使用 `*` 的情况下，以一个额外的 `int` 类型实参指定宽度。如果实参值是负数，那么它导致指定 `-` 标志和正的字段宽度。（注意：这是最小宽度：值决不会被截断）。

  - (可选) 后随整数或 `*` 或两者皆无的 `.`，指示转换的*精度* ﻿。在使用 `*` 的情况下，*精度* ﻿由额外的 `int` 类型的实参指定。如果此实参的值是负数，那么它被忽略。如果既不使用数字也不使用 `*`，那么精度采用零。*精度* ﻿的确切效果见下表。

  - (可选) 指定实参大小的*长度修饰符*（其与格式指示符组合，指定对应实参的类型）。

  - 转换格式指示符

​	下列格式指示符可用：

|                          转换指示符                          |                             解释                             | 期望的实参类型  |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :-------------: | :--------------: | :------------: | :-------------: | :------------------: | :----------------------------------------------------------: | :----------------------------------------------------: | :----------------------------------------------------------: | ------------- |
|                         长度修饰符→                          |                              hh                              |        h        |        无        |       l        |       ll        |          j           |                              z                               |                           t                            |                              L                               |               |
|                       仅从 C99 起可用→                       |                              是                              |                 |                  |                |       是        |          是          |                              是                              |                           是                           |                                                              |               |
|                             `%`                              | ​	写入字面的 `%`。完整的转换指示必须是 `%%`。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `c`                              | ​	写入**单个字符**。实参首先被转换成 `unsigned char`。如果使用 **l** 修饰符，那么实参首先被转换成字符串，如同通过以 `wchar_t[2]` 实参使用 **%ls**。 |     不适用      |      不适用      |     `int`      |     wint_t      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `s`                              | ​	写入**字符串**。实参必须是指向字符数组首元素的指针。*精度* ﻿指定写入最大的字符数。如果没有指定*精度*，那么写每个字节直到而不含首个空终止符。如果使用 **l** 指示符，那么实参必须是指向 `wchar_t` 数组首元素的指针，数组会被转换成 `char` 数组，如同通过以零初始化转换状态调用 [wcrtomb](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb)。 |     不适用      |      不适用      |    `char*`     |   `wchar_t*`    |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                           `d` `i`                            | ​	转换**有符号整数**为十进制表示 *[-]dddd*。*精度* ﻿指定出现的最小数位数。默认精度是 `1`。如果被转换的值和精度都是 `0`，那么转换结果无字符。对于 `z` 修饰符，期望的实参类型是 [size_t](https://zh.cppreference.com/w/c/types/size_t) 的有符号版本。 |  `signed char`  |     `short`      |     `int`      |     `long`      |     `long long`      |  [intmax_t](https://zh.cppreference.com/w/c/types/integer)   |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) | 不适用        |
|                             `o`                              | ​	转换**无符号整数**为八进制表示 *oooo*。*精度* ﻿指定出现数字的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现* ﻿中精度按需增加，以写入一个前导零。在此情况下如果被转换值和精度都是 `0`，那么写入单个 `0`。 | `unsigned char` | `unsigned short` | `unsigned int` | `unsigned long` | `unsigned long long` |  [uintmax_t](https://zh.cppreference.com/w/c/types/integer)  | [size_t](https://zh.cppreference.com/w/c/types/size_t) | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) 的无符号版本 | 不适用        |
|                           `x` `X`                            | ​	转换**无符号整数**为十六进制表示 *hhhh*。`x` 转换使用字母 `abcdef`。`X` 转换使用 `ABCDEF`。*精度*指定出现数位的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现中* ﻿如果被转换值非零，那么结果有 `0x` 或 `0X` 前缀。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                             `u`                              | ​	转换**无符号整数**为十进制表示 *dddd*。*精度* ﻿指定出现的数位最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                        `f` `F` (C99)                         | ​	转换**浮点数**为 *[-]ddd.ddd* 样式的十进制记法。*精度* ﻿指定小数点字符后出现的确切数位数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |    `double`    | `double` (C99)  |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | `long double` |
|                           `e` `E`                            | ​	转换**浮点数**为十进制指数记法。`e` 转换样式使用 *[-]d.ddd* ﻿`e`*±dd*。`E` 转换样式使用 *[-]d.ddd* ﻿`E`*±dd*。指数至少含两个数位，仅当需要时才使用更多数位。如果值是 `0`，那么指数也是 `0`。*精度* ﻿指定小数点字符后出现数位的最小个数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                 `a` `A`​	(C99)                 | ​	转换**浮点数**为十六进制指数记法。`a` 转换样式使用 *[-]* ﻿`0x`*h.hhh* ﻿`p`*±d*。`A` 转换样式使用 *[-]* ﻿`0X`*h.hhh* ﻿`P`*±d*。如果参数是正规化的浮点数，那么首个十六进制数位非 `0`。如果值是 `0`，那么指数也是 `0`。*精度*指定小数点字符后出现数位的最小个数。默认精度足以精确表示该值。在*替用实现*中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                           `g` `G`                            | ​	转换**浮点数**为十进制小数或十进制指数记法，依赖于值和*精度*。`g` 转换样式将进行带样式 `e` 或 `f` 的转换。`G` 转换样式将进行带样式 `E` 或 `f`(C99 前)`F`(C99 起) 的转换。令 `P` 等于精度，如果它非零，那么精度在未指定时是 `6`，如果精度是 `0` 那么等于 `1`。然后，如果带样式 `E` 的转换会有指数 `X`，那么：如果 *P > X ≥ −4*，那么转换带 `f` 或 `F`(C99 起) 风格，及精度 *P − 1 − X*。否则，转换带 `e` 或 `E` 风格，及精度 *P − 1*。除非要求*替用表示*，否则末尾零会被移除，且在不留下小数部分时小数点也会被移除。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/fprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                             `n`                              | ​	返回对函数的此调用迄今为止**写入的字符数**。结果被*写入* ﻿到实参所指向的值。该指示不可含有任何*标签*、*域宽* ﻿或*精度*。对于 `z` 修饰符，实参类型是 `S*`，其中 `S` 是 `[size_t](http://zh.cppreference.com/w/c/types/size_t)` 的有符号版本。 | `signed char*`  |     `short*`     |     `int*`     |     `long*`     |     `long long*`     | [intmax_t](https://zh.cppreference.com/w/c/types/integer)`*` |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)`*` | 不适用        |
|                             `p`                              |          写入定义了**指针**的由实现定义的字符序列。          |     不适用      |      不适用      |    `void*`     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             注解                             |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| ​	浮点数转换函数转换无穷大为 `inf` 或 `infinity`。由实现定义使用其中哪一个。​	非数转换成 `nan` 或 `nan(*char_sequence*)`。由实现定义使用其中哪一个。​	转换 `F`、`E`、`G`、`A` 替代上面输出 `INF`、`INFINITY`、`NAN`。​	用于打印 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short` 的转换指示符实际期待[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)后的类型，但在打印前会转换到 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short`。直接向函数传递这些类型的值是安全的，因为在调用变参数函数时会发生提升。​	定宽字符类型（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确转换指示在标头 [`<inttypes.h>`](https://zh.cppreference.com/w/c/header/inttypes) 定义（尽管 [PRIdMAX](https://zh.cppreference.com/w/c/types/integer)、[PRIuMAX](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。​	内存写入转换指示符 `%n` 是安全漏洞的常见目标，这里格式字符串依赖用户输入，而有边界检查的 `printf_s` 系列函数不支持此转换指示符(C11 起)。​	在每个转换指示符的行动后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许于同一变量多次存入 `%n` 的结果，并在同一此调用中打印出先前以 `%n` 存储的值。​	如果转换指示非法，那么行为未定义。 |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |

**返回值**

1,2) 传输到输出流的字符数，或若出现输出错误或编码错误（对于字符串和字符转换说明符）则为负值。

3） 写入到 `buffer` 的字符数（不计空终止字符），或若输出错误或编码错误（对于字符串和字符转换说明符）发生则为负值。

4） 假如忽略 `bufsz` 则本应写入到 `buffer` 的字符数（不计空终止字符），或若出现输出错误或编码错误（对于字符串和字符转换说明符）则为负值。

5,6) 传输到输出流的字符数，或若出现输出错误、运行时制约违规错误或编码错误则为负值。

7） 写入到 `buffer` 的字符数，不计空终止字符（只要 `buffer` 不是空指针且 `bufsz` 非零且不大于 RSIZE_MAX，就写入它），在运行时制约违规时为零，而在编码错误时为负值。

8） 假如忽略 `bufsz` 则本应写入 `buffer` 的字符数的，不包含空终止字符（只要 `buffer` 不是空指针而 `bufsz` 非零且不大于 RSIZE_MAX，就写入它），或若出现输出错误、运行时制约违规错误或编码错误则为负值。

**注解**

​	C 标准及 [POSIX](https://pubs.opengroup.org/onlinepubs/9699919799/functions/fprintf.html) 指定 `sprintf` 及其变体的行为在参数与目标缓冲区重叠时未定义。示例：

```
sprintf(dst, "%s and %s", dst, t); // <- 有错：未定义行为
```

​	[POSIX 规定](http://pubs.opengroup.org/onlinepubs/9699919799/functions/fprintf.html)在错误时设置 [errno](https://zh.cppreference.com/w/c/error/errno)。它还规定额外的转换指示，最值得注意的是对实参重排序的支持（紧随 `%` 后的 `n$` 指示第 `n` 个实参）。

​	以零为 `bufsz` 和空指针为 `buffer` 调用 `snprintf` 可用于决定包含输出的缓冲区大小：

```
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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.6.1 The fprintf function （第 TBD 页）

  - 7.21.6.3 The printf function （第 TBD 页）

  - 7.21.6.5 The snprintf function （第 TBD 页）

  - 7.21.6.6 The sprintf function （第 TBD 页）

  - K.3.5.3.1 The fprintf_s function （第 TBD 页）

  - K.3.5.3.3 The printf_s function （第 TBD 页）

  - K.3.5.3.5 The snprintf_s function （第 TBD 页）

  - K.3.5.3.6 The sprintf_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.6.1 The fprintf function （第 225-230 页）

  - 7.21.6.3 The printf function （第 236 页）

  - 7.21.6.5 The snprintf function （第 237 页）

  - 7.21.6.6 The sprintf function （第 237 页）

  - K.3.5.3.1 The fprintf_s function （第 430 页）

  - K.3.5.3.3 The printf_s function （第 432 页）

  - K.3.5.3.5 The snprintf_s function （第 432-433 页）

  - K.3.5.3.6 The sprintf_s function （第 433 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.6.1 The fprintf function （第 309-316 页）

  - 7.21.6.3 The printf function （第 324 页）

  - 7.21.6.5 The snprintf function （第 325 页）

  - 7.21.6.6 The sprintf function （第 325-326 页）

  - K.3.5.3.1 The fprintf_s function （第 591 页）

  - K.3.5.3.3 The printf_s function （第 593-594 页）

  - K.3.5.3.5 The snprintf_s function （第 594-595 页）

  - K.3.5.3.6 The sprintf_s function （第 595-596 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.6.1 The fprintf function （第 274-282 页）

  - 7.19.6.3 The printf function （第 290 页）

  - 7.19.6.5 The snprintf function （第 290-291 页）

  - 7.19.6.6 The sprintf function （第 291 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.6.1 The fprintf function

  - 4.9.6.3 The printf function

  - 4.9.6.5 The sprintf function

**参阅**

| [wprintf (C95)<br />fwprintf (C95)<br />swprintf (C95)<br />wprintf_s (C95)<br />fwprintf_s (C95)<br />swprintf_s (C95)<br />snwprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fwprintf) | 打印格式化宽字符输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [vprintf <br />vfprintf <br />vsprintf <br />vsnprintf (C99)<br />vprintf_s (C99)<br />vfprintf_s (C11)<br />vsprintf_s (C11)<br />vsnprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/vfprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 使用可变参数列表 (函数) |
| [fputs<br />](https://zh.cppreference.com/w/c/io/fputs)    | 将一个字符串写入文件流 (函数)                                |
| [scanf <br />fscanf <br />sscanf <br />scanf_s (C11)<br />fscanf_s (C11)<br />sscanf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fscanf) | 从[stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 (函数) |
| **printf, fprintf, sprintf, snprintf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fprintf)** |                                                              |





### sprintf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### sscanf

原址：[http://zh.cppreference.com/w/c/io/fscanf](http://zh.cppreference.com/w/c/io/fscanf)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
// (1)
int scanf( const char          *format, ... );// (C99 前)
int scanf( const char *restrict format, ... );// (C99 起)
// (2)
int fscanf( FILE          *stream, const char          *format, ... );// (C99 前)
int fscanf( FILE *restrict stream, const char *restrict format, ... );// (C99 起)
// (3)
int sscanf( const char          *buffer, const char          *format, ... );// (C99 前)
int sscanf( const char *restrict buffer, const char *restrict format, ... );// (C99 起)
int scanf_s(const char *restrict format, ...);// (4)(C11 起)
int fscanf_s(FILE *restrict stream, const char *restrict format, ...);// (5)(C11 起)
int sscanf_s(const char *restrict buffer, const char *restrict format, ...);// (6)(C11 起)
```

​	从各种资源读取数据，按照 `format` 转译，并将结果存储到指定位置。

1） 从 [stdin](https://zh.cppreference.com/w/c/io) 读取数据

2） 从文件流 `stream` 读取数据

3） 从空终止字符串 `buffer` 读取数据。抵达字符串结尾等价于 `fscanf` 的抵达文件尾条件

4-6) 同 (1-3) ，除了 `%c` 、 `%s` 及 `%[` 转换指示符要求二个参数（通常的指针和指示获取用数组大小的 rsize_t 类型的值，在以 %c 读取单个字符时可以为 1 ），并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - 任何指针类型的参数为空指针
  - `format` 、 `stream` 或 `buffer` 为空指针
  - `%c` 、 `%s` 或 `%[` 会写入的字符数，加上空终止字符，要超过提供给这些转换指示符的第二个（ rsize_t ）参数
  - 可选，任何其他可检测错误，例如未知转换指示符

**参数**

| stream | -    | 要读取的输入文件流                       |
| ------ | ---- | ---------------------------------------- |
| buffer | -    | 指向要读取的空终止字符串的指针           |
| format | -    | 指向指定读取输入方式的空终止字符串的指针 |
| ...    | -    | 各接收实参                               |

- 非空白多字节字符，除了 `%`：每个格式字符串中的这种字符处理一个来自输入流的完全相同的字符，或在它与流的下个字符比较不相等时导致函数失败。
- 空白字符：任何格式字符串中的单个空白字符处理所有来自输入的可用连续空白字符（如同通过于循环中调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 确定）。注意，格式字符串中 ``"\n"``、`" "`、`"**\t****\t**"` 或其他空白无区别。
- 转换指示：每个转换指示拥有下列格式：

  - 引入用 `%` 字符

  - (可选) 赋值抑制字符 `*`。如果存在此选项，那么此函数不将结果赋值给任何接收用实参。

  - (可选) 指定*最大字段宽度* ﻿的整数数字（大于零），即函数进行在当前转换指示所指定的转换时，允许处理的最大字符数。注意如果没有提供宽度，那么 `%s` 和 `%[` 可能导致缓冲区溢出。

  - (可选) 指定接收实参大小的*长度修饰符*，即实际目标类型。这影响转换准确性和溢出规则。默认目标类型对每个转换类型有所不同（见下表）。

  - 转换格式指示符。

​	下列格式指示符可用：

|                          转换指示符                          |                             解释                             |           期望的实参类型           |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :--------------------------------: | :----------------------------------: | :------------------------------: | :--------------------------------: | :------------------------------------------: | :----------------------------------------------------------: | :------------------------------------------------------: | :----------------------------------------------------------: | -------------- |
|                         长度修饰符→                          |                              hh                              |                 h                  |                  无                  |                l                 |                 ll                 |                      j                       |                              z                               |                            t                             |                              L                               |                |
|                       仅从 C99 起可用→                       |                              是                              |                                    |                                      |                                  |                 是                 |                      是                      |                              是                              |                            是                            |                                                              |                |
|                             `%`                              |                      匹配字面 `%`。                      |               不适用               |                不适用                |              不适用              |               不适用               |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             `c`                              | ​	匹配一个**字符**或**字符**的序列。如果使用了宽度指示符，那么匹配恰好*宽度*个字符（该实参必须是指向有充足空间的数组的指针）。与 %s 和 %[ 不同，它不会在数组后附加空字符。 |               不适用               |                不适用                |             `char*`              |             `wchar_t*`             |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             `s`                              | ​	匹配非空白字符的序列（一个**字符串**）。如果使用宽度指示符，那么至多匹配*宽度*个字符，或匹配到首个提前出现的空白符前。总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                        `[`*集合* ﻿`]`                         | ​	匹配*集合* ﻿中的字符的一个非空字符序列。如果集合的首字符是 `^`，那么匹配所有不在集合中的字符。如果集合以 `]` 或 `^]` 开始，那么 `]` 字符也会被包含入集合。在扫描集合的非最初位置的字符 `-` 是否可以指示范围，如 `[0-9]`，由实现定义。如果使用宽度指示符，那么最多匹配到*宽度*。总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `d`                              | ​	匹配一个**十进制整数**。该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 `10` 为 `base` 时期望的格式相同。 | `signed char*` 或 `unsigned char*` | `signed short*` 或 `unsigned short*` | `signed int*` 或 `unsigned int*` | `signed long*` 或 `unsigned long*` | `signed long long*` 或 `unsigned long long*` | `[intmax_t](http://zh.cppreference.com/w/c/types/integer)*` 或 `[uintmax_t](http://zh.cppreference.com/w/c/types/integer)*` | `[size_t](http://zh.cppreference.com/w/c/types/size_t)*` | `[ptrdiff_t](http://zh.cppreference.com/w/c/types/ptrdiff_t)*` | 不适用         |
|                             `i`                              | ​	匹配一个**整数**。该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 `0` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `u`                              | ​	匹配一个无符号**十进制整数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `10` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `o`                              | ​	匹配一个无符号**八进制数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `8` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                           `x` `X`                            | ​	匹配一个无符号**十六进制整数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `16` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `n`                              | ​	返回**迄今读取的字符数**。不消耗输出。不增加赋值计数。如果此指示符拥有赋值抑制运算符，那么行为未定义。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|      `a` (C99) `A` (C99) `e` `E` `f` `F` (C99) `g` `G`       | ​	匹配一个**浮点数**。该数的格式与 [strtof](https://zh.cppreference.com/w/c/string/byte/strtof) 期望的格式相同。 |               不适用               |                不适用                |             `float*`             |             `double*`              |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | `long double*` |
|                             `p`                              | ​	匹配定义了一个**指针**的由实现定义的字符序列。`printf` 系列函数使用 `%p` 格式指示符时应该产生同样的序列。 |               不适用               |                不适用                |             `void**`             |               不适用               |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             注解                             |                                                              |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
| ​	对于每个 `n` 以外的转换指示符，不超过任何指定字段宽度，且要么恰好是转换指示符所期待，要么是其所期待的前缀的最长输入字符序列，即是从流中消耗的内容。此消耗序列后的首个字符如果存在，那么保持未读取。如果被消耗序列长度为零，或被消耗序列不能转换成上面所指定的项目，那么发生匹配失败，除非遇到文件尾、编码错误，或阻止从流输入的读取错误，此情况下此为输入失败。​	所有异于 `[`、`c` 和 `n` 的转换指示符，在尝试分析输入前消耗并舍弃所有前导空白字符（如同以调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 来确定）。这些被消耗的字符不计入指定的最大字段宽度。​	转换指示符 `lc`、`ls` 和 `l[` 进行多字节到宽字符转换，如同如同在转换首字符前，通过用初始化为零的 [mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 对象调用 [mbrtowc](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc)。​	转换指示符 `s` 与 `[` 始终在匹配字符之后存储一个空字符。目标数组的大小必须至少比指定字段宽度大一。未指定目标数组大小时，对 `%s` 或 `%[` 的使用，与 [gets](https://zh.cppreference.com/w/c/io/gets) 同样不安全。​	[定宽整数类型](https://zh.cppreference.com/w/c/types/integer)（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确的转换指示在标头 [](https://zh.cppreference.com/w/c/types/integer) 定义（虽然 [`<CNdMA>`](https://zh.cppreference.com/w/c/types/integer)、[`<CNuMA>`](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。​	在每个转换指示符后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许存储多个字段到同一“池”变量中。​	在分析以无数字指数为结尾的不完整浮点数，如以转换指示符 `%f` 分析 `"100er"` 时，消耗序列 `"100e"` （可能为合法浮点数的最长前缀），并导致匹配错误（被消耗序列不能转换成浮点数），而留下 `"r"`。某些既存实现不遵守此规则并回滚，通过消耗 `"100"` 而留下 `"er"`，例如 [glibc 漏洞 1765](https://sourceware.org/bugzilla/show_bug.cgi?id=1765)。​	如果转换指示非法，那么行为未定义。 |                                                              |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |

**返回值**

1-3) 被成功赋值的接收参数的数量（可以为零，在首个接收用参数赋值前就发生匹配失败的情况下），或者若在首个接收用参数赋值前就发生输入失败，则为 [EOF](https://zh.cppreference.com/w/c/io)。

4-6) 同 (1-3) ，除了当发生运行时制约违规时，亦返回 [EOF](https://zh.cppreference.com/w/c/io)。

**复杂度**

​	无保证。需要注意的是，有些 `sscanf` 的实现为 *O(N)*，其中 `N = [strlen](http://zh.cppreference.com/w/c/string/byte/strlen)(buffer)` [[1\]](https://sourceware.org/bugzilla/show_bug.cgi?id=17577)。

**注解**

​	因为多数转换指示符首先消耗掉所有连续空白符，如下的代码

```
scanf("%d", &a);
scanf("%d", &b);
```

​	将读取在不同行上（第二个 %d 会消耗第一个剩下的换行符）或同一行由空格或制表符分隔（第二个 %d 会消耗空格或制表符）的整数。

​	不消耗前导空白符的转换指示符，如 `%c`，可以通过在格式字符串中前置一个空白符令它如此：

```
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

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.6.2 The fscanf function （第 231-236 页）

  - 7.21.6.4 The scanf function （第 236-237 页）

  - 7.21.6.7 The sscanf function （第 238-239 页）

  - K.3.5.3.2 The fscanf_s function （第 430-431 页）

  - K.3.5.3.4 The scanf_s function （第 432 页）

  - K.3.5.3.7 The sscanf_s function （第 433 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.6.2 The fscanf function （第 317-324 页）

  - 7.21.6.4 The scanf function （第 325 页）

  - 7.21.6.7 The sscanf function （第 326 页）

  - K.3.5.3.2 The fscanf_s function （第 592-593 页）

  - K.3.5.3.4 The scanf_s function （第 594 页）

  - K.3.5.3.7 The sscanf_s function （第 596 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.6.2 The fscanf function （第 282-289 页）

  - 7.19.6.4 The scanf function （第 290 页）

  - 7.19.6.7 The sscanf function （第 291 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.6.2 The fscanf function

  - 4.9.6.4 The scanf function

  - 4.9.6.6 The sscanf function

**参阅**

| [vscanf (C99)<br />vfscanf (C99)<br />vsscanf (C99)<br />vscanf_s (C99)<br />vfscanf_s (C99)<br />vsscanf_s (C99)<br />](https://zh.cppreference.com/w/c/io/vfscanf) | 从 [stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 使用可变参数列表 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [fgets<br />](https://zh.cppreference.com/w/c/io/fgets)    | 从文件流获取一个字符串 (函数)                                |
| [printf <br />fprintf <br />sprintf <br />snprintf (C99)<br />printf_s (C99)<br />fprintf_s (C11)<br />sprintf_s (C11)<br />snprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 (函数) |
| **scanf, fscanf, sscanf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/fscanf)** |                                                              |





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
```c
// 在标头 <stdio.h> 定义
int ungetc( int ch, FILE* stream );
```

​	若 `ch` 不等于 [EOF](https://zh.cppreference.com/w/c/io)，则推入字符 `ch`（转译为 `unsigned char`）到与流 `stream` 关联的输入缓冲区，方式满足从 `stream` 的后继读取操作将取得该字符。不修改与流关联的外部设备。

​	流重寻位操作 [fseek](https://zh.cppreference.com/w/c/io/fseek)、[fsetpos](https://zh.cppreference.com/w/c/io/fsetpos) 和 [rewind](https://zh.cppreference.com/w/c/io/rewind) 弃去 `ungetc` 的效果。

​	若多次调用 `ungetc` 而无介入其间的读取或重寻位，则可能失败（换言之，保证大小为 1 的回放缓冲区，但任何更大的缓冲区是实现定义的）。若成功进行多次 `ungetc` ，则读取操作以 `ungetc` 的逆序取得回放的字符。

​	若 `ch` 等于 [EOF](https://zh.cppreference.com/w/c/io)，则操作失败而不影响流。

​	对 `ungetc` 的成功调用清除文件尾状态标志 [feof](https://zh.cppreference.com/w/c/io/feof)。

​	在二进制流上对 `ungetc` 的成功调用将流位置指示器减少一（若流位置指示器为零，则行为不确定）。

​	在文本流上对 `ungetc` 的成功调用以未指定方式修改流位置指示器，但保证在以读取操作取得所有回放字符后，流位置指示器等于其在 `ungetc` 之前的值。

**参数**

| ch     | -    | 要推入输入流缓冲区的字符 |
| ------ | ---- | ------------------------ |
| stream | -    | 要回放字符到的文件流     |

**返回值**

​	成功时返回 `ch`。

​	失败时返回 [EOF](https://zh.cppreference.com/w/c/io)，而给定的流保持不变。

**注解**

​	实践中，回放缓冲区的大小会在 4k（Linux、MacOS）和 4（Solaris）或保证的最小值 1（HPUX、AIX）间变化。

​	若回放的字符等于存在于外部字符序列中该位置的字符，则回放缓冲区的表观大小可以更大（实现可以简单地自减读取的文件位置指示器，并避免维护回放缓冲区）。

**示例**

​	展示 `ungetc` 的原目的：实现 [scanf](https://zh.cppreference.com/w/c/io/fscanf)

```c
#include <ctype.h>
#include <stdio.h>
 
void demo_scanf(const char* fmt, FILE* s)
{
    while (*fmt != '\0')
    {
        if (*fmt == '%')
        {
            int c;
            switch (*++fmt)
            {
                case 'u':
                    while (isspace(c=getc(s))) {}
                    unsigned int num = 0;
                    while (isdigit(c))
                    {
                        num = num*10 + c-'0';
                        c = getc(s);
                    }
                    printf("%%u scanned %u\n", num);
                    ungetc(c, s);
                    break;
                case 'c':
                    c = getc(s);
                    printf("%%c scanned '%c'\n", c);
                    break;
            }
        }
        else
            ++fmt;
    }
}
 
int main(void)
{
    FILE* f = fopen("input.txt", "w+");
    if (f != NULL)
    {
        fputs("123x", f);
        rewind(f);
        demo_scanf("%u%c", f);
        fclose(f);
    }
    return 0;
}
```

​	输出：

```txt
%u scanned 123
%c scanned 'x'
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.7.10 The ungetc function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.7.10 The ungetc function （第 243 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.7.10 The ungetc function （第 334 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.7.11 The ungetc function （第 300 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.7.11 The ungetc function

**参阅**

| [fgetc<br />getc<br />](https://zh.cppreference.com/w/c/io/fgetc) | 从文件流获取一个字符 (函数) |
| ------------------------------------------------------------ | --------------------------- |
| **ungetc** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/ungetc)** |                             |





### vfprintf

原址：[http://zh.cppreference.com/w/c/io/vfprintf](http://zh.cppreference.com/w/c/io/vfprintf)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
// (1)
int vprintf( const char *format, va_list vlist );// (C99 前)
int vprintf( const char *restrict format, va_list vlist );// (C99 起)
// (2)
int vfprintf( FILE *stream, const char *format, va_list vlist );// (C99 前)
int vfprintf( FILE *restrict stream, const char *restrict format, 
              va_list vlist );// (C99 起)
// (3)
int vsprintf( char *buffer, const char *format, va_list vlist );// (C99 前)
int vsprintf( char *restrict buffer, const char *restrict format, 
              va_list vlist );// (C99 起)
int vsnprintf( char *restrict buffer, size_t bufsz, 
               const char *restrict format, va_list vlist );// (4)(C99 起)
int vprintf_s( const char *restrict format, va_list vlist );// (5)(C11 起)
int vfprintf_s( FILE *restrict stream, const char *restrict format,
                va_list vlist );// (6)(C11 起)
int vsprintf_s( char *restrict buffer, rsize_t bufsz,
                const char *restrict format, va_list vlist );// (7)(C11 起)
int vsnprintf_s( char *restrict buffer, rsize_t bufsz,
                 const char *restrict format, va_list vlist );// (8)(C11 起)
```

​	从 `vlist` 所定义的位置加载数据，将它们转换成字符串等价物，并将结果写入各种池。

1） 将结果写入 [stdout](https://zh.cppreference.com/w/c/io)。

2） 将结果写入文件流 `stream`。

3） 将结果写入字符串 `buffer`。

4） 将结果写入字符串 `buffer`。至多写入 `bufsz - 1` 个字符。产生的字符串将以空字符终止，除非 `bufsz` 为零。若 `bufsz` 为零，则不写入任何内容，且 `buffer` 可为空指针，然而照样计算并返回返回值（本应写入的字节数，不包含空终止符）。

5-8) 同 (1-4)，除了在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `format` 中存在转换说明符 `%n`
  - 任何一个对应 `%s` 的参数是空指针
  - `format` 或 `buffer` 是空指针
  - `bufsz` 为零或大于 RSIZE_MAX
  - 任何一个字符串及字符转换说明符中出现编码错误
  - （仅对于 `vsprintf_s`）存储于 `buffer` 的字符串（包括尾随空字符）长度将超出 `bufsz`

同所有边界检查函数，`vprintf_s`、`vfprintf_s`、`vsprintf_s` 与 `vsnprintf_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。

**参数**

| stream | -    | 要写入的输出文件流                              |
| ------ | ---- | ----------------------------------------------- |
| buffer | -    | 指向要写入的字符串的指针                        |
| bufsz  | -    | 至多可以写入 `bufsz - 1` 个字符，再加上空终止符 |
| format | -    | 指向指定数据转译方式的空终止字符串的指针        |
| vlist  | -    | 包含要打印数据的变量参数列表                    |

​	**格式**字符串由普通多字节字符（除了 `%`）和转换指示构成，前者被不改动地复制到输出流。每个转换指示均拥有下列格式：

  - 引入的 `%` 字符。

  - (可选) 一或多个修改转换行为的标志：
  - `-`：转换结果在域内左对齐（默认为右对齐）。
  - `+`：有符号转换的符号始终前置于转换结果（默认仅当结果为负时前置负号）。
  - *空格*：如果有符号转换的结果不以符号开始，或为空，那么前置空格于结果。存在 `+` 标志时忽略*空格*。
  - `#`：进行*替用形式* ﻿的转换。确切的效果见下表，其他情况下行为未定义。
  - `0`：对于整数和浮点数转换，使用前导零代替*空格* ﻿字符填充字段。对于整数，如果显式指定了精度，那么忽略此标志。对于其他转换，使用此标志导致未定义行为。存在 `-` 标志时忽略 `0`。

  - (可选) 整数或 `*`，指定最小字段宽度。如果有要求，那么结果会以*空格* ﻿字符（默认情况）填充，在右对齐时于左，左对齐时于右。使用 `*` 的情况下，以一个额外的 `int` 类型实参指定宽度。如果实参值是负数，那么它导致指定 `-` 标志和正的字段宽度。（注意：这是最小宽度：值决不会被截断）。

  - (可选) 后随整数或 `*` 或两者皆无的 `.`，指示转换的*精度* ﻿。在使用 `*` 的情况下，*精度* ﻿由额外的 `int` 类型的实参指定。如果此实参的值是负数，那么它被忽略。如果既不使用数字也不使用 `*`，那么精度采用零。*精度* ﻿的确切效果见下表。

  - (可选) 指定实参大小的*长度修饰符*（其与格式指示符组合，指定对应实参的类型）。

  - 转换格式指示符

​	下列格式指示符可用：

|                          转换指示符                          |                             解释                             | 期望的实参类型  |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :-------------: | :--------------: | :------------: | :-------------: | :------------------: | :----------------------------------------------------------: | :----------------------------------------------------: | :----------------------------------------------------------: | ------------- |
|                         长度修饰符→                          |                              hh                              |        h        |        无        |       l        |       ll        |          j           |                              z                               |                           t                            |                              L                               |               |
|                       仅从 C99 起可用→                       |                              是                              |                 |                  |                |       是        |          是          |                              是                              |                           是                           |                                                              |               |
|                             `%`                              | ​	写入字面的 `%`。完整的转换指示必须是 `%%`。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `c`                              | ​	写入**单个字符**。实参首先被转换成 `unsigned char`。如果使用 **l** 修饰符，那么实参首先被转换成字符串，如同通过以 `wchar_t[2]` 实参使用 **%ls**。 |     不适用      |      不适用      |     `int`      |     wint_t      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `s`                              | ​	写入**字符串**。实参必须是指向字符数组首元素的指针。*精度* ﻿指定写入最大的字符数。如果没有指定*精度*，那么写每个字节直到而不含首个空终止符。如果使用 **l** 指示符，那么实参必须是指向 `wchar_t` 数组首元素的指针，数组会被转换成 `char` 数组，如同通过以零初始化转换状态调用 [wcrtomb](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb)。 |     不适用      |      不适用      |    `char*`     |   `wchar_t*`    |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                           `d` `i`                            | ​	转换**有符号整数**为十进制表示 *[-]dddd*。*精度* ﻿指定出现的最小数位数。默认精度是 `1`。如果被转换的值和精度都是 `0`，那么转换结果无字符。对于 `z` 修饰符，期望的实参类型是 [size_t](https://zh.cppreference.com/w/c/types/size_t) 的有符号版本。 |  `signed char`  |     `short`      |     `int`      |     `long`      |     `long long`      |  [intmax_t](https://zh.cppreference.com/w/c/types/integer)   |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) | 不适用        |
|                             `o`                              | ​	转换**无符号整数**为八进制表示 *oooo*。*精度* ﻿指定出现数字的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现* ﻿中精度按需增加，以写入一个前导零。在此情况下如果被转换值和精度都是 `0`，那么写入单个 `0`。 | `unsigned char` | `unsigned short` | `unsigned int` | `unsigned long` | `unsigned long long` |  [uintmax_t](https://zh.cppreference.com/w/c/types/integer)  | [size_t](https://zh.cppreference.com/w/c/types/size_t) | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) 的无符号版本 | 不适用        |
|                           `x` `X`                            | ​	转换**无符号整数**为十六进制表示 *hhhh*。`x` 转换使用字母 `abcdef`。`X` 转换使用 `ABCDEF`。*精度*指定出现数位的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现中* ﻿如果被转换值非零，那么结果有 `0x` 或 `0X` 前缀。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                             `u`                              | ​	转换**无符号整数**为十进制表示 *dddd*。*精度* ﻿指定出现的数位最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                        `f` `F` (C99)                         | ​	转换**浮点数**为 *[-]ddd.ddd* 样式的十进制记法。*精度* ﻿指定小数点字符后出现的确切数位数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |    `double`    | `double` (C99)  |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | `long double` |
|                           `e` `E`                            | ​	转换**浮点数**为十进制指数记法。`e` 转换样式使用 *[-]d.ddd* ﻿`e`*±dd*。`E` 转换样式使用 *[-]d.ddd* ﻿`E`*±dd*。指数至少含两个数位，仅当需要时才使用更多数位。如果值是 `0`，那么指数也是 `0`。*精度* ﻿指定小数点字符后出现数位的最小个数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                 `a` `A`​	(C99)                 | ​	转换**浮点数**为十六进制指数记法。`a` 转换样式使用 *[-]* ﻿`0x`*h.hhh* ﻿`p`*±d*。`A` 转换样式使用 *[-]* ﻿`0X`*h.hhh* ﻿`P`*±d*。如果参数是正规化的浮点数，那么首个十六进制数位非 `0`。如果值是 `0`，那么指数也是 `0`。*精度*指定小数点字符后出现数位的最小个数。默认精度足以精确表示该值。在*替用实现*中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                           `g` `G`                            | ​	转换**浮点数**为十进制小数或十进制指数记法，依赖于值和*精度*。`g` 转换样式将进行带样式 `e` 或 `f` 的转换。`G` 转换样式将进行带样式 `E` 或 `f`(C99 前)`F`(C99 起) 的转换。令 `P` 等于精度，如果它非零，那么精度在未指定时是 `6`，如果精度是 `0` 那么等于 `1`。然后，如果带样式 `E` 的转换会有指数 `X`，那么：如果 *P > X ≥ −4*，那么转换带 `f` 或 `F`(C99 起) 风格，及精度 *P − 1 − X*。否则，转换带 `e` 或 `E` 风格，及精度 *P − 1*。除非要求*替用表示*，否则末尾零会被移除，且在不留下小数部分时小数点也会被移除。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                             `n`                              | ​	返回对函数的此调用迄今为止**写入的字符数**。结果被*写入* ﻿到实参所指向的值。该指示不可含有任何*标签*、*域宽* ﻿或*精度*。对于 `z` 修饰符，实参类型是 `S*`，其中 `S` 是 `[size_t](http://zh.cppreference.com/w/c/types/size_t)` 的有符号版本。 | `signed char*`  |     `short*`     |     `int*`     |     `long*`     |     `long long*`     | [intmax_t](https://zh.cppreference.com/w/c/types/integer)`*` |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)`*` | 不适用        |
|                             `p`                              |          写入定义了**指针**的由实现定义的字符序列。          |     不适用      |      不适用      |    `void*`     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             注解                             |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| ​	浮点数转换函数转换无穷大为 `inf` 或 `infinity`。由实现定义使用其中哪一个。​	非数转换成 `nan` 或 `nan(*char_sequence*)`。由实现定义使用其中哪一个。​	转换 `F`、`E`、`G`、`A` 替代上面输出 `INF`、`INFINITY`、`NAN`。​	用于打印 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short` 的转换指示符实际期待[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)后的类型，但在打印前会转换到 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short`。直接向函数传递这些类型的值是安全的，因为在调用变参数函数时会发生提升。​	定宽字符类型（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确转换指示在标头 [`<inttypes.h>`](https://zh.cppreference.com/w/c/header/inttypes) 定义（尽管 [PRIdMAX](https://zh.cppreference.com/w/c/types/integer)、[PRIuMAX](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。​	内存写入转换指示符 `%n` 是安全漏洞的常见目标，这里格式字符串依赖用户输入，而有边界检查的 `printf_s` 系列函数不支持此转换指示符(C11 起)。​	在每个转换指示符的行动后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许于同一变量多次存入 `%n` 的结果，并在同一此调用中打印出先前以 `%n` 存储的值。​	如果转换指示非法，那么行为未定义。 |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |

**返回值**

1-3) 若成功则为写入的字符数，若出现错误则为负值。

4） 若成功则为写入的字符数，若出现错误则为负值。若产生的字符串因 `bufsz` 限制被截断，函数返回假如未强加限制则本应写入的字符数（不包含空终止字节）。

5,6) 传输到输出流的字符数，或若输出错误、运行时制约违规错误、编码错误发生则为负值。

7） 写入 `buffer` 的字符数，不计空字符（只要 `buffer` 不是空指针且 `bufsz` 非零且不大于 RSIZE_MAX，就会写入它），运行时制约违规时为零，编码错误发生时为负值。

8） 不含空终止字符的（只要 `buffer` 不是空指针且 `bufsz` 非零且不大于 RSIZE_MAX，就会写入它）假如忽略 `bufsz` 则本应写入 `buffer` 的字符数，或若出现运行时制约违规或编码错误为负值。

**注解**

​	所有这些函数调用 va_arg 至少一次，返回后 `vlist` 的值不确定。这些函数不调用 va_end，而这必须由调用方进行。

​	不同于 `vsprintf_s`，`vsnprintf_s` 将截断结果以适应 `buffer` 所指向的数组。

​	[Microsoft CRT](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l) 中的 `vsnprintf_s` 实现不符合 C 标准。微软的版本有一个额外的第三形参 `[size_t](http://zh.cppreference.com/w/c/types/size_t) count`，它包含所要写入的不包括空终止符的最大字符数量。这个形参可能与通过形参 `[size_t](http://zh.cppreference.com/w/c/types/size_t) bufsz` 提供的缓冲区大小有所区别。

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

​	可能的输出：

```txt
02/20/15 21:58:09.072683 UTC [debug]: Logging, 1, 2, 3
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.6.8 The vfprintf function （第 TBD 页）

  - 7.21.6.10 The vprintf function （第 TBD 页）

  - 7.21.6.12 The vsnprintf function （第 TBD 页）

  - 7.21.6.13 The vsprintf function （第 TBD 页）

  - K.3.5.3.8 The vfprintf_s function （第 TBD 页）

  - K.3.5.3.10 The vprintf_s function （第 TBD 页）

  - K.3.5.3.12 The vsnprintf_s function （第 TBD 页）

  - K.3.5.3.13 The vsprintf_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.6.8 The vfprintf function （第 238 页）

  - 7.21.6.10 The vprintf function （第 239 页）

  - 7.21.6.12 The vsnprintf function （第 239-240 页）

  - 7.21.6.13 The vsprintf function （第 240 页）

  - K.3.5.3.8 The vfprintf_s function （第 434 页）

  - K.3.5.3.10 The vprintf_s function （第 435 页）

  - K.3.5.3.12 The vsnprintf_s function （第 436-437 页）

  - K.3.5.3.13 The vsprintf_s function （第 437 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.6.8 The vfprintf function （第 326-327 页）

  - 7.21.6.10 The vprintf function （第 328 页）

  - 7.21.6.12 The vsnprintf function （第 329 页）

  - 7.21.6.13 The vsprintf function （第 329 页）

  - K.3.5.3.8 The vfprintf_s function （第 597 页）

  - K.3.5.3.10 The vprintf_s function （第 598-599 页）

  - K.3.5.3.12 The vsnprintf_s function （第 600 页）

  - K.3.5.3.13 The vsprintf_s function （第 601 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.6.8 The vfprintf function （第 292 页）

  - 7.19.6.10 The vprintf function （第 293 页）

  - 7.19.6.12 The vsnprintf function （第 294 页）

  - 7.19.6.13 The vsprintf function （第 295 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.6.7 The vfprintf function

  - 4.9.6.8 The vprintf function

  - 4.9.6.9 The vsprintf function

**参阅**

| [vwprintf (C95)<br />vfwprintf (C95)<br />vswprintf (C95)<br />vwprintf_s (C95)<br />vfwprintf_s (C95)<br />vswprintf_s (C95)<br />vsnwprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/vfwprintf) | 打印格式化宽字符输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 使用可变参数列表 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [printf <br />fprintf <br />sprintf <br />snprintf (C99)<br />printf_s (C99)<br />fprintf_s (C11)<br />sprintf_s (C11)<br />snprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 (函数) |
| [vscanf (C99)<br />vfscanf (C99)<br />vsscanf (C99)<br />vscanf_s (C99)<br />vfscanf_s (C99)<br />vsscanf_s (C99)<br />](https://zh.cppreference.com/w/c/io/vfscanf) | 从 [stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 使用可变参数列表 (函数) |
| **vprintf, vfprintf, vsprintf, vsnprintf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/vfprintf)** |                                                              |





### vfprintf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### vfscanf

原址：[http://zh.cppreference.com/w/c/io/vfscanf](http://zh.cppreference.com/w/c/io/vfscanf)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int vscanf( const char *restrict format, va_list vlist );// (1)(C99 起)
int vfscanf( FILE *restrict stream, const char *restrict format, 
             va_list vlist );// (2)(C99 起)
int vsscanf( const char *restrict buffer, const char *restrict format, 
             va_list vlist );// (3)(C99 起)
int vscanf_s(const char *restrict format, va_list vlist);// (4)(C11 起)
int vfscanf_s( FILE *restrict stream, const char *restrict format,
               va_list vlist);// (5)(C11 起)
int vsscanf_s( const char *restrict buffer, const char *restrict format,
               va_list vlist);// (6)(C11 起)
```

​	从各种源读取数据，按照 `format` 转换并存储结果到 `vlist` 所定义的位置。

1） 从 [stdin](https://zh.cppreference.com/w/c/io) 读取数据。

2） 从文件流 `stream` 读取数据。

3） 从空终止字符串 `buffer` 读取数据。抵达字符串结尾等价于 `vfscanf` 的抵达文件尾条件

4-6) 同 (1-3)，但 `%c`、`%s` 及 `%[` 转换指示符要求两个参数（通常的指针和指示获取用数组大小的 rsize_t 类型值，以 %c 读取单个字符时可以为 1），并且在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - 任何指针类型参数为空指针
  - `format`、`stream` 或 `buffer` 为空指针
  - %c 、 %s 或 %[ 本会写入的字符数，加上空终止字符，要超过提供给这些转换指示符的第二个（rsize_t）参数
  - 可选，任何其他可检测错误，例如未知转换指示符

**参数**

| stream | -    | 要读取的输入文件流                       |
| ------ | ---- | ---------------------------------------- |
| buffer | -    | 指向要读取的空终止字符串的指针           |
| format | -    | 指向指定读取输入方式的空终止字符串的指针 |
| vlist  | -    | 包含接收各实参的可变实参列表             |

- 非空白多字节字符，除了 `%`：每个格式字符串中的这种字符处理一个来自输入流的完全相同的字符，或在它与流的下个字符比较不相等时导致函数失败。
- 空白字符：任何格式字符串中的单个空白字符处理所有来自输入的可用连续空白字符（如同通过于循环中调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 确定）。注意，格式字符串中 ``"\n"``、`" "`、`"**\t****\t**"` 或其他空白无区别。
- 转换指示：每个转换指示拥有下列格式：

  - 引入用 `%` 字符

  - (可选) 赋值抑制字符 `*`。如果存在此选项，那么此函数不将结果赋值给任何接收用实参。

  - (可选) 指定*最大字段宽度* ﻿的整数数字（大于零），即函数进行在当前转换指示所指定的转换时，允许处理的最大字符数。注意如果没有提供宽度，那么 `%s` 和 `%[` 可能导致缓冲区溢出。

  - (可选) 指定接收实参大小的*长度修饰符*，即实际目标类型。这影响转换准确性和溢出规则。默认目标类型对每个转换类型有所不同（见下表）。

  - 转换格式指示符。

​	下列格式指示符可用：

|                          转换指示符                          |                             解释                             |           期望的实参类型           |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :--------------------------------: | :----------------------------------: | :------------------------------: | :--------------------------------: | :------------------------------------------: | :----------------------------------------------------------: | :------------------------------------------------------: | :----------------------------------------------------------: | -------------- |
|                         长度修饰符→                          |                              hh                              |                 h                  |                  无                  |                l                 |                 ll                 |                      j                       |                              z                               |                            t                             |                              L                               |                |
|                       仅从 C99 起可用→                       |                              是                              |                                    |                                      |                                  |                 是                 |                      是                      |                              是                              |                            是                            |                                                              |                |
|                             `%`                              |                      匹配字面 `%`。                      |               不适用               |                不适用                |              不适用              |               不适用               |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             `c`                              | ​	匹配一个**字符**或**字符**的序列。如果使用了宽度指示符，那么匹配恰好*宽度*个字符（该实参必须是指向有充足空间的数组的指针）。与 %s 和 %[ 不同，它不会在数组后附加空字符。 |               不适用               |                不适用                |             `char*`              |             `wchar_t*`             |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             `s`                              | ​	匹配非空白字符的序列（一个**字符串**）。如果使用宽度指示符，那么至多匹配*宽度*个字符，或匹配到首个提前出现的空白符前。总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                        `[`*集合* ﻿`]`                         | ​	匹配*集合* ﻿中的字符的一个非空字符序列。如果集合的首字符是 `^`，那么匹配所有不在集合中的字符。如果集合以 `]` 或 `^]` 开始，那么 `]` 字符也会被包含入集合。在扫描集合的非最初位置的字符 `-` 是否可以指示范围，如 `[0-9]`，由实现定义。如果使用宽度指示符，那么最多匹配到*宽度*。总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `d`                              | ​	匹配一个**十进制整数**。该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 `10` 为 `base` 时期望的格式相同。 | `signed char*` 或 `unsigned char*` | `signed short*` 或 `unsigned short*` | `signed int*` 或 `unsigned int*` | `signed long*` 或 `unsigned long*` | `signed long long*` 或 `unsigned long long*` | `[intmax_t](http://zh.cppreference.com/w/c/types/integer)*` 或 `[uintmax_t](http://zh.cppreference.com/w/c/types/integer)*` | `[size_t](http://zh.cppreference.com/w/c/types/size_t)*` | `[ptrdiff_t](http://zh.cppreference.com/w/c/types/ptrdiff_t)*` | 不适用         |
|                             `i`                              | ​	匹配一个**整数**。该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 `0` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `u`                              | ​	匹配一个无符号**十进制整数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `10` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `o`                              | ​	匹配一个无符号**八进制数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `8` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                           `x` `X`                            | ​	匹配一个无符号**十六进制整数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `16` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `n`                              | ​	返回**迄今读取的字符数**。不消耗输出。不增加赋值计数。如果此指示符拥有赋值抑制运算符，那么行为未定义。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|      `a` (C99) `A` (C99) `e` `E` `f` `F` (C99) `g` `G`       | ​	匹配一个**浮点数**。该数的格式与 [strtof](https://zh.cppreference.com/w/c/string/byte/strtof) 期望的格式相同。 |               不适用               |                不适用                |             `float*`             |             `double*`              |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | `long double*` |
|                             `p`                              | ​	匹配定义了一个**指针**的由实现定义的字符序列。`printf` 系列函数使用 `%p` 格式指示符时应该产生同样的序列。 |               不适用               |                不适用                |             `void**`             |               不适用               |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             注解                             |                                                              |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
| ​	对于每个 `n` 以外的转换指示符，不超过任何指定字段宽度，且要么恰好是转换指示符所期待，要么是其所期待的前缀的最长输入字符序列，即是从流中消耗的内容。此消耗序列后的首个字符如果存在，那么保持未读取。如果被消耗序列长度为零，或被消耗序列不能转换成上面所指定的项目，那么发生匹配失败，除非遇到文件尾、编码错误，或阻止从流输入的读取错误，此情况下此为输入失败。​	所有异于 `[`、`c` 和 `n` 的转换指示符，在尝试分析输入前消耗并舍弃所有前导空白字符（如同以调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 来确定）。这些被消耗的字符不计入指定的最大字段宽度。​	转换指示符 `lc`、`ls` 和 `l[` 进行多字节到宽字符转换，如同如同在转换首字符前，通过用初始化为零的 [mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 对象调用 [mbrtowc](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc)。​	转换指示符 `s` 与 `[` 始终在匹配字符之后存储一个空字符。目标数组的大小必须至少比指定字段宽度大一。未指定目标数组大小时，对 `%s` 或 `%[` 的使用，与 [gets](https://zh.cppreference.com/w/c/io/gets) 同样不安全。​	[定宽整数类型](https://zh.cppreference.com/w/c/types/integer)（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确的转换指示在标头 [](https://zh.cppreference.com/w/c/types/integer) 定义（虽然 [`<CNdMA>`](https://zh.cppreference.com/w/c/types/integer)、[`<CNuMA>`](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。​	在每个转换指示符后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许存储多个字段到同一“池”变量中。​	在分析以无数字指数为结尾的不完整浮点数，如以转换指示符 `%f` 分析 `"100er"` 时，消耗序列 `"100e"` （可能为合法浮点数的最长前缀），并导致匹配错误（被消耗序列不能转换成浮点数），而留下 `"r"`。某些既存实现不遵守此规则并回滚，通过消耗 `"100"` 而留下 `"er"`，例如 [glibc 漏洞 1765](https://sourceware.org/bugzilla/show_bug.cgi?id=1765)。​	如果转换指示非法，那么行为未定义。 |                                                              |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |

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

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.6.9 The vfscanf function （第 327 页）

  - 7.21.6.11 The vscanf function （第 328 页）

  - 7.21.6.14 The vsscanf function （第 330 页）

  - K.3.5.3.9 The vfscanf_s function （第 597-598 页）

  - K.3.5.3.11 The vscanf_s function （第 599 页）

  - K.3.5.3.14 The vsscanf_s function （第 602 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.6.9 The vfscanf function （第 293 页）

  - 7.19.6.11 The vscanf function （第 294 页）

  - 7.19.6.14 The vsscanf function （第 295 页）

**参阅**

| [scanf <br />fscanf <br />sscanf <br />scanf_s (C11)<br />fscanf_s (C11)<br />sscanf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fscanf) | 从[stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [vprintf <br />vfprintf <br />vsprintf <br />vsnprintf (C99)<br />vprintf_s (C99)<br />vfprintf_s (C11)<br />vsprintf_s (C11)<br />vsnprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/vfprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 使用可变参数列表 (函数) |
| **vscanf, vfscanf, vsscanf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/vfscanf)** |                                                              |





### vfscanf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### vprintf

原址：[http://zh.cppreference.com/w/c/io/vfprintf](http://zh.cppreference.com/w/c/io/vfprintf)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
// (1)
int vprintf( const char *format, va_list vlist );// (C99 前)
int vprintf( const char *restrict format, va_list vlist );// (C99 起)
// (2)
int vfprintf( FILE *stream, const char *format, va_list vlist );// (C99 前)
int vfprintf( FILE *restrict stream, const char *restrict format, 
              va_list vlist );// (C99 起)
// (3)
int vsprintf( char *buffer, const char *format, va_list vlist );// (C99 前)
int vsprintf( char *restrict buffer, const char *restrict format, 
              va_list vlist );// (C99 起)
int vsnprintf( char *restrict buffer, size_t bufsz, 
               const char *restrict format, va_list vlist );// (4)(C99 起)
int vprintf_s( const char *restrict format, va_list vlist );// (5)(C11 起)
int vfprintf_s( FILE *restrict stream, const char *restrict format,
                va_list vlist );// (6)(C11 起)
int vsprintf_s( char *restrict buffer, rsize_t bufsz,
                const char *restrict format, va_list vlist );// (7)(C11 起)
int vsnprintf_s( char *restrict buffer, rsize_t bufsz,
                 const char *restrict format, va_list vlist );// (8)(C11 起)
```

​	从 `vlist` 所定义的位置加载数据，将它们转换成字符串等价物，并将结果写入各种池。

1） 将结果写入 [stdout](https://zh.cppreference.com/w/c/io)。

2） 将结果写入文件流 `stream`。

3） 将结果写入字符串 `buffer`。

4） 将结果写入字符串 `buffer`。至多写入 `bufsz - 1` 个字符。产生的字符串将以空字符终止，除非 `bufsz` 为零。若 `bufsz` 为零，则不写入任何内容，且 `buffer` 可为空指针，然而照样计算并返回返回值（本应写入的字节数，不包含空终止符）。

5-8) 同 (1-4)，除了在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `format` 中存在转换说明符 `%n`
  - 任何一个对应 `%s` 的参数是空指针
  - `format` 或 `buffer` 是空指针
  - `bufsz` 为零或大于 RSIZE_MAX
  - 任何一个字符串及字符转换说明符中出现编码错误
  - （仅对于 `vsprintf_s`）存储于 `buffer` 的字符串（包括尾随空字符）长度将超出 `bufsz`

同所有边界检查函数，`vprintf_s`、`vfprintf_s`、`vsprintf_s` 与 `vsnprintf_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。

**参数**

| stream | -    | 要写入的输出文件流                              |
| ------ | ---- | ----------------------------------------------- |
| buffer | -    | 指向要写入的字符串的指针                        |
| bufsz  | -    | 至多可以写入 `bufsz - 1` 个字符，再加上空终止符 |
| format | -    | 指向指定数据转译方式的空终止字符串的指针        |
| vlist  | -    | 包含要打印数据的变量参数列表                    |

​	**格式**字符串由普通多字节字符（除了 `%`）和转换指示构成，前者被不改动地复制到输出流。每个转换指示均拥有下列格式：

  - 引入的 `%` 字符。

  - (可选) 一或多个修改转换行为的标志：
  - `-`：转换结果在域内左对齐（默认为右对齐）。
  - `+`：有符号转换的符号始终前置于转换结果（默认仅当结果为负时前置负号）。
  - *空格*：如果有符号转换的结果不以符号开始，或为空，那么前置空格于结果。存在 `+` 标志时忽略*空格*。
  - `#`：进行*替用形式* ﻿的转换。确切的效果见下表，其他情况下行为未定义。
  - `0`：对于整数和浮点数转换，使用前导零代替*空格* ﻿字符填充字段。对于整数，如果显式指定了精度，那么忽略此标志。对于其他转换，使用此标志导致未定义行为。存在 `-` 标志时忽略 `0`。

  - (可选) 整数或 `*`，指定最小字段宽度。如果有要求，那么结果会以*空格* ﻿字符（默认情况）填充，在右对齐时于左，左对齐时于右。使用 `*` 的情况下，以一个额外的 `int` 类型实参指定宽度。如果实参值是负数，那么它导致指定 `-` 标志和正的字段宽度。（注意：这是最小宽度：值决不会被截断）。

  - (可选) 后随整数或 `*` 或两者皆无的 `.`，指示转换的*精度* ﻿。在使用 `*` 的情况下，*精度* ﻿由额外的 `int` 类型的实参指定。如果此实参的值是负数，那么它被忽略。如果既不使用数字也不使用 `*`，那么精度采用零。*精度* ﻿的确切效果见下表。

  - (可选) 指定实参大小的*长度修饰符*（其与格式指示符组合，指定对应实参的类型）。

  - 转换格式指示符

​	下列格式指示符可用：

|                          转换指示符                          |                             解释                             | 期望的实参类型  |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :-------------: | :--------------: | :------------: | :-------------: | :------------------: | :----------------------------------------------------------: | :----------------------------------------------------: | :----------------------------------------------------------: | ------------- |
|                         长度修饰符→                          |                              hh                              |        h        |        无        |       l        |       ll        |          j           |                              z                               |                           t                            |                              L                               |               |
|                       仅从 C99 起可用→                       |                              是                              |                 |                  |                |       是        |          是          |                              是                              |                           是                           |                                                              |               |
|                             `%`                              | ​	写入字面的 `%`。完整的转换指示必须是 `%%`。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `c`                              | ​	写入**单个字符**。实参首先被转换成 `unsigned char`。如果使用 **l** 修饰符，那么实参首先被转换成字符串，如同通过以 `wchar_t[2]` 实参使用 **%ls**。 |     不适用      |      不适用      |     `int`      |     wint_t      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `s`                              | ​	写入**字符串**。实参必须是指向字符数组首元素的指针。*精度* ﻿指定写入最大的字符数。如果没有指定*精度*，那么写每个字节直到而不含首个空终止符。如果使用 **l** 指示符，那么实参必须是指向 `wchar_t` 数组首元素的指针，数组会被转换成 `char` 数组，如同通过以零初始化转换状态调用 [wcrtomb](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb)。 |     不适用      |      不适用      |    `char*`     |   `wchar_t*`    |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                           `d` `i`                            | ​	转换**有符号整数**为十进制表示 *[-]dddd*。*精度* ﻿指定出现的最小数位数。默认精度是 `1`。如果被转换的值和精度都是 `0`，那么转换结果无字符。对于 `z` 修饰符，期望的实参类型是 [size_t](https://zh.cppreference.com/w/c/types/size_t) 的有符号版本。 |  `signed char`  |     `short`      |     `int`      |     `long`      |     `long long`      |  [intmax_t](https://zh.cppreference.com/w/c/types/integer)   |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) | 不适用        |
|                             `o`                              | ​	转换**无符号整数**为八进制表示 *oooo*。*精度* ﻿指定出现数字的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现* ﻿中精度按需增加，以写入一个前导零。在此情况下如果被转换值和精度都是 `0`，那么写入单个 `0`。 | `unsigned char` | `unsigned short` | `unsigned int` | `unsigned long` | `unsigned long long` |  [uintmax_t](https://zh.cppreference.com/w/c/types/integer)  | [size_t](https://zh.cppreference.com/w/c/types/size_t) | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) 的无符号版本 | 不适用        |
|                           `x` `X`                            | ​	转换**无符号整数**为十六进制表示 *hhhh*。`x` 转换使用字母 `abcdef`。`X` 转换使用 `ABCDEF`。*精度*指定出现数位的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现中* ﻿如果被转换值非零，那么结果有 `0x` 或 `0X` 前缀。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                             `u`                              | ​	转换**无符号整数**为十进制表示 *dddd*。*精度* ﻿指定出现的数位最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                        `f` `F` (C99)                         | ​	转换**浮点数**为 *[-]ddd.ddd* 样式的十进制记法。*精度* ﻿指定小数点字符后出现的确切数位数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |    `double`    | `double` (C99)  |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | `long double` |
|                           `e` `E`                            | ​	转换**浮点数**为十进制指数记法。`e` 转换样式使用 *[-]d.ddd* ﻿`e`*±dd*。`E` 转换样式使用 *[-]d.ddd* ﻿`E`*±dd*。指数至少含两个数位，仅当需要时才使用更多数位。如果值是 `0`，那么指数也是 `0`。*精度* ﻿指定小数点字符后出现数位的最小个数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                 `a` `A`​	(C99)                 | ​	转换**浮点数**为十六进制指数记法。`a` 转换样式使用 *[-]* ﻿`0x`*h.hhh* ﻿`p`*±d*。`A` 转换样式使用 *[-]* ﻿`0X`*h.hhh* ﻿`P`*±d*。如果参数是正规化的浮点数，那么首个十六进制数位非 `0`。如果值是 `0`，那么指数也是 `0`。*精度*指定小数点字符后出现数位的最小个数。默认精度足以精确表示该值。在*替用实现*中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                           `g` `G`                            | ​	转换**浮点数**为十进制小数或十进制指数记法，依赖于值和*精度*。`g` 转换样式将进行带样式 `e` 或 `f` 的转换。`G` 转换样式将进行带样式 `E` 或 `f`(C99 前)`F`(C99 起) 的转换。令 `P` 等于精度，如果它非零，那么精度在未指定时是 `6`，如果精度是 `0` 那么等于 `1`。然后，如果带样式 `E` 的转换会有指数 `X`，那么：如果 *P > X ≥ −4*，那么转换带 `f` 或 `F`(C99 起) 风格，及精度 *P − 1 − X*。否则，转换带 `e` 或 `E` 风格，及精度 *P − 1*。除非要求*替用表示*，否则末尾零会被移除，且在不留下小数部分时小数点也会被移除。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                             `n`                              | ​	返回对函数的此调用迄今为止**写入的字符数**。结果被*写入* ﻿到实参所指向的值。该指示不可含有任何*标签*、*域宽* ﻿或*精度*。对于 `z` 修饰符，实参类型是 `S*`，其中 `S` 是 `[size_t](http://zh.cppreference.com/w/c/types/size_t)` 的有符号版本。 | `signed char*`  |     `short*`     |     `int*`     |     `long*`     |     `long long*`     | [intmax_t](https://zh.cppreference.com/w/c/types/integer)`*` |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)`*` | 不适用        |
|                             `p`                              |          写入定义了**指针**的由实现定义的字符序列。          |     不适用      |      不适用      |    `void*`     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             注解                             |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| ​	浮点数转换函数转换无穷大为 `inf` 或 `infinity`。由实现定义使用其中哪一个。​	非数转换成 `nan` 或 `nan(*char_sequence*)`。由实现定义使用其中哪一个。​	转换 `F`、`E`、`G`、`A` 替代上面输出 `INF`、`INFINITY`、`NAN`。​	用于打印 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short` 的转换指示符实际期待[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)后的类型，但在打印前会转换到 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short`。直接向函数传递这些类型的值是安全的，因为在调用变参数函数时会发生提升。​	定宽字符类型（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确转换指示在标头 [`<inttypes.h>`](https://zh.cppreference.com/w/c/header/inttypes) 定义（尽管 [PRIdMAX](https://zh.cppreference.com/w/c/types/integer)、[PRIuMAX](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。​	内存写入转换指示符 `%n` 是安全漏洞的常见目标，这里格式字符串依赖用户输入，而有边界检查的 `printf_s` 系列函数不支持此转换指示符(C11 起)。​	在每个转换指示符的行动后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许于同一变量多次存入 `%n` 的结果，并在同一此调用中打印出先前以 `%n` 存储的值。​	如果转换指示非法，那么行为未定义。 |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |

**返回值**

1-3) 若成功则为写入的字符数，若出现错误则为负值。

4） 若成功则为写入的字符数，若出现错误则为负值。若产生的字符串因 `bufsz` 限制被截断，函数返回假如未强加限制则本应写入的字符数（不包含空终止字节）。

5,6) 传输到输出流的字符数，或若输出错误、运行时制约违规错误、编码错误发生则为负值。

7） 写入 `buffer` 的字符数，不计空字符（只要 `buffer` 不是空指针且 `bufsz` 非零且不大于 RSIZE_MAX，就会写入它），运行时制约违规时为零，编码错误发生时为负值。

8） 不含空终止字符的（只要 `buffer` 不是空指针且 `bufsz` 非零且不大于 RSIZE_MAX，就会写入它）假如忽略 `bufsz` 则本应写入 `buffer` 的字符数，或若出现运行时制约违规或编码错误为负值。

**注解**

​	所有这些函数调用 va_arg 至少一次，返回后 `vlist` 的值不确定。这些函数不调用 va_end，而这必须由调用方进行。

​	不同于 `vsprintf_s`，`vsnprintf_s` 将截断结果以适应 `buffer` 所指向的数组。

​	[Microsoft CRT](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l) 中的 `vsnprintf_s` 实现不符合 C 标准。微软的版本有一个额外的第三形参 `[size_t](http://zh.cppreference.com/w/c/types/size_t) count`，它包含所要写入的不包括空终止符的最大字符数量。这个形参可能与通过形参 `[size_t](http://zh.cppreference.com/w/c/types/size_t) bufsz` 提供的缓冲区大小有所区别。

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

​	可能的输出：

```txt
02/20/15 21:58:09.072683 UTC [debug]: Logging, 1, 2, 3
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.6.8 The vfprintf function （第 TBD 页）

  - 7.21.6.10 The vprintf function （第 TBD 页）

  - 7.21.6.12 The vsnprintf function （第 TBD 页）

  - 7.21.6.13 The vsprintf function （第 TBD 页）

  - K.3.5.3.8 The vfprintf_s function （第 TBD 页）

  - K.3.5.3.10 The vprintf_s function （第 TBD 页）

  - K.3.5.3.12 The vsnprintf_s function （第 TBD 页）

  - K.3.5.3.13 The vsprintf_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.6.8 The vfprintf function （第 238 页）

  - 7.21.6.10 The vprintf function （第 239 页）

  - 7.21.6.12 The vsnprintf function （第 239-240 页）

  - 7.21.6.13 The vsprintf function （第 240 页）

  - K.3.5.3.8 The vfprintf_s function （第 434 页）

  - K.3.5.3.10 The vprintf_s function （第 435 页）

  - K.3.5.3.12 The vsnprintf_s function （第 436-437 页）

  - K.3.5.3.13 The vsprintf_s function （第 437 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.6.8 The vfprintf function （第 326-327 页）

  - 7.21.6.10 The vprintf function （第 328 页）

  - 7.21.6.12 The vsnprintf function （第 329 页）

  - 7.21.6.13 The vsprintf function （第 329 页）

  - K.3.5.3.8 The vfprintf_s function （第 597 页）

  - K.3.5.3.10 The vprintf_s function （第 598-599 页）

  - K.3.5.3.12 The vsnprintf_s function （第 600 页）

  - K.3.5.3.13 The vsprintf_s function （第 601 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.6.8 The vfprintf function （第 292 页）

  - 7.19.6.10 The vprintf function （第 293 页）

  - 7.19.6.12 The vsnprintf function （第 294 页）

  - 7.19.6.13 The vsprintf function （第 295 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.6.7 The vfprintf function

  - 4.9.6.8 The vprintf function

  - 4.9.6.9 The vsprintf function

**参阅**

| [vwprintf (C95)<br />vfwprintf (C95)<br />vswprintf (C95)<br />vwprintf_s (C95)<br />vfwprintf_s (C95)<br />vswprintf_s (C95)<br />vsnwprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/vfwprintf) | 打印格式化宽字符输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 使用可变参数列表 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [printf <br />fprintf <br />sprintf <br />snprintf (C99)<br />printf_s (C99)<br />fprintf_s (C11)<br />sprintf_s (C11)<br />snprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 (函数) |
| [vscanf (C99)<br />vfscanf (C99)<br />vsscanf (C99)<br />vscanf_s (C99)<br />vfscanf_s (C99)<br />vsscanf_s (C99)<br />](https://zh.cppreference.com/w/c/io/vfscanf) | 从 [stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 使用可变参数列表 (函数) |
| **vprintf, vfprintf, vsprintf, vsnprintf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/vfprintf)** |                                                              |





### vprintf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### vscanf

原址：[http://zh.cppreference.com/w/c/io/vfscanf](http://zh.cppreference.com/w/c/io/vfscanf)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int vscanf( const char *restrict format, va_list vlist );// (1)(C99 起)
int vfscanf( FILE *restrict stream, const char *restrict format, 
             va_list vlist );// (2)(C99 起)
int vsscanf( const char *restrict buffer, const char *restrict format, 
             va_list vlist );// (3)(C99 起)
int vscanf_s(const char *restrict format, va_list vlist);// (4)(C11 起)
int vfscanf_s( FILE *restrict stream, const char *restrict format,
               va_list vlist);// (5)(C11 起)
int vsscanf_s( const char *restrict buffer, const char *restrict format,
               va_list vlist);// (6)(C11 起)
```

​	从各种源读取数据，按照 `format` 转换并存储结果到 `vlist` 所定义的位置。

1） 从 [stdin](https://zh.cppreference.com/w/c/io) 读取数据。

2） 从文件流 `stream` 读取数据。

3） 从空终止字符串 `buffer` 读取数据。抵达字符串结尾等价于 `vfscanf` 的抵达文件尾条件

4-6) 同 (1-3)，但 `%c`、`%s` 及 `%[` 转换指示符要求两个参数（通常的指针和指示获取用数组大小的 rsize_t 类型值，以 %c 读取单个字符时可以为 1），并且在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - 任何指针类型参数为空指针
  - `format`、`stream` 或 `buffer` 为空指针
  - %c 、 %s 或 %[ 本会写入的字符数，加上空终止字符，要超过提供给这些转换指示符的第二个（rsize_t）参数
  - 可选，任何其他可检测错误，例如未知转换指示符

**参数**

| stream | -    | 要读取的输入文件流                       |
| ------ | ---- | ---------------------------------------- |
| buffer | -    | 指向要读取的空终止字符串的指针           |
| format | -    | 指向指定读取输入方式的空终止字符串的指针 |
| vlist  | -    | 包含接收各实参的可变实参列表             |

- 非空白多字节字符，除了 `%`：每个格式字符串中的这种字符处理一个来自输入流的完全相同的字符，或在它与流的下个字符比较不相等时导致函数失败。
- 空白字符：任何格式字符串中的单个空白字符处理所有来自输入的可用连续空白字符（如同通过于循环中调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 确定）。注意，格式字符串中 ``"\n"``、`" "`、`"**\t****\t**"` 或其他空白无区别。
- 转换指示：每个转换指示拥有下列格式：

  - 引入用 `%` 字符

  - (可选) 赋值抑制字符 `*`。如果存在此选项，那么此函数不将结果赋值给任何接收用实参。

  - (可选) 指定*最大字段宽度* ﻿的整数数字（大于零），即函数进行在当前转换指示所指定的转换时，允许处理的最大字符数。注意如果没有提供宽度，那么 `%s` 和 `%[` 可能导致缓冲区溢出。

  - (可选) 指定接收实参大小的*长度修饰符*，即实际目标类型。这影响转换准确性和溢出规则。默认目标类型对每个转换类型有所不同（见下表）。

  - 转换格式指示符。

​	下列格式指示符可用：

|                          转换指示符                          |                             解释                             |           期望的实参类型           |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :--------------------------------: | :----------------------------------: | :------------------------------: | :--------------------------------: | :------------------------------------------: | :----------------------------------------------------------: | :------------------------------------------------------: | :----------------------------------------------------------: | -------------- |
|                         长度修饰符→                          |                              hh                              |                 h                  |                  无                  |                l                 |                 ll                 |                      j                       |                              z                               |                            t                             |                              L                               |                |
|                       仅从 C99 起可用→                       |                              是                              |                                    |                                      |                                  |                 是                 |                      是                      |                              是                              |                            是                            |                                                              |                |
|                             `%`                              |                      匹配字面 `%`。                      |               不适用               |                不适用                |              不适用              |               不适用               |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             `c`                              | ​	匹配一个**字符**或**字符**的序列。如果使用了宽度指示符，那么匹配恰好*宽度*个字符（该实参必须是指向有充足空间的数组的指针）。与 %s 和 %[ 不同，它不会在数组后附加空字符。 |               不适用               |                不适用                |             `char*`              |             `wchar_t*`             |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             `s`                              | ​	匹配非空白字符的序列（一个**字符串**）。如果使用宽度指示符，那么至多匹配*宽度*个字符，或匹配到首个提前出现的空白符前。总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                        `[`*集合* ﻿`]`                         | ​	匹配*集合* ﻿中的字符的一个非空字符序列。如果集合的首字符是 `^`，那么匹配所有不在集合中的字符。如果集合以 `]` 或 `^]` 开始，那么 `]` 字符也会被包含入集合。在扫描集合的非最初位置的字符 `-` 是否可以指示范围，如 `[0-9]`，由实现定义。如果使用宽度指示符，那么最多匹配到*宽度*。总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `d`                              | ​	匹配一个**十进制整数**。该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 `10` 为 `base` 时期望的格式相同。 | `signed char*` 或 `unsigned char*` | `signed short*` 或 `unsigned short*` | `signed int*` 或 `unsigned int*` | `signed long*` 或 `unsigned long*` | `signed long long*` 或 `unsigned long long*` | `[intmax_t](http://zh.cppreference.com/w/c/types/integer)*` 或 `[uintmax_t](http://zh.cppreference.com/w/c/types/integer)*` | `[size_t](http://zh.cppreference.com/w/c/types/size_t)*` | `[ptrdiff_t](http://zh.cppreference.com/w/c/types/ptrdiff_t)*` | 不适用         |
|                             `i`                              | ​	匹配一个**整数**。该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 `0` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `u`                              | ​	匹配一个无符号**十进制整数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `10` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `o`                              | ​	匹配一个无符号**八进制数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `8` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                           `x` `X`                            | ​	匹配一个无符号**十六进制整数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `16` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `n`                              | ​	返回**迄今读取的字符数**。不消耗输出。不增加赋值计数。如果此指示符拥有赋值抑制运算符，那么行为未定义。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|      `a` (C99) `A` (C99) `e` `E` `f` `F` (C99) `g` `G`       | ​	匹配一个**浮点数**。该数的格式与 [strtof](https://zh.cppreference.com/w/c/string/byte/strtof) 期望的格式相同。 |               不适用               |                不适用                |             `float*`             |             `double*`              |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | `long double*` |
|                             `p`                              | ​	匹配定义了一个**指针**的由实现定义的字符序列。`printf` 系列函数使用 `%p` 格式指示符时应该产生同样的序列。 |               不适用               |                不适用                |             `void**`             |               不适用               |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             注解                             |                                                              |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
| ​	对于每个 `n` 以外的转换指示符，不超过任何指定字段宽度，且要么恰好是转换指示符所期待，要么是其所期待的前缀的最长输入字符序列，即是从流中消耗的内容。此消耗序列后的首个字符如果存在，那么保持未读取。如果被消耗序列长度为零，或被消耗序列不能转换成上面所指定的项目，那么发生匹配失败，除非遇到文件尾、编码错误，或阻止从流输入的读取错误，此情况下此为输入失败。​	所有异于 `[`、`c` 和 `n` 的转换指示符，在尝试分析输入前消耗并舍弃所有前导空白字符（如同以调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 来确定）。这些被消耗的字符不计入指定的最大字段宽度。​	转换指示符 `lc`、`ls` 和 `l[` 进行多字节到宽字符转换，如同如同在转换首字符前，通过用初始化为零的 [mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 对象调用 [mbrtowc](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc)。​	转换指示符 `s` 与 `[` 始终在匹配字符之后存储一个空字符。目标数组的大小必须至少比指定字段宽度大一。未指定目标数组大小时，对 `%s` 或 `%[` 的使用，与 [gets](https://zh.cppreference.com/w/c/io/gets) 同样不安全。​	[定宽整数类型](https://zh.cppreference.com/w/c/types/integer)（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确的转换指示在标头 [](https://zh.cppreference.com/w/c/types/integer) 定义（虽然 [`<CNdMA>`](https://zh.cppreference.com/w/c/types/integer)、[`<CNuMA>`](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。​	在每个转换指示符后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许存储多个字段到同一“池”变量中。​	在分析以无数字指数为结尾的不完整浮点数，如以转换指示符 `%f` 分析 `"100er"` 时，消耗序列 `"100e"` （可能为合法浮点数的最长前缀），并导致匹配错误（被消耗序列不能转换成浮点数），而留下 `"r"`。某些既存实现不遵守此规则并回滚，通过消耗 `"100"` 而留下 `"er"`，例如 [glibc 漏洞 1765](https://sourceware.org/bugzilla/show_bug.cgi?id=1765)。​	如果转换指示非法，那么行为未定义。 |                                                              |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |

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

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.6.9 The vfscanf function （第 327 页）

  - 7.21.6.11 The vscanf function （第 328 页）

  - 7.21.6.14 The vsscanf function （第 330 页）

  - K.3.5.3.9 The vfscanf_s function （第 597-598 页）

  - K.3.5.3.11 The vscanf_s function （第 599 页）

  - K.3.5.3.14 The vsscanf_s function （第 602 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.6.9 The vfscanf function （第 293 页）

  - 7.19.6.11 The vscanf function （第 294 页）

  - 7.19.6.14 The vsscanf function （第 295 页）

**参阅**

| [scanf <br />fscanf <br />sscanf <br />scanf_s (C11)<br />fscanf_s (C11)<br />sscanf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fscanf) | 从[stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [vprintf <br />vfprintf <br />vsprintf <br />vsnprintf (C99)<br />vprintf_s (C99)<br />vfprintf_s (C11)<br />vsprintf_s (C11)<br />vsnprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/vfprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 使用可变参数列表 (函数) |
| **vscanf, vfscanf, vsscanf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/vfscanf)** |                                                              |





### vscanf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### vsnprintf

原址：[http://zh.cppreference.com/w/c/io/vfprintf](http://zh.cppreference.com/w/c/io/vfprintf)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
// (1)
int vprintf( const char *format, va_list vlist );// (C99 前)
int vprintf( const char *restrict format, va_list vlist );// (C99 起)
// (2)
int vfprintf( FILE *stream, const char *format, va_list vlist );// (C99 前)
int vfprintf( FILE *restrict stream, const char *restrict format, 
              va_list vlist );// (C99 起)
// (3)
int vsprintf( char *buffer, const char *format, va_list vlist );// (C99 前)
int vsprintf( char *restrict buffer, const char *restrict format, 
              va_list vlist );// (C99 起)
int vsnprintf( char *restrict buffer, size_t bufsz, 
               const char *restrict format, va_list vlist );// (4)(C99 起)
int vprintf_s( const char *restrict format, va_list vlist );// (5)(C11 起)
int vfprintf_s( FILE *restrict stream, const char *restrict format,
                va_list vlist );// (6)(C11 起)
int vsprintf_s( char *restrict buffer, rsize_t bufsz,
                const char *restrict format, va_list vlist );// (7)(C11 起)
int vsnprintf_s( char *restrict buffer, rsize_t bufsz,
                 const char *restrict format, va_list vlist );// (8)(C11 起)
```

​	从 `vlist` 所定义的位置加载数据，将它们转换成字符串等价物，并将结果写入各种池。

1） 将结果写入 [stdout](https://zh.cppreference.com/w/c/io)。

2） 将结果写入文件流 `stream`。

3） 将结果写入字符串 `buffer`。

4） 将结果写入字符串 `buffer`。至多写入 `bufsz - 1` 个字符。产生的字符串将以空字符终止，除非 `bufsz` 为零。若 `bufsz` 为零，则不写入任何内容，且 `buffer` 可为空指针，然而照样计算并返回返回值（本应写入的字节数，不包含空终止符）。

5-8) 同 (1-4)，除了在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `format` 中存在转换说明符 `%n`
  - 任何一个对应 `%s` 的参数是空指针
  - `format` 或 `buffer` 是空指针
  - `bufsz` 为零或大于 RSIZE_MAX
  - 任何一个字符串及字符转换说明符中出现编码错误
  - （仅对于 `vsprintf_s`）存储于 `buffer` 的字符串（包括尾随空字符）长度将超出 `bufsz`

同所有边界检查函数，`vprintf_s`、`vfprintf_s`、`vsprintf_s` 与 `vsnprintf_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。

**参数**

| stream | -    | 要写入的输出文件流                              |
| ------ | ---- | ----------------------------------------------- |
| buffer | -    | 指向要写入的字符串的指针                        |
| bufsz  | -    | 至多可以写入 `bufsz - 1` 个字符，再加上空终止符 |
| format | -    | 指向指定数据转译方式的空终止字符串的指针        |
| vlist  | -    | 包含要打印数据的变量参数列表                    |

​	**格式**字符串由普通多字节字符（除了 `%`）和转换指示构成，前者被不改动地复制到输出流。每个转换指示均拥有下列格式：

  - 引入的 `%` 字符。

  - (可选) 一或多个修改转换行为的标志：
  - `-`：转换结果在域内左对齐（默认为右对齐）。
  - `+`：有符号转换的符号始终前置于转换结果（默认仅当结果为负时前置负号）。
  - *空格*：如果有符号转换的结果不以符号开始，或为空，那么前置空格于结果。存在 `+` 标志时忽略*空格*。
  - `#`：进行*替用形式* ﻿的转换。确切的效果见下表，其他情况下行为未定义。
  - `0`：对于整数和浮点数转换，使用前导零代替*空格* ﻿字符填充字段。对于整数，如果显式指定了精度，那么忽略此标志。对于其他转换，使用此标志导致未定义行为。存在 `-` 标志时忽略 `0`。

  - (可选) 整数或 `*`，指定最小字段宽度。如果有要求，那么结果会以*空格* ﻿字符（默认情况）填充，在右对齐时于左，左对齐时于右。使用 `*` 的情况下，以一个额外的 `int` 类型实参指定宽度。如果实参值是负数，那么它导致指定 `-` 标志和正的字段宽度。（注意：这是最小宽度：值决不会被截断）。

  - (可选) 后随整数或 `*` 或两者皆无的 `.`，指示转换的*精度* ﻿。在使用 `*` 的情况下，*精度* ﻿由额外的 `int` 类型的实参指定。如果此实参的值是负数，那么它被忽略。如果既不使用数字也不使用 `*`，那么精度采用零。*精度* ﻿的确切效果见下表。

  - (可选) 指定实参大小的*长度修饰符*（其与格式指示符组合，指定对应实参的类型）。

  - 转换格式指示符

​	下列格式指示符可用：

|                          转换指示符                          |                             解释                             | 期望的实参类型  |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :-------------: | :--------------: | :------------: | :-------------: | :------------------: | :----------------------------------------------------------: | :----------------------------------------------------: | :----------------------------------------------------------: | ------------- |
|                         长度修饰符→                          |                              hh                              |        h        |        无        |       l        |       ll        |          j           |                              z                               |                           t                            |                              L                               |               |
|                       仅从 C99 起可用→                       |                              是                              |                 |                  |                |       是        |          是          |                              是                              |                           是                           |                                                              |               |
|                             `%`                              | ​	写入字面的 `%`。完整的转换指示必须是 `%%`。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `c`                              | ​	写入**单个字符**。实参首先被转换成 `unsigned char`。如果使用 **l** 修饰符，那么实参首先被转换成字符串，如同通过以 `wchar_t[2]` 实参使用 **%ls**。 |     不适用      |      不适用      |     `int`      |     wint_t      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `s`                              | ​	写入**字符串**。实参必须是指向字符数组首元素的指针。*精度* ﻿指定写入最大的字符数。如果没有指定*精度*，那么写每个字节直到而不含首个空终止符。如果使用 **l** 指示符，那么实参必须是指向 `wchar_t` 数组首元素的指针，数组会被转换成 `char` 数组，如同通过以零初始化转换状态调用 [wcrtomb](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb)。 |     不适用      |      不适用      |    `char*`     |   `wchar_t*`    |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                           `d` `i`                            | ​	转换**有符号整数**为十进制表示 *[-]dddd*。*精度* ﻿指定出现的最小数位数。默认精度是 `1`。如果被转换的值和精度都是 `0`，那么转换结果无字符。对于 `z` 修饰符，期望的实参类型是 [size_t](https://zh.cppreference.com/w/c/types/size_t) 的有符号版本。 |  `signed char`  |     `short`      |     `int`      |     `long`      |     `long long`      |  [intmax_t](https://zh.cppreference.com/w/c/types/integer)   |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) | 不适用        |
|                             `o`                              | ​	转换**无符号整数**为八进制表示 *oooo*。*精度* ﻿指定出现数字的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现* ﻿中精度按需增加，以写入一个前导零。在此情况下如果被转换值和精度都是 `0`，那么写入单个 `0`。 | `unsigned char` | `unsigned short` | `unsigned int` | `unsigned long` | `unsigned long long` |  [uintmax_t](https://zh.cppreference.com/w/c/types/integer)  | [size_t](https://zh.cppreference.com/w/c/types/size_t) | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) 的无符号版本 | 不适用        |
|                           `x` `X`                            | ​	转换**无符号整数**为十六进制表示 *hhhh*。`x` 转换使用字母 `abcdef`。`X` 转换使用 `ABCDEF`。*精度*指定出现数位的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现中* ﻿如果被转换值非零，那么结果有 `0x` 或 `0X` 前缀。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                             `u`                              | ​	转换**无符号整数**为十进制表示 *dddd*。*精度* ﻿指定出现的数位最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                        `f` `F` (C99)                         | ​	转换**浮点数**为 *[-]ddd.ddd* 样式的十进制记法。*精度* ﻿指定小数点字符后出现的确切数位数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |    `double`    | `double` (C99)  |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | `long double` |
|                           `e` `E`                            | ​	转换**浮点数**为十进制指数记法。`e` 转换样式使用 *[-]d.ddd* ﻿`e`*±dd*。`E` 转换样式使用 *[-]d.ddd* ﻿`E`*±dd*。指数至少含两个数位，仅当需要时才使用更多数位。如果值是 `0`，那么指数也是 `0`。*精度* ﻿指定小数点字符后出现数位的最小个数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                 `a` `A`​	(C99)                 | ​	转换**浮点数**为十六进制指数记法。`a` 转换样式使用 *[-]* ﻿`0x`*h.hhh* ﻿`p`*±d*。`A` 转换样式使用 *[-]* ﻿`0X`*h.hhh* ﻿`P`*±d*。如果参数是正规化的浮点数，那么首个十六进制数位非 `0`。如果值是 `0`，那么指数也是 `0`。*精度*指定小数点字符后出现数位的最小个数。默认精度足以精确表示该值。在*替用实现*中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                           `g` `G`                            | ​	转换**浮点数**为十进制小数或十进制指数记法，依赖于值和*精度*。`g` 转换样式将进行带样式 `e` 或 `f` 的转换。`G` 转换样式将进行带样式 `E` 或 `f`(C99 前)`F`(C99 起) 的转换。令 `P` 等于精度，如果它非零，那么精度在未指定时是 `6`，如果精度是 `0` 那么等于 `1`。然后，如果带样式 `E` 的转换会有指数 `X`，那么：如果 *P > X ≥ −4*，那么转换带 `f` 或 `F`(C99 起) 风格，及精度 *P − 1 − X*。否则，转换带 `e` 或 `E` 风格，及精度 *P − 1*。除非要求*替用表示*，否则末尾零会被移除，且在不留下小数部分时小数点也会被移除。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                             `n`                              | ​	返回对函数的此调用迄今为止**写入的字符数**。结果被*写入* ﻿到实参所指向的值。该指示不可含有任何*标签*、*域宽* ﻿或*精度*。对于 `z` 修饰符，实参类型是 `S*`，其中 `S` 是 `[size_t](http://zh.cppreference.com/w/c/types/size_t)` 的有符号版本。 | `signed char*`  |     `short*`     |     `int*`     |     `long*`     |     `long long*`     | [intmax_t](https://zh.cppreference.com/w/c/types/integer)`*` |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)`*` | 不适用        |
|                             `p`                              |          写入定义了**指针**的由实现定义的字符序列。          |     不适用      |      不适用      |    `void*`     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             注解                             |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| ​	浮点数转换函数转换无穷大为 `inf` 或 `infinity`。由实现定义使用其中哪一个。​	非数转换成 `nan` 或 `nan(*char_sequence*)`。由实现定义使用其中哪一个。​	转换 `F`、`E`、`G`、`A` 替代上面输出 `INF`、`INFINITY`、`NAN`。​	用于打印 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short` 的转换指示符实际期待[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)后的类型，但在打印前会转换到 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short`。直接向函数传递这些类型的值是安全的，因为在调用变参数函数时会发生提升。​	定宽字符类型（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确转换指示在标头 [`<inttypes.h>`](https://zh.cppreference.com/w/c/header/inttypes) 定义（尽管 [PRIdMAX](https://zh.cppreference.com/w/c/types/integer)、[PRIuMAX](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。​	内存写入转换指示符 `%n` 是安全漏洞的常见目标，这里格式字符串依赖用户输入，而有边界检查的 `printf_s` 系列函数不支持此转换指示符(C11 起)。​	在每个转换指示符的行动后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许于同一变量多次存入 `%n` 的结果，并在同一此调用中打印出先前以 `%n` 存储的值。​	如果转换指示非法，那么行为未定义。 |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |

**返回值**

1-3) 若成功则为写入的字符数，若出现错误则为负值。

4） 若成功则为写入的字符数，若出现错误则为负值。若产生的字符串因 `bufsz` 限制被截断，函数返回假如未强加限制则本应写入的字符数（不包含空终止字节）。

5,6) 传输到输出流的字符数，或若输出错误、运行时制约违规错误、编码错误发生则为负值。

7） 写入 `buffer` 的字符数，不计空字符（只要 `buffer` 不是空指针且 `bufsz` 非零且不大于 RSIZE_MAX，就会写入它），运行时制约违规时为零，编码错误发生时为负值。

8） 不含空终止字符的（只要 `buffer` 不是空指针且 `bufsz` 非零且不大于 RSIZE_MAX，就会写入它）假如忽略 `bufsz` 则本应写入 `buffer` 的字符数，或若出现运行时制约违规或编码错误为负值。

**注解**

​	所有这些函数调用 va_arg 至少一次，返回后 `vlist` 的值不确定。这些函数不调用 va_end，而这必须由调用方进行。

​	不同于 `vsprintf_s`，`vsnprintf_s` 将截断结果以适应 `buffer` 所指向的数组。

​	[Microsoft CRT](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l) 中的 `vsnprintf_s` 实现不符合 C 标准。微软的版本有一个额外的第三形参 `[size_t](http://zh.cppreference.com/w/c/types/size_t) count`，它包含所要写入的不包括空终止符的最大字符数量。这个形参可能与通过形参 `[size_t](http://zh.cppreference.com/w/c/types/size_t) bufsz` 提供的缓冲区大小有所区别。

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

​	可能的输出：

```txt
02/20/15 21:58:09.072683 UTC [debug]: Logging, 1, 2, 3
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.6.8 The vfprintf function （第 TBD 页）

  - 7.21.6.10 The vprintf function （第 TBD 页）

  - 7.21.6.12 The vsnprintf function （第 TBD 页）

  - 7.21.6.13 The vsprintf function （第 TBD 页）

  - K.3.5.3.8 The vfprintf_s function （第 TBD 页）

  - K.3.5.3.10 The vprintf_s function （第 TBD 页）

  - K.3.5.3.12 The vsnprintf_s function （第 TBD 页）

  - K.3.5.3.13 The vsprintf_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.6.8 The vfprintf function （第 238 页）

  - 7.21.6.10 The vprintf function （第 239 页）

  - 7.21.6.12 The vsnprintf function （第 239-240 页）

  - 7.21.6.13 The vsprintf function （第 240 页）

  - K.3.5.3.8 The vfprintf_s function （第 434 页）

  - K.3.5.3.10 The vprintf_s function （第 435 页）

  - K.3.5.3.12 The vsnprintf_s function （第 436-437 页）

  - K.3.5.3.13 The vsprintf_s function （第 437 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.6.8 The vfprintf function （第 326-327 页）

  - 7.21.6.10 The vprintf function （第 328 页）

  - 7.21.6.12 The vsnprintf function （第 329 页）

  - 7.21.6.13 The vsprintf function （第 329 页）

  - K.3.5.3.8 The vfprintf_s function （第 597 页）

  - K.3.5.3.10 The vprintf_s function （第 598-599 页）

  - K.3.5.3.12 The vsnprintf_s function （第 600 页）

  - K.3.5.3.13 The vsprintf_s function （第 601 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.6.8 The vfprintf function （第 292 页）

  - 7.19.6.10 The vprintf function （第 293 页）

  - 7.19.6.12 The vsnprintf function （第 294 页）

  - 7.19.6.13 The vsprintf function （第 295 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.6.7 The vfprintf function

  - 4.9.6.8 The vprintf function

  - 4.9.6.9 The vsprintf function

**参阅**

| [vwprintf (C95)<br />vfwprintf (C95)<br />vswprintf (C95)<br />vwprintf_s (C95)<br />vfwprintf_s (C95)<br />vswprintf_s (C95)<br />vsnwprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/vfwprintf) | 打印格式化宽字符输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 使用可变参数列表 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [printf <br />fprintf <br />sprintf <br />snprintf (C99)<br />printf_s (C99)<br />fprintf_s (C11)<br />sprintf_s (C11)<br />snprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 (函数) |
| [vscanf (C99)<br />vfscanf (C99)<br />vsscanf (C99)<br />vscanf_s (C99)<br />vfscanf_s (C99)<br />vsscanf_s (C99)<br />](https://zh.cppreference.com/w/c/io/vfscanf) | 从 [stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 使用可变参数列表 (函数) |
| **vprintf, vfprintf, vsprintf, vsnprintf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/vfprintf)** |                                                              |





### vsnprintf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### vsprintf

原址：[http://zh.cppreference.com/w/c/io/vfprintf](http://zh.cppreference.com/w/c/io/vfprintf)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
// (1)
int vprintf( const char *format, va_list vlist );// (C99 前)
int vprintf( const char *restrict format, va_list vlist );// (C99 起)
// (2)
int vfprintf( FILE *stream, const char *format, va_list vlist );// (C99 前)
int vfprintf( FILE *restrict stream, const char *restrict format, 
              va_list vlist );// (C99 起)
// (3)
int vsprintf( char *buffer, const char *format, va_list vlist );// (C99 前)
int vsprintf( char *restrict buffer, const char *restrict format, 
              va_list vlist );// (C99 起)
int vsnprintf( char *restrict buffer, size_t bufsz, 
               const char *restrict format, va_list vlist );// (4)(C99 起)
int vprintf_s( const char *restrict format, va_list vlist );// (5)(C11 起)
int vfprintf_s( FILE *restrict stream, const char *restrict format,
                va_list vlist );// (6)(C11 起)
int vsprintf_s( char *restrict buffer, rsize_t bufsz,
                const char *restrict format, va_list vlist );// (7)(C11 起)
int vsnprintf_s( char *restrict buffer, rsize_t bufsz,
                 const char *restrict format, va_list vlist );// (8)(C11 起)
```

​	从 `vlist` 所定义的位置加载数据，将它们转换成字符串等价物，并将结果写入各种池。

1） 将结果写入 [stdout](https://zh.cppreference.com/w/c/io)。

2） 将结果写入文件流 `stream`。

3） 将结果写入字符串 `buffer`。

4） 将结果写入字符串 `buffer`。至多写入 `bufsz - 1` 个字符。产生的字符串将以空字符终止，除非 `bufsz` 为零。若 `bufsz` 为零，则不写入任何内容，且 `buffer` 可为空指针，然而照样计算并返回返回值（本应写入的字节数，不包含空终止符）。

5-8) 同 (1-4)，除了在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `format` 中存在转换说明符 `%n`
  - 任何一个对应 `%s` 的参数是空指针
  - `format` 或 `buffer` 是空指针
  - `bufsz` 为零或大于 RSIZE_MAX
  - 任何一个字符串及字符转换说明符中出现编码错误
  - （仅对于 `vsprintf_s`）存储于 `buffer` 的字符串（包括尾随空字符）长度将超出 `bufsz`

同所有边界检查函数，`vprintf_s`、`vfprintf_s`、`vsprintf_s` 与 `vsnprintf_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。

**参数**

| stream | -    | 要写入的输出文件流                              |
| ------ | ---- | ----------------------------------------------- |
| buffer | -    | 指向要写入的字符串的指针                        |
| bufsz  | -    | 至多可以写入 `bufsz - 1` 个字符，再加上空终止符 |
| format | -    | 指向指定数据转译方式的空终止字符串的指针        |
| vlist  | -    | 包含要打印数据的变量参数列表                    |

​	**格式**字符串由普通多字节字符（除了 `%`）和转换指示构成，前者被不改动地复制到输出流。每个转换指示均拥有下列格式：

  - 引入的 `%` 字符。

  - (可选) 一或多个修改转换行为的标志：
  - `-`：转换结果在域内左对齐（默认为右对齐）。
  - `+`：有符号转换的符号始终前置于转换结果（默认仅当结果为负时前置负号）。
  - *空格*：如果有符号转换的结果不以符号开始，或为空，那么前置空格于结果。存在 `+` 标志时忽略*空格*。
  - `#`：进行*替用形式* ﻿的转换。确切的效果见下表，其他情况下行为未定义。
  - `0`：对于整数和浮点数转换，使用前导零代替*空格* ﻿字符填充字段。对于整数，如果显式指定了精度，那么忽略此标志。对于其他转换，使用此标志导致未定义行为。存在 `-` 标志时忽略 `0`。

  - (可选) 整数或 `*`，指定最小字段宽度。如果有要求，那么结果会以*空格* ﻿字符（默认情况）填充，在右对齐时于左，左对齐时于右。使用 `*` 的情况下，以一个额外的 `int` 类型实参指定宽度。如果实参值是负数，那么它导致指定 `-` 标志和正的字段宽度。（注意：这是最小宽度：值决不会被截断）。

  - (可选) 后随整数或 `*` 或两者皆无的 `.`，指示转换的*精度* ﻿。在使用 `*` 的情况下，*精度* ﻿由额外的 `int` 类型的实参指定。如果此实参的值是负数，那么它被忽略。如果既不使用数字也不使用 `*`，那么精度采用零。*精度* ﻿的确切效果见下表。

  - (可选) 指定实参大小的*长度修饰符*（其与格式指示符组合，指定对应实参的类型）。

  - 转换格式指示符

​	下列格式指示符可用：

|                          转换指示符                          |                             解释                             | 期望的实参类型  |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :-------------: | :--------------: | :------------: | :-------------: | :------------------: | :----------------------------------------------------------: | :----------------------------------------------------: | :----------------------------------------------------------: | ------------- |
|                         长度修饰符→                          |                              hh                              |        h        |        无        |       l        |       ll        |          j           |                              z                               |                           t                            |                              L                               |               |
|                       仅从 C99 起可用→                       |                              是                              |                 |                  |                |       是        |          是          |                              是                              |                           是                           |                                                              |               |
|                             `%`                              | ​	写入字面的 `%`。完整的转换指示必须是 `%%`。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `c`                              | ​	写入**单个字符**。实参首先被转换成 `unsigned char`。如果使用 **l** 修饰符，那么实参首先被转换成字符串，如同通过以 `wchar_t[2]` 实参使用 **%ls**。 |     不适用      |      不适用      |     `int`      |     wint_t      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             `s`                              | ​	写入**字符串**。实参必须是指向字符数组首元素的指针。*精度* ﻿指定写入最大的字符数。如果没有指定*精度*，那么写每个字节直到而不含首个空终止符。如果使用 **l** 指示符，那么实参必须是指向 `wchar_t` 数组首元素的指针，数组会被转换成 `char` 数组，如同通过以零初始化转换状态调用 [wcrtomb](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb)。 |     不适用      |      不适用      |    `char*`     |   `wchar_t*`    |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                           `d` `i`                            | ​	转换**有符号整数**为十进制表示 *[-]dddd*。*精度* ﻿指定出现的最小数位数。默认精度是 `1`。如果被转换的值和精度都是 `0`，那么转换结果无字符。对于 `z` 修饰符，期望的实参类型是 [size_t](https://zh.cppreference.com/w/c/types/size_t) 的有符号版本。 |  `signed char`  |     `short`      |     `int`      |     `long`      |     `long long`      |  [intmax_t](https://zh.cppreference.com/w/c/types/integer)   |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) | 不适用        |
|                             `o`                              | ​	转换**无符号整数**为八进制表示 *oooo*。*精度* ﻿指定出现数字的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现* ﻿中精度按需增加，以写入一个前导零。在此情况下如果被转换值和精度都是 `0`，那么写入单个 `0`。 | `unsigned char` | `unsigned short` | `unsigned int` | `unsigned long` | `unsigned long long` |  [uintmax_t](https://zh.cppreference.com/w/c/types/integer)  | [size_t](https://zh.cppreference.com/w/c/types/size_t) | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) 的无符号版本 | 不适用        |
|                           `x` `X`                            | ​	转换**无符号整数**为十六进制表示 *hhhh*。`x` 转换使用字母 `abcdef`。`X` 转换使用 `ABCDEF`。*精度*指定出现数位的最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。在*替用实现中* ﻿如果被转换值非零，那么结果有 `0x` 或 `0X` 前缀。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                             `u`                              | ​	转换**无符号整数**为十进制表示 *dddd*。*精度* ﻿指定出现的数位最小个数。默认精度是 `1`。如果被转换值和精度都是 `0`，那么转换结果无字符。 |     不适用      |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
|                        `f` `F` (C99)                         | ​	转换**浮点数**为 *[-]ddd.ddd* 样式的十进制记法。*精度* ﻿指定小数点字符后出现的确切数位数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |    `double`    | `double` (C99)  |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | `long double` |
|                           `e` `E`                            | ​	转换**浮点数**为十进制指数记法。`e` 转换样式使用 *[-]d.ddd* ﻿`e`*±dd*。`E` 转换样式使用 *[-]d.ddd* ﻿`E`*±dd*。指数至少含两个数位，仅当需要时才使用更多数位。如果值是 `0`，那么指数也是 `0`。*精度* ﻿指定小数点字符后出现数位的最小个数。默认精度是 `6`。在*替用实现* ﻿中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                 `a` `A`​	(C99)                 | ​	转换**浮点数**为十六进制指数记法。`a` 转换样式使用 *[-]* ﻿`0x`*h.hhh* ﻿`p`*±d*。`A` 转换样式使用 *[-]* ﻿`0X`*h.hhh* ﻿`P`*±d*。如果参数是正规化的浮点数，那么首个十六进制数位非 `0`。如果值是 `0`，那么指数也是 `0`。*精度*指定小数点字符后出现数位的最小个数。默认精度足以精确表示该值。在*替用实现*中即使没有小数点后数位也写小数点。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                           `g` `G`                            | ​	转换**浮点数**为十进制小数或十进制指数记法，依赖于值和*精度*。`g` 转换样式将进行带样式 `e` 或 `f` 的转换。`G` 转换样式将进行带样式 `E` 或 `f`(C99 前)`F`(C99 起) 的转换。令 `P` 等于精度，如果它非零，那么精度在未指定时是 `6`，如果精度是 `0` 那么等于 `1`。然后，如果带样式 `E` 的转换会有指数 `X`，那么：如果 *P > X ≥ −4*，那么转换带 `f` 或 `F`(C99 起) 风格，及精度 *P − 1 − X*。否则，转换带 `e` 或 `E` 风格，及精度 *P − 1*。除非要求*替用表示*，否则末尾零会被移除，且在不留下小数部分时小数点也会被移除。无穷大和非数的转换样式见[注解](https://zh.cppreference.com/w/c/io/vfprintf#.E6.B3.A8.E8.A7.A3)。 |     不适用      |      不适用      |     不适用     |     不适用      |        不适用        |                            不适用                            |                                                        |                                                              |               |
|                             `n`                              | ​	返回对函数的此调用迄今为止**写入的字符数**。结果被*写入* ﻿到实参所指向的值。该指示不可含有任何*标签*、*域宽* ﻿或*精度*。对于 `z` 修饰符，实参类型是 `S*`，其中 `S` 是 `[size_t](http://zh.cppreference.com/w/c/types/size_t)` 的有符号版本。 | `signed char*`  |     `short*`     |     `int*`     |     `long*`     |     `long long*`     | [intmax_t](https://zh.cppreference.com/w/c/types/integer)`*` |                           ※                            | [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)`*` | 不适用        |
|                             `p`                              |          写入定义了**指针**的由实现定义的字符序列。          |     不适用      |      不适用      |    `void*`     |     不适用      |        不适用        |                            不适用                            |                         不适用                         |                            不适用                            | 不适用        |
|                             注解                             |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |
| ​	浮点数转换函数转换无穷大为 `inf` 或 `infinity`。由实现定义使用其中哪一个。​	非数转换成 `nan` 或 `nan(*char_sequence*)`。由实现定义使用其中哪一个。​	转换 `F`、`E`、`G`、`A` 替代上面输出 `INF`、`INFINITY`、`NAN`。​	用于打印 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short` 的转换指示符实际期待[默认实参提升](https://zh.cppreference.com/w/c/language/conversion#.E9.BB.98.E8.AE.A4.E5.AE.9E.E5.8F.82.E6.8F.90.E5.8D.87)后的类型，但在打印前会转换到 `char`、`unsigned char`、`signed char`、`short` 和 `unsigned short`。直接向函数传递这些类型的值是安全的，因为在调用变参数函数时会发生提升。​	定宽字符类型（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确转换指示在标头 [`<inttypes.h>`](https://zh.cppreference.com/w/c/header/inttypes) 定义（尽管 [PRIdMAX](https://zh.cppreference.com/w/c/types/integer)、[PRIuMAX](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。​	内存写入转换指示符 `%n` 是安全漏洞的常见目标，这里格式字符串依赖用户输入，而有边界检查的 `printf_s` 系列函数不支持此转换指示符(C11 起)。​	在每个转换指示符的行动后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许于同一变量多次存入 `%n` 的结果，并在同一此调用中打印出先前以 `%n` 存储的值。​	如果转换指示非法，那么行为未定义。 |                                                              |                 |                  |                |                 |                      |                                                              |                                                        |                                                              |               |

**返回值**

1-3) 若成功则为写入的字符数，若出现错误则为负值。

4） 若成功则为写入的字符数，若出现错误则为负值。若产生的字符串因 `bufsz` 限制被截断，函数返回假如未强加限制则本应写入的字符数（不包含空终止字节）。

5,6) 传输到输出流的字符数，或若输出错误、运行时制约违规错误、编码错误发生则为负值。

7） 写入 `buffer` 的字符数，不计空字符（只要 `buffer` 不是空指针且 `bufsz` 非零且不大于 RSIZE_MAX，就会写入它），运行时制约违规时为零，编码错误发生时为负值。

8） 不含空终止字符的（只要 `buffer` 不是空指针且 `bufsz` 非零且不大于 RSIZE_MAX，就会写入它）假如忽略 `bufsz` 则本应写入 `buffer` 的字符数，或若出现运行时制约违规或编码错误为负值。

**注解**

​	所有这些函数调用 va_arg 至少一次，返回后 `vlist` 的值不确定。这些函数不调用 va_end，而这必须由调用方进行。

​	不同于 `vsprintf_s`，`vsnprintf_s` 将截断结果以适应 `buffer` 所指向的数组。

​	[Microsoft CRT](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l) 中的 `vsnprintf_s` 实现不符合 C 标准。微软的版本有一个额外的第三形参 `[size_t](http://zh.cppreference.com/w/c/types/size_t) count`，它包含所要写入的不包括空终止符的最大字符数量。这个形参可能与通过形参 `[size_t](http://zh.cppreference.com/w/c/types/size_t) bufsz` 提供的缓冲区大小有所区别。

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

​	可能的输出：

```txt
02/20/15 21:58:09.072683 UTC [debug]: Logging, 1, 2, 3
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.6.8 The vfprintf function （第 TBD 页）

  - 7.21.6.10 The vprintf function （第 TBD 页）

  - 7.21.6.12 The vsnprintf function （第 TBD 页）

  - 7.21.6.13 The vsprintf function （第 TBD 页）

  - K.3.5.3.8 The vfprintf_s function （第 TBD 页）

  - K.3.5.3.10 The vprintf_s function （第 TBD 页）

  - K.3.5.3.12 The vsnprintf_s function （第 TBD 页）

  - K.3.5.3.13 The vsprintf_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.21.6.8 The vfprintf function （第 238 页）

  - 7.21.6.10 The vprintf function （第 239 页）

  - 7.21.6.12 The vsnprintf function （第 239-240 页）

  - 7.21.6.13 The vsprintf function （第 240 页）

  - K.3.5.3.8 The vfprintf_s function （第 434 页）

  - K.3.5.3.10 The vprintf_s function （第 435 页）

  - K.3.5.3.12 The vsnprintf_s function （第 436-437 页）

  - K.3.5.3.13 The vsprintf_s function （第 437 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.6.8 The vfprintf function （第 326-327 页）

  - 7.21.6.10 The vprintf function （第 328 页）

  - 7.21.6.12 The vsnprintf function （第 329 页）

  - 7.21.6.13 The vsprintf function （第 329 页）

  - K.3.5.3.8 The vfprintf_s function （第 597 页）

  - K.3.5.3.10 The vprintf_s function （第 598-599 页）

  - K.3.5.3.12 The vsnprintf_s function （第 600 页）

  - K.3.5.3.13 The vsprintf_s function （第 601 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.6.8 The vfprintf function （第 292 页）

  - 7.19.6.10 The vprintf function （第 293 页）

  - 7.19.6.12 The vsnprintf function （第 294 页）

  - 7.19.6.13 The vsprintf function （第 295 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.9.6.7 The vfprintf function

  - 4.9.6.8 The vprintf function

  - 4.9.6.9 The vsprintf function

**参阅**

| [vwprintf (C95)<br />vfwprintf (C95)<br />vswprintf (C95)<br />vwprintf_s (C95)<br />vfwprintf_s (C95)<br />vswprintf_s (C95)<br />vsnwprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/vfwprintf) | 打印格式化宽字符输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 使用可变参数列表 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [printf <br />fprintf <br />sprintf <br />snprintf (C99)<br />printf_s (C99)<br />fprintf_s (C11)<br />sprintf_s (C11)<br />snprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 (函数) |
| [vscanf (C99)<br />vfscanf (C99)<br />vsscanf (C99)<br />vscanf_s (C99)<br />vfscanf_s (C99)<br />vsscanf_s (C99)<br />](https://zh.cppreference.com/w/c/io/vfscanf) | 从 [stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 使用可变参数列表 (函数) |
| **vprintf, vfprintf, vsprintf, vsnprintf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/vfprintf)** |                                                              |





### vsprintf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### vsscanf

原址：[http://zh.cppreference.com/w/c/io/vfscanf](http://zh.cppreference.com/w/c/io/vfscanf)

作用：

备注：
```c
// 在标头 <stdio.h> 定义
int vscanf( const char *restrict format, va_list vlist );// (1)(C99 起)
int vfscanf( FILE *restrict stream, const char *restrict format, 
             va_list vlist );// (2)(C99 起)
int vsscanf( const char *restrict buffer, const char *restrict format, 
             va_list vlist );// (3)(C99 起)
int vscanf_s(const char *restrict format, va_list vlist);// (4)(C11 起)
int vfscanf_s( FILE *restrict stream, const char *restrict format,
               va_list vlist);// (5)(C11 起)
int vsscanf_s( const char *restrict buffer, const char *restrict format,
               va_list vlist);// (6)(C11 起)
```

​	从各种源读取数据，按照 `format` 转换并存储结果到 `vlist` 所定义的位置。

1） 从 [stdin](https://zh.cppreference.com/w/c/io) 读取数据。

2） 从文件流 `stream` 读取数据。

3） 从空终止字符串 `buffer` 读取数据。抵达字符串结尾等价于 `vfscanf` 的抵达文件尾条件

4-6) 同 (1-3)，但 `%c`、`%s` 及 `%[` 转换指示符要求两个参数（通常的指针和指示获取用数组大小的 rsize_t 类型值，以 %c 读取单个字符时可以为 1），并且在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - 任何指针类型参数为空指针
  - `format`、`stream` 或 `buffer` 为空指针
  - %c 、 %s 或 %[ 本会写入的字符数，加上空终止字符，要超过提供给这些转换指示符的第二个（rsize_t）参数
  - 可选，任何其他可检测错误，例如未知转换指示符

**参数**

| stream | -    | 要读取的输入文件流                       |
| ------ | ---- | ---------------------------------------- |
| buffer | -    | 指向要读取的空终止字符串的指针           |
| format | -    | 指向指定读取输入方式的空终止字符串的指针 |
| vlist  | -    | 包含接收各实参的可变实参列表             |

- 非空白多字节字符，除了 `%`：每个格式字符串中的这种字符处理一个来自输入流的完全相同的字符，或在它与流的下个字符比较不相等时导致函数失败。
- 空白字符：任何格式字符串中的单个空白字符处理所有来自输入的可用连续空白字符（如同通过于循环中调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 确定）。注意，格式字符串中 ``"\n"``、`" "`、`"**\t****\t**"` 或其他空白无区别。
- 转换指示：每个转换指示拥有下列格式：

  - 引入用 `%` 字符

  - (可选) 赋值抑制字符 `*`。如果存在此选项，那么此函数不将结果赋值给任何接收用实参。

  - (可选) 指定*最大字段宽度* ﻿的整数数字（大于零），即函数进行在当前转换指示所指定的转换时，允许处理的最大字符数。注意如果没有提供宽度，那么 `%s` 和 `%[` 可能导致缓冲区溢出。

  - (可选) 指定接收实参大小的*长度修饰符*，即实际目标类型。这影响转换准确性和溢出规则。默认目标类型对每个转换类型有所不同（见下表）。

  - 转换格式指示符。

​	下列格式指示符可用：

|                          转换指示符                          |                             解释                             |           期望的实参类型           |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :--------------------------------: | :----------------------------------: | :------------------------------: | :--------------------------------: | :------------------------------------------: | :----------------------------------------------------------: | :------------------------------------------------------: | :----------------------------------------------------------: | -------------- |
|                         长度修饰符→                          |                              hh                              |                 h                  |                  无                  |                l                 |                 ll                 |                      j                       |                              z                               |                            t                             |                              L                               |                |
|                       仅从 C99 起可用→                       |                              是                              |                                    |                                      |                                  |                 是                 |                      是                      |                              是                              |                            是                            |                                                              |                |
|                             `%`                              |                      匹配字面 `%`。                      |               不适用               |                不适用                |              不适用              |               不适用               |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             `c`                              | ​	匹配一个**字符**或**字符**的序列。如果使用了宽度指示符，那么匹配恰好*宽度*个字符（该实参必须是指向有充足空间的数组的指针）。与 %s 和 %[ 不同，它不会在数组后附加空字符。 |               不适用               |                不适用                |             `char*`              |             `wchar_t*`             |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             `s`                              | ​	匹配非空白字符的序列（一个**字符串**）。如果使用宽度指示符，那么至多匹配*宽度*个字符，或匹配到首个提前出现的空白符前。总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                        `[`*集合* ﻿`]`                         | ​	匹配*集合* ﻿中的字符的一个非空字符序列。如果集合的首字符是 `^`，那么匹配所有不在集合中的字符。如果集合以 `]` 或 `^]` 开始，那么 `]` 字符也会被包含入集合。在扫描集合的非最初位置的字符 `-` 是否可以指示范围，如 `[0-9]`，由实现定义。如果使用宽度指示符，那么最多匹配到*宽度*。总是在匹配的字符后存储一个空字符（因此实参数组必须有至少*宽度 +1*个字符的空间）。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `d`                              | ​	匹配一个**十进制整数**。该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 `10` 为 `base` 时期望的格式相同。 | `signed char*` 或 `unsigned char*` | `signed short*` 或 `unsigned short*` | `signed int*` 或 `unsigned int*` | `signed long*` 或 `unsigned long*` | `signed long long*` 或 `unsigned long long*` | `[intmax_t](http://zh.cppreference.com/w/c/types/integer)*` 或 `[uintmax_t](http://zh.cppreference.com/w/c/types/integer)*` | `[size_t](http://zh.cppreference.com/w/c/types/size_t)*` | `[ptrdiff_t](http://zh.cppreference.com/w/c/types/ptrdiff_t)*` | 不适用         |
|                             `i`                              | ​	匹配一个**整数**。该数的格式与 [strtol](https://zh.cppreference.com/w/c/string/byte/strtol) 以值 `0` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `u`                              | ​	匹配一个无符号**十进制整数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `10` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `o`                              | ​	匹配一个无符号**八进制数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `8` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                           `x` `X`                            | ​	匹配一个无符号**十六进制整数**。该数的格式与 [strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul) 以值 `16` 为 `base` 时期望的格式相同。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|                             `n`                              | ​	返回**迄今读取的字符数**。不消耗输出。不增加赋值计数。如果此指示符拥有赋值抑制运算符，那么行为未定义。 |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
|      `a` (C99) `A` (C99) `e` `E` `f` `F` (C99) `g` `G`       | ​	匹配一个**浮点数**。该数的格式与 [strtof](https://zh.cppreference.com/w/c/string/byte/strtof) 期望的格式相同。 |               不适用               |                不适用                |             `float*`             |             `double*`              |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | `long double*` |
|                             `p`                              | ​	匹配定义了一个**指针**的由实现定义的字符序列。`printf` 系列函数使用 `%p` 格式指示符时应该产生同样的序列。 |               不适用               |                不适用                |             `void**`             |               不适用               |                    不适用                    |                            不适用                            |                          不适用                          |                            不适用                            | 不适用         |
|                             注解                             |                                                              |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |
| ​	对于每个 `n` 以外的转换指示符，不超过任何指定字段宽度，且要么恰好是转换指示符所期待，要么是其所期待的前缀的最长输入字符序列，即是从流中消耗的内容。此消耗序列后的首个字符如果存在，那么保持未读取。如果被消耗序列长度为零，或被消耗序列不能转换成上面所指定的项目，那么发生匹配失败，除非遇到文件尾、编码错误，或阻止从流输入的读取错误，此情况下此为输入失败。​	所有异于 `[`、`c` 和 `n` 的转换指示符，在尝试分析输入前消耗并舍弃所有前导空白字符（如同以调用 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 来确定）。这些被消耗的字符不计入指定的最大字段宽度。​	转换指示符 `lc`、`ls` 和 `l[` 进行多字节到宽字符转换，如同如同在转换首字符前，通过用初始化为零的 [mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 对象调用 [mbrtowc](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc)。​	转换指示符 `s` 与 `[` 始终在匹配字符之后存储一个空字符。目标数组的大小必须至少比指定字段宽度大一。未指定目标数组大小时，对 `%s` 或 `%[` 的使用，与 [gets](https://zh.cppreference.com/w/c/io/gets) 同样不安全。​	[定宽整数类型](https://zh.cppreference.com/w/c/types/integer)（[int8_t](https://zh.cppreference.com/w/c/types/integer) 等）的正确的转换指示在标头 [](https://zh.cppreference.com/w/c/types/integer) 定义（虽然 [`<CNdMA>`](https://zh.cppreference.com/w/c/types/integer)、[`<CNuMA>`](https://zh.cppreference.com/w/c/types/integer) 等就是 `%jd`、`%ju` 等的别名）。​	在每个转换指示符后有一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)；这允许存储多个字段到同一“池”变量中。​	在分析以无数字指数为结尾的不完整浮点数，如以转换指示符 `%f` 分析 `"100er"` 时，消耗序列 `"100e"` （可能为合法浮点数的最长前缀），并导致匹配错误（被消耗序列不能转换成浮点数），而留下 `"r"`。某些既存实现不遵守此规则并回滚，通过消耗 `"100"` 而留下 `"er"`，例如 [glibc 漏洞 1765](https://sourceware.org/bugzilla/show_bug.cgi?id=1765)。​	如果转换指示非法，那么行为未定义。 |                                                              |                                    |                                      |                                  |                                    |                                              |                                                              |                                                          |                                                              |                |

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

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.21.6.9 The vfscanf function （第 327 页）

  - 7.21.6.11 The vscanf function （第 328 页）

  - 7.21.6.14 The vsscanf function （第 330 页）

  - K.3.5.3.9 The vfscanf_s function （第 597-598 页）

  - K.3.5.3.11 The vscanf_s function （第 599 页）

  - K.3.5.3.14 The vsscanf_s function （第 602 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.19.6.9 The vfscanf function （第 293 页）

  - 7.19.6.11 The vscanf function （第 294 页）

  - 7.19.6.14 The vsscanf function （第 295 页）

**参阅**

| [scanf <br />fscanf <br />sscanf <br />scanf_s (C11)<br />fscanf_s (C11)<br />sscanf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fscanf) | 从[stdin](https://zh.cppreference.com/w/c/io)、文件流或缓冲区读取格式化输入 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [vprintf <br />vfprintf <br />vsprintf <br />vsnprintf (C99)<br />vprintf_s (C99)<br />vfprintf_s (C11)<br />vsprintf_s (C11)<br />vsnprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/vfprintf) | 打印格式化输出到 [stdout](https://zh.cppreference.com/w/c/io)、文件流或缓冲区 使用可变参数列表 (函数) |
| **vscanf, vfscanf, vsscanf** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c/vfscanf)** |                                                              |





### vsscanf_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 <stdio.h> 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：







