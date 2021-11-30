<template>
  <el-carousel :interval="4000" class="carousel">
    <el-carousel-item v-for="item in swiperData" :key="item">
      <el-image :src="item" fit="fill"></el-image>
    </el-carousel-item>
  </el-carousel>
</template>

<script>
export default {
  name: "Carousel",
  data() {
    return {
      swiperData: [
        require("./assets/section-img1.png"),
        require("./assets/section-img2.png"),
        require("./assets/section-img8.png"),
      ],
    };
  },
};
</script>

<style>
.carousel {
  height: 580px;
  display: none;
}
.el-carousel__container {
  height: 100% !important;
}
@media (max-width: 768px) {
  .carousel {
    display: block;
    height: 200px;
  }
  #app {
    background: #f9f9f9;
  }
}
</style>