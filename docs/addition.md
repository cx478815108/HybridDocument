## 关于Flex 布局的说明

**整个框架都是使用Flex布局，如果你不熟悉，这里有一个[playground](https://yogalayout.com/playground/)可以供你练习。**

**flex布局的学习可以参考[这里](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)**

**特别说明：**

```
1. 不支持margin:0 auto;的写法，事实上浏览器内部在解析的时候也是将0解析为margin-left:0px;margin-right:0px;margin-top:0px;margin-bottom:0px;所以需要拆开写；
2. 暂时不支持font 的写法，需要拆分为font-size:xxx font-family:xxx;这样的写法
3. 支持对于margin和padding 支持margin:0px; margin:4px 4px;这样的写法，因为编译器做了处理。
```

## 关于文本内容不显示的问题

* 有可能是给label 或者button 组件的宽高太小，无法容纳文本造成的。
* **本框架已经尽力向CSS 标准靠拢了，由于需要将xml 属性解析后给native 组件设置，所以这些差异性的存在难以避免。在以后的版本中，将会尽量抹掉。**

