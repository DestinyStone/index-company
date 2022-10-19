<template>
  <index-item-container class="product-concat"  background="#F7F7F7" min-title="专业的产品介绍一对一客户服务" min-title-position="bottom" title="联系我们, 获取尊享服务">
    <div slot="content">
      <div style="display: flex; justify-content: center;">
        <div>
          <div class="concat-button">
            <div style="padding-left: 20px;">
              联系我们
              <i class="el-icon-right"/>
            </div>
          </div>
        </div>
      </div>
    </div>
  </index-item-container>
</template>

<script>
  import IndexItemContainer from "./index-item-container";
  export default {
    name: "index-item-product-concat",
    components: {IndexItemContainer},
    data() {
      return {

      }
    },
  }
</script>

<style scoped>
  .product-concat .concat-button {
    width: 200px;
    height:  55px;
    line-height: 55px;
    background: #2468F2;
    text-align: center;
    color: #ffffff;
    font-size: 20px;
    cursor: pointer;
  }
</style>
