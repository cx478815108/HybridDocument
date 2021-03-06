# JavaScript 响应式功能

现有组件

```html
<div @bind = "app">
    <label>我是{{name}}<label>
</div>
```
现有JS脚本如下

```JavaScript
const app = {
    data(){
        return {
            name:"Alex"
        }
    }
}
// 将app注册为 可以使用@bind绑值为'app'的组件
const main = token.registComponent("app", app);
```

想要修改label的文字？
直接修改属性即可

```JavaScript
main.data.name = "Bob"
```

## 数组的响应式
!> 由于本框架自己写了一个`runtime.js` 观察JavaScript 的对象数据的更改，有一些不足之处
对数组整体的修改最好是重新赋值，不要调用数组的方法 例如 `[].reverce(),[].shift()`等。
但是对于数组的内部元素的修改 `list[2].name` 等修改是没有问题的。
哪位大神帮助一下实现`Proxy`对数组的完美拦截，得到数据路径？

## 使用JS 获取某个DOM元素，进而实现某些高级功能

> $native 对象是被注入到JavaScript运行环境的工具
 
### $native.el()
`$native.el("label")` 相当于浏览器`document.getElementById("label")`;

**例如开始动画功能**

```html

<div class = "root" @bind = "app">
    <scroll class = "scroll">
        <button class = "border" style = "width: 80px;height: 44px;margin-bottom: 20px;" @click = "buttonPressed">长度变化</button>
        <div id = "red" style = "background-color: rgb(220,0,0);margin-left: 20px;width: 40%;height: 100px;"></div>
        <div id = "green" style = "background-color: rgb(0,220,0);margin-top: 10px;margin-left: 20px;width: 40%;height: 100px;"></div>
    </scroll>
</div>

```

```JavaScript
const app = {
    methods:{
        buttonPressed(){
            let red = $native.el("red");
            let green = $native.el("green");
            let fast = red.animation({
                layout:{
                    width:"80%",
                    "background-color":"rgb(123,34,78)"
                },
                parameters:{
                    duration:2,
                    spring:1
                }
            })
    
            let slow = green.animation({
                layout:{
                    width:"70%",
                    height:"300px"
                },
                parameters:{
                    duration:0.25
                }
            })

            fast.commit().then(()=>{
                log("fast finish");
                slow.commit().then(()=>{
                    log("slow finish");
                })
            })

            
        }
    },
    data(){
        return {}
    }
}

token.registComponent("app", app);
```

