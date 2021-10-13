html-css
==

## Table Of Contents
#### html
* [html概述](readmd/html.md#html概述)
* [注释](readmd/html.md#注释)
* [网页结构](readmd/html.md#网页结构)
* [标签分类](readmd/html.md#标签分类)
* [属性](readmd/html.md#属性)
* [常用标签](readmd/html.md#常用标签)
* [文本标签](readmd/html.md#文本标签)
* [列表标签](readmd/html.md#列表标签)
* [图片标签](readmd/html.md#图片标签)
* [table表标签](readmd/html.md#table表标签)
    * [第一行colspan合并单元格后，设置td宽度失效的解决方法](readmd/html.md#第一行colspan合并单元格后设置td宽度失效的解决方法)
* [form表单](readmd/html.md#form表单)
* [input与textarea标签](readmd/html.md#input与textarea标签)
* [select下拉列表](readmd/html.md#select下拉列表)
* [base标签](readmd/html.md#base标签)
* [实体(转义字符)](readmd/html.md#实体转义字符)
* [相对路径](readmd/html.md#相对路径)
* [xHTML语法规范](readmd/html.md#xHTML语法规范)
* [IE版本判断](readmd/html.md#IE版本判断)
* [使用iframe代理一个网站](../source_08/day08/iframe全屏.html)
* 可跨站标签（可以引用站点之外的资源）
   * \<img>标签的src属性
   * \<script>标签的src属性
   * \<link>标签的href属性
   * css中的@import + 空格 + url(css文件路径地址);
   * 多媒体\<embed>标签的src属性

***

#### 盒子模式
* [概述](readmd/盒子模型.md#概述)
* [框的组成部分](readmd/盒子模型.md#框的组成部分)
    * [元素内容区(宽高)](readmd/盒子模型.md#元素内容区宽高)
        * [max最大min最小宽、高](readmd/盒子模型.md#max最大min最小宽高)
    * [内边距padding](readmd/盒子模型.md#内边距padding)
    * [边框border](readmd/盒子模型.md#边框border)
    * [外边距margin](readmd/盒子模型.md#外边距margin)
* [内联元素的盒子模型规则](readmd/盒子模型.md#内联元素的盒子模型规则)
* [盒模型相关的样式：display、visibility、overflow](readmd/盒子模型.md#盒模型相关的样式displayvisibilityoverflow)
* [文档流](readmd/盒子模型.md#文档流)

***

#### html布局
* [float浮动](readmd/html布局.md#float浮动)
    * [浮动元素的特点](readmd/html布局.md#浮动元素的特点)
        * [块元素浮动后特点](readmd/html布局.md#块元素浮动后特点)
        * [内联元素浮动后特点](readmd/html布局.md#内联元素浮动后特点)
    * [浮动后其父元素高度塌陷问题的修复 .clearfix](readmd/html布局.md#浮动后其父元素高度塌陷问题的修复)
* [position定位](readmd/html布局.md#position定位)
    * [relative相对定位](readmd/html布局.md#relative相对定位)
    * [absolute绝对定位](readmd/html布局.md#absolute绝对定位)
    * [fixed固定定位](readmd/html布局.md#fixed固定定位)
    * [层级](readmd/html布局.md#层级)
    * [偏移量](readmd/html布局.md#偏移量)
    * **[position定位使用总结](readmd/html布局.md#position定位使用总结)**
* [inline-block布局 vs 浮动布局](readmd/inline-block布局vs浮动布局.md)
    * [布局总结](readmd/inline-block布局vs浮动布局.md#总结)
* [其他](readmd/html布局.md#其他)
    * [如何使一个空的div占用空间](readmd/html布局.md#如何使一个空的div占用空间)
    * [实现div里的img图片水平垂直居中](readmd/html布局.md#实现div里的img图片水平垂直居中)

***

### flex弹性布局
* [什么是flex弹性布局](readmd/flex弹性布局.md#什么是flex弹性布局)
    * [怎么开启flex布局](readmd/flex弹性布局.md#怎么开启flex布局)
* [一、基本概念](readmd/flex弹性布局.md#一基本概念)
* [二、容器属性](readmd/flex弹性布局.md#二容器属性)
    * [2.1 flex-direction](readmd/flex弹性布局.md#2.1-flex-direction)
    * [2.2 flex-wrap](readmd/flex弹性布局.md#2.2-flex-wrap)
    * [2.3 justify-content](readmd/flex弹性布局.md#2.3-justify-content)
    * [2.4 align-items](readmd/flex弹性布局.md#2.4-align-items)
    * [2.5 align-content](readmd/flex弹性布局.md#2.5-align-content)
    * [flex-direction、justify-content、align-items结合](readmd/flex弹性布局.md#flex-directionjustify-contentalign-items结合)
* [三、项目属性](readmd/flex弹性布局.md#三项目属性)
    * [3.1 order属性](readmd/flex弹性布局.md#3.1-order属性)
    * [3.2 flex-grow属性](readmd/flex弹性布局.md#3.2-flex-grow属性)
    * [3.3 flex-shrink属性](readmd/flex弹性布局.md#3.3-flex-shrink属性)
    * [3.4 align-self属性](readmd/flex弹性布局.md#3.4-align-self属性)

***

#### CSS
* [概述](readmd/css.md#概述)
* [css注释](readmd/css.md#css注释)
* [css代码位置](readmd/css.md#css代码位置)
    * [元素内联style属性](readmd/css.md#元素内联style属性)
    * [head块内style标签](readmd/css.md#head块内style标签)
    * [引入外部css资源](readmd/css.md#引入外部css资源)
* [基本语法](readmd/css.md#基本语法)
* [常用选择器](readmd/css.md#常用选择器)
    * [css声明块](readmd/css.md#css声明块)
        * [css声明块特殊说明](readmd/css.md#css声明块特殊说明)
* [伪类、伪元素选择器](readmd/css.md#伪类和伪元素选择器)
    * [子元素的伪类选择器](readmd/css.md#子元素的伪类选择器)
    * [否定伪类选择器](readmd/css.md#否定伪类选择器)
        * [最后一个元素除外](readmd/css.md#最后一个元素除外)
* [选择器的优先级](readmd/css.md#选择器的优先级)
    * [优先级值](readmd/css.md#优先级值)
    * [优先规则](readmd/css.md#优先规则)
* [选择器的性能](readmd/css.md#选择器的性能)
* [元素之间的关系](readmd/css.md#元素之间的关系)
* [样式的继承](readmd/css.md#样式的继承)
* [块元素和内联元素特点](readmd/css.md#块元素和内联元素特点)
    * [块元素](readmd/css.md#块元素)
    * [内联元素](readmd/css.md#内联元素)
    * [包裹规则](readmd/css.md#包裹规则)
* [单位](readmd/css.md#单位)
    * [长度单位](readmd/css.md#长度单位)
    * [颜色单位](readmd/css.md#颜色单位)
    * [文本和字体单位](readmd/css.md#文本和字体单位)
        * [字体](readmd/css.md#字体)
        * [文本](readmd/css.md#文本)
* [背景](readmd/css.md#背景)
* 其他
    * [清除默认样式](source_10/polo-360/css/reset.css)
    * [清除a标签默认样式](readmd/css.md#清除a标签默认样式)
    * [IE6处理png问题](source_10/polo-360/js/DD_belatedPNG_0.0.8a-min.js)
    * [多个inline-block元素垂直方向居中](readmd/css.md#多个inline-block元素垂直方向居中)
    * [cursor光标样式](readmd/css.md#cursor光标样式)
    * [vertical-align属性](readmd/css.md#vertical-align属性)
