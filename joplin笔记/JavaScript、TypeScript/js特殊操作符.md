> 参考链接 [js特殊操作符](https://blog.csdn.net/weixin_43858446/article/details/117992266)
- ?? (空值合并操作符)
**当左侧值为 null 或 undefined 时，返回 ?? 符号右边的值**
ps: 0??undefined 等于0 

- .? (可选链操作符)
**允许读取位于连接对象链深处的属性的值，而不必明确验证链中的每个引用是否有效。**
ps: person?.name (等同于person&&person.name)
在正常情况下如果person不存为undefined时，这个时候读取它的属性，是会抛出错误的，而使用了可选操作符就会在它等于undefined的时候提前终止，不会抛出错误。

- ~~ （向下取整）
**两个波浪可以达到和Math.floor()一样的效果**
