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
        匹配跟在 prev 后为 next 的next这个兄弟元素
        prev与next为同级
        ```
    * prev ~ siblings
        ```text
        查找与prev同辈的兄弟元素中为siblings的元素 （不包括prev）
        prev与siblings为同级
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
### 子元素的伪类
* :first-child
* :last-child
* :nth-child(n|even|odd|formula)
    ```text
    n
    匹配子元素序号
    必须为整数，注意从1开始而不是0
    
    even
    匹配所有偶数元素
    
    odd
    匹配所有奇数元素
    
    formula
    使用特殊公式如(an + b)进行选择. 
    例如:nth-of-type(3n+2) 从第二个具此标签元素开始，匹配每个3的倍数的元素
    ```
* :first-of-type
* :last-of-type
* :nth-of-type(n|even|odd|formula)，参数同nth-child
 
### 否定伪类
* :not(选择器)
    >如：.abc:not(div)

## 样式的继承
* 为祖先元素设置样式，会同时应用到它的后代元素上，这一特性称为样式的继承。
* 通过样式的继承可以将一些样式统一设置给祖先元素，这样所有的后代都会应用到相同的样式。
* 但是并不是所有的样式都会继承，比如：背景相关的，边框相关的，定位相关的。具体参考文档

## 选择器的优先级
### 优先级值
* 内联样式：1000
* id选择器：100
* 类和伪类选择器：10
* 元素选择器：1
* 通配选择器：0
* 继承的样式：没有优先级

### 优先规则
* 当样式发生冲突时，需要将相关的选择器优先级进行求和计算，优先级高的优先显示，如果优先级一样，则显示靠后的样式
* 优先级计算时，总大小不能超过他的最大的数量级
* 可以在样式后边添加一个!important获取最大的优先级
```text
div {
    color: #f00 !important;
}
div {
    color: #000;
}
如果样式中添加了该内容，则该样式将会获取最大的优先级，
将会优先于所有的样式显示，包括内联样式，但是这个属性要慎用。
```

## 选择器的性能
* 浏览器在解析一组选择器时，是从后边往前一个一个的解析的
* 如果选择器编写过于长的话，浏览器解析起来性能会比较差，所以在编写选择器时，越短越好。
* *通配选择器，性能也比较差，要避免使用通配选择器

## 单位
### 长度单位
* px
    >一个像素指的就是一个像素点，不同的显示器中，一个像素的大小是不同的，越清晰的屏幕像素越小  
    绝对大小
* %
    >百分比，如20%
* em
    >相对于当前对象内文本的font-size的倍数
* rem
    >相对于根元素<html>的font-size的倍数

### 颜色单位
* 颜色单词
    >red green blue orange
* RGB值  
    语法
    ```text
    rgb(红色, 绿色, 蓝色)
    这三个值需要一个0-255之间的值
    也可以使用百分数来设置RGB值，需要0%-100%之间的值
    ```
* 十六进制RGB值
    16进制数字来表RGB值
    语法
    ```text
    #红色绿色蓝色
    值范围：[00, FF]
    
    如果颜色的是两位两位重复的，可以进行简写为一个字符
    比如 #BBFFAA 可以写成 #BFA
    ```
### 文本单位
#### 字体
* color
* font-size
* font-family 字体
* font-style
* font-weight
* font-variant
* font
```text
字体的简写属性，可同时设置字体所有相关的样式

* 语法
    font: [加粗 斜体 小大字母] 大小[/行高] 字体;
    
    * 加粗，斜体，小大字母，顺序无所谓，写不写都行，如果不写使用默认值
    * 文本大小，和字体必须写，且大小必须是倒数第二个，字体必须是最后一个
    * 大小后可以设置行高，可写可不写，如果不写则使用默认值
```

#### 文本

