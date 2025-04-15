+++
title = "空终止字节字符串"
date = 2025-04-15T08:51:31+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/string/byte](https://zh.cppreference.com/w/c/string/byte)

​	空终止字节字符串（NTBS）是非零字节的序列后随一个零值字节（空终止字符）。字节字符串中的每个字节都是某个字符集中被编码的一个字符。例如，字符数组 `{'\x63','\x61','\x74','\0'}` 是一个以 ASCII 编码表示字符串 `"cat"` 的 NTBS。

## 函数

### 字符分类

| 在标头 `<ctype.h>` 定义                                    |                                   |
| ------------------------------------------------------------ | --------------------------------- |
| [isalnum<br />](https://zh.cppreference.com/w/c/string/byte/isalnum) | 检查字符是否是字母或数字 (函数)   |
| [isalpha<br />](https://zh.cppreference.com/w/c/string/byte/isalpha) | 检查字符是否是字母 (函数)         |
| [islower<br />](https://zh.cppreference.com/w/c/string/byte/islower) | 检查字符是否是小写字母 (函数)     |
| [isupper<br />](https://zh.cppreference.com/w/c/string/byte/isupper) | 检查字符是否是大写字母 (函数)     |
| [isdigit<br />](https://zh.cppreference.com/w/c/string/byte/isdigit) | 检查字符是否是数字 (函数)         |
| [isxdigit<br />](https://zh.cppreference.com/w/c/string/byte/isxdigit) | 检查字符是否是十六进制字符 (函数) |
| [iscntrl<br />](https://zh.cppreference.com/w/c/string/byte/iscntrl) | 检查字符是否是控制字符 (函数)     |
| [isgraph<br />](https://zh.cppreference.com/w/c/string/byte/isgraph) | 检查字符是否是图形字符 (函数)     |
| [isspace<br />](https://zh.cppreference.com/w/c/string/byte/isspace) | 检查字符是否是空白字符 (函数)     |
| [isblank (C99)<br />](https://zh.cppreference.com/w/c/string/byte/isblank) | 检查字符是否是空格字符 (函数)     |
| [isprint<br />](https://zh.cppreference.com/w/c/string/byte/isprint) | 检查字符是否是可打印字符 (函数)   |
| [ispunct<br />](https://zh.cppreference.com/w/c/string/byte/ispunct) | 检查字符是否是标点字符 (函数)     |

### 字符操作

| [tolower<br />](https://zh.cppreference.com/w/c/string/byte/tolower) | 将字符转换成小写 (函数) |
| ------------------------------------------------------------ | ----------------------- |
| [toupper<br />](https://zh.cppreference.com/w/c/string/byte/toupper) | 将字符转换成大写 (函数) |

> 注意
>
> 将来可能添加以 `to` 或 `is` 后随小写字母起始的新增函数到头文件 [`<ctype.h>`](https://zh.cppreference.com/w/c/header/ctype)，故包含该头文件的程序中不应定义这些函数。

| ASCII 值 |   ASCII 值    |   ASCII 值    |              字符               | [`iscntrl`](https://zh.cppreference.com/w/c/string/byte/iscntrl) [`iswcntrl`](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | [`isprint`](https://zh.cppreference.com/w/c/string/byte/isprint) [`iswprint`](https://zh.cppreference.com/w/c/string/wide/iswprint) | [`isspace`](https://zh.cppreference.com/w/c/string/byte/isspace) [`iswspace`](https://zh.cppreference.com/w/c/string/wide/iswspace) | [`isblank`](https://zh.cppreference.com/w/c/string/byte/isblank) [`iswblank`](https://zh.cppreference.com/w/c/string/wide/iswblank) | [`isgraph`](https://zh.cppreference.com/w/c/string/byte/isgraph) [`iswgraph`](https://zh.cppreference.com/w/c/string/wide/iswgraph) | [`ispunct`](https://zh.cppreference.com/w/c/string/byte/ispunct) [`iswpunct`](https://zh.cppreference.com/w/c/string/wide/iswpunct) | [`isalnum`](https://zh.cppreference.com/w/c/string/byte/isalnum) [`iswalnum`](https://zh.cppreference.com/w/c/string/wide/iswalnum) | [`isalpha`](https://zh.cppreference.com/w/c/string/byte/isalpha) [`iswalpha`](https://zh.cppreference.com/w/c/string/wide/iswalpha) | [`isupper`](https://zh.cppreference.com/w/c/string/byte/isupper) [`iswupper`](https://zh.cppreference.com/w/c/string/wide/iswupper) | [`islower`](https://zh.cppreference.com/w/c/string/byte/islower) [`iswlower`](https://zh.cppreference.com/w/c/string/wide/iswlower) | [`isdigit`](https://zh.cppreference.com/w/c/string/byte/isdigit) [`iswdigit`](https://zh.cppreference.com/w/c/string/wide/iswdigit) | [`isxdigit`](https://zh.cppreference.com/w/c/string/byte/isxdigit) [`iswxdigit`](https://zh.cppreference.com/w/c/string/wide/iswxdigit) |
| :------: | :-----------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | ---- | ---- |
|  十进制  |   十六进制    |                            八进制                            |  |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |      |      |
|   0–8    |  `\x0`–`\x8`  |                          `\0`–`\10`                          |                      控制码 (`NUL` 等)                       |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|    9     |     `\x9`     |                            `\11`                             |                        制表符 (`\t`)                         |                             `≠0`                             |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|  10–13   |  `\xA`–`\xD`  |                         `\12`–`\15`                          |               空白符 (`\n`, `\v`, `\f`, `\r`)                |                             `≠0`                             |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|  14–31   | `\xE`–`\x1F`  |                         `\16`–`\37`                          |                            控制码                            |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|    32    |    `\x20`     |                            `\40`                             |                             空格                             |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|  33–47   | `\x21`–`\x2F` |                         `\41`–`\57`                          |                      `!"#$%&'()*+,-./`                       |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|  48–57   | `\x30`–`\x39` |                         `\60`–`\71`                          |                         `0123456789`                         |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              | `≠0` | `≠0` |
|  58–64   | `\x3A`–`\x40` |                         `\72`–`\100`                         |                          `:;<=>?@`                           |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|  65–70   | `\x41`–`\x46` |                        `\101`–`\106`                         |                           `ABCDEF`                           |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `≠0`                             |                             `0`                              | `0`  | `≠0` |
|  71–90   | `\x47`–`\x5A` |                        `\107`–`\132`                         |                  `GHIJKLMNOP` `QRSTUVWXYZ`                   |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `≠0`                             |                             `0`                              | `0`  | `0`  |
|  91–96   | `\x5B`–`\x60` |                        `\133`–`\140`                         |                  [\]^_\`  |**`0`**|**`≠0`**|**`0`**|**`0`**|**`≠0`**|**`0`**|**`≠0`**|**`≠0`**|**`≠0`**|**`0`**|**`0`**|**`0`**|
|  97–102  | `\x61`–`\x66` |                        `\141`–`\146`                         |                           `abcdef`                           |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `0`                              |                             `≠0`                             | `0`  | `≠0` |
| 103–122  | `\x67`–`\x7A` |                        `\147`–`\172`                         |                  `ghijklmnop` `qrstuvwxyz`                   |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `0`                              |                             `≠0`                             | `0`  | `0`  |
| 123–126  | `\x7B`–`\x7E` |                        `\173`–`\176`                         |                            `{|}~`                            |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|   127    |    `\x7F`     |                            `\177`                            |                        退格符 (`DEL`)                        |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |

### 根据数值格式的双向转换

| 在标头 `<stdlib.h>` 定义                                   |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [atof<br />](https://zh.cppreference.com/w/c/string/byte/atof) | 将字节字符串转换成浮点数 (函数)                              |
| [atoi <br />atol <br />atoll (C99)<br />](https://zh.cppreference.com/w/c/string/byte/atoi) | 将字节字符串转换成整数 (函数)                                |
| [strtol <br />strtoll (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtol) | 将字节字符串转换成整数 (函数)                                |
| [strtoul <br />strtoull (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtoul) | 将字节字符串转换成无符号整数 (函数)                          |
| [strtof (C99)<br />strtod (C99)<br />strtold <br />](https://zh.cppreference.com/w/c/string/byte/strtof) | 将字节字符串转换成浮点数 (函数)                              |
| [strfromf (C23)<br />strfromd (C23)<br />strfromld (C23)<br />](https://zh.cppreference.com/w/c/string/byte/strfromf) | 转换浮点数为字节字符串 (函数)                                |
| 在标头 `<inttypes.h>` 定义                                 |                                                              |
| [strtoimax (C99)<br />strtoumax (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtoimax) | 将字节字符串转换成 [intmax_t](https://zh.cppreference.com/w/c/types/integer) 或 [uintmax_t](https://zh.cppreference.com/w/c/types/integer) (函数) |

### 字符串操作

| 在标头 `<string.h>` 定义                                   |                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------ |
| [strcpy <br />strcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcpy) | 复制字符串给另一个 (函数)                              |
| [strncpy <br />strncpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strncpy) | 从字符串复制一定数量的字符到另一个 (函数)              |
| [strcat <br />strcat_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcat) | 连接两个字符串 (函数)                                  |
| [strncat <br />strncat_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strncat) | 连接两个字符串的一定数量字符 (函数)                    |
| [strxfrm<br />](https://zh.cppreference.com/w/c/string/byte/strxfrm) | 变换字符串，使得 strcmp 会产生同 strcoll 的结果 (函数) |
| [strdup (C23)<br />](https://zh.cppreference.com/w/c/string/byte/strdup) | 分配字符串的副本 (函数)                                |
| [strndup (C23)<br />](https://zh.cppreference.com/w/c/string/byte/strndup) | 分配拥有指定大小的字符串副本 (函数)                    |

### 字符串检验

| 在标头 `<string.h>` 定义                                   |                                                           |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [strlen <br />strnlen_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strlen) | 返回给定字符串的长度 (函数)                               |
| [strcmp<br />](https://zh.cppreference.com/w/c/string/byte/strcmp) | 比较两个字符串 (函数)                                     |
| [strncmp<br />](https://zh.cppreference.com/w/c/string/byte/strncmp) | 比较两个字符串的一定数量字符 (函数)                       |
| [strcoll<br />](https://zh.cppreference.com/w/c/string/byte/strcoll) | 比较两个字符串，根据当前本地环境 (函数)                   |
| [strchr<br />](https://zh.cppreference.com/w/c/string/byte/strchr) | 查找字符的首次出现 (函数)                                 |
| [strrchr<br />](https://zh.cppreference.com/w/c/string/byte/strrchr) | 查找字符的最后一次出现 (函数)                             |
| [strspn<br />](https://zh.cppreference.com/w/c/string/byte/strspn) | 返回由另一个字符串中的字符分割的最大起始段长度 (函数)     |
| [strcspn<br />](https://zh.cppreference.com/w/c/string/byte/strcspn) | 返回另一个字符串所不具有的字符分割的最大起始段长度 (函数) |
| [strpbrk<br />](https://zh.cppreference.com/w/c/string/byte/strpbrk) | 查找字符串中的任意字符在另一个字符串中的首个位置 (函数)   |
| [strstr<br />](https://zh.cppreference.com/w/c/string/byte/strstr) | 查找子串字符的首次出现 (函数)                             |
| [strtok <br />strtok_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strtok) | 查找字节字符串中的下一个记号 (函数)                       |

### 字符数组操作

| 在标头 `<string.h>` 定义                                   |                                                 |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [memchr<br />](https://zh.cppreference.com/w/c/string/byte/memchr) | 在数组中搜索字符的首次出现 (函数)               |
| [memcmp<br />](https://zh.cppreference.com/w/c/string/byte/memcmp) | 比较两块缓冲区 (函数)                           |
| [memset <br />memset_explicit (C23)<br />memset_s (C23)<br />](https://zh.cppreference.com/w/c/string/byte/memset) | 以字符填充缓冲区 (函数)                         |
| [memcpy <br />memcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memcpy) | 复制缓冲区到另一个 (函数)                       |
| [memmove <br />memmove_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memmove) | 移动缓冲区到另一个 (函数)                       |
| [memccpy (C23)<br />](https://zh.cppreference.com/w/c/string/byte/memccpy) | 复制缓冲区到另一个，在指定的分隔符后停止 (函数) |

### 杂项

| 在标头 `<string.h>` 定义                                   |                                 |
| ------------------------------------------------------------ | ------------------------------- |
| [strerror <br />strerror_s (C11)<br />strerrorlen_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strerror) | 返回给定错误码的文本版本 (函数) |

## 参阅

​	**空终止字节字符串**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte)**

