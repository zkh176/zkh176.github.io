# JaJS对象基本用法


## 1.声明对象的两种语法

-   对象的定义

1.  无序的数据集合。
1.  键值对的集合。

-   写法

1.正规的写法：let 对象名=new Object({'键名（属性名）':'键值（属性值）'})

```
let obj = new Object ({'name':'xxx'})
```

2.简易写法：

```
let obj = {'name':'xxx','age':'xx'}
```

-   细节

1.  键名是字符串，不是标识符，可以包含任意字符。
1.  引号可以省略，省略之后就只能写标识符，但是数字也可以所谓开头。
1.  就算引号省略了，键名还是字符串。没有数字键名，没有数字下标。

***

## 2.如何删除对象的属性

-   delete obj.xxx或delete obj['xxx']

1.  即可删除obj的xxx属性。
1.  请区分【属性名为undefined】和【不含属性名】

\


-   不含属性名

'xxx' in obj == false

\


-   含有属性名，但是值为undefined

'xxx' in obj && obj.xxx ===undefined

\


-   注意obj.xxx === undefined

不能断定'xxx'是否为Obj的属性，要判断属性必须用in obj。

\


## 3.如何查看对象的属性

### 3.1、查看自身所有属性

Object.keys(obj):用来查看所有属性名

Object.values(obj):用来查看所有属性值

\


-   查看自身+共有属性

1.  console.dir(obj)
1.  或者自己依次用Object.keys打印出obj.__proto__（不推荐）

\


-   判断一个属性是自身的还是共有的

obj.hasOwnProperty('toString')

是自身的话会返回true，是共有的会返回false。

\


### 3.2、查看对象的某一个属性

-   两种方法查看属性

1.  中括号语法：obj['key']
1.  点语法：obj.key
1.  坑新人语法：obj[key]//变量key值一般不为'key'

## 4.如何修改或增加对象的属性

### 4.1、赋值

-   直接赋值

```
et obj = {name:'frank'}//name是字符串
obj.name = 'frank'// name是字符串
obj ['name'] = 'frank'
obj[name] = 'frank'//错，因为name值不确定。
obj['na'+'me'] = 'frank'
let key ='name'; obj[key] = 'frank'
let key = 'name';obj.key = 'frank'//错，因为obj.key等价于obj['key']
```

-   批量赋值

```
object.assign(obj,{age:18, gender:'man'})
```

### 4.2、修改或增加共有属性

-   无法通过自身修改或增加共有属性

```
let obj = {},obj2 = {}//共有toString
obj.toString = 'xxx'只会改obj自身属性。
```

obj2.toString还是在原型上。

-   我偏要修改或增加原型上的属性

```
obj.__proto__.toString = 'xxx'//不推荐用__proto__。
Object.prototype.toString = 'xxx'
```

一般来说，不要修改原型，会引起很多问题。

-   修改隐藏属性

```
let obj = {name:'frank'}
let obj2 = {name:'jack'}
let common = {kind:''human}
obj.__proto__ = common
obj2. __proto__ = common
```

不推荐使用__proto__

```
let obj = Object.create(common)
obj.name = 'frank'
let obj2 = Object.create(common)
obj2.name = 'jack'
```

推荐使用Object.create。

## 5.'name' in obj和obj.hasOwnProperty('name') 的区别

in和Object.hasOwnProperty()都可以用来检测对象中是否具有某个属性，它们最主要的区别在于前者不光检测当前对象，还会检测当前对象原型链中是否具有这个属性，后者只在当前对象自身上检测。

\


\
