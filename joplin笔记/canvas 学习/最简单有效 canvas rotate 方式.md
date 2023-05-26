>> 最近在做canvas的时候，被canvas的rotate困扰了很久，在内网查了好多资料，都不靠谱，最后去外网才解决了这个问题。步骤如下：

```javascript
 ctx.save(); // 先保存原始状态 （这边保存的是原始的坐标）
 ctx.translate(x,y); // 需要旋转图像的中心坐标
 ctx.rotate(x*Math.PI*180); 需要旋转的图像
 ctx.translate(-x,-y); // 旋转到初始点
 ctx.drawImage(img, x, y, w, h); // 绘制图像
 ctx.restore(); // 还原坐标 不影响已经绘制完成的图像
```