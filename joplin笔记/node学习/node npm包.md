## npm包管理

- 下载指定版本号加一个@符
- 包版本号详解
    ![e25cbc78a3247dfcca7468552a81f54f.png](../_resources/e25cbc78a3247dfcca7468552a81f54f.png)

## npm 重点

> ==通过下述代码去生成依赖文件，项目上传到github时就可以通过这些依赖来精准的下载需要的包。==

- node项目执行`npm install`会生成package.lock.json（重要）
- node项目执行`npm init -y`会生成package.json （重要）

## 开发依赖与依赖区分

![d78af1a82804291fc05f607556cfdc79.png](../_resources/d78af1a82804291fc05f607556cfdc79.png)

## 下包慢问题

- 根据下图切换为淘宝镜像，提高下载速度。
    ![84dd4fc404eeb9f7a466ea9378ff8563.png](../_resources/84dd4fc404eeb9f7a466ea9378ff8563.png)
- nrm 镜像管理工具
    ![6f681ee20cda9cd7af5f53a48a63e9d1.png](../_resources/6f681ee20cda9cd7af5f53a48a63e9d1.png)

## npm 包分类

- 项目包分两类
    ![a0da5a3314ca2e50327a695146c4aa70.png](../_resources/a0da5a3314ca2e50327a695146c4aa70.png)
- 全局包
    ![7066cac5c6a810b1dccd63b12658f265.png](../_resources/7066cac5c6a810b1dccd63b12658f265.png)
- i5ting_toc 可以将md文档转为html （牛逼）
    ![4113ddeef259aa9e4f696be7246b5bc5.png](../_resources/4113ddeef259aa9e4f696be7246b5bc5.png)

## 开发属于自己的包

> 包必须严格按照规范来实现

### 包的规范

- 包的一些基本规范
    ![cdfc1108aa2e70a8f2feff10031e353d.png](../_resources/cdfc1108aa2e70a8f2feff10031e353d.png)
    
- 包的案例截图
    ![465c3719932ee51d1494efaa5bda905a.png](../_resources/465c3719932ee51d1494efaa5bda905a.png)
    
- 总结一下包需要哪些要求
    
    1.  包必须为一个单独的文件夹。
    2.  index.js 为入口文件，package.json 为依赖，README.md为介绍。
    3.  可以将类似功能的函数拆分到不同的.js文件中，再通过require导入到index.js主入口文件中。
    4.  在终端执行npm login 登陆，按照要求输入账号、密码、邮箱。需要注意的是不能使用镜像，必须使用npm 官方路径。
    5.  发布只需要打开包的根目录终端，输入npm publish 即可成功把包上传到npm。
- 删除发布的包
    ![f13590b96b3f0624423809fc141ce9cb.png](../_resources/f13590b96b3f0624423809fc141ce9cb.png)
    

## 模块优先缓存加载

1.  require执行多次相同代码，只执行第一次
    ![6295e243f98c0932f86a15e90cd18bb2.png](../_resources/6295e243f98c0932f86a15e90cd18bb2.png)
2.  内置模块优先级最高
    ![7c1552dd4c5f8ef2d8fa4ec8554d56bf.png](../_resources/7c1552dd4c5f8ef2d8fa4ec8554d56bf.png)
3.  自定义模块必须用相对路径，不然系统会把他误认为是内置模块或第三方模块。
    ![86709447541994d17d5da3b48e0d0883.png](../_resources/86709447541994d17d5da3b48e0d0883.png)
4.  第三方模块判定机制
    ![1f233037f3d1193274ca36c91bd12973.png](../_resources/1f233037f3d1193274ca36c91bd12973.png)
5.  目录作为模块
    ![ad118b1e391ad7382febe3643cca4ab8.png](../_resources/ad118b1e391ad7382febe3643cca4ab8.png)