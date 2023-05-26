# 组件的创建笔记

## 创建组件案例 :



```js
const  Student = Vue.extend({

这里面除了不能写el，其他的和Vue构造函数的实例vm一样

})
```

下面这个为大概的结构，内部代码还有很多很多，完整版去看**vue.js**

```javascript
 Vue.extend = function (extendOptions) {
      var Sub = function VueComponent (options) {
        this._init(options);
      };
      return Sub
    };
  }
```

##  组件的流程理解 :



通过上面简略版的代码块可以知道：

1. 每当调用Vue.extend这个方法时，调用结果都是返回一个VueComponets构造函数，而且每次返回的都是一个全新的VueComponent函数！！！！！

   

2. 当我们使用组件标签的时候，Vue会帮我们使用专属的VueComonenet函数去创建一个实例对象vc

   - 例如 :  <Student/>  
   - 每当我们使用一次 <Student/>，就会创建一个实例对象，实例对象中可以完成一系列的配置，data、methods、computed等等

   

3. 通过之前的学习可以知道**VueComponent.prototype.__ proto __  ===  Vue.prototype**

   

 

##    老师的总结  :



关于VueComponent：



​            1.school组件本质是一个名为VueComponent的构造函数，且不是程序员定义的，是Vue.extend生成的。

​          2.我们只需要写<school/>或<school></school>，Vue解析时会帮我们创建school组件的实例对象， 即Vue帮我们执行的：new  VueComponent(options)。 ///**这个很重要**

​            3.特别注意：每次调用Vue.extend，返回的都是一个全新的VueComponent！！！！

​            4.关于this指向：

​                (1).组件配置中：

​                      data函数、methods中的函数、watch中的函数、computed中的函数 它们的this均是【VueComponent实例对象】。



​                (2).new Vue(options)配置中：

​                      data函数、methods中的函数、watch中的函数、computed中的函数 它们的this均是【Vue实例对象】。



​            5.VueComponent的实例对象，以后简称vc（也可称之为：组件实例对象）。

​              Vue的实例对象，以后简称vm。

