<template>
  <div>
    <section class="img-wrap">
      <img
        id="scream"
        src="https://dss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2534506313,1688529724&fm=26&gp=0.jpg"
        alt="The Scream"
      />
    </section>

    <p>Canvas:</p>
    <canvas
      id="myCanvas"
      width="800"
      height="600"
      style="border:1px solid #d3d3d3;"
    >
      您的浏览器不支持 HTML5 canvas 标签。</canvas
    >
  </div>
</template>
<script>
export default {
  mounted() {
    var c = document.getElementById("myCanvas");
    var ctx = c.getContext("2d");
    var img = document.getElementById("scream");
    img.onload = function() {
      ctx.drawImage(img, 0, 100, 300, 300, 0, 0, 300, 300);
    };
  }
};
</script>
<style lang="less" scoped>
.img-wrap {
  width: 600px;
  height: 600px;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid #ccc;
  img {
    max-width: 600px;
    max-height: 600px;
  }
}
/* #myCanvas {
  width: 600px;
  height: 600px;
  border: 1px solid #d3d3d3;
} */
</style>
