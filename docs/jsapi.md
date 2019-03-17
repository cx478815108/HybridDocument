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

## 定位

```
token.getLocation((obj)=>{
    console.log(obj.longitude);
    console.log(latitude);
});
```

## 打电话

```
token.makePhoneCall('110');
```

## 存储照片到相册

```
token.saveImage({
    url:'http:xxx',
    success:()=>{  //存储成功回调
    },
    failure:(reason)=>{  //存储失败回调 reason 字符串
    }
);
```

## 本地同步存储方法

```
//把数据存储到iPhone 磁盘  - 全局存储
token.setGlobleStorage({
    key : "自定义key",
    value : 自定义value
});
//从iPhone 磁盘根据自定义key获取数据   - 全局存储 所有的页面都可以获取
token.getGlobleStorage();
//从iPhone 磁盘 清除的所有磁盘数据
token.clearGlobleStorage();
```

## 打log

仅供有hybrid引擎源码的用户使用

```
token.log('xxx');
```

## 获取设备运营商

```
token.getCarrier();
```

## 获取电量

```
token.getBatteryInfo();
```

## 获取充电状态

```
token.getChargingStatus();
```

## 弹出警告框

```
token.alert('标题','信息');
```

## 请求生物识别

```
token.requestBiometrics(title, callback);//参数是标题和callback
```

## 屏幕宽高

```
token.screenWidth();
token.screenHeight();
```

## 获取媒体音量

```
token.getMediaVolume();
```

## 获取屏幕亮度

```
token.getScreenBrightness();
```

## 系统版本

```
token.getClientOSVersion();
```

## 剪切板设置和获取值

```
token.setPasteboardString('xxx')
token.getPasteboardString();
```

## openURL

```
token.openAppWithURL('url str');
```

## 通过URL清除cookie

```
token.clearCookieSessions('url str');
```