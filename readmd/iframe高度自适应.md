iframe高度自适应
==

## iframe内容未知，高度可预测

示例
```js
<script type="text/javascript">
    // document.domain = "caibaojian.com";

    // iframe 高度自适应
    function setIframeHeight(iframe) {
        if (iframe) {
            var iframeWin = iframe.contentWindow || iframe.contentDocument.parentWindow;
            if (iframeWin.document.body) {
                iframe.height = iframeWin.document.documentElement.scrollHeight || iframeWin.document.body.scrollHeight;
            }
        }
    }

    window.onload = function () {
        setIframeHeight(document.getElementById('dg_index'));
    };
</script>
```

如果在同个顶级域名下，不同子域名之间互通信息，设置document.domain="caibaojian.com" 只要修改以上的iframe的ID即可了。

```html
<iframe src="backtop.html" frameborder="0" scrolling="no" id="external-frame" onload="setIframeHeight(this)"></iframe>
```
建议使用window.onload，这样避免污染HTML代码


## 