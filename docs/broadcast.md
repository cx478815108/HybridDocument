# 跨页面通信

跨页面通信有两种方式
1. 使用$storage存储，但是效率低，需要访问磁盘
2. 使用广播

在把不同的页面可以注册同一个频道的广播

```
const broadcast = $native.getBroadcast(channelName) // channelName 字符串


broadcast.onReceiveMessage((msg)=>{
    console.log('收到了消息',msg);
})

broadcast.postMessage(data) // data是 字符串或者 json 对象
```




