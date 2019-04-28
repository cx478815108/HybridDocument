# 存储操作
将数据存储在iPhone 的磁盘上，使用`$storage`对象

## 存储到本小程序

```
$storage.setItem(key, value, time) // value 可以是字符串 或者是 JSON对象,time可选，数据存储的时间，单位s，超过该时间自动被删除.
$storage.getItem(key) // 根据key取对象
```
## 存储到所有小程序都能访问的地方

```
$storage.setPublicItem(key, value, time) // value 可以是字符串 或者是 JSON对象
$storage.getPublicItem(key) // 根据key取对象
```


