<template>
  <div class="index-carousel" style="height: 514px; width: 100%;">
    <el-carousel style="height: 514px;">
      <el-carousel-item v-for="item in data" :key="item">
        <el-image style="width: 100%;" :src="item.src"></el-image>
      </el-carousel-item>
    </el-carousel>
  </div>
</template>

<script>
  export default {
    name: "carousel",
    data() {
      return {
        data: [
          {src: "/v2_rihpjs.png"},
          {src: "/v2_rihpjs.png"},
          {src: "/v2_rihpjs.png"},
          {src: "/v2_rihpjs.png"},
        ],
      }
    }
  }
</script>

<style >
  .index-carousel .el-carousel__container {
    height: 514px;
  }

</style>
