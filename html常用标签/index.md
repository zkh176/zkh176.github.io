# HTML常用标签


## 一.a 标签的用法

a标签现在学到的有三种用法：

1.helf：

是hyper跟reference的缩写，意思是超链接或者超级引用。

### helf的取值有：

```
 <a href="//google.com">超链接</a>
 <a href="index.html">以文件夹为路径的链接</a>
 <a href="javascript:alert(1);">伪协议，用来写一个什么都不做的a标签，分号冒号用的都是英文符号</a>
```

2.target：

用属性指定在何处显示链接的资源：

_blank：在新标签页打开对应链接

_top：在顶层页面打开对应链接

_parent：在上一级区域打开对应链接。

_self：在当前页面打开对应链接（默认值）

示例：

```
    <a href="https://baidu.com" target="_blank">xxx网址</a>
    <a href="https://baidu.com" target="_top">xxx网址</a>
    <a href="https://baidu.com" target="_parent">xxx网址</a>
    <a href="https://baidu.com" target="_self">xxx网址</a>
```

3.download
理论上是用来下载网页，但是实际上很多浏览器不支持，知道就好。

## 二.img标签的用法

-   作用：发出get请求，展示一张图片。
-   属性：alt（输入当图片加载失败时出现的东西）/height（高）/width（宽）/src（图片地址）
-   注意：不要同时写宽和高，会使图片变形，绝对不要是图片变形
-   事件：onload/inerror：两者用来表示图片加载成功或者失败时显示的样式，后者可加入备用图片用以图片显示失败时可以使用

示例：

```
    <img src="dog.png" alt="">
    <script>
        xxx.onload = function () {
            console.log(图片加载成功)
        }
        xxx.onerror = function () {
            console.log(图片加载失败)
        }
    </script>
```

\


### 三.table 标签的用法

现在table常用的只有thead、tbody、tfoot三个标签，三个标签写的顺序跟网页表现出来的顺序没关系，html会自动排列顺序。

使用的主要元素有：

tr：意思是table row，table里面的一行。

th：意思是表格内的表头单元格。

td：意思是一个包含数据的表格单元格。

示例：

```
    <table>
        <thead>
            <tr>
                <th>英语</th>
                <th>翻译</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>hyper</td>
                <td>超级</td>
            </tr>
            <tr>
                <td>target</td>
                <td>目标</td>
            </tr>
            <tr>
                <td>reference</td>
                <td>引用</td>
            </tr>

        </tbody>

        <tfoot>
            <tr>
                <td>空</td>
                <td>空</td>
            </tr>
        </tfoot>
    </table>
```

table的style：在head里面写入style输入需要修改格式的对应代码，然后在{}里输入下列对应属性可以简易更改table的样式。

table-layout： CSS属性定义了用于布局表格单元格，行和列的算法。

auto：根据表格内容算出对应的宽度。

fixed：等宽列出表格内容。

border-collapser：一般后面属性跟collapse，用来合并表格边框。

border-spacing:一般后面跟多少像素，用来表示边框的空隙有多大。

```
 <style>
        table {
            width: 600px;
            table-layout: auto;
            border-spacing: 0px;
            border-collapse: collapse;
        }

        td,
        th {
            border: 1px solid blue;
        }
    </style>
```

### 四.其他感想

在学习的过程中，感到光是听课记笔记其实是没有太过于直观的印象，所以现在我把每一堂课的所有属性标签全部写成代码，保存至本地，以便之后自己随时查阅，希望这个能对我学习前端知识有帮助。
