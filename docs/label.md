# label组件

> label组件是高性能的文本显示组件

使用方法

```
<label style="width: 100%;
       height: auto;
       background-color: rgb(20,120,130);
       font-size: 14px">
    {{name}}
</label>
```

## 点击事件
使用 `@click` 绑定点击事件

```
<div @click = "buttonClick()">
    按钮文本
</div>
```

### 可用于label 的css属性

同时支持所有div 的css 属性

**Tips:** 想要**背景为无色**可以按1,2设置，无色背景不会影响到文字颜色
1. `background-color : rgba(0,0,0,0);`
2. `background-color : none;`

```
label {
    line-height : 30px;  // 行高 css里面可以带px
    text-align : center;  // left, center, right
    font-size  : 14px;
    line-clamp : 2;
    color      : rgb(255,0,0); // 支持red blue 等语义化颜色
}
```

## 支持响应式的属性
可以使用胡子语法绑定该属性，直接使用js 修改

**注意**：响应式属性的值不要带px

属性列表

| 属性key | 可选值 | 描述 |
| --- | --- | --- |
| line-clamp| 数字类型，如：2| 文本显示的行数 |
| line-height| 数字类型，如：16 注意这里不带px | 文本行数的高 |
| text-align| 数字型，只接受 0,1,2|文本对齐方式，0左对齐，1居中对齐，2右对齐 |


