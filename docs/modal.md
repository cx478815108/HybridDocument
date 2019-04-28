# 弹出模态页面
本工程对弹出的模态页面也会进行预编译。
虽然提示用户下载成功，处理完成的通知可以使用JS API完成，但是仍然需要自定义整个弹出视图。

```
 .(TokenHybridCompiler)
└── welcome
    └── routers     // 子页面根文件夹
        └── second
            ...
    └── widgets     // 模态视图文件夹
        ├── alert.html   // 模态A面板
        ├── input.html   // 模态B面板
    
```

## 如何弹出模态面板？

```
// 弹出模态A面板
$native.showPanel({
                name:"alert",  // name 参数为文件的名字, alert.html 取alert
                finish:function () {
                    log('finish');
                }})
            
            
// 弹出模态B面板
$native.showPanel({
                name:"input",
                finish:function () {
                    log('finish');
                }})
```

## 如何取消模态面板？

```
$native.dismissPanel(()=>{
                log('dismissPanel finish');
})
```


