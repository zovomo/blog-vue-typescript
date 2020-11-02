<template>
  <div class="home">
    <!-- <div class="pannel" @mouseup="up" @mousedown="down" @mousemove="move"></div> -->
    <!-- <div class="rect-item"></div> -->
    <!-- <rect-hot></rect-hot> -->
  </div>
</template>

<script lang="ts">
// 这是波浪效果，要先在 public index.html 里面引用了 three.min.js 才能用

import { Component, Vue } from "vue-property-decorator";
import rectHot from "./rect-hot.vue";

@Component({ components: { rectHot } })
export default class Home extends Vue {
  startX = 0;
  startY = 0;
  private create() {
    console.log(this.$attrs, 2222);
  }
  down(e: any) {
    // var div = document.createElement("div");
    // div.className = "select-box";
    // div.id = "select-box";
    // div.style.left = e.clientX + "px";
    // div.style.top = e.clientY + "px";
    // div.style.width = 0 + "px";
    // div.style.height = 0 + "px";
    // document.getElementById("edit").appendChild(div);
    // console.log(e, 11111111111111);
  }
  move(e: any) {
    // console.log(e, 222222222);
    var startX = this.startX;
    var startY = this.startY;
    var evt = e;
    var rectLeft = startX - e.clientX > 0 ? e.clientX - 5 : this.startX + 5;
    var rectTop = startY - e.clientY > 0 ? e.clientY - 5 : this.startY + 5;
    var rectHeight = Math.abs(startY - e.clientY);
    var rectWidth = Math.abs(startX - e.clientX);
    var div = document.getElementById("select-box");
    // console.log(rectWidth, 888888888888);
    if (div) {
      div.style.width = e.clientX + "px";
      div.style.height = e.clientY + "px";
    }
  }
  up(e: any) {
    // console.log(e, 3333);
  }
}
</script>
<style lang="less" scoped>
.home {
  width: 400px;
  height: 719px;
  border: 1px solid #ccc;
  border-radius: 10px;
  margin: 20px auto;
  position: relative;
  .pannel {
    height: 100%;
    background: rgb(151, 225, 228);
  }
}
</style>
