<!--为了在加载的过程中等待效果更好，封装一个全局骨架屏组件。-->
<template>
<div class="xtx-skeleton" :style="{width,height}" :class="{shan:animated}">
<!-- 1.盒子 -->
<div class="block" :style="{backgrooundColor:bg}"></div>
<!-- 2闪效果 xtx-skeleton伪元素 -->
</div>
</template>
<script>
export default {
  name: 'XtxSkeleton',
  // 使用的时候需要动态设置高度，宽度，背景颜色，是否闪下
  props: {
    bg: {
      type: String,
      default: '#efefef'
    },
    width: {
      type: String,
      default: '100px'
    },
    height: {
      type: String,
      default: '100px'
    },
    animated: {
      type: Boolean,
      default: false
    }
  }
}
</script>
<style lang="less">
.xtx-skeleton {
  display: inline-block;
  position: relative;
  overflow: hidden;
  vertical-align: middle;
  .block {
    width: 100%;
    height: 100%;
    border-radius: 2px;
  }
}
.shan {
  &::after {
    content: "";
    position: absolute;
    animation: shan 1.5s ease 0s infinite;
    top: 0;
    width: 50%;
    height: 100%;
    background: linear-gradient(
      to left,
      rgba(255, 255, 255, 0) 0,
      rgba(255, 255, 255, 0.3) 50%,
      rgba(255, 255, 255, 0) 100%
    );
    transform: skewX(-45deg);
  }
}
@keyframes shan {
  0% {
    left: -100%;
  }
  100% {
    left: 120%;
  }
}
</style>
