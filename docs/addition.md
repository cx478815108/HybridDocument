## 框架的技术原理

## 编译过程
编译器会读取开发者的`html,css`文件

1. 首先利用工具`gulp-file-include`合并`html`，`postcss-import`合并`css` 文件。生成一个`main.html, main.css`；
2. 再用`rollup`打包`js`文件，生成`main.js`文件
3. 开始真正的编译过程，读取用步骤一的文件，用`JavaScript`生成一颗渲染树。
4. 分析渲染树上`{{}}`绑定的数据
5. 将渲染树保存为`production.json`文件，此时已经没有`html,css`等文件了

## 客户端渲染过程

1. 读取安装包内`production.json`文件，生成Native 的渲染树，避免了`HTML, CSS `的解析
2. 开始对渲染树进行遍历，从根节点遍历到子节点，遍历过程中根据节点`tagName`创建`Native`组件，并设置各种信息
3. 启动`JavaScriptCore`执行安装包内`main.js` 文件

## 客户端如何创建Native 组件

```
<div class="card">
      <label class="card__cardno">文本1</label>
      <label class="card__bankno">文本2 </label>
    <image class="card__qrcode icon" src="images/qrcode.png"></image>
</div> 


1. 客户端从根遍历，首先创建 div 对应的Native 组件，再遍历div 的子节点
2. 创建label 组件，设置渲染的文字：'文本1'，并添加到div组件的子组件
3. 创建label 组件，设置渲染的文字：'文本2'，并添加到div组件的子组件
4. 创建image 组件，设置渲染的图片，并添加到div组件的子组件
```

**因此：组件的遮挡问题，和谁在谁上面的问题，你需要知道，节点层次越深，越在最上层显示**

## 关于Flex 布局的说明

**不熟悉Flex布局，可以阅读Flex的[学习文档](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)，这里还有一个[playground](https://yogalayout.com/playground/)可以供你练习。**

**特别说明：**

```
1. 不支持margin:0 auto;的写法，事实上浏览器内部在解析的时候也是将0解析为margin-left:0px;margin-right:0px;margin-top:0px;margin-bottom:0px; 所以需要拆开写；
2. 暂时不支持font 的写法，需要拆分为font-size:xxx;font-family:xxx;这样的写法
3. 支持对于margin和padding 支持margin:0px; margin:4px 4px;这样的写法，因为编译器做了处理。
```

## 关于文本内容不显示的问题

* 有可能是给label 或者button 组件的宽高太小，无法容纳文本造成的。
* **本框架已经尽力向CSS 标准靠拢了，由于需要将xml 属性解析后给native 组件设置，所以这些差异性的存在难以避免。在以后的版本中，将会尽量抹掉。**

