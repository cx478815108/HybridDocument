# label组件

> label组件是高性能的文本显示组件

使用方法

```
<label style="width: 100%;height: auto;background-color: rgb(20,120,130);font-size: 14px"" @click="buttonClick">{{name}}
</label>
```

## 支持设置的`Native`属性

| 属性 key         | 可选值                                           | 描述                              |
| ---------------- | ------------------------------------------------ | --------------------------------- |
| line-clamp       | 数字类型，单位:无 ,例如：2                       | 文本行数                          |
| color            | 字符串类型，接受rgb,rgba,16进制                  | 文本颜色                          |
| background-color | 字符串类型，接受rgb,rgba,16进制 如：rgb(200,0,0) | 组件的背景色                      |
| border-color     | 字符串类型，接受rgb,rgba,16进制                  | 组件的边框颜色                    |
| alpha            | 字符串类型，范围 0 - 1                           | 组件的透明度，0代表完全透明       |
| border-width     | 数字类型，单位:无 ,例如：2                       | 组件的边框宽度                    |
| border-radius    | 数字类型，单位:无 ,例如：8                       | 组件的圆角                        |
| z-index          | 数字类型，例如：1000                             | 组件的视图层级,越高越在最前面显示 |
| clip             | 数字类型，只接受1或者0                           | 组件的子视图是否超出自身范围可见  |
|font-size      |例如：14px                                                |字号                                             |
|                  |                                                  |                                   |
