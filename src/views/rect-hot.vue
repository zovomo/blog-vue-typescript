<template>
  <div class="item" :style="{ left, top }"></div>
</template>

<script lang="ts">
// 这是波浪效果，要先在 public index.html 里面引用了 three.min.js 才能用

import { Component, Vue } from "vue-property-decorator";

@Component({})
export default class Home extends Vue {
  private left = "0";
  private top = "0";
  private drag = false;
  private start = 0;
  private down(e: any) {
    this.left = e.screenX;
    this.top = e.screenY;
    this.drag = true;

    console.log(e, "main down");
  }
  private move(e: any) {
    // if (!this.drag) return;
    // const offset =
    this.left = e.target.parentNode.offsetLeft + "px";
    this.top = e.target.parentNode.offsetTop + "px";
    console.log(e, "main move");
  }
  private up(e: any) {
    this.drag = false;
    console.log("main up");
  }

  private downTop(e: any) {
    console.log("TopBar down");
  }
  private moveTop(e: any) {
    console.log("TopBar move");
  }
  private upTop(e: any) {
    console.log("TopBar up");
  }

  private downRight(e: any) {
    console.log("RightBar down");
  }
  private moveRight(e: any) {
    console.log("RightBar move");
  }
  private upRight(e: any) {
    console.log("RightBar up");
  }

  private downBottom(e: any) {
    console.log("BottomBar down");
  }
  private moveBottom(e: any) {
    console.log("BottomBar move");
  }
  private upBottom(e: any) {
    console.log("BottomBar up");
  }

  private downLeft(e: any) {
    console.log("LeftBar down");
  }
  private moveLeft(e: any) {
    console.log("LeftBar move");
  }
  private upLeft(e: any) {
    console.log("LeftBar up");
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
