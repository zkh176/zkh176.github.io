# MVC小结


# MVC三个对象分别做什么？

**MVC（Model View Controller）是一种架构模式。分为M、V、C三个部分。**

**M：model，数据层（数据模型），负责操作所有的数据。**

**V：view，视图层，负责所有UI界面，是提供给用户的操作界面，是程序的外壳。**

**C：controller，控制层，负责格局用户从“视图层”输入指令，选取“数据层中的数据”，对其进行相应的操作（绑定事件等），然后产生最终结果。**

这三层是紧密联系在一起的，但是又相互独立，每一层内部的变化不影响其他层。每一层都对外提供接口，供上面一层调用。

这样一来，软件就可以实现模块化，修改外观或者变更数据都不用修改其他层，大大方便了维护和升级。

关于MVC，事实上没有一个明确的定义，每个前端对其理解都会有些许偏差，我理解的MVC是将代码结构化的一种抽象的概念，比如说：

## Model数据层
```
//示例
let Model = {
  data: { 数据源 },
  create: { 增加数据 },
  delete: { 删除数据 },
  update(data) {
    Object.assign(m.data, data); //用新数据替换旧数据
    eventBus.trigger("m:update"); //eventBus触发'm:update'信息，通知View刷新界面
  },
  get: { 获取数据 },
};
```

## View视图层
```
//示例
let View={
    el:要刷新的元素，
    html：'要显示在页面上的刷新内容'
    init(){
        v.el:初始化需要刷新的元素
    }，
    render(){
        刷新页面
    }
}

```

## Controller控制层
```
let Controller={
    init(){
        v.init()//初始化View
        v.render()//第一次渲染页面
        c.autoBindEvents()//自动的事件绑定
        eventBus.on('m:update',()=>{v.render()}//当enentsBus触发'm:update'是View刷新
    }，
    events:{事件以哈希表的方式记录存储},
    //例如：
   events: {
    'click #add1': 'add',
    'click #minus1': 'minus',
    'click #mul2': 'mul',
    'click #divide2': 'div',
    },
    add() {
      m.update({n: m.data.n + 1})
    },
    minus() {
      m.update({n: m.data.n - 1})
    },
    mul() {
      m.update({n: m.data.n * 2})
    },
    div() {
      m.update({n: m.data.n / 2})
    },
    method(){
        data=新数据
        m.update(data) // controller 通知 model去更新数据
    },
    autoBindEvents(){
    	for (let key in c.events) { // 遍历events表，然后自动绑定事件
      const value = c[c.events[key]]
      const spaceIndex = key.indexOf(' ')
      const part1 = key.slice(0, spaceIndex) // 拿到 'click'
      const part2 = key.slice(spaceIndex + 1)  // 拿到'#add1'
      v.el.on(part1, part2, value)
    }
}

```

# EventBus 有哪些 API，是做什么用的

**前面提到MVC三层是紧密联系在一起的，又互相独立的，每一层内部的变化不影响其它层。当层与层之间需要通信时，这时就需要EventBus，它主要用于组件之间的监听与通信。**

```
eventBus.trigger('m:updated') //触发事件 

eventBus.on('m:updated',()=>{ //监听事件
     v.render(m.data.n)
 })
 eventBus.off('m:updated')//取消监听

```

# 表驱动编程是做什么的？

## 为什么会出现表驱动编程？

随着逻辑复杂性的增加，if/else或switch中的代码变得越来越臃肿，代码可读性不强，所谓的表驱动程序，指的是把一大堆的if...else...这样的逻辑进行处理，从而转化成从一个hash表中查找kry--value对的过程。

# 模块化的理解
## 这里的模块化指的是前端模块化，模块化也是MVC的重要前提。它把相对独立的代码从一大段代码里抽取成一个个小模块，每个模块之间相对独立，这样也方便日后的维护。

ES6的语法里引入了import和export，就是用来实现模块化：

```
export default c; // 默认导出
export { c }; // 另外一种导出方式。记得要加花括号
```
# 划分模块的一个准则是「高内聚、低耦合」

**高内聚**，是指一个软件模块是由相关性很强的代码组成，只负责一项任务，也就是常说的单一责任原则。

**低耦合**，是指模块之间的联系越少越好，接口越简单越好，实现低耦合，细线通信。

如果各个模块之间接口很复杂，说明功能划分有不合理之处、模块之间的耦合太高，同时也说明单个模块的内聚不高。

