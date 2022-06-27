# 浅析jQuery设计思想


学习了jQuery一段时间，对于jQuery的基本设计思想和主要用法的简单总结，就是“选择某个网页元素，然后对其进行简单的操作”。

记录一下最近学习了之后大概总结的一些用法。

# jQuery如何获取元素
---
### css选择器获取元素
```
$(document)//选择整个文档对象
$('#myId')//选择ID为myID的网页元素
$('div.myClass') // 选择class为myClass的div元素 $('input[name=first]') // 选择name属性等于first的input元素
```
### jQuery特有的表达式获取元素

```
$('a:first') //选择网页中第一个a元素
$('tr:odd') //选择表格的奇数行
$('#myForm :input') // 选择表单中的input元素
$('div:visible') //选择可见的div元素
$('div:gt(2)') // 选择所有的div元素，除了前三个
$('div:animated') // 选择当前处于动画状态的div元素

```

# jQuery的链式操作是怎样的
---
jQuery将最终选中的网页元素，对它进行一系列操作，并且所有的操作可以链接在一起，以链条的形式写出来，这就叫链式操作，比如：
```
$('.div').addClass('.red').text().find('h2')

```
能这样操作的原因是每一步的jQuery操作，返回的都是一个jQuery对象，所以不同的操作可以连在一起，这是jQuery最令人称道，也是最方便的特点。

### jQuery还提供了.end()方法，使结果集可以后退一步：

```
$('div')

　　　.find('h3')

　　　.eq(2)

　　　.html('Hello')

　　　**.end() //退回到选中所有的h3元素的那一步**

　　　.eq(0) //选中第一个h3元素

　　　.html('World'); //将它的内容改为World
```


# jQuery如何创建元素
---

```
$('<div>被创建的元素<div>')
$('<h2>被创建的元素<h2>')
$('<div><h2>被创建的元素</h2><div>')

```

# jQuery如何移动元素
---

```
insertAfter()和.after()：在现存元素的外部，从后面插入元素
.insertBefore()和.before()：在现存元素的外部，从前面插入元素
.appendTo()和.append()：在现存元素的内部，从后面插入元素
.prependTo()和.prepend()：在现存元素的内部，从前面插入元素

```

# jQuery如何修改元素的属性
---

```
　$('h1').html(); //html()没有参数，表示取出h1的值

　$('h1').html('Hello'); //html()有参数Hello，表示对h1进行赋值

```
也就是说，使用一个函数，来完成取值（getter）和赋值（setter）的两种操作。

常见的取值和赋值函数如下：

```
    .html() 取出或设置html内容
　　 .text() 取出或设置text内容
　　 .attr() 取出或设置某个属性的值
　　 .width() 取出或设置某个元素的宽度
　　 .height() 取出或设置某个元素的高度
　　 .val() 取出某个表单元素的值

```
**如果结果集包含多个元素，那么赋值的时候，将对其中的所有元素赋值。**

**取值的时候，则是只取出第一个元素的值（.text()例外，它取出所有元素的text元素）。**
