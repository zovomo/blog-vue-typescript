<template>
  <div class="d"></div>
  <!-- <div id="edit" @mouseup="up" @mousedown="down" @mousemove="move"></div> -->

  <!-- <div class="project left" style="backgroud: black"> -->

  <!-- <LoadingCustom v-if="isLoading"></LoadingCustom>
    <LoadEnd v-if="isLoadEnd"></LoadEnd> -->
</template>
<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
// import $ from "jquery";

@Component({
  components: {}
})
export default class Timeline extends Vue {
  startX = 0;
  startY = 0;
  private created() {
    console.log(this.$attrs);
  }
  //   down(e: any) {
  //     var div = document.createElement("div");
  //     div.addEventListener("mousedown", function(e) {
  //       div.style.left = e.clientX + "px";
  //       div.style.top = e.clientY + "px";
  //     });
  //     div.addEventListener("mousemove", function(e) {
  //       div.style.left = e.clientX + "px";
  //       div.style.top = e.clientY + "px";
  //     });
  //     div.className = "select-box";
  //     div.id = "select-box";
  //     div.style.left = e.clientX + "px";
  //     div.style.top = e.clientY + "px";
  //     div.style.width = 0 + "px";
  //     div.style.height = 0 + "px";
  //     document.getElementById("edit").appendChild(div);
  //     console.log(e, 11111111111111);
  //   }
  //   move(e: any) {
  //     console.log(e, 222222222);
  //     var startX = this.startX;
  //     var startY = this.startY;
  //     var evt = e;
  //     var rectLeft = startX - e.clientX > 0 ? e.clientX - 5 : this.startX + 5;
  //     var rectTop = startY - e.clientY > 0 ? e.clientY - 5 : this.startY + 5;
  //     var rectHeight = Math.abs(startY - e.clientY);
  //     var rectWidth = Math.abs(startX - e.clientX);
  //     var div = document.getElementById("select-box");
  //     console.log(rectWidth, 888888888888);
  //     if (div) {
  //       div.style.width = e.clientX + "px";
  //       div.style.height = e.clientY + "px";
  //     }
  //   }
  //   up(e: any) {
  //     console.log(e, 3333);
  //   }
  //   // lifecycle hook
  //   mounted(): void {
  //     var startX = 0,
  //       startY = 0,
  //       flag = false;
  //     // document.getElementById("edit").addEventListener("mousedown", function(e) {
  //     //   console.log(e, 66666);

  //     //   var evt = window.event || e;
  //     //   startX = e.clientX;
  //     //   startY = e.clientY;
  //     //   var div = document.getElementById("select-box");
  //     //   if (div == null) {
  //     //     div = document.createElement("div");
  //     //   }
  //     //   div.id = "select-box";
  //     //   div.className = "select-box";
  //     //   div.style.left = e.offsetX + "px";
  //     //   div.style.top = e.offsetY + "px";
  //     //   div.style.width = 0;
  //     //   div.style.height = 0;
  //     //   document.getElementById("edit").appendChild(div);
  //     // });

  //     // document.getElementById("edit").addEventListener("mousemove", function(e) {
  //     //   console.log(e.offsetX, e.offsetY);

  //     // var evt = window.event || e;
  //     // var rectLeft = startX - e.clientX > 0 ? e.clientX - 5 : startX + 5;
  //     // var rectTop = startY - e.clientY > 0 ? e.clientY - 5 : startY + 5;
  //     // var rectHeight = Math.abs(startY - e.clientY);
  //     // var rectWidth = Math.abs(startX - e.clientX);
  //     // var div = document.getElementById("select-box");
  //     // console.log(rectWidth, 888888888888);
  //     // if (div) {
  //     //   div.style.width = rectWidth + "px";
  //     //   div.style.height = rectHeight + "px";
  //     // }

  //     // $("#select-box")
  //     //   .css("left", rectLeft)
  //     //   .css("top", rectTop)
  //     //   .css("width", rectWidth)
  //     //   .css("height", rectHeight)
  //     //   .css("display", "block")
  //     //   .css("zIndex", 100);
  //     // });

  //     // document.getElementById("edit").on("mouseup", function(e) {
  //     //   console.log(e, 9999);

  //     //   document
  //     //     .getElementById("edit")
  //     //     .removeEventListener("mousemove", function(ee) {
  //     //       console.log(ee);
  //     //     });
  //     // });
  //   }
}
</script>
<style lang="less">
#edit {
  width: 800px;
  height: 800px;
  background: blue;
  position: relative;
}
#select-box,
.select-box {
  background: red;
  position: absolute;
  z-index: 3;
}
.left {
  background: black;
}
.resize {
  cursor: w-resize;
}
.drag {
  background: red;
  height: 40px;
  cursor: -moz-grab;
}
.project {
  overflow: hidden;
  padding: 40px 0;
  .el-col-pointer {
    cursor: pointer;
  }
  .content {
    height: 70px;
    text-overflow: ellipsis;
  }
  .image {
    width: 100%;
    height: 250px;
  }
}
</style>
