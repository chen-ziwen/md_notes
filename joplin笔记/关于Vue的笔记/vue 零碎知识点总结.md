# vue 零碎知识点总结

## props和attrs的区别
props
- props必须主动去声明接收，不声明的值，props中取不到。
- props可以接收静态值和动态值，静态值为字符串，动态值就是通过v-bind或v-model绑定的值，动态值可以是任意数据类型，包括函数。
- props不接收事件，指令。

attrs
- attrs会被动接收props中没有声明的值，一旦props主动声明接收了，attrs中就不会接收。
- attrs不仅可以接收值，还能接收事件，但是也不能接收指令。

##