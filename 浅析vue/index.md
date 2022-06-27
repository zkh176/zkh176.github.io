# 浅析Vue


# Vue的两个版本
### vue有两个版本，分别是完整版（Vue.js）和非完整版（vue.runtime.js），两者的区别：

![1jpg.jpg](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/838b926fcce44de1959f80b0c9c457b3~tplv-k3u1fbpfcp-watermark.image?)

两个版本推荐使用非完整版，然后配合vue-loader和vue文件使用。

# template 和 render 怎么用

## 用template——html的方式做渲染

完整版的vue必须使用template。

用创建一个加1的代码举例：

```
new Vue({
  data: {
    n: 0,
  },
  template: `
  <div id="app">
  <p>{{ n }}</p>
  <button @click="add">+1</button>
  </div>
  `,
  methods: {
    add() {
      this.n += 1;
    },
  },
}).$mount('#app');

```

## render——js的方式做渲染

非完整版需要用render写法，用 const h = creatElement创建一个标签。
用同样的代码举例：
```
new Vue({
  el:'#app',
  data:{
    n:0,
  },
  
  //用js创建一段HTML
  render(h){
    return h('div',[
      this.n,
      h(
        'button',
        {
          on:{
            click:this.add, 
             },
          },
          '+1',
        ),
    ]);
  },
  methods:{
    add(){
      this.n +=1;
    },
  },
});
```

# 有时候人在外面没电脑，但是急需要写个vue代码，怎么办呢？
## 用codesandbox.io就可以很方便的写代码。

**第一步**
![微信截图_20220215185635.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/363b13896c074a8b85ec324124d37d4f~tplv-k3u1fbpfcp-watermark.image?)
点击Vue图标就可以直接创建。
tips：不要登录，登录了就只能用50个demo，不创建就能一直用。

**第二步**
![2.png](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a0a6dcda0ddf44879928d29fff283137~tplv-k3u1fbpfcp-watermark.image?)
直接再界面进行操作和编辑。


**第三部**
如果想下载就可以点击左上角的file然后点击 Export to ZIP就可以导出写的代码啦。
