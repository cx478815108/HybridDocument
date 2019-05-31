# div组件

> div组件是一个纯净的Native 视图组件

使用方法

```html
<div class = "pure" ></div>
```
## 点击事件
使用 `@click` 绑定点击事件

```
<div @click = "buttonClick()">
    按钮文本
</div>
```

## 可用于div 的css属性

```
label {
    background-color : rgb(255,0,0);  // 组件的背景色
    border-color : rgb(255,205,0);    // 组件的边框颜色
    border-width : 2px;               // 组件的边框宽度
    border-radius : 4px;              // 组件的边框圆角大小
    z-index : 10;                     // 组件的zindex
}
```

## 支持响应式的属性
可以使用胡子语法绑定该属性，直接使用js 修改
**注意**响应式的属性 颜色不支持 "red"等语义化的颜色表示，只能使用"rgb,rgba,16进制表示"

例如

```html
<div background-color = "{{myColor}}" hidden = "{{shouldShow}}"></div>
``` 

属性列表

| 属性key | 可选值 | 描述 |
| --- | --- | --- |
| background-color| 字符串类型，接受rgb,rgba,16进制 如：rgb(200,0,0)| 组件的背景色 |
| border-color| 字符串类型，接受rgb,rgba,16进制 | 组件的边框颜色 |
| alpha| 字符串类型，范围 0 - 1  | 组件的透明度，0代表完全透明 |
| border-width| 数字类型，单位:无 ,例如：2 | 组件的边框宽度 |
| border-radius| 数字类型，单位:无 ,例如：8| 组件的圆角 |
| z-index| 数字类型，例如：1000 | 组件的视图层级,越高越在最前面显示 |
| clip| 数字类型，只接受1或者0 | 组件的子视图是否超出自身范围可见|
| hidden| 数字类型，只接受1或者0 | 组件是否可见|
| disable| 数字类型，只接受1或者0 | 组件是否可以和用户交互|




