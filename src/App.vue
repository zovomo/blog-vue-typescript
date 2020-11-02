<template>
  <div>
    <canvasClip></canvasClip>
  </div>
</template>
<script lang="ts">
import { Vue, Watch, Provide } from "vue-property-decorator";
import Component from "vue-class-component";
import { Route } from "vue-router";
import Nav from "@/components/nav.vue"; // @ is an alias to /src
import Slider from "@/components/slider.vue"; // @ is an alias to /src
import Footer from "@/components/footer.vue"; // @ is an alias to /src
import ArrowUp from "@/components/arrowUp.vue"; // @ is an alias to /src
import canvasClip from "./canvas-clip.vue";

import { isMobileOrPc } from "@/utils/utils";

@Component({
  components: {
    Nav,
    Slider,
    ArrowUp,
    Footer,
    canvasClip
  }
})
/* eslint-disable */
// @ts-nocheck
export default class App extends Vue {
  private isShowNav: boolean = false;
  private isShowSlider: boolean = false;
  private canvasImg = "";
  
}
</script>

<style lang="less">
@import url("./less/index.less");
@import url("./less/mobile.less");
#app {
  width: 100vw;
  height: 100vh;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  // width: 1200px;
  margin: 0 auto;
  padding-top: 61px;
}
img {
  vertical-align: bottom;
}
.canvas-popup {
  // display: none;
  text-align: center;
  .inlineBlock {
    display: inline-block;
    padding: 30px;
    background: #fff;
  }
  .bottom {
    margin-top: 10px;
    line-height: 40px;
  }
  .tip {
    font-size: 20px;
    color: #999;
  }
  .left {
    float: left;
  }
  .right {
    float: right;
  }
}
</style>
