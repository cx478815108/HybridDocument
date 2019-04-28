# 发送网络请求

发送网络请求使用`$http`对象
该对象使用promise 封装了native的网络请求

> `$http` 的所有接口

1. `$http.postJSON(url, data)`;
2. `$http.getJSON(url, data)`;
3. `$http.postText(url, data)`;
4. `$http.getText(url, data)`;
5. `$http.request(obj)`;

```
// url 地址，data 请求的参数 返回对象均为promise
// POST的方式 请求json 
const promise = $http.postJSON(url, data) // data是post的参数
promise.then((obj)=>{
    // obj.response 响应体
    // obj.data 获取的JSON
})
.catch((err)=>{
 // 请求错误，错误的原因
})
```


> 自定义request 

```
const obj = {
    url:'xxx',
    method: 'POST', // 可以为空，参数为：'POST'、'GET',
    timeout: 30, // 可以为空，单位：秒,默认30s,
    type:'json', //返回数据数据， 参数：'json'、'text', 可以为空， 默认为json
    cache:false, // 是否忽略缓存，
    ua:'xxx',    // UA 标识, 可以为空
    headers:{},   // 请求头, 可以为空
    data:{},      // 请求参数, 可以为空
    redirect:function (url,response){
        // 请求重定向，请返回一个新的请求
        return null;
    }
}


const promise = $http.request(obj) // 生成一个网络请求

```



