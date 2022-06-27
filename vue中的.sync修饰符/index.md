# Vue中的.sync修饰符


# 为什么用.sync修饰符

当一个子组件改变了一个 prop 的值时，这个变化也会同步到父组件中所绑定。如果我们不用.sync，我们想做上面的那个弹窗功能，我们也可以props传初始值，然后事件监听，实现起来也不算复杂。这里用sync实现，只是给大家提供一个思路，让其明白他的实现原理，可能有其它复杂的功能适用sync。

## 实例代码

```
<div id="app">
    <div>{{bar}}</div>
    <my-comp :foo.sync="bar"></my-comp>
    <!-- <my-comp :foo="bar" @update:foo="val => bar = val"></my-comp> -->
</div>
<script>
    Vue.component('my-comp', {
        template: '<div @click="increment">点我+1</div>',
        data: function() {
            return {copyFoo: this.foo}
        },
        props: ['foo'],
        methods: {
            increment: function() {
                this.$emit('update:foo', ++this.copyFoo);
            }
        }
    });
    new Vue({
        el: '#app',
        data: {bar: 0}
    });
</script>
```

代码<my-comp :foo.sync="bar"></my-comp>会被扩展成<comp :foo="bar" @update:foo="val => bar = val"></comp>，就是一个语法糖。
