---
layout: post
title:  "不定宽度父元素内部文本如何使用text-overflow属性"
date:   2018-06-06 18:08:54
---

使用text-overflow的时候通常都会添加max-width属性，用来定义元素的最大宽度，但这个值通常为固定宽度、如果父元素宽度不定该如何设置样式？

效果图：

正常：
![](../pics/宽度不定使用text-overflow2.png)

缩小宽度：
![](../pics/宽度不定使用text-overflow1.png)

如何实现：绝对定位

	.des-container{
      position: relative;
    }
    
    
    .des-control{
      width: 100%;
      white-space:nowrap;
      overflow:hidden;
      text-overflow:ellipsis;
      table-layout: fixed;
      position: absolute;
      left: 0;
      top: 7px;
    }
    
    
 
 画了个位置关系图：
 
 ![](../pics/宽度不定使用text-overflow3.png)