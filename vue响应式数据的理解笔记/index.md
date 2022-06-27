# Vue响应式数据的理解笔记


---
theme: scrolls-light
---
[图片及部分文章参考出处](https://cn.vuejs.org/v2/guide/reactivity.html)


![data.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f63fde027a974a879b54724e27cad5ea~tplv-k3u1fbpfcp-watermark.image?)

# 响应式原理

数据响应式系统，其非侵入性的响应式系统，是vue最独特的特性之一。数据模型是被代理的JavaScript对象。而当修改它们的时候，视图就会进行更新。

当你把一个普通的 JavaScript 对象传入 Vue 实例作为 data 选项，Vue 将遍历此对象所有的 property，并使用 Object.defineProperty 把这些 property 全部转为 getter/setter。Object.defineProperty 是 ES5 中一个无法 shim 的特性，这也就是 Vue 不支持 IE8 以及更低版本浏览器的原因。

这些 getter/setter 对用户来说是不可见的，但是在内部它们让 Vue 能够追踪依赖，在 property 被访问和修改时通知变更。这里需要注意的是不同浏览器在控制台打印数据对象时对 getter/setter 的格式化并不同，所以建议安装 vue-devtools 来获取对检查数据更加友好的用户界面。

每个组件实例都对应一个 watcher 实例，它会在组件渲染的过程中把“接触”过的数据 property 记录为依赖。之后当依赖项的 setter 触发时，会通知 watcher，从而使它关联的组件重新渲染

由于 JavaScript 的限制，Vue 不能检测数组和对象的变化。尽管如此我们还是有一些办法来回避这些限制并保证它们的响应性


# getter和setter的用法

```javascript
const obj3 = {
  firstName: 'chen',
  lastName: 'shanqiong',
 get name() {
 return this.firstName + this.lastName
  },
 set name(name) {
 this.firstName = name[0],
 this.lastName = name.substring(1)
  },
  age: 18
}
obj3.name = '李四'; //相当于触发了setter函数
console.log("obj3的姓名：" + obj3.name) //obj3的姓名：李四
 //在方法名之前加一个get 这样不加括号也可以调用  
//getter就是在函数名前面加get 

```
* 需要注意的点
* get name()的写法，不要忘记加括号（ES6新语法）

## vue中数组的变异方法

Vue将被侦听的变更方法进行了包裹，所以它们也将会触发视图更新。这些被包裹的方法包括：
*   `push()`
*   `pop()`
*   `shift()`
*   `unshift()`
*   `splice()`
*   `sort()`
*   `reverse()`

### 变异园里的代码模仿实现

```javascript
class VueArray extends Array{
      push(...args){
            const oldLength=this.length  
           super.push(...args)
           for(let i=oldLength;i<this.length;i++){
                Vue.set(this,i,this[i])   //将每一个新增的key都告诉Vue
          }
      }
}

```

# 小结
Vue是以数据响应式为核心的UI框架，核心思想就是把所有的数据放到一个对象里，然后去操作对象，对象就会改变数据，监听这个改变从而改变UI，当然Vue不能检测到对象属性的添加或删除，如果一开始没有在Data上声明属性，就算你对这个属性做出更改，也不会更新UI。解决的方法是手动调用Vue.set或者this.$set(注意：此处的this等于vm）


