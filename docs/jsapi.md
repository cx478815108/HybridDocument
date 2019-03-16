# JSAPI

## 1.网络请求
先进的网络请求工具，有Native 多线程支持，无跨域限制，支持网络重定向

```javascript
token.request(
    {
        url:"https://xxxxx",
        method:"POST",
        UA:"",
        timeout:30,  //请求超时时间 ，30s
        header:{     //http请求头
            "key1":"value1",
            "key2":"value2",
        },
        httpParameter:{  // POST参数 - 方式1
            "key1":"value1",
            "key2":"value2",
        },
        jsonParameter:{  // POST参数 - 方式2   当方式一不行时尝试方式二,会相互覆盖
            "key1":"value1",
            "key2":"value2",
        },
        resultType:"text",   //请求结果的类型，是text还是json text|json
        success :(response) => {
        },
        failure:(code,reason) => {
        },
    }
);
```

