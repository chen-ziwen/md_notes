### Vue2生命周期钩子
1. beforeCreate
2. create
3. befroeMount
4. mount
5. beforeUpdata
6. updated
7. beforeDestroy
8. destroy
### Vue3生命周期钩子
1. setup
2. onBeforeMount
3. onMount
4. onBeforeUpdate
5. onUpdated
6. onBeforeMount
7. onUnmounted

### 将 Vue2 的生命周期钩子代码更新到 Vue3
>这个从Vue2 到Vue3的生命周期映射是直接从Vue 3 Composition API文档中获得的:

```
beforeCreate -> 使用 setup()

created -> 使用 setup()

beforeMount -> onBeforeMount

mounted -> onMounted

beforeUpdate -> onBeforeUpdate

updated -> onUpdated

beforeDestroy -> onBeforeUnmount

destroyed -> onUnmounted

errorCaptured -> onErrorCaptured
```

### vue3生命周期详细介绍
1. onBeforeMount – 在挂载开始之前被调用：相关的 render 函数首次被调用。
2. onMounted – 组件挂载时调用
3. onBeforeUpdate – 数据更新时调用，发生在虚拟 DOM 打补丁之前。这里适合在更新之前访问现有的 DOM，比如手动移除已添加的事件监听器。
4. onUpdated – 由于数据更改导致的虚拟 DOM 重新渲染和打补丁，在这之后会调用该钩子。
5. onBeforeUnmount – 在卸载组件实例之前调用。在这个阶段，实例仍然是完全正常的。
6. onUnmounted – 卸载组件实例后调用。调用此钩子时，组件实例的所有指令都被解除绑定，所有事件侦听器都被移除，所有子组件实例被卸载。
7. onActivated – 被 keep-alive 缓存的组件激活时调用
8. onDeactivated – 被 keep-alive 缓存的组件停用时调用。
9. onErrorCaptured – 当捕获一个来自子孙组件的错误时被调用。此钩子会收到三个参数：错误对象、发生错误的组件实例以及一个包含错误来源信息的字符串。此钩子可以返回 false 以阻止该错误继续向上传播。