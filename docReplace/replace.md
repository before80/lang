

替换html

```js
// 1
// 将 出现在表格中的h3 h4 h5 h6 单独出来，生成菜单后方便查找

function splitTableByHeadings() {
    const tables = document.querySelectorAll('table.t-dsc-begin');
    tables.forEach((table) => {
        const splitIndices = [];
        const rows = Array.from(table.rows);

        // 收集所有需要分割的行索引
        rows.forEach((row, index) => {
            const headings = row.querySelectorAll('h3, h4, h5, h6');
            if (headings.length > 0) {
                splitIndices.push(index);
            }
        });

        // 从后往前分割表格，避免索引混乱
        for (let i = splitIndices.length - 1; i >= 0; i--) {
            const splitIndex = splitIndices[i];
            const newTable = document.createElement('table');
            newTable.classList.add('t-dsc-begin');

            const headingRow = rows[splitIndex];
            const heading = headingRow.querySelector('h3, h4, h5, h6');

            // 移除当前表格中分割点之后的行，并添加到新表格
            for (let j = rows.length - 1; j > splitIndex; j--) {
                const rowToMove = rows[j];
                if (rowToMove.parentNode && rowToMove.textContent.trim()!== '') {
                    newTable.insertBefore(rowToMove.cloneNode(true), newTable.firstChild);
                    rowToMove.parentNode.removeChild(rowToMove);
                }
            }

            // 插入标题元素
            table.parentNode.insertBefore(heading, table.nextSibling);

            // 插入新表格，仅当新表格有内容时
            if (newTable.rows.length > 0) {
                table.parentNode.insertBefore(newTable, heading.nextSibling);
            }
        }

        // 处理标题在第一行的情况
        const firstRow = table.rows[0];
        if (firstRow) {
            const firstRowHeadings = firstRow.querySelectorAll('h4, h5, h6');
            if (firstRowHeadings.length > 0) {
                const newTable = document.createElement('table');
                newTable.classList.add('t-dsc-begin');

                const heading = firstRowHeadings[0];

                // 移除原表格的第一行
                if (firstRow.parentNode) {
                    firstRow.parentNode.removeChild(firstRow);
                }

                // 将原表格剩余行添加到新表格
                const remainingRows = Array.from(table.rows);
                remainingRows.forEach((row) => {
                    if (row.parentNode && row.textContent.trim()!== '') {
                        newTable.appendChild(row.cloneNode(true));
                        row.parentNode.removeChild(row);
                    }
                });

                // 插入标题元素
                table.parentNode.insertBefore(heading, table.nextSibling);

                // 插入新表格，仅当新表格有内容时
                if (newTable.rows.length > 0) {
                    table.parentNode.insertBefore(newTable, heading.nextSibling);
                }
            }
        }
    });
}

// 调用函数
splitTableByHeadings();
    


// 2
// 替换 html中的td行内容: 即将C99版本加在函数名后面，避免出现多行C99在单独行的情况
let tdElements = document.querySelectorAll('div.t-dsc-member-div');
tdElements.forEach((td) => {
    const firstDiv = td.querySelector('.t-dsc-member-div > div:first-child');
    const secondDiv = td.querySelector('.t-dsc-member-div > div:nth-child(2)');

    if (firstDiv && secondDiv) {
        const secondDivSpans = secondDiv.querySelectorAll('.t-lines span');
        const firstDivSpans = firstDiv.querySelectorAll('.t-lines span');

        firstDivSpans.forEach((span, index) => {
            if (secondDivSpans[index]) {
                let contentToAppend = secondDivSpans[index].textContent;
                // console.log("span.textContent=",span.textContent,"contentToAppend=",contentToAppend)
                span.textContent += "   " + contentToAppend;
            }
        });
		// 移除不要的html标签
        secondDiv.remove();
    }
});

// 3
// 增加 .t-lines span 下的文本内容，增加@!br !@用于后面在md文档中替换成换行符
let spans = document.querySelectorAll('.t-lines span');

// 遍历每个 span 元素
spans.forEach(span => {
    // 获取原文本内容
    const originalText = span.textContent;
    // 在原文本末尾添加两个空格
    span.textContent = originalText + '@!br /!@';
});


// 4
// 替换tt标签中的< 和 > 为 @!和 !@
let ttElements = document.querySelectorAll('a tt');
        ttElements.forEach((tt) => {
            let text = tt.textContent;
            if (text.length > 0) {
                text = '@!' + text.slice(1, -1) + '!@';
                tt.textContent = text;
            }
});



```





替换

```txt

// @! 替换成 <

// !@ 替换成 >



```



## LATEX 公式

```txt
启用必须有 math = true的配置
并在行中使用\\(公式内容\\)

\over  对应 分数线
\sqrt{} 对应 开方
\sqrt[3]{} 对应 开立方
_ 对应 底数
^ 对应 指数
\ne 对应 不等于
\pm 对应 正负号
```





```
function splitTableByHeadings() {
    const tables = document.querySelectorAll('table.t-dsc-begin');
    tables.forEach((table) => {
        const splitIndices = [];
        const rows = Array.from(table.rows);

        // 收集所有需要分割的行索引
        rows.forEach((row, index) => {
            const headings = row.querySelectorAll('h4, h5, h6');
            if (headings.length > 0) {
                splitIndices.push(index);
            }
        });

        // 从后往前分割表格，避免索引混乱
        for (let i = splitIndices.length - 1; i >= 0; i--) {
            const splitIndex = splitIndices[i];
            const newTable = document.createElement('table');
            newTable.classList.add('t-dsc-begin');

            const headingRow = rows[splitIndex];
            const heading = headingRow.querySelector('h4, h5, h6');

            // 移除当前表格中分割点之后的行，并添加到新表格
            for (let j = rows.length - 1; j > splitIndex; j--) {
                const rowToMove = rows[j];
                if (rowToMove.parentNode) {
                    newTable.insertBefore(rowToMove.cloneNode(true), newTable.firstChild);
                    rowToMove.parentNode.removeChild(rowToMove);
                }
            }

            // 插入标题元素
            table.parentNode.insertBefore(heading, table.nextSibling);

            // 插入新表格
            table.parentNode.insertBefore(newTable, heading.nextSibling);
        }

        // 处理标题在第一行的情况
        const firstRow = table.rows[0];
        if (firstRow) {
            const firstRowHeadings = firstRow.querySelectorAll('h4, h5, h6');
            if (firstRowHeadings.length > 0) {
                const newTable = document.createElement('table');
                newTable.classList.add('t-dsc-begin');

                const heading = firstRowHeadings[0];

                // 移除原表格的第一行
                if (firstRow.parentNode) {
                    firstRow.parentNode.removeChild(firstRow);
                }

                // 将原表格剩余行添加到新表格
                const remainingRows = Array.from(table.rows);
                remainingRows.forEach((row) => {
                    if (row.parentNode) {
                        newTable.appendChild(row.cloneNode(true));
                        row.parentNode.removeChild(row);
                    }
                });

                // 插入标题元素
                table.parentNode.insertBefore(heading, table.nextSibling);

                // 插入新表格
                table.parentNode.insertBefore(newTable, heading.nextSibling);
            }
        }
    });
}

// 调用函数
splitTableByHeadings();
```

