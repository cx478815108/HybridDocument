# 页面导航模块

App页面间导航可以使用`$nav` 对象

```
const item = {
    url:'xxx/xxx', // 页面的url
    animated:true, // 带push动画
    parameters:obj, // 传递到下一个页面的参数
    title:"下一个页面的标题"
}

$nav.push(item) // 打开下一个页面
$nav.pop(item) // 返回上一个页面，且无需带url参数
$nav.popToFirst(item) // 返回第一个页面，栈顶页面且无需带url参数

```

