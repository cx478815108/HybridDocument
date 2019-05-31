# button组件

> button组件是能够相应用户状态的按钮组件

使用方法

```
<button style:"width: 100%; 
        height: auto; 
        src:"www.xxxxx.com/xxxx.photo"; 
        highlighted-src:"www.xxx.com/highlightphoto"; 
        contentMode:"www.xxx.com/highlightphoto"; ">
    按钮文本
</button>
```

**注意：**按钮也可以显示图片，但是显示图片后不会显示文字。

## 点击事件
使用 `@click` 绑定点击事件

```
<button @click = "buttonClick()">
    按钮文本
</button>
```

## 可用于button 的css属性

所有css 属性

## 支持响应式的属性

| 属性 key          | 可选值                          | 描述             |
| ----------------- | ------------------------------- | ---------------- |
| src               | 字符串类型，图片url             | 图片             |
| highlighted-src   | 字符串类型，高亮图片url         | 高亮图片         |
| contentMode       | 字符串类型                      | 图片填充方式     |
| showActivity      | 字符串类型                      | 是否显示加载菊花 |
| text-align        | 字符串类型                       | 对齐方式|
| color             | 字符串类型，接受rgb,rgba,16进制 | 文本颜色         |
| highlighted-color | 字符串类型，接受rgb,rgba,16进制 | 高亮文本颜色     |

## 注意

button组件的 contentMode值可以设置为如下的

```
非响应式 可以使用语义化的值，因为编译器会自动转为数字
<button contentMode:"scaleAspectFit">
    按钮文本
</button>

contentMode响应式属性的值只能为数字
<button contentMode:"{{modeValue}}"> // modeValue 只能是数字 scaleToFill对应0 bottomRight对应1
    按钮文本
</button>
```



```
"scaleToFill",
"scaleAspectFit",
"scaleAspectFill",
"redraw",
"center",
"top",
"bottom",
"left",
"right",
"topLeft",
"topRight",
"bottomLeft",
"bottomRight",
```


