<template>
  <div class="home">
    <div class="pannel"></div>
    <div class="rect-item"></div>
  </div>
</template>

<script lang="ts">
// 这是波浪效果，要先在 public index.html 里面引用了 three.min.js 才能用

import { Component, Vue } from "vue-property-decorator";

@Component({})
export default class Home extends Vue {}
</script>
<style lang="less" scoped>
.home {
  width: 400px;
  height: 719px;
  border: 1px solid #ccc;
  border-radius: 10px;
  margin: 20px auto;
  .pannel {
    height: 100%;
    background: cadetblue;
  }
  .rect-item {
    position: absolute;
    left: 20px;
    top: 50px;
    background: #ccc;
  }
}
</style>
