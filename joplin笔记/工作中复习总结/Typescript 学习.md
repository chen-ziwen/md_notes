# Typescript 学习

学习链接 :[http://ts.xcatliu.com/basics/type-of-object-interfaces.html](http://ts.xcatliu.com/basics/type-of-object-interfaces.html)

## 重点：

1. Ts类型定义可以找出很多js找不出的问题，会避免很多的错误操作。

```ts
eg. 
     let a:String = "我是字符串类型"
     let b:Boolean = true
```

​         ts学到断言类型 

## ts 泛型函数

***
软件工程中，我们不仅要创建一致的定义良好的API，同时也要考虑可重用性。组件不仅能够支持当前的数据类型，同时也能支持未来的数据类型，这在创建大型系统时为你提供了十分灵活的功能。

可以使用泛型来创建可重用的组件，一个组件可以支持多种类型的数据。 这样用户就可以以自己的数据类型来使用组件。

- 泛型是指在定义函数，接口，类的时候，不预先指定具体的类型，而在使用的时候再指定类型的一种特性。

- 泛型<T> T类型变量，表示任何类型。帮助我们捕获用户传入的类型（比如：number）

- 传入泛型用 <number>,尖括号括起来的

- 创建泛型函数时，编译器要求你在函数体必须正确的使用这个通用的类型
 
***

```js
//添加类型变量T，T帮助我们捕获用户传入的类型（比如：number）
//参数类型为T，返回值类型为T
function fun1<T>(x: T): T {
    return x;
}
//这里传入T为string类型，创建的时候不定义类型，等到使用的时候再定义类型
fun1<string>('a')

```

## interface 和 type 
 这两者的功能几乎是一样的，在大部分情况下自由选择使用下面来说说两者的不同。

1. type可以定义所有的数据类型，但是interface只能定义对象，函数，类，类型。

```JS
type hello= string 

let a:hello = '你好'

interface hello = {
    //不能像上面那么写
}
```

​          2. interface定义后可以随时添加，但type不能修改。因为同名的接口会合并，所以可以随时添加新的属性。

​          3. type可以继承type也可以继承interface,继承的符号用&，interface可以继承interface也可以继承type 继承符号是

​              extends。

​          4. 类可以实现接口，也可以实现type。

##      类型断言

1.   let a =<number>()

##      非空断言运算符（后缀`!`）

1. TypeScript 还具有一种特殊的语法，用于在不进行任何显式检查的情况下从类型中删除`null`和删除`undefined`。`!`在任何表达式之后写实际上是一个类型断言，该值不是`null`or `undefined`：

```
function liveDangerously(x?: number | null) {
  // No error
  console.log(x!.toFixed());
}
```

