# Chiko Music音乐
## 简介

 **本次项目是基于Vue3.0+TypeScript+Sass+NodeJs进行开发的,通过开发项目来加强对技术的理解和实际应用,同时学习更多关于Web应用的全栈开发,相比于之前的Chiko宠物信息网站项目来说,这次的开发难度要远远超过之前的项目,需要运用到的知识体系也会复杂很多,所以在这先列出此次项目的目的以及需要注意的点.** 
___
## Chiko Music项目

### 网易云接口地址
>  - 数据来源:  [网易云音乐接口](https://binaryify.github.io/NeteaseCloudMusicApi/#/?id=neteasecloudmusicapi/)
>
### 参考项目地址
> 1. [项目构建架构](https://blog.csdn.net/weixin_42290927/article/details/94432587/)(各种文件的资源命名)
> 2. [vue3.0+ts+node 音乐开发](https://github.com/SmallRuralDog/vue3-music/)(主要参考这个)
___
## **项目可以收获的知识**

- #### 接口的封装 
- #### ts类型的应用
- #### node的学习
- #### 大项目的设计模式
- #### axiso的拦截封装

___
## **项目需要注意的点**
- #### 尽可能的把模块细化 都写成小组件
- #### 用最新的Vuex版本 可能用pinia
- #### 把每个接口都封装起来 通用export单独暴露 import 解构引入 
- #### 路由和pinia的模块化
- #### hook的运用 类似于mixin封装
- #### axiso的封装 
___
## **目前成功引入**

- [x] **ElementPlus 按需引入成功**
- [x] **router模块细分成功**

## 音乐项目还需要实现的点
1. 登录模块 cookie
2. 搜索歌曲功能
3. 歌手模块的mv和相似歌手还有专辑的跳转页面
4. mv  （和上面的mv共用组件）另外得写一个mv跳转页面
5. 新碟 （调用api就行 其他的都有写好的东西）
6. 登录后的特有的一些功能（可写可不写）
