# Vue监视数据的原理：

##         1. vue会监视data中所有层次的数据。



##         2. 如何监测对象中的数据？



​                通过setter实现监视，且要在new Vue时就传入要监测的数据。

​                  (1).对象中后追加的属性，**Vue默认不做响应式处理**

​                  (2).如需给后添加的属性做响应式，请使用如下API：

​                          **Vue.set(target，propertyName/index，value)** 或 

​                          **vm.$set(target，propertyName/index，value)**



##         3. 如何监测数组中的数据？

​                  通过包裹数组更新元素的方法实现，本质就是做了两件事：

​                    (1).调用原生对应的方法对数组进行更新。

​                    (2).重新解析模板，进而更新页面。



##     4.在Vue修改数组中的某个元素一定要用如下方法：



​      1. 使用这些API:

1. push()
2. pop()
3. shift()
4. unshift()
5. splice()
6. sort()
7. reverse()

​      2. Vue.set() 或 vm.$set()

​        **特别注意：Vue.set() 和 vm.$set() 不能给vm 或 vm的根数据对象 添加属性！！！***

