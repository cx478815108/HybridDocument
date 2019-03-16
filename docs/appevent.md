# App事件介绍

现有如下App

```html
<div @bind = "app">
    <label>我是{{name}}<label>
</div>
```
## App事件如下

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

App({
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
    onExit(){
        log("App即将销毁");
    }
})

```



