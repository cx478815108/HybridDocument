# 创建工程
## 1. 示例程序解释

> 当我们用词App的时候，其实也是一个页面，个人倾向于把页面也称呼为App，只不过它只有一个页面

#### 文件解释

你会看到编译器根目录下的 `welcome`文件夹

 ```
 .(TokenHybridCompiler)
└── welcome
    ├── index.html   (UI 界面描述文件)
    ├── index.js     (js 脚本)
    ├── index.css    (这个就不解释了哈)
    └── config.json （App配置文件）
 
 ```
>  关于多个JS，CSS文件
 
 ```
 当我们想要创建一个App的时候 通常包括html js css 这三个文件。
 你可以在welcome 文件夹下有任意多个css文件，每个css文件都会生效。
 因为编译器会自动递归搜寻 welcome 目录包括子文件夹下的所有css 文件
 编译器也会对JS 文件进行同样的操作
 ```

!> 注意config.json 文件必不可少

```
config.json 
{
    "title":"我是界面标题",
    "entryJS": "example",  // js 主入口文件
    "entryJSON":"production" // 这个固定就行
}
```

## 2. 根目录project.json

```
{
    "projects":[
        {
            "projectId": "welcome",         // 一个App工程的Id，建议同名
            "exportZipName": "welcome",      // 打包后的zip文件名，这个非常重要
            "EnteryHTMLName" : "index.html", //编译器编译入口的html文件
            "projectFolderName":"welcome",   // 整个App文件夹的名字
            "version":"1.0.1"                //版本
        }
    ],
    "debugReloadZipNames" : ["welcome"],  //UI 调试工具重载App列表 注意是zip名
    "debugCompileProjects": ["welcome"],  //UI 调试工具编译目录列表
    "currentProject":"welcome"           // 编译器当前编译目录
}
```


