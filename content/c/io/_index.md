+++
title = "文件输入/输出"
date = 2025-04-15T19:21:44+08:00
weight = 110
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文[https://zh.cppreference.com/w/c/io](https://zh.cppreference.com/w/c/io)

​	[`<stdio.h>`]({{< ref "/c/header/stdio" >}}) 头文件提供了通用的文件操作支持，并提供了具有窄字符输入/输出功能的函数。

​	[`<wchar.h>`]({{< ref "/c/header/wchar" >}}) 头文件提供了具有宽字符输入/输出功能的函数。

​	I/O 流由 **FILE** 类型的对象表示，该对象只能通过 FILE* 类型的指针访问及操作。每个流都与外部的物理设备（文件、标准输入流、打印机、序列端口等）相关联。

## 类型

| 在标头 `<stdio.h>` 定义                                   |                                                              |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| [FILE<br />](https://zh.cppreference.com/w/c/io/FILE)     | 对象类型，能够保存控制 C I/O 流所需的全部信息 (typedef)      |
| [fpos_t<br />](https://zh.cppreference.com/w/c/io/fpos_t) | 非数组完整对象类型，足以唯一指定文件的位置和多字节解析状态 (typedef) |

## 预定义标准流

| 在标头 `<stdio.h>` 定义                                    |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [stdin<br />stdout<br />stderr<br />](https://zh.cppreference.com/w/c/io/std_streams) | 与标准输入流关联的 FILE* 类型表达式 与标准输出流关联的 FILE* 类型表达式 与标准错误输出流关联的 FILE* 类型表达式 (宏常量) |

## 函数

### 文件访问

| 在标头 `<stdio.h>` 定义                                    |                                                 |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [fopen <br />fopen_s (C11)<br />](https://zh.cppreference.com/w/c/io/fopen) | 打开文件 (函数)                                 |
| [freopen <br />freopen_s (C11)<br />](https://zh.cppreference.com/w/c/io/freopen) | 以不同名称打开既存的文件流 (函数)               |
| [fclose<br />](https://zh.cppreference.com/w/c/io/fclose)  | 关闭文件 (函数)                                 |
| [fflush<br />](https://zh.cppreference.com/w/c/io/fflush)  | 将输出流与实际文件同步 (函数)                   |
| [setbuf<br />](https://zh.cppreference.com/w/c/io/setbuf)  | 为文件流设置缓冲区 (函数)                       |
| [setvbuf<br />](https://zh.cppreference.com/w/c/io/setvbuf) | 为文件流设置缓冲区和其大小 (函数)               |
| 在标头 `<wchar.h>` 定义                                    |                                                 |
| [fwide (C95)<br />](https://zh.cppreference.com/w/c/io/fwide) | 将文件流在宽字符 I/O 和窄字符 I/O 间切换 (函数) |

### 直接输入/输出

| 在标头 `<stdio.h>` 定义                                   |                   |
| ----------------------------------------------------------- | ----------------- |
| [fread<br />](https://zh.cppreference.com/w/c/io/fread)   | 从文件读取 (函数) |
| [fwrite<br />](https://zh.cppreference.com/w/c/io/fwrite) | 写入到文件 (函数) |

### 无格式输入/输出

#### 窄字符

| 在标头 `<stdio.h>` 定义                                    |                                    |
| ------------------------------------------------------------ | ---------------------------------- |
| [fgetc<br />getc<br />](https://zh.cppreference.com/w/c/io/fgetc) | 从文件流获取一个字符 (函数)        |
| [fgets<br />](https://zh.cppreference.com/w/c/io/fgets)    | 从文件流获取一个字符串 (函数)      |
| [fputc<br />putc<br />](https://zh.cppreference.com/w/c/io/fputc) | 将一个字符写入文件流 (函数)        |
| [fputs<br />](https://zh.cppreference.com/w/c/io/fputs)    | 将一个字符串写入文件流 (函数)      |
| [getchar<br />](https://zh.cppreference.com/w/c/io/getchar) | 从 **stdin** 读取一个字符 (函数)   |
| [gets (C11 移除)<br />gets_s (C11 移除)<br />](https://zh.cppreference.com/w/c/io/gets) | 从 **stdin** 读取一个字符串 (函数) |
| [putchar<br />](https://zh.cppreference.com/w/c/io/putchar) | 将一个字符写入 **stdout** (函数)   |
| [puts<br />](https://zh.cppreference.com/w/c/io/puts)      | 将一个字符串写入 **stdout** (函数) |
| [ungetc<br />](https://zh.cppreference.com/w/c/io/ungetc)  | 将一个字符送回文件流 (函数)        |

#### 宽字符

| 在标头 `<wchar.h>` 定义                                    |                                    |
| ------------------------------------------------------------ | ---------------------------------- |
| [fgetwc (C95)<br />getwc (C95)<br />](https://zh.cppreference.com/w/c/io/fgetwc) | 从文件流获取一个宽字符 (函数)      |
| [fgetws (C95)<br />](https://zh.cppreference.com/w/c/io/fgetws) | 从文件流获取一个宽字符串 (函数)    |
| [fputwc (C95)<br />putwc (C95)<br />](https://zh.cppreference.com/w/c/io/fputwc) | 将一个宽字符写入文件流 (函数)      |
| [fputws (C95)<br />](https://zh.cppreference.com/w/c/io/fputws) | 将一个宽字符串写入文件流 (函数)    |
| [getwchar (C95)<br />](https://zh.cppreference.com/w/c/io/getwchar) | 从 **stdin** 读取一个宽字符 (函数) |
| [putwchar (C95)<br />](https://zh.cppreference.com/w/c/io/putwchar) | 将一个宽字符写入 **stdout** (函数) |
| [ungetwc (C95)<br />](https://zh.cppreference.com/w/c/io/ungetwc) | 将一个宽字符送回文件流 (函数)      |

### 有格式输入/输出

#### 窄字符

| 在标头 `<stdio.h>` 定义                                    |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [scanf <br />fscanf <br />sscanf <br />scanf_s (C11)<br />fscanf_s (C11)<br />sscanf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fscanf) | 从**stdin**、文件流或缓冲区读取格式化输入 (函数)             |
| [vscanf (C99)<br />vfscanf (C99)<br />vsscanf (C99)<br />vscanf_s (C99)<br />vfscanf_s (C99)<br />vsscanf_s (C99)<br />](https://zh.cppreference.com/w/c/io/vfscanf) | 从 **stdin**、文件流或缓冲区读取格式化输入 使用可变参数列表 (函数) |
| [printf <br />fprintf <br />sprintf <br />snprintf (C99)<br />printf_s (C99)<br />fprintf_s (C11)<br />sprintf_s (C11)<br />snprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fprintf) | 打印格式化输出到 **stdout**、文件流或缓冲区 (函数)           |
| [vprintf <br />vfprintf <br />vsprintf <br />vsnprintf (C99)<br />vprintf_s (C99)<br />vfprintf_s (C11)<br />vsprintf_s (C11)<br />vsnprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/vfprintf) | 打印格式化输出到 **stdout**、文件流或缓冲区 使用可变参数列表 (函数) |

#### 宽字符

| 在标头 `<wchar.h>` 定义                                    |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [wscanf (C95)<br />fwscanf (C95)<br />swscanf (C95)<br />wscanf_s (C95)<br />fwscanf_s (C95)<br />swscanf_s (C95)<br />](https://zh.cppreference.com/w/c/io/fwscanf) | 从 **stdin**、文件流或缓冲区读取格式化宽字符输入 (函数)      |
| [vwscanf (C99)<br />vfwscanf (C99)<br />vswscanf (C99)<br />vwscanf_s (C99)<br />vfwscanf_s (C99)<br />vswscanf_s (C99)<br />](https://zh.cppreference.com/w/c/io/vfwscanf) | 从 **stdin**、文件流或缓冲区读取格式化宽字符输入 使用可变参数列表 (函数) |
| [wprintf (C95)<br />fwprintf (C95)<br />swprintf (C95)<br />wprintf_s (C95)<br />fwprintf_s (C95)<br />swprintf_s (C95)<br />snwprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/fwprintf) | 打印格式化宽字符输出到 **stdout**、文件流或缓冲区 (函数)     |
| [vwprintf (C95)<br />vfwprintf (C95)<br />vswprintf (C95)<br />vwprintf_s (C95)<br />vfwprintf_s (C95)<br />vswprintf_s (C95)<br />vsnwprintf_s (C11)<br />](https://zh.cppreference.com/w/c/io/vfwprintf) | 打印格式化宽字符输出到 **stdout**、文件流或缓冲区 使用可变参数列表 (函数) |

### 文件定位

| 在标头 `<stdio.h>` 定义                                    |                                               |
| ------------------------------------------------------------ | --------------------------------------------- |
| [ftell<br />](https://zh.cppreference.com/w/c/io/ftell)    | 返回当前的文件位置指示值 (函数)               |
| [fgetpos<br />](https://zh.cppreference.com/w/c/io/fgetpos) | 获取文件位置指示器 (函数)                     |
| [fseek<br />](https://zh.cppreference.com/w/c/io/fseek)    | 将文件位置指示符移动到文件中的指定位置 (函数) |
| [fsetpos<br />](https://zh.cppreference.com/w/c/io/fsetpos) | 将文件位置指示器移动到文件中的指定位置 (函数) |
| [rewind<br />](https://zh.cppreference.com/w/c/io/rewind)  | 将文件位置指示器移动到文件首 (函数)           |

### 错误处理

| 在标头 `<stdio.h>` 定义                                    |                                              |
| ------------------------------------------------------------ | -------------------------------------------- |
| [clearerr<br />](https://zh.cppreference.com/w/c/io/clearerr) | 清除错误 (函数)                              |
| [feof<br />](https://zh.cppreference.com/w/c/io/feof)      | 检查文件结尾 (函数)                          |
| [ferror<br />](https://zh.cppreference.com/w/c/io/ferror)  | 检查文件错误 (函数)                          |
| [perror<br />](https://zh.cppreference.com/w/c/io/perror)  | 显示对应当前错误的字符串到 **stderr** (函数) |

### 对文件的操作

| 在标头 `<stdio.h>` 定义                                    |                               |
| ------------------------------------------------------------ | ----------------------------- |
| [remove<br />](https://zh.cppreference.com/w/c/io/remove)  | 删除文件 (函数)               |
| [rename<br />](https://zh.cppreference.com/w/c/io/rename)  | 重命名文件 (函数)             |
| [tmpfile <br />tmpfile_s (C11)<br />](https://zh.cppreference.com/w/c/io/tmpfile) | 返回指向临时文件的指针 (函数) |
| [tmpnam <br />tmpnam_s (C11)<br />](https://zh.cppreference.com/w/c/io/tmpnam) | 返回唯一的文件名 (函数)       |

## 宏常量

| 在标头 `<stdio.h>` 定义                        |                                                              |
| ------------------------------------------------ | ------------------------------------------------------------ |
| EOF<br />                                      | int 类型的负数整数常量表达式 (宏常量)                        |
| FOPEN_MAX<br />                                | 能同时打开的最大文件数 (宏常量)                              |
| FILENAME_MAX<br />                             | 保有最长受支持文件名所需的 char 数组大小 (宏常量)            |
| BUFSIZ<br />                                   | [setbuf](https://zh.cppreference.com/w/c/io/setbuf) 所用的缓冲区大小 (宏常量) |
| _IOFBF<br />_IOLBF<br />_IONBF<br />       | 指示全缓冲 I/O 的 [setvbuf](https://zh.cppreference.com/w/c/io/setvbuf) 参数 指示行缓冲 I/O 的 [setvbuf](https://zh.cppreference.com/w/c/io/setvbuf) 参数 指示无缓冲 I/O 的 [setvbuf](https://zh.cppreference.com/w/c/io/setvbuf) 参数 (宏常量) |
| SEEK_SET<br />SEEK_CUR<br />SEEK_END<br /> | 指示从文件首开始寻位的 [fseek](https://zh.cppreference.com/w/c/io/fseek) 参数 指示从文件当前位置开始寻位的 [fseek](https://zh.cppreference.com/w/c/io/fseek) 参数 指示从文件尾开始寻位的 [fseek](https://zh.cppreference.com/w/c/io/fseek) 参数 (宏常量) |
| TMP_MAX <br />TMP_MAX_S (C11)<br />          | [tmpnam](https://zh.cppreference.com/w/c/io/tmpnam) 所能生成的独有文件名的最大数量 tmpnam_s 所能生成的独有文件名的最大数量 (宏常量) |
| L_tmpnam <br />L_tmpnam_s (C11)<br />        | 保有 [tmpnam](https://zh.cppreference.com/w/c/io/tmpnam) 结果所需的 char 数组大小 保有 tmpnam_s 结果所需的 char 数组大小 (宏常量) |

## 参阅

**C 风格文件输入/输出**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/io/c)**
