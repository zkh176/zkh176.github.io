# JS函数的执行时机


## 解释下为什么以下代码会打印 6 个 6


```JS
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}

```

## 答案：
首先setTimeout的作用是等一会再执行打印，for循环会先进行执行，执行的最终结果为6，循环过程中i从0到6，一共执行了六次。因此打印结果为6个6。

## 让这个代码打印出 0、1、2、3、4、5 的方法

```JS
for(let i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}

```

## 除了使用 for let 配合，还有什么其他方法可以打印出 0、1、2、3、4、5

找到了两种答案：

### for in


```js
let arr=['a','d','e','f','g','q']
for(i in arr){
  console.log(i)
}

```

### 立即执行函数


```js
let i = 0
for (i = 0;i < 6; i++){
    !function (i) {
        setTimeout(() => {
            console.log(i)
        },0)}(i)
    }

```
