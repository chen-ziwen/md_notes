> 打算手动实现js的一些原生方法
### filter方法
```javascript
 Array.prototype.myFilter = function (fun) {
        let newArr = [];
        let len = this.length; 
  // 这个this指向为包含fun函数的方法，例如数组要使用，则是arr.myFilter(),this指向则为arr。
        for (let i = 0; i < len; i++) {
  // 这一步是调用函数,因为符合条件的函数会返回true，不符合返回false，返回true则项推入新数组
            if (fun(this[i], i, this)) {
	// 这一步也很巧妙，因为filter必须有返回值，返回值为true时，将当前值推入新数组。
                if (typeof this[i] === 'object') {
                    newArr.push(JSON.parse(JSON.stringify(this[i])));
                } else {
                    newArr.push(this[i]);
                }
            }
        }
        return newArr;
    }
```
### map方法
```javascript
 Array.prototype.myMap = function (fun) {
        let newArr = [];
        let len = this.length;
        for (let i = 0; i < len; i++) {
            if (typeof this[i] === 'object') {
                newArr.push(JSON.parse(JSON.stringify(fun(this[i], i, this))));
            } else {
                newArr.push(fun(this[i], i, this))
            }
        }
        return newArr;
    }
```
