<template>
  <div>
    <div class="bar">
      <div style="width: 80%;">
        <el-row style="width: 100%">
          <el-col :span="5" class="center">
            <div>
              <slot name="title"/>
            </div>
          </el-col>
          <el-col :span="14" class="center">
            <div style="min-width: 1200px;">
              <slot name="content"/>
            </div>
          </el-col>
          <el-col :span="5" class="center">
            <slot name="phone"/>
          </el-col>
        </el-row>
      </div>
    </div>
    <div style="height: 80px;"></div>
  </div>
</template>

<script>
  export default {
    name: "bar"
  }
</script>

<style scoped>
  .bar {
    display: flex;
    position: fixed;
    top: 0;
    z-index: 9999;
    background: #ffffff;
    width: 100%;
    justify-content: center;
    height: 80px;
    line-height: 80px;
    text-align: center;
  }
 .bar .center {
   display: flex;
   justify-content: center;
 }
</style>
