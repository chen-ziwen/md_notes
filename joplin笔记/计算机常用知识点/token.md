# 前后端的身份认证

## 身份认证
 身份认证又称“身份验证”、“鉴权”，是指通过一定的手段，完成对用户身份的确认。
## 不同开发模式下的身份认证
对于服务端渲染和前后端分离这两种开发模式来说，分别有着不同的身份认证方案：
1. 服务端渲染推荐使用Session认证机制。
2. 前后端分离推荐使用JWT认证机制。

## HTTP协议的无状态性
了解HTTP协议的无状态性是进一步学习Session认证的必要前提。
HTTP协议的无状态性，指的是客户端的每次HTTP请求都是独立的，连续多个请求之间没有直接的关系，**服务器不会主动保留每次HTTP请求的状态**。
## 认识Cookie
- 什么叫Cookie
1. 身份认证方式在Web开发中的专业术语叫做Cookie
2. Cookie是存储在用户浏览器中一段不超过4kb的字符串。它由一个名称和一个值和其他几个用于控制Cookie有效期、安全性、使用范围的可选属性组成。
3. 不同域名下的Cookie各自独立，每当客户端发起请求时，会**自动**把**当前域名下**所有**未过期的Cookie**一同发送到服务器。

- Cookie的几大特性
1. 自动发送
2. 域名独立
3. 过期时限
4. 4kb限制
- Cookie在身份认证中的作用
1. 客户端第一次请求服务器的时候，服务器**通过响应头的形式**，向客户端发送一个身份认证的Cookie，客户端会自动将Cookie保存到浏览器中。
2. 随后，当客户端浏览器每次请求服务器的时候，浏览器会**自动**将身份认证相关的Cookie，**通过请求头的形式**发送给服务器，服务器即可验证客户端的身份。
3. 请求头中的Cookie是一大串字符串，里面包含非常多的键值对。与服务器发送的Cookie键值对列表一一对应。
- Cookie不具有安全性
    由于Cookie是存储在浏览器中的，而且浏览器也提供了读写Cookie的API，因此Cookie很容易被伪造，不具有安全性。因此不建议服务器将重要的隐私数据，通过Cookie的形式发送给浏览器。
    **千万不要使用Cookie存储重要且隐私的东西！比如用户的身份信息、密码等。**
## Session的工作原理
- 利用Session的话，就不需要把一些敏感信息保存在Cookie中，客户端只保存一个加密后SessionId，后续的请求只需要将这个SessionId返回给服务器，服务器便能通过
这个Id，验证用户的身份。
1. 客户端登录时，提交账号与密码，服务器成功验证账号和密码后，将登录成功后的用户信息存储在服务器内存中，同时生成对应的SessionId。
2. 服务端将生成的SessionId通过Cookie的形式响应给客户端，浏览器自动把Cookie存储在当前的域名下。
3. 客户端再次发起请求时，通过请求头自动把当前域名下所有可用的Cookie发送给服务器。
4. 服务器根据请求头中携带的Cookie，从内存中查找对应的用户信息，用户的身份认证成功后，服务器针对当前用户生成生成特定的响应内容。
5. 服务器把当前的内容响应给浏览器。
- Session认证的局限性
Session认证机制需要配合Cookie才能实现。由于Cookie默认不支持跨域访问，所以，当涉及到前端跨域请求后端接口的时候，需要做很多额外的配置，才能实现Session认证。

## JWT认证
 - 什么是JWT
 JWT（英文名全程：JSON Web Token）是目前最流行的跨域认证解决方案
 - JWT有三个部分组成，从前到后分别是Header、Payload、Signature
 1. **Payload**部分**才是真正的用户信息**，它是用户信息经过加密之后产生的字符串。
 2. Header和Signature是**安全性相关**的部分，只是为了保证Token的安全性。


## 总结
我们利用cookie、session、token实现免密登陆的本质上，就是因为这三者都必须携带完整的用户登陆验证信息，例如用户名，用户密码，用户手机等等。而单纯使用cookie来实现的话，这些敏感信息很容易的就能被别人看到，例如在浏览器cookie中直接看到别人的登陆密码或者手机号码（虽然可以给cookie加密）。而session则是将用户的完整信息保存在服务器端，只给客户端返回一个sessionid，当客户端请求服务器时，会将这个sessionid带上，服务器再通过这个sessionid来获取完整用户信息，对比cookie，使用seesion方式，可以更好的保护用户的隐私，不会直接暴露用户信息。但是缺点就是比较占用服务器的资源，因为每个用户的完整信息都必须保存在服务器中。同时呢，cookie和seesion都不支持跨域请求，使用起来会比较麻烦。
token则是一种更好的解决方案，当用户请求服务端时，服务端会将用户的信息进行分段加密，最后再通过这几个分段的加密信息，再去生成一个秘钥，最终将分段信息和秘钥拼接起来，就形成了一个完整的token。同时，token不会自动保存，需要手动的将它保存在浏览器中，token加密信息中，包含着用户的完整信息，所以我们通过给请求头属性Authorization赋值token的方式，去请求服务端，服务端通过解析token就可以获取到完整的用户信息，从而实现验证。token并不存在跨域问题，同时不会在浏览器中直接暴露用户的具体信息，是一种非常不错的验证身份的方式。