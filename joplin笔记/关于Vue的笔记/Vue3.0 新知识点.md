# Vue3.0 新知识点

**vue3.0的文档重头到尾翻了一遍，大部分内容和vue2.0没有什么区别 下面是记录一下多出来的东西，以及学到的新知识点。**

***

## 1.new Vue、 Vue.createApp

- 这两个函数都可以使用,具体区别看文档。

##  2.provide、 inject 的使用

- **provide父组件传  inject 子组件接收 依赖注入 类似于props。**
- 实际上，你可以将依赖注入看作是“长距离的 prop”，除了:

1.  父组件不需要知道哪些子组件使用了它 provide 的 property
2. 子组件不需要知道 inject 的 property 来自哪里
3. `Vue.createApp（{}）.mount(‘#app’) 相当与 new Vue({el :'#app'})`

## 4.setup函数 组合式api

- setup函数接收两个参数 一个props 一个content。ref、recative 用到那个就必须引入哪个 


```js
 eg.   import {ref,reactive} from 'vue'
```



- ref() 函数和reactive() 函数   :    

1.  ref类似于 data（） { return {}}中的字符，数字等简单的数据 reactive类似于难的数据 比如数组，对象

​                  函数可以直接写在setup函数中 。

​            2.所有的setup中定义的数据都必须通过return 暴露出去 不然外面接收不到

## 5.toRef、 toRefs 、ref

-   toRef

     `创建一个ref类型数据, 并和以前的数据关联`

-   toRefs

   `批量创建ref类型数据, 并和以前数据关联`

-   toRef和ref区别

    `ref-创建出来的数据和以前无关(复制)`

-   toRef-创建出来的数据和以前的有关(引用)

     `ref-数据变化会自动更新界面`

******

**通过toRef创建的数据不会更新渲染到页面,但是如果是通过toRef将某个对象中的属性值变为响应式数据时，那么我们修改响应式的数据是会影响到原始数据的，但页面仍然不更新。**

**采用引用的方式，修改响应式数据，会影响原始数据，并且数据发生改变，界面也不会更新**



### 使用ref的注意事项



- 其一，在模板中引入ref的值，vue会进行自动解套，也就是不用.value。但如果是深层的不会自动解套。
- 其二，在setup内部，对其操作必须使用ref.value的方式
- 使用reactive的注意事项
- 类型有限，只能是对象或者数组或者集合、映射。
- reactive可以包裹ref对象，包裹后，在模板中同样也会自动解包，包括ref对象，用的时候不加value

- **ref、toRef、toRefs 都可以将某个对象中的属性变成响应式数据**
- **ref的本质是拷贝，修改响应式数据，不会影响到原始数据，视图会更新**
- <u>**toRef、toRefs的本质是引用，修改响应式数据，会影响到原始数据，视图不会更新**</u>
- **toRef 一次仅能设置一个数据，接收两个参数，第一个参数是哪个对象，第二个参数是对象的哪个属性**

- **toRefs接收一个对象作为参数，它会遍历对象身上的所有属性，然后挨个调用toRef执行**

***

  结论: 

1.  如果利用ref将某一个对象中的属性变成响应式的数据 我们修改响应式的数据是不会影响到原始数据的obj !== state。
2.  如果利用toRef将某一个对象中的属性变成响应式的数据， 我们修改响应式的数据是会影响到原始数据的。但是如果响应式的数据是通过toRef创建的, 那么修改了数据并不会触发UI界面的更新。

## 6.setup()中的知识点

1. prop是响应式的，不能解构赋值，不然会失去响应性。

2. 如果需要解构 prop，可以在 `setup` 函数中使用 [`toRefs`](https://v3.cn.vuejs.org/guide/reactivity-fundamentals.html#响应式状态解构) 函数来完成此操作：

   ```js
   // MyBook.vue
   
   import { toRefs } from 'vue'
   
   setup(props) {
     const { title } = toRefs(props)
   
     console.log(title.value)
   }
   ```

​           3.content不是响应的，可以去解构。content里面包含很多方法可以去使用。

​          4. 执行 `setup` 时，组件实例尚未被创建。因此，你只能访问以下 property:

- `props`
- `attrs`
- `slots`
- `emit`

​           换句话说，你**将无法访问**以下组件选项：

- `data`
- `computed`
- `methods`
- `refs` (模板 ref)

## 7.mixin混入

1. 当组件和 mixin 对象含有同名选项时，这些选项将以恰当的方式进行“合并”。比如，每个 mixin 可以拥有自己的 `data` 函数。每个 `data` 函数都会被调用，并将返回结果合并。在数据的 property 发生冲突时，会以组件自身的数据为优先。
2. 同名钩子函数将合并为一个数组，因此都将被调用。另外，mixin 对象的钩子将在组件自身钩子**之前**调用。
3. 值为对象的选项，例如 `methods`、`components` 和 `directives`，将被合并为同一个对象。两个对象键名冲突时，取组件对象的键值对。
4. 全局mix

