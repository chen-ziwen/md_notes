> 工作中，一般都是直接用ref，或者reactive，虽然也没有什么影响，但是如果数据量一大，可能就有性能上的问题

### shallowRef()

`ref()`的浅层作用形式

- 类型

```js
function shallowRef<T>(value: T): ShallowRef<T>

interface ShallowRef<T> {
  value: T
}
```

- 详细信息
    和 `ref()` 不同，浅层 ref 的内部值将会原样存储和暴露，并且不会被深层递归地转为响应式。只有对 `.value` 的访问是响应式的。
    `shallowRef()` ==常常用于对大型数据结构的性能优化或是与外部的状态管理系统集成。==
    例如当`shallowRef()`中的数据是一个对象类型的时候，==当对象中的某一个值变化时，shallowRef是没有响应式，只有当一整个对象发生替换时，才有响应式。==
- 示例

```js
const state = shallowRef({ count: 1 })

// 不会触发更改，对value外的数据没反应
state.value.count = 2

// 会触发更改，因为整个对象替换了
state.value = { count: 2 }
```

### triggerRef()

强制触发依赖于一个浅层 ref 的副作用，这通常在对浅引用的内部值进行深度变更后使用。

- 类型

```js
function triggerRef(ref: ShallowRef): void
```

- 示例

```js
const shallow = shallowRef({
  greet: 'Hello, world'
})
```

```js

// 触发该副作用第一次应该会打印 "Hello, world"
watchEffect(() => {
// 因为watchEffect副作用会自动触发一次
console.log(shallow.value.greet)
})

// 这次变更不应触发副作用，因为这个 ref 是浅层的
// 原本是不应该触发的，因为改变的不是.value，副作用也监听不到
// 但是通过triggerRef可以强制让浅层ref触发副作用。
shallow.value.greet = 'Hello, universe'

// 打印 "Hello, universe"
triggerRef(shallow)
```

### shallowReactive()
`reactive()` 的浅层作用形式。

- 类型

```ts
function shallowReactive<T extends object>(target: T): T
```
- 详细信息
和 ` reactive() `不同，这里没有深层级的转换：一个浅层响应式对象里只有根级别的属性是响应式的。属性的值会被原样存储和暴露，这也意味着值为 ref 的属性不会被自动解包了。

- ==谨慎使用==
 浅层数据结构应该只用于组件中的根级状态。请避免将其嵌套在深层次的响应式对象中，因为它创建的树具有不一致的响应行为，这可能很难理解和调试。

- 示例

```js
const state = shallowReactive({
  foo: 1,
  nested: {
    bar: 2
  }
})
// 更改状态自身的属性是响应式的
state.foo++

// ...但下层嵌套对象不会被转为响应式
isReactive(state.nested) // false

// 不是响应式的
state.nested.bar++
```
