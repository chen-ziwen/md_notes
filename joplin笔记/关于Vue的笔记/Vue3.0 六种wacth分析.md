# Vue3.0 五种wacth分析
## 1.当监听数据为简单的ref类型时：
### depp、immediate 正常使用
**`const date = ref(x)`**

**`const app = watch(date,(newV,oldV)=>{}，{deep：true，immediate：true})`**

## 2.当监听数据为多个简单的ref类型时：
### depp、immediate 正常使用
**`const date = ref(x)`**

**`const date2 = ref(x)`**

**`const app = watch([date,date2],(newV,oldV)=>{}，{deep：true，immediate：true})`**

## 3当监听对象为一整个对象时：
### （1）deep失效，变为默认开启，immediate 正常使用
### （2）watch的 oldV 失去效果，值变的和newV一样
**`const obj = reactive({xx:xx})`**

**`const app =watch(obj,(newV,oldV)=>{})`**

## 4.当监视对象为对象中的某一个值时：
### depp、immediate 正常使用
**`const obj = reactive({name:'czw'})`**

**`const app = watch(()=>obj.czw,(newV,oldV)=>{}，{deep：true，immediate：true})`**

## 5.当监听对象为不同（相同）对象中的多个值时：
### （1）depp、immediate 正常使用
### （2）newV和oldV的值变为数组形式
**`const obj = reactive（{name:'czw'}）`**

**`const obj2 = reactive（{age:22}）`**

**`const app = wacth([()=>obj.name,()=>obj2.age],()=>{},{deep：true，immediate：true})`**

## 6.当监听的数据为对象中的对象的话(特殊)：
### （1）depp、immediate 正常使用
### （2）newV和oldV的值变为数组形式
**`const obj = reactive（{person：{name:'czw',age:22}}）`**

**`const app = wacth(()=>obj.person,()=>{},{deep：true，immediate：true})`**
