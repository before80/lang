+++
title = "<ctype.h>"
date = 2025-04-15T09:12:20+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：

## 类型





## 宏





## 函数



### isalnum

原址：[https://zh.cppreference.com/w/c/string/byte/isalnum](https://zh.cppreference.com/w/c/string/byte/isalnum)

```c
int isalnum( int ch );
```

​	检查给定的字符是否为当前 C 本地环境所分类的字母数字字符。在默认本地环境中，下列字符为字母数字：

- 数字（`0123456789`）
- 大写字母（`ABCDEFGHIJKLMNOPQRSTUVWXYZ`）
- 小写字母（`abcdefghijklmnopqrstuvwxyz`）

​	若 `ch` 的值不能表示为 unsigned char 且不等于 [EOF](http://zh.cppreference.com/w/c/io)，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |

**返回值**

​	若字符为字母数字字符，则为非零，否则为 0。

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

可能的输出：

```txt
isalnum('\xdf') 在默认 C 本地环境中返回 0
isalnum('\xdf') in ISO-8859-1 locale returned 1
```

### isalpha

原址：[https://zh.cppreference.com/w/c/string/byte/isalpha](https://zh.cppreference.com/w/c/string/byte/isalpha)

```c
int isalpha( int ch );
```

​	检查给定字符是否为字母字符，即是大写字母（`ABCDEFGHIJKLMNOPQRSTUVWXYZ`）或小写字母（`abcdefghijklmnopqrstuvwxyz`）。

​	在异于 `"C"` 的本地环境中，字母字符是 [isupper()](https://zh.cppreference.com/w/c/string/byte/isupper) 或 [islower()](https://zh.cppreference.com/w/c/string/byte/islower) 对其返回 `true` 的字符，或任何其他被本地环境认为是字母的字符。任何情况下，[iscntrl()](https://zh.cppreference.com/w/c/string/byte/iscntrl)、[isdigit()](https://zh.cppreference.com/w/c/string/byte/isdigit)、[ispunct()](https://zh.cppreference.com/w/c/string/byte/ispunct) 及 [isspace()](https://zh.cppreference.com/w/c/string/byte/isspace) 将对此字符返回 `false`。

​	若 `ch` 的值不能表示为 `unsigned char` 且不等于 [EOF](http://zh.cppreference.com/w/c/io)，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |

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

可能的输出：

```txt
isalpha('\xdf') 在默认 C 本地环境中返回 0
isalpha('\xdf') 在 ISO-8859-1 本地环境中返回 1
```

### isblank <- 99+

原址：[https://zh.cppreference.com/w/c/string/byte/isblank](https://zh.cppreference.com/w/c/string/byte/isblank)

```c
int isblank( int ch ); // (C99 起)
```

​	检查给定的字符在当前的 C 本地环境中是否为空白字符。在默认 C 本地环境中，只有空格（`0x20`）与水平制表符（`0x09`）被分类为空白字符。

​	若 ch 的值不能表示为 unsigned char 且不等于 [EOF](http://zh.cppreference.com/w/c/io)，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |

**返回值**

若字符为空白字符则为非零值，否则为零。

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

输出：

```txt
0x09
0x20
```

### iscntrl

原址：[https://zh.cppreference.com/w/c/string/byte/iscntrl](https://zh.cppreference.com/w/c/string/byte/iscntrl)

```c
int iscntrl( int ch );
```

​	检查给定字符是否为控制字符，即编码 `[0x00, 0x1F]` 及 `0x7F`。

​	若 `ch` 的值不能表示为 unsigned char 且不等于 [EOF](http://zh.cppreference.com/w/c/io)，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |

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

### isdigit

原址：[https://zh.cppreference.com/w/c/string/byte/isdigit](https://zh.cppreference.com/w/c/string/byte/isdigit)

```c
int isdigit( int ch );
```

​	检查给定的字符是否为数字字符（`0123456789`）。

​	若 ch 的值不能表示为 unsigned char 且不等于 [EOF](http://zh.cppreference.com/w/c/io)，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |

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

### isgraph

原址：[https://zh.cppreference.com/w/c/string/byte/isgraph](https://zh.cppreference.com/w/c/string/byte/isgraph)

```c
int isgraph( int ch );
```

​	检查给定的字符是否拥有图形表示，即它是数字（`0123456789`）、大写字母（`ABCDEFGHIJKLMNOPQRSTUVWXYZ`）、小写字母（`abcdefghijklmnopqrstuvwxyz`）或标点字符（`!"#$%&'()*+,-./:;<=>?@[\]^_\`{|}~`），或任何指定于当前 C 本地环境的图形字符之一。

​	若 `ch` 的值不能表示为 unsigned char 且不等于 [EOF](http://zh.cppreference.com/w/c/io)，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |

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

### islower

原址：

```c

```





### isprint

原址：[https://zh.cppreference.com/w/c/string/byte/isprint](https://zh.cppreference.com/w/c/string/byte/isprint)

```c
int isprint( int ch );
```

​	检查给定的字符能否被打印，即为数字（`0123456789`）、大写字母（`ABCDEFGHIJKLMNOPQRSTUVWXYZ`）、小写字母（`abcdefghijklmnopqrstuvwxyz`）、标点字符（`!"#$%&'()*+,-./:;<=>?@[\]^_`{|}~`）或空格之一，或任何当前 C 本地环境分类为可打印的字符。

​	若 ch 的值不能表示为 unsigned char 且不等于 [EOF](http://zh.cppreference.com/w/c/io)，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |

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

### ispunct

原址：[https://zh.cppreference.com/w/c/string/byte/ispunct](https://zh.cppreference.com/w/c/string/byte/ispunct)

```c
int ispunct( int ch );
```

​	检查给定的字符是否为当前 C 本地环境分类为标点字符。默认 C 本地环境分类字符 `!"#$%&'()*+,-./:;<=>?@[\]^_\`{|}~` 为标点。

​	若 ch 的值不能表示为 unsigned char 且不等于 [EOF](http://zh.cppreference.com/w/c/io)，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |

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



### isspace

原址：

```c

```





### isupper

原址：

```c

```





### isxdigit

原址：[https://zh.cppreference.com/w/c/string/byte/isxdigit](https://zh.cppreference.com/w/c/string/byte/isxdigit)

```c
int isxdigit( int ch );
```

​	检查给定的字符是否为十六进制数字字符（`0123456789abcdefABCDEF`）或被分类为十六进制字符。

​	若 `ch` 的值不能表示为 unsigned char 且不等于 [EOF](http://zh.cppreference.com/w/c/io)，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |

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

### islower

原址：[https://zh.cppreference.com/w/c/string/byte/islower](https://zh.cppreference.com/w/c/string/byte/islower)

```c
int islower( int ch );
```

​	检查给定字符是否按照当前 C 本地环境分类为小写字符。默认 `"C"` 本地环境中，`islower` 仅对小写字母（`abcdefghijklmnopqrstuvwxyz`）返回非零值。

​	若 `islower` 返回非零值，则保证同一 C 本地环境中 [iscntrl](http://zh.cppreference.com/w/c/string/byte/iscntrl)、[isdigit](http://zh.cppreference.com/w/c/string/byte/isdigit)、[ispunct](http://zh.cppreference.com/w/c/string/byte/ispunct) 和 [isspace](http://zh.cppreference.com/w/c/string/byte/isspace) 对同一字符返回零。

​	若 `ch` 不可表示为 `unsigned char` 且不等于 [EOF](http://zh.cppreference.com/w/c/io)，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |

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

可能的输出：

```txt
在默认的 C 本地环境中，\xe5 不是小写字母
在 ISO-8859-1 本地环境中，\xe5 是小写字母
```

### isspace

原址：[https://zh.cppreference.com/w/c/string/byte/isspace](https://zh.cppreference.com/w/c/string/byte/isspace)

```c
int isspace( int ch );
```

​	检查给定的字符是否为

- 标准空白字符：
  - 空格（0x20），`' '`、
  - 换页（0x0c），`'\f'`、
  - 换行（0x0a），`'\n'`、
  - 回车（0x0d），`'\r'`、
  - 水平制表符（0x09），`'\t'`、
  - 垂直制表符（0x0b），`'\v'`，


- 或者本地环境特定的空白字符。

​	若 `ch` 的值不能表示为 unsigned char 且不等于 [EOF](http://zh.cppreference.com/w/c/io)，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |

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

### isupper

原址：[https://zh.cppreference.com/w/c/string/byte/isupper](https://zh.cppreference.com/w/c/string/byte/isupper)

```c
int isupper( int ch );
```

​	根据当前 C 本地环境检查给定字符是否为大写字母。在默认 `"C"` 本地环境中，`isupper` 仅对大写拉丁字母（`ABCDEFGHIJKLMNOPQRSTUVWXYZ`）返回非零值。

​	若 `isupper`返回非零，则保证 [iscntrl](https://zh.cppreference.com/w/c/string/byte/iscntrl)、[isdigit](https://zh.cppreference.com/w/c/string/byte/isdigit)、[ispunct](https://zh.cppreference.com/w/c/string/byte/ispunct) 及 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 在同一 C 本地环境中对同一字符返回零。

​	若 ch 的值不能表示为 unsigned char 且不等于 [EOF](http://zh.cppreference.com/w/c/io)，则行为未定义。

**参数**

| ch   | -    | 要分类的字符 |
| ---- | ---- | ------------ |

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
### tolower

原址：[https://zh.cppreference.com/w/c/string/byte/tolower](https://zh.cppreference.com/w/c/string/byte/tolower)

```c
int tolower( int ch );
```

​	按照当前安装的 C 本地环境所定义的规则，转换给定字符为小写。

​	默认 `"C"` 本地环境中，以相应的小写字母 `abcdefghijklmnopqrstuvwxyz` 替换大写字母 `ABCDEFGHIJKLMNOPQRSTUVWXYZ`。

**参数**

| ch   | -    | 要转换的字符。若 ch 的值不能表示为 unsigned char 且不等于 [EOF](http://zh.cppreference.com/w/c/io)，则行为未定义。 |
| ---- | ---- | ------------------------------------------------------------ |

**返回值**

​	ch 的小写版本，或若当前 C 本地环境中无小写版本，则返回不修改的 ch。

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
### toupper

原址：[https://zh.cppreference.com/w/c/string/byte/toupper](https://zh.cppreference.com/w/c/string/byte/toupper)

```c
int toupper( int ch );
```

​	按照当前安装的 C 本地环境所定义的字符转换规则，转换给定字符为大写。

​	默认 "C" 本地环境中，以相应的大写字母 `ABCDEFGHIJKLMNOPQRSTUVWXYZ` 替换下列小写字母 `abcdefghijklmnopqrstuvwxyz`。

**参数**

| ch   | -    | 要转化的字符。若 `ch` 的值不能表示为 unsigned char 且不等于 [EOF](http://zh.cppreference.com/w/c/io)，则行为未定义。 |
| ---- | ---- | ------------------------------------------------------------ |

**返回值**

​	ch 的大写版本，或若无大写版本列于当前 C 本地环境，则为不修改的 ch。

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



