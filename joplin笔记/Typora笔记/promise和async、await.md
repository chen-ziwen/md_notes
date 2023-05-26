### 异步函数 async和await

- #### async函数的返回值一定是一个promise对象， 就算没有return值，它也会返回一个成功状态的promise，res值为undefined，当有return值时，分两种情况，一种情况是return一个非promise的数据，那么这个return值会作为promise成功执行reslove（res）中的res值，如果返回的是promise，则按平常的情况进行。
    
- #### 当代码执行到await时，会停留等待，直到await右边的式子执行完毕后，才会进行下一步操作， await 后面可以一般跟promise ，它会将promise对象解包，将promise成功状态下的res值解包出来。所以它的返回值会等于promise成功状态下的reslove的参数值res，也就是一般网络请求中，需要用到的respond。
    

### promise

- ### promise内的代码就像写在window中一样，是会直接执行的，不需要去像函数一样调用。（then,catch,finally 这些操作会被推入消息队列，延后执行）
    
- <u>后续有不懂的再补充</u>

### function

- ### 当我们执行函数时，函数中的return 后面跟的如果是表达式，那么这个表达式也会执行。
    
- ### 如果函数没写返回值，默认返回undefined