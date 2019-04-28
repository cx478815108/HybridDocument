# App事件介绍

现有如下App

```html
<div @bind = "app">
    <label>我是{{name}}<label>
</div>
```
## App生命周期如下

在正确的生命周期中做正确的事情，十分重要

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

token.appLife({
    onLaunch(){
        log("即将开始渲染该App");
    },
    onLoad(){
        log("界面元素创建完毕，相当于前端的window.onload");
    },
    willShow(obj){
        log("即将显示该App的界面");
    },
    didShow(){
        log("开始已经显示完毕");
    },
    willDisappear(){
        log("页面即将不可见");  
    },
    didDisappear(){
        log("页面已经不可见");
    },
    onPanelLoad(obj){
        log("App modal 面板出现渲染完毕");
    }
})

```



