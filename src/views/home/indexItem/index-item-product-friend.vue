<template>
  <index-item-container background="#F7F7F7" title="合作伙伴">
    <div slot="content">
      <div style="display: flex; flex-wrap: wrap;">
        <div v-for="(item, index) in data" :key="'item' + index" style="width: 25%; max-width: 25%; background: #ffffff; height: 150px; display: flex; justify-content: center;">
          <div style="display: flex; flex-flow: column; justify-content: center;">
           <div>
             <el-image :src="item.src"></el-image>
           </div>
          </div>
        </div>
      </div>
    </div>
  </index-item-container>
</template>

<script>
  import IndexItemContainer from "./index-item-container";
  import {getImageUrl} from "../../../util/util";
  export default {
    name: "index-item-product-friend",
    components: {IndexItemContainer},
    data() {
      return {
        data: [
          {
            src: getImageUrl("/home/v2_rik0xq.jpg")
          },
          {
            src: getImageUrl("/home/v2_rik0xq.jpg")
          },
          {
            src: getImageUrl("/home/v2_rik0xq.jpg")
          },
          {
            src: getImageUrl("/home/v2_rik0xq.jpg")
          },
          {
            src: getImageUrl("/home/v2_rik0xq.jpg")
          },
          {
            src: getImageUrl("/home/v2_rik0xq.jpg")
          },
          {
            src: getImageUrl("/home/v2_rik0xq.jpg")
          },
          {
            src: getImageUrl("/home/v2_rik0xq.jpg")
          },
        ]
      }
    },
    computed: {
      userData() {
        if (this.data.length === 4) {
          return [[this.data[0], this.data[1]], [this.data[2], this.data[3]]];
        }
        return [];
      }
    }
  }
</script>

<style scoped>

</style>
