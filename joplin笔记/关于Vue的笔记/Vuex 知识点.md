# Vuex 知识点

1. 通过Vue.use()使用Vuex插件，可以调用这个插件中的Store构造函数 : 

   ```js
   Vuex.Store({ 
       actions,
       mutations,
       state,
       getters
   })
   ```

   然后在main.js中去声明这个配置项，声明后的$store会出现在各个VueComponents实例对象中和vm中，包括路由组件。这样就可以达到一种共享互相通信的作用。
   

2. 四个简写方式

   - mapState 、mapGetter 、 mapActions 、mapMutations  

     `需要引入 :  import { mapState ,mapGetter , mapActions ,mapMutations } from 'vuex'`

   - 当我们需要用到Vuex中state中数据的时候，一般情况下在vue的{{ }}中只能写成$store.state.xxx,

     但这么写模板语言不够清晰简单，会很难看。下面的这些方法可以大大的提高代码的可读性，可以使代码只需要在{{}} 中写入xxx即可。
   
   ```js
              //靠程序员自己亲自去写计算属性，这样写可以最简单也是最笨的达到目的。
        1.  computed : {
   			sum(){
   				return this.$store.state.sum
   			},
   			school(){
   				return this.$store.state.school
   			},
   			subject(){
   				return this.$store.state.subject
   			}, 
                   }
   
   			//借助mapState生成计算属性，从state中读取数据。（对象写法）
   			// ...mapState({he:'sum',xuexiao:'school',xueke:'subject'}),
   
   			//借助mapState生成计算属性，从state中读取数据。（数组写法）
          
   		2.	computed : {
                // 这行代码起到和上面代码完全一致的作用
               
               /*mapState会自动帮我们生成上面的三个函数，
               然后我们通过...扩展运算符把这三个函数遍历出来，
               在分别放入这个computed 对象中*/
               
               ...mapState(['sum','school','subject']),
                   
                  
           3. computed : {
   			bigSum(){
   				return this.$store.getters.bigSum
   			},   
                 }
               
               
               //借助mapGetters生成计算属性，从getters中读取数据。（对象写法）
   			// ...mapGetters({bigSum:'bigSum'})
   			
   			//借助mapGetters生成计算属性，从getters中读取数据。（数组写法）
              4. computed : {
                  //与上面d
   			 ...mapGetters(['bigSum'])
                  
                }
   ```
   
   
   
3. Vuex的state和vue的data用法上的区别？

- 当我们需要组件之间共用的数据时，就使用state，组件间独立的话就使用data 。但能用data的情况下，最好不要用Vuex，因为不好维护。

​                 



##      下面这些代码和注释要经常去看

```js
 actions: {
        duo(context,value){
        if(context.state.age > 15)  {
            console.log('我是action中duo函数的第一个参数',context)
            //由后台数据可知，context是一个对象，里面有state，action，commit，dispath等的对象
            console.log('我是action中duo函数的第二个参数',value)
            //value是父组件传来的一个参数，就是dispath(1,2){}的第2g参数
            context.commit('duo',value)
        }
            
            
            
  mutations: {
       duo(state,value) {
        console.log('duo在Mutation中被调用了')
        state.age += value
        console.log('我是mutation中duo函数的第一个参数',state)
        //第一个参数是state对象，第二个参数是父组件传来的一个参数
        console.log('我是mutation中duo函数的第二个参数',value)
       }
```

