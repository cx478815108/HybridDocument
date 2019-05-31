# 工程文件模块化

> 实现原理
CSS 模块化使用了前端的[`postcss-import`](https://github.com/postcss/postcss-import)
html 模块化使用了[ `gulp-file-include`](https://github.com/haoxins/gulp-file-include)


## 导入html 模块

详细请参考[ `gulp-file-include`](https://github.com/haoxins/gulp-file-include)
编译器会根据你指定的入口文件，假如是`index.html` ，开始导入其他的模块。

假如你有如下模块

``` 
<!--view.html-->
<h1>view</h1>
```

``` 
<!--var.html-->
<label>@@name</label>
<label>@@age</label>
<label>@@socials.fb</label>
<label>@@socials.tw</label>
```
主入口文件如下

```
<div>
  <div>
  @@include('./view.html')         // 导入和'index.html'同目录下的view.html
  @@include('../var.html', {       // 导入'index.html'上级目录下的var.html
    "name": "haoxin",
    "age": 12345,
    "socials": {
      "fb": "facebook.com/include",
      "tw": "twitter.com/include"
    }
  })
  </div>
</div>
```

经过编译器处理后是

```
<div>
  <div>
      <h1>view</h1>
      <label>haoxin</label>
      <label>12345</label> 
      <label>facebook.com/include</label>
      <label>twitter.com/include</label>
  </div>
</div>
```

## 导入css 模块

在CSS 文件的开头使用 @import
详细请参考 [`postcss-import`](https://github.com/postcss/postcss-import)

```
@import "cssrecipes-defaults"; 
@import "normalize.css"; 
@import "foo.css"; 

body {
  background: black;
}
```


