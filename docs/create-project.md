# 创建工程
## 1. 示例程序解释

> 我们约定客户端每个可见的最大范围称之为页面。

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
    "title":"小程序示例",
    "entryJS": "index.js",
    "exportZipName":"example",
    "bundle.identifier":"com.token.example.demo",
    "displayName":"示例"
}

```


