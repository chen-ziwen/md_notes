# 自定义事件

##  绑定一个自定义事件的方法

​      

```js
@czw = 'add'
......

methods : {
    add() {
        alert("我是第一种方法")
    }
}
```



```js
$on('czw',()=> {
    alert("我是第二种方法")
}
```

## 触发自定义事件的方法



```js
$emit()  

sendStudentlName(){
				//触发Student组件实例身上的atguigu事件
				this.$emit('atguigu',this.name,666,888,900)
				// this.$emit('demo')
				// this.$emit('click')
			},
			unbind(){
				this.$off('atguigu') //解绑一个自定义事件
				// this.$off(['atguigu','demo']) //解绑多个自定义事件
				// this.$off() //解绑所有的自定义事件
			},
			death(){
				this.$destroy()
                //销毁了当前Student组件的实例，销毁后所有Student实例的自定义事件全都不奏效。
			}
```

## 技巧小总结:

1.  **$emit **用来触发自定义事件，一般来说，哪里需要传数据，就把**$emit**写在哪里。

   第一个参数为自定义事件名，后面的参数为需要传递的数据。emit单词是发出射的意思

   

2. **$on**  用来自定义事件，一般来说，哪里需要接收数据，就把**$on**写在哪里。第一个参数为自定义事件名，第二个参数是一个回调函数。一般需要写在mounted钩子中。

   如果说这个回调函数是写在**methods**中的时候，只需要写    **this.回调函数 ** 。如果是写在**$on**内部的话，则要写成**箭头函数**的形式。

   

3. **$off**  用来解除自定义事件  只需要一个参数，参数为自定义事件名。一般来说写在beforeDestroy钩子中。

​       

