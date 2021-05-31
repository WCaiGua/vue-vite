<template>
    <!--css 多行省略展开收起-->
    <div class="wrap">
        <div :class="ifUnfold ? 'text' : 'text-fold'">
            <button @click="ifUnfold = !ifUnfold" class="btn">{{ifUnfold ?'收起' :'展开'}}</button>
            浮动元素是如何定位的 浮动元素是如何定位的 浮动元素是如何定位的 浮动元素是如何定位的
            正如我们前面提到的那样，当一个元素浮动之后，它会被移出正常的文档流，然后向左或者向右平移，一直平移直到碰到了所处的容器的边框，或者碰到另外一个浮动的元素。
            正如我们前面提到的那样，当一个元素浮动之后，它会被移出正常的文档流，然后向左或者向右平移，一直平移直到碰到了所处的容器的边框，或者碰到另外一个浮动的元素。
            正如我们前面提到的那样，当一个元素浮动之后，它会被移出正常的文档流，然后向左或者向右平移，一直平移直到碰到了所处的容器的边框，或者碰到另外一个浮动的元素。
        </div>
    </div>

    <div class="compatible-wrapper">
        <input type="checkbox" id="exp">
        <div class="compatible-text" line-clamp="3">
            <!--<button class="compatible-btn">这是一个占位</button>-->
            <label class="compatible-btn" for="exp"></label>
            浮动元素是如何定位的
            正如我们前面提到的那样，当一个元素浮动之后，它会被移出正常的文档流，然后向左或者向右平移，一直平移直到碰到了所处的容器的边框，或者碰到另外一个浮动的元素。

            在下面的图片中，有三个红色的正方形。其中有两个向左浮动，一个向右浮动。要注意到第二个向左浮动的正方形被放在第一个向左浮动的正方形的右边。如果还有更多的正方形这样浮动，它们会继续向右堆放，直到填满容器一整行，之后换行至下一行。
            在前面的例子当中，浮动的元素的高度比它们所在的容器元素（是块元素）的高度小。然而如果块元素内的文本太短，不足以把块元素的大小撑到高度大于所有浮动元素的高度，我们可能会看到意想不到的效果。例如，如果上面图片中的文字只有"Lorem
            ipsum dolor sit amet,"，并且接下来是另外一个和"Floats
            Example"这个标题一样风格的标题元素，那么第二个标题元素会出现在红色的正方形之间。然而在大多数这种情况下，我们希望这个标题元素是靠左对齐的。为了实现这个效果，我们需要清除浮动。
        </div>
    </div>
<div class="compatible-wrapper">
        <div class="compatible-text" line-clamp="5">
            <button class="compatible-btn">这是一个占位</button>
            浮动元素是如何定位的
            正如我们前面提到的那样，当一个元素浮动之后，它会被移出正常的文档流，然后向左或者向右平移，一直平移直到碰到了所处的容器的边框，或者碰到另外一个浮动的元素。

            在下面的图片中，有三个红色的正方形。其中有两个向左浮动，一个向右浮动。要注意到第二个向左浮动的正方形被放在第一个向左浮动的正方形的右边。如果还有更多的正方形这样浮动，它们会继续向右堆放，直到填满容器一整行，之后换行至下一行。
            在前面的例子当中，浮动的元素的高度比它们所在的容器元素（是块元素）的高度小。然而如果块元素内的文本太短，不足以把块元素的大小撑到高度大于所有浮动元素的高度，我们可能会看到意想不到的效果。例如，如果上面图片中的文字只有"Lorem
            ipsum dolor sit amet,"，并且接下来是另外一个和"Floats
            Example"这个标题一样风格的标题元素，那么第二个标题元素会出现在红色的正方形之间。然而在大多数这种情况下，我们希望这个标题元素是靠左对齐的。为了实现这个效果，我们需要清除浮动。
        </div>
    </div>
</template>

<script>
export default {
  name: 'ForEllipsis',
  components: {},
  data() {
    return {
      ifUnfold: false,//unfold展开
    }
  },
  methods: {}
}
</script>
<style>

    [line-clamp='1']{
        max-height:1.5em;
    }
    [line-clamp='3']{
        max-height:4.5em;
    }
    [line-clamp='5']{
        max-height:7.5em;
    }
    .wrap {
        display: flex;
    }

    .text, .text-fold {
        font-size: 14px;
        line-height: 1.5;
        text-align: left;
    }

    .text-fold {
        display: -webkit-box;
        -webkit-box-orient: vertical;
        -webkit-line-clamp: 3;
        overflow: hidden;
    }

    .text::before, .text-fold::before {
        content: '';
        float: right;
        width: 0;
        /*height:100%;*/
        height: calc(100% - 20px);
        /*margin-bottom:-24px;*/
        background-color: orangered;
    }

    .btn {
        float: right;
        clear: both;
        height: 20px;
        line-height: 20px;
        padding: 0 8px;
    }

    .compatible-wrapper {
        display: flex;
        margin: 50px auto;
        width: 800px;
        overflow: hidden;
        border-radius: 8px;
        padding: 15px;
        box-shadow: 20px 20px 60px #bebebe, -20px -20px 60px #fff;
        resize: auto;
    }

    .compatible-text {
        position: relative;
        font-size: 20px;
        line-height: 1.5;
        /*max-height: 4.5em;*/
        overflow: hidden;
        text-overflow: ellipsis;
        text-align: justify;
        transition:.3s max-height;
    }

    .compatible-text::before {
        content: '';
        height: calc(100% - 26px);
        float: right;
    }
    .compatible-text::after{
        content: '';
        width:100%;
        height: 100%;
        position: absolute;
        background-color: #fff;
    }

    .compatible-btn {
        position: relative;
        float: right;
        clear: both;
        margin-left: 20px;
        font-size: 16px;
        padding: 0 8px;
        background-color: #3f51b5;
        line-height: 24px;
        border-radius: 4px;
        color: #fff;
        cursor: pointer;
        border: 0;
    }

    .compatible-btn::before {
        content: '...';
        position: absolute;
        left: -5px;
        color: #333;
        transform: translateX(-100%);
    }
    .compatible-btn::after{
        content: '展开';
    }
    #exp{
        display: none;
    }
    #exp:checked+.compatible-text{
        /*如果给max-height设置一个合适的值，注意，是合适的值，可以加上过渡动画*/
        max-height: 900px;
    }
    #exp:checked+.compatible-text::after{
        visibility: hidden;
    }
    #exp:checked+.compatible-text .compatible-btn::before{
        visibility: hidden;
    }
    #exp:checked+.compatible-text .compatible-btn::after{
        content:'收起'
    }
</style>

