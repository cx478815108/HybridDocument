# 创建工程
> 我们约定客户端每个可见的最大范围称之为页面。

#### 工程文件解释
假如使用`TokenHybrid` 调试工具在demo文件夹📂创建工程你会得到如下的目录结构

 ```
demo
├── assets           //（资源文件夹） 该文件夹会被整个拷贝，你可以在此存放各种图片，或者webview加载可能用到的文件
├── mainPage
    ├── index.html   // (UI 界面描述文件,入口html文件)
    ├── index.js     // (js 脚本)
    ├── index.css    // (入口 css脚本)
    ├── config.json  //（App工程配置文件）
    └── modalPages   // 该目录下存放弹出的页面 全部为.html文件 使用js api 弹出，名字为文件的名称
    
├── otherPage
    └── secondPage   // 这是第二个页面 页面的URL 为 (secondPage)
        ├── index.html   
        ├── ...      
        └── config.json    
├── dist       // 编译后的文件存放地址
└── production // 编译后的zip 文件存放地址 

 
 ```


!> 注意config.json 文件不能删除 是每个页面的配置文件

```
config.json 
{
    "title":"小程序示例",
    "entryJS": "index.js", // 入口js 文件名
    "entryCSS":"index.css",  // 入口css 文件名
    "entryHTML":"index.html",  // 入口html 文件名
    "navBar.style": "black", // 设置状态栏为黑色 (电池，信号那一栏) 
    "navBar.color": "rgb(255,255, 255)" // 设置导航栏的颜色
    "navBar.shadowline": "true" // 显示导航栏下面的黑线
}

```


