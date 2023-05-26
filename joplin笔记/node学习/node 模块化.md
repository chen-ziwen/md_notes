## 三大模块
![c5540fc539b860e7e1e1fc5e2afbd822.png](../_resources/c5540fc539b860e7e1e1fc5e2afbd822.png)
### 加载模块
![5ee69864b160c23951cf113a1b124cde.png](../_resources/5ee69864b160c23951cf113a1b124cde.png)

### require知识点
- 当我们使用require导入模块时，路径使用相对路径，例如 ./a/b. ，且.js后缀可以省略，同时呢，被引入的模块会自动调用。
- 使用require导入模块时，默认导入的是该模块中的module.exportsd对象，也就是`module.exports={}`，所以如果module.exports没有暴露数据的化，require引入的也就是空对象。
- module.exports可以简写成exports
![ce10224e41c850e83d567468369ef020.png](../_resources/ce10224e41c850e83d567468369ef020.png)
![2836eb688a08ac508990780b5eb9ebe8.png](../_resources/2836eb688a08ac508990780b5eb9ebe8.png)
- ==永远以module.exports的指向为准。==
![9bf667212071db66e17479f340ccc601.png](../_resources/9bf667212071db66e17479f340ccc601.png)
### commonjs 规范
![6481174b25ff4dd0d98d138e4b252710.png](../_resources/6481174b25ff4dd0d98d138e4b252710.png)
