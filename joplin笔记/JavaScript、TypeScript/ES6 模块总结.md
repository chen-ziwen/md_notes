# ES6 模块化总结

## 模块暴露的方式：

### 分别暴露

- 一次暴露一个数据，可以是一个字符串，数组，对象，函数，集合，映射等等

```js
export function mod () {  
    console.log("我爱你")
}

export let obj = {   
     name : "你好",
     age : 18,
     phone : "小米"
 }
```

### 合并暴露

- 合并暴露可以同时暴露出多个数据
- 每个暴露出去的数据可以是任意的数据类型，不限内容

```js
function moudel () {
     console.log("我是一个测试用的")
 }

 let array = [1,3,56,89,,56,23,3,3]

 export {moudel,array}; //暴露出一个函数和一个数组

```

### 默认暴露

- 默认暴露需要加上关键词 **default**
- 每个模块只能有一个默认暴露，不然会报错

```js
export default {
    name:"陈子文",
    hello:function () {
        console.log("你好")
    }
}
```

## 模块导入的方法：

### 导入前提

- 原生**javascript**中的**import**必须写在**script**标签中，且标签类型必须写为**module**类型
- 通过**src**直接导入**app.js** 中引入的两个模块，**m1.js**和**m2.js**

```html
<script type="module">
    import * as czw from './czw.js'
</script>
```

```html
<script src="app.js" type="module"></script> 
```

### 通用导入

- 原生js中导入的文件后缀必须写上 .**js**,例如Vue就不用写
- 下面代码的这种写法意思是：把**m1.js**文件中所有前缀带有**export**的数据全部集合成一个**module**对象暴露，并用**as**重新命名为**m1**。
- 星号代表全部的暴露数据，类似**css**中的 ***{ margin : 0px; padding : 0px;}** ***指代所有**

```js
import * as m1 from "./m1.js" 
console.log(m1);

import * as m2 from "./m2.js"
console.log(m2.default.hello());
```

### 解构赋值导入

- **<u>最灵活的暴露方式</u>**
- 这种导入方法的优势在于，当我们需要的不是一个完整的模块，而是模块中的某个数据或多个数据时，可以有选择的去导入某个数据，而不是去导入整个模块。
- 下面第一条代码的意思是，同时导入了m1模块中的mod数据和obj数据，同时为mod重新取个名字，这个名字是mods
- 默认暴露使用这种方式导入的话，必须用**as**重新命名后才可以导入成功

```js
import {mod as mods,obj} from "./m1.js"  //重新命名mod
console.log(mods,obj);

import {default as m2} from "./m2.js"//default必须改名字才能用
console.log(m2);
```

### 默认暴露导入

- 最简便的暴露方式，但是只有默认暴露的数据才可以这么导入

```js
import m2 from "./m2.js"
console.log(m2);
```

## 暴露并导入方式

> 用来将多个文件中暴露的内容集中到一个文件夹中，方便管理。

### 集合导入暴露

```js
export * from './m2.js'
// 将m2文件中的暴露的方法全部引入并再次暴露
```
