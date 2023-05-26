> 工作中没怎么接触rem，em这种自适应单位，这边我来总结一下
> 参考链接：
> [rem](http://www.muzhuangnet.com/show/57129.html)
>[rem详细教程]( https://www.jianshu.com/p/ccbe9eb285e2)
1. rem 单位的值是相对于html根元素的font-size的值， 因为font-size的默认值为16px，所以1rem也就为16px，移动端的屏幕大小不一样，如果使用px会导致布局错乱。rem怎么使用呢，例如一份设计稿的宽度为750px，ipone6的屏幕宽度为375px，将html的font-size 设置为10px，也就是说，那么总宽度就是32.5rem，如果我想要在屏幕宽度为750px的设备上查看该网页的话，只需要将html根元素上的font-size改为20px，即可完美适应750px宽度的屏幕。

2. 总得来说就是，rem这个单位是动态的，想要在不同像素的屏幕上完美适配的话，只需要计算一下屏幕与设计稿的比例，动态调整rem的初始值，就可以完成移动端的大小屏幕适配。