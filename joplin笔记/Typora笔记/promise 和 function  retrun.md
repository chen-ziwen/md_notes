# promise 和 function  retrun
## promise 
- ### promise内的代码就像写在window中一样，是会直接执行的，不需要去像函数一样调用。（then,catch,finally 这些操作会被推入消息队列，延后执行）
## function
- ### 当我们执行函数时，函数中的retrun 后面跟的如果是表达式，那么这个表达式也会执行。
- ### 如果函数没写返回值，默认返回undefined
