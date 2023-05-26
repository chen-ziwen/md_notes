### get
```javascript
// 编写get接口
router.get('/get', (req, res) => {
    res.setHeader('content-Type', 'text/html;charset=utf-8');

    const query = req.query;
    res.send({
        status: 200,
        msg: 'get请求成功',
        data: query
    })
})
```
### post
```javascript
router.post('/post', (req, res) => {
    res.setHeader('content-Type', 'text/html;charset=utf-8');
    // const query = req.query;
    //  通过req.body 获取请求体中包含的url-encoded格式的数据
    const body = req.body;
    // 通过res.send()方法 向客户端响应数据
    res.send({
        status: 200,
        msg: 'post请求成功',
        data: body
    })
})

// body数据必须使用node自带的中间件进行解析，
// 配置解析表单数据的中间件
app.use(express.urlencoded({ extended: false }));
```