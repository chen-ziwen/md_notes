> 在日常开发中，可能会遇到需要多层传递的事件，比如孙子需要传递一个事件由爷爷来触发，这个时候普通的事件写法是没办法触发的。Vue3 中 爷孙通信其实很简单 ，v-bind:$attrs 写在父亲组件作为通信媒介即可。
> 
> 参考链接：https://blog.csdn.net/qq_45616003/article/details/121561312 

- 在Vue2中，爷孙之间的事件想要触发会利用到"\$listeners"，只要在中间层父组件上写上v-on="\$listeners"，这样即可完成多层事件的传递与绑定。
- 在Vue3中，v-on="\$listeners"被移除，这个时候想要完成组件之间的事件通信时，必须在中间层父组件上写v-bind=‘\$attrs’，这样就可以实现多层事件之间的传递了。
```javascript
// vue3中的写法
<template>
    <SelfComponent v-bind="$attrs"
        测试
    </SelfComponent>
</template>

// 等同于 vue2中如此写法
<template>
    <SelfComponent v-bind="$attrs" v-on="$listeners"
        测试
    </SelfComponent>
</template>
```
==补充==
在Vue3中，\$attrs可以接收除了被props接收以外的所有信息，包括事件，包括style，className。（如果组件props不接受任何信息，则添加在组件上的全部信息都会被放到$attrs对象上）