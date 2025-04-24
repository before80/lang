
+++
title = "<float.h>"
date = 2025-04-24T18:05:40+08:00
weight = 50
type = "docs"
description = "浮点数类型的极限"
isCJKLanguage = true
draft = false

+++

## 类型




## 枚举




## 宏



### DBL_DECIMAL_DIG

原址：

作用：将 `float`/`double`/`long double` 转换为带有至少 FLT_DECIMAL_DIG/DBL_DECIMAL_DIG/LDBL_DECIMAL_DIG 个数位的十进制数，再转换回去为恒等转换：此为序列号/反序列化浮点数值所需的十进制精度。分别至少定义为 `6`、`10` 和 `10`，或对于 IEEE float 为 `9`，对于 IEEE double 为 `17`（另见 C++ 对应物：max_digits10）  (宏常量)

备注：





### DBL_DIG

原址：

作用：在“文本 → `float`/`double`/`long double` → 文本”往返转换中保证被保留且不会印舍入或溢出而改变的十进制数位个数（参见 C++ 对应物 digits10 的详情）  (宏常量)

备注：





### DBL_EPSILON

原址：

作用：分别为 `1.0` 与 `float`、`double` 和 `long double` 的下一个可表示值之差的绝对值  (宏常量)

备注：





### DBL_HAS_SUBNORM

原址：

作用：类型是否支持非正规）数值：`-1` – 不确定, `​0​` – 不支持, `1` – 支持  (宏常量)

备注：





### DBL_MANT_DIG

原址：

作用：分别为 `float`、`double` 和 `long double` 可表示且不损失精度的 FLT_RADIX 进制有效数字数位个数  (宏常量)

备注：





### DBL_MAX

原址：

作用：分别为 `float`、`double` 和 `long double` 的最大有穷值  (宏常量)

备注：





### DBL_MAX_10_EXP

原址：

作用：分别为对于 `float`、`double` 和 `long double` 的最大正整数，使得 10 的该整数次方是该类型的可表示有穷值  (宏常量)

备注：





### DBL_MAX_EXP

原址：

作用：分别为对于 `float`、`double` 和 `long double` 的最大正整数，使得 FLT_RADIX 的该整数减一次方是该类型的可表示有穷值  (宏常量)

备注：





### DBL_MIN

原址：

作用：分别为 `float`、`double` 和 `long double` 的最小正规正数值  (宏常量)

备注：





### DBL_MIN_10_EXP

原址：

作用：分别为对于 `float`、`double` 和 `long double` 的最小负整数，使得 10 的该整数次方是该类型的正规值  (宏常量)

备注：





### DBL_MIN_EXP

原址：

作用：分别为对于 `float`、`double` 和 `long double` 的最小负整数，使得 FLT_RADIX 的该整数减一次方是该类型的正规值  (宏常量)

备注：





### DBL_TRUE_MIN

原址：

作用：分别为 `float`、`double` 和 `long double` 的最小整数值  (宏常量)

备注：





### DECIMAL_DIG

原址：

作用：将 `long double` 转换为带有至少 DECIMAL_DIG 个数位的十进制数，再转换回 `long double` 为恒等转换：此为序列化/反序列化 `long double` 所需的十进制精度  (宏常量)

备注：





### FLT_DECIMAL_DIG

原址：

作用：将 `float`/`double`/`long double` 转换为带有至少 FLT_DECIMAL_DIG/DBL_DECIMAL_DIG/LDBL_DECIMAL_DIG 个数位的十进制数，再转换回去为恒等转换：此为序列号/反序列化浮点数值所需的十进制精度。分别至少定义为 `6`、`10` 和 `10`，或对于 IEEE float 为 `9`，对于 IEEE double 为 `17`（另见 C++ 对应物：max_digits10）  (宏常量)

备注：





### FLT_DIG

原址：

作用：在“文本 → `float`/`double`/`long double` → 文本”往返转换中保证被保留且不会印舍入或溢出而改变的十进制数位个数（参见 C++ 对应物 digits10 的详情）  (宏常量)

备注：





### FLT_EPSILON

原址：

作用：分别为 `1.0` 与 `float`、`double` 和 `long double` 的下一个可表示值之差的绝对值  (宏常量)

备注：





### FLT_EVAL_METHOD

原址：[https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD)

作用：指定所有算术运算以什么精度执行  (宏常量)

备注：
```c
// 在标头 <float.h> 定义
#define FLT_EVAL_METHOD /* 由实现定义 */// (C99 起)
```

​	指定从浮点常量和除了赋值、转型及库函数调用外的所有运算（运算符、操作数的隐式转换）所获得的浮点值的范围和精度。

| 值               | 解释                                                         |
| ---------------- | ------------------------------------------------------------ |
| 除 `-1` 外的负值 | 实现定义行为                                                 |
| `-1`             | 默认精度未知                                                 |
| `0`              | 以所用类型的范围和精度进行所有运算和常量求值。而且，`float_t` 和 `double_t` 分别等价于 `float` 和 `double` |
| `1`              | 以 `double` 的范围和精度进行所有运算和常量求值。而且，`float_t` 和 `double_t` 都等价于 `double` |
| `2`              | 以 `long double` 的范围和精度进行所有运算和常量求值。而且，`float_t` 和 `double_t` 都等价于 `long double` |

**注解**

​	无关乎 `FLT_EVAL_METHOD` 的值，任何浮点表达式都可以被*缩短*，即如同所有中间结果拥有无限范围和精度一般进行（除非关闭 [`<#pragm>`](https://zh.cppreference.com/w/cpp/preprocessor/impl) `STDC FP_CONTRACT`）。

​	转型和复制会剥除任何额外的范围和精度：这模拟从扩展精度 FPU 寄存器存储值到标准大小内存位置的动作。

**参阅**

| [float_t (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/float_t) | 宽度至少等于 `float` 的最高效浮点数类型 (typedef) |
| ------------------------------------------------------------ | ------------------------------------------------- |
| [double_t (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/float_t) | 宽度至少等于 `double` 的最高效浮点类型 (typedef)  |
| **FLT_EVAL_METHOD** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/climits/FLT_EVAL_METHOD)** |                                                   |





### FLT_HAS_SUBNORM

原址：

作用：类型是否支持非正规）数值：`-1` – 不确定, `​0​` – 不支持, `1` – 支持  (宏常量)

备注：





### FLT_MANT_DIG

原址：

作用：分别为 `float`、`double` 和 `long double` 可表示且不损失精度的 FLT_RADIX 进制有效数字数位个数  (宏常量)

备注：





### FLT_MAX

原址：

作用：分别为 `float`、`double` 和 `long double` 的最大有穷值  (宏常量)

备注：





### FLT_MAX_10_EXP

原址：

作用：分别为对于 `float`、`double` 和 `long double` 的最大正整数，使得 10 的该整数次方是该类型的可表示有穷值  (宏常量)

备注：





### FLT_MAX_EXP

原址：

作用：分别为对于 `float`、`double` 和 `long double` 的最大正整数，使得 FLT_RADIX 的该整数减一次方是该类型的可表示有穷值  (宏常量)

备注：





### FLT_MIN

原址：

作用：分别为 `float`、`double` 和 `long double` 的最小正规正数值  (宏常量)

备注：





### FLT_MIN_10_EXP

原址：

作用：分别为对于 `float`、`double` 和 `long double` 的最小负整数，使得 10 的该整数次方是该类型的正规值  (宏常量)

备注：





### FLT_MIN_EXP

原址：

作用：分别为对于 `float`、`double` 和 `long double` 的最小负整数，使得 FLT_RADIX 的该整数减一次方是该类型的正规值  (宏常量)

备注：





### FLT_RADIX

原址：

作用：全部三种浮点数类型的表示所用的基数（整数基）  (宏常量)

备注：





### FLT_ROUNDS

原址：[https://zh.cppreference.com/w/c/types/limits/FLT_ROUNDS](https://zh.cppreference.com/w/c/types/limits/FLT_ROUNDS)

作用：浮点数算术的舍入模式  (宏常量)

备注：
*//* *移除不需要的元素 以及 替换复制不了的元素
**//* *移除页头
**function* *removeHead*() {
    document.querySelector('#mw-head').remove();
}

*//* *移除页尾
**function* *removeFooter*() {
    document.querySelector('#cpp-footer-base').remove();
}

*//* *移除* *H1
**function* *removeH1*() {
    document.querySelector('#firstHeading').remove();
}

*//* *移除 面包屑导航菜单
**function* *removeBreadcrumbMenu*() {
    document.querySelector('#mw-content-text div.*t-navbar*').remove();
}

*//* *替换定义所在表格
**//* *注意必须在其他替换之前执行
**function* *replaceDefineTableToPreCode*() {
    *//* *获取第一个* *table.t-dcl-begin* *元素
\*    *const* table = document.querySelector('table.*t-dcl-begin*');

​    *if* (table) {
​        *//* *用于存储转换后的内容
\*        *let* preContent = '';

​        *//* *遍历表格的行，除了表头行
\*        *for* (*let* i = 0; i < table.rows.length; i++) {
​            *const* row = table.rows[i];
​            *const* tdContent = row.cells[0].textContent.trim();
​            *const* comment1 = row.cells[1].textContent.trim();
​            *const* comment2 = row.cells[2].textContent.trim();
​            *let* line
​            *if* (tdContent.startsWith("在标头")) {
​                *// line = "<span style='display:flex;'><span>//" + tdContent + "<span><span>";
\*                line = `<span style='display:flex;'><span>// ${tdContent}<span><span>`;
​            } *else* {
​                line = `<span style='display:flex;'><span>${tdContent}<span><span>`;
​                *// line = "<span style='display:flex;'><span>" + tdContent + "<span><span>";
\*                *if* (comment1) {
​                    *if* (comment2) {
​                        line += "// " + comment1 + comment2 + "<span></span>";
​                    } *else* {
​                        line += "// " + comment1 + "<span></span>";
​                    }
​                } *else* {
​                    *if* (comment2) {
​                        line += "// " + comment2 + "<span></span>";
​                    }
​                }
​            }
​            line += '</span>\n';
​            preContent += line;
​        }

​        *//* *用* *<pre>* *标签包裹内容
\*        *const* result = "<pre>" + preContent + "</pre>";

​        *//* *创建一个新的元素来存储处理后的内容
\*        *const* newElement = document.createElement('div');
​        newElement.innerHTML = result;

​        *//* *移除原表格
\*        table.parentNode.replaceChild(newElement, table);
​    }
}


*//* *移除* *h3=**引用 的内容
**function* *removeH3YinYong*() {
    *const* allH3 = document.querySelectorAll('h3');

*//* *遍历查找包含**"**引用**"**的* *h3* *标签
\*    *let* targetH3 = *null*;
    *for* (*const* h3 *of* allH3) {
        *const* headlineSpan = h3.querySelector('.*mw-headline*');
        *if* (headlineSpan && headlineSpan.textContent.trim() === '引用') {
            targetH3 = h3;
            *break*;
        }
    }

​    *if* (targetH3) {
​        *//* *删除操作
\*        *let* nextElement = targetH3.nextElementSibling;

​        *//* *循环处理后续元素，直到遇到下一个* *h3
\*        *while* (nextElement && nextElement.tagName !== 'H3') {
​            *const* currentElement = nextElement;
​            nextElement = currentElement.nextElementSibling; *//* *先保存下一个元素
**
\*            *//* *删除符合要求的* *div
\*            *if* (currentElement.tagName === 'DIV' && currentElement.className.startsWith('t-ref-std')) {
​                currentElement.remove();
​            }
​        }

​        *//* *最后删除目标* *h3* *本身
\*        targetH3.remove();
​    }
}


*//* *移除* *h3=**参阅 的内容
**function* *removeH3CanYue*() {
    *const* allH3 = document.querySelectorAll('h3');

*//* *遍历查找包含**"**引用**"**的* *h3* *标签
\*    *let* targetH3 = *null*;
    *for* (*const* h3 *of* allH3) {
        *const* headlineSpan = h3.querySelector('.*mw-headline*');
        *if* (headlineSpan && headlineSpan.textContent.trim() === '参阅') {
            targetH3 = h3;
            *break*;
        }
    }

​    *if* (targetH3) {
​        *//* *删除操作
\*        *let* nextElement = targetH3.nextElementSibling;

​        *//* *循环处理后续元素，直到遇到下一个* *h3
\*        *while* (nextElement) {
​            *const* currentElement = nextElement;
​            nextElement = currentElement.nextElementSibling; *//* *先保存下一个元素
**
\*            *//* *删除
\*            currentElement.remove();
​        }

​        *//* *最后删除目标* *h3* *本身
\*        targetH3.remove();
​    }
}

*function* *removeRunCode*() {
    *const* allDiv = document.querySelectorAll('.*t-example-live-link*');
    *for* (*const* div *of* allDiv) {
        div.remove()
    }
}

*//* *移除页面中所有* *<p><br></p>
**function* *removePBr*() {
    *const* paragraphs = document.getElementsByTagName('p');
    *const* paragraphsToRemove = [];

​    *for* (*let* i = 0; i < paragraphs.length; i++) {
​        *const* paragraph = paragraphs[i];
​        *if* (paragraph.childElementCount === 1 && paragraph.firstElementChild.tagName === 'BR') {
​            paragraphsToRemove.push(paragraph);
​        }
​    }

​    paragraphsToRemove.forEach(paragraph => {
​        paragraph.parentNode.removeChild(paragraph);
​    });
}

*function* *replaceSpanSourceC*() {
    document.querySelectorAll('span.*mw-geshi*.*c*.*source-c*').forEach(span => {
        *if* (!span.querySelector(".*kw486*")) {
            *//* *在原有内容前后添加反引号（保留内部**HTML**结构）
\*            span.innerHTML = "\u0060" + span.innerHTML + "\u0060";
        }
    });
}

*function* *replaceDlToUl*() {
    document.querySelectorAll('dl').forEach(dl => {
        *const* ul = document.createElement('ul');
        ul.style.listStyleType = 'disc'; *//* *保持列表样式
**
\*        *//* *将* *<dd><ul>* *转换为常规列表
\*        dl.querySelectorAll('li').forEach(li => {
            *const* newLi = document.createElement('li');
            newLi.innerHTML = "​	" + li.innerHTML; *//* *保留原有内容
\*            ul.appendChild(newLi);
        });

​        *//* *替换原有* *<dl>* *结构
\*        dl.parentNode.replaceChild(ul, dl);
​    });
}

*function* *replaceXuHao*() {
    *//* *找到所有* *class="t-li"* *的元素
\*    *const* elements = document.querySelectorAll('.*t-li1* .*t-li*');

​    *//* *遍历每个元素
\*    elements.forEach(element => {
​        *//* *获取元素的文本内容
\*        *const* text = element.textContent.trim();

​        *//* *使用正则表达式检查内容是否符合要求
\*        *const* regex = /^\d+\)$/; *//* *匹配以数字开头，以* *)* *结尾的内容
**
\*        *if* (regex.test(text)) {
​            *//* *替换* *)* *为 ）
\*            element.textContent = text.replace(')', '）');
​        }
​    });
}

*//* *在**p**标签前面添加一个**span**，其内容为**​	**用于后期在**markdown**中替换成**Tab**符号
**function* *replaceP*() {
    *//* *在**p**标签前面插入**​	
\*    *let* pElements = document.querySelectorAll('p');

​    pElements.forEach(*function* (element) {
​        *let* newSpan = document.createElement('span');
​        newSpan.textContent = '​	';
​        *if* (element.firstChild) {
​            element.insertBefore(newSpan, element.firstChild);
​        } *else* {
​            *//* *如果* *p* *元素没有子节点，直接将新* *span* *元素添加到* *p* *元素中
\*            element.appendChild(newSpan);
​        }
​    });
}

*function* *replaceTableContentAddBr*() {
    *//* *增加* *.t-lines span* *下的文本内容，增加**<br >**用于后面在**md**文档中替换成换行符
\*    *let* spans = document.querySelectorAll('.*t-lines* span');

*//* *遍历每个* *span* *元素
\*    spans.forEach(span => {
        *//* *获取原文本内容
\*        *const* originalText = span.textContent;
        *//* *在原文本末尾添加两个空格
\*        span.textContent = originalText + '<br />';
    });
}

*function* *replaceLtGt*() {
    *//* *替换**tt**标签中的**<* *和* *>* *为* *<**和* *>
\*    *let* ttElements = document.querySelectorAll('a tt');
    ttElements.forEach((tt) => {
        *let* text = tt.textContent;
        *if* (text.length > 0) {
            text = '<' + text.slice(1, -1) + '>';
            tt.textContent = text;
        }
    });
}

*function* *replaceNotice*() {
    *const* tables = document.querySelectorAll('table.*metadata*.*plainlinks*.*ambox*.*mbox-small-left*.*ambox-notice*');

​    tables.forEach(table => {
​        *const* blockquote = document.createElement('blockquote');
​        *const* rows = table.querySelectorAll('tr');

​        rows.forEach(row => {
​            *const* p = document.createElement('p');
​            *let* hasContent = *false*;
​            *const* cells = Array.from(row.querySelectorAll('td'));

​            *for* (*let* i = 0; i < cells.length; i++) {
​                *const* cell = cells[i];
​                *if* (cell.textContent.trim() !== '') {
​                    hasContent = *true*;
​                    *const* clonedCell = cell.cloneNode(*true*);
​                    *const* brTags = clonedCell.querySelectorAll('br');
​                    brTags.forEach(br => {
​                        *const* newBr = document.createElement('br');
​                        br.parentNode.insertBefore(newBr, br.nextSibling);
​                    });
​                    clonedCell.childNodes.forEach(child => {
​                        p.appendChild(child.cloneNode(*true*));
​                    });
​                }
​            }

​            *if* (hasContent) {
​                blockquote.appendChild(p);
​            }
​        });

​        table.parentNode.replaceChild(blockquote, table);
​    });
}

*//* *替换形似行的**table**，将**table**的内容替换成**p**标签包裹
**function* *replaceTRevBeginTable*() {
    *const* tables = document.querySelectorAll('table.*t-rev-begin*');

​    tables.forEach(table => {
​        *const* parent = table.parentNode;
​        *const* rows = table.querySelectorAll('tr');

​        rows.forEach(row => {
​            *const* p = document.createElement('p');
​            *const* cells = row.querySelectorAll('td');

​            cells.forEach(cell => {
​                *const* clonedCell = cell.cloneNode(*true*);
​                *const* brTags = clonedCell.querySelectorAll('br');
​                brTags.forEach(br => {
​                    br.parentNode.removeChild(br);
​                });

​                *const* pTags = clonedCell.querySelectorAll('p');
​                *if* (pTags.length > 0) {
​                    pTags.forEach(pTag => {
​                        pTag.childNodes.forEach(child => {
​                            p.appendChild(child.cloneNode(*true*));
​                        });
​                    });
​                } *else* {
​                    clonedCell.childNodes.forEach(child => {
​                        p.appendChild(child.cloneNode(*true*));
​                    });
​                }

​                *// if (cells[cells.length - 1]!== cell) {
\*                *//     p.appendChild(document.createElement('br'));
\*                *// }
\*            });

​            parent.insertBefore(p, table);
​        });

​        parent.removeChild(table);
​    });
}

*function* *replaceTableAddVersionAfterIdentifier*() {
    *//* *替换* *html**中的**td**行内容**:* *即将**C99**版本加在函数名后面，避免出现多行**C99**在单独行的情况
\*    *let* divElements = document.querySelectorAll('div.*t-dsc-member-div*');
    divElements.forEach((div) => {
        *const* firstDiv = div.querySelector('div:first-child');
        *const* secondDiv = div.querySelector('div:nth-child(2)');

​        *if* (firstDiv && secondDiv) {
​            *const* secondDivSpans = secondDiv.querySelectorAll('.*t-lines* span');
​            *const* firstDivSpans = firstDiv.querySelectorAll('.*t-lines* span');

​            firstDivSpans.forEach((span, index) => {
​                *if* (secondDivSpans[index]) {
​                    *let* contentToAppend = secondDivSpans[index].textContent;
​                    *// console.log("span.textContent=",span.textContent,"contentToAppend=",contentToAppend)
\*                    span.textContent += "   " + contentToAppend;
​                }
​            });
​            *//* *移除不要的**html**标签
\*            secondDiv.remove();
​        }
​    });
}

*removeHead*();
*removeFooter*();
*removeH1*();
*removeBreadcrumbMenu*();
*removePBr*();
*replaceLtGt*();
*replaceDefineTableToPreCode*();
*// removeH3YinYong();
**// removeH3CanYue();
**removeRunCode*();
*replaceSpanSourceC*();
*replaceDlToUl*();
*replaceXuHao*();
*replaceP*();
*replaceNotice*();
*replaceTRevBeginTable*();
*replaceTableAddVersionAfterIdentifier*();
*replaceTableContentAddBr*();

*//* *转义字符为正则表达式中可以直接使用的字符
**function* *quoteMeta*(str) {
    *return* str.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
}





### FLT_TRUE_MIN

原址：

作用：分别为 `float`、`double` 和 `long double` 的最小整数值  (宏常量)

备注：





### LDBL_DECIMAL_DIG

原址：

作用：将 `float`/`double`/`long double` 转换为带有至少 FLT_DECIMAL_DIG/DBL_DECIMAL_DIG/LDBL_DECIMAL_DIG 个数位的十进制数，再转换回去为恒等转换：此为序列号/反序列化浮点数值所需的十进制精度。分别至少定义为 `6`、`10` 和 `10`，或对于 IEEE float 为 `9`，对于 IEEE double 为 `17`（另见 C++ 对应物：max_digits10）  (宏常量)

备注：





### LDBL_DIG

原址：

作用：在“文本 → `float`/`double`/`long double` → 文本”往返转换中保证被保留且不会印舍入或溢出而改变的十进制数位个数（参见 C++ 对应物 digits10 的详情）  (宏常量)

备注：





### LDBL_EPSILON

原址：

作用：分别为 `1.0` 与 `float`、`double` 和 `long double` 的下一个可表示值之差的绝对值  (宏常量)

备注：





### LDBL_HAS_SUBNORM

原址：

作用：类型是否支持非正规）数值：`-1` – 不确定, `​0​` – 不支持, `1` – 支持  (宏常量)

备注：





### LDBL_MANT_DIG

原址：

作用：分别为 `float`、`double` 和 `long double` 可表示且不损失精度的 FLT_RADIX 进制有效数字数位个数  (宏常量)

备注：





### LDBL_MAX

原址：

作用：分别为 `float`、`double` 和 `long double` 的最大有穷值  (宏常量)

备注：





### LDBL_MAX_10_EXP

原址：

作用：分别为对于 `float`、`double` 和 `long double` 的最大正整数，使得 10 的该整数次方是该类型的可表示有穷值  (宏常量)

备注：





### LDBL_MAX_EXP

原址：

作用：分别为对于 `float`、`double` 和 `long double` 的最大正整数，使得 FLT_RADIX 的该整数减一次方是该类型的可表示有穷值  (宏常量)

备注：





### LDBL_MIN

原址：

作用：分别为 `float`、`double` 和 `long double` 的最小正规正数值  (宏常量)

备注：





### LDBL_MIN_10_EXP

原址：

作用：分别为对于 `float`、`double` 和 `long double` 的最小负整数，使得 10 的该整数次方是该类型的正规值  (宏常量)

备注：





### LDBL_MIN_EXP

原址：

作用：分别为对于 `float`、`double` 和 `long double` 的最小负整数，使得 FLT_RADIX 的该整数减一次方是该类型的正规值  (宏常量)

备注：





### LDBL_TRUE_MIN

原址：

作用：分别为 `float`、`double` 和 `long double` 的最小整数值  (宏常量)

备注：






## 函数




