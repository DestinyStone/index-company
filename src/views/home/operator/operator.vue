<template>
  <div class="index-operator" :style="{'top': topHeight + 'px'}">
    <div class="btn" v-for="(item, index) in data" :key="'operator' + index">
      <div style="display: flex; justify-content: center;">
        <el-image style="height: 35px; width: 35px; margin-top: 10px;" :src="item.src"/>
      </div>
    </div>
    <div class="btn">
      <div style="text-align: center;" @click="handlerClickTop">
        <div style="height: 5px; line-height: 30px">
          <i class="el-icon-arrow-up"/>
        </div>
        TOP
      </div>
    </div>
  </div>
</template>

<script>
  import {getImageUrl} from "../../../util/util";

  export default {
    name: "operator",
    data() {
      return {
        topHeight: 0,
        data: [
          {
            icon: "el-icon-user",
            src: getImageUrl('/home/person.png'),
          },
          {
            icon: "el-icon-user",
            src: getImageUrl('/home/phone.png'),
          },
          {
            icon: "el-icon-user",
            src: getImageUrl('/home/wechat.png'),
          },
        ]
      }
    },
    methods: {
      handlerClickTop() {
        window.scrollTo(0, 0);
      }
    },
    mounted() {
      this.topHeight =  window.innerHeight / 2 - 150;
    }
  }
</script>

<style scoped>
  .index-operator {
    position: fixed;
    z-index: 999;
    right: 0;
    color: #2468F2;

  }
  .index-operator .btn {
    width: 60px;
    height: 60px;
    line-height: 60px;
    cursor: pointer;
    background: #ffffff;
    box-shadow: rgb(0 0 0 / 10%) 0px 2px 10px 0px;
    text-align: center;
  }
</style>
