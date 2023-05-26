## express学习目标
> ## ==注意 ： app.use()函数的作用就是用来注册全局中间件。==
![76ca310022b52d489f9814cd744ed73d.png](../_resources/76ca310022b52d489f9814cd744ed73d.png)
### express介绍
![26b7f982f75c6320b157d7e2931da352.png](../_resources/26b7f982f75c6320b157d7e2931da352.png)
### express 作用
![f8d1f1084a79f88cf17e166866f8e1dc.png](../_resources/f8d1f1084a79f88cf17e166866f8e1dc.png)
- app.get 监听get请求
![38a5b0e5f96159807f563dbbc12b61c1.png](../_resources/38a5b0e5f96159807f563dbbc12b61c1.png)
- app.post 监听post请求
![fd490a1bcc4404d535bfc4666c23efd5.png](../_resources/fd490a1bcc4404d535bfc4666c23efd5.png)
- res.send()将请求到的数据发送给客户端
- 简易版app.get和app.set请求
```javascript
//下面的代码是 app.get()和app.post的简易封装。

   const http = require('http');
   const server = http.createServer();
   server.on('request', (req, res) => {
      const url = req.url;
      console.log(req.method)
      if (req.method === 'GET') {
          if (url === '/user') {
              res.end(JSON.stringify({ name: '陈子文', age: 22, sex:'男'    }))
          }
      }
      else if (req.method === 'POST') {
          if (url === '/user') {
              res.end('请求成功')
          }
      }
   })
   server.listen(8080, () => {
      console.log('web server running at http://127.0.0.1:8080')
   })
```
### 获取url中携带的参数
- req.query 
![8d44699b1c5f268c1885383a80770efc.png](../_resources/8d44699b1c5f268c1885383a80770efc.png)
- req.parmas
![21de2aadcb59885a3008581ebf6b9815.png](../_resources/21de2aadcb59885a3008581ebf6b9815.png)
### ==托管静态资源(这个好)==
> express.static() 挂在静态资源文件
1. 挂载单个静态资源
![6598dbb09db0a55dcd0d6249850ee359.png](../_resources/6598dbb09db0a55dcd0d6249850ee359.png)
2. 挂载多个静态资源文件
![427b6b6b7171ef6b9864ec76c47b7e82.png](../_resources/427b6b6b7171ef6b9864ec76c47b7e82.png)
3. 挂在路径前缀
![ac7bc8715d69a02197d1d4586f5d4baa.png](../_resources/ac7bc8715d69a02197d1d4586f5d4baa.png)
4.使用nodeman
![d56ddec8ad66c8b7bf99e51491d66a2b.png](../_resources/d56ddec8ad66c8b7bf99e51491d66a2b.png)
### express 路由
1. 路由匹配
![9d4d4a200ab0d3ba52ac58b03c4b5437.png](../_resources/9d4d4a200ab0d3ba52ac58b03c4b5437.png)
2. 路由模块化步骤
![299bcfb2dc13fe8af90d52c27426ec5f.png](../_resources/299bcfb2dc13fe8af90d52c27426ec5f.png)
3. 路由模块化实操
![6ca2b58e7d9ab07a77d53c0768ad9ed2.png](../_resources/6ca2b58e7d9ab07a77d53c0768ad9ed2.png)
4. 路由前缀，与静态资源前缀同理
![516a0bd3be0bb516aed03858582bf093.png](../_resources/516a0bd3be0bb516aed03858582bf093.png)
5.express 中间件
   - 中间件比喻
   ![977c64d6ec8c5ff182e1994928335c11.png](../_resources/977c64d6ec8c5ff182e1994928335c11.png)
   - 中间件概念
   ![2bf819ff81d95e9754c12d61260a27dc.png](../_resources/2bf819ff81d95e9754c12d61260a27dc.png)
   - 请求函数包含next() 函数 就说明它是一个中间件，否则就是一个路由处理函数
   ![d33782a6bb5b81015ef58217e8cb942e.png](../_resources/d33782a6bb5b81015ef58217e8cb942e.png)
   - 定义中间件函数
   ![c52210355f13599a619800be334a936e.png](../_resources/c52210355f13599a619800be334a936e.png)
   - 定义全局中间件
   ![267260c1c371acf7610a87a9f4f9ffc5.png](../_resources/267260c1c371acf7610a87a9f4f9ffc5.png)
   - 中间件的作用
   ![79c246cd78eb3ff16658cf824e63b71b.png](../_resources/79c246cd78eb3ff16658cf824e63b71b.png)
      - 中间件跟下级的req，res是共享的，写在这个就可以在下一个中间件中使用。
	  ![fae547fc7ce1686be257feb973927978.png](../_resources/fae547fc7ce1686be257feb973927978.png)
	  - 定义单个局部中间件
	  ![0d6332f0971bb6c9d2e3a1ea54b35e8a.png](../_resources/0d6332f0971bb6c9d2e3a1ea54b35e8a.png)
	  - 定义多个局部中间件
	  ![a72c8ba4282fa55b0be61e94134cf49b.png](../_resources/a72c8ba4282fa55b0be61e94134cf49b.png)
### 中间件的五项注意点（单独一大列）
![19fa9588ff744eec24d727fb38eb34ac.png](../_resources/19fa9588ff744eec24d727fb38eb34ac.png)
1. 应用级中间件
![0bfc8330ba013a23b9b0a139c0f8cac3.png](../_resources/0bfc8330ba013a23b9b0a139c0f8cac3.png)
2.路由级别中间件
![1fed59873812a2456064e3f562b37478.png](../_resources/1fed59873812a2456064e3f562b37478.png)
3.错误级别中间件
> ==有四个参数，必须定义在路由之后，不然程序不执行==

![d2b73af93a5d3f344fac8e1ed5cc5d88.png](../_resources/d2b73af93a5d3f344fac8e1ed5cc5d88.png)

4. express 内置中间件
![9608e03a1425a0a1499f7cbd9393cec1.png](../_resources/9608e03a1425a0a1499f7cbd9393cec1.png)
   - express.json 中间件
   ![332d2dabc0cfb41fc554861ecbacb054.png](../_resources/332d2dabc0cfb41fc554861ecbacb054.png)
   - express.urlencode 中间件
   ![f7a42bc8278319de3ae03ffd42ee5a31.png](../_resources/f7a42bc8278319de3ae03ffd42ee5a31.png)
   5. 第三方中间件 （案例介绍）
   ![3eb4168a1ad25a05444054ae794ee000.png](../_resources/3eb4168a1ad25a05444054ae794ee000.png)
### 自定义中间件
1. 基本步骤
![09672b734f6563a0e7f95da544b015b3.png](../_resources/09672b734f6563a0e7f95da544b015b3.png)
2. 监听并拼接数据
![f7d3e67949c52039940aa99ff9a9ede7.png](../_resources/f7d3e67949c52039940aa99ff9a9ede7.png)

	  