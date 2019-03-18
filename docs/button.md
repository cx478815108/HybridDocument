# button组件

> button组件是能够相应用户状态的按钮组件

使用方法

```
<button style:"width: 100%; height: auto; src:www.xxxxx.com/xxxx.photo; highlighted-src:www.xxx.com/highlightphoto; contentMode:xxxxx; ">xx</button>
```

## 支持设置的`native`属性

| 属性 key          | 可选值                          | 描述             |
| ----------------- | ------------------------------- | ---------------- |
| src               | 字符串类型，图片url             | 图片             |
| highlighted-src   | 字符串类型，高亮图片url         | 高亮图片         |
| contentMode       | 字符串类型                      | 图片填充方式     |
| showActivity      | 字符串类型                      | 是否显示加载菊花 |
| text              | 字符串类型                      | 按钮文字         |
| text-align        |                                 | 对齐方式         |
| color             | 字符串类型，接受rgb,rgba,16进制 | 文本颜色         |
| highlighted-color | 字符串类型，接受rgb,rgba,16进制 | 高亮文本颜色     |

其他通用属性请参考div