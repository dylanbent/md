title: 《你不知道的javaScript》上卷 · this
date: 2016-03-04 08:59:24
tags: Web
---

> 关于this的讨论，将结合《你不知道的javaScript》一书,围绕this的作用，this的误解与this是什么，this的绑定展开

+ this的作用
    - this 提供了一种更优雅的方式来隐式“传递”一个对象引用，因此可以将API设计得更加简洁并且易于复用；也就是我们可以通过apply, call，bind等方法来指定我们this，从而传递了一个隐式对象引用，而不是显式传递，这样做更加函数更加灵活

+ this的误解与this是什么
    - this 不是指向函数自身
    - this 不是指向函数的作用域
    - this 是运行时绑定的，这与作用域是编译时确定的不同。this的绑定和函数声明的位置没有关系，只取决于函数的调用方式。当一个函数被调用时，会创建一个活动记录(执行上下文)，这个记录会包含函数在哪里被调用，函数的调用方式等信息，this就是记录其中的一个属性，在函数执行的过程中用到
    - 总之，this实际上是在函数被调用时发生的绑定，它指向什么完全取决于函数在哪里被调用
    
+ this的绑定规则
    - 函数是否在 new 中调用（ new 绑定）？如果是的话 this 绑定的是新创建的对象。
    -  函数是否通过call、apply（显式绑定）或者硬绑定调用？如果是的话， this 绑定的是指定的对象。
    -  函数是否在某个上下文对象中调用（隐式绑定）？如果是的话， this 绑定的是那个上下文对象。
    -  如果都不是的话，使用默认绑定。如果在严格模式下，就绑定到 undefined ，否则绑定到全局对象。