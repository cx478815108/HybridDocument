# image组件

> image组件用来加载图片，支持gif, png, jpeg, webp, apng格式
> 也支持设置点击事件的设置

使用方法

```
<image style = "width: 50%; height: 30%" 
       src = "www.xxxx.com/ava.png" 
       contentMode = "scaleToFill" 
       showActivity = "1">
<image>
```

> **src**
当src以http开头，会用网络加载图片
否则当做本地图片的路径进行加载

## 可用于image 的css属性

支持所有div 的css 属性


## 支持响应式的属性

| 属性 key     | 可选值                  | 描述           |
| ------------ | ----------------------- | -------------- |
| src          | 字符串类型              | 图片地址URL 或者直接设置本地图片   |
| highlighted-src | 字符串类型              | 高亮图片地址URL 或者直接设置本地图片   |
| contentMode  | 数字类型                | 图片拉伸和填充的方式 |
| showActivity | 布尔类型，可选值"0" "1"  | 是否加载菊花动画   |




**注意**
> **contentMode** 
1. 如果被胡子语法绑定 必须绑定值是数字
2. 如果不被胡子语法绑定， 可以使用语义化的值，因为编译器会转化为数字

##### 举例: 不被胡子语法绑定

```
<image contentMode = "scaleAspectFit" ></image>
```

##### 举例: 被胡子语法绑定
```
<!--被胡子语法绑定-->
<image contentMode = "{{mode}}" ></image>

const app = {
    data(){
        return {
            mode:1 // 必须是数字 或 ”1“
        }
    }
}

```

## 语义化的值和数字对应表

```
contentMode 对照表
{
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
    "bottomRight"    : 12,
}
```

## 使用DOM API
**所有div的DOM API 均可以使用**

特有API 

```
setImage(src)            // 设置图片
setHighlightedImage(src) // 设置高亮图片
stopAnimating();         // 停止播放动画
startAnimating();        // 开始播放动画图片
```

