# webview组件

> webview组件是网页视图组件，下拉刷新和上拉刷新参考scroll组件用法


## 可用于webview 的css属性

所有div 组件的属性均支持

## 支持响应式的属性
可以使用胡子语法绑定该属性，直接使用js 修改

属性列表

| 属性key | 可选值 | 描述 |
| --- | --- | --- |
| preview| 布尔类型| 是否允许长按webview出现预览|
| selection| 布尔类型| 是否允许webview选择|
| showMenu| 布尔类型| 是否允许弹出 3d-touch预览|
| scale| 布尔类型| 是否允许webview缩放|


## 事件处理

```
<!--绑定回调监听者-->
<webview @listener = "webListener"></webview>
```

| 事件回调函数 | 说明 |
| --- | --- |
| onStart()   | webview开始加载 |
| onFinish()   | webview加载结束 |
| onError(reason)   | webview加载发生错误 |
| onReceiveBridgeMessage(message)| webview的js 调用了postMessage |
| onHandleCustomScheme(schemeURL)| 根据的自定义的scheme数据协议，返回数据 |

在JavaScript 中处理事件回调

```
const app = {
    listeners:{
        webListener:{
            onStart(){
                console.log("webView开始加载");
            },
            onHandleCustomScheme(schemeURL){
                // 以下3个字段必不可少
               const data = {
                   result: 1, // 告诉webview 你自定义的数据请求被处理了
                   body: "最好是base64字符串"，
                   mimetype :"image/jpeg" // 查w3c mimetype
               }
               return data;
            },
            onReceiveBridgeMessage(message){
                // webview 内部js调用了postMessage
                console.log(message);
            }
            ...
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
<webview id = "webView"></webview>
```

```
const web = $native.el('webView'); // id值
web.reload(); // 重新加载
```

API 列表

```
1. web.reload(); // 重新加载
2. web.loadHTML(htmlText); // 加载html文本
3. web.eval(js, success, failure)
   
   web.eval("alert('hello')", ()=>{
        // 执行成功回调
    }, ()=>{
        //执行失败回调
   })
   
4. web.addBridge(name) // 增加一个webview 内部postMessage的属性
5. web.addCustomURLScheme(scheme) // 增加一个自定义资源加载的scheme
6. web.goBack() // 返回上一页
7. web.goForward() // 前进一页
8. web.stopLoading() // 停止加载
9. web.enableHeaderRefresh(value) // 是否开启下拉刷新
10. web.enableFooterRefresh(value) // 是否开启上拉加载更多功能
11. web.title // 获取网页的标题
12. web.progress // 获取加载的进度
13. web.url // 获取当前网页的url
```






