##  TypeScript 防抖和节流类的实现

> 参考链接知乎：https://zhuanlan.zhihu.com/p/520748253
> 
> 参考链接简书：https://www.jianshu.com/p/53e4aae15aa4

### 1. 防抖实现
```typescript
/**
 * @class 防抖，规定时间内多次只触发一次
 * @param {Function} fun  传入一个需要防抖的函数
 * @param {number} delay  规定时间
 * @param {boolean} immediate 触发的第一次是否立即执行
 * @return {Function}  返回一个函数
 */
// 防抖完整版写法
export class Debounce {
    public use: (fun: Function, delay: number) => Function;
    constructor() {
        this.use = (fun, delay) => {
            let tiemout: NodeJS.Timeout | undefined = undefined;
            return (...args: any) => {
                clearTimeout(tiemout);
                tiemout = setTimeout(() => {
                    fun.apply(this, args);
                }, delay)
            }
        }
    }
}
// 可以这么简写
export class Debounce2 {
    public use = (fun: Function, delay: number): Function => {
        let tiemout: NodeJS.Timeout | undefined = undefined;
        return (...args: any) => {
            clearTimeout(tiemout);
            tiemout = setTimeout(() => {
                fun.apply(this, args);
            }, delay)
        }
    }
}
```

2.  使用方式

```typescript
// 引入防抖函数
import { Debounce } from '@/general/debounce';

// 需要防抖的函数
function touch(name: string, age: number) {
    console.log(`姓名${name},年龄${age}`);
}

// 传入需要防抖的函数，以及防抖的时间
const debounce = new Debounce().use(touch, 2000);

// 将参数传递给需要防抖的函数
debounce('chiko', 18)

完成 ！！！
```

### 2.节流实现
```TypeScript
/**
 * @class 节流，每间隔一段时间执行一次
 * @param {Function} fun  传入一个需要节流的函数
 * @param {number} delay  间隔的时间
 * @param {boolean} immediate 触发的第一次是否立即执行
 * @return {Function}  返回一个函数
 */
export class Throttle {
    public use: (fun: Function, delay: number, immediate?: boolean) => Function;
    constructor() {
        this.use = (fun, delay, immediate = false) => {
            let tiemout: NodeJS.Timeout | undefined = undefined;
            let flag = true;
            return (...args: any) => {
                if (immediate) {
                    fun.apply(this, args);
                    immediate = false;
                    return;
                }
                if (!flag) {
                    return;
                }
                flag = false;
                tiemout = setTimeout(() => {
                    fun.apply(this, args);
                    flag = true;
                    clearTimeout(tiemout);
                }, delay)
            }
        }
    }
}
```

