CSS
==

## 概述
```text
Cascading Style Sheets，层叠样式表，
控制网页样式并允许将样式信息与网页内容分离的一种标记性语言。
CSS负责结构、表现、行为中的表现
如设置背景颜色、字体颜色、字体大小等
```

## css注释
块注释
```css
/* 注释内容 */
```

## css代码位置
### 元素内联style属性
只对当前标签起作用，不能对样式进行复用，不方便后期维护，不推荐使用
```html
<p style="color:red;"></p>
```

### head块内style标签
样式写到head块中的style标签中
进一步将表现和结构分离，可以同时为多个元素设置样式，方便后期的维护
```html
<head>
    <style type="text/css">
        p {
            color:red;
            background-color:yellow;
        }
    </style>
</head>
```

### 引入外部css资源
可以在不同的页面中使用同一个css文件，完全将表现和结构分离，方便后期的维护，推荐使用的方式

```html
<head>
    <link rel="stylesheet" type="text/css" href="css文件的相对路径 或 URL(如//bar.tmall.com/index.css)"/>
</head>
```

## 基本语法
### 选择器
通过选择器可以选中页面中的一组元素，然后为其设置样式  
可参考 http://jquery.cuishifeng.cn/

* 元素选择器  
    根据标签名，选中页面中的指定元素
    ```css
    标签名 {
        /* 样式 */
    }
    
    /* 示例 */
    div {
        font-size: 14px;
    }
    ```
* id选择器  
    根据元素的id属性值选中一个唯一的元素
    ```css
    #id {}

    #box1 {}
    ``` 
* 类选择器  
    根据元素的class属性值，选中一组元素
    ```css
    .class {}
    
    .box {}
    ``` 

* 选中页面中的所有元素  
    性能比较差，尽量避免使用
    ```css
    * {}
    ```
* 并集选择器  
    可以同时选中符合多个选择器的元素
    ```css
    选择器1, 选择器2, 选择器N {}
    
    div, p, #box, .hello {}
    ```
* 交集选择器  
    可以选中满足多个条件的元素
    ```css
    选择器1 选择器2 选择器N {}
    
    div p.hello {}
    ```
* 层级选择器
    * 后代元素选择器
        ```css
        祖先元素 后代元素 {}
        
        div span {}
        ```
    * 子元素选择器
        选中指定元素的指定子元素
        ```css
        父元素 > 子元素 {}
        
        div > p {}
        ```
    * prev + next
        ```text
        匹配跟在 prev 后的 next 这个兄弟元素
        ```
    * prev ~ siblings
        ```text
        查找与prev同辈的 siblings 所有兄弟元素（不包括prev）
        ```
* 属性选择器
```text
[attribute]
有属性attribute

[attribute=value]
attribute值 等于 value

[attribute!=value]
attribute值 不等于 value

[attribute^=value]
属性attribute名已value开头

[attribute$=value]
属性attribute名以value结尾

[attribute*=value]
属性attribute包含value

[attrSel1][attrSel2][attrSelN]
多个属性选择器为与关系，同时满足这些选择器
```

### css声明块
一个声明就是一个样式，以k:v键值对行使表示
```text
color: red;
font-size: 20px;
```

## 元素之间的关系
* 父元素  
    直接包含当前元素的的元素叫做父元素
* 子元素
    直接被当前元素包含的元素叫做子元素
* 祖先元素  
    直接或间接包含当前元素的元素叫做祖先元素，即父元素和父元素的父元素
* 后代元素  
    直接或间接被当前元素包含的元素叫后代元素，即子元素和子元素的子元素

* 兄弟元素  
    拥有相同父元素的元素叫做兄弟元素
    
## 块元素和内联元素
### 块元素
```text
块元素会独占页面中的一行，无论他的内容的多少
一般使用块元素对页面进行布局

* 常见的块元素:
    div
    p 
    h1~h6 
    table 
    form
```

### 内联元素
```text
内联元素也叫行内元素（inline）

内联元素只占用自身的大小，不会独占一行
一般内联元素都是用来为文本来设置效果

* 常见的内联元素
    span
    a
    img
    input
    button
```

### 包裹规则
* 一般都是使用块元素去包裹内联元素，而不会使用内联去包裹块元素
* a元素可以包含任意元素，除了a本身
* p元素不能包含任何块元素

## 伪类和伪元素
伪类用来表示元素所处的一个特殊的状态，伪元素用来表示元素所在的位置

* :link
    >表示一个普通的链接（未访问过的链接）
* :visited
    >表示访问过的链接
* :hover
    >鼠标移入的链接，也可以为其他元素设置hover
* :active
    >正在被点击的链接，也可以为其他元素设置active
* :focus
    >表示元素获取焦点的状态，一般用于文本框
* ::selection
    >表示内容被选中的状态，在火狐中使用::-moz-selection来代替
* :first-letter
    >表示第一个字符
* :first-line
    >表示文字的第一行
* :before
    >选中元素的innerHTML的最前边  
    一般该伪类都会结合content一起使用，通过content可以向指定位置添加内容
* :after
    >选中元素的innerHTML的最后边  
    一般该伪类都会结合content一起使用，通过content可以向指定位置添加内容