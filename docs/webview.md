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

## API 列表

#### 1. 请求加载网页

```
web.load(request); // 加载网页

参数：request  
说明：Object 对象
举例：
{
    "url":"https://xxx.xx",
    "ignoreCache" : "0"              // 0代表忽略本地网络请求的缓存 可以不设置，
    "timeout":"30",                     // 请求超时设置为30s,可以不设置,
    "header": {                            // 可以不设置
        "key1","val1"                    // 自定义的请求头信息,
        "Set-Cookie":"xxxxxxx"   // 设置cookie 信息
    }
}
```
#### 2. 重新加载

```
web.reload(); // 重新加载
```

#### 3. 渲染html文本字符串

```
web.loadHTML(htmlText);  

参数：htmlText  
说明：HTML 文本，类型为字符串
```

#### 4. 让webView 执行js 语句

```
web.eval(js, success, failure)

参数 js ,js 文本, success:成功回调, failure:失败回调
举例：

web.eval('alert("弹框")', (result)=>{
    // 成功回调
},(error)=>{
    // 失败回调
})

```

#### 5. 让webView 加载自定义资源

```
webview 加载自定义的资源都是通过scheme 实现的，
比如有这样的一个标签
<imag src="customScheme://www.test.com/test.jpg">

需要首先
web.addCustomURLScheme('customScheme'); 告诉webview 自定义了一个scheme

那么如何返回自定义数据给webview 呢？
需要你在webview 的事件回调中实现如下的方法
 onHandleCustomScheme(schemeURL){
    // 以下3个字段必不可少
   const data = {
       result: 1,            // 告诉webview 你自定义的数据请求被处理了
       body: "最好是base64字符串"，
       mimetype :"image/jpeg"  // 查w3c mimetype
   }
   return data;
}

```
#### 6. webView postMessage 处理

当webview内的网页 运行的时候，可能会有`js` 调用`native` 的功能，但是这里的`native `相当于引擎

```
window.webkit.messageHandlers.<方法名>.postMessage(<数据>)
```

如何响应这个来自webview内部js的调用呢？

```
首先你要注册对应的方法名
比如 window.webkit.messageHandlers.sayHello.postMessage('cx');
你应该在onLoad里面就注册
webView.addBridge('cx')，告诉webview 可以处理这个postMessage;

最会在'native'里面实现执行逻辑
onReceiveBridgeMessage(messageName){
    // webview 内部js调用了postMessage 方法名是 messageName
    console.log(messageName);
}
```

#### 7. 其他 API

```   
1. web.goBack()                                  // 返回上一页
2. web.goForward()                             // 前进一页
3. web.stopLoading()                          // 停止加载
4. web.enableHeaderRefresh(value)  // 是否开启下拉刷新
5. web.enableFooterRefresh(value)   // 是否开启上拉加载更多功能
6. web.title                                         // 获取网页的标题
7. web.progress                                // 获取加载的进度
8. web.url                                          // 获取当前网页的url
```






