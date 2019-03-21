# image组件

> image组件是高性能的图片加载组件，支持GIF, PNG, JPEG, WEBP等格式
>
> 也支持设置点击事件的设置

使用方法

```
<image style:"width: 50%; height: 30%" src: www.xxxx.com contentMode: "scaleToFill" showActivity: "1"><image>
```

## 支持设置的`native`属性

| 属性 key     | 可选值                  | 描述           |
| ------------ | ----------------------- | -------------- |
| src          | 字符串类型              | 图片地址URL    |
| contentMode  | 字符串类型              | 图片拉伸等属性 |
| showActivity | 布尔类型，可选值"0" "1" | 加载菊花动画   |

```
contentMode 属性列表
 		"scaleToFill"    : 0,
    "scaleAspectFit" : 1,
    "scaleAspectFill": 2,
    "redraw"         : 3,
    "center"         : 4,
    "top"            : 5,
    "bottom"         : 6,
    "left"           : 7,
    "right"          : 8,
    "topLeft"        : 9,
    "topRight"       : 10,
    "bottomLeft"     : 11,
    "bottomRight"    : 12，
支持以上属性
```

