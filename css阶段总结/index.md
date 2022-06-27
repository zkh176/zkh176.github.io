# CSS阶段总结


## CSS的渲染原理

-   浏览器渲染过程

步骤

1.  根据HTML构建HTML树（DOM）
1.  根据CSS构建CSS树（CSSDOM）
1.  将两棵树合并成一颗渲染树（RenderTree）
1.  Layout布局（文档流、盒模型、计算大小和位置）
1.  Paint绘制（把边框颜色、文字颜色、阴影等画出来）
1.  Compose合成（根据层叠关系展示画面）

\


-   CSS 动画的两种做法（transition 和 animation）

\


## transition

意思：过渡

作用：补充中间帧，给个秒数，会自动把中间帧补齐。

\


语法

transition：属性名、时长、过渡方式、延迟：

transition：left 200ms linear

可以用逗号分隔两个不同属性：

transition:left200ms,top 400ms;

可以用all代表所有属性

transition:all200ms;

过渡方式有：linear 丨ease丨ease-in丨ease-out丨ease-in-out丨cnic-bezier丨step-start丨step-end丨steps，具体含义要靠数学知识。

\


注意

并不是所有属性都能过渡

-   display：none=>block没法过渡
-   一般改成cisibility:hidden=>cisible（不要问为什么）
-   display和visibility的区别自己搜一下
-   bcakground颜色可以过渡吗？
-   opacity透明度可以过渡吗？（不推荐使用，容易出问题）

\


过渡必须要有起始

一般只有一次动画，或者两次，比如hover和非hover状态的过渡。

\


除了起始，还有中间点的话怎么办？

两种办法

-   使用两次traniform

.a===transform===>.b

.b===transform===>.c

如何知道到了中间点呢？

用setTimeout或者监听transitionend事件transition

意思：过渡

作用：补充中间帧，给个秒数，会自动把中间帧补齐。

\


语法

transition：属性名、时长、过渡方式、延迟：

transition：left 200ms linear

可以用逗号分隔两个不同属性：

transition:left200ms,top 400ms;

可以用all代表所有属性

transition:all200ms;

过渡方式有：linear 丨ease丨ease-in丨ease-out丨ease-in-out丨cnic-bezier丨step-start丨step-end丨steps，具体含义要靠数学知识。

\


注意

并不是所有属性都能过渡

-   display：none=>block没法过渡
-   一般改成cisibility:hidden=>cisible

过渡必须要有起始

一般只有一次动画，或者两次，比如hover和非hover状态的过渡。

除了起始，还有中间点的话怎么办？

两种办法

-   使用两次traniform

.a===transform===>.b

.b===transform===>.c

如何知道到了中间点呢？

用setTimeout或者监听transitionend事件。




## animation

作用：声明关键帧，添加动画。

缩写语法

1.  animation：时长、过渡方式、延迟、次数、方向、填充模式、是否暂停、动画名；
1.  时长：1s或者1000ms
1.  过渡方式：跟transition取值一样，如linear
1.  次数：3或者2.4或者infinte
1.  方向：reverse/alternate/alternate-reverse
1.  填充模式：none/forwards/backwards/both
1.  是否暂停：paused/running
1.  以上所有属性都有对应的单独属性


