---
title: HTML学习笔记
date: 2018-04-26
tag:
  - html
  - css
category: HTML
---

- `<em>`表示强调，形式为斜体
- `<strong>`表示更加强调，形式为粗体
- `<span>`没有特殊语义，一般用于给单独文本加形式用

- `<q>` 引用标记，会自动加双引号
- `<blockquote>` 大段引用标记，浏览器会解析成缩进样式

- `<br />`是换行，不要使用`<br>`，虽然它也是有效的
- `<hr />`是水平线
- `&nbsp;`是空格，HTML是忽略空格和换行的，需要特殊的标记来显示

- `<address>`用来定义一个地址，默认样式为斜体
- `<code>`来标记一行代码
- `<pre>`来标记大段代码
- 无序列表`unordered list`
    ```
    <ul>
        <li>精彩少年</li>
        <li>美丽突然出现</li>
        <li>触动心灵的旋律</li>
    </ul>
    ```
- 有序列表`ordered list`
    ```
    <ol>
        <li>精彩少年</li>
        <li>美丽突然出现</li>
        <li>触动心灵的旋律</li>
    </ol>
    ```
- `<div>`用来划分不同的逻辑块

- `<table>`描述表格，其中`summary`字段显示表格摘要
    - `<caption>`表格标题
    - `<tbody>`用于划分块
    - `<tr>`标记一行数据
    - `<th>`用于描述顶部标题单元格
    - `<td>`用于描述表格普通内容单元格

- `<a>`超链接，`href`字段填写地址，`title`字段填写鼠标悬浮提示，`target`字段填为`_blank`时，将在新窗口打开链接
    - 发送邮件`<a href="mailto:收件人1;收件人2?cc=抄送人&bcc=密件抄送人&subject=邮件主题&body=邮件内容">`

- `<img>`图片标签
    - `src`标识图像的位置；
    - `alt`指定图像的描述性文本，当图像不可见时（下载不成功时），可看到该属性指定的文本；
    - `title`提供在图像可见时对图像的描述(鼠标滑过图片时显示的文本)；

- `<form>`表单标签
    - `method`数据传送方式(post/get)
    - `action`数据传送到的地方，如一个php页面(save.php)

- `<label>`文本标签
    - `for` 填写对应的`input`的`id`进行绑定

- `<textarea>`多段文本输入框
    - `cols` 列数
    - `rows` 行数

- `<input>`输入标签
    - `type`
        - `text` 普通文本框
        - `password` 密码文本框
        - `submit` 提交按钮
        - `reset` 重置按钮
        - `radio` 单选框
        - `checkbox` 复选框
    - `name`文本框名字
    - `value`文本框默认值
    - `id` 同一组的控件name要相同，但不同的控件id不同

- `<select>`下拉列表标签，配合`<section>`选项标签使用
    ```
    <select multiple="multiple">
        <option value="看书">看书</option>
        <option value="旅游">旅游</option>
        <option value="运动" selected="selected">运动</option>
        <option value="购物">购物</option>
    </select>
    ```
    
- `<link href="style.css" rel="stylesheet" type="text/css">`外链式css

- css选择器没有前缀是标签选择器，`.`是类`(class)`选择器，`#`是ID选择器
    ```css
    h1{
        color:blue;
    }
    .setGreen{
        color:green;
    }
    #stress{
        color:red;
    }
    ```

- 类选择器可以同时使用多个，id选择器不可以
    ```html
    <!--正确-->
    <p>到了<span class="stress bigsize">三年级</span>下学期时，我们班上了一节公开课...</p>
    
    <!--错误-->
    <p>到了<span id="stressid bigsizeid">三年级</span>下学期时，我们班上了一节公开课...</p>
    ```
    
- 子选择器`>`，类选择器下的扩展，如：
    ```css
    .first>span{border:1px solid red;}
    ```
    ```html
    <p class="first">三年级时，<span>我还是一个<span>胆小如鼠</span>的小女孩</span>，上课从来不敢回答老师提出的问题，生怕回答错了老师会批评我。就一直没有这个勇气来回答老师提出的问题。学校举办的活动我也没勇气参加。</p>
    ```

- 包含选择器` `，和子选择器不同的是会递归影响
    ```css
    .first span{border:1px solid red;}
    ```
    
- 通用选择器`*`，影响所有html里的标签元素
    ```css
    * {color:red;}
    ```
    
- `,` 可以用来间隔多个相同样式的选择器
    ```css
    .first,#second span{color:green;}
    ```

- 同时有多个css样式，按权值生效
    ```css
    p{color:red;} /*权值为1*/
    p span{color:green;} /*权值为1+1=2*/
    .warning{color:white;} /*权值为10*/
    p span.warning{color:purple;} /*权值为1+1+10=12*/
    #footer .note p{color:yellow;} /*权值为100+10+1=111*/
    ```
    
- 强制提升权值`!important`，不用再分号间隔
    ```css
    p{color:red!important;}
    p.first{color:green;}
    ```
- 文字排版
    - 设置字体 `body{font-family:"Microsoft Yahei";}`
    - 设置字号、颜色 `body{font-size:12px;color:#666}`
    - 设置粗体 `a{font-weight:bold;}`, 取消粗体a{font-weight:normal;}
    - 设置斜体 `p{font-style:italic;}`
    - 设置下划线 `p{text-decoration:underline;}`
    - 设置删除线 `.oldPrice{text-decoration:line-through;}`
    - 设置段首缩进 `p{text-indent:2em;}`
    - 设置行间距 `p{line-height:2em;}`
    - 设置字母间距 `h1{letter-spacing:20px;}`
    - 设置单词间距 `h1{word-spacing:50px;}`
    - 设置对齐方式 `div{text-align:center;}`

- 常用的块状元素有：
    `<div>、<p>、<h1>...<h6>、<ol>、<ul>、<dl>、<table>、<address>、<blockquote> 、<form>`

- 常用的内联元素有：
    `<a>、<span>、<br>、<i>、<em>、<strong>、<label>、<q>、<var>、<cite>、<code>`

- 常用的内联块状元素有：
    `<img>、<input>`

- 可以加入 `a{display:block}` 让元素显示为块状元素，特点：
    - 每个块级元素都从新的一行开始，并且其后的元素也另起一行。（真霸道，一个块级元素独占一行）
    - 元素的高度、宽度、行高以及顶和底边距都可设置
    - 元素宽度在不设置的情况下，是它本身父容器的100%（和父元素的宽度一致），除非设定一个宽度
    
- 可以加入 `a{display:inline}` 让元素显示为内联元素，特点：
    - 和其他元素都在一行上
    - 元素的高度、宽度及顶部和底部边距不可设置
    - 元素的宽度就是它包含的文字或图片的宽度，不可改变
    
- 可以加入 `a{display:inline-block}` 让元素显示为内联块状元素，特点：
    - 和其他元素都在一行上
    - 元素的高度、宽度及顶部和底部边距可以设置