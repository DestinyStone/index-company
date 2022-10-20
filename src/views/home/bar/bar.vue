<template>
  <div>
    <div class="bar">
      <div :style="{width: width + 'px'}">
        <div style="display: flex; justify-content: space-around;">
          <div ref="title">
            <slot name="title"/>
          </div>
          <div ref="content" :style="{width: contentWidth + 'px'}">
            <slot name="content"/>
          </div>
          <div ref="phone">
            <slot name="phone"/>
          </div>
        </div>
      </div>
    </div>
    <div style="height: 80px;"></div>
  </div>
</template>

<script>
  export default {
    name: "bar",
    data() {
      return {
        width: 0,
        contentWidth: 0,
      }
    },
    methods: {
      setWidth() {
        this.width = window.innerWidth;
      },
      setContentTitle() {
        let contentWidth = window.innerWidth - (this.$refs['title'].offsetWidth + this.$refs['phone'].offsetWidth) - 100;
        this.contentWidth = contentWidth > 1000 ? 1000: contentWidth;
      }
    },
    mounted() {
      this.setWidth();
      this.setContentTitle();
    }
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
