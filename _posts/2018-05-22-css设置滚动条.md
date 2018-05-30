滚动条伪元素指示对象应该使用自定义滚动条。当这个伪元素存在时，WebKit将关闭其内置的滚动条渲染，并使用CSS中提供的信息。

> ::-webkit-scrollbar {
> 
>     width: 5px;
>     height: 5px;
> }

滚动条元素的宽度和高度属性表示垂直滚动条的宽度和水平滚动条的高度。也可以为这些值指定百分比，在这种情况下，滚动条将占用视口区域的百分比。

滚动条由滚动条按钮和轨道组成。赛道本身又被细分为赛道和大拇指。跟踪片代表拇指上方和下方的区域。

此外，现在可以调整滚动条的角落，以及可调整大小的textareas使用的调整器。

这里是所有新的伪元素的完整列表。所有这些伪元素都必须以前缀-webkit-。

> scrollbar - 滚动条整体部分，其中的属性有width,height,background,border（就和一个块级元素一样）等
> 
> scrollbar-button - 滚动条两端的按钮。可以用display:none让其不显示，也可以添加背景图片，颜色改变显示效果。
> 
> scrollbar-track -  外层轨道。可以用display:none让其不显示，也可以添加背景图片，颜色改变显示效果。
> 
> scrollbar-track-piece - 内层轨道，滚动条中间部分（除去）。
> 
> scrollbar-thumb - 滚动条里面可以拖动的那部分
> 
> scrollbar-corner - 边角

> resize - 定义右下角拖动块的样式

滚动条中的各个部分和DOM中块级元素是一样的。通过::-webkit-scrollbar等就类似于原来所说的CSS中的选择器。而{}中的属性，你就像控制一般块级元素一样简单

这些对象中的每一个都可以用边框，阴影和背景图像等来创建样式，以创建完全自定义的滚动条，只要按钮放置和点击行为，仍然会遵守操作系统的设置。

下面的伪类已经被引入并且可以被应用于伪元素。

> :horizontal - 水平伪类适用于任何具有水平方向的滚动条。

> :vertical - 垂直伪类适用于任何垂直方向的滚动条。

> :decrement - 递减伪类适用于按钮和曲目片段。它指示按钮或轨道片段在使用时是否将递减视图的位置（例如，在垂直滚动条上，左侧水平滚动条上）。
> 
> :increment - 增量伪类应用于按钮和曲目片段。它指示按钮或轨道片段在使用时是否将增加视图的位置（例如，在垂直滚动条上，在水平滚动条上的右边）。
> 
> :start - 开始伪类适用于按钮和轨道片段。它指示对象是否放在拇指之前。
> 
> :end - 结束伪类适用于按钮和曲目片段。它指示对象是否放在拇指后面。
> 
> :double-button - 双按钮伪类应用于按钮和曲目片段。它用于检测按钮是否位于滚动条同一端的一对按钮的一部分。对于轨道部件，它指示轨道部件是否邻接一对按钮。
> 
> :single-button - 单按钮伪类适用于按钮和跟踪片段。它用于检测按钮本身是否在滚动条的末尾。对于轨道片段，它指示轨道片段是否邻接单个按钮。
> 
> :no-button - 适用于跟踪棋子并指示棋子是否跑到滚动条的边缘，即在棋子的那一端没有按钮。
> 
> :corner-present - 适用于所有滚动条，并指示滚动条角是否存在。
> 
> :window-inactive - 适用于所有滚动条，并指示包含滚动条的窗口当前是否处于活动状态。（在最近的夜晚，这个伪类现在也适用于:: selection，我们计划扩展它以处理任何内容，并将其作为一个新的标准伪类提出来。）

另外：enabled，：disabled，：hover和：active伪类也可用于滚动条。

显示属性可以设置为无，以隐藏特定的部分。

## 举例：
HTML：


<div`` class="inner">

    <div class="innerbox">
        <p style="height:200px;">这是内容111</p>
        <p style="height:400px;">这里是内容222</p>
        <p>这里是内容333</p>
    </div>
</div>

css:

.inner{

    width: 265px;
    height: 400px;
    position: absolute;
    top: 33px;
    left: 13px;
    /*cursor: pointer;*/
    overflow:hidden;
}

.innerbox{

    overflow-x: hidden;
    overflow-y: auto;
    color: #000;
    font-size: .7rem;
    font-family: "\5FAE\8F6F\96C5\9ED1",Helvetica,"黑体",Arial,Tahoma;
    height: 100%;
}

/ * 滚动条样式 * /

.innerbox::-webkit-scrollbar {/ * 滚动条整体样式 * /

    width: 4px;     /*高宽分别对应横竖滚动条的尺寸*/
    height: 4px;
}

.innerbox::-webkit-scrollbar-thumb {/ * 滚动条里面小方块 * /

    border-radius: 5px;
    -webkit-box-shadow: inset 0 0 5px rgba(0,0,0,0.2);
    background: rgba(0,0,0,0.2);
}

.innerbox::-webkit-scrollbar-track {/ * 滚动条里面轨道 * /

    -webkit-box-shadow: inset 0 0 5px rgba(0,0,0,0.2);
    border-radius: 0;
    background: rgba(0,0,0,0.1);
}
