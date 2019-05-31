# input组件

> input组件是文本输入组件

使用方法

```
<input style:"width: 200; height: 30" 
       borderStyle: line 
       align: center>
</input>
```

## 可用于input 的css 属性

所有div 的css 属性均支持

## 支持响应式的属性

| 属性 key    | 可选值             | 描述     |
| ----------- | ------------------ | -------- |
| borderStyle | 字符串类型：line   | 边框类型 |
| align       | 字符串类型：center | 对齐类型 |
| placeholder | 字符串类型        | 占位文本  |
| cursorColor | 字符串类型        | 占位文本  |
| align | 字符串类型        | 文本对齐方式  |
| secure | 布尔类型        | 是否用圆点显示，适合密码输入  |
| showClear | 布尔类型        | 是否显示清除按钮  |
| keyboardType | 数字类型   | 键盘类型  |
| returnType | 数字类型    | 键盘返回按钮类型  |
| colorModeType | 数字类型   | 键盘颜色类型  |

**注意**

> **borderStyle** , **keyboardType**, **returnType**, **colorModeType**, **align**
1. 如果被胡子语法绑定 必须绑定值是数字
2. 如果不被胡子语法绑定， 可以使用语义化的值，因为编译器会转化为数字


##### 举例: 不被胡子语法绑定

```
<input borderStyle = "line" ></input>
```

##### 举例: 被胡子语法绑定
```
<!--被胡子语法绑定-->
<input borderStyle = "{{style}}" ></input>

const app = {
    data(){
        return {
            style:1 // 必须是数字 或 ”1“
        }
    }
}

```

## 语义化的值和数字对应表
```
align 的语义化的值和数字对应如下
{
    "left"  : 0,
    "center": 1,
    "right" : 2
}

borderStyle 的语义化的值和数字对应如下
{
    "none"       : 0,
    "line"       : 1,
    "bezel"      : 2,
    "roundedRect": 3
}

keyboardType 的语义化的值和数字对应如下
{
    "default"     : 0,
    "ascii"       : 1,
    "numbers"     : 2,
    "emailaddress": 7,
    "decimalpad"  : 8,
    "websearch"   : 10,
}

returnType 的语义化的值和数字对应如下
{
    "default"      : 0,
    "go"           : 1,
    "google"       : 2,
    "join"         : 3,
    "next"         : 4,
    "route"        : 5,
    "search"       : 6,
    "send"         : 7,
    "yahoo"        : 8,
    "done"         : 9,
    "emergencycall": 10,
    "continue"     : 10
}

colorModeType 的语义化的值和数字对应如下
{
    "default": 0,
    "dark"   : 1,
    "light"  : 2,
}

```

## 事件处理

```
<!--绑定回调监听者-->
<input @listener = "inputListener"></input>
```

在JavaScript 中设置回调

```
const app = {
    listeners:{
        inputListener:{
            onBeginEditing(text){
                console.log("开始编辑了");
            },
            onTextChange(text){
                console.log("文本变化了");
            },
            onEndEditing(text){
                console.log("结束了编辑，通常是用户隐藏了键盘");
            },
            onReturn(text){
                console.log("用户点击了键盘上的 return 按钮");
            }
        },
    },
    data(){
        return {
            ...
        }
    }
}
```

## 使用DOM API

```
<!--绑定回调监听者-->
<input id = "myInput"></input>
```

```
const input = $native.el('myInput'); // id值
```

### API 列表
-------

可读可写

```
1. input.value       // 读取或者设置input 的文本
2. input.placeholder // 读取或者设置input 的占位文本
```

可调用的方法

```
input.beginEditing(); // 弹出键盘，获取焦点
input.endEditing();   // 关闭输入，让键盘消失
```


