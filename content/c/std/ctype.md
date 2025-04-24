
+++
title = "<ctype.h>"
date = 2025-04-24T19:20:52+08:00
weight = 20
type = "docs"
description = "用来确定包含于字符数据中的类型的函数"
isCJKLanguage = true
draft = false

+++

## 类型




## 枚举




## 宏




## 函数



### isalnum

原址：[https://zh.cppreference.com/w/c/string/byte/isalnum](https://zh.cppreference.com/w/c/string/byte/isalnum)

作用：检查字符是否是字母或数字  (函数)

备注：
```c
// 在标头 <ctype.h> 定义
int isalnum( int ch );
```

​	检查给定的字符是否为当前 C 本地环境所分类的字母数字字符。在默认本地环境中，下列字符为字母数字：

- 数字（`0123456789`）
- 大写字母（`ABCDEFGHIJKLMNOPQRSTUVWXYZ`）
- 小写字母（`abcdefghijklmnopqrstuvwxyz`）

​	若 `ch` 的值不能表示为 `unsigned char` 且不等于 `[EOF](http://zh.cppreference.com/w/c/io)`，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |
|      |      |              |

**返回值**

​	若字符为字母数字字符，则为非零，否则为 `0`。

**示例**

​	演示以不同的本地环境（操作系统限定）使用 `isalnum()`。

```c
#include <ctype.h>
#include <locale.h>
#include <stdio.h>
 
int main(void)
{
    unsigned char c = '\xdf'; // ISO-8859-1 中的德文字母 ß 
 
    printf("isalnum('\\xdf') 在默认 C 本地环境中返回 %d\n", !!isalnum(c));
 
    if (setlocale(LC_CTYPE, "de_DE.iso88591"))
        printf("isalnum('\\xdf') 在 ISO-8859-1 本地环境中返回 %d\n", !!isalnum(c));
}
```

​	可能的输出：

```txt
isalnum('\xdf') 在默认 C 本地环境中返回 0
isalnum('\xdf') in ISO-8859-1 locale returned 1
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.4.1.1 The isalnum function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.4.1.1 The isalnum function （第 145 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.4.1.1 The isalnum function （第 200 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.4.1.1 The isalnum function （第 181 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.3.1.1 The isalnum function

**参阅**

| [iswalnum (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswalnum) | 检查宽字符是否为字母或数字 (函数) |
| ------------------------------------------------------------ | --------------------------------- |
| **isalnum** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/isalnum)** |                                   |

| ASCII 值 |     字符      | ​	[`<scntr>`](https://zh.cppreference.com/w/c/string/byte/iscntrl) [`<swcntr>`](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | ​	[`<sprin>`](https://zh.cppreference.com/w/c/string/byte/isprint) [`<swprin>`](https://zh.cppreference.com/w/c/string/wide/iswprint) | ​	[`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) [`<swspac>`](https://zh.cppreference.com/w/c/string/wide/iswspace) | ​	[`<sblan>`](https://zh.cppreference.com/w/c/string/byte/isblank) [`<swblan>`](https://zh.cppreference.com/w/c/string/wide/iswblank) | ​	[`<sgrap>`](https://zh.cppreference.com/w/c/string/byte/isgraph) [`<swgrap>`](https://zh.cppreference.com/w/c/string/wide/iswgraph) | ​	[`<spunc>`](https://zh.cppreference.com/w/c/string/byte/ispunct) [`<swpunc>`](https://zh.cppreference.com/w/c/string/wide/iswpunct) | ​	**`isalnum`** [`<swalnu>`](https://zh.cppreference.com/w/c/string/wide/iswalnum) | ​	[`<salph>`](https://zh.cppreference.com/w/c/string/byte/isalpha) [`<swalph>`](https://zh.cppreference.com/w/c/string/wide/iswalpha) | ​	[`<suppe>`](https://zh.cppreference.com/w/c/string/byte/isupper) [`<swuppe>`](https://zh.cppreference.com/w/c/string/wide/iswupper) | ​	[`<slowe>`](https://zh.cppreference.com/w/c/string/byte/islower) [`<swlowe>`](https://zh.cppreference.com/w/c/string/wide/iswlower) | ​	[`<sdigi>`](https://zh.cppreference.com/w/c/string/byte/isdigit) [`<swdigi>`](https://zh.cppreference.com/w/c/string/wide/iswdigit) | ​	[`<sxdigi>`](https://zh.cppreference.com/w/c/string/byte/isxdigit) [`<swxdigi>`](https://zh.cppreference.com/w/c/string/wide/iswxdigit) |          |          |
| :------: | :-----------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | -------- | -------- |
|  十进制  |   十六进制    |                            八进制                            |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |          |          |
|   0–8    |  `\x0`–`\x8`  |                          `\0`–`\10`                          |                      控制码 (`NUL` 等)                       |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    9     |     `\x9`     |                            `\11`                             |                        制表符 (`\t`)                         |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  10–13   |  `\xA`–`\xD`  |                         `\12`–`\15`                          |               空白符 (`\n`, `\v`, `\f`, `\r`)                |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  14–31   | `\xE`–`\x1F`  |                         `\16`–`\37`                          |                            控制码                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    32    |    `\x20`     |                            `\40`                             |                             空格                             |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  33–47   | `\x21`–`\x2F` |                         `\41`–`\57`                          |                      `!"#$%&'()*+,-./`                       |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  48–57   | `\x30`–`\x39` |                         `\60`–`\71`                          |                         `0123456789`                         |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`≠0`** | **`≠0`** |
|  58–64   | `\x3A`–`\x40` |                         `\72`–`\100`                         |                          `:;<=>?@`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  65–70   | `\x41`–`\x46` |                        `\101`–`\106`                         |                           `ABCDEF`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`≠0`** |
|  71–90   | `\x47`–`\x5A` |                        `\107`–`\132`                         |                  `GHIJKLMNOP` `QRSTUVWXYZ`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`0`**  |
|  91–96   | `\x5B`–`\x60` |                        `\133`–`\140`                         |                           `[\]^_``                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  97–102  | `\x61`–`\x66` |                        `\141`–`\146`                         |                           `abcdef`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`≠0`** |
| 103–122  | `\x67`–`\x7A` |                        `\147`–`\172`                         |                  `ghijklmnop` `qrstuvwxyz`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`0`**  |
| 123–126  | `\x7B`–`\x7E` |                        `\173`–`\176`                         |                            `{|}~`                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|   127    |    `\x7F`     |                            `\177`                            |                        退格符 (`DEL`)                        |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |





### isalpha

原址：[https://zh.cppreference.com/w/c/string/byte/isalpha](https://zh.cppreference.com/w/c/string/byte/isalpha)

作用：检查字符是否是字母  (函数)

备注：
```c
// 在标头 <ctype.h> 定义
int isalpha( int ch );
```

​	检查给定字符是否为字母字符，即是大写字母（`ABCDEFGHIJKLMNOPQRSTUVWXYZ`）或小写字母（`abcdefghijklmnopqrstuvwxyz`）。

​	在异于 `"C"` 的本地环境中，字母字符是 [isupper()](https://zh.cppreference.com/w/c/string/byte/isupper) 或 [islower()](https://zh.cppreference.com/w/c/string/byte/islower) 对其返回 `true` 的字符，或任何其他被本地环境认为是字母的字符。任何情况下，[iscntrl()](https://zh.cppreference.com/w/c/string/byte/iscntrl)、[isdigit()](https://zh.cppreference.com/w/c/string/byte/isdigit)、[ispunct()](https://zh.cppreference.com/w/c/string/byte/ispunct) 及 [isspace()](https://zh.cppreference.com/w/c/string/byte/isspace) 将对此字符返回 `false`。

​	若 `ch` 的值不能表示为 `unsigned char` 且不等于 `[EOF](http://zh.cppreference.com/w/c/io)`，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |
|      |      |              |

**返回值**

​	若字符为字母字符则为非零值，否则为零。

**示例**

​	演示以不同的本地环境使用 `isalpha()`（操作系统限定）。

```c
#include <ctype.h>
#include <locale.h>
#include <stdio.h>
 
int main(void)
{
    unsigned char c = '\xdf'; // ISO-8859-1 的德文字母 ß
 
    printf("isalpha('\\xdf') 在默认 C 本地环境中返回 %d\n", !!isalpha(c));
 
    setlocale(LC_CTYPE, "de_DE.iso88591");
    printf("isalpha('\\xdf') 在 ISO-8859-1 本地环境中返回 %d\n", !!isalpha(c));
}
```

​	可能的输出：

```txt
isalpha('\xdf') 在默认 C 本地环境中返回 0
isalpha('\xdf') 在 ISO-8859-1 本地环境中返回 1
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.4.1.2 The isalpha function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.4.1.2 The isalpha function （第 145 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.4.1.2 The isalpha function （第 200-201 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.4.1.2 The isalpha function （第 181-182 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.3.1.2 The isalpha function

**参阅**

| [iswalpha (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswalpha) | 检查宽字符是否为字母 (函数) |
| ------------------------------------------------------------ | --------------------------- |
| **isalpha** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/isalpha)** |                             |

| ASCII 值 |     字符      | ​	[`<scntr>`](https://zh.cppreference.com/w/c/string/byte/iscntrl) [`<swcntr>`](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | ​	[`<sprin>`](https://zh.cppreference.com/w/c/string/byte/isprint) [`<swprin>`](https://zh.cppreference.com/w/c/string/wide/iswprint) | ​	[`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) [`<swspac>`](https://zh.cppreference.com/w/c/string/wide/iswspace) | ​	[`<sblan>`](https://zh.cppreference.com/w/c/string/byte/isblank) [`<swblan>`](https://zh.cppreference.com/w/c/string/wide/iswblank) | ​	[`<sgrap>`](https://zh.cppreference.com/w/c/string/byte/isgraph) [`<swgrap>`](https://zh.cppreference.com/w/c/string/wide/iswgraph) | ​	[`<spunc>`](https://zh.cppreference.com/w/c/string/byte/ispunct) [`<swpunc>`](https://zh.cppreference.com/w/c/string/wide/iswpunct) | ​	[`<salnu>`](https://zh.cppreference.com/w/c/string/byte/isalnum) [`<swalnu>`](https://zh.cppreference.com/w/c/string/wide/iswalnum) | ​	**`isalpha`** [`<swalph>`](https://zh.cppreference.com/w/c/string/wide/iswalpha) | ​	[`<suppe>`](https://zh.cppreference.com/w/c/string/byte/isupper) [`<swuppe>`](https://zh.cppreference.com/w/c/string/wide/iswupper) | ​	[`<slowe>`](https://zh.cppreference.com/w/c/string/byte/islower) [`<swlowe>`](https://zh.cppreference.com/w/c/string/wide/iswlower) | ​	[`<sdigi>`](https://zh.cppreference.com/w/c/string/byte/isdigit) [`<swdigi>`](https://zh.cppreference.com/w/c/string/wide/iswdigit) | ​	[`<sxdigi>`](https://zh.cppreference.com/w/c/string/byte/isxdigit) [`<swxdigi>`](https://zh.cppreference.com/w/c/string/wide/iswxdigit) |          |          |
| :------: | :-----------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | -------- | -------- |
|  十进制  |   十六进制    |                            八进制                            |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |          |          |
|   0–8    |  `\x0`–`\x8`  |                          `\0`–`\10`                          |                      控制码 (`NUL` 等)                       |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    9     |     `\x9`     |                            `\11`                             |                        制表符 (`\t`)                         |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  10–13   |  `\xA`–`\xD`  |                         `\12`–`\15`                          |               空白符 (`\n`, `\v`, `\f`, `\r`)                |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  14–31   | `\xE`–`\x1F`  |                         `\16`–`\37`                          |                            控制码                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    32    |    `\x20`     |                            `\40`                             |                             空格                             |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  33–47   | `\x21`–`\x2F` |                         `\41`–`\57`                          |                      `!"#$%&'()*+,-./`                       |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  48–57   | `\x30`–`\x39` |                         `\60`–`\71`                          |                         `0123456789`                         |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`≠0`** | **`≠0`** |
|  58–64   | `\x3A`–`\x40` |                         `\72`–`\100`                         |                          `:;<=>?@`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  65–70   | `\x41`–`\x46` |                        `\101`–`\106`                         |                           `ABCDEF`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`≠0`** |
|  71–90   | `\x47`–`\x5A` |                        `\107`–`\132`                         |                  `GHIJKLMNOP` `QRSTUVWXYZ`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`0`**  |
|  91–96   | `\x5B`–`\x60` |                        `\133`–`\140`                         |                           `[\]^_``                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  97–102  | `\x61`–`\x66` |                        `\141`–`\146`                         |                           `abcdef`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`≠0`** |
| 103–122  | `\x67`–`\x7A` |                        `\147`–`\172`                         |                  `ghijklmnop` `qrstuvwxyz`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`0`**  |
| 123–126  | `\x7B`–`\x7E` |                        `\173`–`\176`                         |                            `{|}~`                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|   127    |    `\x7F`     |                            `\177`                            |                        退格符 (`DEL`)                        |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |





### isblank

原址：[https://zh.cppreference.com/w/c/string/byte/isblank](https://zh.cppreference.com/w/c/string/byte/isblank)

作用：检查字符是否是空格字符   (函数)

备注：
```c
// 在标头 <ctype.h> 定义
int isblank( int ch );// (C99 起)
```

​	检查给定的字符在当前的 C 本地环境中是否为空白字符。在默认 C 本地环境中，只有空格（`0x20`）与水平制表符（`0x09`）被分类为空白字符。

​	若 `ch` 的值不能表示为 `unsigned char` 且不等于 `[EOF](http://zh.cppreference.com/w/c/io)`，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |
|      |      |              |

**返回值**

​	若字符为空白字符则为非零值，否则为零。

**示例**

```c
#include <ctype.h>
#include <limits.h>
#include <stdio.h>
 
int main(void)
{
    for (int ndx = 0; ndx != UCHAR_MAX; ++ndx)
        if (isblank(ndx))
            printf("0x%02x\n", ndx);
}
```

​	输出：

```txt
0x09
0x20
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.4.1.3 The isblank function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.4.1.3 The isblank function （第 145 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.4.1.3 The isblank function （第 201 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.4.1.3 The isblank function （第 182 页）

**参阅**

| [iswblank (C99)<br />](https://zh.cppreference.com/w/c/string/wide/iswblank) | 检查宽字符是否为空格 (函数) |
| ------------------------------------------------------------ | --------------------------- |
| **isblank** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/isblank)** |                             |

| ASCII 值 |     字符      | ​	[`<scntr>`](https://zh.cppreference.com/w/c/string/byte/iscntrl) [`<swcntr>`](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | ​	[`<sprin>`](https://zh.cppreference.com/w/c/string/byte/isprint) [`<swprin>`](https://zh.cppreference.com/w/c/string/wide/iswprint) | ​	[`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) [`<swspac>`](https://zh.cppreference.com/w/c/string/wide/iswspace) | ​	**`isblank`** [`<swblan>`](https://zh.cppreference.com/w/c/string/wide/iswblank) | ​	[`<sgrap>`](https://zh.cppreference.com/w/c/string/byte/isgraph) [`<swgrap>`](https://zh.cppreference.com/w/c/string/wide/iswgraph) | ​	[`<spunc>`](https://zh.cppreference.com/w/c/string/byte/ispunct) [`<swpunc>`](https://zh.cppreference.com/w/c/string/wide/iswpunct) | ​	[`<salnu>`](https://zh.cppreference.com/w/c/string/byte/isalnum) [`<swalnu>`](https://zh.cppreference.com/w/c/string/wide/iswalnum) | ​	[`<salph>`](https://zh.cppreference.com/w/c/string/byte/isalpha) [`<swalph>`](https://zh.cppreference.com/w/c/string/wide/iswalpha) | ​	[`<suppe>`](https://zh.cppreference.com/w/c/string/byte/isupper) [`<swuppe>`](https://zh.cppreference.com/w/c/string/wide/iswupper) | ​	[`<slowe>`](https://zh.cppreference.com/w/c/string/byte/islower) [`<swlowe>`](https://zh.cppreference.com/w/c/string/wide/iswlower) | ​	[`<sdigi>`](https://zh.cppreference.com/w/c/string/byte/isdigit) [`<swdigi>`](https://zh.cppreference.com/w/c/string/wide/iswdigit) | ​	[`<sxdigi>`](https://zh.cppreference.com/w/c/string/byte/isxdigit) [`<swxdigi>`](https://zh.cppreference.com/w/c/string/wide/iswxdigit) |          |          |
| :------: | :-----------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | -------- | -------- |
|  十进制  |   十六进制    |                            八进制                            |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |          |          |
|   0–8    |  `\x0`–`\x8`  |                          `\0`–`\10`                          |                      控制码 (`NUL` 等)                       |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    9     |     `\x9`     |                            `\11`                             |                        制表符 (`\t`)                         |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  10–13   |  `\xA`–`\xD`  |                         `\12`–`\15`                          |               空白符 (`\n`, `\v`, `\f`, `\r`)                |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  14–31   | `\xE`–`\x1F`  |                         `\16`–`\37`                          |                            控制码                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    32    |    `\x20`     |                            `\40`                             |                             空格                             |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  33–47   | `\x21`–`\x2F` |                         `\41`–`\57`                          |                      `!"#$%&'()*+,-./`                       |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  48–57   | `\x30`–`\x39` |                         `\60`–`\71`                          |                         `0123456789`                         |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`≠0`** | **`≠0`** |
|  58–64   | `\x3A`–`\x40` |                         `\72`–`\100`                         |                          `:;<=>?@`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  65–70   | `\x41`–`\x46` |                        `\101`–`\106`                         |                           `ABCDEF`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`≠0`** |
|  71–90   | `\x47`–`\x5A` |                        `\107`–`\132`                         |                  `GHIJKLMNOP` `QRSTUVWXYZ`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`0`**  |
|  91–96   | `\x5B`–`\x60` |                        `\133`–`\140`                         |                           `[\]^_``                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  97–102  | `\x61`–`\x66` |                        `\141`–`\146`                         |                           `abcdef`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`≠0`** |
| 103–122  | `\x67`–`\x7A` |                        `\147`–`\172`                         |                  `ghijklmnop` `qrstuvwxyz`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`0`**  |
| 123–126  | `\x7B`–`\x7E` |                        `\173`–`\176`                         |                            `{|}~`                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|   127    |    `\x7F`     |                            `\177`                            |                        退格符 (`DEL`)                        |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |





### iscntrl

原址：[https://zh.cppreference.com/w/c/string/byte/iscntrl](https://zh.cppreference.com/w/c/string/byte/iscntrl)

作用：检查字符是否是控制字符  (函数)

备注：
```c
// 在标头 <ctype.h> 定义
int iscntrl( int ch );
```

​	检查给定字符是否为控制字符，即编码 `[``0x00``, ``0x1F``]` 及 `0x7F`。

​	若 `ch` 的值不能表示为 `unsigned char` 且不等于 `[EOF](http://zh.cppreference.com/w/c/io)`，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |
|      |      |              |

**返回值**

​	若字符为控制字符则为非零，否则为零。

**示例**

```c
#include <ctype.h>
#include <locale.h>
#include <stdio.h>
 
int main(void)
{
    unsigned char c = '\x94'; // ISO-8859-1 的控制码 CCH
    printf("在默认的 C 本地环境中，\\x94 %s是控制字符\n",
           iscntrl(c) ? "" : "不" );
    setlocale(LC_ALL, "en_GB.iso88591");
    printf("在 ISO-8859-1 本地环境中，\\x94 %s是控制字符\n",
           iscntrl(c) ? "" : "不" );
}
```

​	输出：

```txt
在默认的 C 本地环境中，\x94 不是控制字符
在 ISO-8859-1 本地环境中，\x94 是控制字符
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.4.1.4 The iscntrl function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.4.1.4 The iscntrl function （第 146 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.4.1.4 The iscntrl function （第 201 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.4.1.4 The iscntrl function （第 182 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.3.1.3 The iscntrl function

**参阅**

| [iswcntrl (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | 检查宽字符是否为控制字符 (函数) |
| ------------------------------------------------------------ | ------------------------------- |
| **iscntrl** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/iscntrl)** |                                 |

| ASCII 值 |     字符      | ​	**`iscntrl`** [`<swcntr>`](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | ​	[`<sprin>`](https://zh.cppreference.com/w/c/string/byte/isprint) [`<swprin>`](https://zh.cppreference.com/w/c/string/wide/iswprint) | ​	[`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) [`<swspac>`](https://zh.cppreference.com/w/c/string/wide/iswspace) | ​	[`<sblan>`](https://zh.cppreference.com/w/c/string/byte/isblank) [`<swblan>`](https://zh.cppreference.com/w/c/string/wide/iswblank) | ​	[`<sgrap>`](https://zh.cppreference.com/w/c/string/byte/isgraph) [`<swgrap>`](https://zh.cppreference.com/w/c/string/wide/iswgraph) | ​	[`<spunc>`](https://zh.cppreference.com/w/c/string/byte/ispunct) [`<swpunc>`](https://zh.cppreference.com/w/c/string/wide/iswpunct) | ​	[`<salnu>`](https://zh.cppreference.com/w/c/string/byte/isalnum) [`<swalnu>`](https://zh.cppreference.com/w/c/string/wide/iswalnum) | ​	[`<salph>`](https://zh.cppreference.com/w/c/string/byte/isalpha) [`<swalph>`](https://zh.cppreference.com/w/c/string/wide/iswalpha) | ​	[`<suppe>`](https://zh.cppreference.com/w/c/string/byte/isupper) [`<swuppe>`](https://zh.cppreference.com/w/c/string/wide/iswupper) | ​	[`<slowe>`](https://zh.cppreference.com/w/c/string/byte/islower) [`<swlowe>`](https://zh.cppreference.com/w/c/string/wide/iswlower) | ​	[`<sdigi>`](https://zh.cppreference.com/w/c/string/byte/isdigit) [`<swdigi>`](https://zh.cppreference.com/w/c/string/wide/iswdigit) | ​	[`<sxdigi>`](https://zh.cppreference.com/w/c/string/byte/isxdigit) [`<swxdigi>`](https://zh.cppreference.com/w/c/string/wide/iswxdigit) |          |          |
| :------: | :-----------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | -------- | -------- |
|  十进制  |   十六进制    |                            八进制                            |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |          |          |
|   0–8    |  `\x0`–`\x8`  |                          `\0`–`\10`                          |                      控制码 (`NUL` 等)                       |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    9     |     `\x9`     |                            `\11`                             |                        制表符 (`\t`)                         |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  10–13   |  `\xA`–`\xD`  |                         `\12`–`\15`                          |               空白符 (`\n`, `\v`, `\f`, `\r`)                |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  14–31   | `\xE`–`\x1F`  |                         `\16`–`\37`                          |                            控制码                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    32    |    `\x20`     |                            `\40`                             |                             空格                             |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  33–47   | `\x21`–`\x2F` |                         `\41`–`\57`                          |                      `!"#$%&'()*+,-./`                       |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  48–57   | `\x30`–`\x39` |                         `\60`–`\71`                          |                         `0123456789`                         |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`≠0`** | **`≠0`** |
|  58–64   | `\x3A`–`\x40` |                         `\72`–`\100`                         |                          `:;<=>?@`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  65–70   | `\x41`–`\x46` |                        `\101`–`\106`                         |                           `ABCDEF`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`≠0`** |
|  71–90   | `\x47`–`\x5A` |                        `\107`–`\132`                         |                  `GHIJKLMNOP` `QRSTUVWXYZ`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`0`**  |
|  91–96   | `\x5B`–`\x60` |                        `\133`–`\140`                         |                           `[\]^_``                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  97–102  | `\x61`–`\x66` |                        `\141`–`\146`                         |                           `abcdef`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`≠0`** |
| 103–122  | `\x67`–`\x7A` |                        `\147`–`\172`                         |                  `ghijklmnop` `qrstuvwxyz`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`0`**  |
| 123–126  | `\x7B`–`\x7E` |                        `\173`–`\176`                         |                            `{|}~`                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|   127    |    `\x7F`     |                            `\177`                            |                        退格符 (`DEL`)                        |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |





### isdigit

原址：[https://zh.cppreference.com/w/c/string/byte/isdigit](https://zh.cppreference.com/w/c/string/byte/isdigit)

作用：检查字符是否是数字  (函数)

备注：
```c
// 在标头 <ctype.h> 定义
int isdigit( int ch );
```

​	检查给定的字符是否为数字字符（`0123456789`）。

​	若 `ch` 的值不能表示为 `unsigned char` 且不等于 `[EOF](http://zh.cppreference.com/w/c/io)`，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |
|      |      |              |

**返回值**

​	若字符为数字则为非零值，否则为零。

**注解**

​	`isdigit` 与 [isxdigit](https://zh.cppreference.com/w/c/string/byte/isxdigit) 是仅有的不受当前安装的 C 本地环境影响的标准窄字符分类函数，尽管一些实现（例如 Microsoft 于 [1252 代码页](https://en.wikipedia.org/wiki/Windows-1252)）可能将额外的单字节字符分类为数字。

**示例**

```c
#include <ctype.h>
#include <limits.h>
#include <stdio.h>
 
int main(void)
{
    for (int ndx=0; ndx<=UCHAR_MAX; ++ndx)
        if (isdigit(ndx))
            printf("%c", ndx);
    printf("\n");
}
```

​	输出：

```txt
0123456789
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.4.1.5 The isdigit function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.4.1.5 The isdigit function （第 146 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.4.1.5 The isdigit function （第 201 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.4.1.5 The isdigit function （第 182 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.3.1.4 The isdigit function

**参阅**

| [iswdigit (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswdigit) | 检查宽字符是否为数字 (函数) |
| ------------------------------------------------------------ | --------------------------- |
| **isdigit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/isdigit)** |                             |

| ASCII 值 |     字符      | ​	[`<scntr>`](https://zh.cppreference.com/w/c/string/byte/iscntrl) [`<swcntr>`](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | ​	[`<sprin>`](https://zh.cppreference.com/w/c/string/byte/isprint) [`<swprin>`](https://zh.cppreference.com/w/c/string/wide/iswprint) | ​	[`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) [`<swspac>`](https://zh.cppreference.com/w/c/string/wide/iswspace) | ​	[`<sblan>`](https://zh.cppreference.com/w/c/string/byte/isblank) [`<swblan>`](https://zh.cppreference.com/w/c/string/wide/iswblank) | ​	[`<sgrap>`](https://zh.cppreference.com/w/c/string/byte/isgraph) [`<swgrap>`](https://zh.cppreference.com/w/c/string/wide/iswgraph) | ​	[`<spunc>`](https://zh.cppreference.com/w/c/string/byte/ispunct) [`<swpunc>`](https://zh.cppreference.com/w/c/string/wide/iswpunct) | ​	[`<salnu>`](https://zh.cppreference.com/w/c/string/byte/isalnum) [`<swalnu>`](https://zh.cppreference.com/w/c/string/wide/iswalnum) | ​	[`<salph>`](https://zh.cppreference.com/w/c/string/byte/isalpha) [`<swalph>`](https://zh.cppreference.com/w/c/string/wide/iswalpha) | ​	[`<suppe>`](https://zh.cppreference.com/w/c/string/byte/isupper) [`<swuppe>`](https://zh.cppreference.com/w/c/string/wide/iswupper) | ​	[`<slowe>`](https://zh.cppreference.com/w/c/string/byte/islower) [`<swlowe>`](https://zh.cppreference.com/w/c/string/wide/iswlower) | ​	**`isdigit`** [`<swdigi>`](https://zh.cppreference.com/w/c/string/wide/iswdigit) | ​	[`<sxdigi>`](https://zh.cppreference.com/w/c/string/byte/isxdigit) [`<swxdigi>`](https://zh.cppreference.com/w/c/string/wide/iswxdigit) |          |          |
| :------: | :-----------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | -------- | -------- |
|  十进制  |   十六进制    |                            八进制                            |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |          |          |
|   0–8    |  `\x0`–`\x8`  |                          `\0`–`\10`                          |                      控制码 (`NUL` 等)                       |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    9     |     `\x9`     |                            `\11`                             |                        制表符 (`\t`)                         |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  10–13   |  `\xA`–`\xD`  |                         `\12`–`\15`                          |               空白符 (`\n`, `\v`, `\f`, `\r`)                |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  14–31   | `\xE`–`\x1F`  |                         `\16`–`\37`                          |                            控制码                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    32    |    `\x20`     |                            `\40`                             |                             空格                             |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  33–47   | `\x21`–`\x2F` |                         `\41`–`\57`                          |                      `!"#$%&'()*+,-./`                       |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  48–57   | `\x30`–`\x39` |                         `\60`–`\71`                          |                         `0123456789`                         |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`≠0`** | **`≠0`** |
|  58–64   | `\x3A`–`\x40` |                         `\72`–`\100`                         |                          `:;<=>?@`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  65–70   | `\x41`–`\x46` |                        `\101`–`\106`                         |                           `ABCDEF`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`≠0`** |
|  71–90   | `\x47`–`\x5A` |                        `\107`–`\132`                         |                  `GHIJKLMNOP` `QRSTUVWXYZ`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`0`**  |
|  91–96   | `\x5B`–`\x60` |                        `\133`–`\140`                         |                           `[\]^_``                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  97–102  | `\x61`–`\x66` |                        `\141`–`\146`                         |                           `abcdef`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`≠0`** |
| 103–122  | `\x67`–`\x7A` |                        `\147`–`\172`                         |                  `ghijklmnop` `qrstuvwxyz`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`0`**  |
| 123–126  | `\x7B`–`\x7E` |                        `\173`–`\176`                         |                            `{|}~`                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|   127    |    `\x7F`     |                            `\177`                            |                        退格符 (`DEL`)                        |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |





### isgraph

原址：[https://zh.cppreference.com/w/c/string/byte/isgraph](https://zh.cppreference.com/w/c/string/byte/isgraph)

作用：检查字符是否是图形字符  (函数)

备注：
```c
// 在标头 <ctype.h> 定义
int isgraph( int ch );
```

​	检查给定的字符是否拥有图形表示，即它是数字（`0123456789`）、大写字母（`ABCDEFGHIJKLMNOPQRSTUVWXYZ`）、小写字母（`abcdefghijklmnopqrstuvwxyz`）或标点字符（`!"#$%&'()*+,-./:;<=>?@[\]^_`{|}~`），或任何指定于当前 C 本地环境的图形字符之一。

​	若 `ch` 的值不能表示为 `unsigned char` 且不等于 `[EOF](http://zh.cppreference.com/w/c/io)`，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |
|      |      |              |

**返回值**

​	若字符拥有图形表示，则为非零，否则为零。

**示例**

```c
#include <ctype.h>
#include <locale.h>
#include <stdio.h>
 
int main(void)
{
    unsigned char c = '\xb6'; // ISO-8859-1 的字符 ¶
    printf("在默认的 C 本地环境中，\\xb6 %s是图形字符\n",
           isgraph(c) ? "" : "不" );
    setlocale(LC_ALL, "en_GB.iso88591");
    printf("在 ISO-8859-1 本地环境中，\\xb6 %是图形字符\n",
           isgraph(c) ? "" : "不" );
}
```

​	可能的输出：

```txt
在默认的 C 本地环境中，\xb6 不是图形字符
在 ISO-8859-1 本地环境中，\xb6 是图形字符
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.4.1.6 The isgraph function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.4.1.6 The isgraph function （第 146 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.4.1.6 The isgraph function （第 201-202 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.4.1.6 The isgraph function （第 182-183 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.3.1.5 The isgraph function

**参阅**

| [iswgraph (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswgraph) | 检查宽字符是否为图形字符 (函数) |
| ------------------------------------------------------------ | ------------------------------- |
| **isgraph** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/isgraph)** |                                 |

| ASCII 值 |     字符      | ​	[`<scntr>`](https://zh.cppreference.com/w/c/string/byte/iscntrl) [`<swcntr>`](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | ​	[`<sprin>`](https://zh.cppreference.com/w/c/string/byte/isprint) [`<swprin>`](https://zh.cppreference.com/w/c/string/wide/iswprint) | ​	[`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) [`<swspac>`](https://zh.cppreference.com/w/c/string/wide/iswspace) | ​	[`<sblan>`](https://zh.cppreference.com/w/c/string/byte/isblank) [`<swblan>`](https://zh.cppreference.com/w/c/string/wide/iswblank) | ​	**`isgraph`** [`<swgrap>`](https://zh.cppreference.com/w/c/string/wide/iswgraph) | ​	[`<spunc>`](https://zh.cppreference.com/w/c/string/byte/ispunct) [`<swpunc>`](https://zh.cppreference.com/w/c/string/wide/iswpunct) | ​	[`<salnu>`](https://zh.cppreference.com/w/c/string/byte/isalnum) [`<swalnu>`](https://zh.cppreference.com/w/c/string/wide/iswalnum) | ​	[`<salph>`](https://zh.cppreference.com/w/c/string/byte/isalpha) [`<swalph>`](https://zh.cppreference.com/w/c/string/wide/iswalpha) | ​	[`<suppe>`](https://zh.cppreference.com/w/c/string/byte/isupper) [`<swuppe>`](https://zh.cppreference.com/w/c/string/wide/iswupper) | ​	[`<slowe>`](https://zh.cppreference.com/w/c/string/byte/islower) [`<swlowe>`](https://zh.cppreference.com/w/c/string/wide/iswlower) | ​	[`<sdigi>`](https://zh.cppreference.com/w/c/string/byte/isdigit) [`<swdigi>`](https://zh.cppreference.com/w/c/string/wide/iswdigit) | ​	[`<sxdigi>`](https://zh.cppreference.com/w/c/string/byte/isxdigit) [`<swxdigi>`](https://zh.cppreference.com/w/c/string/wide/iswxdigit) |          |          |
| :------: | :-----------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | -------- | -------- |
|  十进制  |   十六进制    |                            八进制                            |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |          |          |
|   0–8    |  `\x0`–`\x8`  |                          `\0`–`\10`                          |                      控制码 (`NUL` 等)                       |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    9     |     `\x9`     |                            `\11`                             |                        制表符 (`\t`)                         |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  10–13   |  `\xA`–`\xD`  |                         `\12`–`\15`                          |               空白符 (`\n`, `\v`, `\f`, `\r`)                |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  14–31   | `\xE`–`\x1F`  |                         `\16`–`\37`                          |                            控制码                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    32    |    `\x20`     |                            `\40`                             |                             空格                             |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  33–47   | `\x21`–`\x2F` |                         `\41`–`\57`                          |                      `!"#$%&'()*+,-./`                       |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  48–57   | `\x30`–`\x39` |                         `\60`–`\71`                          |                         `0123456789`                         |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`≠0`** | **`≠0`** |
|  58–64   | `\x3A`–`\x40` |                         `\72`–`\100`                         |                          `:;<=>?@`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  65–70   | `\x41`–`\x46` |                        `\101`–`\106`                         |                           `ABCDEF`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`≠0`** |
|  71–90   | `\x47`–`\x5A` |                        `\107`–`\132`                         |                  `GHIJKLMNOP` `QRSTUVWXYZ`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`0`**  |
|  91–96   | `\x5B`–`\x60` |                        `\133`–`\140`                         |                           `[\]^_``                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  97–102  | `\x61`–`\x66` |                        `\141`–`\146`                         |                           `abcdef`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`≠0`** |
| 103–122  | `\x67`–`\x7A` |                        `\147`–`\172`                         |                  `ghijklmnop` `qrstuvwxyz`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`0`**  |
| 123–126  | `\x7B`–`\x7E` |                        `\173`–`\176`                         |                            `{|}~`                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|   127    |    `\x7F`     |                            `\177`                            |                        退格符 (`DEL`)                        |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |





### islower

原址：[https://zh.cppreference.com/w/c/string/byte/islower](https://zh.cppreference.com/w/c/string/byte/islower)

作用：检查字符是否是小写字母  (函数)

备注：
```c
// 在标头 <ctype.h> 定义
int islower( int ch );
```

​	检查给定字符是否按照当前 C 本地环境分类为小写字符。默认 "C" 本地环境中，`islower` 仅对小写字母（`abcdefghijklmnopqrstuvwxyz`）返回非零值。

​	若 `islower` 返回非零值，则保证同一 C 本地环境中 `[iscntrl](http://zh.cppreference.com/w/c/string/byte/iscntrl)`、`[isdigit](http://zh.cppreference.com/w/c/string/byte/isdigit)`、`[ispunct](http://zh.cppreference.com/w/c/string/byte/ispunct)` 和 `[isspace](http://zh.cppreference.com/w/c/string/byte/isspace)` 对同一字符返回零。

​	若 `ch` 不可表示为 `unsigned char` 且不等于 `[EOF](http://zh.cppreference.com/w/c/io)`，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |
|      |      |              |

**返回值**

​	若字符为小写字母则为非零值，否则为零。

**示例**

```c
#include <ctype.h>
#include <locale.h>
#include <stdio.h>
 
int main(void)
{
    unsigned char c = '\xe5'; // ISO-8859-1 的字母 å
    printf("在默认的 C 本地环境中，\\xe5 %s是小写字母\n",
           islower(c) ? "" : "不" );
    setlocale(LC_ALL, "en_GB.iso88591");
    printf("在 ISO-8859-1 本地环境中，\\xe5 %s是小写字母\n",
           islower(c) ? "" : "不" );
}
```

​	可能的输出：

```txt
在默认的 C 本地环境中，\xe5 不是小写字母
在 ISO-8859-1 本地环境中，\xe5 是小写字母
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.4.1.7 The islower function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.4.1.7 The islower function （第 146 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.4.1.7 The islower function （第 202 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.4.1.7 The islower function （第 183 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.3.1.6 The islower function

**参阅**

| [iswlower (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswlower) | 检查宽字符是否为小写 (函数) |
| ------------------------------------------------------------ | --------------------------- |
| **islower** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/islower)** |                             |

| ASCII 值 |     字符      | ​	[`<scntr>`](https://zh.cppreference.com/w/c/string/byte/iscntrl) [`<swcntr>`](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | ​	[`<sprin>`](https://zh.cppreference.com/w/c/string/byte/isprint) [`<swprin>`](https://zh.cppreference.com/w/c/string/wide/iswprint) | ​	[`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) [`<swspac>`](https://zh.cppreference.com/w/c/string/wide/iswspace) | ​	[`<sblan>`](https://zh.cppreference.com/w/c/string/byte/isblank) [`<swblan>`](https://zh.cppreference.com/w/c/string/wide/iswblank) | ​	[`<sgrap>`](https://zh.cppreference.com/w/c/string/byte/isgraph) [`<swgrap>`](https://zh.cppreference.com/w/c/string/wide/iswgraph) | ​	[`<spunc>`](https://zh.cppreference.com/w/c/string/byte/ispunct) [`<swpunc>`](https://zh.cppreference.com/w/c/string/wide/iswpunct) | ​	[`<salnu>`](https://zh.cppreference.com/w/c/string/byte/isalnum) [`<swalnu>`](https://zh.cppreference.com/w/c/string/wide/iswalnum) | ​	[`<salph>`](https://zh.cppreference.com/w/c/string/byte/isalpha) [`<swalph>`](https://zh.cppreference.com/w/c/string/wide/iswalpha) | ​	[`<suppe>`](https://zh.cppreference.com/w/c/string/byte/isupper) [`<swuppe>`](https://zh.cppreference.com/w/c/string/wide/iswupper) | ​	**`islower`** [`<swlowe>`](https://zh.cppreference.com/w/c/string/wide/iswlower) | ​	[`<sdigi>`](https://zh.cppreference.com/w/c/string/byte/isdigit) [`<swdigi>`](https://zh.cppreference.com/w/c/string/wide/iswdigit) | ​	[`<sxdigi>`](https://zh.cppreference.com/w/c/string/byte/isxdigit) [`<swxdigi>`](https://zh.cppreference.com/w/c/string/wide/iswxdigit) |          |          |
| :------: | :-----------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | -------- | -------- |
|  十进制  |   十六进制    |                            八进制                            |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |          |          |
|   0–8    |  `\x0`–`\x8`  |                          `\0`–`\10`                          |                      控制码 (`NUL` 等)                       |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    9     |     `\x9`     |                            `\11`                             |                        制表符 (`\t`)                         |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  10–13   |  `\xA`–`\xD`  |                         `\12`–`\15`                          |               空白符 (`\n`, `\v`, `\f`, `\r`)                |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  14–31   | `\xE`–`\x1F`  |                         `\16`–`\37`                          |                            控制码                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    32    |    `\x20`     |                            `\40`                             |                             空格                             |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  33–47   | `\x21`–`\x2F` |                         `\41`–`\57`                          |                      `!"#$%&'()*+,-./`                       |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  48–57   | `\x30`–`\x39` |                         `\60`–`\71`                          |                         `0123456789`                         |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`≠0`** | **`≠0`** |
|  58–64   | `\x3A`–`\x40` |                         `\72`–`\100`                         |                          `:;<=>?@`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  65–70   | `\x41`–`\x46` |                        `\101`–`\106`                         |                           `ABCDEF`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`≠0`** |
|  71–90   | `\x47`–`\x5A` |                        `\107`–`\132`                         |                  `GHIJKLMNOP` `QRSTUVWXYZ`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`0`**  |
|  91–96   | `\x5B`–`\x60` |                        `\133`–`\140`                         |                           `[\]^_``                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  97–102  | `\x61`–`\x66` |                        `\141`–`\146`                         |                           `abcdef`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`≠0`** |
| 103–122  | `\x67`–`\x7A` |                        `\147`–`\172`                         |                  `ghijklmnop` `qrstuvwxyz`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`0`**  |
| 123–126  | `\x7B`–`\x7E` |                        `\173`–`\176`                         |                            `{|}~`                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|   127    |    `\x7F`     |                            `\177`                            |                        退格符 (`DEL`)                        |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |





### isprint

原址：[https://zh.cppreference.com/w/c/string/byte/isprint](https://zh.cppreference.com/w/c/string/byte/isprint)

作用：检查字符是否是可打印字符  (函数)

备注：
```c
// 在标头 <ctype.h> 定义
int isprint( int ch );
```

​	检查给定的字符能否被打印，即为数字（`0123456789`）、大写字母（`ABCDEFGHIJKLMNOPQRSTUVWXYZ`）、小写字母（`abcdefghijklmnopqrstuvwxyz`）、标点字符（`!"#$%&'()*+,-./:;<=>?@[\]^_`{|}~`）或空格之一，或任何当前 C 本地环境分类为可打印的字符。

​	若 `ch` 的值不能表示为 `unsigned char` 且不等于 `[EOF](http://zh.cppreference.com/w/c/io)`，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |
|      |      |              |

**返回值**

​	若字符能被打印则为非零，否则为零。

**示例**

```c
#include <ctype.h>
#include <locale.h>
#include <stdio.h>
 
int main(void)
{
    unsigned char c = '\xa0'; // ISO-8859-1 的无中断空格
    printf("在默认的 C 本地环境中，\\xa0 %s是可打印字符\n", isprint(c)?"":"不");
    setlocale(LC_ALL, "en_GB.iso88591");
    printf("在 ISO-8859-1 本地环境中，\\xa0 %s是可打印字符\n", isprint(c)?"":"不");
}
```

​	可能的输出：

```txt
在默认的 C 本地环境中，\xa0 不是可打印字符
在 ISO-8859-1 本地环境中，\xa0 是可打印字符
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.4.1.8 The isprint function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.4.1.8 The isprint function （第 146 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.4.1.8 The isprint function （第 202 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.4.1.8 The isprint function （第 183 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.3.1.7 The isprint function

**参阅**

| [iswprint (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswprint) | 检查宽字符是否为打印字符 (函数) |
| ------------------------------------------------------------ | ------------------------------- |
| **isprint** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/isprint)** |                                 |

| ASCII 值 |     字符      | ​	[`<scntr>`](https://zh.cppreference.com/w/c/string/byte/iscntrl) [`<swcntr>`](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | ​	**`isprint`** [`<swprin>`](https://zh.cppreference.com/w/c/string/wide/iswprint) | ​	[`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) [`<swspac>`](https://zh.cppreference.com/w/c/string/wide/iswspace) | ​	[`<sblan>`](https://zh.cppreference.com/w/c/string/byte/isblank) [`<swblan>`](https://zh.cppreference.com/w/c/string/wide/iswblank) | ​	[`<sgrap>`](https://zh.cppreference.com/w/c/string/byte/isgraph) [`<swgrap>`](https://zh.cppreference.com/w/c/string/wide/iswgraph) | ​	[`<spunc>`](https://zh.cppreference.com/w/c/string/byte/ispunct) [`<swpunc>`](https://zh.cppreference.com/w/c/string/wide/iswpunct) | ​	[`<salnu>`](https://zh.cppreference.com/w/c/string/byte/isalnum) [`<swalnu>`](https://zh.cppreference.com/w/c/string/wide/iswalnum) | ​	[`<salph>`](https://zh.cppreference.com/w/c/string/byte/isalpha) [`<swalph>`](https://zh.cppreference.com/w/c/string/wide/iswalpha) | ​	[`<suppe>`](https://zh.cppreference.com/w/c/string/byte/isupper) [`<swuppe>`](https://zh.cppreference.com/w/c/string/wide/iswupper) | ​	[`<slowe>`](https://zh.cppreference.com/w/c/string/byte/islower) [`<swlowe>`](https://zh.cppreference.com/w/c/string/wide/iswlower) | ​	[`<sdigi>`](https://zh.cppreference.com/w/c/string/byte/isdigit) [`<swdigi>`](https://zh.cppreference.com/w/c/string/wide/iswdigit) | ​	[`<sxdigi>`](https://zh.cppreference.com/w/c/string/byte/isxdigit) [`<swxdigi>`](https://zh.cppreference.com/w/c/string/wide/iswxdigit) |          |          |
| :------: | :-----------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | -------- | -------- |
|  十进制  |   十六进制    |                            八进制                            |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |          |          |
|   0–8    |  `\x0`–`\x8`  |                          `\0`–`\10`                          |                      控制码 (`NUL` 等)                       |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    9     |     `\x9`     |                            `\11`                             |                        制表符 (`\t`)                         |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  10–13   |  `\xA`–`\xD`  |                         `\12`–`\15`                          |               空白符 (`\n`, `\v`, `\f`, `\r`)                |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  14–31   | `\xE`–`\x1F`  |                         `\16`–`\37`                          |                            控制码                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    32    |    `\x20`     |                            `\40`                             |                             空格                             |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  33–47   | `\x21`–`\x2F` |                         `\41`–`\57`                          |                      `!"#$%&'()*+,-./`                       |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  48–57   | `\x30`–`\x39` |                         `\60`–`\71`                          |                         `0123456789`                         |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`≠0`** | **`≠0`** |
|  58–64   | `\x3A`–`\x40` |                         `\72`–`\100`                         |                          `:;<=>?@`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  65–70   | `\x41`–`\x46` |                        `\101`–`\106`                         |                           `ABCDEF`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`≠0`** |
|  71–90   | `\x47`–`\x5A` |                        `\107`–`\132`                         |                  `GHIJKLMNOP` `QRSTUVWXYZ`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`0`**  |
|  91–96   | `\x5B`–`\x60` |                        `\133`–`\140`                         |                           `[\]^_``                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  97–102  | `\x61`–`\x66` |                        `\141`–`\146`                         |                           `abcdef`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`≠0`** |
| 103–122  | `\x67`–`\x7A` |                        `\147`–`\172`                         |                  `ghijklmnop` `qrstuvwxyz`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`0`**  |
| 123–126  | `\x7B`–`\x7E` |                        `\173`–`\176`                         |                            `{|}~`                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|   127    |    `\x7F`     |                            `\177`                            |                        退格符 (`DEL`)                        |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |





### ispunct

原址：[https://zh.cppreference.com/w/c/string/byte/ispunct](https://zh.cppreference.com/w/c/string/byte/ispunct)

作用：检查字符是否是标点字符  (函数)

备注：
```c
// 在标头 <ctype.h> 定义
int ispunct( int ch );
```

​	检查给定的字符是否为当前 C 本地环境分类为标点字符。默认 C 本地环境分类字符 `!"#$%&'()*+,-./:;<=>?@[\]^_`{|}~` 为标点。

​	若 `ch` 的值不能表示为 `unsigned char` 且不等于 `[EOF](http://zh.cppreference.com/w/c/io)`，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |
|      |      |              |

**返回值**

​	若字符为标点字符则为非零值，否则为零。

**示例**

```c
#include <ctype.h>
#include <locale.h>
#include <stdio.h>
 
int main(void)
{
    unsigned char c = '\xd7'; // ISO-8859-1 的字符 ×（乘号）
    printf("在默认的 C 本地环境中，\\xd7 %s是标点符号\n",
           ispunct(c) ? "" : "不" );
    setlocale(LC_ALL, "en_GB.iso88591");
    printf("在 ISO-8859-1 本地环境中，\\xd7 %s是标点符号\n",
           ispunct(c) ? "" : "不" );
}
```

​	可能的输出：

```txt
在默认的 C 本地环境中，\xd7 不是标点符号
在 ISO-8859-1 本地环境中，\xd7 是标点符号
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.4.1.9 The ispunct function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.4.1.9 The ispunct function （第 146 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.4.1.9 The ispunct function （第 202 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.4.1.9 The ispunct function （第 183 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.3.1.8 The ispunct function

**参阅**

| [iswpunct (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswpunct) | 检查宽字符是否为标点字符 (函数) |
| ------------------------------------------------------------ | ------------------------------- |
| **ispunct** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/ispunct)** |                                 |

| ASCII 值 |     字符      | ​	[`<scntr>`](https://zh.cppreference.com/w/c/string/byte/iscntrl) [`<swcntr>`](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | ​	[`<sprin>`](https://zh.cppreference.com/w/c/string/byte/isprint) [`<swprin>`](https://zh.cppreference.com/w/c/string/wide/iswprint) | ​	[`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) [`<swspac>`](https://zh.cppreference.com/w/c/string/wide/iswspace) | ​	[`<sblan>`](https://zh.cppreference.com/w/c/string/byte/isblank) [`<swblan>`](https://zh.cppreference.com/w/c/string/wide/iswblank) | ​	[`<sgrap>`](https://zh.cppreference.com/w/c/string/byte/isgraph) [`<swgrap>`](https://zh.cppreference.com/w/c/string/wide/iswgraph) | ​	**`ispunct`** [`<swpunc>`](https://zh.cppreference.com/w/c/string/wide/iswpunct) | ​	[`<salnu>`](https://zh.cppreference.com/w/c/string/byte/isalnum) [`<swalnu>`](https://zh.cppreference.com/w/c/string/wide/iswalnum) | ​	[`<salph>`](https://zh.cppreference.com/w/c/string/byte/isalpha) [`<swalph>`](https://zh.cppreference.com/w/c/string/wide/iswalpha) | ​	[`<suppe>`](https://zh.cppreference.com/w/c/string/byte/isupper) [`<swuppe>`](https://zh.cppreference.com/w/c/string/wide/iswupper) | ​	[`<slowe>`](https://zh.cppreference.com/w/c/string/byte/islower) [`<swlowe>`](https://zh.cppreference.com/w/c/string/wide/iswlower) | ​	[`<sdigi>`](https://zh.cppreference.com/w/c/string/byte/isdigit) [`<swdigi>`](https://zh.cppreference.com/w/c/string/wide/iswdigit) | ​	[`<sxdigi>`](https://zh.cppreference.com/w/c/string/byte/isxdigit) [`<swxdigi>`](https://zh.cppreference.com/w/c/string/wide/iswxdigit) |          |          |
| :------: | :-----------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | -------- | -------- |
|  十进制  |   十六进制    |                            八进制                            |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |          |          |
|   0–8    |  `\x0`–`\x8`  |                          `\0`–`\10`                          |                      控制码 (`NUL` 等)                       |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    9     |     `\x9`     |                            `\11`                             |                        制表符 (`\t`)                         |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  10–13   |  `\xA`–`\xD`  |                         `\12`–`\15`                          |               空白符 (`\n`, `\v`, `\f`, `\r`)                |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  14–31   | `\xE`–`\x1F`  |                         `\16`–`\37`                          |                            控制码                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    32    |    `\x20`     |                            `\40`                             |                             空格                             |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  33–47   | `\x21`–`\x2F` |                         `\41`–`\57`                          |                      `!"#$%&'()*+,-./`                       |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  48–57   | `\x30`–`\x39` |                         `\60`–`\71`                          |                         `0123456789`                         |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`≠0`** | **`≠0`** |
|  58–64   | `\x3A`–`\x40` |                         `\72`–`\100`                         |                          `:;<=>?@`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  65–70   | `\x41`–`\x46` |                        `\101`–`\106`                         |                           `ABCDEF`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`≠0`** |
|  71–90   | `\x47`–`\x5A` |                        `\107`–`\132`                         |                  `GHIJKLMNOP` `QRSTUVWXYZ`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`0`**  |
|  91–96   | `\x5B`–`\x60` |                        `\133`–`\140`                         |                           `[\]^_``                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  97–102  | `\x61`–`\x66` |                        `\141`–`\146`                         |                           `abcdef`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`≠0`** |
| 103–122  | `\x67`–`\x7A` |                        `\147`–`\172`                         |                  `ghijklmnop` `qrstuvwxyz`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`0`**  |
| 123–126  | `\x7B`–`\x7E` |                        `\173`–`\176`                         |                            `{|}~`                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|   127    |    `\x7F`     |                            `\177`                            |                        退格符 (`DEL`)                        |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |





### isspace

原址：[https://zh.cppreference.com/w/c/string/byte/isspace](https://zh.cppreference.com/w/c/string/byte/isspace)

作用：检查字符是否是空白字符  (函数)

备注：
```c
// 在标头 <ctype.h> 定义
int isspace( int ch );
```

​	检查给定的字符是否为

- 标准空白字符：

  - 空格（`0x20`），`' '`、
  - 换页（`0x0c`），``'\f'``、
  - 换行（`0x0a`），``'\n'``、
  - 回车（`0x0d`），``'\r'``、
  - 水平制表符（`0x09`），``'\t'``、
  - 垂直制表符（`0x0b`），``'\v'``，

- 或者本地环境特定的空白字符。

​	若 `ch` 的值不能表示为 `unsigned char` 且不等于 `[EOF](http://zh.cppreference.com/w/c/io)`，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |
|      |      |              |

**返回值**

​	若字符为空白符则为非零值，否则为零。

**示例**

```c
#include <ctype.h>
#include <limits.h>
#include <stdio.h>
 
int main(void)
{
    for (int ndx = 0; ndx <= UCHAR_MAX; ++ndx)
        if (isspace(ndx))
            printf("0x%02x ", ndx);
}
```

​	输出：

```txt
0x09 0x0a 0x0b 0x0c 0x0d 0x20
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.4.1.10 The isspace function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.4.1.10 The isspace function （第 147 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.4.1.10 The isspace function （第 202-203 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.4.1.10 The isspace function （第 183-184 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.3.1.9 The isspace function

**参阅**

| [iswspace (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswspace) | 检查宽字符是否为空白符 (函数) |
| ------------------------------------------------------------ | ----------------------------- |
| **isspace** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/isspace)** |                               |

| ASCII 值 |     字符      | ​	[`<scntr>`](https://zh.cppreference.com/w/c/string/byte/iscntrl) [`<swcntr>`](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | ​	[`<sprin>`](https://zh.cppreference.com/w/c/string/byte/isprint) [`<swprin>`](https://zh.cppreference.com/w/c/string/wide/iswprint) | ​	**`isspace`** [`<swspac>`](https://zh.cppreference.com/w/c/string/wide/iswspace) | ​	[`<sblan>`](https://zh.cppreference.com/w/c/string/byte/isblank) [`<swblan>`](https://zh.cppreference.com/w/c/string/wide/iswblank) | ​	[`<sgrap>`](https://zh.cppreference.com/w/c/string/byte/isgraph) [`<swgrap>`](https://zh.cppreference.com/w/c/string/wide/iswgraph) | ​	[`<spunc>`](https://zh.cppreference.com/w/c/string/byte/ispunct) [`<swpunc>`](https://zh.cppreference.com/w/c/string/wide/iswpunct) | ​	[`<salnu>`](https://zh.cppreference.com/w/c/string/byte/isalnum) [`<swalnu>`](https://zh.cppreference.com/w/c/string/wide/iswalnum) | ​	[`<salph>`](https://zh.cppreference.com/w/c/string/byte/isalpha) [`<swalph>`](https://zh.cppreference.com/w/c/string/wide/iswalpha) | ​	[`<suppe>`](https://zh.cppreference.com/w/c/string/byte/isupper) [`<swuppe>`](https://zh.cppreference.com/w/c/string/wide/iswupper) | ​	[`<slowe>`](https://zh.cppreference.com/w/c/string/byte/islower) [`<swlowe>`](https://zh.cppreference.com/w/c/string/wide/iswlower) | ​	[`<sdigi>`](https://zh.cppreference.com/w/c/string/byte/isdigit) [`<swdigi>`](https://zh.cppreference.com/w/c/string/wide/iswdigit) | ​	[`<sxdigi>`](https://zh.cppreference.com/w/c/string/byte/isxdigit) [`<swxdigi>`](https://zh.cppreference.com/w/c/string/wide/iswxdigit) |          |          |
| :------: | :-----------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | -------- | -------- |
|  十进制  |   十六进制    |                            八进制                            |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |          |          |
|   0–8    |  `\x0`–`\x8`  |                          `\0`–`\10`                          |                      控制码 (`NUL` 等)                       |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    9     |     `\x9`     |                            `\11`                             |                        制表符 (`\t`)                         |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  10–13   |  `\xA`–`\xD`  |                         `\12`–`\15`                          |               空白符 (`\n`, `\v`, `\f`, `\r`)                |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  14–31   | `\xE`–`\x1F`  |                         `\16`–`\37`                          |                            控制码                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    32    |    `\x20`     |                            `\40`                             |                             空格                             |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  33–47   | `\x21`–`\x2F` |                         `\41`–`\57`                          |                      `!"#$%&'()*+,-./`                       |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  48–57   | `\x30`–`\x39` |                         `\60`–`\71`                          |                         `0123456789`                         |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`≠0`** | **`≠0`** |
|  58–64   | `\x3A`–`\x40` |                         `\72`–`\100`                         |                          `:;<=>?@`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  65–70   | `\x41`–`\x46` |                        `\101`–`\106`                         |                           `ABCDEF`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`≠0`** |
|  71–90   | `\x47`–`\x5A` |                        `\107`–`\132`                         |                  `GHIJKLMNOP` `QRSTUVWXYZ`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`0`**  |
|  91–96   | `\x5B`–`\x60` |                        `\133`–`\140`                         |                           `[\]^_``                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  97–102  | `\x61`–`\x66` |                        `\141`–`\146`                         |                           `abcdef`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`≠0`** |
| 103–122  | `\x67`–`\x7A` |                        `\147`–`\172`                         |                  `ghijklmnop` `qrstuvwxyz`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`0`**  |
| 123–126  | `\x7B`–`\x7E` |                        `\173`–`\176`                         |                            `{|}~`                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|   127    |    `\x7F`     |                            `\177`                            |                        退格符 (`DEL`)                        |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |





### isupper

原址：[https://zh.cppreference.com/w/c/string/byte/isupper](https://zh.cppreference.com/w/c/string/byte/isupper)

作用：检查字符是否是大写字母  (函数)

备注：
```c
// 在标头 <ctype.h> 定义
int isupper( int ch );
```

​	根据当前 C 本地环境检查给定字符是否为大写字母。在默认 `"C"` 本地环境中，`isupper` 仅对大写拉丁字母（`ABCDEFGHIJKLMNOPQRSTUVWXYZ`）返回非零值。

​	若 `isupper`返回非零，则保证 [iscntrl](https://zh.cppreference.com/w/c/string/byte/iscntrl)、[isdigit](https://zh.cppreference.com/w/c/string/byte/isdigit)、[ispunct](https://zh.cppreference.com/w/c/string/byte/ispunct) 及 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 在同一 C 本地环境中对同一字符返回零。

​	若 `ch` 的值不能表示为 `unsigned char` 且不等于 `[EOF](http://zh.cppreference.com/w/c/io)`，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |
|      |      |              |

**返回值**

​	若字符为大写字母则为非零值，否则为零。

**示例**

```c
#include <ctype.h>
#include <locale.h>
#include <stdio.h>
 
int main(void)
{
    unsigned char c = '\xc6'; // ISO-8859-1的 字母 Æ 
    printf("在默认的 C 本地环境中，\\xc6 %s是大写字母\n",
           isupper(c) ? "" : "不" );
    setlocale(LC_ALL, "en_GB.iso88591");
    printf("在 ISO-8859-1 本地环境中，\\xc6 %s是大写字母\n",
           isupper(c) ? "" : "不" );
}
```

​	可能的输出：

```txt
在默认的 C 本地环境中，\xc6 不是大写字母
在 ISO-8859-1 本地环境中，\xc6 是大写字母
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.4.1.11 The isupper function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.4.1.11 The isupper function （第 147 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.4.1.11 The isupper function （第 203 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.4.1.11 The isupper function （第 184 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.3.1.10 The isupper function

**参阅**

| [iswupper (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswupper) | 检查宽字符是否为大写 (函数) |
| ------------------------------------------------------------ | --------------------------- |
| **isupper** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/isupper)** |                             |

| ASCII 值 |     字符      | ​	[`<scntr>`](https://zh.cppreference.com/w/c/string/byte/iscntrl) [`<swcntr>`](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | ​	[`<sprin>`](https://zh.cppreference.com/w/c/string/byte/isprint) [`<swprin>`](https://zh.cppreference.com/w/c/string/wide/iswprint) | ​	[`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) [`<swspac>`](https://zh.cppreference.com/w/c/string/wide/iswspace) | ​	[`<sblan>`](https://zh.cppreference.com/w/c/string/byte/isblank) [`<swblan>`](https://zh.cppreference.com/w/c/string/wide/iswblank) | ​	[`<sgrap>`](https://zh.cppreference.com/w/c/string/byte/isgraph) [`<swgrap>`](https://zh.cppreference.com/w/c/string/wide/iswgraph) | ​	[`<spunc>`](https://zh.cppreference.com/w/c/string/byte/ispunct) [`<swpunc>`](https://zh.cppreference.com/w/c/string/wide/iswpunct) | ​	[`<salnu>`](https://zh.cppreference.com/w/c/string/byte/isalnum) [`<swalnu>`](https://zh.cppreference.com/w/c/string/wide/iswalnum) | ​	[`<salph>`](https://zh.cppreference.com/w/c/string/byte/isalpha) [`<swalph>`](https://zh.cppreference.com/w/c/string/wide/iswalpha) | ​	**`isupper`** [`<swuppe>`](https://zh.cppreference.com/w/c/string/wide/iswupper) | ​	[`<slowe>`](https://zh.cppreference.com/w/c/string/byte/islower) [`<swlowe>`](https://zh.cppreference.com/w/c/string/wide/iswlower) | ​	[`<sdigi>`](https://zh.cppreference.com/w/c/string/byte/isdigit) [`<swdigi>`](https://zh.cppreference.com/w/c/string/wide/iswdigit) | ​	[`<sxdigi>`](https://zh.cppreference.com/w/c/string/byte/isxdigit) [`<swxdigi>`](https://zh.cppreference.com/w/c/string/wide/iswxdigit) |          |          |
| :------: | :-----------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | -------- | -------- |
|  十进制  |   十六进制    |                            八进制                            |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |          |          |
|   0–8    |  `\x0`–`\x8`  |                          `\0`–`\10`                          |                      控制码 (`NUL` 等)                       |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    9     |     `\x9`     |                            `\11`                             |                        制表符 (`\t`)                         |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  10–13   |  `\xA`–`\xD`  |                         `\12`–`\15`                          |               空白符 (`\n`, `\v`, `\f`, `\r`)                |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  14–31   | `\xE`–`\x1F`  |                         `\16`–`\37`                          |                            控制码                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    32    |    `\x20`     |                            `\40`                             |                             空格                             |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  33–47   | `\x21`–`\x2F` |                         `\41`–`\57`                          |                      `!"#$%&'()*+,-./`                       |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  48–57   | `\x30`–`\x39` |                         `\60`–`\71`                          |                         `0123456789`                         |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`≠0`** | **`≠0`** |
|  58–64   | `\x3A`–`\x40` |                         `\72`–`\100`                         |                          `:;<=>?@`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  65–70   | `\x41`–`\x46` |                        `\101`–`\106`                         |                           `ABCDEF`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`≠0`** |
|  71–90   | `\x47`–`\x5A` |                        `\107`–`\132`                         |                  `GHIJKLMNOP` `QRSTUVWXYZ`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`0`**  |
|  91–96   | `\x5B`–`\x60` |                        `\133`–`\140`                         |                           `[\]^_``                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  97–102  | `\x61`–`\x66` |                        `\141`–`\146`                         |                           `abcdef`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`≠0`** |
| 103–122  | `\x67`–`\x7A` |                        `\147`–`\172`                         |                  `ghijklmnop` `qrstuvwxyz`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`0`**  |
| 123–126  | `\x7B`–`\x7E` |                        `\173`–`\176`                         |                            `{|}~`                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|   127    |    `\x7F`     |                            `\177`                            |                        退格符 (`DEL`)                        |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |





### isxdigit

原址：[https://zh.cppreference.com/w/c/string/byte/isxdigit](https://zh.cppreference.com/w/c/string/byte/isxdigit)

作用：检查字符是否是十六进制字符  (函数)

备注：
```c
// 在标头 <ctype.h> 定义
int isxdigit( int ch );
```

​	检查给定的字符是否为十六进制数字字符（`0123456789``abcdefABCDEF`）或被分类为十六进制字符。

​	若 `ch` 的值不能表示为 `unsigned char` 且不等于 `[EOF](http://zh.cppreference.com/w/c/io)`，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |
|      |      |              |

**返回值**

​	若字符为十六进制数字数字则为非零值，否则为零。

**注解**

​	`isdigit` 和 `isxdigit` 是仅有的不受当前安装的 C 本地环境影响的标准窄字符分类函数。尽管某些实现（例如 Microsoft 在 1252 代码页）可能分类另外的单字节字符为数字。

**示例**

```c
#include <ctype.h>
#include <limits.h>
#include <stdio.h>
 
int main(void)
{
    for (int ndx = 0; UCHAR_MAX >= ndx; ++ndx)
        if (isxdigit(ndx))
            printf("%c", ndx);
    printf("\n");
}
```

​	输出：

```txt
0123456789ABCDEFabcdef
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.4.1.12 The isxdigit function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.4.1.12 The isxdigit function （第 147 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.4.1.12 The isxdigit function （第 203 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.4.1.12 The isxdigit function （第 184 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.3.1.11 The isxdigit function

**参阅**

| [iswxdigit (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswxdigit) | 检查宽字符是否为十六进制字符 (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| **isxdigit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/isxdigit)** |                                     |

| ASCII 值 |     字符      | ​	[`<scntr>`](https://zh.cppreference.com/w/c/string/byte/iscntrl) [`<swcntr>`](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | ​	[`<sprin>`](https://zh.cppreference.com/w/c/string/byte/isprint) [`<swprin>`](https://zh.cppreference.com/w/c/string/wide/iswprint) | ​	[`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) [`<swspac>`](https://zh.cppreference.com/w/c/string/wide/iswspace) | ​	[`<sblan>`](https://zh.cppreference.com/w/c/string/byte/isblank) [`<swblan>`](https://zh.cppreference.com/w/c/string/wide/iswblank) | ​	[`<sgrap>`](https://zh.cppreference.com/w/c/string/byte/isgraph) [`<swgrap>`](https://zh.cppreference.com/w/c/string/wide/iswgraph) | ​	[`<spunc>`](https://zh.cppreference.com/w/c/string/byte/ispunct) [`<swpunc>`](https://zh.cppreference.com/w/c/string/wide/iswpunct) | ​	[`<salnu>`](https://zh.cppreference.com/w/c/string/byte/isalnum) [`<swalnu>`](https://zh.cppreference.com/w/c/string/wide/iswalnum) | ​	[`<salph>`](https://zh.cppreference.com/w/c/string/byte/isalpha) [`<swalph>`](https://zh.cppreference.com/w/c/string/wide/iswalpha) | ​	[`<suppe>`](https://zh.cppreference.com/w/c/string/byte/isupper) [`<swuppe>`](https://zh.cppreference.com/w/c/string/wide/iswupper) | ​	[`<slowe>`](https://zh.cppreference.com/w/c/string/byte/islower) [`<swlowe>`](https://zh.cppreference.com/w/c/string/wide/iswlower) | ​	[`<sdigi>`](https://zh.cppreference.com/w/c/string/byte/isdigit) [`<swdigi>`](https://zh.cppreference.com/w/c/string/wide/iswdigit) | ​	**`isxdigit`** [`<swxdigi>`](https://zh.cppreference.com/w/c/string/wide/iswxdigit) |          |          |
| :------: | :-----------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | -------- | -------- |
|  十进制  |   十六进制    |                            八进制                            |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |          |          |
|   0–8    |  `\x0`–`\x8`  |                          `\0`–`\10`                          |                      控制码 (`NUL` 等)                       |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    9     |     `\x9`     |                            `\11`                             |                        制表符 (`\t`)                         |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  10–13   |  `\xA`–`\xD`  |                         `\12`–`\15`                          |               空白符 (`\n`, `\v`, `\f`, `\r`)                |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  14–31   | `\xE`–`\x1F`  |                         `\16`–`\37`                          |                            控制码                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|    32    |    `\x20`     |                            `\40`                             |                             空格                             |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  33–47   | `\x21`–`\x2F` |                         `\41`–`\57`                          |                      `!"#$%&'()*+,-./`                       |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  48–57   | `\x30`–`\x39` |                         `\60`–`\71`                          |                         `0123456789`                         |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`≠0`** | **`≠0`** |
|  58–64   | `\x3A`–`\x40` |                         `\72`–`\100`                         |                          `:;<=>?@`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  65–70   | `\x41`–`\x46` |                        `\101`–`\106`                         |                           `ABCDEF`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`≠0`** |
|  71–90   | `\x47`–`\x5A` |                        `\107`–`\132`                         |                  `GHIJKLMNOP` `QRSTUVWXYZ`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            | **`0`**  | **`0`**  |
|  91–96   | `\x5B`–`\x60` |                        `\133`–`\140`                         |                           `[\]^_``                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|  97–102  | `\x61`–`\x66` |                        `\141`–`\146`                         |                           `abcdef`                           |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`≠0`** |
| 103–122  | `\x67`–`\x7A` |                        `\147`–`\172`                         |                  `ghijklmnop` `qrstuvwxyz`                   |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`≠0`**                           | **`0`**  | **`0`**  |
| 123–126  | `\x7B`–`\x7E` |                        `\173`–`\176`                         |                            `{|}~`                            |                           **`0`**                            |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`≠0`**                           |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |
|   127    |    `\x7F`     |                            `\177`                            |                        退格符 (`DEL`)                        |                           **`≠0`**                           |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            |                           **`0`**                            | **`0`**  | **`0`**  |





### tolower

原址：[https://zh.cppreference.com/w/c/string/byte/tolower](https://zh.cppreference.com/w/c/string/byte/tolower)

作用：将字符转换成小写  (函数)

备注：
```c
// 在标头 <ctype.h> 定义
int tolower( int ch );
```

​	按照当前安装的 C 本地环境所定义的规则，转换给定字符为小写。

​	默认 `"C"` 本地环境中，以相应的小写字母 `abcdefghijklmnopqrstuvwxyz` 替换大写字母 `ABCDEFGHIJKLMNOPQRSTUVWXYZ`。

**参数**

| ch   | -    | 要转换的字符。若 `ch` 的值不能表示为 `unsigned char` 且不等于 `[EOF](http://zh.cppreference.com/w/c/io)`，则行为未定义。 |
| ---- | ---- | ------------------------------------------------------------ |
|      |      |                                                              |

**返回值**

​	`ch` 的小写版本，或若当前 C 本地环境中无小写版本，则返回不修改的 `ch`。

**示例**

```c
#include <ctype.h>
#include <limits.h>
#include <locale.h>
#include <stdio.h>
 
int main(void)
{
    // 在默认本地环境中
    for (unsigned char u = 0; u < UCHAR_MAX; u++)
    {
        unsigned char l = tolower(u);
        if (l != u)
            printf("%c%c ", u, l);
    }
    printf("\n\n");
 
    unsigned char c = '\xb4'; // ISO-8859-15 的字符 Ž
                              // 但在 ISO-8859-1为 ´（锐音符）
    setlocale(LC_ALL, "en_US.iso88591");
    printf("在 iso8859-1 中，tolower('0x%x') 得到 0x%x\n", c, tolower(c));
    setlocale(LC_ALL, "en_US.iso885915");
    printf("在 iso8859-15 中，tolower('0x%x') 得到 0x%x\n", c, tolower(c));
}
```

​	可能的输出：

```txt
Aa Bb Cc Dd Ee Ff Gg Hh Ii Jj Kk Ll Mm Nn Oo Pp Qq Rr Ss Tt Uu Vv Ww Xx Yy Zz
 
在 iso8859-1 中，tolower('0xb4') 得到 0xb4
在 iso8859-15 中，tolower('0xb4') 得到 0xb8
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.4.2.1 The tolower function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.4.2.1 The tolower function （第 147 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.4.2.1 The tolower function （第 203 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.4.2.1 The tolower function （第 184 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.3.2.1 The tolower function

**参阅**

| [toupper<br />](https://zh.cppreference.com/w/c/string/byte/toupper) | 将字符转换成大写 (函数) |
| ------------------------------------------------------------ | ----------------------- |
| [towlower (C95)<br />](https://zh.cppreference.com/w/c/string/wide/towlower) | 转换宽字符为小写 (函数) |
| **tolower** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/tolower)** |                         |





### toupper

原址：[https://zh.cppreference.com/w/c/string/byte/toupper](https://zh.cppreference.com/w/c/string/byte/toupper)

作用：将字符转换成大写  (函数)

备注：
```c
// 在标头 <ctype.h> 定义
int toupper( int ch );
```

​	按照当前安装的 C 本地环境所定义的字符转换规则，转换给定字符为大写。

​	默认 `"C"` 本地环境中，以相应的大写字母 `ABCDEFGHIJKLMNOPQRSTUVWXYZ` 替换下列小写字母 `abcdefghijklmnopqrstuvwxyz`。

**参数**

| ch   | -    | 要转化的字符。若 `ch` 的值不能表示为 `unsigned char` 且不等于 `[EOF](http://zh.cppreference.com/w/c/io)`，则行为未定义。 |
| ---- | ---- | ------------------------------------------------------------ |
|      |      |                                                              |

**返回值**

​	`ch` 的大写版本，或若无大写版本列于当前 C 本地环境，则为不修改的 `ch`。

**示例**

```c
#include <ctype.h>
#include <limits.h>
#include <locale.h>
#include <stdio.h>
 
int main(void)
{
    // 在默认本地环境：
    for (unsigned char l = 0, u; l != UCHAR_MAX; ++l)
        if ((u = toupper(l)) != l)
            printf("%c%c ", l, u);
    printf("\n\n");
 
    unsigned char c = '\xb8'; // ISO-8859-15 中的字母 ž
                              // 但在 ISO-8859-1 中为 ¸（下加符）
    setlocale(LC_ALL, "en_US.iso88591");
    printf("iso8859-1 下，toupper('0x%x') 结果为 0x%x\n", c, toupper(c));
    setlocale(LC_ALL, "en_US.iso885915");
    printf("iso8859-15 下，toupper('0x%x') 结果为 0x%x\n", c, toupper(c));
}
```

​	可能的输出：

```txt
aA bB cC dD eE fF gG hH iI jJ kK lL mM nN oO pP qQ rR sS tT uU vV wW xX yY zZ 
 
iso8859-1 下，toupper('0xb8') 结果为 0xb8
iso8859-15 下，toupper('0xb8') 结果为 0xb4
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.4.2.2 The toupper function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.4.2.2 The toupper function （第 147-148 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.4.2.2 The toupper function （第 204 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.4.2.2 The toupper function （第 185 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.3.2.2 The toupper function

**参阅**

| [tolower<br />](https://zh.cppreference.com/w/c/string/byte/tolower) | 将字符转换成小写 (函数) |
| ------------------------------------------------------------ | ----------------------- |
| [towupper (C95)<br />](https://zh.cppreference.com/w/c/string/wide/towupper) | 转换宽字符为大写 (函数) |
| **toupper** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/toupper)** |                         |






