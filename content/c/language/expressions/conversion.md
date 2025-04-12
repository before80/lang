+++
title = "隐式转换"
date = 2025-04-12T16:57:45+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/conversion](https://zh.cppreference.com/w/c/language/conversion)

​	当表达式用在期待相异类型的值语境中时，可以发生*转换*：

```c
int n = 1L; // 表达式 1L 类型为 long，期待 int
n = 2.1; // 表达式 2.1 类型为 double，期待 int
char* p = malloc(10); // 表达式 malloc(10) 类型为 void*，期待 char*
```

​	下列情况下将发生转换：

## 如同赋值的转换

- 在[赋值](https://zh.cppreference.com/w/c/language/operator_assignment)运算符中，右操作数的值被转换成左操作数的无限定类型。
- 在[标量初始化](https://zh.cppreference.com/w/c/language/scalar_initialization)中，初始化式表达式的值被转换成待初始化对象的无限定类型。
- 在对有原型函数的[函数调用表达式](https://zh.cppreference.com/w/c/language/operator_other)中，每个实参表达式的值被转换成对应形参的声明类型。
- 在 [return 语句](https://zh.cppreference.com/w/c/language/return)中，return 的操作数的值被转换成具有该函数返回类型的对象。

> 注意
>
> ​	在实际赋值中，除转换外，还会移除浮点数类型的额外范围和精度，并禁止重叠；这些特性对于如同赋值的转换不适用。

## 默认实参提升

​	在[函数调用表达式](https://zh.cppreference.com/w/c/language/operator_other#.E5.87.BD.E6.95.B0.E8.B0.83.E7.94.A8)中，当调用下列函数时

1) [无原型函数](https://zh.cppreference.com/w/c/language/function_declaration) (C23 前)，
2) [变参数函数](https://zh.cppreference.com/w/c/language/variadic)，其中实参表达式是匹配省略号参数的尾部实参之一。

​	每个整数类型的实参都会经历[整数提升](https://zh.cppreference.com/w/c/language/conversion#.E6.95.B4.E6.95.B0.E6.8F.90.E5.8D.87)，而每个 float 类型的实参都隐式转换为 double 类型

```c
int add_nums(int count, ...);
int sum = add_nums(2, 'c', true); // add_nums 将以三个 int 调用：(2, 99, 1)
```

> 注意  (C99 起)
>
> ​	float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex) 和 float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary) 在此语境中不会提升到 double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex) 和 double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)。

## 一般算术转换

​	下列算术运算符的实参会经历隐式转换，以获得*公共实数类型* ﻿，这是执行计算所用的类型：

- [二元算术](https://zh.cppreference.com/w/c/language/operator_arithmetic) `*`, `/`, `%`, `+`, `-`，
- [关系运算符](https://zh.cppreference.com/w/c/language/operator_comparison) `<`, `>`, `<=`, `>=`, `==`, `!=`，
- [二元逐位算术](https://zh.cppreference.com/w/c/language/operator_arithmetic) `&`, `^`, `|`，
- [条件运算符](https://zh.cppreference.com/w/c/language/operator_other) `?:`。



1. 若一个操作数具有十进制浮点数类型，则另一个操作数不能为标准浮点数、复数或虚数类型。 (C23 起)
   - 否则，如果任一操作数的类型为 `_Decimal128`，则另一操作数转换为 `_Decimal128`。
   - 否则，如果任一操作数的类型为 `_Decimal64`，则另一操作数转换为 `_Decimal64`。
   - 否则，如果任一操作数的类型为 `_Decimal32`，则另一操作数转换为 `_Decimal32`。

2) 否则，若一个操作数是 long double、long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex) 或 long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)，则会按下列方式隐式转换另一操作数：

   - 整数或实浮点数类型转换成 `long double`
   - 复数类型转换成 long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)
   - 虚数类型转换成 long double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)

3) 否则，若一个操作数是 double、double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex) 或 double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)，则会按下列方式隐式转换另一操作数：

   - 整数或实浮点数类型转换成 double
   - 复数类型转换成 double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)
   - 虚数类型转换成 double [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)

4) 否则，若一个操作数是 float、float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex) 或 float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)，则会按下列方式隐式转换另一操作数：

   - 整数类型转换成 float（唯一可能的实数类型是 float，它保持原状）
   - 复数类型保持 float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex)
   - 虚数类型保持 float [imaginary](http://zh.cppreference.com/w/c/numeric/complex/imaginary)

5) 否则两个操作数均为整数。两个操作数都会经历[整数提升](https://zh.cppreference.com/w/c/language/conversion#.E6.95.B4.E6.95.B0.E6.8F.90.E5.8D.87)；经过整数提升后，适用于以下情况之一：

   - 若两类型相同，则该类型即为公共类型

   - 否则，两类型不同：

     - 若两类型有相同的符号性（均为有符号或均为无符号），则拥有较低*转换等级* ﻿[[1\]](https://zh.cppreference.com/w/c/language/conversion#cite_note-1)者会隐式转换[[2\]](https://zh.cppreference.com/w/c/language/conversion#cite_note-2)为另一类型
     - 否则，两者符号性不同：
       - 若无符号类型的*转换等级*大于或等于有符号类型的等级，则有符号类型操作数会隐式转换成无符号类型
       - 否则，无符号类型的*转换等级*小于有符号类型：
         - 若有符号类型可以表达无符号类型的所有值，则无无符号类型的操作数被隐式转换成有符号操作数的类型。
         - 否则，两个操作数都会经历隐式转换，转换为有符号类型对应的无符号类型。

     (1)[↑](https://zh.cppreference.com/w/c/language/conversion#cite_ref-1) 有关分级规则，参见下文的[整数提升](https://zh.cppreference.com/w/c/language/conversion#.E6.95.B4.E6.95.B0.E6.8F.90.E5.8D.87)。

     (2)[↑](https://zh.cppreference.com/w/c/language/conversion#cite_ref-2) 参见下文[隐式转换语义](https://zh.cppreference.com/w/c/language/conversion#.E9.9A.90.E5.BC.8F.E8.BD.AC.E6.8D.A2.E8.AF.AD.E4.B9.89)中的“整数转换”部分。

```c
1.f + 20000001; // int 被转换成 float，给出 20000000.00
                // 相加后舍入到 float，给出 20000000.00
 
(char)'a' + 1L; // 首先，char 'a'，其值为 97，被提升为 int
                // 类型不同：int 和 long
                // 符号性相同：均有符号
                // 等级不同：long 的等级大于 int
                // 因而，int 97 转换为 long 97
                // 结果为 97 + 1 = 98，类型为 signed long
 
2u - 10; // 类型不同：unsigned int 和 signed int
         // 符号性不同
         // 等级相同
         // 因而，signed int 10 被转换为 unsigned int 10
         // 这是由于要对无符号整数实施算术运算
         // （参见“算术运算符”话题），所实施的计算为 (2 - 10)
         // 模 (2 的 n 次方)，其中 n 为 unsigned int 的值位数
         // 若 unsigned int 为 32 位宽，且其对象表示中
         // 没有填充位，则其结果为 (-8) 模 (2 的 32 次方) = 4294967288
         // 类型为 unsigned int
 
5UL - 2ULL; // 类型不同：unsigned long 和 unsigned long long
            // 符号性相同
            // 等级不同：unsigned long long 的等级更大
            // 因而，unsigned long 5 被转换为 unsigned long long 5
            // 这是由于要对无符号整数实施算术运算
            // （参见“算术运算符”话题），
            // 若 unsigned long long 为 64 位宽，则
            // 其结果为 (5 - 2) 模 (2 的 64 次方) = 3
            // 类型为 unsigned long long
 
0UL - 1LL; // 类型不同：unsigned long 和 signed long long
           // 符号性不同
           // 等级不同：signed long long 的等级更大。
           // 若 ULONG_MAX > LLONG_MAX，则 signed long long 不能表示
           // unsigned long 的所有值，因而，这属于最后一种情况：两操作数均被
           // 转换为 unsigned long long，unsigned long 0 被转换为 unsigned long long 0
           // long long 1 被转换为 unsigned long long 1，这是由于
           // 要对无符号整数实施算术运算
           // （参见“算术运算符”话题），
           // 若 unsigned long long 为 64 位宽，则
           // 计算为 (0 - 1) 模 (2 的 64 次方)
           // 因此，其结果为 18446744073709551615 (ULLONG_MAX)，
           // 类型为 unsigned long long
```

|      | (C99 起) |
| ---- | -------- |
|      |          |

​	结果类型按下列方式确定：(C99 起)

- 若两操作数均为复数，则结果类型是复数；
- 若两操作数均为虚数，则结果类型是虚数；
- 若两操作数均为实数，则结果类型为实数；
- 若两浮点数操作数拥有不同定义域（复数 VS 实数、复数 VS 虚数，或虚数 VS 实数），则结果类型是复数。

```c
double complex z = 1 + 2*I;
double f = 3.0;
z + f; // z 保持原态，f 被转换成 double ，结果是 double complex
```

​	浮点数运算符的结果可能照常会有大于其类型所指示的范围和及精度（见 [FLT_EVAL_METHOD](http://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD)）。

> 注意 (C99 起)
>
> ​	实数和虚数操作数不会隐式转换成复数，因为这么做需要额外计算，会在牵涉到无穷大、`NaN` 和有符号零的具体情况时产生不想要的结果。例如，若实数被转换成复数，`2.0×(3.0+i∞)` 会按照 `(2.0+i0.0)×(3.0+i∞) ⇒ (2.0×3.0–0.0×∞) + i(2.0×∞+0.0×3.0) ⇒ NaN+i∞` 求值，而非正确的 `6.0+i∞`。若虚数被转换成复数，则 `i2.0×(∞+i3.0)` 会按照 `(0.0+i2.0) × (∞+i3.0) ⇒ (0.0×∞ – 2.0×3.0) + i(0.0×3.0 + 2.0×∞) ⇒ NaN + i∞` 求值，而非 `–6.0 + i∞`。

> 注意
>
> ​	无关乎一般算术转换，可以在[如同规则](https://zh.cppreference.com/w/c/language/as_if)下，始终以窄于这些规则指定的类型进行计算。

## 值变换

### 左值转换

​	任何非数组类型的[左值表达式](https://zh.cppreference.com/w/c/language/value_category)，在用于异于下列语境时

- 作为[取值运算符](https://zh.cppreference.com/w/c/language/operator_member_access)的操作数（若允许），
- 作为前/后[自增减运算符](https://zh.cppreference.com/w/c/language/operator_incdec)的操作数，
- 作为[成员访问](https://zh.cppreference.com/w/c/language/operator_member_access)（点）运算符的左操作数，
- 作为[赋值与复合赋值](https://zh.cppreference.com/w/c/language/operator_assignment)运算符的左操作数，
- 作为 [`sizeof`](https://zh.cppreference.com/w/c/language/sizeof) 的操作数，

​	会经历*左值转换* ﻿：类型保持相同，但失去 [`const`](https://zh.cppreference.com/w/c/language/const)/[`volatile`](https://zh.cppreference.com/w/c/language/volatile)/[`restrict`](https://zh.cppreference.com/w/c/language/restrict) 限定符及[原子](https://zh.cppreference.com/w/c/language/atomic)属性，若原先有。值保持相同，但失去其左值属性（不再能取其地址）。

​	若左值拥有不完整类型，则行为未定义。

​	若左值指代自动存储期的对象，该对象从不被取地址，且若该对象未被初始化（没有用初始化器声明且没有在使用它前赋值），则行为未定义。

​	此转换模拟从内存中其位置加载对象的值。

```c
volatile int n = 1;
int x = n;            // n 上左值转换读 n 的的值
volatile int* p = &n; // 无左值转换：不读 n 的值
```

### 数组到指针转换

​	任何[数组类型](https://zh.cppreference.com/w/c/language/array)的[左值表达式](https://zh.cppreference.com/w/c/language/value_category)(C99 前)[表达式](https://zh.cppreference.com/w/c/language/expressions)(C99 起)，在用于下列语境之外时

- 作为[取址运算符](https://zh.cppreference.com/w/c/language/operator_member_access)的操作数，
- 作为 [`sizeof`](https://zh.cppreference.com/w/c/language/sizeof) 的操作数，
- 作为 [`typeof`](https://zh.cppreference.com/w/c/language/typeof) 和 [`typeof_unqual`](https://zh.cppreference.com/w/c/language/typeof_unqual) 的操作数 (C23 起)，
- 作为用于[数组初始化](https://zh.cppreference.com/w/c/language/array_initialization)的字符串字面量，

​	会经历到指向其首元素的非左值指针的转换。

​	若数组声明为 [`register`](https://zh.cppreference.com/w/c/language/storage_duration)，则行为未定义。

​	非左值数组或其任何元素不可访问(C99 前)拥有[临时生存期](https://zh.cppreference.com/w/c/language/lifetime#.E4.B8.B4.E6.97.B6.E7.94.9F.E5.AD.98.E6.9C.9F)(C99 起)。

```v
int a[3], b[3][4];
int* p = a;      /* 转换成 &a[0] */
int (*q)[4] = b; /* 转换成 &b[0] */
 
struct S
{
    int a[1];
};
 
struct S f(void)
{
    struct S result = {{0}}; /* C99 起支持 {0} */
    return result;
}
 
void g(void)
{
    int* p = f().a;    /* C99 前错误；C99 起 OK */
    int n  = f().a[0]; /* C99 前错误；C99 起 OK */
    f().a[0] = 13      /* C99 前错误；C99 起 UB */
    (void)p, (void)n;
}
 
int main(void) { return 0; }
```

### 函数到指针转换

​	任何函数指代器表达式，在用于异于下列语境时

- 作为[取址运算符](https://zh.cppreference.com/w/c/language/operator_member_access)的操作数，
- 作为 [`sizeof`](https://zh.cppreference.com/w/c/language/sizeof) 的操作数，
- 作为 [`typeof`](https://zh.cppreference.com/w/c/language/typeof) 和 [`typeof_unqual`](https://zh.cppreference.com/w/c/language/typeof_unqual) 的操作数 (C23 起)，

​	会经历到指向表达式所指代函数的指针的转换。

```
int f(int);
int (*p)(int) = f; // 转换成 &f
(***p)(1); // 重复解引用到 f 和转换回 &f
```

## 隐式转换语义

​	隐式转换，要么是*如同赋值* ﻿要么是*一般算术转换* ﻿，由二阶段组成：

1) 值变换（若可应用），
2) 下列转换之一（若它能产生目标类型）。

### 兼容类型

​	将任何类型的值转换成任何[兼容类型](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)始终是无操作，且不改变表示。

```c
uint8_t (*a)[10];         // 若 uint8_t 是对 unsigned char 的 typedef
unsigned char (*b)[] = a; // 则这些指针类型是兼容的
```

### 整数提升

​	整数提升是任何*等级*小于或等于 `int` *等级*的整数类型，或是 `_Bool`(C23 前)`bool`(C23 起)、`int`、`signed int`、`unsigned int` 类型的[位域](https://zh.cppreference.com/w/c/language/bit_field)类型的值到 `int` 或 `unsigned int` 类型值的隐式转换。

​	若 `int` 能表示原类型的整个值域（或原位域的值域），则值转换成 `int` 类型。否则值转化成 `unsigned int` 类型。

​	位精确整数类型的位域的值，转换为对应的位精确整数类型。其他情况下，位精确整数类型免于遵守整数提升规则。(C23 起)

​	整数提升保持值，包含符号：

```c
int main(void)
{
   void f(); // 旧式函数声明
             // 自 C23 起，void f(...) 在提升方面具有相同行为
   char x = 'a'; // 整数转换 int 到 char
   f(x); // 整数提升 char 回 int
}
 
void f(x) int x; {} // 函数期待 int
```

​	上述的*等级*是每个[整数类型](https://zh.cppreference.com/w/c/language/types)的属性，定义如下：

1) 所有有符号整数的等级都不同，且按其精度递增：signed char 等级 < short 等级 < int 等级 < long 等级 < long long 等级
2) 所有有符号整数等级与对应无符号整数等级相等
3) 任何标准整数类型的等级大于任何相同大小的扩充整数类型或位精确整数类型(C23 起)的等级（即 __int64 等级 < long long 等级，但根据规则(1)，long long 等级 < __int128 等级）
4) char 的等级等于 signed char 和 unsigned char 的等级
5) _Bool(C23 前)bool(C23 起) 的等级小于任何其他标准整数类型的等级
6) 任何枚举类型的等级等于其兼容整数类型的等级
7) 等级排行是传递性的：若 T1 等级 < T2 等级 且 T2 等级 < T3 等级 ，则 T1 等级 < T3 等级。
8) 位精确有符号整数类型的等级，应当大于任何更小宽度的标准整数类型或更小宽度的位精确整数类型的等级。(C23 起)
9) 任何位精确整数类型的等级，与相同宽度的扩充整数类型的等级之间的关系由实现定义。(C23 起)

10) 任何上面未提及的扩展整数类型排行方面是实现定义的

> 注意
>
> ​	整数提升仅应用于
>
> - *一般算术转换*的一部分（见前述），
> - *默认参数提升*的一部分（见前述），
> - 给一元算术运算符 + 和 - 的操作数，
> - 给一元位运算符 ~ 的操作数，
> - 给位移运算符 << 和 >> 的两个操作数。

### 布尔转换 (C99 起)

​	任何标量类型的值可以隐式转换成 `_Bool`(C23 前)`bool`(C23 起)。与值为零的整型常量表达式比较相等的值(C23 前)值为零（对于算术类型）、`null`（对于指针类型），或类型为 [nullptr_t](https://zh.cppreference.com/w/c/types/nullptr_t) 的值(C23 起)转换成 `0`(C23 前)`false`(C23 起)，所有其他值转换成 `1`(C23 前)`true`(C23 起)。

```c
bool b1 = 0.5;              // b1 == 1 （0.5 转换成 int 会是零）
bool b2 = 2.0*_Imaginary_I; // b2 == 1 （但转换成 int 会是零）
bool b3 = 0.0 + 3.0*I;      // b3 == 1 （但转换成 int 会是零）
bool b4 = 0.0 / 0.0;        // b4 == 1 （NaN 与零比较不相等）
bool b5 = nullptr;          // b5 == 0 （C23 起：nullptr 转换为 false）
```



### 整数转换

​	任何整数类型的值可以隐式转换到任何其他整数类型。除了上述整数提升和布尔转换所提及的情况，规则为：

- 若目标类型能表示值，则值不变，
- 否则，若目标类型为无符号，则源值会重复减或加值 \\(2^b\\)，其中 `b` 是目标类型的值位数，直到结果符合目标类型。换言之，无符号整数实现模算术。
- 否则，若目标类型为有符号，则行为是实现定义的（可能包括引发信号）。

```c
char x = 'a'; // int -> char，结果不变
unsigned char n = -123456; // 目标是无符号数，结果为 192 （即 -123456+483*256 ）
signed char m = 123456;    // 目标是有符号数，结果由实现定义
assert(sizeof(int) > -1);  // 断言失败：
                           // 运算符 > 要求 -1 到 size_t 的转换，
                           // 目标为无符号，结果是 SIZE_MAX
```

### 实浮点数整数转换

​	任何实浮点数类型的有限值可以隐式转换到任何整数类型。除了上述布尔转换所提及的情况，规则为：

- 忽略小数部分（向零取整）。
  - 若结果值可表示成目标类型，则使用该值
  - 否则，行为未定义。

```c
int n = 3.14; // n == 3
int x = 1e10; // 对于 32 位 int 是未定义行为
```

​	任何整数类型的值可以隐式转换成任何实浮点数类型。

- 若值能被目标类型准确表示，则它不变。
- 若值能被表示，但无法准确表示，则结果是最接近的较高或较低值之间由实现定义的选择，尽管若支持IEEE算术，则向最近舍入。此情况下是否引发 [FE_INEXACT](http://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 是未指定的。
- 若值不能被表示，则行为未定义，尽管若支持 IEEE 算术，则引发 [FE_INVALID](http://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 且值为未指定。

​	此转换的结果可能拥有大于其目标类型所指示的值和精度（见 [FLT_EVAL_METHOD](http://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD)）。

​	若在浮点数到整数转换中控制 [FE_INEXACT](http://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)，则可以使用 [rint](https://zh.cppreference.com/w/c/numeric/math/rint) 及 [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint)。

```c
double d = 10; // d = 10.00
float f = 20000001; // f = 20000000.00 (FE_INEXACT)
float x = 1 + (long long)FLT_MAX; // 未定义行为
```

### 实浮点数转换

​	任何实浮点数类型的值可以隐式转换到任何其他实浮点数类型。

- 若值能被目标类型准确表示，则它不变。

- 若值能被表示，但无法准确表示，则结果是最接近的较高或较低值（换言之，舍入方向是实现定义的），尽管若支持IEEE算术，则向最近舍入。

- 若值不能被表示，则行为未定义

  > 本节未完成 
  >
  > 原因：检查 IEEE ，是否适用于有符号无穷大

  。

​	此转换的结果可能拥有大于其目标类型所指示的值和精度（见 [FLT_EVAL_METHOD](http://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD)）。

```c
double d = 0.1; // d = 0.1000000000000000055511151231257827021181583404541015625
float f = d;    // f = 0.100000001490116119384765625
float x = 2 * (double)FLT_MAX; // 未定义
```

### 复数类型转换

​	任何复数类型的值可以隐式转换成任何另一种复数类型。实部和虚部各自遵循实浮点数类型的转换规则。

```c
double complex d = 0.1 + 0.1*I;
float complex f = d; // f 为 (0.100000001490116119384765625, 0.100000001490116119384765625)
```

### 虚数类型转换

​	任何虚数类型的值可以隐式转换成另一种虚数类型。虚部遵循实浮点数类型的转换规则。

```c
double imaginary d = 0.1*_Imaginary_I;
float imaginary f = d; // f 为 0.100000001490116119384765625*I
```

### 实复数转换

​	任何实浮点数类型的值可以隐式转换成任何复数类型。

- 结果的实部根据实浮点数类型的转换规则确定
- 结果的虚部是正零（或非 IEEE 系统上的无符号零）

​	任何复数类型的值可以隐式转换成任何实浮点数类型

- 实部遵循实浮点数类型的规则转换
- 虚部被忽略。

> 注意
>
> ​	在复到实转换中，虚部的 NaN 不会传播到实结果。

```c
double complex z = 0.5 + 3*I;
float f = z;  // 舍去虚部，设置 f 为 0.5
z = f;        // 设置 z 为 0.5 + 0*I
```

### 实虚数转换

​	任何虚数类型的值可以转换到任何实数类型（整数或浮点数）。结果始终是正（或无符号）零，除非目标类型是 `_Bool`(C23 前)`bool`(C23 起)，这种情况下会应用布尔转换规则。

​	任何实数类型的值可以隐式转换成任何虚数类型。结果始终是虚数正零。

```c
double imaginary z = 3*I;
bool b = z;  // 布尔转换：设置 b 为 true 
float f = z; // 实虚转换：设置 f 为 0.0 
z = 3.14;    // 虚实转换：设置 z 为 0*_Imaginary_I
```

### 复虚数转换

​	任何虚数类型的值可以隐式转换到任何复数类型。

- 结果的实部是正零。
- 结果的虚部遵循对应的实类型转换规则。

​	任何复数类型可以隐式转换到任何虚数类型。

- 实部被忽略。
- 结果的虚部遵循对应的实数类型转换规则。

```c
double imaginary z = I * (3*I); // 复结果 -3.0+0i 失去实部
                                // 设置 z 为 0*_Imaginary_I
```

### 指针转换

​	指向 void 可与任何指向对象指针类型间相互隐式转换，并拥有下列语义：

- 若指向对象的指针被转换成指向void的指针再转换回来，则其值与原指针比较相等。
- 不提供其他保证。

```c
int* p = malloc(10 * sizeof(int)); // malloc 返回 void*
```

​	指向无限定类型的指针可以隐式转换成指向该类型有限定版本的指针（换言之，可以添上 [`const`](https://zh.cppreference.com/w/c/language/const)、[`volatile`](https://zh.cppreference.com/w/c/language/volatile)、及 [`restrict`](https://zh.cppreference.com/w/c/language/restrict) 限定符）。原指针与结果比较相等。

```c
int n;
const int* p = &n; // &n 拥有类型 int*
```

​	任何拥有值 0 的整数[常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)也是一个拥有转换成 void* 类型的零的整数指针表达式，可以隐式转换成任意指针类型（既可以是指向对象指针，又可以是指向函数指针）。结果是该类型的空指针值，保证与任何该类型的非空指针值比较不相等。此整数或 void* 表达式又称*空指针常量*，而且标准库提供此常量作为宏 [NULL](https://zh.cppreference.com/w/c/types/NULL) 的一种定义。

```c
int* p = 0;
double* q = NULL;
```

## 注解

​	尽管有符号整数在任何算术运算符中的溢出是未定义行为，在整数类型转换中溢出有符号整数仅是未指定行为。

另一方面，尽管任何算术运算符（和整数转换）中无符号整数溢出是良好定义的操作，并遵循模算术规则，在浮点数到整数转换中溢出无符号整数是未定义行为：可以转换成无符号整数的实浮点数类型值是来自开区间 \\((-1, Unnn_MAX + 1) \\)的值。

```c
unsigned int n = -1.0; // 未定义行为
```

​	指针和整数间（除了从指针到 `_Bool`(C23 前)`bool`(C23 起) 和从拥有零值的整数常量表达式到指针）、指向对象指针间（除了从或到指向 `void` 的指针）以及指向函数指针间（除非函数拥有兼容类型）的转换始终非隐式，并要求有[转换运算符](https://zh.cppreference.com/w/c/language/cast)。

​	不存在（隐式或显式的）指向函数指针与指向对象指针（包括 `void*`）或整数间的转换。

## 参阅

**隐式转换**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/implicit_cast)**