<template>
  <index-content-container style="border-bottom: 1px solid #c6c6c6; line-height: 35px; height: 35px;">
    <el-row>
      <el-col :span="10">
        <div style="display: flex;">
          <div v-for="(item, index) in data" style="display: flex;">
            <div :style="{'color': index === 0 ? 'unset' : '#2468F2'}">{{item.title}}</div>
            <div v-if="index !== data.length - 1">>></div>
          </div>
        </div>
      </el-col>
      <el-col :span="14">
        <div style="display: flex; justify-content: space-around; cursor: pointer;">
          <div v-for="item in barData || []">
            {{item.title}}
          </div>
        </div>
      </el-col>
    </el-row>
  </index-content-container>
</template>

<script>
  import IndexContentContainer from "./index-content-container";
  export default {
    name: "index-content-nav",
    components: {IndexContentContainer},
    data() {
      return {
        barData: [
          {title: "企业介绍"},
          {title: "荣誉资质"},
          {title: "新闻动态"},
          {title: "加入我们"},
          {title: "联系我们"},
        ],
        data: [
          {title: "首页"},
          {title: "关于我们"},
        ]
      }
    }
  }
</script>

<style scoped>

</style>
