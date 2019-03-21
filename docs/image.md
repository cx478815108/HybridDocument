# image组件

> image组件是高性能的图片加载组件，支持GIF, PNG, JPEG, WEBP等格式
>
> 也支持设置点击事件的设置

使用方法

```
<image style:"width: 50%; height: 30%" src: www.xxxx.com contentMode: "6" showActivity: "1"><image>
```

## 支持设置的`native`属性

| 属性 key     | 可选值                      | 描述           |
| ------------ | --------------------------- | -------------- |
| src          | 字符串类型                  | 图片地址URL    |
| contentMode  | 字符串数字，支持 "0" - "12" | 图片拉伸等属性 |
| showActivity | 布尔类型，可选值"0" "1"     | 加载菊花动画   |

```
contentMode 属性列表 下面从 0 对应到 12
		UIViewContentModeScaleToFill,
    UIViewContentModeScaleAspectFit,      // contents scaled to fit with fixed aspect. remainder is transparent
    UIViewContentModeScaleAspectFill,     // contents scaled to fill with fixed aspect. some portion of content may be clipped.
    UIViewContentModeRedraw,              // redraw on bounds change (calls -setNeedsDisplay)
    UIViewContentModeCenter,              // contents remain same size. positioned adjusted.
    UIViewContentModeTop,
    UIViewContentModeBottom,
    UIViewContentModeLeft,
    UIViewContentModeRight,
    UIViewContentModeTopLeft,
    UIViewContentModeTopRight,
    UIViewContentModeBottomLeft,
    UIViewContentModeBottomRight,
```

