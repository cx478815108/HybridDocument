# list组件

> list组件是高性能的大列表加载组件，具有组件重复利用，渐进加载的特点

**list 会根据设置的数据类型，用匹配的视图去渲染数据**

1. list 内部的视图不会被立即渲染，在需要时才会进行渲染
2. list 只会渲染 `<row>`标签 包裹的视图，`row`也是特殊的`div`标签
3. list 标签需要使用`t:for`设置渲染的数组

看下面例子

**使用一个list 组件 设置了其渲染的数组是`dataSource`，
并且匹配的是数组中的元素的`rowType`**

```
<list id = "form" 
       t:data = "item in dataSource"  // 你也可以写成 "(item, index) in dataSource"
       t:switch = "rowType" >
            
    <row t:case="A" id = "{{index}}">
       <label>{{item.name}} -- {{index}}</label>
    </row>
    
    <!--你可以写多个row去匹配，没有限制-->
    
    <row t:default >
       <label>{{item.name}}</label>
    </row>
</list>
```

再看看怎么填充数据

```
const app = token.registComponent("app", {
    data(){
            return {
                dataSource:[
                    {
                        rowType:"A",
                        name:"我会被t:case = 'A'的row 渲染"
                    }，
                    {
                        name:"我会被t:default 的row 渲染"
                    }
                ]
            }
        }
});
```

## 下拉刷新和上拉刷新参考scroll组件用法

## 事件回调

使用`@listener`表明需要在`listeners`的`listListener`里面处理事件

```
<list @listener = "listListener" ></list>
```

回调代码和方法如下

```
const app = {
    listeners:{
        listListener:{
            onSelectItem(data){
                // 某个row 被点击了
                console.log(data);
            },
            onDeselectItem(data){
                // 某个row 被取消点击了
                console.log(data);
            }
        },
    },
    data(){
        return {
            ...
        }
    }
}
```

## 个性化设置

list 的个性化设置 

| 属性 key  | 可选值     | 描述     |
| ---------- | ----------|----------|
| showSeparator | 布尔类型 | 是否显示大列表的分割线 |
| separatorLeft | 数字类型 | 大列表的分割线左边缩进 |
| separatorRight | 数字类型 | 大列表的分割线右边缩进 |
| allowDelete | 布尔类型 | 是否允许左滑删除某个row |

row 的个性化设置

| 属性 key  | 可选值     | 描述     |
| ---------- | ----------|----------|
| shouldHighlight | 布尔类型 | 是否有高亮状态 |
| highlightedColor | 字符串类型 | 高亮状态的颜色 |
| rightType | 数字类型 | row 最右边的装扮组件类型 |


**注意**
> **rightType** 
1. 如果被胡子语法绑定 必须绑定值是数字
2. 如果不被胡子语法绑定， 可以使用语义化的值，因为编译器会转化为数字

##### 举例: 不被胡子语法绑定

```
<row rightType = "indicator" ></row>
```

##### 举例: 被胡子语法绑定
```
<!--被胡子语法绑定-->
<row rightType = "customType" ></row>

const app = {
    data(){
        return {
            dataSource:[{
                rowType:"A",
                name:"我会被t:case = 'A'的row 渲染",
                customType:1 // 必须是数字 或 "1"
            }]
        }
    }
}

```

## 语义化的值和数字对应表

```
rightType 对照表
{
    "none"            : 0,
    "indicator"       : 1,
    "detaildisclosure": 2,
    "checkmark"       : 3,
    "detail"          : 4
}
```


## 使用DOM API
**所有div的DOM API 均可以使用**

```
<!--绑定回调监听者-->
<list id = "list"></list>
```

```
const list = $native.el('list'); // id值
list.removeAtIndex(0, 3)          // 删除第0个数据 ，使用第3种动画
```

##### API 列表

可调用的方法

```
1. removeAtIndex(index, animationType) // 删除第index个数据 使用animationType动画
2. pushData(arrayData, animationType)  // 在尾部追加一个数组，使用animationType动画
3. popData(length, animationType)      // 删除尾部length 长度的数据，使用animationType动画
4. scrollToItem(index, animationType)  // 滚动到第index 个list ，使用animationType动画
5. refreshData(list)                   // 使用list重新渲染数据
6. reload() //刷新整个列表数据
7. enableHeaderRefresh(value)          // 是否开启下拉刷新
8. enableFooterRefresh(value)          // 是否开启上拉加载更多功能
```





