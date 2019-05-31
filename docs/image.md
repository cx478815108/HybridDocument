# image组件

> image组件用来加载图片，支持gif, png, jpeg, webp格式
> 也支持设置点击事件的设置

使用方法

```
<image style:"width: 50%; height: 30%" 
        src:"www.xxxx.com/ava.png" 
        contentMode: "scaleToFill" 
        showActivity: "1">
<image>
```

## 可用于image 的css属性

支持所有div 的css 属性


## 支持响应式的属性

| 属性 key     | 可选值                  | 描述           |
| ------------ | ----------------------- | -------------- |
| src          | 字符串类型              | 图片地址URL 或者直接设置本地图片   |
| highlighted-src | 字符串类型              | 高亮图片地址URL 或者直接设置本地图片   |
| contentMode  | 数字类型                | 图片拉伸等属性 |
| showActivity | 布尔类型，可选值"0" "1"  | 是否加载菊花动画   |


## 注意

image组件的 contentMode值可以设置为如下的

```
非响应式 可以使用语义化的值，因为编译器会自动转为数字
<image contentMode:"scaleAspectFit">
    按钮文本
</image>

contentMode响应式属性的值只能为数字
<image contentMode:"{{modeValue}}"> // modeValue 只能是数字 scaleToFill对应0 bottomRight对应1
    按钮文本
</image>
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

