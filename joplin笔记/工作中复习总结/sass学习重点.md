# sass学习重点

1. ## @mixin 混入 可以很好的去重复使用一些样式 ，可以写成函数的形式。

   ```css
   eg.
   @mixin abc($color,$l,$r) {
       color : $color; 
       background-size : $l $r
   }
   
   ```

   ## 2.@include 引入  可以引入@mixin中定义好的样式，可以传递参数。

   ​                

   ```css
    eg.
   @include abc(red,20px,20px)
   ```

   3. ## @extend 继承 可以继承别的选择器样式

      ```css
      eg.
      apple {
      color : red
      } 
      hot {
      @extend apple
      }
      ```

   4. ## & 指的是当前的父选择器

   5. ## @for  to 和@for though

   6. ## @each  in

   7. ## 等等等 其他不常用 需要时再说吧

##        3. Sass  语法

1. ### SassScript 支持 CSS 的两种字符串类型：有引号字符串 ，与无引号字符串 (unquoted strings)，如 `sans-serif` `bold`，在编译 CSS 文件时不会改变其类型。只有一种情况例外，使用 `#{}` (interpolation) 时，有引号字符串将被编译为无引号字符串，这样便于在 mixin 中引用选择器名.



1. sass maps相当于js中的对象
2. sass数组就是用圆括号括起来