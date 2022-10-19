<template>
  <div class="index-carousel" style="height: 514px; width: 100%;">
    <el-carousel style="height: 514px;">
      <el-carousel-item v-for="(item, index) in data" :key="'item' + index">
        <el-image style="width: 100%; height: 514px;" :src="item.src"></el-image>
      </el-carousel-item>
    </el-carousel>
  </div>
</template>

<script>
  import {getImageUrl} from "../../../util/util";

  export default {
    name: "carousel",
    data() {
      return {
        data: [
          {src: getImageUrl("/home/v2_rihpjs.png")},
          {src: getImageUrl("/home/v2_rihq2o.png")},
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
