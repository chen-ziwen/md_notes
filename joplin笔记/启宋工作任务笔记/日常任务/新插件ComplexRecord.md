v-for渲染多选框选择的标签，去除标签就不渲染那一项

1. 数据问题
2. 循环data对象,监听this.config.messageModule.value，用v-show来判断是否要展示，只要遍历出来的key不包含在这个this.mData.value.listKey中，就隐藏（用includes来判断）。