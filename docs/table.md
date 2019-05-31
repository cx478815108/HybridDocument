# table组件

> table组件是高性能的大列表加载组件，具有组件重复利用，渐进加载的特点

**table 会根据设置的数据类型，用匹配的视图去渲染数据**

1. table 内部的视图不会被立即渲染，在需要是才会进行渲染
2. table 只会渲染 `<cell>`标签 包裹的视图，cell 也是特殊的div 标签
3. table 标签需要使用`t:for`设置渲染的数组

看下面例子

**使用一个table 组件 设置了其渲染的数组是`dataSource`，
并且匹配的是数组中的元素的`cellType`**

```
<table id = "form" 
       t:data = "item in dataSource"  // 你也可以写成 "(item, index) in dataSource"
       t:switch = "cellType" >
            
    <cell t:case="A" id = "{{index}}">
       <label>{{item.name}} -- {{index}}</label>
    </cell>
    
    <!--你可以写多个cell去匹配，没有限制-->
    
    <cell t:default >
       <label>{{item.name}}</label>
    </cell>
</table>
```

再看看怎么填充数据

```
const app = token.registComponent("app", {
    data(){
            return {
                dataSource:[
                    {
                        cellType:"A",
                        name:"我会被t:case = 'A'的cell 渲染"
                    }，
                    {
                        name:"我会被t:default 的cell 渲染"
                    }
                ]
            }
        }
});
```

## 下拉刷新和上拉刷新参考scroll组件用法

## 事件回调

使用`@listener`表明需要在`listeners`的`tableListener`里面处理事件

```
<table @listener = "tableListener" ></table>
```

回调代码和方法如下

```
const app = {
    listeners:{
        tableListener:{
            onSelectItem(data){
                // 某个cell 被点击了
                console.log(data);
            },
            onDeselectItem(data){
                // 某个cell 被取消点击了
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

table 的个性化设置 

| 属性 key  | 可选值     | 描述     |
| ---------- | ----------|----------|
| showSeparator | 布尔类型 | 是否显示大列表的分割线 |
| separatorLeft | 数字类型 | 大列表的分割线左边缩进 |
| separatorRight | 数字类型 | 大列表的分割线右边缩进 |
| allowDelete | 布尔类型 | 是否允许左滑删除某个cell |

cell 的个性化设置

| 属性 key  | 可选值     | 描述     |
| ---------- | ----------|----------|
| shouldHighlight | 布尔类型 | 是否有高亮状态 |
| highlightedColor | 字符串类型 | 高亮状态的颜色 |
| rightType | 数字类型 | cell 最右边的装扮组件类型 |


**注意**
> **rightType** 
1. 如果被胡子语法绑定 必须绑定值是数字
2. 如果不被胡子语法绑定， 可以使用语义化的值，因为编译器会转化为数字

##### 举例: 不被胡子语法绑定

```
<cell rightType = "indicator" ></cell>
```

##### 举例: 被胡子语法绑定
```
<!--被胡子语法绑定-->
<cell rightType = "customType" ></cell>

const app = {
    data(){
        return {
            dataSource:[{
                cellType:"A",
                name:"我会被t:case = 'A'的cell 渲染",
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




