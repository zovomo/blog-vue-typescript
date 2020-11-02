<template>
  <div class="content" @mouseup="up" @mousedown="down" @mousemove="move"></div>
</template>

<script lang="ts">
// 这是波浪效果，要先在 public index.html 里面引用了 three.min.js 才能用

import { Component, Vue } from "vue-property-decorator";

@Component({})
export default class Home extends Vue {
  private startX = 0;
  private startY = 0;
  private drag = false
  private down(e: any) {
      this.drag = true
  }
  private move(e: any) {
      if (!this.drag) return
    this.@emit('move', e.off)
    

  }
  private up(e: any) {
    console.log(e, 3333);
  }
}
</script>
<style lang="less" scoped>
.item {
  position: absolute;
  left: 20px;
  top: 50px;
  width: 200px;
  height: 110px;
  z-index: 2;
  background: #ccc;
  .content {
    position: absolute;
    width: 100%;
    height: 100%;
    background: chartreuse;
    position: absolute;
    cursor: move;
  }
  .top {
    width: 100%;
    height: 5px;
    top: 0;
    cursor: n-resize;
    background: rgb(105, 51, 77);
    position: absolute;
    z-index: 998;
  }
  .right {
    width: 5px;
    height: 100%;
    top: 0;
    right: 0;
    cursor: e-resize;
    background: rgb(162, 190, 35);
    position: absolute;
    z-index: 998;
  }
  .bottom {
    width: 100%;
    height: 5px;
    bottom: 0;
    cursor: s-resize;
    background: rgb(19, 173, 40);
    position: absolute;
    z-index: 998;
  }
  .left {
    width: 5px;
    height: 100%;
    top: 0;
    cursor: w-resize;
    background: rgb(15, 133, 78);
    position: absolute;
    z-index: 998;
  }
}
</style>
