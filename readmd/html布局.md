html布局
==

## float浮动
float设置元素浮动

* 可选值
    * none
        >默认不浮动，元素在文档流中
    * left
        >元素向左浮动
    * right
        >元素向右浮动
        
### 浮动元素的特点
* 元素浮动以后会完全脱离文档流
* 浮动以后元素会一直向父元素的最上方移动
* 直到遇到父元素的边框或者其他的浮动元素，会停止移动
* 如果浮动元素的上边是一个块元素，则浮动元素不会覆盖块元素
* 浮动元素不会超过他上边的浮动的兄弟元素，最多上边齐，水平方向上挤满了就往下排
* 浮动元素不会覆盖文字，文字会自动环绕在浮动元素的周围，可以通过浮动来实现文字环绕的效果
* **浮动的元素必须设置宽度才能生效**

#### 块元素浮动后特点
块元素脱离文档流后，
* 不会独占一行
* 宽度和高度都会被内容撑开

#### 内联元素浮动后特点
内联元素脱离文档流以后会变成浮动的块元素，特点同浮动块元素

**块元素、内联元素浮动后，都以 inline-block 显示**

### 浮动后其父元素高度塌陷问题的修复
```text
父元素在文档流中高度默认是被子元素撑开的，
当子元素脱离文档流以后，将无法撑起父元素的高度，
也就会导致父元素的高度塌陷

* 元素浮动带来的问题：
父元素的高度一旦塌陷所有元素的位置将会上移，导致整个页面的布局混乱
```
    
* 高度塌陷问题的修复方法1  
    在塌陷的父元素内容的最后添加一个空白的div，然后对该div进行清除浮动
    ```html
    <!-- 示例： -->
    <div class="box1">
        <div class="box2"></div>
        <div style="clear: both;"></div>
    </div>
    ```
    不足：页面中添加了多余的结构
    
* **高度塌陷、垂直相邻父子元素外边距重叠问题的修复方法2**  
    ```text
    在浮动的父元素上添加 class="clearfix"
    
    .clearfix:before  使用空的table标签可以隔离父子元素的外边距，阻止外边距的重叠，同时还能修复该元素之前塌陷问题
    .clearfix:after  高度塌陷修复，原理同方法1
    这样就相当于在父元素内容的收尾加了两条撑开线
    * 为什么display: 用talbe而不用block?
        * .clearfix:before问题：子元素和父元素相邻的垂直外边距会发生重叠，子元素的外边距会传递给父元素
            空block标签不能解决， 空table可以解决，因为添加的table后带有一个换行符
    ```
    
    * 优化版: 既解决高度塌陷，又确保父元素和子元素的垂直外边距不会重叠
        ```css
        .clearfix:before, 
        .clearfix:after {
            display: table;
            content: "";
            clear: both;
        }
        
        /* 
        针对IE 6
        不支持before、after伪类，则开启hasLayout功能来解决
        */
        .clearfix {
            *zoom: 1; /* 缩放比例 */
        }
        ```
    * [优化版详解示例](../source_08/day08/05.完善clearfix.html)
    
* 高度塌陷问题的修复方法3
    ```text
    开启父元素的BFC或hasLayout(IE 6解决方案)

    此解决方案不理想，有其他的弊端
    ```

    * Block Formatting Context：块级格式化环境
        ```text
        BFC是元素的隐含属性，默认是在关闭状态的

        * 开启BFC以后元素特点：
            父元素的垂直外边距不会与子元素重叠
            开启BFC的元素不会被浮动元素所覆盖
            开启BFC的元素可以包含浮动子元素
        
        * 开启BFC的方式
            - 设置元素浮动
            - 设置元素绝对定位
            - 设置元素的类型为inline-block
            - 设置overflow为一个非默认值，一般用 overflow: hidden; 来开启BFC
        ``` 
    * hasLayout
        ```text
        在IE6中没有BFC，但是有一个和BFC类似的hasLayout
        
        副作用最小的开启方式
            * zoom: 1;
            * 当为元素设置宽度非默认值时，会自动开启hasLayout
        ```

## position定位
position设置元素位置，可以将页面中的元素摆放到页面的任意位置

* 可选值
    * static
        >默认值，元素没有开启定位
    * relative
        >开启元素的相对定位
    * absolute
        >开启元素的绝对定位
    * fixed
        >开启元素的固定定位，也是绝对定位的一种

### relative相对定位
* 开启元素的相对定位后，如果不设置偏移量元素不会发生任何变化
* 相对定位元素相对于其自身在文档流中的位置来定位
* 相对定位的元素**不会脱离文档流**
* 相对定位不会改变元素的性质，块元素还是块元素，内联元素还是内联元素
* 相对定位的元素会提升一个层级，相当于上一层
```css
.box2 {
    position: relative;
    left: 200px;
    top: 100px;
}
```
[relative相对定位 示例](../source_07/day07/01.相对定位.html)

### absolute绝对定位
* 开启元素绝对定位以后，如果不设置偏移量，元素的位置不会发生变化
* 绝对定位的元素是**相对于距离它最近的开启了定位的祖先元素进行定位**，如果所有的**祖先元素都没开启定位**，则相对于**浏览器窗口**进行定位。
* 绝对定位的元素**会完全脱离文档流**
* 绝对定位会改变元素的性质。内联变块，块的高度和宽度都被内容撑开，并且不独占一行
* 绝对定位会使元素提升一个层级
```css
.box2 {
    position: absolute;				
    left: 100px;
    top: 100px;
}
```
[absolute绝对定位 示例](../source_07/day07/02.绝对定位.html)

### fixed固定定位
* **会完全脱离文档流**
* 固定定位是一种特殊的绝对定位，它的特点大部分都和绝对定位一样
* 不同的是，固定定位的元素永远都是相对于浏览器窗口进行定位的。并且它不会随滚动条滚动
* IE6不支持固定定位
```css
.box2 {
position: fixed;				
    right: 20px;
    bottom: 30px;
}
```
[fixed固定定位 示例](../source_07/day07/03.固定定位.html)

### 层级
* 定位元素 > 浮动元素 > 文档流中的元素
* 当元素开启了定位以后，可以通过z-index来设置元素的层级数，为整数
* z-index值越高元素越优先显示
* 如果z-index值一样，或者都没有z-index则优先显示下边的元素
* 父元素永远不会盖住子元素

### 偏移量
* 当元素开启了定位以后，可以通过偏移量来设置元素的位置
    * top  元素距离定位位置的上边距离
    * right  元素距离定位位置的右侧距离
    * bottom  元素距离定位位置的底部距离
    * left  元素距离定位位置的左侧距离
* 一般情况下，只使用两个值即可定义一个元素的位置。

### position定位使用总结
```text
以父元素为基准点(父元素的左上角这个点)，子元素都以基准点来绝对定位

一般给父元素，开启相对定位，不设置偏移量，
给子元素，开启绝对定位，设置相应的偏移量，各子元素分别指定层级
```

## 其他
### 如何使一个空的div占用空间
解决思路：给div设置高度（height）、溢出（overflow）属性

* style标签属性
    ```html
    <div style="width:100%; min-height:1px; overflow:hidden"></div>
    
    <!-- 或 -->
    <div style="width:100%; height:0; overflow:hidden; "></div>
    ```

* css样式
    ```css
    .empty-takes-space {
        min-height: 1px;
        overflow: hidden;
    }
    ```

### 实现div里的img图片水平垂直居中
html代码
```html
<body>
    <div class="flowerbox">
        <img src="/i/eg_tulip.jpg"  alt="上海鲜花港 - 郁金香" />
    </div>
</body>
```

* 方法1

    将display设置成table-cell，然后水平居中设置text-align为center，垂直居中设置vertical-align为middle
    ```css
    .flowerbox {
        width:150px;
        height: 100px;
        display: table-cell;
        vertical-align: middle;
        text-align: center;
        border:1px solid #000;
    }

    .flowerbox img {
        width: 50px;
        height: 50px;
    }
    ```

* 方法2
    ```
    通过position定位来实现。
    将div设置成相对定位relative，将img设置成绝对定位absolute，left:50%，top:50%，
    此时图片的左上角位于div的中心，
    要使图片的中心位于div的中心，就需要将图片向上移动图片高度的一半，并向左移动图片宽度的一半。
    ```
    ```css
    .flowerbox {
        width:150px;
        height: 100px;
        position: relative;
        border:1px solid #000;
    }

    .flowerbox img {
        width: 50px;
        height: 50px;
        position: absolute;
        top: 50%;
        left: 50%;
        margin-top: -25px; /* 高度的一半 */
        margin-left: -25px; /* 宽度的一半 */
    }
    ```
    
* 方法3：在不清楚图片或元素的真实宽高情况下
    ```
    还是通过position定位来实现。
    将div设置成相对定位relative，将img设置成绝对定位absolute，left:50%，top:50%，
    此时图片的左上角位于div的中心，
    要使图片的中心位于div的中心，就需要将图片向上移动图片高度的一半，并向左移动图片宽度的一半，
    如果不知道元素的宽高，可以用 transform: translate(-50%, -50%);
    ```
    ```css
    .flowerbox {
        width:150px;
        height: 100px;
        position: relative;
        border:1px solid #000;
    }

    .flowerbox img {
        width: 50px;
        height: 50px;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%); /* 也可以值指定一个值 transform: translate(-50%) 来调整 */
    }
    ```


* 方法4
    ```css
    .flowerbox {
        width:150px;
        height: 100px;
        position: relative;
        border:1px solid #000;
    }

    .flowerbox img {
        width: 50px;
        height: 50px;
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        margin: auto;
    }
    ```

* flex弹性布局
    ```css
        .flowerbox{
            width:150px;
            height: 100px;
            border:1px solid #000;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .flowerbox img {
            width: 50px;
            height: 50px;
        }
    ```
