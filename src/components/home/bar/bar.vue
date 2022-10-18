<template>
  <div class="bar" style="display: flex; justify-content: center; height: 60px; line-height: 60px; text-align: center;">
    <div style="width: 80%;">
      <el-row style="width: 100%">
        <el-col :span="5" class="center">
          <div>
            <slot name="title"/>
          </div>
        </el-col>
        <el-col :span="14" class="center">
          <slot name="content"/>
        </el-col>
        <el-col :span="5" class="center">
          <slot name="phone"/>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
  export default {
    name: "bar"
  }
</script>

<style scoped>
 .bar .center {
   display: flex;
   justify-content: center;
 }
</style>
