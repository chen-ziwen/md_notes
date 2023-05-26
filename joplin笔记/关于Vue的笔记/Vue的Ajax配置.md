# Vue的Ajax配置

- 跨域就是违背了同源策略 必须同协议名，主机名，端口号一致
- vue中的public就是8080端口号的地址，，而且通过url去访问的话，会优先访问自身里的文件，如果自身没有的话再去服务器里寻找访问

##   原生ajax

```js
const xhr = new XMLHttpRequest()

xhr.open('get',url)

xhr.send()

xhr.onreadyStatechange = function () {
    
//readyState的状态码为1-4 4表示已经接收到所有的响应，可以使用了
    
if(xhr.readyState === 4) {

    //status 表示响应的HTTP状态 一般为2XX
    //第一步检查status属性确保响应成功
if(xhr.status>=200&&xhr.status<300) {
    //这里面写上需要实现的程序问题
    
    
}

}

}
```

