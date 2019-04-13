# TokenHybrid

#### TokenHybrid是什么？

> TokenHybrid是一个使用XML模板, CSS, JavaScript 构建iOS原生应用界面的库，它可以帮你快速构建高性能的原生应用程序
**拥有类似Vue 的API，可以做到对JS 对象数据的细粒度追踪**

Example
![](http://tokenhybriddocument.oss-cn-beijing.aliyuncs.com/example.png)

## 性能怎么样？
对比框架 React-native 
测试用例：豆瓣评分前100条电影数据大列表渲染
测试环境：iPhone 7 12.1.4（16D57）
Xcode 性能分析工具，快速滚动测试FPS

![](http://tokenhybriddocument.oss-cn-beijing.aliyuncs.com/fps.png)



| 数据指标 | TokenHybrid | react-native |
| --- | --- | --- |
| cpu占用 | 相对稳定，最高158% | 不稳定，上下波动 最高184% |
| 10次启动平均启动耗时 | 11.59ms | 132.7ms(正式环境) 936.72ms(测试环境) |
| 内存占用 | 31.7M | 153M |
| FPS 均值 | 58.87 无卡顿 | 41.29 明显卡顿 |

## 调试特定

* 支持无线刷新UI
* 支持无线个Project工程
* 支持无线调试JavaScript 并输出调试结果
* 编辑器支持API 提示

## more 
coming...

