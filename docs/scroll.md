# scroll组件

> scroll组件是滑动组件，当组件超过屏幕后，需要滑动展示，并且可以控制是否显示下拉刷新，或者上拉加载更多

**scroll组件不支持事件点击**
使用方法

```
<scroll style:"width: 100%; height: 50%;" 
    showVIndicator = "false" 
    showHIndicator = "false" >
</scroll>
```

## 可用于div 的css属性
支持所有div的属性

## 支持响应式的属性
可以使用胡子语法绑定该属性，直接使用js 修改
**注意**响应式的属性 颜色不支持 "red"等语义化的颜色表示，只能使用"rgb,rgba,16进制表示"


| 属性 key       | 可选值   | 描述                   |
| -------------- | -------- | ---------------------- |
| showVIndicator | 布尔类型 可选值:"0","1"| 是否展示垂直滚动指示器 |
| showHIndicator | 布尔类型 可选值:"0","1"| 是否展示水平滚动指示器 |
| allowScroll    | 布尔类型 可选值:"0","1"| 是否允许滚动           |
| allowBounces   | 布尔类型 可选值:"0","1"| 是否允许有边界回弹     |
| allowPage      | 布尔类型 可选值:"0","1"| 是否允许翻页           |

## 下拉刷新或者上拉加载更多

```
<scroll style:"width: 100%; height: 50%;" 
    headerRefresh = "true" // 开启下拉刷新 
    footerRefresh = "true" // 开启上拉加载更多
    onHeaderRefresh = "onHeaderRefresh()" // 回调
    onFooterRefresh = "onFooterRefresh()" // 回调
    >
</scroll>
```

在JavaScript 中设置回调

```
const app = {
    methods:{
        onHeaderRefresh:{

        },
        onFooterRefresh(){
        
        }
    },
    data(){
        return {
            ...
        }
    }
}
```


## scroll 滚动状态回调

```
<!--绑定回调监听者-->
<scroll @listener = "scrollListener">
</scroll>
```

在JavaScript 中设置回调

```
const app = {
    listeners:{
        scrollListener:{
            onStateChange(state){
                log("state 改变了" + state);
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

