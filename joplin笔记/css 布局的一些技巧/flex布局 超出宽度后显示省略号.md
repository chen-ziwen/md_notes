> 在项目开发中，遇到这么一个问题，就是flex布局和显示省略号的冲突，当我想要某一个盒子为自适应放大时，等到这个盒子的宽度达到一个临界点后，里面的内容显示省略号。 这个时候只需要两行代码：
> 参考链接：https://blog.csdn.net/qq_31411389/article/details/122707812?utm_medium=distribute.pc_aggpage_search_result.none-task-blog-2~aggregatepage~first_rank_ecpm_v1~rank_v31_ecpm-1-122707812-null-null.pc_agg_new_rank&utm_term=flex%E5%B8%83%E5%B1%80css+%E8%B6%85%E5%87%BA%E9%83%A8%E5%88%86%E7%94%A8%E7%9C%81%E7%95%A5%E5%8F%B7%E6%98%BE%E7%A4%BA&spm=1000.2123.3001.4430

```css
/* 意思就是将宽度和高度都设为0，全部的高度和宽度都由flex-来撑开 */
  flex-grow:1;
  width:0px; //
/* 必须指定宽度为0，不然会出现自适应盒子将其他内容挤出最外层盒子的现象 */

  flex-grow:1;
  height:0px; 
/* 同样有效 */
```

