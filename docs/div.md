# div组件

> div组件是一个纯净的Native 视图组件

使用方法

```html
<div class = "pure" ></div>
```

## 支持设置的`Native`属性
当我们想要div组件禁止和用户交互可以使用 `disable` 
例子 `<div class = "pure" disable = "1"></div>` 这样就不会有点击事件的传递了

div的`Native` 属性是所有组件都可以设置的，也就是`label,button,scroll,webview`等都可以设置

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




