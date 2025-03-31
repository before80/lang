+++
title = "原生JS操作HTML"
date = 2025-02-27T20:39:05+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

## 元素获取

```js
// 根据元素的 id 属性值来获取单个元素。
// 返回类型是：HTMLElement 或其派生类型。HTMLElement 是所有 HTML 元素的基类，
//   不同类型的 HTML 元素会返回其具体的派生类型对象，例如：
//     如果指定 id 的元素是 <div>，则返回 HTMLDivElement 对象，它继承自 HTMLElement。
//     如果指定 id 的元素是 <input>，则返回 HTMLInputElement 对象。
// 特点：当文档中不存在具有指定 id 的元素时，该方法返回 null。
// 因此在使用返回值之前，最好先检查是否为 null，以避免出现错误。
const divElement = document.getElementById('myDivId');

// 根据元素的标签名来获取元素集合。
// 返回类型： HTMLCollection，实时的集合（即 HTMLCollection 会自动随 DOM 变化而更新）
// 特点：如果没有匹配的标签，则返回一个空的 HTMLCollection。
// 其他说明：HTMLCollection 是一个类似数组的对象
// （它有 length 属性，并且可以通过索引访问元素），
// 但它并不是真正的数组，没有继承数组的方法，所以不具备 forEach 方法。
const pElements = document.getElementsByTagName('p');
for (let i = 0; i < pElements.length; i++) {
    console.log(pElements[i]);
}

// 根据元素的 class 属性值来获取元素集合。
// 返回类型： HTMLCollection，实时的集合（即 HTMLCollection 会自动随 DOM 变化而更新）
// 特点：如果没有匹配的标签，则返回一个空的 HTMLCollection。
// 其他说明：HTMLCollection 是一个类似数组的对象
// （它有 length 属性，并且可以通过索引访问元素），
// 但它并不是真正的数组，没有继承数组的方法，所以不具备 forEach 方法。
const divElements = document.getElementsByClassName('myClass');
for (let i = 0; i < divElements.length; i++) {
    console.log(divElements[i]);
}

// 根据 CSS 选择器来获取单个元素。
// 返回类型： 单个 DOM 元素对象（Element）
// 特点： 返回匹配 CSS 选择器的第一个元素；如果没有找到匹配项，则返回 null。
const firstDiv = document.querySelector('.myClass');

// 根据 CSS 选择器来获取元素集合。
// 返回类型： NodeList，静态的集合（即 NodeList 不会自动随 DOM 变化而更新）
// 其他说明：在较新的浏览器环境（如 Chrome、Firefox、Safari 等现代主流浏览器）中，
// NodeList 对象已经实现了 forEach 方法。
// （它有 length 属性，并且可以通过索引访问元素），
const divElements = document.querySelectorAll('.myClass');
divElements.forEach(function (element) {
    console.log(element);
});
```



## 元素值的设置/选中/取消选中

```js
// 以下 getElementById 可以使用 getElementByTagName、getElementsByClassName等方法进行替换

// input 输入框
document.getElementById('myInput').value="设置的文本内容";

document.getElementsByTagName('input')[0].value="设置的文本内容";

document.getElementsByClassName('user')[0].value="设置的文本内容";

document.querySelector('.user').value="设置的文本内容";

document.querySelectorAll('.user')[0].value="设置的文本内容";

// radio 单选框
document.getElementById('male').checked=true;// 选中
document.getElementById('female').checked=true;// 选中


// checkbox 复选框
document.getElementById('hobbyReading').checked = true;// 选中
document.getElementById('hobbyReading').checked = false;// 取消选中

// select 单选的下拉框
document.getElementById('mySelect').value="某一选项值";

// select 多选的下拉框（即存在multiple属性，可通过按住CTRL 键进行跳选/ SHIFT键进行连续多选）
const options = document.getElementById('multiSelect').options;
for (let i = 0; i < options.length; i++) {
    if (options[i].value === 'red' || options[i].value === 'blue') {
        options[i].selected = true;
    }
}


// textarea 多行文本输入框
document.getElementById('myTextarea').value="设置的文本内容";

```



## 元素属性的获取/设置/移除

```js
// 获取 id=myLink 元素的 href 属性
// 方法1：通过 getAttribute 方法
const hrefValue = document.getElementById('myLink').getAttribute('href');

// 方法2：直接通过属性名
const hrefValue = document.getElementById('myLink').href;

// 设置 data-my-custom 属性的值
// 方法1：通过 setAttribute 方法
document.getElementById('myDiv').setAttribute('data-my-custom', 'custom value');

// 方法2：间接通过dataset属性
document.getElementById('myDiv').dataset.myCustom = 'custom value';

// 移除 disabled 属性
document.getElementById('myBtn').removeAttribute('disabled');

```



## 元素创建

```js
// document.createElement
// 创建一个指定标签名的 HTML 元素。
// 返回类型：一个HTMLElement 对象或者其具体的派生类型对象。
const divElement = document.createElement('div');
divElement.textContent="Hello World";
divElement.classList.add("class1");

// 最后 divElement 是：<div class="class1">Hello World</div>

// document.createDocumentFragment
// 创建一个轻量级的文档片段。
// 返回类型：一个新的 DocumentFragment 对象，一种特殊类型的 DOM 节点。
// 其他说明：DocumentFragment 对象，它不属于文档树，通常作为临时容器来存储多个元素。
// 当将文档片段插入到文档中时，文档片段中的所有子元素会被移动到目标位置，
// 而文档片段本身不会被插入到文档中。
const fragment = document.createDocumentFragment();
const newParagraph = document.createElement('p');
newParagraph.textContent = '这是新创建的段落。';
fragment.appendChild(newParagraph);

const parentDiv = document.getElementById('parentDiv');
parentDiv.appendChild(fragment);
console.log(fragment instanceof DocumentFragment); // 输出: true

// 使用 innerHTML 属性
document.getElementById('container').innerHTML = '<span>这是通过 innerHTML 创建的元素。</span>';


// 使用 insertAdjacentHTML 方法
const targetDiv = document.getElementById('targetDiv');

// 在目标元素之前插入内容
targetDiv.insertAdjacentHTML('beforebegin', '<p>在目标元素之前插入的段落</p>');

// 在目标元素内部的开始位置插入内容
targetDiv.insertAdjacentHTML('afterbegin', '<span>在目标元素内部开始位置插入的文本</span>');

// 在目标元素内部的结束位置插入内容
targetDiv.insertAdjacentHTML('beforeend', '<em>在目标元素内部结束位置插入的文本</em>');

// 在目标元素之后插入内容
targetDiv.insertAdjacentHTML('afterend', '<p>在目标元素之后插入的段落</p>');
```



## 元素插入到指定位置

```js
// 方法1：使用 appendChild 方法，将新元素添加到父元素的末尾
const newParagraph = document.createElement('p');
newParagraph.textContent = '新添加的段落';
const parentDiv = document.getElementById('parentDiv');
parentDiv.appendChild(newParagraph);


// 方法2：使用 insertBefore 方法，将元素插入到指定元素之前
const newParagraph = document.createElement('p');
newParagraph.textContent = '新添加的段落';

const parentDiv = document.getElementById('parentDiv');
const existingParagraph = document.getElementById('existingParagraph');

// 将新元素插入到参考元素之前
parentDiv.insertBefore(newParagraph, existingParagraph);

// 方法3： 参见元素创建中使用的 insertAdjacentHTML 方法


// 方法4：使用 insertAdjacentElement 方法
const newParagraph = document.createElement('p');
newParagraph.textContent = '新添加的段落';

const targetDiv = document.getElementById('targetDiv');
// 在目标元素之前插入新元素
targetDiv.insertAdjacentElement('beforebegin', newParagraph);
// 在目标元素内部的开始位置插入新元素
targetDiv.insertAdjacentElement('afterbegin', newParagraph);
// 在目标元素内部的结束位置插入新元素
targetDiv.insertAdjacentElement('beforeend', newParagraph);
// 在目标元素之后插入新元素
targetDiv.insertAdjacentElement('afterend', newParagraph);

```





## 元素删除

```js
// 使用 removeChild 方法 【推荐】，兼容性好
// 注意：removeChild 方法要求要删除的元素必须是调用该方法的元素的直接子元素

const parentList = document.getElementById('myList');
const itemToRemove = document.getElementById('itemToRemove');
parentList.removeChild(itemToRemove);


// 使用 remove 方法，HTML5 新增的方法
// 注意：在现代浏览器（如 Chrome、Firefox、Safari 等较新版本）中得到了很好的支持，
// 但在 Internet Explorer 中不支持
// 特点：它可以直接在元素上调用，无需通过父元素来删除自身。
document.getElementById('myDiv').remove();


// 使用 replaceWith 方法
// 注意：在现代浏览器（如 Chrome、Firefox、Safari 等较新版本）中得到了很好的支持，
// 但在 Internet Explorer 中不支持
// 特点：调用 replaceWith 时不传入任何参数(元素节点、文本节点)，
// 那么当前节点将会被移除，相当于删除该节点。
document.getElementById('toBeRemoved').replaceWith();
```





