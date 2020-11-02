<template>
  <div id="app" class="container">
    <canvas
      id="myCanvas"
      width="550"
      height="600"
      style="border:1px solid #d3d3d3;"
    ></canvas>
    <img :src="canvasImg" alt="" />
    <input
      type="file"
      id="weibo_img"
      name="weiboimg"
      class="weiboimg"
      value=""
    />
    <img
      id="ddd"
      src="https://dss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2534506313,1688529724&fm=26&gp=0.jpg"
      alt=""
    />
    <div class="popup-wrap-outer canvas-popup">
      <div class="popup-wrap-inner">
        <div class="popup-con">
          <div class="canvas-content inlineBlock">
            <div id="canvasContainer">
              <img src="" id="imgCrop" alt="" />
              <div id="canvas"></div>
            </div>
            <!-- 预览块 -->
            <!-- <div style="width:200px;height:150px">
              <div id="canvas"></div>
            </div> -->
            <div class="bottom clear">
              <p class="tip left">
                <span style="font-size:15px;">按住鼠标左键裁剪图片</span>
              </p>
              <span style="color:red; font-size:15px;"
                >裁剪比例:(小图、多图展示选:4:3, 大图展示选16:9)</span
              >
              <el-button type="primary" id="changeRatio43">4:3</el-button>
              <el-button type="primary" id="changeRatio169">16:9</el-button>
              <div class="btns right">
                <el-button type="primary" id="cancelClip">取消</el-button>
                <el-button type="primary" id="submitClip">确定</el-button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- <Nav v-if="isShowNav" /> -->
    <div class=" layout">
      <!-- <router-view /> -->
      <!-- <Slider v-if="isShowSlider"></Slider> -->
    </div>
    <!-- <ArrowUp></ArrowUp> -->
    <!-- <Footer v-show="isShowNav"></Footer> -->
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

import { isMobileOrPc } from "@/utils/utils";

// 移动端 rem 单位适配
if (isMobileOrPc()) {
  // width * 100 / 750 = width / 7.5
  // 1rem = 100px
  var width = window.screen.width;
  window.document.getElementsByTagName("html")[0].style.fontSize =
    width / 7.5 + "px";
}

@Component({
  components: {
    Nav,
    Slider,
    ArrowUp,
    Footer
  }
})
/* eslint-disable */
// @ts-nocheck
export default class App extends Vue {
  private isShowNav: boolean = false;
  private isShowSlider: boolean = false;
  private canvasImg = "";
  mounted(): void {
    function convertBase64UrlToBlob(urlData, type) {
      //去掉url的头，并转换为byte     //处理异常,将ascii码小于0的转换为大于0
      var bytes = window.atob(urlData.split(",")[1]);
      var ab = new ArrayBuffer(bytes.length);
      var ia = new Uint8Array(ab);
      for (var i = 0; i < bytes.length; i++) {
        ia[i] = bytes.charCodeAt(i);
      }
      return new Blob([ab], { type: "image/" + type });
    }

    this.routeChange(this.$route, this.$route);
    document.getElementById("weibo_img").onchange = function(e) {
      let file = document.getElementById("weibo_img").files[0];
      let c = "";
      let canvasPopup = "";
      try {
        canvasPopup = document.getElementsByClassName("canvas-popup")[0];
        // canvasPopup.style.display = "table";
        c = new CanvasClip({
          previewContainer: document.getElementById("canvasContainer"),
          source: file,
          canvasWidth: 800,
          quality: 1
        });
        console.log(c);

        document.getElementById("submitClip").onclick = function(e) {
          c.clip();
          console.log(111, c.ret64);

          if (c.ret64) {
            let uploadFile = convertBase64UrlToBlob(c.ret64, "image/jpeg");
            console.log(uploadFile);
          }
        };
      } catch (error) {}
    };
  }

  move() {}

  private created() {
    console.log(this.$attrs);
  }

  @Watch("$route")
  routeChange(val: Route, oldVal: Route): void {
    const referrer: any = document.getElementById("referrer");
    if (val.path === "/") {
      this.isShowNav = false;
      referrer.setAttribute("content", "always");
    } else {
      this.isShowNav = true;
      referrer.setAttribute("content", "never");
    }
    if (
      val.path === "/articles" ||
      val.path === "/archive" ||
      val.path === "/project" ||
      val.path === "/timeline" ||
      val.path === "/message"
    ) {
      this.isShowSlider = true;
    } else {
      this.isShowSlider = false;
    }
    if (isMobileOrPc()) {
      this.isShowSlider = false;
    }
  }
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
