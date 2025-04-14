+++
title = "<stdio.h>"
date = 2025-04-13T23:02:13+08:00
weight = 220
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/stdio](https://zh.cppreference.com/w/c/header/stdio)

​	此标头是[输入输出](https://zh.cppreference.com/w/c/io)库的一部分，提供通用的文件操作支持，还提供在窄字符上工作的 I/O 函数。

> 本节未完成 
>
> 原因：7.23 Input/output <stdio.h>; copy/share subset of [c/io](https://zh.cppreference.com/w/c/io)

### 概要

```c
#define __STDC_VERSION_STDIO_H__ 202311L
 
typedef /* 见描述 */ FILE;
typedef /* 见描述 */ size_t;
typedef /* 见描述 */ FILE;
typedef /* 见描述 */ fpos_t;
 
#define NULL         /* 见描述 */
#define _IOFBF       /* 见描述 */
#define _IOLBF       /* 见描述 */
#define _IONBF       /* 见描述 */
#define BUFSIZ       /* 见描述 */
#define EOF          /* 见描述 */
#define FOPEN_MAX    /* 见描述 */
#define FILENAME_MAX /* 见描述 */
#define L_tmpnam     /* 见描述 */
#define SEEK_CUR     /* 见描述 */
#define SEEK_END     /* 见描述 */
#define SEEK_SET     /* 见描述 */
#define TMP_MAX      /* 见描述 */
 
#define stdin        /* 见描述 */
#define stdout       /* 见描述 */
#define stderr       /* 见描述 */
 
#define _PRINTF_NAN_LEN_MAX /* 见描述 */
 
int remove(const char* filename);
int rename(const char* old, const char* new);
FILE* tmpfile(void);
char* tmpnam(char* s);
int fclose(FILE* stream);
int fflush(FILE* stream);
FILE* fopen(const char* restrict filename, const char* restrict mode);
FILE* freopen(const char* restrict filename, const char* restrict mode,
FILE* restrict stream);
void setbuf(FILE* restrict stream, char* restrict buf);
int setvbuf(FILE* restrict stream, char* restrict buf, int mode, size_t size);
int printf(const char* restrict format, ...);
int scanf(const char* restrict format, ...);
int snprintf(char* restrict s, size_t n, const char* restrict format, ...);
int sprintf(char* restrict s, const char* restrict format, ...);
int sscanf(const char* restrict s, const char* restrict format, ...);
int vfprintf(FILE* restrict stream, const char* restrict format, va_list arg);
int vfscanf(FILE* restrict stream, const char* restrict format, va_list arg);
int vprintf(const char* restrict format, va_list arg);
int vscanf(const char* restrict format, va_list arg);
int vsnprintf(char* restrict s, size_t n, const char* restrict format, va_list arg);
int vsprintf(char* restrict s, const char* restrict format, va_list arg);
int vsscanf(const char* restrict s, const char* restrict format, va_list arg);
int fgetc(FILE* stream);
char* fgets(char* restrict s, int n, FILE* restrict stream);
int fputc(int c, FILE* stream);
int fputs(const char* restrict s, FILE* restrict stream);
int getc(FILE* stream);
int getchar(void);
int putc(int c, FILE* stream);
int putchar(int c);
int puts(const char* s);
int ungetc(int c, FILE* stream);
size_t fread(void* restrict ptr, size_t size, size_t nmemb,
FILE* restrict stream);
size_t fwrite(const void* restrict ptr, size_t size, size_t nmemb,
FILE* restrict stream);
int fgetpos(FILE* restrict stream, fpos_t* restrict pos);
int fseek(FILE* stream, long int offset, int whence);
int fsetpos(FILE* stream, const fpos_t* pos);
long int ftell(FILE* stream);
void rewind(FILE* stream);
void clearerr(FILE* stream);
int feof(FILE* stream);
int ferror(FILE* stream);
void perror(const char* s);
int fprintf(FILE* restrict stream, const char* restrict format, ...);
int fscanf(FILE* restrict stream, const char* restrict format, ...);
```

​	仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 `<stdio.h>` 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：

```c
#if defined(__STDC_WANT_LIB_EXT1__)
 
#define L_tmpnam_s /* 见描述 */
#define TMP_MAX_S  /* 见描述 */
 
typedef /* 见描述 */ errno_t;
typedef /* 见描述 */ rsize_t;
 
errno_t tmpfile_s(FILE* restrict* restrict streamptr);
errno_t tmpnam_s(char* s, rsize_t maxsize);
errno_t fopen_s(FILE* restrict* restrict streamptr,
const char* restrict filename, const char* restrict mode);
errno_t freopen_s(FILE* restrict* restrict newstreamptr,
const char* restrict filename, const char* restrict mode,
FILE* restrict stream);
int fprintf_s(FILE* restrict stream, const char* restrict format, ...);
int fscanf_s(FILE* restrict stream, const char* restrict format, ...);
int printf_s(const char* restrict format, ...);
int scanf_s(const char* restrict format, ...);
int snprintf_s(char* restrict s, rsize_t n, const char* restrict format, ...);
int sprintf_s(char* restrict s, rsize_t n, const char* restrict format, ...);
int sscanf_s(const char* restrict s, const char* restrict format, ...);
int vfprintf_s(FILE* restrict stream, const char* restrict format, va_list arg);
int vfscanf_s(FILE* restrict stream, const char* restrict format, va_list arg);
int vprintf_s(const char* restrict format, va_list arg);
int vscanf_s(const char* restrict format, va_list arg);
int vsnprintf_s(char* restrict s, rsize_t n, const char* restrict format, va_list arg);
int vsprintf_s(char* restrict s, rsize_t n, const char* restrict format, va_list arg);
int vsscanf_s(const char* restrict s, const char* restrict format, va_list arg);
char* gets_s(char* s, rsize_t n);
#endif
```