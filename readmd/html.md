html
==


## html概述
```text
HTML:Hyper Text Markup Language 超文本标记语言

负责页面中的结构，定义出页面中的各个组成部分
HTML是采用纯文本的形式的编写，采用HTML标签来标识出页面中的不同部分
```

## 注释
块注释
```html
<!-- 注释内容 -->
```

## 网页结构
* 三个组成部分
```text
    * 结构
        结构是页面的整体结构，哪里是标题，哪里是段落，哪里是图片
        结构使用HTML来编写
    * 表现
        表现是页面的外在的样式，比如字体，字体大小，字体颜色，背景... ... 
        使用CSS来设置页面中元素的样式
    * 行为


一个设计优良的网页要求结构、表现、行为三者分离
在开发中总是要面临一个问题，就是程序之间的耦合，三者分离就是为了解耦合
```

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <!-- 网页主体 -->
</body>
</html>
```

## 标签分类
* 成对标签
    ><标签名></标签名>
* 自结束标签
```text
<标签名/>
后面的/也可以省略

<img>
<input>
<link>
<br>
<hr>
```

## 属性
标签中的设置的键值对，多个属性之间使用空格分隔
```text
<标签名 属性名="属性值" 属性名="属性值"></标签名>

<标签名 属性名="属性值" 属性名="属性值" />
```

* 文档声明
    ```html
    <!doctype html>
    标识当前页面的html的版本，以上的是html 5版本
    ```
    
## 常用标签
```text
<html>  网页根元素，一个网页文件只能有一个
<head>
<body>
<h1> - <h6>
<p>
<br />
<hr />
```

* 内联框架iframe  
    使用内联框架可以引入一个外部的页面  
    内联框架中的内容不会被搜索引擎所检索，所以开发中尽量不要使用内联框架
    
    ```html
    <iframe src=""></iframe>
    ```
    * 属性
        * src
        * width
        * height
        * name
            ```text
            可以为内联框架指定一个名字
            可以将该属性值设置为超链接的target属性的值
            这样当点击超链接时，页面将会在相应的内联框架中打开
            ```
* frameset框架集
    ```text
    框架集和内联框架的作用类似，都是用于在一个页面中引入其他的外部的页面，
    框架集可以同时引入多个页面，而内联框架只能引入一个，
    在h5标准中，推荐使用框架集，而不使用内联框架
    frameset和iframe一样，它里边的内容都不会被搜索引擎所检索，
    
    属性：
        rows，指定框架集中的所有的框架，一行一行的排列
        cols， 指定框架集中的所有的页面，一列一列的排列
        这两个属性frameset必须选择一个，并且需要在属性中指定每一部分所占的大小
    frameset中也可以再嵌套frameset
    ```
    [frameset框架集示例](../source_08/day08/07.框架集.html)  
            
* 超链接
    ```
    <a href="">连接的文本</a>
    ```
    * 属性
    * href
        ```text
        指向链接跳转的目标地址
        还可以是#id属性值，这样当点击超链接以后，将会跳转到当前页面的指定位置
        可以使用mailto:来创建一个发送电子邮件的超链接
        ```
    * target
        * _self  默认值，当前窗口打开链接
        * _blank  新窗口打开链接
        * 内联框架的name属性值  在指定的内联框架中打开链接
[meta标签示例](../source_02/demo/01_meta.html)
        
## 文本标签
```html
<em></em>  表示语气上的强调，斜体显示

<strong></strong>  表示强调的内容，表示内容的重要性，加粗显示

<i></i>  斜体

<b></b>  加粗

<u></u>  下划线

<del></del>  删除线，表示要删除的内容

<small></small>  表示细则一类的内容

<cite></cite>  表示参考的内容，凡是用书名号的都可以用cite

<q></q>  短引用，行内引用

<blockquote></blockquote>  长引用，块级引用

<sup></sup>  上标

<sub></sub>  下标

<ins></ins>  插入的内容

<pre></pre>  预格式，可以保留代码中空格、换行等这些格式

<code></code>  表示程序代码

```

## 列表标签
* ul无序列表
    ```html
    使用ul来创建一个无序列表，在列表中使用li来表示一个列表项
    无序列表使用符号作为项目符号
    通过type属性可以修改无序列表的项目符号
        可选值：
            disc  默认值，实心的圆点
            square  实心的方块
            circle  空心的圆
    
    示例：
    <ul>
        <li></li>
        <li></li>
        <li></li>
    </ul>
    ```
* ol有序列表
    ```html
    使用ol来创建一个无序列表，在列表中使用li来表示一个列表项
    使用有序的序号作为项目符号
    type属性，可以指定序号的类型
        可选值：
            1  默认值，使用阿拉伯数字
            a/A  小写或大写字母作为序号
            i/I  小写或大写的罗马数字作为序号
    示例：
    <ol>
        <li></li>
        <li></li>
        <li></li>
    </ol>
    ```
* dl自定义列表
    ```html
    dl中有两个子标签
        dt  被定义的内容
        dd  对定义内容的描述
    示例：
    <dl>
        <dt>景点</dt>
            <dd>杭州西湖</dd>
            <dd>天涯海角</dd>
        <dt>城市</dt>
            <dd>汉城</dd>
            <dd>深圳</dd>
    </dl>
    ```
    效果图:  
    ![](../images/dl示例.png)  
    
* 列表相关的元素都是块元素，他们之间可以互相嵌套
* 去除项目符号
  >list-style: none;

## 图片标签
```html
<img />

属性：
    src  图片路径或URL
    alt  在图片无法加载时对图片的描述，搜索引擎主要通过该属性来识别图片的内容，不写该属性则搜索引擎会对图片进行收录
    width
    height
```

## table表标签
table是块元素

* 子标签
```html
<tr></tr>  一行，可写多行
<td></td>  一列，一个单元格
<th></th>  表头中的一列，它的用法和td一样，不同的是它会有一些默认效果（加粗）

<thead></thead>  表头，有默认样式，永远会显示在表格的头部
<tbody></tbody>  表体，永远都会显示表格的中间
<tfoot></tfoot>  表底部，永远都会显示表格的底部
以上三个标签都可以省略不写

如果表格中没有写tbody，浏览器会自动在表格中添加tbody
并且将所有的tr都放到tbody中，所以注意tr并不是table的子元素，而是tbody的子元素
通过table > tr 无法选中行 需要通过tbody > tr


```
* 属性
    ```text
    border  边框
    border-spacing  table和td边框之间默认有一个距离
    border-collapse: collapse;  设置表格的边框合并，border宽度为0，如果设置了边框合并，则border-spacing自动失效
    border-spacing: 长度;  相邻单元格的边框间的距离，仅border-collapse: separate; "边框分离"模式时生效
    rowspan="n"  由此单元格纵向向下合并n个单元格
    colspan="n"  由此单元格横向向右合并n个单元格
    ```
    示例：
    ```css
    div table {
        width: 300px;
        margin: 0 auto;
        border-collapse: collapse; /* 合并表格边距 */
    }
    
    td, th {
        border: 1px solid black;
    }
    ```

```html
<table>
    <thead>
        <tr>
            <th>日期</th>
            <th>收入</th>
            <th>支出</th>
            <th>合计</th>
        </tr>    
    </thead>
    
    <tfoot>
        <tr>
            <td></td>
            <td></td>
            <td>合计</td>
            <td>100</td>
        </tr>
    </tfoot>  
      
    <tbody>
        <tr>
            <td>10.24</td>
            <td>500</td>
            <td>300</td>
            <td>200</td>
        </tr>
        <tr>
            <td>10.25</td>
            <td>600</td>
            <td>200</td>
            <td>400</td>
        </tr>
    </tbody>
</table>
```

## 实体(转义字符)
```text
语法：
&实体名;
```

* 常用实体
    ```html
    空格  &nbsp;
    <  $lt;
    >  &gt;
    版权符号  &copy;
    ```

## 相对路径
相对于当前资源所在的目录的路径
```text
./  表示当前路径，可以省略
../  上一层目录，可以使用多层
```

## xHTML语法规范
* HTML中不区分大小写，但是尽量使用小写
* HTML的注释不能嵌套
* 标签必须结构完整，要么成对出现，要么是自结束标签
* 标签可以嵌套但是不能交叉嵌套
* 属性必须有值，且值必须加引号，单引号双引号都可以




