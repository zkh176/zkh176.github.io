# HTML入门笔记



1.HTML 是谁发明的。

HTML是李爵士发明的。

2.HTML 起手应该写什么。

HTML的起手式的快捷键是！+TAB。表现出来的代码是

```html
<!DOCTYPE html>
<html lang="en">
<head> 
      <meta charset="UTF-8"> 
      <meta http-equiv="X-UA-Compatible" content="IE=edge"> 
      <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
      <title>Document</title> 
</head> 
<body> 
</body> 
</html>
```
其中DOCTYPE html指的是文件类型是html；html lang="en"指的是使用的语言是英文，改成中文的话把en改成zh-CN即可；文件的字符编码一定是UTF-8；title里面写的是网页的标题；其他的东西不要去改动他。

3.常用的表章节的标签有哪些，分别是什么意思。

常用的表章节的标签及意思分别是：

标题：h1~h6

章节：section

文章：article

段落：p

头部：header

脚部：footer

主要内容：main

旁支内容：aside

划分：div

4.全局属性有哪些。

全局属性有以下的：

class：给某个标签一个标记或者分类

contenteditable：使任何一个元素可以被编辑

hidden：加在标签里面可以让一个东西看不见

id：不到万不得已，不要用ID，因为ID不报错

style：每一个元素可以使用一个style元素，

tabindex:代表按tab时响应的顺序，正数按从小到大的顺序，0是最后一个，负数代表不会到这个词条上。

title：用来显示完整的内容。

5.常用的内容标签有哪些，分别是什么意思。

常用的内容标签及意思：

ol+li:有序列表

ul+li:无序列表

dl+dt+dd：description list简称dl里面是用来描述的对象和内容

pre：如果想要保留回车空格等，就用pre把内容包裹起来

hr：做分割线用的

br:用于强制换行

a:用来超链接

em:用来强调语气

strong:用来强调内容本身

code:用来在里面写代码

quote:引用某个东西

blockquote：可以换行的引用
